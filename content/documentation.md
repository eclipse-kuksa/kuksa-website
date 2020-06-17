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
* The second extension is a custom Eclipse Che Assembly. A quick start steps can be found from the link [here](https://kuksa-che-ide.readthedocs.io/en/latest/quick/index.html).

Eclipse Kuksa offers various APIs for implementing vehicle applications based on AGL (Eclipse Kuksa IDE based on Eclipse Che) or docker (Eclipse Kuksa IDE based on VSCode) as well as provisioning built applications at the Eclipse Kuksa App Store. This enables accessing existing communication interfaces for the secure data transmission, storage, management, and authentication without having to take separate measurements for processing or interpreting the data.

Eclipse Kuksa also supports the simplified deployment of new applications for both the cloud and vehicle components. Configuration, building and deployment can be done at the push of a button without further configuration or processing. Depending on the application, different development tools (e.g. Logging, Debugging, Tracing,...) can be included. Of course, syntax highlighting, code completion, and other necessary IDE functions are supported. For instance, the in-vehicle Eclipse Kuksa Che stack for AGL development activities features including Yocto based SDKs in order to support target specific programming shown in the screenshot below. After compiling and building software, specifying a target IP allows also the deployment process. [Click here](https://www.eclipse.org/community/eclipse_newsletter/2018/july/kuksa.php) to read more. The Eclipse Kuksa IDE provides an easy and straight forward mechanism to create new projects based on AGL as outlined [here](https://gitlab-pages.idial.institute/pedro.cuadrachamorro/kuksa-ide/samples/index.html).

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

The user can trigger extensions from the Command Palette and also from the Editor Title.
The Kuksa extension follows the VSCode Extension file structure with standard folders like .vscode and src. It also includes the essential configuration files like launch.json, tasks.json and tsconfig.json.
Apart from the standard folders, there is also a kuksa folder. The kuksa folder contains Kuksa-specific python and shell scripts.

The most important configuration file of an extension is called the Extension Manifest. This file should be located at the root of the extension directory structure. Essentially it is a package.json file which contains a mix of Node.js and VS Code specific fields. The fields activationEvents and contributes are specially important since every extension uses a combination of these two and the VS Code API for extending VS Code’s functionality. The Extension Manifest also determines how the extension looks in the VS Code Marketplace with the icon, author,licence and repository.

### 1.2.1  Kuksa: Initialize Workspace

The Kuksa: Initialize Workspace was conceived as a way to provide new developers with the Kuksa project structure. The command generates the directories and the required build scripts. It also creates an empty yaml configuration file to be used in the next steps. The entire tree structure is as follows:
* docker
  * build.sh
* include
* kuksa.yaml

The user has to provide the IDE with the desired name of the project and the project structure will be generated with the required files and directories.
At the first step, the OS on which VSCode is running will be checked. At the moment due to file system issues only Unix-based Operating Systems like Linux or MacOS is supported. Next, the user will be asked to provide a valid name for the project. Invalid or duplicate project names will lead to a error and eventual termination of the process. Once this is successful, the corresponding bash script will be triggered and the project folder will be opened automatically in VSCode.

### 1.2.2 Kuksa: Generate Docker Image

The command 'Kuksa: Generate Docker Image' is to automate the process of creating a Docker image from a particular Dockerfile and tag it appropriately so that it can be used as an artifact for Hawkbit and consequently the Kuksa AppStore.
The command is also responsible for copying the QEMU binary to the Kuksa project directory so that it can be compiled with the source code. The underlying script of this command is again a Bash script, which is created during initialization of the project.
Important to note that the files and folders mentioned as part of the Dockerfile have to be present in the proper system paths.

### 1.2.3 Kuksa: Configure Kuksa Environment (YAML)

The command 'Kuksa: Configure Kuksa Environment' helps the developer to generate the configuration file needed for publishing the application. The command triggers a HTML form which holds some required fields to be filled.
Some of the required fields are as follows:
* Application Name
* App Version and Description
* Corresponding Docker Image
* Hawkbit, Appstore and KeyCloak URL
* Corresponding Credentials
The form as in features a tabbed look for the General, AppStore and Keycloak fields.
The configuration file is generated as YAML form. A Python script converts the field objects into the YAML format.

Undoubtedly, the most important among the Kuksa commands is Publish to Appstore. This command is responsible for packaging and deploying new or updated Kuksa applications to the Hawkbit and ultimately to the Kuksa AppStore. Keeping in mind the usability, this complex process is scaled down to only selecting a single configuration file (the same one explained above).
A Python script runs in the backend of this command. This script gets the authentication token from KeyCloak, creates a new application category if required, creates a new application or updates a new application and uploads corresponding artifacts to Hawkbit.
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
- Go to Profile → Preferences → Yocto Settings and add a new SDK with a Name, e.g. "agl-rover", a Version, e.g. "1.0.0" and a link to an appropriate AGL SDK, e.g. the AGL [Rover](https://github.com/app4mc-rover) SDK from "https://owncloud.idial.institute/s/3rjXHYTRS5HNGYN", as Download Link. Then select the added Yocto SDK. To avoid connection trouble, open the Terminal and ssh into the appropriate Device: ssh < User >@< IP >

### 1.3.3 Model-driven Development of AGL Applications and Services

The Eclipse Che Kuksa instance simplifies the development of AGL applications and services. AGL features the usage of automotive applications based on HTML5, JavaScript, and C/C++, which run on top of AGL. While applications realize a distinct use case, services offers functionality to all applications. For more information please refer to the [AGL documentation](https://docs.automotivelinux.org).

The following sections demonstrate the development of AGL applications/services in a model-driven way based on the tool RAML2AGL (cf. Section [Raml2AGL](https://github.com/eclipse/kuksa.ide/tree/master/che-6#raml2agl) ) as well as the building and deployment of AGL applications/services to a remote device running AGL (cf. Section [Building & Deploying](https://github.com/eclipse/kuksa.ide/tree/master/che-6)).


# 2. Kuksa In-Vehicle platform

## 2.1 Getting started with the In-vehicle platform

[Eclipse Kuksa](https://www.eclipse.org/kuksa/) includes an open and secure cloud platform that interconnects a wide range of vehicles to the cloud via open in-car and internet connection and is supported by an integrated open source software development ecosystem. The Eclipse Kuksa project consists of a set of repositories and the [in-vehicle repo](https://github.com/eclipse/kuksa.invehicle) contains in-vehicle platform code as well as required layers and bindings to build a Kuksa adapted AGL (Automotive Grade Linux) distribution. If not using AGL, any other platform can be chosen that supports docker. For the former, Eclipse Kuksa provides a wrapper project around AGL. From its side, AGL uses Yocto/Bitbake building system to build an automotive domain specific Linux distribution. Therefore, this projects provides a building system that adds Kuksa's specific Bitbake layers on top of the original AGL. The scripts in this project help ease the process of building an AGL image by simple using a few commands. This project includes the yocto recipes found in meta-kuksa project.

## 2.2 Required System Configuration (HW/SW) for AGL

In order to Build the Image/SDK with cmake scripts, the required system configuration both (hardware and software) are:
- Ubuntu 16
- Fast Internet connection.
- Minimum of 100 GB memory.
- Some patience as it takes about 8 hours the first time.

## 2.3 Build AGL Image/SDK

To build the Image/SDK, run:
```
    cd <agl-kuksa-root>
    mkdir build
    cd build
    cmake ..
    make <agl-kuksa-target>
```

Where \<agl-kuksa-target> can be
```
    agl-kuksa-sdk: AGL kuksa image and SDK
    agl-kuksa: AGL kuksa Image only
```

The output images can be seen at \<agl-kuksa-root>/build/images and the SDKs at `<agl-kuksa-root>/build/sdk`.

Install the necessary packages:

```
    sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib build-essential chrpath socat libsdl1.2-dev xterm cpio curl
```

Then set up the repo tool. Repo tool is used to download the recipes for AGL image.
```
    export AGL_TOP=$HOME/workspace_agl; mkdir -p $AGL_TOP
    mkdir -p ~/bin ; export PATH=~/bin:$PATH ;curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo; chmod a+x ~/bin/repo
```

Then download the Funky Flounder version of AGL. This version has been tested and is recommended.
```
    cd $AGL_TOP ;repo init -b flounder -m flounder_6.0.1.xml -u https://gerrit.automotivelinux.org/gerrit/AGL/AGL-repo ;repo sync
```

Start the build system and would take about 7 hours to complete if you are running for the first time, so you could take a nap :P. The Yocto/bitbake build system has a caching mechanism and hence from the next time on, this would only take a few minutes.
```
    source meta-agl/scripts/aglsetup.sh -m raspberrypi3 agl-demo agl-netboot agl-appfw-smack ; bitbake agl-demo-platform
```

Go to `$HOME/workspace_agl/build/conf` folder and open the `bblayers.conf` file.

Append the following lines to the end of the file.
```
    BBLAYERS =+ " \
        ${METADIR}/meta-kuksa \
        ${METADIR}/meta-kuksa/meta-kuksa-bsp \
        ${METADIR}/meta-virtualization \
    "
```


Now copy the meta-kuksa folder (Link : https://github.com/eclipse/kuksa.invehicle/agl-kuksa) into the `$HOME/workspace_agl` directory.

## 2.4 Set up the AGL platform on RPI3

To get started with In-Vehicle platform: AGL KUKSA Build and Run on Raspberry Pi 3 / Compute Module 3 (Lite) can be found from the link [here](https://github.com/eclipse/kuksa.invehicle/tree/0.2.0/agl-kuksa/meta-kuksa).

To build for the Raspberry Pi CM3 (Lite) platform, go to `$HOME/workspace_agl/build/conf` folder and open `local.conf` file.

Append the following lines to the end of the file.
```
    KERNEL_IMAGETYPE = "zImage"
```

The Kuksa layer contains recipes for the APIs and Apps contained in Eclipse Kuksa In-vehicle repo.

The AGL image with meta-kuksa layer adds w3c-visserver-api and elm327-visdatafeeder as systemd services. It will install the datalogger apps in the respective locations `/usr/bin/datalogger-\<PROTOCOL>`.


### 2.4.1 Set up wifi

*NOTE. Ignore this step if wifi is not required.*

With meta-kuksa layer the wifi connection could be set up while building an Image so that the target device connects to the specified wifi, which make it easier to ssh into the device. The wifi settings could be configured by modifying the `meta-kuksa/recipes-devtools/wifi-conf/files/wifi_default.config` file. Update the "Name" and the "Passphrase" of the wifi you want the device to connect to. More more secured wifi connection please refer to the link.

### 2.4.2. Configure Bluetooth connection with ELM 327 bluetooth adapter

The elm327-datafeeder service connects to an ELM327 Bluetooth adapter to retrieve data from the vehicle. Hence the bluetooth connection with the ELM327 adapter needs to be established before the service starts. The BT connection can be configured by Updating the MAC-Address of the adapter along with its pairing PIN. The MAC-Addr and PIN can be updated in `meta-kuksa/recipes-elm327-visdatafeeder/elm327-visdatafeeder/files/bt_setup.sh`.

Update the fields

<p style="text-align:center;">
 <a href="/kuksa/docimgs/bt_setup.png">
   <img src="/kuksa/docimgs/bt_setup.png" width="60%" alt="Bluetooth connection setup"/>
 </a><br/>
</p>
Now, build image with Kuksa layers:
```
    source meta-agl/scripts/aglsetup.sh -m raspberrypi3 agl-demo agl-netboot agl-appfw-smack ; bitbake agl-demo-platform
```
This would take a few minutes to execute and at the end of the process the bootable image for RaspberryPi 3 will be found in the below location
```
    $HOME/workspace_agl/build/tmp/deploy/images/raspberrypi3
```

### 2.4.3 Connect the platform to Kuksa portal

Once the image is ready, burn it onto a SD-card and boot up the image on RPi3. The w3c-visserver-api requires the vss_rel_1.0.json file to set up the vss tree structure. This file can be copied to the `/usr/bin/w3c-visserver` folder by using scp command (sample file is available under https://github.com/GENIVI/vehicle_signal_specification or could also be generated using the tools in the repo). Once the file has been copied reboot the RPi3.

&nbsp;

### 2.4.4 Launch Datalogger Apps

The Datalogger apps connect to a remote HONO-Instance and hence the IP-address of the Hono-Instance needs to be updated. The datalogger apps are already installed if you have followed the above steps. Now update the Hono configuration in the `/usr/bin/datalogger-*/start.sh` with valid IP-address for the respective adapters (e.g., HTTP and MQTT), Port, Device and password for Hono. Also, the datalogger apps should be started by executing `./usr/bin/datalogger-/start.sh`.
The apps connect to the w3c-visserver service using a websocket connection and retrieves Signal.OBD.RPM and Signal.OBD.Speed values to send to hono by packing the retrieved data into a json which looks like this {SPEED:xxx} & {RPM:yyy}. The Datalogger example for kuksa-app which connects to the w3c-visserver service via Websocket and talks to the Eclipse Hono MQTT adapter are [DataLogger-HTTP app](https://github.com/eclipse/kuksa.invehicle/tree/master/datalogger-http) and [DataLogger-Mqtt](https://github.com/eclipse/kuksa.invehicle/tree/master/datalogger-mqtt).

### 2.4.5 Installing RoverApp

This tutorial [link](https://app4mc-rover.github.io/rover-docs/content/installation.html#) contains how to set up a Rover-specific Raspbian image from scratch and the basic workflow to run the Roverapp applications.

<!-- THE FOLLOWING IS COPY PASTE STUFF FROM APPSTACLE AND MUST BE CHECKED WRT RELEVANCE FOR THIS DOC
### *In-Vehicle Platform*
The Kuksa environment is created to provide addon services to the connected vehicles. This provides a complite functionality of the vehicles through deploying the *Apps* on the in-vehicle platform. Therefore, three layers of components are required to enable this purpose:

**Core Layer**: Contains the in-vehicle platform components, such as operating system and application runtime. It, furthermore, allows the vehicle owner to interact with the vehicle, e.g., via smartphone access. In addition, it provides an intrface to the 5G infrastructure similar to the core layer of the cloud back-end.

**API / Binding Layer**: consists of relevant APIs and components for internal and external communication.

**Application Layer**: It represents the arrangement of all Apps that are running within the in-vehicle platform.

The in-vehicle platform addtionally provides means for rertrieving telemetry data collected by the vehicle itself as well as a human machine interface (HMI ) for user interaction.

### *In-vehicle connectivity*

This section provides an overview of the communication protocols that are currently used in the existing automotive architectures as well as their interconnections in the Electrical / Electronic (E/E) in-vehicle architecture.
The scope of these protocols defines the in-vehicle communication interfaces for
the APPSTACLE platform.

#### *Protocols*

Automotive protocols are classified by the Society of Automotive Engineers (SAE) into four categories according to the transmission rate and their role in the automotive architecture. Specifically, Class A defines the protocols that are used for convenience systems (e.g. lighting, windows, seatcontrols) and require inexpensive, low-speed communication. Class B defines the protocols supporting instrument cluster or vehicle speed communication and require medium-speed communication. Furthermore, Class C is defined for real-time control ECUs such as the engine, braking and steer-by-wire and require high-speed communication. Finally, telematics systems usually require higher communication speed for multimedia (audio / video) and navigation, and therefore SAE defined the additional Class D communications. All four protocol Class categories are illustrated in <span style="color:lightblue">Table 1</span> along with the protocols that belong to each category and are used for in-vehicle communication in terms of their characteristics.

<p style="text-align:center;">
	<a href="AutomotiveNetwork.png">
		<img src="AutomotiveNetwork.png"
			alt="Automotive network" width="60%">
	</a>
</p>

&nbsp;

**Table 12.: Characteristics of the communication protocols**

|Bus|LIN|CAN|CAN FD|FlexRay|MOST|Automotive Ethernet|
|---|----|----|----|----|----|----|
|Used in Application domains Message transmission Access control Maximum Data Rate Protocol Class | Subnets Body Soft Synchronous Polling 20 kbps A|Soft real-time Powertrain, Chassis Asynchronous CSMA/CA 1 Mbps BC| Soft real-time a a CSMA/CA 10 Mbps D|Hard real-time Chassis, Powertrain Synchronous and Asynchronous TDMA 10 Mbps D | Multimedia Multimedia and Telematics Synchronous and Asynchronous CSMA/CA 24Mbps D| Multimedia Telematics and active safety Synchronous and Asynchronous CSMA/CD 100Mbps D|

&nbsp;

#### *Architectural Overview of In-vehicle*

Modern automotive embedded systems consist of several subsystems, which are comprised of one or several Electronic Control Units (ECUs). In turn, the ECUs are made up of a micro-controller and a set of sensors and actuators. They are able to communicate through the transmission of electronic or optical signals through a dedicated communication unit. The subsystems that rely on network communication in automotive systems are divided into five main categories: power train, chassis, body, HMI, and telematics (illustrated in <span style="color:lightblue">Figure 3</span>). Each subsystem uses a different protocol to communicate, which is selected based on the architectural requirements and the subsystem functionality. Specifically, the powertrain domain is related to the systems that participate in the longitudinal propulsion of the vehicle,including engine, transmission and all subsidiary components. This domain is supported by a dedicated subsystem called Drive CAN using the Controller Area Network (CAN) for data exchange. The chassis domain refers to the four wheels and their relative position and movement; in this domain the systems are mainly steering and braking. In this subsystem category we find two protocols that are used for high-critical communication, namely CAN and FlexRay, as well as the Local Interconnect Network (LIN) for the lower critical functionalities (e.g. door locking, window raising / lowering). According to the EAST-EEA 1 project definition the body domain includes the entities that do not belong to the vehicle dynamics (i.e., being those that support the car’s user) such as airbags, wipers, lighting, etc. Today’s cars sometimes use two CAN buses (peripheral CAN and body CAN) which interconnect the ECUs of the comfort domain. The telematics domain includes the equipment allowing information exchange between electronic systems and the driver (displays and switches). Such interactions are possible through the infotainment subsystem that is supported by the MOST protocol. Finally additional peripheral systems (e.g.,cameras) allow the in-vehicle system to monitor and extract information from its physical environment through the use of Automotive Ethernet technologies. All the aforementioned systems are able to exchange data through a central gateway (<span style="color:lightblue">Figure 3</span>) that is able to map (through packet encapsulation) or forward messages from one subsystem to another.

1. It enables communication with the infotainment unit or the ECUs internal to the vehicle.
2. Telemetry data or data specified in the Cloud platform related to internal vehicle functionality.
    * Vehicle diagnostics (e.g. health monitoring).
    * System metadata (which components are present, heartbeats etc).
3. Interacts with the in-vehicle HW for data gathering and with the ex-vehicle connectivity for data forwarding.
4. One component per vehicle with different interfaces according to the employed protocols.
5. Information about the protocols used in the internal vehicle architecture.
    * Depending on the chosen protocols: what components are communicating what information.
    * Development of software modules for handling data for each protocol.

### *Ex-vehicle connectivity*

The technology evolution in the automotive vehicles contributed to the demands for smarter mobility solutions. These solutions are focused on several types of V2X communication:

* Vehicle-2-Vehicle (V2V)
* Vehicle-2-Infrastructure/Infrastructure-2-Vehicle (V2I,I2V)
* Vehicle-2-Pedestrian (V2P) / Pedestrian-2-Vehicle (P2V)
* Vehicle-2-Network (V2N) / Network-2-Vehicle (N2V), 5) Infrastructure-2-Network (I2N) / Network-2-Infrastructure (N2I).

These types along with their interactions are demonstrated below.

<p style="text-align:center;">
	<a href="V2XCommunicationType.png">
		<img src="V2XCommunicationType.png"
			alt="V2X communication types" width="60%">
	</a>
</p>

The units supporting V2X communication are:

* *RoadSide unit (RSU)*: It is connected to road sensors (e.g. induction loops, cameras) and a local control center, such that it performs actions or exchanges critical information other vehicles or servers about road or traffic management.
* *OnBoard unit (OBU)*: The on-board unit (OBU) is a radio built-in vehicle device mounted on each vehicle that transmits vehicle data (i.e. identification and location) to a transponder. The OBU itself is a transponder, that is, a data exchange takes place automatically and only on request of one of the participating devices. It allows Vehicle-to-Vehicle (V2V) and Vehicle-to-Infrastructure (V2I, I2V) communications with other OBUs or RSUs.
* *Backend server* : It is composed by a PKI, traffic management and roadside unit management servers, all accessible via the RSU’s or cellular base stations. In order to facilitate this evolution a couple of solutions were defined that are split into 3 main categories:
* *5G radio access technologies*: This technology provides wide area, broadband access. The 5G technology is currently in the process of conceptual development and standardization by the World Radiocommunication Conference (WRC). The 5G technology is expected to have a specific V2X aspect of the 5G technology in a practical scale after 2020. However, in this document we are leveraging the limited standardization to illustrate conceptually its main scope and architectural view.
* *Pre-5G radio access technologies*: Multiple cellular technologies were identified by the ETSI 3rd Generation Partnership Project (3GPP), LoRa Alliance and other organizations, such as Narrowband IoT , Long Term Evolution for Machines (LTE-M), LoRA are considered. Even though these technologies are already used in V2P/P2V, the main challenge when adopting them in other V2X communication types are reliability and safety, which are currently not addressed in the scope of Low-Power Wide Area Networks (LPWAN).
* *Non-cellular technologies providing wireless access*: IEEE has defined different standards for wireless communication, such as 802.11ac and 802.11p, however only 802.11p is flexible in terms of throughput and offers higher reliability, even though its maximal throughout is more limited than 802.11ac (from 3 to 27 Mbps raw data rate). The reason behind this is that 802.11p was designed particularly for for safety-related Vehicular Ad-hoc NETworks (VANET), including the V2V and V2I/I2V concepts. IEEE 802.11p technology is currently fully specified and already deployed in different locations. The following paragraphs start with a description of the scenarios supported by 802.11p communi-cation and cellular communication. This is followed by a description on both the 802.11p and 5G technologies. In the scope of this section we focus on these two technologies, because, to the best of our knowledge, they are considered as the leading candidates for V2X communication.


**Property:**
1. It enables outward and inward communication between the vehicle and the external entity.
2. No data processing as such.
    * Re-Packs the data received from bus to appropriate format for the external entity and vice versa.
3. It has the direct connection to the BUS and no direct user interaction.
4. There will be multiple instances in the minimum two cases.
5. Driver for hardware component.
    * (Since Development Stage) Need manual configuration at the moment for 5G mm Radio.


### *App Runtime*

**Property:**
1. The APP Runtime provides the environment for executing APPs and starts / stops APPs. It has to provide and control resources for the APP, enforce access control (permissions), and isolate APPs from each other.
2. APPs, configuration data (permissions, options, ...), APP data.
3. The APP Runtime permits or denies communication between APPs, or APP and backend (depending on "the policy"). The APP Runtime obtains APPs from the marketplace. It can be configured by the OEM and/or the vehicle owner (via backend and/or an in-vehicle user interface; probably also by devices [with authorization]).
4. There is one APP Runtime per in-vehicle platform. It could be part of the operating system.
5. Initialisation / start up: The APP Runtime is started during the (secure) boot process. It can be configured by the OEM and the vehicle owner (details are left open in this document), e.g., to configure permissions ("the policy").

### *Automotive API*

The Application Programming Interface (API) for vehicles are introduced and discussed in here. The automotive APIs try to achieve (a) merging the potentially very complex device and network structure of a car into a single virtual device and (b) hiding the differences between manufacturers, models and makes behind a common interface. On the other hand these interfaces strongly differ in their scope (data-subset or use-case), technological approach and creators.

#### *AUTOSAR*

AUTomotive Open System ARchitecture (AUTOSAR) is a cooperation between car manufacturers, OEMs and tool manufacturers and defines a software development paradigm for Electronic Control Units (ECUs) in the automotive domain. In order to separate the development process of application software from the chosen ECU hardware platform, AUTOSAR is introducing a layer model with the three layers Application Software, Runtime Environment and Basic Software.

<p style="text-align:center;">
	<a href="AutosarLayerModel.png">
		<img src="AutosarLayerModel.png"
			alt="Autosar Layers" width="60%">
	</a>
</p>

The top layer is formed by the application software. It is divided into software components, each of which realizes a part of the application and can consume and provide data via so-called ports. Any communication that does not take place via port connections is forbidden. A port is classified via a port interface (here referred to as interface). Two ports can only be connected to each other if both ports use compatible interfaces.
Two important communication paradigms, that are selected by interfaces, are client-server and sender-receiver communication. For client-server communication, a server component provides functions (C, C++) which can be called by clients. A 1:n communication is also possible (i. e. a server can provide its functionality to several clients). In sender-receiver communication, a sender provides data that can be consumed by receiver components. Both 1:n and m:1 communication is possible here (i.e. a date can be consumed by several components or several senders provide a date for one receiver concurrently). Many-to-many communication is not provided.

The lower layer consists of the basic software and contains the hardware drivers, the operating system and the communication stack. The communication stack handles communication from and to other ECUs that are connected via network interfaces like CAN, LIN, Flexray, automotive Ethernet, etc.

All communication, whether between software components on the upper level or between software components and basic software on the lower level, is realized via the runtime environment (RTE), which forms the middle layer. The RTE specification document defines a schema for API functions (C, C++), which are usually generated by code generators of the AUTOSAR modeling tools according to the modeled communication between software components and basic software. All communication must take place via the (generated) API functions. Other communication is not permitted. Likewise, all communication interfaces must be defined at the time of development, which makes it impossible to dynamically extend the software architecture at runtime.

**Property:**
1. The Automotive API provides an interface to in-vehicle data for APPs (and cloud ser-vices? other entities??). An (operating system) service ("Automotive API server") implements the Automotive API, for instance similar to the "Vehicle Information Service" specified by the W3C.
2. Vehicle data (sensor data, diagnosis information, configuration of vehicle components, vehicle status information, ...).
3. It can be used by APPs (and cloud services, etc.) to retrieve information from the vehicle, to send data to in-vehicle components, and to write (vehicle) configuration data.
4. There is one Automotive API per in-vehicle platform.
5. Initialisation / start up: The "Automotive API" service is started during the (secure) boot process.


### *Apps*

**Property:**
1. (In-vehicle) APPs are programs that provide new features to the vehicle.
2. App data (depends on APP / use case).
3. APPs are executed and controlled by the APP Runtime and can access in-vehicle data via the Automotive API. They can communicate with other entities via connectivity APIs (cf. architecture picture). If permitted (by "the policy"), they might communicate with cloud services (backend providers) and other APPs, and they could interact with the driver via a GUI (if available). APPs can access resources via the APP Runtime (subject to "the policy"). A user can install APPs from the Marketplace in the vehicle.
4. There can be multiple APPs per in-vehicle platform.
5. Initialisation / start up: APPs are started by the APP Runtime. Configuration data depends on the APP / use case.

### *Device Management Client*

**Property:**
1. The DM is responsible for keeping the devices compliant to the whole system land-scape. This starts with building up a base in communication and process protocols. It is also providing features for securely enrolling new devices, governing and con-figuring them while being out in the field, monitoring and debugging their behavior remotely and maintaining the devices with software updates. Four subjects can be distinguished:
    * Enrollment includes provisioning and authentication for bringing new devices into an IoT landscape. The authentication assures that only trust-worthy devices are added to the network and connected to cloud services. Also only authorized users should be able to bring in new devices and gain access according to their roles granted.
    * Governing contains features for controlling and configuring devices. As IT systems are often under a constant development, some parts change and so do some of their constants, for example network addresses or ports.
    * Monitoring keeps an eye on all components of the system and their status. Reports and alerts for incidents are raised and logged. An on-time awareness of system issues is enabled. For diagnosis and solving software bugs it is also imperative to load log dumps remotely from devices.
    * Maintenance with the ability to distribute and apply software updates is the fourth subject. The device management assures that the update is delivered and applied to the device according to the present constraints. Feedback mechanisms answer back to the cloud for a detailed status of the update.
2. **Process**
    * System states
    * Application states
    * Update states
    * Management Calls
    * Push Calls
    * Alarms
    * Enrollment policies
    * Updates, Update scheduling
    * Inventory Hardware/Software listings
    * Communication requests

   **Provides**
    * Access to resources through OMA-DM Management Objects (http://www.openmobilealliance.org/wp/OMNA/LwM2M/LwM2MRegistry.html)
        * Management access through LwM2M)
    * Push Service (for notifying in-vehicle Applications form the cloud)
    * Monitoring Service
    * Update Service (Maintenance)
    * Keep-Alive Signal Service
    * Inventory Hardware/Software
    * Enrollment Service
    * Control Service (e.g. shutdown certain components)
3. **Apps, OS: (Re-)Configure, Update**
    * ECU: Flashing/Updating ECUs
    * Apps: Notify/Wake Up through push
    * HW/SW: Read Inventory
    * HW/SW: access on resource (if Management Object is defined)
    * User: Update scheduling
4. **The DM can only exist once per vehicle. But it is split into its functional groups (subjects). A hierarchical design of distributed DMs in a vehicle might be the subject of another design.**
5. **Authentication Set (MAC, UUID, Public Key)**
    * Cloud contact
        * Address of DM at the desired cloud
        * Certificate

### *Operating System (OS)*

1. **The Operating System is the backbone any platform where it operates including In-vehicle platform. We also consider drivers as being part of the Operating system.**

*Operating System*
* consists of kernel and user space components
* provides security
* I/O and networking services to applications running in user space
* runs on bare metal or hypervisor
* OS kernel provides:
    * processes/thread management including scheduling
    * inter process communication
    * memory management
    * access to underlying HW
    * networking stacks
    * I/O stacks
    * security subsystem include:
        * access control (e.g. MAC)
        * crypto and key management
        * integrity measurement
        * entropy pools and gatherig entropy from variouos sources It is also important to highlight that the security hardening of an OS scrucial to the platform and application security
2. **Process**
* data to/from underlying HW
* data to/from networking
* data to/from file system
* user input
* data exchanged between kernel and user space
* data exchanged between processes
* configuration data such as security policies, system settings,..

*Provide*
* System state information (running processes, CPU utilization, etc.)
* log data
* debug or diagnostics data if certain debug features are enabled
3. **Access to underlying HW**
    * peripherals
    * networking interfaces
    * any physical interface
    * HW based crypto and key management functionality
    * HW based TRNG (True Random Number Generator)
*   App-Runtime (transport layer)
    * Provide transport layer interface for Apps (inter-app communication, app to cloud backend communication)
    * Provide system level services (file access, etc.)
*   Device Management Client (transport layer)
    * Provide transport layer interface for communication with device management (cloud backend)
* 5G Infrastructure (data link layer)
    * Connection Management
*   Smartphone (data link layer)
    * Pairing
    * Connection Management
    * Data Transfer
* Net-IDS
    * Provides Interface to allow the Net-IDS to monitor network traffic.
4. Different subsystems on a vehicle may be running their own OSes
* whether on bare metal or virtualized
* whether micro kernel based, unikernel based or rich OS such as Linux
5. build and runtime OS configuration
    * for process, resource management, memory management, functionality, security,..
    * policies (e.g. security)
    * configuration of different processes
    * networking configuration
* User credentials

&nbsp;

## *2.4 Overview of the Kuksa In-Vehicle API*

The Kuksa In-Vehicle API implementation is based on [W3C Vehicle Information Service Specification](https://www.w3.org/TR/2018/CR-vehicle-information-service-20180213/).

The implementation provides all the major funtionality defined in the above specification and also uses JWT Token for permissions handling with decent amount of uni-tests covering all the basic funtions. This project uses components from other open source projects namely

1. [Simple-WebSocket-Server](https://gitlab.com/eidheim/Simple-WebSocket-Server) which is under MIT license.
2. [jsoncons](https://github.com/danielaparker/jsoncons) which is under Boost Software license.
3. [jwt-cpp](https://github.com/Thalhammer/jwt-cpp) which is under MIT license.

The overall details on how to build and run W3C as well as details of W3C VIS Server Implementation can be found from the repo [link here](https://github.com/eclipse/kuksa.invehicle/tree/master/w3c-visserver-api).


-->

# 3. Eclipse Kuksa Cloud Platform

The Eclipse Kuksa project consists of a cloud backend. This backend provides services that interact with the vehicles and thus enable the owners to manage their vehicles and provide interfaces to third-party services.

## 3.1 Getting started with the cloud platform

The [Eclipse Kuksa Cloud Repository](https://github.com/eclipse/kuksa.cloud/tree/master) contains the source code for some of the services and descriptors to set up an instance of the cloud backend. The two services developed within the Kuksa Cloud repository are an [app store](https://github.com/eclipse/kuksa.cloud/tree/master/kuksa-appstore) and a [Hono-InfluxDB-Connector](https://github.com/eclipse/kuksa.cloud/tree/master/utils/hono-influxdb-connector) which writes data from Eclipse Hono to an InfluxDB. Please refer to the Readme files in the linked directories for more details on how to use and extend the two services. There is also an example application to showcase the integration with a third-party service. The particular example is part of a use case where the owner gets an e-mail once the car senses an error which it would signal with a [malfunction indication light (MIL)](https://github.com/eclipse/kuksa.cloud/tree/master/examples/malfunction-indicator-light).

In addition, the Kuksa Cloud Repository provides scripts and resources to enable developers and operators to setup their own instance of the Kuksa cloud on a running Kubernetes instance. This is also important because the Kuksa Clouds makes use of a number of Open Source projects like Eclipse Hono, Eclipse hawkBit or Keycloak instead of solving the same challenges with custom solutions. More information on the deployment is located in the [deployment] (https://github.com/eclipse/kuksa.cloud/tree/master/deployment) folder. The recomended way for the deployment is to use the [Helm chart] (https://github.com/eclipse/kuksa.cloud/tree/master/deployment/helm). As mentioned above, the deployment of the Kuksa cloud requires [Kubernetes] (kubernetes.io) which is either available through many cloud providers or needs to be setup before.

<!-- WHAT IS THIS?

**Kuksa documentation version**

    |No.|  Author  | Ver.  | Date     | verified by | Remark    |
    |---|----------|-------|----------|-------------|-----------|
    |1. |  Kirubel | 0.1   |28.07.2019|    Nill     | No remarks|
-->
