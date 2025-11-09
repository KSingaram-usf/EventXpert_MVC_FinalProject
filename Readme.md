# 🏟️ EventXpert: Dynamic Sports Event Platform (MVC Implementation)

## 🌟 Project Introduction

EventXpert is a web application designed to track, manage, and analyze sports events, primarily focusing on Tampa Bay teams like the USF Bulls. EventXpert has been successfully transformed from a static website into a dynamic, **full-stack web application** built on the **ASP.NET Core MVC framework**. Designed with a USF and Tampa Bay sports theme, the application serves as a central hub for managing and analyzing events.

This current iteration fully implements the **Model-View-Controller (MVC) architecture**, establishing a clear separation between data logic, application functionality, and the user interface.

## Key Features

* **Persistent Data Management:** Event details are securely saved using an **EF Core/SQLite database**.
* **Full Event Management:** A complete **Create, Read, Update, Delete (CRUD)** interface is implemented for managing event records.
* **Dynamic Dashboard:** Real-time content is provided through integration with **external APIs** for live sports scores and local weather updates.
* **Cloud Deployment:** The entire application is successfully hosted and operational on **Microsoft Azure**.

---

## 💻 Technologies Used

* **Framework:** ASP.NET Core MVC (C#)
* **Database:** SQLite (managed by Entity Framework Core)
* **Cloud:** Microsoft Azure

## Key Functions of EventXpert

EventXpert is a dynamic platform designed to manage and display information about Tampa Bay sports events.

* **Event Management (Full CRUD):** Users can easily **Create, Read, Update, and Delete** sports event records (including matches, dates, venues, and prices) via a dedicated interface.
* **Data Visualization:** The application integrates **interactive charts** (using Chart.js) to provide analytical insights, such as visualizing average ticket prices by team and event counts per venue.
* **Real-Time Dashboard:** The homepage offers dynamic content by fetching and displaying live external data, including:
    * Local **Tampa weather** conditions (from the Open-Meteo API).
    * **Live sports scores** and match statuses (from TheSportsDB API).
* **Robust Architecture:** The final application is built using a formal **MVC (Model-View-Controller) structure** and uses a persistent **SQLite database** for reliable data storage.
* **USF Theme:** The entire design incorporates the official **University of South Florida** green, gold, and white color schemes for a cohesive look.

## 1. 🏗️ Functional Web Application: MVC Transformation

The core focus of this project phase was transitioning the initial static HTML prototype into a robust, dynamic application using the **Model-View-Controller (MVC) architectural pattern** built on ASP.NET Core.

This transformation ensured that application logic, data handling, and the user interface are cleanly separated, resulting in a scalable and maintainable codebase.

### Full CRUD Implementation

We have successfully implemented complete **Create, Read, Update, and Delete (CRUD)** operations for the core `Event` entity.

* **Dynamic Data Reflection:** Changes made through any CRUD operation (adding, editing, or deleting an event) are immediately reflected across the entire application:
    * The **Manage Events** page updates instantly.
    * The **Event Dashboard** reflects upcoming events accurately.
    * The **Data Visualization** charts dynamically recalculate to include or exclude the updated data points.
* **Dual Interface:** CRUD functionality is exposed via two mechanisms:
    1.  Standard **MVC Views** (server-side rendering).
    2.  A dedicated **REST API endpoint** (`api/EventsApi`) used by JavaScript on the client-side for highly interactive event management.

## Data Management and Persistence

Our application utilizes an **External Database** model for persistent data management, ensuring all event records remain consistent across user sessions and application deployments.

* **Database Choice:** We selected **SQLite** (a local, file-based relational database) for streamlined development, managed entirely by **Entity Framework Core (EF Core)**.
* **Data Consistency:** EF Core handles the structural setup, querying, and updating of the `eventxpert.db` file, guaranteeing that all **CRUD operations** reliably save changes to the data layer.
* **Configuration:** Database connection details are managed securely via the application's configuration files:
    ```json
    "ConnectionStrings": {
      "DefaultConnection": "Data Source=eventxpert.db"
    }
    ```
* **Scalability Note:** While SQLite is suitable for this project's requirements, the EF Core abstraction ensures the application is structured to easily migrate to a cloud-hosted database (like Azure SQL Database or PostgreSQL) if scalability were required in the future.

## API Integration and Real-Time Data Fetching

We successfully integrated external APIs relevant to our application's domain *only* for fetching and displaying real-time data, ensuring we adhere to the rule of not using them for persistent data storage.

### Dynamic Dashboard Content

The application's homepage has been transformed into a dynamic dashboard by fetching live information from two separate services:

* **Local Weather:** We use the **Open-Meteo API** to fetch the current temperature, wind speed, and precipitation chance for Tampa, which helps users prepare for local events.
* **Live Sports Scores:** We utilize **TheSportsDB API** to display a scoreboard of ongoing soccer matches, adding real-time relevance to our sports hub.

### Technical Implementation

* **Secure Key Handling:** All API keys are loaded **securely from the `IConfiguration` service** (defined in `appsettings.json`) in the backend. This ensures the keys are never exposed on the client-side or hardcoded directly into the application's source files.
* **Performance (Asynchronous Processing):** All external API calls are handled **asynchronously** within the `HomeController`. This technique prevents the entire application from freezing while waiting for external servers to respond, ensuring the user interface remains fast and responsive.

## Azure Deployment and Resource Management

The final, fully dynamic MVC application is hosted in the cloud on **Microsoft Azure App Service** to ensure global accessibility and stability.

* **Deployment Status:** The site has been successfully deployed, thoroughly tested, and is **fully accessible** via its public Azure URL. All core features—including **CRUD operations**, data persistence (SQLite), and real-time API fetching—were verified post-deployment.

* **Hosting Configuration:** The application uses the **ASP.NET Core Module V2** to execute the compiled application (`.dll`) via the `dotnet` command line process within the Azure environment.

* **Cost Management Strategy:** We actively practiced effective resource management to minimize unnecessary costs:
    * Development services and App Services were selected based on the **lowest-cost tier** that met the application's runtime needs.
    * Services are monitored and **paused or scaled down** when not in active use (e.g., outside of testing hours) to avoid incurring charges for idle resources.

## 👥 About Our Team - EventXpert

 Our focus was on applying modern web development principles, including **MVC architecture**, **data persistence**, and **API integration**, to create a functional sports hub.

### Team Member Roles

| Member Name | Role & Core Focus | Contact |
| :--- | :--- | :--- |
| **Arnav Mohite** | **Architecture & Framework** 
| **Raees Parker** | **Data Persistence & CRUD** 
| **Kajal Sharma** | **API Integration & Data Display** 
| **Kushal Reddy** | **Azure Deployment** 

---

## Technical Project Documentation

For complete technical details, implementation strategies, and solutions developed during the MVC migration and cloud deployment, see the sections below.

### Key Technical Aspects Covered:

* **API Endpoints:** 

### External API Endpoints (Data Fetching Only)

The EventXpert platform integrates with the following external services to fetch real-time, dynamic data. These APIs are used strictly for display and are **not** used for persistent data storage.

| External API | Purpose | Data Fetched |
| :--- | :--- | :--- |
| **Open-Meteo** | Real-time local weather conditions. | Current temperature, wind speed, and precipitation chance for Tampa. |
| **TheSportsDB** | Live sports data. | Live scores, match statuses, and event details for display on the scoreboard. |

* **Data Model (ERD):** A breakdown of the logical data model illustrating the core entities (`Event`, `Team`, `Venue`) and their relationships (1:N).

This diagram illustrates the core entities and their relationships within the EventXpert application's database structure. It defines the logical architecture underpinning all CRUD operations and data persistence.

* **Core Entities:** `Event`, `Team`, and `Venue`.
* **Relationships:** Events have a **Many-to-One (N:1)** relationship with both `Team` and `Venue` (meaning one team can have many events, and one venue can host many events).
* **Implementation Note:** While the logical model is normalized (as shown below), the current EF Core implementation uses a flattened structure, leveraging foreign keys to maintain these relationships within the SQLite database.

* **Overview of CRUD Implementation:** A deep dive into how Create, Read, Update, and Delete operations were fully implemented for data persistence using EF Core with SQLite.

### CRUD Implementation Details: Controller Mapping

The core CRUD logic for the `Event` entity is handled within the `EventsController`. This table maps each operation (Create, Read, Update, Delete) to its corresponding MVC Controller method and the specific EF Core function used for data persistence.

| Operation | Controller Method | User Action | Technical Function (EF Core) |
| :--- | :--- | :--- | :--- |
| **Create (C)** | `Create(Event event)` | Submitting the "Add New Event" form. | Uses `_context.Events.Add(event)` to insert a new record into the SQLite database. |
| **Read (R)** | `Index()` and `Details(id)` | Viewing the main events list or a single event's page. | Uses `_context.Events.ToList()` or `_context.Events.Find(id)` to retrieve data and display it in a Razor View. |
| **Update (U)** | `Edit(id, Event event)` | Submitting changes to an existing event form. | Uses `_context.Events.Update(event)` to modify the existing record in the database. |
| **Delete (D)** | `DeleteConfirmed(id)` | Clicking the "Delete" button on the confirmation screen. | Uses `_context.Events.Remove(event)` to permanently remove the record from the database. |


* **Notable Technical Challenges and Solutions:** 

## 💡 Key Technical Challenges & Solutions

This table highlights the significant technical hurdles encountered during the project and the solutions implemented across architecture, persistence, and deployment.

| Area | Challenge Faced | Solution Implemented |
| :--- | :--- | :--- |
| **Architecture** | Fitting static HTML/CSS into the dynamic **Razor View system** without breaking the USF-themed layout. | Adapted the design into the main **`_Layout.cshtml`** file and organized all static files within the **`wwwroot`** folder. |
| **Data Persistence** | Ensuring the application was correctly connected to the local **SQLite database file** and that it persisted across sessions. | Configured the `DefaultConnection` string in `appsettings.json` and correctly **injected the `DbContext`** into the controllers. |
| **Concurrency** | Preventing data corruption or conflicts if multiple users attempted to edit the same event record simultaneously. | Implemented **concurrency handling logic** using EF Core to manage and prevent conflicting database updates. |
| **API Integration** | Matching the messy, non-standard field names from external APIs (like sports scores) to our simple, internal C# models. | Used the **`[JsonPropertyName]` attribute** on C# classes to accurately map the foreign JSON field names to the correct internal properties. |
| **Azure Launch** | Confirming the MVC application correctly launched the `.dll` file using the necessary `dotnet` process command required by Azure. | Verified the `web.config` contained the correct **`arguments`** (`.\EventXpert.dll`) and **`processPath`** (`dotnet`) settings. |
| **Cloud Data Safety** | Ensuring the local **SQLite database file** didn't get lost or wiped clean during the move to the Azure cloud environment. | Verified the database file was created within the guaranteed **persistent storage path** provided by the Azure App Service environment. |