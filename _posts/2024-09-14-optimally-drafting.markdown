---
layout: post
title:  Optimally drafting
date:   2024-09-14
categories: league-of-legends
excerpt: Mathematically optimally drafting your champion
---
## Intro

The "draft" gamemode in *League of Legends* features a pre-game champion-selection step, in which the two teams "pick" (choose to play) and "ban" (remove from the choosable champion pool), with each player in the game having the opportunity to make one ban and one pick.

With each player on both teams having a pre-selected role, the draft phase can be treat as an adversarial one-vs-one problem, in which a player on each team aims to "counter-pick" the opposing player of the same role.

<!---
In this approach to the draft phase, picking prior to your adversary would only be optimal when the best choice
-->

In this approach to the draft phase, there exists two situations: counter-picking your opponent as you have the opportunity to pick after them, and "blindly" picking as your opponent has the opportunity to counter-pick you.

## Project

### Overview

The main aim of this project was to find the "safest" champion to blindly pick for each of the 5 roles. The safest choice would be the champion that has the greatest win-rate against its worst possible matchup. A champions worst possible matchup would be against the champion it has its second-lowest win-rate against, since the lowest win-rate champion can simply be banned by the blind-picker.

### Win-rate confidence

To adjust for the difference in magnitude of the sample size between different matchups, it is important to calculate confidence bounds for the win-rates between matchups.

<!---
TODO
-->
