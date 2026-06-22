# 5 скиллов для Claude Code

Подборка из рилса: пять скиллов, которые делают Claude Code сильнее. Маркетинговый отдел, человеческий текст, дорогой дизайн, видео по одному промпту и экономия токенов.

Все пять – чужие открытые проекты. Здесь только мой гайд и ссылки на оригиналы авторов. Файлы скиллов не копирую: ставишь их с репозиториев авторов, ниже команды.

## Как вообще ставится скилл Claude Code

Скилл живёт в `~/.claude/skills/<имя>/SKILL.md`. Три рабочих способа:

```bash
# 1. через плагин-маркет (если у автора он настроен)
/plugin marketplace add <owner>/<repo>

# 2. через npx skills (open-стандарт agentskills.io)
npx skills add <owner>/<repo>

# 3. руками – просто клонируешь папку в скиллы
git clone https://github.com/<owner>/<repo>.git ~/.claude/skills/<имя>
```

После установки перезапусти сессию – Claude увидит новый скилл и сам подтянет его, когда задача подходит.

---

## 1. Marketing Skills – маркетинговый отдел в терминале

Набор готовых маркетинговых скиллов от **Corey Haines**: CRO, копирайтинг, SEO, аналитика, имейл-воронки, конкурентный анализ, разбор позиционирования, планирование кампаний. На момент рилса их было около 23, сейчас уже 45 – репозиторий растёт. Подключаешь нужные – и агент работает как маркетинговая команда.

- Репозиторий: https://github.com/coreyhaines31/marketingskills
- Лицензия: MIT · автор [Corey Haines](https://corey.co)
- Установка:
  ```bash
  npx skills add coreyhaines31/marketingskills          # все скиллы
  npx skills add coreyhaines31/marketingskills --list    # список
  # или через плагин:
  /plugin marketplace add coreyhaines31/marketingskills
  /plugin install marketing-skills@marketingskills
  ```

## 2. Stop Slop – Claude пишет по-человечески

Скилл от **Hardik Pandya**. Убирает AI-почерк: канцелярит, длинные тире, штампы, «рамочные» обороты, лишние наречия. Один markdown-файл, никакого кода – кладёшь в скиллы, и текст перестаёт пахнуть нейросетью.

- Репозиторий: https://github.com/hardikpandya/stop-slop
- Лицензия: MIT · автор [Hardik Pandya](https://hvpandya.com)
- Установка:
  ```bash
  git clone https://github.com/hardikpandya/stop-slop.git ~/.claude/skills/stop-slop
  ```

## 3. UI UX Pro Max – интерфейсы, которые выглядят дорого

Дизайн-база от **nextlevelbuilder**: 67 стилей, 161 палитра, 57 пар шрифтов, 99 UX-правил, 25 типов графиков под 10 стеков (React, Next.js, Vue, Svelte, Tailwind, shadcn/ui, SwiftUI, Flutter и др.). Claude рисует UI по системе, а не дефолтным шаблоном. Самый популярный дизайн-скилл сообщества.

- Репозиторий: https://github.com/nextlevelbuilder/ui-ux-pro-max-skill
- Лицензия: MIT · сайт [uupm.cc](https://uupm.cc)
- Установка:
  ```bash
  /plugin marketplace add nextlevelbuilder/ui-ux-pro-max-skill
  /plugin install ui-ux-pro-max@ui-ux-pro-max-skill
  # либо через CLI:
  npm install -g uipro-cli
  uipro init --ai claude --global
  ```

## 4. Remotion – анимированное видео по одному промпту

Remotion – это видео на React: описываешь ролик словами, Claude собирает его кодом, любую правку вносишь сообщением в чат. Тот самый рилс частично собран на нём.

Официальный скилл Remotion – это internal-пакет **без отдельной лицензии и документации**, отдельно ставить его неудобно. Поэтому проще взять мой готовый стартер-пак: скилл + шаблон ролика 9:16 + формулировки правок, проверено от установки до рендера.

- Официальный скилл: https://github.com/remotion-dev/skills (internal, без лицензии)
- **Готовый стартер-пак (рекомендую):** https://github.com/maximsamus/remotion-starter-pack
- Лицензия стартер-пака: MIT. Сам движок Remotion – бесплатно для физлиц, НКО и компаний до 3 человек; от 4 сотрудников нужна Company License ([remotion.pro/license](https://remotion.pro/license)).
- Установка стартер-пака:
  ```bash
  git clone https://github.com/maximsamus/remotion-starter-pack
  cp -R remotion-starter-pack/skill ~/.claude/skills/remotion-starter
  npx create-video@latest
  ```

## 5. Context Engineering Kit – меньше токенов, реже лимиты

Набор скиллов от **NeoLabHQ** с минимальным token-footprint: команды-ориентированные скиллы и суб-агенты вместо «простыней» контекста. Контекст забивается меньше – реже упираешься в лимит, ответы дешевле и стабильнее.

- Репозиторий: https://github.com/NeoLabHQ/context-engineering-kit
- Лицензия: GPL-3.0 · док [neolab.gitbook.io/cek](https://neolab.gitbook.io/cek)
- Установка:
  ```bash
  /plugin marketplace add NeoLabHQ/context-engineering-kit
  /plugin install <плагин>@context-engineering-kit   # напр. reflexion, sdd
  # или точечно через npx:
  npx -y skills add neolabhq/context-engineering-kit --skill <имя> --agent claude-code
  ```

---

## Промпты-примеры

Короткие формулировки, чтобы запустить каждый скилл из чата, – в [`prompts-examples.md`](./prompts-examples.md).

## Лицензия

Этот гайд – под [MIT](./LICENSE). Каждый из пяти скиллов живёт по своей лицензии (указана выше), ставится с репозитория автора. Уважайте лицензии оригиналов.

---

Собрал **Максим Самусь** – зарабатываю на нейросетях, собираю на них продукты для себя и бизнеса. Разборы и инструменты – в канале [@ai_smart_usage](https://t.me/ai_smart_usage).
