


# itscode-monorepo

La aplicación itscode full-stack orquestada con Docker, que cuenta con una API en .NET 8, un dashboard en React y un frontend en Vanilla JS.

## Arquitectura

Este proyecto utiliza una estructura de monorepo con submódulos de Git. Se compone de una API central en .NET 8, un frontend al estilo Vanilla JS, un dashboard en React y una base de datos MySQL.

## Stack Tecnológico

-   **Backend**: .NET 8, Entity Framework Core, MySQL
-   **Frontend**: HTML/CSS/JS
-   **Dashboard**: React
-   **Base de Datos**: MySQL 8.0
-   **Orquestación**: Docker, Docker Compose, Nginx

## Prerrequisitos

Asegúrate de tener instalado [Docker](https://www.docker.com/get-started/) y [Docker Compose](https://docs.docker.com/compose/install/) en tu máquina.

## Inicio Rápido

1.  **Clona el repositorio:**
    ```bash
    git clone https://github.com/luirro777/itscode-monorepo.git
    cd itscode-monorepo
    ```

2.  **Inicializa los submódulos:**
    ```bash
    git submodule update --init --recursive
    ```

3.  **Configura las variables de entorno:**
    Renombra el archivo `.env-example` a `.env` en la raíz del proyecto y ajusta las credenciales a los valores necesarios.
    ```bash
    cp .env.example .env
    ```

4.  **Levanta el entorno:**
    ```bash
    docker-compose up --build
    ```

## Acceso a las Aplicaciones

Una vez que los contenedores estén en ejecución, puedes acceder a las siguientes URLs:

-   **Frontend Público**: `http://localhost:3000`
-   **Dashboard de Administración**: `http://localhost:5052`
-   **API**: `http://localhost:3001` (Swagger UI disponible en `/swagger`)

## Estructura del Proyecto

-   `services/`: Contiene el código fuente de las aplicaciones principales (API, frontends) como submódulos de Git.
-   `dockerfiles/`: Alberga todos los archivos de configuración de Docker, manteniendo la lógica de construcción separada del código de la aplicación.
-   `nginx/`: Contiene las configuraciones de Nginx al frontend.
-   `.env`: Variables de entorno para el desarrollo local (no se rastrea en Git).
-   `docker-compose.yml`: El archivo principal de orquestación para todo el entorno.

