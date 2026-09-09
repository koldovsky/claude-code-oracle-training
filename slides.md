---
theme: ./theme
title: Claude Code для Oracle-розробки
info: |
  Сесія 1 — основи, контекст, робота з базою.
  Навчальна база Oracle 19c.
colorSchema: dark
layout: cover
brand: Claude Code · Oracle
tag: сесія 1 · 2 години
mdc: true
transition: slide-left
routerMode: hash
selectable: true
---

<GfEyebrow>Навчальна база · Oracle 19c</GfEyebrow>

# Claude Code<br><span class="grad">для Oracle</span>

Основи, контекст-інжиніринг і робота з базою. Дві вправи руками — з перевіркою результату.

<div class="day-jump-wrap flex gap-3 flex-wrap" style="margin-top:1.5em">
<a href="https://koldovsky.github.io/claude-code-oracle-training/cheatsheet.html" target="_blank">Шпаргалка з усіма командами →</a>
<a href="https://github.com/koldovsky/acordbank-oracle-training" target="_blank">Репозиторій курсу →</a>
</div>

<!--
Не затримуйтесь тут. Одразу далі — розклад дає людям опору на всі дві години.
-->

---

<GfEyebrow>Сьогодні</GfEyebrow>

## Дві години, дві вправи

<div class="flow f4" style="margin-top:1.4em">
  <div class="fn on"><div class="dot"></div><div class="t">Контекст</div><div class="s">0:00 – 0:45</div></div>
  <div class="fn"><div class="dot"></div><div class="t">Вправа 1</div><div class="s">0:45 – 1:00</div></div>
  <div class="fn"><div class="dot"></div><div class="t">База</div><div class="s">1:10 – 1:35 · перерва 1:00</div></div>
  <div class="fn"><div class="dot"></div><div class="t">Вправа 2</div><div class="s">1:35 – 1:55</div></div>
</div>

<div class="chips" style="margin-top:2em">
  <span class="pill green">каталог db/ — 63 файли DDL</span>
  <span class="pill cyan">схеми HR · CO · SH</span>
  <span class="pill">своя схема у кожного</span>
</div>

<div class="lead" style="margin-top:1.4em">
Слайдів мало навмисно. Дві третини часу — руки на клавіатурі.
</div>

---
layout: section
---

<GfEyebrow>Головне непорозуміння</GfEyebrow>

# Він не знає<br>вашу базу

Він знає рівно те, що бачить у цю мить.

---

<GfEyebrow>Два наслідки</GfEyebrow>

## Що з цього випливає

<div class="grid grid-cols-2 gap-5" style="margin-top:1.2em">

<div class="card hot">
<div class="kick green">рішення за вами</div>
<p><b>Ви вирішуєте, що він побачить.</b></p>
<p>Це не пошуковик по вашій системі. Це виконавець, якому ви даєте матеріал.</p>
<p style="margin-top:.8em;color:var(--green-400)">Якість відповіді = якість матеріалу.</p>
</div>

<div class="card warn">
<div class="kick amber">контекст коштує</div>
<p><b>Він обмежений і платний.</b></p>
<p>«Дати все про всяк випадок» — не обережність.</p>
<p style="margin-top:.8em;color:var(--amber-400)">Це найдорожчий спосіб отримати гіршу відповідь.</p>
</div>

</div>

---

<GfEyebrow>Межі інструмента</GfEyebrow>

## Чого очікувати, а чого ні

<div class="cmp c2" style="margin-top:1em">
  <div class="row head"><div class="c good">Працює добре</div><div class="c bad">Працює погано</div></div>
  <div class="row"><div class="c">Прочитати чужий PL/SQL і пояснити</div><div class="c">Вгадати, що ви мали на увазі під «залишками»</div></div>
  <div class="row"><div class="c">Знайти всі місця використання — <b>якщо дали де шукати</b></div><div class="c">Знайти щось у 250 000 обʼєктів без карти</div></div>
  <div class="row"><div class="c">Побудувати запит по відомій структурі</div><div class="c">Згадати структуру, якої не бачив</div></div>
  <div class="row"><div class="c">Пояснити план виконання</div><div class="c">Сказати, чи запит швидкий, не запустивши</div></div>
</div>

<!--
Демо: відкрити db/, спитати "що це за схема, коротко".
Показати, ЯКІ ФАЙЛИ він прочитав. Він не знав — він прочитав.
-->

---
layout: section
---

<GfEyebrow>Перш ніж торкатися бази</GfEyebrow>

# Що він уміє<br>і що йому дозволено

---

<GfEyebrow>Можливості</GfEyebrow>

## Чотири речі, які він робить у вашому проєкті

<div class="grid grid-cols-2 gap-5" style="margin-top:1em">

<div class="card">
<div class="kick green">читає</div>
<p>Файли, вивід команд, схему з каталогу. <b>Тільки те, що ви дали</b> — не «всю систему»</p>
</div>

<div class="card">
<div class="kick cyan">запускає</div>
<p>Команди в терміналі: <code>grep</code>, <code>git</code>, <code>sql</code>. Щоразу питає дозвіл</p>
</div>

<div class="card">
<div class="kick violet">редагує</div>
<p>Файли на диску. Показує diff <b>до</b> застосування</p>
</div>

<div class="card">
<div class="kick amber">підключається</div>
<p>До зовнішніх систем через MCP. Сьогодні це SQLcl → Oracle</p>
</div>

</div>

<div class="lead" style="margin-top:1.2em">
Усе інше — надбудови над цими чотирма: skills, subagents, hooks. Це Сесія 2.
</div>

---

<GfEyebrow>Налаштування</GfEyebrow>

## Що варто знати з першого дня

<div class="cmp c2" style="margin-top:1em">
  <div class="row head"><div class="c">Команда</div><div class="c">Навіщо</div></div>
  <div class="row"><div class="c"><code>/help</code></div><div class="c">перелік усього, що є</div></div>
  <div class="row"><div class="c"><code>/model</code></div><div class="c">сильніша для розбору коду, легша для рутини — це прямо впливає на вартість</div></div>
  <div class="row"><div class="c"><code>/permissions</code></div><div class="c">що йому дозволено робити без запиту</div></div>
  <div class="row"><div class="c"><code>Shift+Tab</code></div><div class="c">перемикання режиму дозволів</div></div>
  <div class="row"><div class="c"><code>/clear</code></div><div class="c">почати з чистим контекстом — коли розмова «поїхала»</div></div>
  <div class="row"><div class="c"><code>Esc</code></div><div class="c">зупинити його посеред дії</div></div>
</div>

<div class="callout amber" style="margin-top:1.2em">Вартість залежить від обсягу контексту — економія контексту це і якість, і гроші</div>

---
layout: section
---

<GfEyebrow>Особлива увага</GfEyebrow>

# Безпека

Три речі, які треба вирішити <b>до</b> того, як інструмент торкнеться робочої системи

---

<GfEyebrow>Безпека · 1</GfEyebrow>

## Режими дозволів — сходинка, а не перемикач

<div class="ladder" style="grid-template-columns:repeat(3,1fr);margin-top:1.2em">
  <div class="rung on">
    <div class="s">рівень 1</div>
    <div class="nm">Питати щоразу</div>
    <p>Кожна команда й кожне редагування — з вашого підтвердження. <b>Сьогодні працюємо так</b></p>
    <div class="bar"></div>
  </div>
  <div class="rung">
    <div class="s">рівень 2</div>
    <div class="nm">Дозволити читання</div>
    <p>Читає й шукає без запиту, зміни — з підтвердженням</p>
    <div class="bar"></div>
  </div>
  <div class="rung">
    <div class="s">рівень 3</div>
    <div class="nm">Не питати нічого</div>
    <p>У банку <b>не використовується</b>. Ми не показуємо його навіть як варіант</p>
    <div class="bar"></div>
  </div>
</div>

<div class="lead" style="margin-top:1.3em">
Режим фіксується <b>у файлі проєкту</b>, а не в чиїйсь пам'яті — тоді він однаковий
у всіх і його видно в рев'ю.
</div>

---

<GfEyebrow>Безпека · 2</GfEyebrow>

## Що виходить за межі машини, а що ні

<div class="cmp c2" style="margin-top:1em">
  <div class="row head"><div class="c bad">Іде до моделі</div><div class="c good">Не йде нікуди</div></div>
  <div class="row"><div class="c">Файли, які він <b>прочитав</b></div><div class="c">Файли, яких він не читав</div></div>
  <div class="row"><div class="c">Вивід команд, які він запустив</div><div class="c">Уся решта вашої системи</div></div>
  <div class="row"><div class="c">Ваші запитання й правки</div><div class="c">Паролі зі сховища SQLcl</div></div>
</div>

<div class="card warn" style="margin-top:1.2em">
<p><b>Практичний висновок.</b> Межа проходить рівно там, де ви її провели контекстом.
Тому «дати все про всяк випадок» — це не лише дорого, це ще й рішення про те,
що саме залишить периметр.</p>
</div>

<div class="lead" style="margin-top:1em">
Для банку є варіанти, де трафік не виходить за ваш хмарний акаунт — Bedrock, Vertex,
власний шлюз. Це рішення вашої ІБ, і воно вже у концепті.
</div>

---

<GfEyebrow>Безпека · 3</GfEyebrow>

## Чотири правила, які діють з сьогодні

<div class="grid grid-cols-2 gap-5" style="margin-top:1em">

<div class="card hot">
<div class="kick green">1 · доступ до бази</div>
<p>Окремий обліковий запис із мінімальними правами. <b>Ніколи не ADMIN</b>, ніколи не спільний на групу</p>
</div>

<div class="card hot">
<div class="kick green">2 · перевіряти SQL</div>
<p>Не приймайте число, не подивившись на запит. <code>«покажи SQL, який ти виконав»</code></p>
</div>

<div class="card hot">
<div class="kick green">3 · секрети</div>
<p>Паролі не в командному рядку і не у файлах проєкту. Збережене з'єднання, <code>.gitignore</code></p>
</div>

<div class="card hot">
<div class="kick green">4 · продакшн</div>
<p>Прямого доступу немає. У Фазі 3 — сходинками, кожна окремим рішенням ІБ</p>
</div>

</div>

<div class="callout" style="margin-top:1.3em">Увесь згенерований SQL видно штатним аудитом Oracle — «що там робив ШІ» має точну відповідь</div>

<!--
Це той слайд, який показують службі ІБ. Проговоріть пункт 4 повільно:
сьогодні ми в пісочниці, і це не тимчасове обмеження, а конструкція.
-->

---
layout: section
---

<GfEyebrow>Головна тема заняття</GfEyebrow>

# Контекст-<br>інжиніринг

Погана відповідь майже завжди означає поганий контекст, а не «модель дурна».

---

<GfEyebrow>Три антипатерни</GfEyebrow>

## Як питають і чому це ламається

<div class="cmp c2" style="margin-top:1em">
  <div class="row head"><div class="c bad">Як питають</div><div class="c">Чому ламається</div></div>
  <div class="row"><div class="c">«Подивись у базі й скажи»</div><div class="c">Не знає, де дивитись; бачить лише те, на що має права</div></div>
  <div class="row"><div class="c">Вивалити всю схему</div><div class="c">Не влазить, дорого, якість падає</div></div>
  <div class="row"><div class="c">Питати без критерію</div><div class="c">«Таблиця із залишками» → 400 кандидатів</div></div>
</div>

<div class="chips" style="margin-top:1.6em">
  <span class="pill green">конкретний матеріал</span>
  <span class="pill green">3–5 потрібних обʼєктів</span>
  <span class="pill green">ознака, за якою відрізнити потрібне</span>
</div>

---

<GfEyebrow>Демонстрація</GfEyebrow>

## Скільки місць треба виправити?

Змінюємо тип `CO.CUSTOMERS.CUSTOMER_ID`

<GfTerminal title="db/ — bash" accent="green" style="margin-top:1em">
<div><span style="color:var(--green-400)">$ </span>grep -rl 'CUSTOMER_ID' db/CO/</div>
<div style="color:var(--fg-3)">db/CO/tables/CUSTOMERS.sql</div>
<div style="color:var(--fg-3)">db/CO/tables/ORDERS.sql</div>
<div style="color:var(--fg-3)">db/CO/tables/SHIPMENTS.sql</div>
<div style="color:var(--fg-3)">… ще 3 індекси і 1 вʼюха</div>
</GfTerminal>

<div v-click class="callout" style="margin-top:1.2em">7 файлів. Ми впевнені, що це все?</div>

<!--
ПАУЗА. Дайте групі відповісти. Не поспішайте на наступний слайд.
-->

---

<GfEyebrow>Ні</GfEyebrow>

## Ще один файл лишився невидимим

<GfTerminal title="db/ — bash" accent="amber">
<div><span style="color:var(--amber-400)">$ </span>grep -ril 'customer_id' db/CO/</div>
<div style="color:var(--fg-3)">… ті самі 7 …</div>
<div style="color:var(--amber-400)">db/CO/views/PRODUCT_ORDERS.sql</div>
</GfTerminal>

<div v-click style="margin-top:1.2em">

У цій вʼюсі колонка записана **малими літерами** — тому регістрозалежний пошук її не побачив:

<div class="codeline">ON o.customer_id = c.customer_id</div>

</div>

<!--
Відкрийте PRODUCT_ORDERS.sql і покажіть рядок з o.customer_id.
Вправа далі — та сама задача, але інша колонка. Метод той самий, відповідь інша.
-->

---
layout: section
---

# Питання не «що він знайшов»

<div class="callout" style="margin-top:.6em">а <b>чого він не міг знайти</b></div>

<p>Вʼюха — рівно те, що зламалося б у продакшені.<br>
На 250 000 обʼєктів ця різниця — між робочою зміною і інцидентом.</p>

---
layout: section
---

<GfEyebrow>10 хвилин роботи + розбір</GfEyebrow>

# Вправа 1

Наслідки зміни колонки

---

<GfEyebrow>Вправа 1 · тільки каталог db/, база не потрібна</GfEyebrow>

## Що зламається, якщо змінити тип?

<div class="lead" style="margin-top:.8em">
Ми плануємо змінити тип <code>CO.PRODUCTS.PRODUCT_ID</code>.
</div>

<div class="grid grid-cols-3 gap-4" style="margin-top:1.2em">
<div class="card"><div class="kick green">1</div><p>Знайдіть <b>усі</b> місця, яких це торкнеться</p></div>
<div class="card"><div class="kick green">2</div><p>Напишіть, що саме зламається в кожному</p></div>
<div class="card hot"><div class="kick green">3</div><p><b>Як ви переконалися, що нічого не пропустили?</b></p></div>
</div>

<div class="callout amber" style="margin-top:1.2em">Третій пункт — головний</div>

<div class="day-jump-wrap" style="margin-top:1em"><a href="https://koldovsky.github.io/claude-code-oracle-training/cheatsheet.html#s3" target="_blank">Умова і команди — шпаргалка, розділ 3 →</a></div>

<!--
ЦЕЙ СЛАЙД ЛИШАЄТЬСЯ НА ЕКРАНІ 10 хвилин.
На розборі питайте не "скільки знайшли", а "хто знайшов сім і що зробив далі".
-->

---

<GfEyebrow>Вправа 1 · відповідь</GfEyebrow>

## Три відповіді, і всі три різні

<div class="cmp c3" style="margin-top:1em">
  <div class="row head"><div class="c">Як шукали</div><div class="c">Знайшло</div><div class="c">Вердикт</div></div>
  <div class="row"><div class="c"><code>grep 'PRODUCT_ID'</code></div><div class="c">7 файлів</div><div class="c bad">замало — немає вʼюх</div></div>
  <div class="row"><div class="c"><code>grep -i 'product_id'</code></div><div class="c">9 файлів</div><div class="c good">саме те, що зламається</div></div>
  <div class="row"><div class="c">словник даних</div><div class="c">+ ще одна вʼюха</div><div class="c mid">забагато — вона не зламається</div></div>
</div>

<div class="lead" style="margin-top:1.2em">
<code>DBA_DEPENDENCIES</code> знає про <b>три</b> залежні вʼюхи. Третя —
<code>PRODUCT_REVIEWS</code> — залежить від таблиці, але <b>жодного разу не згадує</b>
<code>PRODUCT_ID</code>: вона читає <code>product_details</code> через <code>JSON_TABLE</code>.
Тому текстовий пошук її не бачить — і правильно робить.
</div>

<!--
Ось чому це важливо: пошук по файлах буває і завузьким, і заширшим.
Каталог у Фазі 3 будується саме для того, щоб поєднати обидва джерела.
-->

---

<GfEyebrow>Вправа 1 · що саме зламається</GfEyebrow>

## Дев'ять місць, три категорії

<div class="grid grid-cols-3 gap-4" style="margin-top:1em">

<div class="card">
<div class="kick green">3 таблиці</div>
<p><code>PRODUCTS</code> — сама колонка, вона ж <b>identity</b>, і первинний ключ</p>
<p><code>ORDER_ITEMS</code>, <code>INVENTORY</code> — зовнішні ключі, тип має збігатися <b>точно</b></p>
</div>

<div class="card">
<div class="kick cyan">4 індекси</div>
<p><code>PRODUCTS_PK</code>, <code>ORDER_ITEMS_PRODUCT_U</code>,
<code>INVENTORY_PRODUCT_ID_I</code>, <code>INVENTORY_STORE_PRODUCT_U</code></p>
<p>перебудуються автоматично</p>
</div>

<div class="card hot">
<div class="kick amber">2 вʼюхи</div>
<p><code>PRODUCT_ORDERS</code>, <code>CUSTOMER_ORDER_PRODUCTS</code></p>
<p>стануть <b>INVALID</b> і перекомпілюються при першому зверненні — тобто впадуть <b>у рантаймі</b>, а не на <code>ALTER</code></p>
</div>

</div>

<div class="callout" style="margin-top:1.3em">Перевірено: інвалідується лише вʼюха, що <b>використовує</b> колонку</div>

<!--
Ми це справді прогнали на тестовій таблиці: вʼюха, яка колонку не читає,
лишилась VALID. Oracle 19c відстежує залежності на рівні колонок.
Головне для групи: view впаде не тоді, коли ви робите ALTER, а тоді,
коли хтось уперше до неї звернеться. Тобто вночі, у звіті.
-->

---
layout: section
---

# Перерва

<p>10 хвилин</p>

---
layout: section
---

<GfEyebrow>Друга частина</GfEyebrow>

# Підключення<br>до бази

---

<GfEyebrow>Як влаштований ланцюг</GfEyebrow>

## Claude Code → SQLcl → Oracle

<div class="flow f3" style="grid-template-columns:repeat(3,1fr);margin-top:1.2em">
  <div class="fn on"><div class="dot"></div><div class="t">Claude Code</div><div class="s">ваш термінал</div></div>
  <div class="fn on"><div class="dot"></div><div class="t">SQLcl</div><div class="s">sql -mcp</div></div>
  <div class="fn on"><div class="dot"></div><div class="t">навчальна БД</div><div class="s"><сервіс>_low</div></div>
</div>

<div style="margin-top:1.6em">
Підключення йде під <b>вашим особистим</b> обліковим записом — тому у кожного своя схема.
</div>

<div class="grid grid-cols-3 gap-5" style="margin-top:1.4em">
  <GfStat value="107" label="HR.EMPLOYEES" accent="green" />
  <GfStat value="1 950" label="CO.ORDERS" accent="cyan" />
  <GfStat value="3 914" label="CO.ORDER_ITEMS" accent="violet" />
</div>

<!--
Після відповіді обовʼязково: "покажи SQL, який ти виконав".
Ніколи не приймайте число, не подивившись на запит.
-->

---

<GfEyebrow>Спробуйте у себе</GfEyebrow>

## Ізоляція — перевірте на таблиці сусіда

<GfTerminal title="<сервіс>_low" accent="cyan">
<div><span style="color:var(--cyan-400)">SQL&gt; </span>select count(*) from trainee3.my_probe;</div>
<div style="color:var(--rose-400)">ORA-00942: table or view does not exist</div>
<div style="margin-top:.6em"><span style="color:var(--cyan-400)">SQL&gt; </span>create table hr.probe (x number);</div>
<div style="color:var(--rose-400)">ORA-01031: insufficient privileges</div>
</GfTerminal>

<div v-click class="card" style="margin-top:1.2em">
<p>Ви <b>точно знаєте</b>, що таблиця є — сусід щойно її створив.
Oracle усе одно каже «<b>не існує</b>», а не «немає доступу»: навмисно,
щоб не можна було вивідати склад бази.</p>
</div>

---
layout: section
---

<GfEyebrow>12 хвилин роботи + розбір</GfEyebrow>

# Вправа 2

Звіт із перевіркою

---

<GfEyebrow>Вправа 2 · потрібна база</GfEyebrow>

## Порахуйте виручку і звірте

<div class="grid grid-cols-3 gap-4" style="margin-top:1em">
<div class="card"><div class="kick green">1</div><p>Виручка по кожному товару в схемі <code>CO</code></p></div>
<div class="card hot"><div class="kick green">2</div><p><b>Звірте з вʼюхою</b> <code>CO.PRODUCT_ORDERS</code></p></div>
<div class="card"><div class="kick green">3</div><p>Не збіглося — знайдіть причину</p></div>
</div>

<div class="codeline" style="margin-top:1.2em">select * from co.product_orders order by total_sales desc;</div>

<div style="margin-top:1.2em;display:flex;align-items:center;gap:20px">
  <GfStat value="308 598,53" label="контрольне число — загальна виручка" accent="green" />
</div>

<div class="callout amber" style="margin-top:1em">Інше число? Спершу перевірте, звідки ви берете ціну</div>

<div class="day-jump-wrap" style="margin-top:.9em"><a href="https://koldovsky.github.io/claude-code-oracle-training/cheatsheet.html#s6" target="_blank">Запити й підказки — шпаргалка, розділ 6 →</a></div>

<!--
ЛИШАЄТЬСЯ НА ЕКРАНІ 12 хвилин.
Пастка: UNIT_PRICE є і в ORDER_ITEMS, і в PRODUCTS.
-->

---

<GfEyebrow>Пастка</GfEyebrow>

## `UNIT_PRICE` існує у двох таблицях

<div class="grid grid-cols-2 gap-5" style="margin-top:1.2em">

<div class="card hot">
<div class="kick green">oi.unit_price</div>
<p>скільки клієнт <b>заплатив</b></p>
<div style="margin-top:.8em"><GfStat value="308 598,53" accent="green" /></div>
</div>

<div class="card bad">
<div class="kick rose">p.unit_price</div>
<p>скільки товар коштує <b>зараз</b></p>
<div style="margin-top:.8em"><GfStat value="313 628,34" accent="plain" /></div>
</div>

</div>

<div class="lead" style="margin-top:1.2em">
Розбіжність <b>1,6%</b>. Запит виконується. Число правдоподібне.
<b>98% позицій</b> мають ціну, відмінну від поточної — помилка систематична.
</div>

---
layout: section
---

# Правдоподібне число —<br>найнебезпечніший вид<br>неправильного

<p>Інструмент дає швидкість. Правильність усе одно забезпечуєте ви.<br>
Єдиний спосіб — звірка з незалежним джерелом.</p>

---

<GfEyebrow>Домашнє завдання №1</GfEyebrow>

## Доведіть покращення, а не заявіть його

<div class="cmp c2" style="margin-top:1em">
  <div class="row head"><div class="c good">Приймається</div><div class="c bad">Не приймається</div></div>
  <div class="row"><div class="c">Логічні читання: з N до M</div><div class="c">«Помітно швидше»</div></div>
  <div class="row"><div class="c">План: full scan → index range scan</div><div class="c">«Додав індекс, має бути краще»</div></div>
  <div class="row"><div class="c">Показано, що результат не змінився</div><div class="c">Результат не перевірявся</div></div>
</div>

<div class="card warn" style="margin-top:1.3em">
<p>Плюс окремим пунктом: <b>які обʼєкти ви дали Claude і чому виключили решту.</b>
Оцінюється нарівні з рештою — саме це переноситься у Фазу 3.</p>
</div>

<!--
Чому не час: усі на спільній базі через _low.
Час залежить від сусідів, логічні читання — ні.
-->

---
layout: end
brand: Claude Code · Oracle · Claude Code для Oracle-розробки
---

# Сесія 2

<p>Як навчити інструмент <b>вашим</b> правилам:<br>
skills · subagents · hooks · spec-driven development</p>

<div class="day-jump-wrap flex gap-3 flex-wrap" style="margin-top:1.6em">
<a href="https://koldovsky.github.io/claude-code-oracle-training/cheatsheet.html" target="_blank">Шпаргалка →</a>
<a href="https://github.com/koldovsky/acordbank-oracle-training" target="_blank">Репозиторій →</a>
<a href="https://github.com/koldovsky/acordbank-oracle-training/blob/main/training/HANDOUT-SESSION-1.md" target="_blank">Робочий листок →</a>
</div>
