# EM Register

[![NPM](https://nodei.co/npm/em-register-v1.png)](https://nodei.co/npm/em-register-v1/)

The `EM Register` is a lightweight service locator used for managing and retrieving singleton instances of various services in a centralized manner. It provides methods to register, retrieve, and clear services, making it easier to manage dependencies across your application.

## Installation

To install the package via npm, run the following command:

```bash  
npm install em-register-v1
OR 
yarn add em-register-v1
```

### Class: `ServiceRegistry`

### Static Methods

- **`registerService<T>(key: string, serviceConstructor: new () => T): void`**
  - Registers a service by a unique key. If the service is not already registered, it will create a new instance using the provided constructor and store it in the registry.
  - **Parameters**:
    - `key`: A unique string identifier for the service.
    - `serviceConstructor`: A constructor for the service class.

- **`getService<T>(key: string): T | undefined`**
  - Retrieves a service instance from the registry by its unique key.
  - **Parameters**:
    - `key`: The unique identifier for the service.
  - **Returns**: The service instance or `undefined` if it is not registered.

- **`getAllServices(): { [key: string]: any }`**
  - Retrieves all registered services.
  - **Returns**: An object containing all registered services, where keys are service identifiers.

- **`clearRegistry(): void`**
  - Clears all services from the registry.

### Example Usage

The following example demonstrates how to register and retrieve services using the `ServiceRegistry` in your application:

```ts
import { IUserService } from "../interfaces/user.interface";
import { ServiceRegistry } from "em-register-v1";
import UserService from "../services/user.service";

// Services
// Register here
ServiceRegistry.registerService("UserService", UserService);

// Export service here for global access
export const userService =
    ServiceRegistry.getService<IUrlService>("UserService");

```

### Key Features

- **Centralized Service Management**: Easily register and access services across your application.
- **Lazy Initialization**: Services are instantiated only once, ensuring that multiple calls to `getService` return the same instance.
- **Clearable Registry**: You can reset the service registry by calling `clearRegistry`.

### Use Cases

- **Dependency Injection**: Simplifies dependency injection in complex applications by allowing services to be registered and retrieved in a decoupled manner.
- **Singleton Management**: Ensures that services are treated as singletons by controlling their instantiation and lifecycle through the registry.

### Author

Created and maintained by [Ethern Myth](https://github.com/Ethern-Myth)
