---
layout: post
title:  Map of the agents
date:   2024-05-15
categories: valorant
excerpt: Visualising the similarities between agents
image: map-of-the-agents-3d.gif
---

## Intro
This experiment aims to visually represent the similarities between the different agents. The goal is to create a "map" in which:
- Similar agents are placed close together.
- Dissimilar agents are placed far apart.

Visualising these relationships may show:
- Existing patterns in agents' playstyles.
- Gaps in the current pool of agent designs.

## Project

### Methodology

Agents are represented as embeddings in a multidimensional space.

Agent similarity is measured based on their **covariance in pick rates across pro player careers**.
* High covariances occur when two agents are commonly chosen by the same players throughout their careers.
* Low covariances occur when two agents are rarely chosen by the same players.

To prevent outliers caused by agents with lesser usage, these covariances are then scaled by the agents' pick-rate.

The embeddings are iteratively updated using gradient descent - a loss function is employed which can be minimised by fitting the trend of the distances between agents' embeddings to their covariances.

## Results
The project supports N-dimensions, and is able to show the relationships between agents in a simple view, displaying player preferences and potential areas in which the game's agent roster could expand.

<table>
<td><img src="{{ site.baseurl }}/images/map-of-the-agents.png"/></td>
<td><img src="{{ site.baseurl }}/images/map-of-the-agents-3d.gif"/></td>
</table>
