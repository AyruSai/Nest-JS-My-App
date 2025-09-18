````markdown
# NestJS Full Project – REST API with Authentication and MySQL

This is a backend application built using **NestJS**.
It demonstrates how to build scalable and maintainable server-side applications
with core features like modules, controllers, services, authentication, and MySQL integration.

The project is inspired by the YouTube course:
[NestJS Tutorial - Full Course for Beginners](https://www.youtube.com/watch?v=Mgr5_r70OJQ)

---

## 📚 Summary

This project guides you through building a REST API with:

- Full CRUD operations using TypeORM
- JWT-based authentication
- Class validation using decorators
- Protected routes with PassportJS
- Environment-based configuration
- Request payload validation and stripping unwanted data
- Modular structure (User, Auth, Profile modules)


## 🔧 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/AyruSai/Nest-JS-My-App.git
cd <project-directory>
````

### 2. Install Dependencies

```bash
npm install
```

### 3. Set Up Environment Variables

Create a `.env` file in the root directory:

```env
DB_HOST=localhost
DB_PORT=3306
DB_USERNAME=root
DB_PASSWORD=yourpassword
DB_NAME=nestdb
JWT_SECRET=secretKey
```

---

## ▶️ Running the Application

```bash
# Run in development mode
npm run start:dev
```

Visit: [http://localhost:3000](http://localhost:3000)

---

## 📫 API Endpoints

### 📁 User

| Method | Endpoint    | Description       |
| ------ | ----------- | ----------------- |
| GET    | `/user`     | Get all users     |
| GET    | `/user/:id` | Get user by ID    |
| POST   | `/user`     | Create new user   |
| PATCH  | `/user/:id` | Update user by ID |
| DELETE | `/user/:id` | Delete user by ID |

* Validation: Accepts only `name` (string), `email` (valid email), and `password` (string)
* Strips unwanted properties using class-validator + whitelist

Example `CreateUserDto`:

```ts
import { IsEmail, IsString } from 'class-validator';

export class CreateUserDto {
  @IsString()
  name: string;

  @IsEmail()
  email: string;

  @IsString()
  password: string;
}
```

---

### 🔐 Authentication

| Method | Endpoint      | Description   |
| ------ | ------------- | ------------- |
| POST   | `/auth/login` | Get JWT Token |

* Requires valid credentials from `/user`
* Returns JWT token with `Bearer` prefix

---

### 🔒 Protected Routes

| Method | Endpoint   | Description            |
| ------ | ---------- | ---------------------- |
| GET    | `/profile` | Get user profile (JWT) |

* Requires Bearer token in header:
  `Authorization: Bearer <JWT_TOKEN>`

---

## 🧪 Testing

NestJS comes with built-in testing tools.

```bash
# Run unit tests
npm run test

# Run e2e tests
npm run test:e2e
```

---

## 📁 Project Structure (Top Level)

```
src/
├── app.controller.ts
├── app.module.ts
├── auth
│   ├── auth.constant.ts
│   ├── auth.controller.spec.ts
│   ├── auth.controller.ts
│   ├── auth.module.ts
│   ├── auth.service.spec.ts
│   ├── auth.service.ts
│   ├── jwt.strategy.ts
│   └── local.strategy.ts
├── main.ts
├── profile
│   ├── profile.controller.spec.ts
│   ├── profile.controller.ts
│   └── profile.module.ts
└── user
    ├── dto
    ├── entity
    ├── user.controller.spec.ts
    ├── user.controller.ts
    ├── user.module.ts
    ├── user.service.spec.ts
    └── user.service.ts
```

---

## 🛠️ Technologies Used

* NestJS
* TypeORM
* MySQL
* Passport JWT
* Class Validator
* dotenv

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
