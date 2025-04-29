University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Cloud platforms as the basis of technology entrepreneurship](https://) ADD link  
Year: 2024/2025  
Group: OPOTP  
Author: Karpovich ILya  
Lab: Lab4  
Date of create: 29.04.2025  
Date of finished: 29.04.2025  

# Проектирование инфраструктуры MVP AI-приложения с финансовыми расчетами

[Схема инфраструктуры](https://miro.com/welcomeonboard/RWpVcnNpeko5d1VwNkdVYThzTmFibFNIVlZRVUVzVWwvZmU0VCtiNkZqUWdUK2s0eWJicDVVRmV1R3VLT2pTNTAycVRCN0ZROVBTRUNSeVVOZHkxdmkrc1RoREtleXo1TWVEc2ZnWm5JZ0dubTJ3T0hoSWNiemxHT0NiSHZtc3RQdGo1ZEV3bUdPQWRZUHQzSGl6V2NBPT0hdjE=?share_link_id=632307119820)

## 1.Начальный этап (PoC)  
Инструменты:  
  
Frontend: Firebase Hosting (статичный сайт)  
Backend: Cloud Functions (Node.js/Python)  
AI-модель: Vertex AI Predictions (предобученные модели)  
База данных: Firestore (NoSQL)  
Хранение: Cloud Storage  
  
Финансовые расчеты:  
![image](https://github.com/user-attachments/assets/d68ee9f0-c41a-44fc-8916-7688df647af2)  
Схема:  
![image](https://github.com/user-attachments/assets/a431332a-fc0f-40f1-9f0c-1b8abdefed7f)  
  
Описание архитектеры  
Простая serverless-архитектура с минимальными компонентами. Пользователи обращаются к Cloud Run, который обрабатывает запросы и сохраняет данные в Firestore. Медиафайлы хранятся в Cloud Storage. Vertex AI интегрирован напрямую в Cloud Run для базовых предсказаний. Нет балансировщиков нагрузки и сложных систем мониторинга. Подходит для MVP с нагрузкой до 100 RPS.  
  
Обоснование выбора инструментов:  
Почему serverless? Минимальные затраты ($2.35/мес), нулевое администрирование.  
Firestore vs SQL: NoSQL достаточно для нереляционных данных MVP.  
Vertex AI Predictions: Дешевле кастомных моделей ($1.5 за 1K запросов).  
  
## 2.Тестирование партнерами  
Инструменты:  
  
Frontend: Load Balancer + Compute Engine (Nginx)  
Backend: Cloud Run (Go/Python)  
AI-модель: Custom Container на AI Platform  
База данных: Cloud SQL (PostgreSQL)  
Кеширование: Memorystore (Redis)  
  
Финансовые расчеты:  
![image](https://github.com/user-attachments/assets/8b8d27f6-44bb-4073-a3fa-71e61dca1808)  
Схема:  
![image](https://github.com/user-attachments/assets/1620dca5-4824-4369-92fa-e3af3c6e1400)  
  
Описание архитектеры  
Масштабируемая архитектура с балансировщиком нагрузки и разделением сервисов. Compute Engine обслуживает фронтенд, Cloud Run — бекенд-API. Cloud SQL заменяет Firestore для сложных запросов, Memorystore кеширует данные. AI Platform использует кастомные модели. Позволяет обрабатывать до 1,000 RPS с ручным масштабированием.  
  
Обоснование выбора инструментов:  
Cloud Run + GCE: Баланс цены и производительности. Cloud Run дешевле Kubernetes на малых нагрузках.  
Memorystore: Ускоряет запросы к AI-моделям (снижает latency на 40%).  
Cloud SQL: Подходит для структурированных данных партнеров.  
  
## 3.Продовое решение  
  
Инструменты:  
Frontend: Global Load Balancer + CDN  
Backend: GKE Autopilot (Kubernetes)  
AI-модель: Vertex AI Custom Training + TPU  
База данных: Cloud Spanner (горизонтальное масштабирование)  
Мониторинг: Cloud Monitoring + Logging  
  
Финансовые расчеты:  
![image](https://github.com/user-attachments/assets/a4582c4d-1355-42fb-a371-735f01b72abc)  
Схема:  
![image](https://github.com/user-attachments/assets/62e46830-b360-478e-9786-f2ffcdfeb496) 
  
Описание архитектеры  
Глобально распределённая отказоустойчивая система. GKE Autopilot автоматически масштабирует кластер под нагрузку. Cloud Spanner обеспечивает транзакции между регионами. Vertex AI с TPU ускоряет инференс в 5 раз. Pub/Sub обрабатывает асинхронные задачи. Поддерживает 10,000+ RPS с SLA 99.95%.  
  
Обоснование выбора инструментов:  
GKE Autopilot: Автоматическое масштабирование (+ экономия 20% vs ручной GKE).  
Cloud Spanner: Глобальная репликация для отказоустойчивости.  
TPU: Ускоряет инференс в 5x по сравнению с GPU.  
