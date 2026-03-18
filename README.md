# Задача: Команды управления процессами
# Роман Салий

1. Отправка сигналов процессу топ

   `- kill -STOP, kill -CONT, kill -KILL`


<img width="1139" height="742" alt="image" src="https://github.com/user-attachments/assets/72b71122-cbdd-4522-82bd-58ce2402a01b" />



2. Установка `nginx`, вывод процессов `nginx(ppid, pid, command)`

   `- sudo systemctl status nginx`
   
   `- ps -ef | grep nginx`  


<img width="859" height="462" alt="image" src="https://github.com/user-attachments/assets/6f7e77e7-f021-4ad7-95c7-37145d1143aa" />


<img width="1031" height="223" alt="image" src="https://github.com/user-attachments/assets/7f54ecc3-ff75-4ff4-99db-247b29caa02b" />


3. Вывод процессов `nginx` в виде дерева через `htop`

   `- filter -nginx --> f4`

   `- tree --> f5`


<img width="1192" height="340" alt="image" src="https://github.com/user-attachments/assets/48850bc5-050b-480d-a079-602ca2a42a0d" />


4. Убийство `nginx master` 


<img width="1210" height="754" alt="image" src="https://github.com/user-attachments/assets/c77f6949-4a08-431c-a5d4-fd0b870f1eec" />


5. Перезапуск сервиса `nginx`

   `- sudo systemctl start nginx`


<img width="1210" height="754" alt="image" src="https://github.com/user-attachments/assets/1aa13688-e0c4-4b67-bdd6-52c0e43e5dc8" />


6. Убийство воркеров приводит к их перезапуску


<img width="1210" height="754" alt="image" src="https://github.com/user-attachments/assets/30964eca-8ff3-4587-a5f5-032fa010f043" />


7. Запуск `sleep`, остановка, `jobs, bg, fg`


<img width="1045" height="552" alt="image" src="https://github.com/user-attachments/assets/0e1b9a47-cc62-4f0e-b665-c7aae8c81ce6" />




# Задача: Установить Redis и запустить второй экземпляр.

1. Установил redis



2. Что я сделал исследовал где находятся файлы redis и начал создавать рядом их копии в этих же директориях
 
   - sudo mkdir /etc/redis-secondary

   - sudo mkdir /var/lib/redis-secondary

   - sudo mkdir /var/log/redis-secondaty

   - sudo mkdir /run/redis-secondary
 
   - Скопировал конфиг /etc/redis/redis.conf в /etc/redis-secondary/redis.conf ---> единственное что нужно поменять это порт(обязательнео еще раз проверить права)
 
   - Далее используем chown redis:redis на каждую созданную директорию и файл

   - sudo journalctl -u redis-secondary -n 50 --no-pager --> Использовал для поиска ошибок(сам нарвался на недостаток прав)

   - Далее создаем unit файл /etc/systemd/system/redis-secondary.service и заполняем скриншот ниже(можно еще убрать restart чтоб экземляр не вставал сам)

   - Делаем копию ppid файл из /run/redis в /run/redis-secondary


3. Скриншот обоих экземпляров



