
# 📱 PROJECT DOCUMENT

## Project Name (suggested)

**Surname Family Networking App**

---

## 1. 🎯 Project Overview

This is a **private networking mobile application** built for people belonging to the **same surname and village-based family community** (approx. 5000+ members).

The app will be developed using:

* **Frontend:** Flutter
* **Backend:** Java Spring Boot
* **Database:** MySQL / PostgreSQL

Only verified family members can register and use this app.

---

## 2. 🧠 Purpose of the App

1. Help family members **list their businesses and services**.
2. Encourage members to **buy/sell within the family network**.
3. Improve **internal networking and trust**.
4. Share **important instructions, notices, and announcements**.
5. Build a **self-growing economic ecosystem** within the surname & village community.

Example:

> If a family member wants to buy a TV, they first search inside the app to find another family member who sells TVs.

---

## 3. 👥 User Roles

### 1. MEMBER (Normal User)

* Register & login
* Create profile
* View businesses
* Contact business owners
* View announcements

### 2. BUSINESS OWNER (Same as member but with business access)

* Add business/service
* Edit/delete business
* View business inquiries

### 3. ADMIN

* Approve/reject users
* Approve/reject businesses
* Create announcements
* Delete fake users/businesses
* Broadcast messages

---

## 4. 🔐 Authentication & Verification

### Registration Rules:

* Only users with:

  * Correct **surname**
  * Correct **village**
  * Valid **mobile number**
* Admin approves user before activation

### Login:

* Mobile number / Email + Password
* JWT Token based authentication

---

## 5. 🧩 Core Features

### 5.1 User Management

* Register user
* Login user
* Update profile
* Upload profile photo
* View other members (optional)

---

### 5.2 Business & Service Listing

Each member can:

* Add business/service
* Select category (TV shop, doctor, plumber, teacher, etc.)
* Add:

  * Business name
  * Description
  * Address
  * Contact number
  * Optional price range
* Business visible only after admin approval

---

### 5.3 Business Discovery

* Search by:

  * Business name
  * Category
  * Location
* Filter by:

  * Village
  * Service type

---

### 5.4 Announcements / Instructions

Admin can:

* Create announcements like:

  * Meetings
  * Emergency messages
  * Community rules
  * Marriage/funeral information
* All users receive notification

---

### 5.5 Contact / Networking

* Click to call business owner
* WhatsApp link
* (Optional future) In-app chat

---

## 6. 🗃️ Data Models (Entities)

### USER

```
id
fullName
surname
village
mobileNumber
email
password
profilePhoto
role (MEMBER, ADMIN)
isApproved
createdAt
```

---

### BUSINESS

```
id
ownerId (FK -> User)
businessName
category
description
address
contactNumber
priceRange
status (PENDING, APPROVED, REJECTED)
createdAt
```

---

### ANNOUNCEMENT

```
id
title
message
createdBy (Admin ID)
createdAt
```

---

### CATEGORY

```
id
name (Doctor, Electrician, Shop, Farmer, Teacher etc.)
```

---

## 7. 🔗 API DESIGN (Backend Endpoints)

### 🔐 AUTH APIs

```
POST   /api/auth/register
POST   /api/auth/login
POST   /api/auth/logout
```

---

### 👤 USER APIs

```
GET    /api/users/profile
PUT    /api/users/profile
GET    /api/users/list   (Admin)
PUT    /api/users/approve/{id} (Admin)
```

---

### 🏪 BUSINESS APIs

```
POST   /api/business/add
PUT    /api/business/update/{id}
DELETE /api/business/delete/{id}
GET    /api/business/my
GET    /api/business/all
GET    /api/business/search?category=&village=
PUT    /api/business/approve/{id} (Admin)
```

---

### 📢 ANNOUNCEMENT APIs

```
POST   /api/announcements/create (Admin)
GET    /api/announcements/all
DELETE /api/announcements/delete/{id} (Admin)
```

---

## 8. 🛡️ Security & Access Control

* JWT authentication
* Role-based authorization:

  * Only admin can approve users
  * Only admin can post announcements
* Password encrypted using BCrypt
* API protected using Spring Security

---

## 9. 🗄️ Database Design (Relations)

```
USER (1) ------ (M) BUSINESS
ADMIN (1) ---- (M) ANNOUNCEMENT
CATEGORY (1) -- (M) BUSINESS
```

---

## 10. 📲 Notification System (Optional)

* New business added
* New announcement posted
* User approved

Can use:

* Firebase Cloud Messaging (FCM)

---

## 11. 🌱 Future Enhancements (Phase 2)

* In-app chat
* Ratings & reviews
* Family tree
* Event management
* Matrimonial section
* Job posting
* Donation & fund section

---

## 12. 🛠️ Tech Stack (Backend)

* Java 17+
* Spring Boot
* Spring Security
* JWT
* Hibernate / JPA
* MySQL / PostgreSQL
* Swagger for API documentation

---

## 13. 🧾 Admin Panel (Web or App)

Admin should be able to:

* View pending users
* Approve users
* View pending businesses
* Approve businesses
* Post announcements
* Delete misuse content

---

## 14. 📌 Key Rules

* Only surname family members can register
* All businesses must be family-owned
* Admin verification mandatory
* Data is private (no public access)

---

## 15. 🎯 Final Goal

✔ Increase internal business
✔ Improve communication
✔ Build trust
✔ Strengthen family economy
✔ Digital identity for surname community

