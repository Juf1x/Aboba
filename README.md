Для того, чтобы начать выполнять задания на Oracle Linux, в виртуальной машине нужно выставить некоторые характеристики: 
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

Заходим в браузер по адресу localhost:3000 и вводим логин (Admin) и пароль (Admin)

![image](https://github.com/user-attachments/assets/ad6f761c-5b60-4c2b-a876-db7b296c7855)









