# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Янин Семён Васильевич`


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

`Установите Zabbix Server с веб-интерфейсом.`

 `Версия Zabbix: 7.0 LTS`
 `ОС Ubuntu`
 `Версия 24.04`
 `БД: PostgreSQL`
 `Apache`

```
$ sudo apt update`
$ sudo apt install postgresql`
$ wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu24.04_all.deb`
$ sudo dpkg -i zabbix-release_latest_7.0+ubuntu24.04_all.deb`
$ sudo apt update`
$ sudo apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-apache-conf zabbix-sql-scripts`
$ sudo -u postgres createuser --pwprompt zabbix`
$ sudo -u postgres createdb -O zabbix zabbix`
$ sudo zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
$ systemctl restart zabbix-server apache2
$ systemctl enable zabbix-server apache2
$ systemctl status zabbix-server.service`
$ sudo nano /etc/apache2/ports.conf
$ sudo kill -9 $(sudo lsof -i :8080)
$ systemctl restart zabbix-server apache2
```

![Скриншот входа в Zabbix](img/zabbixlogin.png)

---

### Задание 2

`Установите Zabbix Agent на два хоста.`

```
$ sudo apt update
$ sudo apt install zabbix-agent
$ sudo nano /etc/zabbix/zabbix_agentd.conf
$ sudo systemctl restart zabbix-agent.service
$ systemctl status zabbix-agent.service
```

![Скриншот Hosts](img/zabbixhosts.png)
![Скриншот tail](img/zabbixtail.png)
![Скриншот Latest](img/zabbixlatest.png)

---
