University: [ITMO University](https://itmo.ru/ru/)
Faculty: [FICT](https://fict.itmo.ru)
Course: [Cloud platforms as the basis of technology entrepreneurship](https://) ADD link
Year: 2024/2025
Group: OPOTP
Author: Karpovich ILya
Lab: Lab2
Date of create: 23.04.2025
Date of finished: 24.04.2025

Первое задание. Открыли Clour Run и создали Service с портом 8080
![2025-04-24_16-17-52](https://github.com/user-attachments/assets/68ae6075-9a2c-400f-a6df-46dfcff5a6a2)
Проверили что он запускается 
![2025-04-24_16-18-07](https://github.com/user-attachments/assets/01c4c455-4d80-4312-aa5a-4abe53d1872b)
Открыли раздел Логи 
![2025-04-24_16-18-34](https://github.com/user-attachments/assets/2b295d8c-5a06-4474-af51-2f2d8ce3a400)
Поменяли порт на 8090, сервер успено запустился
![2025-04-24_16-22-02](https://github.com/user-attachments/assets/eab5f24c-a8d6-4202-acd5-5fe67f971c9b)
Открыли раздел метрики и логи
![2025-04-24_16-22-26](https://github.com/user-attachments/assets/82549843-7620-4444-9cc4-2b296ec43fc2)
![2025-04-24_16-22-50](https://github.com/user-attachments/assets/96bffa22-d61f-490c-ba06-c594bab66194)

Выводы:
1. Анализ логов после изменения порта на 8090
Успешный старт контейнера на новом порту:

В логах зафиксировано сообщение:
2025/04/24 11:21:51 Hello from Cloud Run. The container started successfully and is listening for HTTP requests on port 8090.
Это подтверждает, что контейнер переключился на новый порт.

Проверка здоровья (TCP probe):

Запись:
Default STARTUP TCP probe succeeded after 1 attempt for container "hello-1" on port 8090.
Cloud Run успешно проверил доступность порта 8090.

Событие обновления сервиса:

В аудит-логах появилась запись:
Cloud Run ReplaceService hellokarpovicj-9990t-qfn... methodName: /Services.ReplaceService.
Это указывает на замену версии сервиса через Cloud Console.

2. Сравнение метрик при переключении трафика
Container Instance Count:
Во время обновления наблюдался всплеск до 2 активных экземпляров (старая и новая версии работали параллельно).
После завершения переключения количество вернулось к 0 (из-за настройки Min: 0).

Request Count:
До изменения порта: ~0.046 запросов/сек (стабильный трафик).
После изменения: падение до 0, так как порт 8999 не обрабатывал запросы (если образ слушал только 8080).

Request Latency:
Среднее время ответа: 26 мс для рабочей версии (порт 8080).
Для нерабочей версии (порт 8999) — ошибки Connection refused.

Resource Utilization:
CPU: ~1% (минимальная нагрузка для "Hello World").
Память: 10-20% от выделенного лимита (512 MiB).
Max Concurrent Requests: 2 запроса (пик во время переключения).
