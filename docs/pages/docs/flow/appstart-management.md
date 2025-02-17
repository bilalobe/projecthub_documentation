﻿<!DOCTYPE  html>

<html  lang="en">

  

<head>

<meta  charset="UTF-8">

<title>Application Startup Management - ProjectHub</title>

<link  rel="stylesheet"  href="../docs/styles.css">

<script  type="module">

import mermaid from  'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';

mermaid.initialize({ startOnLoad: true });

</script>

</head>

  

<body  class="non-copiable">

<!-- Documentation Section -->

<section  aria-labelledby="appstart-management-doc">

<h1  id="appstart-management-title">Application Startup Management</h1>

<p>Documentation for ProjectHub's application startup process, detailing initialization sequences, resource loading, and view setup procedures.</p>

</section>

  

<!-- In-Page Navigation Links -->

<nav  aria-label="Appstart Management Navigation">

<div  class="documentation-links">

<a  href="#ui-component-hierarchy">UI Component Hierarchy</a> |

<a  href="#startup-sequence-diagram">Startup Sequence Diagram</a> |

<a  href="#data-dictionary">Data Dictionary</a> |

<a  href="javascript:history.back()">Go Back</a>

</div>

</nav>

  

<!-- Component Hierarchy -->

<div  class="diagram-section"  aria-label="UI Component Hierarchy"  id="ui-component-hierarchy">

<h2>UI Component Hierarchy</h2>

<div  class="mermaid">

graph TD

%% Main Components

Root[BorderPane: Root]

Stage[Stage: MainStage]

Scene[Scene: MainScene]

Resources[ResourceBundle]

Styles[StylesheetManager]

%% View Components

NavDrawer[VBox: NavigationDrawer]

AppBar[HBox: AppBar]

Content[StackPane: Content]

StatusBar[HBox: StatusBar]

%% Hierarchy

Stage --> Scene

Scene --> Root

Root --> Resources

Root --> Styles

Root --> NavDrawer

Root --> AppBar

Root --> Content

Root --> StatusBar

%% Resource Management

Resources --> Messages[i18n.messages]

Resources --> Config[app.config]

Styles --> Theme[theme.css]

%% Styling

classDef container fill:#e1f5fe,stroke:#01579b

classDef component fill:#fff,stroke:#0288d1

classDef resource fill:#e8f5e9,stroke:#2e7d32

class Stage,Scene,Root container

class NavDrawer,AppBar,Content,StatusBar component

class Resources,Styles,Messages,Config,Theme resource

</div>

</div>

  

<!-- Sequence Diagram Section -->

<div  class="sequence-diagrams"  aria-label="Startup Sequence Diagram"  id="startup-sequence-diagram">

<h2>Application Startup Sequence</h2>

<div  class="mermaid">

sequenceDiagram

participant App as MainApp

participant Stage as MainStage

participant View as MainView

participant Controller as MainViewController

participant Resources as ResourceBundle

participant CSS as StylesheetManager

  

Note over App,Resources: Application Startup Phase

App->>Resources: getBundle("i18n.messages")

Resources-->>App: ResourceBundle

  

Note over App,Stage: View Initialization

App->>Stage: new Stage()

App->>View: loadMainView()

View->>Controller: initialize()

  

par Resource Loading

Controller->>Resources: loadMessages()

Resources-->>Controller: i18n strings

Controller->>CSS: loadStyles()

CSS-->>Controller: stylesheets

end

  

Note over Controller: View Setup

Controller->>Controller: setupNavigation()

Controller->>Controller: setupAppBar()

Controller->>Controller: initializeContent()

  

Note over App,Stage: Display

App->>Stage: setScene()

App->>Stage: show()

Stage-->>App: viewReady

  

Note over App: Error Handling

alt Loading Error

App->>App: logError()

App->>Stage: showErrorDialog()

end

</div>

</div>

  

<!-- Data Dictionary Section -->

<div  id="data-dictionary"  class="data-dictionary"  aria-labelledby="data-dictionary">

<h2  id="data-dictionary">Data Dictionary</h2>

<p  class="section-description">Key components and their responsibilities in the application startup process.</p>

  

<h3>Core Components</h3>

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

<td>MainApp</td>

<td>Application</td>

<td>Main application class that initiates the startup sequence.</td>

</tr>

<tr>

<td>MainView</td>

<td>FXML View</td>

<td>Root view container for the application UI.</td>

</tr>

<tr>

<td>MainViewController</td>

<td>Controller</td>

<td>Controls main view behavior and navigation.</td>

</tr>

<tr>

<td>ResourceBundle</td>

<td>Resource Manager</td>

<td>Manages internationalization resources.</td>

</tr>

<tr>

<td>StylesheetManager</td>

<td>Style Manager</td>

<td>Handles application styling and themes.</td>

</tr>

</tbody>

</table>

  

<h3>Configuration Properties</h3>

<table>

<thead>

<tr>

<th>Property</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>i18n.messages</td>

<td>Properties</td>

<td>Internationalization string resources.</td>

</tr>

<tr>

<td>app.config</td>

<td>Properties</td>

<td>Application configuration settings.</td>

</tr>

<tr>

<td>theme.css</td>

<td>Stylesheet</td>

<td>Custom application styling.</td>

</tr>

</tbody>

</table>

</div>

  

<!-- Process Explanation Section -->

<div  class="explanation"  aria-labelledby="process-explanation">

<h2  id="process-explanation">Startup Process Explanation</h2>

<ul>

<li><strong>Resource Loading:</strong> Initializes application resources including internationalization bundles and configuration properties.</li>

<li><strong>View Initialization:</strong> Loads the main FXML view and establishes controller bindings.</li>

<li><strong>Style Application:</strong> Applies both Gluon framework styles and custom application themes.</li>

<li><strong>Error Handling:</strong> Implements graceful error handling during startup with user notifications.</li>

<li><strong>Navigation Setup:</strong> Configures the navigation drawer and main content area for the application.</li>

</ul>

</div>

  

<!-- ARIA Compliance Enhancements -->

<main  role="main">

<!-- Existing content with ARIA attributes added -->

</main>

  



</body>

  

</html>
