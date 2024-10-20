---
## Front matter
title: "Доклад"
subtitle: "Ошибки проверки вводимых данных: инъекция кода"
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

# Введение

**SQL-инъекция** (SQLi) — это одна из наиболее распространенных уязвимостей веб-приложений, позволяющая злоумышленникам манипулировать базами данных через внедрение вредоносного SQL-кода в запросы. Эта проблема возникает, когда вводимые пользователями данные не фильтруются должным образом, что может привести к утечке конфиденциальной информации или даже полному разрушению базы данных. По данным исследований, более 80% атак на веб-приложения связаны с SQL-инъекциями, что подчеркивает важность понимания этой угрозы.

# Определение SQL-инъекции

SQL-инъекция представляет собой метод атаки, при котором злоумышленник внедряет SQL-код в запросы, отправляемые к серверу базы данных. Это может произойти через формы ввода на веб-сайте, где пользователь вводит данные, которые затем обрабатываются сервером без должной проверки. Уязвимости SQL-инъекции могут использоваться для выполнения различных действий, таких как:

- Извлечение данных из базы данных.
- Изменение или удаление данных.
- Выполнение произвольных команд на сервере базы данных.

# Как происходят атаки на основе SQL-инъекции

Атака SQL-инъекцией может быть реализована несколькими способами:

### 1. Внутриполосная атака (In-band SQLi)

Использует один и тот же канал для получения результатов. Существует два подвида:

- **Атака на основе ошибок**: Злоумышленник вызывает ошибку базы данных, чтобы получить информацию о ее структуре.
- **Атака на основе объединения**: Использует оператор UNION для объединения результатов нескольких запросов.

### 2. Инференциальная атака (Blind SQLi)

Злоумышленник не видит результаты запроса, но может делать выводы на основе поведения приложения. Например, если приложение возвращает разные сообщения об ошибках в зависимости от того, существует ли запись в базе данных.

### 3. Сложные атаки

Включают использование нескольких команд в одном запросе, что позволяет выполнять сложные операции с базой данных. Например, злоумышленник может использовать подзапросы или временные таблицы для достижения своих целей.

# Примеры SQL-инъекций

Пример уязвимости можно продемонстрировать на простом SQL-запросе:

> SELECT * FROM users WHERE username = '$username';

Если злоумышленник введет в поле ввода admin' --, итоговый запрос станет:

> SELECT * FROM users WHERE username = 'admin' --';

Здесь символ $--$ игнорирует остальную часть запроса, что позволяет злоумышленнику обойти проверку пароля и получить доступ к учетной записи администратора.

**Другие примеры**

Извлечение данных:
> ' OR '1'='1

Этот код всегда будет возвращать истинное значение и позволит злоумышленнику получить доступ ко всем записям.

Удаление данных:
> '; DROP TABLE users; --

Этот код приведет к удалению таблицы users, что может вызвать серьезные последствия для приложения.

# Причины уязвимости
Основные причины возникновения уязвимостей SQL-инъекций включают:

- Динамическое построение SQL-запросов: Неправильное использование пользовательских данных в запросах без фильтрации.
- Небезопасная конфигурация СУБД: Учетные записи с избыточными правами могут выполнять непредусмотренные команды.
- Недостаток обучения разработчиков: Многие разработчики не знакомы с основами безопасности и лучшими практиками защиты от атак.

# Защита от SQL-инъекций
Для защиты от SQL-инъекций рекомендуется использовать следующие методы:

1. **Параметризация запросов**
Использование подготовленных выражений для предотвращения внедрения вредоносного кода. Например, вместо динамического построения запроса:
> SELECT * FROM users WHERE username = '$username';

Следует использовать подготовленный запрос:
> $stmt = $pdo->prepare('SELECT * FROM users WHERE username = :username');
> $stmt->execute(['username' => $username]);

2. **Фильтрация входных данных**
Проверка и очистка всех пользовательских данных перед их использованием в запросах. Это включает в себя удаление или экранирование специальных символов.

3. **Минимизация привилегий**
Учетные записи базы данных должны иметь минимальные необходимые права доступа. Например, учетная запись, используемая приложением, не должна иметь прав на удаление таблиц или изменение структуры базы данных.

4. **Регулярные обновления и патчи**
Поддержание актуальности программного обеспечения и систем управления базами данных помогает закрыть известные уязвимости.

5. **Использование веб-файрволов**
Веб-файрволы могут помочь в обнаружении и блокировке подозрительных запросов до того, как они достигнут приложения.

# Заключение
SQL-инъекции представляют собой серьезную угрозу для безопасности веб-приложений. Понимание механизмов этих атак и применение эффективных методов защиты могут значительно снизить риск компрометации данных. Важно, чтобы разработчики и администраторы систем уделяли внимание безопасности своих приложений и регулярно обновляли свои знания о новых методах защиты.

# Список литературы
1. Kaspersky Lab. "SQL-инъекция и как ее предотвратить";
2. Positive Technologies. "SQL Injection от А до Я";
3. OWASP Foundation. "OWASP Top Ten - A10:2021 - Server-Side Request Forgery";
4. Яндекс. "SQL-инъекция - Вебмастер".