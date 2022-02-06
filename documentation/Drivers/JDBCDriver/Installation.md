---
layout: plain
title: Installing the JDBC Driver
---

The JDBC driver (poylpheny-jdbc-driver) is provided as a JAR file, available as an artifact in Maven for download or integrating directly into your Java-based projects.

Before downloading or integrating the driver, you may want to first verify the version of the driver you are currently using. To verify your driver version, connect to Polypheny-DB through a client application that uses the driver and check the driver version.  https://github.com/polypheny/Polypheny-JDBC-Driver/releases

## Downloading the Driver

To download the driver:
1. Select your desired release version:
  https://github.com/polypheny/Polypheny-JDBC-Driver/releases

2. Download the polypheny-jdbc-driver-#.#.#.jar file.

## Integrating the Driver into a Maven Project

To integrate the driver into a Maven project, add the driver as a dependency to your pom.xml file. For example:
```xml
<dependency>
  <groupId>org.polypheny</groupId>
  <artifactId>polypheny-jdbc-driver</artifactId>
  <version>1.5.2</version>
</dependency>
```

Where the <version> tag specifies the version of the driver you wish to integrate. Note that version 1.5.2 is used in this example for illustration purposes only. The latest available version of the driver may be higher.

The developer notes are hosted along with the source code on [GitHub](https://github.com/polypheny/Polypheny-JDBC-Driver).