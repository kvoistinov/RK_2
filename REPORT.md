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
> echo "# TIMP's RK_2" > README.md

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
> cmake -H. -Bbuild
-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/ USER_NAME/PATH .../build

!!! EDIT

> cmake --build _build
[ 50%] Building CXX object CMakeFiles/rk_2.dir/source/pattern_memento.cpp.o
[100%] Linking CXX executable rk_2
[100%] Built target rk_2

> cd build
> ./rk_2
2
1
3

> cd ..
> git add .
git commit -m "Build project"
[main e630f8d] Build project
 33 files changed, 3623 insertions(+), 7 deletions(-)
 create mode 100644 build/CMakeCache.txt
 create mode 100644 build/CMakeFiles/3.29.0/CMakeCCompiler.cmake
 create mode 100644 build/CMakeFiles/3.29.0/CMakeCXXCompiler.cmake
 create mode 100755 build/CMakeFiles/3.29.0/CMakeDetermineCompilerABI_C.bin
 create mode 100755 build/CMakeFiles/3.29.0/CMakeDetermineCompilerABI_CXX.bin
 create mode 100644 build/CMakeFiles/3.29.0/CMakeSystem.cmake
 create mode 100644 build/CMakeFiles/3.29.0/CompilerIdC/CMakeCCompilerId.c
 create mode 100755 build/CMakeFiles/3.29.0/CompilerIdC/a.out
 create mode 100644 build/CMakeFiles/3.29.0/CompilerIdCXX/CMakeCXXCompilerId.cpp
 create mode 100755 build/CMakeFiles/3.29.0/CompilerIdCXX/a.out
 create mode 100644 build/CMakeFiles/CMakeConfigureLog.yaml
 create mode 100644 build/CMakeFiles/CMakeDirectoryInformation.cmake
 create mode 100644 build/CMakeFiles/Makefile.cmake
 create mode 100644 build/CMakeFiles/Makefile2
 create mode 100644 build/CMakeFiles/TargetDirectories.txt
 create mode 100644 build/CMakeFiles/cmake.check_cache
 create mode 100644 build/CMakeFiles/progress.marks
 create mode 100644 build/CMakeFiles/rk_2.dir/DependInfo.cmake
 create mode 100644 build/CMakeFiles/rk_2.dir/build.make
 create mode 100644 build/CMakeFiles/rk_2.dir/cmake_clean.cmake
 create mode 100644 build/CMakeFiles/rk_2.dir/compiler_depend.make
 create mode 100644 build/CMakeFiles/rk_2.dir/compiler_depend.ts
 create mode 100644 build/CMakeFiles/rk_2.dir/depend.make
 create mode 100644 build/CMakeFiles/rk_2.dir/flags.make
 create mode 100644 build/CMakeFiles/rk_2.dir/link.txt
 create mode 100644 build/CMakeFiles/rk_2.dir/progress.make
 create mode 100644 build/CMakeFiles/rk_2.dir/source/pattern_memento.cpp.o
 create mode 100644 build/CMakeFiles/rk_2.dir/source/pattern_memento.cpp.o.d
 create mode 100644 build/Makefile
 create mode 100644 build/cmake_install.cmake
 create mode 100755 build/rk_2

> git push origin main
Enumerating objects: 45, done.
Counting objects: 100% (45/45), done.
Delta compression using up to 8 threads
Compressing objects: 100% (40/40), done.
Writing objects: 100% (42/42), 69.61 KiB | 5.80 MiB/s, done.
Total 42 (delta 7), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (7/7), completed with 1 local object.
To https://github.com/Trener-Egor/RK_2.git
   3a1bd1c..e630f8d  main -> main
```

# GitHub Actions
```
> mkdir -p .github/workflows
> touch .github/workflows/build.yml
> nvim .github/workflows/build.yml
name: TIMP RK_2 workflow

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Install GCC
        run: sudo apt-get update && sudo apt-get install -y g++

      - name: Create build directory
        run: mkdir build && cd build

      - name: Configure CMake
        run: cmake ..

      - name: Build
        run: make

      - name: Upload artifact
        uses: actions/upload-artifact@v2
        with:
          name: rk_2_executable
          path: build/rk_2

> git add . &&  git commit -m "Add GitHub Actions"
> git push origin main
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 380 bytes | 380.00 KiB/s, done.
Total 4 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/Trener_Egor/RK_2.git
   cda561e..c91759e  main -> main




````

# GTest
```



```

# CPack
```



```


