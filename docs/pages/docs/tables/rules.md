# Project Rules

## Access Control Rules

| Rule ID | Description | Roles |
|---------|-------------|-------|
| RG-001 | Only administrators can create/modify user roles | ADMIN |
| RG-002 | Teachers can create and manage projects | TEACHER |
| RG-003 | Students can only view assigned projects | STUDENT |
| RG-004 | Team leaders can assign tasks to team members | TEAM_LEAD |

## Project Management Rules

| Rule ID | Description | Priority |
|---------|-------------|----------|
| RG-010 | Projects must have defined objectives | HIGH |
| RG-011 | Tasks must be assigned to team members | HIGH |
| RG-012 | Progress updates required weekly | MEDIUM |
| RG-013 | Resource allocation must be documented | MEDIUM |

## Technical Requirements

| Rule ID | Description | Category |
|---------|-------------|----------|
| RG-020 | Use Spring Boot 3.x | Backend |
| RG-021 | Use JavaFX for UI | Frontend |
| RG-022 | PostgreSQL for database | Database |
| RG-023 | Implement JWT authentication | Security |

## Evaluation Criteria

| Rule ID | Description | Weight |
|---------|-------------|--------|
| RG-030 | Code quality and organization | 30% |
| RG-031 | Feature completeness | 25% |
| RG-032 | Documentation quality | 25% |
| RG-033 | UI/UX design | 20% |

!!! note "Rule Updates"
    Rules may be updated throughout the project lifecycle. Check changelog for updates.