---
layout: page
title: Pipeline Components
subtitle: Dissecting Wavefier's Modular Structure
---

A modular framework is well suited to meet Wavefier's requirements to build a multi-messenger framework which can be leveraged by scientists. Containerization enables portability and scalability in a resource efficient context along with the possibility of fast development and deployment. Moreover, Wavefier's architecture allows the user to customize the pipeline by introducing additional containers to analyse data from different astrophysical domains.

Let's delve into Wavefier's base modules one by one.

## Wavefier importers
The purpose of this class of modules is to create a mechanism to import files within the Wavefier pipeline. The files can be written in different formats and contain raw data or trigger alerts from different observatories involved in multi-messenger searches. The [wavefier-importer](https://github.com/wavefier/wavefier-importer) module retrieves 1 second gravitational frame files as they are written to the filesystem. The [wavefier-frb-disk-importer](https://github.com/wavefier/wavefier-frb-disk-importer) module imports fast radio burst trigger data from the CHIME radio telescope to the Wavefier Kafka stream. The data is taken from the public catalogs accessible at this [link](https://www.chime-frb.ca/catalog:). The [wavefier-grb-disk-importer](https://github.com/wavefier/wavefier-grb-disk-importer) module imports custom gamma-ray burst trigger data from the Fermi GBM Trigger [catalog](https://heasarc.gsfc.nasa.gov/db-perl/W3Browse/w3table.pl?tablehead=name%3Dfermigtrig&Action=More+Options) and the Fermi LAT Second Gamma-Ray Burst [catalog](https://heasarc.gsfc.nasa.gov/db-perl/W3Browse/w3table.pl?tablehead=name%3Dfermilgrb&Action=More+Options). The [wavefier-grb-fermi-importer](https://github.com/wavefier/wavefier-grb-fermi-importer) imports NASA General Coordinates Network ([GCN](https://gcn.nasa.gov)) notices for the Fermi GBM and LAT, and INTEGRAL experiments. It is possible configure the modules via docker-compose exploiting environment variables. 

## Wavefier import handlers
This library encapsulates code that retrieves the files imported in the internal Wavefier Kafka stream and makes it available to modules which process the data contained in the files (see Wavefier WDF for an example).

## Wavefier alert dispatchers
The dispatcher modules transmit the FRB and GRB alerts to the following parts of the Wavefier framework, so that they can be visualized as triggers in a database and processed by machine-learning multi-messenger pipelines. The alert data does not undergo any transformation.

## Wavefier trigger handler
The [wavefier-trigger-handler](https://github.com/wavefier/wavefier-trigger-handlers) module contains all the code to send and receive triggers in the Wavefier framework.

## Wavefier WDF
This library is responsible for the application of *Wavelet Detection Filter* (WDF) on the gravitational wave data incoming via Kafka. The WDF is an end-to-end pipeline that carries out a number of tasks: raw data downsampling, data whitening, event trigger generation via wavelet transform and signal reconstruction. For further details, we suggest you to visit the dedicated webpage [here](https://wdfpipe.gitlab.io).

## Wavefier common
This library has the intent to contain all the common part used in the wavefier project.

## Wavefier ML
Currently in development phase, this module will provide a machine-learning driven pipeline to analyse multi-messenger data imported into Wavefier.
