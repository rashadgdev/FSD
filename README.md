---

# Feature-Sliced Design (FSD) Architecture

This project follows the **Feature-Sliced Design (FSD)** pattern, a modular architecture pattern aimed at improving scalability, maintainability, and code quality in large applications. In this approach, we focus primarily on organizing the application into **pages** that encapsulate specific features and their related components.

## Overview

Feature-Sliced Design (FSD) divides your application into **pages** (or features), ensuring that each part of the application is organized around domain logic. This results in better modularization, scalability, and separation of concerns. 

## Folder Structure

```
src/
  app/
    providers/             ← Core app providers (e.g., theme, authentication)
    routes/                ← Routing setup for the app
  pages/
    home/
      api/                 ← API logic related to the home page
      components/          ← UI components specific to the home page
      hooks/               ← Custom hooks for home page
      lib/                 ← Helper functions related to the home page
      providers/           ← Context providers specific to the home page
      Home.tsx             ← The page component itself (entry point for the page)
  shared/
    api/                   ← Shared API services and helpers
    components/            ← Reusable UI components (buttons, forms, etc.)
    hooks/                 ← Shared hooks (useDebounce, useFetch, etc.)
    lib/                   ← Shared utilities (validation, logging, etc.)
    types/                 ← Shared types/interfaces used across pages
  assets/                  ← Static assets (images, fonts, etc.)
  index.ts                 ← Entry point for the app
  App.tsx                  ← App setup and routing
```

---

## Folder Breakdown

### **`app/`** - Global configuration and setup
- **`providers/`**: Contains providers that are used globally throughout the application, such as `ThemeProvider`, `AuthProvider`, `HttpClientProvider`.
- **`routes/`**: Holds route configuration and routing logic for the app. This is where the main `AppRoutes` are defined.

### **`pages/`** - Pages in the application
Each **page** is self-contained and encapsulates everything related to that page (UI, state management, API logic). Pages can include:
- **`api/`**: Services related to interacting with an API for that specific page (e.g., `getUserData`, `getPosts`).
- **`components/`**: UI components specific to that page (e.g., `Header`, `Footer`, `ProfileCard`).
- **`hooks/`**: Custom React hooks scoped to the page (e.g., `useFetchData`, `useSubmitForm`).
- **`lib/`**: Helper functions related to the page (e.g., form validation, date formatting).
- **`providers/`**: Context providers specific to that page, such as managing local page-level state or context.
- **`PageName.tsx`**: The main page component (entry point) that organizes the page structure and connects the components, hooks, and other logic.

### **`shared/`** - Shared code that can be reused across pages
- **`api/`**: Shared services that can be used by any page (e.g., `httpClient.ts`).
- **`components/`**: Reusable UI components that can be used across pages (e.g., buttons, modals, form elements).
- **`hooks/`**: Reusable hooks used across the app (e.g., `useDebounce`, `useFetchData`).
- **`lib/`**: Shared utilities that can be used by all pages (e.g., formatting functions, logging, or validation utilities).
- **`types/`**: Shared TypeScript types/interfaces used across pages.

### **`assets/`** - Static assets such as images, fonts, and other media.

---

## Why Feature-Sliced Design (FSD) for Pages?

### **Modularity**
FSD organizes the application around pages, with each page being self-contained. This modularity makes it easier to develop, maintain, and scale your application as you can focus on a single page at a time. 

### **Separation of Concerns**
By dividing the app into pages and ensuring each page has its own logic, components, hooks, and API services, FSD ensures that there’s a clear separation of concerns. Pages can manage their own local state and interactions without affecting other parts of the app.

### **Reusability**
Pages can reuse shared components, hooks, and utilities from the `shared/` folder, which promotes consistency and reduces code duplication across pages. For example, a button component in `shared/components/Button.tsx` can be reused in multiple pages.

### **Scalability**
As your app grows and more pages are added, FSD allows for easy scaling. You can add a new page by creating a folder under the `pages/` directory, and within it, organize its components, hooks, and API services. This results in a clear and scalable project structure.

---

## Example: Home Page Structure

```
/pages/home/
  api/
    getUserData.ts         ← API service for fetching user data
  components/
    ProfileCard.tsx        ← UI component for showing a user profile
  hooks/
    useFetchUserData.ts    ← Custom hook to fetch user data
  lib/
    validateUser.ts        ← Helper function to validate user input
  providers/
    UserContext.tsx        ← Context provider for managing user state
  Home.tsx                 ← The main component that uses all the above parts
```

---

## Best Practices

- **Page Isolation**: Keep each page isolated from other pages to reduce dependencies. Only share common logic through the `shared/` folder.
- **Reusable Components**: For components that are used across different pages, place them in the `shared/components/` folder.
- **Custom Hooks**: Define hooks in the `shared/hooks/` folder if they are generic and reusable across pages. Use page-specific hooks only when necessary.
- **Types**: Shared types should reside in `shared/types/`, while page-specific types should be placed within the page folder.

---

## Conclusion

Feature-Sliced Design (FSD) focuses on organizing the application by **pages** instead of layers, making it easier to manage, scale, and maintain. By following this approach, your codebase will be modular, reusable, and easy to extend with new features or pages. 

This architecture helps you maintain a clear structure as your application grows, with each page encapsulating its own logic, components, and services, while still allowing shared resources to be reused across the app.

---

i need this in azerbaijani
