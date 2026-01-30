Welcome to the IMS Explorer Github repository.  This repository provides you information for the new IMS Explorer for VS Code offering.  You can find announcements of the latest updates as well as to provide feedback, submit questions, polls, request for enhancements and files issues. 

# License

- The license for the files managed in this repository, which may consists of files for issues, discussion items and education collaterals is in the file LICENSE.
- The license and notices files for the IMS Explorer for VS Code offering can be found in the product-licenses folder.

# IBM IMS® Explorer for VS Code

**IMS Explorer for VS Code provides modern development practices and simplifies complex IMS development tasks using Visual Studio Code.**

Designed for application developers, database administrators, and system programmers, IMS Explorer for VS Code provides built-in features to access IMS inside Visual Studio Code IDE. By combining multiple activities into one environment, IMS Explorer for VS Code promotes modern development practices and simplifies complex IMS development tasks. IMS Explorer for VS Code 1.0.0 supports the following actions:

- Create and edit projects, driver definitions, and database connections.
- Connect to IMS Catalog and browse IMS databases.
- View PSB, DBD, DDL sources, segments and fields of your database.
- Access IMS data with SQL queries.

See [Capabilities](#capabilities) below for more details.

Visit [IMS Explorer Github repository](https://github.com/IBM/ims-explorer-about) for documentation and additional information. Engage in the [community forum](https://github.com/IBM/ims-explorer-about/discussions) for announcements of latest updates, provide feedback, submit questions, polls or request for ideas.

## Table of contents

- [Support](#support)
- [Prerequisites](#prerequisites)
- [Extension settings](#extension-settings)
- [Configuring IMS Workspaces](#configuring-ims-workspaces)
- [Configuring Java](#configuring-java)
- [Capabilities](#capabilities)

## Support

To report issues or submit feedback about this extension, please open an [issue in our GitHub repository](https://github.com/IBM/ims-explorer-about/issues). GitHub issues may also be used to submit requests for future enhancements

## Prerequisites

Review the [IMS Explorer for VS Code License Agreement](https://github.com/IBM/ims-explorer-about/raw/main/product-licenses/LICENSE.txt) and [Third Party Notices](https://github.com/IBM/ims-explorer-about/raw/main/product-licenses/NOTICES.txt) before downloading.

The following software requirements must be met to run IMS Explorer for VS Code.

- Microsoft VS Code version 1.105.0 or later.
<!-- We recommend using always the latest VS Code version available. If you do not have VS Code installed we recommend using the [Visual Studio Code for Java Installer](https://code.visualstudio.com/docs/languages/java#_install-visual-studio-code-for-java) provided by Microsoft as it automatically downloads and installs a Java SDK together with VS Code. (See, but skip the next bullet for the Java dependency, if you use this option.) -->

- Java SDK or JRE version 21 or later - 64 bit: The language servers included in this extension are implemented in Java, and require a 64-bit Java SDK or Runtime in order to start successfully. Examples of supported Java runtimes include the following:
  - Version 21 of [IBM's Semeru Runtime](https://developer.ibm.com/languages/java/semeru-runtimes/) that can be [downloaded here](https://developer.ibm.com/languages/java/semeru-runtimes/downloads).
  - [Oracle Java 21](https://www.oracle.com/java/technologies/downloads/#java21).
  - [OpenJDK](https://adoptium.net/temurin/releases?version=21&os=any&arch=any).
  - Newer versions of Java should also work, but IMS Explorer for VS Code is developed on and tested for Java 21.

<!-- (Optional) Git: To use the features that involve Git, you must install Git and have it available in your system path so that VS Code can display it. On Macs, Git comes out of the box. On Linux, you can install Git with your distribution's package manager. On Windows, you can get Git from <https://git-scm.com>. -->

## Extension settings

Configurations can be made in VS Code Extension settings in order to specify the following:

- Java dependency Jar files for the IMS SQL service
- Specific Java installations used for IMS connections
- Maximum heap size for IMS connections
- Storage location for extension data
- Large list limit thresholds

## Configuring IMS workspaces

Before getting started with an IMS project, ensure that the desired workspace for your IMS projects has been specified using the IMS Workspace status bar option. This option determines the location for the `ims.connections.json` file, and can provide a common location for IMS project files to be shared in source control.

## Configuring Java

The IMS Explorer for VS Code extension utilizes VS Code user settings to configure Java. These settings allow you to select the specific installation of Java to pick, in case you have several installations, as well as set parameters such as how much memory you want the language servers to use.

### Selecting the Java installation to use

IMS Explorer for VS Code extension will scanned the following locations, in the order specified, for the first Java installation that is at least Version 21 and 64-Bit to be used. If the target Java fails to meet requirements, the remaining target locations will be scanned:

1. The `ims.explorer.connection.property.javaHome` VS Code user setting.
1. The `java.jdt.ls.java.home` VS Code user setting.
1. The `JAVA_HOME` environment variable.
1. The PATH defined for the environment in which IMS Explorer for VS Code runs (i.e. you default Windows or MacOS path)
1. A typical platform-specific location. For example, on MacOS it will execute the `/usr/libexec/java_home -V` and on Windows the `where java.exe` commands to locate a valid Java installation.

Note that the methods at the end of the list require a significant amount of time as they are executing programs on your system. To improve startup times you should consider user settings as they provide the best startup performance.

If Java cannot be located check the VS Code Output view's IMS Explorer for VS Code tab for any error and try to fix the problem by either setting the `JAVA_HOME` environment variable or create an entry in your VS Code user settings.

To define a user setting use the Preferences > Settings menu and either locate the setting in the graphical editor under IMS Explorer for VS Code or edit the setting json file directly by adding an entry as follows using an absolute path name to the Java installation directory.

On Mac:

```json
"ims.explorer.connection.property.javaHome": "/Library/Java/JavaVirtualMachines/jdk21/Contents/Home"
```

On Windows:

```json
"ims.explorer.connection.property.javaHome": "C:\\Program Files\\Java\\jdk21"
```

### Configuring Java memory allocation

By default, a maximum of 2 gigabytes of memory will be allocated to be used for each IMS database connection. Ensure that your system has enough memory to support multiple database connections and SQL calls by using the following VS Code Settings provided to specify the maximum value of allocated memory.

```json
"ims.explorer.connection.property.maxHeapSize": "2g"
```

### Configuring log level

The default Java logging level is info. Use the following VS Code Setting to change the value.

```json
"ims.explorer.logging.level": "INFO"
```

The logs appear in the Output panel. Additional logs would be displayed in the `IBM IMS Explorer for VS Code` output channel and the `IBM IMS Explorer LSP server` output channel.

### Configuring IMS Workspace

Use the following VS Code Setting to change the defult directory of the IMS Workspace location to store associated extension files.

On macOS:
Default directory is the user home directory.

```json
"ims.explorer.property.ImsWorkspace": "/Users/<username>/.vscode/ims-workspace"
```

On Windows:
Default directory is current the user profile directory.

```json
"ims.explorer.property.ImsWorkspace": "C:\\Users\\%USERNAME%\\.vscode\\ims-workspace"
```

## Capabilities

The following sections offer a preview of the features available with the IMS Explorer for VS Code.

<!-- For a complete view of all available features and how to use them, see the online documentation. -->

### IMS connection profiles

Create connections to IMS databases using the IMS connections view. IMS connections can be organized into folders and expanded or collapsed.

![ ](https://github.com/IBM/ims-explorer-about/raw/HEAD/readme/connections.gif)

### IMS connections tree and table views

You can add multiple IMS database connections in a tree view. Browse DBDs, PSBs, and PCBs for IMS databases using the IMS Connections tree view. You can use this view to:

- Add IMS catalog and database connections
- Expand and collapse database connection contents to view DBDs, PSBs, and PCBs
- Select an individual DBD, PSB, or PCB and right-click to view DDL, segments, and source code

In addition to segments and fields, IMS database DBDs, PSBs, and PCBs can also be viewed in a table. This allows simple click navigation between related PSBs and PCBs to find associated segments and fields.

![ ](https://github.com/IBM/ims-explorer-about/raw/HEAD/readme/databaseview.gif)

You can verify connections to IMS databases or select another connection using the IMS Connection option in the status bar.

### IMS Projects

Create IMS projects to edit and organize SQL queries to execute on IMS databases.

![ ](https://github.com/IBM/ims-explorer-about/raw/HEAD/readme/sqlproject.gif)

### Edit and execute SQL

Edit and execute SQL from an IMS project file against an IMS database using a specified database connection. A results window is provided with a table containing the resulting query information. You can sort and filter results within the table.

Each result set from SQL queries are stored in a query history view. You can download SQL result sets as a CSV file.

![ ](https://github.com/IBM/ims-explorer-about/raw/HEAD/readme/sqlresulthistory.gif)

