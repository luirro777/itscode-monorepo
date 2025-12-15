


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

## Seteos necesarios en la BD

1.  **Ingresaremos al contenedor de mysql**
    ```bash
    docker exec -ti itscode-mysql mysql -u root -p
    ```
2.  **Colocamos el password de root que hayamos seteado en nuestro .env**

3.  **Procedemos a ejecutar estas sentecias**
    ```bash
    use itscode;
    insert into Roles (Id,Name) values ('1','User');
    insert into Roles (Id,Name) values ('2','Admin');
    ```
4.  **Dejamos abierto este terminal, al cual regresaremos en breve**

## Acceso a las Aplicaciones

Una vez que los contenedores estén en ejecución, puedes acceder a las siguientes URLs:

-   **Frontend Público**: `http://localhost:3000`
-   **Dashboard de Administración**: `http://localhost:3001`
-   **API**: `http://localhost:5052` (Swagger UI disponible en `/swagger`)

## Creación de usuario administrador para el Dashboard

Para crear el usuario administrador, utilizaremos el frontend público y crearemos la cuenta desde allí, con total normalidad.

## Seteos en la BD para activar el usuario administrador

1.  **En la misma terminal donde estabamos (mysql), consultamos los Id de las cuentas**

    ```bash
    select * from Persons;
    ```
2.  **Ubicamos el Id de la cuenta a la que queremos hacer admin, y actualizamos**
    
    Por ejemplo, si es la cuenta con el Id = 2

    ```bash
    update Persons set RoleId = 2 where Id = 2;
    ```
3.  **Ya podemos ingresar al dashboard con dicha cuenta**

## Estructura del Proyecto

-   `services/`: Contiene el código fuente de las aplicaciones principales (API, frontends) como submódulos de Git.
-   `dockerfiles/`: Alberga todos los archivos de configuración de Docker, manteniendo la lógica de construcción separada del código de la aplicación.
-   `nginx/`: Contiene las configuraciones de Nginx al frontend.
-   `.env`: Variables de entorno para el desarrollo local (no se rastrea en Git).
-   `docker-compose.yml`: El archivo principal de orquestación para todo el entorno.


## Créditos

Este proyecto ha sido posible gracias al esfuerzo y dedicación de las siguientes personas.

### Desarrollo Principal

*   **[Nombre del Desarrollador 1]** - [Rol, ej. Backend (.NET), Frontend (React), etc.] - [GitHub](enlace-opcional)
*   **[Nombre del Desarrollador 2]** - [Rol] - [GitHub](enlace-opcional)
*   **[Nombre del Desarrollador 3]** - [Rol] - [GitHub](enlace-opcional)

### Monorepo

*   **[Luis Romano]** - Configuración de Docker y orquestación con Docker Compose.


