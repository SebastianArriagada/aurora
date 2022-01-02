# Implementación PMV0.1

## Requerimientos

* Docker https://www.docker.com/get-started
* pAdmin https://www.pgadmin.org/
* Go https://golang.org/
* Android Studio https://developer.android.com/studio
* Flutter https://flutter.dev

## Despliegue

### aurora_database

- Entrar a la carpeta aurora_database y compilar la imagen docker (utilizando docker build)

``
sudo docker build --tag "aurora_database" .
``

- Desplegar en máquina local 

``
sudo docker run -it aurora_database -p 6000:5432 -e POSTGRES_PASSWORD=test aurora_database
``

- Utilizar pgAdmin para ingresar a la base de datos y explorarla.

### aurora_go

- Entrar a la carpeta aurora_go e instalar dependencias 

``
go get
``

- Compilar imagen la imagen docker 

``
sudo docker build --tag "aurora_go" .
``

- Desplegar en conexión a la base de datos en postgres

``
sudo docker run --network host -e DATABASE_URI=postgres://postgres:test@127.0.0.1:6000/aurora -e LISTEN_URI=0.0.0.0:5500 aurora_go
``

### aurora_flutter
- Abrir el proyecto con Android Studio (e instalar plugins de ser necesario)
- Aprovisionar (crear un emulador o utilizar su celular)
- Compilar la aplicación y ejecutarla
- Conectarse al servidor

## Resumen ejecución

### Database 

Activar la imagen docker para la base de datos

``
sudo docker run -it aurora_database -p 6000:5432 -e POSTGRES_PASSWORD=test aurora_database
``

### Go 

Activar la imagen docker de Go en conexión a la base de datos

``
sudo docker run --network host -e DATABASE_URI=postgres://postgres:test@127.0.0.1:6000/aurora -e LISTEN_URI=0.0.0.0:5500 aurora_go
``

### Flutter

Abrir android studio con el proyecto aurora_flutter

``
cd /usr/local/android-studio/bin
./studio.sh
``

Ejecutar la aplicación

``
flutter run
``
