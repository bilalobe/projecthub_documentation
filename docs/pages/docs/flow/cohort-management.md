﻿
<!DOCTYPE  html>

<html  lang="en">

  

<head>

<meta  charset="UTF-8">

<title>Cohort Management - Data Dictionary and Sequence Diagram</title>

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

  

<!-- Documentation Section -->

<section  aria-labelledby="cohort-management-doc">

<h1  id="cohort-management-title">Cohort Management</h1>

<p>This documentation provides a comprehensive overview of the Cohort Management module, including data models, user interfaces, and operational workflows.</p>

</section>

  

<div  class="diagram-section"  aria-label="UI Component Hierarchy">

<h2>UI Component Hierarchy</h2>

<div  class="mermaid">

graph TD

%% Main Components

Root[BorderPane: Root]

Content[SplitPane: Content]

List[VBox: CohortList]

Details[ScrollPane: Details]

  

%% List Components

SearchBar[TextField: Search]

CohortTable[TableView: Cohorts]

AddButton[Button: AddCohort]

  

%% Details Components

CohortForm[Form: CohortForm]

NameField[TextField: Name]

DatePicker[DatePicker: Dates]

TeamList[ListView: Teams]

  

%% Action Components

Actions[HBox: Actions]

SaveBtn[Button: Save]

DeleteBtn[Button: Delete]

  

%% Dialog Components

DialogPane[DialogPane: Confirmation]

DialogBtns[ButtonBar: DialogButtons]

  

%% Hierarchy

Root --> Content

Content --> List

Content --> Details

  

List --> SearchBar

List --> CohortTable

List --> AddButton

  

Details --> CohortForm

CohortForm --> NameField

CohortForm --> DatePicker

CohortForm --> TeamList

Details --> Actions

  

Actions --> SaveBtn

Actions --> DeleteBtn

  

Root --> DialogPane

DialogPane --> DialogBtns

  

%% Styling

classDef container fill:#e1f5fe,stroke:#01579b

classDef component fill:#fff,stroke:#0288d1

classDef control fill:#e8f5e9,stroke:#2e7d32

  

class Root,Content container

class List,Details,CohortForm,DialogPane component

class SearchBar,CohortTable,NameField,DatePicker,TeamList,SaveBtn,DeleteBtn,DialogBtns control

</div>

</div>

  

<!-- Sequence Diagram Section -->

<div  class="diagram"  aria-label="Sequence Diagram">

<h2>Sequence Diagram</h2>

<p  class="section-description">

The following sequence diagram illustrates the interactions between the user interface, view models,

services, and the database during cohort management operations.

</p>

<div  class="mermaid">

sequenceDiagram

actor User

participant UI as User Interface

participant ViewModel as CohortViewModel

participant Service as CohortService

participant Database as Database

participant Notification as NotificationSystem

  

%% Main Navigation

User->>UI: Navigate to Cohorts

UI->>ViewModel: Load Cohort List

ViewModel->>Service: Fetch Cohorts

Service->>Database: Retrieve Cohorts

Database-->>Service: Provide Cohort Data

Service-->>ViewModel: Return Cohorts

ViewModel-->>UI: Display Cohort List

  

%% Create Cohort

User->>UI: Add New Cohort

UI->>ViewModel: Initialize New Cohort Form

User->>UI: Enter Cohort Details

UI->>ViewModel: Submit New Cohort

ViewModel->>Service: Save Cohort

Service->>Database: Persist Cohort

Database-->>Service: Confirmation

Service-->>ViewModel: Cohort Saved

ViewModel-->>UI: Update Cohort List

UI->>Notification: Show Success Message

  

%% Edit Cohort

User->>UI: Select Cohort to Edit

UI->>ViewModel: Load Cohort Details

ViewModel->>Service: Fetch Cohort by ID

Service->>Database: Retrieve Cohort Data

Database-->>Service: Provide Cohort Details

Service-->>ViewModel: Return Cohort Data

ViewModel-->>UI: Populate Edit Form

User->>UI: Modify Cohort Details

UI->>ViewModel: Submit Changes

ViewModel->>Service: Update Cohort

Service->>Database: Update Cohort Record

Database-->>Service: Confirmation

Service-->>ViewModel: Cohort Updated

ViewModel-->>UI: Refresh Cohort List

UI->>Notification: Show Update Success

  

%% Delete Cohort

User->>UI: Delete Cohort

UI->>ViewModel: Confirm Deletion

ViewModel->>Service: Remove Cohort

Service->>Database: Delete Cohort Record

Database-->>Service: Confirmation

Service-->>ViewModel: Cohort Deleted

ViewModel-->>UI: Update Cohort List

UI->>Notification: Show Deletion Success

  

%% Navigation Guard

User->>UI: Attempt to Navigate Away

UI->>ViewModel: Check for Unsaved Changes

alt Unsaved Changes Present

ViewModel->>UI: Prompt to Save or Discard

User->>UI: Choose to Discard

UI->>ViewModel: Proceed with Navigation

else No Unsaved Changes

UI->>ViewModel: Proceed with Navigation

end

</div>

</div>

  
  

<!-- Data Dictionary Section -->

<div  class="entity"  aria-labelledby="data-dictionary">

<h2  id="data-dictionary">Data Dictionary</h2>

<p  class="section-description">

The Data Dictionary below outlines the key data entities used within the Cohort Management module, detailing

their attributes, types, and descriptions.

</p>

  

<!-- User Entity -->

<div  class="entity">

<h3>User</h3>

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

<td>UserID</td>

<td>UUID</td>

<td>Unique identifier for the user.</td>

</tr>

<tr>

<td>Username</td>

<td>String</td>

<td>Name of the user.</td>

</tr>

<tr>

<td>Role</td>

<td>Enum</td>

<td>Role of the user (e.g., Admin, Manager).</td>

</tr>

</tbody>

</table>

</div>

  

<!-- Cohort Entity -->

<div  class="entity">

<h3>Cohort</h3>

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

<td>id</td>

<td>UUID</td>

<td>Unique identifier for the cohort.</td>

</tr>

<tr>

<td>name</td>

<td>String</td>

<td>Name of the cohort.</td>

</tr>

<tr>

<td>description</td>

<td>String</td>

<td>Description of the cohort.</td>

</tr>

<tr>

<td>startDate</td>

<td>Date</td>

<td>Start date of the cohort.</td>

</tr>

<tr>

<td>endDate</td>

<td>Date</td>

<td>End date of the cohort.</td>

</tr>

<tr>

<td>teams</td>

<td>List&lt;Team&gt;</td>

<td>List of teams associated with the cohort.</td>

</tr>

</tbody>

</table>

</div>

  

<!-- Team Entity -->

<div  class="entity">

<h3>Team</h3>

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

<td>teamId</td>

<td>UUID</td>

<td>Unique identifier for the team.</td>

</tr>

<tr>

<td>teamName</td>

<td>String</td>

<td>Name of the team.</td>

</tr>

<tr>

<td>members</td>

<td>List&lt;User&gt;</td>

<td>List of team members.</td>

</tr>

</tbody>

</table>

</div>

  

<!-- Dialog Entity -->

<div  class="entity">

<h3>Dialog</h3>

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

<td>dialogType</td>

<td>Enum</td>

<td>Type of dialog (e.g., Confirmation, Warning).</td>

</tr>

<tr>

<td>message</td>

<td>String</td>

<td>The content displayed in the dialog.</td>

</tr>

<tr>

<td>userResponse</td>

<td>Enum</td>

<td>User's response to the dialog (e.g., Confirm, Cancel).</td>

</tr>

</tbody>

</table>

</div>

</div>

  
  

<!-- Explanation Section -->

<div  class="explanation"  aria-labelledby="explanation-section">

<h2  id="explanation-section">Explanation</h2>

<ul>

<li><strong>Main Navigation:</strong> Users navigate to the Cohort Management interface and load the list of

cohorts.</li>

<li><strong>Create Cohort:</strong> Describes the process of adding a new cohort, from initializing the form

to saving the cohort and updating the UI.</li>

<li><strong>Edit Cohort:</strong> Details how users can select and modify existing cohorts, including

loading details, submitting changes, and refreshing the cohort list.</li>

<li><strong>Delete Cohort:</strong> Explains the steps involved in removing a cohort, including confirmation

and updating the UI.</li>

<li><strong>Navigation Guard:</strong> Discusses how the system handles attempts to navigate away with

unsaved changes, prompting the user to save or discard.</li>

</ul>

</div>

  

<!-- ARIA Compliance Enhancements -->

<main  role="main">

<!-- Existing content with ARIA attributes added -->

</main>

  

<!-- Footer Section -->



</body>

  

</html>
