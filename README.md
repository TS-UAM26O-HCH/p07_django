# Practica 4 para TSCC

## Instrucciones

Instalacion de Dependencias

```bash
# pip
python -m venv .venv
source .venv/bin/activate
pip install .
```

```bash
# uv
uv sync
```

Levantar Servicios

```bash
cd proyecto_django/back_end_django
docker compose build
docker compose up -d
docker ps
```

Conectarse a la Base de Datos

```bash
 ./pgres.bash
```

Listar las tablas dentro de la Base de Datos

```sql
\dt
```

Preparar el entorno con la Base de Datos

```bash
python3 manage.py migrate
python3 manage.py check
python3 manage.py initadmin
# python3 manage.py runserver # No es necesario pues se levanta el servidor con Docker
python3 manage.py test
```

```bash
# uv
uv run manage.py migrate
uv run manage.py check
uv run manage.py initadmin
# uv run manage.py runserver # No es necesario pues se levanta el servidor con Docker
uv run manage.py test
```

Visualizacion de la API

```
http://127.0.0.1:8000/swagger/
```

Para el uso de la api es necesario _autenticacion_

Dentro del endpoint "auth/token/
Ingresar las credenciales Hardcodeadas en ...gestion_usuarios/management/commands/initadmin.py

```
Admin
AdminApiDjango123
```

Copiar el Access Token sin comillas y dentro de el boton `Authorize` de Swagger ingresar:

`Bearer` seguida del access token dejando un espacio

Para realizar los tests probablemente sea necesario reclamar la propiedad de los logs

```bash
sudo chown -R $USER:$USER {Path del proyecto}/back_end_django/logs

chmod -R u+rwX {Path del proyecto}/back_end_django/logs
```
