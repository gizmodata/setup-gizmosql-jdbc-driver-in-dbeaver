# Setting Up DBeaver with the GizmoSQL JDBC Driver (macOS)

[<img src="https://img.shields.io/badge/dockerhub-image-green.svg?logo=Docker">](https://hub.docker.com/r/gizmodata/gizmosql)
[<img src="https://img.shields.io/badge/GitHub-gizmodata%2Fgizmosql-blue.svg?logo=Github">](https://github.com/gizmodata/gizmosql)
[![JDBC Driver](https://img.shields.io/badge/GizmoSQL%20JDBC%20Driver-download%20artifact-red?logo=Apache%20Maven)](https://downloads.gizmodata.com/gizmosql-jdbc-driver/latest/gizmosql-jdbc-driver.jar)

## Prerequisites

1. A running GizmoSQL server — you can use [this repo](https://github.com/gizmodata/gizmosql) to start one.
2. [DBeaver Community Edition](https://dbeaver.io) installed.
3. The [GizmoSQL JDBC driver](https://downloads.gizmodata.com/gizmosql-jdbc-driver/latest/gizmosql-jdbc-driver.jar) jar file downloaded.

## Configure the JDBC Driver

1. Launch DBeaver.

2. Open **Database > Driver Manager** from the menu bar:

   <img src="images/dbeaver_database_driver_manager_menu_option.png?raw=true" alt="Driver Manager menu option" width="600">

3. Click the **New** button:

   <img src="images/driver_manager_new_button.png?raw=true" alt="Driver Manager New button" width="600">

4. Add the JDBC jar file:
   1. Click the **Libraries** tab.
   2. Click **Add File**, select the `gizmosql-jdbc-driver-x.x.x.jar` file downloaded earlier, and click **Open**.

      <img src="images/select_driver_jar_file.png?raw=true" alt="Select jar file" width="600">

   3. Click **Find Class** — the value `org.apache.arrow.driver.jdbc.ArrowFlightJdbcDriver` should populate automatically:

      <img src="images/class_path.png?raw=true" alt="Driver class path" width="600">

5. Configure the driver settings:
   1. Click the **Settings** tab.
   2. Fill in the following fields:

      | Field | Value |
      |---|---|
      | **Driver Name** | `GizmoSQL` |
      | **Class Name** | `org.apache.arrow.driver.jdbc.ArrowFlightJdbcDriver` |
      | **URL Template** | `jdbc:gizmosql://{host}:{port}?useEncryption=true&disableCertificateVerification=true` |
      | **Driver Type** | `Generic` |
      | **Default Port** | `31337` (optional) |

      Your window should look like this:

      <img src="images/driver_manager_completed_window.png?raw=true" alt="Driver Manager completed" width="600">

   3. Click **OK** to save the driver, then **Close** to exit the Driver Manager.

## Create a Database Connection

1. Open **Database > New Database Connection** from the menu bar:

   <img src="images/new_database_connection_menu_option.png?raw=true" alt="New Database Connection" width="600">

2. Type `Gizmo` in the search bar and select the **GizmoSQL** driver:

   <img src="images/database_selection_window.png?raw=true" alt="Connect to a database window" width="600">

3. Click **Next >**.

4. Fill in your connection details — Host (e.g. `localhost`), Port (`31337`), Username (`gizmosql_username`), and Password:

   <img src="images/database_settings_window.png?raw=true" alt="Database settings window" width="600">

5. Click **Test Connection** to verify connectivity:

   <img src="images/test_connection_button_results.png?raw=true" alt="Test Connection results" width="600">

6. Click **OK** to close the test results.

7. Click **Connection details (name, type, ...)** on the right and give the connection a name (e.g. `GizmoSQL - tutorial`):

   <img src="images/naming_database_connection.png?raw=true" alt="Name the Database Connection" width="600">

8. Click **Finish** to save the connection.

## Run a Query

1. Right-click the new connection in the sidebar and choose **SQL Editor > Open SQL Console**:

   <img src="images/open_sql_console.png?raw=true" alt="Open SQL Console" width="600">

2. Enter a query, for example: `SELECT * FROM region;`

3. Click the execute button (or press **Ctrl+Enter**):

   <img src="images/triangle_execute_button.png?raw=true" alt="Execute SQL" width="600">

4. You should see the query results:

   <img src="images/query_results.png?raw=true" alt="Query Results" width="600">

## You're all set!
