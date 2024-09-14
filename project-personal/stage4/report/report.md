---
## Front matter
title: "Индивидуальный проект. Этап №1"
subtitle: "Установка Kali Linux"
author: "Камкина Арина Леонидовна"

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
lot: false # List of tables
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
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Установить дистрибутив Kali Linux в виртальную машину.

---

# Выполнение лабораторной работы

## Базовая настройка виртуальной машины

Создаём новую виртуальную машину с именем Kali(рис. [-@fig:001])

![Окно создания виртуальной машины](image/1.png){ #fig:001 width=70% }

Выделяем память под неё(рис. [-@fig:002])

![Выделение памяти](image/2.png){ #fig:002 width=70% }

Настраиваем жесткий диск - Виртуальный Жесткий Диск 20Гб(рис. [-@fig:003])

![Настройка жесткого диска](image/3.png){ #fig:003 width=70% }

Выбираем язык (русский)(рис. [-@fig:004])

![Выбор языка](image/5.png){ #fig:004 width=70% }

## Настройка сети

Вводим имя компьютера(рис. [-@fig:005])

![Имя компьютера](image/6.png){ #fig:005 width=70% }

Задаём имя домена(рис. [-@fig:006])

![Имя домена](image/7.png){ #fig:006 width=70% }

## Настройка учётных записей пользователей и паролей

Вводим своё реальное имя(рис. [-@fig:007])

![Моё имя](image/8.png){ #fig:007 width=70% }

Задаём имя учётной записи(рис. [-@fig:008])

![Имя учётной записи](image/9.png){ #fig:008 width=70% }

Задаём пароль для учётной записи(рис. [-@fig:009])

![Создание пароля](image/10.png){ #fig:009 width=70% }

## Разметка дисков

Задаём разметку диска
(рис. [-@fig:010])(рис. [-@fig:011])(рис. [-@fig:012])(рис. [-@fig:013])

![Выбор метода разметки](image/11.png){ #fig:010 width=70% }
![Выбор диска для разметки](image/12.png){ #fig:011 width=70% }
![Схема разметки диска](image/13.png){ #fig:012 width=70% }
![Запись изменений на диск](image/14.png){ #fig:013 width=70% }

## Выбор программного обеспечения

(рис. [-@fig:014])

![Выбор ПО](image/15.png){ #fig:014 width=70% }

## Учётная запись создана

Входим в аккаунт - вводим имя пользователя и пароль и переходмм на рабочий стол
(рис. [-@fig:015])(рис. [-@fig:016])

![Вход в аккаунт](image/16.png){ #fig:015 width=70% }
![Рабочий стол](image/17.png){ #fig:016 width=70% }

---

# Вывод

В ходе выполнения работы был установлен Kali Linux на виртальную машину.

---


