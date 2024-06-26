![[001.png]]
**Git** - это распределённая система контроля и управления версиями, которая позволяет отслеживать изменения в коде и управлять ими. 
Она нужна для того, чтобы несколько разработчиков могли работать над одним проектом, не конфликтуя друг с другом, и чтобы иметь возможность отслеживать изменения и возвращаться к предыдущим версиям кода.

А теперь немного вводных...

**Репозиторием** называют хранилище нашего кода и историю его изменений. 
Git работает локально и все наши репозитории хранятся в определенных папках на жестком диске.


Так же наши репозитории можно хранить и в интернете. Обычно для этого используют три сервиса:

[GitHub](https://github.com/)
[Bitbucket](https://bitbucket.org/)
[GitLab](https://gitlab.com/)

Каждая точка сохранения нашего проекта носит название **коммит** (**commit**). 
Он хранит отрезок информации от предыдущего коммита до себя.
У каждого commit-a есть **hash** (**уникальный id**) и **комментарий**. 
Из таких commit-ов собирается **ветка** (**это история изменений**).
У каждой ветки есть свое название. 
Репозиторий может содержать в себе несколько веток, которые создаются из других веток или вливаются в них.

Спасибо за внимание!
### Настройка конфигурации пользователя

Перед началом работы с git необходимо установить данные пользователя.
Это нужно для того, чтобы git мог сохранять информацию о том, кто и когда вносил изменения.

```bash
git config --global user.name "username"
git config --global user.email "username@mail.com"
```

Существует 3 уровня настройки
```
--system // на уровне системы
--global // на уровне учётной записи конкретного пользователя
--local // на уровне каталога
```

### Инициализация репозитория

В папке проекта необходимо инициализировать Git-репозиторий
```bash
git init
```

Теперь Git отслеживает изменения файлов проекта. Но, так как вы только создали репозиторий в нем нет вашего кода. Для этого необходимо создать commit.

### Первый коммит

```bash
#Добавим все файлы проекта в нам будующий commit
git add .
#Или так
git add --all
#Или так
git add -A

#Если хотим добавить конкретный файл то можно так
git add <имя_файла> 

#Теперь создаем commit. 
git commit // Через редактор nano. Позволяет добавить сообщение в несколько строк.
#Или так
git commit -m "<сообщение>" // Привычная команда с добавлением сообщения в одну стрку.
#Или так
git commit -am "<сообщение>" // Совмещает в себе комманды git add --all и git commit -m "<сообщение>"
```

Отлично. Вы создали свой первый репозиторий и заполнили его первым commit!

---

### Немного базовых команд

```bash
git status // отображает список измененных файлов, готовых к коммиту

git commit -m "My commit message" // создаёт коммит с сообщением "My commit message"
git commit --amend -m "New commit message" // изменяет сообщение последний коммит

git log // показывет историю коммитов

git checkout -b newBranchName // создаёт новую ветку newBranchName и сразу переходит на неё
git checkout master // переходит на ветку master
git branch // посмотреть список всех веток (знак * указывает на ветку, на которой мы находимся)
git switch -c // создает новую ветку и переключает на нее (аналогична команде git checkout -b, но с более четким разделением функций между git switch и git checkout)

git remote add origin https://github.com/user/repo.git // добавляет новый удалённый репозиторий с именем origin и адресом https://github.com/user/repo.git
git remote -v // Посмотреть список удалённых репозиториев
git remote set-url origin https://new-url.com/repo.git // изменяет адрес origin
git remote remove origin // удаляет origin

git reset HEAD// Откат до определённного коммита вместе с перемещением указателя HEAD. Коммиты, находящиеся выше в иерархии удаляются (с возможностью восстановления с помощью git reflog).
// Имеет флаги:
--soft // изменения сохраняются в индексе и в рабочем каталоге 
--mixed // (по умолчанию) // изменения сохраняются в рабочем каталоге, но удаляются из индекса
--hard // Полное удаление! (из индекса и рабочего каталога)

git revert HEAD // Создает новый коммит равный указанному HEAD, сохраняя иторию коммитов

// ! Важное замечание !
// К коммиту можно обращаться через HEAD~n, где n - целое число, отступ от последнего коммита.
```

**Полезные ссылки:**

- Краткий обзор Git - https://www.atlassian.com/git
- Плейлист для чайников с нуля - https://www.youtube.com/watch?v=W4hoc24K93E&list=PLDyvV36pndZFHXjXuwA_NywNrVQO0aQqb
- Тренажер - https://learngitbranching.js.org/?locale=ru_RU
- $ git revert https://www.atlassian.com/git/tutorials/undoing-changes/git-revert
- $ git reset - https://www.git-scm.com/book/ru/v2/%D0%98%D0%BD%D1%81%D1%82%D1%80%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-Git-%D0%A0%D0%B0%D1%81%D0%BA%D1%80%D1%8B%D1%82%D0%B8%D0%B5-%D1%82%D0%B0%D0%B9%D0%BD-reset 
 - $ git reset - https://www.atlassian.com/git/tutorials/undoing-changes/git-reset
