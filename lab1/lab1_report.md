University: [ITMO University](https://itmo.ru/ru/)
Faculty: [FICT](https://fict.itmo.ru)
Course: [Cloud platforms as the basis of technology entrepreneurship](https://) ADD link
Year: 2025/2026
Group: OPOTPICT2-1
Author: Karpovich Ilya
Lab: Lab1
Date of create: 21.04.2025
Date of finished: 21.04.2025

Зашли в вкладку IAM, создали service account с ролью Storage Admin
![2025-04-21_19-26-13](https://github.com/user-attachments/assets/8542902f-8aa6-43d1-bdf9-fd607fb59fed)
Создал минимальный compute engine (виртуальную машину) с Machine type e2-micro в режиме spot.
![2025-04-21_19-25-53](https://github.com/user-attachments/assets/2b481d0a-6a7f-4ecd-adb0-c7e3ca95c9d5)
С помощью утилиты gsutils нашел бакет lab1-bucket-itmo и скопировал 3 файла в локальную папку на VM. Используя команду ls -lah отобразил, что эти файлы хранятся у вас на VM.
![2025-04-21_19-25-03](https://github.com/user-attachments/assets/f514f535-b2d2-4226-b30b-2f5978237dd9)
Поменял права доступа для вашего service account с Storage Admin на Compute Viewer, попробовал повторить пункт с копированием данных, сделал выводы - нет возможности подключиться к VM.
![2025-04-21_21-19-32](https://github.com/user-attachments/assets/5940d00e-4b47-413a-ace5-45b756d1ce76)
![2025-04-21_21-18-35](https://github.com/user-attachments/assets/b35a4084-7171-48c8-8be4-3400f8170799)
