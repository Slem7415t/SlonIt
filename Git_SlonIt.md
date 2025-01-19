# <img src="images/logo.jpg" alt="logo" width="80"/> Git - система контроля версий(хранилище истории проекта).

[<span style="color:yellow">add</span> |](#add)
[<span style="color:yellow">commit</span> |](#commit)
[<span style="color:yellow">удаление</span> |](#удаление)
[<span style="color:yellow">переименование</span> |](#переименование)
[<span style="color:yellow">алиас</span> |](#алиас)
[<span style="color:yellow">gitignore</span>](#gitignore)

---

<span style="color:blue">*\$ git init*</span> - создаём репозиторий (папку с git), создавать ее нужно в корне проекта.

**команды:**    
<span style="color:blue">*\$ git config user.name "имя пользователя"*</span>    
<span style="color:blue">*\$ git config user.email почта*</span>    
\- указывают автора и почту для созданного репозитория, если указать флаг <span style="color:blue">*--global*</span>, то в проектах почта и имя будут устанавливаться автоматически при создании.   
<span style="color:blue">*\$ git config --global user.name "имя пользователя"*</span>   
<span style="color:blue">*\$ git config --global user.email почта*</span>

**Директории бывают 3х видов:**  
\- системные (*--system*)    
\- глобальные (*--global*)   
\- локальные (*--local*)     
git сначала ищет в локальной директории, затем если не нашел в глобальной и если и там нет, то уже в системной.

**команды:**    
<span style="color:blue">*\$ git config --unset user.name*</span>    
<span style="color:blue">*\$ git config --unset user.email*</span>  
\- удалят локальные автора и почту.     
Можно выполнить операцию одной командой вместо двух, которая удалит всю директорию <span style="color:blue">*user*</span>.     
<span style="color:blue">*\$ git config --remove-section user*</span>   
Также можно открыть файл <span style="color:blue">*config*</span> в текстовом редакторе и отредактировать на его прямую.
Команда <span style="color:blue">*\$ git config --global core.editor путь к файлу флаги(если нужны)*</span>  - позволяет установить или поменять текстовый редактор для git.

**<a id="алиас">АЛИАСЫ</a>** - позволяют делать заготовки команд, чтобы не писать их каждый раз.  
<span style="color:blue">*\$ git config --global alias.c config*</span> - создаст алиас **с** вместо **config**.     
<span style="color:blue">*\$ git config --global alias.sayhi '!echo "hello"; echo "from git"'*</span> - алиас **sayhi** будет вызывать сразу две команды.

<span style="color:blue">*\$ git config ~h*</span> - вызывает список команд.     
<span style="color:blue">*\$ git help имя команды*</span> - вызывает опции команды.      
В поиске листалки:  
- <span style="color:blue">*/слово*</span> -поиск нужного слова
- <span style="color:blue">*n*</span> - поиск в верх
- <span style="color:blue">*shift+n*</span> - поиск в низ
- <span style="color:blue">*q*</span> - выход

<span style="color:blue">*\$ git status*</span> - выводит информацию о файлах проекта.

<a id="add"><span style="color:blue">*\$ git add имя файла*</span></a> - добавляет файл в отслеживаемые файлы(директория *index*).     
<span style="color:blue">*\$ git add .*</span> - добавляет все.     
<span style="color:blue">*\$ git add -p название файла*</span> - позволяет выборочно добавлять разные куски кода из файла.  
<a id="commit"><span style="color:blue">*\$ git commit*</span></a> - добавляет файл в историю проекта(директория *Repository*, где храниться вся история проекта).         
Проекту заранее должны быть присвоены *автор* и *почта* или commit не сработает.    
Далее нас перебросит в редактор, где нужно указать <span style="color:blue">*название commit*</span>(можно сделать комментарий, оставив пустую строку после названия и после звездочки в каждой строке, написать комментарий к нему).         
<span style="color:blue">*\$ git commit -m 'имя commit'*</span> - позволяет без редактора добавить commit.  
<span style="color:blue">*\$ git commit -am 'имя commit'*</span> - сразу запишет commit в репозиторий без *add*, но он игнорирует не отслеживаемые файлы.  
<span style="color:blue">*\$ git commit -m 'имя commit' путь*</span> - сразу закомитит файлы без *add*, но только по указанному пути. Но тоже только проиндексированные(отслеживаемые) файлы.

Файл может иметь разные **права** и быть **исполнимым** или **нет**. Число перед именем закомиченного файла 100644 означает(100 - что тип файл, 644 - что он не исполнимый, у исполнимого 755).     
На windows команды:     
<span style="color:blue">*chmod +x имя файла*</span> - делает его исполнимым.    
<span style="color:blue">*chmod -x имя файла*</span> - делает его не исполнимым.

Команда <span style="color:blue">*\$ git show --prett=fuller индификатор(или его начало не менее 4х символов)*</span> - выводит информацию о commit(можно без флага, будет меньше информации).  
<span style="color:blue">*\$ git commit --author='имя автора <почта>' --date='дата'*</span> - меняют автора(кто создал commit) и время создания commit, но не создателя(кто добавил commit в репозиторий). С помощью другой команды можно поменять и его.

<span style="color:blue">*\$ git reset HEAD название папки или файла*</span> - отменяет изменения для указанного каталога.

Файл <a id="gitignore"><span style="color:blue">*.gitignore*</span></a> - создаем в корне проекта и туда добавляем (каждое с новой строки) названия папок и файлов, которые нужно игнорировать.   
<span style="color:blue">*\$ git add -f имя файла или папки*</span> - добавляет принудительно игнорируемый файл.    
Если написать <span style="color:blue">*\*.расширение файла*</span> - git будет игнорировать все файлы с данным расширением.        
<span style="color:blue">*\$ git config --global core.excludasFile ~/.gitignore*</span> - создаст глобальный игнор файл.

**ХОРОШИЙ COMMIT** - атомарный и логически завершенный(не большой на какую-нибудь одну функциональность).

**Виды оформления заголовков:**
1. Заголовок с должен быть с большой буквы, в конце не ставится точка.
2. компонент: над чем работали описание
3. характер работы(компонент над которым работали): детали

После удаления файла команда <a id="удаление"><span style="color:blue">*\$ git add имя файла*</span></a> - удалит его из директории *index*, затем командой
 <span style="color:blue">*\$ git commit -m Cleanup*</span> - фиксируем изменения в директории *Reposiory*.     
<span style="color:blue">*\$ git rm путь*</span> - для удалении файла по пути.      
<span style="color:blue">*\$ git -r имя папки*</span> - для удаления директории, *add* в том случае не нужно.     
<span style="color:blue">*\$ git -r --cached имя папки*</span> - удалит только из *index*.    
<span style="color:blue">*--cached*</span> - используется и в других командах, где требуются операции только с *index*.     
<span style="color:blue">*$ git rm -f имя файла*</span> - удалит не закомиченный файл, без предупреждения.

При <a id="переименование">переименовании</a> файла git воспринимает операцию как: удаление одного файла и создание нового файла. Только после *add*, он понимает что произошло переименование.            
Затем мы все ровно делаем *commit*, чтобы зафиксировать изменение в репозиторий.        
<span style="color:blue">*\$ git mv старое имя файла новое имя файла*</span> - переименовывает в одну команду (*add* + *commit*).

---
Документация к [<span style="color:blue">Markdown</span>](https://gist.github.com/Jekins/2bf2d0638163f1294637)