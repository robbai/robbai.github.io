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

**Last update:** Patch 14.20

### Top

<details>
<summary>Click to view</summary>

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
	<td>53.21% [53.1%-53.3%]</td>
	<td>567,237</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>49.58% [<b>47.9%</b>-51.3%]</td>
	<td>3,431</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.84% [<b>47.9%</b>-49.8%]</td>
	<td>12,009</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>49.98% [<b>47.9%</b>-52.0%]</td>
	<td>2,375</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>49.93% [<b>49.0%</b>-50.8%]</td>
	<td>11,977</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>49.89% [<b>49.0%</b>-50.8%]</td>
	<td>13,303</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.84% [47.9%-<b>49.8%</b>]</td>
	<td>12,009</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>49.89% [49.0%-<b>50.8%</b>]</td>
	<td>13,303</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>49.93% [49.0%-<b>50.8%</b>]</td>
	<td>11,977</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>50.18% [49.5%-<b>50.9%</b>]</td>
	<td>19,024</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>50.28% [49.5%-<b>51.1%</b>]</td>
	<td>15,948</td>
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
	<td>52.89% [52.8%-53.0%]</td>
	<td>785,188</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.14% [<b>45.7%</b>-48.6%]</td>
	<td>4,714</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.24% [<b>47.5%</b>-49.0%]</td>
	<td>17,958</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>48.65% [<b>47.7%</b>-49.6%]</td>
	<td>12,193</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>48.63% [<b>48.0%</b>-49.2%]</td>
	<td>26,549</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.87% [<b>48.1%</b>-49.6%]</td>
	<td>18,470</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.14% [45.7%-<b>48.6%</b>]</td>
	<td>4,714</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.24% [47.5%-<b>49.0%</b>]</td>
	<td>17,958</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>48.63% [48.0%-<b>49.2%</b>]</td>
	<td>26,549</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>48.65% [47.7%-<b>49.6%</b>]</td>
	<td>12,193</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.87% [48.1%-<b>49.6%</b>]</td>
	<td>18,470</td>
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
	<td>52.29% [52.2%-52.4%]</td>
	<td>824,045</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.17% [<b>45.0%</b>-49.3%]</td>
	<td>2,099</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>47.89% [<b>46.6%</b>-49.2%]</td>
	<td>5,755</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.18% [<b>47.2%</b>-49.2%]</td>
	<td>9,871</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>49.03% [<b>47.7%</b>-50.4%]</td>
	<td>5,317</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>49.87% [<b>47.9%</b>-51.8%]</td>
	<td>2,641</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.53% [48.0%-<b>49.1%</b>]</td>
	<td>35,506</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.56% [48.1%-<b>49.1%</b>]</td>
	<td>39,121</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.18% [47.2%-<b>49.2%</b>]</td>
	<td>9,871</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>47.89% [46.6%-<b>49.2%</b>]</td>
	<td>5,755</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.17% [45.0%-<b>49.3%</b>]</td>
	<td>2,099</td>
</tr>
</table>

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
	<td>51.20% [51.1%-51.3%]</td>
	<td>602,181</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.23% [<b>44.6%</b>-49.9%]</td>
	<td>1,406</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.26% [<b>46.1%</b>-48.4%]</td>
	<td>7,256</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.40% [<b>46.8%</b>-48.0%]</td>
	<td>23,991</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>49.38% [<b>47.0%</b>-51.8%]</td>
	<td>1,695</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.52% [<b>47.0%</b>-50.0%]</td>
	<td>4,522</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.40% [46.8%-<b>48.0%</b>]</td>
	<td>23,991</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.26% [46.1%-<b>48.4%</b>]</td>
	<td>7,256</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.89% [47.1%-<b>48.6%</b>]</td>
	<td>17,556</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.53% [48.0%-<b>49.1%</b>]</td>
	<td>31,886</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>48.53% [47.7%-<b>49.4%</b>]</td>
	<td>13,195</td>
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
	<td>51.60% [51.5%-51.7%]</td>
	<td>556,675</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.55% [<b>45.0%</b>-48.1%]</td>
	<td>4,099</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.73% [<b>46.0%</b>-47.5%]</td>
	<td>16,727</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.71% [<b>46.3%</b>-49.1%]</td>
	<td>4,888</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>48.49% [<b>46.3%</b>-50.6%]</td>
	<td>2,153</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>48.78% [<b>46.4%</b>-51.1%]</td>
	<td>1,837</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.73% [46.0%-<b>47.5%</b>]</td>
	<td>16,727</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.55% [45.0%-<b>48.1%</b>]</td>
	<td>4,099</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.66% [46.9%-<b>48.5%</b>]</td>
	<td>15,811</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>48.44% [47.8%-<b>49.1%</b>]</td>
	<td>25,750</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.71% [46.3%-<b>49.1%</b>]</td>
	<td>4,888</td>
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
	<td>51.25% [51.1%-51.4%]</td>
	<td>341,354</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.31% [<b>45.3%</b>-47.3%]</td>
	<td>9,586</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>49.29% [<b>45.8%</b>-52.7%]</td>
	<td>842</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>48.27% [<b>46.1%</b>-50.5%]</td>
	<td>2,082</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.83% [<b>46.6%</b>-51.1%]</td>
	<td>1,925</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.47% [<b>46.6%</b>-50.3%]</td>
	<td>2,845</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.31% [45.3%-<b>47.3%</b>]</td>
	<td>9,586</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.54% [46.8%-<b>48.3%</b>]</td>
	<td>16,382</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.91% [46.9%-<b>48.9%</b>]</td>
	<td>9,972</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.97% [46.9%-<b>49.0%</b>]</td>
	<td>9,122</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.82% [47.9%-<b>49.7%</b>]</td>
	<td>13,092</td>
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
	<td>51.86% [51.7%-52.0%]</td>
	<td>428,854</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.11% [<b>45.4%</b>-46.8%]</td>
	<td>20,539</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.97% [<b>45.8%</b>-52.1%]</td>
	<td>1,017</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>48.83% [<b>46.6%</b>-51.1%]</td>
	<td>1,958</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.75% [<b>46.9%</b>-50.6%]</td>
	<td>2,991</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>48.16% [<b>47.2%</b>-49.1%]</td>
	<td>11,850</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.11% [45.4%-<b>46.8%</b>]</td>
	<td>20,539</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.17% [47.3%-<b>49.0%</b>]</td>
	<td>13,795</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>48.16% [47.2%-<b>49.1%</b>]</td>
	<td>11,850</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>48.36% [47.6%-<b>49.2%</b>]</td>
	<td>15,630</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.11% [48.0%-<b>50.2%</b>]</td>
	<td>7,701</td>
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
	<td>50.45% [50.3%-50.6%]</td>
	<td>701,822</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.09% [<b>45.1%</b>-47.1%]</td>
	<td>9,894</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.49% [<b>45.6%</b>-47.3%]</td>
	<td>14,055</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.48% [<b>45.7%</b>-47.3%]</td>
	<td>14,798</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.39% [<b>45.9%</b>-46.9%]</td>
	<td>34,882</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>46.84% [<b>46.1%</b>-47.5%]</td>
	<td>20,003</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.39% [45.9%-<b>46.9%</b>]</td>
	<td>34,882</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.09% [45.1%-<b>47.1%</b>]</td>
	<td>9,894</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.48% [45.7%-<b>47.3%</b>]</td>
	<td>14,798</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.49% [45.6%-<b>47.3%</b>]</td>
	<td>14,055</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>46.84% [46.1%-<b>47.5%</b>]</td>
	<td>20,003</td>
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
	<td>52.09% [52.0%-52.2%]</td>
	<td>528,295</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.37% [<b>43.6%</b>-47.1%]</td>
	<td>3,143</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.27% [<b>45.5%</b>-47.1%]</td>
	<td>15,779</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>47.31% [<b>45.6%</b>-49.0%]</td>
	<td>3,545</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.04% [<b>46.3%</b>-47.7%]</td>
	<td>19,771</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.15% [<b>46.5%</b>-47.8%]</td>
	<td>24,461</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.27% [45.5%-<b>47.1%</b>]</td>
	<td>15,779</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.37% [43.6%-<b>47.1%</b>]</td>
	<td>3,143</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.04% [46.3%-<b>47.7%</b>]</td>
	<td>19,771</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.15% [46.5%-<b>47.8%</b>]</td>
	<td>24,461</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.54% [46.7%-<b>48.4%</b>]</td>
	<td>13,750</td>
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
	<td>52.14% [51.9%-52.4%]</td>
	<td>131,177</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.55% [<b>45.2%</b>-49.9%]</td>
	<td>1,754</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>47.68% [<b>45.4%</b>-50.0%]</td>
	<td>1,894</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.96% [<b>45.5%</b>-48.4%]</td>
	<td>4,549</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>49.19% [<b>45.8%</b>-52.6%]</td>
	<td>860</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.44% [<b>45.8%</b>-49.1%]</td>
	<td>3,832</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.96% [45.5%-<b>48.4%</b>]</td>
	<td>4,549</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.81% [46.6%-<b>49.0%</b>]</td>
	<td>7,290</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.44% [45.8%-<b>49.1%</b>]</td>
	<td>3,832</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.55% [45.2%-<b>49.9%</b>]</td>
	<td>1,754</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>47.68% [45.4%-<b>50.0%</b>]</td>
	<td>1,894</td>
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
	<td>51.24% [51.0%-51.4%]</td>
	<td>267,130</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>48.43% [<b>45.0%</b>-51.9%]</td>
	<td>826</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.51% [<b>45.4%</b>-49.7%]</td>
	<td>2,172</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>48.69% [<b>45.6%</b>-51.7%]</td>
	<td>1,070</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.36% [<b>46.3%</b>-48.4%]</td>
	<td>8,868</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>48.61% [<b>46.3%</b>-50.9%]</td>
	<td>1,872</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.36% [46.3%-<b>48.4%</b>]</td>
	<td>8,868</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.83% [47.0%-<b>48.7%</b>]</td>
	<td>13,440</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.23% [47.2%-<b>49.2%</b>]</td>
	<td>9,999</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.50% [47.7%-<b>49.3%</b>]</td>
	<td>14,019</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>48.38% [47.1%-<b>49.6%</b>]</td>
	<td>6,414</td>
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
	<td>51.56% [51.4%-51.7%]</td>
	<td>338,503</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.16% [<b>44.2%</b>-46.1%]</td>
	<td>11,647</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.88% [<b>45.1%</b>-46.7%]</td>
	<td>16,510</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.51% [<b>45.8%</b>-51.2%]</td>
	<td>1,379</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>47.76% [<b>46.5%</b>-49.1%]</td>
	<td>5,911</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>47.75% [<b>46.8%</b>-48.7%]</td>
	<td>11,752</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.16% [44.2%-<b>46.1%</b>]</td>
	<td>11,647</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.88% [45.1%-<b>46.7%</b>]</td>
	<td>16,510</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>47.75% [46.8%-<b>48.7%</b>]</td>
	<td>11,752</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>47.76% [46.5%-<b>49.1%</b>]</td>
	<td>5,911</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>48.04% [47.0%-<b>49.1%</b>]</td>
	<td>8,666</td>
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
	<td>51.51% [51.3%-51.7%]</td>
	<td>273,215</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.78% [<b>44.7%</b>-46.9%]</td>
	<td>8,388</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.93% [<b>45.1%</b>-48.8%]</td>
	<td>2,898</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>48.63% [<b>46.0%</b>-51.2%]</td>
	<td>1,499</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.27% [<b>46.6%</b>-50.0%]</td>
	<td>3,431</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.83% [<b>46.9%</b>-48.7%]</td>
	<td>12,748</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.78% [44.7%-<b>46.9%</b>]</td>
	<td>8,388</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.83% [46.9%-<b>48.7%</b>]</td>
	<td>12,748</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.93% [45.1%-<b>48.8%</b>]</td>
	<td>2,898</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.27% [46.6%-<b>50.0%</b>]</td>
	<td>3,431</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>49.30% [48.3%-<b>50.3%</b>]</td>
	<td>10,078</td>
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
	<td>49.10% [48.9%-49.3%]</td>
	<td>439,064</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.40% [<b>43.6%</b>-45.2%]</td>
	<td>15,393</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.30% [<b>44.4%</b>-46.2%]</td>
	<td>12,520</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.62% [<b>44.5%</b>-48.8%]</td>
	<td>2,192</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.61% [<b>44.8%</b>-46.4%]</td>
	<td>16,479</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.24% [<b>45.2%</b>-49.3%]</td>
	<td>2,388</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.40% [43.6%-<b>45.2%</b>]</td>
	<td>15,393</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.30% [44.4%-<b>46.2%</b>]</td>
	<td>12,520</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.61% [44.8%-<b>46.4%</b>]</td>
	<td>16,479</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.52% [45.6%-<b>47.5%</b>]</td>
	<td>10,986</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.69% [45.7%-<b>47.6%</b>]</td>
	<td>11,256</td>
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
	<td>50.12% [50.0%-50.3%]</td>
	<td>450,886</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.77% [<b>44.1%</b>-47.5%]</td>
	<td>3,358</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.14% [<b>44.4%</b>-45.9%]</td>
	<td>16,895</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.78% [<b>44.4%</b>-47.2%]</td>
	<td>5,188</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.00% [<b>45.0%</b>-47.0%]</td>
	<td>9,669</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.20% [<b>45.2%</b>-49.2%]</td>
	<td>2,496</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.14% [44.4%-<b>45.9%</b>]</td>
	<td>16,895</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.00% [45.0%-<b>47.0%</b>]</td>
	<td>9,669</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.20% [45.3%-<b>47.1%</b>]</td>
	<td>11,792</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.78% [44.4%-<b>47.2%</b>]</td>
	<td>5,188</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.46% [45.5%-<b>47.4%</b>]</td>
	<td>11,087</td>
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
	<td>50.36% [50.2%-50.5%]</td>
	<td>737,053</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.97% [<b>44.2%</b>-45.7%]</td>
	<td>16,826</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>45.13% [<b>44.3%</b>-45.9%]</td>
	<td>15,374</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.04% [<b>44.5%</b>-45.6%]</td>
	<td>28,883</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.25% [<b>44.6%</b>-47.9%]</td>
	<td>3,749</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.52% [<b>45.2%</b>-47.9%]</td>
	<td>5,611</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.04% [44.5%-<b>45.6%</b>]</td>
	<td>28,883</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.97% [44.2%-<b>45.7%</b>]</td>
	<td>16,826</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>45.13% [44.3%-<b>45.9%</b>]</td>
	<td>15,374</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.99% [45.3%-<b>46.7%</b>]</td>
	<td>19,855</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.14% [45.5%-<b>46.8%</b>]</td>
	<td>22,609</td>
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
	<td>50.31% [50.1%-50.5%]</td>
	<td>299,211</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.45% [<b>43.6%</b>-47.3%]</td>
	<td>2,988</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.25% [<b>43.9%</b>-48.6%]</td>
	<td>1,866</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>46.84% [<b>44.5%</b>-49.1%]</td>
	<td>1,885</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.49% [<b>45.4%</b>-47.6%]</td>
	<td>7,875</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.46% [<b>45.6%</b>-47.3%]</td>
	<td>13,169</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.45% [43.6%-<b>47.3%</b>]</td>
	<td>2,988</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.46% [45.6%-<b>47.3%</b>]</td>
	<td>13,169</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.49% [45.4%-<b>47.6%</b>]</td>
	<td>7,875</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>46.70% [45.7%-<b>47.7%</b>]</td>
	<td>10,081</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.72% [45.6%-<b>47.8%</b>]</td>
	<td>8,386</td>
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
	<td>48.31% [48.2%-48.4%]</td>
	<td>733,379</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.12% [<b>42.9%</b>-45.3%]</td>
	<td>6,952</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.16% [<b>43.7%</b>-46.6%]</td>
	<td>4,544</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>45.73% [<b>44.1%</b>-47.4%]</td>
	<td>3,676</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.11% [<b>44.5%</b>-45.7%]</td>
	<td>26,327</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.40% [<b>44.6%</b>-46.2%]</td>
	<td>15,642</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.12% [42.9%-<b>45.3%</b>]</td>
	<td>6,952</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.11% [44.5%-<b>45.7%</b>]</td>
	<td>26,327</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.36% [44.8%-<b>45.9%</b>]</td>
	<td>29,955</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.40% [44.6%-<b>46.2%</b>]</td>
	<td>15,642</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>45.63% [45.0%-<b>46.2%</b>]</td>
	<td>26,887</td>
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
	<td>51.55% [51.4%-51.7%]</td>
	<td>342,561</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.56% [<b>43.6%</b>-47.5%]</td>
	<td>2,680</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.68% [<b>43.7%</b>-45.7%]</td>
	<td>9,863</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.76% [<b>45.5%</b>-52.0%]</td>
	<td>968</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.87% [<b>45.8%</b>-47.9%]</td>
	<td>9,422</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.78% [<b>45.9%</b>-47.7%]</td>
	<td>11,626</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.68% [43.7%-<b>45.7%</b>]</td>
	<td>9,863</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.56% [43.6%-<b>47.5%</b>]</td>
	<td>2,680</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.78% [45.9%-<b>47.7%</b>]</td>
	<td>11,626</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.87% [45.8%-<b>47.9%</b>]</td>
	<td>9,422</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.14% [46.4%-<b>47.9%</b>]</td>
	<td>17,282</td>
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
	<td>48.99% [48.9%-49.1%]</td>
	<td>741,294</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.52% [<b>42.9%</b>-44.2%]</td>
	<td>22,771</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.86% [<b>43.6%</b>-46.1%]</td>
	<td>6,694</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.36% [<b>43.7%</b>-45.0%]</td>
	<td>25,636</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.79% [<b>44.5%</b>-49.1%]</td>
	<td>1,823</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.53% [<b>44.5%</b>-48.5%]</td>
	<td>2,452</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.52% [42.9%-<b>44.2%</b>]</td>
	<td>22,771</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.36% [43.7%-<b>45.0%</b>]</td>
	<td>25,636</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.33% [44.7%-<b>45.9%</b>]</td>
	<td>27,907</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.86% [43.6%-<b>46.1%</b>]</td>
	<td>6,694</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.31% [45.7%-<b>46.9%</b>]</td>
	<td>25,079</td>
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
	<td>49.51% [49.4%-49.6%]</td>
	<td>759,121</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.09% [<b>42.7%</b>-45.5%]</td>
	<td>5,178</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.07% [<b>43.6%</b>-48.5%]</td>
	<td>1,680</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.32% [<b>44.0%</b>-46.7%]</td>
	<td>5,302</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.74% [<b>44.0%</b>-45.4%]</td>
	<td>20,216</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>46.27% [<b>45.5%</b>-47.0%]</td>
	<td>19,125</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.74% [44.0%-<b>45.4%</b>]</td>
	<td>20,216</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.09% [42.7%-<b>45.5%</b>]</td>
	<td>5,178</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.32% [44.0%-<b>46.7%</b>]</td>
	<td>5,302</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>46.27% [45.5%-<b>47.0%</b>]</td>
	<td>19,125</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.66% [46.0%-<b>47.4%</b>]</td>
	<td>20,444</td>
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
	<td>49.86% [49.7%-50.0%]</td>
	<td>295,420</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.16% [<b>42.9%</b>-49.5%]</td>
	<td>912</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.19% [<b>43.6%</b>-46.8%]</td>
	<td>3,917</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.97% [<b>43.7%</b>-46.3%]</td>
	<td>5,784</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.57% [<b>43.7%</b>-45.4%]</td>
	<td>13,728</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.37% [<b>43.8%</b>-48.9%]</td>
	<td>1,544</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.57% [43.7%-<b>45.4%</b>]</td>
	<td>13,728</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.99% [44.0%-<b>45.9%</b>]</td>
	<td>11,017</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.18% [44.1%-<b>46.2%</b>]</td>
	<td>8,954</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.97% [43.7%-<b>46.3%</b>]</td>
	<td>5,784</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.19% [43.6%-<b>46.8%</b>]</td>
	<td>3,917</td>
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
	<td>49.42% [49.3%-49.6%]</td>
	<td>489,760</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.53% [<b>41.7%</b>-43.4%]</td>
	<td>14,368</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.56% [<b>43.6%</b>-45.5%]</td>
	<td>10,638</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.49% [<b>44.1%</b>-46.8%]</td>
	<td>5,515</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.41% [<b>44.4%</b>-50.4%]</td>
	<td>1,099</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.23% [<b>44.5%</b>-46.0%]</td>
	<td>18,380</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.53% [41.7%-<b>43.4%</b>]</td>
	<td>14,368</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.56% [43.6%-<b>45.5%</b>]</td>
	<td>10,638</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.23% [44.5%-<b>46.0%</b>]</td>
	<td>18,380</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.57% [44.7%-<b>46.4%</b>]</td>
	<td>14,714</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.01% [45.3%-<b>46.7%</b>]</td>
	<td>22,522</td>
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
	<td>52.39% [52.1%-52.7%]</td>
	<td>106,473</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.81% [<b>40.1%</b>-47.6%]</td>
	<td>703</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.96% [<b>43.2%</b>-46.7%]</td>
	<td>3,303</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.91% [<b>43.5%</b>-50.3%]</td>
	<td>857</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.23% [<b>43.6%</b>-46.9%]</td>
	<td>3,732</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>47.84% [<b>45.0%</b>-50.7%]</td>
	<td>1,248</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.96% [43.2%-<b>46.7%</b>]</td>
	<td>3,303</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.23% [43.6%-<b>46.9%</b>]</td>
	<td>3,732</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.81% [40.1%-<b>47.6%</b>]</td>
	<td>703</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.91% [43.5%-<b>50.3%</b>]</td>
	<td>857</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>47.84% [45.0%-<b>50.7%</b>]</td>
	<td>1,248</td>
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
	<td>50.00% [49.9%-50.1%]</td>
	<td>451,088</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.56% [<b>42.9%</b>-46.3%]</td>
	<td>3,418</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.69% [<b>43.2%</b>-48.2%]</td>
	<td>1,624</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.51% [<b>43.4%</b>-49.7%]</td>
	<td>1,004</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.81% [<b>44.0%</b>-47.6%]</td>
	<td>2,949</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.47% [<b>44.2%</b>-46.7%]</td>
	<td>6,319</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.56% [42.9%-<b>46.3%</b>]</td>
	<td>3,418</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.47% [44.2%-<b>46.7%</b>]</td>
	<td>6,319</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.77% [46.0%-<b>47.5%</b>]</td>
	<td>18,872</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>46.78% [45.9%-<b>47.6%</b>]</td>
	<td>13,445</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.81% [44.0%-<b>47.6%</b>]</td>
	<td>2,949</td>
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
	<td>51.02% [50.8%-51.3%]</td>
	<td>154,793</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.44% [<b>42.9%</b>-46.0%]</td>
	<td>4,221</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.49% [<b>43.2%</b>-45.8%]</td>
	<td>5,554</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.82% [<b>43.2%</b>-50.4%]</td>
	<td>771</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.14% [<b>44.0%</b>-46.3%]</td>
	<td>7,375</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.56% [<b>44.0%</b>-51.1%]</td>
	<td>799</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.49% [43.2%-<b>45.8%</b>]</td>
	<td>5,554</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.44% [42.9%-<b>46.0%</b>]</td>
	<td>4,221</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.14% [44.0%-<b>46.3%</b>]</td>
	<td>7,375</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>46.31% [44.3%-<b>48.3%</b>]</td>
	<td>2,414</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.33% [45.6%-<b>49.1%</b>]</td>
	<td>3,216</td>
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
	<td>48.87% [48.7%-49.0%]</td>
	<td>447,339</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.53% [<b>42.6%</b>-44.5%]</td>
	<td>11,325</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.32% [<b>43.1%</b>-45.5%]</td>
	<td>7,116</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.47% [<b>43.6%</b>-47.3%]</td>
	<td>2,839</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.78% [<b>43.9%</b>-45.7%]</td>
	<td>12,232</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.84% [<b>44.0%</b>-45.7%]</td>
	<td>13,491</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.53% [42.6%-<b>44.5%</b>]</td>
	<td>11,325</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.32% [43.1%-<b>45.5%</b>]</td>
	<td>7,116</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.81% [44.0%-<b>45.6%</b>]</td>
	<td>16,116</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.78% [43.9%-<b>45.7%</b>]</td>
	<td>12,232</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.84% [44.0%-<b>45.7%</b>]</td>
	<td>13,491</td>
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
	<td>49.09% [48.9%-49.3%]</td>
	<td>248,616</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.30% [<b>42.7%</b>-47.9%]</td>
	<td>1,488</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.17% [<b>42.9%</b>-45.4%]</td>
	<td>6,036</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.42% [<b>43.1%</b>-51.7%]</td>
	<td>542</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.47% [<b>43.4%</b>-45.6%]</td>
	<td>7,887</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.98% [<b>43.4%</b>-46.6%]</td>
	<td>4,000</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.17% [42.9%-<b>45.4%</b>]</td>
	<td>6,036</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.47% [43.4%-<b>45.6%</b>]</td>
	<td>7,887</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.98% [43.4%-<b>46.6%</b>]</td>
	<td>4,000</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.39% [44.1%-<b>46.7%</b>]</td>
	<td>6,014</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.24% [45.2%-<b>47.3%</b>]</td>
	<td>8,779</td>
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
	<td>51.82% [51.7%-52.0%]</td>
	<td>497,883</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.35% [<b>42.6%</b>-44.1%]</td>
	<td>17,423</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.44% [<b>42.8%</b>-48.1%]</td>
	<td>1,402</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.25% [<b>43.8%</b>-46.7%]</td>
	<td>4,745</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.17% [<b>44.0%</b>-48.3%]</td>
	<td>2,103</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.71% [<b>44.1%</b>-45.3%]</td>
	<td>29,144</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.35% [42.6%-<b>44.1%</b>]</td>
	<td>17,423</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.71% [44.1%-<b>45.3%</b>]</td>
	<td>29,144</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.88% [45.2%-<b>46.6%</b>]</td>
	<td>19,306</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.25% [43.8%-<b>46.7%</b>]</td>
	<td>4,745</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.44% [42.8%-<b>48.1%</b>]</td>
	<td>1,402</td>
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
	<td>50.21% [50.0%-50.4%]</td>
	<td>191,731</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>45.67% [<b>42.3%</b>-49.1%]</td>
	<td>854</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.94% [<b>42.6%</b>-51.2%]</td>
	<td>539</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.94% [<b>42.9%</b>-44.9%]</td>
	<td>9,924</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.90% [<b>43.3%</b>-50.5%]</td>
	<td>759</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.64% [<b>44.1%</b>-47.1%]</td>
	<td>4,391</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.94% [42.9%-<b>44.9%</b>]</td>
	<td>9,924</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.64% [44.1%-<b>47.1%</b>]</td>
	<td>4,391</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.79% [44.4%-<b>47.2%</b>]</td>
	<td>5,163</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>47.05% [46.0%-<b>48.1%</b>]</td>
	<td>8,400</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.60% [44.9%-<b>48.3%</b>]</td>
	<td>3,354</td>
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
	<td>49.28% [49.2%-49.4%]</td>
	<td>792,261</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.72% [<b>42.4%</b>-45.0%]</td>
	<td>5,663</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.14% [<b>42.5%</b>-43.8%]</td>
	<td>24,411</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.57% [<b>42.9%</b>-44.2%]</td>
	<td>23,408</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.98% [<b>43.4%</b>-46.5%]</td>
	<td>4,126</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.44% [<b>43.6%</b>-45.2%]</td>
	<td>15,150</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.14% [42.5%-<b>43.8%</b>]</td>
	<td>24,411</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.57% [42.9%-<b>44.2%</b>]</td>
	<td>23,408</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.72% [42.4%-<b>45.0%</b>]</td>
	<td>5,663</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.44% [43.6%-<b>45.2%</b>]</td>
	<td>15,150</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.91% [44.4%-<b>45.4%</b>]</td>
	<td>39,030</td>
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
	<td>51.08% [50.9%-51.2%]</td>
	<td>467,417</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.13% [<b>41.1%</b>-45.2%]</td>
	<td>2,395</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.34% [<b>42.5%</b>-44.2%]</td>
	<td>13,827</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.81% [<b>42.7%</b>-44.9%]</td>
	<td>7,975</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.81% [<b>43.1%</b>-44.5%]</td>
	<td>18,707</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.44% [<b>43.4%</b>-45.5%]</td>
	<td>8,683</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.34% [42.5%-<b>44.2%</b>]</td>
	<td>13,827</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.81% [43.1%-<b>44.5%</b>]</td>
	<td>18,707</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.81% [42.7%-<b>44.9%</b>]</td>
	<td>7,975</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.13% [41.1%-<b>45.2%</b>]</td>
	<td>2,395</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.44% [43.4%-<b>45.5%</b>]</td>
	<td>8,683</td>
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
	<td>50.33% [50.0%-50.6%]</td>
	<td>112,194</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.25% [<b>36.4%</b>-48.1%]</td>
	<td>284</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.79% [<b>42.2%</b>-51.3%]</td>
	<td>483</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.53% [<b>43.1%</b>-52.0%]</td>
	<td>507</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>48.81% [<b>43.9%</b>-53.7%]</td>
	<td>420</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.80% [<b>44.0%</b>-49.6%]</td>
	<td>1,312</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.35% [44.7%-<b>48.0%</b>]</td>
	<td>3,696</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.25% [36.4%-<b>48.1%</b>]</td>
	<td>284</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.24% [44.3%-<b>48.1%</b>]</td>
	<td>2,768</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.61% [45.8%-<b>49.4%</b>]</td>
	<td>3,195</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>47.99% [46.5%-<b>49.5%</b>]</td>
	<td>4,591</td>
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
	<td>48.86% [48.7%-49.0%]</td>
	<td>318,602</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.80% [<b>41.9%</b>-49.7%]</td>
	<td>666</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.80% [<b>42.2%</b>-45.4%]</td>
	<td>3,968</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.05% [<b>42.5%</b>-45.6%]</td>
	<td>4,161</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.86% [<b>42.6%</b>-47.1%]</td>
	<td>1,995</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>45.41% [<b>43.3%</b>-47.5%]</td>
	<td>2,202</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.80% [42.2%-<b>45.4%</b>]</td>
	<td>3,968</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.05% [42.5%-<b>45.6%</b>]</td>
	<td>4,161</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.81% [43.9%-<b>45.7%</b>]</td>
	<td>11,527</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.23% [44.2%-<b>46.2%</b>]</td>
	<td>10,175</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.20% [44.1%-<b>46.3%</b>]</td>
	<td>8,650</td>
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
	<td>49.50% [49.3%-49.7%]</td>
	<td>190,745</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.10% [<b>40.6%</b>-49.6%]</td>
	<td>490</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.40% [<b>42.0%</b>-44.8%]</td>
	<td>4,913</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.69% [<b>42.6%</b>-48.7%]</td>
	<td>1,068</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.73% [<b>43.2%</b>-48.3%]</td>
	<td>1,509</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.23% [<b>43.8%</b>-46.7%]</td>
	<td>4,555</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.40% [42.0%-<b>44.8%</b>]</td>
	<td>4,913</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.23% [43.8%-<b>46.7%</b>]</td>
	<td>4,555</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.95% [44.5%-<b>47.4%</b>]</td>
	<td>4,881</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.69% [43.9%-<b>47.4%</b>]</td>
	<td>3,222</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.49% [45.2%-<b>47.7%</b>]</td>
	<td>6,421</td>
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
	<td>49.74% [49.4%-50.0%]</td>
	<td>110,043</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.47% [<b>38.7%</b>-46.3%]</td>
	<td>671</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.93% [<b>41.8%</b>-48.1%]</td>
	<td>1,006</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.22% [<b>41.9%</b>-50.5%]</td>
	<td>543</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.89% [<b>43.3%</b>-46.5%]</td>
	<td>4,043</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-olaf"></span> Olaf</td>
	<td>46.79% [<b>43.6%</b>-50.0%]</td>
	<td>951</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.47% [38.7%-<b>46.3%</b>]</td>
	<td>671</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.89% [43.3%-<b>46.5%</b>]</td>
	<td>4,043</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.12% [44.3%-<b>47.9%</b>]</td>
	<td>3,122</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.93% [41.8%-<b>48.1%</b>]</td>
	<td>1,006</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.43% [44.8%-<b>48.1%</b>]</td>
	<td>3,640</td>
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
	<td>48.32% [48.1%-48.5%]</td>
	<td>243,241</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.06% [<b>41.6%</b>-44.5%]</td>
	<td>4,633</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>43.69% [<b>41.6%</b>-45.7%]</td>
	<td>2,323</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.40% [<b>42.3%</b>-44.5%]</td>
	<td>7,982</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.18% [<b>42.6%</b>-45.7%]</td>
	<td>4,009</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.73% [<b>43.0%</b>-46.5%]</td>
	<td>3,293</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.40% [42.3%-<b>44.5%</b>]</td>
	<td>7,982</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.06% [41.6%-<b>44.5%</b>]</td>
	<td>4,633</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>43.69% [41.6%-<b>45.7%</b>]</td>
	<td>2,323</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.18% [42.6%-<b>45.7%</b>]</td>
	<td>4,009</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.72% [43.7%-<b>45.8%</b>]</td>
	<td>8,897</td>
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
	<td>48.35% [48.2%-48.5%]</td>
	<td>288,730</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>43.58% [<b>41.1%</b>-46.1%]</td>
	<td>1,565</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.51% [<b>41.6%</b>-43.4%]</td>
	<td>11,556</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>45.12% [<b>42.4%</b>-47.9%]</td>
	<td>1,301</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.91% [<b>42.6%</b>-49.2%]</td>
	<td>904</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.37% [<b>42.8%</b>-48.0%]</td>
	<td>1,470</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.51% [41.6%-<b>43.4%</b>]</td>
	<td>11,556</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.59% [43.4%-<b>45.7%</b>]</td>
	<td>7,529</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>43.58% [41.1%-<b>46.1%</b>]</td>
	<td>1,565</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.41% [44.4%-<b>46.4%</b>]</td>
	<td>10,711</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>44.84% [43.3%-<b>46.4%</b>]</td>
	<td>4,063</td>
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
	<td>48.93% [48.7%-49.2%]</td>
	<td>144,576</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>44.78% [<b>41.2%</b>-48.3%]</td>
	<td>786</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.00% [<b>41.5%</b>-50.5%]</td>
	<td>500</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.86% [<b>42.5%</b>-45.2%]</td>
	<td>5,180</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.49% [<b>42.6%</b>-46.4%]</td>
	<td>2,839</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>45.43% [<b>42.7%</b>-48.1%]</td>
	<td>1,367</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.86% [42.5%-<b>45.2%</b>]</td>
	<td>5,180</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.49% [42.6%-<b>46.4%</b>]</td>
	<td>2,839</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.65% [42.8%-<b>46.5%</b>]</td>
	<td>2,813</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.96% [43.2%-<b>46.7%</b>]</td>
	<td>3,136</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-riven"></span> Riven</td>
	<td>45.14% [43.5%-<b>46.8%</b>]</td>
	<td>3,633</td>
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
	<td>50.97% [50.6%-51.3%]</td>
	<td>76,222</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.45% [<b>41.2%</b>-45.7%]</td>
	<td>1,908</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.60% [<b>41.5%</b>-53.7%]</td>
	<td>271</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.88% [<b>42.0%</b>-49.8%]</td>
	<td>656</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.64% [<b>42.6%</b>-48.7%]</td>
	<td>1,089</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>45.54% [<b>42.8%</b>-48.2%]</td>
	<td>1,368</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.45% [41.2%-<b>45.7%</b>]</td>
	<td>1,908</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>45.54% [42.8%-<b>48.2%</b>]</td>
	<td>1,368</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.93% [43.6%-<b>48.2%</b>]</td>
	<td>1,855</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.64% [42.6%-<b>48.7%</b>]</td>
	<td>1,089</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.88% [42.0%-<b>49.8%</b>]</td>
	<td>656</td>
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
	<td>49.52% [49.3%-49.8%]</td>
	<td>173,929</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.01% [<b>40.7%</b>-43.3%]</td>
	<td>5,984</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.72% [<b>41.2%</b>-44.3%]</td>
	<td>4,113</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.35% [<b>41.3%</b>-43.4%]</td>
	<td>8,929</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.27% [<b>41.9%</b>-50.6%]</td>
	<td>523</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.15% [<b>42.8%</b>-49.5%]</td>
	<td>908</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.01% [40.7%-<b>43.3%</b>]</td>
	<td>5,984</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.35% [41.3%-<b>43.4%</b>]</td>
	<td>8,929</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.72% [41.2%-<b>44.3%</b>]</td>
	<td>4,113</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.96% [45.6%-<b>48.3%</b>]</td>
	<td>5,409</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>46.83% [45.3%-<b>48.3%</b>]</td>
	<td>4,461</td>
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
	<td>50.00% [49.7%-50.3%]</td>
	<td>89,122</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.72% [<b>40.4%</b>-49.0%]</td>
	<td>530</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.49% [<b>40.9%</b>-48.1%]</td>
	<td>753</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.57% [<b>41.2%</b>-45.9%]</td>
	<td>1,811</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>44.35% [<b>41.9%</b>-46.8%]</td>
	<td>1,619</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>45.80% [<b>42.1%</b>-49.5%]</td>
	<td>738</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.57% [41.2%-<b>45.9%</b>]</td>
	<td>1,811</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.51% [42.7%-<b>46.3%</b>]</td>
	<td>3,078</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>44.35% [41.9%-<b>46.8%</b>]</td>
	<td>1,619</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.95% [42.7%-<b>47.2%</b>]</td>
	<td>1,900</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.15% [43.0%-<b>47.3%</b>]</td>
	<td>2,073</td>
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
	<td>47.95% [47.7%-48.2%]</td>
	<td>170,361</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.64% [<b>39.3%</b>-48.0%]</td>
	<td>527</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>43.69% [<b>40.8%</b>-46.6%]</td>
	<td>1,165</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.97% [<b>40.9%</b>-47.1%]</td>
	<td>1,037</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.12% [<b>41.2%</b>-47.0%]</td>
	<td>1,181</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.83% [<b>42.4%</b>-45.3%]</td>
	<td>4,565</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.83% [42.4%-<b>45.3%</b>]</td>
	<td>4,565</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.00% [43.8%-<b>46.2%</b>]</td>
	<td>6,674</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>44.70% [42.9%-<b>46.5%</b>]</td>
	<td>3,215</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.30% [44.0%-<b>46.6%</b>]</td>
	<td>5,976</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>43.69% [40.8%-<b>46.6%</b>]</td>
	<td>1,165</td>
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
	<td>49.88% [49.6%-50.2%]</td>
	<td>126,801</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>41.88% [<b>38.1%</b>-45.6%]</td>
	<td>690</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.99% [<b>40.7%</b>-53.3%]</td>
	<td>249</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.29% [<b>42.5%</b>-46.1%]</td>
	<td>2,971</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-olaf"></span> Olaf</td>
	<td>46.29% [<b>43.1%</b>-49.4%]</td>
	<td>996</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.62% [<b>43.2%</b>-48.0%]</td>
	<td>1,747</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>41.88% [38.1%-<b>45.6%</b>]</td>
	<td>690</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.29% [42.5%-<b>46.1%</b>]</td>
	<td>2,971</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.19% [43.3%-<b>47.1%</b>]</td>
	<td>2,702</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>45.84% [44.2%-<b>47.4%</b>]</td>
	<td>3,868</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.30% [44.8%-<b>47.8%</b>]</td>
	<td>4,214</td>
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
	<td>48.72% [48.4%-49.0%]</td>
	<td>94,729</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.22% [<b>39.5%</b>-45.0%]</td>
	<td>1,279</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.22% [<b>40.3%</b>-44.2%]</td>
	<td>2,572</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-olaf"></span> Olaf</td>
	<td>44.64% [<b>40.5%</b>-48.8%]</td>
	<td>578</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.51% [<b>41.4%</b>-45.6%]</td>
	<td>2,271</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.96% [<b>41.5%</b>-44.5%]</td>
	<td>4,358</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.22% [40.3%-<b>44.2%</b>]</td>
	<td>2,572</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.96% [41.5%-<b>44.5%</b>]</td>
	<td>4,358</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.34% [41.7%-<b>45.0%</b>]</td>
	<td>3,777</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.22% [39.5%-<b>45.0%</b>]</td>
	<td>1,279</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.51% [41.4%-<b>45.6%</b>]</td>
	<td>2,271</td>
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
	<td>48.38% [48.1%-48.7%]</td>
	<td>135,298</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>40.40% [<b>38.3%</b>-42.5%]</td>
	<td>2,104</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.03% [<b>40.3%</b>-43.8%]</td>
	<td>3,112</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.03% [<b>41.3%</b>-44.7%]</td>
	<td>3,470</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>44.81% [<b>41.6%</b>-48.0%]</td>
	<td>953</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.47% [<b>41.9%</b>-49.1%]</td>
	<td>761</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>40.40% [38.3%-<b>42.5%</b>]</td>
	<td>2,104</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.03% [40.3%-<b>43.8%</b>]</td>
	<td>3,112</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.03% [41.3%-<b>44.7%</b>]</td>
	<td>3,470</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.35% [42.3%-<b>46.4%</b>]</td>
	<td>2,266</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.99% [43.4%-<b>46.6%</b>]</td>
	<td>3,896</td>
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
	<td>46.51% [46.2%-46.8%]</td>
	<td>143,262</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>42.88% [<b>38.8%</b>-47.0%]</td>
	<td>576</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>42.98% [<b>40.2%</b>-45.7%]</td>
	<td>1,282</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.63% [<b>40.7%</b>-50.5%]</td>
	<td>412</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>42.89% [<b>40.8%</b>-45.0%]</td>
	<td>2,236</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.25% [<b>40.8%</b>-47.7%]</td>
	<td>843</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.69% [41.1%-<b>44.2%</b>]</td>
	<td>4,022</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>42.89% [40.8%-<b>45.0%</b>]</td>
	<td>2,236</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.86% [42.5%-<b>45.2%</b>]</td>
	<td>5,321</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.76% [42.2%-<b>45.3%</b>]</td>
	<td>3,903</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>43.48% [41.5%-<b>45.5%</b>]</td>
	<td>2,491</td>
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
	<td>47.95% [47.7%-48.2%]</td>
	<td>236,582</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.34% [<b>39.8%</b>-42.9%]</td>
	<td>4,243</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.51% [<b>40.2%</b>-42.8%]</td>
	<td>5,551</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.50% [<b>40.4%</b>-46.6%]</td>
	<td>1,000</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.38% [<b>41.3%</b>-43.4%]</td>
	<td>8,670</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.59% [<b>41.9%</b>-45.3%]</td>
	<td>3,294</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.51% [40.2%-<b>42.8%</b>]</td>
	<td>5,551</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.34% [39.8%-<b>42.9%</b>]</td>
	<td>4,243</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.38% [41.3%-<b>43.4%</b>]</td>
	<td>8,670</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.87% [42.9%-<b>44.8%</b>]</td>
	<td>11,596</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.59% [41.9%-<b>45.3%</b>]</td>
	<td>3,294</td>
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
	<td>46.59% [46.5%-46.7%]</td>
	<td>575,382</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>41.03% [<b>39.7%</b>-42.3%]</td>
	<td>5,725</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>41.60% [<b>40.1%</b>-43.1%]</td>
	<td>4,324</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.28% [<b>40.5%</b>-42.1%]</td>
	<td>15,227</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.91% [<b>41.2%</b>-44.6%]</td>
	<td>3,405</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.54% [<b>41.7%</b>-43.4%]</td>
	<td>14,445</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.28% [40.5%-<b>42.1%</b>]</td>
	<td>15,227</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>41.03% [39.7%-<b>42.3%</b>]</td>
	<td>5,725</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>41.60% [40.1%-<b>43.1%</b>]</td>
	<td>4,324</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.54% [41.7%-<b>43.4%</b>]</td>
	<td>14,445</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.91% [41.2%-<b>44.6%</b>]</td>
	<td>3,405</td>
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
	<td>51.69% [51.4%-51.9%]</td>
	<td>171,045</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.48% [<b>39.0%</b>-49.9%]</td>
	<td>335</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.54% [<b>39.7%</b>-45.4%]</td>
	<td>1,220</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.34% [<b>43.2%</b>-49.5%]</td>
	<td>984</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>49.21% [<b>44.8%</b>-53.7%]</td>
	<td>506</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.64% [<b>44.8%</b>-50.5%]</td>
	<td>1,251</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.54% [39.7%-<b>45.4%</b>]</td>
	<td>1,220</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.27% [46.1%-<b>48.4%</b>]</td>
	<td>7,161</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.70% [46.3%-<b>49.1%</b>]</td>
	<td>4,855</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.34% [43.2%-<b>49.5%</b>]</td>
	<td>984</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>48.03% [46.4%-<b>49.7%</b>]</td>
	<td>3,739</td>
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
	<td>48.31% [48.1%-48.5%]</td>
	<td>241,548</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>41.51% [<b>38.7%</b>-44.3%]</td>
	<td>1,243</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>41.46% [<b>39.4%</b>-43.5%]</td>
	<td>2,231</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>42.36% [<b>40.5%</b>-44.2%]</td>
	<td>2,788</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>41.82% [<b>40.6%</b>-43.0%]</td>
	<td>6,705</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.65% [<b>41.5%</b>-43.8%]</td>
	<td>7,916</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>41.82% [40.6%-<b>43.0%</b>]</td>
	<td>6,705</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>41.46% [39.4%-<b>43.5%</b>]</td>
	<td>2,231</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.65% [41.5%-<b>43.8%</b>]</td>
	<td>7,916</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>42.36% [40.5%-<b>44.2%</b>]</td>
	<td>2,788</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>41.51% [38.7%-<b>44.3%</b>]</td>
	<td>1,243</td>
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
	<td>47.34% [47.1%-47.6%]</td>
	<td>211,792</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>39.93% [<b>38.7%</b>-41.2%]</td>
	<td>6,006</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>40.00% [<b>39.0%</b>-41.0%]</td>
	<td>10,390</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.50% [<b>40.1%</b>-46.9%]</td>
	<td>869</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>43.02% [<b>40.4%</b>-45.6%]</td>
	<td>1,483</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.55% [<b>40.8%</b>-44.3%]</td>
	<td>3,135</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>40.00% [39.0%-<b>41.0%</b>]</td>
	<td>10,390</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>39.93% [38.7%-<b>41.2%</b>]</td>
	<td>6,006</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.55% [40.8%-<b>44.3%</b>]</td>
	<td>3,135</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.45% [42.3%-<b>44.6%</b>]</td>
	<td>7,600</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.72% [42.3%-<b>45.1%</b>]</td>
	<td>5,128</td>
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
	<td>51.61% [51.2%-52.1%]</td>
	<td>50,599</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>45.63% [<b>38.7%</b>-52.6%]</td>
	<td>206</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.06% [<b>38.7%</b>-49.4%]</td>
	<td>345</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.48% [<b>39.6%</b>-53.3%]</td>
	<td>213</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.47% [<b>40.4%</b>-54.6%]</td>
	<td>198</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.58% [<b>42.1%</b>-47.0%]</td>
	<td>1,660</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.58% [42.1%-<b>47.0%</b>]</td>
	<td>1,660</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.06% [38.7%-<b>49.4%</b>]</td>
	<td>345</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>46.34% [42.8%-<b>49.9%</b>]</td>
	<td>779</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>46.29% [42.4%-<b>50.1%</b>]</td>
	<td>674</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.11% [45.9%-<b>50.3%</b>]</td>
	<td>2,091</td>
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
	<td>48.32% [48.0%-48.6%]</td>
	<td>118,941</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>41.82% [<b>37.1%</b>-46.5%]</td>
	<td>440</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.82% [<b>37.9%</b>-47.8%]</td>
	<td>397</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>39.63% [<b>38.2%</b>-41.1%]</td>
	<td>4,413</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>39.84% [<b>38.4%</b>-41.3%]</td>
	<td>4,744</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.30% [<b>40.0%</b>-42.6%]</td>
	<td>5,458</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>39.63% [38.2%-<b>41.1%</b>]</td>
	<td>4,413</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>39.84% [38.4%-<b>41.3%</b>]</td>
	<td>4,744</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.30% [40.0%-<b>42.6%</b>]</td>
	<td>5,458</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.31% [41.4%-<b>45.2%</b>]</td>
	<td>2,796</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>41.82% [37.1%-<b>46.5%</b>]</td>
	<td>440</td>
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
	<td>43.78% [43.6%-44.0%]</td>
	<td>262,582</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>37.03% [<b>35.6%</b>-38.5%]</td>
	<td>4,310</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>38.77% [<b>37.3%</b>-40.2%]</td>
	<td>4,486</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>40.31% [<b>37.7%</b>-43.0%]</td>
	<td>1,377</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>40.94% [<b>38.1%</b>-43.8%]</td>
	<td>1,165</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>39.70% [<b>38.5%</b>-40.9%]</td>
	<td>6,975</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>37.03% [35.6%-<b>38.5%</b>]</td>
	<td>4,310</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>38.77% [37.3%-<b>40.2%</b>]</td>
	<td>4,486</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>39.70% [38.5%-<b>40.9%</b>]</td>
	<td>6,975</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>40.21% [38.8%-<b>41.6%</b>]</td>
	<td>4,957</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>40.92% [40.1%-<b>41.8%</b>]</td>
	<td>12,939</td>
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
	<td>49.56% [49.3%-49.9%]</td>
	<td>104,683</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>40.90% [<b>36.0%</b>-45.8%]</td>
	<td>401</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>40.71% [<b>36.6%</b>-44.8%]</td>
	<td>565</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.86% [<b>37.2%</b>-48.6%]</td>
	<td>301</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.77% [<b>37.9%</b>-45.7%]</td>
	<td>644</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>43.06% [<b>38.9%</b>-47.2%]</td>
	<td>576</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>40.71% [36.6%-<b>44.8%</b>]</td>
	<td>565</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.77% [37.9%-<b>45.7%</b>]</td>
	<td>644</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>40.90% [36.0%-<b>45.8%</b>]</td>
	<td>401</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.06% [41.8%-<b>46.4%</b>]</td>
	<td>1,877</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.78% [42.7%-<b>46.8%</b>]</td>
	<td>2,367</td>
</tr>
</table>

</details>
### Jungle

<details>
<summary>Click to view</summary>

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
	<td>52.52% [52.4%-52.6%]</td>
	<td>767,348</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.83% [<b>47.2%</b>-48.4%]</td>
	<td>27,267</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.27% [<b>48.2%</b>-50.3%]</td>
	<td>9,161</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.52% [<b>48.3%</b>-50.8%]</td>
	<td>6,361</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.91% [<b>48.4%</b>-49.4%]</td>
	<td>35,134</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.92% [<b>48.5%</b>-51.3%]</td>
	<td>4,968</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.83% [47.2%-<b>48.4%</b>]</td>
	<td>27,267</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.91% [48.4%-<b>49.4%</b>]</td>
	<td>35,134</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>49.11% [48.5%-<b>49.7%</b>]</td>
	<td>29,929</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.27% [48.2%-<b>50.3%</b>]</td>
	<td>9,161</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>50.16% [49.7%-<b>50.6%</b>]</td>
	<td>42,501</td>
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
	<td>52.07% [52.0%-52.2%]</td>
	<td>1,011,405</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.15% [<b>46.5%</b>-49.8%]</td>
	<td>3,778</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.65% [<b>48.1%</b>-49.2%]</td>
	<td>34,430</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>49.97% [<b>48.9%</b>-51.0%]</td>
	<td>9,114</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>49.90% [<b>49.2%</b>-50.6%]</td>
	<td>18,723</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>50.10% [<b>49.3%</b>-50.9%]</td>
	<td>16,337</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.65% [48.1%-<b>49.2%</b>]</td>
	<td>34,430</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.15% [46.5%-<b>49.8%</b>]</td>
	<td>3,778</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>49.82% [49.3%-<b>50.3%</b>]</td>
	<td>42,501</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>50.10% [49.6%-<b>50.6%</b>]</td>
	<td>39,554</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>50.04% [49.5%-<b>50.6%</b>]</td>
	<td>30,499</td>
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
	<td>52.06% [51.9%-52.2%]</td>
	<td>723,103</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.03% [<b>43.5%</b>-46.6%]</td>
	<td>4,031</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.42% [<b>48.1%</b>-50.8%]</td>
	<td>5,421</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.55% [<b>48.1%</b>-51.0%]</td>
	<td>5,043</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-karthus"></span> Karthus</td>
	<td>49.17% [<b>48.1%</b>-50.2%]</td>
	<td>9,494</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.81% [<b>48.2%</b>-49.4%]</td>
	<td>26,570</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.03% [43.5%-<b>46.6%</b>]</td>
	<td>4,031</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.81% [48.2%-<b>49.4%</b>]</td>
	<td>26,570</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>49.53% [48.9%-<b>50.1%</b>]</td>
	<td>27,761</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-karthus"></span> Karthus</td>
	<td>49.17% [48.1%-<b>50.2%</b>]</td>
	<td>9,494</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.88% [49.4%-<b>50.4%</b>]</td>
	<td>39,554</td>
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
	<td>52.10% [52.0%-52.2%]</td>
	<td>596,922</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.17% [<b>47.5%</b>-48.9%]</td>
	<td>20,174</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.15% [<b>47.7%</b>-50.6%]</td>
	<td>4,651</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.44% [<b>47.8%</b>-51.0%]</td>
	<td>3,898</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.61% [<b>48.4%</b>-50.8%]</td>
	<td>6,620</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>50.97% [<b>49.1%</b>-52.9%]</td>
	<td>2,786</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.17% [47.5%-<b>48.9%</b>]</td>
	<td>20,174</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.95% [49.4%-<b>50.5%</b>]</td>
	<td>30,499</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.15% [47.7%-<b>50.6%</b>]</td>
	<td>4,651</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>50.14% [49.5%-<b>50.7%</b>]</td>
	<td>28,566</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.61% [48.4%-<b>50.8%</b>]</td>
	<td>6,620</td>
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
	<td>51.63% [51.4%-51.9%]</td>
	<td>205,314</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.34% [<b>45.1%</b>-51.6%]</td>
	<td>964</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.00% [<b>47.4%</b>-50.6%]</td>
	<td>3,694</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.97% [<b>47.4%</b>-50.6%]</td>
	<td>3,900</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>50.45% [<b>47.6%</b>-53.3%]</td>
	<td>1,209</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>49.74% [<b>48.1%</b>-51.4%]</td>
	<td>3,780</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.47% [48.5%-<b>50.4%</b>]</td>
	<td>10,788</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kha-zix"></span> Kha'Zix</td>
	<td>49.36% [48.2%-<b>50.6%</b>]</td>
	<td>6,965</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.97% [47.4%-<b>50.6%</b>]</td>
	<td>3,900</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.55% [48.5%-<b>50.6%</b>]</td>
	<td>8,516</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.00% [47.4%-<b>50.6%</b>]</td>
	<td>3,694</td>
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
	<td>50.60% [50.5%-50.7%]</td>
	<td>846,492</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.72% [<b>46.9%</b>-48.5%]</td>
	<td>15,184</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>48.47% [<b>46.9%</b>-50.0%]</td>
	<td>4,213</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.06% [<b>47.1%</b>-49.1%]</td>
	<td>9,869</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.91% [<b>47.4%</b>-48.4%]</td>
	<td>39,653</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.25% [<b>47.6%</b>-48.9%]</td>
	<td>20,744</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.91% [47.4%-<b>48.4%</b>]</td>
	<td>39,653</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.72% [46.9%-<b>48.5%</b>]</td>
	<td>15,184</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.43% [48.0%-<b>48.9%</b>]</td>
	<td>45,981</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.25% [47.6%-<b>48.9%</b>]</td>
	<td>20,744</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>48.47% [47.9%-<b>49.0%</b>]</td>
	<td>33,235</td>
</tr>
</table>

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
	<td>52.10% [51.9%-52.3%]</td>
	<td>429,129</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.93% [<b>46.5%</b>-49.3%]</td>
	<td>5,189</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>49.14% [<b>46.9%</b>-51.4%]</td>
	<td>2,043</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.57% [<b>47.8%</b>-49.4%]</td>
	<td>15,173</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.76% [<b>48.0%</b>-49.5%]</td>
	<td>17,003</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>49.57% [<b>48.2%</b>-50.9%]</td>
	<td>5,594</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.93% [46.5%-<b>49.3%</b>]</td>
	<td>5,189</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.57% [47.8%-<b>49.4%</b>]</td>
	<td>15,173</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.76% [48.0%-<b>49.5%</b>]</td>
	<td>17,003</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.17% [48.5%-<b>49.8%</b>]</td>
	<td>22,906</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>49.61% [48.9%-<b>50.3%</b>]</td>
	<td>20,671</td>
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
	<td>51.89% [51.8%-52.0%]</td>
	<td>663,201</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.89% [<b>46.7%</b>-49.1%]</td>
	<td>7,014</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.75% [<b>46.9%</b>-48.6%]</td>
	<td>14,332</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.99% [<b>47.0%</b>-49.0%]</td>
	<td>10,788</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.22% [<b>47.6%</b>-50.8%]</td>
	<td>4,015</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>48.55% [<b>47.9%</b>-49.2%]</td>
	<td>20,397</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.75% [46.9%-<b>48.6%</b>]</td>
	<td>14,332</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.99% [47.0%-<b>49.0%</b>]</td>
	<td>10,788</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.89% [46.7%-<b>49.1%</b>]</td>
	<td>7,014</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>48.55% [47.9%-<b>49.2%</b>]</td>
	<td>20,397</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>49.44% [48.6%-<b>50.3%</b>]</td>
	<td>12,639</td>
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
	<td>51.47% [51.3%-51.6%]</td>
	<td>334,737</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.21% [<b>45.5%</b>-50.9%]</td>
	<td>1,400</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.57% [<b>46.8%</b>-50.3%]</td>
	<td>3,243</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.15% [<b>47.0%</b>-49.3%]</td>
	<td>7,742</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.12% [<b>47.2%</b>-49.1%]</td>
	<td>10,925</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.54% [<b>47.6%</b>-49.5%]</td>
	<td>10,773</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.12% [47.2%-<b>49.1%</b>]</td>
	<td>10,925</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.15% [47.0%-<b>49.3%</b>]</td>
	<td>7,742</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.56% [47.7%-<b>49.4%</b>]</td>
	<td>13,118</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.54% [47.6%-<b>49.5%</b>]</td>
	<td>10,773</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>49.23% [48.3%-<b>50.1%</b>]</td>
	<td>12,244</td>
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
	<td>50.76% [50.6%-50.9%]</td>
	<td>613,959</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.58% [<b>44.3%</b>-48.8%]</td>
	<td>2,001</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.68% [<b>46.5%</b>-48.9%]</td>
	<td>6,757</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.14% [<b>47.2%</b>-49.1%]</td>
	<td>11,579</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.08% [<b>47.4%</b>-48.8%]</td>
	<td>19,261</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.40% [<b>47.5%</b>-51.3%]</td>
	<td>2,901</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.08% [47.4%-<b>48.8%</b>]</td>
	<td>19,261</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.58% [44.3%-<b>48.8%</b>]</td>
	<td>2,001</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.68% [46.5%-<b>48.9%</b>]</td>
	<td>6,757</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.14% [47.2%-<b>49.1%</b>]</td>
	<td>11,579</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>48.54% [47.8%-<b>49.2%</b>]</td>
	<td>20,142</td>
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
	<td>49.88% [49.8%-50.0%]</td>
	<td>725,153</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.28% [<b>45.7%</b>-46.9%]</td>
	<td>25,842</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.94% [<b>46.4%</b>-47.4%]</td>
	<td>39,367</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.55% [<b>46.8%</b>-50.3%]</td>
	<td>3,203</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.54% [<b>46.8%</b>-48.3%]</td>
	<td>18,542</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.75% [<b>46.9%</b>-48.6%]</td>
	<td>12,465</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.28% [45.7%-<b>46.9%</b>]</td>
	<td>25,842</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.94% [46.4%-<b>47.4%</b>]</td>
	<td>39,367</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.54% [46.8%-<b>48.3%</b>]</td>
	<td>18,542</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.89% [47.2%-<b>48.6%</b>]</td>
	<td>22,138</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.75% [46.9%-<b>48.6%</b>]</td>
	<td>12,465</td>
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
	<td>49.65% [49.5%-49.8%]</td>
	<td>937,555</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.75% [<b>45.6%</b>-47.9%]</td>
	<td>7,576</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.88% [<b>46.2%</b>-47.5%]</td>
	<td>24,922</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.36% [<b>46.5%</b>-48.2%]</td>
	<td>14,204</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>47.56% [<b>46.5%</b>-48.6%]</td>
	<td>9,279</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.78% [<b>46.7%</b>-50.9%]</td>
	<td>2,208</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.88% [46.2%-<b>47.5%</b>]</td>
	<td>24,922</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.75% [45.6%-<b>47.9%</b>]</td>
	<td>7,576</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.36% [46.5%-<b>48.2%</b>]</td>
	<td>14,204</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.71% [47.1%-<b>48.3%</b>]</td>
	<td>26,989</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.05% [47.6%-<b>48.5%</b>]</td>
	<td>47,044</td>
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
	<td>50.47% [50.4%-50.6%]</td>
	<td>1,434,861</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.39% [<b>45.0%</b>-47.8%]</td>
	<td>5,208</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>46.90% [<b>46.1%</b>-47.7%]</td>
	<td>17,210</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.64% [<b>46.2%</b>-47.1%]</td>
	<td>56,957</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.33% [<b>46.9%</b>-47.8%]</td>
	<td>51,029</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>47.98% [<b>47.4%</b>-48.5%]</td>
	<td>31,812</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.64% [46.2%-<b>47.1%</b>]</td>
	<td>56,957</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>46.90% [46.1%-<b>47.7%</b>]</td>
	<td>17,210</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.33% [46.9%-<b>47.8%</b>]</td>
	<td>51,029</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.39% [45.0%-<b>47.8%</b>]</td>
	<td>5,208</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>47.98% [47.4%-<b>48.5%</b>]</td>
	<td>31,812</td>
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
	<td>50.65% [50.5%-50.8%]</td>
	<td>330,899</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.69% [<b>45.1%</b>-50.3%]</td>
	<td>1,493</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.14% [<b>46.0%</b>-48.3%]</td>
	<td>7,896</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.62% [<b>46.7%</b>-50.6%]</td>
	<td>2,610</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.80% [<b>46.9%</b>-48.7%]</td>
	<td>13,727</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>49.39% [<b>47.2%</b>-51.6%]</td>
	<td>2,047</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.14% [46.0%-<b>48.3%</b>]</td>
	<td>7,896</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.80% [46.9%-<b>48.7%</b>]</td>
	<td>13,727</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.70% [47.8%-<b>49.6%</b>]</td>
	<td>12,032</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.82% [48.0%-<b>49.7%</b>]</td>
	<td>14,228</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.78% [47.8%-<b>49.7%</b>]</td>
	<td>11,439</td>
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
	<td>49.89% [49.7%-50.1%]</td>
	<td>339,425</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.29% [<b>43.6%</b>-47.0%]</td>
	<td>3,418</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.05% [<b>45.9%</b>-48.2%]</td>
	<td>7,211</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.27% [<b>46.4%</b>-48.2%]</td>
	<td>12,341</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.18% [<b>46.8%</b>-49.5%]</td>
	<td>5,590</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>48.81% [<b>47.0%</b>-50.6%]</td>
	<td>2,995</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.29% [43.6%-<b>47.0%</b>]</td>
	<td>3,418</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.27% [46.4%-<b>48.2%</b>]</td>
	<td>12,341</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.05% [45.9%-<b>48.2%</b>]</td>
	<td>7,211</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kha-zix"></span> Kha'Zix</td>
	<td>47.92% [47.0%-<b>48.8%</b>]</td>
	<td>12,647</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.31% [47.3%-<b>49.3%</b>]</td>
	<td>9,697</td>
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
	<td>50.78% [50.6%-50.9%]</td>
	<td>375,271</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.50% [<b>45.8%</b>-47.2%]</td>
	<td>20,093</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>49.22% [<b>45.9%</b>-52.6%]</td>
	<td>892</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.81% [<b>46.4%</b>-49.2%]</td>
	<td>4,913</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.52% [<b>46.4%</b>-48.6%]</td>
	<td>7,872</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.69% [<b>46.5%</b>-48.9%]</td>
	<td>6,500</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.50% [45.8%-<b>47.2%</b>]</td>
	<td>20,093</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.52% [46.4%-<b>48.6%</b>]</td>
	<td>7,872</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.81% [46.8%-<b>48.8%</b>]</td>
	<td>10,619</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.69% [46.5%-<b>48.9%</b>]</td>
	<td>6,500</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.16% [47.2%-<b>49.1%</b>]</td>
	<td>10,375</td>
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
	<td>51.12% [50.9%-51.3%]</td>
	<td>324,803</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.37% [<b>44.6%</b>-50.1%]</td>
	<td>1,313</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.81% [<b>45.7%</b>-48.0%]</td>
	<td>7,496</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.29% [<b>47.3%</b>-49.3%]</td>
	<td>10,505</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.50% [<b>47.4%</b>-51.6%]</td>
	<td>2,184</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.89% [<b>47.5%</b>-52.2%]</td>
	<td>1,808</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.81% [45.7%-<b>48.0%</b>]</td>
	<td>7,496</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.29% [47.3%-<b>49.3%</b>]</td>
	<td>10,505</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.58% [47.8%-<b>49.4%</b>]</td>
	<td>16,194</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.81% [47.9%-<b>49.7%</b>]</td>
	<td>12,356</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.37% [44.6%-<b>50.1%</b>]</td>
	<td>1,313</td>
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
	<td>50.70% [50.5%-50.9%]</td>
	<td>185,260</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-bel-veth"></span> Bel'Veth</td>
	<td>46.20% [<b>44.0%</b>-48.4%]</td>
	<td>2,054</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.70% [<b>45.4%</b>-50.0%]</td>
	<td>1,889</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>49.65% [<b>45.4%</b>-53.9%]</td>
	<td>564</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>47.34% [<b>46.0%</b>-48.7%]</td>
	<td>5,661</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>49.31% [<b>46.1%</b>-52.6%]</td>
	<td>941</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-bel-veth"></span> Bel'Veth</td>
	<td>46.20% [44.0%-<b>48.4%</b>]</td>
	<td>2,054</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>47.34% [46.0%-<b>48.7%</b>]</td>
	<td>5,661</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>47.65% [46.5%-<b>48.8%</b>]</td>
	<td>7,993</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.88% [46.7%-<b>49.1%</b>]</td>
	<td>6,689</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.98% [46.4%-<b>49.6%</b>]</td>
	<td>4,050</td>
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
	<td>48.51% [48.4%-48.6%]</td>
	<td>1,403,020</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.71% [<b>45.2%</b>-46.2%]</td>
	<td>34,165</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.68% [<b>45.2%</b>-46.1%]</td>
	<td>45,130</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.73% [<b>45.4%</b>-46.1%]</td>
	<td>74,033</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.11% [<b>45.4%</b>-48.8%]</td>
	<td>3,568</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.06% [<b>45.6%</b>-46.5%]</td>
	<td>49,163</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.73% [45.4%-<b>46.1%</b>]</td>
	<td>74,033</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.68% [45.2%-<b>46.1%</b>]</td>
	<td>45,130</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.71% [45.2%-<b>46.2%</b>]</td>
	<td>34,165</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.06% [45.6%-<b>46.5%</b>]</td>
	<td>49,163</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.52% [45.9%-<b>47.2%</b>]</td>
	<td>24,112</td>
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
	<td>50.35% [50.2%-50.5%]</td>
	<td>369,110</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.89% [<b>41.3%</b>-46.5%]</td>
	<td>1,490</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.28% [<b>45.2%</b>-47.4%]</td>
	<td>8,407</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.53% [<b>45.5%</b>-49.5%]</td>
	<td>2,470</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.19% [<b>46.2%</b>-50.2%]</td>
	<td>2,403</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.18% [<b>46.4%</b>-48.0%]</td>
	<td>15,124</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.89% [41.3%-<b>46.5%</b>]</td>
	<td>1,490</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.28% [45.2%-<b>47.4%</b>]</td>
	<td>8,407</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.18% [46.4%-<b>48.0%</b>]</td>
	<td>15,124</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.90% [47.1%-<b>48.7%</b>]</td>
	<td>15,394</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.81% [46.6%-<b>49.1%</b>]</td>
	<td>6,384</td>
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
	<td>50.14% [50.0%-50.3%]</td>
	<td>728,537</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.39% [<b>44.9%</b>-45.9%]</td>
	<td>37,796</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>45.80% [<b>45.1%</b>-46.5%]</td>
	<td>22,257</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>46.81% [<b>45.8%</b>-47.8%]</td>
	<td>10,480</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>47.08% [<b>46.2%</b>-47.9%]</td>
	<td>13,216</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.28% [<b>46.3%</b>-48.2%]</td>
	<td>10,983</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.39% [44.9%-<b>45.9%</b>]</td>
	<td>37,796</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>45.80% [45.1%-<b>46.5%</b>]</td>
	<td>22,257</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.00% [46.4%-<b>47.6%</b>]</td>
	<td>28,877</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>46.81% [45.8%-<b>47.8%</b>]</td>
	<td>10,480</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>47.08% [46.2%-<b>47.9%</b>]</td>
	<td>13,216</td>
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
	<td>51.60% [51.3%-51.9%]</td>
	<td>115,633</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>49.17% [<b>44.9%</b>-53.5%]</td>
	<td>539</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.84% [<b>44.9%</b>-52.8%]</td>
	<td>645</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.36% [<b>46.2%</b>-50.5%]</td>
	<td>2,200</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>51.54% [<b>46.2%</b>-56.8%]</td>
	<td>357</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.21% [<b>46.3%</b>-50.1%]</td>
	<td>2,734</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.27% [46.6%-<b>49.9%</b>]</td>
	<td>3,679</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.21% [46.3%-<b>50.1%</b>]</td>
	<td>2,734</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.86% [47.6%-<b>50.1%</b>]</td>
	<td>6,166</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.36% [46.2%-<b>50.5%</b>]</td>
	<td>2,200</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.71% [46.5%-<b>50.9%</b>]</td>
	<td>2,098</td>
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
	<td>50.22% [50.1%-50.4%]</td>
	<td>380,638</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.50% [<b>41.7%</b>-47.3%]</td>
	<td>1,299</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.55% [<b>44.8%</b>-46.3%]</td>
	<td>15,744</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>48.46% [<b>46.3%</b>-50.6%]</td>
	<td>2,237</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.72% [<b>46.4%</b>-49.0%]</td>
	<td>5,960</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.39% [<b>46.8%</b>-49.9%]</td>
	<td>4,112</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.55% [44.8%-<b>46.3%</b>]</td>
	<td>15,744</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.50% [41.7%-<b>47.3%</b>]</td>
	<td>1,299</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>47.76% [47.0%-<b>48.6%</b>]</td>
	<td>15,766</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.72% [46.4%-<b>49.0%</b>]</td>
	<td>5,960</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.11% [47.2%-<b>49.1%</b>]</td>
	<td>11,211</td>
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
	<td>50.35% [50.2%-50.5%]</td>
	<td>301,795</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.76% [<b>40.7%</b>-46.8%]</td>
	<td>1,058</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>47.15% [<b>44.7%</b>-49.6%]</td>
	<td>1,669</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.70% [<b>44.8%</b>-48.6%]</td>
	<td>2,709</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.30% [<b>45.0%</b>-49.6%]</td>
	<td>1,816</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.48% [<b>45.1%</b>-47.8%]</td>
	<td>5,344</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.76% [40.7%-<b>46.8%</b>]</td>
	<td>1,058</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.49% [45.4%-<b>47.6%</b>]</td>
	<td>8,842</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.48% [45.1%-<b>47.8%</b>]</td>
	<td>5,344</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.97% [46.0%-<b>47.9%</b>]</td>
	<td>10,843</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.70% [44.8%-<b>48.6%</b>]</td>
	<td>2,709</td>
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
	<td>48.70% [48.6%-48.8%]</td>
	<td>555,410</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.79% [<b>41.6%</b>-46.0%]</td>
	<td>1,982</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.31% [<b>44.6%</b>-48.0%]</td>
	<td>3,470</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.80% [<b>45.0%</b>-48.6%]</td>
	<td>3,002</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.48% [<b>45.0%</b>-47.9%]</td>
	<td>4,733</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.05% [<b>45.0%</b>-47.1%]</td>
	<td>9,677</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.79% [41.6%-<b>46.0%</b>]</td>
	<td>1,982</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.75% [45.2%-<b>46.3%</b>]</td>
	<td>30,687</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.92% [45.2%-<b>46.6%</b>]</td>
	<td>20,127</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.20% [45.5%-<b>46.9%</b>]</td>
	<td>18,488</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.05% [45.0%-<b>47.1%</b>]</td>
	<td>9,677</td>
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
	<td>50.42% [50.3%-50.6%]</td>
	<td>583,403</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.38% [<b>42.3%</b>-46.5%]</td>
	<td>2,260</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.33% [<b>44.6%</b>-48.1%]</td>
	<td>3,216</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.77% [<b>44.9%</b>-46.7%]</td>
	<td>12,425</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.65% [<b>46.0%</b>-47.3%]</td>
	<td>22,241</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.74% [<b>46.0%</b>-47.5%]</td>
	<td>18,951</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.38% [42.3%-<b>46.5%</b>]</td>
	<td>2,260</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.77% [44.9%-<b>46.7%</b>]</td>
	<td>12,425</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.65% [46.0%-<b>47.3%</b>]</td>
	<td>22,241</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.74% [46.0%-<b>47.5%</b>]</td>
	<td>18,951</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.33% [44.6%-<b>48.1%</b>]</td>
	<td>3,216</td>
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
	<td>50.56% [50.3%-50.8%]</td>
	<td>124,748</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>44.11% [<b>41.2%</b>-47.0%]</td>
	<td>1,154</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>49.01% [<b>44.3%</b>-53.7%]</td>
	<td>455</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>46.04% [<b>44.4%</b>-47.7%]</td>
	<td>3,764</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>48.98% [<b>44.5%</b>-53.5%]</td>
	<td>492</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>50.00% [<b>45.4%</b>-54.6%]</td>
	<td>472</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>44.11% [41.2%-<b>47.0%</b>]</td>
	<td>1,154</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>46.04% [44.4%-<b>47.7%</b>]</td>
	<td>3,764</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>47.91% [46.2%-<b>49.6%</b>]</td>
	<td>3,490</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.84% [45.9%-<b>49.8%</b>]</td>
	<td>2,569</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viego"></span> Viego</td>
	<td>48.76% [47.7%-<b>49.8%</b>]</td>
	<td>8,464</td>
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
	<td>49.15% [49.0%-49.3%]</td>
	<td>606,208</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.23% [<b>44.2%</b>-48.3%]</td>
	<td>2,360</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.10% [<b>44.2%</b>-46.0%]</td>
	<td>13,619</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.17% [<b>45.0%</b>-47.3%]</td>
	<td>7,159</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-karthus"></span> Karthus</td>
	<td>46.17% [<b>45.1%</b>-47.3%]</td>
	<td>8,476</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.57% [<b>45.6%</b>-47.5%]</td>
	<td>10,589</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.10% [44.2%-<b>46.0%</b>]</td>
	<td>13,619</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.30% [45.7%-<b>46.9%</b>]</td>
	<td>32,600</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-karthus"></span> Karthus</td>
	<td>46.17% [45.1%-<b>47.3%</b>]</td>
	<td>8,476</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.17% [45.0%-<b>47.3%</b>]</td>
	<td>7,159</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.67% [46.0%-<b>47.4%</b>]</td>
	<td>19,869</td>
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
	<td>49.60% [49.4%-49.8%]</td>
	<td>251,952</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.45% [<b>42.8%</b>-50.1%]</td>
	<td>760</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.30% [<b>44.1%</b>-46.5%]</td>
	<td>6,825</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>47.03% [<b>44.3%</b>-49.8%]</td>
	<td>1,297</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.57% [<b>44.5%</b>-48.6%]</td>
	<td>2,379</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.40% [<b>44.8%</b>-48.0%]</td>
	<td>3,750</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.30% [44.1%-<b>46.5%</b>]</td>
	<td>6,825</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>46.02% [44.9%-<b>47.1%</b>]</td>
	<td>7,853</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.40% [44.8%-<b>48.0%</b>]</td>
	<td>3,750</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.45% [46.6%-<b>48.3%</b>]</td>
	<td>12,796</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nunu---willump"></span> Nunu & Willump</td>
	<td>47.08% [45.6%-<b>48.6%</b>]</td>
	<td>4,450</td>
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
	<td>48.88% [48.7%-49.1%]</td>
	<td>259,768</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.41% [<b>43.5%</b>-45.4%]</td>
	<td>10,802</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.80% [<b>43.6%</b>-50.0%]</td>
	<td>983</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>47.12% [<b>44.4%</b>-49.8%]</td>
	<td>1,371</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.43% [<b>44.6%</b>-48.2%]</td>
	<td>3,054</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.21% [<b>44.7%</b>-47.7%]</td>
	<td>4,445</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.41% [43.5%-<b>45.4%</b>]</td>
	<td>10,802</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.07% [44.8%-<b>47.4%</b>]</td>
	<td>5,960</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.70% [45.9%-<b>47.5%</b>]</td>
	<td>13,881</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.21% [44.7%-<b>47.7%</b>]</td>
	<td>4,445</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.64% [45.2%-<b>48.1%</b>]</td>
	<td>4,580</td>
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
	<td>49.29% [49.1%-49.4%]</td>
	<td>406,095</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.29% [<b>41.8%</b>-46.8%]</td>
	<td>1,630</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>44.15% [<b>43.4%</b>-44.9%]</td>
	<td>15,592</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>47.11% [<b>45.2%</b>-49.0%]</td>
	<td>2,772</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.99% [<b>45.4%</b>-48.6%]</td>
	<td>3,914</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.20% [<b>45.4%</b>-47.0%]</td>
	<td>16,389</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>44.15% [43.4%-<b>44.9%</b>]</td>
	<td>15,592</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.29% [41.8%-<b>46.8%</b>]</td>
	<td>1,630</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.20% [45.4%-<b>47.0%</b>]</td>
	<td>16,389</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>46.60% [45.9%-<b>47.3%</b>]</td>
	<td>17,960</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>47.05% [46.2%-<b>47.9%</b>]</td>
	<td>13,102</td>
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
	<td>48.97% [48.7%-49.2%]</td>
	<td>191,747</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>44.84% [<b>41.5%</b>-48.2%]</td>
	<td>881</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.36% [<b>43.0%</b>-47.7%]</td>
	<td>1,779</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.27% [<b>43.1%</b>-49.4%]</td>
	<td>1,005</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>45.23% [<b>43.2%</b>-47.3%]</td>
	<td>2,390</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.99% [<b>43.8%</b>-46.2%]</td>
	<td>6,690</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.99% [43.8%-<b>46.2%</b>]</td>
	<td>6,690</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.89% [44.7%-<b>47.1%</b>]</td>
	<td>7,195</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>45.23% [43.2%-<b>47.3%</b>]</td>
	<td>2,390</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.36% [43.0%-<b>47.7%</b>]</td>
	<td>1,779</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>46.53% [45.3%-<b>47.7%</b>]</td>
	<td>6,770</td>
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
	<td>50.29% [50.1%-50.5%]</td>
	<td>195,542</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.49% [<b>42.3%</b>-46.7%]</td>
	<td>2,059</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.99% [<b>43.0%</b>-49.0%]</td>
	<td>1,085</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.58% [<b>43.2%</b>-50.0%]</td>
	<td>863</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.37% [<b>44.1%</b>-46.7%]</td>
	<td>5,814</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.29% [<b>45.2%</b>-47.4%]</td>
	<td>7,729</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.37% [44.1%-<b>46.7%</b>]</td>
	<td>5,814</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.49% [42.3%-<b>46.7%</b>]</td>
	<td>2,059</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.29% [45.2%-<b>47.4%</b>]</td>
	<td>7,729</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.99% [43.0%-<b>49.0%</b>]</td>
	<td>1,085</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.47% [45.8%-<b>49.2%</b>]</td>
	<td>3,457</td>
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
	<td>47.62% [47.4%-47.8%]</td>
	<td>252,908</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.85% [<b>40.7%</b>-47.0%]</td>
	<td>976</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>44.84% [<b>42.9%</b>-46.8%]</td>
	<td>2,529</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.99% [<b>43.0%</b>-46.9%]</td>
	<td>2,623</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>44.92% [<b>43.1%</b>-46.8%]</td>
	<td>2,952</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.04% [<b>43.4%</b>-48.7%]</td>
	<td>1,375</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.37% [44.3%-<b>46.4%</b>]</td>
	<td>9,105</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.62% [44.7%-<b>46.5%</b>]</td>
	<td>12,042</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.46% [44.3%-<b>46.6%</b>]</td>
	<td>7,475</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.69% [44.7%-<b>46.7%</b>]</td>
	<td>9,727</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>44.92% [43.1%-<b>46.8%</b>]</td>
	<td>2,952</td>
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
	<td>50.19% [50.0%-50.4%]</td>
	<td>333,971</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.51% [<b>41.6%</b>-47.4%]</td>
	<td>1,175</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.09% [<b>42.8%</b>-47.4%]</td>
	<td>1,874</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.21% [<b>44.4%</b>-48.0%]</td>
	<td>2,943</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.29% [<b>45.4%</b>-47.1%]</td>
	<td>13,568</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.00% [<b>45.8%</b>-48.2%]</td>
	<td>6,945</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.29% [45.4%-<b>47.1%</b>]</td>
	<td>13,568</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.09% [42.8%-<b>47.4%</b>]</td>
	<td>1,874</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.51% [41.6%-<b>47.4%</b>]</td>
	<td>1,175</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.98% [46.0%-<b>48.0%</b>]</td>
	<td>9,967</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.21% [44.4%-<b>48.0%</b>]</td>
	<td>2,943</td>
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
	<td>52.84% [52.5%-53.2%]</td>
	<td>75,152</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>48.00% [<b>42.5%</b>-53.5%]</td>
	<td>325</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>49.15% [<b>42.6%</b>-55.7%]</td>
	<td>236</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>49.21% [<b>42.9%</b>-55.5%]</td>
	<td>254</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>50.00% [<b>45.4%</b>-54.6%]</td>
	<td>472</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>48.56% [<b>45.6%</b>-51.5%]</td>
	<td>1,149</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>48.52% [46.9%-<b>50.1%</b>]</td>
	<td>3,796</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.88% [47.2%-<b>50.5%</b>]</td>
	<td>3,756</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.48% [46.4%-<b>50.6%</b>]</td>
	<td>2,310</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.99% [47.1%-<b>50.9%</b>]</td>
	<td>2,786</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>48.56% [45.6%-<b>51.5%</b>]</td>
	<td>1,149</td>
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
	<td>49.40% [49.1%-49.7%]</td>
	<td>86,159</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>44.80% [<b>40.0%</b>-49.6%]</td>
	<td>433</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>48.43% [<b>42.5%</b>-54.3%]</td>
	<td>287</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.72% [<b>42.8%</b>-46.6%]</td>
	<td>2,661</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.46% [<b>43.2%</b>-53.8%]</td>
	<td>357</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.93% [<b>43.3%</b>-48.6%]</td>
	<td>1,437</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.72% [42.8%-<b>46.6%</b>]</td>
	<td>2,661</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.50% [43.5%-<b>47.5%</b>]</td>
	<td>2,479</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.93% [43.3%-<b>48.6%</b>]</td>
	<td>1,437</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.67% [44.8%-<b>48.6%</b>]</td>
	<td>2,721</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.47% [45.9%-<b>49.1%</b>]</td>
	<td>3,954</td>
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
	<td>48.04% [47.9%-48.2%]</td>
	<td>301,344</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.93% [<b>39.9%</b>-46.0%]</td>
	<td>1,039</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.72% [<b>42.1%</b>-47.3%]</td>
	<td>1,449</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>46.21% [<b>42.7%</b>-49.8%]</td>
	<td>792</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.24% [<b>43.2%</b>-45.2%]</td>
	<td>9,796</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.54% [<b>43.6%</b>-45.5%]</td>
	<td>10,615</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.24% [43.2%-<b>45.2%</b>]</td>
	<td>9,796</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.54% [43.6%-<b>45.5%</b>]</td>
	<td>10,615</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.93% [39.9%-<b>46.0%</b>]</td>
	<td>1,039</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.98% [43.6%-<b>46.4%</b>]</td>
	<td>5,231</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.79% [45.0%-<b>46.6%</b>]</td>
	<td>15,540</td>
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
	<td>48.33% [48.0%-48.6%]</td>
	<td>105,180</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>41.72% [<b>37.0%</b>-46.5%]</td>
	<td>429</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-bel-veth"></span> Bel'Veth</td>
	<td>45.03% [<b>41.7%</b>-48.3%]</td>
	<td>906</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.29% [<b>42.6%</b>-46.0%]</td>
	<td>3,418</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.77% [<b>43.3%</b>-48.2%]</td>
	<td>1,667</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.03% [<b>43.5%</b>-48.5%]</td>
	<td>1,601</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.29% [42.6%-<b>46.0%</b>]</td>
	<td>3,418</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>41.72% [37.0%-<b>46.5%</b>]</td>
	<td>429</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.04% [44.6%-<b>47.4%</b>]</td>
	<td>5,078</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>46.38% [44.7%-<b>48.1%</b>]</td>
	<td>3,493</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.77% [43.3%-<b>48.2%</b>]</td>
	<td>1,667</td>
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
	<td>49.53% [49.2%-49.9%]</td>
	<td>91,643</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.28% [<b>40.4%</b>-50.1%]</td>
	<td>424</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.32% [<b>41.5%</b>-53.1%]</td>
	<td>298</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>47.40% [<b>43.1%</b>-51.7%]</td>
	<td>538</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>50.20% [<b>43.8%</b>-56.6%]</td>
	<td>245</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.37% [<b>43.9%</b>-48.8%]</td>
	<td>1,639</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.37% [43.9%-<b>48.8%</b>]</td>
	<td>1,639</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>46.98% [45.1%-<b>48.8%</b>]</td>
	<td>2,880</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>47.18% [45.2%-<b>49.1%</b>]</td>
	<td>2,675</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.46% [45.7%-<b>49.2%</b>]</td>
	<td>3,274</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.94% [44.6%-<b>49.3%</b>]</td>
	<td>1,830</td>
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
	<td>47.34% [47.1%-47.5%]</td>
	<td>249,536</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>40.35% [<b>36.9%</b>-43.8%]</td>
	<td>803</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.20% [<b>41.3%</b>-47.1%]</td>
	<td>1,163</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>44.92% [<b>41.8%</b>-48.0%]</td>
	<td>1,013</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.85% [<b>42.7%</b>-45.0%]</td>
	<td>8,014</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.28% [<b>43.2%</b>-45.4%]</td>
	<td>8,153</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>40.35% [36.9%-<b>43.8%</b>]</td>
	<td>803</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.85% [42.7%-<b>45.0%</b>]</td>
	<td>8,014</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>44.32% [43.4%-<b>45.3%</b>]</td>
	<td>11,188</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.28% [43.2%-<b>45.4%</b>]</td>
	<td>8,153</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>44.85% [43.7%-<b>46.0%</b>]</td>
	<td>7,235</td>
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
	<td>47.62% [47.5%-47.8%]</td>
	<td>375,661</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>39.52% [<b>37.0%</b>-42.1%]</td>
	<td>1,450</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>43.33% [<b>41.2%</b>-45.4%]</td>
	<td>2,220</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.19% [<b>41.4%</b>-43.0%]</td>
	<td>14,431</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>43.93% [<b>43.2%</b>-44.7%]</td>
	<td>17,111</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>44.62% [<b>43.3%</b>-46.0%]</td>
	<td>5,435</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>39.52% [37.0%-<b>42.1%</b>]</td>
	<td>1,450</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.19% [41.4%-<b>43.0%</b>]</td>
	<td>14,431</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>43.93% [43.2%-<b>44.7%</b>]</td>
	<td>17,111</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.39% [43.5%-<b>45.3%</b>]</td>
	<td>11,665</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>43.33% [41.2%-<b>45.4%</b>]</td>
	<td>2,220</td>
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
	<td>46.63% [46.4%-46.8%]</td>
	<td>255,230</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>43.22% [<b>40.9%</b>-45.6%]</td>
	<td>1,807</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>44.05% [<b>41.2%</b>-46.9%]</td>
	<td>1,201</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.18% [<b>41.6%</b>-44.8%]</td>
	<td>3,891</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>43.66% [<b>42.0%</b>-45.3%]</td>
	<td>3,527</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>45.37% [<b>42.0%</b>-48.7%]</td>
	<td>875</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.13% [42.1%-<b>44.2%</b>]</td>
	<td>8,823</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>43.49% [42.3%-<b>44.7%</b>]</td>
	<td>6,792</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.18% [41.6%-<b>44.8%</b>]</td>
	<td>3,891</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>43.49% [42.1%-<b>44.9%</b>]</td>
	<td>4,751</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>43.66% [42.0%-<b>45.3%</b>]</td>
	<td>3,527</td>
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
	<td>46.92% [46.7%-47.1%]</td>
	<td>317,205</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>42.71% [<b>39.7%</b>-45.7%]</td>
	<td>1,098</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.14% [<b>41.1%</b>-45.2%]</td>
	<td>2,302</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>43.55% [<b>41.4%</b>-45.7%]</td>
	<td>2,094</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.59% [<b>41.7%</b>-49.5%]</td>
	<td>658</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>43.30% [<b>41.8%</b>-44.8%]</td>
	<td>4,314</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.30% [42.2%-<b>44.4%</b>]</td>
	<td>7,663</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>43.30% [41.8%-<b>44.8%</b>]</td>
	<td>4,314</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.88% [42.7%-<b>45.0%</b>]</td>
	<td>7,446</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.98% [42.9%-<b>45.0%</b>]</td>
	<td>8,869</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.14% [41.1%-<b>45.2%</b>]</td>
	<td>2,302</td>
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
	<td>50.17% [50.0%-50.4%]</td>
	<td>224,840</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>39.04% [<b>35.6%</b>-42.5%]</td>
	<td>812</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>41.78% [<b>40.6%</b>-42.9%]</td>
	<td>7,498</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.45% [<b>43.3%</b>-45.6%]</td>
	<td>7,971</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.70% [<b>44.5%</b>-48.9%]</td>
	<td>2,002</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.38% [<b>44.5%</b>-50.2%]</td>
	<td>1,239</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>39.04% [35.6%-<b>42.5%</b>]</td>
	<td>812</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>41.78% [40.6%-<b>42.9%</b>]</td>
	<td>7,498</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.45% [43.3%-<b>45.6%</b>]</td>
	<td>7,971</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.98% [44.6%-<b>47.3%</b>]</td>
	<td>5,496</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.32% [44.6%-<b>48.1%</b>]</td>
	<td>3,204</td>
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
	<td>48.81% [48.5%-49.1%]</td>
	<td>104,307</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>42.78% [<b>37.5%</b>-48.0%]</td>
	<td>353</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>44.25% [<b>40.4%</b>-48.1%]</td>
	<td>669</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>45.31% [<b>40.6%</b>-50.0%]</td>
	<td>448</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.06% [<b>40.7%</b>-47.4%]</td>
	<td>876</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>44.63% [<b>42.6%</b>-46.6%]</td>
	<td>2,478</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>44.63% [42.6%-<b>46.6%</b>]</td>
	<td>2,478</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.36% [43.4%-<b>47.3%</b>]</td>
	<td>2,553</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.06% [40.7%-<b>47.4%</b>]</td>
	<td>876</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>42.78% [37.5%-<b>48.0%</b>]</td>
	<td>353</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.37% [42.7%-<b>48.1%</b>]</td>
	<td>1,362</td>
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
	<td>48.90% [48.5%-49.3%]</td>
	<td>67,021</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.39% [<b>39.5%</b>-49.3%]</td>
	<td>410</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.22% [<b>39.8%</b>-52.7%]</td>
	<td>238</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.58% [<b>40.3%</b>-50.9%]</td>
	<td>351</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>46.82% [<b>40.7%</b>-52.9%]</td>
	<td>267</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.26% [<b>41.4%</b>-53.1%]</td>
	<td>292</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.50% [42.5%-<b>46.5%</b>]</td>
	<td>2,389</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-viego"></span> Viego</td>
	<td>47.56% [46.2%-<b>49.0%</b>]</td>
	<td>5,088</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.39% [39.5%-<b>49.3%</b>]</td>
	<td>410</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.60% [45.9%-<b>49.3%</b>]</td>
	<td>3,410</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>47.12% [44.9%-<b>49.4%</b>]</td>
	<td>1,944</td>
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
	<td>49.21% [48.9%-49.5%]</td>
	<td>99,347</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>43.76% [<b>39.3%</b>-48.2%]</td>
	<td>505</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>44.74% [<b>39.4%</b>-50.1%]</td>
	<td>342</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.06% [<b>41.4%</b>-52.8%]</td>
	<td>306</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>46.86% [<b>41.8%</b>-52.0%]</td>
	<td>382</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>43.58% [<b>41.8%</b>-45.4%]</td>
	<td>3,086</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>43.58% [41.8%-<b>45.4%</b>]</td>
	<td>3,086</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.83% [44.1%-<b>47.6%</b>]</td>
	<td>3,284</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.78% [44.0%-<b>47.6%</b>]</td>
	<td>3,095</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>43.76% [39.3%-<b>48.2%</b>]</td>
	<td>505</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.33% [44.2%-<b>48.4%</b>]</td>
	<td>2,251</td>
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
	<td>49.16% [48.8%-49.5%]</td>
	<td>89,375</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>42.86% [<b>38.0%</b>-47.7%]</td>
	<td>413</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.08% [<b>39.3%</b>-52.8%]</td>
	<td>217</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.99% [<b>39.7%</b>-50.3%]</td>
	<td>349</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xin-zhao"></span> Xin Zhao</td>
	<td>46.27% [<b>43.6%</b>-49.0%]</td>
	<td>1,381</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.01% [<b>43.7%</b>-48.3%]</td>
	<td>1,867</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>42.86% [38.0%-<b>47.7%</b>]</td>
	<td>413</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.93% [44.0%-<b>47.9%</b>]</td>
	<td>2,580</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.01% [43.7%-<b>48.3%</b>]</td>
	<td>1,867</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.42% [45.9%-<b>48.9%</b>]</td>
	<td>4,285</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xin-zhao"></span> Xin Zhao</td>
	<td>46.27% [43.6%-<b>49.0%</b>]</td>
	<td>1,381</td>
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
	<td>44.25% [44.0%-44.5%]</td>
	<td>168,430</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>40.27% [<b>36.3%</b>-44.3%]</td>
	<td>601</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>37.47% [<b>36.3%</b>-38.7%]</td>
	<td>6,528</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>39.82% [<b>37.6%</b>-42.1%]</td>
	<td>1,866</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>40.65% [<b>39.0%</b>-42.3%]</td>
	<td>3,604</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>42.61% [<b>39.0%</b>-46.2%]</td>
	<td>765</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>37.47% [36.3%-<b>38.7%</b>]</td>
	<td>6,528</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>40.72% [39.4%-<b>42.0%</b>]</td>
	<td>5,913</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>39.82% [37.6%-<b>42.1%</b>]</td>
	<td>1,866</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>40.65% [39.0%-<b>42.3%</b>]</td>
	<td>3,604</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>41.36% [40.3%-<b>42.5%</b>]</td>
	<td>8,122</td>
</tr>
</table>

</details>
### Mid

<details>
<summary>Click to view</summary>

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
	<td>52.75% [52.6%-52.9%]</td>
	<td>352,486</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>49.16% [<b>46.6%</b>-51.7%]</td>
	<td>1,495</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>49.44% [<b>47.9%</b>-50.9%]</td>
	<td>4,486</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>48.65% [<b>48.0%</b>-49.3%]</td>
	<td>22,504</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>52.30% [<b>48.0%</b>-56.6%]</td>
	<td>543</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>49.67% [<b>48.0%</b>-51.3%]</td>
	<td>3,666</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>48.65% [48.0%-<b>49.3%</b>]</td>
	<td>22,504</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>50.02% [49.4%-<b>50.7%</b>]</td>
	<td>23,321</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>49.76% [48.7%-<b>50.8%</b>]</td>
	<td>8,614</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>49.44% [47.9%-<b>50.9%</b>]</td>
	<td>4,486</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>49.83% [48.7%-<b>50.9%</b>]</td>
	<td>8,049</td>
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
	<td>52.24% [52.1%-52.4%]</td>
	<td>687,251</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.47% [<b>45.3%</b>-49.6%]</td>
	<td>2,170</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.48% [<b>47.0%</b>-50.0%]</td>
	<td>4,431</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>49.93% [<b>47.8%</b>-52.1%]</td>
	<td>2,163</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.65% [<b>47.8%</b>-49.5%]</td>
	<td>15,234</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>48.81% [<b>48.0%</b>-49.6%]</td>
	<td>15,529</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.65% [47.8%-<b>49.5%</b>]</td>
	<td>15,234</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>48.81% [48.0%-<b>49.6%</b>]</td>
	<td>15,529</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.47% [45.3%-<b>49.6%</b>]</td>
	<td>2,170</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.48% [47.0%-<b>50.0%</b>]</td>
	<td>4,431</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>49.61% [49.0%-<b>50.3%</b>]</td>
	<td>23,041</td>
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
	<td>50.65% [50.6%-50.7%]</td>
	<td>1,178,900</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.08% [<b>46.6%</b>-47.5%]</td>
	<td>50,135</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.11% [<b>46.8%</b>-49.5%]</td>
	<td>5,489</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.81% [<b>46.8%</b>-48.8%]</td>
	<td>10,048</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>48.08% [<b>47.1%</b>-49.1%]</td>
	<td>10,016</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.65% [<b>47.2%</b>-50.1%]</td>
	<td>4,516</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.08% [46.6%-<b>47.5%</b>]</td>
	<td>50,135</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.81% [46.8%-<b>48.8%</b>]</td>
	<td>10,048</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>48.08% [47.1%-<b>49.1%</b>]</td>
	<td>10,016</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>48.73% [48.2%-<b>49.2%</b>]</td>
	<td>39,504</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>48.84% [48.3%-<b>49.4%</b>]</td>
	<td>35,982</td>
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
	<td>52.60% [52.3%-52.9%]</td>
	<td>146,696</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>49.59% [<b>45.1%</b>-54.1%]</td>
	<td>486</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>51.33% [<b>46.6%</b>-56.0%]</td>
	<td>452</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>49.74% [<b>47.0%</b>-52.5%]</td>
	<td>1,349</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>48.76% [<b>47.0%</b>-50.5%]</td>
	<td>3,359</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>49.56% [<b>47.2%</b>-51.9%]</td>
	<td>1,806</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>48.76% [47.0%-<b>50.5%</b>]</td>
	<td>3,359</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>49.54% [48.1%-<b>50.9%</b>]</td>
	<td>5,075</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>49.18% [47.3%-<b>51.0%</b>]</td>
	<td>2,985</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>50.33% [49.1%-<b>51.5%</b>]</td>
	<td>6,746</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>50.35% [48.9%-<b>51.8%</b>]</td>
	<td>4,552</td>
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
	<td>52.01% [51.9%-52.1%]</td>
	<td>531,651</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.02% [<b>46.1%</b>-48.0%]</td>
	<td>10,888</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>49.24% [<b>46.5%</b>-51.9%]</td>
	<td>1,375</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>48.51% [<b>47.1%</b>-50.0%]</td>
	<td>4,712</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>48.57% [<b>47.3%</b>-49.8%]</td>
	<td>6,537</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.45% [<b>47.9%</b>-51.0%]</td>
	<td>3,943</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.02% [46.1%-<b>48.0%</b>]</td>
	<td>10,888</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.87% [48.0%-<b>49.8%</b>]</td>
	<td>11,918</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>48.57% [47.3%-<b>49.8%</b>]</td>
	<td>6,537</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>48.51% [47.1%-<b>50.0%</b>]</td>
	<td>4,712</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>50.27% [49.7%-<b>50.9%</b>]</td>
	<td>26,143</td>
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
	<td>52.73% [52.5%-52.9%]</td>
	<td>210,834</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.31% [<b>45.9%</b>-48.7%]</td>
	<td>5,054</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.04% [<b>46.5%</b>-51.6%]</td>
	<td>1,570</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>52.65% [<b>46.9%</b>-58.4%]</td>
	<td>302</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>50.97% [<b>47.9%</b>-54.1%]</td>
	<td>1,036</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>50.57% [<b>48.3%</b>-52.8%]</td>
	<td>1,924</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.31% [45.9%-<b>48.7%</b>]</td>
	<td>5,054</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>50.09% [49.0%-<b>51.2%</b>]</td>
	<td>8,556</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>50.62% [49.8%-<b>51.4%</b>]</td>
	<td>14,656</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.04% [46.5%-<b>51.6%</b>]</td>
	<td>1,570</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>50.72% [49.7%-<b>51.8%</b>]</td>
	<td>9,049</td>
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
	<td>50.76% [50.6%-50.9%]</td>
	<td>600,331</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.47% [<b>45.9%</b>-49.0%]</td>
	<td>4,177</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.62% [<b>46.2%</b>-51.1%]</td>
	<td>1,672</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>49.01% [<b>46.9%</b>-51.2%]</td>
	<td>2,163</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>48.29% [<b>46.9%</b>-49.7%]</td>
	<td>5,227</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.84% [<b>47.1%</b>-48.6%]</td>
	<td>16,615</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.84% [47.1%-<b>48.6%</b>]</td>
	<td>16,615</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.99% [47.1%-<b>48.9%</b>]</td>
	<td>12,533</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.47% [45.9%-<b>49.0%</b>]</td>
	<td>4,177</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>48.47% [47.8%-<b>49.2%</b>]</td>
	<td>19,434</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>48.46% [47.5%-<b>49.4%</b>]</td>
	<td>11,225</td>
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
	<td>52.57% [52.4%-52.7%]</td>
	<td>430,894</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.98% [<b>43.1%</b>-46.9%]</td>
	<td>2,750</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.96% [<b>45.6%</b>-50.3%]</td>
	<td>1,816</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.35% [<b>46.3%</b>-50.4%]</td>
	<td>2,430</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.31% [<b>46.6%</b>-50.0%]</td>
	<td>3,471</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>48.30% [<b>46.8%</b>-49.8%]</td>
	<td>4,453</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.98% [43.1%-<b>46.9%</b>]</td>
	<td>2,750</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.03% [47.2%-<b>48.9%</b>]</td>
	<td>14,819</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.65% [47.8%-<b>49.5%</b>]</td>
	<td>14,044</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>48.30% [46.8%-<b>49.8%</b>]</td>
	<td>4,453</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.31% [46.6%-<b>50.0%</b>]</td>
	<td>3,471</td>
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
	<td>49.38% [49.3%-49.5%]</td>
	<td>1,361,027</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>45.80% [<b>45.4%</b>-46.2%]</td>
	<td>50,322</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.34% [<b>45.5%</b>-47.1%]</td>
	<td>15,233</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.96% [<b>45.8%</b>-48.1%]</td>
	<td>7,387</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>46.98% [<b>45.9%</b>-48.1%]</td>
	<td>7,853</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.86% [<b>45.9%</b>-47.8%]</td>
	<td>10,881</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>45.80% [45.4%-<b>46.2%</b>]</td>
	<td>50,322</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.34% [45.5%-<b>47.1%</b>]</td>
	<td>15,233</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.86% [46.3%-<b>47.4%</b>]</td>
	<td>37,965</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.96% [46.5%-<b>47.4%</b>]</td>
	<td>47,293</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.86% [45.9%-<b>47.8%</b>]</td>
	<td>10,881</td>
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
	<td>52.07% [51.9%-52.2%]</td>
	<td>528,160</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.28% [<b>43.9%</b>-48.7%]</td>
	<td>1,759</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.89% [<b>45.1%</b>-48.6%]</td>
	<td>3,235</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.33% [<b>45.5%</b>-47.2%]</td>
	<td>13,060</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.91% [<b>46.0%</b>-47.8%]</td>
	<td>12,130</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.07% [<b>46.3%</b>-49.8%]</td>
	<td>3,189</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.33% [45.5%-<b>47.2%</b>]</td>
	<td>13,060</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.91% [46.0%-<b>47.8%</b>]</td>
	<td>12,130</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.89% [45.1%-<b>48.6%</b>]</td>
	<td>3,235</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.28% [43.9%-<b>48.7%</b>]</td>
	<td>1,759</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.30% [46.9%-<b>49.7%</b>]</td>
	<td>5,470</td>
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
	<td>50.37% [50.2%-50.5%]</td>
	<td>673,871</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>47.33% [<b>44.2%</b>-50.4%]</td>
	<td>1,029</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.16% [<b>44.9%</b>-49.4%]</td>
	<td>1,902</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.30% [<b>45.5%</b>-49.1%]</td>
	<td>3,040</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.76% [<b>46.0%</b>-49.5%]</td>
	<td>3,199</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>47.13% [<b>46.1%</b>-48.1%]</td>
	<td>9,776</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.15% [46.3%-<b>48.0%</b>]</td>
	<td>14,298</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.25% [46.4%-<b>48.1%</b>]</td>
	<td>15,057</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>47.13% [46.1%-<b>48.1%</b>]</td>
	<td>9,776</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.42% [46.7%-<b>48.2%</b>]</td>
	<td>18,194</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-katarina"></span> Katarina</td>
	<td>47.86% [47.1%-<b>48.6%</b>]</td>
	<td>19,650</td>
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
	<td>49.82% [49.7%-49.9%]</td>
	<td>790,166</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.12% [<b>43.5%</b>-44.7%]</td>
	<td>26,540</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.41% [<b>44.6%</b>-48.2%]</td>
	<td>3,109</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.42% [<b>44.7%</b>-48.1%]</td>
	<td>3,496</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.70% [<b>44.8%</b>-46.6%]</td>
	<td>12,886</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.55% [<b>44.9%</b>-46.2%]</td>
	<td>21,055</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.12% [43.5%-<b>44.7%</b>]</td>
	<td>26,540</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.55% [44.9%-<b>46.2%</b>]</td>
	<td>21,055</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.67% [45.1%-<b>46.3%</b>]</td>
	<td>26,001</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.70% [44.8%-<b>46.6%</b>]</td>
	<td>12,886</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.19% [45.2%-<b>47.2%</b>]</td>
	<td>10,764</td>
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
	<td>50.97% [50.8%-51.2%]</td>
	<td>217,545</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.63% [<b>43.7%</b>-49.6%]</td>
	<td>1,158</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.63% [<b>44.5%</b>-52.8%]</td>
	<td>586</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.58% [<b>44.6%</b>-52.5%]</td>
	<td>636</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.78% [<b>45.4%</b>-50.2%]</td>
	<td>1,708</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>51.47% [<b>45.8%</b>-57.2%]</td>
	<td>307</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-akali"></span> Akali</td>
	<td>47.75% [46.6%-<b>48.9%</b>]</td>
	<td>7,878</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.74% [46.3%-<b>49.2%</b>]</td>
	<td>4,788</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.63% [43.7%-<b>49.6%</b>]</td>
	<td>1,158</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>47.85% [45.8%-<b>49.9%</b>]</td>
	<td>2,470</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.64% [47.1%-<b>50.1%</b>]</td>
	<td>4,478</td>
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
	<td>49.94% [49.7%-50.2%]</td>
	<td>121,524</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.75% [<b>42.7%</b>-48.8%]</td>
	<td>1,060</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.26% [<b>44.2%</b>-48.3%]</td>
	<td>2,313</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>51.67% [<b>44.2%</b>-59.1%]</td>
	<td>180</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.90% [<b>44.5%</b>-47.3%]</td>
	<td>4,852</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.74% [<b>44.5%</b>-53.0%]</td>
	<td>554</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.90% [44.5%-<b>47.3%</b>]</td>
	<td>4,852</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.26% [44.2%-<b>48.3%</b>]</td>
	<td>2,313</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.75% [42.7%-<b>48.8%</b>]</td>
	<td>1,060</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.94% [44.7%-<b>49.2%</b>]</td>
	<td>1,979</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>47.57% [46.0%-<b>49.2%</b>]</td>
	<td>3,811</td>
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
	<td>50.54% [50.4%-50.6%]</td>
	<td>970,841</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>40.44% [<b>38.9%</b>-42.0%]</td>
	<td>3,942</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.71% [<b>44.2%</b>-45.3%]</td>
	<td>33,637</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.58% [<b>44.3%</b>-46.8%]</td>
	<td>6,316</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>45.81% [<b>44.7%</b>-46.9%]</td>
	<td>8,300</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.64% [<b>45.0%</b>-46.3%]</td>
	<td>22,800</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>40.44% [38.9%-<b>42.0%</b>]</td>
	<td>3,942</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.71% [44.2%-<b>45.3%</b>]</td>
	<td>33,637</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.64% [45.0%-<b>46.3%</b>]</td>
	<td>22,800</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>46.01% [45.4%-<b>46.6%</b>]</td>
	<td>29,649</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.58% [44.3%-<b>46.8%</b>]</td>
	<td>6,316</td>
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
	<td>50.05% [49.8%-50.3%]</td>
	<td>204,345</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.15% [<b>40.5%</b>-47.8%]</td>
	<td>752</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>46.89% [<b>43.9%</b>-49.9%]</td>
	<td>1,111</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.93% [<b>43.9%</b>-47.9%]</td>
	<td>2,528</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.39% [<b>44.4%</b>-52.4%]</td>
	<td>620</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.07% [<b>44.7%</b>-51.4%]</td>
	<td>880</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.15% [40.5%-<b>47.8%</b>]</td>
	<td>752</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.93% [43.9%-<b>47.9%</b>]</td>
	<td>2,528</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.81% [45.3%-<b>48.3%</b>]</td>
	<td>4,527</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>47.67% [46.7%-<b>48.6%</b>]</td>
	<td>10,819</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lissandra"></span> Lissandra</td>
	<td>46.93% [45.1%-<b>48.7%</b>]</td>
	<td>3,009</td>
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
	<td>49.15% [49.0%-49.3%]</td>
	<td>507,667</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.96% [<b>43.0%</b>-44.9%]</td>
	<td>10,994</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.59% [<b>43.5%</b>-47.7%]</td>
	<td>2,220</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.53% [<b>43.9%</b>-49.2%]</td>
	<td>1,414</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.53% [<b>44.4%</b>-48.6%]</td>
	<td>2,261</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.28% [<b>44.6%</b>-50.0%]</td>
	<td>1,343</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.96% [43.0%-<b>44.9%</b>]</td>
	<td>10,994</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.43% [45.7%-<b>47.2%</b>]</td>
	<td>16,416</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.64% [45.6%-<b>47.6%</b>]</td>
	<td>9,796</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>46.29% [44.9%-<b>47.7%</b>]</td>
	<td>5,180</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.59% [43.5%-<b>47.7%</b>]</td>
	<td>2,220</td>
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
	<td>48.20% [48.0%-48.4%]</td>
	<td>293,094</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.28% [<b>41.3%</b>-45.3%]</td>
	<td>2,410</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.57% [<b>43.3%</b>-45.8%]</td>
	<td>6,044</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.51% [<b>43.5%</b>-45.5%]</td>
	<td>10,574</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.00% [<b>43.6%</b>-50.4%]</td>
	<td>866</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.92% [<b>43.8%</b>-48.0%]</td>
	<td>2,206</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.28% [41.3%-<b>45.3%</b>]</td>
	<td>2,410</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.51% [43.5%-<b>45.5%</b>]</td>
	<td>10,574</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.57% [43.3%-<b>45.8%</b>]</td>
	<td>6,044</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>45.46% [44.4%-<b>46.5%</b>]</td>
	<td>8,821</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>45.94% [44.9%-<b>47.0%</b>]</td>
	<td>8,631</td>
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
	<td>51.02% [50.8%-51.2%]</td>
	<td>307,019</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.01% [<b>40.6%</b>-47.4%]</td>
	<td>868</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.72% [<b>43.2%</b>-48.2%]</td>
	<td>1,564</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.16% [<b>44.2%</b>-48.1%]</td>
	<td>2,552</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>50.50% [<b>45.5%</b>-55.5%]</td>
	<td>402</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.58% [<b>46.3%</b>-48.9%]</td>
	<td>6,137</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.01% [40.6%-<b>47.4%</b>]</td>
	<td>868</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.16% [44.2%-<b>48.1%</b>]</td>
	<td>2,552</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.72% [43.2%-<b>48.2%</b>]</td>
	<td>1,564</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.58% [46.3%-<b>48.9%</b>]</td>
	<td>6,137</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>48.34% [47.5%-<b>49.2%</b>]</td>
	<td>13,818</td>
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
	<td>51.80% [51.7%-51.9%]</td>
	<td>540,508</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.42% [<b>42.3%</b>-46.5%]</td>
	<td>2,260</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.07% [<b>43.0%</b>-47.1%]</td>
	<td>2,403</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.29% [<b>44.6%</b>-50.0%]</td>
	<td>1,402</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.40% [<b>44.7%</b>-50.1%]</td>
	<td>1,367</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.60% [<b>44.9%</b>-46.3%]</td>
	<td>20,218</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.60% [44.9%-<b>46.3%</b>]</td>
	<td>20,218</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.42% [42.3%-<b>46.5%</b>]</td>
	<td>2,260</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.07% [43.0%-<b>47.1%</b>]</td>
	<td>2,403</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.43% [44.9%-<b>48.0%</b>]</td>
	<td>4,254</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>47.40% [46.0%-<b>48.8%</b>]</td>
	<td>5,375</td>
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
	<td>50.62% [50.4%-50.8%]</td>
	<td>303,219</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.46% [<b>41.7%</b>-47.2%]</td>
	<td>1,300</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.60% [<b>42.8%</b>-48.4%]</td>
	<td>1,261</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.81% [<b>43.3%</b>-50.3%]</td>
	<td>831</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.90% [<b>43.6%</b>-48.2%]</td>
	<td>1,904</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.94% [<b>44.1%</b>-47.8%]</td>
	<td>2,869</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.46% [41.7%-<b>47.2%</b>]</td>
	<td>1,300</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.02% [44.5%-<b>47.5%</b>]</td>
	<td>4,598</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.17% [44.7%-<b>47.6%</b>]</td>
	<td>4,750</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.52% [45.4%-<b>47.7%</b>]</td>
	<td>7,432</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.66% [45.6%-<b>47.7%</b>]</td>
	<td>9,348</td>
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
	<td>48.97% [48.9%-49.1%]</td>
	<td>1,159,127</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.57% [<b>42.3%</b>-44.9%]</td>
	<td>5,991</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.40% [<b>42.8%</b>-46.0%]</td>
	<td>3,824</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>44.07% [<b>43.2%</b>-45.0%]</td>
	<td>11,697</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.54% [<b>43.5%</b>-45.6%]</td>
	<td>9,064</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.50% [<b>43.9%</b>-45.1%]</td>
	<td>24,739</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.57% [42.3%-<b>44.9%</b>]</td>
	<td>5,991</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>44.07% [43.2%-<b>45.0%</b>]</td>
	<td>11,697</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.50% [43.9%-<b>45.1%</b>]</td>
	<td>24,739</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.68% [44.2%-<b>45.2%</b>]</td>
	<td>36,658</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.54% [43.5%-<b>45.6%</b>]</td>
	<td>9,064</td>
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
	<td>50.89% [50.6%-51.2%]</td>
	<td>103,641</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>50.41% [<b>41.3%</b>-59.5%]</td>
	<td>121</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.09% [<b>42.8%</b>-49.4%]</td>
	<td>896</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.87% [<b>43.2%</b>-54.6%]</td>
	<td>309</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>48.20% [<b>44.8%</b>-51.6%]</td>
	<td>863</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.95% [<b>44.9%</b>-49.0%]</td>
	<td>2,445</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.95% [44.9%-<b>49.0%</b>]</td>
	<td>2,445</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.25% [45.1%-<b>49.4%</b>]</td>
	<td>2,239</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.09% [42.8%-<b>49.4%</b>]</td>
	<td>896</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>48.59% [47.4%-<b>49.8%</b>]</td>
	<td>6,861</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>47.91% [45.2%-<b>50.6%</b>]</td>
	<td>1,390</td>
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
	<td>50.86% [50.6%-51.1%]</td>
	<td>224,392</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>46.86% [<b>41.8%</b>-52.0%]</td>
	<td>382</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.85% [<b>42.4%</b>-47.3%]</td>
	<td>1,688</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.68% [<b>42.7%</b>-46.7%]</td>
	<td>2,536</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.12% [<b>43.4%</b>-50.9%]</td>
	<td>711</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.17% [<b>43.9%</b>-48.4%]</td>
	<td>1,956</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.68% [42.7%-<b>46.7%</b>]</td>
	<td>2,536</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.85% [42.4%-<b>47.3%</b>]</td>
	<td>1,688</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.86% [44.4%-<b>47.3%</b>]</td>
	<td>4,514</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.35% [44.9%-<b>47.8%</b>]</td>
	<td>4,992</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.11% [45.9%-<b>48.3%</b>]</td>
	<td>6,737</td>
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
	<td>49.43% [49.3%-49.6%]</td>
	<td>643,622</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.05% [<b>41.9%</b>-46.2%]</td>
	<td>2,150</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.15% [<b>41.9%</b>-44.4%]</td>
	<td>6,631</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.17% [<b>42.5%</b>-43.9%]</td>
	<td>21,001</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.48% [<b>43.1%</b>-47.9%]</td>
	<td>1,691</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>44.10% [<b>43.5%</b>-44.7%]</td>
	<td>31,145</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.17% [42.5%-<b>43.9%</b>]</td>
	<td>21,001</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.15% [41.9%-<b>44.4%</b>]</td>
	<td>6,631</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>44.10% [43.5%-<b>44.7%</b>]</td>
	<td>31,145</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.05% [41.9%-<b>46.2%</b>]</td>
	<td>2,150</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.56% [44.9%-<b>46.3%</b>]</td>
	<td>20,171</td>
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
	<td>48.94% [48.8%-49.1%]</td>
	<td>538,118</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.76% [<b>41.3%</b>-46.2%]</td>
	<td>1,684</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.63% [<b>41.9%</b>-43.4%]</td>
	<td>17,068</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.56% [<b>42.0%</b>-45.1%]</td>
	<td>4,020</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.24% [<b>42.1%</b>-46.4%]</td>
	<td>2,163</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.94% [<b>42.1%</b>-45.8%]</td>
	<td>2,956</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.63% [41.9%-<b>43.4%</b>]</td>
	<td>17,068</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.56% [42.0%-<b>45.1%</b>]</td>
	<td>4,020</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.94% [42.1%-<b>45.8%</b>]</td>
	<td>2,956</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.76% [41.3%-<b>46.2%</b>]</td>
	<td>1,684</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.37% [44.5%-<b>46.3%</b>]</td>
	<td>12,139</td>
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
	<td>51.23% [51.1%-51.4%]</td>
	<td>319,920</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.34% [<b>41.1%</b>-45.6%]</td>
	<td>1,913</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.60% [<b>41.7%</b>-47.5%]</td>
	<td>1,177</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.07% [<b>42.5%</b>-47.6%]</td>
	<td>1,511</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.56% [<b>43.1%</b>-50.0%]</td>
	<td>829</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.32% [<b>44.2%</b>-46.4%]</td>
	<td>7,823</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.34% [41.1%-<b>45.6%</b>]</td>
	<td>1,913</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.32% [44.2%-<b>46.4%</b>]</td>
	<td>7,823</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.60% [41.7%-<b>47.5%</b>]</td>
	<td>1,177</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.07% [42.5%-<b>47.6%</b>]</td>
	<td>1,511</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.43% [47.5%-<b>49.3%</b>]</td>
	<td>12,592</td>
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
	<td>48.25% [48.0%-48.5%]</td>
	<td>194,878</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.06% [<b>40.5%</b>-47.6%]</td>
	<td>774</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.92% [<b>41.5%</b>-46.3%]</td>
	<td>1,753</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.65% [<b>42.0%</b>-47.3%]</td>
	<td>1,411</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.50% [<b>42.3%</b>-50.7%]</td>
	<td>557</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>45.20% [<b>42.6%</b>-47.8%]</td>
	<td>1,500</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.62% [43.0%-<b>46.2%</b>]</td>
	<td>3,888</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.92% [41.5%-<b>46.3%</b>]</td>
	<td>1,753</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.48% [44.0%-<b>46.9%</b>]</td>
	<td>4,672</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.65% [42.0%-<b>47.3%</b>]</td>
	<td>1,411</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.55% [43.5%-<b>47.6%</b>]</td>
	<td>2,303</td>
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
	<td>49.84% [49.6%-50.0%]</td>
	<td>256,756</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.09% [<b>39.5%</b>-46.7%]</td>
	<td>745</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.29% [<b>41.5%</b>-45.1%]</td>
	<td>2,966</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.13% [<b>42.0%</b>-44.2%]</td>
	<td>8,030</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.07% [<b>42.6%</b>-47.5%]</td>
	<td>1,633</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.81% [<b>43.0%</b>-48.7%]</td>
	<td>1,218</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.13% [42.0%-<b>44.2%</b>]</td>
	<td>8,030</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.29% [41.5%-<b>45.1%</b>]</td>
	<td>2,966</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.26% [43.9%-<b>46.6%</b>]</td>
	<td>5,133</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.09% [39.5%-<b>46.7%</b>]</td>
	<td>745</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.07% [42.6%-<b>47.5%</b>]</td>
	<td>1,633</td>
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
	<td>52.37% [52.0%-52.7%]</td>
	<td>73,503</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.58% [<b>40.7%</b>-50.4%]</td>
	<td>419</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.92% [<b>41.4%</b>-48.5%]</td>
	<td>788</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.21% [<b>42.2%</b>-50.2%]</td>
	<td>634</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>49.58% [<b>43.1%</b>-56.1%]</td>
	<td>236</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>49.62% [<b>43.4%</b>-55.8%]</td>
	<td>260</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.92% [41.4%-<b>48.5%</b>]</td>
	<td>788</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.70% [46.0%-<b>49.4%</b>]</td>
	<td>3,442</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>47.81% [45.8%-<b>49.8%</b>]</td>
	<td>2,399</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.21% [42.2%-<b>50.2%</b>]</td>
	<td>634</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.36% [46.3%-<b>50.4%</b>]</td>
	<td>2,463</td>
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
	<td>49.65% [49.5%-49.8%]</td>
	<td>394,918</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.32% [<b>40.6%</b>-44.0%]</td>
	<td>3,275</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.41% [<b>41.2%</b>-45.6%]</td>
	<td>2,032</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>45.50% [<b>42.0%</b>-49.0%]</td>
	<td>833</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.48% [<b>43.6%</b>-45.4%]</td>
	<td>11,514</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lissandra"></span> Lissandra</td>
	<td>45.44% [<b>44.3%</b>-46.6%]</td>
	<td>7,571</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.32% [40.6%-<b>44.0%</b>]</td>
	<td>3,275</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.48% [43.6%-<b>45.4%</b>]</td>
	<td>11,514</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.41% [41.2%-<b>45.6%</b>]</td>
	<td>2,032</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lissandra"></span> Lissandra</td>
	<td>45.44% [44.3%-<b>46.6%</b>]</td>
	<td>7,571</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>46.63% [45.9%-<b>47.3%</b>]</td>
	<td>20,593</td>
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
	<td>49.16% [48.9%-49.4%]</td>
	<td>120,354</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>45.03% [<b>39.8%</b>-50.3%]</td>
	<td>362</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>49.03% [<b>41.0%</b>-57.1%]</td>
	<td>155</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.93% [<b>41.7%</b>-52.2%]</td>
	<td>358</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.37% [<b>42.1%</b>-52.6%]</td>
	<td>361</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.35% [<b>42.4%</b>-50.3%]</td>
	<td>643</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>45.26% [42.4%-<b>48.1%</b>]</td>
	<td>1,233</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.43% [44.5%-<b>48.4%</b>]</td>
	<td>2,576</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.49% [44.5%-<b>48.5%</b>]</td>
	<td>2,566</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.35% [44.2%-<b>48.5%</b>]</td>
	<td>2,222</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.16% [45.6%-<b>48.7%</b>]</td>
	<td>3,978</td>
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
	<td>53.27% [52.9%-53.6%]</td>
	<td>72,216</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.82% [<b>39.8%</b>-51.8%]</td>
	<td>275</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.83% [<b>40.8%</b>-48.9%]</td>
	<td>609</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.90% [<b>41.0%</b>-52.8%]</td>
	<td>290</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.38% [<b>42.0%</b>-52.8%]</td>
	<td>344</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-neeko"></span> Neeko</td>
	<td>47.79% [<b>42.4%</b>-53.2%]</td>
	<td>339</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.83% [40.8%-<b>48.9%</b>]</td>
	<td>609</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>48.01% [45.0%-<b>51.0%</b>]</td>
	<td>1,108</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vladimir"></span> Vladimir</td>
	<td>48.31% [44.8%-<b>51.8%</b>]</td>
	<td>826</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.82% [39.8%-<b>51.8%</b>]</td>
	<td>275</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>49.41% [46.9%-<b>52.0%</b>]</td>
	<td>1,538</td>
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
	<td>50.71% [50.5%-50.9%]</td>
	<td>197,679</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>44.20% [<b>39.9%</b>-48.5%]</td>
	<td>543</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>43.14% [<b>40.8%</b>-45.5%]</td>
	<td>1,787</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.11% [<b>41.4%</b>-48.8%]</td>
	<td>716</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.65% [<b>41.8%</b>-49.5%]</td>
	<td>655</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.12% [<b>42.7%</b>-51.5%]</td>
	<td>520</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>43.14% [40.8%-<b>45.5%</b>]</td>
	<td>1,787</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>45.49% [43.2%-<b>47.8%</b>]</td>
	<td>1,851</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>44.20% [39.9%-<b>48.5%</b>]</td>
	<td>543</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.11% [41.4%-<b>48.8%</b>]</td>
	<td>716</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>47.94% [47.0%-<b>48.9%</b>]</td>
	<td>12,014</td>
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
	<td>50.82% [50.5%-51.1%]</td>
	<td>97,086</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.43% [<b>37.7%</b>-47.2%]</td>
	<td>436</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>43.91% [<b>40.7%</b>-47.1%]</td>
	<td>961</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>50.59% [<b>42.9%</b>-58.3%]</td>
	<td>170</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>48.00% [<b>43.0%</b>-53.0%]</td>
	<td>400</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.84% [<b>43.2%</b>-52.5%]</td>
	<td>462</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>43.91% [40.7%-<b>47.1%</b>]</td>
	<td>961</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.43% [37.7%-<b>47.2%</b>]</td>
	<td>436</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.51% [44.7%-<b>48.3%</b>]</td>
	<td>2,991</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-katarina"></span> Katarina</td>
	<td>47.04% [44.9%-<b>49.2%</b>]</td>
	<td>2,143</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>46.87% [44.1%-<b>49.7%</b>]</td>
	<td>1,263</td>
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
	<td>52.48% [52.1%-52.8%]</td>
	<td>87,054</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.53% [<b>40.4%</b>-50.6%]</td>
	<td>380</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>48.26% [<b>40.6%</b>-55.9%]</td>
	<td>172</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.73% [<b>42.4%</b>-51.0%]</td>
	<td>535</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>45.84% [<b>42.7%</b>-49.0%]</td>
	<td>997</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.30% [<b>44.7%</b>-51.9%]</td>
	<td>764</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>45.84% [42.7%-<b>49.0%</b>]</td>
	<td>997</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.43% [45.6%-<b>49.3%</b>]</td>
	<td>2,901</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.53% [40.4%-<b>50.6%</b>]</td>
	<td>380</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.14% [47.4%-<b>50.8%</b>]</td>
	<td>3,494</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>49.42% [48.0%-<b>50.9%</b>]</td>
	<td>4,842</td>
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
	<td>52.79% [52.5%-53.1%]</td>
	<td>108,588</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.14% [<b>40.1%</b>-46.2%]</td>
	<td>1,050</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.39% [<b>40.6%</b>-50.2%]</td>
	<td>434</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>47.29% [<b>41.8%</b>-52.8%]</td>
	<td>332</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.71% [<b>42.3%</b>-51.1%]</td>
	<td>516</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.77% [<b>42.6%</b>-46.9%]</td>
	<td>2,111</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.14% [40.1%-<b>46.2%</b>]</td>
	<td>1,050</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.77% [42.6%-<b>46.9%</b>]</td>
	<td>2,111</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>47.06% [45.1%-<b>49.0%</b>]</td>
	<td>2,520</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.39% [40.6%-<b>50.2%</b>]</td>
	<td>434</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>48.74% [47.3%-<b>50.2%</b>]</td>
	<td>4,725</td>
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
	<td>47.52% [47.3%-47.7%]</td>
	<td>193,264</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.91% [<b>39.8%</b>-46.0%]</td>
	<td>1,016</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.92% [<b>40.5%</b>-49.3%]</td>
	<td>512</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>44.93% [<b>40.8%</b>-49.1%]</td>
	<td>572</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.50% [<b>40.8%</b>-46.2%]</td>
	<td>1,393</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.51% [<b>41.3%</b>-45.8%]</td>
	<td>1,942</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.51% [41.3%-<b>45.8%</b>]</td>
	<td>1,942</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>44.64% [43.3%-<b>45.9%</b>]</td>
	<td>5,775</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.91% [39.8%-<b>46.0%</b>]</td>
	<td>1,016</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.50% [40.8%-<b>46.2%</b>]</td>
	<td>1,393</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>44.83% [43.1%-<b>46.5%</b>]</td>
	<td>3,364</td>
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
	<td>51.75% [51.5%-52.0%]</td>
	<td>155,263</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>44.56% [<b>39.4%</b>-49.7%]</td>
	<td>377</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.92% [<b>40.2%</b>-47.6%]</td>
	<td>724</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.06% [<b>42.5%</b>-49.6%]</td>
	<td>786</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.46% [<b>42.7%</b>-50.2%]</td>
	<td>706</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.90% [<b>43.1%</b>-48.7%]</td>
	<td>1,233</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.92% [40.2%-<b>47.6%</b>]</td>
	<td>724</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>47.47% [46.5%-<b>48.4%</b>]</td>
	<td>11,008</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>46.97% [45.5%-<b>48.5%</b>]</td>
	<td>4,537</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.90% [43.1%-<b>48.7%</b>]</td>
	<td>1,233</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.18% [47.1%-<b>49.2%</b>]</td>
	<td>9,201</td>
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
	<td>50.48% [50.2%-50.8%]</td>
	<td>106,245</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.58% [<b>36.5%</b>-46.6%]</td>
	<td>380</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.41% [<b>40.0%</b>-46.8%]</td>
	<td>850</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.43% [<b>40.7%</b>-48.2%]</td>
	<td>709</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>46.53% [<b>41.7%</b>-51.3%]</td>
	<td>432</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>46.67% [<b>41.8%</b>-51.5%]</td>
	<td>420</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>43.98% [42.0%-<b>46.0%</b>]</td>
	<td>2,449</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.58% [36.5%-<b>46.6%</b>]</td>
	<td>380</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.41% [40.0%-<b>46.8%</b>]</td>
	<td>850</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.64% [43.9%-<b>47.4%</b>]</td>
	<td>3,118</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>45.39% [43.3%-<b>47.5%</b>]</td>
	<td>2,300</td>
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
	<td>47.86% [47.7%-48.0%]</td>
	<td>674,182</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>39.65% [<b>38.4%</b>-40.9%]</td>
	<td>6,454</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>41.24% [<b>39.7%</b>-42.8%]</td>
	<td>3,984</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.79% [<b>41.7%</b>-45.9%]</td>
	<td>2,151</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.58% [<b>41.7%</b>-45.4%]</td>
	<td>2,841</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.34% [<b>42.5%</b>-44.2%]</td>
	<td>13,863</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>39.65% [38.4%-<b>40.9%</b>]</td>
	<td>6,454</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>41.24% [39.7%-<b>42.8%</b>]</td>
	<td>3,984</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.34% [42.5%-<b>44.2%</b>]</td>
	<td>13,863</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.58% [41.7%-<b>45.4%</b>]</td>
	<td>2,841</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>45.29% [44.8%-<b>45.8%</b>]</td>
	<td>38,368</td>
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
	<td>49.17% [49.0%-49.4%]</td>
	<td>244,781</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.90% [<b>38.9%</b>-44.9%]</td>
	<td>1,055</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.20% [<b>39.5%</b>-46.9%]</td>
	<td>706</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.79% [<b>41.0%</b>-46.5%]</td>
	<td>1,297</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>45.09% [<b>42.0%</b>-48.1%]</td>
	<td>1,060</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.86% [<b>42.3%</b>-47.4%]</td>
	<td>1,487</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.90% [38.9%-<b>44.9%</b>]</td>
	<td>1,055</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.79% [41.0%-<b>46.5%</b>]</td>
	<td>1,297</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>45.39% [44.2%-<b>46.6%</b>]</td>
	<td>7,142</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.30% [43.9%-<b>46.7%</b>]</td>
	<td>5,221</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.20% [39.5%-<b>46.9%</b>]</td>
	<td>706</td>
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
	<td>52.18% [51.8%-52.6%]</td>
	<td>54,482</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>41.70% [<b>35.8%</b>-47.6%]</td>
	<td>283</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.26% [<b>39.4%</b>-51.2%]</td>
	<td>285</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>48.13% [<b>40.2%</b>-56.0%]</td>
	<td>160</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-neeko"></span> Neeko</td>
	<td>46.42% [<b>40.9%</b>-52.0%]</td>
	<td>321</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.34% [<b>42.5%</b>-48.2%]</td>
	<td>1,202</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>41.70% [35.8%-<b>47.6%</b>]</td>
	<td>283</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.34% [42.5%-<b>48.2%</b>]</td>
	<td>1,202</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.65% [42.7%-<b>50.6%</b>]</td>
	<td>626</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.26% [39.4%-<b>51.2%</b>]</td>
	<td>285</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.90% [46.6%-<b>51.2%</b>]</td>
	<td>1,867</td>
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
	<td>51.18% [50.9%-51.4%]</td>
	<td>150,244</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.61% [<b>38.0%</b>-47.2%]</td>
	<td>467</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.86% [<b>39.3%</b>-48.4%]</td>
	<td>472</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.12% [<b>41.3%</b>-51.0%]</td>
	<td>425</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.52% [<b>43.9%</b>-47.2%]</td>
	<td>3,651</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>48.59% [<b>44.3%</b>-52.9%]</td>
	<td>533</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.52% [43.9%-<b>47.2%</b>]</td>
	<td>3,651</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.61% [38.0%-<b>47.2%</b>]</td>
	<td>467</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.17% [44.6%-<b>47.7%</b>]</td>
	<td>4,208</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.77% [45.4%-<b>48.1%</b>]</td>
	<td>5,422</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.86% [39.3%-<b>48.4%</b>]</td>
	<td>472</td>
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
	<td>50.98% [50.7%-51.2%]</td>
	<td>146,504</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.58% [<b>38.5%</b>-48.7%]</td>
	<td>374</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>46.01% [<b>39.2%</b>-52.8%]</td>
	<td>213</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.61% [<b>40.4%</b>-48.9%]</td>
	<td>547</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.63% [<b>41.8%</b>-49.5%]</td>
	<td>664</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>44.78% [<b>41.8%</b>-47.8%]</td>
	<td>1,112</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.66% [43.8%-<b>47.5%</b>]</td>
	<td>3,029</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>44.78% [41.8%-<b>47.8%</b>]</td>
	<td>1,112</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.58% [38.5%-<b>48.7%</b>]</td>
	<td>374</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.61% [40.4%-<b>48.9%</b>]</td>
	<td>547</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-neeko"></span> Neeko</td>
	<td>45.91% [42.6%-<b>49.2%</b>]</td>
	<td>893</td>
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
	<td>47.90% [47.6%-48.2%]</td>
	<td>109,347</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>41.96% [<b>38.6%</b>-45.3%]</td>
	<td>858</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>47.13% [<b>39.2%</b>-55.1%]</td>
	<td>157</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.56% [<b>40.4%</b>-46.7%]</td>
	<td>994</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>45.39% [<b>40.4%</b>-50.4%]</td>
	<td>401</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.16% [<b>40.5%</b>-45.8%]</td>
	<td>1,411</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>43.28% [41.6%-<b>45.0%</b>]</td>
	<td>3,357</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.00% [40.8%-<b>45.2%</b>]</td>
	<td>1,949</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>41.96% [38.6%-<b>45.3%</b>]</td>
	<td>858</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.84% [42.3%-<b>45.4%</b>]</td>
	<td>4,204</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.16% [40.5%-<b>45.8%</b>]</td>
	<td>1,411</td>
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
	<td>50.86% [50.6%-51.2%]</td>
	<td>118,282</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>39.26% [<b>34.8%</b>-43.7%]</td>
	<td>484</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>42.40% [<b>38.9%</b>-45.9%]</td>
	<td>809</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.79% [<b>40.5%</b>-51.1%]</td>
	<td>356</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.20% [<b>40.8%</b>-45.6%]</td>
	<td>1,676</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.98% [<b>41.5%</b>-48.5%]</td>
	<td>807</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>39.26% [34.8%-<b>43.7%</b>]</td>
	<td>484</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>43.09% [41.9%-<b>44.3%</b>]</td>
	<td>7,102</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.20% [40.8%-<b>45.6%</b>]</td>
	<td>1,676</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>42.40% [38.9%-<b>45.9%</b>]</td>
	<td>809</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>43.89% [41.7%-<b>46.1%</b>]</td>
	<td>2,103</td>
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
	<td>48.13% [47.9%-48.4%]</td>
	<td>194,553</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.22% [<b>38.3%</b>-46.2%]</td>
	<td>623</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.29% [<b>38.9%</b>-47.7%]</td>
	<td>499</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>41.93% [<b>39.5%</b>-44.3%]</td>
	<td>1,698</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.67% [<b>40.3%</b>-43.0%]</td>
	<td>5,465</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.44% [<b>41.1%</b>-47.8%]</td>
	<td>900</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.67% [40.3%-<b>43.0%</b>]</td>
	<td>5,465</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>41.93% [39.5%-<b>44.3%</b>]</td>
	<td>1,698</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.22% [38.3%-<b>46.2%</b>]</td>
	<td>623</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.32% [43.8%-<b>46.9%</b>]</td>
	<td>4,228</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>45.72% [44.5%-<b>47.0%</b>]</td>
	<td>6,415</td>
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
	<td>44.48% [44.3%-44.6%]</td>
	<td>361,412</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>39.95% [<b>37.5%</b>-42.4%]</td>
	<td>1,597</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>39.42% [<b>38.4%</b>-40.4%]</td>
	<td>9,106</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>40.27% [<b>39.0%</b>-41.5%]</td>
	<td>6,118</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>40.43% [<b>39.1%</b>-41.7%]</td>
	<td>5,773</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>41.55% [<b>39.3%</b>-43.8%]</td>
	<td>1,875</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>39.42% [38.4%-<b>40.4%</b>]</td>
	<td>9,106</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>40.27% [39.0%-<b>41.5%</b>]</td>
	<td>6,118</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>40.43% [39.1%-<b>41.7%</b>]</td>
	<td>5,773</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>41.16% [40.3%-<b>42.0%</b>]</td>
	<td>13,397</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>40.98% [39.6%-<b>42.4%</b>]</td>
	<td>5,059</td>
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
	<td>48.82% [48.5%-49.2%]</td>
	<td>79,390</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>43.42% [<b>36.9%</b>-50.0%]</td>
	<td>228</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.70% [<b>37.5%</b>-47.9%]</td>
	<td>363</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>43.47% [<b>38.6%</b>-48.3%]</td>
	<td>421</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.01% [<b>38.9%</b>-47.1%]</td>
	<td>579</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.96% [<b>39.5%</b>-54.4%]</td>
	<td>181</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.01% [38.9%-<b>47.1%</b>]</td>
	<td>579</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.51% [43.2%-<b>47.9%</b>]</td>
	<td>1,804</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.70% [37.5%-<b>47.9%</b>]</td>
	<td>363</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>44.75% [41.5%-<b>48.0%</b>]</td>
	<td>943</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.11% [44.0%-<b>48.2%</b>]</td>
	<td>2,329</td>
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
	<td>45.55% [45.3%-45.8%]</td>
	<td>132,996</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>39.75% [<b>36.9%</b>-42.6%]</td>
	<td>1,190</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>41.98% [<b>37.4%</b>-46.5%]</td>
	<td>474</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>41.27% [<b>37.8%</b>-44.8%]</td>
	<td>790</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.83% [<b>38.3%</b>-47.3%]</td>
	<td>481</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>42.98% [<b>38.4%</b>-47.5%]</td>
	<td>470</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>39.75% [36.9%-<b>42.6%</b>]</td>
	<td>1,190</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>41.31% [39.9%-<b>42.7%</b>]</td>
	<td>4,798</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>41.87% [40.2%-<b>43.6%</b>]</td>
	<td>3,313</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>41.70% [39.8%-<b>43.6%</b>]</td>
	<td>2,674</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>42.30% [40.9%-<b>43.7%</b>]</td>
	<td>5,345</td>
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
	<td>45.52% [45.2%-45.8%]</td>
	<td>114,528</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>38.30% [<b>34.6%</b>-42.0%]</td>
	<td>705</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.55% [<b>36.7%</b>-48.4%]</td>
	<td>282</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>41.20% [<b>36.8%</b>-45.6%]</td>
	<td>500</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>41.31% [<b>36.9%</b>-45.8%]</td>
	<td>489</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.04% [<b>37.2%</b>-46.9%]</td>
	<td>421</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>38.30% [34.6%-<b>42.0%</b>]</td>
	<td>705</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>40.37% [38.6%-<b>42.1%</b>]</td>
	<td>3,042</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>41.48% [39.3%-<b>43.7%</b>]</td>
	<td>1,984</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>40.62% [37.4%-<b>43.8%</b>]</td>
	<td>943</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.29% [40.5%-<b>44.1%</b>]</td>
	<td>2,932</td>
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
	<td>52.12% [51.7%-52.6%]</td>
	<td>51,330</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>41.53% [<b>35.3%</b>-47.8%]</td>
	<td>248</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.12% [<b>36.5%</b>-51.7%]</td>
	<td>170</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.06% [<b>38.5%</b>-51.6%]</td>
	<td>233</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>45.80% [<b>40.4%</b>-51.2%]</td>
	<td>345</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.59% [<b>40.5%</b>-58.7%]</td>
	<td>121</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>41.53% [35.3%-<b>47.8%</b>]</td>
	<td>248</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.94% [41.5%-<b>48.4%</b>]</td>
	<td>830</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.64% [42.1%-<b>49.2%</b>]</td>
	<td>791</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>46.79% [44.3%-<b>49.3%</b>]</td>
	<td>1,575</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>47.85% [45.9%-<b>49.8%</b>]</td>
	<td>2,692</td>
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
	<td>50.02% [49.6%-50.4%]</td>
	<td>69,154</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>40.78% [<b>33.9%</b>-47.6%]</td>
	<td>206</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>39.72% [<b>34.6%</b>-44.9%]</td>
	<td>360</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>41.70% [<b>35.7%</b>-47.7%]</td>
	<td>271</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.13% [<b>40.3%</b>-50.0%]</td>
	<td>421</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.92% [<b>41.3%</b>-50.5%]</td>
	<td>466</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>39.72% [34.6%-<b>44.9%</b>]</td>
	<td>360</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>44.81% [42.4%-<b>47.3%</b>]</td>
	<td>1,658</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.78% [42.3%-<b>47.3%</b>]</td>
	<td>1,608</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>40.78% [33.9%-<b>47.6%</b>]</td>
	<td>206</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>41.70% [35.7%-<b>47.7%</b>]</td>
	<td>271</td>
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
	<td>43.49% [43.1%-43.9%]</td>
	<td>75,488</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>35.74% [<b>30.4%</b>-41.1%]</td>
	<td>319</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>41.09% [<b>32.4%</b>-49.8%]</td>
	<td>129</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>39.25% [<b>32.6%</b>-45.9%]</td>
	<td>214</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>38.56% [<b>33.6%</b>-43.5%]</td>
	<td>389</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>38.32% [<b>34.2%</b>-42.4%]</td>
	<td>561</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>38.39% [36.2%-<b>40.6%</b>]</td>
	<td>1,956</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>35.74% [30.4%-<b>41.1%</b>]</td>
	<td>319</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>40.78% [39.2%-<b>42.4%</b>]</td>
	<td>3,806</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>40.55% [38.7%-<b>42.4%</b>]</td>
	<td>2,821</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>38.32% [34.2%-<b>42.4%</b>]</td>
	<td>561</td>
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
	<td>42.65% [42.2%-43.1%]</td>
	<td>54,106</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>34.76% [<b>30.1%</b>-39.4%]</td>
	<td>420</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>41.98% [<b>31.0%</b>-52.9%]</td>
	<td>81</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>36.36% [<b>31.2%</b>-41.6%]</td>
	<td>341</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>40.74% [<b>32.3%</b>-49.2%]</td>
	<td>135</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>38.52% [<b>32.4%</b>-44.6%]</td>
	<td>257</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>35.89% [32.9%-<b>38.9%</b>]</td>
	<td>1,045</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>34.76% [30.1%-<b>39.4%</b>]</td>
	<td>420</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>36.54% [33.4%-<b>39.7%</b>]</td>
	<td>925</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>39.13% [37.0%-<b>41.3%</b>]</td>
	<td>2,042</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>36.36% [31.2%-<b>41.6%</b>]</td>
	<td>341</td>
</tr>
</table>

</details>
### ADC

<details>
<summary>Click to view</summary>

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
	<td>53.21% [52.9%-53.5%]</td>
	<td>109,720</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>51.62% [<b>47.5%</b>-55.8%]</td>
	<td>585</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>49.97% [<b>47.6%</b>-52.3%]</td>
	<td>1,837</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>50.11% [<b>47.8%</b>-52.4%]</td>
	<td>1,850</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>52.07% [<b>48.4%</b>-55.7%]</td>
	<td>749</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>51.25% [<b>49.2%</b>-53.3%]</td>
	<td>2,433</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>49.97% [47.6%-<b>52.3%</b>]</td>
	<td>1,837</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>50.11% [47.8%-<b>52.4%</b>]</td>
	<td>1,850</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>51.83% [51.0%-<b>52.7%</b>]</td>
	<td>13,546</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>51.40% [49.6%-<b>53.2%</b>]</td>
	<td>3,241</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>51.25% [49.2%-<b>53.3%</b>]</td>
	<td>2,433</td>
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
	<td>51.83% [51.7%-52.0%]</td>
	<td>333,720</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.63% [<b>44.3%</b>-49.0%]</td>
	<td>1,810</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.31% [<b>46.2%</b>-50.5%]</td>
	<td>2,165</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.43% [<b>46.2%</b>-50.6%]</td>
	<td>2,073</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.14% [<b>46.5%</b>-51.8%]</td>
	<td>1,453</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>48.21% [<b>47.1%</b>-49.4%]</td>
	<td>7,621</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.63% [44.3%-<b>49.0%</b>]</td>
	<td>1,810</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>48.21% [47.1%-<b>49.4%</b>]</td>
	<td>7,621</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>49.81% [49.3%-<b>50.3%</b>]</td>
	<td>47,233</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.31% [46.2%-<b>50.5%</b>]</td>
	<td>2,165</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.43% [46.2%-<b>50.6%</b>]</td>
	<td>2,073</td>
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
	<td>51.17% [51.1%-51.2%]</td>
	<td>2,589,105</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.57% [<b>45.7%</b>-47.4%]</td>
	<td>14,243</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.89% [<b>46.1%</b>-47.7%]</td>
	<td>14,757</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.79% [<b>46.8%</b>-48.8%]</td>
	<td>10,302</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.16% [<b>47.3%</b>-49.0%]</td>
	<td>13,546</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.48% [<b>47.7%</b>-49.2%]</td>
	<td>17,507</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.57% [45.7%-<b>47.4%</b>]</td>
	<td>14,243</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.89% [46.1%-<b>47.7%</b>]</td>
	<td>14,757</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.79% [46.8%-<b>48.8%</b>]</td>
	<td>10,302</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.16% [47.3%-<b>49.0%</b>]</td>
	<td>13,546</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.48% [47.7%-<b>49.2%</b>]</td>
	<td>17,507</td>
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
	<td>50.79% [50.7%-50.9%]</td>
	<td>567,151</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.23% [<b>45.4%</b>-49.1%]</td>
	<td>2,837</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.84% [<b>46.0%</b>-49.7%]</td>
	<td>2,824</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.41% [<b>46.2%</b>-48.6%]</td>
	<td>6,929</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.60% [<b>46.8%</b>-50.4%]</td>
	<td>3,241</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.97% [<b>47.0%</b>-51.0%]</td>
	<td>2,528</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.41% [46.2%-<b>48.6%</b>]</td>
	<td>6,929</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>48.51% [48.1%-<b>48.9%</b>]</td>
	<td>56,571</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.23% [45.4%-<b>49.1%</b>]</td>
	<td>2,837</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.84% [46.0%-<b>49.7%</b>]</td>
	<td>2,824</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>49.42% [48.9%-<b>49.9%</b>]</td>
	<td>37,580</td>
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
	<td>50.09% [50.0%-50.1%]</td>
	<td>2,803,043</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.64% [<b>42.9%</b>-44.4%]</td>
	<td>16,245</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.03% [<b>45.1%</b>-47.0%]</td>
	<td>11,598</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.95% [<b>45.2%</b>-46.7%]</td>
	<td>15,656</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.75% [<b>45.3%</b>-46.2%]</td>
	<td>43,002</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.49% [<b>45.7%</b>-47.3%]</td>
	<td>14,273</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.64% [42.9%-<b>44.4%</b>]</td>
	<td>16,245</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.75% [45.3%-<b>46.2%</b>]</td>
	<td>43,002</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.22% [45.8%-<b>46.6%</b>]</td>
	<td>58,825</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.95% [45.2%-<b>46.7%</b>]</td>
	<td>15,656</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.03% [45.1%-<b>47.0%</b>]</td>
	<td>11,598</td>
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
	<td>50.75% [50.7%-50.8%]</td>
	<td>2,130,008</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.07% [<b>44.2%</b>-45.9%]</td>
	<td>13,030</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.95% [<b>44.9%</b>-47.0%]</td>
	<td>9,657</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.90% [<b>45.9%</b>-47.9%]</td>
	<td>10,080</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.03% [<b>46.0%</b>-48.1%]</td>
	<td>8,593</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.94% [<b>46.5%</b>-47.4%]</td>
	<td>41,705</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.07% [44.2%-<b>45.9%</b>]</td>
	<td>13,030</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.95% [44.9%-<b>47.0%</b>]</td>
	<td>9,657</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.94% [46.5%-<b>47.4%</b>]</td>
	<td>41,705</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.90% [45.9%-<b>47.9%</b>]</td>
	<td>10,080</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.03% [46.0%-<b>48.1%</b>]</td>
	<td>8,593</td>
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
	<td>54.43% [54.1%-54.7%]</td>
	<td>114,350</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.93% [<b>44.3%</b>-51.6%]</td>
	<td>749</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.13% [<b>44.7%</b>-51.5%]</td>
	<td>856</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>49.34% [<b>45.7%</b>-53.0%]</td>
	<td>754</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>52.24% [<b>48.4%</b>-56.0%]</td>
	<td>693</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>51.69% [<b>49.5%</b>-53.8%]</td>
	<td>2,165</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.13% [44.7%-<b>51.5%</b>]</td>
	<td>856</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.93% [44.3%-<b>51.6%</b>]</td>
	<td>749</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>49.34% [45.7%-<b>53.0%</b>]</td>
	<td>754</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>51.69% [49.5%-<b>53.8%</b>]</td>
	<td>2,165</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>53.10% [52.3%-<b>53.9%</b>]</td>
	<td>14,757</td>
</tr>
</table>

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
	<td>50.65% [50.6%-50.7%]</td>
	<td>1,267,657</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.31% [<b>41.0%</b>-43.6%]</td>
	<td>5,500</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.54% [<b>44.2%</b>-46.9%]</td>
	<td>5,481</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.47% [<b>44.9%</b>-48.1%]</td>
	<td>3,839</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.32% [<b>45.1%</b>-47.6%]</td>
	<td>6,455</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.52% [<b>45.4%</b>-47.7%]</td>
	<td>7,637</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.31% [41.0%-<b>43.6%</b>]</td>
	<td>5,500</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.54% [44.2%-<b>46.9%</b>]</td>
	<td>5,481</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.32% [45.1%-<b>47.6%</b>]</td>
	<td>6,455</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.52% [45.4%-<b>47.7%</b>]</td>
	<td>7,637</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.25% [46.6%-<b>47.9%</b>]</td>
	<td>21,816</td>
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
	<td>55.34% [55.0%-55.6%]</td>
	<td>104,242</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.85% [<b>41.5%</b>-50.2%]</td>
	<td>530</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.51% [<b>44.1%</b>-53.0%]</td>
	<td>503</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.38% [<b>44.2%</b>-52.5%]</td>
	<td>585</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.17% [<b>45.8%</b>-50.5%]</td>
	<td>1,833</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>50.66% [<b>47.0%</b>-54.3%]</td>
	<td>754</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.85% [41.5%-<b>50.2%</b>]</td>
	<td>530</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.17% [45.8%-<b>50.5%</b>]</td>
	<td>1,833</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.38% [44.2%-<b>52.5%</b>]</td>
	<td>585</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.51% [44.1%-<b>53.0%</b>]</td>
	<td>503</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>53.10% [52.1%-<b>54.1%</b>]</td>
	<td>10,080</td>
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
	<td>54.24% [53.9%-54.6%]</td>
	<td>86,837</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.81% [<b>43.1%</b>-50.5%]</td>
	<td>720</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.76% [<b>44.0%</b>-51.6%]</td>
	<td>693</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>49.04% [<b>45.2%</b>-52.9%]</td>
	<td>679</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>50.79% [<b>48.2%</b>-53.4%]</td>
	<td>1,453</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>53.44% [<b>48.7%</b>-58.1%]</td>
	<td>451</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.81% [43.1%-<b>50.5%</b>]</td>
	<td>720</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.76% [44.0%-<b>51.6%</b>]</td>
	<td>693</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>49.04% [45.2%-<b>52.9%</b>]</td>
	<td>679</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>51.03% [49.0%-<b>53.0%</b>]</td>
	<td>2,528</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>52.21% [51.2%-<b>53.2%</b>]</td>
	<td>10,302</td>
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
	<td>50.14% [50.1%-50.2%]</td>
	<td>1,459,075</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.48% [<b>42.3%</b>-44.6%]</td>
	<td>7,650</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.77% [<b>43.4%</b>-46.1%]</td>
	<td>5,417</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.64% [<b>44.5%</b>-46.7%]</td>
	<td>8,199</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.85% [<b>44.6%</b>-47.1%]</td>
	<td>6,833</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.56% [<b>45.9%</b>-47.2%]</td>
	<td>23,211</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.48% [42.3%-<b>44.6%</b>]</td>
	<td>7,650</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.77% [43.4%-<b>46.1%</b>]</td>
	<td>5,417</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.64% [44.5%-<b>46.7%</b>]</td>
	<td>8,199</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.85% [44.6%-<b>47.1%</b>]</td>
	<td>6,833</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.56% [45.9%-<b>47.2%</b>]</td>
	<td>23,211</td>
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
	<td>50.26% [50.2%-50.3%]</td>
	<td>1,492,969</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.18% [<b>43.0%</b>-45.4%]</td>
	<td>7,091</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.48% [<b>43.4%</b>-45.6%]</td>
	<td>8,105</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.44% [<b>44.2%</b>-46.7%]</td>
	<td>6,248</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.21% [<b>45.9%</b>-48.6%]</td>
	<td>5,395</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.12% [<b>46.0%</b>-48.2%]</td>
	<td>7,851</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.18% [43.0%-<b>45.4%</b>]</td>
	<td>7,091</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.48% [43.4%-<b>45.6%</b>]</td>
	<td>8,105</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.44% [44.2%-<b>46.7%</b>]</td>
	<td>6,248</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.42% [46.7%-<b>48.1%</b>]</td>
	<td>21,940</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.12% [46.0%-<b>48.2%</b>]</td>
	<td>7,851</td>
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
	<td>52.61% [52.4%-52.8%]</td>
	<td>385,720</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.66% [<b>42.5%</b>-46.8%]</td>
	<td>2,199</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.07% [<b>43.0%</b>-47.1%]</td>
	<td>2,294</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.87% [<b>45.4%</b>-50.4%]</td>
	<td>1,596</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>48.04% [<b>46.7%</b>-49.4%]</td>
	<td>5,708</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.75% [<b>46.7%</b>-50.8%]</td>
	<td>2,433</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.66% [42.5%-<b>46.8%</b>]</td>
	<td>2,199</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.07% [43.0%-<b>47.1%</b>]</td>
	<td>2,294</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>48.04% [46.7%-<b>49.4%</b>]</td>
	<td>5,708</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>48.39% [46.9%-<b>49.8%</b>]</td>
	<td>4,743</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.87% [45.4%-<b>50.4%</b>]</td>
	<td>1,596</td>
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
	<td>49.43% [49.3%-49.6%]</td>
	<td>315,275</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>41.90% [<b>40.3%</b>-43.5%]</td>
	<td>3,967</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.32% [<b>42.8%</b>-47.9%]</td>
	<td>1,518</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.36% [<b>43.6%</b>-49.2%]</td>
	<td>1,277</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.51% [<b>43.6%</b>-49.4%]</td>
	<td>1,174</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.82% [<b>44.5%</b>-49.2%]</td>
	<td>1,826</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>41.90% [40.3%-<b>43.5%</b>]</td>
	<td>3,967</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.32% [42.8%-<b>47.9%</b>]</td>
	<td>1,518</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.91% [45.8%-<b>48.1%</b>]</td>
	<td>7,504</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>47.96% [47.4%-<b>48.5%</b>]</td>
	<td>32,322</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kai-sa"></span> Kai'Sa</td>
	<td>48.57% [48.1%-<b>49.0%</b>]</td>
	<td>43,374</td>
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
	<td>49.05% [48.9%-49.2%]</td>
	<td>739,077</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.41% [<b>42.7%</b>-46.2%]</td>
	<td>3,191</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.33% [<b>42.7%</b>-46.0%]</td>
	<td>3,521</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.55% [<b>43.8%</b>-47.3%]</td>
	<td>3,425</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.32% [<b>44.4%</b>-48.2%]</td>
	<td>2,748</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.10% [<b>45.1%</b>-49.1%]</td>
	<td>2,599</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.33% [42.7%-<b>46.0%</b>]</td>
	<td>3,521</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.41% [42.7%-<b>46.2%</b>]</td>
	<td>3,191</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.27% [45.4%-<b>47.1%</b>]</td>
	<td>12,947</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.55% [43.8%-<b>47.3%</b>]</td>
	<td>3,425</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>46.53% [45.5%-<b>47.6%</b>]</td>
	<td>8,729</td>
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
	<td>48.23% [48.1%-48.4%]</td>
	<td>464,278</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.25% [<b>42.1%</b>-46.4%]</td>
	<td>2,156</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.92% [<b>42.5%</b>-47.4%]</td>
	<td>1,672</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.96% [<b>42.8%</b>-47.1%]</td>
	<td>2,095</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.16% [<b>43.0%</b>-47.3%]</td>
	<td>2,088</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.89% [<b>43.8%</b>-46.0%]</td>
	<td>8,129</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.89% [43.8%-<b>46.0%</b>]</td>
	<td>8,129</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.25% [42.1%-<b>46.4%</b>]</td>
	<td>2,156</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>45.73% [44.6%-<b>46.9%</b>]</td>
	<td>7,185</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>46.45% [45.9%-<b>47.0%</b>]</td>
	<td>28,130</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.96% [42.8%-<b>47.1%</b>]</td>
	<td>2,095</td>
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
	<td>48.33% [48.3%-48.4%]</td>
	<td>1,649,194</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.46% [<b>42.2%</b>-44.7%]</td>
	<td>6,569</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.59% [<b>42.5%</b>-44.7%]</td>
	<td>7,800</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.73% [<b>43.6%</b>-45.8%]</td>
	<td>8,077</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>45.18% [<b>44.2%</b>-46.2%]</td>
	<td>10,036</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.28% [<b>44.5%</b>-46.0%]</td>
	<td>17,583</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.46% [42.2%-<b>44.7%</b>]</td>
	<td>6,569</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.59% [42.5%-<b>44.7%</b>]</td>
	<td>7,800</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.73% [43.6%-<b>45.8%</b>]</td>
	<td>8,077</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.28% [44.5%-<b>46.0%</b>]</td>
	<td>17,583</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>45.18% [44.2%-<b>46.2%</b>]</td>
	<td>10,036</td>
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
	<td>52.33% [52.0%-52.7%]</td>
	<td>79,634</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.51% [<b>41.2%</b>-49.8%]</td>
	<td>534</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.56% [<b>41.9%</b>-51.3%]</td>
	<td>451</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.58% [<b>42.8%</b>-50.4%]</td>
	<td>687</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>51.49% [<b>47.0%</b>-55.9%]</td>
	<td>503</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>50.10% [<b>47.5%</b>-52.7%]</td>
	<td>1,509</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.51% [41.2%-<b>49.8%</b>]</td>
	<td>534</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.58% [42.8%-<b>50.4%</b>]</td>
	<td>687</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.56% [41.9%-<b>51.3%</b>]</td>
	<td>451</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>51.26% [50.3%-<b>52.2%</b>]</td>
	<td>10,658</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>50.10% [47.5%-<b>52.7%</b>]</td>
	<td>1,509</td>
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
	<td>52.69% [52.5%-52.9%]</td>
	<td>250,414</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.88% [<b>40.3%</b>-45.5%]</td>
	<td>1,474</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.38% [<b>41.7%</b>-47.1%]</td>
	<td>1,334</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.49% [<b>42.6%</b>-48.4%]</td>
	<td>1,154</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.70% [<b>42.7%</b>-48.7%]</td>
	<td>1,094</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.09% [<b>43.3%</b>-48.9%]</td>
	<td>1,265</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.88% [40.3%-<b>45.5%</b>]</td>
	<td>1,474</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.38% [41.7%-<b>47.1%</b>]</td>
	<td>1,334</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.49% [42.6%-<b>48.4%</b>]</td>
	<td>1,154</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.70% [42.7%-<b>48.7%</b>]</td>
	<td>1,094</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.09% [43.3%-<b>48.9%</b>]</td>
	<td>1,265</td>
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
	<td>48.07% [47.9%-48.2%]</td>
	<td>493,994</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>42.61% [<b>40.3%</b>-44.9%]</td>
	<td>1,854</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.57% [<b>41.4%</b>-45.7%]</td>
	<td>2,185</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.45% [<b>41.5%</b>-45.4%]</td>
	<td>2,497</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.79% [<b>42.3%</b>-47.2%]</td>
	<td>1,652</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.25% [<b>43.3%</b>-47.2%]</td>
	<td>2,716</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>42.61% [40.3%-<b>44.9%</b>]</td>
	<td>1,854</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.45% [41.5%-<b>45.4%</b>]</td>
	<td>2,497</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.41% [43.4%-<b>45.5%</b>]</td>
	<td>8,969</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.57% [41.4%-<b>45.7%</b>]</td>
	<td>2,185</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>46.24% [45.9%-<b>46.6%</b>]</td>
	<td>66,772</td>
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
	<td>48.78% [48.6%-48.9%]</td>
	<td>470,993</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.16% [<b>40.2%</b>-44.2%]</td>
	<td>2,443</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.36% [<b>41.4%</b>-45.3%]</td>
	<td>2,636</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.19% [<b>42.4%</b>-46.0%]</td>
	<td>3,005</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.10% [<b>43.0%</b>-47.2%]</td>
	<td>2,346</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.48% [<b>43.5%</b>-45.5%]</td>
	<td>10,376</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.16% [40.2%-<b>44.2%</b>]</td>
	<td>2,443</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.36% [41.4%-<b>45.3%</b>]</td>
	<td>2,636</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.48% [43.5%-<b>45.5%</b>]</td>
	<td>10,376</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.19% [42.4%-<b>46.0%</b>]</td>
	<td>3,005</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.44% [44.2%-<b>46.7%</b>]</td>
	<td>6,406</td>
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
	<td>47.87% [47.7%-48.0%]</td>
	<td>446,272</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>40.63% [<b>38.2%</b>-43.1%]</td>
	<td>1,590</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.37% [<b>41.3%</b>-45.5%]</td>
	<td>2,232</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.81% [<b>41.4%</b>-46.2%]</td>
	<td>1,705</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.99% [<b>41.7%</b>-46.2%]</td>
	<td>1,962</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.31% [<b>42.9%</b>-45.8%]</td>
	<td>4,739</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>40.63% [38.2%-<b>43.1%</b>]</td>
	<td>1,590</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.37% [41.3%-<b>45.5%</b>]</td>
	<td>2,232</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.31% [42.9%-<b>45.8%</b>]</td>
	<td>4,739</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.69% [43.6%-<b>45.8%</b>]</td>
	<td>7,706</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.81% [41.4%-<b>46.2%</b>]</td>
	<td>1,705</td>
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
	<td>49.23% [49.1%-49.4%]</td>
	<td>321,372</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>41.91% [<b>39.3%</b>-44.5%]</td>
	<td>1,484</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.83% [<b>41.0%</b>-46.7%]</td>
	<td>1,200</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.83% [<b>42.4%</b>-47.2%]</td>
	<td>1,731</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.01% [<b>43.9%</b>-50.1%]</td>
	<td>1,055</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>46.07% [<b>44.7%</b>-47.5%]</td>
	<td>4,947</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>41.91% [39.3%-<b>44.5%</b>]</td>
	<td>1,484</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.83% [41.0%-<b>46.7%</b>]</td>
	<td>1,200</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.83% [42.4%-<b>47.2%</b>]</td>
	<td>1,731</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>46.07% [44.7%-<b>47.5%</b>]</td>
	<td>4,947</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.01% [46.0%-<b>48.0%</b>]</td>
	<td>9,260</td>
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
	<td>48.73% [48.6%-48.9%]</td>
	<td>435,791</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>42.25% [<b>39.6%</b>-44.9%]</td>
	<td>1,432</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.94% [<b>40.8%</b>-45.1%]</td>
	<td>2,061</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.65% [<b>41.2%</b>-46.1%]</td>
	<td>1,576</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.70% [<b>41.5%</b>-45.9%]</td>
	<td>2,087</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.25% [<b>42.0%</b>-46.5%]</td>
	<td>1,975</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>42.25% [39.6%-<b>44.9%</b>]</td>
	<td>1,432</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.94% [40.8%-<b>45.1%</b>]</td>
	<td>2,061</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.70% [41.5%-<b>45.9%</b>]</td>
	<td>2,087</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.65% [41.2%-<b>46.1%</b>]</td>
	<td>1,576</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.26% [44.1%-<b>46.5%</b>]</td>
	<td>6,843</td>
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
	<td>49.68% [49.5%-49.8%]</td>
	<td>553,382</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>41.36% [<b>39.5%</b>-43.2%]</td>
	<td>2,863</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.33% [<b>40.5%</b>-44.1%]</td>
	<td>3,005</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.08% [<b>43.1%</b>-45.1%]</td>
	<td>10,271</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.45% [<b>43.4%</b>-47.5%]</td>
	<td>2,310</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.52% [<b>44.3%</b>-48.8%]</td>
	<td>1,969</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>41.36% [39.5%-<b>43.2%</b>]</td>
	<td>2,863</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.33% [40.5%-<b>44.1%</b>]</td>
	<td>3,005</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.08% [43.1%-<b>45.1%</b>]</td>
	<td>10,271</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.44% [44.5%-<b>46.4%</b>]</td>
	<td>10,453</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.18% [45.1%-<b>47.3%</b>]</td>
	<td>8,267</td>
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
	<td>47.27% [47.1%-47.4%]</td>
	<td>309,056</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>40.51% [<b>37.7%</b>-43.4%]</td>
	<td>1,180</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>42.52% [<b>40.1%</b>-44.9%]</td>
	<td>1,698</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.83% [<b>41.3%</b>-46.4%]</td>
	<td>1,547</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.14% [<b>41.6%</b>-44.7%]</td>
	<td>4,057</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.19% [<b>41.7%</b>-46.7%]</td>
	<td>1,550</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>40.51% [37.7%-<b>43.4%</b>]</td>
	<td>1,180</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.14% [41.6%-<b>44.7%</b>]</td>
	<td>4,057</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>43.38% [42.0%-<b>44.7%</b>]</td>
	<td>5,535</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>42.52% [40.1%-<b>44.9%</b>]</td>
	<td>1,698</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>45.59% [45.0%-<b>46.2%</b>]</td>
	<td>28,122</td>
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
	<td>47.33% [47.1%-47.5%]</td>
	<td>282,487</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>41.41% [<b>38.6%</b>-44.2%]</td>
	<td>1,263</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.56% [<b>39.8%</b>-45.3%]</td>
	<td>1,304</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>42.44% [<b>39.9%</b>-45.0%]</td>
	<td>1,489</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>42.32% [<b>40.9%</b>-43.7%]</td>
	<td>4,965</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.32% [<b>41.2%</b>-47.5%]</td>
	<td>1,004</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>42.32% [40.9%-<b>43.7%</b>]</td>
	<td>4,965</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>41.41% [38.6%-<b>44.2%</b>]</td>
	<td>1,263</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>42.44% [39.9%-<b>45.0%</b>]</td>
	<td>1,489</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.56% [39.8%-<b>45.3%</b>]</td>
	<td>1,304</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.82% [42.1%-<b>45.6%</b>]</td>
	<td>3,188</td>
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
	<td>48.50% [48.4%-48.6%]</td>
	<td>481,931</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>41.18% [<b>38.9%</b>-43.5%]</td>
	<td>1,870</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>41.49% [<b>39.6%</b>-43.4%]</td>
	<td>2,767</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>41.95% [<b>40.0%</b>-43.9%]</td>
	<td>2,510</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>43.61% [<b>42.4%</b>-44.8%]</td>
	<td>7,228</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.89% [<b>42.7%</b>-47.1%]</td>
	<td>2,047</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>41.49% [39.6%-<b>43.4%</b>]</td>
	<td>2,767</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>41.18% [38.9%-<b>43.5%</b>]</td>
	<td>1,870</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>41.95% [40.0%-<b>43.9%</b>]</td>
	<td>2,510</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>43.61% [42.4%-<b>44.8%</b>]</td>
	<td>7,228</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.24% [42.9%-<b>45.5%</b>]</td>
	<td>5,911</td>
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
	<td>50.99% [50.7%-51.3%]</td>
	<td>131,123</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.59% [<b>38.9%</b>-46.2%]</td>
	<td>735</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.86% [<b>39.5%</b>-46.2%]</td>
	<td>882</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.70% [<b>41.3%</b>-46.1%]</td>
	<td>1,762</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.09% [<b>43.0%</b>-51.2%]</td>
	<td>601</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kalista"></span> Kalista</td>
	<td>48.43% [<b>45.8%</b>-51.0%]</td>
	<td>1,499</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.70% [41.3%-<b>46.1%</b>]</td>
	<td>1,762</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.86% [39.5%-<b>46.2%</b>]</td>
	<td>882</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.59% [38.9%-<b>46.2%</b>]</td>
	<td>735</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>48.72% [47.1%-<b>50.3%</b>]</td>
	<td>3,974</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-samira"></span> Samira</td>
	<td>48.86% [47.2%-<b>50.5%</b>]</td>
	<td>3,700</td>
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
	<td>51.68% [51.6%-51.8%]</td>
	<td>694,352</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.74% [<b>46.5%</b>-50.9%]</td>
	<td>2,068</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>50.75% [<b>48.9%</b>-52.6%]</td>
	<td>2,879</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.70% [<b>49.0%</b>-50.4%]</td>
	<td>18,581</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-bard"></span> Bard</td>
	<td>50.05% [<b>49.0%</b>-51.1%]</td>
	<td>9,680</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.92% [<b>49.1%</b>-50.7%]</td>
	<td>16,356</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.70% [49.0%-<b>50.4%</b>]</td>
	<td>18,581</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.91% [49.2%-<b>50.6%</b>]</td>
	<td>20,134</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>50.12% [49.6%-<b>50.6%</b>]</td>
	<td>37,453</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.92% [49.1%-<b>50.7%</b>]</td>
	<td>16,356</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>50.03% [49.4%-<b>50.7%</b>]</td>
	<td>21,789</td>
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
	<td>51.64% [51.5%-51.7%]</td>
	<td>877,333</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.63% [<b>48.0%</b>-49.3%]</td>
	<td>24,327</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.70% [<b>48.1%</b>-49.3%]</td>
	<td>24,682</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>50.38% [<b>48.6%</b>-52.2%]</td>
	<td>3,021</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>50.32% [<b>48.7%</b>-52.0%]</td>
	<td>3,633</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>50.56% [<b>48.7%</b>-52.4%]</td>
	<td>2,955</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.63% [48.0%-<b>49.3%</b>]</td>
	<td>24,327</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.70% [48.1%-<b>49.3%</b>]</td>
	<td>24,682</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>49.48% [49.1%-<b>49.9%</b>]</td>
	<td>70,966</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.87% [49.4%-<b>50.4%</b>]</td>
	<td>37,453</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.98% [49.4%-<b>50.6%</b>]</td>
	<td>25,624</td>
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
	<td>51.36% [51.2%-51.5%]</td>
	<td>402,559</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>49.32% [<b>46.6%</b>-52.1%]</td>
	<td>1,330</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.91% [<b>47.2%</b>-48.6%]</td>
	<td>20,944</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>50.44% [<b>47.6%</b>-53.3%]</td>
	<td>1,261</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>49.21% [<b>47.8%</b>-50.6%]</td>
	<td>4,822</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.29% [<b>48.0%</b>-50.6%]</td>
	<td>5,952</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.91% [47.2%-<b>48.6%</b>]</td>
	<td>20,944</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.10% [48.0%-<b>50.2%</b>]</td>
	<td>8,503</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-thresh"></span> Thresh</td>
	<td>49.94% [49.3%-<b>50.6%</b>]</td>
	<td>24,668</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.29% [48.0%-<b>50.6%</b>]</td>
	<td>5,952</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.96% [49.3%-<b>50.6%</b>]</td>
	<td>21,789</td>
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
	<td>52.66% [52.5%-52.8%]</td>
	<td>550,957</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>49.19% [<b>46.9%</b>-51.5%]</td>
	<td>1,921</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>49.96% [<b>47.2%</b>-52.7%]</td>
	<td>1,309</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.68% [<b>47.4%</b>-49.9%]</td>
	<td>6,226</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>50.79% [<b>48.0%</b>-53.6%]</td>
	<td>1,270</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>50.13% [<b>48.3%</b>-51.9%]</td>
	<td>3,140</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.68% [47.4%-<b>49.9%</b>]</td>
	<td>6,226</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.22% [48.4%-<b>50.0%</b>]</td>
	<td>16,507</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>49.35% [48.4%-<b>50.3%</b>]</td>
	<td>10,507</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.38% [48.4%-<b>50.4%</b>]</td>
	<td>9,459</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.82% [49.1%-<b>50.6%</b>]</td>
	<td>17,761</td>
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
	<td>50.80% [50.6%-51.0%]</td>
	<td>400,137</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.89% [<b>46.0%</b>-51.8%]</td>
	<td>1,170</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.87% [<b>46.9%</b>-52.8%]</td>
	<td>1,151</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.03% [<b>47.1%</b>-49.0%]</td>
	<td>11,394</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.30% [<b>47.6%</b>-49.0%]</td>
	<td>18,824</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>50.40% [<b>47.7%</b>-53.1%]</td>
	<td>1,389</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.03% [47.1%-<b>49.0%</b>]</td>
	<td>11,394</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.30% [47.6%-<b>49.0%</b>]</td>
	<td>18,824</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.60% [47.9%-<b>49.3%</b>]</td>
	<td>20,805</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.94% [48.0%-<b>49.8%</b>]</td>
	<td>12,081</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>49.81% [49.2%-<b>50.5%</b>]</td>
	<td>23,111</td>
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
	<td>51.14% [51.0%-51.3%]</td>
	<td>811,061</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.11% [<b>45.2%</b>-49.0%]</td>
	<td>2,770</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.64% [<b>46.9%</b>-48.4%]</td>
	<td>16,123</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.57% [<b>46.9%</b>-48.2%]</td>
	<td>23,727</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.19% [<b>47.0%</b>-49.4%]</td>
	<td>6,862</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.66% [<b>47.0%</b>-48.3%]</td>
	<td>25,378</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.57% [46.9%-<b>48.2%</b>]</td>
	<td>23,727</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.66% [47.0%-<b>48.3%</b>]</td>
	<td>25,378</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.64% [46.9%-<b>48.4%</b>]</td>
	<td>16,123</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.06% [47.5%-<b>48.7%</b>]</td>
	<td>27,974</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.11% [45.2%-<b>49.0%</b>]</td>
	<td>2,770</td>
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
	<td>50.62% [50.5%-50.7%]</td>
	<td>921,075</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.33% [<b>46.6%</b>-50.1%]</td>
	<td>3,333</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.58% [<b>46.7%</b>-50.4%]</td>
	<td>2,913</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.34% [<b>47.5%</b>-49.2%]</td>
	<td>13,745</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.11% [<b>47.7%</b>-48.6%]</td>
	<td>48,918</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.34% [<b>47.7%</b>-49.0%]</td>
	<td>22,105</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.11% [47.7%-<b>48.6%</b>]</td>
	<td>48,918</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.34% [47.7%-<b>49.0%</b>]</td>
	<td>22,105</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.34% [47.5%-<b>49.2%</b>]</td>
	<td>13,745</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.09% [48.6%-<b>49.6%</b>]</td>
	<td>46,834</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.00% [48.3%-<b>49.7%</b>]</td>
	<td>22,904</td>
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
	<td>50.78% [50.7%-50.9%]</td>
	<td>1,465,220</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.90% [<b>46.7%</b>-49.1%]</td>
	<td>6,426</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.83% [<b>46.7%</b>-48.9%]</td>
	<td>8,016</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>48.48% [<b>47.0%</b>-49.9%]</td>
	<td>4,746</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.58% [<b>47.2%</b>-48.0%]</td>
	<td>59,790</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.93% [<b>47.3%</b>-50.6%]</td>
	<td>3,779</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.58% [47.2%-<b>48.0%</b>]</td>
	<td>59,790</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.20% [47.7%-<b>48.7%</b>]</td>
	<td>45,980</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.24% [47.6%-<b>48.8%</b>]</td>
	<td>27,678</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.46% [48.0%-<b>48.9%</b>]</td>
	<td>52,630</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.83% [46.7%-<b>48.9%</b>]</td>
	<td>8,016</td>
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
	<td>51.59% [51.4%-51.8%]</td>
	<td>266,872</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.68% [<b>46.4%</b>-53.0%]</td>
	<td>934</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.00% [<b>46.7%</b>-49.3%]</td>
	<td>5,771</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.17% [<b>47.9%</b>-50.5%]</td>
	<td>6,067</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.79% [<b>47.9%</b>-49.7%]</td>
	<td>13,086</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>51.49% [<b>48.0%</b>-55.0%]</td>
	<td>804</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.00% [46.7%-<b>49.3%</b>]</td>
	<td>5,771</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.79% [47.9%-<b>49.7%</b>]</td>
	<td>13,086</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.33% [48.5%-<b>50.2%</b>]</td>
	<td>13,684</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.17% [47.9%-<b>50.5%</b>]</td>
	<td>6,067</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>50.42% [49.6%-<b>51.2%</b>]</td>
	<td>15,394</td>
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
	<td>51.43% [51.3%-51.6%]</td>
	<td>350,749</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.02% [<b>44.0%</b>-50.1%]</td>
	<td>1,074</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.49% [<b>46.2%</b>-50.8%]</td>
	<td>1,924</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>49.61% [<b>47.1%</b>-52.2%]</td>
	<td>1,528</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>51.05% [<b>47.3%</b>-54.8%]</td>
	<td>715</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>49.03% [<b>47.6%</b>-50.5%]</td>
	<td>4,777</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>49.15% [48.4%-<b>49.9%</b>]</td>
	<td>18,132</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.02% [44.0%-<b>50.1%</b>]</td>
	<td>1,074</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>49.03% [47.6%-<b>50.5%</b>]</td>
	<td>4,777</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.74% [48.8%-<b>50.7%</b>]</td>
	<td>10,411</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>49.49% [48.2%-<b>50.8%</b>]</td>
	<td>6,298</td>
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
	<td>51.08% [50.9%-51.2%]</td>
	<td>378,214</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.31% [<b>44.6%</b>-48.0%]</td>
	<td>3,345</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.03% [<b>46.1%</b>-50.0%]</td>
	<td>2,586</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.43% [<b>46.6%</b>-48.2%]</td>
	<td>15,534</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.62% [<b>46.7%</b>-52.5%]</td>
	<td>1,173</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.84% [<b>46.8%</b>-48.9%]</td>
	<td>8,856</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.31% [44.6%-<b>48.0%</b>]</td>
	<td>3,345</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.43% [46.6%-<b>48.2%</b>]</td>
	<td>15,534</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.84% [46.8%-<b>48.9%</b>]</td>
	<td>8,856</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.04% [47.1%-<b>49.0%</b>]</td>
	<td>10,955</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.30% [47.1%-<b>49.5%</b>]</td>
	<td>7,156</td>
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
	<td>53.05% [52.8%-53.3%]</td>
	<td>168,774</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.75% [<b>44.4%</b>-51.1%]</td>
	<td>890</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.58% [<b>46.1%</b>-49.1%]</td>
	<td>4,269</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.66% [<b>46.7%</b>-50.6%]</td>
	<td>2,571</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>52.13% [<b>47.0%</b>-57.3%]</td>
	<td>376</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>52.03% [<b>47.1%</b>-56.9%]</td>
	<td>419</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.58% [46.1%-<b>49.1%</b>]</td>
	<td>4,269</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.15% [47.9%-<b>50.4%</b>]</td>
	<td>6,328</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.66% [46.7%-<b>50.6%</b>]</td>
	<td>2,571</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>49.87% [48.9%-<b>50.9%</b>]</td>
	<td>9,998</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>49.34% [47.6%-<b>51.1%</b>]</td>
	<td>3,397</td>
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
	<td>52.02% [51.9%-52.2%]</td>
	<td>499,904</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.13% [<b>45.7%</b>-50.5%]</td>
	<td>1,712</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.97% [<b>46.0%</b>-51.9%]</td>
	<td>1,166</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.22% [<b>46.3%</b>-50.1%]</td>
	<td>2,731</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>48.45% [<b>46.8%</b>-50.1%]</td>
	<td>3,843</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.53% [<b>46.9%</b>-50.2%]</td>
	<td>3,806</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.33% [47.4%-<b>49.3%</b>]</td>
	<td>11,107</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>48.45% [46.8%-<b>50.1%</b>]</td>
	<td>3,843</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.22% [46.3%-<b>50.1%</b>]</td>
	<td>2,731</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.53% [46.9%-<b>50.2%</b>]</td>
	<td>3,806</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.41% [48.6%-<b>50.2%</b>]</td>
	<td>15,098</td>
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
	<td>49.78% [49.7%-49.9%]</td>
	<td>601,613</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.30% [<b>44.9%</b>-49.7%]</td>
	<td>1,723</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.95% [<b>45.7%</b>-50.2%]</td>
	<td>2,046</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.30% [<b>45.8%</b>-48.8%]</td>
	<td>4,505</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.67% [<b>46.0%</b>-47.4%]</td>
	<td>19,398</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.71% [<b>46.0%</b>-51.4%]</td>
	<td>1,400</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.67% [46.0%-<b>47.4%</b>]</td>
	<td>19,398</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.98% [46.2%-<b>47.7%</b>]</td>
	<td>17,189</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.26% [46.5%-<b>48.0%</b>]</td>
	<td>19,388</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.62% [47.0%-<b>48.3%</b>]</td>
	<td>22,818</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.56% [46.7%-<b>48.5%</b>]</td>
	<td>12,461</td>
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
	<td>49.88% [49.8%-50.0%]</td>
	<td>1,205,128</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.37% [<b>44.8%</b>-45.9%]</td>
	<td>34,632</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.55% [<b>45.6%</b>-47.5%]</td>
	<td>11,824</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.70% [<b>46.1%</b>-47.3%]</td>
	<td>28,787</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.84% [<b>46.2%</b>-47.5%]</td>
	<td>21,770</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.87% [<b>46.3%</b>-49.5%]</td>
	<td>3,869</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.37% [44.8%-<b>45.9%</b>]</td>
	<td>34,632</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.70% [46.1%-<b>47.3%</b>]</td>
	<td>28,787</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.55% [45.6%-<b>47.5%</b>]</td>
	<td>11,824</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.84% [46.2%-<b>47.5%</b>]</td>
	<td>21,770</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.17% [46.7%-<b>47.6%</b>]</td>
	<td>51,227</td>
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
	<td>51.70% [51.5%-51.9%]</td>
	<td>248,255</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.76% [<b>45.3%</b>-48.2%]</td>
	<td>4,998</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.42% [<b>45.4%</b>-49.4%]</td>
	<td>2,478</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.34% [<b>46.2%</b>-48.5%]</td>
	<td>8,031</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>50.78% [<b>46.8%</b>-54.7%]</td>
	<td>644</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.58% [<b>46.9%</b>-50.2%]</td>
	<td>3,736</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.76% [45.3%-<b>48.2%</b>]</td>
	<td>4,998</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.34% [46.2%-<b>48.5%</b>]</td>
	<td>8,031</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.42% [45.4%-<b>49.4%</b>]</td>
	<td>2,478</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.58% [46.9%-<b>50.2%</b>]</td>
	<td>3,736</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>49.32% [48.4%-<b>50.2%</b>]</td>
	<td>11,588</td>
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
	<td>51.21% [51.1%-51.3%]</td>
	<td>549,624</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.74% [<b>45.0%</b>-48.5%]</td>
	<td>3,220</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.15% [<b>45.3%</b>-49.0%]</td>
	<td>2,948</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.30% [<b>46.0%</b>-48.6%]</td>
	<td>6,201</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>48.39% [<b>46.2%</b>-50.5%]</td>
	<td>2,145</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.98% [<b>46.8%</b>-51.2%]</td>
	<td>2,058</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.74% [45.0%-<b>48.5%</b>]</td>
	<td>3,220</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.30% [46.0%-<b>48.6%</b>]</td>
	<td>6,201</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.19% [47.4%-<b>49.0%</b>]</td>
	<td>16,073</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.15% [45.3%-<b>49.0%</b>]</td>
	<td>2,948</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.29% [47.2%-<b>49.4%</b>]</td>
	<td>8,466</td>
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
	<td>49.89% [49.8%-50.0%]</td>
	<td>583,660</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.29% [<b>43.3%</b>-45.3%]</td>
	<td>9,997</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.91% [<b>45.1%</b>-46.8%]</td>
	<td>13,815</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.07% [<b>45.2%</b>-47.0%]</td>
	<td>11,746</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.67% [<b>45.3%</b>-50.0%]</td>
	<td>1,783</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.48% [<b>45.9%</b>-49.1%]</td>
	<td>3,793</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.29% [43.3%-<b>45.3%</b>]</td>
	<td>9,997</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.91% [45.1%-<b>46.8%</b>]</td>
	<td>13,815</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.07% [45.2%-<b>47.0%</b>]</td>
	<td>11,746</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.97% [46.3%-<b>47.7%</b>]</td>
	<td>19,589</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.11% [46.5%-<b>47.7%</b>]</td>
	<td>25,408</td>
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
	<td>50.83% [50.7%-51.0%]</td>
	<td>458,179</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.91% [<b>45.0%</b>-50.9%]</td>
	<td>1,148</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.29% [<b>45.0%</b>-47.6%]</td>
	<td>5,755</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.55% [<b>45.1%</b>-48.0%]</td>
	<td>4,436</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>46.61% [<b>45.1%</b>-48.2%]</td>
	<td>4,147</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.04% [<b>46.1%</b>-48.0%]</td>
	<td>11,283</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.29% [45.0%-<b>47.6%</b>]</td>
	<td>5,755</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>46.93% [46.2%-<b>47.6%</b>]</td>
	<td>19,519</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.04% [46.1%-<b>48.0%</b>]</td>
	<td>11,283</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.55% [45.1%-<b>48.0%</b>]</td>
	<td>4,436</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>46.61% [45.1%-<b>48.2%</b>]</td>
	<td>4,147</td>
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
	<td>49.67% [49.5%-49.8%]</td>
	<td>547,699</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.47% [<b>44.1%</b>-48.8%]</td>
	<td>1,771</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.43% [<b>44.8%</b>-50.0%]</td>
	<td>1,480</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.56% [<b>45.1%</b>-50.1%]</td>
	<td>1,600</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>47.56% [<b>45.2%</b>-50.0%]</td>
	<td>1,724</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.60% [<b>45.3%</b>-47.9%]</td>
	<td>6,198</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.60% [45.3%-<b>47.9%</b>]</td>
	<td>6,198</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.04% [46.2%-<b>47.9%</b>]</td>
	<td>14,556</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.96% [47.3%-<b>48.6%</b>]</td>
	<td>23,393</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.10% [47.5%-<b>48.7%</b>]</td>
	<td>27,359</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.24% [45.8%-<b>48.7%</b>]</td>
	<td>4,519</td>
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
	<td>51.21% [51.0%-51.5%]</td>
	<td>155,303</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.87% [<b>44.6%</b>-49.1%]</td>
	<td>1,918</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.59% [<b>44.6%</b>-50.5%]</td>
	<td>1,141</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.83% [<b>44.7%</b>-52.9%]</td>
	<td>596</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>49.59% [<b>45.1%</b>-54.1%]</td>
	<td>488</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>46.35% [<b>45.1%</b>-47.6%]</td>
	<td>6,880</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>46.35% [45.1%-<b>47.6%</b>]</td>
	<td>6,880</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.18% [45.8%-<b>48.6%</b>]</td>
	<td>4,877</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>47.69% [46.6%-<b>48.8%</b>]</td>
	<td>7,955</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.87% [44.6%-<b>49.1%</b>]</td>
	<td>1,918</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.29% [45.3%-<b>49.3%</b>]</td>
	<td>2,542</td>
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
	<td>49.24% [49.1%-49.4%]</td>
	<td>364,322</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.69% [<b>43.9%</b>-47.5%]</td>
	<td>3,182</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.45% [<b>44.5%</b>-46.4%]</td>
	<td>10,674</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>45.92% [<b>44.7%</b>-47.1%]</td>
	<td>6,749</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.26% [<b>44.8%</b>-49.7%]</td>
	<td>1,640</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.75% [<b>44.8%</b>-50.7%]</td>
	<td>1,177</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.45% [44.5%-<b>46.4%</b>]</td>
	<td>10,674</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>45.92% [44.7%-<b>47.1%</b>]</td>
	<td>6,749</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.38% [45.4%-<b>47.4%</b>]</td>
	<td>10,121</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.69% [43.9%-<b>47.5%</b>]</td>
	<td>3,182</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>46.98% [46.1%-<b>47.9%</b>]</td>
	<td>11,713</td>
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
	<td>50.95% [50.7%-51.2%]</td>
	<td>199,701</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.58% [<b>43.5%</b>-49.7%]</td>
	<td>1,024</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.66% [<b>44.4%</b>-52.9%]</td>
	<td>559</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.93% [<b>44.5%</b>-49.4%]</td>
	<td>1,694</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>50.17% [<b>46.1%</b>-54.3%]</td>
	<td>596</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.45% [<b>46.1%</b>-48.8%]</td>
	<td>5,486</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.45% [46.1%-<b>48.8%</b>]</td>
	<td>5,486</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.93% [44.5%-<b>49.4%</b>]</td>
	<td>1,694</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.58% [43.5%-<b>49.7%</b>]</td>
	<td>1,024</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.69% [47.7%-<b>49.7%</b>]</td>
	<td>9,725</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.00% [47.9%-<b>50.1%</b>]</td>
	<td>8,276</td>
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
	<td>50.13% [49.9%-50.3%]</td>
	<td>229,484</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.83% [<b>44.3%</b>-51.4%]</td>
	<td>805</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.17% [<b>44.3%</b>-48.0%]</td>
	<td>2,883</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.93% [<b>44.4%</b>-49.5%]</td>
	<td>1,498</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.82% [<b>45.5%</b>-48.2%]</td>
	<td>5,487</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.04% [<b>45.8%</b>-50.2%]</td>
	<td>2,065</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.17% [44.3%-<b>48.0%</b>]</td>
	<td>2,883</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.82% [45.5%-<b>48.2%</b>]</td>
	<td>5,487</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.50% [46.6%-<b>48.4%</b>]</td>
	<td>12,500</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.93% [44.4%-<b>49.5%</b>]</td>
	<td>1,498</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>48.43% [47.0%-<b>49.9%</b>]</td>
	<td>4,671</td>
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
	<td>49.16% [49.0%-49.3%]</td>
	<td>395,074</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.78% [<b>44.1%</b>-47.5%]</td>
	<td>3,558</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.06% [<b>44.3%</b>-49.8%]</td>
	<td>1,292</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>45.10% [<b>44.4%</b>-45.8%]</td>
	<td>18,178</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.47% [<b>44.5%</b>-46.5%]</td>
	<td>9,604</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.76% [<b>44.5%</b>-47.0%]</td>
	<td>6,469</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>45.10% [44.4%-<b>45.8%</b>]</td>
	<td>18,178</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.47% [44.5%-<b>46.5%</b>]</td>
	<td>9,604</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.76% [44.5%-<b>47.0%</b>]</td>
	<td>6,469</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.56% [45.9%-<b>47.2%</b>]</td>
	<td>26,414</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.78% [44.1%-<b>47.5%</b>]</td>
	<td>3,558</td>
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
	<td>48.65% [48.5%-48.8%]</td>
	<td>711,726</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>44.34% [<b>42.6%</b>-46.1%]</td>
	<td>3,241</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.47% [<b>44.2%</b>-46.7%]</td>
	<td>6,484</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.63% [<b>44.3%</b>-46.9%]</td>
	<td>5,819</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.86% [<b>45.1%</b>-48.6%]</td>
	<td>3,291</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.45% [<b>45.1%</b>-49.8%]</td>
	<td>1,840</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>44.34% [42.6%-<b>46.1%</b>]</td>
	<td>3,241</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.47% [44.2%-<b>46.7%</b>]</td>
	<td>6,484</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.01% [45.3%-<b>46.7%</b>]</td>
	<td>18,542</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.63% [44.3%-<b>46.9%</b>]</td>
	<td>5,819</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.24% [45.5%-<b>47.0%</b>]</td>
	<td>16,173</td>
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
	<td>51.25% [51.1%-51.4%]</td>
	<td>294,075</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>45.20% [<b>42.1%</b>-48.3%]</td>
	<td>1,042</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>47.45% [<b>44.1%</b>-50.8%]</td>
	<td>883</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.41% [<b>44.3%</b>-48.5%]</td>
	<td>2,185</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.00% [<b>44.6%</b>-51.4%]</td>
	<td>873</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>49.93% [<b>46.2%</b>-53.6%]</td>
	<td>729</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>45.20% [42.1%-<b>48.3%</b>]</td>
	<td>1,042</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.41% [44.3%-<b>48.5%</b>]</td>
	<td>2,185</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.96% [47.0%-<b>49.0%</b>]</td>
	<td>9,809</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.31% [47.0%-<b>49.6%</b>]</td>
	<td>5,591</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.89% [47.8%-<b>50.0%</b>]</td>
	<td>8,648</td>
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
	<td>50.08% [50.0%-50.2%]</td>
	<td>890,721</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.85% [<b>43.9%</b>-45.8%]</td>
	<td>9,899</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.18% [<b>43.9%</b>-46.5%]</td>
	<td>5,960</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.09% [<b>45.3%</b>-46.8%]</td>
	<td>17,563</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.73% [<b>45.5%</b>-47.9%]</td>
	<td>6,989</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.95% [<b>45.8%</b>-48.1%]</td>
	<td>7,152</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.85% [43.9%-<b>45.8%</b>]</td>
	<td>9,899</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.18% [43.9%-<b>46.5%</b>]</td>
	<td>5,960</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.09% [45.3%-<b>46.8%</b>]</td>
	<td>17,563</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.43% [45.8%-<b>47.1%</b>]</td>
	<td>25,219</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.69% [46.2%-<b>47.2%</b>]</td>
	<td>43,940</td>
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
	<td>51.77% [51.5%-52.1%]</td>
	<td>105,593</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.27% [<b>42.2%</b>-50.4%]</td>
	<td>590</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.16% [<b>43.8%</b>-50.5%]</td>
	<td>899</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.48% [<b>44.1%</b>-50.9%]</td>
	<td>872</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.98% [<b>44.4%</b>-49.6%]</td>
	<td>1,473</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>47.65% [<b>44.8%</b>-50.5%]</td>
	<td>1,236</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.14% [45.0%-<b>49.3%</b>]</td>
	<td>2,166</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.98% [44.4%-<b>49.6%</b>]</td>
	<td>1,473</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.08% [46.4%-<b>49.8%</b>]</td>
	<td>3,459</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.39% [46.9%-<b>49.9%</b>]</td>
	<td>4,499</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>48.51% [47.0%-<b>50.0%</b>]</td>
	<td>4,529</td>
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
	<td>50.97% [50.6%-51.3%]</td>
	<td>91,391</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.18% [<b>42.9%</b>-53.5%]</td>
	<td>357</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.55% [<b>43.5%</b>-49.6%]</td>
	<td>1,059</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>50.19% [<b>44.0%</b>-56.4%]</td>
	<td>263</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.00% [<b>44.4%</b>-51.6%]</td>
	<td>750</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.76% [<b>44.7%</b>-52.8%]</td>
	<td>607</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.03% [45.4%-<b>48.7%</b>]</td>
	<td>3,681</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.55% [43.5%-<b>49.6%</b>]</td>
	<td>1,059</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.63% [45.3%-<b>50.0%</b>]</td>
	<td>1,812</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>47.89% [45.6%-<b>50.2%</b>]</td>
	<td>1,825</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.93% [45.3%-<b>50.6%</b>]</td>
	<td>1,402</td>
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
	<td>49.01% [48.9%-49.2%]</td>
	<td>395,450</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.69% [<b>42.5%</b>-44.9%]</td>
	<td>6,890</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>44.79% [<b>43.5%</b>-46.1%]</td>
	<td>5,666</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.05% [<b>43.5%</b>-46.6%]</td>
	<td>4,195</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>45.07% [<b>44.3%</b>-45.9%]</td>
	<td>15,107</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.37% [<b>44.3%</b>-46.4%]</td>
	<td>8,865</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.69% [42.5%-<b>44.9%</b>]</td>
	<td>6,890</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>45.07% [44.3%-<b>45.9%</b>]</td>
	<td>15,107</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>44.79% [43.5%-<b>46.1%</b>]</td>
	<td>5,666</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.37% [44.3%-<b>46.4%</b>]</td>
	<td>8,865</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.05% [43.5%-<b>46.6%</b>]</td>
	<td>4,195</td>
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
	<td>50.52% [50.4%-50.7%]</td>
	<td>349,341</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.75% [<b>42.9%</b>-44.6%]</td>
	<td>12,369</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.21% [<b>43.4%</b>-49.0%]</td>
	<td>1,266</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>45.40% [<b>44.5%</b>-46.3%]</td>
	<td>11,787</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>48.36% [<b>45.1%</b>-51.7%]</td>
	<td>912</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>46.35% [<b>45.1%</b>-47.6%]</td>
	<td>6,578</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.75% [42.9%-<b>44.6%</b>]</td>
	<td>12,369</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>45.40% [44.5%-<b>46.3%</b>]</td>
	<td>11,787</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.24% [45.2%-<b>47.3%</b>]</td>
	<td>9,138</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.36% [45.4%-<b>47.4%</b>]</td>
	<td>10,051</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-karma"></span> Karma</td>
	<td>46.42% [45.4%-<b>47.5%</b>]</td>
	<td>8,916</td>
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
	<td>48.63% [48.5%-48.7%]</td>
	<td>956,904</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>40.88% [<b>40.0%</b>-41.8%]</td>
	<td>11,509</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.12% [<b>43.4%</b>-44.8%]</td>
	<td>18,985</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.30% [<b>44.3%</b>-48.3%]</td>
	<td>2,555</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.01% [<b>44.4%</b>-45.6%]</td>
	<td>26,488</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.76% [<b>44.4%</b>-47.1%]</td>
	<td>5,654</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>40.88% [40.0%-<b>41.8%</b>]</td>
	<td>11,509</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.12% [43.4%-<b>44.8%</b>]</td>
	<td>18,985</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.01% [44.4%-<b>45.6%</b>]</td>
	<td>26,488</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>45.69% [45.2%-<b>46.2%</b>]</td>
	<td>34,451</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.16% [45.7%-<b>46.6%</b>]</td>
	<td>42,510</td>
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
	<td>50.90% [50.6%-51.2%]</td>
	<td>150,679</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.09% [<b>43.2%</b>-49.0%]</td>
	<td>1,189</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.64% [<b>43.4%</b>-51.9%]</td>
	<td>550</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.39% [<b>43.6%</b>-47.2%]</td>
	<td>3,007</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.05% [<b>44.3%</b>-51.8%]</td>
	<td>693</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.55% [<b>45.3%</b>-51.8%]</td>
	<td>931</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.39% [43.6%-<b>47.2%</b>]</td>
	<td>3,007</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.09% [43.2%-<b>49.0%</b>]</td>
	<td>1,189</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.00% [46.6%-<b>49.4%</b>]</td>
	<td>4,765</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.28% [47.0%-<b>49.5%</b>]</td>
	<td>6,574</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>48.37% [47.1%-<b>49.7%</b>]</td>
	<td>6,062</td>
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
	<td>49.51% [49.3%-49.7%]</td>
	<td>280,160</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>42.83% [<b>40.9%</b>-44.8%]</td>
	<td>2,531</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.57% [<b>43.1%</b>-48.0%]</td>
	<td>1,683</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.34% [<b>45.2%</b>-47.4%]</td>
	<td>8,344</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.02% [<b>45.3%</b>-50.8%]</td>
	<td>1,314</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>46.73% [<b>45.5%</b>-48.0%]</td>
	<td>6,274</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>42.83% [40.9%-<b>44.8%</b>]</td>
	<td>2,531</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.34% [45.2%-<b>47.4%</b>]</td>
	<td>8,344</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>46.73% [45.5%-<b>48.0%</b>]</td>
	<td>6,274</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.57% [43.1%-<b>48.0%</b>]</td>
	<td>1,683</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>46.96% [45.9%-<b>48.0%</b>]</td>
	<td>9,024</td>
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
	<td>51.68% [51.3%-52.0%]</td>
	<td>81,090</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.89% [<b>41.0%</b>-50.8%]</td>
	<td>414</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.97% [<b>43.1%</b>-52.9%]</td>
	<td>419</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.67% [<b>43.2%</b>-50.1%]</td>
	<td>840</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.89% [<b>43.3%</b>-54.5%]</td>
	<td>315</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>47.26% [<b>43.9%</b>-50.6%]</td>
	<td>895</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.26% [44.5%-<b>50.0%</b>]</td>
	<td>1,297</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.67% [43.2%-<b>50.1%</b>]</td>
	<td>840</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>47.26% [43.9%-<b>50.6%</b>]</td>
	<td>895</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>48.40% [46.1%-<b>50.7%</b>]</td>
	<td>1,903</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.63% [46.5%-<b>50.8%</b>]</td>
	<td>2,186</td>
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
	<td>48.70% [48.6%-48.8%]</td>
	<td>621,087</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.59% [<b>40.3%</b>-42.9%]</td>
	<td>5,669</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>43.98% [<b>42.3%</b>-45.6%]</td>
	<td>3,577</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.41% [<b>43.0%</b>-47.8%]</td>
	<td>1,711</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.69% [<b>43.7%</b>-45.7%]</td>
	<td>10,658</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.44% [<b>44.6%</b>-48.3%]</td>
	<td>2,995</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.59% [40.3%-<b>42.9%</b>]</td>
	<td>5,669</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>43.98% [42.3%-<b>45.6%</b>]</td>
	<td>3,577</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.69% [43.7%-<b>45.7%</b>]</td>
	<td>10,658</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leona"></span> Leona</td>
	<td>45.88% [45.3%-<b>46.4%</b>]</td>
	<td>32,228</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.80% [45.0%-<b>46.6%</b>]</td>
	<td>16,390</td>
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
	<td>49.18% [48.9%-49.4%]</td>
	<td>171,998</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>45.04% [<b>41.5%</b>-48.5%]</td>
	<td>806</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.38% [<b>42.3%</b>-48.5%]</td>
	<td>1,038</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.51% [<b>42.4%</b>-50.6%]</td>
	<td>587</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.13% [<b>42.5%</b>-47.8%]</td>
	<td>1,407</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>48.08% [<b>43.6%</b>-52.6%]</td>
	<td>495</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>45.39% [44.2%-<b>46.6%</b>]</td>
	<td>7,122</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>45.93% [44.4%-<b>47.5%</b>]</td>
	<td>3,980</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.81% [44.0%-<b>47.6%</b>]</td>
	<td>3,159</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.13% [42.5%-<b>47.8%</b>]</td>
	<td>1,407</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>46.39% [44.5%-<b>48.3%</b>]</td>
	<td>2,740</td>
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
	<td>48.61% [48.3%-48.9%]</td>
	<td>132,056</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>44.88% [<b>39.6%</b>-50.1%]</td>
	<td>361</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>44.18% [<b>42.2%</b>-46.1%]</td>
	<td>2,637</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>44.30% [<b>42.6%</b>-46.0%]</td>
	<td>3,244</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.44% [<b>43.0%</b>-47.9%]</td>
	<td>1,635</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.15% [<b>43.1%</b>-47.2%]</td>
	<td>2,379</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>44.30% [42.6%-<b>46.0%</b>]</td>
	<td>3,244</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>44.18% [42.2%-<b>46.1%</b>]</td>
	<td>2,637</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>45.03% [43.3%-<b>46.8%</b>]</td>
	<td>3,282</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>45.86% [44.8%-<b>47.0%</b>]</td>
	<td>8,325</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.15% [43.1%-<b>47.2%</b>]</td>
	<td>2,379</td>
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
	<td>47.33% [47.2%-47.5%]</td>
	<td>449,410</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.72% [<b>40.0%</b>-43.4%]</td>
	<td>3,253</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.94% [<b>41.5%</b>-46.4%]</td>
	<td>1,675</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.62% [<b>41.9%</b>-47.3%]</td>
	<td>1,358</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>43.34% [<b>42.3%</b>-44.4%]</td>
	<td>8,498</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.04% [<b>42.7%</b>-45.4%]</td>
	<td>5,400</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.72% [40.0%-<b>43.4%</b>]</td>
	<td>3,253</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leona"></span> Leona</td>
	<td>43.42% [42.7%-<b>44.1%</b>]</td>
	<td>21,419</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>43.34% [42.3%-<b>44.4%</b>]</td>
	<td>8,498</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.04% [42.7%-<b>45.4%</b>]</td>
	<td>5,400</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>44.89% [44.0%-<b>45.8%</b>]</td>
	<td>13,185</td>
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
	<td>51.00% [50.6%-51.4%]</td>
	<td>53,084</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>45.67% [<b>38.8%</b>-52.6%]</td>
	<td>208</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.38% [<b>41.4%</b>-51.4%]</td>
	<td>401</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.93% [<b>42.1%</b>-53.8%]</td>
	<td>290</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-renata-glasc"></span> Renata Glasc</td>
	<td>47.12% [<b>42.1%</b>-52.1%]</td>
	<td>399</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.87% [<b>42.7%</b>-53.0%]</td>
	<td>376</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>46.33% [43.8%-<b>48.8%</b>]</td>
	<td>1,582</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.39% [43.9%-<b>48.9%</b>]</td>
	<td>1,593</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.44% [44.9%-<b>49.9%</b>]</td>
	<td>1,585</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.32% [46.3%-<b>50.4%</b>]</td>
	<td>2,382</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>47.89% [44.5%-<b>51.3%</b>]</td>
	<td>877</td>
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
	<td>49.72% [49.4%-50.0%]</td>
	<td>124,835</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.98% [<b>41.0%</b>-49.0%]</td>
	<td>618</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.69% [<b>41.3%</b>-52.0%]</td>
	<td>347</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>46.34% [<b>43.5%</b>-49.2%]</td>
	<td>1,256</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>48.73% [<b>43.7%</b>-53.8%]</td>
	<td>394</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.14% [<b>43.9%</b>-50.4%]</td>
	<td>944</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>46.26% [44.2%-<b>48.3%</b>]</td>
	<td>2,406</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>46.35% [44.3%-<b>48.4%</b>]</td>
	<td>2,408</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.06% [45.5%-<b>48.6%</b>]</td>
	<td>4,303</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.99% [45.3%-<b>48.7%</b>]</td>
	<td>3,441</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.98% [41.0%-<b>49.0%</b>]</td>
	<td>618</td>
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
	<td>49.94% [49.5%-50.3%]</td>
	<td>65,322</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.06% [<b>37.1%</b>-51.0%]</td>
	<td>202</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.60% [<b>39.4%</b>-47.8%]</td>
	<td>555</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.95% [<b>40.3%</b>-47.6%]</td>
	<td>760</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.55% [<b>40.5%</b>-50.6%]</td>
	<td>382</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-bard"></span> Bard</td>
	<td>44.37% [<b>40.6%</b>-48.1%]</td>
	<td>710</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.62% [42.2%-<b>47.1%</b>]</td>
	<td>1,645</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.95% [40.3%-<b>47.6%</b>]</td>
	<td>760</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.60% [39.4%-<b>47.8%</b>]</td>
	<td>555</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-bard"></span> Bard</td>
	<td>44.37% [40.6%-<b>48.1%</b>]</td>
	<td>710</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.77% [44.8%-<b>48.8%</b>]</td>
	<td>2,489</td>
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
	<td>51.22% [50.8%-51.6%]</td>
	<td>61,529</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.20% [<b>34.7%</b>-49.7%]</td>
	<td>173</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>44.95% [<b>39.3%</b>-50.6%]</td>
	<td>307</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.18% [<b>42.6%</b>-51.7%]</td>
	<td>479</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.95% [<b>43.2%</b>-50.7%]</td>
	<td>722</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>50.86% [<b>43.3%</b>-58.4%]</td>
	<td>175</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.20% [34.7%-<b>49.7%</b>]</td>
	<td>173</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.54% [45.0%-<b>50.1%</b>]</td>
	<td>1,546</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>44.95% [39.3%-<b>50.6%</b>]</td>
	<td>307</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.95% [43.2%-<b>50.7%</b>]</td>
	<td>722</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.58% [44.2%-<b>51.0%</b>]</td>
	<td>866</td>
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
	<td>47.41% [47.1%-47.7%]</td>
	<td>102,258</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>38.33% [<b>33.8%</b>-42.9%]</td>
	<td>454</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>43.20% [<b>37.4%</b>-49.0%]</td>
	<td>294</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.02% [<b>37.9%</b>-46.2%]</td>
	<td>564</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>43.95% [<b>38.3%</b>-49.6%]</td>
	<td>314</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.18% [<b>40.0%</b>-52.3%]</td>
	<td>262</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>38.33% [33.8%-<b>42.9%</b>]</td>
	<td>454</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>43.61% [41.8%-<b>45.5%</b>]</td>
	<td>2,864</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>43.52% [41.6%-<b>45.5%</b>]</td>
	<td>2,555</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>43.95% [42.2%-<b>45.7%</b>]</td>
	<td>3,222</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.18% [42.4%-<b>45.9%</b>]</td>
	<td>3,232</td>
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
	<td>46.79% [46.5%-47.1%]</td>
	<td>132,061</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>40.39% [<b>35.5%</b>-45.2%]</td>
	<td>411</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>40.90% [<b>37.3%</b>-44.5%]</td>
	<td>731</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>43.72% [<b>38.5%</b>-48.9%]</td>
	<td>366</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.51% [<b>40.3%</b>-52.7%]</td>
	<td>258</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>42.67% [<b>40.4%</b>-44.9%]</td>
	<td>1,903</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>40.90% [37.3%-<b>44.5%</b>]</td>
	<td>731</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.73% [40.8%-<b>44.6%</b>]</td>
	<td>2,684</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>42.67% [40.4%-<b>44.9%</b>]</td>
	<td>1,903</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>40.39% [35.5%-<b>45.2%</b>]</td>
	<td>411</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>44.39% [43.0%-<b>45.7%</b>]</td>
	<td>5,436</td>
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
	<td>49.68% [49.3%-50.1%]</td>
	<td>59,752</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>42.43% [<b>36.8%</b>-48.1%]</td>
	<td>304</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.55% [<b>37.1%</b>-48.0%]</td>
	<td>329</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.68% [<b>37.4%</b>-51.9%]</td>
	<td>188</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>46.67% [<b>39.5%</b>-53.8%]</td>
	<td>195</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.69% [<b>40.1%</b>-49.3%]</td>
	<td>461</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.55% [37.1%-<b>48.0%</b>]</td>
	<td>329</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>42.43% [36.8%-<b>48.1%</b>]</td>
	<td>304</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>45.54% [42.9%-<b>48.2%</b>]</td>
	<td>1,412</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-blitzcrank"></span> Blitzcrank</td>
	<td>46.76% [44.4%-<b>49.2%</b>]</td>
	<td>1,743</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.69% [40.1%-<b>49.3%</b>]</td>
	<td>461</td>
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
	<td>49.28% [48.9%-49.7%]</td>
	<td>57,456</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>39.85% [<b>34.9%</b>-44.8%]</td>
	<td>394</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>41.10% [<b>36.1%</b>-46.1%]</td>
	<td>382</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>43.21% [<b>37.4%</b>-49.1%]</td>
	<td>287</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>48.21% [<b>40.5%</b>-55.9%]</td>
	<td>168</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.79% [<b>40.7%</b>-52.9%]</td>
	<td>265</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>39.85% [34.9%-<b>44.8%</b>]</td>
	<td>394</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>41.10% [36.1%-<b>46.1%</b>]</td>
	<td>382</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>45.00% [42.3%-<b>47.7%</b>]</td>
	<td>1,369</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>46.15% [44.3%-<b>48.0%</b>]</td>
	<td>2,938</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>45.98% [43.7%-<b>48.2%</b>]</td>
	<td>1,940</td>
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
	<td>47.24% [46.8%-47.7%]</td>
	<td>55,668</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>41.67% [<b>32.7%</b>-50.7%]</td>
	<td>120</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>41.78% [<b>33.6%</b>-49.9%]</td>
	<td>146</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>41.72% [<b>33.7%</b>-49.7%]</td>
	<td>151</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>40.54% [<b>34.4%</b>-46.6%]</td>
	<td>259</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>40.16% [<b>36.3%</b>-44.1%]</td>
	<td>630</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>40.16% [36.3%-<b>44.1%</b>]</td>
	<td>630</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>41.49% [38.1%-<b>44.9%</b>]</td>
	<td>858</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>43.86% [41.7%-<b>46.0%</b>]</td>
	<td>2,061</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>43.84% [41.3%-<b>46.4%</b>]</td>
	<td>1,510</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>43.29% [40.0%-<b>46.5%</b>]</td>
	<td>931</td>
</tr>
</table>

</details>
