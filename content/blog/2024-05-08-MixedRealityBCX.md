+++
title = "KUKSA with mixed reality at Bosch Connected Experience Hackathon"
date = "2024-05-08"
tags = ["KUKSA.val", "VR", "VSS", "BCX"]
categories = ["use-cases"]
banner = "img/banners/2024-05-08-mixed-reality.jpg"
+++

At the recent Bosch Connected Experience (BCX) hackathon, we had the incredible opportunity to fuel the imaginations of around 280 passionate developers, all eager to bring their automotive software concepts to life. Our collaboration with the colleagues at Bosch Digital was nothing short of inspiring, as we equipped these innovators with the tools they needed: hack challenges, hardware, and code templates.

**These resources empowered participants to:**

- Craft vehicle applications using Eclipse KUKSA's Databroker abstraction and the Vehicle Signal Specification (VSS).
- Directly interact with an actual car seat via the KUKSA Databroker.
- Immerse themselves in a custom VR simulation for a truly hands-on experience.

Let's delve into how these hackers harnessed these tools to create mixed-reality vehicle setups that blend physical and virtual elements seamlessly.

## Experiencing Vehicle Applications Without a Car

Developing vehicle applications typically requires an actual car, which can be costly and impractical—especially for rapid prototyping events like BCX. While we couldn't provide each participant with their own test car, we offered the next best thing: a fully functional car seat connected to a KUKSA data broker.

## The Power of KUKSA Databroker

The KUKSA Databroker is the central hub for vehicle signals, providing a unified point of interaction for applications to access and modify various systems within a vehicle. For example, hackers could adjust the car seat by setting the target value for its tilt function through the Databroker. For instance, to tilt the seat, the participants set the target value for the signal:

Vehicle.Cabin.Seat.Row1.DriverSide.Tilt to the desired value. A so-called provider software component on a vehicle computer is connected to the KUKSA Databroker, acts on received target values, and reports back the current status of the seat. An application can check the current value to see if the seat has moved. Another application can then check whether the seat moved by checking the current value of the respective vehicle signal. During the hackathon, several teams successfully manipulated the seat using the KUKSA Python SDK—even without prior experience!

## Virtual Reality Takes It Up a Notch

But why stop at adjusting seats? The VSS data model allowed for even more complex functionalities. To accommodate these advanced use cases without additional physical components, we provided a VR simulation of an entire vehicle. Hackers donned MetaQuest 3 headsets to interact with various parts of a virtual car—from steering wheels to trunks—and even placed their creations in a simulated city environment to observe real-time interactions with vehicle states through motion.

## Merging Worlds with Mixed Reality

One of the highlights at BCX was our mixed-reality setup where physical and virtual realities converged. By connecting both environments to the same KUKSA Databroker, we synchronized state information across both realms. This meant that when someone moved the physical seat, its virtual counterpart responded in kind.

Take a moment to enjoy our demonstration video showcasing this innovative mixed-reality scenario.

{{< youtube faXGg8p4bwA >}}

## Test it out

Now it's your turn! Start experimenting and brainstorming what you can achieve with the abstraction layer provided by KUKSA Databroker. Engage with the KUKSA community or kickstart your project using resources like the [Companion Application Blueprint](https://sdv-blueprints.eclipse.dev/docs/companion-application/)  — a guided journey through creating and executing a seat adjuster application with Eclipse KUKSA and related projects such as [Eclipse Velocitas](https://eclipse-velocitas.github.io/velocitas-docs/) as your toolchain and [Eclipse Leda](https://eclipse-leda.github.io/leda/) as your deployment target.

&nbsp;
