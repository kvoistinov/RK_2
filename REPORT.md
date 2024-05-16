# Создание нового репозитория:
```
// предварительно идем в свой рабочи каталог
> mkdir RK_2

> cd RK_2

> git init

> gh repo create ${GITHUB_USERNAME}/RK_2 --public
```

# Создание каталога source и первый коммит
```
> echo "# TIMO's RK_2" > README.md

> mkdir source

> cd source

> touch pattern_memento.cpp

> nvim pattern_memento.cpp
// add code
> git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   README.md
	new file:   source/pattern_memento.cpp

> git add .
git commit -m "add README.md"
[master (root-commit) 82bfe07] add README.md
 2 files changed, 63 insertions(+)
 create mode 100644 README.md
 create mode 100644 source/pattern_memento.cpp
 
> git branch -M main

> git branch
 * main

> git remote add origin https://github.com/Trener-Egor/RK_2.git

> git push origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 761 bytes | 761.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/Trener-Egor/RK_2.git
 * [new branch]      main -> main
```

# Работа с CMake
```
> touch CMakeLists.txt
> cat > CMakeLists.txt <<EOF
cmake_minimum_required(VERSION 3.10)

project(rk_2)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_COMPILER g++)

# Указываем папку с исходными файлами
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/source)

# Указываем исходный файл
add_executable(rk_2 ${CMAKE_CURRENT_SOURCE_DIR}/source/pattern_memento.cpp) 

EOF

> git commit -m "Add CMakeLists.txt"
[main 3a1bd1c] Add CMakeLists.txt
 2 files changed, 31 insertions(+)
 create mode 100644 CMakeLists.txt

> git push origin main
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 774 bytes | 774.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Trener-Egor/RK_2.git
   dbd921e..3a1bd1c  main -> main

// Создадим сборку
> mkdir build

```
