# Краткий помощник по git

Здесь я собрал необходимые команды для работы с git.
Это шпаргалка для тех, кто уже владеет git и имеет представления о нём.

###Команды предварительной настройки
-создать файл
```bash
touch <file>   
```
-создать папку
```bash
mkdir <file>   
```
изменить хардлинк
```bash
mv <file_before> <file_after>
```

### Команды git

Первоначальная настройка, global применяется ко всем файлам git в системе
```bash
git config --global user.name  "NAME"
git config --global user.email "mail@example.ru" 
```

Посмотреть текущий конфиг
```bash
git config --list
```
инициализировать гит в папке
```bash
git init
```
добавить все файлы/файл в гит
```bash
git add .
git add <file>
```

удалить файлы/файл в гит
```bash
git rm .
git rm <file>
```
добавить коммит
```bash
git commit -m "your commit"
```
посмотреть состояние гит
```bash
git status
```
посмотреть историю коммитов
```bash
git log
```
добавить файлы в удаленный репозиторий
```bash
git push
```

### Клонирование существующего репозитория
```bash
git clone <URL>
```
