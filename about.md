---
layout: page
title: Wavefier in a nusthell
subtitle: A framework for multi-messenger astronomy
---

The **Wavefier** project was born with the aim of building a portable, lightweight framework to run analysis of multi-messenger data from astrophyiscal sources, leveraging modern software solutions and technologies such as containers and event streaming platforms. 

## Multi-messenger Astronomy
An event in the Universe is referred to as *multi-messenger* when it emits a variety of signals that can be detected by observatories
and instruments on Earth and in space. A typical multi-messenger event can be detected through different observation channels:
- Electromagnetic radiation(EM)
- Gravitational waves (GW)
- Neutrinos and antineutrinos
- Cosmic ray particles

Worldwide scientific collaborations study these channels by setting up and maintaining large and complex experiments that collect data and feed them to their low latency or offline analysis pipelines. When a search effort discovers a signal that is deemed of astrophysical origin, the information associated with the event produces a real-time alert which is broadcasted to the broader scientific communities by platforms that rely on event streaming services (e.g. NASA's General Coordinates Network that leverages Kafka). The alerts submitted by scientific facilities are typically in the form of human or machine readable GCN circulars and notices. Experiments and data analysis pipelines can subscribe to receive alerts from other collaborations in order to carry out follow-up studies and enrich our knowledge of the multi-messenger source that produced the event. Some examples of collaborations integrated in this schema that submit alerts are Virgo and LIGO (GW), ICE CUBE (neutrino), Fermi (GRB). 

## Why Wavefier? 
While the multi-messenger schema is well defined and the alert system has dedicated platforms and services, Wavefier is designed to provide a framework to study multi-messenger signals using information from distributed alerts and directly analysing raw and preprocessed data. A number of underlying challenges stand in the way of achieving this goal:
- Data availability and access
- Non unique data formats and data products
- Experiment specific data preprocessing
- Properties of the different signals (such as detectability, onset, duration)
- Combined analysis method
 
In its final implementation Wavefier will tackle each of these aspects to set up a customized multi-messenger analysis pipeline. Through importers Wavefier will retrieve alerts, live and archive data directly from cloud storage, local disk or external sources and send them to an event stream. Analysis pipelines attached to Wavefier will consume messages and process the data to produce triggers that will be stored in a database. A dashboard will produce graphs and plots to provide a visualization of the triggers. The workflow is described in the following section.

## Wavefier Architecture
The project is hosted on GitHub [Wavefier](https://github.com/wavefier) and is composed of different repositories. It relies on two fundamental software technologies: _[Docker containers](https://www.docker.com)_ and _[Confluent Kafka](https://www.confluent.io)_. Containers are standard units of software that put code and all its dependencies into one packaging to run applications quickly and reliably from one computing environment to another, independent of the underlying platform and infrastructure. They guarantee portability and also efficiency since, in contrast to Virtual Machines, they do not package a full copy of the OS. Confluent Kafka is a distributed streaming platform that provides a highly scalable and dependable framework for real-time data processing. 

Wavefier's software architecture is built following a modular scheme; this means that each component can be considered mostly standalone. Modularity is achieved by splitting the key components as libraries in separate Git repositories. Each component is described in a Docker image and bundled in a container. The full Wavefier framework can be deployed in a high performance computing (HPC) cluster or cloud environment with [Kubernetes](https://kubernetes.io).
