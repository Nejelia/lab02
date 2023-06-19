## Laboratory work II

Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```bash
$ open https://git-scm.com
```

## Tasks

- [ ] 1. Создать публичный репозиторий с названием **lab02** и с лиценцией **MIT**
- [ ] 2. Сгенирировать токен для доступа к сервису **GitHub** с правами **repo**
- [ ] 3. Ознакомиться со ссылками учебного материала
- [ ] 4. Выполнить инструкцию учебного материала
- [ ] 5. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```console
$ export GITHUB_USERNAME=Nejelia
$ export GITHUB_EMAIL=viktoriyaucheba@yandex.ru
$ export GITHUB_TOKEN=сгенирированный_токен
$ alias edit=vim
```

```console
$ cd ${GITHUB_USERNAME}/workspace
$ source scripts/activate
```

```console
$ mkdir ~/.config
$ cat > ~/.config/hub <<EOF
github.com:
- user: ${GITHUB_USERNAME}
  oauth_token: ${GITHUB_TOKEN}
  protocol: https
EOF
$ git config --global hub.protocol https
```

```console
$ mkdir projects/lab02 && cd projects/lab02
$ git init
$ git config --global user.name ${GITHUB_USERNAME}
$ git config --global user.email ${GITHUB_EMAIL}
$ git config -e --global
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab02.git
$ git pull origin master
$ touch README.md
$ git status
Текущая ветка: master

Еще нет коммитов

Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	README.md
	node-v6.11.5-linux-x64/
	node/
	projects/
	reports/
	scripts/
	tasks/

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)

$ git add README.md
$ git commit -m"added README.md"
[master (корневой коммит) 9bfc368] added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
$ git push origin master
Username for 'https://github.com': Nejelia
Password for 'https://Nejelia@github.com': 
Перечисление объектов: 3, готово.
Подсчет объектов: 100% (3/3), готово.
Запись объектов: 100% (3/3), 223 байта | 223.00 КиБ/с, готово.
Всего 3 (изменений 0), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: 
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/Nejelia/lab02/pull/new/master
remote: 
To https://github.com/Nejelia/lab02.git
 * [new branch]      master -> master

```

Добавить на сервисе **GitHub** в репозитории **lab02** файл **.gitignore**
со следующем содержимом:

```sh
*build*/
*install*/
*.swp
.idea/
```

```console
$ git pull origin master
Из https://github.com/Nejelia/lab02
 * branch            master     -> FETCH_HEAD
Уже актуально.
$ git log
commit 9bfc3686d834beaddb04530b4d5e617694a45692 (HEAD -> master, origin/master)
Author: Nejelia <viktoriyaucheba@yandex.ru>
Date:   Sun Jun 18 21:41:26 2023 +0300

    added README.md

    Initial commit
```

```console
$ mkdir sources
$ mkdir include
$ mkdir examples
$ cat > sources/print.cpp <<EOF
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
EOF
```

```console
$ cat > include/print.hpp <<EOF
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
EOF
```

```console
$ cat > examples/example1.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
EOF
```

```console
$ cat > examples/example2.cpp <<EOF
#include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
```

```console
$ edit README.md
```

```console
$ git status
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	.README.md.swp
	examples/
	include/
	node-v6.11.5-linux-x64/
	node/
	projects/
	reports/
	scripts/
	sources/
	tasks/

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
$ git add .
$ git commit -m"added sources"
$ git push origin master
Username for 'https://github.com': Nejelia
Password for 'https://Nejelia@github.com': 
```

## Report

```sh
$ cd ~/workspace/
$ export LAB_NUMBER=02
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER}.git tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md
```

## Homework

### Part I

1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).
2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.

```console
$ cd workspace/projects/
bash: cd: workspace/projects: Нет такого файла или каталога
$ mkdir projects
$ cd projects
$ git clone https://github.com/Nejelia/hw2
Клонирование в «hw2»...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Получение объектов: 100% (3/3), готово.
$ cd hw2
$ touch README.md
$ git status
Текущая ветка: main
Эта ветка соответствует «origin/main».

Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
 README.md

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
$ git add README.md
$ git commit -m"added README.md"
[main a95c71f] added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.mdgit push origin main
Username for 'https://github.com': Nejelia
Password for 'https://Nejelia@github.com': 

Перечисление объектов: 4, готово.
Подсчет объектов: 100% (4/4), готово.
При сжатии изменений используется до 16 потоков
Сжатие объектов: 100% (2/2), готово.
Запись объектов: 100% (3/3), 283 байта | 283.00 КиБ/с, готово.
Всего 3 (изменений 0), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
To https://github.com/Nejelia/hw2
   84dfe61..a95c71f  main -> main
```

3. Создайте файл `hello_world.cpp` в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу **Hello world** на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку `using namespace std;`.

```console
$ mkdir sources
$ cat > sources/hello_world.cpp <<EOF
> #include <iostream>
> using namespace std;
> int main()
> {
>  cout<<"Hello world!";
>  return 0;
> }
> EOF
```

4. Добавьте этот файл в локальную копию репозитория.

```console
$ git add sources/hello_world.cpp
```

5. Закоммитьте изменения с *осмысленным* сообщением.

```console
$ git commit -m"added hello_world.cpp"
[main 2963490] added hello_world.cpp
 1 file changed, 7 insertions(+)
 create mode 100644 sources/hello_world.cpp
```
6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение `Hello world from @name`, где `@name` имя пользователя.

```console
$ edit sources/hello_world.cpp
```

7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно `git add`?

```console
$ git commit -m"fixed hello_world.cpp"
```

8. Запуште изменения в удалёный репозиторий.

```console
$ git push origin main
Username for 'https://github.com': Nejelia
Password for 'https://Nejelia@github.com': 
Перечисление объектов: 6, готово.
Подсчет объектов: 100% (6/6), готово.
При сжатии изменений используется до 16 потоков
Сжатие объектов: 100% (4/4), готово.
Запись объектов: 100% (4/4), 430 байтов | 430.00 КиБ/с, готово.
Всего 4 (изменений 1), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Nejelia/hw2
   9371f5f..2963490  main -> main
```

9. Проверьте, что история коммитов доступна в удалёный репозитории.

### Part II

**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*
1. В локальной копии репозитория создайте локальную ветку `patch1`.

```console
$ git checkout -b patch1
Switched to a new branch 'patch1'
```

2. Внесите изменения в ветке `patch1` по исправлению кода и избавления от `using namespace std;`.

```console
$ edit sources/hello_world.cpp
```

3. **commit**, **push** локальную ветку в удалённый репозиторий.

```console
$ git commit -m"fixed hello_world.cpp"
[patch1 777b688] fixed hello_world.cpp
 1 file changed, 1 insertion(+), 1 deletion(-)
nejelia@nejelia-ROG-Strix-G533QM-G533QM:~/workspace/projects/hw2$ git push origin patch1
Username for 'https://github.com': Nejelia
Password for 'https://Nejelia@github.com': 
Перечисление объектов: 7, готово.
Подсчет объектов: 100% (7/7), готово.
При сжатии изменений используется до 16 потоков
Сжатие объектов: 100% (4/4), готово.
Запись объектов: 100% (4/4), 378 байтов | 378.00 КиБ/с, готово.
Всего 4 (изменений 2), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
remote: 
remote: Create a pull request for 'patch1' on GitHub by visiting:
remote:      https://github.com/Nejelia/hw2/pull/new/patch1
remote: 
To https://github.com/Nejelia/hw2
 * [new branch]      patch1 -> patch1
```

4. Проверьте, что ветка `patch1` доступна в удалёный репозитории.
5. Создайте pull-request `patch1 -> master`.
6. В локальной копии в ветке `patch1` добавьте в исходный код комментарии.

```console
$ edit sources/hello_world.cpp
```

7. **commit**, **push**.

```console
$ git add sources/hello_world.cpp 
$ git commit -m"hello_world.cpp with new comments"
[patch1 bd6f2a5] hello_world.cpp with new comments
 1 file changed, 1 insertion(+), 1 deletion(-)
nejelia@nejelia-ROG-Strix-G533QM-G533QM:~/workspace/projects/hw2$ git push origin patch1
Username for 'https://github.com': Nejelia
Password for 'https://Nejelia@github.com': 
Перечисление объектов: 7, готово.
Подсчет объектов: 100% (7/7), готово.
При сжатии изменений используется до 16 потоков
Сжатие объектов: 100% (4/4), готово.
Запись объектов: 100% (4/4), 404 байта | 404.00 КиБ/с, готово.
Всего 4 (изменений 2), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/Nejelia/hw2
   777b688..bd6f2a5  patch1 -> patch1
```

8. Проверьте, что новые изменения есть в созданном на **шаге 5** pull-request
9. В удалённый репозитории выполните  слияние PR `patch1 -> master` и удалите ветку `patch1` в удаленном репозитории.
10. Локально выполните **pull**.

```console
$ git pull origin main
Из https://github.com/Nejelia/hw2
 * branch            main       -> FETCH_HEAD
Уже актуально.
```
11. С помощью команды **git log** просмотрите историю в локальной версии ветки `master`.

```console
$ git log
git log
commit bd6f2a58ccf607ec2ef4174f0a23c6faf38f2ce0 (HEAD -> patch1, origin/patch1)
Author: Nejelia <viktoriyaucheba@yandex.ru>
Date:   Sun Jun 18 23:40:37 2023 +0300

    hello_world.cpp with new comments

commit 777b688344a2ea450494cd8e5de9e1ecea011eb7
Author: Nejelia <viktoriyaucheba@yandex.ru>
Date:   Sun Jun 18 23:37:24 2023 +0300

    fixed hello_world.cpp

commit e0976638782cb7420c639985ff12a956061a5356 (origin/main, origin/HEAD, main)
Author: Nejelia <viktoriyaucheba@yandex.ru>
Date:   Sun Jun 18 23:33:50 2023 +0300

    fixed hello_world.cpp

commit 29634900b2bda1e0fdbafed539b170064ea4c37a
Author: Nejelia <viktoriyaucheba@yandex.ru>
Date:   Sun Jun 18 23:17:16 2023 +0300

    added hello_world.cpp

commit 9371f5f924e15b6311641b7a724e4e0875215119
Author: Nejelia <viktoriyaucheba@yandex.ru>
Date:   Sun Jun 18 23:10:28 2023 +0300

    added sources

commit e6e0d39058b86f100b1238dd8a3fa94a6bf3c356
Author: Nejelia <viktoriyaucheba@yandex.ru>
Date:   Sun Jun 18 23:07:32 2023 +0300

    added .gitignore

commit a95c71f8a9f99baad296dc2f7e509baf23d51768
Author: Nejelia <viktoriyaucheba@yandex.ru>
Date:   Sun Jun 18 23:04:13 2023 +0300

    added README.md

commit 84dfe61ee63249246e0f81ac778612572c3cb0aa
Author: Nejelia <112762288+Nejelia@users.noreply.github.com>
Date:   Sun Jun 18 22:58:43 2023 +0300

```
12. Удалите локальную ветку `patch1`.

```console
$ git branch --delete patch1
error: Нельзя удалить ветку «patch1» т.к. она активна на «/home/nejelia/workspace/projects/hw2»
$ git checkout main
Переключились на ветку «main»
Эта ветка соответствует «origin/main».
$ git branch --delete patch1
error: Ветка «patch1» не слита полностью.
Если вы уверены, что хотите ее удалить, запустите «git branch -D patch1».
$ git branch -D patch1 
Ветка patch1 удалена (была bd6f2a5).
```

### Part III

**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*
1. Создайте новую локальную ветку `patch2`.

```console
$ git checkout -b patch2
Переключились на новую ветку «patch2»
```

2. Измените *code style* с помощью утилиты [**clang-format**](http://clang.llvm.org/docs/ClangFormat.html). Например, используя опцию `-style=Mozilla`.

```console
$ sudo apt install clang-format
$ clang-format -i --style=Mozilla sources/hello_world.cpp
```

3. **commit**, **push**, создайте pull-request `patch2 -> master`.

```console
$ git add sources/hello_world.cpp 
$ git commit -m "new code-style"
$ git push origin patch2 
Username for 'https://github.com': Nejelia
Password for 'https://Nejelia@github.com': 
```

4. В ветке **master** в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.

```console
$ edit sources/hello_world.cpp
$ git commit -m "new comment"
```

5. Убедитесь, что в pull-request появились *конфликты*.
6. Для этого локально выполните **pull** + **rebase** (точную последовательность команд, следует узнать самостоятельно). **Исправьте конфликты**.

```console
$ git pull --rebase origin patch2
Из https://github.com/Nejelia/hw2
 * branch            patch2     -> FETCH_HEAD
Уже актуально.
```

7. Сделайте *force push* в ветку `patch2`

```console
$ git push origin patch2 --force
Username for 'https://github.com': Nejelia
Password for 'https://Nejelia@github.com': 
Everything up-to-date

```

8. Убедитель, что в pull-request пропали конфликтны. 
9. Вмержите pull-request `patch2 -> master`.

## Links

- [hub](https://hub.github.com/)
- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)

```
Copyright (c) 2015-2021 The ISC Authors
```
