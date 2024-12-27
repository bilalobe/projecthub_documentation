
<!DOCTYPE  html>

<html  lang="en">

  

<head>

<meta  charset="UTF-8">

<title>Team Management Documentation - ProjectHub</title>

<link  rel="stylesheet"  href="../docs/styles.css">

<script  type="module">

import mermaid from  'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';

mermaid.initialize({ startOnLoad: true });

</script>

</head>

  

<body  class="non-copiable">
<!-- Documentation Section -->

<section  aria-labelledby="team-management-doc">

<h1  id="team-management-title">Team Management Documentation</h1>
<!-- In-Page Navigation Links -->

<nav  aria-label="Team Management Navigation">

<div  class="documentation-links">

<a  href="#component-hierarchy">Component Hierarchy</a> |

<a  href="#team-management-sequence">Team Management Sequence</a> |

<a  href="#data-dictionary">Data Dictionary</a> |

<a  href="javascript:history.back()">Go Back</a>

</div>

</nav>

<p>This documentation covers ProjectHub's team management system, including team creation, member assignments, and project associations.</p>

</section>


  



  

<!-- Component Hierarchy Diagram -->

<div  class="diagram-section"  aria-label="Component Hierarchy">

<h2  id="component-hierarchy">Component Hierarchy</h2>

<div  class="mermaid">

graph TD

%% Main Components

Root[BorderPane: Root]

Content[SplitPane: Content]

List[VBox: TeamList]

Details[ScrollPane: Details]

  

%% List Components

SearchBar[TextField: Search]

TeamTable[TableView: Teams]

AddButton[Button: AddTeam]

  

%% Details Components

TeamForm[Form: TeamForm]

NameField[TextField: Name]

CohortSelect[ComboBox: Cohort]

MemberList[TableView: Members]

ProjectList[TableView: Projects]

  

%% Action Components

Actions[HBox: Actions]

SaveBtn[Button: Save]

DeleteBtn[Button: Delete]

  

%% Hierarchy

Root --> Content

Content --> List

Content --> Details

  

List --> SearchBar

List --> TeamTable

List --> AddButton

  

Details --> TeamForm

TeamForm --> NameField

TeamForm --> CohortSelect

Details --> MemberList

Details --> ProjectList

Details --> Actions

  

Actions --> SaveBtn

Actions --> DeleteBtn

  

%% Styling

classDef container fill:#e1f5fe,stroke:#01579b

classDef component fill:#fff,stroke:#0288d1

classDef control fill:#e8f5e9,stroke:#2e7d32

  

class Root,Content container

class List,Details,TeamForm component

class SearchBar,TeamTable,NameField,CohortSelect,MemberList,ProjectList,SaveBtn,DeleteBtn control

</div>

</div>

  

<!-- Sequence Diagrams Section -->

<div  class="sequence-diagrams"  aria-label="Team Management Sequence Diagram">

<h2  id="team-management-sequence">Team Management Sequence</h2>

<div  class="mermaid">

sequenceDiagram

actor User

participant View as TeamView

participant Controller as TeamController

participant ViewModel as TeamViewModel

participant Service as TeamService

participant DB as Database

  

%% Load Teams

User->>View: Open Teams

View->>Controller: initialize()

Controller->>ViewModel: loadTeams()

ViewModel->>Service: getAllTeams()

Service->>DB: fetchTeams()

DB-->>Service: teams

Service-->>ViewModel: teamsList

ViewModel-->>View: updateTeamTable()

  

%% Team Operations

User->>View: Create Team

View->>Controller: handleNewTeam()

Controller->>ViewModel: createTeam(TeamDTO)

ViewModel->>Service: saveTeam()

Service->>DB: persist()

DB-->>Service: confirmation

Service-->>View: showSuccess()

  

%% Member Management

User->>View: Add Member

View->>Controller: handleAddMember()

Controller->>ViewModel: addMember(userId)

ViewModel->>Service: assignMember()

Service->>DB: updateTeam()

DB-->>Service: updated

Service-->>View: refreshMembers()

</div>

  

<div  id="data-dictionary"  class="data-dictionary"  aria-labelledby="data-dictionary">

<h2  id="data-dictionary">Data Dictionary</h2>

  

<h3>Team Entity</h3>

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

<td>teamId</td>

<td>UUID</td>

<td>Unique identifier</td>

</tr>

<tr>

<td>name</td>

<td>String</td>

<td>Team name</td>

</tr>

<tr>

<td>cohortId</td>

<td>UUID</td>

<td>Associated cohort</td>

</tr>

<tr>

<td>members</td>

<td>List&lt;UUID&gt;</td>

<td>Team members</td>

</tr>

<tr>

<td>projects</td>

<td>List&lt;UUID&gt;</td>

<td>Assigned projects</td>

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

<td>selectedTeam</td>

<td>TeamDTO</td>

<td>Currently selected team</td>

</tr>

<tr>

<td>memberList</td>

<td>ObservableList&lt;UserDTO&gt;</td>

<td>Team members list</td>

</tr>

<tr>

<td>projectList</td>

<td>ObservableList&lt;ProjectDTO&gt;</td>

<td>Team projects</td>

</tr>

</tbody>

</table>

</div>

</div>

  

<!-- ARIA Compliance Enhancements -->

<main  role="main">

<!-- Existing content with ARIA attributes added -->

</main>

  



</body>

  

</html>
