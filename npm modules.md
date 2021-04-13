# Установка и обновление модулей node.js
### Установка пакетов
Чтобы установить пакет требуется выполнить команду:

    npm install <название пакета>
Для упрощения `install` можно заменить на `i`.

Для установки пакета глобально требуется добавить флаг `--global` или `-g`.

Для установки пакета в проект как зависимость для разработки добавить флаг `-save-d` или `--save-dev`.

---
### Обновление npm
Чтобы обновить версию npm требуется установить [следующий модуль](https://www.npmjs.com/package/npm-windows-upgrade)

    npm install --global npm-windows-upgrade

Для того, чтобы обновить npm, открыть PowerShell и выполнить команду:

    Set-ExecutionPolicy Unrestricted -Scope CurrentUser -Force

Для запуска процесса обновления выполнить указанную ниже команду.

    npm-windows-upgrade

После выполнения команды стрелками выбрать нужную версию и нажать **ENTER**.

В случае, если происходят ошибки, обратиться к указанной странце на которой расположена информация о данном модуле. Возможно потребуется выполнение дополнительных команд.

---
### Обновление пакетов
Чтобы обновить конкретный пакет требуется выполнить

    npm update <имя_пакета>
Для обновления всех пакетов в проекте выполнить

    npm update --save

### Удаление пакетов
Чтобы удалить пакет требуется выполнить

    npm uninstall <имя_пакета> <-g>
Флаг `-g` имеет смысл использовать если нужно удалить пакет установленый глобально.

---
### [Eslint](https://www.npmjs.com/package/eslint) (стандарт языка)
Для начала необходимо установить библиотеку

    npm install -g eslint
Далее требуется установить обновить все требуемые плагины

    npm install -g eslint-config-airbnb-base eslint-plugin-import
Выполнить из корня проекта команду:

    eslint --init
Далее следовать инструкции установщика.

!!! Рекомендуется выбрать файл `yml` и популярное руководство `airbnb-base`.

В итоге получится файл конфигурации `.eslintrc.yml`. В него рекомендуется добавить следующее:

    env:
        browser: true
        commonjs: true
        es2021: true
        node: true
    extends:
        - airbnb-base
        - prettier
    parserOptions:
        ecmaVersion: 12
    rules: {
        'linebreak-style': 0,
        'indent': 0,
        'no-param-reassign': 0,
        'no-console': 0,
        'no-unreachable': 0,
        'no-alert': 0,
        'no-unused-vars': 0,
        'no-undef': 0,
        'no-restricted-syntax': 0,
        'class-methods-use-this': 0,
        'no-unused-expressions': 0,
        'no-array-constructor': 0,
    }
Часть с правилами (`rules`) является не обязательно и приведена для примера.

---
### [Nodemon](https://www.npmjs.com/package/nodemon) (авто перезапуск проекта)

Установка глобально

    npm install -g nodemon
Установка в качестве зависимости разработки

    npm install --save-dev nodemon
Для запуска проекта из данной библиотеки требуется добавить в файл `package.json` следующее:

    "scripts": {
	    "dev": "nodemon index.js"
	}

---
### Работа с переменными среды
Cекретные данные стоит хранить в файле `.env` расположенном в корне проекта. Данный файл не должен индексироваться, а также должен как можно раньше подгружаться при запуске проекта. Для работы с такими файлами требуется установить:

    npm install dotenv

Подключить данный файл можно используя команду:

    require('dotenv').config()

---
### [Prettier](https://www.npmjs.com/package/prettier) (форматирование кода)
Для установки пакеты выполнить команду:

    npm i -g prettier
Выполнить из корня проекта команду:

    prettier --init
Далее следовать инструкции установщика.

!!! Рекомендуется выбрать файл `yml`

В итоге получится файл конфигурации `.prettierrc.yaml`. В него рекомендуется добавить следующее:

    trailingComma: "es5"
    tabWidth: 4
    semi: true
    singleQuote: true
    printWidth: 80
    bracketSpacing: true
    arrowParens: "always"
Данные правила также можно задать через настройки расширение для VSCode.

Также рекомендуется создать файл `.prettierignore`, в который добавить указания о тех файлах и папках, которые должны игнорироваться. Желательно чтобы данный файл основывался на данных из `.gitignore`. Например:

    # Ignore artifacts:
    build
    coverage

    # Ignore all HTML files:
    *.html

Для корректной работы пакета с пакетом ESLint, рекомендуется установить пакеты:

    npm i -save-d eslint-config-airbnb-base eslint-config-prettier eslint-plugin-import

---
### [Jest](https://jestjs.io/docs/en/getting-started) (тестирование)
Для того чтобы установить библиотеку нужно выполнить команду

    npm install --save-dev jest
Также следует добавить в `package.json`

    "scripts": {
	    "test": "jest"
    }
Это позволит запускать тесты всех скриптов сразу.
Для того, чтобы обеспечить получение информативных сообщений о покрытии проекта тестами, также стоит указать в файл `package.json` следующие команды:

    "jest": {
	    "collectCoverage": true,
	    "coverageReporters": ["html"]
    }
 Если не требуется формировать вывод информации в виде html страницы, то команду `"coverageReporters": ["html"]` можно убрать.

    require('iconv-lite').encodingExists('foo')
