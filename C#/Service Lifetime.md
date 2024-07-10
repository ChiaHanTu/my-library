### Transient

> Are created each time they're requested from the service container.

- New instance created each time

### Scoped 

> Indicates that services are created once per client request (connection)

### Singleton

>  Are created either:
>  1. The first time they're requested.
>  2. By the developer, when providing an implementation instance directly to the container. This approach is rarely needed.

- Every subsequent request of the service implementation from the dependency injection container uses **the same instance**.


