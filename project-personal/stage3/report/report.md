---
## Front matter
title: "Индивидуальный проект. Этап №3"
subtitle: "Использование Hydra"
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

Подобрать пароль для пользователя, используя Hydra.

---

# Теоретические сведения

**Hydra** – это программное обеспечение с открытым исходным кодом для перебора паролей в реальном времени от различных онлайн сервисов, веб-приложений, FTP, SSH и других протоколов. Это распараллеленный взломщик для входа в систему, он поддерживает множество протоколов для осуществления атак. Пользователь быстро и с легкостью может добавить новые модули. Hydra предоставляет специалистам в сфере ИБ возможность узнать, насколько легко можно получить несанкционированный доступ к системе с удаленного устройства.

---

# Выполнение лабораторной работы

Перейдём на наш веб сервер DVWA(рис. [-@fig:001])

![Стартовая страница](image/1.png){ #fig:001 width=70% }

И для начала установим самый низкий уровень защиты DVWA(рис. [-@fig:002])

![Уровень защиты](image/2.png){ #fig:002 width=70% }

Перейдём на старницу brute force атаки - так выглядит окно для логина(рис. [-@fig:003])

![Форма для логина](image/3.png){ #fig:002 width=70% }

Левой кнопкой мыши кликаем на экран и выбираем последний пукт - выходит следующее окно - из него берём инофрмацию по Cookies на вкладке Network(рис. [-@fig:004])

![Окно Network](image/4.png){ #fig:004 width=70% }

Распаковываем зип файл, в котором находятся все популярные пароли(рис. [-@fig:005])

![Распаковка файла](image/5.png){ #fig:005 width=70% }

Вводим следующий запрос к Hydra и получаем пароли(рис. [-@fig:006])

![Пароли](image/6.png){ #fig:006 width=70% }

Вводим нужный логин и пароль - выходит следующее окно(рис. [-@fig:007])

![Верный логин и пароль](image/7.png){ #fig:007 width=70% }

---

# Вывод

В ходе выполнения работы была проведена brute force атака c помощью Hydra.

---


