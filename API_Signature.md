# API Design Documentation

This document describes all API endpoints exactly as defined in the project scope.

---

## Important Note

In this API design, both `customerId` and `cartId` are used in requests to ensure
that the provided cart belongs to the authenticated customer.

The `customerId` is extracted from the authentication token, while the `cartId`
is provided explicitly in the request.

This validation guarantees that the customer accessing or modifying
the cart is the rightful owner of that cart.

---

## Standard Response Structure

### ✅ Success Response

```json
{
  "success": true,
  "message": "Operation completed successfully",
  "data": {},
  "code": 200
}
````

### ❌ Error Response

```json
{
  "success": false,
  "message": "Error description",
  "error": "ErrorType",
  "code": 400
}
```

### Common Error Codes

* 400 → Bad Request
* 401 → Unauthorized
* 403 → Forbidden
* 404 → Not Found
* 409 → Conflict
* 500 → Internal Server Error

---

# Cart Management

### addToCart

* signature `/api/v1/cart/add`
* input `[cartItem, customerId]`
* output Success Response (201)
* error 400, 401, 409

---

### modifyCart

* signature `/api/v1/cart/update`
* input `[cartItem, cartId, customerId]`
* output Success Response (200)
* error 400, 401, 404

---

### viewCart

* signature `/api/v1/cart/view`
* input `[cartId, customerId]`
* output Success Response (200)
* error 401, 404

---

### clearCart

* signature `/api/v1/cart/clear`
* input `[cartId, customerId]`
* output Success Response (200)
* error 401, 404

---

### removeItemFromCart

* signature `/api/v1/cart/remove-item`
* input `[cartItemId, cartId, customerId]`
* output Success Response (200)
* error 401, 404

---

### checkOut

* signature `/api/v1/cart/checkout`
* input `[cartId, customerId]`
* output Success Response (201)
* error 400, 401, 409

---

### updateQuantities

* signature `/api/v1/cart/update-quantities`
* input `[cartItemId, quantity, cartId, customerId]`
* output Success Response (200)
* error 400, 401, 404

---

# User Registration & Authentication

### signUp

* signature `/api/v1/auth/signup`
* input `[name, email, phone, password]`
* output Success Response (201)
* error 400, 409

---

### login

* signature `/api/v1/auth/login`
* input `[email, password]`
* output Success Response (200)
* error 401, 403

---

### logout

* signature `/api/v1/auth/logout`
* input `[customerId]`
* output Success Response (200)
* error 401

---

### forgotPassword

* signature `/api/v1/auth/forgot-password`
* input `[email]`
* output Success Response (200)
* error 404

---

### emailSmsOtpVerification

* signature `/api/v1/auth/verify`
* input `[customerId, otp]`
* output Success Response (200)
* error 400, 401

---

### userCustomerProfile

* signature `/api/v1/user/profile`
* input `[customerId]`
* output Success Response (200)
* error 401, 404

---

### socialMediaAuthentication

* signature `/api/v1/auth/social`
* input `[provider, token]`
* output Success Response (200)
* error 400, 401

---

### enableDisableAccount

* signature `/api/v1/user/status`
* input `[customerId, status]`
* output Success Response (200)
* error 401, 403

---

# Restaurant & Menu Management

### registerRestaurant

* signature `/api/v1/restaurants/register`
* input `[restaurantData, ownerId]`
* output Success Response (201)
* error 400, 401

---

### updateRestaurant

* signature `/api/v1/restaurants/update`
* input `[restaurantId, restaurantData]`
* output Success Response (200)
* error 400, 401, 404

---

### enableDisableRestaurant

* signature `/api/v1/restaurants/status`
* input `[restaurantId, status]`
* output Success Response (200)
* error 401, 403

---

### viewRestaurants

* signature `/api/v1/restaurants/view`
* input `[]`
* output Success Response (200)
* error 500

---

# Order Management

### placeOrder

* signature `/api/v1/orders/place`
* input `[cartId, customerId]`
* output Success Response (201)
* error 400, 401, 409

---

### cancelOrderByCustomer

* signature `/api/v1/orders/cancel`
* input `[orderId, customerId]`
* output Success Response (200)
* error 401, 404

---

### updateOrderStatus

* signature `/api/v1/orders/update-status`
* input `[orderId, status]`
* output Success Response (200)
* error 400, 404

---

### orderSummary

* signature `/api/v1/orders/summary`
* input `[orderId]`
* output Success Response (200)
* error 404

---

### orderDetails

* signature `/api/v1/orders/details`
* input `[orderId]`
* output Success Response (200)
* error 404

---

### orderReturn

* signature `/api/v1/orders/return`
* input `[orderId, reason]`
* output Success Response (200)
* error 400, 404

---

### orderStatus

* signature `/api/v1/orders/status`
* input `[orderId]`
* output Success Response (200)
* error 404

---

### sendSmsEmailToCustomer

* signature `/api/v1/orders/notify`
* input `[orderId]`
* output Success Response (200)
* error 500

---

### pushNotification

* signature `/api/v1/notifications/push`
* input `[customerId, message]`
* output Success Response (200)
* error 500

---

# Payment Integration

### paymentIntegrationWithThirdParty

* signature `/api/v1/payment/initiate`
* input `[orderId, paymentMethod]`
* output Success Response (201)
* error 400, 401

---

### paymentStatus

* signature `/api/v1/payment/status`
* input `[transactionId]`
* output Success Response (200)
* error 404

---

# Dashboard & Reports

### countRestaurants

* signature `/api/v1/dashboard/count-restaurants`
* input `[]`
* output Success Response (200)
* error 500

---

### countCustomers

* signature `/api/v1/dashboard/count-customers`
* input `[]`
* output Success Response (200)
* error 500

---

### dailyOrdersCount

* signature `/api/v1/dashboard/daily-orders`
* input `[date]`
* output Success Response (200)
* error 400

---

### monthlyTransactionsCountMoney

* signature `/api/v1/dashboard/monthly-transactions`
* input `[month, year]`
* output Success Response (200)
* error 400

---

### generateDailyTransactionsReport

* signature `/api/v1/reports/daily-transactions`
* input `[date]`
* output Success Response (200)
* error 400

---

### generateMonthlyTransactionsReport

* signature `/api/v1/reports/monthly-transactions`
* input `[month, year]`
* output Success Response (200)
* error 400

```

