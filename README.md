# Контроль версий углублённо (GIT) (семинары)
## Урок 1. Работа с удалёнными репозиториями

### Задание 1

1. Выберите какой-нибудь проект на изучаемом вами языке программирования, с которым вы будете тренироваться работать в Git, и инициализируйте в папке этого проекта локальный репозиторий.
2. Создайте непустой удалённый репозиторий (например, с файлом README.md) с именем, соответствующим имени этого проекта.
3. Подключите свой проект к этому удалённому репозиторию и отправьте в него код этого проекта. Самостоятельно разрешите конфликты и проблемы, если они возникнут при выполнении данного задания.

### Решение:

#### 1.
Возьмем ранний проект на языке Python - написать функцию-генератор чисел Фибоначчи. Тут есть файл *README.md*. Заново инициализируем репозиторий.

    git init

Добавим в репозитарий все файлы проекта, и сделаем коммит

    git add .
    git commit -m "Initial commit"

Назовем текущую ветку *new_feature*

    git branch -m new_feature

#### 2.
Создадим на GitHub удаленный репозитарий. Укажем в нем создание файла README.md  [https://github.com/Zep314/dz_git1.git](https://github.com/Zep314/dz_git1.git)

#### 3.
Подключаем к нему наш проект. 

    git remote add origin git@github.com:Zep314/dz_git1.git

Отправляем изменения локальной версии на удаленный GiHub

    git push -u origin new_feature

Скачиваем с удаленного репозитария недостающую ветку проекта

    git fetch

Смотрим, в каких файлах имеются какие изменения

    git diff


Пробуем переключиться на ветку *main*

    git checkout main
    Switched to a new branch 'main'                                                              branch 'main' set up to track 'origin/main'. 

Пробуем слить обе ветки вместе

    git merge new_feature
    fatal: refusing to merge unrelated histories

Получаем ошибку, которая возникает, когда два не связанных между собой проекта объединяются (то есть они не знают о существовании друг друга и не соответствующие фиксации истории)

Устраняем ошибку с помошью параметра --allow-unrelated-histories

    git merge new_feature --allow-unrelated-historiesAuto-merging README.md
    CONFLICT (add/add): Merge conflict in README.md
    Automatic merge failed; fix conflicts and then commit the result.

Git сообщает нам о конфликте в файле *README.md*. Смотрим на статус всего проекта

    git status                
    On branch main
    Your branch is up to date with 'origin/main'.

    You have unmerged paths.
        (fix conflicts and run "git commit")
        (use "git merge --abort" to abort the merge)

    Changes to be committed:
        new file:   fibonachi.py

    Unmerged paths:
        (use "git add <file>..." to mark resolution)
        both added:      README.md

Убедимся, что мы находимся в правильной ветке

    git branch
    * main
      new_feature

Делаем коммит

    git commit -m "Conflict resolved"

После этого - закачиваем все на GitHub

    git push

