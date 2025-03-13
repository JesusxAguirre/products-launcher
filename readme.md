
# Products Launcher 🚀

**Products Launcher** es un proyecto de microservicios escalable y modular que utiliza tecnologías modernas como **Docker**, **NATS**, **NestJS** y **Prisma**. Este repositorio sirve como un punto de entrada para gestionar y desplegar los microservicios que componen la aplicación: **Auth**, **Products**, **Orders** y **Client Gateway**.

El proyecto está diseñado para ser una base sólida para aplicaciones distribuidas, con un enfoque en la escalabilidad, la comunicación asíncrona entre servicios y la gestión eficiente de bases de datos.

---

## 🛠️ Tecnologías Principales

- **Docker**: Contenerización de los microservicios para un despliegue consistente y aislado.
- **NATS**: Sistema de mensajería ligero y de alto rendimiento para la comunicación entre microservicios.
- **NestJS**: Framework backend para Node.js, utilizado para construir aplicaciones escalables y eficientes.
- **Prisma**: ORM moderno para la gestión de bases de datos con TypeScript.
- **Git Submodules**: Gestión modular del código fuente, dividido en repositorios independientes para cada microservicio.

---

## 📂 Estructura del Proyecto

El repositorio principal actúa como un contenedor para los siguientes submódulos:

1. **Auth**: Microservicio de autenticación y autorización.
2. **Products**: Microservicio para la gestión de productos.
3. **Orders**: Microservicio para la gestión de pedidos.
4. **Client Gateway**: Gateway que actúa como punto de entrada para las solicitudes del cliente.

Cada submódulo es un repositorio independiente, lo que permite un desarrollo y despliegue modular.

---

## 🚀 Cómo Empezar

### Prerrequisitos

- **Docker** y **Docker Compose** instalados.
- **Node.js** (v16 o superior).
- **Git** (para manejar submódulos).

### Pasos para Configurar el Proyecto

1. **Clonar el Repositorio Principal**:
   ```bash
   git clone https://github.com/JesusxAguirre/products-launcher.git
   cd products-launcher
   ```

2. **Inicializar Submódulos**:
   ```bash
   git submodule init
   git submodule update
   ```

3. **Configurar Variables de Entorno**:
   - Crea un archivo `.env` en cada submódulo basado en el archivo `.env.example` proporcionado.
   - Asegúrate de configurar correctamente las credenciales de la base de datos y las URLs de NATS.

4. **Construir y Levantar los Contenedores**:
   ```bash
   docker-compose up --build
   ```

5. **Ejecutar Migraciones con Prisma**:
   - Entra en el contenedor de cada microservicio y ejecuta las migraciones:
     ```bash
     docker exec -it <container_id> bash
     npx prisma migrate dev
     ```

6. **Acceder a los Servicios**:
   - Los microservicios estarán disponibles en los puertos configurados en `docker-compose.yml`.
   - El **Client Gateway** actuará como punto de entrada para las solicitudes del cliente.

---

## 🧩 Microservicios

### 1. **Auth**
- Gestiona la autenticación y autorización de usuarios.
- Utiliza JWT (JSON Web Tokens) para la seguridad.
- Base de datos: PostgreSQL.

### 2. **Products**
- Gestiona el catálogo de productos.
- Expone endpoints para crear, leer, actualizar y eliminar productos.
- Base de datos: PostgreSQL.

### 3. **Orders**
- Gestiona los pedidos realizados por los usuarios.
- Se comunica con el microservicio de **Products** para validar la disponibilidad de productos.
- Base de datos: PostgreSQL.

### 4. **Client Gateway**
- Gateway que centraliza las solicitudes del cliente y las redirige a los microservicios correspondientes.
- Implementa un patrón de API Gateway para simplificar la comunicación con el frontend.

---

## 🌐 Comunicación entre Microservicios

La comunicación entre microservicios se realiza a través de **NATS**, un sistema de mensajería ligero y de alto rendimiento. Esto permite:

- **Comunicación Asíncrona**: Los microservicios pueden enviar y recibir mensajes sin necesidad de estar activos simultáneamente.
- **Escalabilidad**: NATS permite escalar horizontalmente los microservicios sin complicaciones.
- **Desacoplamiento**: Los microservicios no dependen directamente unos de otros, lo que facilita el mantenimiento y la actualización.

---

## 🐳 Docker y Docker Compose

El proyecto utiliza **Docker** para contenerizar cada microservicio y **Docker Compose** para orquestar los contenedores. Esto garantiza:

- **Consistencia**: Todos los entornos (desarrollo, pruebas, producción) son idénticos.
- **Aislamiento**: Cada microservicio se ejecuta en su propio contenedor, evitando conflictos de dependencias.
- **Facilidad de Despliegue**: Con un solo comando (`docker-compose up`), todos los servicios se levantan y configuran automáticamente.

---

## 📊 Prisma y Gestión de Bases de Datos

Cada microservicio utiliza **Prisma** como ORM para interactuar con su base de datos PostgreSQL. Prisma ofrece:

- **Type Safety**: Queries tipados y autocompletado en TypeScript.
- **Migraciones Automáticas**: Facilita la gestión de cambios en el esquema de la base de datos.
- **Relaciones entre Entidades**: Simplifica la definición de relaciones entre tablas.

---

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas! Si deseas contribuir al proyecto, sigue estos pasos:

1. Haz un fork del repositorio.
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`).
3. Realiza tus cambios y haz commit (`git commit -m 'Añadir nueva funcionalidad'`).
4. Haz push a la rama (`git push origin feature/nueva-funcionalidad`).
5. Abre un Pull Request.

---

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**. Consulta el archivo [LICENSE](LICENSE) para más detalles.

---

## ✉️ Contacto

Si tienes alguna pregunta o sugerencia, no dudes en contactarme:

- **Nombre**: Jesús Aguirre
- **GitHub**: [JesusxAguirre](https://github.com/JesusxAguirre)
- **Correo**: quijess6@gmail.com

---

¡Gracias por visitar **Products Launcher**! 🚀

---

Este `README.md` está diseñado para ser claro, profesional y fácil de seguir. Si necesitas ajustes adicionales, no dudes en decírmelo. 😊

## Dev

1. Clonar el repositorio
2. Crear un .env basado en el .env.template
3. Ejecutar el comando `git submodule update --init --recursive` para reconstruir los sub-módulos
4. Ejecutar el comando `docker compose up --build`

### Pasos para crear los Git Submodules

1. Crear un nuevo repositorio en GitHub
2. Clonar el repositorio en la máquina local
3. Añadir el submodule, donde `repository_url` es la url del repositorio y `directory_name` es el nombre de la carpeta donde quieres que se guarde el sub-módulo (no debe de existir en el proyecto)

```
git submodule add <repository_url> <directory_name>
```

4. Añadir los cambios al repositorio (git add, git commit, git push)
   Ej:

```
git add .
git commit -m "Add submodule"
git push
```

5. Inicializar y actualizar Sub-módulos, cuando alguien clona el repositorio por primera vez, debe de ejecutar el siguiente comando para inicializar y actualizar los sub-módulos

```
git submodule update --init --recursive
```

6. Para actualizar las referencias de los sub-módulos

```
git submodule update --remote
```



Si se hace al revés, se perderán las referencias de los sub-módulos en el repositorio principal y tendremos que resolver conflictos.
