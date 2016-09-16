# Guide for deploying Tableau in HA configuration in Azure
## Introduction
This informal document describes patterns for implementing a Disaster Recovery (DR) program for Tableau Server on the Microsoft Azure Cloud Computing platform. It also details how Tableau's existing high availability (HA) guidance can me modified and augmented by Azure's services.

It is assumed the reader understands the differences and distinctions between HA and DR in relation to an enterprise application. They will not be discussed in depth here.

That said, a brief summary of applicable concepts and definitions can be found below:

### High Availability

High availability describes a system’s ability to continue processing and functioning for a certain period of time — normally a very high percentage of time, for example 99.999%.

High availability can be implemented in your IT infrastructure by reducing any single points-of-failure (SPOF), using redundant components. Similarly, clustering and coupling applications between two or more systems can provide a highly available computing environment.

Tableau’s high availability features seek to mitigate failure at the worker (node) and process level.

### Disaster Recovery

Disaster Recovery focuses on business continuity after one or more major failures renders a data center or Tableau server offline. DR typically focuses on two key objectives:

*Recovery Time Objective (RTO)* The Recovery Time Objective is the time needed to recover from a disaster or, saying it another way, how long you can afford to be without your systems.

*Recovery Point Objective (RPO)* Recovery Point Objective describes the age of the data you want the ability to restore in the event of a disaster. For example, if your RPO is six hours, you want to be able to restore systems back to the state they were in, as of no longer than six hours ago. To achieve this, you need to be making backups or other data copies at least every six hours. Any data created or modified inside your recovery point objective will be either lost or must be recreated during a recovery.
