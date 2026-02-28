# Architecture - Home Manager

## Overview
Home Manager is a Progressive Web App that allows multiple household members to manage shared shopping lists in real-time.  
The main technology stack is:

- **Next.js** (App Router) for frontend and backend in the same project.
- **API Routes** serverless on Vercel for CRUD management.
- **PostgreSQL (Supabase)** for data persistence and realtime events.
- **Prisma ORM** for typed database interactions.
- **Clerk** for authentication and user management.
- **Tailwind CSS** for styling.

---

## System Components

- **Frontend**: Next.js + React, handles the user interface and interactions.  
- **API Layer**: API Routes for lists and items, validation and authorization.  
- **Database**: PostgreSQL via Supabase, with tables `Household`, `ShoppingList`, `GroceryItem`.  
- **Authentication**: Clerk verifies identity and access.

---

## Data Flow

1. The user interacts with the interface (adds/completes items).  
2. The request is sent to the API.  
3. The API updates the database via Prisma.  
4. Changes are notified to other users via Supabase Realtime.

---

## Authorization

- Each user belongs to a **Household**.  
- Users can only modify lists and items belonging to their own household.  
- Roles: `admin` (full management), `member` (adds/modifies items).

---

## Known Limitations

- Offline support limited to frontend static cache.  
- No advanced conflict management in the MVP.  
- Scalability beyond tens of users not yet tested.