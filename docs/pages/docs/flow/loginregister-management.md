
<!DOCTYPE  html>

<html  lang="en">

  

<head>

<meta  charset="UTF-8">

<title>Login & Register Documentation - ProjectHub</title>

<link  rel="stylesheet"  href="../docs/styles.css">

<script  type="module">

import mermaid from  'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';

mermaid.initialize({ startOnLoad: true });

</script>

</head>

  

<body  class="non-copiable">

<script>

document.addEventListener('contextmenu', function (e) {

e.preventDefault(); // Disable right-click

});

document.addEventListener('copy', function (e) {

e.preventDefault(); // Disable copy

});

</script>

  

<!-- In-Page Navigation Links -->

<nav  class="documentation-links"  aria-label="Documentation Navigation">

<a  href="#ui-component-hierarchy">UI Component Hierarchy</a> |

<a  href="#login-sequence">Login Sequence Diagram</a> |

<a  href="#register-sequence">Register Sequence Diagram</a> |

<a  href="#data-dictionary">Unified Data Dictionary</a> |

<a  href="javascript:history.back()">Go Back</a>

</nav>

<!-- Documentation Section -->

<section  aria-labelledby="login-register-doc">

<h1  id="login-register-title">Login & Register Documentation</h1>

<p>This documentation provides guidelines on user authentication processes, including login procedures,

registration workflows, and security measures.</p>

</section>

<main  role="main">

<div  class="diagram-section">

<h2  id="ui-component-hierarchy">UI Component Hierarchy</h2>

<div  class="mermaid">

graph TD

%% Main Components

Root[BorderPane: Root]

Content[StackPane: Content]

Forms[VBox: Forms]

  

%% Login Components

LoginForm[VBox: LoginForm]

Username[TextField: Username]

Password[PasswordField: Password]

RememberMe[CheckBox: RememberMe]

LoginBtn[Button: Login]

  

%% Register Components

RegisterForm[VBox: RegisterForm]

RegUsername[TextField: Username]

RegEmail[TextField: Email]

RegPassword[PasswordField: Password]

RegConfirm[PasswordField: Confirm]

RegisterBtn[Button: Register]

  

%% Navigation

NavLinks[HBox: Navigation]

ToLogin[Hyperlink: LoginLink]

ToRegister[Hyperlink: RegisterLink]

  

%% Hierarchy

Root --> Content

Content --> Forms

Forms --> LoginForm

Forms --> RegisterForm

Forms --> NavLinks

  

LoginForm --> Username

LoginForm --> Password

LoginForm --> RememberMe

LoginForm --> LoginBtn

  

RegisterForm --> RegUsername

RegisterForm --> RegEmail

RegisterForm --> RegPassword

RegisterForm --> RegConfirm

RegisterForm --> RegisterBtn

  

NavLinks --> ToLogin

NavLinks --> ToRegister

  

%% Styling

classDef container fill:#e1f5fe,stroke:#01579b

classDef form fill:#fff,stroke:#0288d1

classDef control fill:#e8f5e9,stroke:#2e7d32

classDef nav fill:#fff3e0,stroke:#f57c00

  

class Root,Content,Forms container

class LoginForm,RegisterForm form

class Username,Password,RegUsername,RegEmail,RegPassword,RegConfirm,LoginBtn,RegisterBtn control

class NavLinks,ToLogin,ToRegister nav

</div>

</div>

  

<!-- Login Sequence Diagram Section -->

<div  id="login-sequence"  class="sequence-diagrams">

<h2>Login Sequence Diagram</h2>

<div  class="mermaid">

sequenceDiagram

%% Actors and Participants

actor User

participant LoginView

participant LoginController

participant LoginViewModel

participant AuthService

participant TokenService

participant DB

  

%% Login Flow

User->>LoginView: Enter Credentials

LoginView->>LoginController: handleLogin()

LoginController->>LoginViewModel: login()

LoginViewModel->>LoginViewModel: validateInput()

  

alt Invalid Input

LoginViewModel-->>LoginController: return false

LoginController-->>LoginView: Show Error

else Valid Input

LoginViewModel->>AuthService: authenticate(LoginRequestDTO)

AuthService->>DB: validateCredentials()

  

alt Authentication Success

DB-->>AuthService: User Found

AuthService-->>LoginViewModel: AuthenticationResultDTO

LoginViewModel->>TokenService: storeToken()

LoginViewModel-->>LoginController: return true

LoginController-->>LoginView: navigateToMainView()

else Authentication Failed

DB-->>AuthService: Invalid Credentials

AuthService-->>LoginViewModel: throw InvalidCredentialsException

LoginViewModel-->>LoginController: return false

LoginController-->>LoginView: Show Error

end

end

</div>

<p  class="section-description">

The login sequence diagram illustrates the interaction between the user and the system components

during the authentication process. It highlights the validation steps and the handling of both

successful

and failed authentication attempts.

</p>

  

<!-- Key Features of Login Process -->

<h3>Key Features</h3>

<ul>

<li><strong>Input Validation:</strong> Ensures that user credentials meet required formats and

constraints.

</li>

<li><strong>Authentication:</strong> Validates credentials against stored data to authenticate the user.

</li>

<li><strong>Token Management:</strong> Stores authentication tokens upon successful login for session

management.</li>

<li><strong>Error Handling:</strong> Displays appropriate error messages for invalid inputs or failed

authentications.</li>

<li><strong>Remember Me Functionality:</strong> Allows users to stay logged in across sessions using

tokens.

</li>

</ul>

</div>

  

<!-- Register Sequence Diagram Section -->

<div  id="register-sequence"  class="sequence-diagrams">

<h2>Register Sequence Diagram</h2>

<div  class="mermaid">

sequenceDiagram

%% Actors and Participants

actor User

participant RegisterView

participant RegisterController

participant RegisterViewModel

participant UserService

participant DB

  

%% Register Flow

User->>RegisterView: Click Register

RegisterView->>RegisterController: handleRegister()

RegisterController->>RegisterViewModel: register()

RegisterViewModel->>RegisterViewModel: validateInput()

  

alt Invalid Input

RegisterViewModel-->>RegisterController: return false

RegisterController-->>RegisterView: Show Validation Error

else Valid Input

RegisterViewModel->>UserService: registerUser(RegisterRequestDTO)

UserService->>DB: save()

DB-->>UserService: User Created

UserService-->>RegisterViewModel: Success

RegisterViewModel-->>RegisterController: return true

RegisterController-->>RegisterView: Show Success & Navigate to Login

end

</div>

<p  class="section-description">

The register sequence diagram outlines the process of user registration within the system. It covers

input

validation, user creation, and the subsequent feedback provided to the user upon successful or failed

registration attempts.

</p>

  

<!-- Key Features of Registration Process -->

<h3>Key Features</h3>

<ul>

<li><strong>Input Validation:</strong> Ensures that registration details are valid and meet all

requirements.</li>

<li><strong>User Creation:</strong> Persists new user data to the database upon successful validation.

</li>

<li><strong>Feedback Mechanism:</strong> Notifies users of successful registration and redirects them to

the

login view.</li>

<li><strong>Error Handling:</strong> Displays validation errors if inputs are invalid or if the user

already

exists.</li>

<li><strong>Role Assignment:</strong> Allows assignment of user roles (e.g., Admin, User) during

registration.</li>

</ul>

</div>

  

<!-- Unified Data Dictionary Section -->

<div  id="data-dictionary"  class="data-dictionary">

<h2>Unified Data Dictionary</h2>

<p  class="section-description">This section provides a comprehensive data dictionary for the login and

register

processes.</p>

  

<h3>Data Transfer Objects (DTOs)</h3>

<table>

<thead>

<tr>

<th>DTO</th>

<th>Fields</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>LoginRequestDTO</td>

<td>

String username<br>

String password<br>

boolean rememberMe<br>

String ipAddress

</td>

<td>Data required for user login.</td>

</tr>

<tr>

<td>AuthenticationResultDTO</td>

<td>

String token<br>

String rememberMeToken

</td>

<td>Result of successful authentication.</td>

</tr>

<tr>

<td>RegisterRequestDTO</td>

<td>

String username<br>

String email<br>

String password<br>

String firstName<br>

String lastName<br>

String role

</td>

<td>Data required for user registration.</td>

</tr>

</tbody>

</table>

  

<h3>Entities and Models</h3>

<table>

<thead>

<tr>

<th>Entity/Model</th>

<th>Fields</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>User</td>

<td>

UUID userId<br>

String username<br>

String email<br>

String passwordHash<br>

String firstName<br>

String lastName<br>

String role

</td>

<td>Represents a user in the system.</td>

</tr>

</tbody>

</table>

  

<h3>View States</h3>

<table>

<thead>

<tr>

<th>View State</th>

<th>Fields</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>LoginViewState</td>

<td>

boolean loginInProgress<br>

boolean passkeyAvailable<br>

String errorMessage<br>

boolean rememberMe

</td>

<td>State information for the login view.</td>

</tr>

<tr>

<td>RegisterViewState</td>

<td>

boolean registrationInProgress<br>

PasswordStrength passwordStrength<br>

String errorMessage<br>

boolean rtl

</td>

<td>State information for the register view.</td>

</tr>

</tbody>

</table>

  

<h3>Services</h3>

<table>

<thead>

<tr>

<th>Service Interface</th>

<th>Methods</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>AuthService</td>

<td>

AuthenticationResultDTO authenticate(LoginRequestDTO request) throws

InvalidCredentialsException

</td>

<td>Handles user authentication.</td>

</tr>

<tr>

<td>TokenService</td>

<td>

void storeToken(String token)<br>

String retrieveToken()

</td>

<td>Manages storage and retrieval of authentication tokens.</td>

</tr>

<tr>

<td>UserService</td>

<td>

void registerUser(RegisterRequestDTO request) throws UserAlreadyExistsException

</td>

<td>Handles user registration.</td>

</tr>

<tr>

<td>DB</td>

<td>

User findUserByUsername(String username)<br>

void saveUser(User user)

</td>

<td>Database access object for user data.</td>

</tr>

</tbody>

</table>

  

<h3>Exceptions</h3>

<table>

<thead>

<tr>

<th>Exception</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>InvalidCredentialsException</td>

<td>Thrown when authentication fails due to invalid credentials.</td>

</tr>

<tr>

<td>UserAlreadyExistsException</td>

<td>Thrown when attempting to register a user that already exists.</td>

</tr>

</tbody>

</table>

</div>

</main>

  

<!-- Footer Section -->



</body>

  

</html>
