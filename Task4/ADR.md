### []()**Название задачи:**

### []()**Автор: Куликов Алексей**

### []()**Дата: 20/07/2025**

### []()**Функциональные требования**

Опишите здесь верхнеуровневые Use Cases. Их нужно оформить в виде таблицы с пошаговым описанием:

**№** | **Действующие лица или системы** | **Use Case**                   | **Описание**
:---: | :------------------------------- | :----------------------------- | :------------------------------------------------------------------------------------
  1   | Бэк-офис депозитов               | Актуализация ставок            | Вносит ставки в централизованное хранилище или обновляет Excel-файл.
  2   | Система кол-центра банка         | Получение актуальных ставок    | Получает доступ к текущим ставкам для отображения операторам.
  3   | Партнёрский кол-центр            | Получение файла со ставками    | Получает файл с актуальными ставками для загрузки в свою систему.
  4   | Менеджеры кол-центров            | Консультация клиентов          | Озвучивают ставки клиентам.
  5   | АБС                              | Формирование и отправка файлов | Ежедневно формирует и отправляет файл с актуальными ставками в партнёрский кол-центр.

### []()**Нефункциональные требования**

Опишите здесь нефункциональные требования и архитектурно значимые требования.

**№** | **Требование**
:---: | :----------------------------------------------------------------------------------------
  1   | Передача ставок сотрудникам кол-центра не реже одного раза в сутки.
  2   | Партнёрский кол-центр получает данные в виде XLS или CSV-файла автоматически.             |
  4   | Время доступа к ставкам внутри кол-центра банка -- не более 5 секунд.
  5   | Использование уже существующих технологий -- MS SQL, Oracle, минимизация изменений в АБС.
  6   | Защита персональных данных не требуется, ставки обезличены.

### []()**Решение**

[Context C4](https://www.plantuml.com/plantuml/uml/bLH1Rn916BttLuoSsaJWuibJbTJ4f8rOzDmiCBN4PNSpEnjfZ0c5MZNLLFHWqeE6Yrwnkf52WRymyuzytp3ONM5DFEravhttlUzzCxiPIaV8gEcktMXuDJUgyqYux43A8BnTB0hdMU59Gnv4rIZaekPxadkoKFERnS1rFABbGrbt6zLYwLQ-J5kFTxQBJIUKN61hhqICbYm4L62jp4NeU-irjm6LcoodpjLO3LMi9hgZJvdwhWPgeaPgaDjOOFs02qVwWj2VrKp5kgq6kgEckis0dAfnNfzOXNQI6A0hZui7_-BFi6ph3iWzV8-CtWyrpH1UgnoYhURUNJ_oweuuNAywtjFv7gdtvkQPwaEHbZ_dwhaDzjnIrvrgID3t0FTpjFfwNS54yGk5BmnxWbNCz4jpDC4HZlKRsZeYVQ2cL6m6kwWKqmBieJcxWbjRiUQuRWbfSvD07m3G0RzIWvLj0bNQtSb3RamvwMDAYj3fwLXrVt-VYwrMu0jfv4sy5rI4wNTgX4Xdn2TJAT-czuzKrWxa19mpfeRCZYWswRqYsZ58bsfCmQGquEB5dvbijUHYugLKnr-MHZnKbykT6qCVZ9tNs3c36O0JOT7yTxcRk8_fP3_1renQ0Nz88uHIvzeloa810iltCiCs_Eak4h12DeLK0bPnyPoIJ-KSvnDWkr1v2uPDEEk-8FcaL-pyfRtaEhl4VzKmHP99ueMix3yP902LXzji_YROdVBznR9oxr7P6a_TJ2lwpLeXGNn667mNNzX78wSgNbLbMIvhOebxsykS690yt-GDbthVv5wT_ek_0G00)

[Containers C4](https://www.plantuml.com/plantuml/uml/nLH1Rn915BxpAqQyqAIm5q-UQcaFDQsYgF7M3CkatRZiajcbjZ4cG4qrKLDhF7beGw9tMa4fBSjVcFb7Vc-MRM4buIWG6Dw-zxtllU-zMGb2BiD6pStSSJpRRLH5GxfiDmphmNtBalnrOSS9TnkLHY2axNkXyCA2xTUikiiz2ii7OTLrAbRnNhv4fkTRcrQD1w6GC6qN4S4TJyX2dL9aIa86lfVpwqBoq9SRm9CUTvTPLfsgiUhhfkhgjefqawaBDTA7kWrJNutmxgjVAc9gg29rbTT7P3LFkraA_mxpIBVqeRhIdm0nq4sS-xfD4LTg4Bl3wO8X4N1wiE2W_i2rZMSVrJL3V5jraNc8x-liKffl2Qr2CNFfZd5i6gGJ_BQ8v_yZNF6tkCTtOgeT46mJEY1601uoTQu_gs4UzdS0QqqOVGLEf7hJe0D0ubK-WA2rxLM_uLMvFCXLkFSgjb7S2Pn7XDf171rxSIkoI-nDXZ5yRiOW9_RhlWpBGkuvja3mkldFjXnR-a5i9Ix5kykiy6ZzcU7rWngihgb3r0wJ0krXQe3EeAfpqovqG1_1vvYXgAwwX17EjyL4QaZ5f4lXbI0vKwulgAP3n6TOmsbj5OyVIswxWgtna5TuO9YMdsmQaZz9M3EbXbmwRmgjw3fO98hxfleqB4RfyOpq1BictFgkCr-TQ8wGaHc2jvcPVBPzgrM7t03GHp-xysOJaB6SyL0yv7kSMQpa1-6E54cnPnI6vNm_jznbfY9JpxdfoU_42URPfPdCBFWcigplXxbwl6J5eicKtYe0NVxBUzAX4T0_m79CKz2QBfNIF1Nkd9idwSxYke1X8DANGOhm0WZ2cDxFcsb8YvnAE-Ldnd61UshHaX0eoF9OcpJBXH2fCa_XFTRDvEvXBpVBLh7yOcRtI1IHhmd7dG0chPwgu0og7aEWY5JjgOXew4Ep2UdBRSBUOWzA6m1S4LwrKNF_0W00)

-Централизовать хранение ставок в отдельной таблице внутри АБС.

-Разработать сервис экспорта ставок в виде файлов (XLS/CSV), размещаемых на защищённом веб-сервере или передаваемых по SFTP.

-Интегрировать систему кол-центра банка с этим сервисом или напрямую с АБС для получения ставок.

-Партнёрский кол-центр получает файл ежедневно (или чаще) в ручном или автоматическом режиме по e-meil.

### []()**Альтернативы**

- Передавать ставки в партнёрский кол-центр через API - не поддерживается со стороны партнера.

**Недостатки, ограничения, риски**

- Партнер должен сохранить файл из письма и передать всем опрераторам - возможны задержки, пропуски писем и человеческий фактор
- Доработка системы Call-центра, не являющейся собственной разработкой - риски задержки сроков доработки

### []()**Список крупных задач**

Система               | Задача
--------------------- | --------------------------------------------------------
АБС                   | Добавить таблицу ставок, реализовать API / SQL-выдачу.
Сервис экспорта       | Разработать микросервис для генерации и передачи файлов.
Система кол-центра    | Реализовать загрузку ставок из АБС / отображение в CRM.
Партнёрский кол-центр | Организовать получение и обработку файлов.

[Roadmap](Roadmap.drawio.png)


