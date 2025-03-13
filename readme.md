# Products Launcher 🚀

**Products Launcher** is a scalable and modular microservices project built using modern technologies like **Docker**, **NATS**, **NestJS**, and **Prisma**. This repository serves as an entry point to manage and deploy the microservices that make up the application: **Auth**, **Products**, **Orders**, and **Client Gateway**.

The project is designed to be a solid foundation for distributed applications, with a focus on scalability, asynchronous communication between services, and efficient database management.

---

## 🛠️ Core Technologies

- **Docker**: Containerization of microservices for consistent and isolated deployment.
- **NATS**: Lightweight and high-performance messaging system for communication between microservices.
- **NestJS**: Backend framework for Node.js, used to build scalable and efficient applications.
- **Prisma**: Modern ORM for database management with TypeScript.
- **Git Submodules**: Modular codebase management, split into independent repositories for each microservice.

---

## 📂 Project Structure

The main repository acts as a container for the following submodules:

1. **Auth**: Authentication and authorization microservice.
2. **Products**: Microservice for product management.
3. **Orders**: Microservice for order management.
4. **Client Gateway**: Gateway that acts as the entry point for client requests.

Each submodule is an independent repository, enabling modular development and deployment.

---

## 🚀 Getting Started

### Prerequisites

- **Docker** and **Docker Compose** installed.
- **Node.js** (v16 or higher).
- **Git** (for managing submodules).

### Setup Steps

1. **Clone the Main Repository**:
   ```bash
   git clone https://github.com/JesusxAguirre/products-launcher.git
   cd products-launcher
   ```

2. **Initialize Submodules**:
   ```bash
   git submodule init
   git submodule update
   ```

3. **Configure Environment Variables**:
   - Create a `.env` file in each submodule based on the provided `.env.example` file.
   - Ensure database credentials and NATS URLs are correctly configured.

4. **Build and Start the Containers**:
   ```bash
   docker-compose up --build
   ```

5. **Run Prisma Migrations**:
   - Enter each microservice's container and run the migrations:
     ```bash
     docker exec -it <container_id> bash
     npx prisma migrate dev
     ```

6. **Access the Services**:
   - The microservices will be available on the ports configured in `docker-compose.yml`.
   - The **Client Gateway** will act as the entry point for client requests.

---

## 🧩 Microservices

### 1. **Auth**
- Handles user authentication and authorization.
- Uses JWT (JSON Web Tokens) for security.
- Database: PostgreSQL.

### 2. **Products**
- Manages the product catalog.
- Exposes endpoints for creating, reading, updating, and deleting products.
- Database: PostgreSQL.

### 3. **Orders**
- Manages orders placed by users.
- Communicates with the **Products** microservice to validate product availability.
- Database: PostgreSQL.

### 4. **Client Gateway**
- Gateway that centralizes client requests and routes them to the appropriate microservices.
- Implements an API Gateway pattern to simplify communication with the frontend.

---

## 🌐 Inter-Service Communication

Communication between microservices is handled through **NATS**, a lightweight and high-performance messaging system. This enables:

- **Asynchronous Communication**: Microservices can send and receive messages without needing to be active simultaneously.
- **Scalability**: NATS allows horizontal scaling of microservices without complications.
- **Decoupling**: Microservices are not directly dependent on each other, making maintenance and updates easier.

---

## 🐳 Docker and Docker Compose

The project uses **Docker** to containerize each microservice and **Docker Compose** to orchestrate the containers. This ensures:

- **Consistency**: All environments (development, testing, production) are identical.
- **Isolation**: Each microservice runs in its own container, avoiding dependency conflicts.
- **Ease of Deployment**: With a single command (`docker-compose up`), all services are started and configured automatically.

---

## 📊 Prisma and Database Management

Each microservice uses **Prisma** as the ORM to interact with its PostgreSQL database. Prisma provides:

- **Type Safety**: Typed queries and autocompletion in TypeScript.
- **Automatic Migrations**: Simplifies managing changes to the database schema.
- **Entity Relationships**: Makes defining relationships between tables easier.

---

## 🧪 Testing

Each microservice includes unit and integration tests. To run the tests:

1. Enter the microservice's container:
   ```bash
   docker exec -it <container_id> bash
   ```

2. Run the tests:
   ```bash
   npm test
   ```

---

## 🤝 Contributions

Contributions are welcome! If you'd like to contribute to the project, follow these steps:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/new-feature`).
3. Make your changes and commit them (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature/new-feature`).
5. Open a Pull Request.

---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

## ✉️ Contact

If you have any questions or suggestions, feel free to reach out:

- **Name**: Jesús Aguirre
- **GitHub**: [JesusxAguirre](https://github.com/JesusxAguirre)
- **Email**: quijess6@gmail.com

---

Thanks for visiting **Products Launcher**! 🚀


