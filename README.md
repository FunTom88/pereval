# Перевал — бесплатный DNS-прокси для доступа к ChatGPT, Claude, Gemini и инструментам разработки

**Перевал** — это бесплатный умный DNS-сервер (Smart DNS), который восстанавливает доступ к зарубежным ИИ и инструментам разработки, ограничивающим российские и белорусские IP-адреса по геолокации, **без установки VPN-приложений**, без регистрации и без падения скорости интернета.

👉 **Пошаговая инструкция по подключению и актуальные настройки:**  
**[https://pereval.portbuddy.tech](https://pereval.portbuddy.tech/?utm_source=github&utm_medium=readme&utm_campaign=pereval&utm_content=hero)**

---

## Зачем нужен Перевал

Многие зарубежные нейросети, облачные платформы и инструменты разработки закрывают доступ по геолокации (ошибки *«Unavailable in your country»*, *«Access denied»*, *«Недоступно в вашем регионе»*).

Обычный VPN перенаправляет весь ваш трафик через чужой сервер — из-за этого падает скорость, растёт пинг, отваливаются локальные контейнеры и корпоративные сети, а российские сайты, банки и Госуслуги перестают открываться.

**Перевал решает эту проблему точечно:**
- **Работают только нужные сайты:** через прокси идут исключительно популярные зарубежные AI-сервисы и инструменты для разработчиков, которые ограничивают российские и белорусские IP-адреса по геолокации со своей стороны.
- **Все остальные сайты открываются напрямую:** российские банки, Госуслуги, маркетплейсы, видео и торренты работают на полной скорости вашего провайдера.
- **Без программ и аккаунтов:** настройка занимает одну минуту в стандартных параметрах вашего устройства или роутера.
- **Безопасность данных:** ваши соединения по HTTPS остаются зашифрованными от вашего браузера или приложения до конечного сервиса.

---

## Какие сервисы работают через Перевал

На сайте **[pereval.portbuddy.tech](https://pereval.portbuddy.tech/?utm_source=github&utm_medium=readme&utm_campaign=pereval&utm_content=services)** поддерживаются самые востребованные сервисы для работы с ИИ и разработки (132 домена) с удобным поиском и проверкой:

- **ИИ и языковые модели:** ChatGPT (OpenAI), Claude (Anthropic), Google Gemini, AI Studio, NotebookLM и Jules, Grok (xAI), Microsoft Copilot, Cursor, Windsurf / Codeium, OpenRouter, Groq, Lambda Labs, Lightning AI, Augment Code, Cline, Trae, Qoder, Manus, Genspark, Langdock, DeepL.
- **Инструменты разработки, SaaS и облака:** JetBrains (IDE, AI Assistant, Toolbox, YouTrack, Qodana), HashiCorp (Terraform, Vagrant), Atlassian (Jira, Confluence), Sentry, MongoDB, Redis, Neo4j, Liquibase, Grafana, Graylog, Snyk, PostHog, Amplitude, Pingdom, Buf, Spacelift, Algolia, GitGuardian, Swagger, Netlify, Heroku, Framer, Ngrok, Tailscale, HTTP Toolkit, Oracle, Liberica JDK, Qt, Bitnami, NVIDIA Developer, Mattermost, Outline, ClickUp, Zapier.

> Полный и всегда актуальный список поддерживаемых сайтов и доменных зон доступен на сайте: **[pereval.portbuddy.tech](https://pereval.portbuddy.tech/?utm_source=github&utm_medium=readme&utm_campaign=pereval&utm_content=services_footer)**.

---

## На каких устройствах работает

Подключить **Перевал** можно практически на любом устройстве:

- **iPhone и iPad (iOS / iPadOS)** — через готовый профиль конфигурации (работает и в Wi-Fi, и в мобильной сети).
- **Android** — через встроенную функцию «Частный DNS» (Private DNS) в настройках системы.
- **Компьютеры и ноутбуки** — macOS, Windows 10/11, Linux.
- **Домашние роутеры (Keenetic, MikroTik, ASUS, TP-Link и др.)** — достаточно прописать DNS один раз на роутере, чтобы сервисы заработали сразу на всех устройствах в сети.

---

## Как подключиться

Перейдите на официальный сайт **[https://pereval.portbuddy.tech](https://pereval.portbuddy.tech/?utm_source=github&utm_medium=readme&utm_campaign=pereval&utm_content=setup)** — там вы найдёте:

1. **Актуальный адрес DNS-сервера** и кнопку установки профиля для iOS в один клик.
2. **Подробные пошаговые инструкции** для каждой операционной системы (iOS, Android, macOS, Windows, Linux).
3. **Интерактивный поиск по списку сервисов** — чтобы быстро проверить, поддерживается ли нужный вам сайт или приложение.
4. **Ответы на частые вопросы (FAQ)** — как проверить работу, что делать, если сайт не открывается, и как при необходимости отключить DNS.

---

## Предложить новый сервис

Если нужный вам зарубежный сервис ограничивает доступ по региону (выдаёт ошибку региональной недоступности), но его ещё нет в списке на **[pereval.portbuddy.tech](https://pereval.portbuddy.tech/?utm_source=github&utm_medium=readme&utm_campaign=pereval&utm_content=request)** — создайте обращение в разделе **[Issues](https://github.com/amak-tech/pereval/issues)** репозитория **[github.com/amak-tech/pereval](https://github.com/amak-tech/pereval)** и укажите адрес сайта или название приложения.

---

> **Правовое примечание:** Сервис не является средством обхода блокировок Роскомнадзора или Мининформа РБ, работает строго по фиксированному списку незапрещённых зарубежных IT-платформ и не предоставляет доступ к ресурсам, ограниченным законодательством РФ и РБ. Используя сервис, вы принимаете [Пользовательское соглашение](https://pereval.portbuddy.tech/terms.html) и [Политику конфиденциальности](https://pereval.portbuddy.tech/privacy.html).
