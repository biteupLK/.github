# BiteUp - Modern Food Delivery Microservices

<div align="center">

</div>

## 📋 Overview

BiteUp is a comprehensive food delivery platform implemented as a microservices architecture using Spring Boot. The system is designed for flexibility, scalability, and resilience, allowing each service to be developed, deployed, and scaled independently.

## 🏛️ Architecture

The platform consists of the following microservices:

| Service | Port | Description |
|---------|------|-------------|
| **biteup-gateway** | 5000 | API Gateway that routes requests to appropriate services |
| **user-service** | 8083 | Handles user registration, authentication, and profile management |
| **product-service** | 8080 | Manages product catalog, inventory, and related operations |
| **restaurant-service** | 8081 | Processes restaurant data, menu management, and restaurant-specific features |
| **order-service** | 8082 | Manages order creation, processing, and tracking |
| **keycloak** | 8181 | Identity and access management with OAuth2 support |

## 🚀 Getting Started

### Prerequisites

- Java 17 or higher
- Maven or Gradle
- Docker (recommended for containerization)
- MongoDB (for data persistence)

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/yourusername/biteup.git
cd biteup
```

2. **Build and run each service**

You can run each service individually:

```bash
# For each service directory (repeat for each service)
cd service-name
./mvnw clean install
./mvnw spring-boot:run
```

Alternatively, use the provided script to run all services:

```bash
./run-all-services.sh
```

3. **Access the services**

- API Gateway: http://localhost:5000
- User Service: http://localhost:8083
- Product Service: http://localhost:8080
- Restaurant Service: http://localhost:8081
- Order Service: http://localhost:8082
- Keycloak: http://localhost:8181

## 🐳 Docker Deployment

For containerized deployment, use Docker Compose:

```bash
docker-compose up -d
```

## 🔒 Authentication with Keycloak

BiteUp uses Keycloak for secure authentication, including Google OAuth2 integration.

### Custom Keycloak Theme

BiteUp includes a custom Keycloak theme to match the platform's branding. To use the custom theme:

1. **Download the theme**:
   [Download BiteUp Keycloak Theme](https://drive.google.com/file/d/19UvcLFCLGExOlep_hUVEBAbdlmDlPFcX/view?usp=sharing)

2. **Install the theme**:
   - Extract the theme files
   - Place the theme folder in the `themes` directory of your Keycloak installation
   - Restart Keycloak

3. **Apply the theme**:
   - Log in to the Keycloak Admin Console
   - Navigate to your realm
   - Go to Realm Settings > Themes
   - Select "biteup" from the dropdown menu for Login, Account, and Admin Console themes
   - Save changes

### Setting up Google OAuth2 in Keycloak

1. **Google Cloud Setup**:
   - Create a project in [Google Cloud Console](https://console.cloud.google.com/)
   - Enable the Google+ API
   - Create OAuth 2.0 client credentials
   - Add the redirect URI: `http://localhost:8181/realms/biteup/broker/google/endpoint`

2. **Keycloak Configuration**:
   - Log in to Keycloak Admin Console
   - Navigate to your realm
   - Go to Identity Providers
   - Click "Add provider" and select "Google"
   - Enter your Google Client ID and Client Secret
   - Save the configuration

## 📡 API Endpoints

### User Service
- `GET /users` - List all users
- `POST /users` - Create a new user
- `GET /users/{id}` - Get a specific user

### Product Service
- `GET /products` - List all products
- `POST /products` - Add a new product
- `GET /products/{id}` - Get a specific product

### Restaurant Service
- `GET /restaurants` - List all restaurants
- `POST /restaurants` - Add a new restaurant
- `GET /restaurants/{id}` - Get a specific restaurant

### Order Service
- `GET /orders` - List all orders
- `POST /orders` - Create a new order
- `GET /orders/{id}` - Get a specific order

## 🔄 Service Communication

BiteUp uses both synchronous (REST) and asynchronous (event-driven) communication patterns:

- **Synchronous**: Direct REST calls between services for immediate response requirements
- **Asynchronous**: Event-based communication for decoupled operations

## 💻 Development

### Recommended Tools
- IntelliJ IDEA or VSCode with Spring Boot extensions
- Postman for API testing
- Docker Desktop for container management

### Debugging

Each service includes Spring Boot Actuator endpoints for monitoring and debugging:

```
http://localhost:<service-port>/actuator/health
```

## 📊 Monitoring

The platform includes:
- Spring Boot Actuator for health and metrics
- Prometheus integration for metrics collection
- Grafana dashboards for visualization

## 🤝 Contributing

We welcome contributions to BiteUp! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to your branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

