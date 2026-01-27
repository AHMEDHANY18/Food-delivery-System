# Food delivery System – README

## 📌 Project Overview
The Food delivery System is a complete platform that connects customers with restaurants.
It allows users to browse restaurants and menus, add items to a cart, place orders,
make online payments, and track order status in real time.

---

## 🚀 Features & Functions

### 1️⃣ Cart Management
**Features**
- One cart per user
- Cart is created on user registration or on first item insertion
- In-memory caching using Redis
- Persistent storage in the database

**Functions**
- Add item to cart
- Modify cart
- Update item quantities
- View cart
- Remove item from cart
- Clear cart
- Checkout

---

### 2️⃣ User Registration & Authentication
**Features**
- Complete user account management
- Email or OTP verification
- Social media authentication
- Role-based access control (RBAC)

**Functions**
- Sign up
- Login
- Logout
- Forgot password
- Email / OTP verification
- Enable / Disable account
- Role-based authorization

---

### 3️⃣ Restaurant Management
**Features**
- Full restaurant lifecycle management
- Enable / Disable restaurants
- Restaurant browsing for customers
- Advanced search with filters
- Top-rated restaurants
- Restaurant recommendations

**Functions**
- Add restaurant
- Update restaurant
- Enable / Disable restaurant
- View all restaurants
- Search restaurants
- Top-rated restaurants
- Restaurant recommendations

---

### 4️⃣ Menu Management
**Features**
- Complete menu management
- Support for categories and ingredients
- Menu change history tracking

**Functions**
- Create menu
- Update menu
- Delete menu
- View menu list
- View menu history
- Search menu items
- CRUD menu categories
- CRUD ingredients
- View ingredients (customers)

---

### 5️⃣ Order Management
**Features**
- Full order lifecycle
- Order status tracking
- Order history for customers and restaurants
- Order notifications

**Functions**
- Place order
- Cancel order (customer / restaurant)
- Update order status
- Track order
- View order history
- View order details
- Order summary
- Email / SMS order confirmation

---

### 6️⃣ Customer Management
**Features**
- Customer profile management
- Multiple delivery addresses
- Preferred payment methods
- Customer feedback and ratings
- Customer support

**Functions**
- Manage profile
- Manage delivery addresses
- Set preferred payment methods
- Rate restaurants and orders
- View order history
- Track current orders
- Deactivate account
- Customer support chat

---

### 7️⃣ Payment Integration
**Features**
- Integration with third-party payment gateways
- Multiple payment methods
- Secure payment verification
- Transaction auditing

**Functions**
- Initiate payment
- Verify and validate payment
- Handle payment failures
- Store transaction records
- Generate payment receipts
- Payment status tracking
- Audit payment transactions

---

### 8️⃣ Dashboard & Analytics
**Features**
- System-level dashboard
- Restaurant-level dashboard
- Real-time statistics and reports

**Functions**
- Count restaurants
- Count customers
- Daily and total order statistics
- Daily and total canceled orders
- Daily and total transaction amounts
- Generate daily and monthly reports
- Restaurant-specific performance reports

---

## 🛠 Technical Notes
- RESTful API architecture
- Scalable database design
- Soft delete and hard delete support
- Role-based authorization
- Designed to support thousands of restaurants
