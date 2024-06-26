# Git Started  

**Git** - Система контроля версий, предназначенная для контроля изменений в проекте. Каждая версия или ревизия содержит информацию об изменении и комментарии к изменениям.
Основные функции системы контроля версий:  
- хранит историю изменений в виде отдельных ревизий;
- позволяет манипулировать историей: например, менять порядок ревизий, полностью удалять версии, возвращаться назад в истории;
- помогает анализировать изменения: например, кто и когда вносит изменения, кто чаще всего вносит изменения в определённый файл и так далее.

---

## Basic git commands

- **git init %repo_folder_name** - инициализация (создание) локального репозитория. Команда запускается в локальной папке, где должен храниться репозиторий.  
- **rm -rf .git** - удаление репозитория из папки. В .git храниться информация о проекте и истории изменений, поэтому удалять папку на действующем репозитории не желательно  
- **git status** - показывает текущее состояние репозитория.  
	Команда git status выведет:    
    		- название текущей ветки: On branch master или On branch main;  
    		- сообщение о том, что в репозитории ещё нет коммитов: No commits yet;  
    		- сообщение, которое говорит: «чтобы что-нибудь закоммитить (то есть зафиксировать), нужно сначала это создать» — nothing to commit (create/copy files and use "git add" to track).  
- **git add** - команда добавляет файлы в репозиторий, но не сохраняет содержимое файлов.   
	git add ‒all добавляет все в папке репозитория  
- **git . **- добавляет текущую папку к репозиторию  
- **git commit** - сохраняет в репозиторий файлы и их содержимое. -m позволяет оставить комментарий к коммиту.   

	Сначала команда git add сообщает Git, какие именно файлы нужно сохранить и какую их версию. Затем с помощью команды git commit происходит само сохранение. 
	В прошлом уроке мы сравнили add c добавлением товаров в корзину, а commit — с заказом. Теперь проведём ещё одну аналогию — с фотографией.
	Сначала вы просите друзей встать в ряд — это команда git add. И только после того, как все заняли свои места, поправили волосы и улыбнулись, вы нажимаете кнопку и делаете снимок — это команда git commit. Сам получившийся снимок и будет коммитом. В нашем случае на этой фотографии с обратной стороны ещё есть подпись «Мой первый коммит!».

- **git log** просмотр истории коммитов 
- **git remote add** связать удаленный и локальный репозитории
	(```git remote add origin git@github.com:%ИМЯ_АККАУНТА%/%repo_name%.git```)
- **git remote -v** проверка привязки удаленного репозитория
- **git remote remove %repo_name%** удалить привязку репозитория
- **git branch** -  показать, создать или удалить ветки репозитория

## Git hash

Хешированиe (от англ. hash, «рубить», «крошить», «мешанина») — это способ преобразовать набор данных и получить их «отпечаток» (англ. fingerprint).
Информация о коммите — это набор данных: когда был сделан коммит, содержимое файлов в репозитории на момент коммита и ссылка на предыдущий, или родительский (англ. parent), коммит.
Git хеширует (преобразует) информацию о коммите с помощью алгоритма SHA-1 (от англ. Secure Hash Algorithm — «безопасный алгоритм хеширования») и получает для каждого коммита свой уникальный хеш — результат хеширования.
Обычно хеш — это короткая (40 символов в случае SHA-1) строка, которая состоит из цифр 0—9 и латинских букв A—F (неважно, заглавных или строчных). Она обладает следующими важными свойствами:
- если хеш получить дважды для одного и того же набора входных данных, то результат будет гарантированно одинаковый;
- если хоть что-то в исходных данных поменяется (хотя бы один символ), то хеш тоже изменится (причём сильно).

## Хеш — основной идентификатор коммита

Git хранит таблицу соответствий ```хеш → информация о коммите```. Если вы знаете хеш, вы можете узнать всё остальное: автора и дату коммита и содержимое закоммиченных файлов. Можно сказать, что хеш — основной идентификатор коммита.
Все хеши и таблицу ```хеш → информация о коммите``` Git сохраняет в служебные файлы. Они находятся в скрытой папке ```.git``` в репозитории проекта.

## Git logs

### Элементы описания коммита

После вызова ```git log``` появляется список коммитов.
Разберём элементы, из которых состоит описание:

- строка из цифр и латинских букв после слова commit — это хеш коммита;
- Author — имя автора и его электронная почта;
- Date — дата и время создания коммита;
- в конце находится сообщение коммита.

Получить сокращённый лог можно с помощью команды ```git log``` с флагом ```--oneline``` (англ. «одной строкой»). В терминале появятся только первые несколько символов хеша каждого коммита и их комментарии.

Сокращённый лог полезен, если в репозитории уже много коммитов — например, сотни или тысячи. В этом случае можно быстро найти нужный по описанию.

Сокращённый хеш (то есть первые несколько символов полного) можно использовать точно так же, как и полный. Для этого команда ```git log --oneline``` автоматически подбирает такую длину сокращённых хешей, чтобы они были уникальными в пределах репозитория и Git всегда мог понять, о каком коммите идёт речь 

Файл ```HEAD``` (англ. «голова», «головной») — один из служебных файлов папки ```.git```. Он указывает на коммит, который сделан последним (то есть на самый новый).

Внутри ```HEAD``` — ссылка на служебный файл: ```refs/heads/master``` (или ```refs/heads/main``` в зависимости от названия ветки). Если заглянуть в этот файл, можно увидеть хеш последнего коммита.  Если нужно передать последний коммит, то вместо его хеша можно просто написать слово ```HEAD``` — Git поймёт, что вы имели в виду последний коммит.

## Git file status

Одна из ключевых задач Git — отслеживать изменения файлов в репозитории. Для этого каждый файл помечается каким-либо статусом. Рассмотрим основные.  

- **untracked** (англ. «неотслеживаемый») 
Мы говорили, что новые файлы в Git-репозитории помечаются как ```untracked```, то есть неотслеживаемые. Git «видит», что такой файл существует, но не следит за изменениями в нём. У untracked-файла нет предыдущих версий, зафиксированных в коммитах или через команду ```git add```.

- **staged** (англ. «подготовленный») 
После выполнения команды ```git add``` файл попадает в staging area (от англ. stage — «сцена», «этап [процесса]» и area — «область»), то есть в список файлов, которые войдут в коммит. В этот момент файл находится в состоянии ```staged```.

### Staging area, index and cache

Staging area также называют index (англ. «каталог») или cache (англ. «кеш»), а состояние файла ```staged``` иногда называют ```indexed``` или ```cached```.  
Все три варианта могут встречаться в документации и в качестве флагов команд Git.

- **tracked** (англ. «отслеживаемый») 
Состояние tracked — это противоположность ```untracked```. Оно довольно широкое по смыслу: в него попадают файлы, которые уже были зафиксированы с помощью ```git commit```, а также файлы, которые были добавлены в ```staging area``` командой ```git add```. То есть все файлы, в которых Git так или иначе отслеживает изменения.

- **modified** (англ. «изменённый»)
Состояние ```modified``` означает, что Git сравнил содержимое файла с последней сохранённой версией и нашёл отличия. Например, файл был закоммичен и после этого изменён.  
***Для файлов в состояниях ```staged``` и ```modified``` обычно не указывают, что они также ```tracked```, потому что это состояние подразумевается.***

Команда ```git add``` добавляет в ```staging area``` только текущее содержимое файла. Если вы, например, сделаете ```git add file.txt```, а затем измените file.txt, то новое содержимое файла не будет находиться в ```staging```.
Git сообщит об этом с помощью статуса ```modified```: файл изменён относительно той версии, которая уже в ```staging```. Чтобы добавить в ```staging``` последнюю версию, нужно выполнить ```git add file.txt``` ещё раз.

### Typical life cycle of file in Git

1. Файл только что создали. Git ещё не отслеживает содержимое этого файла. Состояние: ```untracked```.
2. Файл добавили в ```staging area``` с помощью ```git add```. Состояние: ```staged``` (+ ```tracked```). 
	- Возможно, изменили файл ещё раз. Состояния: ```staged```, ```modified``` (+ ```tracked```). Обратите внимание: ```staged``` и ```modified``` у одного файла, но у разных его версий.
	- Ещё раз выполнили ```git add```. Состояние: ```staged``` (+ ```tracked```).
3. Сделали коммит с помощью ```git commit```. Состояние: ```tracked```
4. Изменили файл. Состояние: ```modified``` (+ ```tracked```).
5. Снова добавили в ```staging area``` с помощью ```git add```. Состояния: ```staged``` (+``` tracked```).
6. Сделали коммит. Состояния: ```tracked```.
7. etc


