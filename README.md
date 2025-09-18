# 🚂 Traineeship Application - TrainUp
### Enterprise-Grade Internship Management Platform

![Java](https://img.shields.io/badge/Java-11+-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-2.7+-green)

**Train-Up** is a comprehensive web-based internship management platform developed as part of a personal project. It streamlines the entire internship lifecycle from position posting to final evaluation, connecting students, companies, supervising professors, and the Internship Committee in one integrated ecosystem.

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [System Architecture](#️-system-architecture)
- [Design Patterns](#-design-patterns)
- [Technology Stack](#-technology-stack)
- [User Roles](#-user-roles)
- [Core Workflows](#-core-workflows)
- [Strategic Assignment Algorithms](#-strategic-assignment-algorithms)
- [Project Documentation](#-project-documentation)
- [Getting Started](#-getting-started)

---

## 🎯 Overview

Train-Up addresses the complex challenges of internship management in academic environments by providing:

- **Centralized Platform**: Single point of access for all stakeholders
- **Automated Matching**: Intelligent algorithms for position-student pairing
- **Progress Tracking**: Real-time monitoring through digital logbooks
- **Multi-faceted Evaluation**: Comprehensive assessment from both academic and industry perspectives
- **Strategic Assignment**: Data-driven decision making for optimal placements

---

## 🚀 Key Features

### 📋 **Position Management**
- **Dynamic Publishing**: Companies can create, edit, and manage internship positions with rich metadata
- **Advanced Filtering**: Search by location, skills, interests, duration, and company profile
- **Real-time Availability**: Live updates on position status and application deadlines

### 📝 **Application & Tracking**
- **Streamlined Applications**: One-click application process with profile integration
- **Digital Logbook**: Continuous progress tracking with timestamped entries
- **Status Dashboard**: Real-time visibility into application and assignment status

### ⭐ **Evaluation System**
- **Dual Assessment**: Independent evaluations from both supervising professors and host companies
- **Structured Criteria**: Standardized evaluation metrics (motivation, efficiency, effectiveness)
- **Final Determination**: Committee-based pass/fail decisions with comprehensive reporting

### 🤖 **Intelligent Assignment**
- **Multi-strategy Algorithms**: Position assignment based on interests, location, or hybrid approaches
- **Supervisor Matching**: Automated professor assignment using workload balancing and expertise matching
- **Conflict Resolution**: Smart handling of competing applications and resource constraints

---

## 🏗️ System Architecture

Train-Up follows a **layered architecture** pattern based on Spring Boot MVC principles:

```
┌─────────────────────────────────────┐
│           Presentation Layer        │
│  Controllers, Views (Thymeleaf)     │
├─────────────────────────────────────┤
│            Service Layer            │
│   Business Logic, Strategy Pattern  │
├─────────────────────────────────────┤
│           Persistence Layer         │
│     JPA Repositories, Entities      │
├─────────────────────────────────────┤
│            Domain Model             │
│  Core Entities and Business Rules   │
└─────────────────────────────────────┘
```

### 🗂️ **Core Components**

#### **1. Domain Layer**
- **User Management**: `User`, `Student`, `Professor`, `Company` entities
- **Internship Core**: `TraineeshipPosition`, `Evaluation` entities
- **Security Model**: Role-based access control with `Role` enumeration

#### **2. Service Layer**
- **UserService**: Authentication, authorization, profile management
- **StudentService**: Application submission, logbook management
- **CompanyService**: Position lifecycle, student evaluation
- **ProfessorService**: Supervision duties, academic assessment
- **CommitteeService**: Assignment orchestration, final decisions
- **EmailService**: Automated notifications and reminders

#### **3. Strategy Implementation**
- **Position Search Strategies**: Interest-based, location-based, hybrid matching
- **Supervisor Assignment**: Workload balancing, expertise alignment
- **Factory Pattern**: Dynamic strategy instantiation

---

## 🎨 Design Patterns

### **Strategy Pattern**
Enables flexible algorithm selection for critical business operations:

```java
// Position assignment strategies
PositionsSearchStrategy strategy = PositionsSearchFactory.create("INTERESTS");
List<Position> matches = strategy.searchPositions(student, availablePositions);

// Supervisor assignment strategies  
SupervisorAssignmentStrategy supervisorStrategy = 
    SupervisorAssignmentFactory.create("MIN_LOAD");
Professor assigned = supervisorStrategy.assign(position, professors);
```

### **Factory Pattern**
Centralized object creation with parameterized strategy selection:
- `PositionsSearchFactory`: Creates position matching strategies
- `SupervisorAssignmentFactory`: Instantiates supervisor assignment algorithms

### **MVC Pattern**
Clear separation of concerns with dedicated controllers for each user role:
- `AuthController`: Authentication and verification
- `StudentController`: Student-specific operations
- `CompanyController`: Company position management
- `ProfessorController`: Academic supervision tasks
- `CommitteeController`: Administrative functions

---

## 💻 Technology Stack

### **Backend Framework**
- **Java 11+**: Modern language features and performance optimizations
- **Spring Boot 2.7+**: Rapid application development with auto-configuration
- **Spring Security**: Comprehensive authentication and authorization
- **Spring Data JPA**: Simplified data persistence with ORM

### **Database & Persistence**
- **MySQL**: Production-grade relational database
- **Hibernate**: Object-relational mapping with advanced caching

### **Frontend & Templating**
- **Thymeleaf**: Server-side template engine with Spring integration
- **Bootstrap**: Responsive UI components and styling
- **HTML5/CSS3/JavaScript**: Modern web standards

### **Development Tools**
- **Maven**: Dependency management and build automation
- **Lombok**: Boilerplate code reduction
- **MapStruct**: Type-safe bean mapping
- **JUnit & Mockito**: Comprehensive testing framework

---

## 👥 User Roles

### 🎓 **Students**
- Create and maintain academic profiles with skills and interests
- Browse and apply for available internship positions
- Maintain digital logbooks with progress updates
- View evaluation results and final grades

### 🏢 **Companies**
- Publish detailed internship position descriptions
- Manage application workflows and candidate selection
- Evaluate student performance using structured criteria
- Access analytics on internship program effectiveness

### 👨‍🏫 **Professors**
- Supervise assigned student internships
- Conduct academic evaluations based on learning outcomes
- Monitor student progress through logbook reviews
- Collaborate with industry partners on assessment

### 🏛️ **Committee Members**
- Orchestrate position-student matching using strategic algorithms
- Assign supervising professors based on expertise and workload
- Make final pass/fail determinations based on comprehensive evaluations
- Generate reports and analytics for program improvement

---

## 🔄 Core Workflows

### **1. Position Publication Workflow**
```
Company → Create Position → System Validation → Email Notifications → Student Discovery
```

### **2. Application & Assignment Workflow**
```
Student Application → Committee Review → Strategy Execution → Position Assignment → Supervisor Assignment
```

### **3. Evaluation Workflow**
```
Progress Monitoring → Dual Evaluation (Company + Professor) → Committee Review → Final Decision
```

---

## 🧠 Strategic Assignment Algorithms

### **Position Matching Strategies**

#### **Interest-Based Strategy**
Uses Jaccard similarity coefficient to match student interests with position requirements:
```
similarity = |student_interests ∩ position_topics| / |student_interests ∪ position_topics|
```

#### **Location-Based Strategy**
Prioritizes positions within preferred geographical proximity using distance calculations.

#### **Hybrid Strategy**
Combines multiple criteria with weighted scoring for optimal matches.

### **Supervisor Assignment Strategies**

#### **Expertise Matching**
Aligns professor research interests with internship domain requirements.

#### **Workload Balancing**
Distributes supervision duties evenly across available faculty members.

---

## 📚 Project Documentation

This repository includes comprehensive technical documentation:

- **📋 Use Cases**: Detailed user scenarios and system interactions
- **🔄 Sequence Diagrams**: Process flows and system communications  
- **💪 Robustness Diagrams**: System reliability and error handling
- **🗃️ Class Diagrams**: Object-oriented design and relationships
- **🏗️ Domain Model**: Business logic and entity relationships
- **🧪 Test Cases**: Comprehensive testing scenarios and validation

All diagrams are available in the `/docs` directory with both source files and rendered images.

---

## 🚀 Getting Started

### **Prerequisites**
- Java 11 or higher
- Maven 3.6+
- MySQL

### **Quick Start**
```bash
# Clone the repository
git clone https://github.com/yourusername/train-up.git
cd train-up

# Build the project
mvn clean install

# Edit the application properties
change the fields for your Database and email verification key

# Run with development profile (H2 database)
mvn spring-boot:run -Dspring-boot.run.profiles=dev

# Access the application
open http://localhost:8080
```


<div align="center">

</div>
