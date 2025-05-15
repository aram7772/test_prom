# Monitoring System with Grafana, Prometheus and Filebeat

## Состав системы
- Grafana (доступна на http://localhost:80)
- Prometheus (собирает метрики от node_exporter)
- node_exporter (отдаёт системные метрики)
- Filebeat (агрегирует логи контейнеров и сохраняет их в /var/log/test)
- Ansible Playbook (разворачивает Filebeat)

## Установка

### 1. Запустить Grafana, Prometheus и node_exporter
```bash
docker compose up -d
```

### 2. Развернуть Filebeat с помощью Ansible
```bash
cd ansible
ansible-playbook -i inventory.ini playbook.yml -K (-K нужен чтоб запустить через root)
```

## Проверка

- Grafana доступна по адресу: http://localhost:80 (логин/пароль: admin/admin123)
- Prometheus: http://localhost:9090
- Логи сохраняются в /var/log/test и содержат информацию о контейнерах

## Метрики для Grafana Explore

Примеры:
- node_cpu_seconds_total
- node_memory_MemAvailable_bytes
- node_network_receive_bytes_total