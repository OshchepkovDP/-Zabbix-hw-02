# Домашнее задание к занятию "`#«Система мониторинга Zabbix» - Ощепков Дмитрий`"

В практике есть 2 основных и 1 дополнительное (со звездочкой) задания. Первые два нужно выполнять обязательно, третье - по желанию и его решение никак не повлияет на получение вами зачета по этому домашнему заданию, при этом вы сможете глубже и/или шире разобраться в материале.

Пожалуйста, присылайте на проверку всю задачу сразу. Любые вопросы по решению задач задавайте в чате учебной группы.

Цели задания
Научиться устанавливать Zabbix Server c веб-интерфейсом
Научиться устанавливать Zabbix Agent на хосты
Научиться устанавливать Zabbix Agent на компьютер и подключать его к серверу Zabbix
Чеклист готовности к домашнему заданию
 Просмотрите в личном кабинете занятие "Система мониторинга Zabbix"

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.
---

### Задание 1

Установите Zabbix Server с веб-интерфейсом.

Процесс выполнения
Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.
Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.
Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.
Требования к результатам
Прикрепите в файл README.md скриншот авторизации в админке.
Приложите в файл README.md текст использованных команд в GitHub.


1. `sudo -s`
2. `wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_6.0+ubuntu24.04_all.deb`
3. `dpkg -i zabbix-release_latest_6.0+ubuntu24.04_all.deb`
4. `apt update`
5. `apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent`
6. `sudo -u postgres createuser --pwprompt zabbix`
7. `sudo -u postgres createdb -O zabbix zabbix`
8. `zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix`
9. `DBPassword=123456789`
10. `systemctl restart zabbix-server zabbix-agent apache2`
11. `systemctl enable zabbix-server zabbix-agent apache2`
12. `systemctl status zabbix-server`

```
Поле для вставки кода...
....
....
....
....
....
```

При необходимости прикрепитe сюда скриншоты

![admin_zabbix](https://github.com/OshchepkovDP/-Zabbix-hw-02/blob/main/img/admin_zabbix.jpg)


---

### Задание 2 

Установите Zabbix Agent на два хоста.

Процесс выполнения
Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
Установите Zabbix Agent на 2 вирт.машины, одной из них может быть ваш Zabbix Server.
Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов.
Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera.
Проверьте, что в разделе Latest Data начали появляться данные с добавленных агентов.
Требования к результатам
Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
Приложите в файл README.md текст использованных команд в GitHub

1. `sudo -s`
2. `wget https://repo.zabbix.com/zabbix/7.4/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.4+ubuntu24.04_all.deb`
3. `dpkg -i zabbix-release_latest_7.4+ubuntu24.04_all.deb`
4. `apt update`
5. `apt install zabbix-agent`
6. `systemctl restart zabbix-agent`
7. `systemctl enable zabbix-agen`

```
Поле для вставки кода...
....
....
....
....
```

При необходимости прикрепитe сюда скриншоты

![zabbix_agent_online.jpg](https://github.com/OshchepkovDP/-Zabbix-hw-02/blob/main/img/zabbix_agent_online.jpg)
![zabbix_agent_log.jpg](https://github.com/OshchepkovDP/-Zabbix-hw-02/blob/main/img/zabbix_agent_log.jpg)
![latest-data.jpg](https://github.com/OshchepkovDP/-Zabbix-hw-02/blob/main/img/latest-data.jpg)
![graph.jpg](https://github.com/OshchepkovDP/-Zabbix-hw-02/blob/main/img/graph.jpg)

---

### Задание 3 со звёздочкой*

Установите Zabbix Agent на Windows (компьютер) и подключите его к серверу Zabbix.

Требования к результатам
Приложите в файл README.md скриншот раздела Latest Data, где видно свободное место на диске C:

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

При необходимости прикрепитe сюда скриншоты

![Disk_C_Size.jpg](https://github.com/OshchepkovDP/-Zabbix-hw-02/blob/main/img/Disk_C_Size.jpg)
