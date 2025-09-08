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
p(v) - previous node along the current least cost path from u -> v (temp variable)
c(u,v) - the cost form u to directly attached neighbor v
N' - subset of nodes along the current least cost path from u to v
w - loop temp variable, least cost path from previous iteration of the loop

init step:
- initialize all currently known least cost paths from u to its direct neigbors
- we know what these costs are in the beginning because they are just the costs of the immediate links (known information even in a distributed algo)
- for nodes in the network that are NOT attached to u, the root, we initialize those cost paths to infinity
- finally, initialize the N' set to be just u (root source node)

Iterations:
- after the init step, we do this for each v in the network:
- we loook at set of nodes that are not in N'
- identify a w (node), not in N', with the last cost path from the previous iteration
- then we add that node w into N'. 
- for each neigbor of v (of w), we update D(v) (cost of the least cost path from u to v) with the new cost, 
    - which is the min of 
    the old cost from u to v 
    - or D(w) + c(w,v)
- at this step we're basically testing whether adding an edge will make the distance shorter. 

![alt text](image.png)