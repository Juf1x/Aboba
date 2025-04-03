![image](https://github.com/user-attachments/assets/859bcf7f-14f7-4261-9655-359fd4f12b97)

# Установка Docker'a

![image](https://github.com/user-attachments/assets/37efc11f-1936-403a-a721-f6bc8026d81e)Для того, чтобы начать выполнять задания на Oracle Linux, в виртуальной машине нужно выставить некоторые характеристики: 
2 ядра, 4096 МБ ОЗУ и при самой установке нашей операционной системы нужно выбрать Английский язык (потому что с другими могут быть беды)

После установки Oracle Linux для полного комфорта пользования нужно накатить так называемые Guest Additions (в простонародье Гостевые дополнения)

Гостевые дополнения Linux. Подобно гостевым дополнениям Windows, гостевые дополнения VirtualBox для Linux являются набором драйверов устройств и системных программ которые можно установлены в гостевой операционной системе.

Первыми командами стали установка: `wget`

`wget` — это утилита командной строки для загрузки файлов с веб-серверов.

![image](https://github.com/user-attachments/assets/ca80e968-5de1-4309-96f4-726c7dcc8915)

и сам `curl`

`curl` — это утилита командной строки для передачи данных с или на сервер, поддерживающая множество протоколов, включая HTTP, HTTPS, FTP и другие.

![image](https://github.com/user-attachments/assets/bdd182fb-d4f2-4c59-ae4c-fe30fb48b854)

Установка файла репозитория Docker CE для CentOS
![image](https://github.com/user-attachments/assets/b4f66934-8a89-4d90-831e-9fd762242c31)

`-P /etc/yum.repos.d/` — Указывает директорию, в которую будет сохранён загруженный файл.

Команда была выполнена, и файл Docker CE был загружен и сохранён в указанную директорию. Он необходим для настройки репозитория Docker, что позволит yum устанавливать пакеты Docker CE на нашу систему.

Установка и настройку необходимых пакетов для работы с Docker
![image](https://github.com/user-attachments/assets/50b88a16-3f28-48cf-8010-ebdf160ce6d1)

`docker-ce` — Основной пакет Docker Community Edition. `docker-ce-cli` — Командная строка Docker для управления Docker. `containerd.io` — Контейнерный рантайм, используемый Docker.

Эта команда позволяет использовать Docker для создания и управления контейнерами на системе.

Убедимся в наличие пакета curl

`COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)`

Скачиваем и устанавливаем последнюю версию Docker Compose с помощью команды 
`sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose`

Устанавливаем права на выполнение (делает файл исполняемым) 
`sudo chmod +x /usr/bin/docker-compose и проверяем установленную версию docker c помощью команды docker --version`

Проверка установленной версии Docker Compose
`docker-compose --version`

Клонируем репозиторий с github, где содержится Grafana с помощью команды 
`git clone https://github.com/skl256/grafana_stack_for_docker.git`

Переходим в директорию в Grafana с помощью команды `cd grafana_stack_for_docker`
и создаем директори с помощью команды `sudo mkdir -p /mnt/common_volume/swarm/grafana/config`

Все файлы и каталоги в указанных директориях будут переданы в собственность текущему пользователю и его группе
`sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}`

Файл grafana.ini уже существует, команда обновит его временные метки (время последнего доступа и изменения). Если файл не существует, команда создаст новый пустой файл с указанным именем по указанному пути.
`touch /mnt/common_volume/grafana/grafana-config/grafana.ini`

Копируем все файлы из директории config в `/mnt/common_volume/swarm/grafana/config/` c помощью команды `cp config/* /mnt/common_volume/swarm/grafana/config/`

Переименовываем файл `grafana.yaml` в `docker-compose.yaml` с помощью `mv grafana.yaml docker-compose.yaml`

Запускаем Docker Compose в фоновом режиме с помощью `sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/87fc6075-709c-4f5b-a781-7389310c7732)

Заходим в браузер по адресу `localhost:3000` и вводим логин (Admin) и пароль (Admin)

![image](https://github.com/user-attachments/assets/ad6f761c-5b60-4c2b-a876-db7b296c7855)

С помощью команды `cd grafana_stack_for_docker` переходим в данный файл и заходим в конфигурационный файл докера с помощью команды `vi docker-compose.yaml`

![image](https://github.com/user-attachments/assets/94d267e4-6e0d-4920-93cf-c485abd9160d)

Запускаем grafana с помощью `sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/e0916bad-4890-4964-a45e-e10e02f9beff)

Чтобы остановить grafana понадобится команда `sudo docker compose stop`

![image](https://github.com/user-attachments/assets/1b245bbc-9f4e-4031-9ba2-8481bc312ebb)

А чтобы полностью остановить grafana понадобится команда `sudo docker compose down`

![image](https://github.com/user-attachments/assets/d594e222-d05c-4b0d-89a2-c3c655b83071)

![image](https://github.com/user-attachments/assets/53b95e9d-07bb-4a05-8038-0c8bf402f5ae)

![image](https://github.com/user-attachments/assets/25573ab6-df55-4cfc-a176-b88668780d4b)

![image](https://github.com/user-attachments/assets/2f3f7f98-784d-4a18-a0fa-57e0f99deace)

![image](https://github.com/user-attachments/assets/28e821f2-0049-4148-8a98-37eb50923616)

![image](https://github.com/user-attachments/assets/e3470469-273f-49c2-aed3-cc2bad4436c9)


![image](https://github.com/user-attachments/assets/7da13f0f-385c-45c5-8c7a-40a874217525)

![image](https://github.com/user-attachments/assets/07f4dec4-4605-411b-a274-266012a435c6)

![image](https://github.com/user-attachments/assets/9b4aa78e-e5b3-4ceb-9206-9400a807f891)

![image](https://github.com/user-attachments/assets/8fde00bc-7182-40e4-8a2f-db645c96993f)

![image](https://github.com/user-attachments/assets/ebdaaf89-e29d-4470-bf78-4fff74cec0de)

![image](https://github.com/user-attachments/assets/0a7b1fd8-2ba4-42ad-aed7-b15c2dc46e9a)

![image](https://github.com/user-attachments/assets/71d0f228-c899-40f2-85d3-7e45df1da47a)

![image](https://github.com/user-attachments/assets/0180f155-9c4e-42ce-bd75-839f5d38c370)

![image](https://github.com/user-attachments/assets/c43b53c5-34e2-4fb3-92fe-2cfec471bc19)

![image](https://github.com/user-attachments/assets/86b052b5-8927-491f-a52c-a79adad408a5)

![image](https://github.com/user-attachments/assets/8677b740-a90a-4e50-9146-32176ef7866b)

![image](https://github.com/user-attachments/assets/4a1b05e8-15f7-4b41-91d9-252f78e00b8d)

![image](https://github.com/user-attachments/assets/0f1936b2-732e-4421-992d-2017fd770709)

![image](https://github.com/user-attachments/assets/21119a28-e827-40a3-bf25-e63429c96339)









