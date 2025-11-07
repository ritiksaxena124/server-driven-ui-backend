# 🚀 Server-Driven UI Backend (NestJS)

This project implements the backend side of a **Server-Driven UI (SDUI)** architecture using **NestJS**. Its core function is to decouple the UI structure from the frontend codebase by serving dynamic UI components via JSON endpoints, alongside managing robust user **authentication** using JWT.

## ✨ Key Features

* **Dynamic UI Control:** The server dictates the UI structure, allowing instantaneous frontend changes by updating JSON files/database records on the backend.
* **Decoupled Architecture:** Separates business logic (in NestJS services) from presentation logic (in UI JSON), simplifying maintenance and updates.
* **JWT Authentication:** Secure user registration, login, and profile access using JSON Web Tokens.
* **API-First Design:** Provides dedicated endpoints for both UI components (`/ui/*`) and user management (`/auth/*`).

---

## 🛠️ Technology Stack

| Category | Technology | Purpose |
| :--- | :--- | :--- |
| **Framework** | **NestJS** | High-performance, TypeScript-based Node.js backend. |
| **Authentication** | **JWT (JSON Web Token)** | Secure, state-less authentication mechanism. |
| **Database ORM** | **TypeORM** | TypeScript ORM for interacting with the database. |
| **Database** | **SQLite / PostgreSQL (Supabase)** | Data persistence for user profiles and UI configuration. |

---

## 🔗 API Routes

The backend exposes the following primary endpoints:

| Category | Method | Endpoint | Description | Requires Auth |
| :--- | :--- | :--- | :--- | :--- |
| **Authentication** | `POST` | `/auth/register` | Create a new user account. | No |
| **Authentication** | `POST` | `/auth/login` | Log in and receive a JWT. | No |
| **Authentication** | `GET` | `/auth/profile` | Retrieve the authenticated user's profile. | **Yes** |
| **UI Components** | `GET` | `/ui/home` | Get JSON structure for the Home screen. | No |
| **UI Components** | `GET` | `/ui/auth` | Get JSON structure for the Login screen. | No |
| **UI Components** | `GET` | `/ui/register` | Get JSON structure for the Registration screen. | No |

---

## ⚙️ Local Setup and Running

### Prerequisites

* Node.js (v18+)
* npm

### Steps

1.  **Clone the repository:**
    ```sh
    git clone [Your Repository URL]
    cd backend
    ```

2.  **Install dependencies:**
    ```sh
    npm install
    ```

3.  **Configure Environment Variables:**
    Create a `.env` file in the root of the `backend` directory to configure your database connection and JWT secret.

4.  **Run the development server:**
    ```sh
    npm run start:dev
    ```
    The server should now be running, typically at `http://localhost:3000`.

---

## 💡 How SDUI Works Here

1.  **Frontend Request:** The mobile/web frontend makes a `GET` request to, say, `/ui/home`.
2.  **Backend Response (JSON):** The NestJS controller constructs and returns a JSON object. This object defines the UI components (e.g., `{"type": "header", "text": "Welcome Back!"}`).
3.  **Frontend Rendering:** The frontend iterates through the JSON and uses its native/web renderers for each component `type` (header, button, card, etc.) to display the interface.

This allows developers to change the order, type, and properties of UI elements **without deploying a new frontend build**.

---

## 📜 License

This project is licensed under the MIT License.