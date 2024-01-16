### Install and configure infrastructure with Ansible:
    ansible-playbook infra.yaml


### Restore MySQL data

#### How to check if MySQL backup worked? Part 1
Before beginning restore procedure add some meaningless items in agama application and remember names of the items.

#### Restore MySQL data from the backup:
On demetr25-1:

    1. sudo su
    2. rm -rf /home/backup/restore/mysql
    3. sudo -u backup duplicity --no-encryption restore rsync://demetr25@backup.akamly.dd//home/demetr25/mysql /home/backup/restore/mysql
    4. mysql agama < /home/backup/restore/mysql/agama.sql

#### How to check if MySQL backup worked? Part 2
After the procedure is completed you shouldn't see items which were previously added by you.


### Restore InfluxDB data

#### Restore InfluxDB data from the backup:
On demetr25-3:

    1. sudo su
    2. rm -rf /home/backup/restore/influxdb
    3. sudo -u backup duplicity --no-encryption restore rsync://demetr25@backup.akamly.dd//home/demetr25/influxdb /home/backup/restore/influxdb
    4. service telegraf stop
    5. influx -execute 'DROP DATABASE telegraf'
    6. influxd restore -portable -database telegraf /home/backup/restore/influxdb
    
Run on manager host:

    1. ansible-playbook infra.yaml -ti

#### How to check if InfluxDB backup worked?
To ensure that InfluxDB backup work pay attention to syslog dashboard in Grafana