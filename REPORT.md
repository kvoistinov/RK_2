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
set(CMAKE_CXX_COMPILER g++) 

include_directories(./source/)

add_executable(rk_2 pattern_memento.cpp)

EOF

> 


```
