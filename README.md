# Домашнее задание к занятию 9.02. "`Система мониторинга Zabbix`" - `Емельянов Михаил`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1 

Установите Zabbix Server с веб-интерфейсом.

#### Процесс выполнения
1. Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
2. Установите PostgreSQL. Для установки достаточна та версия что есть в системном репозитороии Debian 11
3. Пользуясь конфигуратором комманд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache
4. Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server

#### Требования к результаты 
1. Прикрепите в файл README.md скриншот авторизации в админке
2. Приложите в файл README.md текст использованных команд в GitHub

#### Ответ:
![Скриншот-1](https://github.com/Monooks/syshomework_9.02/blob/main/img/9.02_1.png)
1. sudo apt update
2. sudo apt install postgresql
3. systemctl status postgresql
4. wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
5. sudo dpkg -i zabbix-release_6.0-4+debian11_all.deb
6. sudo apt update
7. sudo apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
8. systemctl status zabbix-server.service
9. sudo -u postgres createuser --pwprompt zabbix
10. sudo -u postgres createdb -O zabbix zabbix
11. zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
12. sudo nano /etc/zabbix/zabbix_server.conf
13. sudo systemctl restart zabbix-server apache2 # zabbix-agent
14. sudo systemctl enable zabbix-server apache2 # zabbix-agent
---

### Задание 2 со звёздочкой*
*Это дополнительное задание. Его можно не выполнять. Это не повлияет на зачёт. Вы можете его выполнить, если хотите глубже разобраться в материале.*

С помощью Yandex Monitoring сделайте 2 алерта на загрузку процессора: WARN и ALARM. Создайте уведомление по e-mail.

#### Требования к результату
* прикрепите в файл README.md скриншот уведомления в Yandex Monitoring 
![Скриншот-2](https://github.com/Monooks/syshomework901/blob/main/img/2.png)
![Скриншот-3](https://github.com/Monooks/syshomework901/blob/main/img/2_1.png)
## Критерии оценки

1. Выполнено минимум обязательное задание
2. Прикреплен (ы) скриншот(ы) 
3. Задание оформлено в шаблоне с решением и опубликовано на GitHub
