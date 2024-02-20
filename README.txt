В этой сборке, предусмотрена возможность запуска:
    - Farm-Proxy для прокисрования трафика,
    - Prometheus для агрегиции метрик,
    - NodeExporter для сбора и отправки метрик в Promethes,
    - Grafana для отрисовывания графиков,
    - Аlertmanager для оповещения в случае каких-либо событий.

Настройки для Alertmanager находятся в файле monitoring/alertmanager/config.yml 
Настройки для Promethes находятся в файлах monitoring/prometheus/alert.rules и monitoring/prometheus/prometheus.yml 
Настройки для Farm-Proxy находятся в файлах configs/farm-proxy.json и configs/proxy_ports.json 
Логи работы Farm-Proxy так будут находится в папке configs/log

Для запуска Farm-Proxy необходимо из корневого каталога проекта выполнить команду:
     docker compose up -d 
     