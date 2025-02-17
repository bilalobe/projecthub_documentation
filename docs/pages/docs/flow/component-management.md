﻿
<!DOCTYPE  html>

<html  lang="en">

  

<head>

<meta  charset="UTF-8">

<title>Component Management - Data Dictionary and Sequence Diagram</title>

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

<section  aria-labelledby="component-management-doc">

<h1  id="component-management-title">Component Management</h1>

<p>This documentation provides a comprehensive overview of the Component Management module, including data structures, user interface components, and interaction flows.</p>

</section>

  

<!-- UI Component Hierarchy -->

<div  class="diagram-section"  aria-label="UI Component Hierarchy">

<h2>UI Component Hierarchy</h2>

<div  class="mermaid">

graph TD

%% Main Components

Root[BorderPane: Root]

Content[ScrollPane: Content]

Details[VBox: Details]

Actions[HBox: Actions]

  

%% Form Components

ComponentForm[Form: ComponentForm]

NameField[TextField: Name]

DescField[TextArea: Description]

ProjectSelect[ComboBox: Project]

  

%% Action Components

SaveBtn[Button: Save]

DeleteBtn[Button: Delete]

CancelBtn[Button: Cancel]

  

%% Status Components

StatusBar[HBox: StatusBar]

ProgressIndicator[ProgressBar]

StatusLabel[Label: Status]

  

%% Hierarchy

Root --> Content

Content --> Details

Details --> ComponentForm

Details --> Actions

Details --> StatusBar

  

ComponentForm --> NameField

ComponentForm --> DescField

ComponentForm --> ProjectSelect

  

Actions --> SaveBtn

Actions --> DeleteBtn

Actions --> CancelBtn

  

StatusBar --> ProgressIndicator

StatusBar --> StatusLabel

  

%% Styling

classDef container fill:#e1f5fe,stroke:#01579b

classDef component fill:#fff,stroke:#0288d1

classDef control fill:#e8f5e9,stroke:#2e7d32

  

class Root,Content,Details container

class ComponentForm,Actions,StatusBar component

class NameField,DescField,ProjectSelect,SaveBtn,DeleteBtn,CancelBtn,ProgressIndicator,StatusLabel control

</div>

</div>

<!-- Sequence Diagram Section -->

<div  class="diagram"  aria-label="Sequence Diagram">

<h2>Sequence Diagram</h2>

<p  class="section-description">

The following sequence diagram illustrates the interactions between the user interface, controllers, view

models, services, and the database during component management operations.

</p>

<div  class="mermaid">

sequenceDiagram

actor User

participant UI as Component Details UI

participant Controller as ComponentDetailsController

participant ViewModel as ComponentDetailsViewModel

participant Service as ComponentService

participant Database as Database

participant Notification as Notification System

  

%% View Component

User->>UI: View Component Details

UI->>Controller: initialize()

Controller->>ViewModel: Bind Properties

Note right of Controller: Binds UI controls to ViewModel properties

  

%% Create/Edit Flow

User->>UI: Enter Component Details

UI->>Controller: saveComponent(event)

Controller->>Controller: Validate Input

Note right of Controller: Check componentName and projectId

  

alt Invalid Input

Controller-->>UI: Show Validation Error

else Valid Input

Controller->>ViewModel: saveComponent(componentDTO)

ViewModel->>Service: saveComponent() / updateComponent()

Service->>Database: Persist Changes

Database-->>Service: Return Result

Service-->>ViewModel: Return Saved Component

ViewModel-->>Controller: Update UI

Controller-->>UI: Show Success Message

end

  

%% Delete Flow

User->>UI: Click Delete

UI->>Controller: deleteComponent(event)

Controller->>ViewModel: deleteComponent(id)

ViewModel->>Service: deleteComponent()

Service->>Database: Delete Record

Database-->>Service: Confirm Deletion

Service-->>ViewModel: Return Success

ViewModel-->>Controller: clearComponent()

Controller-->>UI: Update UI State

  

%% Error Handling

alt Error Occurs

Service-->>ViewModel: Throw Exception

ViewModel-->>Controller: Log Error

Controller-->>UI: Show Error Dialog

end

</div>

</div>

<!-- Data Dictionary Section -->

<div  class="entity"  aria-labelledby="data-dictionary">

<h2  id="data-dictionary">Data Dictionary</h2>

<p  class="section-description">

The Data Dictionary below outlines the key data entities used within the Component Management module,

detailing their attributes, types, and descriptions.

</p>

  

<!-- Component Entity -->

<div  class="entity">

<h3>Component</h3>

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

<td>componentId</td>

<td>UUID</td>

<td>Unique identifier for the component.</td>

</tr>

<tr>

<td>componentName</td>

<td>String</td>

<td>Name of the component.</td>

</tr>

<tr>

<td>componentDescription</td>

<td>String</td>

<td>Detailed description of the component.</td>

</tr>

<tr>

<td>projectId</td>

<td>UUID</td>

<td>Reference to the parent project.</td>

</tr>

</tbody>

</table>

</div>

</div>

  
  
  

<!-- Explanation Section (Optional) -->

<div  class="explanation"  aria-labelledby="explanation-section">

<h2  id="explanation-section">Explanation</h2>

<p  class="section-description">

This sequence diagram captures the lifecycle of a component within the system, detailing how user actions

propagate through the UI, controllers, view models, services, and the database. It ensures that each step,

from viewing to deleting a component, is clearly defined and handled.

</p>

<ul>

<li><strong>View Component:</strong> The user initiates a request to view component details, triggering the

initialization and property binding processes.</li>

<li><strong>Create/Edit Flow:</strong> Allows users to add or modify component details, incorporating

validation before persisting changes.</li>

<li><strong>Delete Flow:</strong> Facilitates the removal of a component, ensuring confirmation and proper

state updates post-deletion.</li>

<li><strong>Error Handling:</strong> Manages exceptions gracefully by logging errors and notifying the user.

</li>

</ul>

</div>

  
  

<!-- Footer Section (Optional) -->



</body>

  

</html>
