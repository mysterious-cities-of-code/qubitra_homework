# qubitra_homework

This repo contains:

A folder with JSON Specs for the protocal between a client and server as partially detailed 
in the homework task. 

The homework has a lot missing detail, areas that require clarification and parts that could be improved
some design changes.

The decision was made to start from the foundation of the client server layer specs, and already has several
parts marked with comments for clarification, recommendation, or where an initial decision has been made.

The idea is that GitHub Copilot could be instructed to quickly deliver client and server implementations
against the specs, ideally once the marked comments have been discussed and resolved.

Other foundational elements.

The in-memory data store - I would just recommend using Redis Time Series given it's features, which include
natively handing the aggregations. If we were thinking to use a basic data structure to build ourselves, then
we would probably use 

