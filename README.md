# diplomacy
A peer-to-peer geopolitical crysis - Distributed Systems course 2025-2026 @unibo

## Vision
I propose to design and implement Diplomacy, a decentralised peer-to-peer system in which each European country is an autonomous node that can communicate only with its geographical neighbours. The political map of Europe thus becomes the network topology: messages between distant countries must travel through intermediate nodes. Countries are used purely as a topology; no real-world political modelling is involved.

Every country runs as an independent process. There is no central coordinator: an observer only collects events to feed an interactive web map, from which the user can watch the network and eventually inject faults.

The core challenge is dealing with failures in a network where each node has only a local view. This means detecting that a neighbour is gone, limiting the spread of local failures, coping with network partitions, and bringing crashed nodes back to a consistent state. In the project's metaphor, a failure is a breakdown of diplomatic relations, and recovery is the resumption of diplomacy.
###Key Distributed Features

* Neighbour-only communication: nodes exchange messages only with adjacent countries, with multi-hop routing for everything else.
* Failure detection: nodes monitor their neighbours and adapt routing when one becomes unreachable.
* Cascading failures: a failure can overload nearby nodes and propagate across the network.
* Partitions: the system detects and shows when the network splits into disconnected regions.
* Recovery: crashed nodes can be restarted and brought back to a consistent state through checkpointing and message logging.

## Learning Goals

* Dependability: understanding crash and omission faults in a decentralised system, how to detect them, and how local failures propagate.
* Partitions & CAP: observing network partitions in practice and the trade-off between consistency and availability.
* Recovery: designing recovery mechanisms based on checkpointing and message logging.

## Intended Technologies

* Language: Python with asyncio.
* Communication: socket-based messaging between nodes.
* Deployment: Docker & Docker Compose, to run each country as a separate node.
* Visualization: a web dashboard with an interactive map of Europe, updated in real time.

## Intended Deliverables

* Source code (country node, observer, web map).
* Docker Compose setup to run the whole network.
* A fault-injection mechanism (crash a node, cut a link, restart a node) to demonstrate failures and recovery during the exam.
* Final Report.

## Usage Scenarios
* Normal Operation: a message between two distant countries is routed through intermediate nodes, and the map shows its path.
* Partition: a key country is crashed; its neighbours detect the failure, and the map shows a region of Europe becoming isolated.
* Cascade: the failure of a central country overloads its neighbours, and the map shows the failure spreading.
* Recovery: a crashed country is restarted and resumes its role in the network, recovering its state and the messages it missed.
