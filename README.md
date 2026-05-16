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

Other foundational elements:

The in-memory data store - I would just recommend using Redis Time Series given it's features, which include
natively handing the aggregations. If we were thinking to use a basic data structure to build ourselves, then
we would probably use anything from Arrays through to B-Trees / B+ Trees through to Log-Structured Merge (LSM) Trees,
depending on how the data may present (regular vs interval) and if we wanted to optimise for reads, range queries or
higher volume inserts. But still, I would start with Redis.

Admin and related UI - this could be as simple as some HTML, CSS, JS, a small React generated front-end, or if a framework is used (e.g. Django for Python), then turnkey somethign from there.

Communication Considerations:

1. Message Signatures - a simple cert based scheme could suffice for now.
2. Rate Limiting - this is actually a bit more involved, as we need to consider what 'noisy' means. There are a few
   major patterns we might observe:
     a. Spamming for single/small number of meters
     b. Spamming for large number of meters
     c. Client regularly sending bad requests
     d. Client seemingly ignoring ACKs (and NACKs if implemented)
  We would probably have proxies downstream that could be instructed to send all traffic from that client to a null route.
  This does mean though we would need to have an implementation that is sensitive to any/all of the above patterns listed.
  We would also need to consider short-term client issues vs systemic longer-term client issues.

 

