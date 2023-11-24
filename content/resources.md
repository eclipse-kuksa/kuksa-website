---
title: "Finding things"
date: 2021-05-14T09:46:31+02:00
draft: false
---

# Get in touch

### Bi-weekly Meeting
There is the  **bi-weekly** [KUKSA dev/user call on Zoom](https://eclipse.zoom.us/j/87644929505?pwd=cTRpYklVaS9xYjlhMXRtbS9IN0FCQT09) every Thursday on odd calendar weeks from 1-2pm (CET/CEST). 

{{< tui-calendar >}}

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
| Eclipse KUKSA.val        |https://github.com/eclipse/kuksa.val       | KUKSA Vehicle Abstraction Layer, this is a an implementation of a VSS server provding access to in-vehicle signals using VISS or GRPC interfaces  |
| Eclipse KUKSA.val.feeders        |https://github.com/eclipse/kuksa.val.feeders       | Multiple data and actuation providers, gathering vehicle data and transforming it to VSS suitable for KUKSA.val  |
| Eclipse KUKSA.val.services        | https://github.com/eclipse/kuksa.val.services       | Set of example vehicle services  |
| Eclipse KUKSA Android SDK        | https://github.com/eclipse-kuksa/kuksa-android-sdk  | SDK to develop KUKSA clients on Android using Kotlin or Java  |
| Eclipse KUKSA Android Companion        | https://github.com/eclipse-kuksa/kuksa-android-companion  | Example App using the Android SDK to check and control temperature, tire pressure, doors etc. from your phone  |
| Eclipse KUKSA Python SDK        | https://github.com/eclipse-kuksa/kuksa-python-sdk  | SDK to develop KUKSA applications and providers using Python. Also includes a versatile CLI client for testing/debugging  |
| Eclipse KUKSA.hardware   | https://github.com/eclipse-kuksa/kuksa-hardware |Hardware schematics and manufacturing files for the KUKSA SDV prototpying platform. This is a PI-compatible hardware providing access to CAN, OBD and cellular connectivity  |
| KUKSA-website            | https://github.com/eclipse-kuksa/kuksa-website  | The sources for the website you are reading now |
{{< /table >}}

## Dormant projects
This repositories contain components that have been developed in the past, but are currently not actively maintained or whose functionality has been integrated into active components.


 
{{<table "table table-striped table-bordered">}}

| Component                | Source                                     | Description |
|--------------------------|--------------------------------------------|----------|
| Eclipse KUKSA.ide        |  https://github.com/eclipse/kuksa.ide      |  Browser-based IDE used by developers to create applications for the Eclipse Kuksa in-vehicle. If you are searching for an integrated way to build applications based on vehicle data provided by KUKSA.val, you may want to check the [Velocitas framework](https://eclipse-velocitas.github.io/velocitas-docs/). As first step you can have a look at the playground from [digital auto](https://digitalauto.netlify.app/). | 
| KUKSA.Apps               | https://github.com/eclipse/kuksa.apps      | Contains applications to showcase use-cases of Eclipse KUKSA. Demos regarding vehicle signal access have been moved over to [KUKSA.val](https://github.com/eclipse/kuksa.val) |
| KUKSA.In-Vehicle         | https://github.com/eclipse/kuksa.invehicle | The in-vehicle platform of Eclipse Kuksa. The KUKSA hardware has been moved to [KUKSA.hardware](https://github.com/eclipse/kuksa.hardware), the VISS dataserver for accessing in-vehicle data is further developed in [KUKSA.val](https://github.com/eclipse/kuksa.val ). For a modern integrated SDV distribution check [Eclipse LEDA](https://eclipse-leda.github.io/leda/) | 
| Eclipse KUKSA.cloud      | https://github.com/eclipse/kuksa.cloud    | The cloud-backend of Eclipse KUKSA, including the App Store. Provides helmcharts for easy deployment of the KUKSA.cloud. For deploying software in a vehicle check [Eclipse Kanto](https://github.com/eclipse-kanto) or other pojects in [Eclipse SDV](https://sdv.eclipse.org/). For updated versions of the components utilized in KUKSA.cloud check [Eclipse IoT packages](https://github.com/eclipse/packages)  |
{{< /table >}}


