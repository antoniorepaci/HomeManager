# Domain Model - Home Manager

## Overview
Home Manager manages shared household life, starting with shopping lists.  
The main entities for the MVP are:

- **Household**: group of users living together.  
- **User**: person who is part of a Household.  
- **ShoppingList**: shopping list of a Household.  
- **GroceryItem**: single item within a list.

---

## ER Diagram (simplified)

```mermaid
erDiagram
    USER ||--o{ HOUSEHOLD : "belongs to"
    HOUSEHOLD ||--o{ SHOPPING_LIST : "contains"
    SHOPPING_LIST ||--o{ GROCERY_ITEM : "includes"
    
    USER {
        string id PK
        string clerk_id UK
        string email
        string name
        string household_id FK
        string role
    }
    
    HOUSEHOLD {
        string id PK
        string name
        datetime created_at
    }
    
    SHOPPING_LIST {
        string id PK
        string name
        string household_id FK
        boolean is_active
        datetime created_at
    }
    
    GROCERY_ITEM {
        string id PK
        string name
        string shopping_list_id FK
        boolean is_completed
        datetime created_at
    }
```