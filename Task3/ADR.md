### []()**Название задачи:**

### []()**Автор:Куликов Алексей**

### []()**Дата:20/07/2025**

### []()**Функциональные требования**

Опишите здесь верхнеуровневые Use Cases. Их нужно оформить в виде таблицы с пошаговым описанием:

**№** | **Действующие лица или системы** | **Use Case**                      | **Описание**
:---: | :------------------------------- | :-------------------------------- | :--------------------------------------------------------------------------------------
  1   | Клиент сайта                     | Просмотр депозитов, подача заявки | Сайт отображает список депозитов, клиент подаёт заявку, оставляя контактные данные.
  2   | Менеджер кол-центра              | Обработка заявки с сайта          | Получает заявку, связывается с клиентом, вносит данные в CRM/систему кол-центра.
  3   | Клиент интернет-банка            | Открытие депозита онлайн          | Клиент выбирает депозит, вводит сумму и счёт списания, подтверждает операцию СМС-кодом.
  4   | Бэк-офис депозитов               | Обработка заявок                  | Менеджер подтверждает заявку в АБС, открывает депозит.
  5   | АБС                              | Хранение и учёт депозитов         | Регистрация депозита и его параметров в основной системе учёта.
  6   | Фронт-офис                       | Подтверждение личности            | Сотрудник фронт-офиса подтверждает личность нового клиента, вносит информацию в АБС.
  7   | СМС-шлюз                         | Отправка уведомлений              | Система отправляет СМС-коды и подтверждения клиентам.

### []()**Нефункциональные требования**

Опишите здесь нефункциональные требования и архитектурно значимые требования.

**№** | **Требование**
:---: | :------------------------------------------------------------------------
  1   | Доступность 99.9% сервисов интернет-банка и подачи заявок
  2   | Минимальная задержка интерфейсов
  3   | Защита данных при передаче и хранении (TLS, HTTPS, шифрование)
  4   | Использование существующих технологий (MS SQL, Oracle, .NET, Java, React)
  5   | Отказоустойчивость: развертывание в 2 ЦОД, автоматическое переключение
  6   | Горизонтальное масштабирование интернет-банка и фронтов

### []()**Решение**

- Новый микросервис формирует заявки, хранит их БД АБС
- При подтверждении заявки оператором в АБС отправляется команда на открытие депозита.
- API микросервиса разрабатывается командой интернет-банка.
- Все данные между компонентами передаются по HTTPS.
- Новый микросервис позволит маштабировать систему подачи заявок при увеличении нагрузки

[Context C4](https://www.plantuml.com/plantuml/uml/bLJHJXD157tdArQUCA7qnIUVYCJueWcH-4o6PG8RTxTaPrRWZHO53IhoPWmH-mVJXbeeK7xXpXzvxkvGTiAYc1G2C_UUS-wvPpgljCXqdiHJZw8qZFDLcMTniAxrXdhQR6PYSsujqklvIgva5hPIBLCz5xQIvaOiKcvhABqQHolDXIUDHJvwy-fbCn5Aomn7omlSiQNdDfXWQb5cgfNEXBdIhKHciy4q_Q0BEgC1NTdEDFz_GcEwi9zfQ7TfO3ksRGy3soP3vxQ3gyk0pl3XSbplq1KNDQX71d-Ek63wyGrD8bAnLh8SCmD-JkatjmNKirzerA2nVKzd3C_Sw9nQseRoP4Q9MAgbI4jkxfRimOIbgAQVXQ0UH1X6nGtc240ne6jS307C1NrM38eUo40y96CFgO-B4VWSNPJ2hbJgPo9zoz3VxvcluFr5Xi5GO80RW0o581YZmh1tQ3wWI_R9rsBuS4Aw_7nBpuGYZXUmKRSBzhvXzyfrs9roJ3SY9E3i0D8DQxgTP5JCTxiaurEeHBqGMcwAxTBBO-esx4Ve_4h3YO_N1KKVfuSbkAlRnHcsndkbYz9Zv06Kaz3mLBT6YXN5aD_eYBeEl8qcRA7uVHxONRjlZy1GloUE0zi8v3QVsGFx8Q1nwJ7ctSFrUIKdIHHcBJoCTr4eYvpXVeJACTgvey_f2WgUKxJlWy9Bm8CD1kxmBxatBDwf71HKF2DcSbP0yMiPLnwU5_0Jf_YInhps6czcgsfumJwQbzyQmFgCmbhRvWsMPinMVJBU-7S8_TnsMIetthn1zopjfo8oRcK5H6Lk7-F4zwwEljg0e3tySUmxx64rIl2LNQA-GvzyMm7wxZF7XwF4ssTNAnFvtlk1h7zSDQFvRL3mBqiuRooEquvDTkxvxWDy3Rx_bV3Vxn-Wyp9TpPFu3m00)

[Container C4](https://www.plantuml.com/plantuml/uml/jLRVJoDL57xlNp7YWn1R-kAJJmjTT3U1ROMk6v_8j0moElsHcQcuCIPBgwu9keWnqHW34lLzjakXb0B_mfd_oE_ieJVtNgQmFlX0cDwPUxxlVkSxvznxKUo6SQSHvDxoc_MWi-5rmi3PYkDsz7wn6BhRyv_wyLQdrecyiDvgnbupdg-t6iLsu3PvMo6ADmA_LYozLwZmqkELvMB3ZM8lnD9w2JjSl-c5yss6o2qlV59-N5slbYlhzyjF7itEvN8LBunQpTbwu2Fq4w-MTsReTpgd8Gte8kqwwGubT9PsAPdXLuTqYPK1VW_nDw3pz0Vj4uTUul62HlXwpWpzSD6EZ0VyGwnds8681RLPe7wb1Ay6z0fGEsaNpqFyNLAVlyBMNJfpw0eBu42dya9noYAo6KAEykQcN_Su_jySZIaKSAPl68HXwGY_09Rsw1W1XWWnTAZly2fM49tfu-kzzDjCb9fR_ro1q7xw8uqKW4CSWJcVidxCUIecNhu4mmGOU2bBfpZX7lNnQgJfwmP12GfxORdjXMxS2Zda7qmJVyTqmX8xD6Ab2kbteZuYYye7e3FWNqm757RV03YtzXGEQwmljZhD3JTyEXlviJVvmK6Fn126FivNESTHXfpTzceVXAyDlO4TaqVBRgkUMu_dFuk4ALOdr4ua2JJ8KDG1OSYDmz2O4iLT3d8CT-mvs8iFqrrEuKXPKl8nPzDSH4A5fJpP92iFAiBFaYqnP6DM8ZKd1UlF-OCXC-WZe7WShyPfBojNeFNrJTtzcgxwRrFgwORsVgRqTzJZmbfb_j5IrLdvk3HZe47h0TJOaMAKevcMORqJArEi1mjbfnJP4PcWoINlut865EUA9Q94sT0yqaAxhGeEVnTqVDU9Ic-_GTxoml8Adm1PNX-XkexmeiyV0cJCvsOHc21MsPUinq-qJqSMqOPV3rjevbz8Wq0ab3k2IrjznhjlarBdFMb8eW-weHb2h9vPpRUd9jtDA-de5M-64uVOgCw4rzSg5DBl0VE2kF-ESTGibxgrIBCf8lGvxLoSF4QmrUZhp4qr3bx6gKQyQ5G9ICyAbpdRtenNUZrp6EqN6d00HgGhezfPnFjUqDxo-Od-58sW-83RofZtyIw6jRipMA75gFa1ES3OwFHSiJQf-ukCim-SKz4SHnHdCu5owDO3ptdNgImNrpvQvYNw1n3yaMfso44lVPxkfzsCniTMvTfH6JlBMoMZPMVforYR7B8ehLlJUDhKAAsk581qpXdKMgsu5ahjqJ4xLng_ZXWreW_TsDjssGcMWsGIQWus2q-pN0-_kOcoXsGSuwnc9q_4ZQjUe5zjpA53Xr9tp5tk5-n1RXGt2WBAgveKzTLKINjC_46rMba38W2r2uzlm1qegL2O6J3vYO3SGrY64xmNFb1J9iVfjGWMfdctqGj03ec0p5twBXv4f25xbKRYblI5QideHt1bDsk-9e8djnmRpkoc2Gkd5DN7S5w3cIgv06NURcpVwkNRdIYseqF23jA_jD5jnLUnLAKUcjFQlWM9kmnB6RU5rQMrghDGUJXpToo9f6ssMTaXzYr5PIBRBJlTczI0RaGPbMAVR7vMTqAs32rvPMWR0wlNvv3uIaPfPx0s-n2iW97sEFCpLjgG6msMndBlbhPeXZPdg7cG0zE_cMqIJFuBgWbtzxd-1nePFCnMUc3TKR9xfEeQB1U7VSUXds-zn6IEFdKFO5hQk5NQG9W2XnLn473NAKvJwY-PPxVDBcuPMVtX7lpSQGJ_0W00)

### []()**Альтернативы**

Вариант                                     | Описание                            | Причины отклонения
------------------------------------------- | ----------------------------------- | ---------------------------------------------------------------
Хранение ставок в отдельной системе         | Создать отдельный сервис ставок     | Усложнение архитектуры, ставки остаются ручным процессом на MVP
Использование Kafka для всех взаимодействий | Построение event-driven архитектуры | Отсутствие экспертизы, избыточно для MVP

**Недостатки, ограничения, риски**

- Ручная обработка ставок в бэк-офисе.
- Нагрузка на АБС при росте количества заявок, масштабируется только вертикально.
- Слабая отказоустойчивость сайта.
- Ограниченная компетенция в микросервисах внутри интернет-банка.
- Подрядчик контролирует обновления ядра интернет-банка.
