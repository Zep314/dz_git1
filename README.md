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

#### 2.
Создадим на GitHub удаленный репозитарий. Укажем в нем создание файла README.md  [https://github.com/Zep314/dz_git1.git](https://github.com/Zep314/dz_git1.git)

#### 3.
Подключаем к нему наш проект. 

    git remote add origin git@github.com:Zep314/dz_git1.git

Пробуем отправить изменения локальной версии на удаленный GiHub

    git push -u origin main

Получаем ошибку:
    
     ! [rejected]        main -> main (fetch first)
    error: failed to push some refs to 'github.com:Zep314/dz_git1.git'
    hint: Updates were rejected because the remote contains work that you do
    hint: not have locally. This is usually caused by another repository pushing
    hint: to the same ref. You may want to first integrate the remote changes
    hint: (e.g., 'git pull ...') before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.

Скачаем удаленный репозитарий

    git fetch

После - посмотрим разницу, в каких файлах есть различия:

    git diff <<HASH>>

