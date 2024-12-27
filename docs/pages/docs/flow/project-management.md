
<!DOCTYPE  html>

<html  lang="en">

  

<head>

<meta  charset="UTF-8">

<title>Project Management Documentation - ProjectHub</title>

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

  

<h1>Project Management Documentation</h1>

  

<!-- In-Page Navigation Links -->

<nav  aria-label="Project Management Navigation">

<div  class="documentation-links">

<a  href="#ui-component-hierarchy">UI Component Hierarchy</a> |

<a  href="#project-dashboard-sequence">Project Dashboard Sequence</a> |

<a  href="#project-details-sequence">Project Details Sequence</a> |

<a  href="#workshop-sequence">Workshop Sequence</a> |

<a  href="#performance-analysis-sequence">Performance Analysis Sequence</a> |

<a  href="#data-dictionary">Data Dictionary</a> |

<a  href="javascript:history.back()">Go Back</a>

</div>

</nav>

  

<!-- Documentation Section -->

<section  aria-labelledby="project-management-doc">

<h2  id="project-management-doc">Project Management Documentation</h2>

<p>Comprehensive guide on managing projects within ProjectHub, including project setup, milestone tracking, and

resource allocation.</p>

</section>

  

<main  role="main">

<div  class="diagram-section">

<h2  id="ui-component-hierarchy">UI Component Hierarchy</h2>

<div  class="mermaid">
graph TD

%% Core Layout
A[BorderPane: Root]
B[TabPane: Content]
A --> B

%% Tab Views
C[ScrollPane: Dashboard]
D[ScrollPane: Details]
E[ScrollPane: Workshop]
F[ScrollPane: Analytics]

B --> C
B --> D
B --> E
B --> F

%% Dashboard Components
G[Statistics]
H[Progress]
I[Charts]
C --> G & H & I

%% Details Components
J[Details Form]
K[Tasks]
L[Resources]
D --> J & K & L

%% Workshop Components
M[WorkArea]
N[Tools]
O[Layers]
E --> M & N & O

%% Analytics Components
P[Charts]
Q[Metrics]
F --> P & Q

%% Styling
classDef c1 fill:#e1f5fe,stroke:#01579b
classDef c2 fill:#fff,stroke:#0288d1
classDef c3 fill:#e8f5e9,stroke:#2e7d32

class A,B c1
class C,D,E,F c2
class G,H,I,J,K,L,M,N,O,P,Q c3
</div>

  

</div>

  

<h2  id="project-dashboard-sequence">Project Dashboard Sequence Diagram</h2>

<div  class="mermaid">

sequenceDiagram

actor User

participant DashboardView

participant DashboardController

participant ProjectViewModel

participant StatisticsService

participant DB

  

%% Initial Dashboard Load

User->>DashboardView: Open Dashboard

DashboardView->>DashboardController: initialize()

DashboardController->>ProjectViewModel: loadProjects()

ProjectViewModel->>DB: fetchProjects()

DB-->>ProjectViewModel: projects list

ProjectViewModel-->>DashboardController: updateProjectSelector

  

par Statistics Cards

DashboardController->>StatisticsService: getTaskStats()

StatisticsService->>DB: fetch task metrics

DB-->>StatisticsService: task counts

StatisticsService-->>DashboardController: update stat cards

and Progress Grid

DashboardController->>StatisticsService: getProjectProgress()

StatisticsService->>DB: fetch progress data

DB-->>StatisticsService: progress metrics

StatisticsService-->>DashboardController: update progress bars

end

  

DashboardController-->>DashboardView: refresh UI

DashboardView-->>User: Display Dashboard

  

%% Project Selection

User->>DashboardView: Select Project

DashboardView->>DashboardController: handleProjectSelection()

DashboardController->>ProjectViewModel: updateSelectedProject()

ProjectViewModel->>DB: fetchProjectDetails()

DB-->>ProjectViewModel: project details

ProjectViewModel-->>DashboardController: update project view

DashboardController-->>DashboardView: refresh project data

  

%% View Details

User->>DashboardView: Click View Details

DashboardView->>DashboardController: handleViewDetails()

DashboardController-->>DashboardView: navigate to details view

</div>

  

<h2  id="project-details-sequence">Project Details Sequence Diagram</h2>

<div  class="mermaid">

sequenceDiagram

actor User

participant DetailView

participant DetailController

participant ProjectViewModel

participant TaskService

participant FileService

participant ResourceService

participant DB

  

%% Initial Load

User->>DetailView: Open Project Details

DetailView->>DetailController: initialize()

DetailController->>ProjectViewModel: loadProjectsList()

ProjectViewModel->>DB: fetchProjects()

DB-->>ProjectViewModel: projects list

ProjectViewModel-->>DetailController: updateProjectSelector()

  

%% Project Selection

User->>DetailView: Select Project

DetailView->>DetailController: handleProjectSelection(projectId)

  

par Project Info

DetailController->>ProjectViewModel: getProjectDetails()

ProjectViewModel->>DB: fetch project

DB-->>ProjectViewModel: project data

ProjectViewModel-->>DetailController: update project fields

and Task List

DetailController->>TaskService: getProjectTasks()

TaskService->>DB: fetch tasks

DB-->>TaskService: tasks data

TaskService-->>DetailController: update tasksTable

and File List

DetailController->>FileService: getProjectFiles()

FileService->>DB: fetch files

DB-->>FileService: files data

FileService-->>DetailController: update filesTable

and Resources

DetailController->>ResourceService: getProjectResources()

ResourceService->>DB: fetch resources

DB-->>ResourceService: resources data

ResourceService-->>DetailController: update resourcesTable

end

  

DetailController-->>DetailView: refresh UI

  

%% Task Operations

User->>DetailView: Add Task

DetailView->>DetailController: handleAddTask()

DetailController->>TaskService: createTask(taskData)

TaskService->>DB: save task

DB-->>TaskService: confirmation

TaskService-->>DetailController: update tasksTable

  

%% File Operations

User->>DetailView: Upload File

DetailView->>DetailController: handleFileUpload()

DetailController->>FileService: uploadFile(fileData)

FileService->>DB: save file

DB-->>FileService: confirmation

FileService-->>DetailController: update filesTable

  

%% Resource Management

User->>DetailView: Add Resource

DetailView->>DetailController: handleAddResource()

DetailController->>ResourceService: addResource(resourceData)

ResourceService->>DB: save resource

DB-->>ResourceService: confirmation

ResourceService-->>DetailController: update resourcesTable

  

%% Progress Update

DetailController->>ProjectViewModel: updateProgress()

ProjectViewModel->>DB: save progress

DB-->>ProjectViewModel: confirmation

ProjectViewModel-->>DetailController: refresh progress bar

DetailController-->>DetailView: update UI

</div>

  

<h2  id="workshop-sequence">Workshop Sequence Diagram</h2>

<div  class="mermaid">

sequenceDiagram

actor User

participant WorkshopView

participant WorkshopController

participant ResourceManager

participant LayerManager

participant CanvasManager

participant PropertyManager

participant FileSystem

  

%% Initial Load

User->>WorkshopView: Open Workshop

WorkshopView->>WorkshopController: initialize()

  

par Resource Loading

WorkshopController->>ResourceManager: loadResources()

ResourceManager->>FileSystem: fetchResourceList()

FileSystem-->>ResourceManager: resources

ResourceManager-->>WorkshopController: updateResourceList()

and Layer Setup

WorkshopController->>LayerManager: initializeLayers()

LayerManager-->>WorkshopController: layerStructure

and Canvas Setup

WorkshopController->>CanvasManager: setupCanvas()

CanvasManager-->>WorkshopController: canvasReady

end

  

WorkshopController-->>WorkshopView: setup complete

  

%% Resource Operations

User->>WorkshopView: Select Resource

WorkshopView->>WorkshopController: handleResourceSelection()

WorkshopController->>ResourceManager: loadResource()

ResourceManager-->>WorkshopController: resourceLoaded

WorkshopController->>CanvasManager: placeResourceOnCanvas()

  

%% Layer Management

User->>WorkshopView: Add Layer

WorkshopView->>WorkshopController: handleAddLayer()

WorkshopController->>LayerManager: createNewLayer()

LayerManager-->>WorkshopController: layerCreated

WorkshopController->>CanvasManager: refreshLayers()

  

%% Canvas Interactions

User->>WorkshopView: Modify Canvas

WorkshopView->>WorkshopController: handleCanvasAction()

WorkshopController->>CanvasManager: processAction()

CanvasManager->>PropertyManager: updateProperties()

PropertyManager-->>WorkshopController: propertiesUpdated

WorkshopController-->>WorkshopView: refresh view

  

%% Save Operation

User->>WorkshopView: Click Save

WorkshopView->>WorkshopController: handleSave()

WorkshopController->>CanvasManager: captureState()

CanvasManager-->>WorkshopController: currentState

WorkshopController->>FileSystem: saveProject()

FileSystem-->>WorkshopController: saveConfirmed

WorkshopController-->>WorkshopView: show success

  

%% Undo/Redo

User->>WorkshopView: Click Undo

WorkshopView->>WorkshopController: handleUndo()

WorkshopController->>CanvasManager: undoLastAction()

CanvasManager->>PropertyManager: syncProperties()

PropertyManager-->>WorkshopController: stateRestored

WorkshopController-->>WorkshopView: refresh canvas

</div>

  
  

<h2  id="performance-analysis-sequence">Project Performance Analysis Sequence Diagram</h2>

<div  class="mermaid">

sequenceDiagram

actor User

participant AnalyticsView

participant AnalyticsController

participant ChartService

participant ResourceService

participant DB

  

%% Initial Load

User->>AnalyticsView: Open Analytics

AnalyticsView->>AnalyticsController: initialize()

AnalyticsController->>ChartService: loadProjectList()

ChartService->>DB: fetchProjects()

DB-->>ChartService: projects

ChartService-->>AnalyticsController: updateProjectSelector

  

%% Project Selection

User->>AnalyticsView: Select Project

AnalyticsView->>AnalyticsController: handleProjectSelection()

  

par Overall Progress Chart

AnalyticsController->>ChartService: getProgressData()

ChartService->>DB: fetchProgressMetrics

DB-->>ChartService: progress data

ChartService-->>AnalyticsController: updatePieChart

and Tasks Overview

AnalyticsController->>ChartService: getTasksOverview()

ChartService->>DB: fetchTaskMetrics

DB-->>ChartService: tasks data

ChartService-->>AnalyticsController: updateBarChart

and Completion Rate

AnalyticsController->>ChartService: getCompletionTrend()

ChartService->>DB: fetchTrendData

DB-->>ChartService: trend metrics

ChartService-->>AnalyticsController: updateLineChart

and Resource Table

AnalyticsController->>ResourceService: getResourceUtilization()

ResourceService->>DB: fetchResourceData

DB-->>ResourceService: resource metrics

ResourceService-->>AnalyticsController: updateTable

end

  

AnalyticsController-->>AnalyticsView: refreshUI

AnalyticsController->>AnalyticsView: updateStatusBar

AnalyticsView-->>User: Display Analytics

  

%% Back Navigation

User->>AnalyticsView: Click Back

AnalyticsView->>AnalyticsController: handleBack()

AnalyticsController-->>AnalyticsView: navigateToDashboard

</div>

</div>

  
  

<!-- Updated Data Dictionary -->

<div  id="data-dictionary"  class="data-dictionary">

<h2>Unified Data Dictionary</h2>

<p  class="section-description"></p>

Comprehensive data structures used across project management modules.

</p>

  

<h3>Project Entities</h3>

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

<td>Project</td>

<td>

UUID projectId<br>

String name<br>

String description<br>

DateTime startDate<br>

DateTime endDate<br>

ProjectStatus status<br>

Double progress

</td>

<td>Core project information</td>

</tr>

<tr>

<td>Task</td>

<td>

UUID taskId<br>

String title<br>

String description<br>

TaskStatus status<br>

DateTime dueDate<br>

UUID assigneeId

</td>

<td>Project task details</td>

</tr>

<tr>

<td>Resource</td>

<td>

UUID resourceId<br>

String name<br>

ResourceType type<br>

Double utilization<br>

Boolean isAvailable

</td>

<td>Project resource information</td>

</tr>

</tbody>

</table>

  

<h3>Analytics Data</h3>

<table>

<thead>

<tr>

<th>Metric</th>

<th>Fields</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>Performance Metrics</td>

<td>

Double completionRate<br>

Integer taskCount<br>

Integer completedTasks<br>

Double progressPercentage

</td>

<td>Project performance indicators</td>

</tr>

<tr>

<td>Resource Metrics</td>

<td>

Double utilizationRate<br>

Integer activeResources<br>

Integer totalResources<br>

Map&lt;ResourceType, Integer> distribution

</td>

<td>Resource utilization metrics</td>

</tr>

</tbody>

</table>

  

<h3>Workshop Components</h3>

<table>

<thead>

<tr>

<th>Component</th>

<th>Fields</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>Canvas State</td>

<td>

List&lt;Layer> layers<br>

Map&lt;String, Object> properties<br>

List&lt;HistoryAction> undoStack<br>

List&lt;HistoryAction> redoStack

</td>

<td>Workshop canvas state</td>

</tr>

<tr>

<td>Resource Asset</td>

<td>

String assetId<br>

String path<br>

AssetType type<br>

Map&lt;String, String> metadata

</td>

<td>Workshop resource assets</td>

</tr>

</tbody>

</table>

</div>

  
  

</main>

  



</body>

  

</html>
