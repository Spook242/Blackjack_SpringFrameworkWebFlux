# Descripción
Este proyecto consiste en el desarrollo de una API REST para gestionar un juego de Blackjack. El objetivo principal es implementar una arquitectura de microservicios o modular que permita:

Registrar y modificar jugadores.

Jugar partidas de Blackjack (lógica de cartas y puntos).

Almacenar el historial de partidas y estadísticas.

Gestionar rankings de ganadores y perdedores.

La particularidad técnica de este ejercicio es la persistencia híbrida de datos:

MySQL: Para almacenar los datos de los jugadores (Relacional).

MongoDB: Para almacenar las partidas jugadas (NoSQL).

# Tecnologías Utilizadas
El proyecto se ha desarrollado utilizando las siguientes tecnologías y herramientas:

Lenguaje: Java 21 (Eclipse Temurin).

Framework: Spring Boot (Spring Data JPA, Spring Data MongoDB).

Bases de Datos:

MySQL 8.0

MongoDB 6.0

Contenerización: Docker y Docker Compose.

Documentación API: Swagger / OpenAPI (SpringDoc).

Build Tool: Maven.

Repositorio de Imágenes: Docker Hub.

# Requisitos
Para ejecutar este proyecto en local, se necesitan los siguientes requisitos previos:

Docker Desktop instalado y en ejecución (Imprescindible para las bases de datos).

Git (para clonar el repositorio).

(Opcional) Java 21 y Maven instalados si se desea ejecutar fuera de Docker.

(Opcional) IntelliJ IDEA o Eclipse para el desarrollo.

# Instalación
Sigue estos pasos para configurar el entorno en local:

Clonar el repositorio:
git clone <URL_DEL_TEU_REPOSITORIO>
cd blackjack-api

Generar el artefacto (.jar): Es necesario compilar el proyecto antes de construir la imagen Docker.
./mvnw clean package -DskipTests

Construir la imagen Docker (Opcional si se utiliza Docker Hub):
docker build -t blackjack-api .

# Ejecución
Hay dos formas de ejecutar el proyecto.

Opción A: Entorno Completo con Docker Compose (Recomendado)
Esto levantará la API, MySQL y MongoDB automáticamente.

Ejecuta el pedido:
docker-compose up -d

La API estará disponible en el puerto 8082.
Swagger UI: http://localhost:8082/webjars/swagger-ui/index.html

Opción B: Entorno de Desarrollo (Híbrido)
Si quieres desarrollar con IntelliJ pero utilizando las bases de datos de Docker.

Asegúrate de que los contenedores de DB están corriendo (docker-compose up -d).

Ejecuta la aplicación desde tu IDE (IntelliJ).

La API de desarrollo estará disponible en el puerto 8081.

# Despliegue
La imagen del proyecto está subida y disponible en Docker Hub. Para desplegar la aplicación en cualquier servidor con Docker instalado, no es necesario clonar el código, sólo descargar la imagen:

Descargar la imagen:
docker pull spook242/blackjack-api:v1.0

Ejecución: Para su correcto funcionamiento, debe ejecutarse conectándola a las bases de datos correspondientes (o utilizando un archivo docker-compose.yml que referencie esta imagen).

Ejemplo básico de ejecución (requiere red configurada con bases de datos):
docker run -p 8080:8081 --name blackjack-app spook242/blackjack-api:v1.0
