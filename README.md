# Glpi Docker

## Instalação

Criar um volume com o nome __glpi_app__:

``` bash
docker volume create --name=glpi_app
```

Edite o arquivo __php/config_db.php__ com as configurações do banco de dados que será utilizado.

Criar uma stack com o docker-compose do projeto:

```bash
docker stack deploy -c docker-compose.yml glpi-docker
```

## Atualização de uma versão antiga

Após efetuar a instalação, executar no MySQL o script __update_fix.sql__.

Depois de subir o container, acessar o conteiner do php, na pasta /var/www/html/glpi/scripts executar o script __innodb_migration.php__.

```bash
php /var/www/html/glpi/scripts/innodb_migration.php
```