# OmniGrowth

### Modular Microservice-Based Professional Growth Platform

OmniGrowth is a modular microservice-based platform that brings together project and process management, administration, recognition and incentives, holistic learning, and AI-assisted recommendations.

The project is designed with clear business boundaries, independent service ownership, database-per-service isolation, and a team-independent architecture.

---

## 🚀 Core Modules

### 1. Administrative Hub
Manages users, roles, permissions, authentication, authorization, and administrative operations.

### 2. Project & Process Orchestration
Manages projects, tasks, assignments, dependencies, workflow, and project progress.

### 3. Recognition & Incentives
Manages recognition, achievements, points, rewards, and reward redemption.

### 4. Holistic Learning Framework
Manages learning activities, development dimensions, enrollment, progress, and personalized learning recommendations.

---

## 🤖 AI Integration

AI is integrated to provide meaningful assistance such as:

- Personalized learning recommendations
- Progress analysis
- Recognition suggestions
- Intelligent recommendations

The project follows a **free/local-first AI approach**, avoiding mandatory paid AI APIs.

---

## 🏗️ Architecture

OmniGrowth follows a microservice-oriented architecture with independent service databases.


                    OmniGrowth
                        |
                   API Gateway
                        |
        +---------------+---------------+
        |               |               |
        v               v               v
   Admin Service   Project Service   Recognition Service
        |               |               |
     Admin DB       Project DB      Recognition DB
                                       
                        |
                        v
                 Learning Service
                        |
                   Learning DB


### Key Principles

- Microservice-oriented architecture
- Database-per-service
- Clear service boundaries
- No shared database access
- Low coupling
- Documentation-first development
- Team-independent development
- Secure service communication
- Free/local-first AI integration

---

## 🔄 Example Workflow

A typical business flow can connect multiple services without sharing databases:


Task Completed
      ↓
Project Service
      ↓
Recognition Workflow
      ↓
Contribution Evaluation
      ↓
Recognition / Points


---

## 🛠️ Technology Stack

- **Java**
- **Spring Boot**
- **Spring Data JPA**
- **Spring Security**
- **MySQL**
- **REST APIs**
- **JHipster**
- **PlantUML**
- **Docker**
- **Git / GitHub**
- **Flutter** for planned frontend integration

---

## 📁 Repository Structure


OmniGrowth/
│
├── README.md
│
├── 000-requirements/
│   ├── Project Master Document
│   ├── Software Requirements Specification
│   ├── Module Specifications
│   └── User Story Board
│
├── 000-designs/
│   ├── System & Microservice Architecture
│   ├── Architecture Blueprint
│   ├── Technical Blueprint
│   └── ER Diagram
│
└── 000-implementations/
    ├── admin-service/
    ├── project-service/
    ├── recognition-service/
    └── learning-service/
```

---

## 📚 Documentation

Detailed requirements and design information can be found in:

- **000-requirements** → Project requirements and user needs
- **000-designs** → Architecture, database design, and technical blueprints
- **000-implementations** → Actual application implementation

---

## 🚧 Project Status

**Current Phase: Requirements & Architecture → Backend Implementation**

### Completed

- [x] Project definition
- [x] Requirements specification
- [x] Module specifications
- [x] System architecture
- [x] Microservice architecture
- [x] Database / ERD design
- [x] Technical architecture documentation

### Upcoming

- [ ] JHipster backend generation
- [ ] Microservice implementation
- [ ] REST API implementation
- [ ] Database implementation
- [ ] Inter-service communication
- [ ] Security implementation
- [ ] Testing
- [ ] AI integration
- [ ] Flutter integration
- [ ] Docker / CI/CD
- [ ] End-to-end testing

---

## 🎯 Project Goals

The project focuses on practical experience with:

- Java and Spring Boot
- Microservices
- REST API development
- Database design
- Authentication and authorization
- Inter-service communication
- AI integration
- Testing
- Docker and CI/CD
- Git-based development
- End-to-end software development

---

## 👥 Team-Independent Development

The architecture is designed around **business responsibilities rather than individual developers**.

Each service has clear ownership, independent data, defined boundaries, and service-specific responsibilities.

This allows the system to remain maintainable even when developers join, leave, or change responsibilities.

---

## 📌 Project Documentation

This README provides a high-level overview.

For detailed technical information, refer to the documents inside:


000-requirements/
000-designs/

