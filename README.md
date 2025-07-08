# Life Calendar

- [Life Calender Frontend](https://github.com/qkitzero/life-calendar-frontend)
- [Auth Service](https://github.com/qkitzero/auth-service)
- [User Service](https://github.com/qkitzero/user-service)

```mermaid
flowchart TD
    user(User)

    subgraph gcp[GCP]
        life_calendar_frontend(Life Calender Frontend)
        auth_service(Auth Service)
        user_service(User Service)
        auth_service_gateway(Auth Service Gateway)
        user_service_gateway(User Service Gateway)
    end

    auth0(Auth0)
    user_db[(User DB)]

    user --> life_calendar_frontend
    life_calendar_frontend --> auth_service_gateway
    life_calendar_frontend --> user_service_gateway
    auth_service_gateway --> auth_service
    user_service_gateway --> user_service
    user_service --> auth_service
    user_service --> user_db
    auth_service --> auth0
    life_calendar_frontend --> auth0
```
