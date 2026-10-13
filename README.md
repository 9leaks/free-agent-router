# AgentRouter — подключение к VS Code, Claude Code CLI и другим инструментам

AgentRouter — это единый API-шлюз к популярным LLM: Claude, GPT, DeepSeek и другим. Регистрация через GitHub даёт стартовые бонусы, а каждый день можно получать дополнительные кредиты за вход.

👉 **Регистрация с бонусом:** [https://agentrouter.org/register?aff=g96u](https://agentrouter.org/register?aff=g96u)

---

## 1. Регистрация и получение API-ключа

1. Откройте [https://agentrouter.org/register?aff=g96u](https://agentrouter.org/register?aff=g96u).
2. Войдите через **GitHub**.
3. В левом меню перейдите в **API Keys** → **Create Key**.
4. Задайте имя, например `vscode-key`.
5. Скопируйте токен вида `sk-...`. Он понадобится для всех инструментов.

### 🎁 Бонусы при регистрации

При переходе по реферальной ссылке вы получаете:

| Бонус | Сумма |
|---|---|
| Стартовый бонус за регистрацию через GitHub | **$175** |
| Реферальный бонус по ссылке | **+$50** |
| **Итого на старте** | **$225** |

### Ежедневный бонус

На AgentRouter также начисляют дополнительный баланс за ежедневный вход. Чтобы забрать бонус, не нужно менять ключ или пересобирать настройки. Достаточно на сайте AgentRouter выйти из аккаунта и войти заново: **Log out → Log in**. Баланс обновится автоматически.

---

## 2. Базовые URL и модели

Используйте эти адреса в зависимости от типа инструмента:

| Тип API | Base URL |
|---|---|
| OpenAI-совместимый | `https://agentrouter.org/v1` |
| Anthropic-совместимый | `https://agentrouter.org` |

---

## 3. Актуальный список моделей и цены

| Model Name | Поддерживаемые эндпоинты | Model Ratio | Completion Ratio | Prompt / 1M | Completion / 1M |
|---|---|---|---|---|---|
| `gpt-6-astra` | openai | 4 | 5 | **$8.00** | **$40.00** |
| `claude-opus-4-8` | anthropic, openai | 4 | 5 | **$8.00** | **$40.00** |
| `claude-opus-5` | anthropic, openai | 3 | 5 | **$6.00** | **$30.00** |
| `deepseek-v4-flash` | openai, anthropic | 2 | 3 | **$4.00** | **$12.00** |

> Все модели работают по модели оплаты **Pay as you go** (оплата по факту использования). Названия моделей и цены могут обновляться — проверяйте актуальный список в консоли AgentRouter.

---

## 4. Модели подробнее

### 4.1. GPT-6-Astra

Флагманская модель от OpenAI, доступная через OpenAI-совместимый эндпоинт.

- **Цена:** $8.00 / 1M входных токенов, $40.00 / 1M выходных токенов.
- **Эндпоинт:** только `openai` (Chat Completions).
- **Для чего использовать:** максимально сложные задачи, глубокий анализ, генерация большого объёма кода, критически важные приложения.
- **Base URL:** `https://agentrouter.org/v1`
- **Model ID:** `gpt-6-astra`

### 4.2. Claude Opus 4.8

Мощная модель от Anthropic, доступная как через Anthropic, так и через OpenAI-совместимый эндпоинт.

- **Цена:** $8.00 / 1M входных токенов, $40.00 / 1M выходных токенов.
- **Эндпоинты:** `anthropic` (`/v1/messages`) и `openai` (`/v1/chat/completions`).
- **Для чего использовать:** сложные рассуждения, работа с длинным контекстом, написание и рефакторинг кода, агентные задачи.
- **Base URL:** `https://agentrouter.org` (для Anthropic) или `https://agentrouter.org/v1` (для OpenAI).
- **Model ID:** `claude-opus-4-8`

### 4.3. Claude Opus 5

Более новая и доступная версия Opus с оптимизированной стоимостью.

- **Цена:** $6.00 / 1M входных токенов, $30.00 / 1M выходных токенов.
- **Эндпоинты:** `anthropic` и `openai`.
- **Для чего использовать:** те же задачи, что и у Opus 4.8, но с меньшими затратами. Хороший баланс между качеством и ценой для повседневной работы.
- **Base URL:** `https://agentrouter.org` или `https://agentrouter.org/v1`
- **Model ID:** `claude-opus-5`

### 4.4. DeepSeek V4 Flash

Экономичная модель от DeepSeek с поддержкой обоих типов эндпоинтов.

- **Цена:** $4.00 / 1M входных токенов, $12.00 / 1M выходных токенов.
- **Эндпоинты:** `openai` и `anthropic`.
- **Контекст:** до 1M токенов.
- **Для чего использовать:** написание и рефакторинг кода, логический вывод, высоконагруженные задачи (суммаризация, классификация, извлечение данных), прототипирование. Благодаря низкой цене отлично подходит для черновой работы и больших объёмов.
- **Base URL:** `https://agentrouter.org/v1` или `https://agentrouter.org`
- **Model ID:** `deepseek-v4-flash`

---

## 5. VS Code

### 5.1. Cline / Roo Code

1. Установите расширение **Cline** или **Roo Code**.
2. Откройте настройки расширения (шестерёнка) → **API Provider**.
3. Выберите провайдера **Anthropic**.
4. Заполните:
   - **Base URL:** `https://agentrouter.org`
   - **API Key:** ваш ключ `sk-...`
   - **Model:** `claude-opus-5`, `claude-opus-4-8`, `gpt-6-astra` или `deepseek-v4-flash`
5. Сохраните настройки.

### 5.2. Официальное расширение Claude Code для VS Code

1. Установите расширение **Claude Code**.
2. Откройте `Ctrl/Cmd + Shift + P` → **Open User Settings (JSON)**.
3. Добавьте:

```json
{
  "claudeCode.environmentVariables": [
    { "name": "ANTHROPIC_AUTH_TOKEN", "value": "ВАШ_КЛЮЧ" },
    { "name": "ANTHROPIC_BASE_URL", "value": "https://agentrouter.org" },
    { "name": "CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY", "value": "1" },
    { "name": "ANTHROPIC_MODEL", "value": "claude-opus-5" }
  ],
  "claudeCode.disableLoginPrompt": true,
  "claudeCode.initialPermissionMode": "acceptEdits"
}
```

Замените `claude-opus-5` на `claude-opus-4-8`, `gpt-6-astra` или `deepseek-v4-flash` при необходимости.

4. В настройках расширения включите **Disable Login Prompt**.
5. Перезапустите VS Code.

### 5.3. GitHub Copilot Chat (Custom Endpoint)

1. Откройте боковую панель **Copilot Chat**.
2. Перейдите в **Manage Models** → **Add Model** → **Custom Endpoint**.
3. Укажите:
   - **Название:** `AgentRouter`
   - **API Key:** ваш ключ `sk-...`
   - **Base URL:** `https://agentrouter.org/v1`
   - **Формат:**
     - для GPT-6-Astra, DeepSeek — `Chat Completions`
     - для Claude — `Messages`
   - **Model ID:** `gpt-6-astra`, `deepseek-v4-flash`, `claude-opus-4-8` или `claude-opus-5`
4. Сохраните и выберите модель в чате.

---

## 6. Claude Code CLI

Установка:

```bash
npm install -g @anthropic-ai/claude-code
```

### Windows (PowerShell)

```powershell
$env:ANTHROPIC_BASE_URL="https://agentrouter.org"
$env:ANTHROPIC_AUTH_TOKEN="sk-ваш-ключ"
$env:ANTHROPIC_API_KEY="sk-ваш-ключ"
$env:ANTHROPIC_MODEL="claude-opus-5"
claude
```

### Linux / macOS (Bash)

```bash
export ANTHROPIC_BASE_URL="https://agentrouter.org"
export ANTHROPIC_AUTH_TOKEN="sk-ваш-ключ"
export ANTHROPIC_API_KEY="sk-ваш-ключ"
export ANTHROPIC_MODEL="claude-opus-5"
claude
```

Чтобы не вводить переменные каждый раз, добавьте их в `~/.bashrc`, `~/.zshrc` или в профиль PowerShell.

---

## 7. Cursor IDE

1. Откройте **Settings** → **Models**.
2. Включите **OpenAI API Key**.
3. Введите ваш ключ `sk-...`.
4. Включите **Override OpenAI Base URL** и укажите:

```text
https://agentrouter.org/v1
```

5. Добавьте модели вручную:
   - `gpt-6-astra`
   - `claude-opus-5`
   - `claude-opus-4-8`
   - `deepseek-v4-flash`

6. Сохраните настройки и выберите модель в чате Cursor.

---

## 8. OpenCode

В файл `~/.config/opencode/opencode.jsonc` добавьте провайдера:

```json
{
  "providers": {
    "agentrouter": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "AgentRouter",
      "options": {
        "baseURL": "https://agentrouter.org/v1",
        "apiKey": "sk-ваш-ключ"
      },
      "models": {
        "gpt-6-astra": { "name": "GPT-6 Astra" },
        "claude-opus-5": { "name": "Claude Opus 5" },
        "claude-opus-4-8": { "name": "Claude Opus 4.8" },
        "deepseek-v4-flash": { "name": "DeepSeek V4 Flash" }
      }
    }
  }
}
```

---

## 9. Aider и другие OpenAI-совместимые инструменты

Для любых инструментов, которые поддерживают OpenAI API, используйте:

```bash
export OPENAI_API_BASE="https://agentrouter.org/v1"
export OPENAI_API_KEY="sk-ваш-ключ"
```

Пример для Aider:

```bash
aider --model deepseek-v4-flash
```

Или для Claude Opus:

```bash
aider --model claude-opus-5
```

Подойдёт для LangChain, LlamaIndex, N8N, Continue.dev, кастомных скриптов и других решений с поддержкой кастомного Base URL.

---

## 10. Частые вопросы

**Ошибка 401 Unauthorized**  
Проверьте, что ключ начинается с `sk-` и скопирован полностью. Убедитесь, что используете правильный Base URL: `https://agentrouter.org` для Anthropic и `https://agentrouter.org/v1` для OpenAI-совместимых инструментов.

**Модель не найдена**  
Проверьте точное название модели в консоли AgentRouter. Названия могут обновляться.

**Какая модель лучше для кода?**  
`claude-opus-5` — оптимальный баланс качества и цены для серьёзных задач. `deepseek-v4-flash` — лучший выбор для больших объёмов и прототипирования благодаря цене $4/1M входных токенов. `gpt-6-astra` и `claude-opus-4-8` — для максимально сложных задач.

**Баланс не пополняется**  
Выйдите из аккаунта AgentRouter и войдите заново. Ежедневный бонус начисляется после повторного входа.

**Можно ли использовать в production?**  
AgentRouter — сторонний сервис. Для критичных проектов лучше использовать прямые API провайдеров или предусмотреть резервный канал.

## 11. Установка инструментов

Прежде чем настраивать AgentRouter, нужно установить сами инструменты. Ниже — инструкции для Windows, macOS и Linux.

---

### 11.1. Установка Node.js и npm

**npm** входит в состав **Node.js**, поэтому отдельно его ставить не нужно. Установите Node.js LTS — вместе с ним появится команда `npm`.

#### Windows

Самый простой способ — через встроенный менеджер пакетов **winget**:

```powershell
winget install OpenJS.NodeJS.LTS
```

Либо скачайте установщик с официального сайта: [https://nodejs.org](https://nodejs.org) (выберите версию **LTS**).

После установки **перезапустите терминал** и проверьте:

```powershell
node -v
npm -v
```

#### macOS

Через Homebrew:

```bash
brew install node
```

Либо скачайте установщик с [https://nodejs.org](https://nodejs.org).

Проверка:

```bash
node -v
npm -v
```

#### Linux (Ubuntu / Debian)

```bash
sudo apt update
sudo apt install -y nodejs npm
```

Проверка:

```bash
node -v
npm -v
```

> **Рекомендация для Linux и macOS:** чтобы не использовать `sudo` при глобальной установке пакетов, поставьте **nvm** (Node Version Manager):
>
> ```bash
> curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
> source ~/.bashrc   # или ~/.zshrc
> nvm install --lts
> nvm use --lts
> ```
>
> После этого `npm install -g` будет работать без прав root.

---

### 11.2. Claude Code CLI

Установка через npm:

```bash
npm install -g @anthropic-ai/claude-code
```

Проверка:

```bash
claude --version
```

Обновление до последней версии:

```bash
npm update -g @anthropic-ai/claude-code
```

Если при запуске `claude` появляется ошибка прав доступа — используйте nvm (см. выше) или запустите установку с `sudo` (не рекомендуется).

После установки настройте переменные окружения под AgentRouter:

**Windows (PowerShell):**

```powershell
$env:ANTHROPIC_BASE_URL="https://agentrouter.org"
$env:ANTHROPIC_AUTH_TOKEN="sk-ваш-ключ"
$env:ANTHROPIC_API_KEY="sk-ваш-ключ"
$env:ANTHROPIC_MODEL="claude-opus-5"
claude
```

**Linux / macOS (Bash):**

```bash
export ANTHROPIC_BASE_URL="https://agentrouter.org"
export ANTHROPIC_AUTH_TOKEN="sk-ваш-ключ"
export ANTHROPIC_API_KEY="sk-ваш-ключ"
export ANTHROPIC_MODEL="claude-opus-5"
claude
```

---

### 11.3. OpenCode

Установка через npm:

```bash
npm install -g opencode-ai
```

Проверка:

```bash
opencode --version
```

Альтернативный способ (Linux / macOS) — через установочный скрипт:

```bash
curl -fsSL https://opencode.ai/install | bash
```

После установки откройте или создайте файл `~/.config/opencode/opencode.jsonc` и добавьте провайдера AgentRouter (см. раздел 8).

---

### 11.4. Aider

Aider — это Python-инструмент, поэтому устанавливается через `pip`.

Сначала убедитесь, что установлен Python 3.10+ и pip:

```bash
python --version
pip --version
```

Установка Aider:

```bash
pip install aider-chat
```

Если `pip` не найден в PATH, используйте:

```bash
python -m pip install aider-chat
```

Проверка:

```bash
aider --version
```

Запуск с моделью AgentRouter:

```bash
export OPENAI_API_BASE="https://agentrouter.org/v1"
export OPENAI_API_KEY="sk-ваш-ключ"
aider --model deepseek-v4-flash
```

> **Windows:** если команда `python` не работает, попробуйте `py -m pip install aider-chat`.

---

### 11.5. Cline / Roo Code (VS Code)

Это расширения VS Code, npm для них не нужен.

1. Откройте VS Code.
2. Перейдите в панель расширений (`Ctrl/Cmd + Shift + X`).
3. Найдите **Cline** или **Roo Code**.
4. Нажмите **Install**.
5. Настройте провайдера **Anthropic** с Base URL `https://agentrouter.org` и вашим ключом `sk-...` (см. раздел 5.1).

---

### 11.6. Cursor IDE

Cursor — это отдельный редактор, а не расширение.

1. Скачайте установщик с [https://cursor.com](https://cursor.com).
2. Установите и запустите.
3. Откройте **Settings** → **Models**.
4. Включите **OpenAI API Key**, введите ключ `sk-...`.
5. Включите **Override OpenAI Base URL** и укажите `https://agentrouter.org/v1`.
6. Добавьте модели вручную: `gpt-6-astra`, `claude-opus-5`, `claude-opus-4-8`, `deepseek-v4-flash`.

---

### 11.7. Проверка всех установок

Быстрая проверка, что всё на месте:

```bash
node -v
npm -v
claude --version
opencode --version
aider --version
python --version
```

Если какая-то команда не найдена — вернитесь к соответствующему шагу и перезапустите терминал.

---

👉 **Начать: [https://agentrouter.org/register?aff=g96u](https://agentrouter.org/register?aff=g96u)**
