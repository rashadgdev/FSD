---

# Feature-Sliced Design (FSD) Architecture

This project follows the **Feature-Sliced Design (FSD)** pattern, a modular architecture pattern aimed at improving scalability, maintainability, and code quality in large applications. In this approach, we organize the application around **pages**, **features**, **entities**, and **shared resources**, ensuring a clear and consistent structure.

## Overview

Feature-Sliced Design (FSD) divides your application into meaningful segments such as **pages**, **features**, **entities**, and **shared**, allowing better modularization, scalability, and separation of concerns.

## Folder Structure

```
src/
  app/
    providers/             ← Global providers (e.g., servicesProvider)
      servicesProvider.tsx
      index.ts             ← Export providers
    routes/                ← Routing logic and route constants
      routes.tsx
      consts.ts
      index.ts             ← Export routing

  pages/
    view-guarantee/
      api/                 ← API requests with React Query
      lib/                 ← Utilities and helpers
      models/              ← UI-related models
      ui/                  ← Page-specific UI components (no nested components folder)

  entities/
    guaranteeLetters/
      api/                 ← API service and request logic
      models/              ← Interfaces and business models

  features/
    table-guarantee/
      api/                 ← Feature-specific API services
      lib/                 ← Feature utilities
      models/              ← Feature models/interfaces
      ui/                  ← UI components related to this feature

  shared/
    components/            ← Reusable UI components (buttons, inputs, etc.)
    hooks/                 ← Shared hooks (e.g., useParams.ts)
      useParams.ts
      index.ts             ← Exports all shared hooks
    lib/                   ← Shared utilities (validation, formatting, etc.)
    models/                ← Shared types/interfaces
    services/              ← Cross-cutting services (permission, env, notification, etc.)
      index.ts             ← Export all services
    enums/                 ← Enums used across the app
    const.ts               ← Shared constants

  assets/                  ← Static assets (images, fonts, etc.)
  index.ts                 ← App entry point
  App.tsx                  ← App configuration and route mounting
```

---

## Folder Breakdown

### **`app/`** - Application-level setup
- **`providers/`**: Includes global providers like `servicesProvider.tsx`. All providers are exported via `index.ts`.
- **`routes/`**: Contains routing configuration (`routes.tsx`), route constants (`consts.ts`), and exports via `index.ts`.

### **`pages/`** - Top-level views
Each **page** represents a view layer and is self-contained with its own structure:
- **`api/`**: Contains API services using React Query. Instead of splitting into `hooks/` or `queries/`, we keep it unified as `api/`.
- **`lib/`**: Page-specific utilities (e.g., data transformation, helpers).
- **`models/`**: Page-specific UI types/interfaces.
- **`ui/`**: Direct UI components related only to this page.

### **`entities/`** - Business logic and core domain services
- **`api/`**: Business service API logic, such as handling requests and endpoints.
- **`models/`**: Domain models/interfaces for the entity.

### **`features/`** - Functional components that add value to pages
- **`api/`**: Feature-specific API requests.
- **`lib/`**: Feature logic and helpers.
- **`models/`**: Interfaces/models for the feature.
- **`ui/`**: UI components related to the feature, like modals, tables, etc.

### **`shared/`** - Reusable and common logic
- **`components/`**: Reusable UI components shared across the app.
- **`hooks/`**: Shared hooks named explicitly (e.g., `useParams.ts`), all exported through `index.ts`.
- **`lib/`**: Utility functions for validation, formatting, etc.
- **`models/`**: Shared TypeScript interfaces and types.
- **`services/`**: App-wide services like `PermissionService`, `EnvService`, `NotificationService`, and others, all exported through `index.ts`.
- **`enums/`**: Enums used across multiple layers.
- **`const.ts`**: Shared constants.

---

## Why Feature-Sliced Design (FSD)?

### **Modularity**
FSD emphasizes modular design where each folder serves a distinct purpose. Pages, features, and entities are well-isolated and reusable.

### **Separation of Concerns**
Responsibilities are clearly split between domain (entities), UI/UX (features and pages), and global logic (shared).

### **Reusability**
Features and shared components/hooks/services ensure maximum reuse, especially when it comes to business logic or UI components.

### **Scalability**
New features, entities, and pages can be easily added without disrupting existing structures, making the architecture scale smoothly.

---

## Best Practices

- **Keep page logic isolated** in its own folder.
- **Use the `features/` folder** for high-value units like modals or data tables.
- **Place domain-level logic** in the `entities/` folder.
- **Export services/hooks/components cleanly** through `index.ts` files.
- **Use explicit names** for hooks (`useSomething.ts`) instead of generic names.

---

## Conclusion

Feature-Sliced Design (FSD) focuses on organizing the application by **functional boundaries** like pages, features, entities, and shared logic. This structure ensures a scalable, maintainable, and understandable codebase. With clear separation of concerns and modularity at its core, FSD provides an ideal foundation for growing applications with complex business requirements.

---

