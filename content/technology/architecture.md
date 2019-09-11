---
title: "Architecture"
date: 2019-09-13T16:31:34-04:00
description: ""
categories: []
keywords: []
slug: ""
aliases: []
toc: false
draft: false
hide_sidebar: true
#header_wrapper_class: ""
#seo_title: ""
#headline: ""
#subtitle: ""
#tagline: ""
#links: []
---

The Eclipse sim@openPASS platform mainly consists of a GUI and a simulation core interacting with openPASS modules as well as external programs for post-processing
[]

Figure 1: sim@openPASS top-level architecture

In the sim@openPASS GUI, the users will conveniently select traffic scenarios, traffic participants (including vehicles, drivers and systems to be tested) as well as post-processing of the simulation results. The GUI will access module information and enables the parametrization and linking of the comprised models. Furthermore, scenarios available in the OpenDrive format or OpenScenario format can be loaded. The entire configuration of the simulation will be saved in an xml-format which allows re-simulation or batch processing.

The simulation core will import the configuration, load the configured modules and run the specified number of multi-agent simulations. This mainly consists of managing the virtual world, setting up the traffic participants by instantiating their modules as well as scheduling and calling the module interface functions. Additionally, the distribution of simulations over network will be available; this is important if a high number of stochastically varied situations should be simulated, e.g. in a Monte-Carlo simulation.

The openPASS modules will contain the entire functionality of the traffic participants. SpawnPoint modules are responsible for the creation of new traffic participants. Component modules comprise models assigned to the traffic participants, hence including the human behavior and/or system behavior. A general wrapper module to incorporate models using the FMI standard will be provided as one of the demonstrator modules. Observation modules observe the traffic scenario and log general or specific simulation results.

The post-processing of the simulation results will be carried out by separate applications including evaluation or visualization.