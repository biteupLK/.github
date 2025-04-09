# Microservices Architecture with Spring Boot

This project consists of a set of microservices developed using Spring Boot. The application demonstrates a basic structure for implementing microservices with inter-service communication.

## Services

The system includes the following microservices:

- **biteup-gateway** (Port: 5000)  
  API Gateway to route requests to appropriate services.

- **user-service** (Port: 8083)  
  Manages user-related functionalities such as registration, authentication, and user management.

- **product-service** (Port: 8080)  
  Handles product-related data and operations, such as product listing, inventory management, etc.

- **restaurant-service** (Port: 8081)  
  Manages restaurant-specific features, such as restaurant details, menu management, etc.

- **order-service** (Port: 8082)  
  Handles order processing and related operations for users to place orders.

## Prerequisites

Before running the application, ensure that the following software is installed:

- Java 17 (or higher)
- Maven or Gradle (for building the services)
- Docker (optional, for containerization)
- MongoDB (for services that require it, if applicable)

## Running the Application

### Local Development

To run the services locally, follow these steps:

1. Clone the repository:
    ```bash
    git clone <repository-url>
    ```

2. Navigate to the folder of each service and run the application:
    - `biteup-gateway`:
      ```bash
      cd biteup-gateway
      ./mvnw spring-boot:run
      ```
    - `user-service`:
      ```bash
      cd user-service
      ./mvnw spring-boot:run
      ```
    - `product-service`:
      ```bash
      cd product-service
      ./mvnw spring-boot:run
      ```
    - `restaurant-service`:
      ```bash
      cd restaurant-service
      ./mvnw spring-boot:run
      ```
    - `order-service`:
      ```bash
      cd order-service
      ./mvnw spring-boot:run
      ```

3. Services will be running on the following ports:
    - **biteup-gateway**: `http://localhost:5000`
    - **user-service**: `http://localhost:8083`
    - **product-service**: `http://localhost:8080`
    - **restaurant-service**: `http://localhost:8081`
    - **order-service**: `http://localhost:8082`

### Docker (Optional)

To run the services with Docker, build Docker images for each service and then run them with Docker Compose or Kubernetes.

## API Endpoints

### biteup-gateway (API Gateway)
- Routes incoming requests to the appropriate service.

### user-service
- `GET /users`: Retrieve list of all users.
- `POST /users`: Create a new user.
- `GET /users/{id}`: Get details of a specific user.

### product-service
- `GET /products`: Retrieve list of all products.
- `POST /products`: Add a new product.
- `GET /products/{id}`: Get details of a specific product.

### restaurant-service
- `GET /restaurants`: Retrieve list of all restaurants.
- `POST /restaurants`: Add a new restaurant.
- `GET /restaurants/{id}`: Get details of a specific restaurant.

### order-service
- `GET /orders`: Retrieve list of all orders.
- `POST /orders`: Place a new order.
- `GET /orders/{id}`: Get details of a specific order.

## Keycloak Authentication with Google OAuth2

To enable **Google OAuth2** authentication via **Keycloak**, follow the steps below.

### Prerequisites

- A running **Keycloak** server. runs on port 8181
- A **Google Cloud Project** with OAuth 2.0 credentials set up.

### Steps to Set Up Google OAuth2 in Keycloak 

1. **Create a Google OAuth2 Client ID**:
   - Go to the **[Google Cloud Console](https://console.cloud.google.com/)**.
   - Create a new project or select an existing project.
   - Navigate to **APIs & Services** > **Credentials**.
   - Click on **Create Credentials** and select **OAuth 2.0 Client ID**.
   - In the **Application type** section, select **Web application**.
   - Under **Authorized redirect URIs**, add the following URI:
     ```
     http://<your-keycloak-server>/realms/<realm-name>/broker/google/endpoint
     ```
     Replace `<your-keycloak-server>` with your Keycloak server URL and `<realm-name>` with your specific realm.

2. **Get the Client ID and Client Secret** from the Google Cloud Console after creating the credentials.

3. **Configure Keycloak**:
   - Log in to the **Keycloak Admin Console**.
   - Select the **Realm** in which you want to enable Google authentication.
   - Navigate to **Identity Providers** in the left-hand menu.
   - Click **Add provider**, select **Google** from the list.
   - Fill in the **Client ID** and **Client Secret** you obtained from Google.
   - Ensure that **Enabled** is set to `ON` and save the configuration.

4. **Test the Authentication**:
   - Once configured, users should be able to log in to your Keycloak instance via Google OAuth2.
   - Navigate to the login screen and click the **"Login with Google"** button.

### Notes
- Make sure to configure **redirect URIs** properly to ensure Google knows where to send the authentication responses.
- You can customize the appearance and behavior of the login page by modifying the Keycloak theme.

## Notes

- Each service can run independently.
- The gateway service will route requests to the appropriate service based on the request.
- Use MongoDB or other databases where applicable for persistence (depending on the service implementation).
- You can scale individual services independently as needed in a production environment.

## Contributing

Feel free to fork the repository and contribute improvements. To submit changes:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit them (`git commit -am 'Add new feature'`).
4. Push to your forked repository (`git push origin feature-branch`).
5. Create a pull request from your fork to the main repository.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
