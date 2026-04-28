# TaskFlow API

[![Go Version](https://img.shields.io/badge/Go-1.22+-00ADD8?style=flat&logo=go)](https://go.dev/)
[![Gin](https://img.shields.io/badge/Gin-Framework-008ECF?style=flat)](https://gin-gonic.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/ninjadiego/taskflow-api/pulls)

A production-ready RESTful API for task management built with **Go**, **Gin**, **JWT authentication**, and **SQLite**. Designed with clean architecture principles, fully Dockerized, and ready for deployment.

## Features

- **JWT Authentication** with secure user registration and login (bcrypt password hashing)
- - **Full CRUD operations** for task management
  - - **User-scoped tasks** so each user only accesses their own data
    - - **Clean architecture** with clear separation: handlers, services, models, middleware
      - - **Middleware-protected routes** with JWT validation
        - - **Docker-ready** with multi-stage build and docker-compose
          - - **Input validation** using go-playground/validator
            - - **SQLite database** via GORM (lightweight, embedded, zero-config)
              - - **CORS enabled** for frontend consumption
                - - **Unit tests** for services and JWT package
                  - - **CI/CD** with GitHub Actions (test, lint, build)
                   
                    - ## Tech Stack
                   
                    - | Category | Technology |
                    - |----------|------------|
                    - | Language | Go 1.22+ |
                    - | Framework | Gin |
                    - | ORM | GORM |
                    - | Database | SQLite |
                    - | Authentication | JWT (golang-jwt) |
                    - | Password Hashing | bcrypt |
                    - | Validation | go-playground/validator |
                    - | Containerization | Docker, Docker Compose |
                    - | CI/CD | GitHub Actions |
                   
                    - ## Project Structure
                   
                    - ```text
                      taskflow-api/
                        cmd/
                          server/
                            main.go              # Application entry point
                        internal/
                          config/                # Configuration management
                          handlers/              # HTTP handlers
                          middleware/            # JWT auth middleware
                          models/                # Database models
                          routes/                # Route definitions
                          services/              # Business logic
                        pkg/
                          auth/                  # JWT utilities
                        .github/
                          workflows/             # GitHub Actions CI/CD
                        .env.example             # Environment variables template
                        Dockerfile               # Docker configuration
                        docker-compose.yml       # Docker Compose setup
                        go.mod
                        README.md
                      ```

                      ## Getting Started

                      ### Prerequisites

                      - Go 1.22 or higher
                      - - Docker (optional)
                       
                        - ### Installation
                       
                        - Clone the repository:
                       
                        - ```bash
                          git clone https://github.com/ninjadiego/taskflow-api.git
                          cd taskflow-api
                          ```

                          Install dependencies:

                          ```bash
                          go mod download
                          ```

                          Configure environment variables:

                          ```bash
                          cp .env.example .env
                          ```

                          Run the server:

                          ```bash
                          go run cmd/server/main.go
                          ```

                          The API will be available at `http://localhost:8080`.

                          ### Run with Docker

                          ```bash
                          docker-compose up --build
                          ```

                          ## API Endpoints

                          ### Authentication

                          | Method | Endpoint | Description | Auth Required |
                          |--------|----------|-------------|:-------------:|
                          | POST | `/api/v1/auth/register` | Register a new user | No |
                          | POST | `/api/v1/auth/login` | Login and receive JWT | No |

                          ### Tasks (Protected)

                          | Method | Endpoint | Description | Auth Required |
                          |--------|----------|-------------|:-------------:|
                          | GET | `/api/v1/tasks` | List user's tasks | Yes |
                          | POST | `/api/v1/tasks` | Create a new task | Yes |
                          | GET | `/api/v1/tasks/:id` | Get task by ID | Yes |
                          | PUT | `/api/v1/tasks/:id` | Update a task | Yes |
                          | DELETE | `/api/v1/tasks/:id` | Delete a task | Yes |

                          ### Health

                          | Method | Endpoint | Description |
                          |--------|----------|-------------|
                          | GET | `/health` | Service health check |

                          ## Usage Examples

                          ### Register a new user

                          ```bash
                          curl -X POST http://localhost:8080/api/v1/auth/register \
                            -H "Content-Type: application/json" \
                            -d '{"email":"user@example.com","password":"SecurePass123","name":"John Doe"}'
                          ```

                          ### Login

                          ```bash
                          curl -X POST http://localhost:8080/api/v1/auth/login \
                            -H "Content-Type: application/json" \
                            -d '{"email":"user@example.com","password":"SecurePass123"}'
                          ```

                          ### Create a task

                          ```bash
                          curl -X POST http://localhost:8080/api/v1/tasks \
                            -H "Authorization: Bearer YOUR_JWT_TOKEN" \
                            -H "Content-Type: application/json" \
                            -d '{"title":"Learn Go","description":"Master Go programming","status":"pending"}'
                          ```

                          ## Testing

                          ```bash
                          go test ./... -v -cover
                          ```

                          ## Roadmap

                          - PostgreSQL support
                          - - Redis caching
                            - - Pagination and filtering
                              - - Task categories and tags
                                - - Email notifications
                                  - - OpenAPI / Swagger documentation
                                    - - Kubernetes deployment manifests
                                     
                                      - ## Contributing
                                     
                                      - Contributions are welcome. Please feel free to submit a Pull Request.
                                     
                                      - 1. Fork the project
                                        2. 2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
                                           3. 3. Commit your changes (`git commit -m 'feat: add some AmazingFeature'`)
                                              4. 4. Push to the branch (`git push origin feature/AmazingFeature`)
                                                 5. 5. Open a Pull Request
                                                   
                                                    6. ## License
                                                   
                                                    7. Distributed under the MIT License. See `LICENSE` for more information.
                                                   
                                                    8. ## Author
                                                   
                                                    9. **Diego** - [@ninjadiego](https://github.com/ninjadiego)
                                                   
                                                    10. Project Link: [https://github.com/ninjadiego/taskflow-api](https://github.com/ninjadiego/taskflow-api)
