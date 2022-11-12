---
## Front matter
title: "Лабораторная работа №5"
author: "Даниил Щетинин Николаевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
lofTitle: "Список иллюстраций"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Освоение процедуры компиляции и сборки программ, написанных на ассемблере NASM

# Задание

Использовать ассемблер NASM для исполнения и компиляции простейших программ 

# Выполнение лабораторной работы

**Шаг 1** 
Создаём каталог для работы, используя команду mkdir:

```

mkdir ~/work/arch-pc/lab05
```

Перейдём в него

**Шаг 2**
После того как мы перешли в каталог, используем команду touch 

```
touch hello.asm
```

Для создания файла hello.asm

(рис. [-@fig:001])

**Шаг 3**
Убедимся, что файл создан, откроем его с помощью текстового редактора и введём в него код программы:

(рис. [-@fig:002])


**Шаг 4**
Компилируем файл нашей программы с помощью команды nasm 

```
nasm -f elf hello.asm
```

таким образом, текст hello.asm компилируется в файл hello.o

проверим его наличие:

(рис. [-@fig:003])


**Шаг 5**
С помощью команды nasm скомпилируем файл hello.asm в obj.o и создадим файл листинга list.lst:
```
nasm -o obj.o -f elf -g -l list.lst hello.asm
```


(рис. [-@fig:004])

**Шаг 6**
Исполняем команду ld
```
ld -m elf_i386 hello.o -o hello
```
для создания исполняемого файла и проверяем чтобы исполняемый файл hello был создан

(рис. [-@fig:004])


**Шаг 7**
Исполняем команду ld
```
ld -m elf_i386 obj.o -o main
```
для того, чтобы сделать исполняемый файл main из объектного файла obj.o

(рис. [-@fig:005])

**Шаг 8**

Запускаем созданный файл, для этого введём

```
./hello
```
вывод строчки 'Hello World!' на экран:

(рис. [-@fig:005])

# Выполнение самостоятельной работы

**Шаг 1**

Копируем hello.asm с именем lab5.asm, редактируем строчку Hello world! для того, чтобы она отображала фамилию и имя и вводим команды:

```
nasm -f elf lab5.asm
ld -m elf_i386 lab5.o -o lab5

```

для создания исполняемого файла


исполнение файла:

(рис. [-@fig:006])

    


![создание hello.asm](image/1.jpg){ #fig:001 width=90% }

![код файла hello.asm](image/2.jpg){ #fig:002 width=100% }

![создание hello.o](image/3.jpg){ #fig:003 width=100% }

![создание list.lst и obj.o](image/4.jpg){ #fig:004 width=70% }

![создание и исполнение файла hello](image/5.jpg){ #fig:005 width=100% }

![создание и исполнение lab5.o](image/6.jpg){ #fig:006 width=100% }



# Выводы

Я использовал ассемблер NASM для создания и исполнения программы.
