В этой сборке, предусмотрена возможность запуска:
    - Farm-Proxy для прокисрования трафика,
    - Prometheus для агрегиции метрик,
    - NodeExporter для сбора и отправки метрик в Promethes,
    - Grafana для отрисовывания графиков,

Настройки для Promethes находятся в файлах monitoring/prometheus/alert.rules и monitoring/prometheus/prometheus.yml 
Настройки для Farm-Proxy находятся в файлах configs/farm-proxy.json и configs/proxy_ports.json 
Взависимости от ОС, в файле docker-compose.yml, в разделе volume, для ОС windows, необходимо заменить ./configs на .\configs
Логи работы Farm-Proxy так будут находится в папке configs/log

Для запуска Farm-Proxy необходимо из корневого каталога проекта выполнить команду:
     docker compose up -d 
     