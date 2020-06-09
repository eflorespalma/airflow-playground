## Instalación

Obtener la imagen del repositorio de Docker.

    docker pull realplaza/airflow:1.10.9

## Build

Instalación Opcional [Extra Airflow Packages](https://airflow.incubator.apache.org/installation.html#extra-package) :

    docker build --rm --build-arg AIRFLOW_DEPS="datadog,dask" -t realplaza/airflow:1.10.9 .
    docker build --rm --build-arg PYTHON_DEPS="flask_oauthlib>=0.9" -t realplaza/airflow:1.10.9 .

o combinada

    docker build --rm --build-arg AIRFLOW_DEPS="datadog,dask" --build-arg PYTHON_DEPS="flask_oauthlib>=0.9" -t realplaza/docker-airflow:1.10.9 .

No olvidar actualizar las imagenes de airflow a través del archivo docker-compose files to realplaza/docker-airflow:1.10.9.

## Uso

Por defecto, airflow corre con **SequentialExecutor** :

    docker run -d -p 8080:8080 realplaza/airflow:1.10.9 webserver

Si quisieras correrlo con otro ejecutor, puedes usar los archivos docker-compose.yml que están en el repositorio en Azure DevOps.

Para **LocalExecutor** :

    docker-compose -f docker-compose-LocalExecutor.yml up -d

Para **CeleryExecutor** :

    docker-compose -f docker-compose-CeleryExecutor.yml up -d