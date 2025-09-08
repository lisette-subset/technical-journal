+++
date = '2025-09-07T19:39:22-04:00'
draft = false
title = '02_routing'
+++

# Routing Algorithms:

What do we mean by forwarding
- forwarding refers to transferring a packet from an incoming link to to an outgoing link through a **single** router

Routing:
- how routers work together to determine the correct/best routes/paths over which packets travel from source to destination nodes
- on the same domain, this routing is intradomain routing (IGPs, Interior Gateway Protocolss)
- on different router domains, this routing is intradomain routing


Two main classes of algorithms:
- link-state
- distance-vector

On the graph (for representating the algorithm):
- nodes are routers, edges have associated weights, which can represent:
    - length of the cable, time to traverse link, cost, link capacity
    - and current load on the link
        - weights are not static, they can change dynamically because it can depend on the load on the link
        - this can cause **pathological behavior** with **link-state **algorithms

## Zoom in Link State Routing Algorithms

### Dijikstra's Algorithm

$u$ - root node 
$v$ - any other non root node 
$D(v)$ - cost of the current **least cost path** from u to v
