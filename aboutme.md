---
layout: page
title: About Wavefier
subtitle: A framework for multi-messenger astronomy
---

The **Wavefier** project was born with the aim of building a portable, lightweight framework to run analysis of multi-messenger data from astrophyiscal sources, leveraging modern software solutions and technologies such as containers and event streaming platforms. 

### Multi-messenger Astronomy
An event in the Universe is referred to as *multi-messenger* when it emits a variety of signals that can be detected by observatories
and instruments on Earth and in space. A typical multi-messenger event can be detected through different observation channels:
- Electromagnetic radiation(EM)
- Gravitational waves (GW)
- Neutrinos and antineutrinos
- Cosmic ray particles

Worldwide scientific collaborations study these channels by setting up and maintaining large and complex experiments that collect data and feed them to their low latency or offline analysis pipelines. When a search effort discovers a signal that is deemed of astrophysical origin, the information associated with the event produces a real-time alert which is broadcasted to the broader scientific communities by platforms that rely on event streaming services (e.g. NASA's General Coordinates Network that leverages Kafka). The alerts submitted by scientific facilities are typically in the form of human or machine readable GCN circulars and notices. Experiments and data analysis pipelines can subscribe to receive alerts from other collaborations in order to carry out follow-up studies and enrich our knowledge of the multi-messenger source that produced the event. Some examples of collaborations integrated in this schema that submit alerts are Virgo and LIGO (GW), ICE CUBE (neutrino), Fermi (GRB). 

### Why Wavefier? 
While the multi-messenger schema is well defined and the alert system has dedicated platforms and services, Wavefier is designed to provide a framework to study multi-messenger signals using information from distributed alerts and directly analysing raw and preprocessed data. A number of underlying challenges stand in the way of achieving this goal:
- Data availability and access
- Non unique data formats and data products
- Experiment specific data preprocessing
- Properties of the different signals (such as detectability, onset, duration)
- Combined analysis method
In its final implementation Wavefier will tackle each of these aspects to set up a customized multi-messenger analysis pipeline. The workflow is described in the following diagram:

### Wavefier Architecture
