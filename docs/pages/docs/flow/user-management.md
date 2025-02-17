﻿
<!DOCTYPE  html>

<html  lang="en">

  

<head>

<meta  charset="UTF-8">

<title>User Management - ProjectHub</title>

<link  rel="stylesheet"  href="../docs/styles.css">

<script  type="module">

import mermaid from  'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';

mermaid.initialize({ startOnLoad: true });

</script>

</head>

  

<body  class="non-copiable">

<h1>User Management</h1>

  

<!-- In-Page Navigation Links -->

<nav  aria-label="User Management Navigation">

<div  class="documentation-links">

<a  href="#component-hierarchy">Component Hierarchy</a> |

<a  href="#user-management-sequence">User Management Sequence</a> |

<a  href="#data-dictionary">Data Dictionary</a> |

<a  href="javascript:history.back()">Go Back</a>

</div>

</nav>

  

<!-- Documentation Section -->

<section  aria-labelledby="user-management-doc">

<h2  id="user-management-doc">User Management Documentation</h2>

<p>This section provides comprehensive information on managing users within ProjectHub, including user creation, role assignments, and account management.</p>

</section>

  

<!-- ARIA Compliance Enhancements -->

<nav  aria-label="User Management Navigation">

<!-- Navigation links -->

</nav>

<main  role="main">

<!-- Main content -->

</main>

<footer  role="contentinfo"  aria-label="Footer">

<!-- Footer content -->

</footer>

  

<div  class="diagram-section">

<h2  id="component-hierarchy">Component Hierarchy</h2>

<div  class="mermaid">

graph TD

%% Main Components

Root[BorderPane: Root]

Content[SplitPane: Content]

List[VBox: UserList]

Details[ScrollPane: UserDetails]

  

%% List Components

SearchBar[TextField: Search]

UserTable[TableView: Users]

AddButton[Button: AddUser]

  

%% Details Components

UserForm[Form: UserDetails]

NameField[TextField: Name]

EmailField[TextField: Email]

RoleSelect[ComboBox: Role]

Activities[TableView: Activities]

  

%% Actions

Actions[HBox: Actions]

SaveBtn[Button: Save]

ResetPwdBtn[Button: ResetPassword]

  

%% Hierarchy

Root --> Content

Content --> List

Content --> Details

  

List --> SearchBar

List --> UserTable

List --> AddButton

  

Details --> UserForm

UserForm --> NameField

UserForm --> EmailField

UserForm --> RoleSelect

Details --> Activities

Details --> Actions

  

Actions --> SaveBtn

Actions --> ResetPwdBtn

  

%% Styling

classDef container fill:#e1f5fe,stroke:#01579b

classDef component fill:#fff,stroke:#0288d1

classDef control fill:#e8f5e9,stroke:#2e7d32

  

class Root,Content container

class List,Details,UserForm component

class SearchBar,UserTable,NameField,EmailField,RoleSelect,Activities,SaveBtn,ResetPwdBtn control

</div>

  

<h2  id="user-management-sequence">User Management Sequence</h2>

<div  class="mermaid">

sequenceDiagram

actor Admin

participant View as UserManagement

participant Controller

participant ViewModel

participant Service

participant DB

  

%% Load Users

Admin->>View: Open Users

View->>Controller: initialize()

Controller->>ViewModel: loadUsers()

ViewModel->>Service: getUsers()

Service->>DB: fetchUsers()

DB-->>Service: users

Service-->>ViewModel: usersList

ViewModel-->>View: updateUserTable()

  

%% User Operations

Admin->>View: Select User

View->>Controller: handleUserSelect()

Controller->>ViewModel: loadUserDetails()

ViewModel->>Service: getUserDetails()

Service->>DB: fetchDetails()

DB-->>Service: userDetails

Service-->>ViewModel: userDTO

ViewModel-->>View: displayUserDetails()

  

%% Edit User

Admin->>View: Edit User

View->>Controller: handleEditUser()

Controller->>ViewModel: validateUserData()

  

alt Valid Input

ViewModel->>Service: updateUser()

Service->>DB: saveUser()

DB-->>Service: success

Service-->>ViewModel: updated

ViewModel-->>View: showSuccess()

else Invalid Input

ViewModel-->>View: showValidationError()

end

  

%% Role Management

Admin->>View: Change Role

View->>Controller: handleRoleChange()

Controller->>ViewModel: updateUserRole()

ViewModel->>Service: changeRole()

Service->>DB: updateRole()

DB-->>Service: success

Service-->>View: refreshUserDetails()

</div>

  

<div  id="data-dictionary"  class="data-dictionary">

<h2>Data Dictionary</h2>

  

<h3>User Entity</h3>

<table>

<thead>

<tr>

<th>Field</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>email</td>

<td>String</td>

<td>User email</td>

</tr>

<tr>

<td>role</td>

<td>UserRole</td>

<td>User permission level</td>

</tr>

<tr>

<td>status</td>

<td>UserStatus</td>

<td>Account status</td>

</tr>

</tbody>

</table>

  

<h3>Activity Log</h3>

<table>

<thead>

<tr>

<th>Field</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>logId</td>

<td>UUID</td>

<td>Activity identifier</td>

</tr>

<tr>

<td>userId</td>

<td>UUID</td>

<td>User reference</td>

</tr>

<tr>

<td>action</td>

<td>ActivityType</td>

<td>Type of activity</td>

</tr>

<tr>

<td>timestamp</td>

<td>DateTime</td>

<td>When activity occurred</td>

</tr>

</tr>

</tbody>

</table>

</div>

</div>

  

<!-- Documentation Section -->

<section  aria-labelledby="user-management-doc">

<h2  id="user-management-doc">User Management Documentation</h2>

<p>This section provides comprehensive information on managing users within ProjectHub, including user creation, role assignments, and account management.</p>

</section>

</main>

  

<footer  role="contentinfo"  aria-label="Footer">

<p>&copy; 2024 ProjectHub. All rights reserved.</p>

</footer>

</body>

  
  

</html>
