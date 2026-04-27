🚀✨🔐—📝—👤—🏗️—🛡️—🐳—✅—📊—🌐—🛠️📂├──│└──│└──├──│├──│├──│├──│├──│├──│└──├──│└──├──nv.example                 # Environment variables template
├── Dockerfile                   # Docker configuration
├── docker-compose.yml           # Docker Compose setup
├── go.mod
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- Go 1.22 or higher
- Docker (optional)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/ninjadiego/taskflow-api.git
   cd taskflow-api
   ```

2. **Install dependencies**
3.    ```bash
         go mod download
         ```

  3. **Configure environment**
  4.    ```bash
           cp .env.example .env
           ```

    4. **Run the server**
       ```bash
          go run cmd/server/main.go
             ```
             
             The API will be available at `http://localhost:8080`
             
             ### Run with Docker
             
             ```bash
             docker-compose up --build
             ```
             
             ---
             
             ## 📡 API Endpoints
             
             ### Authentication
             
             | Method | Endpoint | Description | Auth |
             |--------|----------|-------------|------|
             | POST | `/api/v1/auth/register` | Register a new user | ❌ |
             | POST | `/api/v1/auth/login` | Login and receive JWT | ❌ |
             
             ### Tasks (Protected)
             
             | Method | Endpoint | Description | Auth |
             |--------|----------|-------------|------|
             | GET | `/api/v1/tasks` | List user's tasks | ✅ |
             | POST | `/api/v1/tasks` | Create a new task | ✅ |
             | GET | `/api/v1/tasks/:id` | Get task by ID | ✅ |
             | PUT | `/api/v1/tasks/:id` | Update a task | ✅ |
             | DELETE | `/api/v1/tasks/:id` | Delete a task | ✅ |
             
             ### Health
             
             | Method | Endpoint | Description |
             |--------|----------|-------------|
             | GET | `/health` | Service health check |
             
             ---
             
             ## 📝 Usage Examples
             
             ### Register a new user
             
             ```bash
             curl -X POST http://localhost:8080/api/v1/auth/register \
               -H "Content-Type: application/json" \
                 -d '{
                     "email": "user@example.com",
                         "password": "SecurePass123",
                             "name": "John Doe"
                               }'
                               ```
                               
                               ### Login
                               
                               ```bash
                               curl -X POST http://localhost:8080/api/v1/auth/login \
                                 -H "Content-Type: application/json" \
                                   -d '{
                                       "email": "user@example.com",
                                           "password": "SecurePass123"
                                             }'
                                             ```
                                             
                                             ### Create a task
                                             
                                             ```bash
                                             curl -X POST http://localhost:8080/api/v1/tasks \
                                               -H "Authorization: Bearer YOUR_JWT_TOKEN" \
                                                 -H "Content-Type: application/json" \
                                                   -d '{
                                                       "title": "Learn Go",
                                                           "description": "Master Go programming language",
                                                               "status": "pending"
                                                                 }'
                                                                 ```
                                                                 
                                                                 ---
                                                                 
                                                                 ## 🧪 Testing
                                                                 
                                                                 ```bash
                                                                 go test ./... -v -cover
                                                                 ```
                                                                 
                                                                 ---
                                                                 
                                                                 ## 🗺️ Roadmap
                                                                 
                                                                 - [ ] PostgreSQL support
                                                                 - [ ] Redis caching
                                                                 - [ ] Pagination and filtering
                                                                 - [ ] Task categories and tags
                                                                 - [ ] Email notifications
                                                                 - [ ] OpenAPI / Swagger documentation
                                                                 - [ ] CI/CD with GitHub Actions
                                                                 - [ ] Kubernetes deployment manifests
                                                                 
                                                                 ---
                                                                 
                                                                 ## 🤝 Contributing
                                                                 
                                                                 Contributions are welcome! Please feel free to submit a Pull Request.
                                                                 
                                                                 1. Fork the project
                                                                 2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
                                                                 3. Commit your changes (`git commit -m 'feat: add some AmazingFeature'`)
                                                                 4. Push to the branch (`git push origin feature/AmazingFeature`)
                                                                 5. Open a Pull Request
                                                                 
                                                                 ---
                                                                 
                                                                 ## 📄 License
                                                                 
                                                                 Distributed under the MIT License. See [`LICENSE`](LICENSE) for more information.
                                                                 
                                                                 ---
                                                                 
                                                                 ## 👨‍#💻 Author
                                                                 
                                                                 **Diego** — [@ninjadiego](https://github.com/ninjadiego)
                                                                 
                                                                 Project Link: [https://github.com/ninjadiego/taskflow-api](https://github.com/ninjadiego/taskflow-api)
                                                                 
                                                                 ---
                                                                 
                                                                 <p align="center">Built with ❤️ and Go</p>
                                                                 
🚀 RESTful API for task management built with Go, Gin, JWT authentication, and SQLite. Clean architecture, Docker-ready, and production-grade.
