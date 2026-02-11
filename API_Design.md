# API Design Documentation

This document describes all API endpoints exactly as defined in the project scope.

---
## Important Note

In this API design, both `customerId` and `cartId` are used in requests to ensure
that the provided cart belongs to the authenticated customer.

The `customerId` is extracted from the authentication token, while the `cartId`
is provided explicitly in the request.
This validation is performed to guarantee that the customer accessing or modifying
the cart is the rightful owner of that cart.


## Cart Management

### addToCart
- signature `/api/v1/cart/add`
- input `[cartItem, customerId]`
- output `status code [201]`

---

### modifyCart
- signature `/api/v1/cart/update`
- input `[cartItem, cartId, customerId]`
- output `status code [200]`

---

### viewCart
- signature `/api/v1/cart/view`
- input `[cartId, customerId]`
- output `status code [200]`

---

### clearCart
- signature `/api/v1/cart/clear`
- input `[cartId, customerId]`
- output `status code [200]`

---

### removeItemFromCart
- signature `/api/v1/cart/remove-item`
- input `[cartItemId, cartId, customerId]`
- output `status code [200]`

---

### checkOut
- signature `/api/v1/cart/checkout`
- input `[cartId, customerId]`
- output `status code [201]`

---

### updateQuantities
- signature `/api/v1/cart/update-quantities`
- input `[cartItemId, quantity, cartId, customerId]`
- output `status code [200]`

---

## User Registration & Authentication

### signUp
- signature `/api/v1/auth/signup`
- input `[name, email, phone, password]`
- output `status code [201]`

---

### login
- signature `/api/v1/auth/login`
- input `[email, password]`
- output `status code [200]`

---

### logout
- signature `/api/v1/auth/logout`
- input `[customerId]`
- output `status code [200]`

---

### forgotPassword
- signature `/api/v1/auth/forgot-password`
- input `[email]`
- output `status code [200]`

---

### emailSmsOtpVerification
- signature `/api/v1/auth/verify`
- input `[customerId, otp]`
- output `status code [200]`

---

### userCustomerProfile
- signature `/api/v1/user/profile`
- input `[customerId]`
- output `status code [200]`

---

### socialMediaAuthentication
- signature `/api/v1/auth/social`
- input `[provider, token]`
- output `status code [200]`

---

### enableDisableAccount
- signature `/api/v1/user/status`
- input `[customerId, status]`
- output `status code [200]`

---

## Restaurant & Menu Management

### registerRestaurant
- signature `/api/v1/restaurants/register`
- input `[restaurantData, ownerId]`
- output `status code [201]`

---

### updateRestaurant
- signature `/api/v1/restaurants/update`
- input `[restaurantId, restaurantData]`
- output `status code [200]`

---

### enableDisableRestaurant
- signature `/api/v1/restaurants/status`
- input `[restaurantId, status]`
- output `status code [200]`

---

### viewRestaurants
- signature `/api/v1/restaurants/view`
- input `[]`
- output `status code [200]`

---

### createNewMenu
- signature `/api/v1/menu/create`
- input `[restaurantId, menuData]`
- output `status code [201]`

---

### updateMenu
- signature `/api/v1/menu/update`
- input `[menuId, menuData]`
- output `status code [200]`

---

### deleteMenu
- signature `/api/v1/menu/delete`
- input `[menuId]`
- output `status code [200]`

---

### enableDisableMenu
- signature `/api/v1/menu/status`
- input `[menuId, status]`
- output `status code [200]`

---

### viewMenuHistory
- signature `/api/v1/menu/history`
- input `[restaurantId]`
- output `status code [200]`

---

### searchRestaurant
- signature `/api/v1/restaurants/search`
- input `[keyword]`
- output `status code [200]`

---

### searchMenuItems
- signature `/api/v1/menu/search`
- input `[keyword]`
- output `status code [200]`

---

### topRatingRestaurants
- signature `/api/v1/restaurants/top-rated`
- input `[]`
- output `status code [200]`

---

### restaurantRecommendations
- signature `/api/v1/restaurants/recommendations`
- input `[customerId]`
- output `status code [200]`

---

## Order Management

### placeOrder
- signature `/api/v1/orders/place`
- input `[cartId, customerId]`
- output `status code [201]`

---

### cancelOrderByCustomer
- signature `/api/v1/orders/cancel`
- input `[orderId, customerId]`
- output `status code [200]`

---

### updateOrderStatus
- signature `/api/v1/orders/update-status`
- input `[orderId, status]`
- output `status code [200]`

---

### restaurantOrderHistory
- signature `/api/v1/orders/restaurant-history`
- input `[restaurantId]`
- output `status code [200]`

---

### orderSummary
- signature `/api/v1/orders/summary`
- input `[orderId]`
- output `status code [200]`

---

### orderDetails
- signature `/api/v1/orders/details`
- input `[orderId]`
- output `status code [200]`

---

### orderReturn
- signature `/api/v1/orders/return`
- input `[orderId, reason]`
- output `status code [200]`

---

### orderStatus
- signature `/api/v1/orders/status`
- input `[orderId]`
- output `status code [200]`

---

### sendSmsEmailToCustomer
- signature `/api/v1/orders/notify`
- input `[orderId]`
- output `status code [200]`

---

### pushNotification
- signature `/api/v1/notifications/push`
- input `[customerId, message]`
- output `status code [200]`

---

## Customer Management

### customerOrderHistory
- signature `/api/v1/customer/orders`
- input `[customerId]`
- output `status code [200]`

---

### preferredPaymentSettings
- signature `/api/v1/customer/payment-settings`
- input `[customerId]`
- output `status code [200]`

---

### addressManagement
- signature `/api/v1/customer/address`
- input `[customerId, addressData]`
- output `status code [200]`

---

### accountDeactivate
- signature `/api/v1/customer/deactivate`
- input `[customerId]`
- output `status code [200]`

---

### ratingAndComments
- signature `/api/v1/customer/rate`
- input `[orderId, rating, comment]`
- output `status code [200]`

---

### trackingOrderStatus
- signature `/api/v1/orders/track`
- input `[orderId]`
- output `status code [200]`

---

## Payment Integration

### paymentIntegrationWithThirdParty
- signature `/api/v1/payment/initiate`
- input `[orderId, paymentMethod]`
- output `status code [201]`

---

### viewPaymentTransactions
- signature `/api/v1/payment/transactions`
- input `[customerId]`
- output `status code [200]`

---

### generateTransactionReceipt
- signature `/api/v1/payment/receipt`
- input `[transactionId]`
- output `status code [200]`

---

### transaction
- signature `/api/v1/payment/transaction`
- input `[transactionData]`
- output `status code [201]`

---

### transactionDetails
- signature `/api/v1/payment/transaction-details`
- input `[transactionId]`
- output `status code [200]`

---

### paymentIntegrationType
- signature `/api/v1/payment/type`
- input `[]`
- output `status code [200]`

---

### paymentIntegrationConfiguration
- signature `/api/v1/payment/config`
- input `[configData]`
- output `status code [200]`

---

### auditing
- signature `/api/v1/payment/audit`
- input `[transactionId]`
- output `status code [200]`

---

### paymentStatus
- signature `/api/v1/payment/status`
- input `[transactionId]`
- output `status code [200]`

---

## Dashboard & Reports

### countRestaurants
- signature `/api/v1/dashboard/count-restaurants`
- input `[]`
- output `status code [200]`

---

### countCustomers
- signature `/api/v1/dashboard/count-customers`
- input `[]`
- output `status code [200]`

---

### dailyOrdersCount
- signature `/api/v1/dashboard/daily-orders`
- input `[date]`
- output `status code [200]`

---

### monthlyTransactionsCountMoney
- signature `/api/v1/dashboard/monthly-transactions`
- input `[month, year]`
- output `status code [200]`

---

### generateDailyTransactionsReport
- signature `/api/v1/reports/daily-transactions`
- input `[date]`
- output `status code [200]`

---

### generateMonthlyTransactionsReport
- signature `/api/v1/reports/monthly-transactions`
- input `[month, year]`
- output `status code [200]`

---
