# Модель данных (ERD)

Модель данных основана на пользовательских сценариях и прототипах. Показывает, какие сущности скрываются за экранами интерфейса.

```mermaid
erDiagram
    CLIENT ||--o{ BOOKING : makes
    TRAINER ||--o{ TRAINING_SESSION : conducts
    TRAINING_SESSION ||--o{ BOOKING : has
    CLIENT ||--o{ NOTIFICATION : receives

    CLIENT {
        int id PK
        string full_name
        string phone_number
        string email
    }
    TRAINER {
        int id PK
        string full_name
        string specialization
        string photo_url
    }
    TRAINING_SESSION {
        int id PK
        string title
        datetime start_time
        int duration_min
        string location
        int capacity
        int trainer_id FK
    }
    BOOKING {
        int id PK
        int client_id FK
        int session_id FK
        string status "active | cancelled"
        datetime created_at
    }
    NOTIFICATION {
        int id PK
        int client_id FK
        string message
        string type "booking | cancellation"
        boolean is_read
    }
       
