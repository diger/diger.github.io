---
layout: help
title: Help/Manuals
---

### Установка

Переходим в папку с модулями установленного биллинга и тащим гитом ветку с Nms:
<pre>
  cd /usr/abills/Abills/modules/
  git clone https://github.com/diger/Nms.git
</pre>
Создаем симлинк для поллера в папку libexec:
<pre>
cd /usr/abills/libexec/
ln -s ../Abills/modules/Nms/nms_poll 
</pre>
Если будем ловить snmp трапы:
<pre>
ln -s ../Abills/modules/Nms/gettrap .
</pre>

###Активируем модуль

Открываем файл */usr/abills/libexec/config.pl*, находим массив @MODULES.  
Добавляем название модуля(Nms) в список.  
Теперь нужно разрешить доступ к модулю [определенным пользователям](http://abills.net.ua/wiki/doku.php/abills:docs:manual:admin:form_admins)

### Выставляем переменные

Добавляем в файл */usr/abills/libexec/config.pl* нужные переменные:  

<div markdown="1" class="uk-table uk-table-justify">
| Переменная            | Описание / Пример                           |
|---|---|
| $conf{NMS_NET}            | **Сеть для мониторинга/управления**  $conf{NMS_NET}='10.0.0.0/24';      |
| $conf{NMS_COMMUNITY_RO}   | **Используемый по-умолчанию community**  $conf{NMS_COMMUNITY_RO}='public';  |
| $conf{NMS_COMMUNITY_RW}   | **Используемый по-умолчанию community(RW)**  $conf{NMS_COMMUNITY_RW}='private'; |
| $conf{GETTRAP_IP}         | **IP адрес, на котором ловим трапы**  $conf{GETTRAP_IP}='10.0.0.1';      |
| $conf{TRAPS_CLEAN_PERIOD} | **Период для очистки истории трапов**  $conf{TRAPS_CLEAN_PERIOD}='10'     |
| $conf{GETTRAP_ALERT_ADDR} | **Список оповещения**  $conf{GETTRAP_ALERT_ADDR}='adm@name.org'; |
| $conf{REDIS_SERV}         | **Адрес сервера с** [Redis](https://redis.io/)  $conf{REDIS_SERV}='10.0.0.2:6379'; |
</div>

