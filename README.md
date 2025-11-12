# Дипломная работа по профессии «Специалист по информационной безопасности»

## Тема диплома: Track Penetration Testing

### Студент: Зайцев Александр Юрьевич гр. SIB-46 2025г.

### Аннотация:  
 
Этот отчет содержит результаты проверки безопасности веб-сервиса 92.51.39.106. Проверка проводилась методом черного ящика по стандартным этапам: разведка, сканирование, поиск уязвимостей и составление отчета.
Были проверены два веб-приложения на портах 8050 и 7788. Обнаружены многочисленные критические уязвимости, такие как:
* SQL-инъекции и выполнение команд на сервере.
* Межсайтовый скриптинг (XSS).
* Возможность чтения системных файлов.
* Небезопасная загрузка файлов, позволившая выполнить код на сервере.
Каждая уязвимость подтверждена, оценена по степени риска и снабжена рекомендациями по исправлению. Отчет показывает серьезные пробелы в безопасности и служит основой для их устранения.

## Вводные данные:
### Задача
Нужно протестировать сервис на безопасность — провести полноценое тестирование на проникновение методом чёрного ящика. Известен только адрес тестируемого приложения — 92.51.39.106.

### Исходные данные
Требования к тестированию. Тестирование должно проходить в рамках пентеста приложения, поэтапно, без деструктивных действий в сторону сервисов и других тестеров. Рекомендуем использовать полезные материалы и open source инструменты, рассмотренные на курсе.


## Этап 1. OSINT
<details>
<summary> Критерии достижения: </summary>

* Собрано необходимое количество информации о сервисе, были использованы различные сервисы для получения инфомрации — Google, Shodan, CVE Details.
* Собранная информация систематизирована, имеет прямое отношение к тестируемому сервису, имеет ценность для тестирвоания.
* Полученная информация оценена и проанализирована.
</details>

На первом этапе использовали сервисы:
* www.shodan.io
* www.criminalip.io
* www.cvedetails.com
* www.google.com

Результаты сбора информации:

### Shodan.io:

GeneralInformation  

| Параметр | Значение |
|:-----------|:----------|
| Hostnames | 1427771-cg36175.tw1.ru |
| Domains | tw1.ru |
| Country | Russian Federation |
| City | Saint Petersburg |
| Organization | TimeWeb Ltd. |
| ISP | TimeWeb Ltd. |
| ASN | AS9123 |
| Operating System | Linux |

WebTechnologies  

| Параметр | Значение |
|:-----------|:----------|
| Operating systems | Ubuntu |
| Programming languages | PHP 5.5.9 |
| Web servers | Apache HTTP Server 2.4.7 |

OpenPorts  

| Параметр | Значение |
|:-----------|:----------|
| 22 | OpenSSH 8.2p1 Ubuntu 4ubuntu0.13 |
| 8050 | Apache/2.4.7 (Ubuntu) NetologyVulnApp.com |
| 10050 | |

Так же найдено множество уязвимостей на порту 8050

Vulnerabilities  

| Параметр | Значение |
|:-----------|:----------|
| Critical | 93 |
| High | 134 |
| Medium | 100 |
| Low | 7 |


[Выявленные уязвимости](./docs/shodan.md)  
[Скриншоты](./docs/shodanscreen.md)



### criminalip.io

Сервис сразу предупреждает:
* This is a malicious IP Address.
* This IP Address has critical vulnerabilities.

Connection  

| Параметр | Значение |
|:-----------|:----------|
| IP Address Owner | Jsc timeweb |
| Hostname | 1427771-cg36175.tw1.ru |
| Country | Russian Federation |

Current Open Ports  

| Параметр | Значение |
|:-----------|:----------|
| TCP 22 | OpenSSH 8.2p1 |
| TCP 8050 | Apache 2.4.7 NetologyVulnApp.com |

WHOIS  

| Параметр | Значение |
|:-----------|:----------|
| ASN | 9123 |
| AS Name | Jsc timeweb |
| Organization Name | TIMEWEB |
| Country Code | RU |
| Country | Russian Federation |
| Region | St.-Petersburg |
| City | St Petersburg |
| Postal Code | 195213 |

Security  

| Параметр | Значение |
|:-----------|:----------|
| Abuse Record | 0 |
| Open Ports | 2 |
| Vulnerabilities | 68 | 
| Exploit DB| 6 | 
| Policy Violation | 1 |
| Remote Address | True |
| Network Device | 0 |
| Admin Page | False |
| Invalid SSL | False |



