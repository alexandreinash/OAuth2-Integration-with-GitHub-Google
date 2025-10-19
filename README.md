# 🧩 OAuth2 Integration with GitHub & Google

A Spring Boot application that integrates **OAuth2 login** using **GitHub** and **Google**, with a secure **user profile management** feature.

---

## 📘 Overview

This project demonstrates OAuth2 integration using **Spring Security** and **Spring Boot**, allowing users to log in via **Google** or **GitHub**.  
Once authenticated, user data is persisted in a relational database (H2 by default). Users can then **view** and **edit** their profile.

---

## 🚀 Features

✅ Login via **Google** or **GitHub** using OAuth2  
✅ Automatically creates a user record on first login  
✅ View and update your **display name** and **bio**  
✅ Secure logout and session management  
✅ Profile picture and email synchronization  
✅ CSRF and frame protection configured for H2 Console

---

## 🧠 Architecture

### 📂 Core Components

| Layer | Package | Description |
|-------|----------|-------------|
| Configuration | `config` | Handles security configuration and OAuth2 login setup. |
| Controller | `controller` | Manages routing for home, profile, and user actions. |
| Model | `model` | Defines JPA entities: `User` and `AuthProvider`. |
| Repository | `repository` | JPA repositories for entity persistence. |
| Service | `service` | Custom `OAuth2UserService` to handle provider-specific logic. |

---

## ⚙️ Tech Stack

| Component | Technology |
|------------|-------------|
| **Backend** | Spring Boot 3, Spring Security, OAuth2 Client |
| **Database** | H2 (In-memory, for development) |
| **Frontend** | Thymeleaf (for simplicity) |
| **Build Tool** | Maven |
| **Language** | Java 17+ |

---

## 🏗️ Project Structure

src/
└── main/
├── java/edu/cit/nashdinapo/oauth2integration/
│ ├── config/
│ │ └── SecurityConfig.java
│ ├── controller/
│ │ ├── HomeController.java
│ │ └── ProfileController.java
│ ├── model/
│ │ ├── User.java
│ │ └── AuthProvider.java
│ ├── repository/
│ │ ├── UserRepository.java
│ │ └── AuthProviderRepository.java
│ └── service/
│ └── CustomOAuth2UserService.java
├── resources/
│ ├── templates/
│ │ ├── home.html
│ │ └── profile.html
│ ├── application.properties
│ └── static/
└── ...

yaml
Copy code

---

## ⚙️ Configuration

Set the following environment variables before running:

### 🧩 Google OAuth2
```properties
spring.security.oauth2.client.registration.google.client-id=${GOOGLE_CLIENT_ID}
spring.security.oauth2.client.registration.google.client-secret=${GOOGLE_CLIENT_SECRET}
🧩 GitHub OAuth2
properties
Copy code
spring.security.oauth2.client.registration.github.client-id=${GITHUB_CLIENT_ID}
spring.security.oauth2.client.registration.github.client-secret=${GITHUB_CLIENT_SECRET}
You can obtain these from:

Google Cloud Console

GitHub Developer Settings

🧪 Run Locally
1️⃣ Clone Repository
bash
Copy code
git clone https://github.com/<your-username>/oauth2integration.git
cd oauth2integration
2️⃣ Configure Environment Variables
Create a .env file or export variables:

bash
Copy code
export GOOGLE_CLIENT_ID=your_google_client_id
export GOOGLE_CLIENT_SECRET=your_google_client_secret
export GITHUB_CLIENT_ID=your_github_client_id
export GITHUB_CLIENT_SECRET=your_github_client_secret
3️⃣ Run the Application
bash
Copy code
mvn spring-boot:run
4️⃣ Access the App
Visit:
👉 http://localhost:8080

🧑‍💻 Usage
Endpoint	Description
/	Landing page with Google and GitHub login buttons
/profile	Displays and allows editing of user profile
/logout	Logs out user and redirects to home

💾 Example Entities
User
Field	Type	Description
id	Long	Primary key
email	String	User email
displayName	String	Display name
avatarUrl	String	Profile picture
bio	String	User bio
createdAt	LocalDateTime	Date created
updatedAt	LocalDateTime	Last updated

AuthProvider
Field	Type	Description
id	Long	Primary key
provider	String	OAuth provider (GOOGLE/GITHUB)
providerUserId	String	Provider-specific user ID
providerEmail	String	Provider email
user	User	Linked user entity

🧰 Security Highlights
CSRF protection enabled, with exception for /h2-console/**

Frame options configured for same-origin (H2 Console)

OAuth2 login with CustomOAuth2UserService

Session-based authentication (no JWT required)

🖼️ UI Overview
🏠 Home Page
Glassmorphism design with animated background

Buttons for Google and GitHub login

👤 Profile Page
Displays user name, email, and avatar

Editable display name and bio

Styled with gradients and animations

🧑‍🏫 Author
Alexandrei Nash Dinapo
📍 CIT University
📧 alexandreinash.dinapo@cit.edu

📅 Submission Details
Due: October 22, 2025 – 11:59 PM
Closes: October 24, 2025 – 11:59 PM

🧾 License
This project is for academic and demonstration purposes only.
© 2025 Alexandrei Nash Dinapo – All Rights Reserved.
