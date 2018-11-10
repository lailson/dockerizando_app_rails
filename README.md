# Docjerizando um app rails com Postgresql

Ponto de partida para utilizar o docker com ruby on rails e postgre

## Utilizando

Siga as instuções abaixo para utilizar de maneira correta o docker com ruby on rails.

### Prerequisitos

É necessário ter docker e git instalados na sua máquina


### Utilizando

Passo a passo:

Clone o projeto na súa máquina

```
git clone https://github.com/lailson/dockerizando_app_rails.git nome_do_projeto
```

Entre na pasta do seu projeto

```
cd nome_do_projeto
```


Crie o seu projeto rails

```
docker-compose run web rails new . --force --database=postgresql
```

Se estiver no linux utilize o comando

```
sudo chown -R $USER:$USER
```

Buildar o projeto

```
docker-compose build
```

Alterar o arquivo config/database.yml
https://gist.github.com/lailson/99498165f9dffa7ba50b601fd46e6f4a

```
default: &default
  adapter: postgresql
  encoding: unicode
  # HOST: olhar nome do serviço em docker-compose.yml
  host: db
  username: postgres
  password: mypassword
  pool: 5

development:
  <<: *default
  database: myapp_development


test:
  <<: *default
  database: myapp_test
```

Criar bd

```
docker-compose run web rails db:create
```

Subir o serviço

```
docker-compose up
```

obs.:
quando finalizar o serviço e for iniciar novamente e encontrar um erro de pid talvez seja necessário utilizar o comando abaixo:
```
rm ./tmp/pids/server.pid
```


## Utilizando

* [Ruby:2.5](https://hub.docker.com/_/ruby/) - Utilizando a imagem do ruby 2.5
* [Rails 5.2.1](https://rubygems.org/gems/rails) - Utilzaindo a gem do rails na versão 5.2.1
* [Postgres](https://www.postgresql.org/) - Utilizando o postgres como banco de dados

## Contribuindo

Para novas verões utile o PR


## Licença

This project is licensed under the MIT License 
