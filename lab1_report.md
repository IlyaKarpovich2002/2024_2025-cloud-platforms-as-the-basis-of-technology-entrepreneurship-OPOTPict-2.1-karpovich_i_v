Зайшли в вкладку IAM, создали service account с ролью Storage Admin
![скрин](https://github.com/user-attachments/assets/1204e10d-86d6-47ee-8d75-e06037021ddf)
Создал минимальный compute engine (виртуальную машину) с Machine type e2-micro в режиме spot.
![2025-04-21_19-25-53](https://github.com/user-attachments/assets/2b481d0a-6a7f-4ecd-adb0-c7e3ca95c9d5)
С помощью утилиты gsutils нашел бакет lab1-bucket-itmo и скопировал 3 файла в локальную папку на VM. Используя команду ls -lah отобразил, что эти файлы хранятся у вас на VM.
![2025-04-21_19-25-03](https://github.com/user-attachments/assets/f514f535-b2d2-4226-b30b-2f5978237dd9)
Поменял права доступа для вашего service account с Storage Admin на Compute Viewer, попробовал повторить пункт с копированием данных, сделал выводы - нет возможности подключиться к VM.
![2025-04-21_21-19-32](https://github.com/user-attachments/assets/5940d00e-4b47-413a-ace5-45b756d1ce76)
![2025-04-21_21-18-35](https://github.com/user-attachments/assets/b35a4084-7171-48c8-8be4-3400f8170799)
