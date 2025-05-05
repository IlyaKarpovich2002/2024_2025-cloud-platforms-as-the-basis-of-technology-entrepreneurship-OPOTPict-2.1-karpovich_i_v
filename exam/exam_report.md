University: ITMO University  
Faculty: FICT  
Course: Cloud platforms as the basis of technology entrepreneurship ADD link  
Year: 2024/2025  
Group: OPOTP  
Author: Karpovich ILya  
Lab: Exam  
Date of create: 05.05.2025  
Date of finished: 05.05.2025  
  
# Билет №2  
![2025-05-05_18-08-59](https://github.com/user-attachments/assets/c2617e0b-3da0-4545-a225-99944841b709)  
  
## 1. Инструменты  
Фронтенд: Cloud CDN + Cloud Storage (хостинг React)  
Бэкенд: Cloud Run (Django в контейнерах)  
База данных: Cloud SQL (PostgreSQL)  
Медиа: Cloud Storage (PDF) + Live Stream API (видео)  
Безопасность: Cloud Armor (WAF) + Secret Manager  
CI/CD: Cloud Build + Artifact Registry  
Мониторинг: Cloud Monitoring + Logging  
  
## 2. Обоснование выбора инструментов  
Cloud Run вместо Kubernetes - Автомасштабирование без управления кластером (экономия на DevOps).Поддержка Django из коробки.  
Cloud SQL: Полностью управляемая PostgreSQL с репликами для чтения.
Live Stream API: Низкая задержка (HLS/DASH) + адаптация качества под сеть пользователя.  
Cloud CDN: Кеширование статики (React, PDF) у edge-узлов.  
Cloud Armor: Защита от DDoS и SQL-инъекций (критично для данных студентов).  
  
## 3. Описание архитектуры
Пользователи подключаются через Global Load Balancer, который распределяет трафик между ближайшими edge-узлами CDN.  
Статичный фронтенд (React) хранится в Cloud Storage и раздается через Cloud CDN (кеширование в 200+ локациях).  
Динамические запросы идут в Cloud Run (Django), который масштабируется от 0 до N экземпляров под нагрузку.  
Данные курсов и пользователей хранятся в Cloud SQL с автоматическими бэкапами.  
PDF-материалы загружаются в Cloud Storage с доступом через CDN.  
Видео транслируются через Live Stream API с адаптацией битрейта (поддерживает 4K/HDR).  
Cloud Build автоматически деплоит новые версии кода из Git в Artifact Registry → Cloud Run.  
Cloud Armor фильтрует трафик, блокируя атаки.  
Secret Manager хранит API-ключи и пароли.  
Cloud Monitoring алертит о проблемах (падение RPS >5%, 5xx ошибки).  

## 4. Финансовые расчеты
![2025-05-05_18-16-01](https://github.com/user-attachments/assets/34a164c8-8942-4943-8801-475afca267ab)  
Примечание: Цены актуальны для региона europe-west3. Для 50K пользователей в месяц.

## 5.Итоги
Решение решает все проблемы EduTech:  
  
Масштабируемость: Cloud Run + CDN выдерживают пиковые нагрузки.  
Надежность: SLA 99.95% у всех компонентов.  
Безопасность: Шифрование данных + WAF.  
Простота: Полностью управляемые сервисы (минимальный DevOps).  
  
![Ai приложение - Frame 1](https://github.com/user-attachments/assets/70fddeac-a54e-4882-8c01-49a0aeaad0e8)

