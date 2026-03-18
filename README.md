# Задача: Команды управления процессами
# Роман Салий

1. Отправка сигналов процессу топ.
   - kill -STOP, kill -CONT, kill -KILL



2. Установка nginx, вывод процессов nginx(ppid, pid, command).
   - sudo systemctl status nginx
   - ps -ef | grep nginx  



3. Вывод процессов nginx в виде дерева через htop
   - filter -nginx --> f4
   - tree --> f5



4. Убийство nginx master 




5. Перезапуск сервиса nginx
   - sudo systemctl start nginx


6. Убийство воркеров приводит к их перезапуску



7. Запуск sleep, остановка, jobs, bg, fg





