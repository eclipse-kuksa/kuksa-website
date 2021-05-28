---
title: "Finding things"
date: 2021-05-14T09:46:31+02:00
draft: false
---

# Get in touch

### Zoom Meeting
There is the  **bi-weekly** [Zoom meeting](https://eclipse.zoom.us/j/537310990) every Thursday on even calendar weeks from 1-2pm (CET/CEST).

### Chat
You can find us on Chat in [Gitter Channel](https://gitter.im/kuksa-val/community), or if you are a Matrix user using the [Gitter-Matrix bridge](https://matrix.to/#/#kuksa-val_community:gitter.im).

### Mailinglist 
You can reach us on the [kuksa-dev mailing list](https://accounts.eclipse.org/mailing-list/kuksa-dev)


# Get the code

The code for the various subprojects is provided in the following Github repositories. Please note that
issues are tracked and discussed in the repository of the respective sub-project.

## Active projects 
{{<table "table table-striped table-bordered">}}
| Component                | Source                                    | Description |
|--------------------------|-------------------------------------------|----------|
| Eclipse KUKSA.val        |https://github.com/eclipse/kuksa.val       | KUKSA Vehicle Abstraction Layer, this is a Genivi/W3C compliant implementation of a VISS server provding access to in-vehicle signals  |
| Eclipse KUKSA.hardware   | https://github.com/eclipse/kuksa.hardware |Hardware schematics and manufacturinng files for the KUKSA hardware dongle. This is a Pi-compatible dongle that runs the KUKSA software and can be plugged into a cars diagnostic port  |
| Eclipse KUKSA.cloud      | https://github.com/eclipse/kuksa.cloud    | The cloud-backend of Eclipse KUKSA, including the App Store. Provides helmcharts for easy deployment of the KUKSA.cloud |
| KUKSA.website            | https://github.com/eclipse/kuksa.website  | The sources for the website you are reading now |


## Dormant projects
This repositories contain components that have been developed in the past, but are currently not actively maintained or whose functionality has been integrated into active components.


 

| Component                | Source                                     | Description |
|--------------------------|--------------------------------------------|----------|
| Eclipse KUKSA.ide        |  https://github.com/eclipse/kuksa.ide      |  Browser-based IDE used by developers to create applications for the Eclipse Kuksa in-vehicle. If you are searching for an integrated way to build applications based on vehicle data provided by KUKSA.val, you may want to check the [IoTEA project](https://github.com/GENIVI/iot-event-analytics) | 
| KUKSA.Apps               | https://github.com/eclipse/kuksa.apps      | Contains applications to showcase use-cases of Eclipse KUKSA. Demos regarding vehicle signal access have been moved over to [KUKSA.val](https://github.com/eclipse/kuksa.val) |
| KUKSA.In-Vehicle         | https://github.com/eclipse/kuksa.invehicle | The in-vehicle platform of Eclipse Kuksa. The KUKSA hardware has been moved to [KUKSA.hardware](https://github.com/eclipse/kuksa.hardware), the VISS dataserver for accessing in-vehicle data is further developed in [KUKSA.val](https://github.com/eclipse/kuksa.val ) | 
| KUKSA.integration        |  https://github.com/eclipse/kuksa.integration |Integration tests for Eclipse Kuksa |



# Getting Started
To learn how to use the KUKSA.val VISS server to access standardized vehicle signals check the [KUKSA.val Readme](https://github.com/eclipse/kuksa.val/blob/master/README.md).

For an end-to-end usecase incuding in-vehicle as well as KUKSA.cloud components, check how the [DIAS project](https://dias-project.com/) used [KUKSA for preventing exhaust system tampering](https://dias-kuksa-doc.readthedocs.io/en/latest/)

<!-- 
A brief documentation link collection can be found [here](https://github.com/eclipse/kuksa.integration#getting-started-with-eclipse-kuksa).

The *Eclipse PMI Community* website can be found [here](https://projects.eclipse.org/projects/iot.kuksa). You will find  information about Eclipse Kuksa's idea, who is involved, developer resources, releases, and contact information there.


# Documentation

* Eclipse Che Kuksa IDE: https://gitlab-pages.idial.institute/pedro.cuadrachamorro/kuksa-ide/
* Rover Docs: https://app4mc-rover.github.io/rover-docs/
* Rover API: https://app4mc-rover.github.io/rover-app/
* Rover Telemetry UI https://github.com/app4mc-rover/rover-telemetry-ui
* Eclipse Kuksa Wiki: https://wiki.eclipse.org/Kuksa
* Entry in Eclipse Foundation Project List: https://projects.eclipse.org/projects/iot.kuksa
 -->

<!-- 
# APPSTACLE Deliverables and more

Eclipse Kuksa was created as part of the APPSTACLE project. More information
regarding the project and the deliverables is available at
https://itea3.org/project/appstacle.html .
--> 

# Talks
* <a href="https://www.youtube.com/watch?v=tD8pt7WMbuQ&t=3s">Automotive meets IoT: Innovating your future vehicle </a> Sebastian Schildt, Bosch
* <a href="https://youtu.be/FuIaJ2tlnRE">Bridging Eclipse SUMO with Eclipse Kuksa</a> Philipp Heisig, Fachhochschule Dortmund
