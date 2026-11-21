# PBOX Admin 1.2: расширенный каталог и диагностика

Рабочая установка: Ubuntu 24.04, `dns.pbox-bk.ru`, VDS `170.168.107.36`, PBOX Admin на `127.0.0.1:8090` (доступ только через SSH-туннель).

## Изменения каталога

В `services.yaml` расширен Spotify: `spotify.com`, `spotify.dev`, `scdn.co`, `spotifycdn.com`, `spotifycdn.net`, `spoti.fi`.

Добавлены: Notion (`notion.so`, `notion.com`, `notion.new`, `notionusercontent.com`, `notion-static.com`, `makenotion.com`), Miro (`miro.com`, `realtimeboard.com`), ElevenLabs (`elevenlabs.io`, `elevenmusic.io`, `elevenreader.io`). Список адаптирован из актуального `amak-tech/pereval` на 22.11.2026. Другие сервисы оригинала не включены автоматически.

## Как обновить VDS

1. Сначала установить пакет **PBOX Admin 1.2** из архива, предоставленного отдельно вместе с инструкцией. Установщик сохраняет пароль, `rules.json` и настройки DNS/DoH/Nginx.
2. Выполнить:

```bash
cd /opt/pbox-pereval
git status --short
git pull --ff-only origin pbox-vds-setup
python3 generate.py services.yaml 170.168.107.36 --check
```

3. Подключиться по SSH-туннелю:

```powershell
ssh -N -L 8090:127.0.0.1:8090 root@170.168.107.36
```

4. В панели `http://127.0.0.1:8090`, вкладка «Домены» нажать **«Проверить и применить»**. Панель сгенерирует новые правила, обновит только `dnsmasq.conf` и карты Nginx, выполнит тесты, сделает резервную копию. **Не применять сгенерированный `nginx.conf`**, поскольку он может стереть рабочий DoH.

## Мониторинг

При установке PBOX Admin 1.2 добавляется `pbox-admin-monitor.timer` (каждые пять минут) и вкладка «Диагностика», которая проверяет:

- DNS-ответ от `127.0.0.1:53` и IP PBOX;
- реальный TLS/SNI через `127.0.0.1:443` и действительность сертификата;
- HTTP-код и время ответа `GET /` через SNI-прокси;
- состояния systemd-служб.

Отдельный непривилегированный пользователь мониторинга сохраняет снимок в `/var/lib/pbox-admin/diagnostics/status.json`, историю смен состояний в `events.jsonl`. Ошибки фильтруются порогом в две последовательные проверки. Мониторинг **не перезагружает сервисы автоматически**.

```bash
systemctl list-timers --all pbox-admin-monitor.timer
journalctl -u pbox-admin-monitor -n 50 --no-pager
dig @127.0.0.1 www.spotify.com A +short
```

Никаких изменений в UFW, DoT, DoH, Certbot и правила доступа снаружи.
