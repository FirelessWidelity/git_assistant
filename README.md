# Краткий помощник по git

Здесь я собрал необходимые команды для работы с git.
Это шпаргалка для тех, кто уже владеет git и имеет представления о нём.

### Команды предварительной настройки
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
git config --global core.editor vim
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

#### Привязать удаленный репозиторий к локальному 
```bash
git remote add origin git@github.com:NAME_OF_THE_ACCOUNT/project.git
```

добавить файлы в удаленный репозиторий в первый раз/в последующие разы
```bash
git push -u origin main
git push
```
#### Чтобы работать в унисон с проектом, нужно периодически производить merge master-branch всех submodules в рабочую ветку
```bash
git checkout <branch-name>
git merge origin/master
```
#### Следующие команды нужно проверить на корректность
#### Перенести последний commit рабочей ветки на HEAD другой ветки
```bash
git cherry-pick commit-hash-1 HEAD-hash
```
### Перенести все коммиты данной ветки на HEAD другой ветки
```bash
git rebase commit-hash-1 commit-hash-2
```


### Клонирование существующего репозитория
```bash
git clone <URL>
```
## SSH
### Сгенерировать новый ssh-key
```bash
ssh-keygen -t ed25519 -C "your@email.com"
```
### Скопировать сгенерированный pub-key в буфер:
```bash
cat ~/.ssh/id_ed25519.pub | xclip -selection clipboard
```
### Протестировать ssh-соединение с github:
```bash
ssh -T git@github.com
```

# CTags

установка ctags производится классическим образом:
```bash
sudo apt install exuberant-ctags
```
либо
```bash
sudo apt install ctags
```

## Основные команды для создания/использования тэгов
Желательно создавать тэги в вышестоящей директории, либо в parent-folder проекта, чтобы рекурсивно собрать все тэги.

Создать рекурсивно тэги линукс-хэдеров в данной папке (флаг --c - язык, +p -- включить прототипы функций):
```bash
ctags --c-kinds=+p -R /usr/include/
```
### Настройки для vim
Искать тэги в данной директории, вплоть до $HOME
```bash
echo -e "set tags=./tags,tags;$HOME" >> ~/.vimrc
source ~/.vimrc
```
## Навигация по тэгам
Открыть файл, содержащий данный тэг:
```bash
vim -t <tagname>
```
### Поиск тэга в Vim
```vim
:ts <tagname>
```
Установить курсор на слово и нажать комбинацию клавиш 
#### Ctrl+]

Чтобы вернуться к предыдущему слову, комбинация
#### Ctrl+o

Также можно ходить по тэгам с помощью комбинаций tag-next tab-prev:
```vim
:tn
:tp
```
