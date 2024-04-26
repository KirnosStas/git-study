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
