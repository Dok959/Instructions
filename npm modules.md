# Установка и обновление модулей node.js
### Обновление npm
Чтобы обновить версию npm требуется установить [следующий модуль](https://www.npmjs.com/package/npm-windows-upgrade) 

    npm install --global npm-windows-upgrade
    
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

---
### Eslint (стандарт языка)
Для начала необходимо установить библиотеку

    npm install -g eslint
Далее требуется установить обновить все требуемые плагины

    npm install -g eslint-config-airbnb-base eslint-plugin-import
Создать в корне проекта файл конфигурации `.eslintrc.yml` и добавить в него следующее:

    extends:  
	   -  'airbnb-base'  
	env:  
	   node:  true  
	   browser:  true
Установить расширение “[linter-eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)” в VS Code.

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
Все секретные данные стоит хранить в файле `.env` расположенном в корне проекта. Данный файл не должен индексироваться, а также должен как можно раньше подгружаться в проект при запуске. Для работы с такими файлами требуется установить:

    npm install dotenv

Подключить данный файл можно используя команду:

    require('dotenv').config()

Для удобной работы с файлами можно установить расширение [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv) в VS Code.

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

