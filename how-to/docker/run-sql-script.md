# How to run scripts inside docker container

## SQL

`$ docker exec -i {container_name} {command}`

- container name : name of the container
- command : command to be run

example:

    $ docker exec -i laradock_mysql_1 mysql -uroot -proot -D cbre_tenant < usonar.sql
