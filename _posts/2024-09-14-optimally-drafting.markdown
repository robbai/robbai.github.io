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
	<td>53.36% [53.3%-53.5%]</td>
	<td>867,979</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>47.58% [<b>45.7%</b>-49.5%]</td>
	<td>2,688</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>49.16% [<b>47.9%</b>-50.5%]</td>
	<td>5,828</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.94% [<b>48.0%</b>-49.9%]</td>
	<td>11,247</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>50.17% [<b>48.1%</b>-52.3%]</td>
	<td>2,296</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>50.40% [<b>49.3%</b>-51.5%]</td>
	<td>7,967</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>47.58% [45.7%-<b>49.5%</b>]</td>
	<td>2,688</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.94% [48.0%-<b>49.9%</b>]</td>
	<td>11,247</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>49.16% [47.9%-<b>50.5%</b>]</td>
	<td>5,828</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>50.50% [49.9%-<b>51.1%</b>]</td>
	<td>25,133</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>50.67% [50.1%-<b>51.2%</b>]</td>
	<td>30,410</td>
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
	<td>52.43% [52.3%-52.6%]</td>
	<td>475,591</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>49.43% [<b>46.6%</b>-52.3%]</td>
	<td>1,236</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.55% [<b>46.8%</b>-50.3%]</td>
	<td>3,106</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>49.24% [<b>47.0%</b>-51.5%]</td>
	<td>1,964</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.02% [<b>47.0%</b>-49.0%]</td>
	<td>9,888</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>48.63% [<b>47.7%</b>-49.6%]</td>
	<td>10,985</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.02% [47.0%-<b>49.0%</b>]</td>
	<td>9,888</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.77% [48.2%-<b>49.4%</b>]</td>
	<td>26,583</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>48.63% [47.7%-<b>49.6%</b>]</td>
	<td>10,985</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.99% [48.1%-<b>49.9%</b>]</td>
	<td>12,397</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>49.28% [48.4%-<b>50.1%</b>]</td>
	<td>14,449</td>
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
	<td>51.43% [51.3%-51.6%]</td>
	<td>335,532</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.67% [<b>45.9%</b>-47.4%]</td>
	<td>17,514</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>48.32% [<b>46.2%</b>-50.4%]</td>
	<td>2,227</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.54% [<b>46.5%</b>-48.6%]</td>
	<td>9,366</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.66% [<b>46.6%</b>-48.7%]</td>
	<td>9,651</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.99% [<b>47.0%</b>-49.0%]</td>
	<td>9,461</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.67% [45.9%-<b>47.4%</b>]</td>
	<td>17,514</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.54% [46.5%-<b>48.6%</b>]</td>
	<td>9,366</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.66% [46.6%-<b>48.7%</b>]</td>
	<td>9,651</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.99% [47.0%-<b>49.0%</b>]</td>
	<td>9,461</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>48.18% [47.0%-<b>49.3%</b>]</td>
	<td>7,546</td>
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
	<td>51.48% [51.3%-51.7%]</td>
	<td>268,326</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.18% [<b>45.2%</b>-47.2%]</td>
	<td>9,815</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.02% [<b>45.4%</b>-50.7%]</td>
	<td>1,412</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>48.67% [<b>45.9%</b>-51.4%]</td>
	<td>1,315</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.98% [<b>46.4%</b>-49.6%]</td>
	<td>4,027</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.26% [<b>46.4%</b>-48.1%]</td>
	<td>14,112</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.18% [45.2%-<b>47.2%</b>]</td>
	<td>9,815</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.26% [46.4%-<b>48.1%</b>]</td>
	<td>14,112</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>48.19% [47.1%-<b>49.3%</b>]</td>
	<td>8,221</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.98% [46.4%-<b>49.6%</b>]</td>
	<td>4,027</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>48.20% [46.8%-<b>49.6%</b>]</td>
	<td>5,064</td>
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
	<td>50.65% [50.5%-50.8%]</td>
	<td>308,205</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.74% [<b>44.9%</b>-46.6%]</td>
	<td>14,224</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>47.10% [<b>45.3%</b>-48.9%]</td>
	<td>2,928</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>48.20% [<b>45.3%</b>-51.1%]</td>
	<td>1,220</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aatrox"></span> Aatrox</td>
	<td>46.29% [<b>45.4%</b>-47.2%]</td>
	<td>11,522</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.44% [<b>45.4%</b>-47.5%]</td>
	<td>9,706</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.74% [44.9%-<b>46.6%</b>]</td>
	<td>14,224</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aatrox"></span> Aatrox</td>
	<td>46.29% [45.4%-<b>47.2%</b>]</td>
	<td>11,522</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.44% [45.4%-<b>47.5%</b>]</td>
	<td>9,706</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>47.10% [45.3%-<b>48.9%</b>]</td>
	<td>2,928</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.99% [46.9%-<b>49.1%</b>]</td>
	<td>7,718</td>
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
	<td>51.59% [51.4%-51.8%]</td>
	<td>283,877</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>48.85% [<b>44.8%</b>-52.9%]</td>
	<td>608</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>47.96% [<b>45.2%</b>-50.7%]</td>
	<td>1,345</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.82% [<b>45.7%</b>-50.0%]</td>
	<td>2,179</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>48.21% [<b>45.8%</b>-50.6%]</td>
	<td>1,788</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.97% [<b>46.3%</b>-51.7%]</td>
	<td>1,356</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.34% [46.4%-<b>48.3%</b>]</td>
	<td>10,273</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.91% [46.9%-<b>49.0%</b>]</td>
	<td>9,223</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>48.12% [47.0%-<b>49.2%</b>]</td>
	<td>8,559</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.57% [47.8%-<b>49.4%</b>]</td>
	<td>15,450</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.16% [46.9%-<b>49.4%</b>]</td>
	<td>6,480</td>
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
	<td>50.63% [50.5%-50.8%]</td>
	<td>656,966</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.50% [<b>43.5%</b>-45.5%]</td>
	<td>9,834</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.03% [<b>45.2%</b>-46.9%]</td>
	<td>14,663</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.75% [<b>45.2%</b>-46.3%]</td>
	<td>35,735</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.17% [<b>45.6%</b>-46.8%]</td>
	<td>26,837</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.40% [<b>45.6%</b>-47.2%]</td>
	<td>16,354</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.50% [43.5%-<b>45.5%</b>]</td>
	<td>9,834</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.75% [45.2%-<b>46.3%</b>]</td>
	<td>35,735</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.17% [45.6%-<b>46.8%</b>]</td>
	<td>26,837</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.03% [45.2%-<b>46.9%</b>]</td>
	<td>14,663</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.40% [45.6%-<b>47.2%</b>]</td>
	<td>16,354</td>
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
	<td>51.58% [51.5%-51.7%]</td>
	<td>668,557</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.56% [<b>44.8%</b>-48.3%]</td>
	<td>3,344</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>45.89% [<b>45.1%</b>-46.7%]</td>
	<td>15,052</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>46.10% [<b>45.3%</b>-46.9%]</td>
	<td>13,880</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.03% [<b>45.3%</b>-46.7%]</td>
	<td>19,704</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>46.96% [<b>45.5%</b>-48.4%]</td>
	<td>4,823</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>45.89% [45.1%-<b>46.7%</b>]</td>
	<td>15,052</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.03% [45.3%-<b>46.7%</b>]</td>
	<td>19,704</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.25% [45.6%-<b>46.9%</b>]</td>
	<td>20,703</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>46.10% [45.3%-<b>46.9%</b>]</td>
	<td>13,880</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.61% [45.8%-<b>47.4%</b>]</td>
	<td>17,013</td>
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
	<td>51.47% [51.3%-51.6%]</td>
	<td>416,842</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.72% [<b>43.6%</b>-49.8%]</td>
	<td>1,021</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.47% [<b>44.8%</b>-46.1%]</td>
	<td>23,391</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.23% [<b>45.3%</b>-47.1%]</td>
	<td>11,903</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.39% [<b>45.5%</b>-49.3%]</td>
	<td>2,756</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>49.46% [<b>46.5%</b>-52.5%]</td>
	<td>1,108</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.47% [44.8%-<b>46.1%</b>]</td>
	<td>23,391</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.23% [45.3%-<b>47.1%</b>]</td>
	<td>11,903</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.99% [47.0%-<b>48.9%</b>]</td>
	<td>10,962</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>48.36% [47.5%-<b>49.3%</b>]</td>
	<td>12,581</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.39% [45.5%-<b>49.3%</b>]</td>
	<td>2,756</td>
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
	<td>50.94% [50.8%-51.1%]</td>
	<td>550,195</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.77% [<b>43.0%</b>-48.5%]</td>
	<td>1,335</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.57% [<b>44.8%</b>-46.3%]</td>
	<td>17,218</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.72% [<b>46.0%</b>-47.4%]</td>
	<td>19,318</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>49.16% [<b>46.1%</b>-52.2%]</td>
	<td>1,068</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>47.28% [<b>46.5%</b>-48.0%]</td>
	<td>17,764</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.57% [44.8%-<b>46.3%</b>]</td>
	<td>17,218</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.72% [46.0%-<b>47.4%</b>]</td>
	<td>19,318</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.47% [46.9%-<b>48.0%</b>]</td>
	<td>32,297</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>47.28% [46.5%-<b>48.0%</b>]</td>
	<td>17,764</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.77% [43.0%-<b>48.5%</b>]</td>
	<td>1,335</td>
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
	<td>52.69% [52.6%-52.8%]</td>
	<td>519,224</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>46.20% [<b>44.6%</b>-47.8%]</td>
	<td>3,870</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.62% [<b>44.7%</b>-46.5%]</td>
	<td>12,897</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.09% [<b>45.3%</b>-46.9%]</td>
	<td>14,711</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.72% [<b>46.1%</b>-49.3%]</td>
	<td>3,971</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>49.86% [<b>47.2%</b>-52.5%]</td>
	<td>1,452</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.62% [44.7%-<b>46.5%</b>]</td>
	<td>12,897</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.09% [45.3%-<b>46.9%</b>]</td>
	<td>14,711</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>46.20% [44.6%-<b>47.8%</b>]</td>
	<td>3,870</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aatrox"></span> Aatrox</td>
	<td>48.12% [47.4%-<b>48.8%</b>]</td>
	<td>21,526</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.72% [46.1%-<b>49.3%</b>]</td>
	<td>3,971</td>
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
	<td>52.37% [52.1%-52.7%]</td>
	<td>126,061</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>47.80% [<b>44.2%</b>-51.4%]</td>
	<td>772</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>50.15% [<b>44.6%</b>-55.7%]</td>
	<td>329</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>46.78% [<b>44.8%</b>-48.8%]</td>
	<td>2,437</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.62% [<b>46.2%</b>-49.1%]</td>
	<td>4,626</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.13% [<b>46.5%</b>-49.7%]</td>
	<td>3,989</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>46.78% [44.8%-<b>48.8%</b>]</td>
	<td>2,437</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.62% [46.2%-<b>49.1%</b>]</td>
	<td>4,626</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.13% [46.5%-<b>49.7%</b>]</td>
	<td>3,989</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>48.67% [46.9%-<b>50.4%</b>]</td>
	<td>3,337</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>49.31% [48.0%-<b>50.6%</b>]</td>
	<td>5,672</td>
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
	<td>50.93% [50.8%-51.1%]</td>
	<td>563,522</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.53% [<b>42.7%</b>-46.3%]</td>
	<td>3,079</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.21% [<b>44.4%</b>-46.1%]</td>
	<td>13,869</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.08% [<b>44.4%</b>-45.8%]</td>
	<td>20,366</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>46.93% [<b>45.9%</b>-48.0%]</td>
	<td>8,590</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>47.71% [<b>46.7%</b>-48.7%]</td>
	<td>9,580</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.08% [44.4%-<b>45.8%</b>]</td>
	<td>20,366</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.21% [44.4%-<b>46.1%</b>]</td>
	<td>13,869</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.53% [42.7%-<b>46.3%</b>]</td>
	<td>3,079</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>46.93% [45.9%-<b>48.0%</b>]</td>
	<td>8,590</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.81% [47.2%-<b>48.4%</b>]</td>
	<td>27,944</td>
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
	<td>51.74% [51.6%-51.9%]</td>
	<td>372,169</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.67% [<b>42.8%</b>-44.6%]</td>
	<td>11,683</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.02% [<b>44.3%</b>-45.7%]</td>
	<td>19,751</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>47.06% [<b>45.9%</b>-48.2%]</td>
	<td>7,339</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>48.27% [<b>46.0%</b>-50.5%]</td>
	<td>1,970</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.81% [<b>46.4%</b>-51.2%]</td>
	<td>1,762</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.67% [42.8%-<b>44.6%</b>]</td>
	<td>11,683</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.02% [44.3%-<b>45.7%</b>]</td>
	<td>19,751</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>47.06% [45.9%-<b>48.2%</b>]</td>
	<td>7,339</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>47.54% [46.6%-<b>48.4%</b>]</td>
	<td>12,463</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.51% [46.6%-<b>48.5%</b>]</td>
	<td>10,846</td>
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
	<td>49.94% [49.8%-50.1%]</td>
	<td>459,775</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>41.17% [<b>40.3%</b>-42.0%]</td>
	<td>14,088</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.76% [<b>43.9%</b>-45.7%]</td>
	<td>12,206</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.89% [<b>43.9%</b>-47.8%]</td>
	<td>2,615</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>47.34% [<b>44.2%</b>-50.4%]</td>
	<td>1,035</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.30% [<b>44.4%</b>-46.2%]</td>
	<td>12,849</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>41.17% [40.3%-<b>42.0%</b>]</td>
	<td>14,088</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.76% [43.9%-<b>45.7%</b>]</td>
	<td>12,206</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.30% [44.4%-<b>46.2%</b>]</td>
	<td>12,849</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.59% [44.9%-<b>46.2%</b>]</td>
	<td>22,850</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>46.46% [45.3%-<b>47.6%</b>]</td>
	<td>7,453</td>
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
	<td>49.34% [49.2%-49.5%]</td>
	<td>432,319</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.76% [<b>41.9%</b>-47.6%]</td>
	<td>1,231</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.54% [<b>43.8%</b>-45.3%]</td>
	<td>18,445</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.21% [<b>44.1%</b>-50.3%]</td>
	<td>1,040</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.91% [<b>44.7%</b>-49.1%]</td>
	<td>2,089</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.75% [<b>44.7%</b>-48.8%]</td>
	<td>2,449</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.54% [43.8%-<b>45.3%</b>]</td>
	<td>18,445</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.78% [44.8%-<b>46.7%</b>]</td>
	<td>10,865</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.81% [44.8%-<b>46.8%</b>]</td>
	<td>9,962</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.79% [44.7%-<b>46.8%</b>]</td>
	<td>9,024</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.20% [45.4%-<b>47.0%</b>]</td>
	<td>14,033</td>
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
	<td>50.90% [50.8%-51.0%]</td>
	<td>462,676</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.59% [<b>42.8%</b>-44.4%]</td>
	<td>14,422</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.32% [<b>43.6%</b>-47.1%]</td>
	<td>3,235</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>47.03% [<b>44.8%</b>-49.3%]</td>
	<td>1,920</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.01% [<b>44.9%</b>-51.1%]</td>
	<td>1,056</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.79% [<b>45.0%</b>-46.6%]</td>
	<td>14,160</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.59% [42.8%-<b>44.4%</b>]</td>
	<td>14,422</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.79% [45.0%-<b>46.6%</b>]</td>
	<td>14,160</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.32% [43.6%-<b>47.1%</b>]</td>
	<td>3,235</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.44% [45.0%-<b>47.8%</b>]</td>
	<td>5,028</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>47.56% [46.9%-<b>48.2%</b>]</td>
	<td>21,629</td>
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
	<td>50.05% [49.9%-50.2%]</td>
	<td>737,955</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.87% [<b>43.4%</b>-48.3%]</td>
	<td>1,657</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.98% [<b>43.5%</b>-46.4%]</td>
	<td>4,831</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.64% [<b>44.2%</b>-47.1%]</td>
	<td>4,976</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>47.13% [<b>44.9%</b>-49.3%]</td>
	<td>2,024</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>46.23% [<b>45.6%</b>-46.9%]</td>
	<td>24,833</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.98% [43.5%-<b>46.4%</b>]</td>
	<td>4,831</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>46.23% [45.6%-<b>46.9%</b>]</td>
	<td>24,833</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.64% [44.2%-<b>47.1%</b>]</td>
	<td>4,976</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.53% [45.8%-<b>47.2%</b>]</td>
	<td>20,337</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.52% [45.7%-<b>47.3%</b>]</td>
	<td>15,868</td>
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
	<td>52.48% [52.2%-52.8%]</td>
	<td>108,929</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.26% [<b>41.5%</b>-49.0%]</td>
	<td>718</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.06% [<b>43.5%</b>-46.6%]</td>
	<td>4,334</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>49.15% [<b>43.8%</b>-54.5%]</td>
	<td>354</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.48% [<b>44.2%</b>-50.8%]</td>
	<td>912</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.59% [<b>44.7%</b>-48.5%]</td>
	<td>2,827</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.06% [43.5%-<b>46.6%</b>]</td>
	<td>4,334</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.59% [44.7%-<b>48.5%</b>]</td>
	<td>2,827</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.26% [41.5%-<b>49.0%</b>]</td>
	<td>718</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.48% [44.2%-<b>50.8%</b>]</td>
	<td>912</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-darius"></span> Darius</td>
	<td>49.19% [47.5%-<b>50.9%</b>]</td>
	<td>3,570</td>
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
	<td>52.80% [52.7%-52.9%]</td>
	<td>498,955</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.66% [<b>42.9%</b>-48.4%]</td>
	<td>1,290</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.12% [<b>43.5%</b>-44.7%]</td>
	<td>29,629</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.31% [<b>43.6%</b>-49.0%]</td>
	<td>1,341</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.80% [<b>44.0%</b>-45.6%]</td>
	<td>15,369</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.73% [<b>44.3%</b>-47.2%]</td>
	<td>4,568</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.12% [43.5%-<b>44.7%</b>]</td>
	<td>29,629</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.80% [44.0%-<b>45.6%</b>]</td>
	<td>15,369</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.29% [45.6%-<b>47.0%</b>]</td>
	<td>19,165</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.73% [44.3%-<b>47.2%</b>]</td>
	<td>4,568</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.21% [46.0%-<b>48.4%</b>]</td>
	<td>6,939</td>
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
	<td>49.45% [49.3%-49.6%]</td>
	<td>740,921</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.61% [<b>42.3%</b>-46.9%]</td>
	<td>1,894</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.19% [<b>43.5%</b>-44.9%]</td>
	<td>19,343</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.95% [<b>43.8%</b>-46.1%]</td>
	<td>7,206</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.52% [<b>43.9%</b>-45.1%]</td>
	<td>27,484</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.78% [<b>44.1%</b>-45.4%]</td>
	<td>23,324</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.19% [43.5%-<b>44.9%</b>]</td>
	<td>19,343</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.52% [43.9%-<b>45.1%</b>]</td>
	<td>27,484</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.78% [44.1%-<b>45.4%</b>]</td>
	<td>23,324</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.95% [43.8%-<b>46.1%</b>]</td>
	<td>7,206</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.61% [42.3%-<b>46.9%</b>]</td>
	<td>1,894</td>
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
	<td>50.74% [50.5%-51.0%]</td>
	<td>210,519</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.16% [<b>41.9%</b>-48.4%]</td>
	<td>941</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.25% [<b>43.3%</b>-51.2%]</td>
	<td>637</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.47% [<b>43.6%</b>-49.3%]</td>
	<td>1,231</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>47.70% [<b>43.7%</b>-51.7%]</td>
	<td>610</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>46.07% [<b>44.5%</b>-47.7%]</td>
	<td>3,864</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.93% [44.8%-<b>47.0%</b>]</td>
	<td>8,347</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>46.10% [44.8%-<b>47.4%</b>]</td>
	<td>5,460</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>46.07% [44.5%-<b>47.7%</b>]</td>
	<td>3,864</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.79% [45.5%-<b>48.1%</b>]</td>
	<td>5,830</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>47.34% [46.3%-<b>48.4%</b>]</td>
	<td>8,839</td>
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
	<td>49.34% [49.1%-49.5%]</td>
	<td>265,411</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.17% [<b>42.9%</b>-47.5%]</td>
	<td>1,884</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.56% [<b>43.2%</b>-45.9%]</td>
	<td>5,649</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.88% [<b>43.5%</b>-46.3%]</td>
	<td>5,054</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.09% [<b>44.0%</b>-46.2%]</td>
	<td>8,261</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.85% [<b>44.2%</b>-47.5%]</td>
	<td>3,494</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.56% [43.2%-<b>45.9%</b>]</td>
	<td>5,649</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.09% [44.0%-<b>46.2%</b>]</td>
	<td>8,261</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.27% [44.3%-<b>46.2%</b>]</td>
	<td>10,873</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.88% [43.5%-<b>46.3%</b>]</td>
	<td>5,054</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>45.80% [44.5%-<b>47.1%</b>]</td>
	<td>6,020</td>
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
	<td>52.15% [52.0%-52.3%]</td>
	<td>360,446</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.68% [<b>41.5%</b>-47.8%]</td>
	<td>1,005</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.73% [<b>42.9%</b>-46.6%]</td>
	<td>2,915</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.92% [<b>44.9%</b>-47.0%]</td>
	<td>9,126</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.89% [<b>44.9%</b>-46.9%]</td>
	<td>10,755</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.94% [<b>45.2%</b>-46.6%]</td>
	<td>20,686</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.73% [42.9%-<b>46.6%</b>]</td>
	<td>2,915</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.94% [45.2%-<b>46.6%</b>]</td>
	<td>20,686</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.89% [44.9%-<b>46.9%</b>]</td>
	<td>10,755</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.92% [44.9%-<b>47.0%</b>]</td>
	<td>9,126</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.68% [41.5%-<b>47.8%</b>]</td>
	<td>1,005</td>
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
	<td>51.14% [50.9%-51.4%]</td>
	<td>155,569</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>47.47% [<b>42.3%</b>-52.6%]</td>
	<td>375</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.87% [<b>42.8%</b>-49.0%]</td>
	<td>1,029</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.10% [<b>43.0%</b>-49.2%]</td>
	<td>1,039</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.89% [<b>43.4%</b>-46.3%]</td>
	<td>4,736</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>47.71% [<b>44.0%</b>-51.4%]</td>
	<td>719</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.89% [43.4%-<b>46.3%</b>]</td>
	<td>4,736</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.37% [44.7%-<b>48.1%</b>]</td>
	<td>3,470</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>46.31% [44.2%-<b>48.4%</b>]</td>
	<td>2,252</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.87% [42.8%-<b>49.0%</b>]</td>
	<td>1,029</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.50% [45.9%-<b>49.1%</b>]</td>
	<td>3,966</td>
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
	<td>49.72% [49.5%-49.9%]</td>
	<td>278,334</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.74% [<b>42.1%</b>-45.4%]</td>
	<td>3,507</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>46.78% [<b>42.5%</b>-51.1%]</td>
	<td>543</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.55% [<b>42.7%</b>-44.4%]</td>
	<td>12,493</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.41% [<b>43.1%</b>-45.7%]</td>
	<td>5,983</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.35% [<b>43.4%</b>-45.3%]</td>
	<td>10,078</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.55% [42.7%-<b>44.4%</b>]</td>
	<td>12,493</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.35% [43.4%-<b>45.3%</b>]</td>
	<td>10,078</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.74% [42.1%-<b>45.4%</b>]</td>
	<td>3,507</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.41% [43.1%-<b>45.7%</b>]</td>
	<td>5,983</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.58% [45.6%-<b>47.6%</b>]</td>
	<td>9,845</td>
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
	<td>49.00% [48.8%-49.2%]</td>
	<td>297,120</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>42.31% [<b>41.0%</b>-43.6%]</td>
	<td>5,765</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.74% [<b>42.4%</b>-47.1%]</td>
	<td>1,835</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.40% [<b>42.5%</b>-46.3%]</td>
	<td>2,858</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.18% [<b>43.2%</b>-45.2%]</td>
	<td>9,753</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.50% [<b>43.8%</b>-49.2%]</td>
	<td>1,359</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>42.31% [41.0%-<b>43.6%</b>]</td>
	<td>5,765</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.18% [43.2%-<b>45.2%</b>]</td>
	<td>9,753</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.06% [44.0%-<b>46.1%</b>]</td>
	<td>8,925</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>44.40% [42.5%-<b>46.3%</b>]</td>
	<td>2,858</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.06% [43.9%-<b>46.3%</b>]</td>
	<td>6,769</td>
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
	<td>49.21% [49.0%-49.4%]</td>
	<td>364,264</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.26% [<b>42.2%</b>-44.3%]</td>
	<td>9,241</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>44.72% [<b>42.3%</b>-47.1%]</td>
	<td>1,742</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>43.90% [<b>42.6%</b>-45.2%]</td>
	<td>5,980</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.77% [<b>43.7%</b>-45.9%]</td>
	<td>8,110</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.03% [<b>44.1%</b>-45.9%]</td>
	<td>12,670</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.26% [42.2%-<b>44.3%</b>]</td>
	<td>9,241</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>43.90% [42.6%-<b>45.2%</b>]</td>
	<td>5,980</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.77% [43.7%-<b>45.9%</b>]</td>
	<td>8,110</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.03% [44.1%-<b>45.9%</b>]</td>
	<td>12,670</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>45.15% [44.3%-<b>46.0%</b>]</td>
	<td>14,483</td>
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
	<td>47.13% [47.0%-47.3%]</td>
	<td>634,086</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-riven"></span> Riven</td>
	<td>42.84% [<b>42.0%</b>-43.7%]</td>
	<td>13,561</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.81% [<b>42.2%</b>-45.4%]</td>
	<td>3,953</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.59% [<b>42.3%</b>-44.9%]</td>
	<td>5,605</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.35% [<b>42.7%</b>-46.0%]</td>
	<td>3,759</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>43.72% [<b>42.8%</b>-44.6%]</td>
	<td>11,702</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-riven"></span> Riven</td>
	<td>42.84% [42.0%-<b>43.7%</b>]</td>
	<td>13,561</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>43.72% [42.8%-<b>44.6%</b>]</td>
	<td>11,702</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>43.99% [43.3%-<b>44.6%</b>]</td>
	<td>22,867</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.95% [43.1%-<b>44.8%</b>]</td>
	<td>14,923</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>44.18% [43.5%-<b>44.9%</b>]</td>
	<td>19,966</td>
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
	<td>50.94% [50.7%-51.2%]</td>
	<td>149,038</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.44% [<b>40.0%</b>-46.9%]</td>
	<td>808</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.78% [<b>42.1%</b>-49.4%]</td>
	<td>747</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.75% [<b>42.7%</b>-46.8%]</td>
	<td>2,449</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.24% [<b>42.8%</b>-45.7%]</td>
	<td>4,625</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.22% [<b>43.6%</b>-46.8%]</td>
	<td>3,974</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.24% [42.8%-<b>45.7%</b>]</td>
	<td>4,625</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.75% [42.7%-<b>46.8%</b>]</td>
	<td>2,449</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.22% [43.6%-<b>46.8%</b>]</td>
	<td>3,974</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.44% [40.0%-<b>46.9%</b>]</td>
	<td>808</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.53% [45.1%-<b>47.9%</b>]</td>
	<td>5,151</td>
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
	<td>51.35% [51.2%-51.5%]</td>
	<td>536,181</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.97% [<b>41.2%</b>-44.8%]</td>
	<td>3,060</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.83% [<b>41.8%</b>-43.8%]</td>
	<td>10,091</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.74% [<b>42.0%</b>-43.5%]</td>
	<td>17,152</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.84% [<b>42.8%</b>-44.9%]</td>
	<td>9,391</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.76% [<b>43.1%</b>-44.4%]</td>
	<td>23,621</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.74% [42.0%-<b>43.5%</b>]</td>
	<td>17,152</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.83% [41.8%-<b>43.8%</b>]</td>
	<td>10,091</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.76% [43.1%-<b>44.4%</b>]</td>
	<td>23,621</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.97% [41.2%-<b>44.8%</b>]</td>
	<td>3,060</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.84% [42.8%-<b>44.9%</b>]</td>
	<td>9,391</td>
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
	<td>51.11% [50.8%-51.4%]</td>
	<td>108,566</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.88% [<b>39.2%</b>-48.6%]</td>
	<td>449</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.08% [<b>41.6%</b>-46.6%]</td>
	<td>1,588</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.50% [<b>41.7%</b>-45.3%]</td>
	<td>2,970</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>46.56% [<b>42.2%</b>-50.9%]</td>
	<td>524</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.55% [<b>42.6%</b>-46.5%]</td>
	<td>2,687</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.50% [41.7%-<b>45.3%</b>]</td>
	<td>2,970</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.55% [42.6%-<b>46.5%</b>]</td>
	<td>2,687</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.08% [41.6%-<b>46.6%</b>]</td>
	<td>1,588</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>46.00% [43.8%-<b>48.2%</b>]</td>
	<td>2,048</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.88% [39.2%-<b>48.6%</b>]</td>
	<td>449</td>
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
	<td>49.30% [49.1%-49.5%]</td>
	<td>310,385</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.34% [<b>37.6%</b>-45.1%]</td>
	<td>704</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.79% [<b>41.4%</b>-46.1%]</td>
	<td>1,770</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.27% [<b>43.2%</b>-45.3%]</td>
	<td>9,313</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.62% [<b>43.3%</b>-45.9%]</td>
	<td>5,972</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.63% [<b>43.5%</b>-45.8%]</td>
	<td>7,202</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.34% [37.6%-<b>45.1%</b>]</td>
	<td>704</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.27% [43.2%-<b>45.3%</b>]</td>
	<td>9,313</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.63% [43.5%-<b>45.8%</b>]</td>
	<td>7,202</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.62% [43.3%-<b>45.9%</b>]</td>
	<td>5,972</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.79% [41.4%-<b>46.1%</b>]</td>
	<td>1,770</td>
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
	<td>48.47% [48.3%-48.7%]</td>
	<td>274,099</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>40.27% [<b>36.2%</b>-44.3%]</td>
	<td>586</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>42.56% [<b>41.4%</b>-43.7%]</td>
	<td>6,938</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.64% [<b>41.7%</b>-43.6%]</td>
	<td>10,941</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.60% [<b>42.1%</b>-47.1%]</td>
	<td>1,538</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>44.47% [<b>42.3%</b>-46.7%]</td>
	<td>2,035</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.64% [41.7%-<b>43.6%</b>]</td>
	<td>10,941</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>42.56% [41.4%-<b>43.7%</b>]</td>
	<td>6,938</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>40.27% [36.2%-<b>44.3%</b>]</td>
	<td>586</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.89% [42.6%-<b>45.2%</b>]</td>
	<td>5,698</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.49% [43.1%-<b>45.9%</b>]</td>
	<td>4,914</td>
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
	<td>50.63% [50.3%-50.9%]</td>
	<td>111,082</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.97% [<b>41.2%</b>-48.7%]</td>
	<td>696</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>45.54% [<b>41.3%</b>-49.7%]</td>
	<td>560</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.07% [<b>41.4%</b>-48.7%]</td>
	<td>750</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.82% [<b>42.1%</b>-49.5%]</td>
	<td>718</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.31% [<b>44.4%</b>-48.2%]</td>
	<td>2,725</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>46.31% [44.4%-<b>48.2%</b>]</td>
	<td>2,725</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.73% [45.0%-<b>48.4%</b>]</td>
	<td>3,398</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.33% [46.0%-<b>48.7%</b>]</td>
	<td>5,447</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.07% [41.4%-<b>48.7%</b>]</td>
	<td>750</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.97% [41.2%-<b>48.7%</b>]</td>
	<td>696</td>
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
	<td>49.05% [48.8%-49.3%]</td>
	<td>188,952</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.03% [<b>40.8%</b>-47.3%]</td>
	<td>929</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.28% [<b>41.3%</b>-47.3%]</td>
	<td>1,111</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.09% [<b>41.4%</b>-50.7%]</td>
	<td>460</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.51% [<b>42.0%</b>-45.0%]</td>
	<td>4,229</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>46.78% [<b>42.1%</b>-51.5%]</td>
	<td>451</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.51% [42.0%-<b>45.0%</b>]</td>
	<td>4,229</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.65% [42.2%-<b>45.1%</b>]</td>
	<td>4,818</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.01% [43.7%-<b>46.4%</b>]</td>
	<td>5,486</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.85% [43.3%-<b>46.4%</b>]</td>
	<td>4,332</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.85% [43.1%-<b>46.6%</b>]</td>
	<td>3,282</td>
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
	<td>50.32% [50.0%-50.6%]</td>
	<td>121,708</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.98% [<b>40.7%</b>-51.2%]</td>
	<td>361</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.93% [<b>41.3%</b>-48.6%]</td>
	<td>739</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.40% [<b>42.1%</b>-54.7%]</td>
	<td>250</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.29% [<b>42.6%</b>-50.0%]</td>
	<td>741</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.56% [<b>43.5%</b>-49.7%]</td>
	<td>1,031</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.62% [44.2%-<b>47.1%</b>]</td>
	<td>4,840</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.57% [43.9%-<b>47.2%</b>]</td>
	<td>3,544</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.66% [43.9%-<b>47.4%</b>]</td>
	<td>3,110</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.93% [41.3%-<b>48.6%</b>]</td>
	<td>739</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-riven"></span> Riven</td>
	<td>46.80% [44.7%-<b>48.9%</b>]</td>
	<td>2,233</td>
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
	<td>49.00% [48.9%-49.1%]</td>
	<td>784,097</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>41.40% [<b>40.7%</b>-42.1%]</td>
	<td>22,826</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.83% [<b>41.2%</b>-42.5%]</td>
	<td>23,637</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.59% [<b>42.2%</b>-45.0%]</td>
	<td>5,244</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.23% [<b>42.4%</b>-44.0%]</td>
	<td>15,687</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.64% [<b>43.4%</b>-47.9%]</td>
	<td>1,937</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>41.40% [40.7%-<b>42.1%</b>]</td>
	<td>22,826</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.83% [41.2%-<b>42.5%</b>]</td>
	<td>23,637</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.23% [42.4%-<b>44.0%</b>]</td>
	<td>15,687</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.39% [43.9%-<b>44.9%</b>]</td>
	<td>39,323</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.59% [42.2%-<b>45.0%</b>]</td>
	<td>5,244</td>
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
	<td>49.48% [49.3%-49.7%]</td>
	<td>286,123</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>40.13% [<b>38.2%</b>-42.1%]</td>
	<td>2,574</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>44.05% [<b>41.1%</b>-47.0%]</td>
	<td>1,101</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>43.49% [<b>42.3%</b>-44.7%]</td>
	<td>6,995</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.05% [<b>42.6%</b>-45.5%]</td>
	<td>4,511</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.91% [<b>42.6%</b>-45.2%]</td>
	<td>5,942</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>40.13% [38.2%-<b>42.1%</b>]</td>
	<td>2,574</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>43.49% [42.3%-<b>44.7%</b>]</td>
	<td>6,995</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.91% [42.6%-<b>45.2%</b>]</td>
	<td>5,942</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.05% [42.6%-<b>45.5%</b>]</td>
	<td>4,511</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>44.56% [43.6%-<b>45.5%</b>]</td>
	<td>10,158</td>
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
	<td>48.33% [48.1%-48.5%]</td>
	<td>216,851</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.30% [<b>40.0%</b>-48.6%]</td>
	<td>544</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.48% [<b>41.0%</b>-44.0%]</td>
	<td>4,254</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.07% [<b>41.1%</b>-47.0%]</td>
	<td>1,155</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.06% [<b>41.3%</b>-44.8%]</td>
	<td>3,107</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>43.96% [<b>41.3%</b>-46.6%]</td>
	<td>1,383</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.48% [41.0%-<b>44.0%</b>]</td>
	<td>4,254</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.22% [42.3%-<b>44.1%</b>]</td>
	<td>12,890</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.06% [41.3%-<b>44.8%</b>]</td>
	<td>3,107</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.61% [42.2%-<b>45.1%</b>]</td>
	<td>4,673</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>45.11% [43.8%-<b>46.4%</b>]</td>
	<td>5,735</td>
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
	<td>50.47% [50.1%-50.8%]</td>
	<td>79,346</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.83% [<b>38.4%</b>-47.2%]</td>
	<td>509</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.87% [<b>40.9%</b>-48.8%]</td>
	<td>633</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.87% [<b>41.1%</b>-44.7%]</td>
	<td>3,002</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.32% [<b>41.7%</b>-51.0%]</td>
	<td>462</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.07% [<b>42.6%</b>-47.5%]</td>
	<td>1,675</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.87% [41.1%-<b>44.7%</b>]</td>
	<td>3,002</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.83% [38.4%-<b>47.2%</b>]</td>
	<td>509</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.25% [43.0%-<b>47.5%</b>]</td>
	<td>1,989</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.07% [42.6%-<b>47.5%</b>]</td>
	<td>1,675</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.31% [42.9%-<b>47.7%</b>]</td>
	<td>1,715</td>
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
	<td>47.02% [46.9%-47.1%]</td>
	<td>649,443</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>40.91% [<b>39.5%</b>-42.3%]</td>
	<td>4,705</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>41.92% [<b>40.9%</b>-42.9%]</td>
	<td>9,644</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.41% [<b>41.6%</b>-43.3%]</td>
	<td>13,694</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.62% [<b>41.9%</b>-43.4%]</td>
	<td>18,300</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.79% [<b>42.5%</b>-47.1%]</td>
	<td>1,815</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>40.91% [39.5%-<b>42.3%</b>]</td>
	<td>4,705</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>41.92% [40.9%-<b>42.9%</b>]</td>
	<td>9,644</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.41% [41.6%-<b>43.3%</b>]</td>
	<td>13,694</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.62% [41.9%-<b>43.4%</b>]</td>
	<td>18,300</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.74% [43.1%-<b>44.4%</b>]</td>
	<td>22,385</td>
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
	<td>49.90% [49.6%-50.2%]</td>
	<td>130,091</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.05% [<b>39.4%</b>-46.7%]</td>
	<td>741</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.99% [<b>40.7%</b>-47.2%]</td>
	<td>932</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.79% [<b>40.8%</b>-52.8%]</td>
	<td>280</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.79% [<b>42.0%</b>-45.6%]</td>
	<td>3,131</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>45.41% [<b>42.5%</b>-48.3%]</td>
	<td>1,176</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.79% [42.0%-<b>45.6%</b>]</td>
	<td>3,131</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.05% [39.4%-<b>46.7%</b>]</td>
	<td>741</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.79% [42.9%-<b>46.7%</b>]</td>
	<td>2,688</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.04% [43.3%-<b>46.7%</b>]</td>
	<td>3,419</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.47% [44.1%-<b>46.8%</b>]</td>
	<td>5,579</td>
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
	<td>48.76% [48.5%-49.0%]</td>
	<td>129,441</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>39.79% [<b>37.9%</b>-41.7%]</td>
	<td>2,614</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>44.90% [<b>40.4%</b>-49.4%]</td>
	<td>490</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.38% [<b>40.6%</b>-44.2%]</td>
	<td>2,980</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.87% [<b>41.5%</b>-48.2%]</td>
	<td>878</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>44.48% [<b>42.1%</b>-46.8%]</td>
	<td>1,774</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>39.79% [37.9%-<b>41.7%</b>]</td>
	<td>2,614</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.38% [40.6%-<b>44.2%</b>]</td>
	<td>2,980</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>44.48% [42.1%-<b>46.8%</b>]</td>
	<td>1,774</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.12% [43.4%-<b>46.9%</b>]</td>
	<td>3,291</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.45% [43.8%-<b>47.1%</b>]</td>
	<td>3,813</td>
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
	<td>142,239</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>42.63% [<b>39.0%</b>-46.3%]</td>
	<td>739</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.75% [<b>40.4%</b>-47.1%]</td>
	<td>880</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>45.08% [<b>41.8%</b>-48.4%]</td>
	<td>905</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.44% [<b>41.8%</b>-51.1%]</td>
	<td>463</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.23% [<b>41.9%</b>-46.6%]</td>
	<td>1,784</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>42.63% [39.0%-<b>46.3%</b>]</td>
	<td>739</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.23% [41.9%-<b>46.6%</b>]</td>
	<td>1,784</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.79% [42.9%-<b>46.7%</b>]</td>
	<td>2,858</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.85% [43.0%-<b>46.7%</b>]</td>
	<td>2,863</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.16% [43.5%-<b>46.9%</b>]</td>
	<td>3,390</td>
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
	<td>51.77% [51.3%-52.2%]</td>
	<td>53,442</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>44.95% [<b>39.1%</b>-50.8%]</td>
	<td>287</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>48.61% [<b>40.3%</b>-56.9%]</td>
	<td>144</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.33% [<b>40.7%</b>-52.0%]</td>
	<td>313</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-olaf"></span> Olaf</td>
	<td>45.55% [<b>41.1%</b>-50.0%]</td>
	<td>494</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>45.21% [<b>41.3%</b>-49.1%]</td>
	<td>657</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.30% [41.8%-<b>46.8%</b>]</td>
	<td>1,526</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>45.21% [41.3%-<b>49.1%</b>]</td>
	<td>657</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-olaf"></span> Olaf</td>
	<td>45.55% [41.1%-<b>50.0%</b>]</td>
	<td>494</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.74% [43.4%-<b>50.1%</b>]</td>
	<td>875</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.03% [45.3%-<b>50.7%</b>]</td>
	<td>1,368</td>
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
	<td>50.14% [49.7%-50.5%]</td>
	<td>63,603</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>43.38% [<b>37.7%</b>-49.1%]</td>
	<td>302</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-olaf"></span> Olaf</td>
	<td>45.24% [<b>40.1%</b>-50.4%]</td>
	<td>378</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.28% [<b>40.4%</b>-48.1%]</td>
	<td>664</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.50% [<b>40.7%</b>-46.3%]</td>
	<td>1,230</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.36% [<b>40.8%</b>-47.9%]</td>
	<td>771</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.50% [40.7%-<b>46.3%</b>]</td>
	<td>1,230</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>44.01% [41.4%-<b>46.6%</b>]</td>
	<td>1,452</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.35% [43.6%-<b>47.1%</b>]</td>
	<td>3,063</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.36% [40.8%-<b>47.9%</b>]</td>
	<td>771</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>44.28% [40.4%-<b>48.1%</b>]</td>
	<td>664</td>
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
	<td>48.34% [48.0%-48.7%]</td>
	<td>86,444</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.79% [<b>36.0%</b>-49.5%]</td>
	<td>215</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.18% [<b>40.0%</b>-44.3%]</td>
	<td>2,072</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>41.64% [<b>40.2%</b>-43.1%]</td>
	<td>4,503</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.57% [<b>40.4%</b>-44.8%]</td>
	<td>2,018</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.34% [<b>40.8%</b>-45.8%]</td>
	<td>1,576</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>41.64% [40.2%-<b>43.1%</b>]</td>
	<td>4,503</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.18% [40.0%-<b>44.3%</b>]</td>
	<td>2,072</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.57% [40.4%-<b>44.8%</b>]</td>
	<td>2,018</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.34% [41.5%-<b>45.2%</b>]</td>
	<td>2,965</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.34% [40.8%-<b>45.8%</b>]</td>
	<td>1,576</td>
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
	<td>47.73% [47.5%-48.0%]</td>
	<td>203,057</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>41.88% [<b>39.1%</b>-44.7%]</td>
	<td>1,225</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.67% [<b>39.7%</b>-47.6%]</td>
	<td>632</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.03% [<b>40.4%</b>-47.6%]</td>
	<td>754</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>43.38% [<b>40.5%</b>-46.3%]</td>
	<td>1,171</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>44.13% [<b>41.8%</b>-46.4%]</td>
	<td>1,874</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>41.88% [39.1%-<b>44.7%</b>]</td>
	<td>1,225</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.23% [43.1%-<b>45.4%</b>]</td>
	<td>7,441</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.95% [42.3%-<b>45.6%</b>]</td>
	<td>3,741</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.32% [42.9%-<b>45.8%</b>]</td>
	<td>4,630</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.52% [43.2%-<b>45.9%</b>]</td>
	<td>5,377</td>
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
	<td>47.73% [47.5%-47.9%]</td>
	<td>305,354</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>41.41% [<b>39.1%</b>-43.7%]</td>
	<td>1,857</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>42.01% [<b>39.2%</b>-44.8%]</td>
	<td>1,221</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>43.57% [<b>41.1%</b>-46.1%]</td>
	<td>1,586</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.33% [<b>41.8%</b>-46.8%]</td>
	<td>1,579</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>42.96% [<b>42.0%</b>-43.9%]</td>
	<td>10,652</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>41.41% [39.1%-<b>43.7%</b>]</td>
	<td>1,857</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>42.96% [42.0%-<b>43.9%</b>]</td>
	<td>10,652</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>42.01% [39.2%-<b>44.8%</b>]</td>
	<td>1,221</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.01% [43.1%-<b>44.9%</b>]</td>
	<td>12,299</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>44.01% [43.0%-<b>45.1%</b>]</td>
	<td>8,911</td>
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
	<td>49.14% [48.9%-49.4%]</td>
	<td>160,910</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.27% [<b>38.9%</b>-47.6%]</td>
	<td>520</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>40.35% [<b>39.1%</b>-41.6%]</td>
	<td>6,396</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.93% [<b>40.3%</b>-43.6%]</td>
	<td>3,494</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.02% [<b>40.6%</b>-47.4%]</td>
	<td>845</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.59% [<b>42.2%</b>-45.0%]</td>
	<td>5,104</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>40.35% [39.1%-<b>41.6%</b>]</td>
	<td>6,396</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.93% [40.3%-<b>43.6%</b>]</td>
	<td>3,494</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.59% [42.2%-<b>45.0%</b>]</td>
	<td>5,104</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.79% [43.5%-<b>46.1%</b>]</td>
	<td>5,818</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.44% [42.5%-<b>46.4%</b>]</td>
	<td>2,581</td>
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
	<td>48.25% [48.1%-48.4%]</td>
	<td>295,979</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>40.60% [<b>38.5%</b>-42.7%]</td>
	<td>2,111</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.61% [<b>38.9%</b>-46.3%]</td>
	<td>704</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.73% [<b>40.5%</b>-45.0%]</td>
	<td>1,954</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.50% [<b>40.5%</b>-48.5%]</td>
	<td>618</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-akali"></span> Akali</td>
	<td>43.57% [<b>41.7%</b>-45.4%]</td>
	<td>2,901</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>40.60% [38.5%-<b>42.7%</b>]</td>
	<td>2,111</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.73% [40.5%-<b>45.0%</b>]</td>
	<td>1,954</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-akali"></span> Akali</td>
	<td>43.57% [41.7%-<b>45.4%</b>]</td>
	<td>2,901</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.52% [43.4%-<b>45.6%</b>]</td>
	<td>8,462</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.63% [43.6%-<b>45.6%</b>]</td>
	<td>9,675</td>
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
	<td>47.78% [47.5%-48.0%]</td>
	<td>186,208</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>39.95% [<b>38.5%</b>-41.4%]</td>
	<td>4,386</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>42.37% [<b>38.7%</b>-46.0%]</td>
	<td>734</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>42.17% [<b>39.9%</b>-44.4%]</td>
	<td>1,923</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.43% [<b>40.0%</b>-46.8%]</td>
	<td>852</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.22% [<b>41.0%</b>-43.4%]</td>
	<td>6,485</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>39.95% [38.5%-<b>41.4%</b>]</td>
	<td>4,386</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.22% [41.0%-<b>43.4%</b>]</td>
	<td>6,485</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>42.17% [39.9%-<b>44.4%</b>]</td>
	<td>1,923</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.13% [41.5%-<b>44.8%</b>]</td>
	<td>3,529</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.22% [43.0%-<b>45.4%</b>]</td>
	<td>7,079</td>
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
	<td>46.36% [46.1%-46.6%]</td>
	<td>145,678</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.24% [<b>36.6%</b>-45.9%]</td>
	<td>451</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.05% [<b>38.7%</b>-45.4%]</td>
	<td>880</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>42.35% [<b>39.2%</b>-45.5%]</td>
	<td>980</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>43.86% [<b>39.5%</b>-48.2%]</td>
	<td>529</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>41.55% [<b>39.7%</b>-43.4%]</td>
	<td>2,756</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>41.55% [39.7%-<b>43.4%</b>]</td>
	<td>2,756</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.14% [40.4%-<b>43.8%</b>]</td>
	<td>3,405</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.74% [41.5%-<b>44.0%</b>]</td>
	<td>5,898</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>42.47% [40.6%-<b>44.4%</b>]</td>
	<td>2,743</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.32% [41.6%-<b>45.0%</b>]</td>
	<td>3,368</td>
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
	<td>49.34% [49.1%-49.6%]</td>
	<td>134,483</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>41.30% [<b>38.0%</b>-44.6%]</td>
	<td>874</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.19% [<b>38.4%</b>-48.0%]</td>
	<td>433</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-olaf"></span> Olaf</td>
	<td>43.58% [<b>39.6%</b>-47.6%]</td>
	<td>615</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>41.52% [<b>39.6%</b>-43.5%]</td>
	<td>2,587</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>43.35% [<b>40.9%</b>-45.8%]</td>
	<td>1,587</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>41.52% [39.6%-<b>43.5%</b>]</td>
	<td>2,587</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>41.30% [38.0%-<b>44.6%</b>]</td>
	<td>874</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>43.35% [40.9%-<b>45.8%</b>]</td>
	<td>1,587</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>43.95% [41.2%-<b>46.7%</b>]</td>
	<td>1,306</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.08% [43.2%-<b>46.9%</b>]</td>
	<td>2,875</td>
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
	<td>48.01% [47.7%-48.3%]</td>
	<td>112,438</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>38.26% [<b>36.8%</b>-39.7%]</td>
	<td>4,595</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>38.43% [<b>36.9%</b>-39.9%]</td>
	<td>4,210</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>42.25% [<b>37.1%</b>-47.4%]</td>
	<td>374</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.55% [<b>38.4%</b>-48.7%]</td>
	<td>372</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.03% [<b>40.0%</b>-44.0%]</td>
	<td>2,391</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>38.26% [36.8%-<b>39.7%</b>]</td>
	<td>4,595</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>38.43% [36.9%-<b>39.9%</b>]</td>
	<td>4,210</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.03% [40.0%-<b>44.0%</b>]</td>
	<td>2,391</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.40% [41.8%-<b>45.0%</b>]</td>
	<td>3,790</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.01% [43.4%-<b>46.6%</b>]</td>
	<td>4,068</td>
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
	<td>45.45% [45.1%-45.8%]</td>
	<td>79,147</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>40.67% [<b>36.3%</b>-45.0%]</td>
	<td>504</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>39.61% [<b>36.6%</b>-42.6%]</td>
	<td>1,088</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>39.33% [<b>37.2%</b>-41.5%]</td>
	<td>2,011</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.36% [<b>38.2%</b>-50.6%]</td>
	<td>257</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>43.12% [<b>38.7%</b>-47.6%]</td>
	<td>494</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>39.33% [37.2%-<b>41.5%</b>]</td>
	<td>2,011</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>39.61% [36.6%-<b>42.6%</b>]</td>
	<td>1,088</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>40.98% [39.0%-<b>43.0%</b>]</td>
	<td>2,367</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.99% [40.5%-<b>43.5%</b>]</td>
	<td>4,258</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>41.99% [39.3%-<b>44.7%</b>]</td>
	<td>1,324</td>
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
	<td>51.94% [51.5%-52.4%]</td>
	<td>50,830</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>41.09% [<b>35.0%</b>-47.2%]</td>
	<td>258</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.09% [<b>36.5%</b>-47.6%]</td>
	<td>316</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>43.16% [<b>36.7%</b>-49.6%]</td>
	<td>234</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-olaf"></span> Olaf</td>
	<td>42.07% [<b>37.2%</b>-46.9%]</td>
	<td>416</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>43.33% [<b>39.9%</b>-46.8%]</td>
	<td>817</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>43.33% [39.9%-<b>46.8%</b>]</td>
	<td>817</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-olaf"></span> Olaf</td>
	<td>42.07% [37.2%-<b>46.9%</b>]</td>
	<td>416</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>41.09% [35.0%-<b>47.2%</b>]</td>
	<td>258</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.94% [42.3%-<b>47.6%</b>]</td>
	<td>1,422</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.09% [36.5%-<b>47.6%</b>]</td>
	<td>316</td>
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
	<td>44.28% [44.1%-44.5%]</td>
	<td>289,751</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>38.29% [<b>35.1%</b>-41.5%]</td>
	<td>935</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>36.72% [<b>35.4%</b>-38.0%]</td>
	<td>5,667</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>39.53% [<b>37.3%</b>-41.8%]</td>
	<td>1,910</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>40.02% [<b>38.7%</b>-41.3%]</td>
	<td>5,570</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>39.82% [<b>38.8%</b>-40.9%]</td>
	<td>8,423</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>36.72% [35.4%-<b>38.0%</b>]</td>
	<td>5,667</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>39.82% [38.8%-<b>40.9%</b>]</td>
	<td>8,423</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>40.04% [38.8%-<b>41.3%</b>]</td>
	<td>5,999</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>40.02% [38.7%-<b>41.3%</b>]</td>
	<td>5,570</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>38.29% [35.1%-<b>41.5%</b>]</td>
	<td>935</td>
</tr>
</table>

</details>
### Jungle

<details>
<summary>Click to view</summary>

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
	<td>52.15% [52.0%-52.3%]</td>
	<td>651,429</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.35% [<b>45.5%</b>-47.2%]</td>
	<td>13,115</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>49.72% [<b>47.9%</b>-51.5%]</td>
	<td>3,023</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.96% [<b>48.1%</b>-49.8%]</td>
	<td>13,333</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>48.83% [<b>48.2%</b>-49.5%]</td>
	<td>23,244</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>49.85% [<b>48.3%</b>-51.4%]</td>
	<td>4,247</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.35% [45.5%-<b>47.2%</b>]</td>
	<td>13,115</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>48.83% [48.2%-<b>49.5%</b>]</td>
	<td>23,244</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.96% [48.1%-<b>49.8%</b>]</td>
	<td>13,333</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-graves"></span> Graves</td>
	<td>49.88% [49.4%-<b>50.4%</b>]</td>
	<td>37,585</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kha-zix"></span> Kha'Zix</td>
	<td>50.09% [49.5%-<b>50.7%</b>]</td>
	<td>24,436</td>
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
	<td>51.26% [51.1%-51.4%]</td>
	<td>352,462</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.20% [<b>44.8%</b>-49.6%]</td>
	<td>1,676</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.45% [<b>47.5%</b>-51.4%]</td>
	<td>2,540</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.67% [<b>47.8%</b>-49.5%]</td>
	<td>14,798</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>48.98% [<b>48.0%</b>-50.0%]</td>
	<td>10,298</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.22% [<b>48.0%</b>-50.4%]</td>
	<td>7,027</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.67% [47.8%-<b>49.5%</b>]</td>
	<td>14,798</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.20% [44.8%-<b>49.6%</b>]</td>
	<td>1,676</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.91% [48.0%-<b>49.8%</b>]</td>
	<td>12,867</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>48.98% [48.0%-<b>50.0%</b>]</td>
	<td>10,298</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.29% [48.4%-<b>50.2%</b>]</td>
	<td>12,822</td>
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
	<td>53.32% [53.2%-53.5%]</td>
	<td>348,782</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.44% [<b>45.9%</b>-50.9%]</td>
	<td>1,598</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>49.84% [<b>47.3%</b>-52.4%]</td>
	<td>1,543</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>50.41% [<b>49.1%</b>-51.7%]</td>
	<td>5,917</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.88% [<b>49.2%</b>-50.6%]</td>
	<td>19,926</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nunu---willump"></span> Nunu & Willump</td>
	<td>50.73% [<b>49.5%</b>-51.9%]</td>
	<td>7,101</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.88% [49.2%-<b>50.6%</b>]</td>
	<td>19,926</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.44% [45.9%-<b>50.9%</b>]</td>
	<td>1,598</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>50.41% [49.1%-<b>51.7%</b>]</td>
	<td>5,917</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nunu---willump"></span> Nunu & Willump</td>
	<td>50.73% [49.5%-<b>51.9%</b>]</td>
	<td>7,101</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>50.78% [49.6%-<b>52.0%</b>]</td>
	<td>7,027</td>
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
	<td>52.32% [52.2%-52.4%]</td>
	<td>710,602</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.37% [<b>46.5%</b>-48.2%]</td>
	<td>13,317</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.76% [<b>46.7%</b>-50.8%]</td>
	<td>2,426</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.45% [<b>46.8%</b>-48.1%]</td>
	<td>24,891</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>49.13% [<b>47.5%</b>-50.8%]</td>
	<td>3,731</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.44% [<b>47.6%</b>-51.2%]</td>
	<td>3,060</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.45% [46.8%-<b>48.1%</b>]</td>
	<td>24,891</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.37% [46.5%-<b>48.2%</b>]</td>
	<td>13,317</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.64% [48.1%-<b>49.2%</b>]</td>
	<td>29,289</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.41% [48.9%-<b>49.9%</b>]</td>
	<td>44,419</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>50.00% [49.3%-<b>50.7%</b>]</td>
	<td>20,703</td>
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
	<td>50.63% [50.5%-50.7%]</td>
	<td>892,758</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.28% [<b>44.5%</b>-46.0%]</td>
	<td>17,783</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.58% [<b>46.1%</b>-49.0%]</td>
	<td>4,660</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.64% [<b>47.1%</b>-50.2%]</td>
	<td>4,161</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.76% [<b>47.5%</b>-50.0%]</td>
	<td>6,513</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.04% [<b>47.6%</b>-48.5%]</td>
	<td>51,176</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.28% [44.5%-<b>46.0%</b>]</td>
	<td>17,783</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.04% [47.6%-<b>48.5%</b>]</td>
	<td>51,176</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.20% [47.7%-<b>48.7%</b>]</td>
	<td>39,293</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-graves"></span> Graves</td>
	<td>48.55% [48.1%-<b>49.0%</b>]</td>
	<td>45,550</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.58% [46.1%-<b>49.0%</b>]</td>
	<td>4,660</td>
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
	<td>50.44% [50.3%-50.5%]</td>
	<td>1,157,696</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.49% [<b>43.8%</b>-47.1%]</td>
	<td>3,667</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.70% [<b>46.0%</b>-47.4%]</td>
	<td>18,502</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.73% [<b>46.0%</b>-49.5%]</td>
	<td>3,266</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.71% [<b>46.0%</b>-47.4%]</td>
	<td>19,045</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.21% [<b>46.8%</b>-49.6%]</td>
	<td>5,256</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.49% [43.8%-<b>47.1%</b>]</td>
	<td>3,667</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.71% [46.0%-<b>47.4%</b>]</td>
	<td>19,045</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.70% [46.0%-<b>47.4%</b>]</td>
	<td>18,502</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.49% [48.1%-<b>48.9%</b>]</td>
	<td>61,779</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.37% [47.8%-<b>49.0%</b>]</td>
	<td>27,780</td>
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
	<td>50.05% [50.0%-50.1%]</td>
	<td>1,196,311</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.73% [<b>45.3%</b>-48.2%]</td>
	<td>4,562</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.47% [<b>45.8%</b>-47.1%]</td>
	<td>21,530</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.37% [<b>45.9%</b>-46.8%]</td>
	<td>43,453</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>47.10% [<b>45.9%</b>-48.3%]</td>
	<td>7,455</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.68% [<b>46.2%</b>-47.2%]</td>
	<td>37,614</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.37% [45.9%-<b>46.8%</b>]</td>
	<td>43,453</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.47% [45.8%-<b>47.1%</b>]</td>
	<td>21,530</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.68% [46.2%-<b>47.2%</b>]</td>
	<td>37,614</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>47.13% [46.3%-<b>48.0%</b>]</td>
	<td>14,249</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.73% [45.3%-<b>48.2%</b>]</td>
	<td>4,562</td>
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
	<td>519,450</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.43% [<b>44.0%</b>-48.8%]</td>
	<td>1,749</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.20% [<b>45.8%</b>-50.6%]</td>
	<td>1,664</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.69% [<b>46.0%</b>-49.4%]</td>
	<td>3,508</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.37% [<b>46.5%</b>-50.3%]</td>
	<td>2,816</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.62% [<b>46.6%</b>-48.6%]</td>
	<td>9,625</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.62% [46.6%-<b>48.6%</b>]</td>
	<td>9,625</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.43% [44.0%-<b>48.8%</b>]</td>
	<td>1,749</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.78% [46.7%-<b>48.9%</b>]</td>
	<td>8,141</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.52% [47.7%-<b>49.3%</b>]</td>
	<td>16,104</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.69% [46.0%-<b>49.4%</b>]</td>
	<td>3,508</td>
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
	<td>52.53% [52.4%-52.6%]</td>
	<td>1,070,692</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.10% [<b>45.6%</b>-48.6%]</td>
	<td>4,452</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.31% [<b>45.7%</b>-49.0%]</td>
	<td>3,640</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.64% [<b>48.1%</b>-49.1%]</td>
	<td>39,017</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>49.25% [<b>48.5%</b>-50.0%]</td>
	<td>19,802</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>50.32% [<b>49.1%</b>-51.6%]</td>
	<td>6,470</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.10% [45.6%-<b>48.6%</b>]</td>
	<td>4,452</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.31% [45.7%-<b>49.0%</b>]</td>
	<td>3,640</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.64% [48.1%-<b>49.1%</b>]</td>
	<td>39,017</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>49.25% [48.5%-<b>50.0%</b>]</td>
	<td>19,802</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>49.81% [49.1%-<b>50.5%</b>]</td>
	<td>20,134</td>
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
	<td>50.29% [50.2%-50.4%]</td>
	<td>761,388</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.66% [<b>43.6%</b>-47.8%]</td>
	<td>2,236</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.10% [<b>45.5%</b>-46.7%]</td>
	<td>26,010</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.92% [<b>46.4%</b>-47.4%]</td>
	<td>44,178</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.60% [<b>46.7%</b>-48.5%]</td>
	<td>11,427</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.83% [<b>46.7%</b>-51.0%]</td>
	<td>2,216</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.10% [45.5%-<b>46.7%</b>]</td>
	<td>26,010</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.92% [46.4%-<b>47.4%</b>]</td>
	<td>44,178</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.66% [43.6%-<b>47.8%</b>]</td>
	<td>2,236</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.60% [46.7%-<b>48.5%</b>]</td>
	<td>11,427</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.95% [47.0%-<b>48.9%</b>]</td>
	<td>10,846</td>
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
	<td>50.57% [50.4%-50.7%]</td>
	<td>408,521</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.73% [<b>44.6%</b>-48.8%]</td>
	<td>2,217</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.59% [<b>45.4%</b>-47.8%]</td>
	<td>7,390</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.65% [<b>45.8%</b>-47.5%]</td>
	<td>13,490</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.44% [<b>46.1%</b>-50.8%]</td>
	<td>1,792</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.87% [<b>46.2%</b>-51.5%]</td>
	<td>1,420</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.65% [45.8%-<b>47.5%</b>]</td>
	<td>13,490</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.59% [45.4%-<b>47.8%</b>]</td>
	<td>7,390</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.73% [44.6%-<b>48.8%</b>]</td>
	<td>2,217</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.40% [47.7%-<b>49.1%</b>]</td>
	<td>23,168</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-graves"></span> Graves</td>
	<td>48.54% [47.8%-<b>49.3%</b>]</td>
	<td>18,310</td>
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
	<td>52.56% [52.4%-52.7%]</td>
	<td>305,930</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.70% [<b>43.9%</b>-49.5%]</td>
	<td>1,274</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.31% [<b>45.4%</b>-51.3%]</td>
	<td>1,153</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.91% [<b>47.9%</b>-49.9%]</td>
	<td>10,271</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>49.00% [<b>48.1%</b>-49.9%]</td>
	<td>11,738</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.57% [<b>48.3%</b>-50.9%]</td>
	<td>5,917</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.70% [43.9%-<b>49.5%</b>]</td>
	<td>1,274</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.91% [47.9%-<b>49.9%</b>]</td>
	<td>10,271</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>49.00% [48.1%-<b>49.9%</b>]</td>
	<td>11,738</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>49.58% [48.3%-<b>50.9%</b>]</td>
	<td>6,152</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.57% [48.3%-<b>50.9%</b>]</td>
	<td>5,917</td>
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
	<td>49.99% [49.8%-50.2%]</td>
	<td>347,177</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.05% [<b>43.5%</b>-48.6%]</td>
	<td>1,518</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.94% [<b>45.2%</b>-50.7%]</td>
	<td>1,289</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.97% [<b>46.5%</b>-51.5%]</td>
	<td>1,595</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.90% [<b>46.6%</b>-49.2%]</td>
	<td>5,534</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>48.55% [<b>46.8%</b>-50.3%]</td>
	<td>3,137</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.05% [43.5%-<b>48.6%</b>]</td>
	<td>1,518</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.78% [46.9%-<b>48.7%</b>]</td>
	<td>12,732</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.83% [47.0%-<b>48.7%</b>]</td>
	<td>14,004</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.29% [47.4%-<b>49.2%</b>]</td>
	<td>11,926</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.90% [46.6%-<b>49.2%</b>]</td>
	<td>5,534</td>
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
	<td>53.90% [53.5%-54.3%]</td>
	<td>77,579</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>49.81% [<b>43.6%</b>-56.0%]</td>
	<td>257</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>51.37% [<b>45.1%</b>-57.6%]</td>
	<td>255</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>50.45% [<b>45.7%</b>-55.2%]</td>
	<td>440</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>51.51% [<b>45.7%</b>-57.3%]</td>
	<td>299</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.77% [<b>45.8%</b>-49.8%]</td>
	<td>2,449</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.77% [45.8%-<b>49.8%</b>]</td>
	<td>2,449</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>50.87% [49.2%-<b>52.5%</b>]</td>
	<td>3,731</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>50.16% [47.6%-<b>52.7%</b>]</td>
	<td>1,543</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>51.36% [49.8%-<b>52.9%</b>]</td>
	<td>4,161</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kha-zix"></span> Kha'Zix</td>
	<td>51.17% [49.0%-<b>53.3%</b>]</td>
	<td>2,216</td>
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
	<td>52.00% [51.9%-52.1%]</td>
	<td>629,907</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.57% [<b>42.9%</b>-46.2%]</td>
	<td>3,511</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.98% [<b>45.0%</b>-49.0%]</td>
	<td>2,565</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.57% [<b>47.2%</b>-50.0%]</td>
	<td>5,211</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.27% [<b>47.4%</b>-49.2%]</td>
	<td>12,094</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.32% [<b>47.4%</b>-49.2%]</td>
	<td>12,997</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.57% [42.9%-<b>46.2%</b>]</td>
	<td>3,511</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.98% [45.0%-<b>49.0%</b>]</td>
	<td>2,565</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.27% [47.4%-<b>49.2%</b>]</td>
	<td>12,094</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.32% [47.4%-<b>49.2%</b>]</td>
	<td>12,997</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.64% [48.0%-<b>49.3%</b>]</td>
	<td>23,155</td>
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
	<td>49.25% [49.1%-49.4%]</td>
	<td>619,340</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>45.03% [<b>44.3%</b>-45.8%]</td>
	<td>18,753</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.21% [<b>44.6%</b>-45.8%]</td>
	<td>30,633</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.85% [<b>44.9%</b>-46.8%]</td>
	<td>10,799</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.58% [<b>44.9%</b>-46.2%]</td>
	<td>23,023</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.47% [<b>45.0%</b>-47.9%]</td>
	<td>4,775</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>45.03% [44.3%-<b>45.8%</b>]</td>
	<td>18,753</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.21% [44.6%-<b>45.8%</b>]</td>
	<td>30,633</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.58% [44.9%-<b>46.2%</b>]</td>
	<td>23,023</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.85% [44.9%-<b>46.8%</b>]</td>
	<td>10,799</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>46.57% [45.6%-<b>47.5%</b>]</td>
	<td>10,418</td>
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
	<td>50.14% [50.0%-50.3%]</td>
	<td>334,178</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.84% [<b>44.6%</b>-51.1%]</td>
	<td>924</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.57% [<b>44.6%</b>-50.6%]</td>
	<td>1,112</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.49% [<b>44.8%</b>-46.2%]</td>
	<td>19,511</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.84% [<b>45.4%</b>-48.3%]</td>
	<td>4,492</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>47.75% [<b>45.4%</b>-50.1%]</td>
	<td>1,803</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.49% [44.8%-<b>46.2%</b>]</td>
	<td>19,511</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.19% [46.1%-<b>48.2%</b>]</td>
	<td>9,035</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.84% [45.4%-<b>48.3%</b>]</td>
	<td>4,492</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.22% [45.9%-<b>48.6%</b>]</td>
	<td>5,584</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.93% [46.8%-<b>49.0%</b>]</td>
	<td>8,200</td>
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
	<td>52.78% [52.4%-53.2%]</td>
	<td>66,822</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.49% [<b>42.7%</b>-54.3%]</td>
	<td>299</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>50.16% [<b>44.5%</b>-55.8%]</td>
	<td>313</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.01% [<b>45.0%</b>-49.1%]</td>
	<td>2,357</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-bel-veth"></span> Bel'Veth</td>
	<td>49.35% [<b>45.3%</b>-53.4%]</td>
	<td>612</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>49.81% [<b>45.4%</b>-54.2%]</td>
	<td>526</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.01% [45.0%-<b>49.1%</b>]</td>
	<td>2,357</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>48.94% [46.4%-<b>51.5%</b>]</td>
	<td>1,555</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>49.98% [48.2%-<b>51.7%</b>]</td>
	<td>3,281</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>49.29% [46.7%-<b>51.9%</b>]</td>
	<td>1,475</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>50.62% [48.4%-<b>52.8%</b>]</td>
	<td>2,106</td>
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
	<td>49.94% [49.8%-50.1%]</td>
	<td>338,237</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.97% [<b>43.7%</b>-46.3%]</td>
	<td>5,944</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.51% [<b>44.5%</b>-50.5%]</td>
	<td>1,103</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.70% [<b>44.9%</b>-50.5%]</td>
	<td>1,237</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>47.62% [<b>45.5%</b>-49.7%]</td>
	<td>2,312</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.13% [<b>45.7%</b>-48.5%]</td>
	<td>5,054</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.97% [43.7%-<b>46.3%</b>]</td>
	<td>5,944</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kha-zix"></span> Kha'Zix</td>
	<td>47.38% [46.5%-<b>48.2%</b>]</td>
	<td>13,616</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.77% [47.0%-<b>48.5%</b>]</td>
	<td>19,124</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.13% [45.7%-<b>48.5%</b>]</td>
	<td>5,054</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.91% [47.0%-<b>48.9%</b>]</td>
	<td>11,203</td>
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
	<td>50.69% [50.5%-50.8%]</td>
	<td>407,881</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.58% [<b>40.0%</b>-45.2%]</td>
	<td>1,421</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.19% [<b>44.3%</b>-50.1%]</td>
	<td>1,208</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>47.12% [<b>45.1%</b>-49.1%]</td>
	<td>2,451</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.52% [<b>45.3%</b>-47.7%]</td>
	<td>6,602</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.28% [<b>45.9%</b>-48.7%]</td>
	<td>5,167</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.58% [40.0%-<b>45.2%</b>]</td>
	<td>1,421</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.52% [45.3%-<b>47.7%</b>]</td>
	<td>6,602</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.57% [46.7%-<b>48.4%</b>]</td>
	<td>14,626</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>47.28% [45.9%-<b>48.7%</b>]</td>
	<td>5,167</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>48.33% [47.7%-<b>49.0%</b>]</td>
	<td>23,777</td>
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
	<td>51.95% [51.7%-52.2%]</td>
	<td>126,003</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.36% [<b>42.1%</b>-50.6%]</td>
	<td>550</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>48.38% [<b>44.2%</b>-52.5%]</td>
	<td>585</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.47% [<b>44.3%</b>-48.6%]</td>
	<td>2,152</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>49.50% [<b>45.1%</b>-53.9%]</td>
	<td>505</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.82% [<b>45.1%</b>-52.5%]</td>
	<td>721</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.47% [44.3%-<b>48.6%</b>]</td>
	<td>2,152</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.38% [45.8%-<b>49.0%</b>]</td>
	<td>3,981</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.36% [42.1%-<b>50.6%</b>]</td>
	<td>550</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.62% [48.5%-<b>50.8%</b>]</td>
	<td>7,462</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>49.70% [48.5%-<b>50.9%</b>]</td>
	<td>6,601</td>
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
	<td>51.07% [50.9%-51.2%]</td>
	<td>391,548</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.84% [<b>43.7%</b>-46.0%]</td>
	<td>7,827</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.82% [<b>44.1%</b>-49.5%]</td>
	<td>1,384</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.02% [<b>45.7%</b>-50.4%]</td>
	<td>1,839</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.73% [<b>46.9%</b>-48.6%]</td>
	<td>13,882</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.23% [<b>47.0%</b>-49.5%]</td>
	<td>6,398</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.84% [43.7%-<b>46.0%</b>]</td>
	<td>7,827</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.83% [47.2%-<b>48.5%</b>]</td>
	<td>23,102</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.73% [46.9%-<b>48.6%</b>]</td>
	<td>13,882</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.23% [47.0%-<b>49.5%</b>]</td>
	<td>6,398</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.82% [44.1%-<b>49.5%</b>]</td>
	<td>1,384</td>
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
	<td>48.76% [48.6%-48.9%]</td>
	<td>572,788</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.51% [<b>43.5%</b>-47.5%]</td>
	<td>2,384</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>44.64% [<b>44.1%</b>-45.2%]</td>
	<td>34,096</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.14% [<b>44.1%</b>-46.2%]</td>
	<td>9,323</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.20% [<b>44.9%</b>-49.5%]</td>
	<td>1,877</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.98% [<b>45.1%</b>-46.9%]</td>
	<td>12,391</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>44.64% [44.1%-<b>45.2%</b>]</td>
	<td>34,096</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.14% [44.1%-<b>46.2%</b>]</td>
	<td>9,323</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.95% [45.2%-<b>46.7%</b>]</td>
	<td>18,670</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.98% [45.1%-<b>46.9%</b>]</td>
	<td>12,391</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>46.06% [45.1%-<b>47.0%</b>]</td>
	<td>11,135</td>
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
	<td>48.83% [48.7%-48.9%]</td>
	<td>1,268,978</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.70% [<b>43.0%</b>-46.4%]</td>
	<td>3,445</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.77% [<b>44.0%</b>-47.5%]</td>
	<td>3,201</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.55% [<b>44.8%</b>-46.3%]</td>
	<td>16,458</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.84% [<b>45.3%</b>-46.3%]</td>
	<td>39,370</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.82% [<b>45.6%</b>-48.1%]</td>
	<td>6,348</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.55% [44.8%-<b>46.3%</b>]</td>
	<td>16,458</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.84% [45.3%-<b>46.3%</b>]</td>
	<td>39,370</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.70% [43.0%-<b>46.4%</b>]</td>
	<td>3,445</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.39% [46.0%-<b>46.8%</b>]</td>
	<td>69,433</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.29% [45.8%-<b>46.8%</b>]</td>
	<td>42,337</td>
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
	<td>50.02% [49.8%-50.2%]</td>
	<td>277,665</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.91% [<b>41.0%</b>-46.8%]</td>
	<td>1,191</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.75% [<b>43.6%</b>-49.9%]</td>
	<td>984</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.32% [<b>43.9%</b>-48.8%]</td>
	<td>1,684</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>47.90% [<b>44.4%</b>-51.4%]</td>
	<td>835</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>47.62% [<b>45.0%</b>-50.2%]</td>
	<td>1,489</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.91% [41.0%-<b>46.8%</b>]</td>
	<td>1,191</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.61% [45.8%-<b>47.4%</b>]</td>
	<td>15,874</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.96% [46.0%-<b>48.0%</b>]</td>
	<td>9,918</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.09% [46.1%-<b>48.1%</b>]</td>
	<td>9,985</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.82% [45.5%-<b>48.1%</b>]</td>
	<td>5,820</td>
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
	<td>48.77% [48.6%-49.0%]</td>
	<td>301,296</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.81% [<b>38.9%</b>-44.8%]</td>
	<td>1,117</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.02% [<b>43.6%</b>-48.5%]</td>
	<td>1,647</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>46.23% [<b>45.0%</b>-47.5%]</td>
	<td>6,268</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.04% [<b>45.0%</b>-47.1%]</td>
	<td>9,597</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.67% [<b>45.1%</b>-52.2%]</td>
	<td>787</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.81% [38.9%-<b>44.8%</b>]</td>
	<td>1,117</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.13% [45.4%-<b>46.9%</b>]</td>
	<td>17,022</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.04% [45.0%-<b>47.1%</b>]</td>
	<td>9,597</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.16% [45.2%-<b>47.1%</b>]</td>
	<td>10,288</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>46.23% [45.0%-<b>47.5%</b>]</td>
	<td>6,268</td>
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
	<td>49.90% [49.7%-50.1%]</td>
	<td>358,735</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.38% [<b>41.6%</b>-47.1%]</td>
	<td>1,307</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>44.16% [<b>43.3%</b>-45.0%]</td>
	<td>14,659</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.85% [<b>45.5%</b>-48.2%]</td>
	<td>5,398</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.71% [<b>45.9%</b>-51.5%]</td>
	<td>1,244</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>47.02% [<b>46.2%</b>-47.8%]</td>
	<td>16,449</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>44.16% [43.3%-<b>45.0%</b>]</td>
	<td>14,659</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.38% [41.6%-<b>47.1%</b>]</td>
	<td>1,307</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>47.02% [46.2%-<b>47.8%</b>]</td>
	<td>16,449</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.85% [45.5%-<b>48.2%</b>]</td>
	<td>5,398</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.33% [46.4%-<b>48.3%</b>]</td>
	<td>11,479</td>
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
	<td>49.63% [49.3%-49.9%]</td>
	<td>103,955</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.88% [<b>41.7%</b>-54.1%]</td>
	<td>259</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.63% [<b>43.1%</b>-54.1%]</td>
	<td>329</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.01% [<b>43.6%</b>-48.4%]</td>
	<td>1,693</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>48.69% [<b>43.8%</b>-53.6%]</td>
	<td>419</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.86% [<b>44.1%</b>-47.6%]</td>
	<td>3,238</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.86% [44.1%-<b>47.6%</b>]</td>
	<td>3,238</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.09% [44.5%-<b>47.7%</b>]</td>
	<td>3,730</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.74% [45.4%-<b>48.1%</b>]</td>
	<td>5,289</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.01% [43.6%-<b>48.4%</b>]</td>
	<td>1,693</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hecarim"></span> Hecarim</td>
	<td>47.67% [45.1%-<b>50.2%</b>]</td>
	<td>1,567</td>
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
	<td>48.81% [48.7%-48.9%]</td>
	<td>581,378</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.31% [<b>42.0%</b>-46.6%]</td>
	<td>1,925</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.70% [<b>43.0%</b>-46.4%]</td>
	<td>3,631</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.91% [<b>43.9%</b>-45.9%]</td>
	<td>10,009</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.98% [<b>43.9%</b>-46.0%]</td>
	<td>9,221</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.62% [<b>44.5%</b>-48.7%]</td>
	<td>2,263</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.91% [43.9%-<b>45.9%</b>]</td>
	<td>10,009</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.98% [43.9%-<b>46.0%</b>]</td>
	<td>9,221</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.70% [43.0%-<b>46.4%</b>]</td>
	<td>3,631</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.31% [42.0%-<b>46.6%</b>]</td>
	<td>1,925</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.19% [45.6%-<b>46.7%</b>]</td>
	<td>33,716</td>
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
	<td>49.51% [49.2%-49.8%]</td>
	<td>107,453</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>46.61% [<b>42.4%</b>-50.8%]</td>
	<td>575</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>46.07% [<b>42.8%</b>-49.4%]</td>
	<td>916</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>47.00% [<b>43.2%</b>-50.8%]</td>
	<td>700</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>49.49% [<b>43.7%</b>-55.3%]</td>
	<td>295</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.06% [<b>43.7%</b>-48.4%]</td>
	<td>1,789</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.65% [44.0%-<b>47.3%</b>]</td>
	<td>3,656</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>45.78% [43.9%-<b>47.7%</b>]</td>
	<td>2,831</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.00% [44.3%-<b>47.7%</b>]</td>
	<td>3,272</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.06% [43.7%-<b>48.4%</b>]</td>
	<td>1,789</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>47.10% [45.7%-<b>48.5%</b>]</td>
	<td>4,769</td>
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
	<td>50.66% [50.5%-50.8%]</td>
	<td>646,724</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.31% [<b>42.4%</b>-46.2%]</td>
	<td>2,688</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.74% [<b>42.7%</b>-46.8%]</td>
	<td>2,347</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>47.57% [<b>46.0%</b>-49.1%]</td>
	<td>4,015</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.67% [<b>46.0%</b>-47.3%]</td>
	<td>24,427</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.94% [<b>46.4%</b>-47.5%]</td>
	<td>36,873</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.31% [42.4%-<b>46.2%</b>]</td>
	<td>2,688</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.74% [42.7%-<b>46.8%</b>]</td>
	<td>2,347</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.67% [46.0%-<b>47.3%</b>]</td>
	<td>24,427</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.94% [46.4%-<b>47.5%</b>]</td>
	<td>36,873</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.65% [46.8%-<b>48.5%</b>]</td>
	<td>13,347</td>
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
	<td>50.49% [50.3%-50.7%]</td>
	<td>251,260</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.93% [<b>38.9%</b>-45.0%]</td>
	<td>1,028</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.96% [<b>42.4%</b>-49.5%]</td>
	<td>779</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.96% [<b>43.4%</b>-46.5%]</td>
	<td>3,930</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.21% [<b>43.6%</b>-46.8%]</td>
	<td>3,864</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.26% [<b>44.1%</b>-50.4%]</td>
	<td>1,005</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.93% [38.9%-<b>45.0%</b>]</td>
	<td>1,028</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.96% [43.4%-<b>46.5%</b>]</td>
	<td>3,930</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.21% [43.6%-<b>46.8%</b>]</td>
	<td>3,864</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.05% [44.9%-<b>47.2%</b>]</td>
	<td>7,604</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>46.60% [45.1%-<b>48.1%</b>]</td>
	<td>4,594</td>
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
	<td>48.75% [48.5%-49.0%]</td>
	<td>176,987</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.69% [<b>41.9%</b>-45.5%]</td>
	<td>2,980</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.22% [<b>41.9%</b>-48.5%]</td>
	<td>920</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.63% [<b>43.3%</b>-46.0%]</td>
	<td>5,198</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>46.83% [<b>43.5%</b>-50.2%]</td>
	<td>899</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>45.63% [<b>43.5%</b>-47.7%]</td>
	<td>2,268</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.69% [41.9%-<b>45.5%</b>]</td>
	<td>2,980</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.63% [43.3%-<b>46.0%</b>]</td>
	<td>5,198</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.92% [43.7%-<b>46.2%</b>]</td>
	<td>6,474</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>45.63% [43.5%-<b>47.7%</b>]</td>
	<td>2,268</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.77% [45.8%-<b>47.8%</b>]</td>
	<td>9,735</td>
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
	<td>50.00% [49.7%-50.3%]</td>
	<td>136,146</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.89% [<b>40.8%</b>-51.0%]</td>
	<td>377</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.60% [<b>41.8%</b>-51.4%]</td>
	<td>427</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.06% [<b>41.8%</b>-52.3%]</td>
	<td>357</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>50.83% [<b>44.4%</b>-57.3%]</td>
	<td>240</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>48.49% [<b>44.8%</b>-52.2%]</td>
	<td>730</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.36% [46.2%-<b>48.5%</b>]</td>
	<td>7,114</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.61% [45.9%-<b>49.3%</b>]</td>
	<td>3,438</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.57% [45.4%-<b>49.7%</b>]</td>
	<td>2,138</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.68% [45.5%-<b>49.8%</b>]</td>
	<td>2,135</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>48.70% [47.4%-<b>50.0%</b>]</td>
	<td>5,708</td>
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
	<td>48.04% [47.9%-48.2%]</td>
	<td>443,031</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>37.69% [<b>35.4%</b>-39.9%]</td>
	<td>1,852</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.41% [<b>41.7%</b>-43.1%]</td>
	<td>19,098</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.18% [<b>42.4%</b>-46.0%]</td>
	<td>3,099</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.34% [<b>42.9%</b>-47.8%]</td>
	<td>1,654</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>44.94% [<b>43.9%</b>-46.0%]</td>
	<td>9,616</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>37.69% [35.4%-<b>39.9%</b>]</td>
	<td>1,852</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.41% [41.7%-<b>43.1%</b>]</td>
	<td>19,098</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>45.07% [44.4%-<b>45.8%</b>]</td>
	<td>21,275</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>44.94% [43.9%-<b>46.0%</b>]</td>
	<td>9,616</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.18% [42.4%-<b>46.0%</b>]</td>
	<td>3,099</td>
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
	<td>50.52% [50.3%-50.8%]</td>
	<td>186,820</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.99% [<b>40.6%</b>-47.3%]</td>
	<td>882</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.87% [<b>41.7%</b>-50.0%]</td>
	<td>569</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.13% [<b>43.4%</b>-50.8%]</td>
	<td>732</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>44.81% [<b>43.5%</b>-46.1%]</td>
	<td>5,718</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.88% [<b>44.0%</b>-47.7%]</td>
	<td>2,949</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>44.81% [43.5%-<b>46.1%</b>]</td>
	<td>5,718</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.99% [40.6%-<b>47.3%</b>]</td>
	<td>882</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.88% [44.0%-<b>47.7%</b>]</td>
	<td>2,949</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.15% [44.4%-<b>47.9%</b>]</td>
	<td>3,146</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.99% [45.8%-<b>48.2%</b>]</td>
	<td>6,831</td>
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
	<td>47.58% [47.4%-47.8%]</td>
	<td>327,966</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.96% [<b>40.2%</b>-45.7%]</td>
	<td>1,313</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.48% [<b>41.6%</b>-47.3%]</td>
	<td>1,205</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.37% [<b>42.1%</b>-44.6%]</td>
	<td>6,041</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.09% [<b>42.6%</b>-45.5%]</td>
	<td>4,640</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>45.03% [<b>43.4%</b>-46.7%]</td>
	<td>3,569</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.37% [42.1%-<b>44.6%</b>]</td>
	<td>6,041</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.09% [42.6%-<b>45.5%</b>]</td>
	<td>4,640</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.96% [40.2%-<b>45.7%</b>]</td>
	<td>1,313</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.26% [44.5%-<b>46.0%</b>]</td>
	<td>18,030</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.22% [44.3%-<b>46.1%</b>]</td>
	<td>11,696</td>
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
	<td>49.25% [48.9%-49.6%]</td>
	<td>83,342</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.20% [<b>39.7%</b>-50.7%]</td>
	<td>323</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.39% [<b>41.5%</b>-51.3%]</td>
	<td>416</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>47.54% [<b>42.2%</b>-52.9%]</td>
	<td>345</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>46.74% [<b>42.4%</b>-51.1%]</td>
	<td>522</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.19% [<b>42.7%</b>-53.7%]</td>
	<td>332</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.91% [44.4%-<b>47.4%</b>]</td>
	<td>4,415</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.18% [42.8%-<b>47.6%</b>]</td>
	<td>1,702</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kha-zix"></span> Kha'Zix</td>
	<td>46.10% [44.3%-<b>47.9%</b>]</td>
	<td>3,163</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.92% [45.0%-<b>48.8%</b>]</td>
	<td>2,809</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>46.80% [44.7%-<b>48.9%</b>]</td>
	<td>2,310</td>
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
	<td>46.56% [46.4%-46.8%]</td>
	<td>244,015</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.43% [<b>40.0%</b>-46.8%]</td>
	<td>852</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.04% [<b>41.4%</b>-44.7%]</td>
	<td>3,687</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.38% [<b>41.7%</b>-45.1%]</td>
	<td>3,384</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.64% [<b>41.8%</b>-49.5%]</td>
	<td>677</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.83% [<b>42.7%</b>-45.0%]</td>
	<td>7,230</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>43.69% [42.8%-<b>44.6%</b>]</td>
	<td>11,948</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.04% [41.4%-<b>44.7%</b>]</td>
	<td>3,687</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.83% [42.7%-<b>45.0%</b>]</td>
	<td>7,230</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.38% [41.7%-<b>45.1%</b>]</td>
	<td>3,384</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>44.66% [43.6%-<b>45.8%</b>]</td>
	<td>8,199</td>
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
	<td>48.94% [48.8%-49.1%]</td>
	<td>375,357</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.34% [<b>40.9%</b>-45.8%]</td>
	<td>1,622</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.32% [<b>41.4%</b>-47.3%]</td>
	<td>1,144</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.49% [<b>41.7%</b>-43.3%]</td>
	<td>15,428</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.74% [<b>43.9%</b>-47.6%]</td>
	<td>2,873</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.06% [<b>44.8%</b>-47.3%]</td>
	<td>6,294</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.49% [41.7%-<b>43.3%</b>]</td>
	<td>15,428</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.34% [40.9%-<b>45.8%</b>]</td>
	<td>1,622</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>46.11% [45.1%-<b>47.1%</b>]</td>
	<td>10,591</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.32% [41.4%-<b>47.3%</b>]</td>
	<td>1,144</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>46.52% [45.8%-<b>47.3%</b>]</td>
	<td>17,499</td>
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
	<td>48.20% [48.0%-48.4%]</td>
	<td>238,329</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.81% [<b>40.7%</b>-47.0%]</td>
	<td>993</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.65% [<b>41.2%</b>-48.1%]</td>
	<td>851</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.74% [<b>43.0%</b>-50.5%]</td>
	<td>721</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.25% [<b>43.1%</b>-49.4%]</td>
	<td>973</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.65% [<b>43.2%</b>-46.1%]</td>
	<td>4,873</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.65% [43.2%-<b>46.1%</b>]</td>
	<td>4,873</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.48% [44.6%-<b>46.3%</b>]</td>
	<td>13,638</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.90% [44.9%-<b>46.9%</b>]</td>
	<td>9,213</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.81% [40.7%-<b>47.0%</b>]</td>
	<td>993</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.70% [44.3%-<b>47.1%</b>]</td>
	<td>5,074</td>
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
	<td>49.03% [48.8%-49.2%]</td>
	<td>208,250</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.90% [<b>39.1%</b>-46.7%]</td>
	<td>676</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.15% [<b>41.1%</b>-47.2%]</td>
	<td>1,060</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.62% [<b>41.8%</b>-45.5%]</td>
	<td>2,859</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.96% [<b>42.0%</b>-49.9%]</td>
	<td>631</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.76% [<b>43.7%</b>-49.8%]</td>
	<td>1,097</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.62% [41.8%-<b>45.5%</b>]</td>
	<td>2,859</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.90% [39.1%-<b>46.7%</b>]</td>
	<td>676</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>44.15% [41.1%-<b>47.2%</b>]</td>
	<td>1,060</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.60% [45.3%-<b>47.9%</b>]</td>
	<td>6,223</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.22% [44.5%-<b>47.9%</b>]</td>
	<td>3,544</td>
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
	<td>48.83% [48.4%-49.3%]</td>
	<td>54,507</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.69% [<b>39.6%</b>-51.8%]</td>
	<td>267</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>48.45% [<b>40.6%</b>-56.3%]</td>
	<td>161</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.18% [<b>40.8%</b>-51.6%]</td>
	<td>340</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.56% [<b>41.2%</b>-53.9%]</td>
	<td>246</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>47.88% [<b>41.7%</b>-54.1%]</td>
	<td>259</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>45.64% [43.8%-<b>47.5%</b>]</td>
	<td>2,947</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-graves"></span> Graves</td>
	<td>46.01% [44.0%-<b>48.0%</b>]</td>
	<td>2,543</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.07% [42.0%-<b>48.1%</b>]</td>
	<td>1,054</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nunu---willump"></span> Nunu & Willump</td>
	<td>45.13% [42.1%-<b>48.2%</b>]</td>
	<td>1,068</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.13% [43.9%-<b>48.3%</b>]</td>
	<td>2,079</td>
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
	<td>49.20% [48.9%-49.5%]</td>
	<td>90,671</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.58% [<b>38.2%</b>-51.0%]</td>
	<td>240</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.21% [<b>40.4%</b>-52.1%]</td>
	<td>290</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.86% [<b>41.0%</b>-50.7%]</td>
	<td>423</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>49.46% [<b>42.1%</b>-56.8%]</td>
	<td>186</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>46.92% [<b>42.2%</b>-51.6%]</td>
	<td>454</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.09% [43.1%-<b>47.1%</b>]</td>
	<td>2,446</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.87% [44.4%-<b>47.3%</b>]</td>
	<td>4,766</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.99% [43.9%-<b>48.1%</b>]</td>
	<td>2,222</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>45.68% [43.1%-<b>48.2%</b>]</td>
	<td>1,541</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.24% [45.4%-<b>49.1%</b>]</td>
	<td>2,803</td>
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
	<td>49.24% [48.9%-49.6%]</td>
	<td>99,708</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>40.51% [<b>34.1%</b>-46.9%]</td>
	<td>237</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.86% [<b>40.0%</b>-51.7%]</td>
	<td>290</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.07% [<b>40.2%</b>-45.9%]</td>
	<td>1,233</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.29% [<b>40.3%</b>-54.3%]</td>
	<td>203</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.05% [<b>41.3%</b>-50.8%]</td>
	<td>443</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.07% [40.2%-<b>45.9%</b>]</td>
	<td>1,233</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.73% [42.9%-<b>46.6%</b>]</td>
	<td>2,810</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>44.12% [41.4%-<b>46.8%</b>]</td>
	<td>1,344</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.09% [43.3%-<b>46.9%</b>]</td>
	<td>3,174</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>40.51% [34.1%-<b>46.9%</b>]</td>
	<td>237</td>
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
	<td>46.52% [46.4%-46.7%]</td>
	<td>369,122</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.60% [<b>38.1%</b>-45.1%]</td>
	<td>810</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>42.36% [<b>39.7%</b>-45.0%]</td>
	<td>1,414</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>41.92% [<b>40.9%</b>-43.0%]</td>
	<td>8,890</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>42.02% [<b>41.1%</b>-43.0%]</td>
	<td>10,886</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.93% [<b>41.2%</b>-48.6%]</td>
	<td>730</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>42.02% [41.1%-<b>43.0%</b>]</td>
	<td>10,886</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>41.92% [40.9%-<b>43.0%</b>]</td>
	<td>8,890</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.11% [42.0%-<b>44.2%</b>]</td>
	<td>7,810</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>43.64% [42.9%-<b>44.4%</b>]</td>
	<td>17,675</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.15% [41.8%-<b>44.5%</b>]</td>
	<td>5,124</td>
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
	<td>48.92% [48.6%-49.3%]</td>
	<td>90,292</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.14% [<b>38.6%</b>-49.7%]</td>
	<td>324</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.13% [<b>39.7%</b>-50.5%]</td>
	<td>339</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.04% [<b>40.5%</b>-49.6%]</td>
	<td>484</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.15% [<b>40.7%</b>-51.6%]</td>
	<td>338</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>44.64% [<b>42.2%</b>-47.1%]</td>
	<td>1,595</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>44.64% [42.2%-<b>47.1%</b>]</td>
	<td>1,595</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>46.25% [44.4%-<b>48.1%</b>]</td>
	<td>2,817</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.98% [45.5%-<b>48.4%</b>]</td>
	<td>4,666</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.75% [43.1%-<b>48.4%</b>]</td>
	<td>1,366</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.31% [43.9%-<b>48.7%</b>]</td>
	<td>1,747</td>
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
	<td>47.26% [47.0%-47.5%]</td>
	<td>140,064</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.61% [<b>39.2%</b>-50.0%]</td>
	<td>334</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.22% [<b>39.2%</b>-49.3%]</td>
	<td>389</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>43.42% [<b>39.6%</b>-47.2%]</td>
	<td>691</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>42.47% [<b>40.3%</b>-44.6%]</td>
	<td>2,117</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.42% [<b>40.9%</b>-49.9%]</td>
	<td>491</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>42.47% [40.3%-<b>44.6%</b>]</td>
	<td>2,117</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.27% [42.8%-<b>45.8%</b>]</td>
	<td>4,418</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.16% [44.1%-<b>46.3%</b>]</td>
	<td>8,060</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.03% [41.8%-<b>46.3%</b>]</td>
	<td>1,910</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kha-zix"></span> Kha'Zix</td>
	<td>44.93% [43.5%-<b>46.4%</b>]</td>
	<td>4,783</td>
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
	<td>49.04% [48.6%-49.4%]</td>
	<td>60,728</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>44.14% [<b>37.9%</b>-50.3%]</td>
	<td>256</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.98% [<b>38.1%</b>-51.9%]</td>
	<td>209</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.26% [<b>39.6%</b>-52.9%]</td>
	<td>227</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>47.04% [<b>41.3%</b>-52.8%]</td>
	<td>304</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>47.76% [<b>41.4%</b>-54.1%]</td>
	<td>245</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.30% [42.0%-<b>46.6%</b>]</td>
	<td>1,903</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.35% [44.2%-<b>48.5%</b>]</td>
	<td>2,192</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.85% [45.2%-<b>48.5%</b>]</td>
	<td>3,477</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.51% [42.2%-<b>48.8%</b>]</td>
	<td>903</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.97% [43.0%-<b>49.0%</b>]</td>
	<td>1,118</td>
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
	<td>49.70% [49.5%-49.9%]</td>
	<td>209,638</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.29% [<b>37.9%</b>-46.7%]</td>
	<td>506</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.57% [<b>38.0%</b>-45.2%]</td>
	<td>753</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>40.42% [<b>39.3%</b>-41.6%]</td>
	<td>7,155</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.67% [<b>41.3%</b>-48.0%]</td>
	<td>873</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.57% [<b>42.3%</b>-44.8%]</td>
	<td>6,568</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>40.42% [39.3%-<b>41.6%</b>]</td>
	<td>7,155</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.57% [42.3%-<b>44.8%</b>]</td>
	<td>6,568</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.57% [38.0%-<b>45.2%</b>]</td>
	<td>753</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.34% [42.4%-<b>46.3%</b>]</td>
	<td>2,652</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.29% [37.9%-<b>46.7%</b>]</td>
	<td>506</td>
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
	<td>48.55% [48.2%-48.9%]</td>
	<td>91,942</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>41.49% [<b>36.7%</b>-46.2%]</td>
	<td>429</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.19% [<b>37.0%</b>-49.4%]</td>
	<td>257</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.74% [<b>39.5%</b>-51.9%]</td>
	<td>258</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>43.64% [<b>40.1%</b>-47.2%]</td>
	<td>770</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.14% [<b>41.6%</b>-46.7%]</td>
	<td>1,493</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>41.49% [36.7%-<b>46.2%</b>]</td>
	<td>429</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.14% [41.6%-<b>46.7%</b>]</td>
	<td>1,493</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>43.64% [40.1%-<b>47.2%</b>]</td>
	<td>770</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.08% [42.8%-<b>47.3%</b>]</td>
	<td>1,932</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kha-zix"></span> Kha'Zix</td>
	<td>45.90% [44.2%-<b>47.6%</b>]</td>
	<td>3,403</td>
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
	<td>45.07% [44.8%-45.3%]</td>
	<td>166,873</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>38.43% [<b>34.6%</b>-42.3%]</td>
	<td>648</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>40.03% [<b>36.1%</b>-44.0%]</td>
	<td>612</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.36% [<b>36.6%</b>-46.1%]</td>
	<td>428</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>41.49% [<b>38.2%</b>-44.8%]</td>
	<td>911</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>41.23% [<b>38.6%</b>-43.8%]</td>
	<td>1,443</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>40.20% [38.9%-<b>41.5%</b>]</td>
	<td>6,012</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>40.81% [39.8%-<b>41.8%</b>]</td>
	<td>8,947</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>40.28% [38.7%-<b>41.9%</b>]</td>
	<td>3,880</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>38.43% [34.6%-<b>42.3%</b>]</td>
	<td>648</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>41.44% [39.6%-<b>43.2%</b>]</td>
	<td>3,024</td>
</tr>
</table>

</details>
### Mid

<details>
<summary>Click to view</summary>

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
	<td>52.69% [52.5%-52.9%]</td>
	<td>209,153</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>49.16% [<b>46.9%</b>-51.5%]</td>
	<td>1,902</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>50.22% [<b>47.5%</b>-52.9%]</td>
	<td>1,360</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>50.35% [<b>47.7%</b>-53.0%]</td>
	<td>1,440</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>50.16% [<b>47.8%</b>-52.5%]</td>
	<td>1,828</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>51.90% [<b>47.9%</b>-55.9%]</td>
	<td>630</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>49.91% [49.1%-<b>50.7%</b>]</td>
	<td>16,423</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>49.64% [48.4%-<b>50.9%</b>]</td>
	<td>6,694</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>50.33% [49.2%-<b>51.4%</b>]</td>
	<td>8,313</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>49.16% [46.9%-<b>51.5%</b>]</td>
	<td>1,902</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>50.34% [49.2%-<b>51.5%</b>]</td>
	<td>7,829</td>
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
	<td>52.30% [52.2%-52.4%]</td>
	<td>608,004</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.85% [<b>46.5%</b>-51.2%]</td>
	<td>1,869</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.55% [<b>47.0%</b>-50.1%]</td>
	<td>4,245</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.79% [<b>47.9%</b>-49.6%]</td>
	<td>13,717</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>50.12% [<b>48.1%</b>-52.1%]</td>
	<td>2,530</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.74% [<b>48.3%</b>-51.2%]</td>
	<td>4,950</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.79% [47.9%-<b>49.6%</b>]</td>
	<td>13,717</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>49.09% [48.4%-<b>49.8%</b>]</td>
	<td>22,222</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.55% [47.0%-<b>50.1%</b>]</td>
	<td>4,245</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>49.93% [49.3%-<b>50.6%</b>]</td>
	<td>22,969</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-katarina"></span> Katarina</td>
	<td>50.04% [49.4%-<b>50.7%</b>]</td>
	<td>21,286</td>
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
	<td>52.22% [52.1%-52.4%]</td>
	<td>520,734</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.71% [<b>44.3%</b>-49.2%]</td>
	<td>1,672</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.48% [<b>46.7%</b>-48.3%]</td>
	<td>16,636</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>48.85% [<b>46.9%</b>-50.8%]</td>
	<td>2,569</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>49.48% [<b>47.1%</b>-51.9%]</td>
	<td>1,724</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>49.70% [<b>47.5%</b>-51.9%]</td>
	<td>2,020</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.48% [46.7%-<b>48.3%</b>]</td>
	<td>16,636</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.71% [44.3%-<b>49.2%</b>]</td>
	<td>1,672</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-smolder"></span> Smolder</td>
	<td>48.54% [47.8%-<b>49.3%</b>]</td>
	<td>16,602</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>49.02% [48.0%-<b>50.0%</b>]</td>
	<td>9,796</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>48.85% [46.9%-<b>50.8%</b>]</td>
	<td>2,569</td>
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
	<td>50.64% [50.6%-50.7%]</td>
	<td>1,291,060</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.40% [<b>45.0%</b>-47.8%]</td>
	<td>5,056</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.72% [<b>46.0%</b>-49.4%]</td>
	<td>3,420</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.51% [<b>46.5%</b>-48.5%]</td>
	<td>10,815</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.16% [<b>46.7%</b>-47.6%]</td>
	<td>50,165</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.76% [<b>47.2%</b>-50.3%]</td>
	<td>3,997</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.16% [46.7%-<b>47.6%</b>]</td>
	<td>50,165</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.40% [45.0%-<b>47.8%</b>]</td>
	<td>5,056</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.51% [46.5%-<b>48.5%</b>]</td>
	<td>10,815</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.73% [48.2%-<b>49.2%</b>]</td>
	<td>38,724</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.72% [46.0%-<b>49.4%</b>]</td>
	<td>3,420</td>
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
	<td>51.78% [51.6%-51.9%]</td>
	<td>504,212</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.52% [<b>44.9%</b>-50.2%]</td>
	<td>1,414</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.17% [<b>45.7%</b>-48.6%]</td>
	<td>4,605</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>49.07% [<b>46.4%</b>-51.7%]</td>
	<td>1,447</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>48.10% [<b>47.0%</b>-49.2%]</td>
	<td>8,037</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>48.59% [<b>47.3%</b>-49.9%]</td>
	<td>6,265</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.17% [45.7%-<b>48.6%</b>]</td>
	<td>4,605</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>48.10% [47.0%-<b>49.2%</b>]</td>
	<td>8,037</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.74% [47.8%-<b>49.7%</b>]</td>
	<td>11,052</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>48.59% [47.3%-<b>49.9%</b>]</td>
	<td>6,265</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>49.09% [48.3%-<b>49.9%</b>]</td>
	<td>16,760</td>
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
	<td>50.61% [50.5%-50.7%]</td>
	<td>576,225</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>47.21% [<b>45.2%</b>-49.2%]</td>
	<td>2,453</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.94% [<b>45.4%</b>-50.5%]</td>
	<td>1,581</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>46.81% [<b>45.5%</b>-48.1%]</td>
	<td>5,751</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.06% [<b>46.2%</b>-47.9%]</td>
	<td>14,379</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>47.75% [<b>46.7%</b>-48.8%]</td>
	<td>8,433</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.06% [46.2%-<b>47.9%</b>]</td>
	<td>14,379</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>46.81% [45.5%-<b>48.1%</b>]</td>
	<td>5,751</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>47.84% [46.9%-<b>48.8%</b>]</td>
	<td>11,570</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>47.75% [46.7%-<b>48.8%</b>]</td>
	<td>8,433</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.22% [47.4%-<b>49.0%</b>]</td>
	<td>14,750</td>
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
	<td>51.55% [51.4%-51.7%]</td>
	<td>525,960</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.15% [<b>43.0%</b>-47.3%]</td>
	<td>2,206</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.22% [<b>45.3%</b>-49.2%]</td>
	<td>2,575</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.64% [<b>45.4%</b>-49.9%]</td>
	<td>2,038</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>48.13% [<b>46.1%</b>-50.1%]</td>
	<td>2,520</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.23% [<b>46.4%</b>-48.1%]</td>
	<td>13,759</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.15% [43.0%-<b>47.3%</b>]</td>
	<td>2,206</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.23% [46.4%-<b>48.1%</b>]</td>
	<td>13,759</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.74% [46.9%-<b>48.5%</b>]</td>
	<td>15,479</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>48.27% [47.8%-<b>48.8%</b>]</td>
	<td>41,602</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.22% [45.3%-<b>49.2%</b>]</td>
	<td>2,575</td>
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
	<td>50.91% [50.7%-51.1%]</td>
	<td>261,735</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.93% [<b>43.0%</b>-48.9%]</td>
	<td>1,143</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.88% [<b>44.9%</b>-48.8%]</td>
	<td>2,600</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jayce"></span> Jayce</td>
	<td>48.73% [<b>45.4%</b>-52.1%]</td>
	<td>903</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>46.50% [<b>45.7%</b>-47.3%]</td>
	<td>14,618</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>49.38% [<b>46.0%</b>-52.7%]</td>
	<td>883</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>46.50% [45.7%-<b>47.3%</b>]</td>
	<td>14,618</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.36% [46.0%-<b>48.7%</b>]</td>
	<td>5,596</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>48.03% [47.3%-<b>48.8%</b>]</td>
	<td>19,023</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.88% [44.9%-<b>48.8%</b>]</td>
	<td>2,600</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.93% [43.0%-<b>48.9%</b>]</td>
	<td>1,143</td>
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
	<td>48.64% [48.5%-48.7%]</td>
	<td>1,073,064</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.88% [<b>44.4%</b>-47.3%]</td>
	<td>4,658</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.93% [<b>44.6%</b>-47.3%]</td>
	<td>5,232</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.83% [<b>44.8%</b>-46.8%]</td>
	<td>9,639</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>46.05% [<b>44.9%</b>-47.2%]</td>
	<td>7,662</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>45.46% [<b>44.9%</b>-46.0%]</td>
	<td>36,048</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>45.46% [44.9%-<b>46.0%</b>]</td>
	<td>36,048</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.83% [44.8%-<b>46.8%</b>]</td>
	<td>9,639</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>46.18% [45.5%-<b>46.9%</b>]</td>
	<td>20,823</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.37% [45.8%-<b>46.9%</b>]</td>
	<td>34,053</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.26% [45.4%-<b>47.1%</b>]</td>
	<td>12,868</td>
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
	<td>51.05% [50.7%-51.4%]</td>
	<td>100,195</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>44.57% [<b>41.2%</b>-47.9%]</td>
	<td>884</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>49.04% [<b>44.4%</b>-53.6%]</td>
	<td>471</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>50.34% [<b>44.5%</b>-56.2%]</td>
	<td>290</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>48.76% [<b>45.5%</b>-52.0%]</td>
	<td>968</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>49.87% [<b>46.3%</b>-53.4%]</td>
	<td>786</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>44.57% [41.2%-<b>47.9%</b>]</td>
	<td>884</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>49.12% [48.0%-<b>50.3%</b>]</td>
	<td>7,461</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.65% [46.9%-<b>50.4%</b>]</td>
	<td>3,408</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>49.08% [47.6%-<b>50.5%</b>]</td>
	<td>4,817</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.73% [46.8%-<b>50.7%</b>]</td>
	<td>2,641</td>
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
	<td>49.74% [49.6%-49.9%]</td>
	<td>812,080</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.81% [<b>44.3%</b>-45.4%]</td>
	<td>32,170</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.03% [<b>44.4%</b>-45.7%]</td>
	<td>25,328</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.62% [<b>44.6%</b>-48.6%]</td>
	<td>2,486</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.47% [<b>44.7%</b>-48.2%]</td>
	<td>3,217</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.04% [<b>44.9%</b>-47.2%]</td>
	<td>7,480</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.81% [44.3%-<b>45.4%</b>]</td>
	<td>32,170</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.03% [44.4%-<b>45.7%</b>]</td>
	<td>25,328</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.83% [45.1%-<b>46.5%</b>]</td>
	<td>20,285</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.04% [44.9%-<b>47.2%</b>]</td>
	<td>7,480</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>46.71% [46.1%-<b>47.3%</b>]</td>
	<td>25,279</td>
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
	<td>50.27% [50.2%-50.4%]</td>
	<td>1,245,631</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>39.53% [<b>38.2%</b>-40.8%]</td>
	<td>5,773</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.73% [<b>44.3%</b>-47.2%]</td>
	<td>4,885</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>45.46% [<b>44.5%</b>-46.4%]</td>
	<td>10,274</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.24% [<b>44.7%</b>-45.8%]</td>
	<td>30,186</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.23% [<b>45.6%</b>-46.9%]</td>
	<td>22,184</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>39.53% [38.2%-<b>40.8%</b>]</td>
	<td>5,773</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.24% [44.7%-<b>45.8%</b>]</td>
	<td>30,186</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>45.46% [44.5%-<b>46.4%</b>]</td>
	<td>10,274</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.04% [45.6%-<b>46.4%</b>]</td>
	<td>59,325</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>46.24% [45.7%-<b>46.7%</b>]</td>
	<td>38,634</td>
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
	<td>50.45% [50.3%-50.6%]</td>
	<td>266,516</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.28% [<b>43.5%</b>-51.1%]</td>
	<td>681</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.16% [<b>43.6%</b>-48.7%]</td>
	<td>1,486</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.97% [<b>44.0%</b>-47.9%]</td>
	<td>2,604</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>46.67% [<b>44.0%</b>-49.3%]</td>
	<td>1,427</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.18% [<b>44.1%</b>-52.2%]</td>
	<td>604</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.42% [45.3%-<b>47.6%</b>]</td>
	<td>7,692</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.97% [44.0%-<b>47.9%</b>]</td>
	<td>2,604</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.61% [45.1%-<b>48.1%</b>]</td>
	<td>4,233</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>47.14% [45.9%-<b>48.4%</b>]</td>
	<td>6,686</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.97% [45.2%-<b>48.7%</b>]</td>
	<td>3,302</td>
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
	<td>50.14% [50.0%-50.3%]</td>
	<td>473,019</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.56% [<b>43.2%</b>-47.9%]</td>
	<td>1,769</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.22% [<b>43.4%</b>-49.0%]</td>
	<td>1,255</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.03% [<b>44.5%</b>-47.6%]</td>
	<td>4,245</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.74% [<b>45.9%</b>-47.6%]</td>
	<td>12,739</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.75% [<b>46.7%</b>-48.8%]</td>
	<td>8,661</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.03% [44.5%-<b>47.6%</b>]</td>
	<td>4,245</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.74% [45.9%-<b>47.6%</b>]</td>
	<td>12,739</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.56% [43.2%-<b>47.9%</b>]</td>
	<td>1,769</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.75% [46.7%-<b>48.8%</b>]</td>
	<td>8,661</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>48.43% [47.9%-<b>48.9%</b>]</td>
	<td>39,134</td>
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
	<td>50.98% [50.8%-51.2%]</td>
	<td>284,872</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>45.36% [<b>43.4%</b>-47.4%]</td>
	<td>2,467</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.94% [<b>43.4%</b>-50.5%]</td>
	<td>784</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.44% [<b>44.1%</b>-50.8%]</td>
	<td>900</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.08% [<b>44.4%</b>-51.7%]</td>
	<td>757</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.39% [<b>46.0%</b>-48.7%]</td>
	<td>5,495</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>45.36% [43.4%-<b>47.4%</b>]</td>
	<td>2,467</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>47.39% [46.0%-<b>48.7%</b>]</td>
	<td>5,495</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>47.89% [46.3%-<b>49.5%</b>]</td>
	<td>4,024</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-akali"></span> Akali</td>
	<td>48.50% [47.5%-<b>49.5%</b>]</td>
	<td>9,677</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>48.87% [48.1%-<b>49.6%</b>]</td>
	<td>17,145</td>
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
	<td>49.45% [49.4%-49.5%]</td>
	<td>1,010,781</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.14% [<b>42.5%</b>-45.8%]</td>
	<td>3,473</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.54% [<b>43.3%</b>-45.7%]</td>
	<td>6,818</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.39% [<b>43.8%</b>-44.9%]</td>
	<td>33,266</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.43% [<b>44.4%</b>-46.5%]</td>
	<td>9,395</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.72% [<b>44.5%</b>-47.0%]</td>
	<td>6,439</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.39% [43.8%-<b>44.9%</b>]</td>
	<td>33,266</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.54% [43.3%-<b>45.7%</b>]</td>
	<td>6,818</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.14% [42.5%-<b>45.8%</b>]</td>
	<td>3,473</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>45.43% [44.4%-<b>46.5%</b>]</td>
	<td>9,395</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.95% [45.2%-<b>46.7%</b>]</td>
	<td>15,882</td>
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
	<td>51.24% [51.0%-51.4%]</td>
	<td>229,389</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.54% [<b>41.9%</b>-49.2%]</td>
	<td>740</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>45.42% [<b>43.3%</b>-47.6%]</td>
	<td>2,173</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.64% [<b>44.8%</b>-48.5%]</td>
	<td>2,933</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.07% [<b>44.9%</b>-47.3%]</td>
	<td>7,026</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.81% [<b>45.0%</b>-50.6%]</td>
	<td>1,303</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.07% [44.9%-<b>47.3%</b>]</td>
	<td>7,026</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>45.42% [43.3%-<b>47.6%</b>]</td>
	<td>2,173</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.64% [44.8%-<b>48.5%</b>]</td>
	<td>2,933</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.49% [46.4%-<b>48.6%</b>]</td>
	<td>7,836</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.58% [46.3%-<b>48.8%</b>]</td>
	<td>6,435</td>
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
	<td>51.64% [51.5%-51.8%]</td>
	<td>488,848</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.70% [<b>42.0%</b>-47.4%]</td>
	<td>1,320</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.19% [<b>43.2%</b>-49.1%]</td>
	<td>1,143</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.81% [<b>44.2%</b>-49.5%]</td>
	<td>1,425</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.13% [<b>44.8%</b>-47.5%]</td>
	<td>5,441</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.67% [<b>44.9%</b>-46.4%]</td>
	<td>16,723</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.67% [44.9%-<b>46.4%</b>]</td>
	<td>16,723</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.70% [42.0%-<b>47.4%</b>]</td>
	<td>1,320</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.13% [44.8%-<b>47.5%</b>]</td>
	<td>5,441</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>46.98% [45.4%-<b>48.6%</b>]</td>
	<td>3,938</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>47.89% [47.1%-<b>48.7%</b>]</td>
	<td>15,733</td>
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
	<td>49.18% [49.0%-49.4%]</td>
	<td>314,464</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>44.11% [<b>42.8%</b>-45.4%]</td>
	<td>5,538</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.14% [<b>42.8%</b>-49.5%]</td>
	<td>893</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.29% [<b>42.9%</b>-47.6%]</td>
	<td>1,793</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.87% [<b>43.0%</b>-46.7%]</td>
	<td>2,806</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.53% [<b>43.0%</b>-50.0%]</td>
	<td>806</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>44.11% [42.8%-<b>45.4%</b>]</td>
	<td>5,538</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.13% [44.0%-<b>46.2%</b>]</td>
	<td>8,382</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.87% [43.0%-<b>46.7%</b>]</td>
	<td>2,806</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>46.09% [44.9%-<b>47.3%</b>]</td>
	<td>7,275</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.77% [44.2%-<b>47.3%</b>]</td>
	<td>4,136</td>
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
	<td>52.47% [52.2%-52.7%]</td>
	<td>151,531</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.02% [<b>41.4%</b>-50.6%]</td>
	<td>465</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.59% [<b>42.7%</b>-50.5%]</td>
	<td>646</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.51% [<b>43.8%</b>-51.2%]</td>
	<td>724</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>45.90% [<b>43.9%</b>-47.9%]</td>
	<td>2,464</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.94% [<b>44.9%</b>-53.0%]</td>
	<td>615</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>45.90% [43.9%-<b>47.9%</b>]</td>
	<td>2,464</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>47.83% [46.8%-<b>48.9%</b>]</td>
	<td>9,316</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>47.74% [46.2%-<b>49.3%</b>]</td>
	<td>4,349</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.59% [42.7%-<b>50.5%</b>]</td>
	<td>646</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.02% [41.4%-<b>50.6%</b>]</td>
	<td>465</td>
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
	<td>50.81% [50.5%-51.1%]</td>
	<td>117,289</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.79% [<b>41.2%</b>-48.4%]</td>
	<td>748</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>45.64% [<b>42.6%</b>-48.7%]</td>
	<td>1,089</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>46.92% [<b>43.7%</b>-50.2%]</td>
	<td>942</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jayce"></span> Jayce</td>
	<td>48.88% [<b>43.9%</b>-53.9%]</td>
	<td>401</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>49.87% [<b>44.7%</b>-55.0%]</td>
	<td>379</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.79% [41.2%-<b>48.4%</b>]</td>
	<td>748</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>45.64% [42.6%-<b>48.7%</b>]</td>
	<td>1,089</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>46.81% [44.8%-<b>48.8%</b>]</td>
	<td>2,480</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>47.85% [46.2%-<b>49.5%</b>]</td>
	<td>3,718</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.03% [45.9%-<b>50.2%</b>]</td>
	<td>2,203</td>
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
	<td>49.37% [49.2%-49.5%]</td>
	<td>535,746</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>42.48% [<b>41.2%</b>-43.8%]</td>
	<td>5,617</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.22% [<b>42.5%</b>-44.0%]</td>
	<td>18,070</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.60% [<b>42.8%</b>-48.4%]</td>
	<td>1,250</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.09% [<b>43.7%</b>-48.4%]</td>
	<td>1,805</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.52% [<b>43.8%</b>-49.2%]</td>
	<td>1,363</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>42.48% [41.2%-<b>43.8%</b>]</td>
	<td>5,617</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.22% [42.5%-<b>44.0%</b>]</td>
	<td>18,070</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>45.00% [44.3%-<b>45.7%</b>]</td>
	<td>22,268</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.54% [45.8%-<b>47.3%</b>]</td>
	<td>19,293</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.58% [45.6%-<b>47.6%</b>]</td>
	<td>10,450</td>
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
	<td>50.14% [49.9%-50.3%]</td>
	<td>238,514</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.91% [<b>41.8%</b>-44.0%]</td>
	<td>7,874</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.20% [<b>42.4%</b>-46.0%]</td>
	<td>3,154</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.63% [<b>43.0%</b>-50.3%]</td>
	<td>757</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.09% [<b>43.0%</b>-47.1%]</td>
	<td>2,371</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.30% [<b>43.7%</b>-46.9%]</td>
	<td>4,068</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.91% [41.8%-<b>44.0%</b>]</td>
	<td>7,874</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.20% [42.4%-<b>46.0%</b>]</td>
	<td>3,154</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.30% [43.7%-<b>46.9%</b>]</td>
	<td>4,068</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>45.09% [43.0%-<b>47.1%</b>]</td>
	<td>2,371</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.39% [45.1%-<b>47.7%</b>]</td>
	<td>6,185</td>
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
	<td>49.23% [49.1%-49.4%]</td>
	<td>429,681</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.05% [<b>41.9%</b>-48.2%]</td>
	<td>990</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.96% [<b>42.3%</b>-47.6%]</td>
	<td>1,370</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.31% [<b>44.6%</b>-48.1%]</td>
	<td>3,211</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.78% [<b>44.6%</b>-47.0%]</td>
	<td>6,879</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.07% [<b>45.4%</b>-50.8%]</td>
	<td>1,375</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.78% [44.6%-<b>47.0%</b>]</td>
	<td>6,879</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.96% [42.3%-<b>47.6%</b>]</td>
	<td>1,370</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.84% [46.0%-<b>47.7%</b>]</td>
	<td>13,393</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>47.20% [46.5%-<b>47.9%</b>]</td>
	<td>19,458</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.31% [44.6%-<b>48.1%</b>]</td>
	<td>3,211</td>
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
	<td>53.92% [53.5%-54.3%]</td>
	<td>65,199</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.71% [<b>41.5%</b>-49.9%]</td>
	<td>571</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.54% [<b>42.1%</b>-55.0%]</td>
	<td>239</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jayce"></span> Jayce</td>
	<td>50.00% [<b>43.1%</b>-56.9%]</td>
	<td>212</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.66% [<b>43.8%</b>-55.5%]</td>
	<td>290</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>49.33% [<b>44.1%</b>-54.5%]</td>
	<td>371</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.71% [41.5%-<b>49.9%</b>]</td>
	<td>571</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>47.95% [44.2%-<b>51.7%</b>]</td>
	<td>707</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>49.48% [45.9%-<b>53.1%</b>]</td>
	<td>776</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>51.15% [48.8%-<b>53.5%</b>]</td>
	<td>1,869</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vladimir"></span> Vladimir</td>
	<td>50.00% [46.1%-<b>53.9%</b>]</td>
	<td>674</td>
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
	<td>52.36% [51.9%-52.8%]</td>
	<td>56,513</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>47.62% [<b>41.6%</b>-53.7%]</td>
	<td>273</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.82% [<b>42.1%</b>-51.6%]</td>
	<td>440</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.81% [<b>42.2%</b>-53.4%]</td>
	<td>320</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.14% [<b>42.9%</b>-49.4%]</td>
	<td>945</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-neeko"></span> Neeko</td>
	<td>50.20% [<b>43.9%</b>-56.5%]</td>
	<td>255</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.14% [42.9%-<b>49.4%</b>]</td>
	<td>945</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.47% [46.3%-<b>50.7%</b>]</td>
	<td>2,096</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.70% [46.1%-<b>51.3%</b>]</td>
	<td>1,503</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.82% [42.1%-<b>51.6%</b>]</td>
	<td>440</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>50.43% [48.8%-<b>52.1%</b>]</td>
	<td>3,680</td>
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
	<td>49.42% [49.3%-49.6%]</td>
	<td>350,725</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>41.13% [<b>38.6%</b>-43.6%]</td>
	<td>1,556</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>44.16% [<b>42.0%</b>-46.3%]</td>
	<td>2,156</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.26% [<b>42.8%</b>-47.7%]</td>
	<td>1,626</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.11% [<b>43.2%</b>-45.0%]</td>
	<td>12,353</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.20% [<b>43.6%</b>-46.8%]</td>
	<td>3,781</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>41.13% [38.6%-<b>43.6%</b>]</td>
	<td>1,556</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.11% [43.2%-<b>45.0%</b>]</td>
	<td>12,353</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>44.16% [42.0%-<b>46.3%</b>]</td>
	<td>2,156</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.20% [43.6%-<b>46.8%</b>]</td>
	<td>3,781</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lissandra"></span> Lissandra</td>
	<td>45.59% [44.4%-<b>46.8%</b>]</td>
	<td>6,535</td>
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
	<td>48.31% [48.1%-48.5%]</td>
	<td>246,440</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.58% [<b>41.3%</b>-47.9%]</td>
	<td>895</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.42% [<b>41.8%</b>-49.0%]</td>
	<td>775</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-neeko"></span> Neeko</td>
	<td>44.47% [<b>42.0%</b>-47.0%]</td>
	<td>1,563</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.13% [<b>42.6%</b>-47.6%]</td>
	<td>1,571</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.73% [<b>43.6%</b>-45.8%]</td>
	<td>7,914</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.73% [43.6%-<b>45.8%</b>]</td>
	<td>7,914</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>45.75% [44.6%-<b>46.9%</b>]</td>
	<td>7,017</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-neeko"></span> Neeko</td>
	<td>44.47% [42.0%-<b>47.0%</b>]</td>
	<td>1,563</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>45.86% [44.6%-<b>47.1%</b>]</td>
	<td>6,385</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>46.25% [45.2%-<b>47.3%</b>]</td>
	<td>8,512</td>
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
	<td>51.25% [51.1%-51.4%]</td>
	<td>333,383</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.92% [<b>40.8%</b>-47.0%]</td>
	<td>1,011</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.70% [<b>41.8%</b>-47.6%]</td>
	<td>1,188</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.72% [<b>43.8%</b>-49.7%]</td>
	<td>1,145</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>47.46% [<b>44.6%</b>-50.3%]</td>
	<td>1,201</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.15% [<b>45.2%</b>-47.1%]</td>
	<td>10,100</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.92% [40.8%-<b>47.0%</b>]</td>
	<td>1,011</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.15% [45.2%-<b>47.1%</b>]</td>
	<td>10,100</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.70% [41.8%-<b>47.6%</b>]</td>
	<td>1,188</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.07% [47.2%-<b>49.0%</b>]</td>
	<td>12,167</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>48.59% [47.6%-<b>49.6%</b>]</td>
	<td>9,239</td>
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
	<td>51.62% [51.4%-51.9%]</td>
	<td>147,887</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.31% [<b>37.9%</b>-46.8%]</td>
	<td>494</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.17% [<b>41.8%</b>-50.6%]</td>
	<td>509</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.95% [<b>42.7%</b>-53.2%]</td>
	<td>365</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>49.08% [<b>45.0%</b>-53.2%]</td>
	<td>595</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.05% [<b>45.5%</b>-48.6%]</td>
	<td>4,225</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.31% [37.9%-<b>46.8%</b>]</td>
	<td>494</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.15% [45.7%-<b>48.6%</b>]</td>
	<td>5,050</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>47.05% [45.5%-<b>48.6%</b>]</td>
	<td>4,225</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.75% [45.7%-<b>49.8%</b>]</td>
	<td>2,486</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>48.56% [47.2%-<b>49.9%</b>]</td>
	<td>5,620</td>
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
	<td>50.54% [50.4%-50.7%]</td>
	<td>278,288</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.90% [<b>41.5%</b>-48.3%]</td>
	<td>873</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.50% [<b>41.7%</b>-47.3%]</td>
	<td>1,263</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.73% [<b>41.7%</b>-45.7%]</td>
	<td>2,447</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.08% [<b>43.5%</b>-48.6%]</td>
	<td>1,517</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.98% [<b>43.9%</b>-50.0%]</td>
	<td>1,075</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.73% [41.7%-<b>45.7%</b>]</td>
	<td>2,447</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.50% [41.7%-<b>47.3%</b>]</td>
	<td>1,263</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>46.40% [45.3%-<b>47.5%</b>]</td>
	<td>7,998</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.90% [41.5%-<b>48.3%</b>]</td>
	<td>873</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.16% [46.0%-<b>48.4%</b>]</td>
	<td>6,968</td>
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
	<td>50.86% [50.6%-51.1%]</td>
	<td>209,024</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.15% [<b>41.4%</b>-48.9%]</td>
	<td>691</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.93% [<b>41.6%</b>-50.2%]</td>
	<td>540</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>48.18% [<b>44.4%</b>-52.0%]</td>
	<td>687</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.36% [<b>44.6%</b>-52.1%]</td>
	<td>703</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>49.05% [<b>45.1%</b>-53.0%]</td>
	<td>632</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.95% [45.5%-<b>48.4%</b>]</td>
	<td>4,635</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-akali"></span> Akali</td>
	<td>47.56% [46.5%-<b>48.7%</b>]</td>
	<td>8,205</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.15% [41.4%-<b>48.9%</b>]</td>
	<td>691</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>48.81% [47.9%-<b>49.7%</b>]</td>
	<td>13,021</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>47.57% [45.3%-<b>49.9%</b>]</td>
	<td>1,873</td>
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
	<td>52.96% [52.6%-53.3%]</td>
	<td>73,676</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.35% [<b>38.0%</b>-50.7%]</td>
	<td>248</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>46.38% [<b>41.4%</b>-51.4%]</td>
	<td>401</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.74% [<b>41.8%</b>-53.6%]</td>
	<td>287</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.53% [<b>44.8%</b>-48.3%]</td>
	<td>3,213</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>48.42% [<b>44.8%</b>-52.0%]</td>
	<td>760</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.53% [44.8%-<b>48.3%</b>]</td>
	<td>3,213</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>47.93% [45.8%-<b>50.0%</b>]</td>
	<td>2,274</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>48.08% [46.1%-<b>50.1%</b>]</td>
	<td>2,498</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.35% [38.0%-<b>50.7%</b>]</td>
	<td>248</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>48.80% [46.8%-<b>50.8%</b>]</td>
	<td>2,449</td>
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
	<td>48.34% [48.2%-48.5%]</td>
	<td>612,973</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>42.10% [<b>40.4%</b>-43.8%]</td>
	<td>3,563</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.29% [<b>41.4%</b>-43.2%]</td>
	<td>11,654</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.76% [<b>41.6%</b>-45.9%]</td>
	<td>2,210</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.25% [<b>41.7%</b>-44.8%]</td>
	<td>3,891</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.30% [<b>43.4%</b>-47.2%]</td>
	<td>2,821</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.29% [41.4%-<b>43.2%</b>]</td>
	<td>11,654</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>42.10% [40.4%-<b>43.8%</b>]</td>
	<td>3,563</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.25% [41.7%-<b>44.8%</b>]</td>
	<td>3,891</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.06% [44.3%-<b>45.8%</b>]</td>
	<td>18,037</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.76% [41.6%-<b>45.9%</b>]</td>
	<td>2,210</td>
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
	<td>49.49% [49.3%-49.7%]</td>
	<td>255,242</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.09% [<b>40.1%</b>-46.1%]</td>
	<td>1,107</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.26% [<b>41.2%</b>-45.3%]</td>
	<td>2,263</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.29% [<b>42.9%</b>-49.7%]</td>
	<td>877</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.74% [<b>43.2%</b>-50.3%]</td>
	<td>783</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.66% [<b>44.0%</b>-47.3%]</td>
	<td>3,563</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.26% [41.2%-<b>45.3%</b>]</td>
	<td>2,263</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.09% [40.1%-<b>46.1%</b>]</td>
	<td>1,107</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.66% [44.0%-<b>47.3%</b>]</td>
	<td>3,563</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.78% [45.6%-<b>48.0%</b>]</td>
	<td>6,715</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.31% [44.4%-<b>48.2%</b>]</td>
	<td>2,658</td>
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
	<td>51.72% [51.4%-52.0%]</td>
	<td>112,932</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.67% [<b>40.2%</b>-49.2%]</td>
	<td>488</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-neeko"></span> Neeko</td>
	<td>45.84% [<b>41.1%</b>-50.6%]</td>
	<td>445</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>44.44% [<b>41.4%</b>-47.4%]</td>
	<td>1,098</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.98% [<b>41.6%</b>-48.4%]</td>
	<td>867</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.98% [<b>41.9%</b>-52.1%]</td>
	<td>381</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>43.24% [42.1%-<b>44.4%</b>]</td>
	<td>7,382</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>44.44% [41.4%-<b>47.4%</b>]</td>
	<td>1,098</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.98% [41.6%-<b>48.4%</b>]</td>
	<td>867</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.75% [44.7%-<b>48.8%</b>]</td>
	<td>2,336</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.67% [40.2%-<b>49.2%</b>]</td>
	<td>488</td>
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
	<td>50.80% [50.5%-51.1%]</td>
	<td>92,697</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.37% [<b>38.8%</b>-52.0%]</td>
	<td>227</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>45.64% [<b>40.9%</b>-50.4%]</td>
	<td>447</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.50% [<b>41.0%</b>-52.0%]</td>
	<td>329</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.45% [<b>42.0%</b>-50.9%]</td>
	<td>493</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>45.80% [<b>42.4%</b>-49.2%]</td>
	<td>869</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.88% [44.0%-<b>47.8%</b>]</td>
	<td>2,707</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>45.80% [42.4%-<b>49.2%</b>]</td>
	<td>869</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-katarina"></span> Katarina</td>
	<td>47.19% [45.0%-<b>49.3%</b>]</td>
	<td>2,170</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>47.31% [45.2%-<b>49.4%</b>]</td>
	<td>2,209</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>47.09% [44.3%-<b>49.9%</b>]</td>
	<td>1,308</td>
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
	<td>50.73% [50.5%-51.0%]</td>
	<td>140,490</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.88% [<b>39.4%</b>-48.4%]</td>
	<td>490</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>45.31% [<b>40.8%</b>-49.8%]</td>
	<td>490</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.49% [<b>43.7%</b>-53.3%]</td>
	<td>431</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.79% [<b>44.6%</b>-52.9%]</td>
	<td>578</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>47.26% [<b>44.8%</b>-49.8%]</td>
	<td>1,587</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.88% [39.4%-<b>48.4%</b>]</td>
	<td>490</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>48.24% [47.2%-<b>49.3%</b>]</td>
	<td>9,778</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>47.26% [44.8%-<b>49.8%</b>]</td>
	<td>1,587</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>47.50% [45.2%-<b>49.8%</b>]</td>
	<td>1,920</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>45.31% [40.8%-<b>49.8%</b>]</td>
	<td>490</td>
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
	<td>49.07% [48.8%-49.4%]</td>
	<td>104,700</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>42.47% [<b>36.8%</b>-48.2%]</td>
	<td>299</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.36% [<b>40.6%</b>-52.1%]</td>
	<td>302</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>46.15% [<b>40.7%</b>-51.6%]</td>
	<td>338</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.51% [<b>41.4%</b>-51.6%]</td>
	<td>387</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>46.60% [<b>42.5%</b>-50.7%]</td>
	<td>588</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>44.89% [42.7%-<b>47.1%</b>]</td>
	<td>1,978</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>42.47% [36.8%-<b>48.2%</b>]</td>
	<td>299</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.85% [43.1%-<b>48.6%</b>]</td>
	<td>1,289</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.84% [45.0%-<b>48.7%</b>]</td>
	<td>2,816</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>46.15% [43.5%-<b>48.8%</b>]</td>
	<td>1,402</td>
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
	<td>48.16% [47.9%-48.5%]</td>
	<td>116,835</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>44.24% [<b>40.0%</b>-48.5%]</td>
	<td>538</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.01% [<b>40.4%</b>-49.6%]</td>
	<td>471</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.80% [<b>40.6%</b>-47.0%]</td>
	<td>936</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.63% [<b>40.6%</b>-46.7%]</td>
	<td>1,068</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>43.96% [<b>40.6%</b>-47.3%]</td>
	<td>878</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.46% [41.3%-<b>45.6%</b>]</td>
	<td>2,193</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>44.55% [43.2%-<b>45.9%</b>]</td>
	<td>5,295</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.60% [41.0%-<b>46.2%</b>]</td>
	<td>1,477</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.93% [43.3%-<b>46.6%</b>]</td>
	<td>3,686</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.84% [43.1%-<b>46.6%</b>]</td>
	<td>3,171</td>
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
	<td>48.91% [48.7%-49.1%]</td>
	<td>185,292</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.49% [<b>39.5%</b>-47.5%]</td>
	<td>614</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.63% [<b>40.1%</b>-49.2%]</td>
	<td>475</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.39% [<b>40.8%</b>-46.0%]</td>
	<td>1,445</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>45.74% [<b>43.1%</b>-48.4%]</td>
	<td>1,386</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>46.44% [<b>43.5%</b>-49.4%]</td>
	<td>1,137</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.39% [40.8%-<b>46.0%</b>]</td>
	<td>1,445</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.49% [39.5%-<b>47.5%</b>]</td>
	<td>614</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>47.41% [46.6%-<b>48.2%</b>]</td>
	<td>14,617</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>45.74% [43.1%-<b>48.4%</b>]</td>
	<td>1,386</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>46.93% [45.3%-<b>48.6%</b>]</td>
	<td>3,678</td>
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
	<td>45.46% [45.3%-45.6%]</td>
	<td>384,042</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>41.11% [<b>39.9%</b>-42.3%]</td>
	<td>6,349</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>41.33% [<b>40.0%</b>-42.7%]</td>
	<td>5,250</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>42.31% [<b>40.1%</b>-44.5%]</td>
	<td>1,997</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>41.58% [<b>40.1%</b>-43.0%]</td>
	<td>4,502</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>42.23% [<b>40.2%</b>-44.2%]</td>
	<td>2,420</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>41.21% [40.3%-<b>42.1%</b>]</td>
	<td>12,484</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>41.11% [39.9%-<b>42.3%</b>]</td>
	<td>6,349</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>41.61% [40.6%-<b>42.6%</b>]</td>
	<td>10,459</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>41.33% [40.0%-<b>42.7%</b>]</td>
	<td>5,250</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>41.58% [40.1%-<b>43.0%</b>]</td>
	<td>4,502</td>
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
	<td>48.22% [48.1%-48.4%]</td>
	<td>509,362</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>40.90% [<b>39.1%</b>-42.7%]</td>
	<td>2,897</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.98% [<b>39.8%</b>-44.1%]</td>
	<td>2,082</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.62% [<b>40.3%</b>-44.9%]</td>
	<td>1,835</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.60% [<b>42.5%</b>-46.7%]</td>
	<td>2,249</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>43.38% [<b>42.6%</b>-44.1%]</td>
	<td>18,030</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>40.90% [39.1%-<b>42.7%</b>]</td>
	<td>2,897</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>43.38% [42.6%-<b>44.1%</b>]</td>
	<td>18,030</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.98% [39.8%-<b>44.1%</b>]</td>
	<td>2,082</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.62% [40.3%-<b>44.9%</b>]</td>
	<td>1,835</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>44.21% [43.3%-<b>45.1%</b>]</td>
	<td>13,240</td>
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
	<td>48.49% [48.3%-48.7%]</td>
	<td>206,265</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>41.40% [<b>39.2%</b>-43.6%]</td>
	<td>1,935</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.89% [<b>39.3%</b>-46.5%]</td>
	<td>767</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.67% [<b>40.4%</b>-49.0%]</td>
	<td>535</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.70% [<b>40.4%</b>-43.0%]</td>
	<td>6,120</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.01% [<b>41.5%</b>-50.5%]</td>
	<td>489</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.70% [40.4%-<b>43.0%</b>]</td>
	<td>6,120</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>41.40% [39.2%-<b>43.6%</b>]</td>
	<td>1,935</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.89% [39.3%-<b>46.5%</b>]</td>
	<td>767</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>45.67% [44.5%-<b>46.9%</b>]</td>
	<td>6,919</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.04% [43.0%-<b>47.1%</b>]</td>
	<td>2,407</td>
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
	<td>50.26% [50.0%-50.5%]</td>
	<td>125,429</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.60% [<b>37.6%</b>-47.6%]</td>
	<td>385</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.76% [<b>39.2%</b>-48.3%]</td>
	<td>473</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.63% [<b>39.3%</b>-49.9%]</td>
	<td>354</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.69% [<b>41.9%</b>-49.4%]</td>
	<td>707</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>47.16% [<b>42.2%</b>-52.1%]</td>
	<td>405</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.11% [44.6%-<b>47.6%</b>]</td>
	<td>4,578</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.60% [37.6%-<b>47.6%</b>]</td>
	<td>385</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.18% [44.1%-<b>48.3%</b>]</td>
	<td>2,237</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.76% [39.2%-<b>48.3%</b>]</td>
	<td>473</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.44% [45.7%-<b>49.2%</b>]</td>
	<td>3,265</td>
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
	<td>46.27% [46.0%-46.5%]</td>
	<td>150,328</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>42.82% [<b>37.7%</b>-48.0%]</td>
	<td>369</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>42.29% [<b>39.0%</b>-45.6%]</td>
	<td>901</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>40.45% [<b>39.1%</b>-41.8%]</td>
	<td>5,451</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.08% [<b>39.8%</b>-48.3%]</td>
	<td>549</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>43.24% [<b>39.9%</b>-46.6%]</td>
	<td>858</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>40.45% [39.1%-<b>41.8%</b>]</td>
	<td>5,451</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>42.46% [40.6%-<b>44.3%</b>]</td>
	<td>2,793</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>42.53% [40.4%-<b>44.6%</b>]</td>
	<td>2,201</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>44.15% [43.2%-<b>45.1%</b>]</td>
	<td>11,847</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>43.68% [42.2%-<b>45.2%</b>]</td>
	<td>4,423</td>
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
	<td>49.89% [49.6%-50.2%]</td>
	<td>96,443</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>42.15% [<b>37.8%</b>-46.5%]</td>
	<td>522</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.45% [<b>38.9%</b>-52.0%]</td>
	<td>231</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jayce"></span> Jayce</td>
	<td>46.20% [<b>40.5%</b>-51.9%]</td>
	<td>303</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.60% [<b>40.8%</b>-52.4%]</td>
	<td>294</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>47.49% [<b>41.7%</b>-53.3%]</td>
	<td>299</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>42.15% [37.8%-<b>46.5%</b>]</td>
	<td>522</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.01% [43.3%-<b>46.7%</b>]</td>
	<td>3,475</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.48% [43.1%-<b>47.9%</b>]</td>
	<td>1,737</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.70% [42.9%-<b>48.5%</b>]</td>
	<td>1,232</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.28% [43.7%-<b>48.9%</b>]</td>
	<td>1,493</td>
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
	<td>47.92% [47.7%-48.2%]</td>
	<td>149,181</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.65% [<b>37.8%</b>-47.5%]</td>
	<td>415</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.07% [<b>38.8%</b>-47.3%]</td>
	<td>541</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.65% [<b>39.6%</b>-47.7%]</td>
	<td>591</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.69% [<b>39.9%</b>-45.5%]</td>
	<td>1,265</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.77% [<b>40.8%</b>-48.8%]</td>
	<td>621</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>43.17% [41.6%-<b>44.7%</b>]</td>
	<td>4,107</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.69% [39.9%-<b>45.5%</b>]</td>
	<td>1,265</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.66% [43.1%-<b>46.3%</b>]</td>
	<td>3,838</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>44.77% [43.2%-<b>46.3%</b>]</td>
	<td>4,260</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>44.65% [42.8%-<b>46.5%</b>]</td>
	<td>2,766</td>
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
	<td>51.17% [50.8%-51.6%]</td>
	<td>67,816</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>44.66% [<b>38.4%</b>-50.9%]</td>
	<td>253</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>42.32% [<b>38.5%</b>-46.1%]</td>
	<td>671</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.54% [<b>39.9%</b>-51.2%]</td>
	<td>314</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.66% [<b>40.3%</b>-49.0%]</td>
	<td>515</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.65% [<b>40.7%</b>-46.6%]</td>
	<td>1,118</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>42.32% [38.5%-<b>46.1%</b>]</td>
	<td>671</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.65% [40.7%-<b>46.6%</b>]</td>
	<td>1,118</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>46.47% [44.9%-<b>48.0%</b>]</td>
	<td>4,248</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.66% [40.3%-<b>49.0%</b>]</td>
	<td>515</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurora"></span> Aurora</td>
	<td>45.97% [42.7%-<b>49.3%</b>]</td>
	<td>905</td>
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
	<td>49.20% [49.0%-49.4%]</td>
	<td>169,156</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>39.70% [<b>37.2%</b>-42.2%]</td>
	<td>1,592</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.17% [<b>38.5%</b>-45.9%]</td>
	<td>709</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.59% [<b>39.9%</b>-49.3%]</td>
	<td>453</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>43.84% [<b>40.7%</b>-47.0%]</td>
	<td>1,006</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.79% [<b>40.8%</b>-48.8%]</td>
	<td>614</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>39.70% [37.2%-<b>42.2%</b>]</td>
	<td>1,592</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.17% [38.5%-<b>45.9%</b>]</td>
	<td>709</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>44.65% [42.7%-<b>46.6%</b>]</td>
	<td>2,598</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>43.84% [40.7%-<b>47.0%</b>]</td>
	<td>1,006</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>46.55% [45.5%-<b>47.6%</b>]</td>
	<td>8,810</td>
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
	<td>47.14% [46.8%-47.4%]</td>
	<td>113,184</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.77% [<b>37.2%</b>-46.3%]</td>
	<td>474</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>42.04% [<b>38.4%</b>-45.7%]</td>
	<td>735</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>42.03% [<b>39.1%</b>-45.0%]</td>
	<td>1,111</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>41.68% [<b>39.1%</b>-44.3%]</td>
	<td>1,466</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>43.74% [<b>40.5%</b>-47.0%]</td>
	<td>919</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>41.68% [39.1%-<b>44.3%</b>]</td>
	<td>1,466</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>42.03% [39.1%-<b>45.0%</b>]</td>
	<td>1,111</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>42.04% [38.4%-<b>45.7%</b>]</td>
	<td>735</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>43.97% [42.3%-<b>45.7%</b>]</td>
	<td>3,364</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>43.66% [41.1%-<b>46.2%</b>]</td>
	<td>1,537</td>
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
	<td>51.18% [50.8%-51.5%]</td>
	<td>91,349</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.23% [<b>37.5%</b>-48.9%]</td>
	<td>303</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>42.60% [<b>37.6%</b>-47.6%]</td>
	<td>385</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.56% [<b>38.6%</b>-48.5%]</td>
	<td>404</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.40% [<b>39.7%</b>-47.1%]</td>
	<td>712</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.68% [<b>40.4%</b>-50.9%]</td>
	<td>359</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.15% [41.9%-<b>46.4%</b>]</td>
	<td>1,973</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.40% [39.7%-<b>47.1%</b>]</td>
	<td>712</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.42% [43.5%-<b>47.4%</b>]</td>
	<td>2,662</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>42.60% [37.6%-<b>47.6%</b>]</td>
	<td>385</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>47.07% [45.7%-<b>48.5%</b>]</td>
	<td>5,216</td>
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
	<td>49.50% [49.1%-49.9%]</td>
	<td>67,448</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.36% [<b>35.4%</b>-49.3%]</td>
	<td>203</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.75% [<b>37.3%</b>-50.2%]</td>
	<td>240</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>44.49% [<b>39.8%</b>-49.2%]</td>
	<td>454</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.38% [<b>39.9%</b>-48.9%]</td>
	<td>489</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.18% [<b>41.3%</b>-53.1%]</td>
	<td>284</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>45.22% [42.7%-<b>47.8%</b>]</td>
	<td>1,539</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>45.47% [42.4%-<b>48.5%</b>]</td>
	<td>1,071</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.38% [39.9%-<b>48.9%</b>]</td>
	<td>489</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>44.49% [39.8%-<b>49.2%</b>]</td>
	<td>454</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.36% [35.4%-<b>49.3%</b>]</td>
	<td>203</td>
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
	<td>50.07% [49.7%-50.5%]</td>
	<td>65,149</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>39.09% [<b>32.5%</b>-45.7%]</td>
	<td>220</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>42.00% [<b>35.8%</b>-48.2%]</td>
	<td>250</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.39% [<b>39.2%</b>-53.6%]</td>
	<td>194</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.26% [<b>40.1%</b>-50.4%]</td>
	<td>369</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.63% [<b>41.1%</b>-46.2%]</td>
	<td>1,547</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>39.09% [32.5%-<b>45.7%</b>]</td>
	<td>220</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.63% [41.1%-<b>46.2%</b>]</td>
	<td>1,547</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.42% [43.1%-<b>47.7%</b>]</td>
	<td>1,911</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>42.00% [35.8%-<b>48.2%</b>]</td>
	<td>250</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>46.37% [43.8%-<b>49.0%</b>]</td>
	<td>1,462</td>
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
	<td>44.78% [44.4%-45.2%]</td>
	<td>69,355</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>38.58% [<b>32.5%</b>-44.7%]</td>
	<td>254</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>39.75% [<b>34.9%</b>-44.6%]</td>
	<td>400</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>38.90% [<b>34.9%</b>-42.9%]</td>
	<td>599</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>39.52% [<b>35.3%</b>-43.7%]</td>
	<td>544</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>40.76% [<b>36.3%</b>-45.3%]</td>
	<td>476</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>39.62% [36.7%-<b>42.5%</b>]</td>
	<td>1,156</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>38.90% [34.9%-<b>42.9%</b>]</td>
	<td>599</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>41.94% [40.2%-<b>43.7%</b>]</td>
	<td>3,250</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>39.52% [35.3%-<b>43.7%</b>]</td>
	<td>544</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.98% [39.8%-<b>44.2%</b>]</td>
	<td>1,982</td>
</tr>
</table>

</details>
### ADC

<details>
<summary>Click to view</summary>

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
	<td>54.40% [54.1%-54.7%]</td>
	<td>150,062</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.94% [<b>46.6%</b>-53.3%]</td>
	<td>899</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>51.36% [<b>47.8%</b>-55.0%]</td>
	<td>771</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>51.36% [<b>48.0%</b>-54.7%]</td>
	<td>880</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>51.91% [<b>48.1%</b>-55.7%]</td>
	<td>705</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>51.22% [<b>49.2%</b>-53.2%]</td>
	<td>2,505</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>51.22% [49.2%-<b>53.2%</b>]</td>
	<td>2,505</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.94% [46.6%-<b>53.3%</b>]</td>
	<td>899</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>52.22% [50.9%-<b>53.6%</b>]</td>
	<td>5,425</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>53.02% [52.2%-<b>53.8%</b>]</td>
	<td>15,149</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>52.81% [51.2%-<b>54.4%</b>]</td>
	<td>4,052</td>
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
	<td>51.00% [50.9%-51.1%]</td>
	<td>2,048,998</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.97% [<b>46.2%</b>-47.8%]</td>
	<td>15,149</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.15% [<b>47.1%</b>-49.2%]</td>
	<td>9,173</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.31% [<b>47.4%</b>-49.2%]</td>
	<td>11,395</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>48.40% [<b>47.7%</b>-49.1%]</td>
	<td>20,249</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.64% [<b>48.4%</b>-50.9%]</td>
	<td>6,039</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.97% [46.2%-<b>47.8%</b>]</td>
	<td>15,149</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>48.40% [47.7%-<b>49.1%</b>]</td>
	<td>20,249</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.15% [47.1%-<b>49.2%</b>]</td>
	<td>9,173</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.31% [47.4%-<b>49.2%</b>]</td>
	<td>11,395</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>49.65% [49.2%-<b>50.1%</b>]</td>
	<td>56,569</td>
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
	<td>51.26% [51.2%-51.3%]</td>
	<td>2,424,035</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.46% [<b>44.8%</b>-46.1%]</td>
	<td>21,509</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.44% [<b>46.5%</b>-48.3%]</td>
	<td>12,531</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.98% [<b>47.5%</b>-48.5%]</td>
	<td>43,227</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.60% [<b>47.5%</b>-49.7%]</td>
	<td>8,504</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.15% [<b>48.1%</b>-50.2%]</td>
	<td>8,342</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.46% [44.8%-<b>46.1%</b>]</td>
	<td>21,509</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.44% [46.5%-<b>48.3%</b>]</td>
	<td>12,531</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.98% [47.5%-<b>48.5%</b>]</td>
	<td>43,227</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.99% [48.6%-<b>49.4%</b>]</td>
	<td>61,269</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.60% [47.5%-<b>49.7%</b>]</td>
	<td>8,504</td>
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
	<td>51.11% [51.0%-51.2%]</td>
	<td>531,270</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.99% [<b>45.4%</b>-48.6%]</td>
	<td>4,071</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.08% [<b>46.5%</b>-51.6%]</td>
	<td>1,524</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.66% [<b>47.6%</b>-51.7%]</td>
	<td>2,374</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>50.36% [<b>47.8%</b>-52.9%]</td>
	<td>1,521</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>49.42% [<b>48.0%</b>-50.9%]</td>
	<td>4,676</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.99% [45.4%-<b>48.6%</b>]</td>
	<td>4,071</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ashe"></span> Ashe</td>
	<td>49.97% [49.5%-<b>50.4%</b>]</td>
	<td>55,250</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>49.62% [48.8%-<b>50.5%</b>]</td>
	<td>13,932</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>49.72% [48.9%-<b>50.6%</b>]</td>
	<td>13,332</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>50.35% [49.9%-<b>50.8%</b>]</td>
	<td>56,569</td>
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
	<td>50.57% [50.5%-50.7%]</td>
	<td>1,373,159</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.35% [<b>43.3%</b>-45.4%]</td>
	<td>9,551</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.89% [<b>46.4%</b>-49.4%]</td>
	<td>4,352</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.21% [<b>46.5%</b>-48.0%]</td>
	<td>17,378</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.86% [<b>46.6%</b>-49.1%]</td>
	<td>6,339</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.58% [<b>47.0%</b>-50.2%]</td>
	<td>3,874</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.35% [43.3%-<b>45.4%</b>]</td>
	<td>9,551</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.21% [46.5%-<b>48.0%</b>]</td>
	<td>17,378</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.10% [47.5%-<b>48.7%</b>]</td>
	<td>32,768</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.97% [47.1%-<b>48.8%</b>]</td>
	<td>13,316</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.86% [46.6%-<b>49.1%</b>]</td>
	<td>6,339</td>
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
	<td>51.29% [51.2%-51.4%]</td>
	<td>562,997</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.53% [<b>45.4%</b>-49.6%]</td>
	<td>2,247</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.55% [<b>46.3%</b>-50.8%]</td>
	<td>1,963</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.76% [<b>46.4%</b>-49.1%]</td>
	<td>5,425</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.89% [<b>46.8%</b>-50.9%]</td>
	<td>2,381</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.35% [<b>47.6%</b>-49.1%]</td>
	<td>18,260</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.35% [47.6%-<b>49.1%</b>]</td>
	<td>18,260</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.76% [46.4%-<b>49.1%</b>]</td>
	<td>5,425</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>48.85% [48.5%-<b>49.2%</b>]</td>
	<td>64,494</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.53% [45.4%-<b>49.6%</b>]</td>
	<td>2,247</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>49.53% [48.7%-<b>50.3%</b>]</td>
	<td>15,146</td>
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
	<td>53.01% [52.7%-53.3%]</td>
	<td>90,948</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>49.59% [<b>45.5%</b>-53.6%]</td>
	<td>609</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>51.25% [<b>45.7%</b>-56.8%]</td>
	<td>320</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>51.45% [<b>46.5%</b>-56.4%]</td>
	<td>414</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>50.06% [<b>46.7%</b>-53.4%]</td>
	<td>899</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>50.69% [<b>47.8%</b>-53.5%]</td>
	<td>1,231</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>50.34% [48.3%-<b>52.4%</b>]</td>
	<td>2,374</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>51.85% [50.8%-<b>52.9%</b>]</td>
	<td>9,173</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>52.14% [50.9%-<b>53.4%</b>]</td>
	<td>6,339</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>50.06% [46.7%-<b>53.4%</b>]</td>
	<td>899</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>52.55% [51.7%-<b>53.4%</b>]</td>
	<td>12,531</td>
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
	<td>52.25% [52.1%-52.4%]</td>
	<td>491,241</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.80% [<b>45.5%</b>-50.1%]</td>
	<td>1,956</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.19% [<b>45.6%</b>-48.8%]</td>
	<td>4,052</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>50.09% [<b>47.6%</b>-52.5%]</td>
	<td>1,669</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>49.90% [<b>48.4%</b>-51.4%]</td>
	<td>4,377</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>50.43% [<b>48.5%</b>-52.3%]</td>
	<td>2,762</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.19% [45.6%-<b>48.8%</b>]</td>
	<td>4,052</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.80% [45.5%-<b>50.1%</b>]</td>
	<td>1,956</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>49.99% [49.6%-<b>50.4%</b>]</td>
	<td>53,676</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>49.50% [48.5%-<b>50.5%</b>]</td>
	<td>10,678</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>50.38% [49.5%-<b>51.2%</b>]</td>
	<td>13,932</td>
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
	<td>50.01% [49.9%-50.2%]</td>
	<td>499,410</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.65% [<b>44.9%</b>-48.4%]</td>
	<td>3,297</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.34% [<b>45.4%</b>-49.3%]</td>
	<td>2,560</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>46.85% [<b>45.5%</b>-48.2%]</td>
	<td>5,667</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>47.48% [<b>46.6%</b>-48.4%]</td>
	<td>12,857</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>49.59% [<b>47.0%</b>-52.2%]</td>
	<td>1,456</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>47.44% [47.0%-<b>47.9%</b>]</td>
	<td>59,074</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>46.85% [45.5%-<b>48.2%</b>]</td>
	<td>5,667</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>47.48% [46.6%-<b>48.4%</b>]</td>
	<td>12,857</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.65% [44.9%-<b>48.4%</b>]</td>
	<td>3,297</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>48.41% [47.8%-<b>49.0%</b>]</td>
	<td>30,486</td>
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
	<td>51.69% [51.5%-51.9%]</td>
	<td>287,455</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.85% [<b>45.1%</b>-50.6%]</td>
	<td>1,327</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>47.77% [<b>45.2%</b>-50.3%]</td>
	<td>1,547</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.70% [<b>46.5%</b>-52.9%]</td>
	<td>994</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>48.77% [<b>46.7%</b>-50.8%]</td>
	<td>2,444</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.78% [<b>46.8%</b>-50.8%]</td>
	<td>2,505</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>48.20% [46.9%-<b>49.5%</b>]</td>
	<td>5,963</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>47.77% [45.2%-<b>50.3%</b>]</td>
	<td>1,547</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>49.94% [49.4%-<b>50.5%</b>]</td>
	<td>30,614</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.85% [45.1%-<b>50.6%</b>]</td>
	<td>1,327</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>49.61% [48.5%-<b>50.8%</b>]</td>
	<td>7,694</td>
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
	<td>50.09% [50.0%-50.2%]</td>
	<td>1,916,375</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.38% [<b>43.6%</b>-45.2%]</td>
	<td>14,657</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.88% [<b>45.1%</b>-46.6%]</td>
	<td>17,340</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.99% [<b>45.7%</b>-48.3%]</td>
	<td>5,610</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.35% [<b>46.2%</b>-48.5%]</td>
	<td>7,918</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.59% [<b>46.3%</b>-48.9%]</td>
	<td>5,865</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.38% [43.6%-<b>45.2%</b>]</td>
	<td>14,657</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.88% [45.1%-<b>46.6%</b>]</td>
	<td>17,340</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>47.27% [46.8%-<b>47.7%</b>]</td>
	<td>54,492</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>47.65% [47.1%-<b>48.2%</b>]</td>
	<td>30,191</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.99% [45.7%-<b>48.3%</b>]</td>
	<td>5,610</td>
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
	<td>51.86% [51.5%-52.3%]</td>
	<td>62,314</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.55% [<b>43.6%</b>-53.5%]</td>
	<td>414</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.64% [<b>45.0%</b>-52.2%]</td>
	<td>771</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>47.94% [<b>45.1%</b>-50.8%]</td>
	<td>1,262</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>51.00% [<b>46.3%</b>-55.7%]</td>
	<td>451</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>49.46% [<b>46.9%</b>-52.0%]</td>
	<td>1,492</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>47.94% [45.1%-<b>50.8%</b>]</td>
	<td>1,262</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>50.36% [49.1%-<b>51.6%</b>]</td>
	<td>6,039</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>50.85% [49.8%-<b>51.9%</b>]</td>
	<td>8,342</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>49.46% [46.9%-<b>52.0%</b>]</td>
	<td>1,492</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.64% [45.0%-<b>52.2%</b>]</td>
	<td>771</td>
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
	<td>50.47% [50.4%-50.6%]</td>
	<td>1,089,889</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.68% [<b>44.0%</b>-47.3%]</td>
	<td>3,660</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.68% [<b>44.5%</b>-46.9%]</td>
	<td>7,171</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.55% [<b>44.7%</b>-48.4%]</td>
	<td>2,909</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.63% [<b>45.3%</b>-47.9%]</td>
	<td>5,882</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.66% [<b>45.9%</b>-47.5%]</td>
	<td>15,274</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.68% [44.5%-<b>46.9%</b>]</td>
	<td>7,171</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.68% [44.0%-<b>47.3%</b>]</td>
	<td>3,660</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.66% [45.9%-<b>47.5%</b>]</td>
	<td>15,274</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.63% [45.3%-<b>47.9%</b>]</td>
	<td>5,882</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.32% [46.4%-<b>48.2%</b>]</td>
	<td>12,305</td>
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
	<td>49.77% [49.6%-49.9%]</td>
	<td>642,918</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.70% [<b>42.2%</b>-45.2%]</td>
	<td>4,348</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.73% [<b>44.4%</b>-49.1%]</td>
	<td>1,759</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.25% [<b>44.9%</b>-49.6%]</td>
	<td>1,816</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.32% [<b>45.3%</b>-49.3%]</td>
	<td>2,534</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.92% [<b>45.8%</b>-48.0%]</td>
	<td>7,869</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.70% [42.2%-<b>45.2%</b>]</td>
	<td>4,348</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>47.22% [46.9%-<b>47.6%</b>]</td>
	<td>73,223</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.83% [46.0%-<b>47.7%</b>]</td>
	<td>13,584</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.92% [45.8%-<b>48.0%</b>]</td>
	<td>7,869</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>48.22% [47.8%-<b>48.6%</b>]</td>
	<td>61,937</td>
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
	<td>48.66% [48.6%-48.7%]</td>
	<td>1,917,528</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.44% [<b>42.8%</b>-44.1%]</td>
	<td>22,866</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.25% [<b>44.2%</b>-46.3%]</td>
	<td>8,235</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.14% [<b>44.3%</b>-46.0%]</td>
	<td>13,733</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.89% [<b>45.6%</b>-48.2%]</td>
	<td>5,639</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.11% [<b>45.6%</b>-46.6%]</td>
	<td>46,034</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.44% [42.8%-<b>44.1%</b>]</td>
	<td>22,866</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.14% [44.3%-<b>46.0%</b>]</td>
	<td>13,733</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.25% [44.2%-<b>46.3%</b>]</td>
	<td>8,235</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.11% [45.6%-<b>46.6%</b>]</td>
	<td>46,034</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>46.93% [46.5%-<b>47.3%</b>]</td>
	<td>63,253</td>
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
	<td>48.59% [48.5%-48.7%]</td>
	<td>1,534,955</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.99% [<b>43.2%</b>-44.8%]</td>
	<td>14,117</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>44.66% [<b>43.5%</b>-45.8%]</td>
	<td>7,962</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.42% [<b>44.4%</b>-46.4%]</td>
	<td>10,360</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.43% [<b>44.9%</b>-48.0%]</td>
	<td>4,295</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.83% [<b>45.6%</b>-48.1%]</td>
	<td>6,378</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.99% [43.2%-<b>44.8%</b>]</td>
	<td>14,117</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>44.66% [43.5%-<b>45.8%</b>]</td>
	<td>7,962</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.42% [44.4%-<b>46.4%</b>]</td>
	<td>10,360</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>46.43% [45.9%-<b>46.9%</b>]</td>
	<td>40,165</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.96% [46.4%-<b>47.5%</b>]</td>
	<td>35,629</td>
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
	<td>48.88% [48.8%-49.0%]</td>
	<td>600,339</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.78% [<b>41.8%</b>-45.7%]</td>
	<td>2,574</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.93% [<b>43.4%</b>-46.5%]</td>
	<td>4,022</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.86% [<b>44.6%</b>-47.1%]</td>
	<td>6,166</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.71% [<b>45.9%</b>-47.6%]</td>
	<td>13,768</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>47.88% [<b>46.1%</b>-49.7%]</td>
	<td>3,114</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.78% [41.8%-<b>45.7%</b>]</td>
	<td>2,574</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.93% [43.4%-<b>46.5%</b>]</td>
	<td>4,022</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.86% [44.6%-<b>47.1%</b>]</td>
	<td>6,166</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>47.00% [46.6%-<b>47.4%</b>]</td>
	<td>73,219</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.71% [45.9%-<b>47.6%</b>]</td>
	<td>13,768</td>
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
	<td>49.54% [49.4%-49.7%]</td>
	<td>442,774</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.41% [<b>43.0%</b>-47.8%]</td>
	<td>1,709</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.79% [<b>43.2%</b>-46.4%]</td>
	<td>3,974</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.49% [<b>43.4%</b>-47.6%]</td>
	<td>2,238</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.03% [<b>43.8%</b>-48.3%]</td>
	<td>1,951</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.37% [<b>44.0%</b>-46.7%]</td>
	<td>5,502</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.79% [43.2%-<b>46.4%</b>]</td>
	<td>3,974</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.37% [44.0%-<b>46.7%</b>]</td>
	<td>5,502</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.49% [43.4%-<b>47.6%</b>]</td>
	<td>2,238</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.41% [43.0%-<b>47.8%</b>]</td>
	<td>1,709</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>47.01% [46.1%-<b>47.9%</b>]</td>
	<td>11,341</td>
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
	<td>49.28% [49.1%-49.4%]</td>
	<td>392,622</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>42.98% [<b>41.2%</b>-44.8%]</td>
	<td>2,955</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.53% [<b>42.7%</b>-48.4%]</td>
	<td>1,208</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.39% [<b>42.7%</b>-46.0%]</td>
	<td>3,661</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.98% [<b>43.1%</b>-48.8%]</td>
	<td>1,207</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.49% [<b>44.5%</b>-46.5%]</td>
	<td>9,696</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>42.98% [41.2%-<b>44.8%</b>]</td>
	<td>2,955</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.39% [42.7%-<b>46.0%</b>]</td>
	<td>3,661</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.49% [44.5%-<b>46.5%</b>]</td>
	<td>9,696</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>47.36% [46.9%-<b>47.8%</b>]</td>
	<td>50,006</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>47.14% [46.3%-<b>48.0%</b>]</td>
	<td>13,167</td>
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
	<td>49.66% [49.5%-49.8%]</td>
	<td>503,839</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.60% [<b>40.6%</b>-44.6%]</td>
	<td>2,331</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.26% [<b>42.7%</b>-47.9%]</td>
	<td>1,465</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.05% [<b>43.0%</b>-45.1%]</td>
	<td>8,567</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>45.18% [<b>44.3%</b>-46.0%]</td>
	<td>13,385</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.70% [<b>45.0%</b>-48.4%]</td>
	<td>3,544</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.60% [40.6%-<b>44.6%</b>]</td>
	<td>2,331</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.05% [43.0%-<b>45.1%</b>]</td>
	<td>8,567</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>45.18% [44.3%-<b>46.0%</b>]</td>
	<td>13,385</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.54% [45.6%-<b>47.4%</b>]</td>
	<td>12,353</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.26% [42.7%-<b>47.9%</b>]</td>
	<td>1,465</td>
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
	<td>53.20% [53.0%-53.4%]</td>
	<td>202,702</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.83% [<b>42.2%</b>-47.5%]</td>
	<td>1,432</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.89% [<b>42.7%</b>-49.1%]</td>
	<td>948</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.57% [<b>43.6%</b>-51.5%]</td>
	<td>639</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.29% [<b>44.6%</b>-52.0%]</td>
	<td>733</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>50.07% [<b>46.3%</b>-53.8%]</td>
	<td>719</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.83% [42.2%-<b>47.5%</b>]</td>
	<td>1,432</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xayah"></span> Xayah</td>
	<td>47.63% [46.4%-<b>48.8%</b>]</td>
	<td>7,147</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.89% [42.7%-<b>49.1%</b>]</td>
	<td>948</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>48.35% [47.0%-<b>49.7%</b>]</td>
	<td>5,167</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>50.50% [49.8%-<b>51.2%</b>]</td>
	<td>22,384</td>
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
	<td>51.41% [51.0%-51.8%]</td>
	<td>60,873</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>41.67% [<b>36.1%</b>-47.3%]</td>
	<td>312</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.47% [<b>42.3%</b>-54.6%]</td>
	<td>262</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.75% [<b>43.2%</b>-54.3%]</td>
	<td>320</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.09% [<b>44.3%</b>-51.9%]</td>
	<td>705</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>51.20% [<b>46.0%</b>-56.4%]</td>
	<td>375</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>41.67% [36.1%-<b>47.3%</b>]</td>
	<td>312</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>49.78% [48.5%-<b>51.0%</b>]</td>
	<td>6,330</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.09% [44.3%-<b>51.9%</b>]</td>
	<td>705</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kai-sa"></span> Kai'Sa</td>
	<td>50.83% [49.5%-<b>52.2%</b>]</td>
	<td>5,414</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>49.64% [47.1%-<b>52.2%</b>]</td>
	<td>1,521</td>
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
	<td>47.69% [47.5%-47.8%]</td>
	<td>488,625</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.09% [<b>41.8%</b>-46.4%]</td>
	<td>1,869</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.94% [<b>42.2%</b>-45.7%]</td>
	<td>3,145</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>45.77% [<b>43.6%</b>-47.9%]</td>
	<td>2,104</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.75% [<b>43.9%</b>-45.6%]</td>
	<td>13,648</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>45.74% [<b>44.5%</b>-47.0%]</td>
	<td>6,591</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.75% [43.9%-<b>45.6%</b>]</td>
	<td>13,648</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.94% [42.2%-<b>45.7%</b>]</td>
	<td>3,145</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.09% [41.8%-<b>46.4%</b>]</td>
	<td>1,869</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>46.09% [45.5%-<b>46.7%</b>]</td>
	<td>25,795</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>46.07% [45.2%-<b>46.9%</b>]</td>
	<td>13,070</td>
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
	<td>51.07% [50.8%-51.4%]</td>
	<td>109,013</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>42.52% [<b>39.8%</b>-45.2%]</td>
	<td>1,343</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.45% [<b>41.6%</b>-51.3%]</td>
	<td>422</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.80% [<b>43.6%</b>-54.0%]</td>
	<td>375</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.00% [<b>44.3%</b>-53.7%]</td>
	<td>451</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.64% [<b>45.3%</b>-52.0%]</td>
	<td>880</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>42.52% [39.8%-<b>45.2%</b>]</td>
	<td>1,343</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xayah"></span> Xayah</td>
	<td>47.03% [45.4%-<b>48.7%</b>]</td>
	<td>3,700</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>47.66% [45.8%-<b>49.6%</b>]</td>
	<td>2,755</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-samira"></span> Samira</td>
	<td>47.90% [46.1%-<b>49.7%</b>]</td>
	<td>3,077</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>48.30% [46.5%-<b>50.1%</b>]</td>
	<td>3,087</td>
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
	<td>50.06% [49.7%-50.5%]</td>
	<td>65,073</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.44% [<b>38.5%</b>-50.4%]</td>
	<td>279</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.43% [<b>41.5%</b>-49.3%]</td>
	<td>656</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.79% [<b>41.6%</b>-52.0%]</td>
	<td>374</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.96% [<b>42.4%</b>-47.5%]</td>
	<td>1,519</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.29% [<b>43.0%</b>-49.6%]</td>
	<td>929</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.96% [42.4%-<b>47.5%</b>]</td>
	<td>1,519</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.43% [41.5%-<b>49.3%</b>]</td>
	<td>656</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.01% [44.6%-<b>49.4%</b>]</td>
	<td>1,770</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>47.19% [44.9%-<b>49.4%</b>]</td>
	<td>1,956</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.29% [43.0%-<b>49.6%</b>]</td>
	<td>929</td>
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
	<td>48.53% [48.4%-48.7%]</td>
	<td>464,085</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.09% [<b>41.3%</b>-46.9%]</td>
	<td>1,286</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.22% [<b>41.5%</b>-45.0%]</td>
	<td>3,253</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.59% [<b>41.9%</b>-47.3%]</td>
	<td>1,350</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>45.94% [<b>44.0%</b>-47.9%]</td>
	<td>2,647</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.45% [<b>44.3%</b>-48.6%]</td>
	<td>2,211</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.22% [41.5%-<b>45.0%</b>]</td>
	<td>3,253</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.09% [41.3%-<b>46.9%</b>]</td>
	<td>1,286</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.05% [45.1%-<b>47.0%</b>]</td>
	<td>10,424</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.59% [41.9%-<b>47.3%</b>]</td>
	<td>1,350</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.12% [44.9%-<b>47.3%</b>]</td>
	<td>6,659</td>
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
	<td>48.23% [48.1%-48.4%]</td>
	<td>434,286</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>42.61% [<b>41.1%</b>-44.1%]</td>
	<td>4,344</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.70% [<b>41.5%</b>-45.9%]</td>
	<td>2,000</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.22% [<b>44.3%</b>-48.1%]</td>
	<td>2,696</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>46.56% [<b>44.5%</b>-48.6%]</td>
	<td>2,343</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>45.65% [<b>44.7%</b>-46.6%]</td>
	<td>10,069</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>42.61% [41.1%-<b>44.1%</b>]</td>
	<td>4,344</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.70% [41.5%-<b>45.9%</b>]</td>
	<td>2,000</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>46.22% [45.8%-<b>46.6%</b>]</td>
	<td>56,756</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>45.65% [44.7%-<b>46.6%</b>]</td>
	<td>10,069</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.87% [44.9%-<b>46.9%</b>]</td>
	<td>10,086</td>
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
	<td>48.07% [47.9%-48.3%]</td>
	<td>252,049</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.19% [<b>40.4%</b>-48.0%]</td>
	<td>688</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.37% [<b>41.3%</b>-47.5%]</td>
	<td>1,021</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.98% [<b>42.1%</b>-45.9%]</td>
	<td>2,726</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.61% [<b>43.0%</b>-50.2%]</td>
	<td>753</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.23% [<b>43.9%</b>-48.5%]</td>
	<td>1,899</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.98% [42.1%-<b>45.9%</b>]</td>
	<td>2,726</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>46.40% [45.8%-<b>47.0%</b>]</td>
	<td>27,620</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.93% [44.7%-<b>47.2%</b>]</td>
	<td>6,138</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.37% [41.3%-<b>47.5%</b>]</td>
	<td>1,021</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.19% [40.4%-<b>48.0%</b>]</td>
	<td>688</td>
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
	<td>48.60% [48.4%-48.8%]</td>
	<td>259,439</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>40.43% [<b>38.6%</b>-42.2%]</td>
	<td>2,946</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>43.63% [<b>41.0%</b>-46.3%]</td>
	<td>1,373</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.10% [<b>44.7%</b>-51.5%]</td>
	<td>867</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.99% [<b>44.7%</b>-49.3%]</td>
	<td>1,913</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>46.19% [<b>44.9%</b>-47.4%]</td>
	<td>6,441</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>40.43% [38.6%-<b>42.2%</b>]</td>
	<td>2,946</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>43.63% [41.0%-<b>46.3%</b>]</td>
	<td>1,373</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.17% [45.0%-<b>47.4%</b>]</td>
	<td>7,113</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>46.19% [44.9%-<b>47.4%</b>]</td>
	<td>6,441</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>47.03% [46.5%-<b>47.6%</b>]</td>
	<td>32,638</td>
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
	<td>46.89% [46.7%-47.1%]</td>
	<td>233,556</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>41.48% [<b>38.9%</b>-44.0%]</td>
	<td>1,490</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.70% [<b>39.4%</b>-46.0%]</td>
	<td>918</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.48% [<b>40.3%</b>-48.7%]</td>
	<td>553</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.86% [<b>41.0%</b>-48.7%]</td>
	<td>671</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.31% [<b>43.0%</b>-45.6%]</td>
	<td>5,890</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>41.48% [38.9%-<b>44.0%</b>]</td>
	<td>1,490</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-corki"></span> Corki</td>
	<td>44.33% [43.2%-<b>45.5%</b>]</td>
	<td>7,368</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.31% [43.0%-<b>45.6%</b>]</td>
	<td>5,890</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-caitlyn"></span> Caitlyn</td>
	<td>45.33% [44.7%-<b>45.9%</b>]</td>
	<td>25,898</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.70% [39.4%-<b>46.0%</b>]</td>
	<td>918</td>
</tr>
</table>

</details>
### Support

<details>
<summary>Click to view</summary>

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
	<td>51.23% [51.1%-51.4%]</td>
	<td>396,627</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.55% [<b>45.4%</b>-51.7%]</td>
	<td>1,038</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>50.28% [<b>47.8%</b>-52.8%]</td>
	<td>1,613</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.74% [<b>47.9%</b>-51.6%]</td>
	<td>2,833</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.89% [<b>48.2%</b>-49.6%]</td>
	<td>19,279</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>51.42% [<b>48.2%</b>-54.7%]</td>
	<td>953</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.89% [48.2%-<b>49.6%</b>]</td>
	<td>19,279</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.16% [48.2%-<b>50.1%</b>]</td>
	<td>11,477</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.46% [48.3%-<b>50.7%</b>]</td>
	<td>6,893</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>49.92% [49.1%-<b>50.7%</b>]</td>
	<td>16,842</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-karma"></span> Karma</td>
	<td>49.82% [48.9%-<b>50.7%</b>]</td>
	<td>12,602</td>
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
	<td>50.69% [50.6%-50.8%]</td>
	<td>871,758</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.93% [<b>47.0%</b>-50.9%]</td>
	<td>2,659</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.49% [<b>47.6%</b>-49.4%]</td>
	<td>13,364</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.38% [<b>47.9%</b>-48.9%]</td>
	<td>36,952</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.78% [<b>47.9%</b>-51.7%]</td>
	<td>2,716</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.57% [<b>47.9%</b>-49.2%]</td>
	<td>22,267</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.38% [47.9%-<b>48.9%</b>]</td>
	<td>36,952</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.57% [47.9%-<b>49.2%</b>]</td>
	<td>22,267</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.49% [47.6%-<b>49.4%</b>]</td>
	<td>13,364</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.89% [48.4%-<b>49.4%</b>]</td>
	<td>46,054</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.92% [48.2%-<b>49.7%</b>]</td>
	<td>18,559</td>
</tr>
</table>

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
	<td>52.03% [51.9%-52.2%]</td>
	<td>692,091</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.76% [<b>46.4%</b>-51.1%]</td>
	<td>1,858</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.90% [<b>47.4%</b>-50.4%]</td>
	<td>4,530</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>50.60% [<b>48.1%</b>-53.1%]</td>
	<td>1,579</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>49.82% [<b>48.1%</b>-51.5%]</td>
	<td>3,575</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.77% [<b>48.9%</b>-50.7%]</td>
	<td>12,699</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.90% [47.4%-<b>50.4%</b>]</td>
	<td>4,530</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.90% [49.2%-<b>50.6%</b>]</td>
	<td>21,024</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.77% [48.9%-<b>50.7%</b>]</td>
	<td>12,699</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>50.34% [49.7%-<b>51.0%</b>]</td>
	<td>23,154</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.76% [46.4%-<b>51.1%</b>]</td>
	<td>1,858</td>
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
	<td>50.94% [50.9%-51.0%]</td>
	<td>1,420,878</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.89% [<b>47.2%</b>-48.5%]</td>
	<td>23,017</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.96% [<b>47.3%</b>-50.6%]</td>
	<td>3,705</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.87% [<b>47.5%</b>-48.3%]</td>
	<td>57,190</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.05% [<b>47.5%</b>-48.6%]</td>
	<td>28,315</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.51% [<b>47.6%</b>-49.4%]</td>
	<td>12,247</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.87% [47.5%-<b>48.3%</b>]</td>
	<td>57,190</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.89% [47.2%-<b>48.5%</b>]</td>
	<td>23,017</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.05% [47.5%-<b>48.6%</b>]</td>
	<td>28,315</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.57% [48.1%-<b>49.0%</b>]</td>
	<td>53,616</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.61% [48.0%-<b>49.2%</b>]</td>
	<td>28,863</td>
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
	<td>50.80% [50.7%-50.9%]</td>
	<td>696,982</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.30% [<b>46.6%</b>-48.0%]</td>
	<td>20,490</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.49% [<b>47.2%</b>-51.8%]</td>
	<td>1,944</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.74% [<b>47.8%</b>-49.7%]</td>
	<td>11,014</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.27% [<b>47.9%</b>-50.7%]</td>
	<td>4,997</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>48.33% [<b>47.9%</b>-48.7%]</td>
	<td>57,667</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.30% [46.6%-<b>48.0%</b>]</td>
	<td>20,490</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>48.33% [47.9%-<b>48.7%</b>]</td>
	<td>57,667</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.67% [48.1%-<b>49.2%</b>]</td>
	<td>30,363</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.93% [48.2%-<b>49.6%</b>]</td>
	<td>19,608</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.74% [47.8%-<b>49.7%</b>]</td>
	<td>11,014</td>
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
	<td>51.50% [51.3%-51.7%]</td>
	<td>408,977</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>49.77% [<b>46.4%</b>-53.2%]</td>
	<td>860</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>49.49% [<b>46.8%</b>-52.2%]</td>
	<td>1,386</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>50.57% [<b>47.6%</b>-53.5%]</td>
	<td>1,145</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>50.25% [<b>47.9%</b>-52.6%]</td>
	<td>1,819</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>49.15% [<b>48.0%</b>-50.3%]</td>
	<td>7,380</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>49.37% [48.6%-<b>50.1%</b>]</td>
	<td>17,725</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.65% [49.0%-<b>50.3%</b>]</td>
	<td>23,154</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>49.15% [48.0%-<b>50.3%</b>]</td>
	<td>7,380</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>49.56% [48.3%-<b>50.8%</b>]</td>
	<td>6,011</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>49.55% [48.1%-<b>51.0%</b>]</td>
	<td>5,043</td>
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
	<td>51.69% [51.5%-51.9%]</td>
	<td>257,586</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.04% [<b>46.5%</b>-49.6%]</td>
	<td>4,109</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>50.39% [<b>46.8%</b>-54.0%]</td>
	<td>768</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.61% [<b>47.0%</b>-50.2%]</td>
	<td>3,808</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>51.69% [<b>47.8%</b>-55.6%]</td>
	<td>650</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.03% [<b>47.8%</b>-50.3%]</td>
	<td>6,422</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.04% [46.5%-<b>49.6%</b>]</td>
	<td>4,109</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.09% [48.2%-<b>49.9%</b>]</td>
	<td>13,943</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.61% [47.0%-<b>50.2%</b>]</td>
	<td>3,808</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.03% [47.8%-<b>50.3%</b>]</td>
	<td>6,422</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>49.59% [48.6%-<b>50.6%</b>]</td>
	<td>10,680</td>
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
	<td>51.30% [51.2%-51.4%]</td>
	<td>775,756</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>46.69% [<b>45.9%</b>-47.5%]</td>
	<td>16,885</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.42% [<b>46.5%</b>-50.3%]</td>
	<td>2,792</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.03% [<b>46.8%</b>-49.3%]</td>
	<td>6,231</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.98% [<b>46.8%</b>-51.2%]</td>
	<td>2,066</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.53% [<b>46.9%</b>-48.2%]</td>
	<td>25,738</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>46.69% [45.9%-<b>47.5%</b>]</td>
	<td>16,885</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.53% [46.9%-<b>48.2%</b>]</td>
	<td>25,738</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.73% [47.1%-<b>48.4%</b>]</td>
	<td>22,505</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.34% [47.7%-<b>49.0%</b>]</td>
	<td>26,038</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.03% [46.8%-<b>49.3%</b>]</td>
	<td>6,231</td>
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
	<td>50.15% [50.0%-50.3%]</td>
	<td>642,886</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.59% [<b>45.2%</b>-50.0%]</td>
	<td>1,761</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>48.45% [<b>46.3%</b>-50.6%]</td>
	<td>2,219</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.80% [<b>46.4%</b>-49.2%]</td>
	<td>4,935</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.22% [<b>46.5%</b>-49.9%]</td>
	<td>3,370</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.31% [<b>46.6%</b>-48.0%]</td>
	<td>21,115</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.31% [46.6%-<b>48.0%</b>]</td>
	<td>21,115</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.51% [46.8%-<b>48.2%</b>]</td>
	<td>18,626</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>48.22% [47.8%-<b>48.6%</b>]</td>
	<td>65,524</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.70% [46.8%-<b>48.6%</b>]</td>
	<td>11,096</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.14% [47.3%-<b>49.0%</b>]</td>
	<td>14,256</td>
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
	<td>52.35% [52.2%-52.5%]</td>
	<td>279,445</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.10% [<b>45.5%</b>-52.7%]</td>
	<td>776</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.16% [<b>46.2%</b>-50.1%]</td>
	<td>2,604</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.69% [<b>47.6%</b>-49.8%]</td>
	<td>7,998</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>50.22% [<b>47.9%</b>-52.6%]</td>
	<td>1,794</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>50.44% [<b>47.9%</b>-53.0%]</td>
	<td>1,578</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.69% [47.6%-<b>49.8%</b>]</td>
	<td>7,998</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.16% [46.2%-<b>50.1%</b>]</td>
	<td>2,604</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.41% [48.4%-<b>50.4%</b>]</td>
	<td>10,670</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.53% [48.4%-<b>50.7%</b>]</td>
	<td>7,948</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>50.12% [49.2%-<b>51.1%</b>]</td>
	<td>11,018</td>
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
	<td>51.68% [51.5%-51.9%]</td>
	<td>250,724</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.59% [<b>45.8%</b>-51.4%]</td>
	<td>1,278</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>50.27% [<b>46.0%</b>-54.5%]</td>
	<td>555</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.26% [<b>46.6%</b>-49.9%]</td>
	<td>3,682</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>51.00% [<b>47.1%</b>-54.9%]</td>
	<td>651</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>50.28% [<b>47.6%</b>-52.9%]</td>
	<td>1,404</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.26% [46.6%-<b>49.9%</b>]</td>
	<td>3,682</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>50.04% [49.3%-<b>50.7%</b>]</td>
	<td>20,682</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-blitzcrank"></span> Blitzcrank</td>
	<td>49.81% [48.6%-<b>51.0%</b>]</td>
	<td>7,024</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>50.22% [49.3%-<b>51.1%</b>]</td>
	<td>12,699</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>49.91% [48.7%-<b>51.2%</b>]</td>
	<td>6,397</td>
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
	<td>52.20% [52.1%-52.3%]</td>
	<td>487,838</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.64% [<b>44.9%</b>-50.4%]</td>
	<td>1,293</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.93% [<b>45.9%</b>-49.9%]</td>
	<td>2,539</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.22% [<b>46.4%</b>-52.1%]</td>
	<td>1,221</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.91% [<b>47.2%</b>-50.6%]</td>
	<td>3,527</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>49.10% [<b>47.3%</b>-50.9%]</td>
	<td>3,106</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.91% [48.0%-<b>49.9%</b>]</td>
	<td>11,093</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.93% [45.9%-<b>49.9%</b>]</td>
	<td>2,539</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.01% [47.9%-<b>50.1%</b>]</td>
	<td>8,052</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.36% [48.5%-<b>50.2%</b>]</td>
	<td>14,011</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.64% [44.9%-<b>50.4%</b>]</td>
	<td>1,293</td>
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
	<td>51.54% [51.4%-51.7%]</td>
	<td>377,864</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.38% [<b>45.5%</b>-49.2%]</td>
	<td>2,925</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.05% [<b>45.7%</b>-48.4%]</td>
	<td>5,503</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.95% [<b>45.9%</b>-50.0%]</td>
	<td>2,415</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.73% [<b>46.2%</b>-49.3%]</td>
	<td>4,115</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.82% [<b>46.8%</b>-52.8%]</td>
	<td>1,124</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.05% [45.7%-<b>48.4%</b>]</td>
	<td>5,503</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.96% [47.0%-<b>48.9%</b>]</td>
	<td>11,828</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.30% [47.4%-<b>49.2%</b>]</td>
	<td>12,589</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.38% [45.5%-<b>49.2%</b>]</td>
	<td>2,925</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.73% [46.2%-<b>49.3%</b>]</td>
	<td>4,115</td>
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
	<td>50.33% [50.2%-50.5%]</td>
	<td>558,605</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.59% [<b>45.4%</b>-47.7%]</td>
	<td>7,415</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.12% [<b>45.6%</b>-50.6%]</td>
	<td>1,598</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.24% [<b>46.4%</b>-50.1%]</td>
	<td>2,927</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.81% [<b>46.9%</b>-50.7%]</td>
	<td>2,811</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.15% [<b>47.0%</b>-49.3%]</td>
	<td>7,387</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.59% [45.4%-<b>47.7%</b>]</td>
	<td>7,415</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.11% [47.3%-<b>48.9%</b>]</td>
	<td>15,459</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.37% [47.7%-<b>49.0%</b>]</td>
	<td>25,174</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.15% [47.0%-<b>49.3%</b>]</td>
	<td>7,387</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.82% [48.0%-<b>49.7%</b>]</td>
	<td>13,635</td>
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
	<td>51.37% [51.2%-51.5%]</td>
	<td>512,715</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.67% [<b>45.4%</b>-47.9%]</td>
	<td>6,497</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.48% [<b>45.5%</b>-49.5%]</td>
	<td>2,523</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.27% [<b>45.5%</b>-49.0%]</td>
	<td>3,334</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.85% [<b>45.6%</b>-50.1%]</td>
	<td>1,887</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>46.93% [<b>45.7%</b>-48.2%]</td>
	<td>6,128</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.67% [45.4%-<b>47.9%</b>]</td>
	<td>6,497</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>46.93% [45.7%-<b>48.2%</b>]</td>
	<td>6,128</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.67% [46.6%-<b>48.7%</b>]</td>
	<td>9,004</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.11% [47.3%-<b>48.9%</b>]</td>
	<td>15,594</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.27% [45.5%-<b>49.0%</b>]</td>
	<td>3,334</td>
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
	<td>1,134,630</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.86% [<b>45.1%</b>-48.6%]</td>
	<td>3,284</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>45.99% [<b>45.4%</b>-46.6%]</td>
	<td>28,728</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.21% [<b>45.6%</b>-46.8%]</td>
	<td>27,941</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.11% [<b>46.1%</b>-48.1%]</td>
	<td>10,727</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.28% [<b>46.5%</b>-48.0%]</td>
	<td>17,266</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>45.99% [45.4%-<b>46.6%</b>]</td>
	<td>28,728</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.21% [45.6%-<b>46.8%</b>]</td>
	<td>27,941</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.53% [47.1%-<b>48.0%</b>]</td>
	<td>48,984</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.28% [46.5%-<b>48.0%</b>]</td>
	<td>17,266</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.11% [46.1%-<b>48.1%</b>]</td>
	<td>10,727</td>
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
	<td>51.53% [51.3%-51.7%]</td>
	<td>292,060</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>46.11% [<b>43.0%</b>-49.2%]</td>
	<td>1,054</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.47% [<b>45.4%</b>-51.6%]</td>
	<td>1,044</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.56% [<b>46.3%</b>-50.9%]</td>
	<td>1,874</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.66% [<b>46.3%</b>-51.0%]</td>
	<td>1,792</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>48.78% [<b>46.6%</b>-51.0%]</td>
	<td>2,042</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>46.11% [43.0%-<b>49.2%</b>]</td>
	<td>1,054</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.53% [47.6%-<b>49.4%</b>]</td>
	<td>11,833</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>48.75% [47.3%-<b>50.2%</b>]</td>
	<td>4,576</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.19% [48.2%-<b>50.2%</b>]</td>
	<td>9,246</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.73% [47.2%-<b>50.3%</b>]</td>
	<td>4,172</td>
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
	<td>51.94% [51.6%-52.3%]</td>
	<td>103,172</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.71% [<b>43.2%</b>-50.3%]</td>
	<td>790</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.15% [<b>45.4%</b>-50.9%]</td>
	<td>1,294</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.98% [<b>46.4%</b>-51.5%]</td>
	<td>1,515</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>51.26% [<b>46.7%</b>-55.8%]</td>
	<td>478</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.40% [<b>46.7%</b>-50.1%]</td>
	<td>3,636</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.40% [46.7%-<b>50.1%</b>]</td>
	<td>3,636</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>48.70% [47.2%-<b>50.2%</b>]</td>
	<td>4,331</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.71% [43.2%-<b>50.3%</b>]</td>
	<td>790</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.15% [45.4%-<b>50.9%</b>]</td>
	<td>1,294</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>49.38% [47.3%-<b>51.4%</b>]</td>
	<td>2,337</td>
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
	<td>51.58% [51.4%-51.7%]</td>
	<td>463,775</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.57% [<b>44.1%</b>-49.0%]</td>
	<td>1,690</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.86% [<b>45.2%</b>-48.5%]</td>
	<td>3,769</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.87% [<b>47.0%</b>-48.7%]</td>
	<td>13,544</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>50.24% [<b>47.1%</b>-53.4%]</td>
	<td>1,027</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>49.73% [<b>47.1%</b>-52.3%]</td>
	<td>1,478</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.86% [45.2%-<b>48.5%</b>]</td>
	<td>3,769</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.87% [47.0%-<b>48.7%</b>]</td>
	<td>13,544</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.57% [44.1%-<b>49.0%</b>]</td>
	<td>1,690</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.37% [47.6%-<b>49.1%</b>]</td>
	<td>16,637</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.27% [47.2%-<b>49.3%</b>]</td>
	<td>9,468</td>
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
	<td>52.35% [52.1%-52.6%]</td>
	<td>143,099</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>49.87% [<b>44.7%</b>-55.0%]</td>
	<td>375</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>49.89% [<b>45.1%</b>-54.7%]</td>
	<td>439</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.12% [<b>45.9%</b>-50.3%]</td>
	<td>2,070</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.39% [<b>46.1%</b>-52.7%]</td>
	<td>901</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>51.65% [<b>46.2%</b>-57.1%]</td>
	<td>333</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>48.28% [46.5%-<b>50.1%</b>]</td>
	<td>3,078</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.57% [46.8%-<b>50.3%</b>]</td>
	<td>3,298</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.12% [45.9%-<b>50.3%</b>]</td>
	<td>2,070</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>49.17% [47.9%-<b>50.4%</b>]</td>
	<td>6,160</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.16% [47.4%-<b>50.9%</b>]</td>
	<td>3,291</td>
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
	<td>49.20% [49.1%-49.3%]</td>
	<td>467,372</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.01% [<b>44.9%</b>-47.1%]</td>
	<td>7,826</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>46.36% [<b>45.0%</b>-47.7%]</td>
	<td>5,533</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.09% [<b>45.3%</b>-48.9%]</td>
	<td>3,141</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.07% [<b>45.5%</b>-48.7%]</td>
	<td>3,960</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.47% [<b>45.5%</b>-47.4%]</td>
	<td>10,778</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.01% [44.9%-<b>47.1%</b>]</td>
	<td>7,826</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.59% [46.0%-<b>47.2%</b>]</td>
	<td>31,718</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.47% [45.5%-<b>47.4%</b>]</td>
	<td>10,778</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.69% [45.9%-<b>47.5%</b>]</td>
	<td>16,145</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>46.75% [46.0%-<b>47.5%</b>]</td>
	<td>17,720</td>
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
	<td>50.01% [49.8%-50.2%]</td>
	<td>270,007</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.55% [<b>43.4%</b>-47.7%]</td>
	<td>2,193</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.57% [<b>44.8%</b>-48.3%]</td>
	<td>3,182</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>46.71% [<b>45.0%</b>-48.4%]</td>
	<td>3,511</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>46.66% [<b>45.3%</b>-48.0%]</td>
	<td>5,187</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.95% [<b>45.5%</b>-50.4%]</td>
	<td>1,610</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.55% [43.4%-<b>47.7%</b>]</td>
	<td>2,193</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>46.87% [45.8%-<b>47.9%</b>]</td>
	<td>9,246</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>46.66% [45.3%-<b>48.0%</b>]</td>
	<td>5,187</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>46.79% [45.5%-<b>48.1%</b>]</td>
	<td>6,268</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.57% [44.8%-<b>48.3%</b>]</td>
	<td>3,182</td>
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
	<td>50.99% [50.8%-51.1%]</td>
	<td>458,665</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.00% [<b>44.2%</b>-49.8%]</td>
	<td>1,285</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.47% [<b>44.5%</b>-48.4%]</td>
	<td>2,692</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.51% [<b>45.9%</b>-49.1%]</td>
	<td>3,900</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.61% [<b>46.3%</b>-48.9%]</td>
	<td>6,074</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.59% [<b>46.6%</b>-48.6%]</td>
	<td>9,640</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.48% [46.7%-<b>48.3%</b>]</td>
	<td>16,491</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.47% [44.5%-<b>48.4%</b>]</td>
	<td>2,692</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.69% [46.9%-<b>48.5%</b>]</td>
	<td>16,398</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.59% [46.6%-<b>48.6%</b>]</td>
	<td>9,640</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.61% [46.3%-<b>48.9%</b>]</td>
	<td>6,074</td>
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
	<td>49.85% [49.7%-50.0%]</td>
	<td>453,054</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.33% [<b>43.5%</b>-47.2%]</td>
	<td>2,848</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>45.86% [<b>44.4%</b>-47.3%]</td>
	<td>4,614</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>45.92% [<b>44.9%</b>-47.0%]</td>
	<td>8,720</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.17% [<b>45.6%</b>-48.7%]</td>
	<td>4,066</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.90% [<b>45.6%</b>-48.2%]</td>
	<td>6,196</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>45.92% [44.9%-<b>47.0%</b>]</td>
	<td>8,720</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.33% [43.5%-<b>47.2%</b>]</td>
	<td>2,848</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>45.86% [44.4%-<b>47.3%</b>]</td>
	<td>4,614</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.01% [46.2%-<b>47.8%</b>]</td>
	<td>15,547</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.09% [46.3%-<b>47.9%</b>]</td>
	<td>15,809</td>
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
	<td>49.86% [49.7%-50.0%]</td>
	<td>777,118</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.85% [<b>43.5%</b>-46.2%]</td>
	<td>5,692</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.62% [<b>44.4%</b>-48.9%]</td>
	<td>1,999</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.13% [<b>45.0%</b>-47.3%]</td>
	<td>7,911</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.22% [<b>45.0%</b>-49.4%]</td>
	<td>2,065</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.88% [<b>45.5%</b>-48.3%]</td>
	<td>5,047</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.85% [43.5%-<b>46.2%</b>]</td>
	<td>5,692</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.14% [45.6%-<b>46.7%</b>]</td>
	<td>37,974</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.13% [45.0%-<b>47.3%</b>]</td>
	<td>7,911</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.87% [46.0%-<b>47.8%</b>]</td>
	<td>12,599</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.18% [46.4%-<b>48.0%</b>]</td>
	<td>16,599</td>
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
	<td>49.92% [49.7%-50.1%]</td>
	<td>252,426</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.80% [<b>44.0%</b>-51.6%]</td>
	<td>703</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.92% [<b>44.4%</b>-47.5%]</td>
	<td>4,059</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.70% [<b>45.1%</b>-50.3%]</td>
	<td>1,522</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.61% [<b>45.3%</b>-47.9%]</td>
	<td>5,640</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.69% [<b>45.5%</b>-49.9%]</td>
	<td>2,118</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.92% [44.4%-<b>47.5%</b>]</td>
	<td>4,059</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.61% [45.3%-<b>47.9%</b>]</td>
	<td>5,640</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.35% [46.2%-<b>48.5%</b>]</td>
	<td>7,951</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.59% [46.6%-<b>48.6%</b>]</td>
	<td>10,787</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>47.30% [45.9%-<b>48.7%</b>]</td>
	<td>5,349</td>
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
	<td>50.73% [50.5%-51.0%]</td>
	<td>194,973</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>47.43% [<b>44.0%</b>-50.9%]</td>
	<td>837</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.46% [<b>44.1%</b>-50.8%]</td>
	<td>906</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.93% [<b>44.2%</b>-49.7%]</td>
	<td>1,336</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.62% [<b>45.6%</b>-51.7%]</td>
	<td>1,088</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.91% [<b>45.7%</b>-54.1%]</td>
	<td>573</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.93% [44.2%-<b>49.7%</b>]</td>
	<td>1,336</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.29% [46.9%-<b>49.7%</b>]</td>
	<td>5,262</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>47.99% [46.2%-<b>49.7%</b>]</td>
	<td>3,236</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.77% [47.6%-<b>49.9%</b>]</td>
	<td>7,941</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.88% [47.8%-<b>49.9%</b>]</td>
	<td>8,746</td>
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
	<td>49.49% [49.3%-49.7%]</td>
	<td>319,056</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>46.58% [<b>43.5%</b>-49.6%]</td>
	<td>1,082</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.23% [<b>43.8%</b>-50.7%]</td>
	<td>847</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.15% [<b>44.9%</b>-51.4%]</td>
	<td>918</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.35% [<b>44.9%</b>-47.8%]</td>
	<td>4,768</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.24% [<b>45.0%</b>-49.5%]</td>
	<td>2,011</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.25% [45.2%-<b>47.3%</b>]</td>
	<td>9,166</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.36% [45.3%-<b>47.4%</b>]</td>
	<td>8,473</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.35% [44.9%-<b>47.8%</b>]</td>
	<td>4,768</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>46.95% [46.0%-<b>47.9%</b>]</td>
	<td>10,433</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.15% [46.1%-<b>48.2%</b>]</td>
	<td>9,892</td>
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
	<td>48.60% [48.5%-48.7%]</td>
	<td>828,791</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.35% [<b>43.3%</b>-47.4%]</td>
	<td>2,249</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.66% [<b>43.7%</b>-47.6%]</td>
	<td>2,534</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>44.73% [<b>44.1%</b>-45.4%]</td>
	<td>25,568</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>45.98% [<b>44.5%</b>-47.4%]</td>
	<td>4,759</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.70% [<b>44.7%</b>-48.7%]</td>
	<td>2,503</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>44.73% [44.1%-<b>45.4%</b>]</td>
	<td>25,568</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>46.32% [45.7%-<b>46.9%</b>]</td>
	<td>28,050</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.49% [45.9%-<b>47.0%</b>]</td>
	<td>32,161</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.41% [45.7%-<b>47.1%</b>]</td>
	<td>18,601</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>46.27% [45.3%-<b>47.2%</b>]</td>
	<td>10,741</td>
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
	<td>50.77% [50.5%-51.1%]</td>
	<td>106,327</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.09% [<b>41.5%</b>-48.7%]</td>
	<td>763</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>48.45% [<b>43.6%</b>-53.3%]</td>
	<td>419</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>47.34% [<b>44.5%</b>-50.1%]</td>
	<td>1,278</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>50.00% [<b>44.7%</b>-55.3%]</td>
	<td>358</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>49.10% [<b>45.2%</b>-53.0%]</td>
	<td>666</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.09% [41.5%-<b>48.7%</b>]</td>
	<td>763</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.16% [45.5%-<b>48.8%</b>]</td>
	<td>3,613</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>47.29% [45.8%-<b>48.8%</b>]</td>
	<td>4,206</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.84% [46.3%-<b>49.4%</b>]</td>
	<td>4,258</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.79% [45.7%-<b>49.8%</b>]</td>
	<td>2,358</td>
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
	<td>49.07% [48.9%-49.2%]</td>
	<td>350,497</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.83% [<b>43.1%</b>-46.6%]</td>
	<td>3,237</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>44.89% [<b>43.5%</b>-46.2%]</td>
	<td>5,458</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.21% [<b>44.2%</b>-50.3%]</td>
	<td>1,076</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.57% [<b>44.2%</b>-48.9%]</td>
	<td>1,765</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.78% [<b>44.3%</b>-47.3%]</td>
	<td>4,454</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>44.89% [43.5%-<b>46.2%</b>]</td>
	<td>5,458</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.83% [43.1%-<b>46.6%</b>]</td>
	<td>3,237</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.00% [45.1%-<b>46.9%</b>]</td>
	<td>11,956</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>46.33% [45.4%-<b>47.3%</b>]</td>
	<td>11,382</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.78% [44.3%-<b>47.3%</b>]</td>
	<td>4,454</td>
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
	<td>52.31% [52.0%-52.6%]</td>
	<td>134,303</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>44.79% [<b>42.5%</b>-47.1%]</td>
	<td>1,909</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.65% [<b>42.8%</b>-52.5%]</td>
	<td>426</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.02% [<b>44.1%</b>-49.9%]</td>
	<td>1,191</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.68% [<b>44.2%</b>-51.1%]</td>
	<td>841</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>51.45% [<b>46.1%</b>-56.8%]</td>
	<td>346</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>44.79% [42.5%-<b>47.1%</b>]</td>
	<td>1,909</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.02% [44.1%-<b>49.9%</b>]</td>
	<td>1,191</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.98% [47.3%-<b>50.6%</b>]</td>
	<td>3,614</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.50% [46.3%-<b>50.7%</b>]</td>
	<td>2,101</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.68% [44.2%-<b>51.1%</b>]</td>
	<td>841</td>
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
	<td>50.85% [50.6%-51.1%]</td>
	<td>143,372</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.25% [<b>42.6%</b>-51.9%]</td>
	<td>455</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>44.98% [<b>42.6%</b>-47.4%]</td>
	<td>1,754</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.79% [<b>43.5%</b>-48.1%]</td>
	<td>1,911</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.62% [<b>44.2%</b>-51.1%]</td>
	<td>842</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>47.14% [<b>45.3%</b>-49.0%]</td>
	<td>2,942</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>44.98% [42.6%-<b>47.4%</b>]</td>
	<td>1,754</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.79% [43.5%-<b>48.1%</b>]</td>
	<td>1,911</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.12% [45.7%-<b>48.6%</b>]</td>
	<td>4,805</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>47.14% [45.3%-<b>49.0%</b>]</td>
	<td>2,942</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.23% [45.3%-<b>49.1%</b>]</td>
	<td>2,799</td>
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
	<td>49.39% [49.1%-49.6%]</td>
	<td>169,395</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.51% [<b>41.8%</b>-47.2%]</td>
	<td>1,357</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.51% [<b>42.6%</b>-46.4%]</td>
	<td>2,703</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.56% [<b>42.8%</b>-48.3%]</td>
	<td>1,295</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.78% [<b>43.6%</b>-49.9%]</td>
	<td>994</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.28% [<b>44.2%</b>-48.4%]</td>
	<td>2,297</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.51% [42.6%-<b>46.4%</b>]</td>
	<td>2,703</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.51% [41.8%-<b>47.2%</b>]</td>
	<td>1,357</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>46.38% [45.1%-<b>47.7%</b>]</td>
	<td>5,766</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.72% [45.5%-<b>47.9%</b>]</td>
	<td>6,980</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>46.22% [44.5%-<b>48.0%</b>]</td>
	<td>3,237</td>
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
	<td>48.77% [48.6%-49.0%]</td>
	<td>206,903</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>44.94% [<b>42.5%</b>-47.4%]</td>
	<td>1,602</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.58% [<b>42.6%</b>-50.6%]</td>
	<td>614</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.27% [<b>42.8%</b>-49.7%]</td>
	<td>832</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.74% [<b>43.1%</b>-48.4%]</td>
	<td>1,421</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.66% [<b>43.5%</b>-51.8%]</td>
	<td>577</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>45.51% [44.3%-<b>46.7%</b>]</td>
	<td>7,185</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>45.31% [43.9%-<b>46.7%</b>]</td>
	<td>4,977</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>45.97% [44.9%-<b>47.0%</b>]</td>
	<td>8,650</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>45.71% [44.2%-<b>47.2%</b>]</td>
	<td>4,651</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>44.94% [42.5%-<b>47.4%</b>]</td>
	<td>1,602</td>
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
	<td>51.30% [51.0%-51.6%]</td>
	<td>83,784</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>45.57% [<b>42.3%</b>-48.8%]</td>
	<td>937</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.55% [<b>42.5%</b>-54.6%]</td>
	<td>276</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.70% [<b>42.6%</b>-50.8%]</td>
	<td>606</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>46.64% [<b>43.2%</b>-50.1%]</td>
	<td>819</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.91% [<b>43.9%</b>-51.9%]</td>
	<td>622</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>45.57% [42.3%-<b>48.8%</b>]</td>
	<td>937</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.69% [44.5%-<b>48.9%</b>]</td>
	<td>2,133</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.29% [45.3%-<b>49.3%</b>]</td>
	<td>2,489</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>48.35% [46.8%-<b>49.9%</b>]</td>
	<td>4,285</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>46.64% [43.2%-<b>50.1%</b>]</td>
	<td>819</td>
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
	<td>48.61% [48.5%-48.7%]</td>
	<td>851,836</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>43.60% [<b>41.5%</b>-45.7%]</td>
	<td>2,337</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.12% [<b>42.1%</b>-44.2%]</td>
	<td>8,860</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.70% [<b>43.3%</b>-46.1%]</td>
	<td>5,255</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.07% [<b>44.2%</b>-45.9%]</td>
	<td>13,784</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>45.42% [<b>44.9%</b>-46.0%]</td>
	<td>32,464</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.12% [42.1%-<b>44.2%</b>]</td>
	<td>8,860</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>43.60% [41.5%-<b>45.7%</b>]</td>
	<td>2,337</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>45.40% [44.9%-<b>45.9%</b>]</td>
	<td>38,362</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.07% [44.2%-<b>45.9%</b>]</td>
	<td>13,784</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>45.42% [44.9%-<b>46.0%</b>]</td>
	<td>32,464</td>
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
	<td>47.18% [47.0%-47.3%]</td>
	<td>420,123</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.72% [<b>41.8%</b>-47.6%]</td>
	<td>1,165</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.85% [<b>41.9%</b>-45.8%]</td>
	<td>2,577</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.55% [<b>42.4%</b>-46.7%]</td>
	<td>2,148</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.78% [<b>42.5%</b>-45.1%]</td>
	<td>5,792</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>43.66% [<b>42.6%</b>-44.7%]</td>
	<td>8,863</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>43.66% [42.6%-<b>44.7%</b>]</td>
	<td>8,863</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leona"></span> Leona</td>
	<td>44.02% [43.3%-<b>44.8%</b>]</td>
	<td>18,166</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.78% [42.5%-<b>45.1%</b>]</td>
	<td>5,792</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>44.68% [43.7%-<b>45.7%</b>]</td>
	<td>10,180</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.85% [41.9%-<b>45.8%</b>]</td>
	<td>2,577</td>
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
	<td>48.81% [48.7%-48.9%]</td>
	<td>597,044</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.78% [<b>41.3%</b>-46.3%]</td>
	<td>1,608</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>43.47% [<b>41.8%</b>-45.1%]</td>
	<td>3,552</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.64% [<b>43.2%</b>-46.1%]</td>
	<td>4,772</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.63% [<b>43.4%</b>-47.9%]</td>
	<td>1,966</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.80% [<b>44.2%</b>-47.4%]</td>
	<td>4,094</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>43.47% [41.8%-<b>45.1%</b>]</td>
	<td>3,552</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>45.15% [44.4%-<b>45.9%</b>]</td>
	<td>18,349</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.64% [43.2%-<b>46.1%</b>]</td>
	<td>4,772</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.78% [41.3%-<b>46.3%</b>]</td>
	<td>1,608</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leona"></span> Leona</td>
	<td>46.25% [45.7%-<b>46.8%</b>]</td>
	<td>28,779</td>
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
	<td>51.14% [50.7%-51.6%]</td>
	<td>50,684</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>43.82% [<b>37.6%</b>-50.1%]</td>
	<td>251</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.09% [<b>41.3%</b>-56.9%]</td>
	<td>165</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>46.23% [<b>41.9%</b>-50.6%]</td>
	<td>530</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.77% [<b>41.9%</b>-53.6%]</td>
	<td>291</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.55% [<b>43.2%</b>-53.9%]</td>
	<td>346</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.41% [44.9%-<b>49.9%</b>]</td>
	<td>1,639</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>43.82% [37.6%-<b>50.1%</b>]</td>
	<td>251</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.54% [45.0%-<b>50.1%</b>]</td>
	<td>1,527</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.76% [43.3%-<b>50.3%</b>]</td>
	<td>817</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>46.23% [41.9%-<b>50.6%</b>]</td>
	<td>530</td>
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
	<td>51.27% [50.8%-51.7%]</td>
	<td>52,984</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>45.33% [<b>38.5%</b>-52.1%]</td>
	<td>214</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.82% [<b>41.2%</b>-52.5%]</td>
	<td>314</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.26% [<b>42.1%</b>-54.5%]</td>
	<td>259</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.69% [<b>42.1%</b>-49.3%]</td>
	<td>766</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.14% [<b>42.3%</b>-54.0%]</td>
	<td>295</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>45.70% [43.1%-<b>48.3%</b>]</td>
	<td>1,431</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.69% [42.1%-<b>49.3%</b>]</td>
	<td>766</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>47.61% [44.5%-<b>50.7%</b>]</td>
	<td>1,065</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.84% [46.5%-<b>51.1%</b>]</td>
	<td>1,902</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.81% [44.1%-<b>51.6%</b>]</td>
	<td>707</td>
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
	<td>47.20% [47.0%-47.4%]</td>
	<td>394,587</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>41.93% [<b>39.4%</b>-44.4%]</td>
	<td>1,548</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>42.93% [<b>41.2%</b>-44.7%]</td>
	<td>3,175</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>42.43% [<b>41.6%</b>-43.3%]</td>
	<td>14,069</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>43.04% [<b>41.6%</b>-44.5%]</td>
	<td>4,835</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>42.86% [<b>42.0%</b>-43.7%]</td>
	<td>12,390</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>42.43% [41.6%-<b>43.3%</b>]</td>
	<td>14,069</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>42.86% [42.0%-<b>43.7%</b>]</td>
	<td>12,390</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>41.93% [39.4%-<b>44.4%</b>]</td>
	<td>1,548</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>43.04% [41.6%-<b>44.5%</b>]</td>
	<td>4,835</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>43.67% [42.7%-<b>44.6%</b>]</td>
	<td>11,564</td>
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
	<td>49.93% [49.5%-50.3%]</td>
	<td>66,539</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.84% [<b>39.6%</b>-54.1%]</td>
	<td>190</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.32% [<b>39.7%</b>-49.0%]</td>
	<td>458</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.01% [<b>40.8%</b>-47.2%]</td>
	<td>943</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.77% [<b>41.2%</b>-52.3%]</td>
	<td>325</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.97% [<b>41.6%</b>-52.3%]</td>
	<td>347</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.01% [40.8%-<b>47.2%</b>]</td>
	<td>943</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.04% [41.9%-<b>48.2%</b>]</td>
	<td>977</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.32% [39.7%-<b>49.0%</b>]</td>
	<td>458</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nautilus"></span> Nautilus</td>
	<td>47.76% [45.9%-<b>49.6%</b>]</td>
	<td>2,885</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.27% [44.7%-<b>49.8%</b>]</td>
	<td>1,504</td>
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
	<td>49.27% [49.0%-49.6%]</td>
	<td>104,023</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>42.43% [<b>37.5%</b>-47.4%]</td>
	<td>403</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>43.67% [<b>39.1%</b>-48.2%]</td>
	<td>474</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.64% [<b>42.9%</b>-48.3%]</td>
	<td>1,352</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.57% [<b>43.4%</b>-51.7%]</td>
	<td>576</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.16% [<b>43.7%</b>-48.6%]</td>
	<td>1,616</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>42.43% [37.5%-<b>47.4%</b>]</td>
	<td>403</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>46.13% [44.5%-<b>47.8%</b>]</td>
	<td>3,785</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>43.67% [39.1%-<b>48.2%</b>]</td>
	<td>474</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.64% [42.9%-<b>48.3%</b>]</td>
	<td>1,352</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.72% [44.8%-<b>48.6%</b>]</td>
	<td>2,789</td>
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
	<td>47.27% [46.9%-47.6%]</td>
	<td>88,293</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>41.75% [<b>36.0%</b>-47.5%]</td>
	<td>297</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>41.92% [<b>39.1%</b>-44.7%]</td>
	<td>1,226</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.83% [<b>39.7%</b>-52.0%]</td>
	<td>264</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.36% [<b>40.0%</b>-48.7%]</td>
	<td>514</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>45.38% [<b>40.3%</b>-50.4%]</td>
	<td>390</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>42.67% [40.6%-<b>44.7%</b>]</td>
	<td>2,360</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>41.92% [39.1%-<b>44.7%</b>]</td>
	<td>1,226</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.40% [41.4%-<b>45.4%</b>]</td>
	<td>2,433</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>43.74% [41.8%-<b>45.7%</b>]</td>
	<td>2,531</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>44.11% [42.1%-<b>46.1%</b>]</td>
	<td>2,555</td>
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
	<td>47.58% [47.3%-47.9%]</td>
	<td>118,657</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>42.38% [<b>38.9%</b>-45.9%]</td>
	<td>807</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.64% [<b>39.1%</b>-46.2%]</td>
	<td>781</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>43.87% [<b>39.5%</b>-48.2%]</td>
	<td>522</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>41.95% [<b>39.7%</b>-44.2%]</td>
	<td>1,931</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-bard"></span> Bard</td>
	<td>44.36% [<b>41.3%</b>-47.4%]</td>
	<td>1,064</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>41.95% [39.7%-<b>44.2%</b>]</td>
	<td>1,931</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>44.46% [43.2%-<b>45.7%</b>]</td>
	<td>6,143</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>42.38% [38.9%-<b>45.9%</b>]</td>
	<td>807</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.64% [39.1%-<b>46.2%</b>]</td>
	<td>781</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>44.88% [42.8%-<b>46.9%</b>]</td>
	<td>2,335</td>
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
	<td>49.68% [49.3%-50.1%]</td>
	<td>54,493</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>37.35% [<b>29.8%</b>-44.9%]</td>
	<td>166</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>44.79% [<b>37.0%</b>-52.6%]</td>
	<td>163</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>43.89% [<b>37.8%</b>-50.0%]</td>
	<td>262</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>45.59% [<b>38.6%</b>-52.6%]</td>
	<td>204</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.30% [<b>39.3%</b>-49.3%]</td>
	<td>395</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>37.35% [29.8%-<b>44.9%</b>]</td>
	<td>166</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rell"></span> Rell</td>
	<td>45.96% [43.1%-<b>48.8%</b>]</td>
	<td>1,251</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.20% [43.4%-<b>49.0%</b>]</td>
	<td>1,277</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>46.36% [43.6%-<b>49.2%</b>]</td>
	<td>1,277</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.30% [39.3%-<b>49.3%</b>]</td>
	<td>395</td>
</tr>
</table>

</details>
