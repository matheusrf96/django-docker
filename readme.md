# Commandos #

1 - Executar: ```docker-compose run web django-admin.py startproject composedjango .```

2 - Iniciar os containers: <br/>
- ```docker-compose up -d```<br/>
- (Aguarde o serviço 'db' iniciar...)<br/>
- ```docker-compose restart```

3 - Fazer as migrações:
```
docker exec app ./manage.py makemigrations
docker exec app ./manage.py migrate
docker exec app ./manage.py createsuperuser
```

## Erros ##

_django.db.utils.OperationalError: (2003, 'Can\'t connect to MySQL server on \'127.0.0.1\' (111 "Connection refused")') docker_<br/>
- Mudar o host para 'db'(nome do container no **docker-compose.yml**) no **settings.py**

_django.db.utils.operationalError: (2059,“Authentication Plugin 'caching_sha2_password'”)_<br/>
- ```ALTER USER 'username'@'ip_address' IDENTIFIED WITH mysql_native_password BY 'password';``` no banco<br/>
- ```docker-compose restart```