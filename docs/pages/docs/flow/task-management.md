
<!DOCTYPE  html>

<html  lang="en">

  

<head>

<meta  charset="UTF-8">

<title>Task Management Documentation - ProjectHub</title>

<link  rel="stylesheet"  href="../docs/styles.css">

<script  type="module">

import mermaid from  'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';

mermaid.initialize({ startOnLoad: true });

</script>

</head>

  

<body  class="non-copiable">

<h1>Task Management Documentation</h1>

  

<!-- In-Page Navigation Links -->

<nav  aria-label="Task Management Navigation">

<div  class="documentation-links">

<a  href="#ui-components-structure">UI Components Structure</a> |

<a  href="#task-operations-sequence">Task Operations Sequence</a> |

<a  href="#data-dictionary">Data Dictionary</a> |

<a  href="javascript:history.back()">Go Back</a>

</div>

</nav>

  

<!-- Documentation Section -->

<section  aria-labelledby="task-management-doc">

<h2  id="task-management-doc">Task Management Documentation</h2>

<p>This section details the processes involved in managing tasks within ProjectHub, including task creation, assignment, tracking, and completion.</p>

</section>

  

<!-- UI Components Diagram -->

<div  class="diagram-section">

<h2  id="ui-components-structure">UI Components Structure</h2>

<div  class="mermaid">

graph TD

%% Main Components

Root[BorderPane: Root]

TopBar[HBox: TopBar]

Content[SplitPane: Content]

SideNav[VBox: Navigation]

TaskList[VBox: TaskList]

Details[ScrollPane: Details]

  

%% Task List Components

SearchBar[SearchBar]

TaskTable[TableView: Tasks]

Filters[HBox: Filters]

  

%% Task Details Components

TaskForm[Form: TaskDetails]

Actions[HBox: Actions]

Status[StatusBar]

  

%% Hierarchy

Root --> TopBar

Root --> Content

Content --> SideNav

Content --> TaskList

Content --> Details

  

%% Task List Breakdown

TaskList --> SearchBar

TaskList --> Filters

TaskList --> TaskTable

  

%% Details Breakdown

Details --> TaskForm

Details --> Actions

Details --> Status

  

%% Styling

classDef container fill:#e1f5fe,stroke:#01579b

classDef component fill:#fff,stroke:#0288d1

classDef action fill:#e8f5e9,stroke:#2e7d32

  

class Root,Content,TaskList,Details container

class SearchBar,TaskTable,TaskForm,Status component

class TopBar,Actions,Filters action

</div>

</div>

  

<!-- Task Operations Flow -->

<div  class="sequence-diagrams">

<h2  id="task-operations-sequence">Task Operations Sequence</h2>

<div  class="mermaid">

sequenceDiagram

actor User

participant View

participant Controller

participant ViewModel

participant Service

participant DB

  

Note over User,View: Task Creation Flow

User->>View: Click Add Task

View->>Controller: handleAddTask()

Controller->>View: showTaskForm()

User->>View: Fill Task Details

User->>View: Click Save

View->>Controller: handleSaveTask()

Controller->>ViewModel: saveTask(TaskDTO)

ViewModel->>Service: saveTask()

Service->>DB: persist()

DB-->>Service: success

Service-->>ViewModel: update

ViewModel-->>Controller: refresh

Controller-->>View: showSuccess()

  

Note over User,View: Task Search Flow

User->>View: Enter Search Query

View->>Controller: onSearchChange()

Controller->>ViewModel: searchTasks()

ViewModel->>Service: searchByQuery()

Service-->>ViewModel: results

ViewModel-->>View: updateTaskList

</div>

</div>

  

<!-- Data Dictionary -->

<div  id="data-dictionary"  class="data-dictionary">

<h2>Data Dictionary</h2>

<h3>Entities</h3>

<table>

<thead>

<tr>

<th>Entity</th>

<th>Fields</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>Task</td>

<td>

UUID id<br>

String name<br>

String description<br>

String status<br>

LocalDate dueDate<br>

UUID assigneeId

</td>

<td>Task entity</td>

</tr>

</tbody>

</table>

  

<h3>Components</h3>

<table>

<thead>

<tr>

<th>Component</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>TaskDetailsController</td>

<td>Controller</td>

<td>Handles user interactions and view logic</td>

</tr>

<tr>

<td>TaskDetailsViewModel</td>

<td>ViewModel</td>

<td>Manages task data and business logic</td>

</tr>

<tr>

<td>TaskService</td>

<td>Service</td>

<td>Handles task persistence and retrieval</td>

</tr>

</tbody>

</table>

  

<h3>Data Transfer Objects</h3>

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

<td>TaskDTO</td>

<td>

UUID id<br>

String name<br>

String description<br>

String status<br>

LocalDate dueDate<br>

UUID assigneeId

</td>

<td>Task data transfer object</td>

</tr>

</tbody>

</table>

  

<h3>View States</h3>

<table>

<thead>

<tr>

<th>State</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>selectedTask</td>

<td>SimpleObjectProperty&lt;TaskDTO&gt;</td>

<td>Currently selected task</td>

</tr>

<tr>

<td>searchQuery</td>

<td>SimpleStringProperty</td>

<td>Current search filter</td>

</tr>

<tr>

<td>tasks</td>

<td>ObservableList&lt;TaskDTO&gt;</td>

<td>List of visible tasks</td>

</tr>

</tbody>

</table>

</div>

  

<!-- ARIA Compliance Enhancements -->

<nav  aria-label="Task Management Navigation">

<!-- Navigation links -->

</nav>

<main  role="main">

<!-- Main content -->

</main>



</body>

  

</html>
