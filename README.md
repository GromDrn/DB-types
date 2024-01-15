# Домашнее задание к занятию "`Базы данных, их типы`" - `Громов Андрей`

---

### Задание 1

Кейс

Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для каждой предметной области.

Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему?

1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков. СУБД должна гарантировать целостность и чёткую структуру данных.

1.1.* Хеширование стало занимать длительно время, какое API можно использовать для ускорения работы?

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? СУБД должны быть гибкими и быстрыми.

1.2.* Можно ли эту задачу закрыть одной СУБД? И если да, то какой именно СУБД и какой реализацией?

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.

1.3.* Можно ли под эту задачу использовать уже существующую СУБД из задач выше и если да, то как лучше это реализовать?

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать со связями.

1.4.* Можно ли к этой СУБД подключить отдел закупок или для них лучше сформировать свою СУБД в связке с СУБД логистов?

1.5.* Можно ли все перечисленные выше задачи решить, используя одну СУБД? Если да, то какую именно?

---

### Решение 1

---

1.1 Лучше всего подойдет реляционная СУБД (например PostgreSQL) т.к. обеспечивает целостность данных и имеет ясную струтуру, позволяя эффективно использовать функции аналитики и прогнозирования.

1.1.* Redis/Memcached

1.2. Гибкая и быстрая NoSQL СУБД типа MongoDB, позволяющая эффективно работать с гибкой структурой данных и масштабировать систему

1.2.* Можно, например исплдьзуя MongoDB, которая позволяет хранить как лендинговые страницы, так и CRM в одной БД.

1.3. Реляционная СУБД типа PostgreSQL или MySQL.

1.3.* Можно из п. 1.1 создав отдельные таблицы или схемы в существующей СУБД.

1.4. Подойдет графовая СУБД, которая хорошо работает с данными, связанными между собой.

1.4.* Думаю стоит создать отдельную СУБД, чтобы она имела свою структуру данных и могла эффективно выполнять свои задачи, так же, при необходимости, можно установить связь с СУБД логистики для обмена определенными данными.

1.5.* Да, например PostgreSQL, который обладает гибкой структурой и поддерживает различные типы данных, а так же обеспечивает возможность работы с данными связями и выполнение сложных запросов.

---

### Задание 2

2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы транзакция завершилась успешно. Ориентируйтесь на шесть действий.

2.1.* Какие действия должны произойти, если пополнение счёта телефона происходило бы через автоплатёж?

---

### Решение 2

2.1.
    1. Аутентификация
    2. Проверка баланса
    3. Резервирование средств
    4. Передача запроса на пополнение
    5. Обработка запроса проваедером
    6. Обновление баланса

2.1.*
    1. Аутентификация
    2. Резервирование средств
    3. Планирование платежа
    4. Исполнение платежа
    5. Обновление баланса

---

### Задание 3

3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL.

3.1.* Какие, на ваш взгляд, преимущества у NewSQL систем перед SQL и NoSQL.

---

### Решение 3

3.1.
    1. Структурированный формат данных
    2. Жесткая схема данных
    3. Поддержка SQL запросов
    4. Транзакции
    5. Масштабируемость

3.1.*
    1. Горизонтальная масштабируемость
    2. Высокая производительность
    3. Гибкость схемы данных
    4. ACID СОВМЕСТИМОСТЬ

---

### Задание 4

Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу выделено 1000 машин.

На основе какого критерия будете выбирать тип СУБД и какая модель распределённых вычислений здесь справится лучше всего и почему?

---

### Решение 4

Для выбора типа СУБД и модели распределённых вычислений можно использовать следующий критерий:

Тип СУБД:
    Реляционная СУБД: подходит, если данные имеют простую структуру и требуют выполнения сложных запросов. Например, если необходимо производить много агрегаций, соединений или группировок данных.
    NoSQL СУБД: подходит, если данные имеют сложную или гибкую структуру, и требуют горизонтального масштабирования. Например, если данные представляют собой документы, графы или временные ряды.

Модель распределённых вычислений:
    Shared-nothing: в этой модели каждая машина выполняет вычисления и хранит свою собственную часть данных. Подходит для масштабируемых вычислений, где данные могут быть разделены на независимые части.
    Shared-disk: в этой модели машины имеют общий доступ к данным, которые хранятся на общих дисках. Подходит, когда данные не могут быть разделены на независимые части или требуют совместного доступа.
    Shared-memory: в этой модели машины имеют общий доступ как к данным, так и к памяти. Подходит для вычислений, требующих высокой скорости обмена данными и общего доступа к памяти.
    
В данном случае, учитывая большое количество вычислений и огромное количество данных, лучшим выбором может быть комбинация NoSQL СУБД и модели распределённых вычислений Shared-nothing. NoSQL СУБД, такие как Apache Cassandra или Apache HBase, обеспечивают горизонтальное масштабирование и гибкую структуру данных, что может быть полезно при обработке большого объема данных.

Модель распределённых вычислений Shared-nothing позволяет каждой машине обрабатывать свою часть данных независимо от других машин. Это обеспечивает высокую масштабируемость и параллелизм вычислений, что может быть полезно при выполнении больших объемов работы. Кроме того, такая модель позволяет эффективно использовать ресурсы каждой машины и обеспечить более высокую отказоустойчивость системы.

Однако, выбор конкретной СУБД и модели распределённых вычислений должен быть основан на уникальных требованиях и особенностях задачи, а также на доступных ресурсах и экономических ограничениях.