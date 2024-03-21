# Farm-Proxy

В этой сборке, предусмотрена возможность запуска:  
- **Farm-Proxy** ![](docs/images/vnish.net_icon.15.png) для прокисрования трафика  
- **Prometheus** ![](docs/images/prometheus.15.png) для агрегации метрик  
- **NodeExporter** ![](docs/images/prometheus.255x256.png) для сбора и отправки метрик в Prometheus  
- **Grafana** ![](docs/images/grafana.15.png) для отрисовывания графиков  

---
# Требования к системе
### Рекомендуемые устройства (предпочтительно Ubuntu 20.04)
1. Устройства с **64-битным Intel/AMD/ARM** процессором и linux: **CentOS 7+**, **Ubuntu 16.04+** или другими совместимыми дистрибутивами
2. Raspberry **PI 3/4/5** на платформе ARM64 (ARMv8) с установленной ОС (устанавливайте ОС только при помощи Raspberry Pi Imager): **Raspberry Pi OS (64-bit)**, **Ubuntu 20.04 LTS** или **Ubuntu 22.04 LTS**
3. Windows 10/11 (64-bit) с установленной **WSL2** (Windows Subsystem for Linux), Ubuntu 20.04 LTS и включенной поддержкой **виртуализации** (включается в настройках BIOS/UEFI)

### Рекомендуемые характеристики устройства:
1. 2 GB RAM
2. **64**-битный Intel/AMD/ARM процессор

### Установка:
1. Установите Docker и Docker Compose ([подробнее о установке Docker](https://docs.docker.com/engine/install/))
2. Установите Git ([подробнее о установке git](https://git-scm.com/book/ru/v2/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0-Git))
3. Выполните команду `git clone git@bitbucket.org:anthill-farm/farm-proxy-package.git`
4. Перейдите в папку `farm-proxy-package`
5. ⚠ В случае Windows: в разделе volume файла docker-compose.yml заменить `./configs` на `.\configs`
6. Выполните команду `docker compose up -d`
7. Перейдите в браузере по адресу `http://localhost:3000`

---
## Как запустить
Для запуска Farm-Proxy необходимо из корневого каталога проекта выполнить команду:  
```shell
docker compose up -d
```

---

## Настройки
1. Настройки **Farm-Proxy** находятся в файлах `configs/farm-proxy.json` и `configs/proxy_ports.json`  
- Пример файла настроек Farm-Proxy [farm-proxy.yaml](configs/farm-proxy.yaml):
    ```yaml
    log_level: info
    mining_algorithm: sha256d
    bind_api_addr: 0.0.0.0:4050
    log_dir: "./configs/log"
    ```

- Пример файла настроек Farm-Proxy [farm-proxy_ports.yaml](configs/proxy_ports.yaml):
    ```yaml
    - bind_port: 4042
      # Соотношения для установки сложности для каждого майнера (0.2 = 1 шара в 5 секунд)
      # Расчетка: 0.2 = 1 / 5 (1 шара в 5 секунду), 
      # где 1 - колечество шар,
      # 5 - количество секунд
      submission_rate: 0.2
      mining_algorithm: scrypt
      pool:
        # Адрес пула
        url: btc.viabtc.io:3333
        # Логин
        user: login
        # Пароль
        pass: password
    - bind_port: 4043
      submission_rate: 0.2
      mining_algorithm: sha256d
      pool:
        url: btc.viabtc.io:3333
        user: login
        pass: password
    ```  
  
2. **Prometheus** находятся в файлах `monitoring/prometheus/alert.rules` и `monitoring/prometheus/prometheus.yml`

---

## Логи
- Farm-Proxy в папке `configs/log`