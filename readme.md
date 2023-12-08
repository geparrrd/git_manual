# Гайд по git и github

## Знакомство с git

### Что такое git и для чего он нужен?

**Git** - это система контроля версий программ, которая позволяет хранить, записывать, удалять историю изменений вашей программы.
Представьте, что вы написали программу по заказу, потом заказчик захотел что-нибудь новое. Вы внесли изменения и сохранили.
Но затем заказчик понял, что ошибся, и захотел, чтобы вы отменили изменения. Но предыдущая версия не сохранилась. И теперь
Вам придётся вспоминать, что вы меняли и переписывать программу. А с **git** вы смогли бы просто откатиться к предыдущей версии.

**Git** - это консольная программа. Другими словами, вы взаимодействуете с ней с помощью инструкций (команд), в отличии от **GUI** -
программ (с графическим интерфейсом), с которыми вы взаимодействуете с помощью мыши, кнопок и окон.  
Кроме того, **git** позволяет работать над проектом в команде, используя связь с удалённым репозиторием на какой-либо платформе (например, **GitHub**).

### Установка git

Скачайте и установите **git** с настройками по умолчанию с [официального сайта](https://git-scm.com/download/win) .
Запустите командную строку `bash.exe` (обычно находится в папке `C:\Program Files\Git\bin`). Теперь вы можете вводить различные команды для управления **git**.
Символ `$` в начале строки указывает на то, что вы можете вводить команду.

### Основные команды

Отметим, что мы установили командную строку `bash` вместе с `git`. Командная строка позволяет управлять файлами и папками (создание, перемещение, копирование, удаление).
Точно так же, как вы перемещаетесь по папкам с помощью нажатия клавишей мыши, можно перемещаться и в консоли. 
Для перехода к какой-либо папке введите `cd <имя папки>` и нажмите `Enter`. Папка должна быть в текущей директории. Но также можно указать абсолютный путь или путь относительно
текущей папки (в которой вы находитесь).

Чтобы узнать текущую рабочую папку введите `pwd` и нажмите `Enter` (в дальнейшем будем указывать только команду. Для её выполнения нужно нажимать `Enter`).
В последней версии **git** рабочая папка всегда отображается, так что команда `pwd` не понадобится.  
Домашняя папка (`C:/Users/user`) обозначается символов тильда `~`. Для перехода к ней: `cd ~`.  
Создайте в любом месте папку `My_projects`. Для этого перейдите в любую директорию и введите `mkdir My_projects`.  
Перейдите в неё и создайте файл `test.txt` с помощью команды `touch test.txt`. Можно создать сразу несколько файлов. Просто перечислите названия файлов
через пробел.
Создайте ещё одну папку `first-project` в этой папке и перейдите в неё.
Для перехода в родительскую папку (ту, что выше): `cd ..`. Двумя точками обозначается родительская папка. Если вы находились в папке `first-project`,
то после этой команды вы окажетесь в папке `My_projects`.  

В консоли также можно перемещать и копировать файлы. Скопируйте файл `test.txt` в папку `first-project` с помощью команды `cp test.txt first-project`.
Для перемещения файла используйте команду `mv`.
Для удаления файла используется команда `rm file.txt`, а для папки `rmdir`. Если папка не пустая, то **git** предупредит об этом, и команда не выполнится.
Если всё же необходимо удалить папку, содержащую что-либо, используйте команду `rm -r папка`. Однако помните, что удаление не перемещает объекты в корзину,
они удаляются безвозвратно.  
Чтобы посмотреть какие файлы и папки находятся в директории введите команду `ls`. Если нужно увидеть также скрытые файлы и папки, то команда `ls -a`.
При этом отобразятся папки `..` и `.` и файлы, названия которых начинаются с `.`. Символ `.` обозначает текущую папку и используется редко.  
Чтобы посмотреть содержимое файла используйте команду: `cat файл`. При этом, если файл не находится в текущей директории, нужно указать полный путь к нему,
например `cat c:\VASILIY\GIT\git_manual\readme.md`.

Если вы хотите ввести команду, которая ранее уже была введена, можно нажать стрелку Вверх. В консоли отобразится последняя команда. Если
ещё раз нажать вверх - предпоследняя, и тд. Если нажать вниз, то будем двигаться в другую сторону.  
Если название папки или файла слишком длинное, но вы помните начало, то начните вводить то, что помните, и нажмите `Tab`. Произойдёт автозаполнение.  
Также можно вводить несколько команд подряд, разделяя их символами `&&`. Например, создайте папку `second-projects` в папке `My_projects` и сразу
перейдите в неё, введя `mkdir second-projects && cd second-projects`.

Ну вот и всё! Теперь вы знаете как управлять файлами и папками. Перейдём к настройке `git`.

### Настройка git

Сейчас вы работали в одиночку, но в работе с командой, нужно знать, кто внёс изменения. Поэтому нужно указать своё имя и адрес электронной почты.  
Для установки своего имени введите команду `git config --global user.name "User Namovich"`.  
Для адреса: `git config --global user.email username@yandex.ru`. При этом не важно, в какой директории вы находитесь. Все глоабльные настройки 
хранятся в файле `.gitconfig` в домашней папке. Чтобы посмотреть содержимое, введите `cat ~/.gitconfig`. 

### Работа с репозиторием

Репозиторием можно назвать любую папку, содержащую файлы программы. Для того, чтобы **git** начал отслеживать изменения в файлах программы, 
необходимо её инициализировать. Пусть папка `first-project` станет вашим первым проектом. Перейдите в неё и введите команду `git init`. 
Теперь файлы папки будут отслеживаться. Создайте файл `todo.txt`, откройте его с помощью любого текстового редактора, запишите в него какое-нибудь
дело и сохраните. Введите команду `git status`, чтобы отобразить статус проекта. Вы увидите, что есть неотслеживаемые файлы `Untracked`.  
Введите команду `git add todo.txt`, чтобы начать отслеживать изменения файла `todo.txt` или `git add --all`, чтобы отслеживать изменения всех файлов. 
Теперь файл отслеживается, но изменения в нём ещё не сохранились. Чтобы записать изменения (сделать коммит), введите `git commit -m "Комментарий к записи"`.  
В консоли отобразится информация об изменениях в файле. Создайте ещё один файл, запишите в нём текст и сохраните. Затем снова сделайте коммит.  
Теперь введите команду `git log`. Вы увидите историю всех изменений - список ваших коммитов.

Ещё один этап пройден! Теперь вы знаете о **git** ещё больше. Но для командной работы этого недостаточно. Нужно поделиться своими изменениями. Для этого используются 
различные платформы. Мы будем использовать `GitHub`.

## Знакомство с GitHub

**GitHub** - это платформа для размещения удалённых репозиториев, а также своего рода социальная сеть для разработчиков. Она помогает миллионам пользователей
делиться своими идеями, присоединиться к чужому открытому проекту, а также даёт возможность работать над проектом в команде.

На **GitHub** можно создать репозитории различных типов:
+ приватный - доступ только у вас
+ командный - для вашей команды
+ публичный - виден всем пользователям

### Настройка аккаунта GitHub

Зарегистрируйтесь на [**GitHub**](https://github.com). Зайдите в профиль и нажмите на вкладку **Repositories**. Нажмите на зелёную кнопку **New**. 
Введите имя своего первого проекта `first-project`. Оно необязательно должно совпадать с названием локального проекта (на вашем компьютере). Не забудьте 
поставить галочку **Private** для создания приватного проекта. Теперь можно нажать кнопку **Create Repository**.  
Поздравляем вы создали свой первый репозиторий на **GitHub**! Теперь нужно связать его с локальным.

### Настройка безопасности соединения

Прежде чем связывать локальный и удалённый репозитории, нужно заиметь ключи безопасности, чтобы никто, кроме вас, не имел доступа к удалённому репозиторию.
Мы будем использовать сетевой протокол **SSH**, обеспечивающий безопасный обмен данными в сети. Он использует пары ключей: приватный и публичный. 
Первый используется для расшифровки данных, второй для шифрования. Публичный могут видеть все, а приватный должен быть известен только вам, иначе доступ 
к данным может получить другой человек.

Прежде чем сгенерировать ключи, убедитесь, что они ещё не были созданы. Перейдите в домашнюю директорию (`cd ~`) и введите команду `ls -la .ssh/`. 
Если ничего не отобразилось, значит папка пуста и всё хорошо. Если это не так и вы не создавали ключи, то удалите их все.  
Для генерации ключей введите команду `ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"`, где `ed25519` - алгоритм
шифрования. Если возникнет ошибка, попробуйте другой алгоритм, например, `rsa -b 4096`. Затем укажите место хранения ключей. По умолчанию будет предложена папка
`.ssh`. Для принятия нажмите `Enter`. Затем появится сообщение о создании кодовой фразы для ключей. Вы можете не придумывать её и нажать `Enter`.

Готово! Проверьте наличие ключей с помощью команды `ls -a ~/.ssh`. На экране отобразятся два файла, один из которых заканчивается на `.pub`. Это публичный ключ.
Скопируйте его содержимое в буфер обмена командой `clip < ~/.ssh/id_ed25519.pub`. 

Перейдите в настройки аккаунта **GitHub** (в правом верхнем углу). Затем слева в меню нажмите на `SSH and GPG keys`. Нажмите на `New SSH key`.  
В поле `Title` введите описание ключа, а в поле `Key` вставьте ключ из буфера обмена. Нажмите `Add SSH key`. 

Проверьте правильность ключа с помощью команды `ssh -T git@github.com`. Если в первый раз соединяетесь с **GitHub**, то выведется сообщение 
`The authenticity of host 'github.com (140.82.121.4)' can't be established. ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU. This key is not known by any other names. Are you sure you want to continue connecting (yes/no/[fingerprint])? `.
Это говорит о том, что **Git** не гарантирует, что **GitHub** является тем, за кого он себя выдаёт. Чтобы убедиться, что это сервер **GitHub**, перейдите
по [ссылке](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints) и проверьте соответствие ключа
в сообщении с одним из ключей на странице. Если всё хорошо, то введите `yes` и нажмите `Enter`.

Поздравляем! Теперь ваш ключ привязан к **GitHub**.

### Синхронизация репозиториев

Перейдите на страницу удалённого репозитория, выберите тип SSH и скопируйте URL.
Перейдите в папку проекта и введите команду `git remote add origin <URL>`. Чтобы вставить текст из буфера в командную строку нажмите `Shift+Insert`.
Нажмите `Enter`. 

Убедитесь, что репозитории связаны: `git remote -v`. Должны отобразиться две строчки:
```bash
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push)
```

Мы связали репозитории. Теперь их нужно синхронизировать. Отправим коммиты в удалённый репозиторий. Сделать это можно с помощью команды 
`git push -u origin master`. Флаг `-u` нужен только для первого связывания. `origin` - это имя удалённого главного репозитория. Обычно он один.
`master` - имя главной ветки. Сейчас у нас всего одна (главная) ветка. Она создаётся автоматически. Также ветки могут разветвляться. Ветки можно представить
как параллельные временные шкалы, в которых происходили изменения. Кроме названия `master` также может использоваться `main`. 

В дальнейшем для связывания веток можно просто писать `git push`.

Зайдите в удалённый репозиторий. Должны появиться файлы проекта. Также возле каждого файла указываются комментарии к коммитам. Чуть выше и правее можно найти
кнопку `commits`. Здесь вы увидите все ваши коммиты. Нажмите на один из них. Вы увидите конкретные изменения, сделанные в файле.

Поздравляем! Теперь вы умеете делать коммиты и отправлять на удалённый репозиторий и ещё много всего полезного!

## Логи, хэши, HEAD, статусы файлов

### Хеш, лог и HEAD

Поговорим об информации, которая отображается после команды `git log`.  
После выполнения команды `git log` вы увидите следующую информацию:
+ Имя автора коммита и его адрес почты
+ Дата и время коммита
+ Описание коммита
+ Хэш коммита (код из 40 символов после слова `commit`)

**Хэш** (или **Хеш**) это уникальный идентификатор. Вся информация коммита, включая содержимое закоммиченного файла, дату и автора коммита, преобразуется в хеш.
Git заносит таблицу `хеш -> информация о коммите` в служебную папку `.git`. По хеш можно определить коммит. Хеш нужен, чтобы зашифровать данные о коммите.
Для этого git использует алгоритм **SHA-1**.

Также возле последнего коммита находится надпись `HEAD -> master` (или main). Это значит, что хеш последнего коммита хранится в файле `HEAD` в папке `.git`.
Точнее там хранится ссылка на него `refs/heads/master`. Если открыть файл `master`, вы увидите хеш последнего коммита.  
Хеш часто нужен в качестве параметра некоторым командам. А если нужно вставить хеш последнего коммита, то можно просто передать `HEAD`. Git поймёт.

Для вывода сокращённой истории коммитов используется команда `git log --oneline`. Отобразятся только первые несколько символов хеша и описание коммита.
Количество символов git подбирает таким образом, чтобы сокращённые хеши были уникальными. По такому хешу также можно идентифицировать коммит.

### Статусы файлов

Типичный жизненный цикл файлов в репозитории имеет следующие статусы:

+ `Untracked`
+ `tracked`
+ `staged`
+ `modified`

Эти статусы вы могли видеть после команды `git status`. Разберём их подробнее.

Статус `Untracked` появляется, когда вы добавили новый файл в проект, но ещё не применили команду `git add`. Это значит, что git знает о файле,
но ещё не отслеживает изменения в нём. Если применить к такому файлу команду `git add`, статус файла изменится на `staged` (подготовленный). То есть,
файл готов для коммита. Если его закоммитить и выполнить команду `git status`, то мы не увидим информацию о статусе данного файла. Это значит,
что он просто отслеживается, находится в состоянии `tracked` - противоположно `Untracked`. Если файл не имеет статус `Untracked`, это значит, что он имеет
статус `tracked` вне зависимости от того, был ли он изменён, подготовлен для коммита или уже закоммичен.  
Изменим закоммиченный файл. Тогда он перейдёт в статус `modified`. Это значит, что файл был изменён.

Но допустим, мы изменили файл, подготовили файл с помощью команды `git add`, но не закоммитили его, а изменили. Тогда мы увидим два статуса `modified`
одного и того же файла, но разных его версий: до команды `git add` и после изменения файла. Если снова применить команду `git add`, то для записи
будет подготовлена последняя версия файла.

Оба статуса `modified` и `staged` относятся к статусу `tracked`. Поскольку этот статус имеет более широкий смысл, чем `modified` и `staged`, обычно
его название упоминается, подразумевая, что файлы и так отслеживаются.

Схематически весь типичный жизненный цикл файла можно представить так:

```mermaid
flowchart TD;
	D("`**Untracked** (неотслеживаемый)`") -- "git add" --> A("`**staged** (в списке на коммит) + **tracked**`");
	A -- "Изменения" --> B("`**modified** (изменённый)`");
	A -- "git commit" --> C("`**tracked** (отслеживаемый)`");
	C -- "Изменения" --> B;
	B -- "git add" --> A;
```

### Оформлений сообщений к коммитам

Часто используется неопределённая форма глагола, например, "Добавить описание". Поэтому тоже так пиши :)

## Изменения коммитов, откаты и прочее

### Изменение последнего коммита

+ `--amend` рассчитан на работу с последним коммитом (`HEAD`).
+ Дополнить коммит новыми файлами можно с помощью `git commit --amend --no-edit`. Благодаря опции `--no-edit` сообщение
к коммиту останется таким, каким и было.
+ Изменить сообщение к коммиту позволяет команда `git commit --amend -m "Обновлённое сообщение коммита"`.

### Откатиться назад, если "всё сломалось"

+ Команда `git restore --staged <file>` переведёт файл из `staged` обратно в `modified` или `untracked`.
+ Команда `git reset --hard <commit hash>` «откатит» историю до коммита с хешем `<hash>`. Более поздние коммиты потеряются!
+ Команда `git restore <file>` «откатит» изменения в файле до последней сохранённой (в коммите или в staging) версии.

### Просмотр изменений в файлах

+ Команда `git diff` сравнит последнюю закоммиченную версию файла с той, что находится в состоянии `modified`.
+ Команда `git diff --staged` покажет изменения в `staged`-файлах относительно последних закоммиченных версий. 
+ Команда `git diff <коммит1> <коммит2>` сравнит изменения в двух коммитах.

### Игнорирование файлов

+ Если нужно, чтобы Git игнорировал какие-то файлы, стоит составить файл `.gitignore`.
+ Посмотреть, что игнорируется, можно с помощью команды `git status --ignored`.
+ Сам файл `.gitignore` — это обычный файл в репозитории. Его тоже стоит закоммитить.
+ Шаблонов много, но их легко найти в интернете вместе с примерами использования.

## Шпаргалка

### Инициализация репозитория

`git init` (от англ. initialize, «инициализировать») — инициализируй репозиторий.

### Синхронизация локального и удалённого репозиториев

`git remote add origin https://github.com/YandexPracticum/first-project.git` (от англ. remote, «удалённый» + add, «добавить») — привяжи локальный
репозиторий к удалённому с URL `https://github.com/YandexPracticum/first-project.git`;
`git remote -v` (от англ. verbose, «подробный») — проверь, что репозитории действительно связались;
`git push -u origin main` (от англ. push, «толкать») — в первый раз загрузи все коммиты из локального репозитория в удалённый с названием `origin`.
`git push` (от англ. push, «толкать») — загрузи коммиты в удалённый репозиторий после того, как он был привязан с помощью флага `-u`.

### Подготовка файла к коммиту

`git add todo.txt` (от англ. add, «добавить») — подготовь файл `todo.txt` к коммиту;
`git add --all` (от англ. add, «добавить» + all, «всё») — подготовь к коммиту сразу все файлы, в которых были изменения, и все новые файлы;
`git add .` — подготовь к коммиту текущую папку и все файлы в ней.

### Создание и публикация коммита

`git commit -m "Комментарий к коммиту."` (от англ. commit, «совершать», фиксировать» + message, «сообщение») — сделай коммит и оставь
комментарий, чтобы было проще понять, какие изменения сделаны;
`git push` (от англ. push, «толкать») — добавь изменения в удалённый репозиторий.

### Просмотр информации о коммитах

`git log` (от англ. log, «журнал [записей]») — выведи подробную историю коммитов;
`git log --oneline` (от англ. log, «журнал [записей]» + oneline, «одной строкой») — покажи краткую информацию о коммитах: сокращённый хеш и сообщение.

### Просмотр состояния файлов

`git status` (от англ. status, «статус», «состояние») — покажи текущее состояние репозитория.

### Добавление изменений в последний коммит

`git commit --amend --no-edit` (от англ. amend, «исправить») — добавь изменения к последнему коммиту и оставь сообщение прежним;
`git commit --amend -m "Новое сообщение"` — измени сообщение к последнему коммиту на `Новое сообщение`.

**Важно**
Выйти из редактора Vim: нажать `Esc`, ввести `:qa!`, нажать `Enter`.

### «Откат» файлов и коммитов

`git restore --staged hello.txt` (от англ. restore, «восстановить») — переведи файл `hello.txt` из состояния `staged` обратно в `untracked` или `modified`;
`git restore hello.txt` — верни файл `hello.txt` к последней версии, которая была сохранена через `git commit` или `git add`;
`git reset --hard b576d89` (от англ. reset, «сброс», «обнуление» + hard, «суровый») — удали все незакоммиченные изменения из staging и
«рабочей зоны» вплоть до указанного коммита.

### Просмотр изменений

`git diff` (от англ. difference, «отличие», «разница») — покажи изменения в «рабочей зоне», то есть в `modified`-файлах;
`git diff a9928ab 11bada1` — выведи разницу между двумя коммитами;
`git diff --staged` — покажи изменения, которые добавлены в `staged`-файлах.

## Работа с Git в команде

### Клонирование репозитория

+ Команда `git clone` копирует проект на локальный компьютер.
+ `git clone` автоматически связывает локальный репозиторий с удалённым.
+ `git clone git@github.com:YandexPraktikum/first-project.git` (от англ. clone, «клон», «копия») — склонируй репозиторий 
с URL `first-project.git` из аккаунта `YandexPraktikum` на мой локальный компьютер.

### Форк

+ «Форк» позволяет получить точную копию GitHub-репозитория в ваш аккаунт.
+ Копия, которая получена с помощью «форка», полностью независима от оригинального проекта — изменения не будут синхронизированы.

### Ветки

+ Ветка — это последовательность независимых изменений.
+ Благодаря веткам несколько человек могут работать над одним репозиторием и не мешать друг другу. А ещё ветки помогают декомпозировать
большую и страшную задачу на маленькие и понятные.
+ Основная версия проекта хранится в главной ветке `main` (или `master`).
+ С помощью команды `git branch` можно посмотреть, какие в проекте есть ветки и в какой из них вы сейчас находитесь.
+ `git branch -a` — покажи все известные ветки, как локальные (в локальном репозитории), так и удалённые (в `origin`, или на GitHub).
+ С помощью команды `git branch <Название ветки>` можно создать новую ветку от текущей.

#### Переключение между ветками

+ Команда `git checkout <название_ветки>` позволяет переключаться на другую ветку.
+ Разные ветки в одном проекте существуют независимо. Изменения в одной не влияют на изменения в другой.
+ В Git можно создать ветку и сразу же перейти в неё командой `git checkout -b <название_ветки>`.
+ Ветка указывает на коммит, который сделан в ней последним. При этом две ветки могут ссылаться на один и тот же коммит — например,
если вы только что создали ветку, но ещё не успели внести в неё коммит.

#### Сравнение коммитов в разных ветках

+ `git diff` может сравнивать ветки по их названиям. Например, команда `git diff main feature/my-feature` выведет разницу между основной 
веткой и веткой `feature/my-feature`.
+ Git поддерживает суффикс навигации `~`. С его помощью можно сослаться на предыдущие коммиты. Например, если вы находитесь в ветке 
`main` и хотите вывести разницу между тем коммитом, который был три коммита назад, и текущим, нужно выполнить `git diff main~3 main`.

#### Слияние и удаление веток

+ Выполнить слияние веток позволяет команда `git merge <название_ветки>`. В качестве параметра указывают название ветки, которую нужно влить в текущую.
+ Удалять ненужные ветки после слияния — хорошая практика. Так в вашем репозитории всегда будет порядок. За удаление веток отвечает команда 
`git branch -D <название_ветки>` и её щадящий вариант с флагом `-d`. Последний удалит ветку, только если она была объединена с другой.
+ Удаление ветки в Git не удаляет ветку на GitHub!

### Работа с удалённым репозиторием

`git push -u origin my-branch` (от англ. push, «толкнуть», «протолкнуть») — отправь новую ветку `my-branch` в удалённый репозиторий и свяжи локальную 
ветку с удалённой, чтобы при дополнительных коммитах можно было писать просто `git push` без `-u`;
`git push my-branch` — отправь дополнительные изменения в ветку `my-branch`, которая уже существует в удалённом репозитории.

Свои изменения можно влить в основную ветку удалённого репозитория, но перед этим их должны проверить другие участники команды.
Для этого есть `pull request` (пул-реквест) на GitHub. Другими словами, запросить слияние. Как только запрос отправлен, коллеги могут сделать ревью кода
и либо принять их, и тогда можно сделать `merge`, либо попросить внести правки, тогда запрос закрывается.

### Загрузка изменения из удалённого репозитория

+ Команда `git pull` позволяет подтянуть изменения из удалённого репозитория в локальный.
+ Перед созданием нового пул-реквеста считается хорошей практикой перейти в главную ветку, «подтянуть» в неё изменения, а затем добавить 
эти изменения в вашу ветку с помощью `git merge main`.

## Работа с ветками на практике

### Режим fast-forward

+ Если истории двух веток не «разошлись» и их коммиты выстраиваются в одну цепочку, эти ветки можно объединить в режиме fast-forward.
+ Режим fast-forward можно отключить с помощью флага `--no-ff`.

### Режим Non-fast-forward

+ Если истории двух веток всё же «разошлись», при слиянии веток Git создаст коммит слияния.
+ При объединении веток в состоянии не-fast-forward возможны (но не обязательны) конфликты. Если конфликты всё же возникли, Git 
попытается разрешить их самостоятельно или попросит вас сделать это вручную.

### Модели веток

+ Разные компании и команды используют разные модели работы с Git. Эти модели описывают структуру веток в проекте, а также правила 
создания и слияния коммитов в них.
+ Один из самых простых и популярных подходов — feature branch workflow. Он предполагает, что работа над функциональностью ведётся 
в отдельной feature-ветке. Когда всё готово, эта ветка вливается в основную.
+ Подход feature branch workflow — лишь шаблон, по которому можно действовать. Многие компании и команды меняют его под свои нужды, 
но неизменно одно: хочешь сделать новую функциональность или исправить баг — создай новую ветку!

### Пул-реквест

+ Во многих командах пул-реквест — это основной путь, по которому изменения или исправления попадают в основную ветку проекта.
+ Важный этап пул-реквеста — ревью. В ходе ревью коллега оценит правки и предложит доработки, если они нужны. Когда всё будет 
готово, ревьюер примет («апрувнет») изменения, затем их можно будет интегрировать в main.
+ Если вы уже участник проекта (или collaborator в терминах GitHub), можно клонировать репозиторий напрямую. А если нет, нужно 
предварительно сделать «форк». Также для участников доступна кнопка Merge после ревью, а для неучастников — нет.

### Разрешение конфликта

+ Конфликты — это ситуация, в которой две ветки или более изменяют один и тот же файл в разных местах и пытаются объединиться в одну ветку.
+ При возникновении конфликта Git добавит в файлы маркеры конфликтов. Вы можете разрешить конфликт вручную: достаточно удалить маркеры и 
принять правильные изменения.
+ Для разрешения конфликтов вы также можете использовать vimdiff — он доступен по умолчанию.
+ Когда один и тот же файл меняется в нескольких ветках, при их слиянии может произойти конфликт. Пугаться конфликтов не нужно, это 
нормальная часть работы с системами контроля версий. IDE, вроде VSCode или Intellij IDEA, помогут «склеить» файл из двух конфликтующих версий.

### Основная ветка убежала во время ревью

+ В командной работе регулярно случаются конфликты — и в этом нет ничего страшного.
+ Чтобы разрешить конфликт слияния, который возникает, когда главная ветка «уходит» вперёд, можно сделать следующее. Сначала локально 
получить новые изменения через `git pull`, а затем выполнить `git merge` и разрешить конфликт. Далее создать коммит слияния и отправить 
новые изменения без конфликтов обратно в удалённый репозиторий командой `git push`.

### Алгоритм-шпаргалка для создания PR

1. Склонировать репозиторий.  
  1.1. Если вы не участник проекта, предварительно сделать «форк» исходного репозитория.  
1.2. На странице репозитория или «форка» нажать кнопки: *Code* → *SSH* → *скопировать ссылку*.  
1.3. Выполнить команду `git clone <ссылка на репозиторий>`.  
2. Создать ветку для вашей задачи: `git checkout -b my-task-branch-name`.  
3. Добавить и «закоммитить» изменения, которые вы хотите внести в проект.  
4. «Запушить» ветку: `git push --set-upstream origin HEAD` или `git push -u origin my-task-branch-name`.  
4.1. GitHub (с помощью Git) выведет ссылку на создание PR. По ней нужно перейти.  
4.2. PR можно также создать через интерфейс GitHub.  
5. Сообщить о пул-реквесте ревьюеру.  
5.1. Иногда ревьюеры назначаются автоматически, тогда сообщать не нужно.  
6. Обсуждать с ревьюером предлагаемые изменения и вносить правки, пока эти изменения не будут одобрены (пока не будет получен «апрув»).  
6.1. Если кто-то добавил конфликтующие изменения в `main`, пока ваш PR был на ревью, нужно разрешить конфликт:  
+ Обновить `main`: `git checkout main && git pull`.
+ Влить `main` в свою ветку: `git checkout my-task-branch-name && git merge main`.
+ Разрешить конфликты слияния с помощью IDE или вручную.
+ Создать коммит слияния: `git commit --no-edit` или `git commit -m 'merge main'`.
+ Сделать `git push` своей ветки.
7. Нажать кнопку **Merge** или подождать, пока её нажмёт кто-то ещё.
8. Ещё раз обновить `main`, чтобы «подтянуть» ваши изменения в основную ветку локального репозитория: `git checkout main && git pull`.
9. Вы великолепны! Можете начинать снова со второго пункта.



