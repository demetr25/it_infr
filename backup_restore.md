### Install and configure infrastructure with Ansible:

    ansible-playbook infra.yaml

### How to check if MySQL backup worked? Part 1

    -Before beginning restore procedure add some meaningless items in agama application and remember names of the items.

### Restore MySQL data from the backup:

    1. sudo su
    2. cd /home/backup/restore
    3. rm -rf mysql
    4. exit
    5. sudo -u backup duplicity --no-encryption restore rsync://demetr25@backup.akakamly.dd//home/demetr25/mysql /home/backup/restore/mysql
    6. sudo su
    7. mysql agama < /home/backup/restore/mysql/agama.sql

### How to check if MySQL backup worked? Part 2

    After the procedure is completed you shouldn't see items which were previously added by you.

### Restore InfluxDB data from the backup:

    1. sudo su
    2. cd /home/backup/restore
    3. rm -rf influxdb
    4. exit
    5. sudo -u backup duplicity --no-encryption restore rsync://demetr25@backup.akamly.dd//home/demetr25/influxdb /home/backup/restore/influxdb
    6. sudo su
    7. service telegraf stop
    8. influx -execute 'DROP DATABASE telegraf'
    9. influxd restore -portable -database telegraf /home/backup/restore/influxdb
    10. run "ansible-playbook infra.yaml" on manager host

### How to check if InfluxDB backup worked?

    To ensure that InfluxDB backup work pay attention to syslog dashboard in Grafana