---
title: "Finding things"
date: 2021-05-14T09:46:31+02:00
draft: false
---

# Get in touch

### Bi-weekly Meeting
There is the  **bi-weekly** [KUKSA dev/user call on Zoom](https://eclipse.zoom.us/j/87644929505?pwd=cTRpYklVaS9xYjlhMXRtbS9IN0FCQT09) every Thursday on odd calendar weeks from 1-2pm (CET/CEST). 


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
| Eclipse KUKSA.val        |https://github.com/eclipse/kuksa.val       | KUKSA Vehicle Abstraction Layer, this is a COVESA/W3C compliant implementation of a VSS server provding access to in-vehicle signals using VISS or GRPC interfaces  |
| Eclipse KUKSA.val.feeders        |https://github.com/eclipse/kuksa.val.feeders       | Multiple feeders to gathering vehicle data and transforming it to VSS suitable for KUKSA.val  |
| Eclipse KUKSA.val.services        |https://github.com/eclipse/kuksa.val.services       | Set of example vehicle services  |
| Eclipse KUKSA.hardware   | https://github.com/eclipse/kuksa.hardware |Hardware schematics and manufacturinng files for the KUKSA SDV prototpying platform. This is a PI-compatible hardware providing access to CAN, OBD and cellular connectivity  |
| Eclipse KUKSA.cloud      | https://github.com/eclipse/kuksa.cloud    | The cloud-backend of Eclipse KUKSA, including the App Store. Provides helmcharts for easy deployment of the KUKSA.cloud |
| KUKSA.website            | https://github.com/eclipse/kuksa.website  | The sources for the website you are reading now |


## Dormant projects
This repositories contain components that have been developed in the past, but are currently not actively maintained or whose functionality has been integrated into active components.


 

| Component                | Source                                     | Description |
|--------------------------|--------------------------------------------|----------|
| Eclipse KUKSA.ide        |  https://github.com/eclipse/kuksa.ide      |  Browser-based IDE used by developers to create applications for the Eclipse Kuksa in-vehicle. If you are searching for an integrated way to build applications based on vehicle data provided by KUKSA.val, you may want to check the [IoTEA project](https://github.com/GENIVI/iot-event-analytics) | 
| KUKSA.Apps               | https://github.com/eclipse/kuksa.apps      | Contains applications to showcase use-cases of Eclipse KUKSA. Demos regarding vehicle signal access have been moved over to [KUKSA.val](https://github.com/eclipse/kuksa.val) |
| KUKSA.In-Vehicle         | https://github.com/eclipse/kuksa.invehicle | The in-vehicle platform of Eclipse Kuksa. The KUKSA hardware has been moved to [KUKSA.hardware](https://github.com/eclipse/kuksa.hardware), the VISS dataserver for accessing in-vehicle data is further developed in [KUKSA.val](https://github.com/eclipse/kuksa.val ). For a modern integrated SDV distribution check [Eclipse LEDA](https://eclipse-leda.github.io/leda/) | 




# Talks & Videos

* 04/2022 [KUKSA CANOPi Hardware for SDV development](https://www.youtube.com/watch?v=y6zAF-tSS2Q)
* 06/2021 [Eclipse KUKSA.val for SCR Anti-Tampering Monitoring in Heavy Vehicles](https://www.youtube.com/watch?v=20U8bWwWfgw), ([Slides](https://events.eclipse.org/2021/saam-mobility/presentations/D2-02-Presentation.pdf)) at Eclipse SAAM 2021 by Sebastian Schildt, Bosch
* 08/2020 [Eclipse Kuksa.val DBC Feeder Demo](https://www.youtube.com/watch?v=nTzmDDy3iwQ)
* 05/2019 [Bridging Eclipse SUMO with Eclipse Kuksa](https://youtu.be/FuIaJ2tlnRE) by Philipp Heisig, Fachhochschule Dortmund
* 03/2019 [Appstacle Use Case: Remote Driver Authentication](https://youtu.be/eZHSCXSc2wc). KUKSA PoC by OTOKAR and Netaş
* 11/2018 [Automotive meets IoT: Innovating your future vehicle](https://www.youtube.com/watch?v=tD8pt7WMbuQ) by Sebastian Schildt, Bosch
* 05/2018 [APPSTACLE interview](https://www.youtube.com/watch?v=qCyBjZnGK2E) with Robert Höttger Fachhochschule Dortmund - University of Applied Science and Art at Eclipsecon France