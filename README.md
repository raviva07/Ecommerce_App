# 🛒 E-Commerce Platform (Spring Boot + React)

A full-stack E-Commerce web application with authentication, product management, cart system, order processing, and payment integration.

---

## 🚀 Features

### 👤 Authentication & Authorization

* JWT-based authentication
* Role-based access (ADMIN / USER)
* Secure APIs with Spring Security

---

### 🛍️ Product Management (Admin)

* Add product (Multipart / JSON)
* Upload images via:

  * File upload (Cloudinary)
  * Image URL (Google / external → Cloudinary)
* Update product
* Soft delete (mark inactive)
* Search products

---

### 🛒 Cart System

* Add to cart
* Update quantity
* Remove item
* Clear cart
* Auto total calculation

---

### 📦 Order Management

* Create order from cart
* View user orders
* Admin: View all orders
* Update order status
* Cancel order (with stock restore)

---

### 💳 Payment Integration

* Razorpay integration
* Payment verification
* Order status update after payment

---

### ☁️ Image Upload

* Cloudinary integration
* Upload via file or URL
* Stores optimized CDN images

---

## 🛠️ Tech Stack

### Backend

* Java 17
* Spring Boot
* Spring Security (JWT)
* Spring Data JPA
* Hibernate
* MySQL

### Frontend

* React.js
* Redux Toolkit
* Axios

### Tools

* Swagger (API Testing)
* Postman
* Cloudinary
* Razorpay

---

## ⚙️ Setup Instructions

### 1️⃣ Clone Repository

```bash
git clone https://github.com/your-username/ecommerce-platform.git
cd ecommerce-platform
```

---

### 2️⃣ Backend Setup

#### Configure `application.properties`

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce_db
spring.datasource.username=root
spring.datasource.password=yourpassword

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# JWT
jwt.secret=your_secret_key

# Cloudinary
cloudinary.cloud-name=your_cloud_name
cloudinary.api-key=your_api_key
cloudinary.api-secret=your_api_secret

# Razorpay
razorpay.key=your_key
razorpay.secret=your_secret
```

---

### 3️⃣ Run Backend

```bash
mvn clean install
mvn spring-boot:run
```

Server runs at:

```
http://localhost:8080
```

---

### 4️⃣ Swagger API Docs

```
http://localhost:8080/swagger-ui/index.html
```

---

## 🔐 IMPORTANT: Admin Registration (Swagger)

👉 There is **no public admin signup API**

### To create ADMIN:

1. Open Swagger UI
2. Use **Register API** (normal user registration)
3. Create a user
4. Go to database (`users` table)
5. Change role:

```
ROLE_USER → ROLE_ADMIN
```

✅ Now login as admin and access admin APIs

---

## 📸 Image Upload APIs

### 1️⃣ Upload Image via URL (Cloudinary)

```
POST /api/products/upload-url
```

```json
{
  "imageUrl": "https://example.com/image.jpg"
}
```

✅ Returns Cloudinary URL

---

### 2️⃣ Create Product (Multipart)

```
POST /api/products (form-data)
```

Fields:

* name
* description
* price
* stock
* category
* file (optional)
* files (optional)
* imageUrl (optional)

---

### 3️⃣ Create Product (JSON)

```
POST /api/products
```

```json
{
  "name": "Phone",
  "description": "Good phone",
  "price": 15000,
  "stock": 10,
  "category": "Electronics",
  "imageUrl": "cloudinary-url"
}
```

---

## 🛒 API Endpoints

### 🔹 Auth

* POST `/api/auth/register`
* POST `/api/auth/login`

---

### 🔹 Products

* GET `/api/products`
* GET `/api/products/{id}`
* GET `/api/products/search?keyword=phone`
* POST `/api/products` (Admin)
* PUT `/api/products/{id}` (Admin)
* DELETE `/api/products/{id}` (Admin)

---

### 🔹 Cart

* GET `/api/cart`
* POST `/api/cart/add`
* PUT `/api/cart/update`
* DELETE `/api/cart/remove`
* DELETE `/api/cart/clear`

---

### 🔹 Orders

* POST `/api/orders`
* GET `/api/orders/my`
* GET `/api/orders/all` (Admin)
* PUT `/api/orders/{id}/status` (Admin)
* PUT `/api/orders/{id}/cancel`
* PUT `/api/orders/{id}/admin-cancel`

---

## 🧪 Running Tests

```bash
mvn test
```

---

## 📦 Deployment

### Backend

* Render / Railway / AWS

### Frontend

* Netlify / Vercel

---

## 📌 Notes

* All admin APIs require JWT token
* Use Swagger for testing APIs
* Ensure Cloudinary & Razorpay keys are valid
* Product images are stored in Cloudinary

---

## 👨‍💻 Author

**Ravi Varma**

---

## ⭐ If you like this project

Give it a ⭐ on GitHub!
