# PBOX Pereval: тестовая версия

Отдельная ветка для адаптации оригинального проекта «Перевал» к VDS. Основная ветка `main` не изменена.

## Параметры стенда

- ОС: Ubuntu 24.04 LTS
- Имя сервера: `box-988502`
- IPv4: `170.168.107.36`
- Домен: `dns.pbox-bk.ru`
- Список сервисов и исключений: оригинальный `services.yaml`
- На VDS уже есть AdGuard Home и Nginx; **новая версия ещё не развёрнута**

## Предварительная проверка без изменения работающих служб

```bash
sudo apt update
sudo apt install -y git python3 python3-yaml
cd /opt
sudo git clone --branch pbox-vds-setup https://github.com/FunTom88/pereval.git pbox-pereval
cd /opt/pbox-pereval
python3 generate.py services.yaml 170.168.107.36 --check
mkdir -p /tmp/pbox-generated
python3 generate.py services.yaml 170.168.107.36 --out-dir /tmp/pbox-generated
ls -lh /tmp/pbox-generated
```

Оригинальный генератор получает IP аргументом, а наш домен и название уже указаны в `services.yaml`.

## Перед переключением

1. Создать snapshot VDS и копию текущих `/etc/nginx`, `/opt/AdGuardHome`, `/etc/letsencrypt` и настроек firewall.
2. Учесть, что прежний DoH через Nginx занимает TCP 443. В оригинальном «Перевале» этот порт используется для SNI TCP proxy. Одновременно использовать оба конфига без дополнительного маршрутизатора нельзя.
3. Проверить конфликт dnsmasq с `systemd-resolved` на порту 53 и доступность SSH.
4. Проверить сгенерированный Nginx и dnsmasq перед переключением служб. Не направлять системный DNS самого VDS на Smart DNS во избежание циклических подключений.
5. Ограничить доступ к рекурсивному DNS на порту 53 доверенными адресами: открытый DNS может использоваться посторонними.
6. Переключать устройства по одному, сначала Android по DoT, затем ПК/роутер.

`deploy.sh` и существующий GitHub Actions workflow пока не адаптированы к этому серверу: **не запускайте автоматическое развёртывание**. Настройка в GitHub сама по себе не изменяет сервер.

## Проверки после будущего развёртывания

```bash
dig @127.0.0.1 claude.ai A +short
dig @127.0.0.1 google.com A +short
```

Для Android системный «Частный DNS» (DoT) будет использовать имя `dns.pbox-bk.ru`, без URL `https://`. Обычный DNS Windows требует доступного порта 53 и не эквивалентен прежнему DoH.

Для обновления списка сервисов редактируем `services.yaml`, затем запускаем `generate.py --check` и тестируем изменения прежде, чем переносить их на сервер.
