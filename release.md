---
layout: page
title: Release
---

The easiest way to setup Polypheny-DB is to use our [latest release](https://github.com/polypheny/Polypheny-DB/releases/latest). On this page, we describe how to deploy Polypheny-DB on different operating systems using these releases. It is of course also possible to [manually build](#) Polypheny-DB or to use [Polypheny Control](/documentation/Polypheny-Control/). However, this is not recommended for productive deployments.


## Prerequisites
Everything is completely self-contained and comes with its own JVM. The only dependency is Docker. However, Docker is only required for some features. We nevertheless recommend setting up Docker since it makes the deployment of stores more seamless. See [this](/documentation/Stores/Docker/) on how to setup Docker to use the built-in Docker-based data store deployment.


## Binaries
We provide binaries for Windows, macOS and Linux. Furthermore, we provide a JAR which allows to deploy Polypheny-DB on every system running Java.

### Windows
Please download the `.msi` file from the GitHub [release page](https://github.com/polypheny/Polypheny-DB/releases/latest) and follow the installer. After the installation has completed, Polypheny-DB can be started using the Desktop icon or the entry in the start menu. After Polypheny-DB has been started, it adds itself to the system tray. 

### macOS
Please download the `.dmg` file from the GitHub [release page](https://github.com/polypheny/Polypheny-DB/releases/latest). As usual, Polypheny-DB is installed by dragging the Polypheny icon on the application folder. This adds Polypheny to the applications overview.  After Polypheny-DB has been started, it adds itself to the system tray. 

### Linux
We provide binaries for `.deb` and `.rpm` systems. These binaries come with systemd scripts for controlling Polypheny-DB. Please check the manual of your Linux distribution on how to install the `.deb` or `.rpm` file.

### Other
Please use the `.jar` file provided on the [release page](https://github.com/polypheny/Polypheny-DB/releases/latest). Polypheny-DB requires a Java runtime version 11 or higher.



## Data Folder
Polypheny-DB stores files in the local file system. By default, this is done in a special folder called `.polypheny` in the home directory of the executing user.
This location can be customized by setting a system environment variable called `POLYPHENY_HOME` pointing to the desired location before Polypheny-DB is started.
