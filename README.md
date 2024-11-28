# Little Lemon API

The **Little Lemon API** is a backend project designed to support the operations of the Little Lemon restaurant. This API enables clients to build web and mobile applications by providing endpoints to manage users, menu items, orders, and more. The API incorporates role-based access control to ensure secure and organized functionality.

---

## Features

- **User Management**: Registration, login, and role-based access control.
- **Menu Management**: Create, update, delete, and view menu items based on roles (Manager or Customer).
- **Order Management**: Place orders, assign orders to delivery crew, and track order statuses.
- **Cart Management**: Add and remove items from a cart.
- **User Group Management**: Assign users to groups (Manager or Delivery Crew) via API.
- **Filtering, Pagination, and Sorting**: Applied to endpoints for menu items and orders.
- **Throttling**: Rate-limiting for authenticated and unauthenticated users.
- **Detailed Error Handling**: Proper HTTP status codes and messages for various errors.

---

## Roles and Permissions

1. **Manager**:
   - Manage menu items.
   - View and assign users to groups.
   - View, update, and delete orders.

2. **Delivery Crew**:
   - View orders assigned to them.
   - Update the delivery status of orders.

3. **Customer**:
   - Browse menu items.
   - Add items to the cart.
   - Place and view their own orders.

Users not assigned to a specific group are treated as **Customers** by default.

---

## API Endpoints Overview

### 1. **User Management**
- **Register a new user**: `/api/users` (POST)
- **Login to get access token**: `/token/login/` (POST)
- **View current user**: `/api/users/me/` (GET)

### 2. **Menu Items**
- Customers/Delivery Crew can:
  - View all menu items: `/api/menu-items` (GET)
  - View single menu item: `/api/menu-items/{menuItem}` (GET)

- Managers can:
  - Create, update, or delete menu items.
  - Access endpoints with full permissions.

### 3. **User Group Management**
- Assign or remove users from **Manager** and **Delivery Crew** groups:
  - `/api/groups/manager/users` (GET, POST)
  - `/api/groups/delivery-crew/users` (GET, POST)

### 4. **Cart Management**
- Manage cart items for the current user:
  - `/api/cart/menu-items` (GET, POST, DELETE)

### 5. **Order Management**
- Customers can:
  - Place orders: `/api/orders` (POST)
  - View their orders: `/api/orders` (GET)

- Managers can:
  - View all orders.
  - Assign delivery crew and update statuses: `/api/orders/{orderId}` (PUT, PATCH)

- Delivery Crew can:
  - View their assigned orders: `/api/orders` (GET)
  - Update order status: `/api/orders/{orderId}` (PATCH)

---


## Additional Features

1. **Filtering, Pagination, and Sorting**:
   - Applied to `/api/menu-items` and `/api/orders`.

2. **Throttling**:
   - Rate limits for authenticated and unauthenticated users to prevent abuse.

---

