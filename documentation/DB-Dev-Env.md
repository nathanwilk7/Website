---
layout: plain
title: DB Development Environment
---

This guideline describes how to set up Polypheny-DB in an IDE.

## Prerequisites
You need a Java JDK in version 11 or higher. Furthermore, we recommend setting up Docker since it makes the deployment of stores more seamless. Please consult [this](/documentation/Stores/Docker/) on how to set up Docker for Polypheny-DB and configure the Docker-based data store deployment.


## Using IntelliJ
1. Fork and checkout Polypheny-DB
2. Import the project by opening the folder you have just checkout in IntelliJ.
3. Set up Lombok support by following [this tutorial](https://www.baeldung.com/lombok-ide).
4. Wait until the project has been fully imported in IntelliJ
5. Start Polypheny-DB using the automatically added run-configurations.


## Other IDEs
We recommend using IntelliJ; however, you can also use another IDE.

1. Fork and checkout Polypheny-DB
2. Import the project in your favorite IDE as Gradle project.
3. Set up Lombok support in your IDE. See [this tutorial](https://www.baeldung.com/lombok-ide) for further information.
4. Import the [coding style](https://github.com/polypheny/Admin/tree/master/CodeStyle).
5. Start Polypheny-DB using its main-Class (`dbms/src/main/java/org/polypheny/db/PolyphenyDb.java`). There are no arguments required. 

## Reset Polypheny 
If you would like to reset the catalog (and thus Polypheny) you can use the argument `-resetCatalog` on startup.


## Polypheny-UI
There is no need to manually set up the UI if you do not plan to work at the UI. Polypheny-DB pulls the latest version of the UI in the build process. If you would like to work on the Polypheny-UI, please follow [this tutorial](/documentation/UI-Dev-Env/).