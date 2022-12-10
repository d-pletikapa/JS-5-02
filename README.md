# git-config (JS-5-02)
## Действия после установки git

### посмотреть настройки
```shell
git config --list
```

```shell
git config --global user.name “имя”
git config --global user.email “почта”


git config --global core.safecrlf warn
git config --global core.quotepath off
git config --global init.defaultBranch main # Ветка по умолчанию
```

### windows
```shell
git config --global core.autocrlf true
```


### MAC & UNIX
```shell
git config --global core.autocrlf input
```


## Действия при инициализации нового репозитория и при работе с ним


### инициализация git репозитория
```shell
git init
```

### текущее состояние репозитория
```shell
git status
```

### добавить в трек (отслеживаемые) файл или папку
```shell
git add index.html
```

### добавить все файлы из корня в трек
```shell
git add .
```

### выполнить коммит (сделать слепок) текущего состояния проекта
```shell
git commit -m "сообщение"
```

### показывает изменения
```shell
git diff
git diff --color-words // показывает по строкам изменения
```

## отменить коммит "ПЕРЕПИСЫВАЕТ ИСТОРИЮ"

### вернуться к коммиту старому но оставить текущие изменения, если коммит еще не отправлен в репозиторий
```shell
git reset 'HASH commit'
```

### вернуться к коммиту и удалить все изменения, если коммит еще не отправлен в репозиторий
```shell
git reset --hard 'HASH commit'
git reset --hard HEAD~    //~2 ~3 на сколько коммитов откатить
```

### откатить изменения
```shell
### у всех файлов трека
git checkout .  
git clean -fd (удалить все неотслеживаемые файлы)
```
```shell
### в одном файле или каталоге
git checkout name.file //откатить изменения в одном файле или каталоге
git restore index.html //возвратить файл до исходного состояния)

git branch //посмотреть где находимся
git checkout main //вернутся к основной ветке
```

### отправить изменения в удаленный репозиторий
```shell
git push 
```

### клонирование репозитория
```shell
git clone https://github.com/Quper87/git-lesson.git
```

### сохраняет изменения отслеживаемых файлов и выполняет коммит
```shell
git commit -a -m 'сохраняет изменения отслеживаемых файлов и выполняет коммит'
```

## ЗАМЕТКИ

### generate key:
```shell
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

ssh-keygen -t ed25519 -C "mail@.com"

agent:
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

### Adding a new SSH key to your account (github --web):
```shell
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

clip < ~/.ssh/id_ed25519.pub
```

### логи и pull
```shell
git pull --rebase //подтянуть данные не поломав коммиты

git log //логи коммитов
git show 'хэш коммита можно первые 8 символов'
git log --oneline // краткие логи коммитов в одну строку
git blame index.html (посмотреть кто изменял какую строку)
git grep h1  (поиск подстроки)
```

### отменить коммит
```shell
git revert 'хэш коммита'
```

### поправить коммит (например забыли добавить что-то)
```shell
Выполнить stage отслеживание:
git add . или git add music.css
Выполнить
git commit --ammend
```

### отложить в кладовку написанный код
```shell
Выполнить stage отслеживание:
git add . или git add music.css
Выполнить
git stash
### достать написанный код
git pop 
```
### работа с ветками branch
```shell
git chekout -b 'название новой ветки' // создать и перейти в новую ветку.
```
```shell
отправляем ветку в удаленный репозиторий как обычно:
git add .
git push

Чтобы слить ветку с main:
git checkout main //переходим в main
git merge 'имя ветки для слияния в мейн'
git branch -d 'имя ветки для удаления' //удаляем ненужную ветку
git push -d origin имя-ветки // чтобы также удалить в репозиторий удаленном
```
```shell
Конфликты merge 
git diff - посмотреть детально конфликт в консоли
исправить конфликт ручками и затем
git add . 
git commit -a -m ''
```
