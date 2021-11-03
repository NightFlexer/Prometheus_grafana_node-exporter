1) Установить статический ip на внешний интерфейс, например 192.168.28.129
2) Добавить записи в свой файл /etc/hosts:
192.168.28.129 grafana.domain.com
192.168.28.129 jbpm.domain.com
3) Собрать образ из докерфайла: docker build -t jboss/jbpm-server-full:latest .
4) docker-compose up -d
5) Внести правила iptables из файла iptables_rules, чтобы ограничить доступ к контейнерам. 

Возможны проблемы с экспортом dashboar: Datasource named ${DS_TEST1} was not found
Это известная проблема графаны: https://github.com/grafana/grafana/issues/10786
В случае неудачного экспорта, удалить dashboard в панели графаны и экспортировать его на вкладке Data Sources/Prometheus/Dashboards - Import (Prometheus 2.0 Stats)
