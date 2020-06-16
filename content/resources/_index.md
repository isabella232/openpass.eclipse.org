---
title: "Resources"
date: 2020-05-19T14:08:12-04:00
description: ""
categories: []
keywords: []
slug: ""
aliases: []
toc: false
draft: false
hide_sidebar: true
layout: "single"
---

## Sim@openPASS

Sim@openPASS is the platform which is created, developed and maintained by the openPASS WG. The Eclipse sim@openPASS platform mainly consists of a GUI and a simulation core interacting with openPASS modules as well as external programs for post-processing. More information about the project can be found on the [project page](https://projects.eclipse.org/projects/technology.simopenpass). [This link](https://git.eclipse.org/r/plugins/gitiles/simopenpass/simopenpass/) directs you to the git repository to download the simulation platform.

## Installation

Here you can download [the installation guide for sim@openPASS](osi_world_set_up.pdf).

Besides that, the openPASS WG cooperates with the High-Performance Computing Center Stuttgart HLRS. They provide a Windows installer for openPASS. The openPASS WG and the Eclipse Foundation are not responsible for the content and the installer did not went through any Eclipse Foundation processes. For a quick setup please have a look on their [site](https://fs.hlrs.de/projects/covise/support/download/openPASS/). If you are also interested to make distributions regarding openPASS relevant content, please get in contact with us. The contact information can be found in the tab "Contact".

## Tutorial

Here you can download a [tutorial on how to configure a simulation with openPASS](tutorial_openpass_gui.pdf).

## Documentation

Here you can download the [documentation to openPASS](openpass_function_docu.chm).

Here you can download the [documentation to the openPASS GUI](documentation.chm).

## Glossary  
### General  

|Term                 |Definition|
|---------------------|---|
|Active safety Systems|Active safety systems are, within the context of the tool, systems that have notable safety effect on the course of simulated situations.|
|ADAS                 |Advanced Driver Assistance System|
|PCM of GIDAS         |PreCrash Matrix from the database of the German In-Depth Accident Study|

### openPASS
#### Framework-Architecture  

|Term          |Definition|
|--------------|---|
|Core          |Consists of a master-slave system and provides the main functionality of the framework, like creating agents, scheduling tasks and coordinating the flow of information.|
|Core Module   |A module that provides a main function to the core, like a detection of collisions or some stochastic equations. These modules are not part of the core, but part of the framework itself. They´re exchangeable, so that some functionality can be implemented differently.|
|Framework     |A software environment which provides the functionality to simulate a set of different traffic scenarios. Consists of the Core and the Core Modules.|
|openPASS      |Framework for the simulative evaluation of active safety systems in vehicles.|
|OpenPassMaster|Coordinator of the simulation process. It starts one slave for each scenario.|
|OpenPassSlave |The OpenPassSLAVE is the simulator. It runs one scenario with a defined number of similar situations.|


#### Agents  

|Term           |Definition|
|---------------|---|
|Agent          |An arbitrary static or dynamic object in the simulation of a traffic situation. Therefore, it might (but does not have to) be a traffic participant. An agent consists of one Agent Equipment and its physical parameters.|
|Agent Equipment|A set of components determining an agent’s behavior.|
|Component      |A module that defines a specific part of an agent’s behavior, like sensing the environment (Sensor) or calculating a desired acceleration (Algorithm).|
|Signal         |A general term that subsumes inputs and outputs. Signals are transported by channels within an agent’s equipment.|

## Report a Bug

The openPASS WG uses Tuleap, an open source agile project management tool. Among other things, we are using it to track bugs, create user stories, epics and plan the next releases. Under the tracker “Bug” you can report your bug. Furthermore, you can find a summary which concludes all the previous fixed, ongoing and the new bugs. [Click here to create your first bug](https://tuleap.eclipse.org/plugins/tracker/?tracker=112).
