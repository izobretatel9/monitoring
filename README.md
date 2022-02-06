# Описание скрипта

### Презентация по мониторингу [Monitoring.pptx](https://github.com/izobretatel9/monitoring/blob/main/Monitoring.pptx "click")
#
Скрипт позволяет устанавить такие сервисы:
```
1. grafana
2. nginx-proxy
3. victoriametrics
4. vmalert
5. alertmanager
6. blackbox-exporter
7. cadvisor
8. mongodb
9. elasticsearch
10. graylog
```
На дополнительне диски для данных:
```
volumes:
  grafana-storage:
    driver: local
    name: grafanastorage
    driver_opts:
      type: "ext4"
      device: "/dev/vdg"
  victoriametrics-storage:
    driver: local
    name: victoriametricsstorage
    driver_opts:
      type: "ext4"
      device: "/dev/vdb"
  mongo_data:
    driver: local
    name: mongostorage
    driver_opts:
      type: "ext4"
      device: "/dev/vdd"
  es_data:
    driver: local
    name: esstorage
    driver_opts:
      type: "ext4"
      device: "/dev/vde"
  graylog_data:
    driver: local
    name: graylogstorage
    driver_opts:
      type: "ext4"
      device: "/dev/vdf"
```
## Инструкция по применению: 

1. Настроить машину
2. Добавить диски и смонтировать по Lable:
```
fdisk -l
mkfs.ext4 /dev/vdg
e2label /dev/vdg grafana # Lable
echo "LABEL=grafana /mnt/grafana ext4 lazytime,discard 0 2" | sudo tee -a /etc/fstab
...
...
...
```
3. Устанавить docker и docker-compose
https://github.com/izobretatel9/docker
4. Изменить docker-compose.yml для этого репозитория и запустить
## Дполнительные информация: 

1. Папка "etc" содерджит все "*.yml" для сервисов
2. Папка "dashboards" содерджит необходимые dashboards для Grafana "*.json"
3. Папка "graylog" содерджит файлы для запуска Graylog

## P.s Изначальный создатель скрипта

@izobretatel9