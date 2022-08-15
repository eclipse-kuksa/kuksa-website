---
title: "About"
date: 2021-02-20T10:08:18+01:00
draft: false
---


A modern car contains more than 200 millions lines of code. This code is distributed between low level embedded components and increasingly also high-performance Vehicle Computers running operating systems and technologies originated in the IT and IoT industry.


{{< emph >}} A modern car contains more than 200 millions lines of code. {{< /emph >}}

With this shift to more computational power and faster innovation cycles, value creation for a vehicle - that is a mobility service provider -  shifts to software. Today these systems are still developed in silos by each car manufacturer or OEM in-house. However, maintaining 100s of millions of lines of code in separate silos for separate product lines is neither time- nor cost effective. Today mainstream OS installations of Linux, Windows and OS X probably share a lot more code between each other than vehicles from any two OEMs.

{{< emph >}} Linux, Windows and OS X probably share a lot more code between each other than vehicles from any two OEMs. {{< /emph >}}


<!--Establishing shared standards and software infrastructure for vehicle software ecosystems ranging from the vehicle itself  to the cloud increases development speed, saves cost and helps establishing markets and open platforms to various automotive players from OEMs to suppliers to third party service providers without compromising safety or security.
-->

The open Eclipse KUKSA project aims to provide shared building blocks for the Software Defined Vehicles that can be shared across the industry. That millions lines of code should go into generating customer value and not reinvented wheels. KUKSA tries to provide you with a solid set of wheels that can act a solid foundation for a variety of competing products and services. In that sense KUKSA components encourage cooperation on the plumbing, enabling competition and faster innovation cycles on the customer-value creating procelain.

{{< emph >}} Cooperate on plumbing. Compete on porcelain.{{< /emph >}}

One of the main features of KUKSA is abstracting vehicle data and interfaces to a common format based for example on the [Vehicle Signal Specification](https://covesa.github.io/vehicle_signal_specification/). That way, all functions sitting on top of KUKSA can run on all enabled cars. KUKSA itself focusses on the adaptation of various Vehicle Interfaces into a basic basic interfaces using simple APIs. 
This enables you to add your preferred onboard or offboard techstack to new vehicle architectures more easily. If you are looking for a complete toolchain and paradigm to build vehicle apps, you may want to check out the [Eclipse Velocitas](https://websites.eclipseprojects.io/velocitas/) project. 

The following picture shows an example deployment of KUKSA.


![Basic KUKSA example deployment](./../img/archexample.png )

To learn more about KUKSA components and activites check [our talks & publications]({{< ref "/publications" >}}) or head over to [our resources page]({{< ref "/resources" >}}).




<!-- ![KUKSA architecture](./EKuksa.png) -->

