# Life Calendar

- [Life Calender Frontend](https://github.com/qkitzero/life-calendar-frontend)
- [Auth Service](https://github.com/qkitzero/auth-service)
- [User Service](https://github.com/qkitzero/user-service)
- [Event Service](https://github.com/qkitzero/event-service)
- [Logging Service](https://github.com/qkitzero/logging-service)

```mermaid
flowchart TD
    user(User)

    subgraph gcp[GCP]
        subgraph cloud_run[Cloud Run]
            life_calendar_frontend(Life Calender Frontend)
            auth_service(Auth Service)
            auth_service_gateway(Auth Service Gateway)
            user_service(User Service)
            user_service_gateway(User Service Gateway)
            event_service(Event Service)
            event_service_gateway(Event Service Gateway)
            logging_service(Logging Service)
        end
    end

    subgraph external[External]
        auth0(Auth0)
        user_db[(User DB)]
        event_db[(Event DB)]
        logging_db[(Logging DB)]
    end

    user --> life_calendar_frontend

    life_calendar_frontend --> auth_service_gateway --> auth_service --> auth0
    life_calendar_frontend --> user_service_gateway --> user_service
    life_calendar_frontend --> event_service_gateway --> event_service
    life_calendar_frontend --> auth0

    user_service --> auth_service
    event_service --> auth_service
    logging_service --> auth_service

    event_service --> user_service

    user_service --> logging_service
    event_service --> logging_service

    user_service --> user_db
    event_service --> event_db
    logging_service --> logging_db
```
