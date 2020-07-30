---
title: "Architecture"
date: 2019-09-13T16:31:34-04:00
description: ""
categories: []
keywords: []
slug: ""
aliases: []
toc: false
hide_sidebar: true
---
## Platform Concept

The platform concept is shown in the following picture.

{{< figure class="padding-30 margin-right-50 margin-left-50" src="/architecture/platform-concept.jpg" alt="openPASS platform concept" >}}

The platform is built up in a modular manner. The simulation core calculates different simulation runs. Scenarios and agent components can connect to the core over standardized interfaces like OpenSCENARIO, OpenDRIVE, OSI and FMI. The openPASS WG provides simple examples of scenarios and agent components. Consequently, the user can freely connect their own scenarios and agent components to the simulation core. Possible use cases of using openPASS are accident research, functional development, safety performance assessment, virtual testing and virtual homologation. 

{{< figure class="padding-30 margin-right-50 margin-left-50" src="/architecture/openpass-interfaces.jpg" alt="Diagram containing interfaces of openPASS" >}}

## Top-level Architecture

{{< figure class="padding-30 margin-right-50 margin-left-50" src="/architecture/top-level-platform-diagram.jpg" alt="Top level system architecture diagram" >}}

openPASS has two main parts: the graphical user interface (GUI) and the simulation framework.  

The GUI is meant to give the user an easy access to configure experiments prior to simulation. In order to perform a traffic simulation an input must be available, which can be prepared and offered by one of the GUI plugins. In the GUI, the users will conveniently select traffic scenarios, traffic participants (including vehicles, drivers and systems to be tested) as well as post-processing of the simulation results. openPASS simulation accepts open formats such as openDRIVE, openSCENARIO and several openPASS-specific formats. Each file defines either simulation parameters, traffic scenario, traffic composition, events or other key data. It is built as a modular software allowing attachment of independent or dependent plugins. A plugin can read input data (e.g. from a PCM database), process this data and prepare an experiment configuration, which can be understood by the simulation.  

The simulation framework is a standalone executable (to be precise, two of them). It consists of:  

- the simulation core (master and slave),
- the core modules
- and the agent components.  

The core is a mostly generic assembly of data I/O routines, scheduler and a collection of interfaces. The master executable is meant to only collect and organize input data. The slave executable is the one performing the actual simulation. A master can, if configured so, start several experiments simultaneously by triggering several slaves.  

The core modules and agent components belong to the slave application. Both communicate with the slave via interfaces and bound dynamically at runtime.

{{< figure class="padding-30 margin-right-50 margin-left-50" src="/architecture/core-module-diagram.jpg" alt="Core module diagram" >}}

Core modules are all singletons and used by the slave and/or agent components. These are necessary for every simulation to run and cover basic needs like e.g.:  

- contain world representation  
- initiate agents within the world  
- perform random number operations  
- detect event  
- log and output simulation results  

On the other hand, agent components represent a composition of participants or agents. They define the behaviour and dynamics of each agent. A set of such components is then called system. 

{{< figure class="padding-30 margin-right-50 margin-left-50" src="/architecture/agent-component-diagram.jpg" alt="Agent component diagram" >}}

Unlike core modules, components can be freely selected and assembled by the user according to his scope of application. A typical system would consist of a sensor perceiving the environment, an algorithm performing analysis of this environment and making decisions and a dynamics algorithm receiving directives from the algorithm and calculating the actual physical simulation step. When assembling a system, the user shall of course care about connecting the chosen component via signals, which are understood by the sender and the receiver.  

Completing the loop back to the graphical UI, a plugin can await the completion of one or several experiments and collect the output produced by the simulation in order to evaluate and/or visualize the results.

## Simulation Process from the User Perspective  

{{< figure class="padding-30 margin-right-50 margin-left-50" src="/architecture/simulation-user-perspective.jpg" alt="User perspective of the simulation process" >}}

The illustration above shows the simulation process in openPASS. Over configurations in the GUI the user set up the desired simulation run. Basically, the GUI supports the user to set up the simulation in accessing and writing .xml, openSCENARIO and openDRIVE files. After the setup of the configuration files the simulation can be executed. As an output .csv and .xml files are generated. For the future, the evaluation over the GUI should be available which is yet still under development.
