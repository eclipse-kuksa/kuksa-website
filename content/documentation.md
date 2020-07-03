+++
title = "Eclipse Kuksa documentation"
date = "2020-04-25"
tags = ["Eclipse Kuksa Documentation"]
toc = true
+++

Eclipse Kuksa builds a platform to connect vehicles to the cloud and enable the development of specific applications of connected driving. This documentation covers the core pillars as follows: 1. the Eclipse Kuksa IDE, 2. the Eclipse Kukse In-Vehicle Platform, and 3. the Eclipse Kuksa Cloud Platform.

This documentation intends to give a high-level overview of the Eclipse Kuksa components. For more detailed information and documentation on the different aspects, we recommend consulting the respective repositories and their Readme files. The development around Eclipse Kuksa divides into seven repositories. An overview of these repositories and what they focus on is available on the Kuksa Website under [Resources](https://www.eclipse.org/kuksa/resources/).

# 1. Eclipse Kuksa IDE

## 1.1 Introduction

Extensions are available for two different kind of existing IDEs.
* The latest extension is available for MS Visual Studio Code in form of a downloadable extension from the [marketplace](https://marketplace.visualstudio.com/items?itemName=Eclipse-Kuksa-Team.kuksa-ide&utm_source=VSCode.pro&utm_campaign=AhmadAwais).
* The second extension is a custom Eclipse Che Assembly. A quick start can be found [here](https://kuksa-che-ide.readthedocs.io/en/latest/quick/index.html).

Eclipse Kuksa offers various APIs for implementing vehicle applications based on AGL (Eclipse Kuksa IDE based on Eclipse Che) or docker (Eclipse Kuksa IDE based on VSCode) as well as provisioning built applications at the Eclipse Kuksa App Store. This enables accessing existing communication interfaces for secure data transmission, storage, management, and authentication without having to take separate measurements for processing or interpreting the data.

Eclipse Kuksa also supports the simplified deployment of new applications for both the cloud and vehicle components. Configuration, building and deployment can be done at the push of a button without further configuration or processing. Depending on the application, different development tools (e.g. Logging, Debugging, Tracing,...) can be included. Of course, syntax highlighting, code completion, and other necessary IDE functions are supported. For instance, the in-vehicle Eclipse Kuksa Che stack for AGL development activities features including Yocto based SDKs in order to support target specific programming shown in the screenshot below. After compiling and building software, the deployment on a specific target can be triggered by only specifying a target IP within a dedicated deployment process. [Click here](https://www.eclipse.org/community/eclipse_newsletter/2018/july/kuksa.php) to read more. The Eclipse Kuksa IDE provides an easy and straight forward mechanism to create new projects based on AGL as outlined [here](https://gitlab-pages.idial.institute/pedro.cuadrachamorro/kuksa-ide/samples/index.html).

<p style="text-align:center;">
 <a href="/kuksa/docimgs/Kuksa_IDE.png">
   <img src="/kuksa/docimgs/Kuksa_IDE.png" width="60%" alt="Kuksa IDE"/>
 </a><br/>
</p>


Ecslipe Kuksa Demo Apps for the In-Vehicle platform can be found at the [according repository](https://github.com/eclipse/kuksa.apps/tree/master/invehicle-apps).
Eclipse Kuksa Demo Cloud Apps can be at [the same repository at a different location](https://github.com/eclipse/kuksa.apps/tree/master/cloud-apps).

## 1.2 Eclipse Kuksa IDE based on VSCode

The VSCode Kuksa extension is a package of four different extensions bundled into one. These are as follows:
1. Kuksa: Initialize Workspace
2. Kuksa: Configure Kuksa Environment(YAML)
3. Kuksa: Generate Docker Image
4. Kuksa: Publish to AppStore

The user can trigger extensions from the Command Palette and also from the _Editor Header_. The Eclispe Kuksa extension follows the VSCode Extension file structure with standard folders like `.vscode` and `src`. It also includes the essential configuration files like `launch.json`, `tasks.json` and `tsconfig.json`.
Apart from the standard folders, there is also a Kuksa specific folder, which contains  python and shell scripts.

An important configuration file of a VSCode extension is the _Extension Manifest_. This file should be located at the root of the extension directory structure. Essentially, it is a `package.json` file which contains a mix of `Node.js` and VSCode specific fields. The fields _activationEvents_ and _contributes_ are especially important since every extension uses a combination of these two and the VSCode API for extending VSCode’s functionality. The _Extension Manifest_ also determines how the extension looks in the VS Code Marketplace with the icon, author, licence, and repository.

### 1.2.1 Initializing the Workspace

The `Kuksa: Initialize Workspace` extension was conceived as a way to provide new developers with the Kuksa project structure. The command generates the directories and  required build scripts. It also creates an empty `yaml` configuration file to be used in the next steps. The entire tree structure is as follows:
* docker
  * build.sh
* include
* kuksa.yaml

The user has to provide the IDE with the desired name of the project and the project structure will be generated with the required files and directories.
At the first step, the OS, on which VSCode is running, will be checked. Currently, only Unix-based Operating Systems like Linux or MacOS are supported. Next, the user is asked to provide a valid name for the project. Invalid or duplicate project names will lead to an error and eventual termination of the process. Once this is successful, the corresponding bash script is triggered and the project folder is opened automatically in VSCode.

### 1.2.2 Generating a Docker Image

The command `Kuksa: Generate Docker Image` is intended to automate the process of creating a Docker image from a particular Dockerfile and tag it appropriately so that it can be used as an artifact for Eclispe Hawkbit and consequently the Eclipse Kuksa AppStore.
The command is also responsible for copying the `QEMU` binary to the Kuksa project directory so that it can be compiled with the source code. The underlying script of this command is again a Bash script, which is created during initialization of the project.
It is important to note that the files and folders mentioned as part of the Dockerfile have to be present in the proper system paths.

### 1.2.3 Configuring the Kuksa Environment (YAML)

The command `Kuksa: Configure Kuksa Environment` helps the developer to generate the configuration file needed for publishing an application. The command triggers a HTML form which holds some required fields to be filled.
Some of the required fields are as follows:

* Application Name
* App Version and Description
* Corresponding Docker Image
* Eclipse Hawkbit, Appstore and KeyCloak URL
* Corresponding Credentials

The form features a _tabbed_ look for the _General_, _AppStore_ and _Keycloak_ fields.
The configuration file is generated based on the YAML format. A Python script converts the field objects into the YAML format.

Finally, publishing an application to the Eclipse Kuksa Appstore can be performed. The according command is responsible for packaging and deploying new or updated Kuksa applications to Eclipse Hawkbit and registering the App at the Kuksa AppStore. Keeping in mind the usability, this complex process is scaled down to only selecting a single configuration file (the same one explained above).
A Python script runs in the backend of this command. This script gets the authentication token from KeyCloak, creates a new application category if required, creates a new application or updates on an existing application and uploads corresponding artifacts to Eclipse Hawkbit.
Apart from being integrated as part of the IDE, it also covers KeyCloak authentication which is now applied over all Kuksa WebServices. The configuration file generated by the previous commands holds all the crucial information like the credentials and URLs for the script to work. REST APIs use these details to post and get responses from the URLs.


## 1.3 Eclipse Kuksa IDE based on Eclipse Che

The Eclipse Kuksa extension to Eclipse Che is based on GWT and hence Eclipse Che 6.X (not Eclipse Che 7.X and later).

### 1.3.1 System requirements

The neccessary prerequisite to build and deploy Eclipse Che Kuksa are:

-  A running docker instance on a Linux host system (tested with Ubuntu 18.04).
-  Maven

Additionally, steps for building and running a Eclipse Che Kuksa instance in version 6.X are available [here](https://kuksa-che-ide.readthedocs.io/en/latest/).

### 1.3.2 How to setup the IDE

To set up Eclipse Che Kuksa, the following steps are necessary. If one wants to build and deploy AGL applications & services within Che:

- Create a new workspace with Automotive Grade Linux (AGL) as selected stack
- Go to "Profile" → "Preferences" → "Remote Targets" and add a new Remote Target with the device IP and the according User, e.g. "root". Then select the Target.
- Go to Profile → Preferences → Yocto Settings and add a new SDK with a Name, e.g. "agl-rover", a Version, e.g. "1.0.0" and a link to an appropriate AGL SDK, e.g. the AGL [Rover](https://github.com/app4mc-rover) SDK from "https://owncloud.idial.institute/s/YiS5wceBmSj4gyr", as Download Link. Then select the added Yocto SDK. To avoid connection trouble, open the Terminal and ssh into the appropriate Device: `ssh < User >@< IP >`.

### 1.3.3 Model-driven Development of AGL Applications and Services

The Eclipse Che Kuksa instance simplifies the development of AGL applications and services. AGL features the usage of automotive applications based on HTML5, JavaScript, and C/C++, which run on top of AGL. While applications realize a distinct use case, services offers functionality to all applications. For more information please refer to the [AGL documentation](https://docs.automotivelinux.org).

The following sections demonstrate the development of AGL applications/services in a model-driven way based on the tool RAML2AGL (cf. Section [Raml2AGL](https://github.com/eclipse/kuksa.ide/tree/master/che-6#raml2agl) ) as well as the building and deployment of AGL applications/services to a remote device running AGL (cf. Section [Building & Deploying](https://github.com/eclipse/kuksa.ide/tree/master/che-6)).


# 2. Kuksa In-Vehicle platform

[Eclipse Kuksa](https://www.eclipse.org/kuksa/) includes an open and secure cloud platform that interconnects a wide range of vehicles to the cloud via open in-car and internet connections and is supported by an integrated open source software development ecosystem. The [in-vehicle repo](https://github.com/eclipse/kuksa.invehicle) contains in-vehicle platform code as well as required layers and bindings to build a Kuksa adapted AGL (Automotive Grade Linux) distribution. If not using AGL, any other platform can be chosen that supports docker. For the former, Eclipse Kuksa provides a wrapper project around AGL. From its side, AGL uses Yocto/Bitbake building system to build an automotive domain specific Linux distribution. Therefore, this projects provides a building system that adds Kuksa's specific Bitbake layers on top of the original AGL. The scripts in this project help ease the process of building an AGL image by simple using a few commands. This project includes the yocto recipes found in meta-kuksa project.

## 2.1 Build AGL Image/SDK RPI3

Please have a look at the repositories [readme file](https://github.com/eclipse/kuksa.invehicle/tree/0.2.0/agl-kuksa).

## 2.2 RoverApp

[This tutorial](https://app4mc-rover.github.io/rover-docs/content/installation.html#) contains how to set up a Rover-specific Raspbian image from scratch and the basic workflow to run the Roverapp applications.


# 3. Eclipse Kuksa Cloud Platform

The Eclipse Kuksa project consists of a cloud backend. This backend provides services that interact with the vehicles and thus enable the owners to manage their vehicles and provide interfaces to third-party services.

## 3.1 Getting started with the cloud platform

The [Eclipse Kuksa Cloud Repository](https://github.com/eclipse/kuksa.cloud/tree/master) contains the source code for some of the services and descriptors to set up an instance of the cloud backend. The two services developed within the Kuksa Cloud repository are an [app store](https://github.com/eclipse/kuksa.cloud/tree/master/kuksa-appstore) and a [Hono-InfluxDB-Connector](https://github.com/eclipse/kuksa.cloud/tree/master/utils/hono-influxdb-connector) which writes data from Eclipse Hono to an InfluxDB. Please refer to the Readme files in the linked directories for more details on how to use and extend the two services. There is also an example application to showcase the integration with a third-party service. The particular example is part of a use case where the owner gets an e-mail once the car senses an error which it would signal with a [malfunction indication light (MIL)](https://github.com/eclipse/kuksa.cloud/tree/master/examples/malfunction-indicator-light).

In addition, the Kuksa Cloud Repository provides scripts and resources to enable developers and operators to setup their own instance of the Kuksa cloud on a running Kubernetes instance. This is also important because the Kuksa Clouds makes use of a number of Open Source projects like Eclipse Hono, Eclipse hawkBit or Keycloak instead of solving the same challenges with custom solutions. More information on the deployment is located in the [deployment] (https://github.com/eclipse/kuksa.cloud/tree/master/deployment) folder. The recomended way for the deployment is to use the [Helm chart] (https://github.com/eclipse/kuksa.cloud/tree/master/deployment/helm). As mentioned above, the deployment of the Kuksa cloud requires [Kubernetes] (kubernetes.io) which is either available through many cloud providers or needs to be setup before.