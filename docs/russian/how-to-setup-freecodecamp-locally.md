# Локальная установка freeCodeCamp

Следуйте этим рекомендациям для локальной установки freeCodeCamp. Это очень рекомендуется если вы собираетесь вкладываться регулярно.

Некоторые процессы вроде предпросмотра страниц для руководства, кодерских испытаний, отладки и исправления ошибок в базе кода, требуют от вас локальной установки freeCodeCamp.

## Копирование репозитория на GitHub

['Копирование'](https://help.github.com/articles/about-forks/) это шаг на котором вы получаете вашу собственную копию основного репозитория freeCodeCamp (также _repo_) на GitHub.

Это важно, потому что этот способ позволит вам работать с собственной копией freeCodeCamp на GitHub, или загрузить её для работы локально. Позже, вы сможете запросить добавление изменений в основной репозиторий при помощи запроса на добавление (pull request'a).

> **Профессиональный совет:**
> Репозиторий по адресу `https://github.com/freeCodeCamp/freeCodeCamp` в основном называется `главным` репозиторием(потоком).
> Ваша копия по адресу `https://github.com/ВАШЕ_ИМЯ_ПОЛЬЗОВАТЕЛЯ/freeCodeCamp` в основном называется `источником` для другого репозитория.

**Следуйте этим шагам чтобы скопировать `https://github.com/freeCodeCamp/freeCodeCamp` репозиторий:**

1. Перейдите на GitHub репозиторий freeCodeCamp: <https://github.com/freeCodeCamp/freeCodeCamp>
2. нажмите кнопку "Fork" в правом верхнем углу интерфейса ([Больше подробностей тут](https://help.github.com/articles/fork-a-repo/))
3. После копирования репозитория, вы будете перемещены к вашей собственной копии freeCodeCamp `https://github.com/ВАШЕ_ИМЯ_ПОЛЬЗОВАТЕЛЯ/freeCodeCamp`

![GIF - Как скопировать freeCodeCamp на Github](/docs/images/github/how-to-fork-freeCodeCamp.gif)

## Подготовка среды разработки

После начальных настроек вам необходимо подготовить среду разработки. Это характерно для многих рабочих процессов разработки, и вам понадобится сделать это только один раз.

**Следуйте этим шагам чтобы подготовить вашу рабочую среду:**

1. Установите [Git](https://git-scm.com/) или ваш любимый Git клиент, если вы не сделали этого раньше. Обновитесь до последней версии, если ваш клиент предустановлен с вашей ОС, то он мог устареть.

2. (Необязательно, но рекомендуется) [Установить SSH ключ](https://help.github.com/articles/generating-an-ssh-key/) для GitHub.

3. Установите редактор кода на свой выбор.

    Мы очень рекомендуем использовать [VS Code](https://code.visualstudio.com/) или [Atom](https://atom.io/). Это отличные бесплатные редакторы кода с открытым исходным кодом.

4. Установите статический анализатор (также lint) для вашего редактора кода.

    У вас в редакторе должен быть запущен [ESLint](http://eslint.org/docs/user-guide/integrations.html), и он подсветит все что не соответствует с [руководством JavaScript стиля от freeCodeCamp](http://forum.freecodecamp.org/t/free-code-camp-javascript-style-guide/19121).

    > Пожалуйста не игнорируйте любые ошибки статического анализатора. Они предназначены чтобы **помочь** вам, для обеспечения чистого и простого кода.

## Клонирование вашей копии freeCodeCamp

['Клонирование'](https://help.github.com/articles/cloning-a-repository/) это шаг в котором вы **скачиваете** копию репозитория, пренадлежащую вам или кому-либо еще, из `удаленной` локации. В вашем случае, эта удаленная локация ваша `копия` репозитория freeCodeCamp, она должна быть доступна по адресу `https://github.com/ВАШЕ_ИМЯ_ПОЛЬЗОВАТЕЛЯ/freeCodeCamp`.

Выполните эти команды на вашем устройстве:

1. Откройте Терминал / Командную строку / Оболочку терминала в директории вашего проекта

    _т.е.: `/директориявашегопроекта/`_

2. Клонируйте вашу копию freeCodeCamp, заменив `ВАШЕ_ИМЯ_ПОЛЬЗОВАТЕЛЯ` вашим именем пользователя GitHub

    ```shell
    git clone https://github.com/ВАШЕ_ИМЯ_ПОЛЬЗОВАТЕЛЯ/freeCodeCamp.git
    ```

Это загрузит весь репозиторий freeCodeCamp в вашу директорию проекта.

## Установка `главного` репозитория

Теперь, когда вы загрузили вашу копию, вам нужно установить `главный` репозиторий.

Как упоминалось ранее, репозиторий по адресу `https://github.com/freeCodeCamp/freeCodeCamp` зачастую называют `главным` репозиторием. Ваша копия по адресу `https://github.com/ВАШЕ_ИМЯ_ПОЛЬЗОВАТЕЛЯ/freeCodeCamp` зачастую называется `источником` для других репозиториев.

Вам нужно создать локальнй клон для `главного` репозитория в дополнение к `источнику`. Это позволит синхронизировать изменения из главного репозитория. Таким образом, вам удастся избежать повторного копирования и клонирования снова и снова.

1. Измените текущую директорию на директорию freeCodeCamp:

    ```shell
    cd freeCodeCamp
    ```

2. Добавьте удаленное соединение с главным репозиторием freeCodeCamp:

    ```shell
    git remote add upstream https://github.com/freeCodeCamp/freeCodeCamp.git
    ```

3. Убедитесь, что конфигурация выглядит хорошо:

    ```shell
        git remote -v
    ```

        На выходе вы должны получить что-то вроде этого:

    ```shell
        origin    https://github.com/YOUR_USER_NAME/freeCodeCamp.git (fetch)
        origin    https://github.com/YOUR_USER_NAME/freeCodeCamp.git (push)
        upstream    https://github.com/freeCodeCamp/freeCodeCamp.git (fetch)
        upstream    https://github.com/freeCodeCamp/freeCodeCamp.git (push)
    ```

## Локальный запуск freeCodeCamp на вашем устройстве

Теперь, когда у вас есть клон freeCodeCamp, вы можете следовать этим интрукциям чтобы локально запустить его. Это позволит вам:

- Предпросматривать изменения страниц, как на обучающей платформе.
- Работать над проблемами и улучшениями связанными с интерфейсом.
- Отлаживать и исправлять проблемы серверов и клиентов приложений.

Вы можете пропустить локальный запуск freeCodeCamp, если вы просто редактируете файлы, проводите `перебазировку` или решаете проблемы `слияния`. Вы всегда сможете вернуться к этой части инструкции позже.

[Пропустить локальный запуск freeCodeCamp](#Локальное-внесение-изменений-в-ваш-клон-freecodecamp)

### Установка необходимого ПО

Начните с установки этого необходимого ПО.

| Необходимое ПО                               | Версия | Записи |
| ------------------------------------------- | ------- | ----- |
| [MongoDB Общественный Сервер](https://docs.mongodb.com/manual/administration/install-community/) | `3.6`   | [Записи релизов](https://docs.mongodb.com/manual/release-notes/), Актуальная версия `3.6`, планируется [обновление](https://github.com/freeCodeCamp/freeCodeCamp/issues/18275).
| [Node.js](http://nodejs.org)                | `8.x`   | [График LTS](https://github.com/nodejs/Release#release-schedule) |
| npm (идет вместе с Node)               | `6.x`   | Не предоставляет LTS релизов, мы используем версию в комплекте с Node LTS |

**Важно:**

Мы настоятельно рекомендуем обновляться до последних стабильных релизов (также известных как LTS релизы) упомянутых выше.
Если Node.js или MongoDB уже установлены на вашем устройстве, выполните следующие команды для проверки версий:

```shell
node -v
mongo --version
npm -v
```

> Если у вас другая версия, пожалуйста установите рекомендуемую версию. Мы предоставляем поддержку только для рекомендуемых версий.

**У меня возникли проблемы с установкой необходимого ПО. Что мне делать?**

Мы регулярно разрабатываем на популярных ОС вроде macOS 10.12 и новее, Ubuntu 16.04 и новее, и Windows 10. Рекомендуется поискать вашу проблему на таких ресурсах как Google, Stack Overflow или Stack Exchange. Скорее всего, кто-то уже столкнулся с той же проблемой, и уже есть конкретное решение.

Если вы используете другую ОС, и/или все еще сталкиваетесь с проблемами, обратитесь к [сообществу разработчиков на нашем общественном форуме](https://www.freeCodeCamp.org/c/contributors) или в [Чат разработчиков](https://gitter.im/freeCodeCamp/Contributors). Возможно мы сможем устранить некоторые распостраненные проблемы.

Мы не можем помочь вам в GitHub, потому-что проблемы с установкой ПО выходят за рамки этого проекта.

### Установка зависимостей

Начните с установки зависимосте, необходимых для запуска приложения.

```shell
# Install NPM dependencies
npm install
```

Затем вам нужно добавить переменные частной среды (API ключи):

```shell
# Создайте копию "sample.env" и назовите ее ".env".
# Заполните ее необходимыми API ключами и секретами:

# macOS / Linux
cp sample.env .env

# Windows
copy sample.env .env
```

Для локального запуска приложения ключи изменять не нужно. Вы можете оставить стандартные значения из `sample.env` как есть.

`MONGOHQ_URL` один из важнейших. Если у вас не был установлен MongoDB с настройками отличными от стандартных, URL адрес в `sample.env` должен отлично работать.

Вы можете оставить остальные ключи как есть. Имейте ввиду, если вы захотите использовать другие сервисы, вам нажно будет получить свои собственные API ключи для этих сервисов и изменить их в`.env`файле.

Затем давайте загрузим разные сервисы, т.е. api-server, клиентское UI приложение, и т.д. Вы можете [узнать больше об этих сервисах в этом руководстве](#).

При загрузке вы связываете ссылки между сервисами. Они полунезависимы. Это значит что в продукции эти сервисы разворачиваются в их собственных местах, но во время локального запуска вы делаете так чтобы все они были доступны для вас.

```shell
# Загрузите все проекты внути этого репозитория
npm run bootstrap
```

### запуск MongoDB

Перез запуском приложения вам нужно запустить MongoDB:

Запустите сервер MongoDB в отдельном терминале

- macOS & Ubuntu:

    ```shell
    mongod
    ```

- Windows, вам нужно указать полный путь к бинарному файлу `mongod`

    Не забудьте заменить `3.6` на установленную вами версию

    ```shell
    "C:\Program Files\MongoDB\Server\3.6\bin\mongod"
    ```

> Професиональный совет:
> Вы можете избежать запуска MongoDB каждый раз, установив его в качестве фонового сервиса.
> Вы можете [узнать больше об этом в документации для вашей ОС](https://docs.mongodb.com/manual/administration/install-community/)

### Наполнение базы данных

Дальше, давайте наполним базу данных. На этом этапе, мы запускаем команду которая наполнит сервер MongoDB некоторыми начальными наборами данных, которые необходимы для других сервисов. Это включает в себя несколько схем, помимо всего прочего.

```shell
npm run seed
```

### Запуск API сервера и клиента freeCodeCamp

Теперь вы можете запустить API сервер и клиентские приложения.

```shell
npm run develop
```

Эта единственная команда запустит все сервисы, включая API сервер и доступные вам клиентские приложения.

Теперь откройте браузер и посетите <http://localhost:8000>. Если приложение загружается, мои поздравления – все готово.

> Профессиональный совет:
>
> API сервер обслуживает API по адресу `http://localhost:3000`
> Приложение Gatsby обслуживает клиентское приложение по адресу `http://localhost:8000`

А это значит, что если вы посетите <http://localhost:3000/explorer> вы должны увидеть все имеющиеся у нас APIs.

Поздравляем 🎉! Теперь у вас есть копия всей обучающей платформы freeCodeCamp на вашем локальном устройстве.

## Ссылка на быстрые команды при локальной работе

[Вот краткая ссылка](/docs/russian/README.md) на список команд которые могут понадобиться время от времени.

## Локальное внесение изменений в ваш клон freeCodeCamp

Теперь, вы можете изменять и фиксировать свои изменения.

Следуйте этим шагам:

1. Убедитесь что вы на `master` ветке

    ```shell
    git status
    ```

    На выходе вы должны получить что-то вроде этого:

    ```shell
    On branch master
    Your branch is up-to-date with 'origin/master'.

    nothing to commit, working directory clean
    ```

    Если вы не на  `master` ветке, или ваша рабочая директория не чиста, разберитесь с любыми выведенными файлами/коммитами и проверьте `master`:

    ```shell
    git checkout master
    ```

2. Затем вы захотите `перебазироваться` из `главного` потока.

    Этот шаг **синхронизирует последние изменения** из главного freeCodeCamp репозитория. Важно проводить `перебазировку` как можно чаще, чтобы избежать возможных конфликтов.

    ```shell
    git pull --rebase upstream master
    ```

    Возможно вы захотите выгрузить эту ветку обратно в ваш `источник`, чтобы иметь чистую историю на своей ветке GitHub.

    ```shell
    git push origin master --force
    ```

3. далее, вам нужно создать новую свежую ветку.

    Работа над каждой проблемой в отдельной ветке поможет вам держать вашу локалуную рабочую копию в чистоте. Вы никогда не должны вести работы в `master` ветке. Это испортит вашу копию freeCodeCamp, и вам, возможно, придется начать с нового клона или ветки.

    Убедитесь в том что вы находитесь в `master` ветке, и, как и объясняется выше, создайте новое ответвление:

    ```shell
    git checkout -b fix/update-guide-for-xyz
    ```

    Имя вашей ветки должно начинаться с `fix/`, `feat/`, и т.д. Избегайте использования номеров вопросов в названиях веток. делайте их короткими, осмысленными и уникальными.

    Вот несколько примеров хороших названий веток:

    ```md
    fix/update-challenges-for-react
    fix/update-guide-for-html-css
    fix/platform-bug-sign-in-issues
    feat/add-guide-article-for-javascript
    translate/add-spanish-basic-html
    ```

4. Next, you can work on the editing pages and working on the code in your favorite text editor.

5. Once you are happy with the changes you should optionally run freeCodeCamp locally to preview the changes.

6. Make sure you fix any errors, and check the formating of your changes. We have style guide for the Guide articles and Coding challenges.

7. Next, check and confirm the files you are updating

    ```shell
    git status
    ```

    This should show a list of `unstaged` files that you have edited.

    ```shell
    On branch feat/documentation
    Your branch is up to date with 'upstream/feat/documentation'.

    Changes not staged for commit:
    (use "git add/rm <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   CONTRIBUTING.md
        modified:   docs/README.md
        modified:   docs/how-to-setup-freecodecamp-locally.md
        modified:   docs/how-to-work-on-guide-articles.md
    ...
    ```

8. Stage the changes and make a commit.

    In this step you should only mark files that you have edited, or added. You can perform a reset, and resolve files that you did not intend to change.

    ```shell
    git add path/to/my/changed/file.ext
    ```

    Or, alternatively you can add all the `unstaged` files to the staging area:

    ```shell
    git add .
    ```

    Only the files that were moved to the staging area will added when you make a commit.

    ```shell
    git status
    ```

    Output:
    ```shell
    On branch feat/documentation
    Your branch is up to date with 'upstream/feat/documentation'.

    Changes to be committed:
    (use "git reset HEAD <file>..." to unstage)

        modified:   CONTRIBUTING.md
        modified:   docs/README.md
        modified:   docs/how-to-setup-freecodecamp-locally.md
        modified:   docs/how-to-work-on-guide-articles.md
    ```

    Now, you can commit your changes with a short message like so:

    ```shell
    git commit -m "fix: my short commit message"
    ```

    Some examples:

    ```md
    fix: update guide article for Java - for loop
    feat: add guide article for alexa skills
    ```

    Optional:

    We highly recommend making a conventional commit message. This is a good practice that you will see on some of the popular Open Source repositories. As a developer, this encourages you to follow standard practices.

    Some examples of conventional commit messages are:

    ```md
    fix: update HTML guide article
    fix: update build scripts for Travis-CI
    feat: add article for JavaScript hoisting
    docs: update contributing guidelines
    ```

    Keep these short, not more than 50 characters. You can always add additional information in the description of the commit message.

    This does not take any additional time than a unconventional message like 'update file' or 'add index.md'

    You can learn more about why you should use conventional commits [here](https://www.conventionalcommits.org/en/v1.0.0-beta.2/#why-use-conventional-commits).

9. If you realise that you need to edit a file or, update the commit message after making a commit you can do so after editing the files with:

    ```shell
    git commit --amend
    ```

    This will open up a default, text editor like `nano` or `vi` where you can edit the commit message title and add/edit description.

10. Next, you can push your changes to your fork.

    ```shell
    git push origin branch/name-here
    ```

## Proposing a Pull Request (PR)

1. Once the edits have been committed, you will be prompted to create a pull request on your fork's GitHub Page.

    ![Image - Compare pull request prompt on GitHub](/docs/images/github/compare-pull-request-prompt.png)

2. By default, all pull requests should be against the freeCodeCamp main repo, `master` branch.

    Make sure that your Base Fork is set to freeCodeCamp/freeCodeCamp when raising a Pull Request.**

    ![Image - Comparing forks when making a pull request](/docs/images/github/comparing-forks-for-pull-request.png)

3. Submit the pull request from your branch to freeCodeCamp's `master` branch.

4. In the body of your PR include a more detailed summary of the changes you made and why.

    - You will be presented with a pull request template. This is a checklist that you should have followed before opening the pull request.

    - Fill in the details as they seem fit you. This information will be reviewed and decide whether or not, your pull request is going to be accepted.

    - If the PR is meant to fix an existing bug/issue then, at the end of
      your PR's description, append the keyword `closes` and #xxxx (where xxxx
      is the issue number). Example: `closes #1337`. This tells GitHub to
      automatically close the existing issue, if the PR is accepted and merged.

5. Indicate if you have tested on a local copy of the site or not.

    This is very important when you are making changes that are not copy editing markdown files. For example, changes to CSS or JavaScript code, etc.

## Get your PR accepted



## Getting Help

If you are stuck, and need help, let us know by asking in the ['Contributors' category on our forum](https://www.freecodecamp.org/forum/c/contributors) or the [Contributors chat room](https://gitter.im/FreeCodeCamp/Contributors) on Gitter.

There might be an error in the console of your browser or in Bash / Terminal / Command Line that will help identify the problem.

### Troubleshooting

If the app launches but you are encountering errors with the UI itself, for example if fonts are not being loaded or if the code editor is not displaying properly, you may try the following troubleshooting steps at least once:

```shell
# Remove all installed node modules
rm -rf node_modules ./**/node_modules

# Reinstall npm packages
npm install

# Bootstrap the project
npm run bootstrap

# Seed the database
npm run seed

# Re-start the application
npm run develop
```
