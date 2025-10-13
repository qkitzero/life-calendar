# Life Calendar

- [Life Calender Frontend](https://github.com/qkitzero/life-calendar-frontend)
- [Auth Service](https://github.com/qkitzero/auth-service)
- [User Service](https://github.com/qkitzero/user-service)
- [Event Service](https://github.com/qkitzero/event-service)

```mermaid
flowchart TD
    user(User)

    subgraph gcp[GCP]
        subgraph cloud_run[Cloud Run]
            life_calendar_frontend(Life Calender Frontend)
            auth_service(Auth Service)
            user_service(User Service)
            event_service(Event Service)
            auth_service_gateway(Auth Service Gateway)
            user_service_gateway(User Service Gateway)
            event_service_gateway(Event Service Gateway)
        end
    end

    subgraph external[External]
        auth0(Auth0)
        user_db[(User DB)]
        event_db[(Event DB)]
    end

    user --> life_calendar_frontend
    life_calendar_frontend --> auth_service_gateway --> auth_service
    life_calendar_frontend --> user_service_gateway --> user_service
    life_calendar_frontend --> event_service_gateway --> event_service
    event_service --> auth_service
    user_service --> auth_service
    event_service --> user_service
    user_service --> user_db
    event_service --> event_db
    auth_service --> auth0
    life_calendar_frontend --> auth0
```
