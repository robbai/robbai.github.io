---
layout: post
title:  Optimally drafting
date:   2024-09-14
categories: league-of-legends
excerpt: Mathematically optimally drafting your champion
image: optimally-drafting.png
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

The confidence bounds will be 2 standard deviations above and below the win-rate, where the upper win-rate will be used for the perspective of the opponent, and the lower win-rate will be used for our perspective.

By using confidence bounds when calculating the safety of a champion, we effectively penalise choosing champions who have a low pick-rate, as well as penalise champions would potentially have a bad matchup against a low pick-rate champion. On the other hand, for the opponent, these effects are reversed.

In essence, we assume the opponent has the better side of the odds, in order to maximise the safety of our pick against the influence of differing pick-rates between the different champions.

An important note is that the data source, [op.gg](https://www.op.gg/) uses a minimum pick-rate threshold of 0.5% per role, preventing extreme outliers from affecting the results of this project.

## Results

**Last update:** Patch 2025.S1.3

### Top

<details>
<summary>Click to view</summary>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-sett"></span> Sett</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.69% [51.6%-51.8%]</td>
	<td>719,334</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.74% [<b>46.8%</b>-48.6%]</td>
	<td>12,245</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.14% [<b>46.9%</b>-49.4%]</td>
	<td>6,377</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.84% [<b>47.0%</b>-48.7%]</td>
	<td>13,280</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.72% [<b>47.1%</b>-48.4%]</td>
	<td>22,409</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>48.43% [<b>47.1%</b>-49.8%]</td>
	<td>5,725</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.72% [47.1%-<b>48.4%</b>]</td>
	<td>22,409</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.74% [46.8%-<b>48.6%</b>]</td>
	<td>12,245</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.84% [47.0%-<b>48.7%</b>]</td>
	<td>13,280</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>48.58% [47.8%-<b>49.4%</b>]</td>
	<td>15,778</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.14% [46.9%-<b>49.4%</b>]</td>
	<td>6,377</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-urgot"></span> Urgot</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.41% [52.2%-52.6%]</td>
	<td>356,103</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>47.96% [<b>45.1%</b>-50.8%]</td>
	<td>1,203</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.92% [<b>46.9%</b>-49.0%]</td>
	<td>8,898</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>50.42% [<b>47.3%</b>-53.5%]</td>
	<td>1,053</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>48.58% [<b>47.4%</b>-49.7%]</td>
	<td>7,486</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.74% [<b>47.6%</b>-49.8%]</td>
	<td>8,254</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.92% [46.9%-<b>49.0%</b>]</td>
	<td>8,898</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>48.58% [47.4%-<b>49.7%</b>]</td>
	<td>7,486</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.74% [47.6%-<b>49.8%</b>]</td>
	<td>8,254</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>49.46% [48.8%-<b>50.2%</b>]</td>
	<td>19,902</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>47.96% [45.1%-<b>50.8%</b>]</td>
	<td>1,203</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-yorick"></span> Yorick</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.63% [52.5%-52.8%]</td>
	<td>434,051</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.73% [<b>44.1%</b>-49.3%]</td>
	<td>1,487</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.32% [<b>46.2%</b>-48.4%]</td>
	<td>7,939</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.73% [<b>46.6%</b>-48.8%]</td>
	<td>8,551</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.02% [<b>47.1%</b>-49.0%]</td>
	<td>10,709</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>48.39% [<b>47.4%</b>-49.4%]</td>
	<td>10,590</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.32% [46.2%-<b>48.4%</b>]</td>
	<td>7,939</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.73% [46.6%-<b>48.8%</b>]</td>
	<td>8,551</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.02% [47.1%-<b>49.0%</b>]</td>
	<td>10,709</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.73% [44.1%-<b>49.3%</b>]</td>
	<td>1,487</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>48.39% [47.4%-<b>49.4%</b>]</td>
	<td>10,590</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-cho-gath"></span> Cho'Gath</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.88% [51.7%-52.0%]</td>
	<td>464,595</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.60% [<b>44.7%</b>-46.5%]</td>
	<td>13,135</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.71% [<b>46.1%</b>-47.3%]</td>
	<td>25,678</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>49.09% [<b>46.4%</b>-51.7%]</td>
	<td>1,434</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>47.75% [<b>47.1%</b>-48.4%]</td>
	<td>22,769</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiora"></span> Fiora</td>
	<td>48.45% [<b>47.3%</b>-49.6%]</td>
	<td>7,589</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.60% [44.7%-<b>46.5%</b>]</td>
	<td>13,135</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.71% [46.1%-<b>47.3%</b>]</td>
	<td>25,678</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>47.75% [47.1%-<b>48.4%</b>]</td>
	<td>22,769</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>48.42% [47.3%-<b>49.5%</b>]</td>
	<td>8,281</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiora"></span> Fiora</td>
	<td>48.45% [47.3%-<b>49.6%</b>]</td>
	<td>7,589</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-garen"></span> Garen</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.07% [51.0%-51.2%]</td>
	<td>869,782</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>45.21% [<b>44.5%</b>-45.9%]</td>
	<td>21,780</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>46.66% [<b>45.9%</b>-47.4%]</td>
	<td>16,399</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.85% [<b>46.3%</b>-47.4%]</td>
	<td>30,960</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.37% [<b>46.3%</b>-48.4%]</td>
	<td>9,269</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.37% [<b>46.8%</b>-48.0%]</td>
	<td>26,693</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>45.21% [44.5%-<b>45.9%</b>]</td>
	<td>21,780</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.85% [46.3%-<b>47.4%</b>]</td>
	<td>30,960</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>46.66% [45.9%-<b>47.4%</b>]</td>
	<td>16,399</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.37% [46.8%-<b>48.0%</b>]</td>
	<td>26,693</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.52% [47.1%-<b>48.0%</b>]</td>
	<td>45,943</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-mordekaiser"></span> Mordekaiser</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.98% [51.9%-52.1%]</td>
	<td>817,123</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.92% [<b>45.7%</b>-48.1%]</td>
	<td>6,843</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.83% [<b>45.8%</b>-49.8%]</td>
	<td>2,452</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.46% [<b>46.3%</b>-48.7%]</td>
	<td>7,024</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.26% [<b>46.5%</b>-48.0%]</td>
	<td>19,042</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.82% [<b>46.7%</b>-48.9%]</td>
	<td>8,696</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.26% [46.5%-<b>48.0%</b>]</td>
	<td>19,042</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.92% [45.7%-<b>48.1%</b>]</td>
	<td>6,843</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.46% [46.3%-<b>48.7%</b>]</td>
	<td>7,024</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.82% [46.7%-<b>48.9%</b>]</td>
	<td>8,696</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>48.27% [47.4%-<b>49.1%</b>]</td>
	<td>14,671</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ornn"></span> Ornn</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.82% [50.6%-51.0%]</td>
	<td>295,184</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.61% [<b>44.7%</b>-50.5%]</td>
	<td>1,218</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>47.25% [<b>45.2%</b>-49.3%]</td>
	<td>2,480</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.22% [<b>46.5%</b>-48.0%]</td>
	<td>17,266</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.15% [<b>46.7%</b>-49.6%]</td>
	<td>4,479</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>50.48% [<b>47.0%</b>-54.0%]</td>
	<td>822</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.22% [46.5%-<b>48.0%</b>]</td>
	<td>17,266</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.33% [47.5%-<b>49.2%</b>]</td>
	<td>14,771</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>47.25% [45.2%-<b>49.3%</b>]</td>
	<td>2,480</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.15% [46.7%-<b>49.6%</b>]</td>
	<td>4,479</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.48% [47.2%-<b>49.7%</b>]</td>
	<td>6,367</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-kayle"></span> Kayle</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.25% [52.1%-52.4%]</td>
	<td>322,052</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.92% [<b>44.4%</b>-51.5%]</td>
	<td>795</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.41% [<b>45.2%</b>-51.6%]</td>
	<td>979</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.41% [<b>45.4%</b>-51.5%]</td>
	<td>1,072</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.09% [<b>45.7%</b>-48.4%]</td>
	<td>5,521</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.47% [<b>46.5%</b>-48.5%]</td>
	<td>10,248</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.09% [45.7%-<b>48.4%</b>]</td>
	<td>5,521</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.47% [46.5%-<b>48.5%</b>]</td>
	<td>10,248</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>48.04% [47.1%-<b>49.0%</b>]</td>
	<td>10,413</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.65% [47.6%-<b>49.7%</b>]</td>
	<td>8,598</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>48.90% [47.7%-<b>50.1%</b>]</td>
	<td>7,508</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-sion"></span> Sion</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.12% [49.9%-50.3%]</td>
	<td>311,650</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.57% [<b>45.0%</b>-48.2%]</td>
	<td>3,961</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.16% [<b>45.1%</b>-51.3%]</td>
	<td>1,038</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.38% [<b>45.4%</b>-47.4%]</td>
	<td>9,684</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>46.20% [<b>45.4%</b>-47.0%]</td>
	<td>14,646</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.88% [<b>45.7%</b>-48.1%]</td>
	<td>6,729</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>46.20% [45.4%-<b>47.0%</b>]</td>
	<td>14,646</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.55% [45.7%-<b>47.4%</b>]</td>
	<td>14,846</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.38% [45.4%-<b>47.4%</b>]</td>
	<td>9,684</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.88% [45.7%-<b>48.1%</b>]</td>
	<td>6,729</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.57% [45.0%-<b>48.2%</b>]</td>
	<td>3,961</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-teemo"></span> Teemo</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.03% [51.9%-52.2%]</td>
	<td>528,918</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.23% [<b>44.4%</b>-48.0%]</td>
	<td>3,015</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>45.60% [<b>44.7%</b>-46.5%]</td>
	<td>11,647</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.97% [<b>44.9%</b>-49.0%]</td>
	<td>2,399</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.25% [<b>45.5%</b>-47.0%]</td>
	<td>16,838</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.98% [<b>45.5%</b>-50.5%]</td>
	<td>1,636</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>45.60% [44.7%-<b>46.5%</b>]</td>
	<td>11,647</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.25% [45.5%-<b>47.0%</b>]</td>
	<td>16,838</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.23% [44.4%-<b>48.0%</b>]</td>
	<td>3,015</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.32% [46.6%-<b>48.1%</b>]</td>
	<td>16,961</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>47.40% [46.2%-<b>48.6%</b>]</td>
	<td>6,402</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-singed"></span> Singed</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.04% [51.8%-52.3%]</td>
	<td>149,244</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.91% [<b>42.7%</b>-49.1%]</td>
	<td>980</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>46.16% [<b>44.5%</b>-47.8%]</td>
	<td>3,812</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.38% [<b>44.8%</b>-50.0%]</td>
	<td>1,473</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.97% [<b>45.4%</b>-48.5%]</td>
	<td>4,285</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>49.23% [<b>45.5%</b>-53.0%]</td>
	<td>719</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>46.16% [44.5%-<b>47.8%</b>]</td>
	<td>3,812</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.97% [45.4%-<b>48.5%</b>]</td>
	<td>4,285</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.08% [45.5%-<b>48.6%</b>]</td>
	<td>4,146</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.57% [46.1%-<b>49.1%</b>]</td>
	<td>4,481</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.91% [42.7%-<b>49.1%</b>]</td>
	<td>980</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-shen"></span> Shen</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.91% [49.7%-50.1%]</td>
	<td>330,977</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.24% [<b>44.1%</b>-50.4%]</td>
	<td>1,016</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.25% [<b>44.5%</b>-46.0%]</td>
	<td>18,309</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.47% [<b>44.6%</b>-50.4%]</td>
	<td>1,190</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.44% [<b>44.6%</b>-46.2%]</td>
	<td>15,849</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.49% [<b>45.3%</b>-47.7%]</td>
	<td>6,742</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.25% [44.5%-<b>46.0%</b>]</td>
	<td>18,309</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.44% [44.6%-<b>46.2%</b>]</td>
	<td>15,849</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.49% [45.3%-<b>47.7%</b>]</td>
	<td>6,742</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.78% [45.6%-<b>48.0%</b>]</td>
	<td>7,267</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.92% [45.5%-<b>48.4%</b>]</td>
	<td>4,678</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-gnar"></span> Gnar</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.66% [49.5%-49.8%]</td>
	<td>294,953</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.91% [<b>44.0%</b>-45.8%]</td>
	<td>11,631</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.52% [<b>44.4%</b>-50.7%]</td>
	<td>1,012</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.89% [<b>44.5%</b>-51.3%]</td>
	<td>856</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.03% [<b>44.6%</b>-49.4%]</td>
	<td>1,722</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>46.18% [<b>45.0%</b>-47.3%]</td>
	<td>7,505</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.91% [44.0%-<b>45.8%</b>]</td>
	<td>11,631</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.17% [45.1%-<b>47.3%</b>]</td>
	<td>8,517</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>46.18% [45.0%-<b>47.3%</b>]</td>
	<td>7,505</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>46.40% [45.2%-<b>47.6%</b>]</td>
	<td>6,549</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.93% [45.8%-<b>48.1%</b>]</td>
	<td>7,378</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-dr--mundo"></span> Dr. Mundo</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.54% [51.4%-51.7%]</td>
	<td>363,491</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.10% [<b>43.3%</b>-48.9%]</td>
	<td>1,310</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>46.08% [<b>44.1%</b>-48.1%]</td>
	<td>2,415</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.18% [<b>44.2%</b>-46.2%]</td>
	<td>9,459</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.86% [<b>44.7%</b>-47.0%]</td>
	<td>7,971</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>46.71% [<b>45.4%</b>-48.0%]</td>
	<td>5,816</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.18% [44.2%-<b>46.2%</b>]</td>
	<td>9,459</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.86% [44.7%-<b>47.0%</b>]</td>
	<td>7,971</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>46.71% [45.4%-<b>48.0%</b>]</td>
	<td>5,816</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>46.08% [44.1%-<b>48.1%</b>]</td>
	<td>2,415</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aatrox"></span> Aatrox</td>
	<td>47.66% [46.7%-<b>48.6%</b>]</td>
	<td>12,045</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-aatrox"></span> Aatrox</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.61% [49.5%-49.7%]</td>
	<td>541,496</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.68% [<b>43.3%</b>-46.1%]</td>
	<td>4,836</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.38% [<b>43.8%</b>-46.9%]</td>
	<td>4,208</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.52% [<b>44.6%</b>-46.4%]</td>
	<td>12,601</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.99% [<b>44.9%</b>-47.0%]</td>
	<td>8,880</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.37% [<b>45.4%</b>-47.4%]</td>
	<td>10,240</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.68% [43.3%-<b>46.1%</b>]</td>
	<td>4,836</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.52% [44.6%-<b>46.4%</b>]</td>
	<td>12,601</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.38% [43.8%-<b>46.9%</b>]</td>
	<td>4,208</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.99% [44.9%-<b>47.0%</b>]</td>
	<td>8,880</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.37% [45.4%-<b>47.4%</b>]</td>
	<td>10,240</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-cassiopeia"></span> Cassiopeia</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.82% [50.5%-51.1%]</td>
	<td>108,446</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.48% [<b>42.4%</b>-50.5%]</td>
	<td>611</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.91% [<b>43.7%</b>-54.1%]</td>
	<td>370</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.06% [<b>44.0%</b>-48.1%]</td>
	<td>2,416</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.98% [<b>44.1%</b>-49.9%]</td>
	<td>1,194</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.49% [<b>44.7%</b>-48.3%]</td>
	<td>2,994</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.06% [44.0%-<b>48.1%</b>]</td>
	<td>2,416</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.49% [44.7%-<b>48.3%</b>]</td>
	<td>2,994</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.98% [45.5%-<b>48.4%</b>]</td>
	<td>4,614</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.06% [45.0%-<b>49.1%</b>]</td>
	<td>2,284</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>47.29% [45.2%-<b>49.4%</b>]</td>
	<td>2,180</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-jayce"></span> Jayce</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.29% [48.1%-48.4%]</td>
	<td>474,958</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.11% [<b>41.2%</b>-43.0%]</td>
	<td>11,615</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-olaf"></span> Olaf</td>
	<td>45.02% [<b>43.6%</b>-46.4%]</td>
	<td>4,893</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.67% [<b>43.7%</b>-45.7%]</td>
	<td>9,547</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.84% [<b>43.7%</b>-46.0%]</td>
	<td>7,923</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>44.64% [<b>43.8%</b>-45.4%]</td>
	<td>15,704</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.11% [41.2%-<b>43.0%</b>]</td>
	<td>11,615</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>44.64% [43.8%-<b>45.4%</b>]</td>
	<td>15,704</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.67% [43.7%-<b>45.7%</b>]</td>
	<td>9,547</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.79% [43.9%-<b>45.7%</b>]</td>
	<td>11,845</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.84% [43.7%-<b>46.0%</b>]</td>
	<td>7,923</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-darius"></span> Darius</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.61% [49.5%-49.7%]</td>
	<td>870,468</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.52% [<b>42.6%</b>-46.4%]</td>
	<td>2,675</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.10% [<b>43.4%</b>-44.8%]</td>
	<td>23,247</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.58% [<b>43.6%</b>-45.6%]</td>
	<td>10,052</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.27% [<b>43.7%</b>-44.9%]</td>
	<td>28,719</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.12% [<b>44.1%</b>-46.1%]</td>
	<td>9,780</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.10% [43.4%-<b>44.8%</b>]</td>
	<td>23,247</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.27% [43.7%-<b>44.9%</b>]</td>
	<td>28,719</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.58% [43.6%-<b>45.6%</b>]</td>
	<td>10,052</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.45% [44.8%-<b>46.1%</b>]</td>
	<td>24,787</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.12% [44.1%-<b>46.1%</b>]</td>
	<td>9,780</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-warwick"></span> Warwick</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.33% [52.1%-52.5%]</td>
	<td>260,673</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.19% [<b>42.2%</b>-46.2%]</td>
	<td>2,385</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.87% [<b>43.4%</b>-50.3%]</td>
	<td>849</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.68% [<b>43.5%</b>-51.9%]</td>
	<td>562</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.58% [<b>44.4%</b>-46.8%]</td>
	<td>7,046</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>47.00% [<b>44.4%</b>-49.6%]</td>
	<td>1,502</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.19% [42.2%-<b>46.2%</b>]</td>
	<td>2,385</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.58% [44.4%-<b>46.8%</b>]</td>
	<td>7,046</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.58% [45.0%-<b>48.2%</b>]</td>
	<td>3,986</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>47.48% [46.1%-<b>48.9%</b>]</td>
	<td>5,231</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>47.00% [44.4%-<b>49.6%</b>]</td>
	<td>1,502</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-nasus"></span> Nasus</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.10% [49.9%-50.3%]</td>
	<td>338,307</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.43% [<b>42.2%</b>-48.6%]</td>
	<td>964</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.57% [<b>43.4%</b>-45.7%]</td>
	<td>7,206</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.86% [<b>43.7%</b>-50.0%]</td>
	<td>990</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.63% [<b>43.9%</b>-51.4%]</td>
	<td>720</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>45.58% [<b>44.3%</b>-46.8%]</td>
	<td>6,408</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.57% [43.4%-<b>45.7%</b>]</td>
	<td>7,206</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.83% [45.1%-<b>46.5%</b>]</td>
	<td>21,231</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>45.58% [44.3%-<b>46.8%</b>]</td>
	<td>6,408</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.27% [45.2%-<b>47.4%</b>]</td>
	<td>8,489</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.42% [45.2%-<b>47.7%</b>]</td>
	<td>6,507</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-riven"></span> Riven</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.79% [49.6%-50.0%]</td>
	<td>324,155</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.52% [<b>43.2%</b>-45.8%]</td>
	<td>5,626</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.20% [<b>43.3%</b>-49.1%]</td>
	<td>1,199</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.90% [<b>43.7%</b>-46.1%]</td>
	<td>7,146</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.97% [<b>44.0%</b>-46.0%]</td>
	<td>9,843</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.91% [<b>44.2%</b>-45.6%]</td>
	<td>19,874</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.91% [44.2%-<b>45.6%</b>]</td>
	<td>19,874</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.52% [43.2%-<b>45.8%</b>]</td>
	<td>5,626</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.97% [44.0%-<b>46.0%</b>]</td>
	<td>9,843</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.90% [43.7%-<b>46.1%</b>]</td>
	<td>7,146</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.36% [45.1%-<b>47.6%</b>]</td>
	<td>6,635</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-irelia"></span> Irelia</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.09% [49.9%-50.3%]</td>
	<td>341,897</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>41.79% [<b>40.5%</b>-43.1%]</td>
	<td>6,061</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.01% [<b>43.3%</b>-48.7%]</td>
	<td>1,330</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.56% [<b>43.3%</b>-45.8%]</td>
	<td>6,263</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>45.54% [<b>43.4%</b>-47.7%]</td>
	<td>2,123</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>45.49% [<b>44.2%</b>-46.8%]</td>
	<td>6,166</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>41.79% [40.5%-<b>43.1%</b>]</td>
	<td>6,061</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.56% [43.3%-<b>45.8%</b>]</td>
	<td>6,263</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.25% [44.3%-<b>46.2%</b>]</td>
	<td>10,417</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.74% [45.0%-<b>46.5%</b>]</td>
	<td>16,344</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>45.49% [44.2%-<b>46.8%</b>]</td>
	<td>6,166</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-trundle"></span> Trundle</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.80% [50.6%-51.0%]</td>
	<td>337,911</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.96% [<b>41.8%</b>-48.1%]</td>
	<td>974</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.21% [<b>43.3%</b>-45.2%]</td>
	<td>10,921</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>47.47% [<b>44.2%</b>-50.7%]</td>
	<td>931</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.61% [<b>44.8%</b>-48.4%]</td>
	<td>3,087</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.04% [<b>45.2%</b>-48.9%]</td>
	<td>3,025</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.21% [43.3%-<b>45.2%</b>]</td>
	<td>10,921</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.96% [41.8%-<b>48.1%</b>]</td>
	<td>974</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.06% [45.8%-<b>48.3%</b>]</td>
	<td>6,111</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>47.30% [46.2%-<b>48.4%</b>]</td>
	<td>8,635</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.61% [44.8%-<b>48.4%</b>]</td>
	<td>3,087</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-heimerdinger"></span> Heimerdinger</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.77% [51.5%-52.0%]</td>
	<td>159,571</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.82% [<b>43.0%</b>-46.6%]</td>
	<td>2,998</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.65% [<b>43.2%</b>-46.1%]</td>
	<td>4,882</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.33% [<b>44.2%</b>-50.5%]</td>
	<td>993</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.74% [<b>44.2%</b>-53.3%]</td>
	<td>478</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-smolder"></span> Smolder</td>
	<td>48.66% [<b>44.8%</b>-52.5%]</td>
	<td>676</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.65% [43.2%-<b>46.1%</b>]</td>
	<td>4,882</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.82% [43.0%-<b>46.6%</b>]</td>
	<td>2,998</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.81% [45.1%-<b>48.5%</b>]</td>
	<td>3,433</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>47.00% [45.1%-<b>48.9%</b>]</td>
	<td>2,804</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>47.33% [45.5%-<b>49.1%</b>]</td>
	<td>3,101</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-maokai"></span> Maokai</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.20% [50.0%-50.4%]</td>
	<td>178,008</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.01% [<b>40.9%</b>-43.1%]</td>
	<td>8,438</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.94% [<b>43.2%</b>-46.7%]</td>
	<td>3,244</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.72% [<b>44.3%</b>-47.2%]</td>
	<td>4,748</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>47.37% [<b>44.4%</b>-50.4%]</td>
	<td>1,104</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.04% [<b>44.4%</b>-51.7%]</td>
	<td>766</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.01% [40.9%-<b>43.1%</b>]</td>
	<td>8,438</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.94% [43.2%-<b>46.7%</b>]</td>
	<td>3,244</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.72% [44.3%-<b>47.2%</b>]</td>
	<td>4,748</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.21% [44.5%-<b>47.9%</b>]</td>
	<td>3,551</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.34% [44.8%-<b>47.9%</b>]</td>
	<td>3,953</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-volibear"></span> Volibear</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.60% [50.4%-50.8%]</td>
	<td>375,560</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>42.72% [<b>41.7%</b>-43.7%]</td>
	<td>10,322</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>45.58% [<b>43.0%</b>-48.1%]</td>
	<td>1,516</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.62% [<b>43.4%</b>-45.9%]</td>
	<td>6,497</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.22% [<b>44.4%</b>-48.1%]</td>
	<td>2,938</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>48.68% [<b>45.4%</b>-51.9%]</td>
	<td>951</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>42.72% [41.7%-<b>43.7%</b>]</td>
	<td>10,322</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.62% [43.4%-<b>45.9%</b>]</td>
	<td>6,497</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>46.62% [45.5%-<b>47.7%</b>]</td>
	<td>8,468</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gnar"></span> Gnar</td>
	<td>46.77% [45.5%-<b>48.0%</b>]</td>
	<td>6,632</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.22% [44.4%-<b>48.1%</b>]</td>
	<td>2,938</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-tryndamere"></span> Tryndamere</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.93% [49.7%-50.1%]</td>
	<td>249,490</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.90% [<b>42.9%</b>-44.9%]</td>
	<td>9,858</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.46% [<b>43.0%</b>-45.9%]</td>
	<td>4,739</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.54% [<b>43.4%</b>-45.7%]</td>
	<td>7,566</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.07% [<b>43.9%</b>-52.3%]</td>
	<td>570</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>48.22% [<b>44.1%</b>-52.3%]</td>
	<td>593</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.90% [42.9%-<b>44.9%</b>]</td>
	<td>9,858</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.54% [43.4%-<b>45.7%</b>]</td>
	<td>7,566</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.46% [43.0%-<b>45.9%</b>]</td>
	<td>4,739</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.23% [44.8%-<b>47.7%</b>]</td>
	<td>4,659</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.66% [45.3%-<b>48.0%</b>]</td>
	<td>5,578</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-renekton"></span> Renekton</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.34% [49.2%-49.5%]</td>
	<td>386,034</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.20% [<b>42.2%</b>-44.2%]</td>
	<td>10,378</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.91% [<b>42.8%</b>-45.0%]</td>
	<td>8,166</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.13% [<b>42.9%</b>-47.3%]</td>
	<td>2,045</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.72% [<b>43.5%</b>-46.0%]</td>
	<td>6,410</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.31% [<b>44.1%</b>-46.5%]</td>
	<td>6,722</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.20% [42.2%-<b>44.2%</b>]</td>
	<td>10,378</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.91% [42.8%-<b>45.0%</b>]</td>
	<td>8,166</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.72% [43.5%-<b>46.0%</b>]</td>
	<td>6,410</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.31% [44.1%-<b>46.5%</b>]</td>
	<td>6,722</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.20% [45.5%-<b>46.9%</b>]</td>
	<td>17,995</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-malphite"></span> Malphite</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.77% [50.6%-50.9%]</td>
	<td>447,177</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.60% [<b>41.7%</b>-43.5%]</td>
	<td>12,013</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.54% [<b>42.8%</b>-48.3%]</td>
	<td>1,313</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.95% [<b>43.0%</b>-44.9%]</td>
	<td>10,514</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.55% [<b>43.0%</b>-48.1%]</td>
	<td>1,563</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>44.82% [<b>43.4%</b>-46.2%]</td>
	<td>4,964</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.60% [41.7%-<b>43.5%</b>]</td>
	<td>12,013</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.95% [43.0%-<b>44.9%</b>]</td>
	<td>10,514</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.28% [43.6%-<b>45.0%</b>]</td>
	<td>20,195</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.59% [43.5%-<b>45.7%</b>]</td>
	<td>7,729</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.63% [43.5%-<b>45.8%</b>]</td>
	<td>7,191</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-tahm-kench"></span> Tahm Kench</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.00% [49.8%-50.2%]</td>
	<td>288,327</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.25% [<b>39.4%</b>-43.1%]</td>
	<td>2,727</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.25% [<b>42.7%</b>-49.8%]</td>
	<td>800</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.32% [<b>43.1%</b>-45.5%]</td>
	<td>7,160</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.36% [<b>44.1%</b>-46.6%]</td>
	<td>6,097</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.41% [<b>44.3%</b>-48.5%]</td>
	<td>2,344</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.25% [39.4%-<b>43.1%</b>]</td>
	<td>2,727</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.32% [43.1%-<b>45.5%</b>]</td>
	<td>7,160</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.36% [44.1%-<b>46.6%</b>]</td>
	<td>6,097</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.97% [45.2%-<b>46.7%</b>]</td>
	<td>17,150</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.74% [44.6%-<b>46.9%</b>]</td>
	<td>7,864</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-gangplank"></span> Gangplank</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.28% [48.1%-48.5%]</td>
	<td>220,890</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.63% [<b>42.3%</b>-45.0%]</td>
	<td>5,537</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.96% [<b>42.6%</b>-45.3%]</td>
	<td>5,140</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.08% [<b>43.0%</b>-45.1%]</td>
	<td>9,150</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.79% [<b>43.3%</b>-46.3%]</td>
	<td>4,460</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>45.06% [<b>43.5%</b>-46.6%]</td>
	<td>4,074</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.63% [42.3%-<b>45.0%</b>]</td>
	<td>5,537</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.08% [43.0%-<b>45.1%</b>]</td>
	<td>9,150</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.96% [42.6%-<b>45.3%</b>]</td>
	<td>5,140</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.79% [43.3%-<b>46.3%</b>]</td>
	<td>4,460</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>45.06% [43.5%-<b>46.6%</b>]</td>
	<td>4,074</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-pantheon"></span> Pantheon</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.60% [49.4%-49.8%]</td>
	<td>201,059</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>44.07% [<b>41.9%</b>-46.3%]</td>
	<td>2,024</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.83% [<b>42.4%</b>-45.3%]</td>
	<td>4,594</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.44% [<b>42.4%</b>-50.5%]</td>
	<td>618</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.82% [<b>42.5%</b>-47.2%]</td>
	<td>1,769</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.58% [<b>43.2%</b>-45.9%]</td>
	<td>5,562</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.83% [42.4%-<b>45.3%</b>]</td>
	<td>4,594</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.58% [43.2%-<b>45.9%</b>]</td>
	<td>5,562</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>44.07% [41.9%-<b>46.3%</b>]</td>
	<td>2,024</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.65% [44.2%-<b>47.1%</b>]</td>
	<td>4,849</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>45.49% [43.9%-<b>47.1%</b>]</td>
	<td>3,917</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ambessa"></span> Ambessa</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.88% [47.7%-48.0%]</td>
	<td>371,872</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>41.51% [<b>40.4%</b>-42.6%]</td>
	<td>7,488</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.15% [<b>42.2%</b>-44.1%]</td>
	<td>9,975</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.55% [<b>42.3%</b>-44.8%]</td>
	<td>6,675</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>45.46% [<b>43.6%</b>-47.3%]</td>
	<td>2,822</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.09% [<b>43.9%</b>-48.3%]</td>
	<td>2,063</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>41.51% [40.4%-<b>42.6%</b>]</td>
	<td>7,488</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.15% [42.2%-<b>44.1%</b>]</td>
	<td>9,975</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.55% [42.3%-<b>44.8%</b>]</td>
	<td>6,675</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.01% [44.2%-<b>45.8%</b>]</td>
	<td>15,561</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>45.11% [44.0%-<b>46.2%</b>]</td>
	<td>8,412</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-yone"></span> Yone</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.78% [47.6%-47.9%]</td>
	<td>438,842</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>43.59% [<b>41.7%</b>-45.5%]</td>
	<td>2,661</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.35% [<b>42.1%</b>-44.6%]</td>
	<td>6,656</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-riven"></span> Riven</td>
	<td>43.39% [<b>42.3%</b>-44.5%]</td>
	<td>8,610</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>43.95% [<b>42.9%</b>-45.0%]</td>
	<td>9,794</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.76% [<b>43.4%</b>-48.2%]</td>
	<td>1,724</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-riven"></span> Riven</td>
	<td>43.39% [42.3%-<b>44.5%</b>]</td>
	<td>8,610</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.35% [42.1%-<b>44.6%</b>]</td>
	<td>6,656</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>44.23% [43.5%-<b>44.9%</b>]</td>
	<td>19,666</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>43.95% [42.9%-<b>45.0%</b>]</td>
	<td>9,794</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.79% [44.1%-<b>45.5%</b>]</td>
	<td>21,615</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-camille"></span> Camille</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.68% [49.5%-49.9%]</td>
	<td>195,681</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>44.97% [<b>41.8%</b>-48.2%]</td>
	<td>965</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.47% [<b>42.1%</b>-50.8%]</td>
	<td>525</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.71% [<b>42.2%</b>-45.2%]</td>
	<td>4,417</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.46% [<b>42.7%</b>-48.2%]</td>
	<td>1,300</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.76% [<b>43.0%</b>-46.6%]</td>
	<td>3,067</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.71% [42.2%-<b>45.2%</b>]</td>
	<td>4,417</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.22% [44.1%-<b>46.3%</b>]</td>
	<td>8,003</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.76% [43.0%-<b>46.6%</b>]</td>
	<td>3,067</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.32% [43.6%-<b>47.1%</b>]</td>
	<td>3,228</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.98% [44.6%-<b>47.4%</b>]</td>
	<td>4,875</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-malzahar"></span> Malzahar</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.76% [51.3%-52.2%]</td>
	<td>54,580</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>46.91% [<b>41.4%</b>-52.5%]</td>
	<td>324</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.58% [<b>42.0%</b>-51.2%]</td>
	<td>468</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>45.85% [<b>42.0%</b>-49.7%]</td>
	<td>687</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>46.26% [<b>42.1%</b>-50.5%]</td>
	<td>562</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>45.13% [<b>42.1%</b>-48.2%]</td>
	<td>1,068</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>45.13% [42.1%-<b>48.2%</b>]</td>
	<td>1,068</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.97% [44.3%-<b>49.6%</b>]</td>
	<td>1,439</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>45.85% [42.0%-<b>49.7%</b>]</td>
	<td>687</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>46.26% [42.1%-<b>50.5%</b>]</td>
	<td>562</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>48.45% [45.9%-<b>51.0%</b>]</td>
	<td>1,550</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-poppy"></span> Poppy</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.83% [49.5%-50.1%]</td>
	<td>104,806</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.88% [<b>39.6%</b>-52.1%]</td>
	<td>255</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.15% [<b>41.2%</b>-49.1%]</td>
	<td>640</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.80% [<b>42.3%</b>-47.3%]</td>
	<td>1,589</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.57% [<b>42.4%</b>-46.7%]</td>
	<td>2,100</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-smolder"></span> Smolder</td>
	<td>48.90% [<b>42.9%</b>-54.9%]</td>
	<td>274</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.57% [42.4%-<b>46.7%</b>]</td>
	<td>2,100</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.80% [42.3%-<b>47.3%</b>]</td>
	<td>1,589</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.24% [44.8%-<b>47.7%</b>]</td>
	<td>4,961</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>46.10% [44.5%-<b>47.7%</b>]</td>
	<td>4,095</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.94% [43.9%-<b>48.0%</b>]</td>
	<td>2,307</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-fiora"></span> Fiora</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.17% [49.0%-49.4%]</td>
	<td>243,426</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.06% [<b>38.2%</b>-45.9%]</td>
	<td>649</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>42.56% [<b>41.1%</b>-44.0%]</td>
	<td>4,635</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.77% [<b>41.5%</b>-46.1%]</td>
	<td>1,880</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.78% [<b>43.0%</b>-48.6%]</td>
	<td>1,258</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.54% [<b>43.0%</b>-46.1%]</td>
	<td>4,124</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>42.56% [41.1%-<b>44.0%</b>]</td>
	<td>4,635</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.06% [38.2%-<b>45.9%</b>]</td>
	<td>649</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.77% [41.5%-<b>46.1%</b>]</td>
	<td>1,880</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.54% [43.0%-<b>46.1%</b>]</td>
	<td>4,124</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.29% [44.3%-<b>46.3%</b>]</td>
	<td>10,544</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-olaf"></span> Olaf</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.14% [48.8%-49.4%]</td>
	<td>118,569</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>43.79% [<b>40.4%</b>-47.1%]</td>
	<td>879</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>44.87% [<b>41.0%</b>-48.8%]</td>
	<td>644</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>43.20% [<b>41.3%</b>-45.1%]</td>
	<td>2,625</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-akali"></span> Akali</td>
	<td>45.23% [<b>41.5%</b>-49.0%]</td>
	<td>714</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.95% [<b>41.9%</b>-54.0%]</td>
	<td>269</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>43.20% [41.3%-<b>45.1%</b>]</td>
	<td>2,625</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.78% [43.2%-<b>46.4%</b>]</td>
	<td>3,919</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.22% [42.0%-<b>46.5%</b>]</td>
	<td>1,983</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.10% [43.6%-<b>46.6%</b>]</td>
	<td>4,332</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.78% [42.6%-<b>47.0%</b>]</td>
	<td>2,023</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-jax"></span> Jax</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.74% [47.6%-47.9%]</td>
	<td>408,469</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.25% [<b>40.2%</b>-42.3%]</td>
	<td>8,710</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>41.88% [<b>40.8%</b>-43.0%]</td>
	<td>8,159</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>42.79% [<b>41.2%</b>-44.4%]</td>
	<td>3,650</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>41.92% [<b>41.3%</b>-42.5%]</td>
	<td>26,125</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.67% [<b>41.7%</b>-43.6%]</td>
	<td>10,539</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.25% [40.2%-<b>42.3%</b>]</td>
	<td>8,710</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>41.92% [41.3%-<b>42.5%</b>]</td>
	<td>26,125</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>41.88% [40.8%-<b>43.0%</b>]</td>
	<td>8,159</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.67% [41.7%-<b>43.6%</b>]</td>
	<td>10,539</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>42.79% [41.2%-<b>44.4%</b>]</td>
	<td>3,650</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-kled"></span> Kled</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.35% [50.1%-50.6%]</td>
	<td>115,552</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>42.68% [<b>39.7%</b>-45.7%]</td>
	<td>1,080</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.03% [<b>40.8%</b>-47.3%]</td>
	<td>931</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.89% [<b>42.0%</b>-49.8%]</td>
	<td>658</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.42% [<b>43.1%</b>-51.7%]</td>
	<td>544</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.83% [<b>43.4%</b>-54.2%]</td>
	<td>344</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>42.68% [39.7%-<b>45.7%</b>]</td>
	<td>1,080</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.03% [40.8%-<b>47.3%</b>]</td>
	<td>931</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.52% [43.7%-<b>47.4%</b>]</td>
	<td>2,913</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.40% [44.3%-<b>48.5%</b>]</td>
	<td>2,269</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.90% [44.7%-<b>49.1%</b>]</td>
	<td>2,053</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-gragas"></span> Gragas</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.07% [48.9%-49.3%]</td>
	<td>207,009</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.05% [<b>40.7%</b>-47.4%]</td>
	<td>867</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.27% [<b>40.8%</b>-45.8%]</td>
	<td>1,555</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.35% [<b>41.2%</b>-49.5%]</td>
	<td>571</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.69% [<b>42.2%</b>-45.2%]</td>
	<td>4,275</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.81% [<b>42.4%</b>-47.3%]</td>
	<td>1,660</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.77% [42.4%-<b>45.1%</b>]</td>
	<td>5,562</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.69% [42.2%-<b>45.2%</b>]</td>
	<td>4,275</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.27% [40.8%-<b>45.8%</b>]</td>
	<td>1,555</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.81% [42.4%-<b>47.3%</b>]</td>
	<td>1,660</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.05% [40.7%-<b>47.4%</b>]</td>
	<td>867</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-vladimir"></span> Vladimir</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.57% [48.4%-48.8%]</td>
	<td>214,376</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.22% [<b>39.8%</b>-42.6%]</td>
	<td>5,143</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>43.52% [<b>40.8%</b>-46.3%]</td>
	<td>1,282</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.15% [<b>41.2%</b>-47.1%]</td>
	<td>1,146</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.65% [<b>43.2%</b>-46.1%]</td>
	<td>4,562</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.57% [<b>43.3%</b>-49.9%]</td>
	<td>906</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.22% [39.8%-<b>42.6%</b>]</td>
	<td>5,143</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.79% [43.5%-<b>46.1%</b>]</td>
	<td>5,954</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.65% [43.2%-<b>46.1%</b>]</td>
	<td>4,562</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>43.52% [40.8%-<b>46.3%</b>]</td>
	<td>1,282</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.45% [44.4%-<b>46.5%</b>]</td>
	<td>9,218</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-yasuo"></span> Yasuo</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.80% [47.6%-48.0%]</td>
	<td>199,710</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>43.70% [<b>40.6%</b>-46.8%]</td>
	<td>1,032</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.56% [<b>40.6%</b>-48.5%]</td>
	<td>635</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>44.14% [<b>41.2%</b>-47.1%]</td>
	<td>1,135</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>43.57% [<b>41.6%</b>-45.5%]</td>
	<td>2,538</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.02% [<b>42.1%</b>-45.9%]</td>
	<td>2,651</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>43.25% [42.2%-<b>44.3%</b>]</td>
	<td>9,495</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>43.51% [42.4%-<b>44.6%</b>]</td>
	<td>8,159</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>44.00% [42.7%-<b>45.3%</b>]</td>
	<td>6,034</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>43.57% [41.6%-<b>45.5%</b>]</td>
	<td>2,538</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.59% [43.6%-<b>45.6%</b>]</td>
	<td>9,550</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-kennen"></span> Kennen</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.62% [49.3%-49.9%]</td>
	<td>126,974</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.51% [<b>38.7%</b>-48.3%]</td>
	<td>432</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.38% [<b>40.5%</b>-44.2%]</td>
	<td>2,857</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.11% [<b>41.1%</b>-49.1%]</td>
	<td>614</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.31% [<b>41.3%</b>-45.3%]</td>
	<td>2,544</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.93% [<b>41.9%</b>-48.0%]</td>
	<td>1,066</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.38% [40.5%-<b>44.2%</b>]</td>
	<td>2,857</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.31% [41.3%-<b>45.3%</b>]</td>
	<td>2,544</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.29% [42.3%-<b>46.2%</b>]</td>
	<td>2,592</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.56% [42.8%-<b>46.4%</b>]</td>
	<td>3,020</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.60% [42.4%-<b>46.8%</b>]</td>
	<td>2,121</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ryze"></span> Ryze</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.06% [50.7%-51.5%]</td>
	<td>60,445</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>45.88% [<b>39.6%</b>-52.1%]</td>
	<td>255</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>44.21% [<b>40.4%</b>-48.1%]</td>
	<td>665</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.47% [<b>40.4%</b>-46.5%]</td>
	<td>1,058</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.65% [<b>40.7%</b>-50.6%]</td>
	<td>403</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.13% [<b>42.3%</b>-53.9%]</td>
	<td>295</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.47% [40.4%-<b>46.5%</b>]</td>
	<td>1,058</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>44.21% [40.4%-<b>48.1%</b>]</td>
	<td>665</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.41% [42.6%-<b>48.2%</b>]</td>
	<td>1,253</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>46.02% [43.2%-<b>48.8%</b>]</td>
	<td>1,295</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>46.06% [42.9%-<b>49.2%</b>]</td>
	<td>990</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-rumble"></span> Rumble</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.75% [47.5%-48.0%]</td>
	<td>130,507</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.20% [<b>40.0%</b>-48.4%]</td>
	<td>552</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.94% [<b>40.1%</b>-45.8%]</td>
	<td>1,241</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.58% [<b>40.4%</b>-46.7%]</td>
	<td>998</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.56% [<b>41.6%</b>-47.6%]</td>
	<td>1,104</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.81% [<b>42.0%</b>-45.6%]</td>
	<td>2,919</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.81% [42.0%-<b>45.6%</b>]</td>
	<td>2,919</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.94% [40.1%-<b>45.8%</b>]</td>
	<td>1,241</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.66% [43.3%-<b>46.0%</b>]</td>
	<td>5,487</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.34% [42.3%-<b>46.4%</b>]</td>
	<td>2,336</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.04% [43.6%-<b>46.5%</b>]</td>
	<td>4,620</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-quinn"></span> Quinn</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.78% [48.4%-49.1%]</td>
	<td>79,975</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>44.52% [<b>38.7%</b>-50.3%]</td>
	<td>292</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>43.46% [<b>39.9%</b>-47.0%]</td>
	<td>773</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>44.29% [<b>40.4%</b>-48.1%]</td>
	<td>666</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.31% [<b>40.7%</b>-43.9%]</td>
	<td>3,746</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.01% [<b>40.7%</b>-45.3%]</td>
	<td>1,904</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.31% [40.7%-<b>43.9%</b>]</td>
	<td>3,746</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.01% [40.7%-<b>45.3%</b>]</td>
	<td>1,904</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.70% [41.2%-<b>46.2%</b>]</td>
	<td>1,556</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.66% [42.9%-<b>46.4%</b>]</td>
	<td>3,282</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.15% [41.9%-<b>46.4%</b>]</td>
	<td>1,932</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-zac"></span> Zac</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.20% [50.8%-51.6%]</td>
	<td>59,506</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>42.35% [<b>39.0%</b>-45.7%]</td>
	<td>876</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.25% [<b>39.8%</b>-54.7%]</td>
	<td>182</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>47.22% [<b>40.4%</b>-54.0%]</td>
	<td>216</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.50% [<b>41.1%</b>-49.9%]</td>
	<td>523</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.40% [<b>42.6%</b>-48.2%]</td>
	<td>1,229</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>42.35% [39.0%-<b>45.7%</b>]</td>
	<td>876</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.86% [43.8%-<b>47.9%</b>]</td>
	<td>2,333</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.40% [42.6%-<b>48.2%</b>]</td>
	<td>1,229</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.01% [45.1%-<b>48.9%</b>]</td>
	<td>2,869</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.50% [41.1%-<b>49.9%</b>]</td>
	<td>523</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-illaoi"></span> Illaoi</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.78% [50.6%-51.0%]</td>
	<td>326,747</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>39.25% [<b>36.2%</b>-42.3%]</td>
	<td>1,042</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>43.21% [<b>39.8%</b>-46.6%]</td>
	<td>840</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.52% [<b>41.5%</b>-43.5%]</td>
	<td>9,402</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.28% [<b>41.7%</b>-44.9%]</td>
	<td>3,738</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>42.96% [<b>41.8%</b>-44.2%]</td>
	<td>6,917</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>39.25% [36.2%-<b>42.3%</b>]</td>
	<td>1,042</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.52% [41.5%-<b>43.5%</b>]</td>
	<td>9,402</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>42.96% [41.8%-<b>44.2%</b>]</td>
	<td>6,917</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.16% [42.2%-<b>44.2%</b>]</td>
	<td>9,962</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.54% [42.8%-<b>44.2%</b>]</td>
	<td>20,368</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-akali"></span> Akali</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.25% [48.0%-48.5%]</td>
	<td>121,492</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.03% [<b>39.4%</b>-48.7%]</td>
	<td>461</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.20% [<b>39.8%</b>-48.6%]</td>
	<td>500</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>44.20% [<b>40.6%</b>-47.8%]</td>
	<td>776</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>43.39% [<b>40.8%</b>-46.0%]</td>
	<td>1,438</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.02% [<b>41.1%</b>-45.0%]</td>
	<td>2,608</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.02% [41.1%-<b>45.0%</b>]</td>
	<td>2,608</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.66% [41.7%-<b>45.6%</b>]</td>
	<td>2,567</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>43.63% [41.4%-<b>45.8%</b>]</td>
	<td>2,065</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>43.39% [40.8%-<b>46.0%</b>]</td>
	<td>1,438</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.88% [42.8%-<b>47.0%</b>]</td>
	<td>2,270</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-vayne"></span> Vayne</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.53% [50.2%-50.8%]</td>
	<td>124,078</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>39.47% [<b>35.4%</b>-43.5%]</td>
	<td>575</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>40.96% [<b>39.5%</b>-42.4%]</td>
	<td>4,677</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>41.67% [<b>40.1%</b>-43.2%]</td>
	<td>4,103</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.61% [<b>40.6%</b>-50.7%]</td>
	<td>388</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.92% [<b>41.2%</b>-50.7%]</td>
	<td>442</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>40.96% [39.5%-<b>42.4%</b>]</td>
	<td>4,677</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>41.67% [40.1%-<b>43.2%</b>]</td>
	<td>4,103</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>39.47% [35.4%-<b>43.5%</b>]</td>
	<td>575</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.48% [43.5%-<b>47.4%</b>]</td>
	<td>2,568</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.01% [42.3%-<b>47.7%</b>]</td>
	<td>1,395</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-wukong"></span> Wukong</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.77% [50.5%-51.1%]</td>
	<td>99,171</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.98% [<b>37.9%</b>-50.1%]</td>
	<td>266</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.27% [<b>39.5%</b>-51.1%]</td>
	<td>296</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.41% [<b>41.7%</b>-49.1%]</td>
	<td>709</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.50% [<b>41.7%</b>-49.3%]</td>
	<td>690</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>47.23% [<b>42.7%</b>-51.7%]</td>
	<td>489</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.69% [43.1%-<b>46.3%</b>]</td>
	<td>3,788</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.28% [44.3%-<b>48.2%</b>]</td>
	<td>2,584</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.83% [43.2%-<b>48.4%</b>]</td>
	<td>1,488</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.93% [45.0%-<b>48.9%</b>]</td>
	<td>2,678</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.41% [41.7%-<b>49.1%</b>]</td>
	<td>709</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-gwen"></span> Gwen</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.44% [48.2%-48.7%]</td>
	<td>213,399</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.44% [<b>38.4%</b>-46.5%]</td>
	<td>596</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.34% [<b>38.9%</b>-43.8%]</td>
	<td>1,664</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>41.55% [<b>39.2%</b>-43.9%]</td>
	<td>1,776</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>44.02% [<b>40.1%</b>-48.0%]</td>
	<td>636</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>41.94% [<b>40.3%</b>-43.5%]</td>
	<td>3,800</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>41.94% [40.3%-<b>43.5%</b>]</td>
	<td>3,800</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.34% [38.9%-<b>43.8%</b>]</td>
	<td>1,664</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>41.55% [39.2%-<b>43.9%</b>]</td>
	<td>1,776</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.33% [43.4%-<b>45.3%</b>]</td>
	<td>10,306</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.33% [43.0%-<b>45.7%</b>]</td>
	<td>5,370</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-k-sante"></span> K'Sante</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>46.38% [46.2%-46.5%]</td>
	<td>384,362</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>38.55% [<b>37.5%</b>-39.6%]</td>
	<td>8,341</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>40.14% [<b>38.5%</b>-41.8%]</td>
	<td>3,702</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.44% [<b>39.2%</b>-45.7%]</td>
	<td>933</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.82% [<b>40.7%</b>-42.9%]</td>
	<td>7,840</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.71% [<b>40.8%</b>-44.6%]</td>
	<td>2,788</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>38.55% [37.5%-<b>39.6%</b>]</td>
	<td>8,341</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>40.14% [38.5%-<b>41.8%</b>]</td>
	<td>3,702</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.82% [40.7%-<b>42.9%</b>]</td>
	<td>7,840</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.57% [41.5%-<b>43.7%</b>]</td>
	<td>8,023</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.20% [42.5%-<b>43.9%</b>]</td>
	<td>21,938</td>
</tr>
</table>

</details>
### Jungle

<details>
<summary>Click to view</summary>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-briar"></span> Briar</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.51% [52.4%-52.7%]</td>
	<td>430,501</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>49.07% [<b>46.3%</b>-51.8%]</td>
	<td>1,294</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>50.41% [<b>48.0%</b>-52.9%]</td>
	<td>1,678</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.91% [<b>48.3%</b>-49.6%]</td>
	<td>23,349</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>50.33% [<b>48.3%</b>-52.3%]</td>
	<td>2,501</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>50.11% [<b>48.4%</b>-51.8%]</td>
	<td>3,592</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.91% [48.3%-<b>49.6%</b>]</td>
	<td>23,349</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>49.34% [48.6%-<b>50.1%</b>]</td>
	<td>19,394</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.62% [48.9%-<b>50.3%</b>]</td>
	<td>21,392</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>49.79% [48.8%-<b>50.8%</b>]</td>
	<td>9,620</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>50.21% [49.5%-<b>50.9%</b>]</td>
	<td>21,639</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-nocturne"></span> Nocturne</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.24% [52.1%-52.3%]</td>
	<td>906,453</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.84% [<b>47.2%</b>-50.5%]</td>
	<td>3,585</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>49.19% [<b>47.2%</b>-51.2%]</td>
	<td>2,596</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>49.11% [<b>48.2%</b>-50.1%]</td>
	<td>11,284</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>48.88% [<b>48.4%</b>-49.4%]</td>
	<td>43,765</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>50.64% [<b>48.8%</b>-52.5%]</td>
	<td>2,887</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>48.88% [48.4%-<b>49.4%</b>]</td>
	<td>43,765</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>49.11% [48.2%-<b>50.1%</b>]</td>
	<td>11,284</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.62% [49.1%-<b>50.1%</b>]</td>
	<td>44,323</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.84% [47.2%-<b>50.5%</b>]</td>
	<td>3,585</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>50.21% [49.8%-<b>50.7%</b>]</td>
	<td>49,633</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-warwick"></span> Warwick</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.13% [52.0%-52.2%]</td>
	<td>724,923</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.91% [<b>45.8%</b>-50.0%]</td>
	<td>2,300</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.18% [<b>46.6%</b>-49.8%]</td>
	<td>3,895</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>48.86% [<b>47.1%</b>-50.6%]</td>
	<td>3,160</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>49.02% [<b>47.1%</b>-50.9%]</td>
	<td>2,709</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.99% [<b>47.5%</b>-48.5%]</td>
	<td>41,285</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.99% [47.5%-<b>48.5%</b>]</td>
	<td>41,285</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.18% [46.6%-<b>49.8%</b>]</td>
	<td>3,895</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>49.04% [48.3%-<b>49.8%</b>]</td>
	<td>17,765</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.91% [45.8%-<b>50.0%</b>]</td>
	<td>2,300</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.66% [49.2%-<b>50.2%</b>]</td>
	<td>41,399</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-diana"></span> Diana</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.24% [52.1%-52.3%]</td>
	<td>931,128</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.82% [<b>46.2%</b>-49.4%]</td>
	<td>4,000</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>48.09% [<b>46.3%</b>-49.8%]</td>
	<td>3,225</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.88% [<b>47.2%</b>-48.5%]</td>
	<td>22,896</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>49.35% [<b>47.4%</b>-51.3%]</td>
	<td>2,697</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.10% [<b>47.6%</b>-48.6%]</td>
	<td>36,411</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.88% [47.2%-<b>48.5%</b>]</td>
	<td>22,896</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.10% [47.6%-<b>48.6%</b>]</td>
	<td>36,411</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.82% [46.2%-<b>49.4%</b>]</td>
	<td>4,000</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>48.09% [46.3%-<b>49.8%</b>]</td>
	<td>3,225</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>49.35% [48.8%-<b>49.9%</b>]</td>
	<td>38,252</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-amumu"></span> Amumu</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.82% [52.7%-52.9%]</td>
	<td>798,503</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.42% [<b>45.0%</b>-47.9%]</td>
	<td>4,767</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.95% [<b>46.2%</b>-49.7%]</td>
	<td>3,249</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.76% [<b>46.9%</b>-50.6%]</td>
	<td>3,004</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>50.17% [<b>49.0%</b>-51.3%]</td>
	<td>7,934</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>49.72% [<b>49.3%</b>-50.2%]</td>
	<td>45,611</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.42% [45.0%-<b>47.9%</b>]</td>
	<td>4,767</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.95% [46.2%-<b>49.7%</b>]</td>
	<td>3,249</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>49.72% [49.3%-<b>50.2%</b>]</td>
	<td>45,611</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.76% [46.9%-<b>50.6%</b>]</td>
	<td>3,004</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>50.37% [49.9%-<b>50.8%</b>]</td>
	<td>44,323</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-udyr"></span> Udyr</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.30% [50.1%-50.5%]</td>
	<td>220,437</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.24% [<b>41.8%</b>-48.7%]</td>
	<td>842</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>49.35% [<b>45.9%</b>-52.8%]</td>
	<td>849</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.37% [<b>46.1%</b>-48.7%]</td>
	<td>5,746</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>49.53% [<b>46.3%</b>-52.7%]</td>
	<td>977</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>49.06% [<b>46.6%</b>-51.6%]</td>
	<td>1,604</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.24% [41.8%-<b>48.7%</b>]</td>
	<td>842</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.37% [46.1%-<b>48.7%</b>]</td>
	<td>5,746</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.14% [47.2%-<b>49.1%</b>]</td>
	<td>11,142</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>48.65% [47.7%-<b>49.6%</b>]</td>
	<td>12,031</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.62% [47.6%-<b>49.6%</b>]</td>
	<td>9,612</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-viego"></span> Viego</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.58% [50.5%-50.7%]</td>
	<td>1,433,017</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.88% [<b>43.4%</b>-46.4%]</td>
	<td>4,463</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.29% [<b>45.9%</b>-46.7%]</td>
	<td>65,300</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.61% [<b>46.3%</b>-49.0%]</td>
	<td>5,503</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.40% [<b>47.0%</b>-47.8%]</td>
	<td>55,696</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.97% [<b>47.3%</b>-50.6%]</td>
	<td>3,716</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.88% [43.4%-<b>46.4%</b>]</td>
	<td>4,463</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.29% [45.9%-<b>46.7%</b>]</td>
	<td>65,300</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.40% [47.0%-<b>47.8%</b>]</td>
	<td>55,696</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>48.46% [48.1%-<b>48.8%</b>]</td>
	<td>73,028</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>48.19% [47.4%-<b>48.9%</b>]</td>
	<td>17,634</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-yorick"></span> Yorick</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>54.37% [54.0%-54.8%]</td>
	<td>60,022</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.29% [<b>41.6%</b>-49.0%]</td>
	<td>733</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>51.16% [<b>45.8%</b>-56.6%]</td>
	<td>344</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.70% [<b>46.2%</b>-51.2%]</td>
	<td>1,579</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>53.68% [<b>46.4%</b>-60.9%]</td>
	<td>190</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>51.25% [<b>46.7%</b>-55.8%]</td>
	<td>478</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.29% [41.6%-<b>49.0%</b>]</td>
	<td>733</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.35% [47.5%-<b>51.2%</b>]</td>
	<td>2,887</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.70% [46.2%-<b>51.2%</b>]</td>
	<td>1,579</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>50.97% [49.0%-<b>52.9%</b>]</td>
	<td>2,709</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>50.71% [48.1%-<b>53.3%</b>]</td>
	<td>1,461</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-lillia"></span> Lillia</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.62% [50.5%-50.8%]</td>
	<td>411,192</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.97% [<b>44.3%</b>-49.6%]</td>
	<td>1,439</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.30% [<b>45.6%</b>-47.0%]</td>
	<td>21,762</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.69% [<b>45.7%</b>-47.7%]</td>
	<td>9,769</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.33% [<b>45.8%</b>-48.8%]</td>
	<td>4,481</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>48.35% [<b>46.6%</b>-50.1%]</td>
	<td>3,406</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.30% [45.6%-<b>47.0%</b>]</td>
	<td>21,762</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.69% [45.7%-<b>47.7%</b>]</td>
	<td>9,769</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.33% [45.8%-<b>48.8%</b>]</td>
	<td>4,481</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>48.02% [47.2%-<b>48.9%</b>]</td>
	<td>14,377</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.52% [47.8%-<b>49.2%</b>]</td>
	<td>20,182</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-shyvana"></span> Shyvana</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.66% [51.4%-51.9%]</td>
	<td>200,220</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.14% [<b>43.1%</b>-51.2%]</td>
	<td>596</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>47.82% [<b>45.3%</b>-50.3%]</td>
	<td>1,589</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>49.67% [<b>46.0%</b>-53.3%]</td>
	<td>759</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.71% [<b>46.2%</b>-49.2%]</td>
	<td>4,648</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>49.87% [<b>46.3%</b>-53.4%]</td>
	<td>802</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.66% [46.5%-<b>48.8%</b>]</td>
	<td>7,931</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.71% [46.2%-<b>49.2%</b>]</td>
	<td>4,648</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.10% [48.1%-<b>50.1%</b>]</td>
	<td>10,597</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>49.18% [48.2%-<b>50.1%</b>]</td>
	<td>11,115</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>49.13% [48.0%-<b>50.3%</b>]</td>
	<td>7,591</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-jarvan-iv"></span> Jarvan IV</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.99% [50.8%-51.1%]</td>
	<td>422,142</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.98% [<b>44.4%</b>-49.6%]</td>
	<td>1,475</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.92% [<b>45.3%</b>-48.6%]</td>
	<td>3,744</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>48.34% [<b>45.7%</b>-51.0%]</td>
	<td>1,419</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>49.28% [<b>46.7%</b>-51.9%]</td>
	<td>1,461</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.77% [<b>46.7%</b>-48.8%]</td>
	<td>9,067</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>47.81% [47.2%-<b>48.5%</b>]</td>
	<td>23,608</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.92% [45.3%-<b>48.6%</b>]</td>
	<td>3,744</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.77% [46.7%-<b>48.8%</b>]</td>
	<td>9,067</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.45% [47.7%-<b>49.2%</b>]</td>
	<td>18,522</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>48.71% [47.9%-<b>49.5%</b>]</td>
	<td>14,967</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-wukong"></span> Wukong</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.90% [51.8%-52.0%]</td>
	<td>829,953</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.13% [<b>43.4%</b>-46.9%]</td>
	<td>3,237</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.11% [<b>45.2%</b>-49.0%]</td>
	<td>2,876</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.01% [<b>45.9%</b>-50.1%]</td>
	<td>2,314</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.97% [<b>47.0%</b>-49.0%]</td>
	<td>10,295</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.55% [<b>47.1%</b>-48.0%]</td>
	<td>40,142</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.13% [43.4%-<b>46.9%</b>]</td>
	<td>3,237</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.55% [47.1%-<b>48.0%</b>]</td>
	<td>40,142</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.97% [47.0%-<b>49.0%</b>]</td>
	<td>10,295</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.11% [45.2%-<b>49.0%</b>]</td>
	<td>2,876</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.36% [47.7%-<b>49.0%</b>]</td>
	<td>21,042</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-kayn"></span> Kayn</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.10% [50.0%-50.2%]</td>
	<td>847,216</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.65% [<b>45.0%</b>-48.3%]</td>
	<td>3,777</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.94% [<b>45.2%</b>-48.7%]</td>
	<td>3,219</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>48.31% [<b>46.5%</b>-50.1%]</td>
	<td>3,175</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.05% [<b>46.6%</b>-47.5%]</td>
	<td>42,185</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.86% [<b>46.9%</b>-48.8%]</td>
	<td>10,861</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.05% [46.6%-<b>47.5%</b>]</td>
	<td>42,185</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.65% [45.0%-<b>48.3%</b>]</td>
	<td>3,777</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>47.90% [47.4%-<b>48.4%</b>]</td>
	<td>39,432</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.96% [47.5%-<b>48.4%</b>]</td>
	<td>43,510</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.94% [45.2%-<b>48.7%</b>]</td>
	<td>3,219</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-vi"></span> Vi</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.63% [49.5%-49.8%]</td>
	<td>638,935</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.44% [<b>43.1%</b>-47.7%]</td>
	<td>1,888</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.22% [<b>45.1%</b>-49.3%]</td>
	<td>2,285</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.69% [<b>45.2%</b>-48.2%]</td>
	<td>4,403</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.91% [<b>45.7%</b>-48.1%]</td>
	<td>6,748</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>47.68% [<b>45.7%</b>-49.6%]</td>
	<td>2,609</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.41% [45.9%-<b>47.0%</b>]</td>
	<td>32,211</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.44% [43.1%-<b>47.7%</b>]</td>
	<td>1,888</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.97% [46.1%-<b>47.8%</b>]</td>
	<td>14,145</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.22% [46.6%-<b>47.8%</b>]</td>
	<td>27,047</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.23% [46.6%-<b>47.9%</b>]</td>
	<td>23,962</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-master-yi"></span> Master Yi</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.38% [50.3%-50.5%]</td>
	<td>739,561</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.72% [<b>43.7%</b>-47.7%]</td>
	<td>2,465</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>45.63% [<b>45.1%</b>-46.2%]</td>
	<td>33,385</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.99% [<b>45.5%</b>-46.5%]</td>
	<td>36,158</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>46.33% [<b>45.6%</b>-47.0%]</td>
	<td>21,175</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.44% [<b>45.9%</b>-46.9%]</td>
	<td>38,588</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>45.63% [45.1%-<b>46.2%</b>]</td>
	<td>33,385</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.99% [45.5%-<b>46.5%</b>]</td>
	<td>36,158</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.44% [45.9%-<b>46.9%</b>]</td>
	<td>38,588</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>46.33% [45.6%-<b>47.0%</b>]</td>
	<td>21,175</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.72% [43.7%-<b>47.7%</b>]</td>
	<td>2,465</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-volibear"></span> Volibear</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.32% [51.2%-51.5%]</td>
	<td>350,805</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.69% [<b>44.9%</b>-50.5%]</td>
	<td>1,260</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.81% [<b>44.9%</b>-50.7%]</td>
	<td>1,169</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.13% [<b>45.8%</b>-50.4%]</td>
	<td>1,903</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>49.04% [<b>46.3%</b>-51.7%]</td>
	<td>1,362</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.14% [<b>47.0%</b>-49.3%]</td>
	<td>7,857</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.14% [47.0%-<b>49.3%</b>]</td>
	<td>7,857</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.99% [48.3%-<b>49.7%</b>]</td>
	<td>19,936</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>49.05% [48.3%-<b>49.8%</b>]</td>
	<td>19,522</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.15% [48.4%-<b>49.9%</b>]</td>
	<td>17,820</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>49.23% [48.5%-<b>50.0%</b>]</td>
	<td>16,596</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-nunu---willump"></span> Nunu & Willump</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.50% [50.3%-50.7%]</td>
	<td>324,638</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.65% [<b>42.9%</b>-48.4%]</td>
	<td>1,334</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.66% [<b>44.7%</b>-50.6%]</td>
	<td>1,177</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.37% [<b>45.6%</b>-47.2%]</td>
	<td>16,232</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.71% [<b>45.6%</b>-47.8%]</td>
	<td>8,073</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>49.69% [<b>46.5%</b>-52.9%]</td>
	<td>984</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.37% [45.6%-<b>47.2%</b>]</td>
	<td>16,232</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.71% [45.6%-<b>47.8%</b>]</td>
	<td>8,073</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>47.45% [46.7%-<b>48.2%</b>]</td>
	<td>17,595</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.65% [42.9%-<b>48.4%</b>]</td>
	<td>1,334</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>48.08% [47.2%-<b>48.9%</b>]</td>
	<td>14,134</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-lee-sin"></span> Lee Sin</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.72% [48.6%-48.8%]</td>
	<td>1,205,116</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.65% [<b>41.7%</b>-45.6%]</td>
	<td>2,689</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.21% [<b>44.6%</b>-45.9%]</td>
	<td>23,912</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.64% [<b>45.1%</b>-46.1%]</td>
	<td>38,483</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.23% [<b>45.3%</b>-47.2%]</td>
	<td>11,259</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.05% [<b>45.3%</b>-46.8%]</td>
	<td>17,321</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.65% [41.7%-<b>45.6%</b>]</td>
	<td>2,689</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.21% [44.6%-<b>45.9%</b>]</td>
	<td>23,912</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.64% [45.1%-<b>46.1%</b>]</td>
	<td>38,483</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.96% [45.6%-<b>46.3%</b>]</td>
	<td>66,032</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.20% [45.8%-<b>46.6%</b>]</td>
	<td>61,912</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-trundle"></span> Trundle</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.72% [51.5%-52.0%]</td>
	<td>137,323</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.54% [<b>41.4%</b>-49.7%]</td>
	<td>573</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>48.18% [<b>44.2%</b>-52.2%]</td>
	<td>633</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>50.18% [<b>45.8%</b>-54.5%]</td>
	<td>532</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>50.08% [<b>45.9%</b>-54.3%]</td>
	<td>563</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>49.79% [<b>46.1%</b>-53.5%]</td>
	<td>733</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.54% [41.4%-<b>49.7%</b>]</td>
	<td>573</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>48.09% [46.2%-<b>50.0%</b>]</td>
	<td>2,749</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.16% [48.0%-<b>50.3%</b>]</td>
	<td>7,206</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>49.30% [48.0%-<b>50.6%</b>]</td>
	<td>5,861</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.82% [48.7%-<b>50.9%</b>]</td>
	<td>7,934</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-gwen"></span> Gwen</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.29% [50.0%-50.6%]</td>
	<td>133,776</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-bel-veth"></span> Bel'Veth</td>
	<td>45.96% [<b>43.1%</b>-48.8%]</td>
	<td>1,238</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.95% [<b>43.8%</b>-52.1%]</td>
	<td>586</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>48.74% [<b>44.2%</b>-53.3%]</td>
	<td>478</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>47.58% [<b>44.3%</b>-50.9%]</td>
	<td>933</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>45.97% [<b>44.5%</b>-47.4%]</td>
	<td>4,679</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>45.97% [44.5%-<b>47.4%</b>]</td>
	<td>4,679</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.74% [45.3%-<b>48.2%</b>]</td>
	<td>4,957</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.26% [46.1%-<b>48.4%</b>]</td>
	<td>7,109</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-bel-veth"></span> Bel'Veth</td>
	<td>45.96% [43.1%-<b>48.8%</b>]</td>
	<td>1,238</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.48% [45.7%-<b>49.2%</b>]</td>
	<td>3,245</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-shaco"></span> Shaco</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.93% [48.8%-49.1%]</td>
	<td>512,951</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.97% [<b>40.7%</b>-45.2%]</td>
	<td>1,894</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.96% [<b>43.7%</b>-46.2%]</td>
	<td>6,114</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>44.96% [<b>44.1%</b>-45.8%]</td>
	<td>13,017</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.34% [<b>44.7%</b>-45.9%]</td>
	<td>27,928</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.38% [<b>44.8%</b>-46.0%]</td>
	<td>28,626</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.97% [40.7%-<b>45.2%</b>]</td>
	<td>1,894</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>44.96% [44.1%-<b>45.8%</b>]</td>
	<td>13,017</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.34% [44.7%-<b>45.9%</b>]</td>
	<td>27,928</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.38% [44.8%-<b>46.0%</b>]</td>
	<td>28,626</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.96% [43.7%-<b>46.2%</b>]</td>
	<td>6,114</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ekko"></span> Ekko</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.35% [48.2%-48.5%]</td>
	<td>301,894</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.06% [<b>40.9%</b>-47.2%]</td>
	<td>985</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.80% [<b>43.6%</b>-50.0%]</td>
	<td>955</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.35% [<b>44.2%</b>-46.5%]</td>
	<td>7,197</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.58% [<b>44.4%</b>-48.7%]</td>
	<td>2,123</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>46.66% [<b>44.7%</b>-48.6%]</td>
	<td>2,610</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.35% [44.2%-<b>46.5%</b>]</td>
	<td>7,197</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.06% [40.9%-<b>47.2%</b>]</td>
	<td>985</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.44% [45.6%-<b>47.3%</b>]</td>
	<td>13,964</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.69% [45.9%-<b>47.5%</b>]</td>
	<td>16,590</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.88% [46.1%-<b>47.7%</b>]</td>
	<td>15,764</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-graves"></span> Graves</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.82% [48.7%-49.0%]</td>
	<td>474,456</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.73% [<b>42.0%</b>-47.5%]</td>
	<td>1,281</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.91% [<b>42.8%</b>-49.1%]</td>
	<td>1,004</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.02% [<b>43.3%</b>-48.7%]</td>
	<td>1,371</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.37% [<b>44.7%</b>-46.0%]</td>
	<td>23,530</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>47.20% [<b>44.9%</b>-49.5%]</td>
	<td>1,824</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.37% [44.7%-<b>46.0%</b>]</td>
	<td>23,530</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.03% [45.3%-<b>46.7%</b>]</td>
	<td>21,188</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.37% [45.7%-<b>47.0%</b>]</td>
	<td>23,402</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.50% [45.7%-<b>47.3%</b>]</td>
	<td>15,194</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.73% [42.0%-<b>47.5%</b>]</td>
	<td>1,281</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-sejuani"></span> Sejuani</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.32% [49.1%-49.5%]</td>
	<td>298,760</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.96% [<b>41.8%</b>-48.1%]</td>
	<td>1,003</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.01% [<b>42.3%</b>-47.8%]</td>
	<td>1,313</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>46.02% [<b>43.2%</b>-48.8%]</td>
	<td>1,245</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.82% [<b>43.3%</b>-50.4%]</td>
	<td>788</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>44.83% [<b>43.7%</b>-45.9%]</td>
	<td>8,097</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>44.83% [43.7%-<b>45.9%</b>]</td>
	<td>8,097</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.53% [44.7%-<b>46.3%</b>]</td>
	<td>14,992</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.41% [45.6%-<b>47.2%</b>]</td>
	<td>15,477</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.46% [45.6%-<b>47.3%</b>]</td>
	<td>13,531</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.64% [43.7%-<b>47.6%</b>]</td>
	<td>2,712</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-pantheon"></span> Pantheon</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.46% [49.2%-49.7%]</td>
	<td>142,302</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.08% [<b>38.4%</b>-47.8%]</td>
	<td>448</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.62% [<b>42.1%</b>-51.1%]</td>
	<td>489</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.76% [<b>43.1%</b>-48.5%]</td>
	<td>1,359</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>47.55% [<b>43.6%</b>-51.5%]</td>
	<td>635</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.67% [<b>43.6%</b>-49.7%]</td>
	<td>1,067</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.12% [44.9%-<b>47.3%</b>]</td>
	<td>7,246</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.15% [44.9%-<b>47.4%</b>]</td>
	<td>6,253</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.08% [38.4%-<b>47.8%</b>]</td>
	<td>448</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.74% [45.5%-<b>48.0%</b>]</td>
	<td>6,394</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.18% [46.0%-<b>48.4%</b>]</td>
	<td>6,933</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-bel-veth"></span> Bel'Veth</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.07% [48.8%-49.3%]</td>
	<td>162,085</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.32% [<b>37.1%</b>-45.6%]</td>
	<td>542</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.17% [<b>42.1%</b>-50.3%]</td>
	<td>589</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>44.49% [<b>42.1%</b>-46.8%]</td>
	<td>1,789</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.58% [<b>43.4%</b>-45.8%]</td>
	<td>7,003</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>48.07% [<b>43.9%</b>-52.2%]</td>
	<td>572</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.32% [37.1%-<b>45.6%</b>]</td>
	<td>542</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.58% [43.4%-<b>45.8%</b>]</td>
	<td>7,003</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.37% [44.1%-<b>46.6%</b>]</td>
	<td>6,155</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>44.49% [42.1%-<b>46.8%</b>]</td>
	<td>1,789</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.00% [44.8%-<b>47.2%</b>]</td>
	<td>7,405</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-fiddlesticks"></span> Fiddlesticks</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.11% [49.9%-50.3%]</td>
	<td>211,054</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.17% [<b>41.8%</b>-48.5%]</td>
	<td>881</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.50% [<b>41.9%</b>-49.1%]</td>
	<td>778</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.29% [<b>43.9%</b>-46.7%]</td>
	<td>5,113</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.69% [<b>44.7%</b>-52.7%]</td>
	<td>614</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.52% [<b>44.9%</b>-48.1%]</td>
	<td>3,822</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.29% [43.9%-<b>46.7%</b>]</td>
	<td>5,113</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.20% [45.1%-<b>47.3%</b>]</td>
	<td>8,422</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.51% [45.5%-<b>47.5%</b>]</td>
	<td>10,022</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>47.00% [46.1%-<b>47.9%</b>]</td>
	<td>11,204</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.52% [44.9%-<b>48.1%</b>]</td>
	<td>3,822</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-dr--mundo"></span> Dr. Mundo</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.17% [51.7%-52.6%]</td>
	<td>50,812</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.80% [<b>37.2%</b>-50.4%]</td>
	<td>226</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>50.35% [<b>41.9%</b>-58.8%]</td>
	<td>141</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.73% [<b>42.7%</b>-54.7%]</td>
	<td>277</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>50.00% [<b>43.0%</b>-57.0%]</td>
	<td>206</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>51.63% [<b>43.5%</b>-59.7%]</td>
	<td>153</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.65% [44.9%-<b>50.4%</b>]</td>
	<td>1,322</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.80% [37.2%-<b>50.4%</b>]</td>
	<td>226</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>48.81% [45.7%-<b>51.9%</b>]</td>
	<td>1,053</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>50.09% [47.9%-<b>52.2%</b>]</td>
	<td>2,172</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>50.61% [48.7%-<b>52.5%</b>]</td>
	<td>2,697</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-zac"></span> Zac</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.08% [48.9%-49.3%]</td>
	<td>274,179</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.52% [<b>41.3%</b>-47.8%]</td>
	<td>941</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.11% [<b>41.7%</b>-48.5%]</td>
	<td>849</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>44.82% [<b>41.9%</b>-47.8%]</td>
	<td>1,140</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>44.86% [<b>43.7%</b>-46.0%]</td>
	<td>7,914</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.88% [<b>44.1%</b>-51.6%]</td>
	<td>710</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>44.86% [43.7%-<b>46.0%</b>]</td>
	<td>7,914</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.70% [44.9%-<b>46.5%</b>]</td>
	<td>14,233</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>46.30% [45.4%-<b>47.2%</b>]</td>
	<td>12,671</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.52% [41.3%-<b>47.8%</b>]</td>
	<td>941</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>44.82% [41.9%-<b>47.8%</b>]</td>
	<td>1,140</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-hecarim"></span> Hecarim</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.59% [48.4%-48.8%]</td>
	<td>336,099</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>41.89% [<b>38.9%</b>-44.9%]</td>
	<td>1,110</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.04% [<b>41.6%</b>-48.4%]</td>
	<td>857</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.93% [<b>42.9%</b>-48.9%]</td>
	<td>1,095</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.34% [<b>43.3%</b>-49.4%]</td>
	<td>1,081</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>44.93% [<b>43.8%</b>-46.0%]</td>
	<td>7,931</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>41.89% [38.9%-<b>44.9%</b>]</td>
	<td>1,110</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>44.93% [43.8%-<b>46.0%</b>]</td>
	<td>7,931</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.78% [45.0%-<b>46.6%</b>]</td>
	<td>16,664</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.78% [45.0%-<b>46.6%</b>]</td>
	<td>14,555</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.01% [45.1%-<b>46.9%</b>]</td>
	<td>11,967</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-talon"></span> Talon</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.15% [49.9%-50.4%]</td>
	<td>157,124</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.79% [<b>41.0%</b>-50.6%]</td>
	<td>428</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.33% [<b>41.5%</b>-51.2%]</td>
	<td>423</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.93% [<b>41.8%</b>-52.1%]</td>
	<td>375</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>46.77% [<b>42.3%</b>-51.3%]</td>
	<td>496</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>47.39% [<b>43.7%</b>-51.0%]</td>
	<td>749</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.75% [45.0%-<b>48.5%</b>]</td>
	<td>3,247</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>47.50% [46.4%-<b>48.6%</b>]</td>
	<td>8,742</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.68% [46.5%-<b>48.9%</b>]</td>
	<td>6,971</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.44% [46.0%-<b>48.9%</b>]</td>
	<td>4,584</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.12% [47.0%-<b>49.3%</b>]</td>
	<td>7,352</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-zyra"></span> Zyra</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.04% [48.7%-49.4%]</td>
	<td>103,854</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.22% [<b>39.3%</b>-51.1%]</td>
	<td>283</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>45.11% [<b>41.4%</b>-48.8%]</td>
	<td>727</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.62% [<b>41.6%</b>-47.6%]</td>
	<td>1,098</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.18% [<b>41.8%</b>-44.6%]</td>
	<td>5,115</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.74% [<b>42.3%</b>-53.2%]</td>
	<td>333</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.18% [41.8%-<b>44.6%</b>]</td>
	<td>5,115</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>44.86% [43.4%-<b>46.3%</b>]</td>
	<td>4,941</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.62% [41.6%-<b>47.6%</b>]</td>
	<td>1,098</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nunu---willump"></span> Nunu & Willump</td>
	<td>45.67% [43.2%-<b>48.1%</b>]</td>
	<td>1,686</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>46.63% [44.9%-<b>48.4%</b>]</td>
	<td>3,212</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-xin-zhao"></span> Xin Zhao</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.65% [50.5%-50.8%]</td>
	<td>453,799</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.17% [<b>40.3%</b>-46.0%]</td>
	<td>1,186</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.97% [<b>41.4%</b>-46.5%]</td>
	<td>1,494</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.59% [<b>44.8%</b>-48.4%]</td>
	<td>3,097</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>49.26% [<b>46.1%</b>-52.4%]</td>
	<td>1,027</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.47% [<b>46.7%</b>-50.3%]</td>
	<td>3,138</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.17% [40.3%-<b>46.0%</b>]</td>
	<td>1,186</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.97% [41.4%-<b>46.5%</b>]</td>
	<td>1,494</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.59% [44.8%-<b>48.4%</b>]</td>
	<td>3,097</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>48.10% [47.4%-<b>48.8%</b>]</td>
	<td>21,753</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.02% [47.2%-<b>48.8%</b>]</td>
	<td>16,570</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-rammus"></span> Rammus</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.26% [50.0%-50.5%]</td>
	<td>191,461</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.60% [<b>37.9%</b>-45.3%]</td>
	<td>697</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.18% [<b>41.4%</b>-51.0%]</td>
	<td>433</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.83% [<b>41.4%</b>-44.2%]</td>
	<td>4,944</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.61% [<b>41.5%</b>-49.7%]</td>
	<td>581</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>46.90% [<b>42.4%</b>-51.4%]</td>
	<td>501</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.83% [41.4%-<b>44.2%</b>]</td>
	<td>4,944</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.62% [42.5%-<b>44.7%</b>]</td>
	<td>7,922</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.60% [37.9%-<b>45.3%</b>]</td>
	<td>697</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.25% [44.1%-<b>46.4%</b>]</td>
	<td>7,794</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.92% [44.2%-<b>47.7%</b>]</td>
	<td>3,229</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-kindred"></span> Kindred</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.58% [48.4%-48.8%]</td>
	<td>300,104</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.86% [<b>40.8%</b>-46.9%]</td>
	<td>1,067</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.91% [<b>41.0%</b>-46.9%]</td>
	<td>1,125</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.21% [<b>41.9%</b>-48.5%]</td>
	<td>920</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.33% [<b>44.1%</b>-48.6%]</td>
	<td>1,977</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.28% [<b>44.1%</b>-46.4%]</td>
	<td>7,354</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>45.13% [44.2%-<b>46.0%</b>]</td>
	<td>12,630</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.28% [44.1%-<b>46.4%</b>]</td>
	<td>7,354</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.65% [44.8%-<b>46.5%</b>]</td>
	<td>14,529</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.91% [41.0%-<b>46.9%</b>]</td>
	<td>1,125</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.86% [40.8%-<b>46.9%</b>]</td>
	<td>1,067</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-mordekaiser"></span> Mordekaiser</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.87% [52.5%-53.2%]</td>
	<td>72,497</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.53% [<b>40.0%</b>-51.1%]</td>
	<td>325</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.61% [<b>40.5%</b>-52.7%]</td>
	<td>266</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>48.83% [<b>41.2%</b>-56.5%]</td>
	<td>172</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>48.08% [<b>42.2%</b>-54.0%]</td>
	<td>287</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-karthus"></span> Karthus</td>
	<td>49.90% [<b>45.6%</b>-54.2%]</td>
	<td>551</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>48.36% [46.6%-<b>50.1%</b>]</td>
	<td>3,147</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>49.05% [47.5%-<b>50.6%</b>]</td>
	<td>3,914</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.53% [40.0%-<b>51.1%</b>]</td>
	<td>325</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.80% [46.5%-<b>51.1%</b>]</td>
	<td>1,926</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.80% [46.4%-<b>51.2%</b>]</td>
	<td>1,674</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-skarner"></span> Skarner</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.43% [48.3%-48.6%]</td>
	<td>364,778</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.76% [<b>40.2%</b>-45.3%]</td>
	<td>1,492</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.30% [<b>40.3%</b>-46.3%]</td>
	<td>1,120</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.88% [<b>43.0%</b>-46.8%]</td>
	<td>2,736</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.29% [<b>43.3%</b>-49.2%]</td>
	<td>1,147</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.05% [<b>44.1%</b>-46.0%]</td>
	<td>11,043</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.76% [40.2%-<b>45.3%</b>]</td>
	<td>1,492</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.05% [44.1%-<b>46.0%</b>]</td>
	<td>11,043</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.22% [44.4%-<b>46.0%</b>]</td>
	<td>16,047</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.52% [44.8%-<b>46.2%</b>]</td>
	<td>19,591</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.30% [40.3%-<b>46.3%</b>]</td>
	<td>1,120</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-kha-zix"></span> Kha'Zix</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.44% [48.3%-48.6%]</td>
	<td>375,138</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.21% [<b>39.0%</b>-45.4%]</td>
	<td>957</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.34% [<b>39.9%</b>-46.8%]</td>
	<td>826</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.77% [<b>42.6%</b>-46.9%]</td>
	<td>2,095</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>45.76% [<b>42.8%</b>-48.7%]</td>
	<td>1,169</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.85% [<b>43.9%</b>-49.8%]</td>
	<td>1,112</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.21% [39.0%-<b>45.4%</b>]</td>
	<td>957</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>44.75% [44.0%-<b>45.5%</b>]</td>
	<td>18,673</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>44.93% [44.1%-<b>45.7%</b>]</td>
	<td>15,731</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.04% [44.2%-<b>45.9%</b>]</td>
	<td>13,610</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.49% [44.8%-<b>46.2%</b>]</td>
	<td>19,060</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-evelynn"></span> Evelynn</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>46.72% [46.5%-46.9%]</td>
	<td>217,984</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>39.67% [<b>36.1%</b>-43.3%]</td>
	<td>736</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.03% [<b>39.1%</b>-46.9%]</td>
	<td>639</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.82% [<b>39.5%</b>-46.2%]</td>
	<td>878</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.11% [<b>42.1%</b>-50.2%]</td>
	<td>605</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.16% [<b>42.2%</b>-44.1%]</td>
	<td>10,172</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>39.67% [36.1%-<b>43.3%</b>]</td>
	<td>736</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.16% [42.2%-<b>44.1%</b>]</td>
	<td>10,172</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.72% [42.8%-<b>44.6%</b>]</td>
	<td>12,100</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>43.72% [42.4%-<b>45.1%</b>]</td>
	<td>5,516</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.38% [43.4%-<b>45.4%</b>]</td>
	<td>9,402</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-maokai"></span> Maokai</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.95% [47.6%-48.3%]</td>
	<td>65,430</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>41.54% [<b>37.1%</b>-46.0%]</td>
	<td>491</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>45.53% [<b>38.9%</b>-52.2%]</td>
	<td>224</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.66% [<b>38.9%</b>-52.4%]</td>
	<td>219</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.07% [<b>40.1%</b>-52.0%]</td>
	<td>280</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.99% [<b>40.3%</b>-47.7%]</td>
	<td>716</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.32% [41.7%-<b>45.0%</b>]</td>
	<td>3,603</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>41.54% [37.1%-<b>46.0%</b>]</td>
	<td>491</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>44.84% [43.1%-<b>46.6%</b>]</td>
	<td>3,171</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>44.99% [42.5%-<b>47.5%</b>]</td>
	<td>1,629</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.99% [40.3%-<b>47.7%</b>]</td>
	<td>716</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-zed"></span> Zed</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.17% [47.8%-48.5%]</td>
	<td>81,795</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>43.44% [<b>37.4%</b>-49.5%]</td>
	<td>267</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.04% [<b>38.4%</b>-51.7%]</td>
	<td>222</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.31% [<b>39.1%</b>-53.5%]</td>
	<td>190</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>44.58% [<b>41.2%</b>-48.0%]</td>
	<td>850</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.86% [<b>41.2%</b>-50.5%]</td>
	<td>460</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>44.16% [42.4%-<b>45.9%</b>]</td>
	<td>3,222</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>44.62% [43.0%-<b>46.3%</b>]</td>
	<td>3,709</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sejuani"></span> Sejuani</td>
	<td>44.18% [41.5%-<b>46.9%</b>]</td>
	<td>1,376</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.75% [44.2%-<b>47.3%</b>]</td>
	<td>4,345</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.65% [43.8%-<b>47.5%</b>]</td>
	<td>2,878</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-rek-sai"></span> Rek'Sai</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.59% [48.2%-49.0%]</td>
	<td>71,461</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.56% [<b>37.2%</b>-51.9%]</td>
	<td>184</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>43.14% [<b>38.2%</b>-48.1%]</td>
	<td>401</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.36% [<b>40.3%</b>-56.4%]</td>
	<td>153</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.44% [<b>40.6%</b>-54.3%]</td>
	<td>215</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>46.04% [<b>40.7%</b>-51.3%]</td>
	<td>354</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.17% [42.2%-<b>46.2%</b>]</td>
	<td>2,481</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>43.76% [40.8%-<b>46.8%</b>]</td>
	<td>1,099</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>45.30% [43.5%-<b>47.1%</b>]</td>
	<td>3,192</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.55% [43.8%-<b>47.3%</b>]</td>
	<td>3,174</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.08% [44.4%-<b>47.8%</b>]</td>
	<td>3,548</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-jax"></span> Jax</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.40% [49.1%-49.7%]</td>
	<td>144,029</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.39% [<b>37.5%</b>-45.3%]</td>
	<td>645</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.34% [<b>37.8%</b>-46.9%]</td>
	<td>477</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.92% [<b>39.1%</b>-48.7%]</td>
	<td>428</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>46.29% [<b>42.0%</b>-50.6%]</td>
	<td>540</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>44.69% [<b>42.2%</b>-47.2%]</td>
	<td>1,537</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.39% [37.5%-<b>45.3%</b>]</td>
	<td>645</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.78% [43.6%-<b>46.0%</b>]</td>
	<td>6,815</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.34% [37.8%-<b>46.9%</b>]</td>
	<td>477</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>44.69% [42.2%-<b>47.2%</b>]</td>
	<td>1,537</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.28% [44.5%-<b>48.1%</b>]</td>
	<td>3,044</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-darius"></span> Darius</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.26% [50.9%-51.6%]</td>
	<td>72,142</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.87% [<b>36.8%</b>-51.0%]</td>
	<td>196</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>44.33% [<b>37.5%</b>-51.2%]</td>
	<td>212</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.89% [<b>38.5%</b>-51.2%]</td>
	<td>245</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.94% [<b>43.3%</b>-52.6%]</td>
	<td>463</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.70% [<b>43.6%</b>-53.8%]</td>
	<td>386</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.33% [45.7%-<b>49.0%</b>]</td>
	<td>3,615</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.70% [46.9%-<b>50.5%</b>]</td>
	<td>3,164</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>49.25% [47.6%-<b>50.9%</b>]</td>
	<td>3,567</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.87% [36.8%-<b>51.0%</b>]</td>
	<td>196</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>49.17% [47.3%-<b>51.0%</b>]</td>
	<td>2,918</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-rengar"></span> Rengar</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>45.22% [45.0%-45.5%]</td>
	<td>169,858</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>39.57% [<b>35.6%</b>-43.5%]</td>
	<td>619</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.15% [<b>37.2%</b>-45.1%]</td>
	<td>622</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>41.68% [<b>37.3%</b>-46.0%]</td>
	<td>511</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.82% [<b>38.1%</b>-47.5%]</td>
	<td>439</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>40.69% [<b>38.4%</b>-43.0%]</td>
	<td>1,821</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>40.61% [39.1%-<b>42.1%</b>]</td>
	<td>4,168</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>40.95% [39.7%-<b>42.2%</b>]</td>
	<td>6,593</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>41.56% [40.5%-<b>42.7%</b>]</td>
	<td>7,894</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>40.69% [38.4%-<b>43.0%</b>]</td>
	<td>1,821</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>41.86% [40.7%-<b>43.0%</b>]</td>
	<td>7,544</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-teemo"></span> Teemo</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.38% [49.1%-49.7%]</td>
	<td>98,825</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.50% [<b>36.0%</b>-47.0%]</td>
	<td>318</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.09% [<b>36.8%</b>-47.3%]</td>
	<td>354</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.82% [<b>41.9%</b>-47.7%]</td>
	<td>1,169</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.03% [<b>43.2%</b>-52.8%]</td>
	<td>433</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>44.88% [<b>43.4%</b>-46.3%]</td>
	<td>4,788</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>44.88% [43.4%-<b>46.3%</b>]</td>
	<td>4,788</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.50% [36.0%-<b>47.0%</b>]</td>
	<td>318</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.83% [44.5%-<b>47.2%</b>]</td>
	<td>5,494</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.09% [36.8%-<b>47.3%</b>]</td>
	<td>354</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.82% [41.9%-<b>47.7%</b>]</td>
	<td>1,169</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ivern"></span> Ivern</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.20% [47.8%-48.6%]</td>
	<td>78,983</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>41.69% [<b>35.6%</b>-47.8%]</td>
	<td>259</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.70% [<b>36.7%</b>-48.7%]</td>
	<td>274</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.47% [<b>39.6%</b>-53.3%]</td>
	<td>213</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>46.13% [<b>40.7%</b>-51.6%]</td>
	<td>336</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.27% [<b>40.8%</b>-49.7%]</td>
	<td>497</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>43.66% [41.5%-<b>45.8%</b>]</td>
	<td>2,139</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.57% [42.9%-<b>46.3%</b>]</td>
	<td>3,428</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.44% [43.6%-<b>47.3%</b>]</td>
	<td>2,852</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.90% [44.4%-<b>47.4%</b>]</td>
	<td>4,339</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.97% [44.3%-<b>47.6%</b>]</td>
	<td>3,661</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-karthus"></span> Karthus</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.38% [48.1%-48.6%]</td>
	<td>170,144</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>37.76% [<b>33.5%</b>-42.0%]</td>
	<td>527</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.36% [<b>36.7%</b>-46.1%]</td>
	<td>440</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>45.99% [<b>42.2%</b>-49.8%]</td>
	<td>674</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-bel-veth"></span> Bel'Veth</td>
	<td>45.30% [<b>42.8%</b>-47.8%]</td>
	<td>1,629</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.99% [<b>42.9%</b>-45.1%]</td>
	<td>8,728</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>37.76% [33.5%-<b>42.0%</b>]</td>
	<td>527</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.99% [42.9%-<b>45.1%</b>]</td>
	<td>8,728</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>44.27% [43.0%-<b>45.5%</b>]</td>
	<td>6,371</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.36% [36.7%-<b>46.1%</b>]</td>
	<td>440</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.50% [44.4%-<b>46.6%</b>]</td>
	<td>8,660</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-poppy"></span> Poppy</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.01% [48.6%-49.4%]</td>
	<td>70,298</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.80% [<b>36.5%</b>-49.1%]</td>
	<td>250</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.95% [<b>36.6%</b>-51.3%]</td>
	<td>182</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>42.96% [<b>38.1%</b>-47.8%]</td>
	<td>412</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>45.11% [<b>38.3%</b>-51.9%]</td>
	<td>215</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>45.93% [<b>39.6%</b>-52.3%]</td>
	<td>246</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>43.75% [41.9%-<b>45.6%</b>]</td>
	<td>2,868</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.95% [42.8%-<b>47.1%</b>]</td>
	<td>2,202</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>44.67% [42.1%-<b>47.2%</b>]</td>
	<td>1,493</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.43% [43.5%-<b>47.3%</b>]</td>
	<td>2,804</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.19% [42.7%-<b>47.7%</b>]</td>
	<td>1,549</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-elise"></span> Elise</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>46.16% [45.9%-46.4%]</td>
	<td>223,702</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>39.14% [<b>35.4%</b>-42.9%]</td>
	<td>682</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>40.20% [<b>36.2%</b>-44.2%]</td>
	<td>597</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>41.76% [<b>40.8%</b>-42.7%]</td>
	<td>11,490</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>42.72% [<b>41.0%</b>-44.4%]</td>
	<td>3,499</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>42.32% [<b>41.3%</b>-43.4%]</td>
	<td>8,987</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>41.76% [40.8%-<b>42.7%</b>]</td>
	<td>11,490</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>39.14% [35.4%-<b>42.9%</b>]</td>
	<td>682</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>42.32% [41.3%-<b>43.4%</b>]</td>
	<td>8,987</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>42.49% [41.6%-<b>43.4%</b>]</td>
	<td>11,932</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>40.20% [36.2%-<b>44.2%</b>]</td>
	<td>597</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-nidalee"></span> Nidalee</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>45.32% [45.1%-45.5%]</td>
	<td>187,845</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>39.55% [<b>34.7%</b>-44.4%]</td>
	<td>402</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>40.09% [<b>35.4%</b>-44.8%]</td>
	<td>434</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.63% [<b>38.0%</b>-49.2%]</td>
	<td>314</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>41.40% [<b>38.3%</b>-44.5%]</td>
	<td>983</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>41.86% [<b>38.6%</b>-45.1%]</td>
	<td>910</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>39.96% [38.9%-<b>41.0%</b>]</td>
	<td>8,921</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>40.98% [39.6%-<b>42.4%</b>]</td>
	<td>4,880</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>40.86% [39.2%-<b>42.5%</b>]</td>
	<td>3,553</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>41.58% [40.2%-<b>42.9%</b>]</td>
	<td>5,348</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>42.55% [41.5%-<b>43.6%</b>]</td>
	<td>8,675</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-gragas"></span> Gragas</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>44.84% [44.6%-45.1%]</td>
	<td>144,500</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>35.64% [<b>30.3%</b>-41.0%]</td>
	<td>317</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>36.23% [<b>31.1%</b>-41.3%]</td>
	<td>356</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.11% [<b>36.6%</b>-45.6%]</td>
	<td>484</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>42.29% [<b>37.7%</b>-46.9%]</td>
	<td>461</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>42.80% [<b>38.6%</b>-47.0%]</td>
	<td>549</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>35.64% [30.3%-<b>41.0%</b>]</td>
	<td>317</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>36.23% [31.1%-<b>41.3%</b>]</td>
	<td>356</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>40.70% [39.5%-<b>41.9%</b>]</td>
	<td>7,081</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>40.63% [39.3%-<b>42.0%</b>]</td>
	<td>5,491</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>41.73% [40.5%-<b>43.0%</b>]</td>
	<td>6,385</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-taliyah"></span> Taliyah</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>46.43% [46.0%-46.8%]</td>
	<td>59,943</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>35.81% [<b>27.9%</b>-43.7%]</td>
	<td>148</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>36.46% [<b>29.3%</b>-43.6%]</td>
	<td>181</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>41.69% [<b>35.8%</b>-47.6%]</td>
	<td>283</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.36% [<b>37.4%</b>-49.3%]</td>
	<td>279</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>43.55% [<b>37.7%</b>-49.4%]</td>
	<td>287</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>36.46% [29.3%-<b>43.6%</b>]</td>
	<td>181</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>35.81% [27.9%-<b>43.7%</b>]</td>
	<td>148</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>42.28% [39.9%-<b>44.7%</b>]</td>
	<td>1,736</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.32% [41.5%-<b>45.1%</b>]</td>
	<td>3,114</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viego"></span> Viego</td>
	<td>44.01% [42.6%-<b>45.4%</b>]</td>
	<td>5,259</td>
</tr>
</table>

</details>
### Mid

<details>
<summary>Click to view</summary>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-malzahar"></span> Malzahar</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.51% [52.4%-52.6%]</td>
	<td>628,248</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.32% [<b>46.4%</b>-50.2%]</td>
	<td>2,773</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>48.46% [<b>46.5%</b>-50.4%]</td>
	<td>2,581</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.79% [<b>47.1%</b>-48.5%]</td>
	<td>21,758</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>49.49% [<b>47.6%</b>-51.4%]</td>
	<td>2,762</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>49.53% [<b>47.7%</b>-51.4%]</td>
	<td>3,014</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.79% [47.1%-<b>48.5%</b>]</td>
	<td>21,758</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>49.05% [48.1%-<b>50.0%</b>]</td>
	<td>10,097</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.32% [46.4%-<b>50.2%</b>]</td>
	<td>2,773</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>48.46% [46.5%-<b>50.4%</b>]</td>
	<td>2,581</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.26% [48.0%-<b>50.5%</b>]</td>
	<td>6,451</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-syndra"></span> Syndra</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.92% [50.8%-51.1%]</td>
	<td>487,987</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.04% [<b>45.8%</b>-50.3%]</td>
	<td>1,994</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.42% [<b>46.5%</b>-48.4%]</td>
	<td>11,349</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>47.96% [<b>46.9%</b>-49.1%]</td>
	<td>8,181</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>48.37% [<b>46.9%</b>-49.9%]</td>
	<td>4,525</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.94% [<b>46.9%</b>-51.0%]</td>
	<td>2,470</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.42% [46.5%-<b>48.4%</b>]</td>
	<td>11,349</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>47.96% [46.9%-<b>49.1%</b>]</td>
	<td>8,181</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.58% [47.9%-<b>49.3%</b>]</td>
	<td>19,335</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-katarina"></span> Katarina</td>
	<td>48.77% [48.0%-<b>49.6%</b>]</td>
	<td>15,690</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.71% [47.8%-<b>49.6%</b>]</td>
	<td>11,747</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-lux"></span> Lux</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.52% [51.4%-51.7%]</td>
	<td>498,809</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.10% [<b>43.9%</b>-48.3%]</td>
	<td>2,080</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.62% [<b>46.4%</b>-48.9%]</td>
	<td>6,514</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.81% [<b>46.5%</b>-51.1%]</td>
	<td>1,899</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>48.50% [<b>46.9%</b>-50.1%]</td>
	<td>3,888</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.49% [<b>47.1%</b>-49.9%]</td>
	<td>5,293</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.10% [43.9%-<b>48.3%</b>]</td>
	<td>2,080</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.62% [46.4%-<b>48.9%</b>]</td>
	<td>6,514</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.68% [48.0%-<b>49.4%</b>]</td>
	<td>21,706</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.72% [47.8%-<b>49.6%</b>]</td>
	<td>11,814</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>49.29% [48.7%-<b>49.8%</b>]</td>
	<td>33,270</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-anivia"></span> Anivia</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.80% [51.5%-52.1%]</td>
	<td>145,295</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.06% [<b>44.3%</b>-51.8%]</td>
	<td>697</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>48.02% [<b>45.8%</b>-50.2%]</td>
	<td>2,080</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>50.18% [<b>45.9%</b>-54.5%]</td>
	<td>538</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-neeko"></span> Neeko</td>
	<td>50.23% [<b>46.2%</b>-54.2%]</td>
	<td>627</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.01% [<b>46.3%</b>-51.7%]</td>
	<td>1,367</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.71% [46.5%-<b>48.9%</b>]</td>
	<td>6,947</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.20% [46.4%-<b>50.0%</b>]</td>
	<td>3,224</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>48.02% [45.8%-<b>50.2%</b>]</td>
	<td>2,080</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>49.87% [48.5%-<b>51.3%</b>]</td>
	<td>5,219</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>50.13% [48.7%-<b>51.5%</b>]</td>
	<td>5,160</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-hwei"></span> Hwei</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.06% [49.9%-50.2%]</td>
	<td>490,752</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.13% [<b>44.8%</b>-47.4%]</td>
	<td>5,835</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.93% [<b>45.7%</b>-50.2%]</td>
	<td>1,959</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.10% [<b>46.1%</b>-48.1%]</td>
	<td>9,396</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.38% [<b>46.2%</b>-50.6%]</td>
	<td>2,102</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.60% [<b>46.8%</b>-48.4%]</td>
	<td>14,102</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.13% [44.8%-<b>47.4%</b>]</td>
	<td>5,835</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.10% [46.1%-<b>48.1%</b>]</td>
	<td>9,396</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.60% [46.8%-<b>48.4%</b>]</td>
	<td>14,102</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>47.96% [47.2%-<b>48.7%</b>]</td>
	<td>17,685</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>48.13% [47.4%-<b>48.8%</b>]</td>
	<td>20,082</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-veigar"></span> Veigar</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.28% [52.1%-52.4%]</td>
	<td>522,168</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.50% [<b>45.3%</b>-49.7%]</td>
	<td>2,126</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.63% [<b>45.5%</b>-49.8%]</td>
	<td>2,175</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.24% [<b>46.9%</b>-49.6%]</td>
	<td>5,395</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>48.53% [<b>47.4%</b>-49.7%]</td>
	<td>7,648</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.85% [<b>48.2%</b>-49.5%]</td>
	<td>23,923</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.85% [48.2%-<b>49.5%</b>]</td>
	<td>23,923</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.24% [46.9%-<b>49.6%</b>]</td>
	<td>5,395</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.50% [45.3%-<b>49.7%</b>]</td>
	<td>2,126</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>48.53% [47.4%-<b>49.7%</b>]</td>
	<td>7,648</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.63% [45.5%-<b>49.8%</b>]</td>
	<td>2,175</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-vel-koz"></span> Vel'Koz</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.40% [52.1%-52.7%]</td>
	<td>139,051</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>47.73% [<b>45.0%</b>-50.5%]</td>
	<td>1,303</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>49.31% [<b>45.2%</b>-53.5%]</td>
	<td>580</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>49.68% [<b>46.5%</b>-52.9%]</td>
	<td>962</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>49.50% [<b>47.1%</b>-51.9%]</td>
	<td>1,701</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>49.17% [<b>47.2%</b>-51.1%]</td>
	<td>2,662</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>47.73% [45.0%-<b>50.5%</b>]</td>
	<td>1,303</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>49.53% [48.1%-<b>50.9%</b>]</td>
	<td>5,059</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>49.17% [47.2%-<b>51.1%</b>]</td>
	<td>2,662</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>49.86% [48.4%-<b>51.3%</b>]</td>
	<td>4,697</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.77% [48.0%-<b>51.5%</b>]</td>
	<td>3,164</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-aurelion-sol"></span> Aurelion Sol</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.92% [51.7%-52.1%]</td>
	<td>210,083</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>47.23% [<b>45.0%</b>-49.4%]</td>
	<td>2,028</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.45% [<b>45.0%</b>-49.9%]</td>
	<td>1,709</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.47% [<b>45.2%</b>-51.7%]</td>
	<td>953</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.49% [<b>45.3%</b>-49.7%]</td>
	<td>2,032</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>49.43% [<b>46.1%</b>-52.8%]</td>
	<td>884</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>47.57% [46.5%-<b>48.6%</b>]</td>
	<td>8,833</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.77% [46.3%-<b>49.2%</b>]</td>
	<td>4,693</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>47.23% [45.0%-<b>49.4%</b>]</td>
	<td>2,028</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.49% [45.3%-<b>49.7%</b>]</td>
	<td>2,032</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.45% [45.0%-<b>49.9%</b>]</td>
	<td>1,709</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-viktor"></span> Viktor</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.24% [50.1%-50.4%]</td>
	<td>776,512</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.56% [<b>44.5%</b>-46.6%]</td>
	<td>9,611</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.59% [<b>44.9%</b>-48.2%]</td>
	<td>3,614</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.67% [<b>45.8%</b>-49.5%]</td>
	<td>2,941</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.11% [<b>46.5%</b>-47.8%]</td>
	<td>23,517</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>47.71% [<b>46.6%</b>-48.8%]</td>
	<td>8,546</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.56% [44.5%-<b>46.6%</b>]</td>
	<td>9,611</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.11% [46.5%-<b>47.8%</b>]</td>
	<td>23,517</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.59% [44.9%-<b>48.2%</b>]</td>
	<td>3,614</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>47.73% [47.1%-<b>48.3%</b>]</td>
	<td>27,845</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.90% [47.3%-<b>48.5%</b>]</td>
	<td>24,225</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-mel"></span> Mel</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.19% [50.1%-50.3%]</td>
	<td>1,197,734</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.13% [<b>44.5%</b>-45.7%]</td>
	<td>26,210</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.98% [<b>44.7%</b>-47.2%]</td>
	<td>6,289</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>45.77% [<b>45.2%</b>-46.3%]</td>
	<td>35,549</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>47.37% [<b>46.6%</b>-48.2%]</td>
	<td>16,011</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>47.76% [<b>46.6%</b>-48.9%]</td>
	<td>8,003</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.13% [44.5%-<b>45.7%</b>]</td>
	<td>26,210</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>45.77% [45.2%-<b>46.3%</b>]</td>
	<td>35,549</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.98% [44.7%-<b>47.2%</b>]</td>
	<td>6,289</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>47.28% [46.9%-<b>47.7%</b>]</td>
	<td>62,200</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.41% [47.0%-<b>47.8%</b>]</td>
	<td>52,013</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-galio"></span> Galio</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.67% [51.5%-51.8%]</td>
	<td>527,896</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.71% [<b>44.6%</b>-48.8%]</td>
	<td>2,190</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.15% [<b>44.6%</b>-47.7%]</td>
	<td>4,242</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.86% [<b>45.3%</b>-48.4%]</td>
	<td>3,990</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.65% [<b>45.4%</b>-47.9%]</td>
	<td>6,859</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.50% [<b>45.7%</b>-49.3%]</td>
	<td>2,987</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.15% [44.6%-<b>47.7%</b>]</td>
	<td>4,242</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.65% [45.4%-<b>47.9%</b>]</td>
	<td>6,859</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.86% [45.3%-<b>48.4%</b>]</td>
	<td>3,990</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.78% [47.0%-<b>48.6%</b>]</td>
	<td>14,712</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.71% [44.6%-<b>48.8%</b>]</td>
	<td>2,190</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-xerath"></span> Xerath</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.40% [51.2%-51.6%]</td>
	<td>315,203</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.28% [<b>40.5%</b>-46.1%]</td>
	<td>1,236</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.66% [<b>44.4%</b>-48.9%]</td>
	<td>1,995</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.54% [<b>44.6%</b>-50.5%]</td>
	<td>1,140</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-akshan"></span> Akshan</td>
	<td>47.40% [<b>45.6%</b>-49.2%]</td>
	<td>3,251</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>47.11% [<b>45.7%</b>-48.6%]</td>
	<td>4,703</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.28% [40.5%-<b>46.1%</b>]</td>
	<td>1,236</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.11% [45.8%-<b>48.4%</b>]</td>
	<td>5,835</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>47.11% [45.7%-<b>48.6%</b>]</td>
	<td>4,703</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.66% [44.4%-<b>48.9%</b>]</td>
	<td>1,995</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-akshan"></span> Akshan</td>
	<td>47.40% [45.6%-<b>49.2%</b>]</td>
	<td>3,251</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ahri"></span> Ahri</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.64% [49.5%-49.8%]</td>
	<td>729,781</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.93% [<b>44.2%</b>-47.7%]</td>
	<td>3,298</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>44.82% [<b>44.3%</b>-45.3%]</td>
	<td>38,977</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.90% [<b>44.4%</b>-47.4%]</td>
	<td>4,261</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.97% [<b>45.2%</b>-48.8%]</td>
	<td>3,044</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.33% [<b>45.5%</b>-49.2%]</td>
	<td>2,854</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>44.82% [44.3%-<b>45.3%</b>]</td>
	<td>38,977</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.36% [45.8%-<b>47.0%</b>]</td>
	<td>26,913</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.90% [44.4%-<b>47.4%</b>]</td>
	<td>4,261</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.93% [44.2%-<b>47.7%</b>]</td>
	<td>3,298</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.97% [47.4%-<b>48.5%</b>]</td>
	<td>30,050</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-yasuo"></span> Yasuo</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.00% [49.9%-50.1%]</td>
	<td>773,210</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.89% [<b>42.1%</b>-45.6%]</td>
	<td>3,187</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.27% [<b>44.0%</b>-46.5%]</td>
	<td>6,456</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.35% [<b>44.2%</b>-46.5%]</td>
	<td>8,132</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.74% [<b>44.4%</b>-47.1%]</td>
	<td>5,550</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.00% [<b>44.4%</b>-45.6%]</td>
	<td>29,555</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.00% [44.4%-<b>45.6%</b>]</td>
	<td>29,555</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.89% [42.1%-<b>45.6%</b>]</td>
	<td>3,187</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.35% [44.2%-<b>46.5%</b>]</td>
	<td>8,132</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.27% [44.0%-<b>46.5%</b>]</td>
	<td>6,456</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.74% [44.4%-<b>47.1%</b>]</td>
	<td>5,550</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ryze"></span> Ryze</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.15% [50.9%-51.4%]</td>
	<td>169,507</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>46.34% [<b>43.4%</b>-49.3%]</td>
	<td>1,150</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.50% [<b>43.9%</b>-51.1%]</td>
	<td>781</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.84% [<b>44.6%</b>-47.1%]</td>
	<td>6,622</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>46.52% [<b>44.8%</b>-48.3%]</td>
	<td>3,220</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.48% [<b>44.8%</b>-52.2%]</td>
	<td>728</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.84% [44.6%-<b>47.1%</b>]</td>
	<td>6,622</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>46.52% [44.8%-<b>48.3%</b>]</td>
	<td>3,220</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.55% [46.2%-<b>48.9%</b>]</td>
	<td>5,183</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>46.34% [43.4%-<b>49.3%</b>]</td>
	<td>1,150</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.71% [45.8%-<b>49.7%</b>]</td>
	<td>2,628</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-yone"></span> Yone</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.35% [49.2%-49.5%]</td>
	<td>716,507</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.97% [<b>43.6%</b>-46.3%]</td>
	<td>5,410</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.63% [<b>43.9%</b>-47.4%]</td>
	<td>3,302</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.99% [<b>45.1%</b>-46.9%]</td>
	<td>11,431</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.10% [<b>45.1%</b>-49.1%]</td>
	<td>2,556</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>47.45% [<b>46.1%</b>-48.8%]</td>
	<td>5,767</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.97% [43.6%-<b>46.3%</b>]</td>
	<td>5,410</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.99% [45.1%-<b>46.9%</b>]</td>
	<td>11,431</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.63% [43.9%-<b>47.4%</b>]</td>
	<td>3,302</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>47.17% [46.5%-<b>47.9%</b>]</td>
	<td>19,846</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.27% [46.6%-<b>48.0%</b>]</td>
	<td>21,064</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-aurora"></span> Aurora</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.35% [48.2%-48.5%]</td>
	<td>374,447</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.95% [<b>43.4%</b>-48.5%]</td>
	<td>1,471</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.77% [<b>43.9%</b>-45.7%]</td>
	<td>11,724</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.67% [<b>44.2%</b>-49.1%]</td>
	<td>1,669</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.70% [<b>44.9%</b>-48.5%]</td>
	<td>3,079</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>46.21% [<b>45.0%</b>-47.5%]</td>
	<td>6,307</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.77% [43.9%-<b>45.7%</b>]</td>
	<td>11,724</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.09% [45.2%-<b>46.9%</b>]</td>
	<td>13,528</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>46.21% [45.0%-<b>47.5%</b>]</td>
	<td>6,307</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>46.30% [45.1%-<b>47.5%</b>]</td>
	<td>6,839</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>46.72% [45.9%-<b>47.6%</b>]</td>
	<td>13,437</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-akali"></span> Akali</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.16% [49.0%-49.3%]</td>
	<td>656,340</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.49% [<b>41.6%</b>-45.3%]</td>
	<td>2,860</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.19% [<b>43.5%</b>-44.9%]</td>
	<td>20,188</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.18% [<b>43.5%</b>-46.8%]</td>
	<td>3,654</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.82% [<b>44.2%</b>-45.4%]</td>
	<td>28,476</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.99% [<b>44.3%</b>-45.7%]</td>
	<td>21,102</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.19% [43.5%-<b>44.9%</b>]</td>
	<td>20,188</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.49% [41.6%-<b>45.3%</b>]</td>
	<td>2,860</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.82% [44.2%-<b>45.4%</b>]</td>
	<td>28,476</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.99% [44.3%-<b>45.7%</b>]</td>
	<td>21,102</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.18% [43.5%-<b>46.8%</b>]</td>
	<td>3,654</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-orianna"></span> Orianna</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.61% [49.4%-49.8%]</td>
	<td>306,364</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.14% [<b>42.1%</b>-48.2%]</td>
	<td>1,070</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.89% [<b>43.0%</b>-48.8%]</td>
	<td>1,207</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.03% [<b>43.1%</b>-47.0%]</td>
	<td>2,629</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.75% [<b>44.1%</b>-47.4%]</td>
	<td>3,617</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.43% [<b>44.6%</b>-50.3%]</td>
	<td>1,210</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.03% [43.1%-<b>47.0%</b>]</td>
	<td>2,629</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.75% [44.1%-<b>47.4%</b>]</td>
	<td>3,617</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>46.83% [45.9%-<b>47.7%</b>]</td>
	<td>12,347</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>47.06% [46.0%-<b>48.1%</b>]</td>
	<td>9,703</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.07% [46.0%-<b>48.1%</b>]</td>
	<td>8,895</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-cassiopeia"></span> Cassiopeia</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.81% [51.6%-52.0%]</td>
	<td>270,215</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.79% [<b>42.7%</b>-48.9%]</td>
	<td>1,035</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.54% [<b>42.8%</b>-48.2%]</td>
	<td>1,370</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.91% [<b>44.0%</b>-49.8%]</td>
	<td>1,215</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.12% [<b>44.3%</b>-48.0%]</td>
	<td>2,853</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>48.44% [<b>45.5%</b>-51.4%]</td>
	<td>1,154</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.96% [46.0%-<b>48.0%</b>]</td>
	<td>10,061</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.12% [44.3%-<b>48.0%</b>]</td>
	<td>2,853</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>47.21% [46.2%-<b>48.2%</b>]</td>
	<td>10,220</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.54% [42.8%-<b>48.2%</b>]</td>
	<td>1,370</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.06% [45.7%-<b>48.4%</b>]</td>
	<td>5,458</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ekko"></span> Ekko</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.78% [49.6%-50.0%]</td>
	<td>214,097</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.31% [<b>40.2%</b>-46.4%]</td>
	<td>1,025</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>45.95% [<b>42.7%</b>-49.2%]</td>
	<td>927</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.11% [<b>43.7%</b>-50.5%]</td>
	<td>866</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jayce"></span> Jayce</td>
	<td>47.13% [<b>43.9%</b>-50.4%]</td>
	<td>959</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.09% [<b>43.9%</b>-48.2%]</td>
	<td>2,141</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.31% [40.2%-<b>46.4%</b>]</td>
	<td>1,025</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.09% [43.9%-<b>48.2%</b>]</td>
	<td>2,141</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.17% [45.9%-<b>48.4%</b>]</td>
	<td>6,351</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>47.73% [46.5%-<b>48.9%</b>]</td>
	<td>6,768</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>47.99% [47.0%-<b>49.0%</b>]</td>
	<td>9,354</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-akshan"></span> Akshan</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.11% [49.9%-50.3%]</td>
	<td>183,532</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.92% [<b>42.3%</b>-49.6%]</td>
	<td>749</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.23% [<b>42.6%</b>-49.8%]</td>
	<td>770</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.40% [<b>42.9%</b>-49.9%]</td>
	<td>793</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.52% [<b>43.5%</b>-49.5%]</td>
	<td>1,092</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.05% [<b>43.6%</b>-48.5%]</td>
	<td>1,724</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.49% [45.1%-<b>47.9%</b>]</td>
	<td>5,177</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>46.94% [45.8%-<b>48.1%</b>]</td>
	<td>7,092</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.05% [43.6%-<b>48.5%</b>]</td>
	<td>1,724</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.43% [46.3%-<b>48.6%</b>]</td>
	<td>7,326</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.74% [44.5%-<b>49.0%</b>]</td>
	<td>1,949</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-irelia"></span> Irelia</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.36% [50.2%-50.5%]</td>
	<td>303,482</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>40.45% [<b>37.9%</b>-43.0%]</td>
	<td>1,456</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.41% [<b>42.4%</b>-46.4%]</td>
	<td>2,508</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.56% [<b>42.5%</b>-46.6%]</td>
	<td>2,428</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.68% [<b>43.8%</b>-49.5%]</td>
	<td>1,223</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.73% [<b>44.5%</b>-49.0%]</td>
	<td>1,988</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>40.45% [37.9%-<b>43.0%</b>]</td>
	<td>1,456</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.41% [42.4%-<b>46.4%</b>]</td>
	<td>2,508</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.56% [42.5%-<b>46.6%</b>]</td>
	<td>2,428</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.51% [45.5%-<b>47.6%</b>]</td>
	<td>8,862</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.12% [46.0%-<b>48.2%</b>]</td>
	<td>8,317</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-garen"></span> Garen</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>54.16% [53.8%-54.5%]</td>
	<td>89,634</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.36% [<b>39.6%</b>-49.1%]</td>
	<td>435</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.31% [<b>42.4%</b>-52.2%]</td>
	<td>410</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.83% [<b>42.6%</b>-51.1%]</td>
	<td>553</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>48.91% [<b>44.8%</b>-53.0%]</td>
	<td>599</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>49.07% [<b>45.2%</b>-53.0%]</td>
	<td>652</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.36% [39.6%-<b>49.1%</b>]</td>
	<td>435</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.83% [42.6%-<b>51.1%</b>]</td>
	<td>553</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.31% [42.4%-<b>52.2%</b>]</td>
	<td>410</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>49.07% [45.2%-<b>53.0%</b>]</td>
	<td>652</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>48.91% [44.8%-<b>53.0%</b>]</td>
	<td>599</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-vex"></span> Vex</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.88% [49.7%-50.1%]</td>
	<td>319,867</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.37% [<b>41.6%</b>-47.1%]</td>
	<td>1,280</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>45.41% [<b>42.2%</b>-48.6%]</td>
	<td>960</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.44% [<b>42.6%</b>-48.3%]</td>
	<td>1,197</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.51% [<b>42.8%</b>-48.2%]</td>
	<td>1,349</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.89% [<b>43.0%</b>-44.8%]</td>
	<td>11,358</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.89% [43.0%-<b>44.8%</b>]</td>
	<td>11,358</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.17% [43.8%-<b>46.6%</b>]</td>
	<td>5,094</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>45.96% [45.2%-<b>46.8%</b>]</td>
	<td>15,758</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.02% [43.2%-<b>46.9%</b>]</td>
	<td>2,923</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vladimir"></span> Vladimir</td>
	<td>45.48% [44.1%-<b>46.9%</b>]</td>
	<td>4,982</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-sylas"></span> Sylas</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.80% [48.7%-48.9%]</td>
	<td>699,214</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>37.16% [<b>35.4%</b>-38.9%]</td>
	<td>3,046</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.62% [<b>42.1%</b>-45.2%]</td>
	<td>4,062</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.70% [<b>43.0%</b>-44.4%]</td>
	<td>21,402</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.81% [<b>43.1%</b>-46.5%]</td>
	<td>3,394</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.04% [<b>43.2%</b>-44.9%]</td>
	<td>14,074</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>37.16% [35.4%-<b>38.9%</b>]</td>
	<td>3,046</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.70% [43.0%-<b>44.4%</b>]</td>
	<td>21,402</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.04% [43.2%-<b>44.9%</b>]</td>
	<td>14,074</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.62% [42.1%-<b>45.2%</b>]</td>
	<td>4,062</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.69% [44.1%-<b>45.3%</b>]</td>
	<td>30,350</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-vladimir"></span> Vladimir</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.50% [50.3%-50.7%]</td>
	<td>323,272</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.77% [<b>41.9%</b>-43.6%]</td>
	<td>12,678</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.72% [<b>42.0%</b>-45.5%]</td>
	<td>3,229</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.00% [<b>43.5%</b>-48.5%]</td>
	<td>1,552</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.23% [<b>44.5%</b>-50.0%]</td>
	<td>1,304</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.57% [<b>45.0%</b>-48.1%]</td>
	<td>4,140</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.77% [41.9%-<b>43.6%</b>]</td>
	<td>12,678</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.72% [42.0%-<b>45.5%</b>]</td>
	<td>3,229</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.57% [45.0%-<b>48.1%</b>]</td>
	<td>4,140</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.37% [46.4%-<b>48.3%</b>]</td>
	<td>10,514</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.00% [43.5%-<b>48.5%</b>]</td>
	<td>1,552</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-fizz"></span> Fizz</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.74% [49.6%-49.9%]</td>
	<td>337,227</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.79% [<b>41.1%</b>-46.5%]</td>
	<td>1,329</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.96% [<b>42.0%</b>-45.9%]</td>
	<td>2,493</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.83% [<b>42.4%</b>-47.3%]</td>
	<td>1,637</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>44.47% [<b>42.5%</b>-46.5%]</td>
	<td>2,471</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>43.58% [<b>42.7%</b>-44.5%]</td>
	<td>12,313</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>43.58% [42.7%-<b>44.5%</b>]</td>
	<td>12,313</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.96% [42.0%-<b>45.9%</b>]</td>
	<td>2,493</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>44.47% [42.5%-<b>46.5%</b>]</td>
	<td>2,471</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.79% [41.1%-<b>46.5%</b>]</td>
	<td>1,329</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>44.94% [43.1%-<b>46.8%</b>]</td>
	<td>2,955</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-heimerdinger"></span> Heimerdinger</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>53.33% [53.0%-53.7%]</td>
	<td>71,790</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>47.23% [<b>41.8%</b>-52.6%]</td>
	<td>343</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.62% [<b>41.9%</b>-51.4%]</td>
	<td>444</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.12% [<b>43.8%</b>-52.5%]</td>
	<td>532</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.72% [<b>45.5%</b>-54.0%]</td>
	<td>551</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>49.81% [<b>45.5%</b>-54.1%]</td>
	<td>538</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.01% [46.1%-<b>49.9%</b>]</td>
	<td>2,751</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>48.02% [45.8%-<b>50.2%</b>]</td>
	<td>2,028</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>48.59% [46.6%-<b>50.6%</b>]</td>
	<td>2,455</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>49.38% [48.1%-<b>50.7%</b>]</td>
	<td>5,664</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.45% [45.6%-<b>51.3%</b>]</td>
	<td>1,195</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-kassadin"></span> Kassadin</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.24% [50.0%-50.5%]</td>
	<td>150,855</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.58% [<b>40.4%</b>-48.8%]</td>
	<td>563</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.03% [<b>41.8%</b>-48.3%]</td>
	<td>926</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>44.97% [<b>42.0%</b>-47.9%]</td>
	<td>1,125</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.40% [<b>42.0%</b>-50.8%]</td>
	<td>515</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.79% [<b>42.2%</b>-49.4%]</td>
	<td>773</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>44.97% [42.0%-<b>47.9%</b>]</td>
	<td>1,125</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.96% [43.8%-<b>48.1%</b>]</td>
	<td>2,171</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.03% [41.8%-<b>48.3%</b>]</td>
	<td>926</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.58% [40.4%-<b>48.8%</b>]</td>
	<td>563</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>47.75% [46.5%-<b>49.0%</b>]</td>
	<td>6,200</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-taliyah"></span> Taliyah</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.71% [50.4%-51.0%]</td>
	<td>105,751</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.86% [<b>39.1%</b>-48.6%]</td>
	<td>440</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.39% [<b>41.7%</b>-51.1%]</td>
	<td>444</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.69% [<b>41.8%</b>-51.5%]</td>
	<td>424</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.77% [<b>42.5%</b>-53.0%]</td>
	<td>360</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>46.52% [<b>42.7%</b>-50.3%]</td>
	<td>690</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.62% [44.7%-<b>48.5%</b>]</td>
	<td>2,812</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.86% [39.1%-<b>48.6%</b>]</td>
	<td>440</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-katarina"></span> Katarina</td>
	<td>47.73% [45.8%-<b>49.6%</b>]</td>
	<td>2,776</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>47.75% [45.6%-<b>49.9%</b>]</td>
	<td>2,165</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.88% [43.7%-<b>50.0%</b>]</td>
	<td>994</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-brand"></span> Brand</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.97% [50.6%-51.3%]</td>
	<td>88,830</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.61% [<b>41.2%</b>-48.0%]</td>
	<td>854</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.86% [<b>41.4%</b>-52.3%]</td>
	<td>335</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>46.81% [<b>41.9%</b>-51.8%]</td>
	<td>408</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.79% [<b>42.8%</b>-52.7%]</td>
	<td>408</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.44% [<b>42.9%</b>-50.0%]</td>
	<td>788</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>45.43% [43.0%-<b>47.8%</b>]</td>
	<td>1,699</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.61% [41.2%-<b>48.0%</b>]</td>
	<td>854</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.11% [45.6%-<b>48.6%</b>]</td>
	<td>4,449</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>47.29% [45.5%-<b>49.1%</b>]</td>
	<td>3,165</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.44% [42.9%-<b>50.0%</b>]</td>
	<td>788</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-lissandra"></span> Lissandra</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.06% [49.9%-50.3%]</td>
	<td>227,485</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.64% [<b>40.3%</b>-47.0%]</td>
	<td>857</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.47% [<b>41.3%</b>-47.6%]</td>
	<td>1,005</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.76% [<b>42.3%</b>-47.2%]</td>
	<td>1,644</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.07% [<b>42.5%</b>-45.7%]</td>
	<td>3,880</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>45.56% [<b>44.4%</b>-46.8%]</td>
	<td>6,779</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.07% [42.5%-<b>45.7%</b>]</td>
	<td>3,880</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>45.56% [44.4%-<b>46.8%</b>]</td>
	<td>6,779</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.64% [40.3%-<b>47.0%</b>]</td>
	<td>857</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.97% [44.8%-<b>47.2%</b>]</td>
	<td>6,914</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.76% [42.3%-<b>47.2%</b>]</td>
	<td>1,644</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-kayle"></span> Kayle</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.80% [51.4%-52.2%]</td>
	<td>65,578</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>46.02% [<b>40.8%</b>-51.2%]</td>
	<td>365</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.90% [<b>41.2%</b>-52.6%]</td>
	<td>307</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>46.99% [<b>41.8%</b>-52.2%]</td>
	<td>366</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>46.57% [<b>42.5%</b>-50.6%]</td>
	<td>614</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jayce"></span> Jayce</td>
	<td>49.31% [<b>43.4%</b>-55.2%]</td>
	<td>290</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>46.57% [42.5%-<b>50.6%</b>]</td>
	<td>614</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>46.02% [40.8%-<b>51.2%</b>]</td>
	<td>365</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-orianna"></span> Orianna</td>
	<td>48.40% [45.5%-<b>51.3%</b>]</td>
	<td>1,157</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>49.24% [47.0%-<b>51.5%</b>]</td>
	<td>1,992</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>49.41% [47.0%-<b>51.8%</b>]</td>
	<td>1,696</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-swain"></span> Swain</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.28% [50.0%-50.5%]</td>
	<td>159,106</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.79% [<b>40.5%</b>-47.1%]</td>
	<td>902</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.80% [<b>41.0%</b>-48.6%]</td>
	<td>703</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.05% [<b>41.3%</b>-46.8%]</td>
	<td>1,321</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.59% [<b>43.7%</b>-47.5%]</td>
	<td>2,779</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>48.04% [<b>44.1%</b>-52.0%]</td>
	<td>639</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.05% [41.3%-<b>46.8%</b>]</td>
	<td>1,321</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.79% [40.5%-<b>47.1%</b>]</td>
	<td>902</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.59% [43.7%-<b>47.5%</b>]</td>
	<td>2,779</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.98% [45.6%-<b>48.4%</b>]</td>
	<td>4,933</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.80% [41.0%-<b>48.6%</b>]</td>
	<td>703</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-azir"></span> Azir</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.75% [47.5%-48.0%]</td>
	<td>180,098</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.50% [<b>40.9%</b>-48.1%]</td>
	<td>773</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>43.49% [<b>41.0%</b>-46.0%]</td>
	<td>1,545</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>43.88% [<b>41.3%</b>-46.5%]</td>
	<td>1,488</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>43.44% [<b>41.7%</b>-45.2%]</td>
	<td>3,082</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.72% [<b>41.7%</b>-45.8%]</td>
	<td>2,374</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.59% [42.2%-<b>45.0%</b>]</td>
	<td>5,230</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>43.44% [41.7%-<b>45.2%</b>]</td>
	<td>3,082</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>44.04% [42.5%-<b>45.6%</b>]</td>
	<td>3,903</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>44.36% [43.0%-<b>45.7%</b>]</td>
	<td>5,396</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.72% [41.7%-<b>45.8%</b>]</td>
	<td>2,374</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-diana"></span> Diana</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.76% [49.6%-50.0%]</td>
	<td>230,935</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>42.94% [<b>40.0%</b>-45.9%]</td>
	<td>1,148</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.18% [<b>40.9%</b>-47.4%]</td>
	<td>928</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.84% [<b>41.6%</b>-48.1%]</td>
	<td>932</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.86% [<b>42.5%</b>-47.2%]</td>
	<td>1,792</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.33% [<b>43.2%</b>-49.4%]</td>
	<td>1,023</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>42.94% [40.0%-<b>45.9%</b>]</td>
	<td>1,148</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.72% [43.6%-<b>45.9%</b>]</td>
	<td>7,235</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.86% [42.5%-<b>47.2%</b>]</td>
	<td>1,792</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.18% [40.9%-<b>47.4%</b>]</td>
	<td>928</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.52% [45.4%-<b>47.7%</b>]</td>
	<td>7,501</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-leblanc"></span> LeBlanc</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.88% [47.7%-48.1%]</td>
	<td>340,352</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>42.06% [<b>40.2%</b>-43.9%]</td>
	<td>2,924</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.28% [<b>40.4%</b>-42.1%]</td>
	<td>13,900</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.09% [<b>41.2%</b>-46.9%]</td>
	<td>1,211</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.66% [<b>42.9%</b>-48.4%]</td>
	<td>1,279</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>44.26% [<b>43.6%</b>-44.9%]</td>
	<td>20,926</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.28% [40.4%-<b>42.1%</b>]</td>
	<td>13,900</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>42.06% [40.2%-<b>43.9%</b>]</td>
	<td>2,924</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>44.26% [43.6%-<b>44.9%</b>]</td>
	<td>20,926</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>45.46% [44.6%-<b>46.4%</b>]</td>
	<td>12,517</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.83% [45.0%-<b>46.7%</b>]</td>
	<td>13,079</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-talon"></span> Talon</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.16% [48.9%-49.4%]</td>
	<td>184,561</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.85% [<b>39.1%</b>-46.6%]</td>
	<td>686</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.24% [<b>40.4%</b>-48.1%]</td>
	<td>669</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.14% [<b>40.6%</b>-45.7%]</td>
	<td>1,509</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.22% [<b>42.8%</b>-47.6%]</td>
	<td>1,749</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.02% [<b>43.2%</b>-50.8%]</td>
	<td>689</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.14% [40.6%-<b>45.7%</b>]</td>
	<td>1,509</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.85% [39.1%-<b>46.6%</b>]</td>
	<td>686</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.10% [44.6%-<b>47.6%</b>]</td>
	<td>4,438</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.22% [42.8%-<b>47.6%</b>]</td>
	<td>1,749</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>46.81% [45.9%-<b>47.7%</b>]</td>
	<td>12,964</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-twisted-fate"></span> Twisted Fate</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.68% [48.4%-48.9%]</td>
	<td>157,570</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>42.08% [<b>39.3%</b>-44.9%]</td>
	<td>1,219</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.06% [<b>40.4%</b>-47.7%]</td>
	<td>733</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.82% [<b>41.2%</b>-46.5%]</td>
	<td>1,385</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.48% [<b>41.2%</b>-49.8%]</td>
	<td>543</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.17% [<b>42.2%</b>-48.1%]</td>
	<td>1,129</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>42.08% [39.3%-<b>44.9%</b>]</td>
	<td>1,219</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.82% [41.2%-<b>46.5%</b>]</td>
	<td>1,385</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.06% [40.4%-<b>47.7%</b>]</td>
	<td>733</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>46.13% [44.4%-<b>47.9%</b>]</td>
	<td>3,256</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>46.93% [45.8%-<b>48.0%</b>]</td>
	<td>8,443</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-naafiri"></span> Naafiri</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.88% [50.6%-51.2%]</td>
	<td>126,781</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>43.94% [<b>39.4%</b>-48.5%]</td>
	<td>471</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.04% [<b>40.3%</b>-49.8%]</td>
	<td>444</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.49% [<b>42.5%</b>-50.5%]</td>
	<td>628</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.62% [<b>43.7%</b>-49.5%]</td>
	<td>1,201</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>46.15% [<b>44.0%</b>-48.3%]</td>
	<td>2,121</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>46.41% [45.1%-<b>47.7%</b>]</td>
	<td>5,830</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>46.15% [44.0%-<b>48.3%</b>]</td>
	<td>2,121</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>43.94% [39.4%-<b>48.5%</b>]</td>
	<td>471</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>47.39% [46.1%-<b>48.7%</b>]</td>
	<td>5,889</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>48.07% [47.2%-<b>49.0%</b>]</td>
	<td>11,943</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-cho-gath"></span> Cho'Gath</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.69% [52.3%-53.1%]</td>
	<td>70,991</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>43.93% [<b>39.8%</b>-48.0%]</td>
	<td>585</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.67% [<b>40.1%</b>-51.2%]</td>
	<td>324</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>45.95% [<b>40.6%</b>-51.3%]</td>
	<td>346</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.50% [<b>42.6%</b>-52.4%]</td>
	<td>421</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.08% [<b>43.9%</b>-50.3%]</td>
	<td>962</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>43.93% [39.8%-<b>48.0%</b>]</td>
	<td>585</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.08% [43.9%-<b>50.3%</b>]</td>
	<td>962</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.49% [46.4%-<b>50.6%</b>]</td>
	<td>2,262</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.67% [40.1%-<b>51.2%</b>]</td>
	<td>324</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.14% [47.0%-<b>51.2%</b>]</td>
	<td>2,279</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-zoe"></span> Zoe</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.24% [48.0%-48.5%]</td>
	<td>183,952</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>40.82% [<b>39.7%</b>-42.0%]</td>
	<td>7,116</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.87% [<b>40.0%</b>-47.7%]</td>
	<td>661</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.59% [<b>40.8%</b>-46.3%]</td>
	<td>1,296</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.66% [<b>41.2%</b>-48.2%]</td>
	<td>806</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.92% [<b>41.2%</b>-48.7%]</td>
	<td>710</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>40.82% [39.7%-<b>42.0%</b>]</td>
	<td>7,116</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.59% [40.8%-<b>46.3%</b>]</td>
	<td>1,296</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.23% [44.9%-<b>47.5%</b>]</td>
	<td>5,771</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.87% [40.0%-<b>47.7%</b>]</td>
	<td>661</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.33% [42.9%-<b>47.8%</b>]</td>
	<td>1,652</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-pantheon"></span> Pantheon</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.21% [50.9%-51.5%]</td>
	<td>91,982</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.41% [<b>39.3%</b>-47.5%]</td>
	<td>585</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.37% [<b>40.0%</b>-48.7%]</td>
	<td>516</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.61% [<b>40.6%</b>-50.6%]</td>
	<td>399</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>46.62% [<b>41.9%</b>-51.4%]</td>
	<td>444</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.76% [<b>42.8%</b>-46.7%]</td>
	<td>2,598</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.76% [42.8%-<b>46.7%</b>]</td>
	<td>2,598</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.41% [39.3%-<b>47.5%</b>]</td>
	<td>585</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>46.99% [45.3%-<b>48.7%</b>]</td>
	<td>3,330</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.37% [40.0%-<b>48.7%</b>]</td>
	<td>516</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>46.55% [44.2%-<b>48.9%</b>]</td>
	<td>1,830</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-zed"></span> Zed</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.67% [47.5%-47.8%]</td>
	<td>468,495</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>40.87% [<b>38.7%</b>-43.0%]</td>
	<td>2,121</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>41.14% [<b>39.6%</b>-42.7%]</td>
	<td>3,998</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>40.96% [<b>39.9%</b>-42.0%]</td>
	<td>8,773</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.14% [<b>41.0%</b>-45.3%]</td>
	<td>2,121</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>43.73% [<b>41.4%</b>-46.1%]</td>
	<td>1,772</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>40.96% [39.9%-<b>42.0%</b>]</td>
	<td>8,773</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>41.14% [39.6%-<b>42.7%</b>]</td>
	<td>3,998</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>40.87% [38.7%-<b>43.0%</b>]</td>
	<td>2,121</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.14% [41.0%-<b>45.3%</b>]</td>
	<td>2,121</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.58% [43.8%-<b>45.3%</b>]</td>
	<td>17,198</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-annie"></span> Annie</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.52% [50.2%-50.8%]</td>
	<td>127,140</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.67% [<b>39.3%</b>-48.0%]</td>
	<td>522</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.86% [<b>39.5%</b>-48.2%]</td>
	<td>522</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.52% [<b>40.2%</b>-48.8%]</td>
	<td>539</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.96% [<b>41.5%</b>-50.4%]</td>
	<td>496</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.62% [<b>42.5%</b>-48.7%]</td>
	<td>1,028</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.67% [39.3%-<b>48.0%</b>]</td>
	<td>522</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.86% [39.5%-<b>48.2%</b>]</td>
	<td>522</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.94% [45.4%-<b>48.5%</b>]</td>
	<td>4,186</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.62% [42.5%-<b>48.7%</b>]</td>
	<td>1,028</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.52% [40.2%-<b>48.8%</b>]</td>
	<td>539</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-katarina"></span> Katarina</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.63% [47.5%-47.8%]</td>
	<td>541,111</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>39.92% [<b>38.4%</b>-41.4%]</td>
	<td>4,278</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>41.28% [<b>39.4%</b>-43.1%]</td>
	<td>2,853</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.56% [<b>40.6%</b>-44.6%]</td>
	<td>2,460</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.85% [<b>42.2%</b>-43.5%]</td>
	<td>22,140</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.40% [<b>42.4%</b>-46.4%]</td>
	<td>2,376</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>39.92% [38.4%-<b>41.4%</b>]</td>
	<td>4,278</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>41.28% [39.4%-<b>43.1%</b>]</td>
	<td>2,853</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.85% [42.2%-<b>43.5%</b>]</td>
	<td>22,140</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.56% [40.6%-<b>44.6%</b>]</td>
	<td>2,460</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>43.70% [42.7%-<b>44.7%</b>]</td>
	<td>9,298</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-malphite"></span> Malphite</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.73% [51.4%-52.1%]</td>
	<td>85,341</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.50% [<b>38.8%</b>-48.2%]</td>
	<td>439</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.50% [<b>38.8%</b>-46.2%]</td>
	<td>727</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>44.81% [<b>39.5%</b>-50.1%]</td>
	<td>357</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.43% [<b>40.9%</b>-50.0%]</td>
	<td>482</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.77% [<b>41.2%</b>-48.3%]</td>
	<td>775</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>44.27% [42.8%-<b>45.7%</b>]</td>
	<td>4,802</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.50% [38.8%-<b>46.2%</b>]</td>
	<td>727</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.50% [38.8%-<b>48.2%</b>]</td>
	<td>439</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.77% [41.2%-<b>48.3%</b>]</td>
	<td>775</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>47.78% [46.3%-<b>49.2%</b>]</td>
	<td>4,627</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-neeko"></span> Neeko</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.29% [48.9%-49.7%]</td>
	<td>75,506</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>41.12% [<b>36.4%</b>-45.9%]</td>
	<td>428</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>43.22% [<b>37.9%</b>-48.5%]</td>
	<td>347</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.42% [<b>39.5%</b>-51.3%]</td>
	<td>284</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.58% [<b>40.3%</b>-50.9%]</td>
	<td>351</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.59% [<b>40.4%</b>-52.7%]</td>
	<td>264</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>41.12% [36.4%-<b>45.9%</b>]</td>
	<td>428</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>46.22% [44.8%-<b>47.7%</b>]</td>
	<td>4,798</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.88% [44.0%-<b>47.8%</b>]</td>
	<td>2,744</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.62% [44.8%-<b>48.5%</b>]</td>
	<td>2,949</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>43.22% [37.9%-<b>48.5%</b>]</td>
	<td>347</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-smolder"></span> Smolder</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>44.86% [44.5%-45.2%]</td>
	<td>89,962</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>38.13% [<b>35.5%</b>-40.7%]</td>
	<td>1,382</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-azir"></span> Azir</td>
	<td>39.91% [<b>36.7%</b>-43.1%]</td>
	<td>937</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>42.13% [<b>37.5%</b>-46.7%]</td>
	<td>458</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.42% [<b>37.8%</b>-47.0%]</td>
	<td>462</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>41.81% [<b>38.1%</b>-45.5%]</td>
	<td>696</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>38.13% [35.5%-<b>40.7%</b>]</td>
	<td>1,382</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>40.19% [38.9%-<b>41.5%</b>]</td>
	<td>5,496</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-azir"></span> Azir</td>
	<td>39.91% [36.7%-<b>43.1%</b>]</td>
	<td>937</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>41.44% [39.7%-<b>43.2%</b>]</td>
	<td>3,166</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>41.86% [40.4%-<b>43.4%</b>]</td>
	<td>4,302</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-jayce"></span> Jayce</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.80% [48.4%-49.2%]</td>
	<td>78,540</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.79% [<b>35.8%</b>-47.8%]</td>
	<td>268</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.12% [<b>36.7%</b>-47.6%]</td>
	<td>330</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>44.12% [<b>38.5%</b>-49.7%]</td>
	<td>315</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.00% [<b>39.3%</b>-48.7%]</td>
	<td>450</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.46% [<b>39.7%</b>-47.2%]</td>
	<td>704</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.46% [39.7%-<b>47.2%</b>]</td>
	<td>704</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.12% [36.7%-<b>47.6%</b>]</td>
	<td>330</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.59% [43.6%-<b>47.6%</b>]</td>
	<td>2,395</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.79% [35.8%-<b>47.8%</b>]</td>
	<td>268</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.40% [42.6%-<b>48.2%</b>]</td>
	<td>1,273</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-qiyana"></span> Qiyana</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.82% [47.5%-48.1%]</td>
	<td>119,840</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>37.71% [<b>34.6%</b>-40.8%]</td>
	<td>989</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>39.67% [<b>36.5%</b>-42.9%]</td>
	<td>935</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.75% [<b>41.0%</b>-50.5%]</td>
	<td>448</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.66% [<b>41.1%</b>-50.2%]</td>
	<td>484</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.43% [<b>41.2%</b>-47.6%]</td>
	<td>970</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>37.71% [34.6%-<b>40.8%</b>]</td>
	<td>989</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>39.67% [36.5%-<b>42.9%</b>]</td>
	<td>935</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>45.29% [44.2%-<b>46.3%</b>]</td>
	<td>8,870</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.18% [43.4%-<b>47.0%</b>]</td>
	<td>3,107</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>45.34% [43.7%-<b>47.0%</b>]</td>
	<td>3,537</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ziggs"></span> Ziggs</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.92% [48.6%-49.3%]</td>
	<td>75,444</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>40.55% [<b>35.1%</b>-46.0%]</td>
	<td>323</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>41.32% [<b>35.3%</b>-47.3%]</td>
	<td>271</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>41.74% [<b>36.1%</b>-47.4%]</td>
	<td>309</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>45.30% [<b>41.1%</b>-49.5%]</td>
	<td>554</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>45.07% [<b>41.1%</b>-49.1%]</td>
	<td>619</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>40.55% [35.1%-<b>46.0%</b>]</td>
	<td>323</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>41.32% [35.3%-<b>47.3%</b>]</td>
	<td>271</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>41.74% [36.1%-<b>47.4%</b>]</td>
	<td>309</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.64% [43.5%-<b>47.8%</b>]</td>
	<td>2,145</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.30% [43.9%-<b>48.7%</b>]</td>
	<td>1,665</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-corki"></span> Corki</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>46.56% [46.2%-46.9%]</td>
	<td>68,676</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>39.74% [<b>34.2%</b>-45.3%]</td>
	<td>312</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.04% [<b>34.5%</b>-47.5%]</td>
	<td>229</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>40.50% [<b>36.6%</b>-44.4%]</td>
	<td>637</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.37% [<b>37.9%</b>-48.8%]</td>
	<td>332</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.52% [<b>38.4%</b>-50.6%]</td>
	<td>265</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>40.50% [36.6%-<b>44.4%</b>]</td>
	<td>637</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.78% [40.6%-<b>44.9%</b>]</td>
	<td>2,115</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>39.74% [34.2%-<b>45.3%</b>]</td>
	<td>312</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>42.65% [39.9%-<b>45.4%</b>]</td>
	<td>1,341</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>43.98% [42.3%-<b>45.6%</b>]</td>
	<td>3,567</td>
</tr>
</table>

</details>
### ADC

<details>
<summary>Click to view</summary>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-miss-fortune"></span> Miss Fortune</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>53.18% [53.1%-53.2%]</td>
	<td>2,222,778</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>50.33% [<b>49.3%</b>-51.4%]</td>
	<td>8,811</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>50.06% [<b>49.4%</b>-50.7%]</td>
	<td>26,801</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>50.53% [<b>49.6%</b>-51.5%]</td>
	<td>10,771</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>50.43% [<b>49.6%</b>-51.3%]</td>
	<td>13,540</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>50.71% [<b>49.7%</b>-51.7%]</td>
	<td>9,635</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>50.06% [49.4%-<b>50.7%</b>]</td>
	<td>26,801</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>50.30% [49.7%-<b>50.9%</b>]</td>
	<td>27,308</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>50.43% [49.6%-<b>51.3%</b>]</td>
	<td>13,540</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>50.33% [49.3%-<b>51.4%</b>]</td>
	<td>8,811</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>50.53% [49.6%-<b>51.5%</b>]</td>
	<td>10,771</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-vayne"></span> Vayne</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.65% [51.5%-51.8%]</td>
	<td>632,483</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>48.02% [<b>47.7%</b>-48.4%]</td>
	<td>81,841</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aphelios"></span> Aphelios</td>
	<td>49.48% [<b>48.5%</b>-50.4%]</td>
	<td>11,024</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>50.62% [<b>48.6%</b>-52.6%]</td>
	<td>2,552</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>50.05% [<b>48.9%</b>-51.2%]</td>
	<td>7,552</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>51.50% [<b>49.0%</b>-54.0%]</td>
	<td>1,592</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>48.02% [47.7%-<b>48.4%</b>]</td>
	<td>81,841</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aphelios"></span> Aphelios</td>
	<td>49.48% [48.5%-<b>50.4%</b>]</td>
	<td>11,024</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>50.12% [49.8%-<b>50.5%</b>]</td>
	<td>74,451</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>50.17% [49.8%-<b>50.6%</b>]</td>
	<td>67,027</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>49.95% [49.2%-<b>50.7%</b>]</td>
	<td>19,482</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-jinx"></span> Jinx</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.36% [51.3%-51.4%]</td>
	<td>1,904,680</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.29% [<b>47.1%</b>-49.5%]</td>
	<td>7,285</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>47.87% [<b>47.7%</b>-48.1%]</td>
	<td>269,635</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>49.28% [<b>47.9%</b>-50.7%]</td>
	<td>5,225</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>49.07% [<b>47.9%</b>-50.2%]</td>
	<td>7,442</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.98% [<b>48.3%</b>-49.6%]</td>
	<td>23,452</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>47.87% [47.7%-<b>48.1%</b>]</td>
	<td>269,635</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>48.94% [48.5%-<b>49.3%</b>]</td>
	<td>64,379</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.29% [47.1%-<b>49.5%</b>]</td>
	<td>7,285</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.98% [48.3%-<b>49.6%</b>]</td>
	<td>23,452</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>49.07% [47.9%-<b>50.2%</b>]</td>
	<td>7,442</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-jhin"></span> Jhin</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.84% [49.8%-49.9%]</td>
	<td>1,497,469</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>46.99% [<b>45.9%</b>-48.1%]</td>
	<td>7,918</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.38% [<b>46.6%</b>-48.2%]</td>
	<td>15,246</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>47.37% [<b>46.9%</b>-47.9%]</td>
	<td>41,411</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.28% [<b>47.0%</b>-49.6%]</td>
	<td>5,766</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>47.42% [<b>47.2%</b>-47.6%]</td>
	<td>219,926</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>47.42% [47.2%-<b>47.6%</b>]</td>
	<td>219,926</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>47.37% [46.9%-<b>47.9%</b>]</td>
	<td>41,411</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.65% [47.2%-<b>48.1%</b>]</td>
	<td>53,800</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>46.99% [45.9%-<b>48.1%</b>]</td>
	<td>7,918</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.38% [46.6%-<b>48.2%</b>]</td>
	<td>15,246</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-sivir"></span> Sivir</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.93% [50.8%-51.1%]</td>
	<td>395,140</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>47.20% [<b>46.2%</b>-48.2%]</td>
	<td>9,441</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.04% [<b>46.5%</b>-51.6%]</td>
	<td>1,525</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.20% [<b>46.5%</b>-49.9%]</td>
	<td>3,566</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>50.14% [<b>47.0%</b>-53.3%]</td>
	<td>1,001</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.92% [<b>47.0%</b>-48.8%]</td>
	<td>12,483</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>47.20% [46.2%-<b>48.2%</b>]</td>
	<td>9,441</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>48.08% [47.6%-<b>48.5%</b>]</td>
	<td>52,636</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.92% [47.0%-<b>48.8%</b>]</td>
	<td>12,483</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.20% [46.5%-<b>49.9%</b>]</td>
	<td>3,566</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>49.42% [48.9%-<b>49.9%</b>]</td>
	<td>42,614</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-caitlyn"></span> Caitlyn</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.91% [49.8%-50.0%]</td>
	<td>2,003,945</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.36% [<b>46.3%</b>-48.4%]</td>
	<td>8,826</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.44% [<b>46.3%</b>-48.6%]</td>
	<td>8,091</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.12% [<b>46.5%</b>-47.8%]</td>
	<td>22,526</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.16% [<b>46.8%</b>-49.5%]</td>
	<td>5,654</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>47.63% [<b>47.0%</b>-48.3%]</td>
	<td>23,896</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>47.30% [47.1%-<b>47.5%</b>]</td>
	<td>309,505</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.12% [46.5%-<b>47.8%</b>]</td>
	<td>22,526</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>47.63% [47.0%-<b>48.3%</b>]</td>
	<td>23,896</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.36% [46.3%-<b>48.4%</b>]</td>
	<td>8,826</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.74% [47.0%-<b>48.5%</b>]</td>
	<td>18,459</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-twitch"></span> Twitch</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.90% [50.8%-51.0%]</td>
	<td>486,441</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.00% [<b>41.8%</b>-44.2%]</td>
	<td>6,718</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>47.25% [<b>45.3%</b>-49.2%]</td>
	<td>2,512</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>49.83% [<b>47.5%</b>-52.2%]</td>
	<td>1,822</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>48.01% [<b>47.6%</b>-48.4%]</td>
	<td>66,075</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>50.27% [<b>48.0%</b>-52.5%]</td>
	<td>1,989</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.00% [41.8%-<b>44.2%</b>]</td>
	<td>6,718</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>48.01% [47.6%-<b>48.4%</b>]</td>
	<td>66,075</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>47.25% [45.3%-<b>49.2%</b>]</td>
	<td>2,512</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>50.03% [49.3%-<b>50.7%</b>]</td>
	<td>19,482</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>50.31% [49.9%-<b>50.8%</b>]</td>
	<td>50,681</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ezreal"></span> Ezreal</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.81% [48.7%-48.9%]</td>
	<td>1,798,545</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.13% [<b>44.3%</b>-45.9%]</td>
	<td>15,191</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>46.12% [<b>45.1%</b>-47.2%]</td>
	<td>8,750</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.73% [<b>45.3%</b>-46.1%]</td>
	<td>64,040</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.67% [<b>45.4%</b>-47.9%]</td>
	<td>6,205</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>46.42% [<b>46.0%</b>-46.9%]</td>
	<td>50,860</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.13% [44.3%-<b>45.9%</b>]</td>
	<td>15,191</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.73% [45.3%-<b>46.1%</b>]</td>
	<td>64,040</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>46.55% [46.3%-<b>46.8%</b>]</td>
	<td>238,139</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>46.42% [46.0%-<b>46.9%</b>]</td>
	<td>50,860</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>46.12% [45.1%-<b>47.2%</b>]</td>
	<td>8,750</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-nilah"></span> Nilah</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.74% [52.5%-53.0%]</td>
	<td>188,221</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.12% [<b>43.6%</b>-50.6%]</td>
	<td>817</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>49.18% [<b>44.7%</b>-53.7%]</td>
	<td>490</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xayah"></span> Xayah</td>
	<td>47.55% [<b>45.9%</b>-49.2%]</td>
	<td>3,859</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>50.68% [<b>47.0%</b>-54.4%]</td>
	<td>728</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>50.81% [<b>47.1%</b>-54.5%]</td>
	<td>734</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xayah"></span> Xayah</td>
	<td>47.55% [45.9%-<b>49.2%</b>]</td>
	<td>3,859</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>49.92% [49.3%-<b>50.5%</b>]</td>
	<td>26,801</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.12% [43.6%-<b>50.6%</b>]</td>
	<td>817</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>49.95% [49.2%-<b>50.7%</b>]</td>
	<td>19,849</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>49.94% [48.8%-<b>51.1%</b>]</td>
	<td>7,552</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-lucian"></span> Lucian</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.91% [48.8%-49.1%]</td>
	<td>445,995</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.80% [<b>44.2%</b>-49.4%]</td>
	<td>1,519</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.13% [<b>44.6%</b>-47.6%]</td>
	<td>4,517</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>46.16% [<b>44.7%</b>-47.7%]</td>
	<td>4,441</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>45.89% [<b>45.5%</b>-46.3%]</td>
	<td>59,283</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.27% [<b>45.7%</b>-50.8%]</td>
	<td>1,539</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>45.89% [45.5%-<b>46.3%</b>]</td>
	<td>59,283</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.13% [44.6%-<b>47.6%</b>]</td>
	<td>4,517</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>46.16% [44.7%-<b>47.7%</b>]</td>
	<td>4,441</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>47.30% [46.8%-<b>47.8%</b>]</td>
	<td>48,121</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.20% [46.4%-<b>48.0%</b>]</td>
	<td>15,444</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-smolder"></span> Smolder</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.74% [48.6%-48.9%]</td>
	<td>432,160</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>45.14% [<b>44.3%</b>-46.0%]</td>
	<td>12,965</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.73% [<b>44.4%</b>-49.0%]</td>
	<td>1,868</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.13% [<b>44.7%</b>-47.6%]</td>
	<td>4,704</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.38% [<b>44.9%</b>-49.8%]</td>
	<td>1,646</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.28% [<b>45.0%</b>-49.6%]</td>
	<td>1,842</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>45.14% [44.3%-<b>46.0%</b>]</td>
	<td>12,965</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>46.64% [46.2%-<b>47.1%</b>]</td>
	<td>57,436</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.13% [44.7%-<b>47.6%</b>]</td>
	<td>4,704</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>47.20% [46.8%-<b>47.6%</b>]</td>
	<td>49,615</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>47.26% [46.2%-<b>48.3%</b>]</td>
	<td>8,580</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ziggs"></span> Ziggs</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.98% [50.7%-51.2%]</td>
	<td>166,346</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>46.83% [<b>44.2%</b>-49.4%]</td>
	<td>1,486</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.17% [<b>44.4%</b>-52.0%]</td>
	<td>685</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.98% [<b>44.6%</b>-47.4%]</td>
	<td>4,871</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.30% [<b>44.9%</b>-51.7%]</td>
	<td>884</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zeri"></span> Zeri</td>
	<td>47.57% [<b>45.2%</b>-49.9%]</td>
	<td>1,776</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.98% [44.6%-<b>47.4%</b>]</td>
	<td>4,871</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>46.83% [44.2%-<b>49.4%</b>]</td>
	<td>1,486</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>49.00% [48.4%-<b>49.6%</b>]</td>
	<td>26,856</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>48.14% [46.5%-<b>49.8%</b>]</td>
	<td>3,701</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>48.09% [46.4%-<b>49.8%</b>]</td>
	<td>3,470</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-kog-maw"></span> Kog'Maw</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.84% [51.6%-52.1%]</td>
	<td>185,402</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.05% [<b>42.4%</b>-51.7%]</td>
	<td>459</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.93% [<b>44.3%</b>-51.6%]</td>
	<td>749</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.50% [<b>45.2%</b>-49.8%]</td>
	<td>1,947</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>49.77% [<b>46.4%</b>-53.1%]</td>
	<td>894</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>49.15% [<b>46.7%</b>-51.6%]</td>
	<td>1,601</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>48.68% [48.1%-<b>49.3%</b>]</td>
	<td>25,419</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.50% [45.2%-<b>49.8%</b>]</td>
	<td>1,947</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>48.88% [47.7%-<b>50.1%</b>]</td>
	<td>6,707</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>50.45% [49.7%-<b>51.2%</b>]</td>
	<td>19,964</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.93% [44.3%-<b>51.6%</b>]</td>
	<td>749</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-varus"></span> Varus</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.50% [48.4%-48.6%]</td>
	<td>599,255</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.29% [<b>43.7%</b>-48.9%]</td>
	<td>1,512</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.27% [<b>44.0%</b>-46.6%]</td>
	<td>5,807</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.69% [<b>44.5%</b>-48.9%]</td>
	<td>2,013</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.01% [<b>45.0%</b>-49.1%]</td>
	<td>2,359</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.42% [<b>45.0%</b>-47.8%]</td>
	<td>4,982</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>45.36% [45.0%-<b>45.7%</b>]</td>
	<td>81,089</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.27% [44.0%-<b>46.6%</b>]</td>
	<td>5,807</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>46.88% [46.0%-<b>47.8%</b>]</td>
	<td>12,970</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.42% [45.0%-<b>47.8%</b>]</td>
	<td>4,982</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>47.06% [46.3%-<b>47.8%</b>]</td>
	<td>16,103</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-veigar"></span> Veigar</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.24% [51.9%-52.6%]</td>
	<td>70,425</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>49.47% [<b>43.6%</b>-55.4%]</td>
	<td>287</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.53% [<b>43.8%</b>-53.3%]</td>
	<td>443</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>52.91% [<b>46.5%</b>-59.4%]</td>
	<td>240</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>52.78% [<b>47.1%</b>-58.5%]</td>
	<td>305</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>49.35% [<b>47.4%</b>-51.3%]</td>
	<td>2,553</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>49.45% [48.5%-<b>50.4%</b>]</td>
	<td>10,771</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>49.35% [47.4%-<b>51.3%</b>]</td>
	<td>2,553</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>49.72% [47.5%-<b>52.0%</b>]</td>
	<td>1,989</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>51.70% [50.5%-<b>52.9%</b>]</td>
	<td>7,285</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>51.71% [50.4%-<b>53.0%</b>]</td>
	<td>5,766</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-zeri"></span> Zeri</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.63% [49.4%-49.8%]</td>
	<td>233,419</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.78% [<b>42.0%</b>-49.5%]</td>
	<td>712</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.83% [<b>43.8%</b>-47.9%]</td>
	<td>2,304</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.26% [<b>44.0%</b>-52.5%]</td>
	<td>549</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.49% [<b>45.0%</b>-52.0%]</td>
	<td>798</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>47.87% [<b>45.7%</b>-50.0%]</td>
	<td>2,162</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.83% [43.8%-<b>47.9%</b>]</td>
	<td>2,304</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>47.33% [46.7%-<b>47.9%</b>]</td>
	<td>27,325</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>47.40% [46.8%-<b>48.0%</b>]</td>
	<td>28,802</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.47% [46.3%-<b>48.6%</b>]</td>
	<td>7,667</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>47.39% [46.1%-<b>48.7%</b>]</td>
	<td>5,973</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-corki"></span> Corki</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.03% [48.9%-49.2%]</td>
	<td>415,521</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.32% [<b>42.7%</b>-47.9%]</td>
	<td>1,456</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.81% [<b>43.7%</b>-47.9%]</td>
	<td>2,272</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.83% [<b>44.3%</b>-47.4%]</td>
	<td>4,289</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.06% [<b>46.2%</b>-47.9%]</td>
	<td>14,434</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>49.02% [<b>46.3%</b>-51.8%]</td>
	<td>1,338</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.83% [44.3%-<b>47.4%</b>]</td>
	<td>4,289</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>47.32% [46.9%-<b>47.7%</b>]</td>
	<td>55,168</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.06% [46.2%-<b>47.9%</b>]</td>
	<td>14,434</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.81% [43.7%-<b>47.9%</b>]</td>
	<td>2,272</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.32% [42.7%-<b>47.9%</b>]</td>
	<td>1,456</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-seraphine"></span> Seraphine</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.82% [50.4%-51.3%]</td>
	<td>47,131</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.08% [<b>40.6%</b>-53.5%]</td>
	<td>240</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>47.41% [<b>43.3%</b>-51.5%]</td>
	<td>599</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>49.35% [<b>43.7%</b>-55.0%]</td>
	<td>308</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lucian"></span> Lucian</td>
	<td>48.34% [<b>45.2%</b>-51.5%]</td>
	<td>995</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>50.00% [<b>45.4%</b>-54.6%]</td>
	<td>476</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>47.67% [46.4%-<b>48.9%</b>]</td>
	<td>6,454</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>48.49% [46.0%-<b>51.0%</b>]</td>
	<td>1,592</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mel"></span> Mel</td>
	<td>47.41% [43.3%-<b>51.5%</b>]</td>
	<td>599</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lucian"></span> Lucian</td>
	<td>48.34% [45.2%-<b>51.5%</b>]</td>
	<td>995</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>49.45% [47.0%-<b>51.9%</b>]</td>
	<td>1,666</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-mel"></span> Mel</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.63% [50.4%-50.8%]</td>
	<td>209,980</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.67% [<b>42.5%</b>-48.8%]</td>
	<td>983</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.47% [<b>43.3%</b>-49.6%]</td>
	<td>1,007</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>46.84% [<b>44.8%</b>-48.9%]</td>
	<td>2,393</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.46% [<b>45.3%</b>-49.7%]</td>
	<td>2,048</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.19% [<b>46.1%</b>-48.3%]</td>
	<td>7,710</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.19% [46.1%-<b>48.3%</b>]</td>
	<td>7,710</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.67% [42.5%-<b>48.8%</b>]</td>
	<td>983</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>46.84% [44.8%-<b>48.9%</b>]</td>
	<td>2,393</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>48.28% [47.5%-<b>49.0%</b>]</td>
	<td>17,707</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.47% [43.3%-<b>49.6%</b>]</td>
	<td>1,007</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ashe"></span> Ashe</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.53% [47.4%-47.6%]</td>
	<td>827,586</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.24% [<b>42.4%</b>-46.1%]</td>
	<td>2,852</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.33% [<b>43.2%</b>-45.5%]</td>
	<td>7,184</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.23% [<b>43.4%</b>-47.1%]</td>
	<td>2,978</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.06% [<b>44.1%</b>-48.0%]</td>
	<td>2,666</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>44.68% [<b>44.4%</b>-45.0%]</td>
	<td>124,104</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>44.68% [44.4%-<b>45.0%</b>]</td>
	<td>124,104</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.33% [43.2%-<b>45.5%</b>]</td>
	<td>7,184</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.24% [42.4%-<b>46.1%</b>]</td>
	<td>2,852</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>46.12% [45.8%-<b>46.4%</b>]</td>
	<td>97,645</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>46.06% [45.5%-<b>46.7%</b>]</td>
	<td>27,566</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-tristana"></span> Tristana</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.01% [47.9%-48.2%]</td>
	<td>455,341</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.37% [<b>43.0%</b>-47.7%]</td>
	<td>1,774</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.77% [<b>43.1%</b>-48.4%]</td>
	<td>1,398</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.88% [<b>43.4%</b>-46.3%]</td>
	<td>4,703</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.67% [<b>43.6%</b>-49.8%]</td>
	<td>1,039</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>46.05% [<b>44.0%</b>-48.1%]</td>
	<td>2,258</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>44.56% [44.2%-<b>44.9%</b>]</td>
	<td>75,593</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.88% [43.4%-<b>46.3%</b>]</td>
	<td>4,703</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.55% [44.0%-<b>47.1%</b>]</td>
	<td>4,272</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>47.29% [46.9%-<b>47.7%</b>]</td>
	<td>51,549</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.37% [43.0%-<b>47.7%</b>]</td>
	<td>1,774</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-kai-sa"></span> Kai'Sa</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.08% [48.0%-48.2%]</td>
	<td>1,071,543</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.58% [<b>42.6%</b>-44.5%]</td>
	<td>11,095</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>43.91% [<b>42.9%</b>-44.9%]</td>
	<td>10,547</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.03% [<b>43.4%</b>-46.6%]</td>
	<td>3,888</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>45.12% [<b>44.8%</b>-45.4%]</td>
	<td>132,506</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>46.02% [<b>45.5%</b>-46.5%]</td>
	<td>42,152</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.58% [42.6%-<b>44.5%</b>]</td>
	<td>11,095</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>43.91% [42.9%-<b>44.9%</b>]</td>
	<td>10,547</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>45.12% [44.8%-<b>45.4%</b>]</td>
	<td>132,506</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>46.08% [45.8%-<b>46.4%</b>]</td>
	<td>124,184</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>46.02% [45.5%-<b>46.5%</b>]</td>
	<td>42,152</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-draven"></span> Draven</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.35% [48.2%-48.5%]</td>
	<td>357,591</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.76% [<b>41.0%</b>-46.5%]</td>
	<td>1,332</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.41% [<b>42.9%</b>-45.9%]</td>
	<td>4,181</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.89% [<b>43.4%</b>-46.4%]</td>
	<td>4,466</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.65% [<b>43.6%</b>-49.7%]</td>
	<td>1,106</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.64% [<b>43.9%</b>-49.4%]</td>
	<td>1,295</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>45.41% [45.0%-<b>45.9%</b>]</td>
	<td>49,111</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.41% [42.9%-<b>45.9%</b>]</td>
	<td>4,181</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.89% [43.4%-<b>46.4%</b>]</td>
	<td>4,466</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.76% [41.0%-<b>46.5%</b>]</td>
	<td>1,332</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>47.23% [46.7%-<b>47.7%</b>]</td>
	<td>39,563</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-xayah"></span> Xayah</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.61% [49.4%-49.8%]</td>
	<td>318,684</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.36% [<b>41.6%</b>-49.1%]</td>
	<td>712</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.35% [<b>42.4%</b>-48.3%]</td>
	<td>1,140</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.24% [<b>43.2%</b>-49.3%]</td>
	<td>1,079</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.69% [<b>44.7%</b>-48.7%]</td>
	<td>2,508</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.20% [<b>45.2%</b>-51.2%]</td>
	<td>1,114</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>45.84% [45.3%-<b>46.3%</b>]</td>
	<td>39,425</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>46.89% [46.4%-<b>47.4%</b>]</td>
	<td>34,773</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.35% [42.4%-<b>48.3%</b>]</td>
	<td>1,140</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.69% [44.7%-<b>48.7%</b>]</td>
	<td>2,508</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.36% [41.6%-<b>49.1%</b>]</td>
	<td>712</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-swain"></span> Swain</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.27% [50.9%-51.7%]</td>
	<td>67,078</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.70% [<b>39.6%</b>-53.8%]</td>
	<td>197</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.76% [<b>42.0%</b>-49.6%]</td>
	<td>684</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>50.52% [<b>44.6%</b>-56.4%]</td>
	<td>287</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>48.72% [<b>44.7%</b>-52.7%]</td>
	<td>626</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>46.92% [<b>44.9%</b>-48.9%]</td>
	<td>2,508</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>46.92% [44.9%-<b>48.9%</b>]</td>
	<td>2,508</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.76% [42.0%-<b>49.6%</b>]</td>
	<td>684</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>48.96% [47.8%-<b>50.2%</b>]</td>
	<td>6,976</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>49.28% [48.3%-<b>50.3%</b>]</td>
	<td>9,635</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>48.71% [46.0%-<b>51.4%</b>]</td>
	<td>1,406</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-hwei"></span> Hwei</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.32% [50.9%-51.7%]</td>
	<td>70,366</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.21% [<b>41.5%</b>-52.9%]</td>
	<td>305</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>46.86% [<b>41.9%</b>-51.9%]</td>
	<td>399</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>49.01% [<b>43.3%</b>-54.7%]</td>
	<td>306</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.23% [<b>43.6%</b>-50.9%]</td>
	<td>760</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>50.64% [<b>44.9%</b>-56.3%]</td>
	<td>308</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>48.21% [46.2%-<b>50.3%</b>]</td>
	<td>2,381</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>49.66% [48.6%-<b>50.7%</b>]</td>
	<td>8,811</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.23% [43.6%-<b>50.9%</b>]</td>
	<td>760</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>48.74% [46.6%-<b>50.9%</b>]</td>
	<td>2,187</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>48.86% [46.3%-<b>51.4%</b>]</td>
	<td>1,492</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-yasuo"></span> Yasuo</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.93% [50.6%-51.3%]</td>
	<td>94,999</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>41.38% [<b>38.5%</b>-44.3%]</td>
	<td>1,155</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.47% [<b>41.6%</b>-51.3%]</td>
	<td>426</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.64% [<b>42.8%</b>-54.5%]</td>
	<td>296</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>44.57% [<b>42.9%</b>-46.3%]</td>
	<td>3,484</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kalista"></span> Kalista</td>
	<td>49.23% [<b>45.9%</b>-52.5%]</td>
	<td>914</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>41.38% [38.5%-<b>44.3%</b>]</td>
	<td>1,155</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>44.57% [42.9%-<b>46.3%</b>]</td>
	<td>3,484</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>49.34% [48.3%-<b>50.4%</b>]</td>
	<td>9,667</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>49.56% [48.7%-<b>50.4%</b>]</td>
	<td>13,540</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>48.42% [46.0%-<b>50.8%</b>]</td>
	<td>1,749</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-aphelios"></span> Aphelios</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.28% [49.1%-49.5%]</td>
	<td>307,238</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.07% [<b>41.3%</b>-46.8%]</td>
	<td>1,316</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.96% [<b>41.5%</b>-48.4%]</td>
	<td>825</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.30% [<b>43.5%</b>-47.1%]</td>
	<td>3,119</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.89% [<b>44.9%</b>-48.9%]</td>
	<td>2,416</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.15% [<b>45.1%</b>-51.2%]</td>
	<td>1,055</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>45.66% [45.1%-<b>46.2%</b>]</td>
	<td>36,466</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.07% [41.3%-<b>46.8%</b>]</td>
	<td>1,316</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.30% [43.5%-<b>47.1%</b>]</td>
	<td>3,119</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.96% [41.5%-<b>48.4%</b>]</td>
	<td>825</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>47.99% [47.5%-<b>48.5%</b>]</td>
	<td>39,369</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-kalista"></span> Kalista</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.63% [47.4%-47.9%]</td>
	<td>181,303</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>42.16% [<b>39.9%</b>-44.4%]</td>
	<td>1,921</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.69% [<b>41.4%</b>-50.0%]</td>
	<td>534</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.01% [<b>41.6%</b>-46.4%]</td>
	<td>1,688</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.53% [<b>41.8%</b>-51.2%]</td>
	<td>447</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>43.41% [<b>42.7%</b>-44.1%]</td>
	<td>21,027</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>43.41% [42.7%-<b>44.1%</b>]</td>
	<td>21,027</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>42.16% [39.9%-<b>44.4%</b>]</td>
	<td>1,921</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.01% [41.6%-<b>46.4%</b>]</td>
	<td>1,688</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>45.73% [45.0%-<b>46.4%</b>]</td>
	<td>19,315</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>46.02% [44.7%-<b>47.3%</b>]</td>
	<td>5,940</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-samira"></span> Samira</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.35% [48.2%-48.5%]</td>
	<td>484,988</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.06% [<b>40.8%</b>-45.3%]</td>
	<td>1,890</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.28% [<b>41.0%</b>-45.6%]</td>
	<td>1,832</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>42.48% [<b>41.4%</b>-43.6%]</td>
	<td>7,901</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.79% [<b>43.4%</b>-46.2%]</td>
	<td>4,972</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.90% [<b>43.5%</b>-48.3%]</td>
	<td>1,660</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>42.48% [41.4%-<b>43.6%</b>]</td>
	<td>7,901</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.06% [40.8%-<b>45.3%</b>]</td>
	<td>1,890</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.28% [41.0%-<b>45.6%</b>]</td>
	<td>1,832</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>45.70% [45.3%-<b>46.1%</b>]</td>
	<td>53,903</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>45.78% [45.4%-<b>46.2%</b>]</td>
	<td>70,893</td>
</tr>
</table>

</details>
### Support

<details>
<summary>Click to view</summary>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-nami"></span> Nami</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.15% [52.0%-52.3%]</td>
	<td>775,279</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.81% [<b>47.5%</b>-52.1%]</td>
	<td>1,921</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>50.01% [<b>48.3%</b>-51.7%]</td>
	<td>3,607</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.88% [<b>49.2%</b>-50.5%]</td>
	<td>23,454</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>50.29% [<b>49.4%</b>-51.1%]</td>
	<td>13,715</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>50.54% [<b>49.5%</b>-51.6%]</td>
	<td>8,452</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.88% [49.2%-<b>50.5%</b>]</td>
	<td>23,454</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>50.45% [49.8%-<b>51.1%</b>]</td>
	<td>25,794</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>50.30% [49.5%-<b>51.1%</b>]</td>
	<td>14,614</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>50.29% [49.4%-<b>51.1%</b>]</td>
	<td>13,715</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>50.98% [50.4%-<b>51.6%</b>]</td>
	<td>29,668</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-milio"></span> Milio</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.78% [51.6%-51.9%]</td>
	<td>383,637</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.09% [<b>46.8%</b>-49.4%]</td>
	<td>6,128</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.50% [<b>47.1%</b>-51.9%]</td>
	<td>1,733</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>51.05% [<b>47.8%</b>-54.3%]</td>
	<td>946</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>50.16% [<b>48.0%</b>-52.4%]</td>
	<td>2,061</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>50.75% [<b>48.4%</b>-53.1%]</td>
	<td>1,789</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.09% [46.8%-<b>49.4%</b>]</td>
	<td>6,128</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.53% [48.9%-<b>50.2%</b>]</td>
	<td>25,794</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>50.37% [49.8%-<b>50.9%</b>]</td>
	<td>31,858</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>49.91% [48.8%-<b>51.0%</b>]</td>
	<td>8,599</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-karma"></span> Karma</td>
	<td>50.41% [49.6%-<b>51.2%</b>]</td>
	<td>17,139</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-lulu"></span> Lulu</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.06% [51.0%-51.2%]</td>
	<td>1,004,740</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.05% [<b>46.3%</b>-49.8%]</td>
	<td>3,190</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.85% [<b>47.1%</b>-48.6%]</td>
	<td>16,260</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.86% [<b>48.1%</b>-49.6%]</td>
	<td>17,239</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>49.34% [<b>48.2%</b>-50.5%]</td>
	<td>7,559</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.75% [<b>48.4%</b>-49.1%]</td>
	<td>64,569</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.85% [47.1%-<b>48.6%</b>]</td>
	<td>16,260</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.75% [48.4%-<b>49.1%</b>]</td>
	<td>64,569</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.86% [48.1%-<b>49.6%</b>]</td>
	<td>17,239</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.12% [48.5%-<b>49.7%</b>]</td>
	<td>27,681</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.05% [46.3%-<b>49.8%</b>]</td>
	<td>3,190</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-karma"></span> Karma</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.38% [50.3%-50.5%]</td>
	<td>719,598</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.02% [<b>44.9%</b>-49.2%]</td>
	<td>2,133</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.95% [<b>47.0%</b>-48.9%]</td>
	<td>10,078</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.57% [<b>47.1%</b>-48.1%]</td>
	<td>38,895</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.81% [<b>47.1%</b>-48.5%]</td>
	<td>21,241</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>48.02% [<b>47.1%</b>-48.9%]</td>
	<td>13,055</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.57% [47.1%-<b>48.1%</b>]</td>
	<td>38,895</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.81% [47.1%-<b>48.5%</b>]</td>
	<td>21,241</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>48.02% [47.1%-<b>48.9%</b>]</td>
	<td>13,055</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.95% [47.0%-<b>48.9%</b>]</td>
	<td>10,078</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.02% [44.9%-<b>49.2%</b>]</td>
	<td>2,133</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-sona"></span> Sona</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.01% [51.8%-52.2%]</td>
	<td>240,981</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.84% [<b>44.6%</b>-53.1%]</td>
	<td>561</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>49.22% [<b>46.9%</b>-51.6%]</td>
	<td>1,806</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>51.65% [<b>47.4%</b>-55.9%]</td>
	<td>544</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>51.52% [<b>48.1%</b>-54.9%]</td>
	<td>854</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>49.68% [<b>48.3%</b>-51.1%]</td>
	<td>5,122</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.69% [48.9%-<b>50.5%</b>]</td>
	<td>14,614</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>49.68% [48.3%-<b>51.1%</b>]</td>
	<td>5,122</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>49.22% [46.9%-<b>51.6%</b>]</td>
	<td>1,806</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-thresh"></span> Thresh</td>
	<td>50.83% [49.8%-<b>51.8%</b>]</td>
	<td>9,852</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>50.38% [48.7%-<b>52.0%</b>]</td>
	<td>3,648</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-lux"></span> Lux</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.38% [50.3%-50.5%]</td>
	<td>1,287,054</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.19% [<b>46.2%</b>-48.2%]</td>
	<td>9,968</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.32% [<b>46.8%</b>-47.8%]</td>
	<td>45,068</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.79% [<b>47.0%</b>-50.5%]</td>
	<td>3,265</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.14% [<b>47.1%</b>-49.2%]</td>
	<td>8,525</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.73% [<b>47.2%</b>-50.3%]</td>
	<td>4,122</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.32% [46.8%-<b>47.8%</b>]</td>
	<td>45,068</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.19% [46.2%-<b>48.2%</b>]</td>
	<td>9,968</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.91% [47.4%-<b>48.4%</b>]</td>
	<td>42,620</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.00% [47.4%-<b>48.6%</b>]</td>
	<td>25,620</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.24% [47.8%-<b>48.7%</b>]</td>
	<td>55,571</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-zyra"></span> Zyra</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.15% [52.0%-52.3%]</td>
	<td>481,802</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.51% [<b>45.6%</b>-51.5%]</td>
	<td>1,144</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>48.42% [<b>46.8%</b>-50.1%]</td>
	<td>3,717</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>49.73% [<b>47.0%</b>-52.5%]</td>
	<td>1,303</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.73% [<b>47.8%</b>-49.7%]</td>
	<td>10,788</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.98% [<b>47.8%</b>-50.1%]</td>
	<td>7,345</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.73% [47.8%-<b>49.7%</b>]</td>
	<td>10,788</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>48.42% [46.8%-<b>50.1%</b>]</td>
	<td>3,717</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.98% [47.8%-<b>50.1%</b>]</td>
	<td>7,345</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.50% [48.6%-<b>50.4%</b>]</td>
	<td>12,670</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>50.10% [49.4%-<b>50.8%</b>]</td>
	<td>23,454</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-janna"></span> Janna</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.28% [51.1%-51.5%]</td>
	<td>289,358</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.52% [<b>46.1%</b>-53.0%]</td>
	<td>842</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.41% [<b>46.5%</b>-52.3%]</td>
	<td>1,188</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.27% [<b>46.8%</b>-49.7%]</td>
	<td>4,951</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>49.31% [<b>47.1%</b>-51.5%]</td>
	<td>2,058</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.97% [<b>47.5%</b>-50.4%]</td>
	<td>4,780</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.67% [48.0%-<b>49.4%</b>]</td>
	<td>20,620</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.62% [47.6%-<b>49.7%</b>]</td>
	<td>8,977</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.27% [46.8%-<b>49.7%</b>]</td>
	<td>4,951</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>49.41% [48.7%-<b>50.1%</b>]</td>
	<td>21,367</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.97% [47.5%-<b>50.4%</b>]</td>
	<td>4,780</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-rell"></span> Rell</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.95% [50.8%-51.1%]</td>
	<td>490,884</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.46% [<b>45.1%</b>-47.8%]</td>
	<td>5,312</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>47.60% [<b>46.2%</b>-49.0%]</td>
	<td>5,228</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.97% [<b>46.3%</b>-49.6%]</td>
	<td>3,721</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>47.43% [<b>46.5%</b>-48.4%]</td>
	<td>11,321</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.18% [<b>47.0%</b>-49.3%]</td>
	<td>7,646</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.46% [45.1%-<b>47.8%</b>]</td>
	<td>5,312</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>47.43% [46.5%-<b>48.4%</b>]</td>
	<td>11,321</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.83% [47.2%-<b>48.5%</b>]</td>
	<td>21,950</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>47.60% [46.2%-<b>49.0%</b>]</td>
	<td>5,228</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.21% [47.3%-<b>49.1%</b>]</td>
	<td>11,769</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-morgana"></span> Morgana</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.51% [51.4%-51.6%]</td>
	<td>752,842</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.52% [<b>45.2%</b>-49.9%]</td>
	<td>1,835</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.60% [<b>46.2%</b>-49.0%]</td>
	<td>5,018</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.70% [<b>46.3%</b>-49.1%]</td>
	<td>4,893</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>49.14% [<b>46.8%</b>-51.5%]</td>
	<td>1,811</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.60% [<b>46.8%</b>-48.4%]</td>
	<td>15,312</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.60% [46.8%-<b>48.4%</b>]</td>
	<td>15,312</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.80% [47.2%-<b>48.4%</b>]</td>
	<td>25,034</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.66% [46.9%-<b>48.4%</b>]</td>
	<td>16,054</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.60% [46.2%-<b>49.0%</b>]</td>
	<td>5,018</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.70% [46.3%-<b>49.1%</b>]</td>
	<td>4,893</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-maokai"></span> Maokai</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.19% [51.0%-51.4%]</td>
	<td>309,828</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.43% [<b>44.5%</b>-48.4%]</td>
	<td>2,696</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.05% [<b>46.2%</b>-47.9%]</td>
	<td>12,646</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>48.76% [<b>46.8%</b>-50.7%]</td>
	<td>2,590</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.61% [<b>47.3%</b>-49.9%]</td>
	<td>6,188</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>49.71% [<b>47.4%</b>-52.0%]</td>
	<td>1,953</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.05% [46.2%-<b>47.9%</b>]</td>
	<td>12,646</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.43% [44.5%-<b>48.4%</b>]</td>
	<td>2,696</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.61% [47.3%-<b>49.9%</b>]</td>
	<td>6,188</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>49.04% [47.9%-<b>50.2%</b>]</td>
	<td>7,989</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.10% [48.0%-<b>50.2%</b>]</td>
	<td>8,191</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-vel-koz"></span> Vel'Koz</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.65% [51.5%-51.8%]</td>
	<td>306,125</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.42% [<b>45.2%</b>-49.6%]</td>
	<td>2,058</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>49.53% [<b>46.1%</b>-52.9%]</td>
	<td>864</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.48% [<b>47.0%</b>-50.0%]</td>
	<td>4,426</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>49.31% [<b>47.6%</b>-51.1%]</td>
	<td>3,295</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>50.12% [<b>47.7%</b>-52.6%]</td>
	<td>1,654</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.42% [45.2%-<b>49.6%</b>]</td>
	<td>2,058</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.84% [48.0%-<b>49.7%</b>]</td>
	<td>14,830</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.77% [47.7%-<b>49.8%</b>]</td>
	<td>8,765</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.48% [47.0%-<b>50.0%</b>]</td>
	<td>4,426</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>49.16% [47.9%-<b>50.4%</b>]</td>
	<td>6,505</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-soraka"></span> Soraka</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.89% [50.7%-51.1%]</td>
	<td>360,674</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.94% [<b>44.7%</b>-51.2%]</td>
	<td>947</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>49.17% [<b>46.0%</b>-52.4%]</td>
	<td>968</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.99% [<b>47.3%</b>-48.7%]</td>
	<td>21,450</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.70% [<b>47.4%</b>-50.0%]</td>
	<td>6,188</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.57% [<b>47.6%</b>-49.5%]</td>
	<td>10,583</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.99% [47.3%-<b>48.7%</b>]</td>
	<td>21,450</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.57% [47.6%-<b>49.5%</b>]</td>
	<td>10,583</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.70% [47.4%-<b>50.0%</b>]</td>
	<td>6,188</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.86% [47.6%-<b>50.1%</b>]</td>
	<td>6,573</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>49.62% [49.0%-<b>50.2%</b>]</td>
	<td>26,158</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-senna"></span> Senna</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.32% [50.2%-50.5%]</td>
	<td>474,211</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.32% [<b>42.4%</b>-48.2%]</td>
	<td>1,187</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.62% [<b>45.8%</b>-47.5%]</td>
	<td>14,012</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.15% [<b>46.2%</b>-50.1%]</td>
	<td>2,517</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.68% [<b>46.6%</b>-48.8%]</td>
	<td>8,430</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.48% [<b>46.8%</b>-50.1%]</td>
	<td>3,675</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.62% [45.8%-<b>47.5%</b>]</td>
	<td>14,012</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.32% [42.4%-<b>48.2%</b>]</td>
	<td>1,187</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.67% [47.0%-<b>48.3%</b>]</td>
	<td>24,723</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.68% [46.6%-<b>48.8%</b>]</td>
	<td>8,430</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>48.32% [47.8%-<b>48.8%</b>]</td>
	<td>35,825</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-xerath"></span> Xerath</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.23% [51.1%-51.4%]</td>
	<td>420,188</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.19% [<b>45.3%</b>-51.1%]</td>
	<td>1,162</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.42% [<b>45.8%</b>-49.1%]</td>
	<td>3,610</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.12% [<b>46.3%</b>-47.9%]</td>
	<td>14,888</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.83% [<b>46.4%</b>-49.3%]</td>
	<td>4,929</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.96% [<b>46.8%</b>-49.2%]</td>
	<td>6,840</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.12% [46.3%-<b>47.9%</b>]</td>
	<td>14,888</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.42% [45.8%-<b>49.1%</b>]</td>
	<td>3,610</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.96% [46.8%-<b>49.2%</b>]</td>
	<td>6,840</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.83% [46.4%-<b>49.3%</b>]</td>
	<td>4,929</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>48.18% [47.0%-<b>49.4%</b>]</td>
	<td>7,160</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-tahm-kench"></span> Tahm Kench</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.29% [50.1%-50.4%]</td>
	<td>398,237</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.71% [<b>43.2%</b>-46.3%]</td>
	<td>4,088</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.52% [<b>45.7%</b>-49.4%]</td>
	<td>2,925</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.08% [<b>45.9%</b>-52.3%]</td>
	<td>988</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.37% [<b>46.4%</b>-48.4%]</td>
	<td>9,833</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.51% [<b>46.5%</b>-50.5%]</td>
	<td>2,525</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.71% [43.2%-<b>46.3%</b>]</td>
	<td>4,088</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.37% [46.4%-<b>48.4%</b>]</td>
	<td>9,833</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.75% [47.0%-<b>48.5%</b>]</td>
	<td>16,652</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.79% [46.8%-<b>48.7%</b>]</td>
	<td>11,245</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.68% [46.6%-<b>48.8%</b>]</td>
	<td>8,000</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-pantheon"></span> Pantheon</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.30% [50.1%-50.5%]</td>
	<td>298,093</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.17% [<b>42.2%</b>-46.1%]</td>
	<td>2,540</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.10% [<b>45.4%</b>-52.8%]</td>
	<td>727</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.11% [<b>45.7%</b>-50.5%]</td>
	<td>1,727</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>47.57% [<b>46.3%</b>-48.8%]</td>
	<td>6,249</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.70% [<b>46.5%</b>-50.9%]</td>
	<td>2,014</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.17% [42.2%-<b>46.1%</b>]</td>
	<td>2,540</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.43% [46.5%-<b>48.3%</b>]</td>
	<td>12,245</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>47.57% [46.3%-<b>48.8%</b>]</td>
	<td>6,249</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>48.21% [47.4%-<b>49.0%</b>]</td>
	<td>15,093</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.89% [46.6%-<b>49.2%</b>]</td>
	<td>5,796</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-leona"></span> Leona</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.92% [49.8%-50.0%]</td>
	<td>668,191</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.78% [<b>44.6%</b>-47.0%]</td>
	<td>6,679</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.65% [<b>45.3%</b>-48.0%]</td>
	<td>5,196</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.07% [<b>45.5%</b>-46.6%]</td>
	<td>32,823</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.22% [<b>45.7%</b>-48.7%]</td>
	<td>4,485</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.01% [<b>46.4%</b>-49.7%]</td>
	<td>3,703</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.07% [45.5%-<b>46.6%</b>]</td>
	<td>32,823</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.78% [44.6%-<b>47.0%</b>]</td>
	<td>6,679</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.65% [45.3%-<b>48.0%</b>]</td>
	<td>5,196</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.49% [46.6%-<b>48.3%</b>]</td>
	<td>13,980</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.52% [46.7%-<b>48.4%</b>]</td>
	<td>13,881</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-braum"></span> Braum</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.62% [50.5%-50.8%]</td>
	<td>375,503</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.94% [<b>44.5%</b>-49.4%]</td>
	<td>1,621</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.67% [<b>44.9%</b>-48.4%]</td>
	<td>3,342</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.02% [<b>45.1%</b>-48.9%]</td>
	<td>2,724</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.08% [<b>45.5%</b>-48.7%]</td>
	<td>3,889</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.90% [<b>45.7%</b>-52.1%]</td>
	<td>959</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.07% [46.2%-<b>47.9%</b>]</td>
	<td>14,096</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.01% [45.7%-<b>48.3%</b>]</td>
	<td>5,764</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.67% [44.9%-<b>48.4%</b>]</td>
	<td>3,342</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.48% [46.4%-<b>48.5%</b>]</td>
	<td>8,841</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.08% [45.5%-<b>48.7%</b>]</td>
	<td>3,889</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-shaco"></span> Shaco</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.02% [51.7%-52.3%]</td>
	<td>133,097</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.24% [<b>44.0%</b>-50.5%]</td>
	<td>925</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.48% [<b>44.9%</b>-54.0%]</td>
	<td>483</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.23% [<b>45.0%</b>-51.5%]</td>
	<td>937</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.74% [<b>45.3%</b>-50.2%]</td>
	<td>1,682</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.15% [<b>45.8%</b>-48.5%]</td>
	<td>5,259</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.15% [45.8%-<b>48.5%</b>]</td>
	<td>5,259</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>47.84% [46.7%-<b>49.0%</b>]</td>
	<td>7,738</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.85% [45.8%-<b>49.9%</b>]</td>
	<td>2,476</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.74% [45.3%-<b>50.2%</b>]</td>
	<td>1,682</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.58% [46.9%-<b>50.3%</b>]</td>
	<td>3,361</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-poppy"></span> Poppy</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.98% [50.8%-51.2%]</td>
	<td>246,406</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>46.38% [<b>44.5%</b>-48.3%]</td>
	<td>2,682</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.61% [<b>44.8%</b>-50.4%]</td>
	<td>1,281</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.83% [<b>45.6%</b>-50.1%]</td>
	<td>1,959</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.44% [<b>46.1%</b>-48.8%]</td>
	<td>5,349</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>47.71% [<b>46.4%</b>-49.0%]</td>
	<td>6,059</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>46.38% [44.5%-<b>48.3%</b>]</td>
	<td>2,682</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.44% [46.1%-<b>48.8%</b>]</td>
	<td>5,349</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>47.71% [46.4%-<b>49.0%</b>]</td>
	<td>6,059</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>48.12% [46.7%-<b>49.5%</b>]</td>
	<td>5,220</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>48.86% [48.0%-<b>49.8%</b>]</td>
	<td>12,097</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-yuumi"></span> Yuumi</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.06% [48.9%-49.2%]</td>
	<td>563,389</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.96% [<b>42.4%</b>-45.5%]</td>
	<td>4,003</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>45.49% [<b>44.7%</b>-46.3%]</td>
	<td>16,678</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.64% [<b>44.8%</b>-48.5%]</td>
	<td>2,804</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>46.04% [<b>45.1%</b>-47.0%]</td>
	<td>10,166</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.62% [<b>45.3%</b>-50.0%]</td>
	<td>1,835</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.96% [42.4%-<b>45.5%</b>]</td>
	<td>4,003</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>45.49% [44.7%-<b>46.3%</b>]</td>
	<td>16,678</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leona"></span> Leona</td>
	<td>46.21% [45.6%-<b>46.9%</b>]</td>
	<td>23,014</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>46.04% [45.1%-<b>47.0%</b>]</td>
	<td>10,166</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-thresh"></span> Thresh</td>
	<td>46.48% [45.9%-<b>47.1%</b>]</td>
	<td>26,945</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-thresh"></span> Thresh</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.33% [49.2%-49.4%]</td>
	<td>829,195</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.98% [<b>43.9%</b>-48.1%]</td>
	<td>2,303</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.46% [<b>44.7%</b>-46.3%]</td>
	<td>15,561</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.83% [<b>44.7%</b>-46.9%]</td>
	<td>7,933</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.27% [<b>45.6%</b>-47.0%]</td>
	<td>21,290</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.19% [<b>45.7%</b>-48.7%]</td>
	<td>4,418</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.46% [44.7%-<b>46.3%</b>]</td>
	<td>15,561</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.83% [44.7%-<b>46.9%</b>]</td>
	<td>7,933</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.27% [45.6%-<b>47.0%</b>]</td>
	<td>21,290</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.48% [46.0%-<b>47.0%</b>]</td>
	<td>36,293</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.79% [45.9%-<b>47.6%</b>]</td>
	<td>13,811</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-brand"></span> Brand</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.02% [50.8%-51.2%]</td>
	<td>345,470</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>45.98% [<b>42.5%</b>-49.4%]</td>
	<td>835</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.62% [<b>44.5%</b>-48.8%]</td>
	<td>2,121</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.08% [<b>45.1%</b>-49.1%]</td>
	<td>2,432</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.56% [<b>46.0%</b>-53.1%]</td>
	<td>799</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.75% [<b>46.3%</b>-49.2%]</td>
	<td>4,693</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.51% [46.6%-<b>48.4%</b>]</td>
	<td>11,488</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.62% [46.8%-<b>48.5%</b>]</td>
	<td>14,426</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.65% [46.6%-<b>48.7%</b>]</td>
	<td>8,486</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.62% [44.5%-<b>48.8%</b>]</td>
	<td>2,121</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.78% [46.6%-<b>49.0%</b>]</td>
	<td>6,728</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-zilean"></span> Zilean</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.92% [50.7%-51.2%]</td>
	<td>183,647</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>48.11% [<b>43.9%</b>-52.3%]</td>
	<td>557</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.74% [<b>44.1%</b>-49.3%]</td>
	<td>1,474</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.44% [<b>45.1%</b>-51.8%]</td>
	<td>900</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>48.18% [<b>46.1%</b>-50.2%]</td>
	<td>2,399</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.97% [<b>46.2%</b>-49.7%]</td>
	<td>3,179</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.64% [46.2%-<b>49.0%</b>]</td>
	<td>5,140</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.74% [44.1%-<b>49.3%</b>]</td>
	<td>1,474</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.64% [47.6%-<b>49.7%</b>]</td>
	<td>9,496</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.97% [46.2%-<b>49.7%</b>]</td>
	<td>3,179</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.15% [46.5%-<b>49.8%</b>]</td>
	<td>3,715</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-seraphine"></span> Seraphine</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.42% [49.3%-49.6%]</td>
	<td>516,084</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.50% [<b>43.6%</b>-49.4%]</td>
	<td>1,189</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.94% [<b>44.1%</b>-49.8%]</td>
	<td>1,259</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.96% [<b>44.3%</b>-47.6%]</td>
	<td>3,598</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.57% [<b>44.8%</b>-48.4%]</td>
	<td>3,062</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>46.70% [<b>45.8%</b>-47.6%]</td>
	<td>11,265</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.96% [44.3%-<b>47.6%</b>]</td>
	<td>3,598</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>46.70% [45.8%-<b>47.6%</b>]</td>
	<td>11,265</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.97% [46.2%-<b>47.7%</b>]</td>
	<td>17,473</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.63% [47.0%-<b>48.2%</b>]</td>
	<td>28,700</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.60% [47.0%-<b>48.2%</b>]</td>
	<td>23,666</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-alistar"></span> Alistar</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.02% [48.8%-49.2%]</td>
	<td>291,520</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.67% [<b>43.6%</b>-47.7%]</td>
	<td>2,303</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>44.97% [<b>43.7%</b>-46.2%]</td>
	<td>6,455</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.85% [<b>44.0%</b>-47.7%]</td>
	<td>2,955</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.96% [<b>44.0%</b>-47.9%]</td>
	<td>2,663</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>45.80% [<b>44.3%</b>-47.3%]</td>
	<td>4,617</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>44.97% [43.7%-<b>46.2%</b>]</td>
	<td>6,455</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>45.47% [44.5%-<b>46.5%</b>]</td>
	<td>10,276</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>45.80% [44.3%-<b>47.3%</b>]</td>
	<td>4,617</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>46.18% [44.8%-<b>47.6%</b>]</td>
	<td>4,883</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.02% [44.4%-<b>47.6%</b>]</td>
	<td>3,850</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-galio"></span> Galio</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.83% [50.5%-51.2%]</td>
	<td>97,613</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.08% [<b>43.4%</b>-50.8%]</td>
	<td>720</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>46.01% [<b>43.6%</b>-48.4%]</td>
	<td>1,682</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>47.70% [<b>44.9%</b>-50.5%]</td>
	<td>1,262</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.96% [<b>45.1%</b>-52.8%]</td>
	<td>676</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>48.85% [<b>45.2%</b>-52.5%]</td>
	<td>743</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>46.01% [43.6%-<b>48.4%</b>]</td>
	<td>1,682</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>48.12% [46.7%-<b>49.6%</b>]</td>
	<td>4,648</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.05% [46.0%-<b>50.1%</b>]</td>
	<td>2,387</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.60% [47.0%-<b>50.2%</b>]</td>
	<td>3,860</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.42% [46.6%-<b>50.2%</b>]</td>
	<td>3,079</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-taric"></span> Taric</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.63% [52.4%-52.9%]</td>
	<td>139,355</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.30% [<b>43.1%</b>-51.5%]</td>
	<td>575</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.26% [<b>43.5%</b>-51.1%]</td>
	<td>694</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.57% [<b>43.9%</b>-53.3%]</td>
	<td>455</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-bard"></span> Bard</td>
	<td>48.39% [<b>45.8%</b>-51.0%]</td>
	<td>1,461</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.23% [<b>46.2%</b>-50.3%]</td>
	<td>2,438</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.24% [47.0%-<b>49.5%</b>]</td>
	<td>6,154</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.12% [46.3%-<b>49.9%</b>]</td>
	<td>3,098</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-karma"></span> Karma</td>
	<td>48.66% [47.2%-<b>50.1%</b>]</td>
	<td>4,644</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.23% [46.2%-<b>50.3%</b>]</td>
	<td>2,438</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>49.27% [47.9%-<b>50.7%</b>]</td>
	<td>5,138</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-mel"></span> Mel</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.07% [48.9%-49.2%]</td>
	<td>421,731</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.53% [<b>42.8%</b>-46.3%]</td>
	<td>3,204</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>44.76% [<b>43.5%</b>-46.1%]</td>
	<td>5,933</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.56% [<b>43.7%</b>-47.4%]</td>
	<td>2,838</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>46.79% [<b>43.8%</b>-49.8%]</td>
	<td>1,107</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>45.42% [<b>44.3%</b>-46.5%]</td>
	<td>8,572</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>44.76% [43.5%-<b>46.1%</b>]</td>
	<td>5,933</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.53% [42.8%-<b>46.3%</b>]</td>
	<td>3,204</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>45.42% [44.3%-<b>46.5%</b>]</td>
	<td>8,572</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.05% [45.1%-<b>47.0%</b>]</td>
	<td>11,383</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>46.65% [46.0%-<b>47.3%</b>]</td>
	<td>23,138</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-elise"></span> Elise</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.86% [49.6%-50.1%]</td>
	<td>180,459</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.93% [<b>43.0%</b>-50.9%]</td>
	<td>637</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.08% [<b>43.3%</b>-48.9%]</td>
	<td>1,276</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.95% [<b>44.5%</b>-51.4%]</td>
	<td>830</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.08% [<b>44.6%</b>-47.6%]</td>
	<td>4,335</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.33% [<b>44.9%</b>-49.8%]</td>
	<td>1,648</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.08% [44.6%-<b>47.6%</b>]</td>
	<td>4,335</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>47.63% [46.7%-<b>48.5%</b>]</td>
	<td>12,849</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>46.83% [45.1%-<b>48.5%</b>]</td>
	<td>3,440</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.03% [45.4%-<b>48.7%</b>]</td>
	<td>3,763</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.08% [43.3%-<b>48.9%</b>]</td>
	<td>1,276</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-bard"></span> Bard</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.54% [49.3%-49.8%]</td>
	<td>182,531</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.53% [<b>42.4%</b>-50.7%]</td>
	<td>578</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.67% [<b>43.2%</b>-50.1%]</td>
	<td>827</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.63% [<b>43.4%</b>-49.8%]</td>
	<td>965</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.90% [<b>44.0%</b>-47.8%]</td>
	<td>2,732</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renata-glasc"></span> Renata Glasc</td>
	<td>47.33% [<b>44.9%</b>-49.7%]</td>
	<td>1,747</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.90% [44.0%-<b>47.8%</b>]</td>
	<td>2,732</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.34% [46.0%-<b>48.7%</b>]</td>
	<td>5,792</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.35% [46.0%-<b>48.7%</b>]</td>
	<td>5,613</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>47.11% [45.4%-<b>48.8%</b>]</td>
	<td>3,462</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.43% [46.0%-<b>48.9%</b>]</td>
	<td>4,625</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-shen"></span> Shen</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.68% [50.4%-51.0%]</td>
	<td>105,354</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.94% [<b>39.7%</b>-52.1%]</td>
	<td>259</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.58% [<b>42.9%</b>-50.3%]</td>
	<td>717</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.59% [<b>43.1%</b>-52.1%]</td>
	<td>498</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>45.79% [<b>43.6%</b>-48.0%]</td>
	<td>1,987</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renata-glasc"></span> Renata Glasc</td>
	<td>47.13% [<b>43.7%</b>-50.6%]</td>
	<td>838</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>45.79% [43.6%-<b>48.0%</b>]</td>
	<td>1,987</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>46.94% [45.4%-<b>48.5%</b>]</td>
	<td>4,256</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>47.35% [46.0%-<b>48.7%</b>]</td>
	<td>5,220</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.71% [44.2%-<b>49.2%</b>]</td>
	<td>1,582</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.50% [45.2%-<b>49.8%</b>]</td>
	<td>1,825</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-teemo"></span> Teemo</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>51.95% [51.6%-52.3%]</td>
	<td>97,387</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.29% [<b>42.6%</b>-47.9%]</td>
	<td>1,402</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.77% [<b>42.8%</b>-54.7%]</td>
	<td>285</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.77% [<b>43.2%</b>-54.3%]</td>
	<td>326</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>49.11% [<b>46.7%</b>-51.5%]</td>
	<td>1,745</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>51.38% [<b>46.9%</b>-55.8%]</td>
	<td>504</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.29% [42.6%-<b>47.9%</b>]</td>
	<td>1,402</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>49.31% [47.9%-<b>50.7%</b>]</td>
	<td>5,011</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.22% [47.3%-<b>51.1%</b>]</td>
	<td>2,726</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.17% [47.1%-<b>51.2%</b>]</td>
	<td>2,416</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>49.11% [46.7%-<b>51.5%</b>]</td>
	<td>1,745</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-renata-glasc"></span> Renata Glasc</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.08% [48.8%-49.3%]</td>
	<td>140,532</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.68% [<b>41.3%</b>-52.0%]</td>
	<td>347</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>44.83% [<b>42.8%</b>-46.8%]</td>
	<td>2,509</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.11% [<b>43.2%</b>-51.0%]</td>
	<td>658</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.36% [<b>43.5%</b>-49.2%]</td>
	<td>1,197</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>46.07% [<b>43.7%</b>-48.5%]</td>
	<td>1,747</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>44.83% [42.8%-<b>46.8%</b>]</td>
	<td>2,509</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>45.85% [44.2%-<b>47.5%</b>]</td>
	<td>3,847</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>46.90% [45.9%-<b>47.9%</b>]</td>
	<td>9,847</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.91% [43.8%-<b>48.0%</b>]</td>
	<td>2,326</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.98% [45.9%-<b>48.0%</b>]</td>
	<td>8,742</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-blitzcrank"></span> Blitzcrank</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.56% [48.4%-48.7%]</td>
	<td>515,534</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.44% [<b>41.9%</b>-45.0%]</td>
	<td>4,053</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.58% [<b>42.8%</b>-46.3%]</td>
	<td>3,230</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>44.89% [<b>43.3%</b>-46.5%]</td>
	<td>3,878</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>45.04% [<b>44.2%</b>-45.9%]</td>
	<td>13,563</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.80% [<b>44.9%</b>-48.7%]</td>
	<td>2,784</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.44% [41.9%-<b>45.0%</b>]</td>
	<td>4,053</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>45.04% [44.2%-<b>45.9%</b>]</td>
	<td>13,563</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leona"></span> Leona</td>
	<td>45.65% [45.0%-<b>46.3%</b>]</td>
	<td>22,688</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.58% [42.8%-<b>46.3%</b>]</td>
	<td>3,230</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>44.89% [43.3%-<b>46.5%</b>]</td>
	<td>3,878</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-rakan"></span> Rakan</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.48% [48.3%-48.7%]</td>
	<td>281,263</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.48% [<b>42.5%</b>-46.5%]</td>
	<td>2,428</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.46% [<b>42.8%</b>-50.1%]</td>
	<td>749</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>44.96% [<b>43.7%</b>-46.2%]</td>
	<td>6,552</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.47% [<b>43.8%</b>-47.2%]</td>
	<td>3,501</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.33% [<b>43.9%</b>-46.8%]</td>
	<td>4,526</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>44.96% [43.7%-<b>46.2%</b>]</td>
	<td>6,552</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>45.27% [44.3%-<b>46.3%</b>]</td>
	<td>10,191</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.48% [42.5%-<b>46.5%</b>]</td>
	<td>2,428</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.33% [43.9%-<b>46.8%</b>]</td>
	<td>4,526</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>45.98% [45.1%-<b>46.8%</b>]</td>
	<td>13,201</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-swain"></span> Swain</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.49% [48.3%-48.7%]</td>
	<td>333,386</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>44.49% [<b>41.1%</b>-47.9%]</td>
	<td>836</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>45.99% [<b>42.6%</b>-49.4%]</td>
	<td>848</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.09% [<b>42.7%</b>-49.5%]</td>
	<td>870</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>43.70% [<b>42.8%</b>-44.6%]</td>
	<td>13,372</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.37% [<b>43.1%</b>-45.6%]</td>
	<td>6,226</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>43.70% [42.8%-<b>44.6%</b>]</td>
	<td>13,372</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.37% [43.1%-<b>45.6%</b>]</td>
	<td>6,226</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>44.65% [43.7%-<b>45.6%</b>]</td>
	<td>10,191</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.77% [43.7%-<b>45.9%</b>]</td>
	<td>8,391</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>45.33% [44.6%-<b>46.1%</b>]</td>
	<td>16,902</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-fiddlesticks"></span> Fiddlesticks</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>52.18% [51.7%-52.6%]</td>
	<td>47,447</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.89% [<b>40.4%</b>-51.4%]</td>
	<td>329</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>46.93% [<b>42.4%</b>-51.4%]</td>
	<td>490</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.33% [<b>42.6%</b>-54.1%]</td>
	<td>300</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.25% [<b>43.2%</b>-51.3%]</td>
	<td>620</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.12% [<b>43.4%</b>-50.9%]</td>
	<td>713</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.12% [43.4%-<b>50.9%</b>]</td>
	<td>713</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.25% [43.2%-<b>51.3%</b>]</td>
	<td>620</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.89% [40.4%-<b>51.4%</b>]</td>
	<td>329</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>48.06% [44.7%-<b>51.4%</b>]</td>
	<td>878</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>46.93% [42.4%-<b>51.4%</b>]</td>
	<td>490</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-nautilus"></span> Nautilus</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.53% [48.4%-48.6%]</td>
	<td>738,922</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.00% [<b>41.9%</b>-44.1%]</td>
	<td>8,057</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>44.52% [<b>42.3%</b>-46.8%]</td>
	<td>1,954</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>44.22% [<b>43.6%</b>-44.9%]</td>
	<td>23,603</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.77% [<b>44.4%</b>-47.2%]</td>
	<td>5,055</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>45.13% [<b>44.6%</b>-45.7%]</td>
	<td>34,874</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.00% [41.9%-<b>44.1%</b>]</td>
	<td>8,057</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>44.22% [43.6%-<b>44.9%</b>]</td>
	<td>23,603</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>45.13% [44.6%-<b>45.7%</b>]</td>
	<td>34,874</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>45.43% [44.8%-<b>46.1%</b>]</td>
	<td>24,674</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>44.52% [42.3%-<b>46.8%</b>]</td>
	<td>1,954</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-neeko"></span> Neeko</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.81% [48.6%-49.0%]</td>
	<td>240,721</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>44.99% [<b>41.3%</b>-48.7%]</td>
	<td>729</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.96% [<b>41.9%</b>-50.0%]</td>
	<td>607</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.51% [<b>43.0%</b>-48.1%]</td>
	<td>1,516</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.69% [<b>43.0%</b>-48.4%]</td>
	<td>1,381</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.75% [<b>43.2%</b>-48.3%]</td>
	<td>1,519</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>44.54% [43.4%-<b>45.7%</b>]</td>
	<td>7,519</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.08% [44.8%-<b>47.3%</b>]</td>
	<td>6,430</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.51% [45.6%-<b>47.4%</b>]</td>
	<td>12,150</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>46.49% [45.4%-<b>47.5%</b>]</td>
	<td>9,003</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>46.04% [44.5%-<b>47.6%</b>]</td>
	<td>4,285</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-pyke"></span> Pyke</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.26% [48.1%-48.4%]</td>
	<td>523,071</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>44.01% [<b>41.7%</b>-46.3%]</td>
	<td>1,829</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>43.39% [<b>41.9%</b>-44.9%]</td>
	<td>4,180</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.90% [<b>42.1%</b>-45.7%]</td>
	<td>2,945</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.49% [<b>42.8%</b>-48.1%]</td>
	<td>1,422</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>44.45% [<b>43.2%</b>-45.7%]</td>
	<td>6,301</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>43.39% [41.9%-<b>44.9%</b>]</td>
	<td>4,180</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>44.60% [43.9%-<b>45.3%</b>]</td>
	<td>21,651</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>44.52% [43.6%-<b>45.4%</b>]</td>
	<td>12,560</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>44.45% [43.2%-<b>45.7%</b>]</td>
	<td>6,301</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.90% [42.1%-<b>45.7%</b>]</td>
	<td>2,945</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-sylas"></span> Sylas</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.47% [47.1%-47.8%]</td>
	<td>69,651</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>40.32% [<b>35.6%</b>-45.1%]</td>
	<td>429</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>42.35% [<b>39.5%</b>-45.2%]</td>
	<td>1,164</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>44.95% [<b>39.6%</b>-50.3%]</td>
	<td>347</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.57% [<b>39.8%</b>-49.3%]</td>
	<td>442</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.04% [<b>40.1%</b>-52.0%]</td>
	<td>278</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>40.32% [35.6%-<b>45.1%</b>]</td>
	<td>429</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>42.35% [39.5%-<b>45.2%</b>]</td>
	<td>1,164</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>43.93% [41.3%-<b>46.5%</b>]</td>
	<td>1,475</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>43.63% [40.3%-<b>46.9%</b>]</td>
	<td>896</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>44.24% [41.4%-<b>47.1%</b>]</td>
	<td>1,207</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-zoe"></span> Zoe</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>49.36% [48.9%-49.8%]</td>
	<td>50,269</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.66% [<b>38.9%</b>-50.4%]</td>
	<td>300</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.61% [<b>39.4%</b>-55.8%]</td>
	<td>147</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.65% [<b>40.1%</b>-51.2%]</td>
	<td>322</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>43.99% [<b>40.1%</b>-47.8%]</td>
	<td>666</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.39% [<b>40.5%</b>-54.3%]</td>
	<td>211</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>43.99% [40.1%-<b>47.8%</b>]</td>
	<td>666</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>45.55% [42.9%-<b>48.2%</b>]</td>
	<td>1,394</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.27% [41.9%-<b>48.7%</b>]</td>
	<td>857</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>47.58% [45.8%-<b>49.3%</b>]</td>
	<td>3,211</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nautilus"></span> Nautilus</td>
	<td>47.17% [44.9%-<b>49.4%</b>]</td>
	<td>1,982</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-leblanc"></span> LeBlanc</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>50.28% [49.8%-50.7%]</td>
	<td>53,977</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.55% [<b>35.8%</b>-47.3%]</td>
	<td>296</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.31% [<b>39.1%</b>-53.5%]</td>
	<td>190</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>44.59% [<b>41.0%</b>-48.1%]</td>
	<td>787</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.10% [<b>42.3%</b>-49.9%]</td>
	<td>681</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.62% [<b>42.5%</b>-48.7%]</td>
	<td>1,017</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.55% [35.8%-<b>47.3%</b>]</td>
	<td>296</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>45.92% [44.2%-<b>47.6%</b>]</td>
	<td>3,334</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>44.59% [41.0%-<b>48.1%</b>]</td>
	<td>787</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.62% [42.5%-<b>48.7%</b>]</td>
	<td>1,017</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.89% [42.7%-<b>49.1%</b>]</td>
	<td>963</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-veigar"></span> Veigar</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>47.89% [47.5%-48.3%]</td>
	<td>69,036</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>40.74% [<b>33.6%</b>-47.9%]</td>
	<td>189</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>44.67% [<b>37.6%</b>-51.8%]</td>
	<td>197</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>45.21% [<b>38.6%</b>-51.8%]</td>
	<td>230</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.56% [<b>39.4%</b>-49.7%]</td>
	<td>377</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>43.92% [<b>41.1%</b>-46.8%]</td>
	<td>1,227</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>43.34% [41.1%-<b>45.6%</b>]</td>
	<td>1,952</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>44.27% [41.9%-<b>46.7%</b>]</td>
	<td>1,730</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>43.92% [41.1%-<b>46.8%</b>]</td>
	<td>1,227</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>44.08% [41.2%-<b>47.0%</b>]</td>
	<td>1,166</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>40.74% [33.6%-<b>47.9%</b>]</td>
	<td>189</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-malphite"></span> Malphite</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.05% [47.7%-48.4%]</td>
	<td>110,463</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>40.41% [<b>34.6%</b>-46.2%]</td>
	<td>287</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.08% [<b>37.5%</b>-44.6%]</td>
	<td>774</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>44.54% [<b>39.1%</b>-50.0%]</td>
	<td>330</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>44.50% [<b>41.2%</b>-47.8%]</td>
	<td>883</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.23% [<b>42.0%</b>-46.5%]</td>
	<td>1,917</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.08% [37.5%-<b>44.6%</b>]</td>
	<td>774</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>44.26% [42.4%-<b>46.1%</b>]</td>
	<td>2,993</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>40.41% [34.6%-<b>46.2%</b>]</td>
	<td>287</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.62% [42.8%-<b>46.4%</b>]</td>
	<td>3,088</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.23% [42.0%-<b>46.5%</b>]</td>
	<td>1,917</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-ashe"></span> Ashe</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>45.26% [44.9%-45.6%]</td>
	<td>77,291</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>40.18% [<b>36.0%</b>-44.4%]</td>
	<td>545</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>41.15% [<b>37.5%</b>-44.8%]</td>
	<td>712</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>44.85% [<b>38.1%</b>-51.6%]</td>
	<td>214</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>42.16% [<b>38.2%</b>-46.1%]</td>
	<td>638</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>42.77% [<b>38.4%</b>-47.2%]</td>
	<td>505</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>40.18% [36.0%-<b>44.4%</b>]</td>
	<td>545</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>42.11% [39.7%-<b>44.5%</b>]</td>
	<td>1,719</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>41.15% [37.5%-<b>44.8%</b>]</td>
	<td>712</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>42.08% [39.3%-<b>44.9%</b>]</td>
	<td>1,269</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>43.48% [41.6%-<b>45.3%</b>]</td>
	<td>2,916</td>
</tr>
</table>

<table style="text-align:center; vertical-align:middle">
<tr>
	<th colspan=4><h1><span class="lol-icon lol-icon-big lol-hwei"></span> Hwei</h1></th>
</tr>
<tr>
	<th>Rank</th>
	<th>vs. Champion</th>
	<th>Win-rate</th>
	<th>Games</th>
</tr>
<tr>
	<td colspan=2><i>All</i></td>
	<td>48.79% [48.4%-49.1%]</td>
	<td>83,698</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>42.96% [<b>36.9%</b>-49.1%]</td>
	<td>263</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>43.01% [<b>37.1%</b>-48.9%]</td>
	<td>279</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.38% [<b>39.9%</b>-52.9%]</td>
	<td>235</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>43.89% [<b>40.1%</b>-47.7%]</td>
	<td>672</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>43.17% [<b>41.0%</b>-45.3%]</td>
	<td>2,147</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>43.17% [41.0%-<b>45.3%</b>]</td>
	<td>2,147</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>45.49% [43.8%-<b>47.2%</b>]</td>
	<td>3,537</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>43.89% [40.1%-<b>47.7%</b>]</td>
	<td>672</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>44.74% [41.4%-<b>48.1%</b>]</td>
	<td>885</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>45.74% [43.3%-<b>48.2%</b>]</td>
	<td>1,646</td>
</tr>
</table>

</details>
