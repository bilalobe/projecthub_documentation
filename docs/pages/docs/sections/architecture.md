# Architecture Overview

## System Architecture

The architecture of the ProjectHub system is designed to support a robust and scalable platform for managing educational projects. The system is built using a microservices architecture, which allows for independent deployment and scaling of different components.

### Key Components

1. **User Management Service**: Handles user registration, authentication, and role-based access control.
2. **Project Management Service**: Manages project creation, updates, and tracking of project statuses.
3. **Task Management Service**: Facilitates the creation, assignment, and tracking of tasks associated with projects.
4. **Resource Management Service**: Oversees the allocation and management of resources required for projects.
5. **Notification Service**: Sends notifications to users regarding project updates, task assignments, and deadlines.

### Technology Stack

- **Frontend**: JavaFX for building the user interface.
- **Backend**: Spring Boot for developing microservices.
- **Database**: PostgreSQL for data storage and management.
- **Messaging**: RabbitMQ for inter-service communication.

## Diagrams

### System Context Diagram

```mermaid
C4Context
    title System Context diagram for ProjectHub

    Person(student, "Student", "A student user who can view and manage their projects")
    Person(teacher, "Teacher", "A teacher who manages student projects and evaluations") 
    Person(admin, "Administrator", "System administrator who manages users and settings")

    System(projecthub, "ProjectHub System", "Allows users to manage student projects, evaluations and resources")

    System_Ext(db, "PostgreSQL Database", "Stores user, project and evaluation data")
    System_Ext(auth, "Authentication Service", "Handles user authentication and authorization")
    System_Ext(mq, "RabbitMQ", "Message broker for async communications")

    Rel(student, projecthub, "Views projects, submits work, tracks progress")
    Rel(teacher, projecthub, "Creates/evaluates projects, manages teams")
    Rel(admin, projecthub, "Configures system, manages users")

    Rel(projecthub, db, "Reads from and writes to")
    Rel(projecthub, auth, "Authenticates users via")
    Rel(projecthub, mq, "Publishes/subscribes to messages")
```

### Risk Matrix Diagram

```mermaid
quadrantChart
    title Risk Assessment Matrix
    x-axis Low Impact --> High Impact
    y-axis Low Probability --> High Probability
    quadrant-1 Critical Risk
    quadrant-2 High Risk
    quadrant-3 Medium Risk
    quadrant-4 Low Risk
    Data-Loss: [0.8, 0.6]
    System-Downtime: [0.6, 0.5]
    Security-Breach: [0.9, 0.8]
    Performance-Issues: [0.4, 0.3]
    Integration-Failures: [0.3, 0.2]
```

## Conclusion

The architecture of ProjectHub is designed to ensure flexibility, scalability, and maintainability, enabling efficient management of educational projects and resources.