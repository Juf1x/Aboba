Для того, чтобы начать выполнять задания на Oracle Linux, в виртуальной машине нужно выставить некоторые характеристики: 
2 ядра, 4096 МБ ОЗУ и при самой установке нашей операционной системы нужно выбрать Английский язык (потому что с другими могут быть беды)

После установки Oracle Linux для полного комфорта пользования нужно накатить так называемые Guest Additions (в простонародье Гостевые дополнения)

Гостевые дополнения Linux. Подобно гостевым дополнениям Windows, гостевые дополнения VirtualBox для Linux являются набором драйверов устройств и системных программ которые можно установлены в гостевой операционной системе.

Первыми командами стали установка: wget

wget — это утилита командной строки для загрузки файлов с веб-серверов.

![image](https://github.com/user-attachments/assets/ca80e968-5de1-4309-96f4-726c7dcc8915)

и сам curl

curl — это утилита командной строки для передачи данных с или на сервер, поддерживающая множество протоколов, включая HTTP, HTTPS, FTP и другие.
![image](https://github.com/user-attachments/assets/bdd182fb-d4f2-4c59-ae4c-fe30fb48b854)

Установка файла репозитория Docker CE для CentOS
![image](https://github.com/user-attachments/assets/b4f66934-8a89-4d90-831e-9fd762242c31)

-P /etc/yum.repos.d/ — Указывает директорию, в которую будет сохранён загруженный файл.

Команда была выполнена, и файл Docker CE был загружен и сохранён в указанную директорию. Он необходим для настройки репозитория Docker, что позволит yum устанавливать пакеты Docker CE на нашу систему.

Установка и настройку необходимых пакетов для работы с Docker
![image](https://github.com/user-attachments/assets/50b88a16-3f28-48cf-8010-ebdf160ce6d1)

docker-ce — Основной пакет Docker Community Edition. docker-ce-cli — Командная строка Docker для управления Docker. containerd.io — Контейнерный рантайм, используемый Docker.

Эта команда позволяет использовать Docker для создания и управления контейнерами на системе.


![image](https://github.com/user-attachments/assets/50b88a16-3f28-48cf-8010-ebdf160ce6d1)


