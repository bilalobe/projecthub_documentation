﻿
<!DOCTYPE  html>

<html  lang="en">

<head>

<meta  charset="UTF-8">

<title>Dashboard Management - Data Dictionary and Sequence Diagram</title>

<link  rel="stylesheet"  href="../docs/styles.css">

<script  type="module">

import mermaid from  'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';

mermaid.initialize({ startOnLoad: true, theme: 'default' });

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

<nav  aria-label="Dashboard Management Navigation">

<div  class="documentation-links">

<a  href="#ui-component-hierarchy">UI Component Hierarchy</a> |

<a  href="#sequence-diagram">Sequence Diagram</a> |

<a  href="#data-dictionary">Data Dictionary</a> |

<a  href="javascript:history.back()">Go Back</a>

</div>

</nav>

  

<!-- Documentation Section -->

<section  aria-labelledby="dashboard-management-doc">

<h1  id="dashboard-management-title">Dashboard Management</h1>

<p>This section covers the dashboard management functionalities, including data visualization, user interactions, and performance metrics.</p>

</section>

  

<!-- Component Hierarchy -->

<div  class="diagram-section"  aria-label="UI Component Hierarchy">

<h2  id="ui-component-hierarchy">UI Component Hierarchy</h2>

<div  class="mermaid">

graph TD

%% Main Components

Root[BorderPane: Root]

Content[ScrollPane: Content]

Stats[HBox: Statistics]

Charts[VBox: Charts]

Activities[VBox: Activities]

  

%% Statistics Components

UsersCard[VBox: UsersStats]

ProjectsCard[VBox: ProjectStats]

TeamsCard[VBox: TeamStats]

  

%% Chart Components

PieChart[PieChart: StatusDistribution]

LineChart[LineChart: ActivityTrend]

  

%% Activity Components

ActivityTable[TableView: RecentActivities]

ActivityFilter[ComboBox: Filter]

RefreshBtn[Button: Refresh]

  

%% Hierarchy

Root --> Content

Content --> Stats

Content --> Charts

Content --> Activities

  

Stats --> UsersCard

Stats --> ProjectsCard

Stats --> TeamsCard

  

Charts --> PieChart

Charts --> LineChart

  

Activities --> ActivityFilter

Activities --> ActivityTable

Activities --> RefreshBtn

  

%% Styling

classDef container fill:#e1f5fe,stroke:#01579b

classDef component fill:#fff,stroke:#0288d1

classDef control fill:#e8f5e9,stroke:#2e7d32

  

class Root,Content container

class Stats,Charts,Activities component

class UsersCard,ProjectsCard,TeamsCard,PieChart,LineChart,ActivityTable control

</div>

</div>

  

<!-- Sequence Diagram Section -->

<div  class="diagram"  aria-label="Sequence Diagram">

<h2  id="sequence-diagram">Sequence Diagram</h2>

<p  class="section-description">

The following sequence diagram illustrates the interactions between the user interface, controllers, view

models, services, and the database during dashboard management operations.

</p>

<div  class="mermaid">

sequenceDiagram

actor User

participant UI as Dashboard View

participant Controller as DashboardController

participant ViewModel as DashboardViewModel

participant Service as DashboardService

participant Database as Database

participant Notification as Notification System

  

%% Initialize Dashboard

User->>UI: Open Dashboard

UI->>Controller: initialize()

Controller->>Controller: bindProperties()

Note right of Controller: Bind UI controls to ViewModel properties

Controller->>Controller: setupRecentActivitiesTable()

Note right of Controller: Configure table columns and cell factories

  

%% Load Dashboard Data

Controller->>ViewModel: loadDashboardData()

par Load Statistics

ViewModel->>Service: getTotalUsers()

Service->>Database: Query Users Count

Database-->>Service: Return Count

Service-->>ViewModel: Update totalUsers

and

ViewModel->>Service: getTotalProjects()

Service->>Database: Query Projects Count

Database-->>Service: Return Count

Service-->>ViewModel: Update totalProjects

and

ViewModel->>Service: getTotalTeams()

Service->>Database: Query Teams Count

Database-->>Service: Return Count

Service-->>ViewModel: Update totalTeams

end

  

%% Load Charts and Activities

par Load Project Status

ViewModel->>Service: getProjectStatusDistribution()

Service->>Database: Query Status Data

Database-->>Service: Return Statistics

Service-->>ViewModel: Update pieChart data

and Load Activities

ViewModel->>Service: getRecentActivities()

Service->>Database: Query Activities

Database-->>Service: Return Activities

Service-->>ViewModel: Update activities list

end

  

%% Update UI

ViewModel-->>Controller: Properties Updated

Controller-->>UI: Refresh Display

Note right of UI: Update statistics cards, charts, and table

  

%% Real-time Updates

loop Every 30 seconds

Service->>Database: Poll for Changes

Database-->>Service: Return Updates

Service-->>ViewModel: Update Properties

ViewModel-->>UI: Refresh Display

end

  

%% Error Handling

alt Error Occurs

Service-->>ViewModel: Throw Exception

ViewModel-->>Controller: Log Error

Controller-->>UI: Show Error Dialog

end

</div>

</div>

<!-- Data Dictionary Section -->

<div  class="entity">

<h2  id="data-dictionary">Data Dictionary</h2>

<p  class="section-description">

The Data Dictionary below outlines the key data entities used within the Dashboard Management module,

detailing their attributes, types, and descriptions.

</p>

  

<!-- DashboardStatistics Entity -->

<div  class="entity">

<h3>DashboardStatistics</h3>

<table>

<thead>

<tr>

<th>Attribute</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>totalUsers</td>

<td>Integer</td>

<td>Total number of users in the system.</td>

</tr>

<tr>

<td>totalProjects</td>

<td>Integer</td>

<td>Total number of projects.</td>

</tr>

<tr>

<td>totalTeams</td>

<td>Integer</td>

<td>Total number of teams.</td>

</tr>

</tbody>

</table>

</div>

  

<!-- ProjectStatus Entity -->

<div  class="entity">

<h3>ProjectStatus</h3>

<table>

<thead>

<tr>

<th>Attribute</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>statusType</td>

<td>Enum</td>

<td>Project status (e.g., In Progress, Completed).</td>

</tr>

<tr>

<td>count</td>

<td>Integer</td>

<td>Number of projects in this status.</td>

</tr>

<tr>

<td>percentage</td>

<td>Double</td>

<td>Percentage of total projects.</td>

</tr>

</tbody>

</table>

</div>

  

<!-- RecentActivity Entity -->

<div  class="entity">

<h3>RecentActivity</h3>

<table>

<thead>

<tr>

<th>Attribute</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>activityId</td>

<td>UUID</td>

<td>Unique identifier for the activity.</td>

</tr>

<tr>

<td>timestamp</td>

<td>DateTime</td>

<td>When the activity occurred.</td>

</tr>

<tr>

<td>type</td>

<td>Enum</td>

<td>Type of activity (e.g., Create, Update, Delete).</td>

</tr>

<tr>

<td>description</td>

<td>String</td>

<td>Description of the activity.</td>

</tr>

</tbody>

</table>

</div>

  

<!-- Additional Entities -->

<div  class="entity">

<h3>PieChartData</h3>

<table>

<thead>

<tr>

<th>Attribute</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>category</td>

<td>String</td>

<td>Category name for the pie chart slice.</td>

</tr>

<tr>

<td>value</td>

<td>Double</td>

<td>Numerical value representing the category.</td>

</tr>

</tbody>

</table>

</div>

</div>

  

<!-- Explanation Section -->

<div  class="explanation">

<h2>Explanation</h2>

<ul>

<li><strong>Dashboard Initialization:</strong> Loads and configures UI components, ensuring all elements are

bound to the ViewModel.</li>

<li><strong>Parallel Data Loading:</strong> Efficiently retrieves statistics, charts, and recent activities

concurrently to optimize performance.</li>

<li><strong>Real-time Updates:</strong> Maintains dashboard freshness by periodically polling the database

for updates every 30 seconds.</li>

<li><strong>Error Handling:</strong> Manages exceptions gracefully by logging errors and notifying the user

through dialog boxes.</li>

</ul>

</div>

  

<!-- Footer Section -->



</body>

  

</html>
