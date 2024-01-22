---
layout: page
permalink: /napkin_sketch/
title: Napkin Sketch
description: Inspiration and ideation yet to be demonstrated through prototypes
nav: true
nav_order: 3
---

## Physical Setup
- The game simulation server is expected to be a mid-high performance desktop computer running a Linux based OS.\
- Two or more external AI nodes are executing on single board computers (SBC).\
- The game simulation server and the AI nodes may or may not be in physical proximity to each other.\
- All devices are connected through high speed Ethernet, preferable 1Gbps.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/physical_configuration.png" title="Physical Configuration" class="img-fluid rounded z-depth-1" %}
    </div>

</div>

## Theory of Operation
- The AI nodes will implement a gRPC server that accepts a request from the simulation server. The request will contain structured data that defines the AI controlled units.
- When a gRPC update request is received, the AI node will process the data and calculate what moves the controlled units will make.
- The AI nodes will send a gRPC response the the simulation server with structured data that represents the AI's intentions.
- The game simulation server will then check the response for validity and resolve the game's turn.
- The process repeats until a team is eliminated or other pre-determined conditions are met.
- The game simulation server completes the game with a gRPC notification to the AI node with the match status and a move by move summary of the game.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/communications_flow.png" title="Communications Flow" class="img-fluid rounded z-depth-1" %}
    </div>

</div>