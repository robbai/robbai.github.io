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

**Last update:** Patch 14.19

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
	<td>53.25% [53.1%-53.4%]</td>
	<td>920,408</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>48.54% [<b>47.3%</b>-49.8%]</td>
	<td>6,469</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>49.21% [<b>48.4%</b>-50.0%]</td>
	<td>14,289</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>49.06% [<b>48.6%</b>-49.6%]</td>
	<td>39,929</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>49.20% [<b>48.6%</b>-49.8%]</td>
	<td>29,964</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>49.31% [<b>48.8%</b>-49.8%]</td>
	<td>43,007</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>49.06% [48.6%-<b>49.6%</b>]</td>
	<td>39,929</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>49.20% [48.6%-<b>49.8%</b>]</td>
	<td>29,964</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>48.54% [47.3%-<b>49.8%</b>]</td>
	<td>6,469</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>49.31% [48.8%-<b>49.8%</b>]</td>
	<td>43,007</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>49.21% [48.4%-<b>50.0%</b>]</td>
	<td>14,289</td>
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
	<td>53.39% [53.3%-53.5%]</td>
	<td>557,310</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.26% [<b>48.3%</b>-50.2%]</td>
	<td>10,469</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>49.30% [<b>48.4%</b>-50.2%]</td>
	<td>11,280</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>49.99% [<b>48.4%</b>-51.5%]</td>
	<td>4,159</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>50.25% [<b>49.0%</b>-51.5%]</td>
	<td>5,986</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>49.91% [<b>49.0%</b>-50.8%]</td>
	<td>12,368</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.26% [48.3%-<b>50.2%</b>]</td>
	<td>10,469</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>49.30% [48.4%-<b>50.2%</b>]</td>
	<td>11,280</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>50.08% [49.5%-<b>50.7%</b>]</td>
	<td>27,837</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>49.91% [49.0%-<b>50.8%</b>]</td>
	<td>12,368</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>50.26% [49.7%-<b>50.8%</b>]</td>
	<td>32,225</td>
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
	<td>52.82% [52.7%-52.9%]</td>
	<td>779,587</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.24% [<b>45.7%</b>-48.7%]</td>
	<td>4,431</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.47% [<b>46.7%</b>-48.2%]</td>
	<td>18,838</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.97% [<b>47.4%</b>-48.6%]</td>
	<td>26,027</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.11% [<b>47.4%</b>-48.9%]</td>
	<td>17,530</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>48.83% [<b>47.9%</b>-49.8%]</td>
	<td>10,733</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.47% [46.7%-<b>48.2%</b>]</td>
	<td>18,838</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.97% [47.4%-<b>48.6%</b>]</td>
	<td>26,027</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.24% [45.7%-<b>48.7%</b>]</td>
	<td>4,431</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.11% [47.4%-<b>48.9%</b>]</td>
	<td>17,530</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>48.83% [47.9%-<b>49.8%</b>]</td>
	<td>10,733</td>
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
	<td>53.61% [53.5%-53.7%]</td>
	<td>555,581</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.15% [<b>46.4%</b>-47.9%]</td>
	<td>16,895</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>48.14% [<b>46.5%</b>-49.8%]</td>
	<td>3,808</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>49.14% [<b>47.6%</b>-50.7%]</td>
	<td>4,210</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.51% [<b>47.8%</b>-49.2%]</td>
	<td>19,619</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>49.86% [<b>48.0%</b>-51.8%]</td>
	<td>2,764</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.15% [46.4%-<b>47.9%</b>]</td>
	<td>16,895</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.51% [47.8%-<b>49.2%</b>]</td>
	<td>19,619</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aatrox"></span> Aatrox</td>
	<td>48.93% [48.3%-<b>49.6%</b>]</td>
	<td>22,109</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>49.03% [48.4%-<b>49.7%</b>]</td>
	<td>25,374</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kled"></span> Kled</td>
	<td>48.14% [46.5%-<b>49.8%</b>]</td>
	<td>3,808</td>
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
	<td>52.17% [52.0%-52.3%]</td>
	<td>380,120</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.17% [<b>45.5%</b>-46.8%]</td>
	<td>21,673</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>49.04% [<b>46.5%</b>-51.6%]</td>
	<td>1,558</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.86% [<b>46.9%</b>-48.8%]</td>
	<td>11,802</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>49.19% [<b>47.2%</b>-51.2%]</td>
	<td>2,480</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>48.27% [<b>47.3%</b>-49.3%]</td>
	<td>10,198</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.17% [45.5%-<b>46.8%</b>]</td>
	<td>21,673</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>47.86% [46.9%-<b>48.8%</b>]</td>
	<td>11,802</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>48.27% [47.3%-<b>49.3%</b>]</td>
	<td>10,198</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>49.02% [48.2%-<b>49.9%</b>]</td>
	<td>13,826</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>49.11% [48.1%-<b>50.1%</b>]</td>
	<td>9,594</td>
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
	<td>50.78% [50.7%-50.9%]</td>
	<td>665,906</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.43% [<b>45.7%</b>-49.1%]</td>
	<td>3,437</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.84% [<b>46.2%</b>-47.4%]</td>
	<td>27,205</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>48.26% [<b>46.7%</b>-49.8%]</td>
	<td>4,345</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.48% [<b>46.8%</b>-48.2%]</td>
	<td>21,735</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.04% [<b>46.9%</b>-49.1%]</td>
	<td>8,247</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.84% [46.2%-<b>47.4%</b>]</td>
	<td>27,205</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.46% [47.0%-<b>48.0%</b>]</td>
	<td>40,432</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.48% [46.8%-<b>48.2%</b>]</td>
	<td>21,735</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.86% [47.2%-<b>48.5%</b>]</td>
	<td>26,794</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>48.38% [47.7%-<b>49.1%</b>]</td>
	<td>19,003</td>
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
	<td>52.48% [52.2%-52.8%]</td>
	<td>136,217</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>48.74% [<b>45.4%</b>-52.1%]</td>
	<td>874</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.98% [<b>45.5%</b>-48.4%]</td>
	<td>4,717</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.23% [<b>45.8%</b>-48.7%]</td>
	<td>4,722</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>48.06% [<b>45.8%</b>-50.3%]</td>
	<td>1,931</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.99% [<b>45.8%</b>-50.2%]</td>
	<td>2,065</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>46.98% [45.5%-<b>48.4%</b>]</td>
	<td>4,717</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.23% [45.8%-<b>48.7%</b>]</td>
	<td>4,722</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.49% [47.3%-<b>49.6%</b>]</td>
	<td>7,447</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.99% [45.8%-<b>50.2%</b>]</td>
	<td>2,065</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>48.06% [45.8%-<b>50.3%</b>]</td>
	<td>1,931</td>
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
	<td>51.51% [51.4%-51.7%]</td>
	<td>392,285</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.72% [<b>44.8%</b>-46.6%]</td>
	<td>12,958</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.85% [<b>45.1%</b>-48.6%]</td>
	<td>3,131</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.91% [<b>45.9%</b>-47.9%]</td>
	<td>10,135</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.03% [<b>46.4%</b>-47.7%]</td>
	<td>21,843</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.40% [<b>46.4%</b>-50.4%]</td>
	<td>2,411</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.72% [44.8%-<b>46.6%</b>]</td>
	<td>12,958</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.03% [46.4%-<b>47.7%</b>]</td>
	<td>21,843</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.91% [45.9%-<b>47.9%</b>]</td>
	<td>10,135</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.85% [45.1%-<b>48.6%</b>]</td>
	<td>3,131</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>48.40% [47.5%-<b>49.3%</b>]</td>
	<td>11,096</td>
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
	<td>51.25% [51.1%-51.4%]</td>
	<td>250,394</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.69% [<b>43.6%</b>-45.8%]</td>
	<td>7,758</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.73% [<b>44.9%</b>-48.5%]</td>
	<td>3,039</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.26% [<b>45.4%</b>-47.1%]</td>
	<td>14,205</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>48.91% [<b>46.2%</b>-51.6%]</td>
	<td>1,370</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>48.44% [<b>46.3%</b>-50.6%]</td>
	<td>2,110</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.69% [43.6%-<b>45.8%</b>]</td>
	<td>7,758</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.26% [45.4%-<b>47.1%</b>]</td>
	<td>14,205</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.73% [44.9%-<b>48.5%</b>]</td>
	<td>3,039</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>48.52% [47.5%-<b>49.6%</b>]</td>
	<td>9,401</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>48.21% [46.8%-<b>49.6%</b>]</td>
	<td>5,009</td>
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
	<td>50.65% [50.5%-50.8%]</td>
	<td>512,540</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.04% [<b>44.4%</b>-45.7%]</td>
	<td>21,320</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.92% [<b>44.9%</b>-47.0%]</td>
	<td>8,977</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.23% [<b>45.0%</b>-47.5%]</td>
	<td>6,134</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.93% [<b>45.1%</b>-46.8%]</td>
	<td>13,352</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.44% [<b>45.4%</b>-47.5%]</td>
	<td>8,878</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.04% [44.4%-<b>45.7%</b>]</td>
	<td>21,320</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.93% [45.1%-<b>46.8%</b>]</td>
	<td>13,352</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.92% [44.9%-<b>47.0%</b>]</td>
	<td>8,977</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.44% [45.4%-<b>47.5%</b>]</td>
	<td>8,878</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.23% [45.0%-<b>47.5%</b>]</td>
	<td>6,134</td>
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
	<td>51.66% [51.5%-51.8%]</td>
	<td>563,594</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.55% [<b>44.4%</b>-48.7%]</td>
	<td>2,191</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>46.83% [<b>44.8%</b>-48.8%]</td>
	<td>2,462</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.88% [<b>45.3%</b>-48.5%]</td>
	<td>3,799</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.21% [<b>46.4%</b>-48.0%]</td>
	<td>16,805</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.37% [<b>46.5%</b>-48.3%]</td>
	<td>12,160</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.21% [46.4%-<b>48.0%</b>]</td>
	<td>16,805</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.37% [46.5%-<b>48.3%</b>]</td>
	<td>12,160</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.88% [45.3%-<b>48.5%</b>]</td>
	<td>3,799</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.55% [44.4%-<b>48.7%</b>]</td>
	<td>2,191</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>48.19% [47.5%-<b>48.8%</b>]</td>
	<td>24,240</td>
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
	<td>52.50% [52.2%-52.8%]</td>
	<td>103,130</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.91% [<b>41.1%</b>-48.7%]</td>
	<td>688</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.98% [<b>44.7%</b>-51.3%]</td>
	<td>915</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.74% [<b>44.9%</b>-48.5%]</td>
	<td>3,100</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.75% [<b>45.2%</b>-48.3%]</td>
	<td>4,075</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>49.92% [<b>46.0%</b>-53.9%]</td>
	<td>647</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.75% [45.2%-<b>48.3%</b>]</td>
	<td>4,075</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.74% [44.9%-<b>48.5%</b>]</td>
	<td>3,100</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.91% [41.1%-<b>48.7%</b>]</td>
	<td>688</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.69% [46.7%-<b>50.7%</b>]</td>
	<td>2,413</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.98% [44.7%-<b>51.3%</b>]</td>
	<td>915</td>
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
	<td>49.58% [49.5%-49.7%]</td>
	<td>810,114</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>45.79% [<b>44.1%</b>-47.4%]</td>
	<td>3,632</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.12% [<b>44.4%</b>-45.8%]</td>
	<td>19,544</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>45.05% [<b>44.5%</b>-45.6%]</td>
	<td>28,848</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.47% [<b>44.7%</b>-46.2%]</td>
	<td>17,411</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.23% [<b>44.8%</b>-45.7%]</td>
	<td>47,028</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>45.05% [44.5%-<b>45.6%</b>]</td>
	<td>28,848</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.23% [44.8%-<b>45.7%</b>]</td>
	<td>47,028</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.12% [44.4%-<b>45.8%</b>]</td>
	<td>19,544</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.47% [44.7%-<b>46.2%</b>]</td>
	<td>17,411</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>46.17% [45.5%-<b>46.8%</b>]</td>
	<td>21,792</td>
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
	<td>51.36% [51.2%-51.5%]</td>
	<td>295,784</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.20% [<b>42.3%</b>-44.1%]</td>
	<td>11,610</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.15% [<b>44.4%</b>-45.9%]</td>
	<td>16,674</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.40% [<b>45.6%</b>-51.2%]</td>
	<td>1,312</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>46.95% [<b>45.7%</b>-48.2%]</td>
	<td>6,026</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.44% [<b>46.3%</b>-48.6%]</td>
	<td>7,236</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.20% [42.3%-<b>44.1%</b>]</td>
	<td>11,610</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.15% [44.4%-<b>45.9%</b>]</td>
	<td>16,674</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>46.95% [45.7%-<b>48.2%</b>]</td>
	<td>6,026</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.44% [46.3%-<b>48.6%</b>]</td>
	<td>7,236</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>47.85% [46.9%-<b>48.8%</b>]</td>
	<td>11,864</td>
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
	<td>52.20% [52.0%-52.4%]</td>
	<td>342,646</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.16% [<b>43.3%</b>-47.1%]</td>
	<td>2,766</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.05% [<b>44.0%</b>-46.1%]</td>
	<td>9,484</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>47.71% [<b>45.6%</b>-49.8%]</td>
	<td>2,209</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.52% [<b>45.8%</b>-47.2%]</td>
	<td>20,341</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.06% [<b>46.2%</b>-47.9%]</td>
	<td>13,214</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.05% [44.0%-<b>46.1%</b>]</td>
	<td>9,484</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.16% [43.3%-<b>47.1%</b>]</td>
	<td>2,766</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.52% [45.8%-<b>47.2%</b>]</td>
	<td>20,341</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.06% [46.2%-<b>47.9%</b>]</td>
	<td>13,214</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>47.40% [46.4%-<b>48.4%</b>]</td>
	<td>9,979</td>
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
	<td>51.17% [51.0%-51.4%]</td>
	<td>273,562</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.73% [<b>43.4%</b>-50.1%]</td>
	<td>903</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>46.88% [<b>44.0%</b>-49.7%]</td>
	<td>1,216</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>47.20% [<b>44.6%</b>-49.8%]</td>
	<td>1,449</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.69% [<b>45.0%</b>-50.4%]</td>
	<td>1,409</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>48.30% [<b>46.1%</b>-50.5%]</td>
	<td>2,002</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.47% [46.5%-<b>48.4%</b>]</td>
	<td>10,554</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.91% [47.1%-<b>48.7%</b>]</td>
	<td>15,572</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.15% [47.3%-<b>49.0%</b>]</td>
	<td>13,519</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.81% [46.5%-<b>49.1%</b>]</td>
	<td>5,886</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>46.88% [44.0%-<b>49.7%</b>]</td>
	<td>1,216</td>
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
	<td>49.31% [49.2%-49.4%]</td>
	<td>806,216</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.37% [<b>43.1%</b>-45.6%]</td>
	<td>6,336</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.42% [<b>43.8%</b>-45.1%]</td>
	<td>22,944</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.34% [<b>44.0%</b>-46.7%]</td>
	<td>5,668</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.99% [<b>45.3%</b>-46.7%]</td>
	<td>21,736</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>46.37% [<b>45.6%</b>-47.1%]</td>
	<td>19,132</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.42% [43.8%-<b>45.1%</b>]</td>
	<td>22,944</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.37% [43.1%-<b>45.6%</b>]</td>
	<td>6,336</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.34% [44.0%-<b>46.7%</b>]</td>
	<td>5,668</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.99% [45.3%-<b>46.7%</b>]</td>
	<td>21,736</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>46.37% [45.6%-<b>47.1%</b>]</td>
	<td>19,132</td>
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
	<td>50.91% [50.7%-51.1%]</td>
	<td>178,746</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.02% [<b>43.6%</b>-46.5%]</td>
	<td>4,742</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.17% [<b>43.6%</b>-46.7%]</td>
	<td>4,153</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.78% [<b>43.8%</b>-49.7%]</td>
	<td>1,150</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.72% [<b>44.3%</b>-49.2%]</td>
	<td>1,644</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>46.89% [<b>44.4%</b>-49.4%]</td>
	<td>1,642</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>45.02% [43.6%-<b>46.5%</b>]</td>
	<td>4,742</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.17% [43.6%-<b>46.7%</b>]</td>
	<td>4,153</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.36% [45.2%-<b>47.5%</b>]</td>
	<td>7,733</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.53% [44.6%-<b>48.4%</b>]</td>
	<td>2,813</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.72% [44.3%-<b>49.2%</b>]</td>
	<td>1,644</td>
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
	<td>51.98% [51.8%-52.1%]</td>
	<td>490,101</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.56% [<b>42.8%</b>-44.3%]</td>
	<td>18,219</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.10% [<b>43.5%</b>-44.7%]</td>
	<td>31,245</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.61% [<b>44.2%</b>-49.0%]</td>
	<td>1,783</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.53% [<b>45.0%</b>-48.0%]</td>
	<td>4,526</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>47.90% [<b>46.2%</b>-49.6%]</td>
	<td>3,380</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.56% [42.8%-<b>44.3%</b>]</td>
	<td>18,219</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.10% [43.5%-<b>44.7%</b>]</td>
	<td>31,245</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.53% [45.0%-<b>48.0%</b>]</td>
	<td>4,526</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.41% [46.5%-<b>48.3%</b>]</td>
	<td>12,572</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.61% [44.2%-<b>49.0%</b>]</td>
	<td>1,783</td>
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
	<td>50.16% [50.0%-50.3%]</td>
	<td>307,785</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.00% [<b>43.0%</b>-45.0%]</td>
	<td>9,622</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.31% [<b>43.5%</b>-47.1%]</td>
	<td>3,004</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>46.40% [<b>43.9%</b>-48.9%]</td>
	<td>1,653</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.87% [<b>44.1%</b>-45.7%]</td>
	<td>15,096</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>45.96% [<b>44.9%</b>-47.0%]</td>
	<td>9,504</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.00% [43.0%-<b>45.0%</b>]</td>
	<td>9,622</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.87% [44.1%-<b>45.7%</b>]</td>
	<td>15,096</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>45.96% [44.9%-<b>47.0%</b>]</td>
	<td>9,504</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.31% [43.5%-<b>47.1%</b>]</td>
	<td>3,004</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.03% [46.0%-<b>48.0%</b>]</td>
	<td>10,240</td>
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
	<td>49.48% [49.3%-49.7%]</td>
	<td>330,002</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.16% [<b>42.9%</b>-47.5%]</td>
	<td>1,860</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.46% [<b>43.4%</b>-45.5%]</td>
	<td>9,220</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.04% [<b>44.1%</b>-46.0%]</td>
	<td>11,907</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.63% [<b>44.6%</b>-46.7%]</td>
	<td>9,157</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.63% [<b>45.3%</b>-47.9%]</td>
	<td>5,958</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.46% [43.4%-<b>45.5%</b>]</td>
	<td>9,220</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>45.04% [44.1%-<b>46.0%</b>]</td>
	<td>11,907</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>45.63% [44.6%-<b>46.7%</b>]</td>
	<td>9,157</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.40% [45.6%-<b>47.2%</b>]</td>
	<td>14,245</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.55% [45.7%-<b>47.4%</b>]</td>
	<td>13,014</td>
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
	<td>51.33% [51.1%-51.6%]</td>
	<td>175,205</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.95% [<b>40.0%</b>-45.9%]</td>
	<td>1,134</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.44% [<b>43.4%</b>-49.5%]</td>
	<td>1,081</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.40% [<b>43.8%</b>-47.0%]</td>
	<td>3,892</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>48.75% [<b>44.7%</b>-52.8%]</td>
	<td>599</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>47.72% [<b>45.2%</b>-50.2%]</td>
	<td>1,599</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.95% [40.0%-<b>45.9%</b>]</td>
	<td>1,134</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.40% [43.8%-<b>47.0%</b>]</td>
	<td>3,892</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.99% [45.8%-<b>48.2%</b>]</td>
	<td>6,550</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.24% [45.9%-<b>48.6%</b>]</td>
	<td>5,406</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.44% [43.4%-<b>49.5%</b>]</td>
	<td>1,081</td>
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
	<td>49.91% [49.8%-50.1%]</td>
	<td>478,812</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.97% [<b>42.2%</b>-43.8%]</td>
	<td>15,689</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.00% [<b>43.3%</b>-44.7%]</td>
	<td>17,586</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.68% [<b>43.7%</b>-45.7%]</td>
	<td>10,087</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>45.00% [<b>44.0%</b>-46.0%]</td>
	<td>9,995</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.64% [<b>44.5%</b>-48.8%]</td>
	<td>2,099</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.97% [42.2%-<b>43.8%</b>]</td>
	<td>15,689</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.00% [43.3%-<b>44.7%</b>]</td>
	<td>17,586</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>44.68% [43.7%-<b>45.7%</b>]</td>
	<td>10,087</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>45.00% [44.0%-<b>46.0%</b>]</td>
	<td>9,995</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.65% [45.0%-<b>46.3%</b>]</td>
	<td>26,929</td>
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
	<td>47.42% [47.3%-47.5%]</td>
	<td>710,099</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.15% [<b>42.9%</b>-45.4%]</td>
	<td>6,576</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.03% [<b>43.2%</b>-44.9%]</td>
	<td>14,232</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.74% [<b>43.3%</b>-46.2%]</td>
	<td>4,696</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.18% [<b>44.0%</b>-46.3%]</td>
	<td>7,495</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.87% [<b>44.1%</b>-45.6%]</td>
	<td>17,217</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.03% [43.2%-<b>44.9%</b>]</td>
	<td>14,232</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>44.76% [44.2%-<b>45.3%</b>]</td>
	<td>32,625</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>44.72% [44.1%-<b>45.3%</b>]</td>
	<td>27,303</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.15% [42.9%-<b>45.4%</b>]</td>
	<td>6,576</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.03% [44.5%-<b>45.6%</b>]</td>
	<td>29,569</td>
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
	<td>48.90% [48.8%-49.0%]</td>
	<td>501,375</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>41.72% [<b>40.9%</b>-42.5%]</td>
	<td>14,606</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.83% [<b>43.0%</b>-44.7%]</td>
	<td>12,872</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.72% [<b>44.1%</b>-45.3%]</td>
	<td>28,009</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>45.24% [<b>44.3%</b>-46.2%]</td>
	<td>10,812</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>46.20% [<b>44.4%</b>-48.0%]</td>
	<td>3,039</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>41.72% [40.9%-<b>42.5%</b>]</td>
	<td>14,606</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.83% [43.0%-<b>44.7%</b>]</td>
	<td>12,872</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.72% [44.1%-<b>45.3%</b>]</td>
	<td>28,009</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>45.24% [44.3%-<b>46.2%</b>]</td>
	<td>10,812</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.73% [45.0%-<b>46.5%</b>]</td>
	<td>18,128</td>
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
	<td>50.66% [50.4%-50.9%]</td>
	<td>147,657</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.73% [<b>42.2%</b>-45.2%]</td>
	<td>4,420</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.29% [<b>42.9%</b>-45.7%]</td>
	<td>5,216</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>45.25% [<b>43.3%</b>-47.2%]</td>
	<td>2,497</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.88% [<b>43.7%</b>-46.0%]</td>
	<td>7,273</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>47.72% [<b>43.9%</b>-51.5%]</td>
	<td>702</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.73% [42.2%-<b>45.2%</b>]</td>
	<td>4,420</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.29% [42.9%-<b>45.7%</b>]</td>
	<td>5,216</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.88% [43.7%-<b>46.0%</b>]</td>
	<td>7,273</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>45.25% [43.3%-<b>47.2%</b>]</td>
	<td>2,497</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>45.84% [44.0%-<b>47.7%</b>]</td>
	<td>2,825</td>
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
	<td>49.12% [49.0%-49.3%]</td>
	<td>369,004</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.16% [<b>42.3%</b>-44.0%]</td>
	<td>13,451</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.39% [<b>42.9%</b>-45.9%]</td>
	<td>4,508</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.35% [<b>43.3%</b>-47.4%]</td>
	<td>2,322</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>46.05% [<b>43.7%</b>-48.4%]</td>
	<td>1,850</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.40% [<b>43.9%</b>-46.9%]</td>
	<td>4,628</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.16% [42.3%-<b>44.0%</b>]</td>
	<td>13,451</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.39% [42.9%-<b>45.9%</b>]</td>
	<td>4,508</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.71% [44.8%-<b>46.6%</b>]</td>
	<td>13,169</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.40% [43.9%-<b>46.9%</b>]</td>
	<td>4,628</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.08% [44.9%-<b>47.2%</b>]</td>
	<td>7,403</td>
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
	<td>48.89% [48.8%-49.0%]</td>
	<td>768,638</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.96% [<b>42.4%</b>-43.5%]</td>
	<td>29,805</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.31% [<b>42.7%</b>-43.9%]</td>
	<td>24,511</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.15% [<b>45.0%</b>-47.3%]</td>
	<td>7,042</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.34% [<b>45.3%</b>-47.4%]</td>
	<td>8,488</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>46.26% [<b>45.3%</b>-47.2%]</td>
	<td>11,130</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.96% [42.4%-<b>43.5%</b>]</td>
	<td>29,805</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.31% [42.7%-<b>43.9%</b>]</td>
	<td>24,511</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.46% [45.9%-<b>47.0%</b>]</td>
	<td>28,889</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.36% [45.6%-<b>47.1%</b>]</td>
	<td>19,731</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>46.26% [45.3%-<b>47.2%</b>]</td>
	<td>11,130</td>
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
	<td>49.97% [49.7%-50.2%]</td>
	<td>203,270</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>44.62% [<b>41.2%</b>-48.1%]</td>
	<td>827</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.54% [<b>42.6%</b>-44.5%]</td>
	<td>10,868</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.01% [<b>43.3%</b>-46.7%]</td>
	<td>3,515</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.08% [<b>43.5%</b>-50.7%]</td>
	<td>771</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.87% [<b>43.5%</b>-46.2%]</td>
	<td>5,609</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.54% [42.6%-<b>44.5%</b>]</td>
	<td>10,868</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.84% [43.6%-<b>46.1%</b>]</td>
	<td>6,017</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.87% [43.5%-<b>46.2%</b>]</td>
	<td>5,609</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.01% [43.3%-<b>46.7%</b>]</td>
	<td>3,515</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>46.87% [45.7%-<b>48.0%</b>]</td>
	<td>7,256</td>
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
	<td>48.40% [48.2%-48.6%]</td>
	<td>237,074</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.16% [<b>40.0%</b>-42.3%]</td>
	<td>7,826</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.23% [<b>42.3%</b>-44.2%]</td>
	<td>10,923</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.45% [<b>42.8%</b>-46.1%]</td>
	<td>3,822</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.15% [<b>42.9%</b>-45.4%]</td>
	<td>6,679</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.95% [<b>43.3%</b>-46.6%]</td>
	<td>3,513</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.16% [40.0%-<b>42.3%</b>]</td>
	<td>7,826</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.23% [42.3%-<b>44.2%</b>]</td>
	<td>10,923</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.15% [42.9%-<b>45.4%</b>]</td>
	<td>6,679</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.45% [42.8%-<b>46.1%</b>]</td>
	<td>3,822</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.95% [43.3%-<b>46.6%</b>]</td>
	<td>3,513</td>
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
	<td>50.69% [50.4%-51.0%]</td>
	<td>92,977</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>47.30% [<b>42.1%</b>-52.5%]</td>
	<td>370</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>47.51% [<b>42.3%</b>-52.8%]</td>
	<td>362</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.59% [<b>43.4%</b>-51.8%]</td>
	<td>561</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>46.95% [<b>43.5%</b>-50.4%]</td>
	<td>820</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.57% [<b>44.1%</b>-47.0%]</td>
	<td>4,867</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.57% [44.1%-<b>47.0%</b>]</td>
	<td>4,867</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.72% [46.0%-<b>49.5%</b>]</td>
	<td>3,284</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>48.01% [46.4%-<b>49.6%</b>]</td>
	<td>3,960</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>47.58% [45.5%-<b>49.7%</b>]</td>
	<td>2,310</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.55% [45.2%-<b>49.9%</b>]</td>
	<td>1,779</td>
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
	<td>49.60% [49.5%-49.7%]</td>
	<td>689,060</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.01% [<b>41.3%</b>-42.7%]</td>
	<td>21,959</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.63% [<b>41.9%</b>-43.4%]</td>
	<td>18,772</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.79% [<b>43.4%</b>-46.2%]</td>
	<td>4,983</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.27% [<b>43.7%</b>-46.8%]</td>
	<td>4,272</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.16% [<b>44.1%</b>-46.2%]</td>
	<td>9,070</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.01% [41.3%-<b>42.7%</b>]</td>
	<td>21,959</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.63% [41.9%-<b>43.4%</b>]</td>
	<td>18,772</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.79% [43.4%-<b>46.2%</b>]</td>
	<td>4,983</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.16% [44.1%-<b>46.2%</b>]</td>
	<td>9,070</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.13% [45.6%-<b>46.7%</b>]</td>
	<td>36,353</td>
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
	<td>49.00% [48.8%-49.2%]</td>
	<td>182,210</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.88% [<b>41.4%</b>-44.4%]</td>
	<td>4,454</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.74% [<b>41.9%</b>-47.6%]</td>
	<td>1,189</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.90% [<b>42.0%</b>-47.8%]</td>
	<td>1,167</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.38% [<b>42.0%</b>-44.7%]</td>
	<td>5,343</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.62% [<b>43.0%</b>-46.2%]</td>
	<td>3,906</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.88% [41.4%-<b>44.4%</b>]</td>
	<td>4,454</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.38% [42.0%-<b>44.7%</b>]</td>
	<td>5,343</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.62% [43.0%-<b>46.2%</b>]</td>
	<td>3,906</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.33% [43.8%-<b>46.9%</b>]</td>
	<td>4,158</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.80% [44.7%-<b>46.9%</b>]</td>
	<td>8,337</td>
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
	<td>48.06% [47.9%-48.3%]</td>
	<td>272,721</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>42.49% [<b>41.3%</b>-43.7%]</td>
	<td>7,026</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.06% [<b>41.6%</b>-48.6%]</td>
	<td>810</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.79% [<b>41.8%</b>-43.8%]</td>
	<td>10,461</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.74% [<b>41.9%</b>-47.5%]</td>
	<td>1,254</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.24% [<b>42.4%</b>-44.1%]</td>
	<td>13,188</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>42.49% [41.3%-<b>43.7%</b>]</td>
	<td>7,026</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.79% [41.8%-<b>43.8%</b>]</td>
	<td>10,461</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.24% [42.4%-<b>44.1%</b>]</td>
	<td>13,188</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.92% [42.7%-<b>45.1%</b>]</td>
	<td>7,193</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.03% [43.9%-<b>46.2%</b>]</td>
	<td>7,631</td>
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
	<td>47.46% [47.3%-47.6%]</td>
	<td>286,042</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.21% [<b>41.1%</b>-43.4%]</td>
	<td>7,326</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.90% [<b>41.4%</b>-44.4%]</td>
	<td>4,520</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>43.17% [<b>42.1%</b>-44.2%]</td>
	<td>8,607</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>43.59% [<b>42.2%</b>-45.0%]</td>
	<td>5,136</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.53% [<b>42.6%</b>-44.5%]</td>
	<td>10,255</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.21% [41.1%-<b>43.4%</b>]</td>
	<td>7,326</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>43.17% [42.1%-<b>44.2%</b>]</td>
	<td>8,607</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.90% [41.4%-<b>44.4%</b>]</td>
	<td>4,520</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.53% [42.6%-<b>44.5%</b>]</td>
	<td>10,255</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>43.59% [42.2%-<b>45.0%</b>]</td>
	<td>5,136</td>
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
	<td>48.23% [48.0%-48.5%]</td>
	<td>134,682</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>41.89% [<b>39.9%</b>-43.9%]</td>
	<td>2,528</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.05% [<b>41.3%</b>-44.8%]</td>
	<td>3,043</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.99% [<b>41.6%</b>-48.3%]</td>
	<td>878</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.67% [<b>42.0%</b>-45.3%]</td>
	<td>3,678</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.36% [<b>42.1%</b>-46.6%]</td>
	<td>1,943</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>41.89% [39.9%-<b>43.9%</b>]</td>
	<td>2,528</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>43.05% [41.3%-<b>44.8%</b>]</td>
	<td>3,043</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.67% [42.0%-<b>45.3%</b>]</td>
	<td>3,678</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.91% [42.1%-<b>45.7%</b>]</td>
	<td>3,047</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>45.01% [43.5%-<b>46.5%</b>]</td>
	<td>4,590</td>
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
	<td>48.01% [47.8%-48.2%]</td>
	<td>244,417</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.11% [<b>40.7%</b>-43.5%]</td>
	<td>5,165</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.35% [<b>41.1%</b>-43.6%]</td>
	<td>6,423</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.00% [<b>41.4%</b>-44.6%]</td>
	<td>3,651</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.87% [<b>41.8%</b>-45.9%]</td>
	<td>2,380</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.78% [<b>42.1%</b>-47.4%]</td>
	<td>1,398</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.11% [40.7%-<b>43.5%</b>]</td>
	<td>5,165</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.35% [41.1%-<b>43.6%</b>]</td>
	<td>6,423</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.00% [41.4%-<b>44.6%</b>]</td>
	<td>3,651</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.62% [42.5%-<b>44.7%</b>]</td>
	<td>8,423</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>44.20% [43.4%-<b>45.0%</b>]</td>
	<td>13,724</td>
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
	<td>47.75% [47.5%-48.0%]</td>
	<td>237,617</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.21% [<b>41.0%</b>-45.4%]</td>
	<td>1,995</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.07% [<b>41.1%</b>-43.0%]</td>
	<td>10,405</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.15% [<b>41.4%</b>-46.9%]</td>
	<td>1,282</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>44.41% [<b>41.9%</b>-47.0%]</td>
	<td>1,511</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>43.98% [<b>41.9%</b>-46.1%]</td>
	<td>2,183</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.07% [41.1%-<b>43.0%</b>]</td>
	<td>10,405</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.21% [41.0%-<b>45.4%</b>]</td>
	<td>1,995</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.39% [43.1%-<b>45.7%</b>]</td>
	<td>6,197</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.23% [42.5%-<b>45.9%</b>]</td>
	<td>3,475</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>44.92% [43.9%-<b>46.0%</b>]</td>
	<td>8,712</td>
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
	<td>48.82% [48.5%-49.1%]</td>
	<td>99,801</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.54% [<b>39.7%</b>-43.4%]</td>
	<td>2,797</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.54% [<b>41.1%</b>-46.0%]</td>
	<td>1,594</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.59% [<b>41.2%</b>-46.0%]</td>
	<td>1,654</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.07% [<b>41.4%</b>-50.7%]</td>
	<td>458</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>43.73% [<b>41.5%</b>-46.0%]</td>
	<td>1,946</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.54% [39.7%-<b>43.4%</b>]</td>
	<td>2,797</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.48% [41.9%-<b>45.0%</b>]</td>
	<td>4,186</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>44.09% [42.4%-<b>45.8%</b>]</td>
	<td>3,563</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.97% [42.1%-<b>45.8%</b>]</td>
	<td>2,886</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>43.73% [41.5%-<b>46.0%</b>]</td>
	<td>1,946</td>
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
	<td>50.74% [50.6%-50.9%]</td>
	<td>452,940</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.42% [<b>40.6%</b>-42.3%]</td>
	<td>13,833</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.96% [<b>41.0%</b>-44.9%]</td>
	<td>2,579</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.50% [<b>41.8%</b>-43.2%]</td>
	<td>22,852</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.05% [<b>41.9%</b>-44.2%]</td>
	<td>7,162</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.40% [<b>42.3%</b>-44.5%]</td>
	<td>7,919</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.42% [40.6%-<b>42.3%</b>]</td>
	<td>13,833</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.50% [41.8%-<b>43.2%</b>]</td>
	<td>22,852</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.05% [41.9%-<b>44.2%</b>]</td>
	<td>7,162</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.40% [42.3%-<b>44.5%</b>]</td>
	<td>7,919</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.96% [41.0%-<b>44.9%</b>]</td>
	<td>2,579</td>
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
	<td>48.43% [48.2%-48.7%]</td>
	<td>174,939</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.56% [<b>40.1%</b>-43.0%]</td>
	<td>4,442</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>42.69% [<b>41.0%</b>-44.4%]</td>
	<td>3,251</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.94% [<b>41.5%</b>-44.4%]</td>
	<td>4,928</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.03% [<b>42.3%</b>-47.7%]</td>
	<td>1,339</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.36% [<b>42.4%</b>-46.3%]</td>
	<td>2,667</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.56% [40.1%-<b>43.0%</b>]</td>
	<td>4,442</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>42.94% [41.5%-<b>44.4%</b>]</td>
	<td>4,928</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>42.69% [41.0%-<b>44.4%</b>]</td>
	<td>3,251</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>44.33% [42.7%-<b>46.0%</b>]</td>
	<td>3,666</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.76% [43.5%-<b>46.0%</b>]</td>
	<td>6,208</td>
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
	<td>47.46% [47.2%-47.8%]</td>
	<td>116,570</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.66% [<b>40.3%</b>-47.0%]</td>
	<td>868</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.35% [<b>40.9%</b>-43.8%]</td>
	<td>4,871</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.70% [<b>41.4%</b>-48.0%]</td>
	<td>906</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.31% [<b>41.6%</b>-45.0%]</td>
	<td>3,320</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.44% [<b>42.0%</b>-44.9%]</td>
	<td>4,761</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.35% [40.9%-<b>43.8%</b>]</td>
	<td>4,871</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.44% [42.0%-<b>44.9%</b>]</td>
	<td>4,761</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.31% [41.6%-<b>45.0%</b>]</td>
	<td>3,320</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>43.82% [42.1%-<b>45.5%</b>]</td>
	<td>3,334</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>44.60% [42.6%-<b>46.6%</b>]</td>
	<td>2,444</td>
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
	<td>49.92% [49.8%-50.1%]</td>
	<td>378,531</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.77% [<b>39.8%</b>-43.7%]</td>
	<td>2,485</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>42.75% [<b>40.8%</b>-44.7%]</td>
	<td>2,587</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.63% [<b>44.1%</b>-47.2%]</td>
	<td>4,258</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>47.18% [<b>44.5%</b>-49.8%]</td>
	<td>1,420</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>47.39% [<b>45.7%</b>-49.1%]</td>
	<td>3,353</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.77% [39.8%-<b>43.7%</b>]</td>
	<td>2,485</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>42.75% [40.8%-<b>44.7%</b>]</td>
	<td>2,587</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.63% [44.1%-<b>47.2%</b>]</td>
	<td>4,258</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.72% [45.8%-<b>47.7%</b>]</td>
	<td>11,289</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.16% [46.4%-<b>47.9%</b>]</td>
	<td>16,507</td>
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
	<td>49.20% [49.0%-49.4%]</td>
	<td>169,244</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>40.59% [<b>39.4%</b>-41.8%]</td>
	<td>6,334</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.78% [<b>40.6%</b>-42.9%]</td>
	<td>7,236</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.97% [<b>41.5%</b>-44.5%]</td>
	<td>4,359</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.36% [<b>42.4%</b>-48.3%]</td>
	<td>1,131</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.43% [<b>42.5%</b>-46.4%]</td>
	<td>2,523</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>40.59% [39.4%-<b>41.8%</b>]</td>
	<td>6,334</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.78% [40.6%-<b>42.9%</b>]</td>
	<td>7,236</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>42.97% [41.5%-<b>44.5%</b>]</td>
	<td>4,359</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.43% [42.5%-<b>46.4%</b>]</td>
	<td>2,523</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.68% [44.5%-<b>46.9%</b>]</td>
	<td>6,672</td>
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
	<td>48.22% [48.0%-48.4%]</td>
	<td>256,043</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>40.60% [<b>38.6%</b>-42.6%]</td>
	<td>2,468</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>43.17% [<b>40.6%</b>-45.7%]</td>
	<td>1,508</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>41.88% [<b>40.7%</b>-43.1%]</td>
	<td>6,831</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.99% [<b>40.9%</b>-43.0%]</td>
	<td>8,799</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>43.43% [<b>41.8%</b>-45.1%]</td>
	<td>3,583</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>40.60% [38.6%-<b>42.6%</b>]</td>
	<td>2,468</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.99% [40.9%-<b>43.0%</b>]</td>
	<td>8,799</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>41.88% [40.7%-<b>43.1%</b>]</td>
	<td>6,831</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.53% [42.3%-<b>44.8%</b>]</td>
	<td>6,219</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>43.43% [41.8%-<b>45.1%</b>]</td>
	<td>3,583</td>
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
	<td>48.76% [48.5%-49.0%]</td>
	<td>138,471</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.76% [<b>40.4%</b>-47.2%]</td>
	<td>850</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>42.52% [<b>40.6%</b>-44.5%]</td>
	<td>2,554</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>43.82% [<b>41.3%</b>-46.4%]</td>
	<td>1,536</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>45.10% [<b>41.5%</b>-48.7%]</td>
	<td>765</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>45.54% [<b>41.8%</b>-49.3%]</td>
	<td>718</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>42.52% [40.6%-<b>44.5%</b>]</td>
	<td>2,554</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.98% [42.6%-<b>45.3%</b>]</td>
	<td>5,314</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.28% [42.6%-<b>46.0%</b>]</td>
	<td>3,408</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.51% [42.7%-<b>46.3%</b>]</td>
	<td>3,152</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>43.82% [41.3%-<b>46.4%</b>]</td>
	<td>1,536</td>
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
	<td>50.25% [50.0%-50.5%]</td>
	<td>120,584</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.95% [<b>39.9%</b>-48.0%]</td>
	<td>603</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.84% [<b>40.5%</b>-47.2%]</td>
	<td>885</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>44.83% [<b>40.6%</b>-49.1%]</td>
	<td>542</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>46.76% [<b>43.7%</b>-49.8%]</td>
	<td>1,097</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.60% [<b>43.8%</b>-47.4%]</td>
	<td>3,125</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>43.84% [40.5%-<b>47.2%</b>]</td>
	<td>885</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>45.60% [43.8%-<b>47.4%</b>]</td>
	<td>3,125</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.95% [39.9%-<b>48.0%</b>]</td>
	<td>603</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>47.09% [45.5%-<b>48.7%</b>]</td>
	<td>3,740</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.55% [46.3%-<b>48.8%</b>]</td>
	<td>6,051</td>
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
	<td>46.37% [46.2%-46.5%]</td>
	<td>341,340</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>38.50% [<b>36.6%</b>-40.4%]</td>
	<td>2,709</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>41.29% [<b>39.7%</b>-42.8%]</td>
	<td>4,047</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.50% [<b>40.5%</b>-42.5%]</td>
	<td>8,833</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.75% [<b>40.6%</b>-44.9%]</td>
	<td>2,061</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.19% [<b>41.1%</b>-43.2%]</td>
	<td>8,973</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>38.50% [36.6%-<b>40.4%</b>]</td>
	<td>2,709</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.50% [40.5%-<b>42.5%</b>]</td>
	<td>8,833</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>41.29% [39.7%-<b>42.8%</b>]</td>
	<td>4,047</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.19% [41.1%-<b>43.2%</b>]</td>
	<td>8,973</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>43.08% [42.0%-<b>44.1%</b>]</td>
	<td>8,926</td>
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
	<td>50.75% [50.4%-51.1%]</td>
	<td>76,228</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.14% [<b>39.4%</b>-48.9%]</td>
	<td>435</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.79% [<b>39.6%</b>-44.0%]</td>
	<td>2,015</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.11% [<b>40.8%</b>-51.5%]</td>
	<td>347</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.04% [<b>41.9%</b>-46.2%]</td>
	<td>2,164</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.92% [<b>42.5%</b>-49.3%]</td>
	<td>871</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.79% [39.6%-<b>44.0%</b>]</td>
	<td>2,015</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>44.04% [41.9%-<b>46.2%</b>]</td>
	<td>2,164</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>45.94% [43.3%-<b>48.6%</b>]</td>
	<td>1,428</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.69% [42.6%-<b>48.7%</b>]</td>
	<td>1,068</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.14% [39.4%-<b>48.9%</b>]</td>
	<td>435</td>
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
	<td>49.55% [49.2%-49.9%]</td>
	<td>107,960</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>41.54% [<b>37.2%</b>-45.9%]</td>
	<td>520</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.13% [<b>39.4%</b>-46.9%]</td>
	<td>691</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.69% [<b>41.1%</b>-48.2%]</td>
	<td>781</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.64% [<b>41.2%</b>-44.1%]</td>
	<td>4,465</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.72% [<b>41.8%</b>-45.6%]</td>
	<td>2,731</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.64% [41.2%-<b>44.1%</b>]</td>
	<td>4,465</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>43.72% [41.8%-<b>45.6%</b>]</td>
	<td>2,731</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>41.54% [37.2%-<b>45.9%</b>]</td>
	<td>520</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>43.13% [39.4%-<b>46.9%</b>]</td>
	<td>691</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>44.83% [42.7%-<b>47.0%</b>]</td>
	<td>2,184</td>
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
	<td>47.78% [47.5%-48.1%]</td>
	<td>129,146</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>38.63% [<b>37.3%</b>-40.0%]</td>
	<td>5,125</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>40.64% [<b>39.1%</b>-42.2%]</td>
	<td>4,097</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.66% [<b>39.9%</b>-43.4%]</td>
	<td>3,243</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>44.75% [<b>40.1%</b>-49.4%]</td>
	<td>467</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.31% [<b>40.2%</b>-48.5%]</td>
	<td>571</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>38.63% [37.3%-<b>40.0%</b>]</td>
	<td>5,125</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>40.64% [39.1%-<b>42.2%</b>]</td>
	<td>4,097</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.87% [40.6%-<b>43.1%</b>]</td>
	<td>6,018</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.66% [39.9%-<b>43.4%</b>]</td>
	<td>3,243</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>44.93% [43.6%-<b>46.3%</b>]</td>
	<td>5,286</td>
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
	<td>45.80% [45.5%-46.1%]</td>
	<td>124,533</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>40.31% [<b>37.3%</b>-43.3%]</td>
	<td>1,047</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>42.64% [<b>39.1%</b>-46.2%]</td>
	<td>774</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>41.48% [<b>39.3%</b>-43.6%]</td>
	<td>2,071</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.31% [<b>39.6%</b>-43.0%]</td>
	<td>3,350</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>43.30% [<b>39.7%</b>-46.9%]</td>
	<td>746</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.20% [39.9%-<b>42.5%</b>]</td>
	<td>5,378</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>41.40% [39.8%-<b>43.0%</b>]</td>
	<td>3,981</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.31% [39.6%-<b>43.0%</b>]</td>
	<td>3,350</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>40.31% [37.3%-<b>43.3%</b>]</td>
	<td>1,047</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>41.48% [39.3%-<b>43.6%</b>]</td>
	<td>2,071</td>
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
	<td>49.72% [49.4%-50.1%]</td>
	<td>81,286</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>40.39% [<b>36.0%</b>-44.7%]</td>
	<td>510</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>42.56% [<b>38.7%</b>-46.4%]</td>
	<td>665</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>44.42% [<b>39.4%</b>-49.5%]</td>
	<td>385</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.34% [<b>39.5%</b>-49.2%]</td>
	<td>424</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>44.84% [<b>40.0%</b>-49.7%]</td>
	<td>417</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>40.39% [36.0%-<b>44.7%</b>]</td>
	<td>510</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>42.82% [40.2%-<b>45.5%</b>]</td>
	<td>1,406</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sion"></span> Sion</td>
	<td>42.96% [40.0%-<b>45.9%</b>]</td>
	<td>1,108</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>43.69% [41.2%-<b>46.2%</b>]</td>
	<td>1,586</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>42.56% [38.7%-<b>46.4%</b>]</td>
	<td>665</td>
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
	<td>46.24% [46.0%-46.4%]</td>
	<td>249,527</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>38.43% [<b>37.3%</b>-39.5%]</td>
	<td>7,830</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>39.37% [<b>38.5%</b>-40.2%]</td>
	<td>13,666</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>42.67% [<b>40.3%</b>-45.0%]</td>
	<td>1,746</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.60% [<b>40.4%</b>-42.8%]</td>
	<td>6,757</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>42.92% [<b>41.1%</b>-44.7%]</td>
	<td>3,080</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-yorick"></span> Yorick</td>
	<td>38.43% [37.3%-<b>39.5%</b>]</td>
	<td>7,830</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>39.37% [38.5%-<b>40.2%</b>]</td>
	<td>13,666</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>41.60% [40.4%-<b>42.8%</b>]</td>
	<td>6,757</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.14% [41.2%-<b>43.1%</b>]</td>
	<td>11,311</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>42.86% [41.3%-<b>44.4%</b>]</td>
	<td>4,207</td>
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
	<td>43.91% [43.7%-44.1%]</td>
	<td>211,909</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>39.63% [<b>37.2%</b>-42.1%]</td>
	<td>1,610</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>40.30% [<b>37.3%</b>-43.3%]</td>
	<td>1,057</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>38.96% [<b>37.4%</b>-40.5%]</td>
	<td>3,984</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>38.65% [<b>37.4%</b>-39.9%]</td>
	<td>6,566</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>39.24% [<b>37.9%</b>-40.6%]</td>
	<td>5,176</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-dr--mundo"></span> Dr. Mundo</td>
	<td>38.65% [37.4%-<b>39.9%</b>]</td>
	<td>6,566</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-irelia"></span> Irelia</td>
	<td>38.96% [37.4%-<b>40.5%</b>]</td>
	<td>3,984</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>39.24% [37.9%-<b>40.6%</b>]</td>
	<td>5,176</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>40.72% [39.8%-<b>41.6%</b>]</td>
	<td>11,374</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>40.54% [39.4%-<b>41.7%</b>]</td>
	<td>7,340</td>
</tr>
</table>

</details>
### Jungle

<details>
<summary>Click to view</summary>

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
	<td>53.59% [53.4%-53.7%]</td>
	<td>473,401</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.58% [<b>46.4%</b>-50.8%]</td>
	<td>2,112</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>49.88% [<b>49.0%</b>-50.7%]</td>
	<td>14,338</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>49.95% [<b>49.1%</b>-50.8%]</td>
	<td>12,382</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>50.24% [<b>49.3%</b>-51.2%]</td>
	<td>11,396</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>51.52% [<b>49.5%</b>-53.5%]</td>
	<td>2,469</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>49.88% [49.0%-<b>50.7%</b>]</td>
	<td>14,338</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.58% [46.4%-<b>50.8%</b>]</td>
	<td>2,112</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>49.95% [49.1%-<b>50.8%</b>]</td>
	<td>12,382</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>50.24% [49.3%-<b>51.2%</b>]</td>
	<td>11,396</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>51.08% [50.3%-<b>51.8%</b>]</td>
	<td>17,480</td>
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
	<td>51.93% [51.8%-52.1%]</td>
	<td>504,390</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.69% [<b>46.7%</b>-50.7%]</td>
	<td>2,592</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.73% [<b>47.9%</b>-49.6%]</td>
	<td>13,149</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.90% [<b>48.2%</b>-51.6%]</td>
	<td>3,479</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>50.46% [<b>48.5%</b>-52.4%]</td>
	<td>2,602</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.25% [<b>48.7%</b>-49.8%]</td>
	<td>28,217</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.73% [47.9%-<b>49.6%</b>]</td>
	<td>13,149</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.25% [48.7%-<b>49.8%</b>]</td>
	<td>28,217</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>49.63% [48.9%-<b>50.4%</b>]</td>
	<td>18,784</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>49.74% [49.0%-<b>50.5%</b>]</td>
	<td>18,749</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.69% [46.7%-<b>50.7%</b>]</td>
	<td>2,592</td>
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
	<td>52.12% [52.0%-52.2%]</td>
	<td>723,055</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.78% [<b>46.3%</b>-49.3%]</td>
	<td>4,393</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.61% [<b>47.8%</b>-49.4%]</td>
	<td>16,312</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>48.90% [<b>48.1%</b>-49.7%]</td>
	<td>17,386</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.92% [<b>48.2%</b>-49.7%]</td>
	<td>17,480</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>50.28% [<b>48.4%</b>-52.2%]</td>
	<td>2,687</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.78% [46.3%-<b>49.3%</b>]</td>
	<td>4,393</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.61% [47.8%-<b>49.4%</b>]</td>
	<td>16,312</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>48.90% [48.1%-<b>49.7%</b>]</td>
	<td>17,386</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.92% [48.2%-<b>49.7%</b>]</td>
	<td>17,480</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>49.23% [48.5%-<b>49.9%</b>]</td>
	<td>21,203</td>
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
	<td>52.81% [52.7%-52.9%]</td>
	<td>927,256</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.93% [<b>44.6%</b>-47.3%]</td>
	<td>5,476</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.36% [<b>47.7%</b>-49.0%]</td>
	<td>26,630</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.31% [<b>48.4%</b>-50.2%]</td>
	<td>12,992</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-karthus"></span> Karthus</td>
	<td>49.47% [<b>48.6%</b>-50.4%]</td>
	<td>12,113</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>49.21% [<b>48.7%</b>-49.7%]</td>
	<td>37,195</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.93% [44.6%-<b>47.3%</b>]</td>
	<td>5,476</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.36% [47.7%-<b>49.0%</b>]</td>
	<td>26,630</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>49.21% [48.7%-<b>49.7%</b>]</td>
	<td>37,195</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.31% [48.4%-<b>50.2%</b>]</td>
	<td>12,992</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-karthus"></span> Karthus</td>
	<td>49.47% [48.6%-<b>50.4%</b>]</td>
	<td>12,113</td>
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
	<td>52.05% [51.9%-52.2%]</td>
	<td>662,365</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.32% [<b>46.7%</b>-48.0%]</td>
	<td>23,887</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.33% [<b>46.8%</b>-47.8%]</td>
	<td>40,270</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.62% [<b>47.0%</b>-50.3%]</td>
	<td>3,729</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>48.13% [<b>47.2%</b>-49.1%]</td>
	<td>10,837</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.91% [<b>47.5%</b>-50.4%]</td>
	<td>4,786</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.33% [46.8%-<b>47.8%</b>]</td>
	<td>40,270</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.32% [46.7%-<b>48.0%</b>]</td>
	<td>23,887</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>48.13% [47.2%-<b>49.1%</b>]</td>
	<td>10,837</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.80% [48.0%-<b>49.6%</b>]</td>
	<td>17,334</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>48.90% [48.2%-<b>49.6%</b>]</td>
	<td>21,682</td>
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
	<td>51.95% [51.8%-52.1%]</td>
	<td>450,533</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.47% [<b>46.5%</b>-50.5%]</td>
	<td>2,484</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.56% [<b>46.8%</b>-48.4%]</td>
	<td>15,642</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.80% [<b>47.0%</b>-50.6%]</td>
	<td>3,129</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.56% [<b>47.8%</b>-51.3%]</td>
	<td>3,188</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.32% [<b>48.0%</b>-50.7%]</td>
	<td>5,389</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>47.56% [46.8%-<b>48.4%</b>]</td>
	<td>15,642</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.54% [48.9%-<b>50.1%</b>]</td>
	<td>27,830</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.47% [46.5%-<b>50.5%</b>]</td>
	<td>2,484</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>49.73% [48.9%-<b>50.6%</b>]</td>
	<td>14,306</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.80% [47.0%-<b>50.6%</b>]</td>
	<td>3,129</td>
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
	<td>50.43% [50.3%-50.5%]</td>
	<td>764,707</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.72% [<b>45.4%</b>-48.1%]</td>
	<td>5,368</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.84% [<b>46.2%</b>-49.5%]</td>
	<td>3,662</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.73% [<b>46.8%</b>-48.6%]</td>
	<td>12,058</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.76% [<b>47.1%</b>-48.5%]</td>
	<td>20,174</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.89% [<b>47.2%</b>-48.6%]</td>
	<td>19,931</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.72% [45.4%-<b>48.1%</b>]</td>
	<td>5,368</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.76% [47.1%-<b>48.5%</b>]</td>
	<td>20,174</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.89% [47.2%-<b>48.6%</b>]</td>
	<td>19,931</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.73% [46.8%-<b>48.6%</b>]</td>
	<td>12,058</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>48.31% [47.7%-<b>48.9%</b>]</td>
	<td>30,776</td>
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
	<td>51.88% [51.7%-52.0%]</td>
	<td>447,254</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.76% [<b>44.0%</b>-47.5%]</td>
	<td>3,197</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.31% [<b>46.1%</b>-50.5%]</td>
	<td>2,136</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.20% [<b>47.5%</b>-48.9%]</td>
	<td>22,749</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>49.24% [<b>48.1%</b>-50.4%]</td>
	<td>7,859</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>49.56% [<b>48.2%</b>-50.9%]</td>
	<td>5,256</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.76% [44.0%-<b>47.5%</b>]</td>
	<td>3,197</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.20% [47.5%-<b>48.9%</b>]</td>
	<td>22,749</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.32% [48.6%-<b>50.0%</b>]</td>
	<td>20,678</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>49.24% [48.1%-<b>50.4%</b>]</td>
	<td>7,859</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.31% [46.1%-<b>50.5%</b>]</td>
	<td>2,136</td>
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
	<td>50.57% [50.5%-50.7%]</td>
	<td>749,092</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.11% [<b>43.2%</b>-47.1%]</td>
	<td>2,627</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.29% [<b>46.0%</b>-48.5%]</td>
	<td>6,407</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.83% [<b>46.1%</b>-47.6%]</td>
	<td>18,795</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.86% [<b>47.3%</b>-48.4%]</td>
	<td>35,736</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>48.34% [<b>47.5%</b>-49.1%]</td>
	<td>15,453</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.11% [43.2%-<b>47.1%</b>]</td>
	<td>2,627</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.83% [46.1%-<b>47.6%</b>]</td>
	<td>18,795</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.86% [47.3%-<b>48.4%</b>]</td>
	<td>35,736</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.29% [46.0%-<b>48.5%</b>]</td>
	<td>6,407</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.38% [47.7%-<b>49.1%</b>]</td>
	<td>20,126</td>
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
	<td>51.63% [51.5%-51.7%]</td>
	<td>781,178</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.53% [<b>45.8%</b>-49.3%]</td>
	<td>3,274</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.62% [<b>45.9%</b>-47.3%]</td>
	<td>21,365</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>48.05% [<b>47.3%</b>-48.8%]</td>
	<td>20,239</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.85% [<b>47.4%</b>-50.3%]</td>
	<td>4,749</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>48.53% [<b>47.6%</b>-49.5%]</td>
	<td>10,442</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.62% [45.9%-<b>47.3%</b>]</td>
	<td>21,365</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>48.05% [47.3%-<b>48.8%</b>]</td>
	<td>20,239</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.38% [47.8%-<b>49.0%</b>]</td>
	<td>29,344</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.53% [45.8%-<b>49.3%</b>]</td>
	<td>3,274</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.93% [48.4%-<b>49.4%</b>]</td>
	<td>40,998</td>
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
	<td>50.37% [50.3%-50.5%]</td>
	<td>1,537,528</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.64% [<b>44.4%</b>-46.9%]</td>
	<td>5,971</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>46.38% [<b>45.7%</b>-47.1%]</td>
	<td>21,103</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.47% [<b>46.1%</b>-46.8%]</td>
	<td>69,390</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.63% [<b>46.2%</b>-47.1%]</td>
	<td>51,529</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.45% [<b>46.9%</b>-48.0%]</td>
	<td>37,145</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.47% [46.1%-<b>46.8%</b>]</td>
	<td>69,390</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.64% [44.4%-<b>46.9%</b>]</td>
	<td>5,971</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>46.38% [45.7%-<b>47.1%</b>]</td>
	<td>21,103</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.63% [46.2%-<b>47.1%</b>]</td>
	<td>51,529</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.45% [46.9%-<b>48.0%</b>]</td>
	<td>37,145</td>
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
	<td>51.06% [50.9%-51.2%]</td>
	<td>278,159</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.84% [<b>43.0%</b>-48.7%]</td>
	<td>1,226</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.51% [<b>45.6%</b>-51.4%]</td>
	<td>1,206</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.19% [<b>46.0%</b>-48.4%]</td>
	<td>7,034</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.44% [<b>46.2%</b>-48.7%]</td>
	<td>6,651</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.77% [<b>46.6%</b>-49.0%]</td>
	<td>7,054</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.19% [46.0%-<b>48.4%</b>]</td>
	<td>7,034</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.44% [46.2%-<b>48.7%</b>]</td>
	<td>6,651</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.84% [43.0%-<b>48.7%</b>]</td>
	<td>1,226</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.01% [47.2%-<b>48.8%</b>]</td>
	<td>14,420</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.77% [46.6%-<b>49.0%</b>]</td>
	<td>7,054</td>
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
	<td>49.72% [49.6%-49.8%]</td>
	<td>762,071</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.42% [<b>44.3%</b>-48.5%]</td>
	<td>2,303</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.27% [<b>45.5%</b>-47.0%]</td>
	<td>17,533</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.33% [<b>45.5%</b>-47.1%]</td>
	<td>15,355</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.41% [<b>45.8%</b>-47.1%]</td>
	<td>23,621</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.93% [<b>46.4%</b>-47.5%]</td>
	<td>30,644</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.27% [45.5%-<b>47.0%</b>]</td>
	<td>17,533</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.41% [45.8%-<b>47.1%</b>]</td>
	<td>23,621</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.33% [45.5%-<b>47.1%</b>]</td>
	<td>15,355</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.93% [46.4%-<b>47.5%</b>]</td>
	<td>31,770</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.93% [46.4%-<b>47.5%</b>]</td>
	<td>30,644</td>
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
	<td>50.20% [50.0%-50.4%]</td>
	<td>354,620</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.85% [<b>44.3%</b>-49.4%]</td>
	<td>1,569</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.30% [<b>45.3%</b>-47.3%]</td>
	<td>9,106</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.31% [<b>45.6%</b>-47.0%]</td>
	<td>18,939</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.84% [<b>45.8%</b>-47.9%]</td>
	<td>8,899</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>47.50% [<b>46.6%</b>-48.4%]</td>
	<td>13,180</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.31% [45.6%-<b>47.0%</b>]</td>
	<td>18,939</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.30% [45.3%-<b>47.3%</b>]</td>
	<td>9,106</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.84% [45.8%-<b>47.9%</b>]</td>
	<td>8,899</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>47.50% [46.6%-<b>48.4%</b>]</td>
	<td>13,180</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.02% [47.2%-<b>48.9%</b>]</td>
	<td>13,432</td>
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
	<td>49.84% [49.7%-50.0%]</td>
	<td>722,683</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>43.66% [<b>43.0%</b>-44.3%]</td>
	<td>24,005</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.54% [<b>45.0%</b>-46.1%]</td>
	<td>33,785</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.58% [<b>45.1%</b>-46.1%]</td>
	<td>38,504</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.79% [<b>45.8%</b>-47.8%]</td>
	<td>10,270</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>46.89% [<b>46.0%</b>-47.8%]</td>
	<td>12,334</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>43.66% [43.0%-<b>44.3%</b>]</td>
	<td>24,005</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.54% [45.0%-<b>46.1%</b>]</td>
	<td>33,785</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.58% [45.1%-<b>46.1%</b>]</td>
	<td>38,504</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>46.79% [45.8%-<b>47.8%</b>]</td>
	<td>10,270</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-elise"></span> Elise</td>
	<td>46.89% [46.0%-<b>47.8%</b>]</td>
	<td>12,334</td>
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
	<td>50.16% [50.0%-50.3%]</td>
	<td>369,174</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.94% [<b>42.3%</b>-47.6%]</td>
	<td>1,433</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.00% [<b>44.8%</b>-49.2%]</td>
	<td>2,066</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.83% [<b>44.9%</b>-48.8%]</td>
	<td>2,622</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.51% [<b>45.4%</b>-47.6%]</td>
	<td>8,166</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>47.20% [<b>45.7%</b>-48.7%]</td>
	<td>4,193</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.66% [45.8%-<b>47.5%</b>]</td>
	<td>12,636</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.94% [42.3%-<b>47.6%</b>]</td>
	<td>1,433</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.51% [45.4%-<b>47.6%</b>]</td>
	<td>8,166</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.84% [45.8%-<b>47.9%</b>]</td>
	<td>8,409</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.55% [46.8%-<b>48.3%</b>]</td>
	<td>17,596</td>
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
	<td>50.14% [50.0%-50.3%]</td>
	<td>538,867</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.80% [<b>43.7%</b>-47.9%]</td>
	<td>2,225</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.60% [<b>44.7%</b>-46.5%]</td>
	<td>12,417</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.90% [<b>45.0%</b>-46.8%]</td>
	<td>13,113</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.14% [<b>45.4%</b>-46.9%]</td>
	<td>19,129</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.47% [<b>45.6%</b>-47.3%]</td>
	<td>14,131</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.60% [44.7%-<b>46.5%</b>]</td>
	<td>12,417</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.90% [45.0%-<b>46.8%</b>]</td>
	<td>13,113</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.14% [45.4%-<b>46.9%</b>]</td>
	<td>19,129</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.47% [45.6%-<b>47.3%</b>]</td>
	<td>14,131</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.19% [46.5%-<b>47.9%</b>]</td>
	<td>21,566</td>
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
	<td>54.09% [53.7%-54.4%]</td>
	<td>79,910</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>48.36% [<b>42.6%</b>-54.1%]</td>
	<td>304</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>50.32% [<b>44.6%</b>-56.0%]</td>
	<td>308</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-karthus"></span> Karthus</td>
	<td>50.72% [<b>47.3%</b>-54.2%]</td>
	<td>836</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>50.75% [<b>47.4%</b>-54.1%]</td>
	<td>865</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>53.55% [<b>47.6%</b>-59.5%]</td>
	<td>282</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>49.72% [47.8%-<b>51.6%</b>]</td>
	<td>2,687</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>50.29% [48.7%-<b>51.9%</b>]</td>
	<td>3,752</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>51.38% [49.7%-<b>53.0%</b>]</td>
	<td>3,729</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>51.31% [49.3%-<b>53.3%</b>]</td>
	<td>2,592</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>51.53% [49.5%-<b>53.5%</b>]</td>
	<td>2,484</td>
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
	<td>49.14% [48.9%-49.3%]</td>
	<td>255,085</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>45.80% [<b>42.8%</b>-48.8%]</td>
	<td>1,094</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.82% [<b>44.5%</b>-49.2%]</td>
	<td>1,824</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>46.64% [<b>44.6%</b>-48.7%]</td>
	<td>2,350</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.19% [<b>44.9%</b>-47.4%]</td>
	<td>6,274</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.25% [<b>45.0%</b>-47.5%]</td>
	<td>6,139</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.35% [45.5%-<b>47.2%</b>]</td>
	<td>12,981</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.30% [45.3%-<b>47.3%</b>]</td>
	<td>9,530</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.19% [44.9%-<b>47.4%</b>]</td>
	<td>6,274</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>46.25% [45.0%-<b>47.5%</b>]</td>
	<td>6,139</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>46.94% [45.7%-<b>48.2%</b>]</td>
	<td>6,563</td>
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
	<td>51.18% [50.9%-51.5%]</td>
	<td>123,546</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.63% [<b>43.3%</b>-52.0%]</td>
	<td>527</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>47.83% [<b>44.5%</b>-51.2%]</td>
	<td>876</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>49.34% [<b>45.0%</b>-53.7%]</td>
	<td>527</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>50.34% [<b>45.6%</b>-55.1%]</td>
	<td>445</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>49.92% [<b>45.8%</b>-54.0%]</td>
	<td>601</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.50% [45.9%-<b>49.1%</b>]</td>
	<td>3,699</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>47.73% [46.1%-<b>49.4%</b>]</td>
	<td>3,549</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>47.99% [46.5%-<b>49.5%</b>]</td>
	<td>4,347</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.08% [46.3%-<b>49.9%</b>]</td>
	<td>3,018</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>48.77% [47.2%-<b>50.3%</b>]</td>
	<td>4,253</td>
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
	<td>49.14% [49.0%-49.3%]</td>
	<td>585,681</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.93% [<b>44.1%</b>-45.8%]</td>
	<td>14,032</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.90% [<b>44.4%</b>-49.4%]</td>
	<td>1,546</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.39% [<b>45.2%</b>-47.6%]</td>
	<td>7,282</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.95% [<b>45.2%</b>-46.7%]</td>
	<td>19,446</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.37% [<b>45.4%</b>-49.3%]</td>
	<td>2,571</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.93% [44.1%-<b>45.8%</b>]</td>
	<td>14,032</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.95% [45.2%-<b>46.7%</b>]</td>
	<td>19,446</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.39% [45.2%-<b>47.6%</b>]</td>
	<td>7,282</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>47.26% [46.4%-<b>48.1%</b>]</td>
	<td>14,093</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>47.39% [46.5%-<b>48.3%</b>]</td>
	<td>12,079</td>
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
	<td>50.77% [50.6%-51.0%]</td>
	<td>211,345</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>47.11% [<b>43.9%</b>-50.3%]</td>
	<td>987</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>47.70% [<b>44.3%</b>-51.1%]</td>
	<td>870</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.33% [<b>44.5%</b>-50.1%]</td>
	<td>1,274</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.94% [<b>45.6%</b>-48.3%]</td>
	<td>5,351</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>49.25% [<b>45.9%</b>-52.6%]</td>
	<td>865</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.94% [45.6%-<b>48.3%</b>]</td>
	<td>5,351</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>47.38% [46.1%-<b>48.6%</b>]</td>
	<td>6,431</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>47.61% [46.3%-<b>48.9%</b>]</td>
	<td>5,770</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>48.75% [47.6%-<b>49.9%</b>]</td>
	<td>7,830</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.33% [44.5%-<b>50.1%</b>]</td>
	<td>1,274</td>
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
	<td>50.34% [50.2%-50.5%]</td>
	<td>434,899</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.46% [<b>43.4%</b>-45.5%]</td>
	<td>9,146</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.45% [<b>44.3%</b>-48.6%]</td>
	<td>2,127</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>47.66% [<b>45.3%</b>-50.0%]</td>
	<td>1,773</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.62% [<b>45.4%</b>-47.9%]</td>
	<td>6,222</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>48.60% [<b>45.6%</b>-51.6%]</td>
	<td>1,107</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.46% [43.4%-<b>45.5%</b>]</td>
	<td>9,146</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.51% [45.8%-<b>47.3%</b>]</td>
	<td>18,002</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.89% [46.1%-<b>47.7%</b>]</td>
	<td>15,179</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.89% [45.9%-<b>47.9%</b>]</td>
	<td>10,075</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.62% [45.4%-<b>47.9%</b>]</td>
	<td>6,222</td>
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
	<td>49.77% [49.6%-49.9%]</td>
	<td>322,812</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.89% [<b>43.7%</b>-48.1%]</td>
	<td>2,009</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.85% [<b>44.0%</b>-49.7%]</td>
	<td>1,240</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.63% [<b>45.7%</b>-47.5%]</td>
	<td>11,874</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.09% [<b>45.8%</b>-50.4%]</td>
	<td>1,836</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.27% [<b>46.1%</b>-48.4%]</td>
	<td>7,500</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.63% [45.7%-<b>47.5%</b>]</td>
	<td>11,874</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.89% [43.7%-<b>48.1%</b>]</td>
	<td>2,009</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>47.27% [46.1%-<b>48.4%</b>]</td>
	<td>7,500</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.85% [47.0%-<b>48.7%</b>]</td>
	<td>15,554</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.73% [46.5%-<b>48.9%</b>]</td>
	<td>7,071</td>
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
	<td>50.02% [49.8%-50.3%]</td>
	<td>173,134</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.95% [<b>39.7%</b>-46.2%]</td>
	<td>936</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.72% [<b>43.7%</b>-49.7%]</td>
	<td>1,128</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.40% [<b>43.8%</b>-47.0%]</td>
	<td>4,086</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.48% [<b>43.9%</b>-51.1%]</td>
	<td>773</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>46.40% [<b>44.2%</b>-48.6%]</td>
	<td>2,110</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.95% [39.7%-<b>46.2%</b>]</td>
	<td>936</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.40% [43.8%-<b>47.0%</b>]</td>
	<td>4,086</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.78% [44.5%-<b>47.1%</b>]</td>
	<td>5,861</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.28% [45.2%-<b>47.3%</b>]</td>
	<td>9,067</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>46.40% [44.2%-<b>48.6%</b>]</td>
	<td>2,110</td>
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
	<td>49.08% [49.0%-49.2%]</td>
	<td>592,876</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.25% [<b>42.3%</b>-46.2%]</td>
	<td>2,540</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.32% [<b>43.5%</b>-45.1%]</td>
	<td>15,001</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.32% [<b>43.8%</b>-46.8%]</td>
	<td>4,276</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.77% [<b>44.9%</b>-48.6%]</td>
	<td>2,970</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.88% [<b>45.1%</b>-46.7%]</td>
	<td>14,482</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.32% [43.5%-<b>45.1%</b>]</td>
	<td>15,001</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.25% [42.3%-<b>46.2%</b>]</td>
	<td>2,540</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.80% [45.1%-<b>46.5%</b>]</td>
	<td>22,291</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.06% [45.5%-<b>46.7%</b>]</td>
	<td>27,641</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>45.88% [45.1%-<b>46.7%</b>]</td>
	<td>14,482</td>
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
	<td>49.65% [49.5%-49.8%]</td>
	<td>288,594</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.50% [<b>42.2%</b>-44.8%]</td>
	<td>6,283</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.46% [<b>43.4%</b>-49.5%]</td>
	<td>1,059</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.42% [<b>44.0%</b>-46.8%]</td>
	<td>5,106</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>45.45% [<b>44.2%</b>-46.7%]</td>
	<td>6,572</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>45.71% [<b>44.7%</b>-46.7%]</td>
	<td>9,218</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.50% [42.2%-<b>44.8%</b>]</td>
	<td>6,283</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>45.45% [44.2%-<b>46.7%</b>]</td>
	<td>6,572</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>45.71% [44.7%-<b>46.7%</b>]</td>
	<td>9,218</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.42% [44.0%-<b>46.8%</b>]</td>
	<td>5,106</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>47.96% [47.0%-<b>48.9%</b>]</td>
	<td>11,380</td>
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
	<td>50.92% [50.6%-51.2%]</td>
	<td>99,464</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.46% [<b>42.1%</b>-50.8%]</td>
	<td>523</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>48.76% [<b>43.2%</b>-54.3%]</td>
	<td>322</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>49.21% [<b>44.1%</b>-54.4%]</td>
	<td>378</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.18% [<b>44.5%</b>-47.9%]</td>
	<td>3,400</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>49.31% [<b>45.2%</b>-53.5%]</td>
	<td>578</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>46.18% [44.5%-<b>47.9%</b>]</td>
	<td>3,400</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>48.15% [46.3%-<b>50.0%</b>]</td>
	<td>3,003</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.48% [46.5%-<b>50.5%</b>]</td>
	<td>2,469</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.09% [47.5%-<b>50.6%</b>]</td>
	<td>4,215</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nunu---willump"></span> Nunu & Willump</td>
	<td>48.49% [46.2%-<b>50.8%</b>]</td>
	<td>1,955</td>
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
	<td>50.13% [50.0%-50.3%]</td>
	<td>359,813</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.38% [<b>39.6%</b>-45.1%]</td>
	<td>1,279</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>43.89% [<b>43.1%</b>-44.7%]</td>
	<td>15,889</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.69% [<b>44.6%</b>-46.8%]</td>
	<td>8,433</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>46.58% [<b>45.7%</b>-47.4%]</td>
	<td>14,012</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.22% [<b>46.3%</b>-50.2%]</td>
	<td>2,580</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>43.89% [43.1%-<b>44.7%</b>]</td>
	<td>15,889</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.38% [39.6%-<b>45.1%</b>]</td>
	<td>1,279</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.69% [44.6%-<b>46.8%</b>]</td>
	<td>8,433</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>46.58% [45.7%-<b>47.4%</b>]</td>
	<td>14,012</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>47.52% [46.4%-<b>48.7%</b>]</td>
	<td>7,812</td>
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
	<td>47.94% [47.8%-48.1%]</td>
	<td>293,458</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.63% [<b>39.6%</b>-45.6%]</td>
	<td>1,079</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>43.73% [<b>42.7%</b>-44.8%]</td>
	<td>8,554</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>45.58% [<b>42.8%</b>-48.4%]</td>
	<td>1,257</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.05% [<b>43.9%</b>-46.2%]</td>
	<td>7,612</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.27% [<b>44.2%</b>-46.3%]</td>
	<td>9,219</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>43.73% [42.7%-<b>44.8%</b>]</td>
	<td>8,554</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.63% [39.6%-<b>45.6%</b>]</td>
	<td>1,079</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.15% [44.3%-<b>46.0%</b>]</td>
	<td>14,059</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>45.05% [43.9%-<b>46.2%</b>]</td>
	<td>7,612</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>45.27% [44.2%-<b>46.3%</b>]</td>
	<td>9,219</td>
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
	<td>47.50% [47.4%-47.6%]</td>
	<td>1,213,043</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.14% [<b>42.5%</b>-43.8%]</td>
	<td>25,520</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.31% [<b>42.6%</b>-46.0%]</td>
	<td>3,295</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>44.35% [<b>43.1%</b>-45.6%]</td>
	<td>6,187</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.35% [<b>43.8%</b>-44.9%]</td>
	<td>32,382</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.88% [<b>44.2%</b>-45.6%]</td>
	<td>20,236</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.14% [42.5%-<b>43.8%</b>]</td>
	<td>25,520</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.35% [43.8%-<b>44.9%</b>]</td>
	<td>32,382</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.96% [44.5%-<b>45.4%</b>]</td>
	<td>45,518</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.88% [44.2%-<b>45.6%</b>]</td>
	<td>20,236</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>44.35% [43.1%-<b>45.6%</b>]</td>
	<td>6,187</td>
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
	<td>48.25% [48.1%-48.4%]</td>
	<td>452,317</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.89% [<b>39.5%</b>-44.2%]</td>
	<td>1,757</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.51% [<b>42.5%</b>-44.5%]</td>
	<td>10,562</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>45.56% [<b>44.6%</b>-46.5%]</td>
	<td>10,984</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.39% [<b>44.7%</b>-46.1%]</td>
	<td>21,866</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.94% [<b>44.9%</b>-48.9%]</td>
	<td>2,501</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.89% [39.5%-<b>44.2%</b>]</td>
	<td>1,757</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.51% [42.5%-<b>44.5%</b>]</td>
	<td>10,562</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.39% [44.7%-<b>46.1%</b>]</td>
	<td>21,866</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>45.56% [44.6%-<b>46.5%</b>]</td>
	<td>10,984</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.88% [45.2%-<b>46.6%</b>]</td>
	<td>18,655</td>
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
	<td>49.81% [49.6%-50.0%]</td>
	<td>261,630</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>40.55% [<b>37.6%</b>-43.5%]</td>
	<td>1,100</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.26% [<b>42.0%</b>-44.5%]</td>
	<td>6,634</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.59% [<b>43.0%</b>-48.2%]</td>
	<td>1,441</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.08% [<b>43.7%</b>-48.5%]</td>
	<td>1,695</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.51% [<b>44.4%</b>-46.6%]</td>
	<td>8,421</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>40.55% [37.6%-<b>43.5%</b>]</td>
	<td>1,100</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.26% [42.0%-<b>44.5%</b>]</td>
	<td>6,634</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>45.51% [44.4%-<b>46.6%</b>]</td>
	<td>8,421</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.81% [44.9%-<b>46.7%</b>]</td>
	<td>13,267</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>46.18% [45.0%-<b>47.4%</b>]</td>
	<td>6,798</td>
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
	<td>48.89% [48.7%-49.0%]</td>
	<td>400,191</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.43% [<b>39.0%</b>-43.9%]</td>
	<td>1,610</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.17% [<b>41.9%</b>-44.4%]</td>
	<td>6,036</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>43.06% [<b>42.3%</b>-43.8%]</td>
	<td>18,690</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.27% [<b>43.3%</b>-45.3%]</td>
	<td>9,663</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>44.18% [<b>43.3%</b>-45.1%]</td>
	<td>11,854</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>43.06% [42.3%-<b>43.8%</b>]</td>
	<td>18,690</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>41.43% [39.0%-<b>43.9%</b>]</td>
	<td>1,610</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.17% [41.9%-<b>44.4%</b>]</td>
	<td>6,036</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>44.18% [43.3%-<b>45.1%</b>]</td>
	<td>11,854</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.27% [43.3%-<b>45.3%</b>]</td>
	<td>9,663</td>
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
	<td>47.25% [47.1%-47.4%]</td>
	<td>254,810</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.12% [<b>39.1%</b>-45.1%]</td>
	<td>1,066</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>43.67% [<b>41.9%</b>-45.5%]</td>
	<td>2,995</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>44.03% [<b>41.9%</b>-46.1%]</td>
	<td>2,226</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.15% [<b>42.6%</b>-47.7%]</td>
	<td>1,515</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-wukong"></span> Wukong</td>
	<td>45.19% [<b>43.4%</b>-47.0%]</td>
	<td>3,158</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.12% [39.1%-<b>45.1%</b>]</td>
	<td>1,066</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>43.67% [41.9%-<b>45.5%</b>]</td>
	<td>2,995</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.79% [43.5%-<b>46.1%</b>]</td>
	<td>5,946</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>44.03% [41.9%-<b>46.1%</b>]</td>
	<td>2,226</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.22% [44.2%-<b>46.2%</b>]</td>
	<td>9,784</td>
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
	<td>49.25% [48.9%-49.6%]</td>
	<td>79,223</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>48.97% [<b>41.8%</b>-56.1%]</td>
	<td>194</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>44.51% [<b>41.8%</b>-47.2%]</td>
	<td>1,375</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.15% [<b>42.2%</b>-50.1%]</td>
	<td>624</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rek-sai"></span> Rek'Sai</td>
	<td>47.70% [<b>42.8%</b>-52.6%]</td>
	<td>413</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.06% [<b>42.8%</b>-47.3%]</td>
	<td>1,935</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>44.51% [41.8%-<b>47.2%</b>]</td>
	<td>1,375</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.06% [42.8%-<b>47.3%</b>]</td>
	<td>1,935</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>46.76% [45.1%-<b>48.4%</b>]</td>
	<td>3,813</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>46.25% [44.1%-<b>48.4%</b>]</td>
	<td>2,175</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nunu---willump"></span> Nunu & Willump</td>
	<td>46.24% [43.8%-<b>48.7%</b>]</td>
	<td>1,635</td>
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
	<td>47.60% [47.4%-47.8%]</td>
	<td>207,022</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.37% [<b>40.7%</b>-48.1%]</td>
	<td>728</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>42.73% [<b>41.7%</b>-43.7%]</td>
	<td>9,627</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.96% [<b>42.5%</b>-45.4%]</td>
	<td>4,486</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-talon"></span> Talon</td>
	<td>46.06% [<b>42.8%</b>-49.3%]</td>
	<td>938</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.85% [<b>43.3%</b>-46.4%]</td>
	<td>3,982</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>42.73% [41.7%-<b>43.7%</b>]</td>
	<td>9,627</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.96% [42.5%-<b>45.4%</b>]</td>
	<td>4,486</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.85% [43.3%-<b>46.4%</b>]</td>
	<td>3,982</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>45.67% [44.6%-<b>46.8%</b>]</td>
	<td>8,318</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.73% [44.5%-<b>46.9%</b>]</td>
	<td>7,104</td>
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
	<td>49.14% [49.0%-49.3%]</td>
	<td>379,730</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>39.23% [<b>36.8%</b>-41.7%]</td>
	<td>1,565</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.45% [<b>41.7%</b>-43.2%]</td>
	<td>17,128</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.72% [<b>43.7%</b>-45.8%]</td>
	<td>8,785</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.93% [<b>44.2%</b>-45.6%]</td>
	<td>20,026</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>46.79% [<b>44.7%</b>-48.9%]</td>
	<td>2,289</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>39.23% [36.8%-<b>41.7%</b>]</td>
	<td>1,565</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.45% [41.7%-<b>43.2%</b>]</td>
	<td>17,128</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.93% [44.2%-<b>45.6%</b>]</td>
	<td>20,026</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.72% [43.7%-<b>45.8%</b>]</td>
	<td>8,785</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>46.08% [45.0%-<b>47.1%</b>]</td>
	<td>9,021</td>
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
	<td>51.26% [51.1%-51.5%]</td>
	<td>236,679</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>38.03% [<b>34.8%</b>-41.3%]</td>
	<td>902</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.20% [<b>41.1%</b>-43.3%]</td>
	<td>8,656</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.69% [<b>43.2%</b>-46.2%]</td>
	<td>4,571</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>44.74% [<b>43.4%</b>-46.1%]</td>
	<td>5,221</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.35% [<b>43.4%</b>-45.3%]</td>
	<td>10,672</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>38.03% [34.8%-<b>41.3%</b>]</td>
	<td>902</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>42.20% [41.1%-<b>43.3%</b>]</td>
	<td>8,656</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.35% [43.4%-<b>45.3%</b>]</td>
	<td>10,672</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>44.74% [43.4%-<b>46.1%</b>]</td>
	<td>5,221</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.69% [43.2%-<b>46.2%</b>]</td>
	<td>4,571</td>
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
	<td>46.94% [46.7%-47.2%]</td>
	<td>225,002</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.77% [<b>40.4%</b>-47.1%]</td>
	<td>891</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>42.40% [<b>40.9%</b>-43.9%]</td>
	<td>4,604</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-bel-veth"></span> Bel'Veth</td>
	<td>44.16% [<b>41.7%</b>-46.6%]</td>
	<td>1,635</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.06% [<b>41.9%</b>-44.3%]</td>
	<td>6,842</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>43.40% [<b>41.9%</b>-44.9%]</td>
	<td>4,468</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>42.40% [40.9%-<b>43.9%</b>]</td>
	<td>4,604</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>43.06% [41.9%-<b>44.3%</b>]</td>
	<td>6,842</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>43.40% [41.9%-<b>44.9%</b>]</td>
	<td>4,468</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>43.45% [41.9%-<b>45.0%</b>]</td>
	<td>4,364</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viego"></span> Viego</td>
	<td>44.85% [44.1%-<b>45.6%</b>]</td>
	<td>18,584</td>
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
	<td>48.52% [48.2%-48.8%]</td>
	<td>99,182</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>43.67% [<b>40.8%</b>-46.5%]</td>
	<td>1,232</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.15% [<b>40.9%</b>-51.4%]</td>
	<td>364</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.50% [<b>41.0%</b>-52.0%]</td>
	<td>329</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>48.15% [<b>42.1%</b>-54.2%]</td>
	<td>270</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.45% [<b>42.3%</b>-46.6%]</td>
	<td>2,099</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>43.67% [40.8%-<b>46.5%</b>]</td>
	<td>1,232</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.67% [42.8%-<b>46.5%</b>]</td>
	<td>2,888</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>44.45% [42.3%-<b>46.6%</b>]</td>
	<td>2,099</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.24% [43.6%-<b>46.9%</b>]</td>
	<td>3,506</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>45.35% [43.7%-<b>47.0%</b>]</td>
	<td>3,559</td>
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
	<td>47.31% [47.1%-47.5%]</td>
	<td>354,652</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.02% [<b>40.5%</b>-45.5%]</td>
	<td>1,555</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.61% [<b>40.9%</b>-48.3%]</td>
	<td>724</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>42.97% [<b>41.5%</b>-44.4%]</td>
	<td>4,794</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>42.98% [<b>41.8%</b>-44.1%]</td>
	<td>7,461</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.07% [<b>41.8%</b>-44.3%]</td>
	<td>6,473</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>42.98% [41.8%-<b>44.1%</b>]</td>
	<td>7,461</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>43.07% [41.8%-<b>44.3%</b>]</td>
	<td>6,473</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>42.97% [41.5%-<b>44.4%</b>]</td>
	<td>4,794</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.77% [42.8%-<b>44.7%</b>]</td>
	<td>10,853</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>43.61% [42.4%-<b>44.9%</b>]</td>
	<td>6,393</td>
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
	<td>48.98% [48.8%-49.2%]</td>
	<td>197,447</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>44.10% [<b>40.7%</b>-47.5%]</td>
	<td>848</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.47% [<b>40.9%</b>-48.1%]</td>
	<td>769</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>44.92% [<b>41.6%</b>-48.2%]</td>
	<td>915</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.25% [<b>42.2%</b>-44.3%]</td>
	<td>9,183</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>44.12% [<b>42.2%</b>-46.0%]</td>
	<td>2,781</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.25% [42.2%-<b>44.3%</b>]</td>
	<td>9,183</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>44.12% [42.2%-<b>46.0%</b>]</td>
	<td>2,781</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>44.10% [40.7%-<b>47.5%</b>]</td>
	<td>848</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>46.38% [45.1%-<b>47.6%</b>]</td>
	<td>6,229</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>46.86% [45.7%-<b>48.0%</b>]</td>
	<td>7,877</td>
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
	<td>51.59% [51.3%-51.9%]</td>
	<td>120,933</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.74% [<b>39.5%</b>-48.0%]</td>
	<td>535</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>45.33% [<b>40.8%</b>-49.8%]</td>
	<td>492</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>48.07% [<b>44.3%</b>-51.8%]</td>
	<td>701</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>47.45% [<b>44.6%</b>-50.3%]</td>
	<td>1,195</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.61% [<b>44.9%</b>-48.4%]</td>
	<td>3,261</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>43.74% [39.5%-<b>48.0%</b>]</td>
	<td>535</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>46.61% [44.9%-<b>48.4%</b>]</td>
	<td>3,261</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.57% [47.3%-<b>49.8%</b>]</td>
	<td>6,708</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ivern"></span> Ivern</td>
	<td>45.33% [40.8%-<b>49.8%</b>]</td>
	<td>492</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>47.45% [44.6%-<b>50.3%</b>]</td>
	<td>1,195</td>
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
	<td>49.29% [49.0%-49.6%]</td>
	<td>90,298</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>43.86% [<b>39.2%</b>-48.5%]</td>
	<td>456</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>42.84% [<b>40.5%</b>-45.2%]</td>
	<td>1,746</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.45% [<b>40.5%</b>-52.4%]</td>
	<td>282</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>43.96% [<b>41.5%</b>-46.4%]</td>
	<td>1,640</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>44.24% [<b>41.8%</b>-46.6%]</td>
	<td>1,711</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.61% [42.0%-<b>45.2%</b>]</td>
	<td>4,031</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>42.84% [40.5%-<b>45.2%</b>]</td>
	<td>1,746</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>43.96% [41.5%-<b>46.4%</b>]</td>
	<td>1,640</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>44.24% [41.8%-<b>46.6%</b>]</td>
	<td>1,711</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>44.97% [43.1%-<b>46.8%</b>]</td>
	<td>2,893</td>
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
	<td>48.53% [48.2%-48.9%]</td>
	<td>91,986</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>40.48% [<b>34.3%</b>-46.7%]</td>
	<td>252</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>43.73% [<b>38.5%</b>-49.0%]</td>
	<td>359</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-bel-veth"></span> Bel'Veth</td>
	<td>44.86% [<b>41.6%</b>-48.2%]</td>
	<td>914</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.12% [<b>41.8%</b>-46.4%]</td>
	<td>1,829</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.27% [<b>42.5%</b>-48.1%]</td>
	<td>1,279</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>44.57% [42.9%-<b>46.2%</b>]</td>
	<td>3,572</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>44.12% [41.8%-<b>46.4%</b>]</td>
	<td>1,829</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.61% [42.6%-<b>46.6%</b>]</td>
	<td>2,432</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>40.48% [34.3%-<b>46.7%</b>]</td>
	<td>252</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>45.35% [43.6%-<b>47.1%</b>]</td>
	<td>3,290</td>
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
	<td>46.26% [45.8%-46.7%]</td>
	<td>54,862</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>42.82% [<b>37.5%</b>-48.1%]</td>
	<td>348</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>43.68% [<b>37.7%</b>-49.6%]</td>
	<td>277</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>44.88% [<b>37.9%</b>-51.8%]</td>
	<td>205</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-evelynn"></span> Evelynn</td>
	<td>43.13% [<b>39.2%</b>-47.0%]</td>
	<td>640</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>41.51% [<b>39.5%</b>-43.6%]</td>
	<td>2,298</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>41.51% [39.5%-<b>43.6%</b>]</td>
	<td>2,298</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>43.28% [41.4%-<b>45.1%</b>]</td>
	<td>2,849</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-viego"></span> Viego</td>
	<td>43.97% [42.5%-<b>45.5%</b>]</td>
	<td>4,421</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>43.22% [40.2%-<b>46.2%</b>]</td>
	<td>1,092</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>44.45% [42.3%-<b>46.6%</b>]</td>
	<td>2,164</td>
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
	<td>49.30% [49.0%-49.6%]</td>
	<td>121,112</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>41.40% [<b>37.3%</b>-45.5%]</td>
	<td>570</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>41.98% [<b>37.7%</b>-46.2%]</td>
	<td>536</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>46.56% [<b>41.5%</b>-51.6%]</td>
	<td>393</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>44.69% [<b>42.9%</b>-46.5%]</td>
	<td>2,938</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.45% [<b>43.3%</b>-47.6%]</td>
	<td>2,156</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>41.40% [37.3%-<b>45.5%</b>]</td>
	<td>570</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zed"></span> Zed</td>
	<td>41.98% [37.7%-<b>46.2%</b>]</td>
	<td>536</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>44.69% [42.9%-<b>46.5%</b>]</td>
	<td>2,938</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>45.45% [43.3%-<b>47.6%</b>]</td>
	<td>2,156</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kha-zix"></span> Kha'Zix</td>
	<td>47.22% [45.7%-<b>48.7%</b>]</td>
	<td>4,604</td>
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
	<td>49.19% [48.9%-49.5%]</td>
	<td>89,497</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>39.80% [<b>34.1%</b>-45.5%]</td>
	<td>299</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>42.91% [<b>36.9%</b>-49.0%]</td>
	<td>268</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>42.75% [<b>37.7%</b>-47.8%]</td>
	<td>386</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.10% [<b>42.3%</b>-47.9%]</td>
	<td>1,246</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.63% [<b>42.5%</b>-46.7%]</td>
	<td>2,227</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>39.80% [34.1%-<b>45.5%</b>]</td>
	<td>299</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>44.63% [42.5%-<b>46.7%</b>]</td>
	<td>2,227</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>45.35% [43.6%-<b>47.1%</b>]</td>
	<td>3,292</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>45.59% [43.4%-<b>47.8%</b>]</td>
	<td>2,073</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>42.75% [37.7%-<b>47.8%</b>]</td>
	<td>386</td>
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
	<td>44.09% [43.9%-44.3%]</td>
	<td>173,868</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>38.14% [<b>34.4%</b>-41.9%]</td>
	<td>666</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>38.74% [<b>36.6%</b>-40.9%]</td>
	<td>2,078</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>39.35% [<b>38.1%</b>-40.6%]</td>
	<td>5,982</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>42.64% [<b>38.8%</b>-46.5%]</td>
	<td>666</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>40.61% [<b>39.0%</b>-42.2%]</td>
	<td>3,950</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>39.35% [38.1%-<b>40.6%</b>]</td>
	<td>5,982</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-rammus"></span> Rammus</td>
	<td>38.74% [36.6%-<b>40.9%</b>]</td>
	<td>2,078</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-master-yi"></span> Master Yi</td>
	<td>40.54% [39.3%-<b>41.8%</b>]</td>
	<td>6,250</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>38.14% [34.4%-<b>41.9%</b>]</td>
	<td>666</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>40.83% [39.7%-<b>41.9%</b>]</td>
	<td>8,095</td>
</tr>
</table>

</details>
### Mid

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
	<td>53.44% [53.3%-53.6%]</td>
	<td>717,925</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.01% [<b>48.2%</b>-49.8%]</td>
	<td>17,142</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>49.27% [<b>48.5%</b>-50.0%]</td>
	<td>17,008</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>50.93% [<b>49.2%</b>-52.7%]</td>
	<td>3,189</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>51.49% [<b>49.4%</b>-53.6%]</td>
	<td>2,247</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>50.71% [<b>49.4%</b>-52.0%]</td>
	<td>6,297</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.01% [48.2%-<b>49.8%</b>]</td>
	<td>17,142</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>49.27% [48.5%-<b>50.0%</b>]</td>
	<td>17,008</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>50.53% [49.9%-<b>51.1%</b>]</td>
	<td>27,748</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>50.76% [49.6%-<b>51.9%</b>]</td>
	<td>7,203</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>51.42% [50.9%-<b>52.0%</b>]</td>
	<td>34,335</td>
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
	<td>52.22% [52.1%-52.4%]</td>
	<td>530,485</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.56% [<b>46.6%</b>-48.5%]</td>
	<td>10,607</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.70% [<b>47.8%</b>-49.6%]</td>
	<td>13,300</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>49.35% [<b>48.0%</b>-50.7%]</td>
	<td>5,714</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>50.36% [<b>48.2%</b>-52.6%]</td>
	<td>2,061</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>49.54% [<b>48.2%</b>-50.9%]</td>
	<td>5,329</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.56% [46.6%-<b>48.5%</b>]</td>
	<td>10,607</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.70% [47.8%-<b>49.6%</b>]</td>
	<td>13,300</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.47% [48.9%-<b>50.1%</b>]</td>
	<td>27,748</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>49.35% [48.0%-<b>50.7%</b>]</td>
	<td>5,714</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>49.54% [48.2%-<b>50.9%</b>]</td>
	<td>5,329</td>
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
	<td>50.66% [50.5%-50.8%]</td>
	<td>586,894</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>47.40% [<b>44.9%</b>-49.9%]</td>
	<td>1,599</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.64% [<b>46.3%</b>-49.0%]</td>
	<td>5,399</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.19% [<b>46.4%</b>-47.9%]</td>
	<td>17,299</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.06% [<b>46.6%</b>-49.5%]</td>
	<td>4,661</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>49.19% [<b>47.0%</b>-51.4%]</td>
	<td>2,088</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.19% [46.4%-<b>47.9%</b>]</td>
	<td>17,299</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.83% [47.2%-<b>48.5%</b>]</td>
	<td>23,524</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>48.22% [47.5%-<b>48.9%</b>]</td>
	<td>20,063</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.64% [46.3%-<b>49.0%</b>]</td>
	<td>5,399</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>48.55% [48.0%-<b>49.1%</b>]</td>
	<td>35,451</td>
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
	<td>53.12% [52.9%-53.4%]</td>
	<td>182,743</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>50.10% [<b>45.6%</b>-54.6%]</td>
	<td>495</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.57% [<b>46.0%</b>-49.1%]</td>
	<td>4,303</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>50.15% [<b>47.4%</b>-52.9%]</td>
	<td>1,318</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.03% [<b>47.9%</b>-50.2%]</td>
	<td>7,681</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>51.86% [<b>48.1%</b>-55.6%]</td>
	<td>725</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.57% [46.0%-<b>49.1%</b>]</td>
	<td>4,303</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.03% [47.9%-<b>50.2%</b>]</td>
	<td>7,681</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>50.09% [48.7%-<b>51.5%</b>]</td>
	<td>5,111</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>50.27% [48.7%-<b>51.8%</b>]</td>
	<td>4,271</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>50.65% [49.3%-<b>52.0%</b>]</td>
	<td>5,714</td>
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
	<td>50.60% [50.5%-50.7%]</td>
	<td>808,554</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.63% [<b>44.5%</b>-48.7%]</td>
	<td>2,254</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.74% [<b>46.0%</b>-47.5%]</td>
	<td>18,380</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>46.76% [<b>46.1%</b>-47.4%]</td>
	<td>22,296</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.49% [<b>46.2%</b>-48.8%]</td>
	<td>5,951</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.56% [<b>46.9%</b>-48.2%]</td>
	<td>21,599</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>46.76% [46.1%-<b>47.4%</b>]</td>
	<td>22,296</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.74% [46.0%-<b>47.5%</b>]</td>
	<td>18,380</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.56% [46.9%-<b>48.2%</b>]</td>
	<td>21,599</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-katarina"></span> Katarina</td>
	<td>47.91% [47.3%-<b>48.5%</b>]</td>
	<td>26,341</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.63% [44.5%-<b>48.7%</b>]</td>
	<td>2,254</td>
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
	<td>52.92% [52.7%-53.1%]</td>
	<td>343,451</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>48.36% [<b>45.1%</b>-51.6%]</td>
	<td>947</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.66% [<b>46.0%</b>-49.4%]</td>
	<td>3,426</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>49.14% [<b>46.6%</b>-51.7%]</td>
	<td>1,506</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>49.09% [<b>48.0%</b>-50.2%]</td>
	<td>8,312</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>52.18% [<b>48.0%</b>-56.4%]</td>
	<td>573</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.66% [46.0%-<b>49.4%</b>]</td>
	<td>3,426</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>48.97% [48.3%-<b>49.6%</b>]</td>
	<td>22,017</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>49.09% [48.0%-<b>50.2%</b>]</td>
	<td>8,312</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>50.73% [50.0%-<b>51.5%</b>]</td>
	<td>17,008</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>48.36% [45.1%-<b>51.6%</b>]</td>
	<td>947</td>
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
	<td>50.58% [50.5%-50.7%]</td>
	<td>871,509</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.53% [<b>44.8%</b>-48.2%]</td>
	<td>3,413</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.14% [<b>45.6%</b>-46.6%]</td>
	<td>39,186</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.51% [<b>45.9%</b>-49.1%]</td>
	<td>3,732</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.01% [<b>46.8%</b>-49.2%]</td>
	<td>6,986</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>48.22% [<b>47.1%</b>-49.3%]</td>
	<td>8,500</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.14% [45.6%-<b>46.6%</b>]</td>
	<td>39,186</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.53% [44.8%-<b>48.2%</b>]</td>
	<td>3,413</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>47.95% [47.4%-<b>48.5%</b>]</td>
	<td>29,722</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.51% [45.9%-<b>49.1%</b>]</td>
	<td>3,732</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.01% [46.8%-<b>49.2%</b>]</td>
	<td>6,986</td>
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
	<td>51.89% [51.7%-52.0%]</td>
	<td>487,691</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.03% [<b>44.1%</b>-48.0%]</td>
	<td>2,622</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>48.90% [<b>45.3%</b>-52.5%]</td>
	<td>771</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.38% [<b>45.4%</b>-47.3%]</td>
	<td>11,219</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.73% [<b>46.0%</b>-51.4%]</td>
	<td>1,373</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.29% [<b>46.3%</b>-48.3%]</td>
	<td>9,455</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.38% [45.4%-<b>47.3%</b>]</td>
	<td>11,219</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.03% [44.1%-<b>48.0%</b>]</td>
	<td>2,622</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.29% [46.3%-<b>48.3%</b>]</td>
	<td>9,455</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.42% [47.8%-<b>49.1%</b>]</td>
	<td>23,535</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.43% [47.1%-<b>49.8%</b>]</td>
	<td>5,284</td>
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
	<td>50.89% [50.7%-51.1%]</td>
	<td>228,793</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.68% [<b>41.8%</b>-49.5%]</td>
	<td>672</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.19% [<b>44.6%</b>-51.8%]</td>
	<td>772</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>49.87% [<b>44.7%</b>-55.0%]</td>
	<td>377</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>47.45% [<b>45.2%</b>-49.7%]</td>
	<td>2,042</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.09% [<b>45.8%</b>-48.4%]</td>
	<td>5,783</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.09% [45.8%-<b>48.4%</b>]</td>
	<td>5,783</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-akali"></span> Akali</td>
	<td>47.76% [46.7%-<b>48.8%</b>]</td>
	<td>8,480</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.19% [47.2%-<b>49.2%</b>]</td>
	<td>9,653</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.19% [47.2%-<b>49.2%</b>]</td>
	<td>9,285</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.93% [46.5%-<b>49.4%</b>]</td>
	<td>4,605</td>
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
	<td>52.13% [52.0%-52.3%]</td>
	<td>333,813</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.85% [<b>42.3%</b>-47.4%]</td>
	<td>1,514</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.97% [<b>44.5%</b>-49.4%]</td>
	<td>1,682</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.39% [<b>44.5%</b>-48.2%]</td>
	<td>2,895</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.95% [<b>44.8%</b>-49.1%]</td>
	<td>2,162</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.15% [<b>44.9%</b>-51.4%]</td>
	<td>920</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.85% [42.3%-<b>47.4%</b>]</td>
	<td>1,514</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.13% [46.2%-<b>48.1%</b>]</td>
	<td>11,397</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.39% [44.5%-<b>48.2%</b>]</td>
	<td>2,895</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.82% [44.9%-<b>48.8%</b>]</td>
	<td>2,591</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.94% [47.0%-<b>48.9%</b>]</td>
	<td>10,860</td>
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
	<td>51.45% [51.3%-51.6%]</td>
	<td>336,397</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.57% [<b>43.1%</b>-50.0%]</td>
	<td>831</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.52% [<b>44.4%</b>-48.6%]</td>
	<td>2,287</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.36% [<b>44.6%</b>-48.2%]</td>
	<td>3,067</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.98% [<b>45.1%</b>-50.8%]</td>
	<td>1,213</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.67% [<b>45.8%</b>-51.6%]</td>
	<td>1,202</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.36% [44.6%-<b>48.2%</b>]</td>
	<td>3,067</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>46.52% [44.4%-<b>48.6%</b>]</td>
	<td>2,287</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-akali"></span> Akali</td>
	<td>47.86% [46.9%-<b>48.8%</b>]</td>
	<td>11,727</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>48.08% [46.9%-<b>49.3%</b>]</td>
	<td>7,240</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>48.73% [47.8%-<b>49.6%</b>]</td>
	<td>12,638</td>
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
	<td>48.80% [48.7%-48.9%]</td>
	<td>1,223,309</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>45.32% [<b>43.7%</b>-46.9%]</td>
	<td>3,835</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>44.88% [<b>44.4%</b>-45.3%]</td>
	<td>48,182</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.18% [<b>44.7%</b>-45.7%]</td>
	<td>43,548</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.18% [<b>44.8%</b>-47.5%]</td>
	<td>5,351</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>46.06% [<b>45.0%</b>-47.1%]</td>
	<td>8,402</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>44.88% [44.4%-<b>45.3%</b>]</td>
	<td>48,182</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.18% [44.7%-<b>45.7%</b>]</td>
	<td>43,548</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.05% [45.5%-<b>46.6%</b>]</td>
	<td>34,452</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>45.32% [43.7%-<b>46.9%</b>]</td>
	<td>3,835</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.07% [45.2%-<b>47.0%</b>]</td>
	<td>12,226</td>
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
	<td>50.60% [50.5%-50.7%]</td>
	<td>798,101</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>39.87% [<b>38.1%</b>-41.6%]</td>
	<td>3,223</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.77% [<b>44.4%</b>-47.2%]</td>
	<td>4,999</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.40% [<b>44.7%</b>-46.1%]</td>
	<td>19,617</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.06% [<b>44.9%</b>-47.2%]</td>
	<td>7,598</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>46.19% [<b>45.0%</b>-47.4%]</td>
	<td>7,209</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>39.87% [38.1%-<b>41.6%</b>]</td>
	<td>3,223</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.40% [44.7%-<b>46.1%</b>]</td>
	<td>19,617</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.24% [45.6%-<b>46.8%</b>]</td>
	<td>27,368</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.10% [45.3%-<b>46.9%</b>]</td>
	<td>17,563</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>46.27% [45.7%-<b>46.9%</b>]</td>
	<td>27,704</td>
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
	<td>52.22% [52.0%-52.5%]</td>
	<td>141,996</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>44.97% [<b>39.9%</b>-50.1%]</td>
	<td>378</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.73% [<b>44.1%</b>-53.3%]</td>
	<td>472</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>51.89% [<b>45.0%</b>-58.8%]</td>
	<td>212</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>47.67% [<b>45.1%</b>-50.2%]</td>
	<td>1,542</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.94% [<b>45.4%</b>-50.5%]</td>
	<td>1,531</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>48.31% [46.9%-<b>49.7%</b>]</td>
	<td>5,063</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.26% [46.4%-<b>50.1%</b>]</td>
	<td>3,021</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>44.97% [39.9%-<b>50.1%</b>]</td>
	<td>378</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>47.67% [45.1%-<b>50.2%</b>]</td>
	<td>1,542</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.24% [48.1%-<b>50.4%</b>]</td>
	<td>7,203</td>
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
	<td>50.34% [50.2%-50.5%]</td>
	<td>815,317</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.62% [<b>44.0%</b>-45.3%]</td>
	<td>22,408</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.67% [<b>44.1%</b>-45.2%]</td>
	<td>30,975</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.02% [<b>44.3%</b>-47.7%]</td>
	<td>3,357</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.52% [<b>44.7%</b>-48.3%]</td>
	<td>3,117</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.55% [<b>45.4%</b>-47.7%]</td>
	<td>8,105</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.67% [44.1%-<b>45.2%</b>]</td>
	<td>30,975</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.62% [44.0%-<b>45.3%</b>]</td>
	<td>22,408</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>46.43% [45.8%-<b>47.0%</b>]</td>
	<td>28,289</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.63% [45.9%-<b>47.3%</b>]</td>
	<td>19,500</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.55% [45.4%-<b>47.7%</b>]</td>
	<td>8,105</td>
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
	<td>49.34% [49.2%-49.5%]</td>
	<td>461,202</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.23% [<b>42.2%</b>-44.2%]</td>
	<td>9,607</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.88% [<b>44.0%</b>-49.7%]</td>
	<td>1,216</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.53% [<b>44.1%</b>-49.0%]</td>
	<td>1,685</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>47.03% [<b>44.4%</b>-49.7%]</td>
	<td>1,412</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>45.89% [<b>44.9%</b>-46.8%]</td>
	<td>11,180</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.23% [42.2%-<b>44.2%</b>]</td>
	<td>9,607</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>45.89% [44.9%-<b>46.8%</b>]</td>
	<td>11,180</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.31% [45.5%-<b>47.1%</b>]</td>
	<td>16,991</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.96% [46.1%-<b>47.8%</b>]</td>
	<td>14,066</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>47.58% [47.0%-<b>48.2%</b>]</td>
	<td>30,579</td>
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
	<td>51.97% [51.8%-52.1%]</td>
	<td>570,531</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.21% [<b>42.6%</b>-47.9%]</td>
	<td>1,409</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.03% [<b>43.6%</b>-46.4%]</td>
	<td>4,934</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.55% [<b>44.1%</b>-47.0%]</td>
	<td>4,970</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.45% [<b>44.2%</b>-48.7%]</td>
	<td>1,987</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.15% [<b>44.5%</b>-45.8%]</td>
	<td>24,025</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.15% [44.5%-<b>45.8%</b>]</td>
	<td>24,025</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>45.03% [43.6%-<b>46.4%</b>]</td>
	<td>4,934</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.55% [44.1%-<b>47.0%</b>]</td>
	<td>4,970</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>46.11% [44.6%-<b>47.6%</b>]</td>
	<td>4,238</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.28% [44.7%-<b>47.8%</b>]</td>
	<td>4,177</td>
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
	<td>52.43% [52.1%-52.8%]</td>
	<td>73,703</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>49.19% [<b>41.8%</b>-56.5%]</td>
	<td>185</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>50.26% [<b>43.1%</b>-57.5%]</td>
	<td>193</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>47.47% [<b>43.7%</b>-51.3%]</td>
	<td>691</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.39% [<b>43.9%</b>-50.9%]</td>
	<td>804</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.65% [<b>43.9%</b>-53.4%]</td>
	<td>444</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.73% [44.1%-<b>47.4%</b>]</td>
	<td>3,739</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>47.76% [45.9%-<b>49.6%</b>]</td>
	<td>2,862</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>47.62% [45.6%-<b>49.7%</b>]</td>
	<td>2,417</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.39% [43.9%-<b>50.9%</b>]</td>
	<td>804</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>49.08% [46.9%-<b>51.2%</b>]</td>
	<td>2,129</td>
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
	<td>50.66% [50.5%-50.8%]</td>
	<td>324,291</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.90% [<b>42.7%</b>-47.1%]</td>
	<td>2,067</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.81% [<b>43.0%</b>-46.6%]</td>
	<td>3,062</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>45.53% [<b>43.3%</b>-47.8%]</td>
	<td>1,935</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.61% [<b>43.5%</b>-49.7%]</td>
	<td>1,032</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>45.33% [<b>43.8%</b>-46.9%]</td>
	<td>4,147</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.81% [43.0%-<b>46.6%</b>]</td>
	<td>3,062</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.38% [44.0%-<b>46.7%</b>]</td>
	<td>5,401</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>45.33% [43.8%-<b>46.9%</b>]</td>
	<td>4,147</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.90% [42.7%-<b>47.1%</b>]</td>
	<td>2,067</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.27% [45.2%-<b>47.4%</b>]</td>
	<td>8,185</td>
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
	<td>50.91% [50.7%-51.1%]</td>
	<td>199,712</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.66% [<b>41.3%</b>-48.0%]</td>
	<td>862</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.04% [<b>42.8%</b>-51.3%]</td>
	<td>557</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.43% [<b>43.3%</b>-47.6%]</td>
	<td>2,155</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.04% [<b>43.5%</b>-48.6%]</td>
	<td>1,501</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.17% [<b>44.1%</b>-46.3%]</td>
	<td>8,142</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.17% [44.1%-<b>46.3%</b>]</td>
	<td>8,142</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.04% [44.7%-<b>47.4%</b>]</td>
	<td>5,404</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.43% [43.3%-<b>47.6%</b>]</td>
	<td>2,155</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.66% [41.3%-<b>48.0%</b>]</td>
	<td>862</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.04% [43.5%-<b>48.6%</b>]</td>
	<td>1,501</td>
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
	<td>51.35% [51.1%-51.6%]</td>
	<td>140,361</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.48% [<b>41.8%</b>-51.2%]</td>
	<td>454</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>48.70% [<b>42.6%</b>-54.8%]</td>
	<td>269</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.90% [<b>42.7%</b>-49.1%]</td>
	<td>963</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>47.93% [<b>43.4%</b>-52.5%]</td>
	<td>482</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.96% [<b>43.4%</b>-48.5%]</td>
	<td>1,536</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.70% [44.3%-<b>47.1%</b>]</td>
	<td>5,346</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>46.64% [44.9%-<b>48.3%</b>]</td>
	<td>3,439</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.96% [43.4%-<b>48.5%</b>]</td>
	<td>1,536</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.98% [45.1%-<b>48.9%</b>]</td>
	<td>2,744</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>47.70% [46.5%-<b>48.9%</b>]</td>
	<td>6,949</td>
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
	<td>50.03% [49.9%-50.1%]</td>
	<td>742,603</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.41% [<b>42.4%</b>-44.4%]</td>
	<td>9,300</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.37% [<b>42.4%</b>-46.3%]</td>
	<td>2,630</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.99% [<b>43.3%</b>-44.6%]</td>
	<td>23,499</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>44.71% [<b>44.2%</b>-45.2%]</td>
	<td>38,140</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>48.03% [<b>45.8%</b>-50.3%]</td>
	<td>1,980</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.41% [42.4%-<b>44.4%</b>]</td>
	<td>9,300</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.99% [43.3%-<b>44.6%</b>]</td>
	<td>23,499</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>44.71% [44.2%-<b>45.2%</b>]</td>
	<td>38,140</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.37% [42.4%-<b>46.3%</b>]</td>
	<td>2,630</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.69% [45.9%-<b>47.4%</b>]</td>
	<td>17,527</td>
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
	<td>52.57% [52.2%-52.9%]</td>
	<td>71,430</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.27% [<b>41.6%</b>-52.9%]</td>
	<td>311</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.87% [<b>42.2%</b>-51.5%]</td>
	<td>463</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.29% [<b>42.4%</b>-50.2%]</td>
	<td>661</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>47.39% [<b>43.9%</b>-50.9%]</td>
	<td>804</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>48.11% [<b>44.1%</b>-52.2%]</td>
	<td>607</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.26% [44.5%-<b>48.0%</b>]</td>
	<td>3,145</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.49% [45.0%-<b>50.0%</b>]</td>
	<td>1,556</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.29% [42.4%-<b>50.2%</b>]</td>
	<td>661</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>47.39% [43.9%-<b>50.9%</b>]</td>
	<td>804</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.99% [47.0%-<b>51.0%</b>]</td>
	<td>2,419</td>
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
	<td>48.74% [48.6%-48.9%]</td>
	<td>557,048</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.35% [<b>41.0%</b>-43.7%]</td>
	<td>5,478</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.58% [<b>42.2%</b>-46.9%]</td>
	<td>1,761</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>43.09% [<b>42.2%</b>-43.9%]</td>
	<td>13,826</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.09% [<b>42.6%</b>-45.6%]</td>
	<td>4,604</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.87% [<b>43.4%</b>-46.4%]</td>
	<td>4,446</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.35% [41.0%-<b>43.7%</b>]</td>
	<td>5,478</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>43.09% [42.2%-<b>43.9%</b>]</td>
	<td>13,826</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.09% [42.6%-<b>45.6%</b>]</td>
	<td>4,604</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>45.34% [44.5%-<b>46.2%</b>]</td>
	<td>13,584</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.87% [43.4%-<b>46.4%</b>]</td>
	<td>4,446</td>
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
	<td>48.09% [48.0%-48.2%]</td>
	<td>1,042,056</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>42.19% [<b>40.5%</b>-43.9%]</td>
	<td>3,382</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>42.82% [<b>42.2%</b>-43.5%]</td>
	<td>21,828</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.13% [<b>42.3%</b>-45.9%]</td>
	<td>3,014</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>43.41% [<b>42.5%</b>-44.4%]</td>
	<td>11,115</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.05% [<b>42.6%</b>-45.5%]</td>
	<td>4,463</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>42.82% [42.2%-<b>43.5%</b>]</td>
	<td>21,828</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>42.19% [40.5%-<b>43.9%</b>]</td>
	<td>3,382</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>43.41% [42.5%-<b>44.4%</b>]</td>
	<td>11,115</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.78% [42.9%-<b>44.6%</b>]</td>
	<td>13,877</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.22% [43.7%-<b>44.8%</b>]</td>
	<td>30,641</td>
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
	<td>49.89% [49.7%-50.0%]</td>
	<td>412,041</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.23% [<b>39.3%</b>-45.2%]</td>
	<td>1,101</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>45.08% [<b>42.0%</b>-48.2%]</td>
	<td>1,027</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.04% [<b>42.3%</b>-45.8%]</td>
	<td>3,111</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.32% [<b>42.8%</b>-45.8%]</td>
	<td>4,298</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>45.41% [<b>42.9%</b>-48.0%]</td>
	<td>1,535</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>42.23% [39.3%-<b>45.2%</b>]</td>
	<td>1,101</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.26% [43.3%-<b>45.2%</b>]</td>
	<td>10,182</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.04% [42.3%-<b>45.8%</b>]</td>
	<td>3,111</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.32% [42.8%-<b>45.8%</b>]</td>
	<td>4,298</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lissandra"></span> Lissandra</td>
	<td>45.66% [44.6%-<b>46.7%</b>]</td>
	<td>8,716</td>
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
	<td>52.75% [52.5%-53.0%]</td>
	<td>158,382</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>41.62% [<b>38.9%</b>-44.4%]</td>
	<td>1,300</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.28% [<b>41.8%</b>-48.8%]</td>
	<td>815</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>46.31% [<b>42.8%</b>-49.8%]</td>
	<td>812</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.94% [<b>43.1%</b>-46.8%]</td>
	<td>3,002</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.80% [<b>43.6%</b>-52.0%]</td>
	<td>569</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>41.62% [38.9%-<b>44.4%</b>]</td>
	<td>1,300</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.94% [43.1%-<b>46.8%</b>]</td>
	<td>3,002</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>47.09% [45.8%-<b>48.3%</b>]</td>
	<td>6,335</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.28% [41.8%-<b>48.8%</b>]</td>
	<td>815</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.32% [45.7%-<b>48.9%</b>]</td>
	<td>3,994</td>
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
	<td>51.06% [50.8%-51.4%]</td>
	<td>107,498</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>45.27% [<b>39.5%</b>-51.1%]</td>
	<td>296</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.51% [<b>41.8%</b>-53.3%]</td>
	<td>301</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>46.11% [<b>43.3%</b>-48.9%]</td>
	<td>1,284</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.48% [<b>44.3%</b>-50.6%]</td>
	<td>994</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>49.23% [<b>44.8%</b>-53.6%]</td>
	<td>520</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kassadin"></span> Kassadin</td>
	<td>46.11% [43.3%-<b>48.9%</b>]</td>
	<td>1,284</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-ekko"></span> Ekko</td>
	<td>47.79% [45.1%-<b>50.5%</b>]</td>
	<td>1,377</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>48.43% [46.4%-<b>50.5%</b>]</td>
	<td>2,358</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.29% [48.0%-<b>50.6%</b>]</td>
	<td>6,297</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.48% [44.3%-<b>50.6%</b>]</td>
	<td>994</td>
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
	<td>50.25% [50.0%-50.5%]</td>
	<td>215,589</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>46.72% [<b>41.6%</b>-51.8%]</td>
	<td>381</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.79% [<b>41.7%</b>-47.9%]</td>
	<td>1,027</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.32% [<b>44.1%</b>-50.6%]</td>
	<td>951</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.22% [<b>44.1%</b>-48.3%]</td>
	<td>2,317</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jayce"></span> Jayce</td>
	<td>47.64% [<b>44.2%</b>-51.1%]</td>
	<td>846</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.62% [45.4%-<b>47.9%</b>]</td>
	<td>6,518</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.79% [41.7%-<b>47.9%</b>]</td>
	<td>1,027</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.22% [44.1%-<b>48.3%</b>]</td>
	<td>2,317</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>47.62% [46.7%-<b>48.6%</b>]</td>
	<td>10,655</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-akali"></span> Akali</td>
	<td>47.69% [46.6%-<b>48.7%</b>]</td>
	<td>9,157</td>
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
	<td>49.14% [48.9%-49.3%]</td>
	<td>275,475</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>42.61% [<b>40.8%</b>-44.4%]</td>
	<td>2,943</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.74% [<b>41.6%</b>-43.8%]</td>
	<td>8,067</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.99% [<b>42.2%</b>-47.8%]</td>
	<td>1,267</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.83% [<b>42.5%</b>-45.1%]</td>
	<td>5,720</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.62% [<b>42.5%</b>-46.7%]</td>
	<td>2,268</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.74% [41.6%-<b>43.8%</b>]</td>
	<td>8,067</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>42.61% [40.8%-<b>44.4%</b>]</td>
	<td>2,943</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.16% [43.2%-<b>45.1%</b>]</td>
	<td>11,274</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.83% [42.5%-<b>45.1%</b>]</td>
	<td>5,720</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.62% [42.5%-<b>46.7%</b>]</td>
	<td>2,268</td>
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
	<td>50.77% [50.5%-51.1%]</td>
	<td>99,683</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.41% [<b>39.3%</b>-49.5%]</td>
	<td>376</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>46.83% [<b>41.6%</b>-52.1%]</td>
	<td>363</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.58% [<b>42.9%</b>-50.3%]</td>
	<td>732</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>49.42% [<b>43.2%</b>-55.7%]</td>
	<td>257</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>47.16% [<b>43.7%</b>-50.7%]</td>
	<td>810</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-katarina"></span> Katarina</td>
	<td>45.81% [43.8%-<b>47.8%</b>]</td>
	<td>2,456</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.22% [44.5%-<b>47.9%</b>]</td>
	<td>3,358</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.56% [44.2%-<b>48.9%</b>]</td>
	<td>1,802</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.41% [39.3%-<b>49.5%</b>]</td>
	<td>376</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.91% [45.7%-<b>50.1%</b>]</td>
	<td>2,085</td>
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
	<td>50.41% [50.1%-50.7%]</td>
	<td>104,084</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.59% [<b>39.5%</b>-49.6%]</td>
	<td>388</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.67% [<b>41.5%</b>-49.8%]</td>
	<td>578</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>48.41% [<b>42.1%</b>-54.7%]</td>
	<td>252</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.74% [<b>42.6%</b>-48.9%]</td>
	<td>1,021</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.96% [<b>42.7%</b>-47.2%]</td>
	<td>1,926</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.96% [42.7%-<b>47.2%</b>]</td>
	<td>1,926</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.93% [44.5%-<b>47.4%</b>]</td>
	<td>4,620</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.74% [42.6%-<b>48.9%</b>]</td>
	<td>1,021</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.59% [39.5%-<b>49.6%</b>]</td>
	<td>388</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.40% [43.1%-<b>49.7%</b>]</td>
	<td>903</td>
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
	<td>47.90% [47.8%-48.0%]</td>
	<td>695,473</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.48% [<b>40.5%</b>-42.5%]</td>
	<td>9,239</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>42.58% [<b>41.3%</b>-43.9%]</td>
	<td>6,034</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.61% [<b>41.5%</b>-45.8%]</td>
	<td>2,121</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.72% [<b>41.9%</b>-45.5%]</td>
	<td>3,017</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.55% [<b>42.5%</b>-46.6%]</td>
	<td>2,357</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.48% [40.5%-<b>42.5%</b>]</td>
	<td>9,239</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>42.58% [41.3%-<b>43.9%</b>]</td>
	<td>6,034</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.65% [42.8%-<b>44.5%</b>]</td>
	<td>13,810</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.04% [42.9%-<b>45.2%</b>]</td>
	<td>6,993</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.72% [41.9%-<b>45.5%</b>]</td>
	<td>3,017</td>
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
	<td>48.00% [47.8%-48.2%]</td>
	<td>219,459</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.05% [<b>40.8%</b>-47.3%]</td>
	<td>958</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.57% [<b>41.2%</b>-48.0%]</td>
	<td>857</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.23% [<b>41.3%</b>-49.2%]</td>
	<td>639</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.57% [<b>41.6%</b>-43.6%]</td>
	<td>9,722</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.40% [<b>42.6%</b>-48.2%]</td>
	<td>1,227</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.57% [41.6%-<b>43.6%</b>]</td>
	<td>9,722</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.37% [42.9%-<b>45.9%</b>]</td>
	<td>4,481</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.87% [43.6%-<b>46.2%</b>]</td>
	<td>5,846</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>45.31% [44.0%-<b>46.6%</b>]</td>
	<td>6,153</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>45.55% [44.3%-<b>46.8%</b>]</td>
	<td>6,889</td>
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
	<td>328,279</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.75% [<b>41.0%</b>-44.5%]</td>
	<td>3,043</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.50% [<b>41.1%</b>-47.9%]</td>
	<td>836</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.88% [<b>43.1%</b>-48.7%]</td>
	<td>1,273</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>47.45% [<b>44.0%</b>-50.9%]</td>
	<td>822</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.32% [<b>44.1%</b>-46.6%]</td>
	<td>6,485</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.75% [41.0%-<b>44.5%</b>]</td>
	<td>3,043</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.32% [44.1%-<b>46.6%</b>]</td>
	<td>6,485</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.75% [45.9%-<b>47.6%</b>]</td>
	<td>14,902</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.50% [41.1%-<b>47.9%</b>]</td>
	<td>836</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.88% [43.1%-<b>48.7%</b>]</td>
	<td>1,273</td>
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
	<td>49.09% [48.9%-49.3%]</td>
	<td>260,148</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.10% [<b>40.1%</b>-44.1%]</td>
	<td>2,404</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.95% [<b>41.0%</b>-46.9%]</td>
	<td>1,115</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>44.62% [<b>41.3%</b>-48.0%]</td>
	<td>883</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.13% [<b>41.9%</b>-48.4%]</td>
	<td>924</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>44.69% [<b>41.9%</b>-47.5%]</td>
	<td>1,233</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>42.10% [40.1%-<b>44.1%</b>]</td>
	<td>2,404</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.25% [43.2%-<b>45.3%</b>]</td>
	<td>9,534</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>44.13% [41.9%-<b>46.4%</b>]</td>
	<td>1,960</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>44.64% [42.5%-<b>46.8%</b>]</td>
	<td>2,166</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>45.73% [44.6%-<b>46.8%</b>]</td>
	<td>8,056</td>
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
	<td>52.54% [52.2%-52.9%]</td>
	<td>95,556</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.74% [<b>39.6%</b>-49.8%]</td>
	<td>380</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.85% [<b>40.9%</b>-52.8%]</td>
	<td>286</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>47.13% [<b>41.6%</b>-52.6%]</td>
	<td>331</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.36% [<b>42.6%</b>-50.1%]</td>
	<td>714</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cassiopeia"></span> Cassiopeia</td>
	<td>47.99% [<b>43.8%</b>-52.2%]</td>
	<td>571</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.06% [44.6%-<b>49.6%</b>]</td>
	<td>1,583</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.74% [39.6%-<b>49.8%</b>]</td>
	<td>380</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.36% [42.6%-<b>50.1%</b>]</td>
	<td>714</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.07% [47.3%-<b>50.8%</b>]</td>
	<td>3,189</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>49.11% [47.0%-<b>51.2%</b>]</td>
	<td>2,201</td>
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
	<td>50.61% [50.4%-50.8%]</td>
	<td>193,456</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.85% [<b>40.8%</b>-48.9%]</td>
	<td>602</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.59% [<b>40.9%</b>-50.3%]</td>
	<td>454</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.85% [<b>41.5%</b>-46.2%]</td>
	<td>1,820</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>44.26% [<b>42.0%</b>-46.5%]</td>
	<td>2,020</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>46.91% [<b>42.3%</b>-51.5%]</td>
	<td>469</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.85% [41.5%-<b>46.2%</b>]</td>
	<td>1,820</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>44.26% [42.0%-<b>46.5%</b>]</td>
	<td>2,020</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-pantheon"></span> Pantheon</td>
	<td>46.35% [43.9%-<b>48.8%</b>]</td>
	<td>1,685</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.85% [40.8%-<b>48.9%</b>]</td>
	<td>602</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ryze"></span> Ryze</td>
	<td>46.87% [44.7%-<b>49.0%</b>]</td>
	<td>2,206</td>
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
	<td>48.31% [48.1%-48.5%]</td>
	<td>212,000</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.43% [<b>40.9%</b>-48.0%]</td>
	<td>781</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.18% [<b>40.9%</b>-45.4%]</td>
	<td>1,906</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>46.33% [<b>42.3%</b>-50.4%]</td>
	<td>600</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>44.97% [<b>42.4%</b>-47.5%]</td>
	<td>1,532</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.14% [<b>43.0%</b>-47.2%]</td>
	<td>2,262</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>43.18% [40.9%-<b>45.4%</b>]</td>
	<td>1,906</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>44.89% [43.3%-<b>46.4%</b>]</td>
	<td>4,101</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.52% [44.4%-<b>46.7%</b>]</td>
	<td>7,340</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>45.65% [44.4%-<b>46.9%</b>]</td>
	<td>5,897</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>46.16% [45.2%-<b>47.1%</b>]</td>
	<td>11,765</td>
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
	<td>51.07% [50.8%-51.3%]</td>
	<td>143,401</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.49% [<b>40.2%</b>-48.8%]</td>
	<td>544</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.54% [<b>40.6%</b>-46.5%]</td>
	<td>1,114</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.45% [<b>41.4%</b>-49.5%]</td>
	<td>616</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>46.91% [<b>41.6%</b>-52.2%]</td>
	<td>356</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>47.29% [<b>42.0%</b>-52.6%]</td>
	<td>351</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>43.54% [40.6%-<b>46.5%</b>]</td>
	<td>1,114</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.90% [44.6%-<b>47.2%</b>]</td>
	<td>6,148</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.69% [44.6%-<b>48.7%</b>]</td>
	<td>2,373</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.49% [40.2%-<b>48.8%</b>]</td>
	<td>544</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>45.45% [41.4%-<b>49.5%</b>]</td>
	<td>616</td>
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
	<td>51.84% [51.6%-52.1%]</td>
	<td>169,307</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.13% [<b>40.3%</b>-48.0%]</td>
	<td>673</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.96% [<b>40.4%</b>-49.5%]</td>
	<td>476</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>45.09% [<b>40.5%</b>-49.7%]</td>
	<td>468</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.67% [<b>41.1%</b>-48.2%]</td>
	<td>797</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>47.13% [<b>44.0%</b>-50.2%]</td>
	<td>1,029</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.13% [40.3%-<b>48.0%</b>]</td>
	<td>673</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.67% [41.1%-<b>48.2%</b>]</td>
	<td>797</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.58% [46.4%-<b>48.8%</b>]</td>
	<td>7,009</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>47.70% [46.4%-<b>49.0%</b>]</td>
	<td>5,497</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yone"></span> Yone</td>
	<td>48.29% [47.3%-<b>49.3%</b>]</td>
	<td>10,805</td>
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
	<td>51.81% [51.4%-52.3%]</td>
	<td>49,999</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.81% [<b>36.8%</b>-52.8%]</td>
	<td>154</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.29% [<b>39.9%</b>-48.7%]</td>
	<td>508</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.13% [<b>40.7%</b>-53.5%]</td>
	<td>244</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.64% [<b>40.8%</b>-54.5%]</td>
	<td>212</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>48.42% [<b>41.2%</b>-55.7%]</td>
	<td>190</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>46.47% [44.4%-<b>48.6%</b>]</td>
	<td>2,281</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>44.29% [39.9%-<b>48.7%</b>]</td>
	<td>508</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.89% [44.5%-<b>49.2%</b>]</td>
	<td>1,802</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>48.58% [46.4%-<b>50.7%</b>]</td>
	<td>2,149</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>48.64% [45.9%-<b>51.4%</b>]</td>
	<td>1,357</td>
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
	<td>48.43% [48.2%-48.6%]</td>
	<td>207,854</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>41.61% [<b>39.5%</b>-43.7%]</td>
	<td>2,206</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.39% [<b>39.7%</b>-47.1%]</td>
	<td>703</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.01% [<b>41.6%</b>-44.4%]</td>
	<td>5,136</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.83% [<b>42.2%</b>-47.5%]</td>
	<td>1,392</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>44.85% [<b>42.3%</b>-47.4%]</td>
	<td>1,583</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>41.61% [39.5%-<b>43.7%</b>]</td>
	<td>2,206</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>43.01% [41.6%-<b>44.4%</b>]</td>
	<td>5,136</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>44.59% [43.4%-<b>45.8%</b>]</td>
	<td>6,647</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.30% [42.7%-<b>45.9%</b>]</td>
	<td>3,686</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.44% [44.3%-<b>46.5%</b>]</td>
	<td>8,207</td>
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
	<td>105,667</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>41.94% [<b>36.7%</b>-47.1%]</td>
	<td>360</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>41.93% [<b>39.5%</b>-44.4%]</td>
	<td>1,593</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>45.36% [<b>40.4%</b>-50.3%]</td>
	<td>399</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>43.57% [<b>41.0%</b>-46.1%]</td>
	<td>1,494</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>45.28% [<b>41.3%</b>-49.2%]</td>
	<td>636</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sylas"></span> Sylas</td>
	<td>42.69% [41.4%-<b>44.0%</b>]</td>
	<td>5,730</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>41.93% [39.5%-<b>44.4%</b>]</td>
	<td>1,593</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>43.57% [41.0%-<b>46.1%</b>]</td>
	<td>1,494</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.67% [43.0%-<b>46.3%</b>]</td>
	<td>3,667</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>41.94% [36.7%-<b>47.1%</b>]</td>
	<td>360</td>
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
	<td>47.17% [46.9%-47.4%]</td>
	<td>193,190</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>42.32% [<b>38.5%</b>-46.1%]</td>
	<td>671</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.52% [<b>39.1%</b>-48.0%]</td>
	<td>494</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.98% [<b>39.3%</b>-46.7%]</td>
	<td>726</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.91% [<b>39.4%</b>-44.4%]</td>
	<td>1,589</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.03% [<b>40.1%</b>-45.9%]</td>
	<td>1,155</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>41.91% [39.4%-<b>44.4%</b>]</td>
	<td>1,589</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>43.48% [42.2%-<b>44.7%</b>]</td>
	<td>6,288</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.29% [41.7%-<b>44.9%</b>]</td>
	<td>3,680</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>43.00% [40.6%-<b>45.4%</b>]</td>
	<td>1,693</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>43.06% [40.7%-<b>45.5%</b>]</td>
	<td>1,707</td>
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
	<td>50.00% [49.7%-50.3%]</td>
	<td>104,717</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>41.61% [<b>36.9%</b>-46.3%]</td>
	<td>435</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.11% [<b>38.9%</b>-43.3%]</td>
	<td>1,997</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.02% [<b>39.2%</b>-48.9%]</td>
	<td>418</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.97% [<b>40.3%</b>-49.7%]</td>
	<td>447</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>46.43% [<b>40.5%</b>-52.4%]</td>
	<td>280</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>41.11% [38.9%-<b>43.3%</b>]</td>
	<td>1,997</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.01% [42.1%-<b>45.9%</b>]</td>
	<td>2,647</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>44.04% [42.1%-<b>46.0%</b>]</td>
	<td>2,668</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.45% [42.7%-<b>46.2%</b>]</td>
	<td>3,388</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>41.61% [36.9%-<b>46.3%</b>]</td>
	<td>435</td>
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
	<td>49.25% [49.0%-49.5%]</td>
	<td>127,238</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>42.55% [<b>36.7%</b>-48.4%]</td>
	<td>282</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>43.88% [<b>38.5%</b>-49.3%]</td>
	<td>335</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>44.70% [<b>39.0%</b>-50.4%]</td>
	<td>302</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.39% [<b>39.1%</b>-47.7%]</td>
	<td>537</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.04% [<b>40.8%</b>-47.3%]</td>
	<td>940</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>45.11% [43.2%-<b>47.1%</b>]</td>
	<td>2,616</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nasus"></span> Nasus</td>
	<td>44.04% [40.8%-<b>47.3%</b>]</td>
	<td>940</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>43.39% [39.1%-<b>47.7%</b>]</td>
	<td>537</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.29% [44.9%-<b>47.7%</b>]</td>
	<td>4,921</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.79% [45.6%-<b>48.0%</b>]</td>
	<td>7,143</td>
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
	<td>47.57% [47.3%-47.9%]</td>
	<td>109,030</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>41.69% [<b>37.0%</b>-46.3%]</td>
	<td>451</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>45.51% [<b>38.0%</b>-53.0%]</td>
	<td>178</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>40.99% [<b>38.2%</b>-43.8%]</td>
	<td>1,249</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.54% [<b>39.0%</b>-48.1%]</td>
	<td>480</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.34% [<b>39.0%</b>-45.7%]</td>
	<td>888</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>40.99% [38.2%-<b>43.8%</b>]</td>
	<td>1,249</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.54% [41.0%-<b>44.0%</b>]</td>
	<td>4,401</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>42.34% [39.0%-<b>45.7%</b>]</td>
	<td>888</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>43.59% [41.4%-<b>45.8%</b>]</td>
	<td>2,099</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>43.68% [41.6%-<b>45.8%</b>]</td>
	<td>2,200</td>
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
	<td>49.13% [48.8%-49.5%]</td>
	<td>80,728</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>44.76% [<b>37.9%</b>-51.6%]</td>
	<td>210</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.14% [<b>37.9%</b>-50.3%]</td>
	<td>256</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>44.96% [<b>39.0%</b>-50.9%]</td>
	<td>278</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>45.15% [<b>39.1%</b>-51.2%]</td>
	<td>268</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>45.32% [<b>39.3%</b>-51.3%]</td>
	<td>278</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.43% [43.4%-<b>47.4%</b>]</td>
	<td>2,441</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>46.68% [45.0%-<b>48.4%</b>]</td>
	<td>3,355</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>46.06% [43.5%-<b>48.6%</b>]</td>
	<td>1,522</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>47.08% [45.4%-<b>48.7%</b>]</td>
	<td>3,713</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>46.94% [44.7%-<b>49.1%</b>]</td>
	<td>2,062</td>
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
	<td>52.48% [52.0%-52.9%]</td>
	<td>50,648</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>44.12% [<b>35.6%</b>-52.6%]</td>
	<td>136</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.09% [<b>37.9%</b>-50.3%]</td>
	<td>254</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>41.85% [<b>39.0%</b>-44.7%]</td>
	<td>1,178</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>47.49% [<b>41.3%</b>-53.7%]</td>
	<td>259</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.98% [<b>41.6%</b>-54.3%]</td>
	<td>248</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>41.85% [39.0%-<b>44.7%</b>]</td>
	<td>1,178</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>44.09% [37.9%-<b>50.3%</b>]</td>
	<td>254</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.51% [46.4%-<b>50.6%</b>]</td>
	<td>2,247</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>48.75% [46.7%-<b>50.8%</b>]</td>
	<td>2,318</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.35% [45.9%-<b>50.8%</b>]</td>
	<td>1,607</td>
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
	<td>44.61% [44.4%-44.8%]</td>
	<td>298,025</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>40.02% [<b>37.1%</b>-43.0%]</td>
	<td>1,092</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>38.58% [<b>37.4%</b>-39.7%]</td>
	<td>7,288</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>40.09% [<b>38.7%</b>-41.5%]</td>
	<td>5,074</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>42.34% [<b>39.0%</b>-45.7%]</td>
	<td>862</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>40.72% [<b>39.2%</b>-42.2%]</td>
	<td>4,261</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>38.58% [37.4%-<b>39.7%</b>]</td>
	<td>7,288</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>40.60% [39.8%-<b>41.4%</b>]</td>
	<td>13,353</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>40.09% [38.7%-<b>41.5%</b>]</td>
	<td>5,074</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>40.68% [39.8%-<b>41.5%</b>]</td>
	<td>13,290</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-viktor"></span> Viktor</td>
	<td>40.72% [39.2%-<b>42.2%</b>]</td>
	<td>4,261</td>
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
	<td>45.57% [45.3%-45.8%]</td>
	<td>161,149</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>41.71% [<b>36.9%</b>-46.5%]</td>
	<td>422</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>41.89% [<b>37.4%</b>-46.4%]</td>
	<td>475</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>41.44% [<b>38.3%</b>-44.6%]</td>
	<td>999</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>44.44% [<b>38.6%</b>-50.3%]</td>
	<td>288</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>39.91% [<b>38.7%</b>-41.1%]</td>
	<td>6,435</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>39.91% [38.7%-<b>41.1%</b>]</td>
	<td>6,435</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>40.45% [38.9%-<b>42.0%</b>]</td>
	<td>3,973</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>42.61% [40.9%-<b>44.3%</b>]</td>
	<td>3,377</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>43.08% [41.8%-<b>44.4%</b>]</td>
	<td>6,047</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>43.25% [42.1%-<b>44.4%</b>]</td>
	<td>7,803</td>
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
	<td>50.49% [50.1%-50.9%]</td>
	<td>57,346</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>45.11% [<b>36.5%</b>-53.7%]</td>
	<td>133</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>43.96% [<b>37.1%</b>-50.9%]</td>
	<td>207</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>44.16% [<b>37.1%</b>-51.2%]</td>
	<td>197</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>43.63% [<b>38.4%</b>-48.9%]</td>
	<td>353</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>44.14% [<b>39.0%</b>-49.3%]</td>
	<td>367</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.64% [42.5%-<b>46.8%</b>]</td>
	<td>2,081</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>44.26% [41.5%-<b>47.0%</b>]</td>
	<td>1,290</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>43.63% [38.4%-<b>48.9%</b>]</td>
	<td>353</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>46.95% [44.9%-<b>49.0%</b>]</td>
	<td>2,347</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>44.14% [39.0%-<b>49.3%</b>]</td>
	<td>367</td>
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
	<td>52.21% [51.8%-52.6%]</td>
	<td>52,869</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>43.48% [<b>35.0%</b>-51.9%]</td>
	<td>138</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>42.62% [<b>35.3%</b>-49.9%]</td>
	<td>183</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>41.63% [<b>35.3%</b>-47.9%]</td>
	<td>245</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>44.79% [<b>37.0%</b>-52.6%]</td>
	<td>163</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.14% [<b>38.7%</b>-55.6%]</td>
	<td>140</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>44.44% [41.6%-<b>47.3%</b>]</td>
	<td>1,186</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.38% [41.3%-<b>47.5%</b>]</td>
	<td>1,023</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>44.14% [40.6%-<b>47.7%</b>]</td>
	<td>777</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>41.63% [35.3%-<b>47.9%</b>]</td>
	<td>245</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.60% [42.4%-<b>48.8%</b>]</td>
	<td>954</td>
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
	<td>45.98% [45.7%-46.3%]</td>
	<td>125,886</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>38.08% [<b>33.7%</b>-42.4%]</td>
	<td>499</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>40.56% [<b>34.8%</b>-46.4%]</td>
	<td>286</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>38.40% [<b>35.1%</b>-41.7%]</td>
	<td>875</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>40.54% [<b>37.2%</b>-43.9%]</td>
	<td>856</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gragas"></span> Gragas</td>
	<td>42.03% [<b>37.5%</b>-46.5%]</td>
	<td>483</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>38.40% [35.1%-<b>41.7%</b>]</td>
	<td>875</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>40.84% [39.3%-<b>42.4%</b>]</td>
	<td>4,033</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>38.08% [33.7%-<b>42.4%</b>]</td>
	<td>499</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>40.54% [37.2%-<b>43.9%</b>]</td>
	<td>856</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-malzahar"></span> Malzahar</td>
	<td>42.14% [40.3%-<b>43.9%</b>]</td>
	<td>3,028</td>
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
	<td>41.32% [41.0%-41.6%]</td>
	<td>122,835</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>35.45% [<b>29.0%</b>-41.9%]</td>
	<td>220</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>37.57% [<b>32.3%</b>-42.8%]</td>
	<td>338</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>37.85% [<b>32.4%</b>-43.3%]</td>
	<td>317</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>35.89% [<b>32.6%</b>-39.1%]</td>
	<td>875</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>36.30% [<b>33.3%</b>-39.3%]</td>
	<td>1,000</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>37.45% [36.1%-<b>38.8%</b>]</td>
	<td>4,862</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>35.89% [32.6%-<b>39.1%</b>]</td>
	<td>875</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>37.62% [36.0%-<b>39.2%</b>]</td>
	<td>3,767</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>36.30% [33.3%-<b>39.3%</b>]</td>
	<td>1,000</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>37.64% [35.5%-<b>39.8%</b>]</td>
	<td>2,067</td>
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
	<td>40.96% [40.5%-41.4%]</td>
	<td>50,416</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>28.89% [<b>21.1%</b>-36.7%]</td>
	<td>135</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>35.65% [<b>26.7%</b>-44.6%]</td>
	<td>115</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>37.93% [<b>27.5%</b>-48.3%]</td>
	<td>87</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>37.16% [<b>31.2%</b>-43.1%]</td>
	<td>261</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>34.52% [<b>31.4%</b>-37.7%]</td>
	<td>901</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>28.89% [21.1%-<b>36.7%</b>]</td>
	<td>135</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>34.52% [31.4%-<b>37.7%</b>]</td>
	<td>901</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>37.17% [35.0%-<b>39.4%</b>]</td>
	<td>1,961</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>38.06% [36.0%-<b>40.1%</b>]</td>
	<td>2,160</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ahri"></span> Ahri</td>
	<td>38.65% [36.7%-<b>40.6%</b>]</td>
	<td>2,432</td>
</tr>
</table>

</details>
### ADC

<details>
<summary>Click to view</summary>

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
	<td>52.55% [52.5%-52.6%]</td>
	<td>2,918,314</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.93% [<b>46.1%</b>-47.8%]</td>
	<td>14,047</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.66% [<b>47.8%</b>-49.5%]</td>
	<td>14,442</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.95% [<b>48.0%</b>-49.9%]</td>
	<td>10,300</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.91% [<b>48.2%</b>-49.6%]</td>
	<td>19,963</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>50.64% [<b>49.7%</b>-51.6%]</td>
	<td>11,271</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.93% [46.1%-<b>47.8%</b>]</td>
	<td>14,047</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.66% [47.8%-<b>49.5%</b>]</td>
	<td>14,442</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.91% [48.2%-<b>49.6%</b>]</td>
	<td>19,963</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.95% [48.0%-<b>49.9%</b>]</td>
	<td>10,300</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>50.18% [49.8%-<b>50.5%</b>]</td>
	<td>80,214</td>
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
	<td>54.50% [54.2%-54.8%]</td>
	<td>127,665</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.91% [<b>45.0%</b>-52.8%]</td>
	<td>644</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>50.69% [<b>47.2%</b>-54.2%]</td>
	<td>801</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>51.72% [<b>47.5%</b>-56.0%]</td>
	<td>551</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>52.79% [<b>50.4%</b>-55.2%]</td>
	<td>1,682</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>51.08% [<b>50.4%</b>-51.8%]</td>
	<td>19,963</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>51.08% [50.4%-<b>51.8%</b>]</td>
	<td>19,963</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.91% [45.0%-<b>52.8%</b>]</td>
	<td>644</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>50.69% [47.2%-<b>54.2%</b>]</td>
	<td>801</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>52.81% [51.2%-<b>54.4%</b>]</td>
	<td>4,041</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>52.79% [50.8%-<b>54.8%</b>]</td>
	<td>2,544</td>
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
	<td>51.93% [51.8%-52.1%]</td>
	<td>377,646</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.21% [<b>45.2%</b>-49.2%]</td>
	<td>2,544</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.34% [<b>46.2%</b>-50.4%]</td>
	<td>2,257</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.85% [<b>46.3%</b>-51.4%]</td>
	<td>1,521</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.49% [<b>46.7%</b>-52.3%]</td>
	<td>1,283</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.94% [<b>46.9%</b>-51.0%]</td>
	<td>2,303</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>48.64% [48.2%-<b>49.0%</b>]</td>
	<td>65,061</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.21% [45.2%-<b>49.2%</b>]</td>
	<td>2,544</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>48.94% [47.9%-<b>50.0%</b>]</td>
	<td>9,101</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kai-sa"></span> Kai'Sa</td>
	<td>49.85% [49.4%-<b>50.3%</b>]</td>
	<td>50,622</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.34% [46.2%-<b>50.4%</b>]</td>
	<td>2,257</td>
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
	<td>53.47% [53.1%-53.9%]</td>
	<td>65,889</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>49.18% [<b>45.6%</b>-52.7%]</td>
	<td>797</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>51.16% [<b>45.8%</b>-56.5%]</td>
	<td>346</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>50.72% [<b>46.5%</b>-55.0%]</td>
	<td>554</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>51.96% [<b>46.7%</b>-57.2%]</td>
	<td>358</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>51.09% [<b>47.2%</b>-55.0%]</td>
	<td>644</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>51.05% [50.1%-<b>52.0%</b>]</td>
	<td>10,300</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sivir"></span> Sivir</td>
	<td>49.18% [45.6%-<b>52.7%</b>]</td>
	<td>797</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>50.51% [47.7%-<b>53.3%</b>]</td>
	<td>1,283</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kai-sa"></span> Kai'Sa</td>
	<td>53.07% [52.0%-<b>54.1%</b>]</td>
	<td>8,581</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>50.72% [46.5%-<b>55.0%</b>]</td>
	<td>554</td>
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
	<td>50.71% [50.6%-50.8%]</td>
	<td>2,677,019</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.95% [<b>42.1%</b>-43.8%]</td>
	<td>13,391</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.79% [<b>45.0%</b>-46.6%]</td>
	<td>16,367</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.93% [<b>45.9%</b>-48.0%]</td>
	<td>8,581</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.97% [<b>46.1%</b>-47.8%]</td>
	<td>12,884</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.53% [<b>46.2%</b>-46.9%]</td>
	<td>79,073</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.95% [42.1%-<b>43.8%</b>]</td>
	<td>13,391</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.79% [45.0%-<b>46.6%</b>]</td>
	<td>16,367</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.53% [46.2%-<b>46.9%</b>]</td>
	<td>79,073</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.08% [46.4%-<b>47.7%</b>]</td>
	<td>22,790</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.97% [46.1%-<b>47.8%</b>]</td>
	<td>12,884</td>
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
	<td>50.90% [50.8%-51.0%]</td>
	<td>599,914</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.73% [<b>44.5%</b>-48.9%]</td>
	<td>2,082</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.27% [<b>44.9%</b>-49.6%]</td>
	<td>1,792</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.19% [<b>45.6%</b>-48.8%]</td>
	<td>4,041</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.41% [<b>46.4%</b>-50.4%]</td>
	<td>2,551</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.48% [<b>46.5%</b>-50.4%]</td>
	<td>2,634</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.19% [45.6%-<b>48.8%</b>]</td>
	<td>4,041</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.11% [47.3%-<b>48.9%</b>]</td>
	<td>16,070</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.73% [44.5%-<b>48.9%</b>]</td>
	<td>2,082</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>49.14% [48.8%-<b>49.5%</b>]</td>
	<td>93,591</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.27% [44.9%-<b>49.6%</b>]</td>
	<td>1,792</td>
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
	<td>54.13% [53.8%-54.5%]</td>
	<td>94,371</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.29% [<b>43.9%</b>-52.6%]</td>
	<td>526</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.77% [<b>44.7%</b>-52.8%]</td>
	<td>609</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.28% [<b>45.0%</b>-53.5%]</td>
	<td>554</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.31% [<b>45.8%</b>-52.8%]</td>
	<td>801</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>52.50% [<b>48.1%</b>-56.9%]</td>
	<td>520</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>51.34% [50.5%-<b>52.2%</b>]</td>
	<td>14,442</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.29% [43.9%-<b>52.6%</b>]</td>
	<td>526</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>48.77% [44.7%-<b>52.8%</b>]</td>
	<td>609</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.31% [45.8%-<b>52.8%</b>]</td>
	<td>801</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>51.52% [49.6%-<b>53.5%</b>]</td>
	<td>2,634</td>
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
	<td>52.86% [52.7%-53.0%]</td>
	<td>521,413</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.37% [<b>43.8%</b>-47.0%]</td>
	<td>3,844</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.58% [<b>44.4%</b>-48.8%]</td>
	<td>2,005</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.86% [<b>45.1%</b>-48.7%]</td>
	<td>3,107</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.96% [<b>45.8%</b>-50.1%]</td>
	<td>2,083</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>48.99% [<b>47.9%</b>-50.0%]</td>
	<td>9,168</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.37% [43.8%-<b>47.0%</b>]</td>
	<td>3,844</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.86% [45.1%-<b>48.7%</b>]</td>
	<td>3,107</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.58% [44.4%-<b>48.8%</b>]</td>
	<td>2,005</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>48.99% [47.9%-<b>50.0%</b>]</td>
	<td>9,168</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.96% [45.8%-<b>50.1%</b>]</td>
	<td>2,083</td>
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
	<td>50.27% [50.2%-50.4%]</td>
	<td>1,408,243</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.08% [<b>41.8%</b>-44.3%]</td>
	<td>6,133</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.27% [<b>44.2%</b>-46.4%]</td>
	<td>8,030</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.79% [<b>44.2%</b>-47.4%]</td>
	<td>4,075</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.69% [<b>44.5%</b>-46.9%]</td>
	<td>6,487</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.79% [<b>45.3%</b>-48.3%]</td>
	<td>4,552</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.08% [41.8%-<b>44.3%</b>]</td>
	<td>6,133</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.27% [44.2%-<b>46.4%</b>]</td>
	<td>8,030</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.69% [44.5%-<b>46.9%</b>]</td>
	<td>6,487</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.79% [44.2%-<b>47.4%</b>]</td>
	<td>4,075</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>47.42% [46.9%-<b>47.9%</b>]</td>
	<td>37,169</td>
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
	<td>49.86% [49.8%-49.9%]</td>
	<td>1,736,834</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.28% [<b>43.2%</b>-45.4%]</td>
	<td>8,117</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.71% [<b>43.7%</b>-45.7%]</td>
	<td>10,582</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.21% [<b>43.9%</b>-46.6%]</td>
	<td>5,514</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.19% [<b>44.0%</b>-46.4%]</td>
	<td>7,021</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.54% [<b>44.2%</b>-46.9%]</td>
	<td>5,393</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.28% [43.2%-<b>45.4%</b>]</td>
	<td>8,117</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.71% [43.7%-<b>45.7%</b>]</td>
	<td>10,582</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.19% [44.0%-<b>46.4%</b>]</td>
	<td>7,021</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.21% [43.9%-<b>46.6%</b>]</td>
	<td>5,514</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.54% [44.2%-<b>46.9%</b>]</td>
	<td>5,393</td>
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
	<td>50.23% [50.1%-50.3%]</td>
	<td>1,190,134</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.49% [<b>41.0%</b>-44.0%]</td>
	<td>4,286</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.67% [<b>43.6%</b>-45.7%]</td>
	<td>8,785</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.44% [<b>44.1%</b>-46.8%]</td>
	<td>5,192</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.55% [<b>44.8%</b>-48.3%]</td>
	<td>3,130</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.33% [<b>44.8%</b>-47.9%]</td>
	<td>4,278</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.49% [41.0%-<b>44.0%</b>]</td>
	<td>4,286</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.67% [43.6%-<b>45.7%</b>]</td>
	<td>8,785</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.44% [44.1%-<b>46.8%</b>]</td>
	<td>5,192</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.26% [45.6%-<b>46.9%</b>]</td>
	<td>23,303</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>47.42% [47.2%-<b>47.7%</b>]</td>
	<td>187,339</td>
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
	<td>55.36% [55.0%-55.7%]</td>
	<td>85,369</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.44% [<b>40.4%</b>-48.5%]</td>
	<td>612</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.84% [<b>43.5%</b>-54.2%]</td>
	<td>346</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>49.06% [<b>43.9%</b>-54.3%]</td>
	<td>371</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.59% [<b>46.4%</b>-50.8%]</td>
	<td>2,089</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>51.71% [<b>47.4%</b>-56.1%]</td>
	<td>526</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.44% [40.4%-<b>48.5%</b>]</td>
	<td>612</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.59% [46.4%-<b>50.8%</b>]</td>
	<td>2,089</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>49.86% [47.5%-<b>52.2%</b>]</td>
	<td>1,801</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>51.55% [49.6%-<b>53.5%</b>]</td>
	<td>2,551</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>53.07% [52.2%-<b>53.9%</b>]</td>
	<td>14,047</td>
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
	<td>52.25% [51.9%-52.6%]</td>
	<td>66,208</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.04% [<b>42.8%</b>-53.3%]</td>
	<td>358</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.50% [<b>43.1%</b>-51.9%]</td>
	<td>520</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.28% [<b>44.0%</b>-52.5%]</td>
	<td>551</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>50.94% [<b>45.7%</b>-56.1%]</td>
	<td>371</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>50.70% [<b>45.9%</b>-55.5%]</td>
	<td>426</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>49.36% [48.4%-<b>50.3%</b>]</td>
	<td>11,271</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.50% [43.1%-<b>51.9%</b>]</td>
	<td>520</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kai-sa"></span> Kai'Sa</td>
	<td>51.38% [50.4%-<b>52.4%</b>]</td>
	<td>9,601</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.28% [44.0%-<b>52.5%</b>]</td>
	<td>551</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.04% [42.8%-<b>53.3%</b>]</td>
	<td>358</td>
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
	<td>48.90% [48.8%-49.0%]</td>
	<td>555,745</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.53% [<b>42.4%</b>-46.6%]</td>
	<td>2,275</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.65% [<b>42.8%</b>-46.5%]</td>
	<td>2,889</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.80% [<b>43.2%</b>-48.4%]</td>
	<td>1,415</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.49% [<b>43.4%</b>-47.6%]</td>
	<td>2,238</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.75% [<b>44.3%</b>-49.2%]</td>
	<td>1,615</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>44.65% [42.8%-<b>46.5%</b>]</td>
	<td>2,889</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.53% [42.4%-<b>46.6%</b>]</td>
	<td>2,275</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>46.59% [46.3%-<b>46.9%</b>]</td>
	<td>94,152</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.19% [45.4%-<b>47.0%</b>]</td>
	<td>14,185</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.08% [45.1%-<b>47.1%</b>]</td>
	<td>10,180</td>
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
	<td>48.47% [48.4%-48.6%]</td>
	<td>1,475,792</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.73% [<b>42.4%</b>-45.0%]</td>
	<td>5,946</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.15% [<b>42.6%</b>-45.7%]</td>
	<td>4,032</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.81% [<b>44.5%</b>-47.1%]</td>
	<td>5,957</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.68% [<b>44.6%</b>-46.8%]</td>
	<td>8,371</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.64% [<b>45.1%</b>-48.2%]</td>
	<td>4,288</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.73% [42.4%-<b>45.0%</b>]</td>
	<td>5,946</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.15% [42.6%-<b>45.7%</b>]</td>
	<td>4,032</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.68% [45.1%-<b>46.2%</b>]</td>
	<td>31,901</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>46.10% [45.9%-<b>46.3%</b>]</td>
	<td>264,002</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.68% [44.6%-<b>46.8%</b>]</td>
	<td>8,371</td>
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
	<td>49.29% [49.1%-49.5%]</td>
	<td>334,476</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.15% [<b>41.3%</b>-45.0%]</td>
	<td>2,797</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.92% [<b>42.5%</b>-47.3%]</td>
	<td>1,723</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.40% [<b>43.6%</b>-49.2%]</td>
	<td>1,304</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>47.31% [<b>44.3%</b>-50.3%]</td>
	<td>1,116</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.04% [<b>44.9%</b>-49.1%]</td>
	<td>2,281</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>43.15% [41.3%-<b>45.0%</b>]</td>
	<td>2,797</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.92% [42.5%-<b>47.3%</b>]</td>
	<td>1,723</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.88% [45.9%-<b>47.8%</b>]</td>
	<td>10,955</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kai-sa"></span> Kai'Sa</td>
	<td>47.83% [47.4%-<b>48.3%</b>]</td>
	<td>45,228</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>48.15% [47.7%-<b>48.6%</b>]</td>
	<td>53,342</td>
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
	<td>48.68% [48.6%-48.8%]</td>
	<td>767,806</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.38% [<b>41.6%</b>-45.1%]</td>
	<td>3,278</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.11% [<b>42.2%</b>-46.0%]</td>
	<td>2,691</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.81% [<b>42.3%</b>-45.3%]</td>
	<td>4,268</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.67% [<b>43.6%</b>-47.7%]</td>
	<td>2,400</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.60% [<b>44.5%</b>-48.7%]</td>
	<td>2,365</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.38% [41.6%-<b>45.1%</b>]</td>
	<td>3,278</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.81% [42.3%-<b>45.3%</b>]</td>
	<td>4,268</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.11% [42.2%-<b>46.0%</b>]</td>
	<td>2,691</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.98% [45.2%-<b>46.7%</b>]</td>
	<td>18,565</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>46.67% [46.4%-<b>46.9%</b>]</td>
	<td>130,031</td>
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
	<td>48.03% [47.9%-48.1%]</td>
	<td>1,526,501</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>41.40% [<b>40.2%</b>-42.6%]</td>
	<td>6,993</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.65% [<b>41.7%</b>-43.6%]</td>
	<td>10,246</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.37% [<b>42.0%</b>-44.7%]</td>
	<td>5,476</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.23% [<b>43.7%</b>-46.8%]</td>
	<td>4,205</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.18% [<b>43.7%</b>-46.6%]</td>
	<td>4,805</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>41.40% [40.2%-<b>42.6%</b>]</td>
	<td>6,993</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.65% [41.7%-<b>43.6%</b>]</td>
	<td>10,246</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.37% [42.0%-<b>44.7%</b>]</td>
	<td>5,476</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>44.35% [43.8%-<b>44.9%</b>]</td>
	<td>31,901</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>45.14% [44.9%-<b>45.3%</b>]</td>
	<td>270,060</td>
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
	<td>48.45% [48.3%-48.6%]</td>
	<td>489,662</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.73% [<b>41.0%</b>-44.5%]</td>
	<td>3,286</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.15% [<b>41.6%</b>-46.7%]</td>
	<td>1,572</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.92% [<b>41.8%</b>-46.0%]</td>
	<td>2,188</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.55% [<b>42.3%</b>-46.8%]</td>
	<td>2,009</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.20% [<b>42.6%</b>-47.8%]</td>
	<td>1,447</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.73% [41.0%-<b>44.5%</b>]</td>
	<td>3,286</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.09% [44.2%-<b>46.0%</b>]</td>
	<td>12,547</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.92% [41.8%-<b>46.0%</b>]</td>
	<td>2,188</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>45.80% [45.4%-<b>46.2%</b>]</td>
	<td>79,215</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.15% [41.6%-<b>46.7%</b>]</td>
	<td>1,572</td>
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
	<td>49.59% [49.4%-49.8%]</td>
	<td>259,595</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.21% [<b>41.3%</b>-47.1%]</td>
	<td>1,158</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.48% [<b>41.4%</b>-47.5%]</td>
	<td>1,050</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.01% [<b>43.7%</b>-46.3%]</td>
	<td>5,539</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.21% [<b>44.8%</b>-49.6%]</td>
	<td>1,682</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>47.30% [<b>45.6%</b>-49.0%]</td>
	<td>3,598</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.01% [43.7%-<b>46.3%</b>]</td>
	<td>5,539</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.21% [41.3%-<b>47.1%</b>]</td>
	<td>1,158</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.48% [41.4%-<b>47.5%</b>]</td>
	<td>1,050</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>47.44% [46.9%-<b>47.9%</b>]</td>
	<td>39,928</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>47.30% [45.6%-<b>49.0%</b>]</td>
	<td>3,598</td>
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
	<td>47.57% [47.4%-47.7%]</td>
	<td>449,579</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.37% [<b>40.2%</b>-44.6%]</td>
	<td>2,039</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.42% [<b>41.3%</b>-45.6%]</td>
	<td>2,098</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.10% [<b>41.5%</b>-46.7%]</td>
	<td>1,467</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.68% [<b>41.8%</b>-45.5%]</td>
	<td>2,864</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.98% [<b>42.5%</b>-47.5%]</td>
	<td>1,614</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.37% [40.2%-<b>44.6%</b>]</td>
	<td>2,039</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.68% [41.8%-<b>45.5%</b>]</td>
	<td>2,864</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.67% [43.8%-<b>45.6%</b>]</td>
	<td>12,372</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>44.73% [43.9%-<b>45.6%</b>]</td>
	<td>13,906</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>43.42% [41.3%-<b>45.6%</b>]</td>
	<td>2,098</td>
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
	<td>48.90% [48.7%-49.1%]</td>
	<td>443,002</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.58% [<b>40.4%</b>-44.8%]</td>
	<td>1,975</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.51% [<b>41.2%</b>-45.8%]</td>
	<td>1,917</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.46% [<b>41.7%</b>-45.2%]</td>
	<td>3,150</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.70% [<b>42.3%</b>-47.1%]</td>
	<td>1,707</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>45.08% [<b>43.2%</b>-47.0%]</td>
	<td>2,731</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.58% [40.4%-<b>44.8%</b>]</td>
	<td>1,975</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.46% [41.7%-<b>45.2%</b>]</td>
	<td>3,150</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.51% [41.2%-<b>45.8%</b>]</td>
	<td>1,917</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>45.70% [44.8%-<b>46.6%</b>]</td>
	<td>13,226</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>45.17% [43.5%-<b>46.8%</b>]</td>
	<td>3,613</td>
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
	<td>47.86% [47.7%-48.1%]</td>
	<td>231,064</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>42.98% [<b>39.9%</b>-46.1%]</td>
	<td>1,026</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.69% [<b>40.4%</b>-47.0%]</td>
	<td>904</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.81% [<b>41.0%</b>-48.6%]</td>
	<td>674</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.83% [<b>41.3%</b>-48.4%]</td>
	<td>774</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>43.10% [<b>41.8%</b>-44.4%]</td>
	<td>5,557</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>43.10% [41.8%-<b>44.4%</b>]</td>
	<td>5,557</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>42.98% [39.9%-<b>46.1%</b>]</td>
	<td>1,026</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>45.96% [45.0%-<b>46.9%</b>]</td>
	<td>11,383</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>43.69% [40.4%-<b>47.0%</b>]</td>
	<td>904</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>46.94% [46.4%-<b>47.4%</b>]</td>
	<td>38,714</td>
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
	<td>48.09% [47.9%-48.3%]</td>
	<td>304,275</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>40.92% [<b>38.0%</b>-43.8%]</td>
	<td>1,129</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.96% [<b>40.0%</b>-45.9%]</td>
	<td>1,143</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.23% [<b>40.9%</b>-45.5%]</td>
	<td>1,846</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.80% [<b>41.4%</b>-48.2%]</td>
	<td>846</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.35% [<b>42.8%</b>-49.9%]</td>
	<td>809</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>40.92% [38.0%-<b>43.8%</b>]</td>
	<td>1,129</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>44.93% [44.4%-<b>45.4%</b>]</td>
	<td>42,115</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>43.23% [40.9%-<b>45.5%</b>]</td>
	<td>1,846</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.96% [40.0%-<b>45.9%</b>]</td>
	<td>1,143</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>44.88% [43.7%-<b>46.1%</b>]</td>
	<td>6,633</td>
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
	<td>46.13% [46.0%-46.3%]</td>
	<td>369,551</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>40.16% [<b>38.1%</b>-42.2%]</td>
	<td>2,211</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.83% [<b>39.9%</b>-45.7%]</td>
	<td>1,158</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>43.60% [<b>40.3%</b>-46.9%]</td>
	<td>899</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>42.47% [<b>40.5%</b>-44.5%]</td>
	<td>2,477</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.00% [<b>41.1%</b>-46.9%]</td>
	<td>1,159</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>40.16% [38.1%-<b>42.2%</b>]</td>
	<td>2,211</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>42.96% [41.9%-<b>44.0%</b>]</td>
	<td>8,575</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>42.47% [40.5%-<b>44.5%</b>]</td>
	<td>2,477</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kai-sa"></span> Kai'Sa</td>
	<td>44.27% [43.8%-<b>44.7%</b>]</td>
	<td>48,790</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>43.81% [42.5%-<b>45.1%</b>]</td>
	<td>6,167</td>
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
	<td>46.44% [46.3%-46.6%]</td>
	<td>301,373</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>42.57% [<b>39.3%</b>-45.9%]</td>
	<td>902</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>42.13% [<b>39.5%</b>-44.8%]</td>
	<td>1,360</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.59% [<b>39.8%</b>-45.4%]</td>
	<td>1,214</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>43.02% [<b>39.9%</b>-46.2%]</td>
	<td>995</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.45% [<b>40.1%</b>-44.8%]</td>
	<td>1,722</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>44.12% [43.7%-<b>44.6%</b>]</td>
	<td>48,308</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>43.52% [42.4%-<b>44.6%</b>]</td>
	<td>7,828</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>42.13% [39.5%-<b>44.8%</b>]</td>
	<td>1,360</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>42.45% [40.1%-<b>44.8%</b>]</td>
	<td>1,722</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>43.63% [42.2%-<b>45.1%</b>]</td>
	<td>4,815</td>
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
	<td>50.19% [49.9%-50.5%]</td>
	<td>116,077</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>39.65% [<b>35.6%</b>-43.7%]</td>
	<td>575</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.36% [<b>38.7%</b>-48.0%]</td>
	<td>452</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>42.38% [<b>39.4%</b>-45.4%]</td>
	<td>1,069</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>45.81% [<b>42.5%</b>-49.2%]</td>
	<td>884</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kalista"></span> Kalista</td>
	<td>45.83% [<b>43.0%</b>-48.7%]</td>
	<td>1,200</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>39.65% [35.6%-<b>43.7%</b>]</td>
	<td>575</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>42.38% [39.4%-<b>45.4%</b>]</td>
	<td>1,069</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>43.36% [38.7%-<b>48.0%</b>]</td>
	<td>452</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kalista"></span> Kalista</td>
	<td>45.83% [43.0%-<b>48.7%</b>]</td>
	<td>1,200</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>47.31% [45.7%-<b>48.9%</b>]</td>
	<td>3,900</td>
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
	<td>48.58% [48.4%-48.7%]</td>
	<td>512,887</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>40.08% [<b>37.9%</b>-42.3%]</td>
	<td>1,996</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>40.22% [<b>38.5%</b>-42.0%]</td>
	<td>3,148</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>44.61% [<b>42.1%</b>-47.1%]</td>
	<td>1,558</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>44.30% [<b>42.2%</b>-46.4%]</td>
	<td>2,314</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>43.80% [<b>42.9%</b>-44.7%]</td>
	<td>13,303</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>40.22% [38.5%-<b>42.0%</b>]</td>
	<td>3,148</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>40.08% [37.9%-<b>42.3%</b>]</td>
	<td>1,996</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>43.80% [42.9%-<b>44.7%</b>]</td>
	<td>13,303</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>44.77% [43.7%-<b>45.8%</b>]</td>
	<td>9,397</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>44.60% [43.3%-<b>45.9%</b>]</td>
	<td>6,027</td>
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
	<td>51.81% [51.5%-52.1%]</td>
	<td>139,990</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>41.39% [<b>38.0%</b>-44.7%]</td>
	<td>865</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>42.92% [<b>38.3%</b>-47.5%]</td>
	<td>466</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.55% [<b>38.4%</b>-46.7%]</td>
	<td>557</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>46.34% [<b>41.7%</b>-51.0%]</td>
	<td>464</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>46.49% [<b>42.4%</b>-50.6%]</td>
	<td>598</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>41.39% [38.0%-<b>44.7%</b>]</td>
	<td>865</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.55% [38.4%-<b>46.7%</b>]</td>
	<td>557</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>42.92% [38.3%-<b>47.5%</b>]</td>
	<td>466</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>48.28% [47.5%-<b>49.0%</b>]</td>
	<td>18,686</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>48.04% [46.4%-<b>49.7%</b>]</td>
	<td>3,618</td>
</tr>
</table>

</details>
### Support

<details>
<summary>Click to view</summary>

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
	<td>51.77% [51.7%-51.9%]</td>
	<td>889,410</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>49.78% [<b>48.2%</b>-51.4%]</td>
	<td>3,879</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>50.40% [<b>48.4%</b>-52.4%]</td>
	<td>2,397</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.09% [<b>48.5%</b>-49.7%]</td>
	<td>25,863</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.59% [<b>48.7%</b>-50.4%]</td>
	<td>13,764</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>49.34% [<b>49.0%</b>-49.7%]</td>
	<td>67,987</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.09% [48.5%-<b>49.7%</b>]</td>
	<td>25,863</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>49.34% [49.0%-<b>49.7%</b>]</td>
	<td>67,987</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.68% [49.1%-<b>50.3%</b>]</td>
	<td>30,225</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.62% [49.0%-<b>50.3%</b>]</td>
	<td>22,957</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.59% [48.7%-<b>50.4%</b>]</td>
	<td>13,764</td>
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
	<td>51.24% [51.1%-51.4%]</td>
	<td>741,329</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.72% [<b>46.8%</b>-50.6%]</td>
	<td>2,771</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>49.52% [<b>47.5%</b>-51.5%]</td>
	<td>2,522</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>50.49% [<b>48.2%</b>-52.8%]</td>
	<td>1,840</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.16% [<b>48.5%</b>-49.8%]</td>
	<td>22,067</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.35% [<b>48.5%</b>-50.2%]</td>
	<td>13,509</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>49.27% [48.8%-<b>49.8%</b>]</td>
	<td>42,338</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.16% [48.5%-<b>49.8%</b>]</td>
	<td>22,067</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.35% [48.5%-<b>50.2%</b>]</td>
	<td>13,509</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>50.17% [49.7%-<b>50.6%</b>]</td>
	<td>55,675</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.72% [46.8%-<b>50.6%</b>]</td>
	<td>2,771</td>
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
	<td>52.48% [52.3%-52.6%]</td>
	<td>486,215</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.92% [<b>46.6%</b>-51.2%]</td>
	<td>1,844</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.24% [<b>47.4%</b>-49.1%]</td>
	<td>15,132</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>50.55% [<b>47.6%</b>-53.5%]</td>
	<td>1,185</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.75% [<b>47.7%</b>-49.8%]</td>
	<td>8,656</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.21% [<b>48.0%</b>-50.4%]</td>
	<td>6,815</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.24% [47.4%-<b>49.1%</b>]</td>
	<td>15,132</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.75% [47.7%-<b>49.8%</b>]</td>
	<td>8,656</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.21% [48.0%-<b>50.4%</b>]</td>
	<td>6,815</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>50.04% [49.3%-<b>50.8%</b>]</td>
	<td>18,826</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>50.24% [49.5%-<b>51.0%</b>]</td>
	<td>16,193</td>
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
	<td>51.30% [51.1%-51.5%]</td>
	<td>272,345</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.64% [<b>46.6%</b>-52.7%]</td>
	<td>1,096</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.61% [<b>47.1%</b>-50.1%]</td>
	<td>4,380</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.37% [<b>47.5%</b>-49.2%]</td>
	<td>14,314</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>51.60% [<b>48.0%</b>-55.2%]</td>
	<td>752</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>51.56% [<b>48.2%</b>-55.0%]</td>
	<td>865</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.37% [47.5%-<b>49.2%</b>]</td>
	<td>14,314</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.05% [48.2%-<b>49.9%</b>]</td>
	<td>15,593</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.61% [47.1%-<b>50.1%</b>]</td>
	<td>4,380</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>50.00% [49.2%-<b>50.8%</b>]</td>
	<td>17,544</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>49.66% [48.5%-<b>50.8%</b>]</td>
	<td>7,132</td>
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
	<td>52.12% [52.0%-52.3%]</td>
	<td>513,128</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.57% [<b>46.0%</b>-51.1%]</td>
	<td>1,536</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.39% [<b>47.0%</b>-49.8%]</td>
	<td>5,044</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.36% [<b>47.0%</b>-49.7%]</td>
	<td>5,583</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.27% [<b>47.6%</b>-48.9%]</td>
	<td>23,188</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>49.76% [<b>48.4%</b>-51.1%]</td>
	<td>5,774</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.27% [47.6%-<b>48.9%</b>]</td>
	<td>23,188</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.36% [47.0%-<b>49.7%</b>]</td>
	<td>5,583</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.39% [47.0%-<b>49.8%</b>]</td>
	<td>5,044</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.66% [48.7%-<b>50.6%</b>]</td>
	<td>10,808</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.98% [49.2%-<b>50.7%</b>]</td>
	<td>17,136</td>
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
	<td>50.63% [50.5%-50.7%]</td>
	<td>989,003</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>48.22% [<b>46.5%</b>-50.0%]</td>
	<td>3,237</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.47% [<b>46.7%</b>-50.2%]</td>
	<td>3,375</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.19% [<b>47.0%</b>-49.3%]</td>
	<td>7,651</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.69% [<b>47.3%</b>-48.1%]</td>
	<td>56,405</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.40% [<b>47.6%</b>-49.2%]</td>
	<td>14,356</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.69% [47.3%-<b>48.1%</b>]</td>
	<td>56,405</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.43% [47.8%-<b>49.1%</b>]</td>
	<td>25,149</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.40% [47.6%-<b>49.2%</b>]</td>
	<td>14,356</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.58% [47.9%-<b>49.3%</b>]</td>
	<td>21,338</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>48.50% [47.7%-<b>49.3%</b>]</td>
	<td>14,622</td>
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
	<td>53.16% [52.9%-53.4%]</td>
	<td>156,882</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.97% [<b>46.4%</b>-49.6%]</td>
	<td>3,842</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>51.82% [<b>46.7%</b>-56.9%]</td>
	<td>384</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>49.05% [<b>47.1%</b>-51.0%]</td>
	<td>2,577</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.35% [<b>47.2%</b>-51.5%]</td>
	<td>2,083</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>51.13% [<b>47.2%</b>-55.0%]</td>
	<td>661</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.97% [46.4%-<b>49.6%</b>]</td>
	<td>3,842</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.46% [48.2%-<b>50.7%</b>]</td>
	<td>6,264</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>49.05% [47.1%-<b>51.0%</b>]</td>
	<td>2,577</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>49.83% [48.6%-<b>51.0%</b>]</td>
	<td>6,921</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.83% [48.2%-<b>51.4%</b>]</td>
	<td>3,929</td>
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
	<td>50.85% [50.7%-51.0%]</td>
	<td>434,340</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.64% [<b>46.6%</b>-52.6%]</td>
	<td>1,114</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>49.45% [<b>46.7%</b>-52.2%]</td>
	<td>1,284</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>49.36% [<b>46.8%</b>-52.0%]</td>
	<td>1,489</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.10% [<b>47.0%</b>-49.2%]</td>
	<td>8,808</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>50.35% [<b>47.2%</b>-53.5%]</td>
	<td>987</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.88% [47.2%-<b>48.5%</b>]</td>
	<td>23,303</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.10% [47.0%-<b>49.2%</b>]</td>
	<td>8,808</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>48.40% [47.4%-<b>49.4%</b>]</td>
	<td>10,176</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>49.70% [49.2%-<b>50.2%</b>]</td>
	<td>34,472</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.10% [47.9%-<b>50.3%</b>]</td>
	<td>6,941</td>
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
	<td>50.66% [50.6%-50.7%]</td>
	<td>1,359,232</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.77% [<b>45.5%</b>-48.1%]</td>
	<td>6,076</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.94% [<b>46.5%</b>-47.3%]</td>
	<td>60,291</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.94% [<b>47.0%</b>-48.9%]</td>
	<td>10,796</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.58% [<b>47.0%</b>-48.2%]</td>
	<td>29,402</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.79% [<b>47.1%</b>-50.5%]</td>
	<td>3,589</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.94% [46.5%-<b>47.3%</b>]</td>
	<td>60,291</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.77% [45.5%-<b>48.1%</b>]</td>
	<td>6,076</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.58% [47.0%-<b>48.2%</b>]</td>
	<td>29,402</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.06% [47.3%-<b>48.8%</b>]</td>
	<td>16,865</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.94% [47.0%-<b>48.9%</b>]</td>
	<td>10,796</td>
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
	<td>50.40% [50.2%-50.6%]</td>
	<td>392,268</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.63% [<b>46.0%</b>-51.3%]</td>
	<td>1,427</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.35% [<b>46.0%</b>-50.7%]</td>
	<td>1,787</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.80% [<b>46.1%</b>-51.5%]</td>
	<td>1,336</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.76% [<b>46.2%</b>-49.3%]</td>
	<td>4,282</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.05% [<b>46.8%</b>-49.3%]</td>
	<td>6,679</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.09% [47.4%-<b>48.8%</b>]</td>
	<td>21,368</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.95% [47.0%-<b>48.9%</b>]</td>
	<td>11,431</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.05% [46.8%-<b>49.3%</b>]</td>
	<td>6,679</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.76% [46.2%-<b>49.3%</b>]</td>
	<td>4,282</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.75% [48.0%-<b>49.5%</b>]</td>
	<td>20,126</td>
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
	<td>51.52% [51.3%-51.7%]</td>
	<td>249,552</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.13% [<b>45.2%</b>-53.1%]</td>
	<td>633</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.20% [<b>46.0%</b>-50.4%]</td>
	<td>2,025</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>48.62% [<b>46.7%</b>-50.5%]</td>
	<td>2,791</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>49.31% [<b>47.5%</b>-51.2%]</td>
	<td>2,912</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>50.94% [<b>47.6%</b>-54.3%]</td>
	<td>905</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.61% [47.8%-<b>49.5%</b>]</td>
	<td>13,701</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.20% [46.0%-<b>50.4%</b>]</td>
	<td>2,025</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>48.62% [46.7%-<b>50.5%</b>]</td>
	<td>2,791</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>49.31% [47.5%-<b>51.2%</b>]</td>
	<td>2,912</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-blitzcrank"></span> Blitzcrank</td>
	<td>50.12% [48.9%-<b>51.3%</b>]</td>
	<td>7,252</td>
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
	<td>52.19% [52.0%-52.4%]</td>
	<td>214,810</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.20% [<b>44.3%</b>-50.1%]</td>
	<td>1,214</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.85% [<b>45.6%</b>-48.1%]</td>
	<td>6,423</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.37% [<b>46.2%</b>-50.6%]</td>
	<td>2,057</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>50.32% [<b>46.3%</b>-54.3%]</td>
	<td>634</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>51.57% [<b>47.3%</b>-55.9%]</td>
	<td>543</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.85% [45.6%-<b>48.1%</b>]</td>
	<td>6,423</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.20% [44.3%-<b>50.1%</b>]</td>
	<td>1,214</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.37% [46.2%-<b>50.6%</b>]</td>
	<td>2,057</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>49.13% [47.4%-<b>50.9%</b>]</td>
	<td>3,234</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.80% [48.7%-<b>50.9%</b>]</td>
	<td>8,304</td>
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
	<td>50.75% [50.6%-50.9%]</td>
	<td>754,517</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.27% [<b>45.3%</b>-49.2%]</td>
	<td>2,564</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.78% [<b>45.4%</b>-48.2%]</td>
	<td>5,075</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.97% [<b>46.3%</b>-47.6%]</td>
	<td>23,843</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.30% [<b>46.5%</b>-48.1%]</td>
	<td>16,065</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.52% [<b>46.6%</b>-48.5%]</td>
	<td>10,861</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.97% [46.3%-<b>47.6%</b>]</td>
	<td>23,843</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>47.30% [46.5%-<b>48.1%</b>]</td>
	<td>16,065</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.78% [45.4%-<b>48.2%</b>]</td>
	<td>5,075</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.61% [47.0%-<b>48.2%</b>]</td>
	<td>24,902</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.78% [47.1%-<b>48.4%</b>]</td>
	<td>24,477</td>
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
	<td>51.72% [51.6%-51.9%]</td>
	<td>583,147</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.60% [<b>44.9%</b>-48.3%]</td>
	<td>3,414</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>47.65% [<b>45.4%</b>-49.9%]</td>
	<td>1,933</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>48.03% [<b>46.0%</b>-50.1%]</td>
	<td>2,386</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.67% [<b>46.4%</b>-49.0%]</td>
	<td>5,828</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.89% [<b>46.6%</b>-49.1%]</td>
	<td>6,413</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.60% [44.9%-<b>48.3%</b>]</td>
	<td>3,414</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.74% [46.9%-<b>48.6%</b>]</td>
	<td>15,133</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>47.67% [46.4%-<b>49.0%</b>]</td>
	<td>5,828</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.89% [46.6%-<b>49.1%</b>]</td>
	<td>6,413</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.79% [48.1%-<b>49.5%</b>]</td>
	<td>18,452</td>
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
	<td>51.85% [51.7%-52.0%]</td>
	<td>492,741</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.66% [<b>44.2%</b>-49.1%]</td>
	<td>1,663</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.98% [<b>45.4%</b>-48.6%]</td>
	<td>3,770</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>49.09% [<b>46.2%</b>-52.0%]</td>
	<td>1,208</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.43% [<b>47.1%</b>-49.7%]</td>
	<td>5,901</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.52% [<b>47.4%</b>-49.7%]</td>
	<td>7,418</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.98% [45.4%-<b>48.6%</b>]</td>
	<td>3,770</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.66% [44.2%-<b>49.1%</b>]</td>
	<td>1,663</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.61% [47.8%-<b>49.4%</b>]</td>
	<td>15,900</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.52% [47.4%-<b>49.7%</b>]</td>
	<td>7,418</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.43% [47.1%-<b>49.7%</b>]</td>
	<td>5,901</td>
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
	<td>50.06% [49.9%-50.3%]</td>
	<td>231,215</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>47.82% [<b>44.6%</b>-51.1%]</td>
	<td>939</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.30% [<b>45.1%</b>-49.5%]</td>
	<td>2,015</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.17% [<b>45.1%</b>-51.2%]</td>
	<td>1,094</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.98% [<b>45.3%</b>-52.7%]</td>
	<td>733</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>48.56% [<b>45.4%</b>-51.7%]</td>
	<td>1,009</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.94% [45.8%-<b>48.1%</b>]</td>
	<td>7,235</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.46% [46.6%-<b>48.3%</b>]</td>
	<td>12,973</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.37% [45.9%-<b>48.8%</b>]</td>
	<td>4,691</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.06% [46.7%-<b>49.4%</b>]</td>
	<td>5,776</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.30% [45.1%-<b>49.5%</b>]</td>
	<td>2,015</td>
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
	<td>49.87% [49.8%-50.0%]</td>
	<td>1,148,092</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.71% [<b>44.1%</b>-45.3%]</td>
	<td>30,006</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.73% [<b>44.9%</b>-48.5%]</td>
	<td>3,133</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.54% [<b>45.6%</b>-47.5%]</td>
	<td>11,072</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.48% [<b>45.9%</b>-47.1%]</td>
	<td>28,258</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.20% [<b>46.2%</b>-48.2%]</td>
	<td>9,428</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.71% [44.1%-<b>45.3%</b>]</td>
	<td>30,006</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.48% [45.9%-<b>47.1%</b>]</td>
	<td>28,258</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.54% [45.6%-<b>47.5%</b>]</td>
	<td>11,072</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.38% [46.6%-<b>48.1%</b>]</td>
	<td>17,009</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.45% [46.7%-<b>48.2%</b>]</td>
	<td>19,539</td>
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
	<td>49.63% [49.5%-49.8%]</td>
	<td>539,519</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.91% [<b>43.3%</b>-48.5%]</td>
	<td>1,442</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.93% [<b>44.8%</b>-49.1%]</td>
	<td>2,135</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.79% [<b>44.8%</b>-48.8%]</td>
	<td>2,569</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.49% [<b>45.1%</b>-47.9%]</td>
	<td>5,182</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>48.50% [<b>46.0%</b>-51.0%]</td>
	<td>1,604</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.49% [45.1%-<b>47.9%</b>]</td>
	<td>5,182</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.36% [46.8%-<b>47.9%</b>]</td>
	<td>29,157</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.45% [46.6%-<b>48.3%</b>]</td>
	<td>14,435</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>47.21% [46.0%-<b>48.4%</b>]</td>
	<td>6,958</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.63% [46.8%-<b>48.5%</b>]</td>
	<td>14,009</td>
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
	<td>50.97% [50.7%-51.2%]</td>
	<td>197,058</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>47.01% [<b>43.7%</b>-50.4%]</td>
	<td>887</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.12% [<b>44.7%</b>-49.6%]</td>
	<td>1,649</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>48.33% [<b>44.9%</b>-51.8%]</td>
	<td>836</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.61% [<b>45.0%</b>-52.2%]</td>
	<td>757</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.47% [<b>45.0%</b>-49.9%]</td>
	<td>1,658</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>48.14% [46.8%-<b>49.5%</b>]</td>
	<td>5,444</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>48.20% [46.8%-<b>49.6%</b>]</td>
	<td>5,278</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.12% [44.7%-<b>49.6%</b>]</td>
	<td>1,649</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.47% [45.0%-<b>49.9%</b>]</td>
	<td>1,658</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>49.37% [48.5%-<b>50.3%</b>]</td>
	<td>12,304</td>
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
	<td>51.44% [51.3%-51.6%]</td>
	<td>284,756</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>47.61% [<b>44.1%</b>-51.1%]</td>
	<td>815</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.48% [<b>44.6%</b>-52.4%]</td>
	<td>658</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.76% [<b>44.7%</b>-50.8%]</td>
	<td>1,072</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.05% [<b>45.8%</b>-48.3%]</td>
	<td>6,464</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>48.79% [<b>46.5%</b>-51.0%]</td>
	<td>1,984</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.05% [45.8%-<b>48.3%</b>]</td>
	<td>6,464</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.59% [46.6%-<b>48.6%</b>]</td>
	<td>10,091</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.96% [48.1%-<b>49.9%</b>]</td>
	<td>12,078</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.76% [47.2%-<b>50.4%</b>]</td>
	<td>3,874</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.99% [47.4%-<b>50.6%</b>]</td>
	<td>3,901</td>
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
	<td>50.09% [50.0%-50.2%]</td>
	<td>893,756</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.30% [<b>44.3%</b>-46.3%]</td>
	<td>10,221</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.17% [<b>44.5%</b>-47.8%]</td>
	<td>3,686</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.06% [<b>44.9%</b>-47.2%]</td>
	<td>7,139</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>46.70% [<b>45.3%</b>-48.1%]</td>
	<td>5,090</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.16% [<b>45.4%</b>-46.9%]</td>
	<td>16,498</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.30% [44.3%-<b>46.3%</b>]</td>
	<td>10,221</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.16% [45.4%-<b>46.9%</b>]</td>
	<td>16,498</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.69% [46.2%-<b>47.2%</b>]</td>
	<td>41,525</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.06% [44.9%-<b>47.2%</b>]</td>
	<td>7,139</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.90% [46.2%-<b>47.6%</b>]</td>
	<td>22,200</td>
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
	<td>49.83% [49.7%-50.0%]</td>
	<td>482,578</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.69% [<b>44.1%</b>-49.2%]</td>
	<td>1,542</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.21% [<b>44.2%</b>-46.2%]</td>
	<td>10,127</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.99% [<b>44.7%</b>-49.2%]</td>
	<td>1,958</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.93% [<b>44.7%</b>-47.1%]</td>
	<td>6,983</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.41% [<b>44.8%</b>-48.0%]</td>
	<td>3,730</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.21% [44.2%-<b>46.2%</b>]</td>
	<td>10,127</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.29% [45.6%-<b>47.0%</b>]</td>
	<td>19,270</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.93% [44.7%-<b>47.1%</b>]</td>
	<td>6,983</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.35% [45.4%-<b>47.3%</b>]</td>
	<td>10,208</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>46.72% [45.7%-<b>47.7%</b>]</td>
	<td>10,213</td>
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
	<td>48.91% [48.8%-49.0%]</td>
	<td>691,323</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.82% [<b>44.1%</b>-47.5%]</td>
	<td>3,394</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.42% [<b>44.1%</b>-46.7%]</td>
	<td>5,997</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.07% [<b>44.4%</b>-45.7%]</td>
	<td>25,009</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.94% [<b>44.7%</b>-47.2%]</td>
	<td>5,999</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>46.69% [<b>44.7%</b>-48.7%]</td>
	<td>2,555</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.07% [44.4%-<b>45.7%</b>]</td>
	<td>25,009</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.42% [44.1%-<b>46.7%</b>]</td>
	<td>5,997</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.17% [45.5%-<b>46.8%</b>]</td>
	<td>25,836</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.22% [45.5%-<b>47.0%</b>]</td>
	<td>17,167</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.94% [44.7%-<b>47.2%</b>]</td>
	<td>5,999</td>
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
	<td>50.61% [50.5%-50.8%]</td>
	<td>394,884</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.69% [<b>43.3%</b>-50.0%]</td>
	<td>891</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.53% [<b>44.1%</b>-47.0%]</td>
	<td>4,909</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.27% [<b>44.6%</b>-47.9%]</td>
	<td>3,724</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.21% [<b>44.9%</b>-47.5%]</td>
	<td>5,854</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.94% [<b>45.0%</b>-48.9%]</td>
	<td>2,635</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.53% [44.1%-<b>47.0%</b>]</td>
	<td>4,909</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.07% [45.0%-<b>47.1%</b>]</td>
	<td>8,988</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>46.71% [45.9%-<b>47.5%</b>]</td>
	<td>16,521</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.21% [44.9%-<b>47.5%</b>]</td>
	<td>5,854</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.27% [44.6%-<b>47.9%</b>]</td>
	<td>3,724</td>
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
	<td>49.68% [49.6%-49.8%]</td>
	<td>611,862</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>45.20% [<b>43.1%</b>-47.3%]</td>
	<td>2,321</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.30% [<b>43.8%</b>-48.8%]</td>
	<td>1,596</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>47.12% [<b>45.6%</b>-48.6%]</td>
	<td>4,612</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.34% [<b>45.8%</b>-48.9%]</td>
	<td>4,326</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.82% [<b>45.9%</b>-49.7%]</td>
	<td>2,804</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>45.20% [43.1%-<b>47.3%</b>]</td>
	<td>2,321</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.90% [46.2%-<b>47.6%</b>]</td>
	<td>18,051</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.95% [46.2%-<b>47.7%</b>]</td>
	<td>19,329</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.93% [45.9%-<b>47.9%</b>]</td>
	<td>10,235</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>47.33% [46.5%-<b>48.2%</b>]</td>
	<td>13,613</td>
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
	<td>50.47% [50.3%-50.6%]</td>
	<td>308,883</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.39% [<b>43.2%</b>-47.6%]</td>
	<td>2,018</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>47.21% [<b>43.7%</b>-50.7%]</td>
	<td>824</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.84% [<b>43.8%</b>-45.8%]</td>
	<td>10,055</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>45.83% [<b>44.2%</b>-47.5%]</td>
	<td>3,559</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>45.76% [<b>44.7%</b>-46.8%]</td>
	<td>8,671</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>44.84% [43.8%-<b>45.8%</b>]</td>
	<td>10,055</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>45.76% [44.7%-<b>46.8%</b>]</td>
	<td>8,671</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>45.87% [44.8%-<b>46.9%</b>]</td>
	<td>9,280</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>46.12% [45.2%-<b>47.1%</b>]</td>
	<td>11,192</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>45.83% [44.2%-<b>47.5%</b>]</td>
	<td>3,559</td>
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
	<td>49.11% [49.0%-49.3%]</td>
	<td>408,247</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.46% [<b>43.2%</b>-45.7%]</td>
	<td>6,059</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.62% [<b>43.4%</b>-47.8%]</td>
	<td>2,091</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.13% [<b>43.5%</b>-46.7%]</td>
	<td>3,898</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>44.83% [<b>44.1%</b>-45.6%]</td>
	<td>16,684</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>46.62% [<b>44.2%</b>-49.0%]</td>
	<td>1,759</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>44.83% [44.1%-<b>45.6%</b>]</td>
	<td>16,684</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.46% [43.2%-<b>45.7%</b>]</td>
	<td>6,059</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.13% [43.5%-<b>46.7%</b>]</td>
	<td>3,898</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.81% [44.7%-<b>46.9%</b>]</td>
	<td>8,010</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.48% [45.6%-<b>47.4%</b>]</td>
	<td>12,955</td>
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
	<td>48.60% [48.5%-48.7%]</td>
	<td>988,112</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.18% [<b>40.3%</b>-42.1%]</td>
	<td>11,288</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.79% [<b>43.4%</b>-46.2%]</td>
	<td>5,298</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.51% [<b>43.8%</b>-45.3%]</td>
	<td>17,629</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.91% [<b>44.0%</b>-45.8%]</td>
	<td>12,132</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.32% [<b>44.4%</b>-48.3%]</td>
	<td>2,636</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.18% [40.3%-<b>42.1%</b>]</td>
	<td>11,288</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.51% [43.8%-<b>45.3%</b>]</td>
	<td>17,629</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.91% [44.0%-<b>45.8%</b>]</td>
	<td>12,132</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>45.43% [44.9%-<b>46.0%</b>]</td>
	<td>33,953</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.34% [44.7%-<b>46.0%</b>]</td>
	<td>24,578</td>
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
	<td>48.79% [48.6%-49.0%]</td>
	<td>323,670</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.44% [<b>43.1%</b>-49.7%]</td>
	<td>913</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>45.87% [<b>43.2%</b>-48.5%]</td>
	<td>1,439</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.35% [<b>43.5%</b>-47.2%]</td>
	<td>2,831</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.93% [<b>43.5%</b>-46.3%]</td>
	<td>5,001</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.22% [<b>43.6%</b>-46.8%]</td>
	<td>3,788</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.93% [43.5%-<b>46.3%</b>]</td>
	<td>5,001</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.59% [44.7%-<b>46.5%</b>]</td>
	<td>11,475</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.22% [43.6%-<b>46.8%</b>]</td>
	<td>3,788</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.91% [44.7%-<b>47.1%</b>]</td>
	<td>6,835</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>46.33% [45.5%-<b>47.1%</b>]</td>
	<td>14,841</td>
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
	<td>49.45% [49.3%-49.6%]</td>
	<td>273,628</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>45.68% [<b>41.8%</b>-49.6%]</td>
	<td>659</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.22% [<b>43.2%</b>-49.2%]</td>
	<td>1,099</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.52% [<b>44.2%</b>-48.8%]</td>
	<td>1,928</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.40% [<b>44.3%</b>-46.5%]</td>
	<td>7,558</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>45.72% [<b>44.6%</b>-46.8%]</td>
	<td>7,918</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.40% [44.3%-<b>46.5%</b>]</td>
	<td>7,558</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>45.72% [44.6%-<b>46.8%</b>]</td>
	<td>7,918</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.51% [45.3%-<b>47.7%</b>]</td>
	<td>6,850</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>46.56% [44.8%-<b>48.4%</b>]</td>
	<td>3,041</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.90% [45.3%-<b>48.5%</b>]</td>
	<td>4,036</td>
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
	<td>51.98% [51.7%-52.2%]</td>
	<td>147,015</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>46.35% [<b>41.9%</b>-50.8%]</td>
	<td>507</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.17% [<b>43.1%</b>-49.2%]</td>
	<td>1,083</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.22% [<b>44.7%</b>-51.8%]</td>
	<td>788</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>49.38% [<b>45.8%</b>-52.9%]</td>
	<td>802</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>50.41% [<b>45.9%</b>-54.9%]</td>
	<td>488</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.37% [46.2%-<b>48.6%</b>]</td>
	<td>6,719</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.45% [46.1%-<b>48.8%</b>]</td>
	<td>5,163</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>46.17% [43.1%-<b>49.2%</b>]</td>
	<td>1,083</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>48.78% [47.2%-<b>50.3%</b>]</td>
	<td>4,063</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>48.60% [46.8%-<b>50.4%</b>]</td>
	<td>2,971</td>
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
	<td>51.19% [50.8%-51.6%]</td>
	<td>75,401</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.07% [<b>42.9%</b>-49.3%]</td>
	<td>968</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.96% [<b>43.0%</b>-51.0%]</td>
	<td>624</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>47.89% [<b>43.8%</b>-52.0%]</td>
	<td>593</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>50.95% [<b>44.1%</b>-57.8%]</td>
	<td>210</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>49.35% [<b>44.3%</b>-54.4%]</td>
	<td>387</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>46.07% [42.9%-<b>49.3%</b>]</td>
	<td>968</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.84% [46.1%-<b>49.6%</b>]</td>
	<td>3,363</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-karma"></span> Karma</td>
	<td>48.40% [46.0%-<b>50.8%</b>]</td>
	<td>1,808</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>48.74% [46.6%-<b>50.9%</b>]</td>
	<td>2,140</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.96% [43.0%-<b>51.0%</b>]</td>
	<td>624</td>
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
	<td>51.64% [51.3%-52.0%]</td>
	<td>92,054</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>45.19% [<b>42.3%</b>-48.1%]</td>
	<td>1,206</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.70% [<b>42.6%</b>-54.8%]</td>
	<td>269</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.73% [<b>43.8%</b>-47.7%]</td>
	<td>2,648</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>49.52% [<b>43.8%</b>-55.2%]</td>
	<td>311</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>50.19% [<b>44.0%</b>-56.4%]</td>
	<td>257</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.73% [43.8%-<b>47.7%</b>]</td>
	<td>2,648</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>45.19% [42.3%-<b>48.1%</b>]</td>
	<td>1,206</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.05% [46.5%-<b>49.6%</b>]</td>
	<td>4,179</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>47.45% [45.0%-<b>49.9%</b>]</td>
	<td>1,667</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.00% [46.0%-<b>50.0%</b>]</td>
	<td>2,525</td>
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
	<td>49.79% [49.5%-50.1%]</td>
	<td>121,846</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>45.81% [<b>41.4%</b>-50.2%]</td>
	<td>513</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.25% [<b>42.1%</b>-50.4%]</td>
	<td>586</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.66% [<b>42.4%</b>-49.0%]</td>
	<td>911</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>48.08% [<b>42.8%</b>-53.3%]</td>
	<td>364</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>47.98% [<b>43.1%</b>-52.8%]</td>
	<td>421</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>47.22% [45.8%-<b>48.7%</b>]</td>
	<td>4,754</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>45.66% [42.4%-<b>49.0%</b>]</td>
	<td>911</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.50% [46.0%-<b>49.0%</b>]</td>
	<td>4,364</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.42% [45.7%-<b>49.2%</b>]</td>
	<td>3,279</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-karma"></span> Karma</td>
	<td>47.80% [46.1%-<b>49.5%</b>]</td>
	<td>3,651</td>
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
	<td>48.62% [48.5%-48.7%]</td>
	<td>645,332</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.82% [<b>40.4%</b>-43.2%]</td>
	<td>5,120</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>43.34% [<b>41.9%</b>-44.7%]</td>
	<td>5,058</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.72% [<b>43.0%</b>-46.4%]</td>
	<td>3,426</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>45.90% [<b>43.5%</b>-48.3%]</td>
	<td>1,695</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>45.74% [<b>43.5%</b>-48.0%]</td>
	<td>1,970</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.82% [40.4%-<b>43.2%</b>]</td>
	<td>5,120</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>43.34% [41.9%-<b>44.7%</b>]</td>
	<td>5,058</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>44.67% [43.7%-<b>45.7%</b>]</td>
	<td>9,985</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.47% [44.7%-<b>46.3%</b>]</td>
	<td>15,680</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.72% [43.0%-<b>46.4%</b>]</td>
	<td>3,426</td>
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
	<td>49.27% [49.0%-49.5%]</td>
	<td>172,265</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.96% [<b>41.3%</b>-46.6%]</td>
	<td>1,374</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.22% [<b>41.9%</b>-50.5%]</td>
	<td>543</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>45.68% [<b>42.7%</b>-48.7%]</td>
	<td>1,088</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.14% [<b>42.9%</b>-47.4%]</td>
	<td>1,923</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>47.28% [<b>43.6%</b>-51.0%]</td>
	<td>734</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.96% [41.3%-<b>46.6%</b>]</td>
	<td>1,374</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>45.79% [44.6%-<b>47.0%</b>]</td>
	<td>7,093</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.14% [42.9%-<b>47.4%</b>]</td>
	<td>1,923</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>45.92% [43.8%-<b>48.0%</b>]</td>
	<td>2,280</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>47.13% [45.9%-<b>48.3%</b>]</td>
	<td>7,087</td>
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
	<td>48.78% [48.6%-49.0%]</td>
	<td>252,227</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>44.10% [<b>40.2%</b>-48.0%]</td>
	<td>644</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.63% [<b>41.5%</b>-45.8%]</td>
	<td>2,173</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.09% [<b>43.3%</b>-46.9%]</td>
	<td>3,034</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shaco"></span> Shaco</td>
	<td>46.36% [<b>44.1%</b>-48.6%]</td>
	<td>2,019</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.21% [<b>44.3%</b>-52.2%]</td>
	<td>643</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>43.63% [41.5%-<b>45.8%</b>]</td>
	<td>2,173</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>45.58% [44.4%-<b>46.7%</b>]</td>
	<td>7,541</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>45.09% [43.3%-<b>46.9%</b>]</td>
	<td>3,034</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>45.82% [44.7%-<b>47.0%</b>]</td>
	<td>7,728</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>46.76% [45.6%-<b>47.9%</b>]</td>
	<td>7,083</td>
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
	<td>50.65% [50.3%-51.0%]</td>
	<td>93,746</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>46.69% [<b>40.6%</b>-52.7%]</td>
	<td>272</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.22% [<b>41.4%</b>-49.1%]</td>
	<td>670</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>48.47% [<b>42.3%</b>-54.6%]</td>
	<td>262</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>47.33% [<b>42.5%</b>-52.1%]</td>
	<td>431</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>49.78% [<b>43.2%</b>-56.4%]</td>
	<td>231</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>47.01% [45.5%-<b>48.5%</b>]</td>
	<td>4,484</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>45.22% [41.4%-<b>49.1%</b>]</td>
	<td>670</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.15% [45.2%-<b>49.1%</b>]</td>
	<td>2,530</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>46.81% [44.1%-<b>49.5%</b>]</td>
	<td>1,380</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>48.83% [47.3%-<b>50.4%</b>]</td>
	<td>4,229</td>
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
	<td>52.07% [51.7%-52.4%]</td>
	<td>80,416</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.06% [<b>39.4%</b>-48.7%]</td>
	<td>463</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.84% [<b>41.2%</b>-48.5%]</td>
	<td>756</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.66% [<b>42.4%</b>-49.0%]</td>
	<td>911</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>48.40% [<b>43.2%</b>-53.6%]</td>
	<td>376</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.07% [<b>43.5%</b>-54.6%]</td>
	<td>322</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.02% [44.1%-<b>48.0%</b>]</td>
	<td>2,564</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>44.84% [41.2%-<b>48.5%</b>]</td>
	<td>756</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.06% [39.4%-<b>48.7%</b>]</td>
	<td>463</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>45.66% [42.4%-<b>49.0%</b>]</td>
	<td>911</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>49.18% [47.7%-<b>50.7%</b>]</td>
	<td>4,451</td>
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
	<td>47.05% [46.9%-47.2%]</td>
	<td>470,129</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>42.87% [<b>41.1%</b>-44.6%]</td>
	<td>3,175</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>43.48% [<b>41.2%</b>-45.8%]</td>
	<td>1,856</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>43.26% [<b>42.1%</b>-44.4%]</td>
	<td>7,437</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.89% [<b>42.5%</b>-45.3%]</td>
	<td>4,751</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>43.81% [<b>42.9%</b>-44.7%]</td>
	<td>13,105</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>43.26% [42.1%-<b>44.4%</b>]</td>
	<td>7,437</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>42.87% [41.1%-<b>44.6%</b>]</td>
	<td>3,175</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>43.81% [42.9%-<b>44.7%</b>]</td>
	<td>13,105</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leona"></span> Leona</td>
	<td>44.53% [43.9%-<b>45.2%</b>]</td>
	<td>22,515</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>43.89% [42.5%-<b>45.3%</b>]</td>
	<td>4,751</td>
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
	<td>49.46% [49.0%-49.9%]</td>
	<td>58,268</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>40.85% [<b>35.9%</b>-45.8%]</td>
	<td>399</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>46.95% [<b>41.0%</b>-52.9%]</td>
	<td>279</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>44.11% [<b>41.9%</b>-46.3%]</td>
	<td>2,095</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>49.05% [<b>42.2%</b>-55.9%]</td>
	<td>210</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>45.38% [<b>42.2%</b>-48.5%]</td>
	<td>996</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>40.85% [35.9%-<b>45.8%</b>]</td>
	<td>399</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>44.11% [41.9%-<b>46.3%</b>]</td>
	<td>2,095</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>46.10% [44.4%-<b>47.8%</b>]</td>
	<td>3,371</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>46.12% [43.9%-<b>48.3%</b>]</td>
	<td>2,062</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>45.49% [42.6%-<b>48.3%</b>]</td>
	<td>1,220</td>
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
	<td>51.51% [51.1%-52.0%]</td>
	<td>51,433</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.44% [<b>37.9%</b>-50.9%]</td>
	<td>234</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>47.98% [<b>40.4%</b>-55.6%]</td>
	<td>173</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>48.65% [<b>40.4%</b>-56.9%]</td>
	<td>148</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>46.62% [<b>42.5%</b>-50.8%]</td>
	<td>577</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>48.18% [<b>43.1%</b>-53.3%]</td>
	<td>384</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>47.66% [44.8%-<b>50.5%</b>]</td>
	<td>1,198</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>48.12% [45.6%-<b>50.6%</b>]</td>
	<td>1,573</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>47.20% [43.7%-<b>50.7%</b>]</td>
	<td>805</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zilean"></span> Zilean</td>
	<td>46.62% [42.5%-<b>50.8%</b>]</td>
	<td>577</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>44.44% [37.9%-<b>50.9%</b>]</td>
	<td>234</td>
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
	<td>50.49% [50.1%-50.9%]</td>
	<td>54,010</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>42.86% [<b>37.7%</b>-48.0%]</td>
	<td>371</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>43.45% [<b>40.2%</b>-46.7%]</td>
	<td>909</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>48.72% [<b>40.7%</b>-56.7%]</td>
	<td>156</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>50.00% [<b>41.4%</b>-58.6%]</td>
	<td>134</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>48.58% [<b>41.7%</b>-55.4%]</td>
	<td>212</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>43.45% [40.2%-<b>46.7%</b>]</td>
	<td>909</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>42.86% [37.7%-<b>48.0%</b>]</td>
	<td>371</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>46.85% [44.7%-<b>49.0%</b>]</td>
	<td>2,096</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.62% [42.0%-<b>49.2%</b>]</td>
	<td>754</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-morgana"></span> Morgana</td>
	<td>46.87% [44.3%-<b>49.4%</b>]</td>
	<td>1,502</td>
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
	<td>48.71% [48.4%-49.0%]</td>
	<td>112,517</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>40.07% [<b>34.2%</b>-46.0%]</td>
	<td>277</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>44.02% [<b>39.7%</b>-48.4%]</td>
	<td>518</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-ziggs"></span> Ziggs</td>
	<td>46.51% [<b>39.7%</b>-53.3%]</td>
	<td>215</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>45.80% [<b>40.8%</b>-50.8%]</td>
	<td>393</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.34% [<b>41.4%</b>-47.3%]</td>
	<td>1,130</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>40.07% [34.2%-<b>46.0%</b>]</td>
	<td>277</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>44.20% [42.2%-<b>46.2%</b>]</td>
	<td>2,353</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>44.34% [41.4%-<b>47.3%</b>]</td>
	<td>1,130</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vel-koz"></span> Vel'Koz</td>
	<td>44.91% [42.4%-<b>47.4%</b>]</td>
	<td>1,543</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>45.61% [43.6%-<b>47.6%</b>]</td>
	<td>2,438</td>
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
	<td>50.25% [49.8%-50.7%]</td>
	<td>55,695</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.51% [<b>34.9%</b>-50.2%]</td>
	<td>167</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>45.70% [<b>39.0%</b>-52.4%]</td>
	<td>221</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>44.04% [<b>39.3%</b>-48.7%]</td>
	<td>445</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>45.55% [<b>39.7%</b>-51.4%]</td>
	<td>292</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>46.01% [<b>40.4%</b>-51.6%]</td>
	<td>313</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-maokai"></span> Maokai</td>
	<td>44.04% [39.3%-<b>48.7%</b>]</td>
	<td>445</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-braum"></span> Braum</td>
	<td>46.08% [43.0%-<b>49.1%</b>]</td>
	<td>1,059</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-soraka"></span> Soraka</td>
	<td>46.88% [43.9%-<b>49.9%</b>]</td>
	<td>1,107</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.51% [34.9%-<b>50.2%</b>]</td>
	<td>167</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>46.61% [43.0%-<b>50.2%</b>]</td>
	<td>753</td>
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
	<td>46.97% [46.7%-47.3%]</td>
	<td>117,306</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>42.46% [<b>36.2%</b>-48.7%]</td>
	<td>252</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>41.57% [<b>37.2%</b>-45.9%]</td>
	<td>510</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>41.85% [<b>38.2%</b>-45.5%]</td>
	<td>724</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>40.99% [<b>38.4%</b>-43.6%]</td>
	<td>1,454</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>45.67% [<b>39.8%</b>-51.5%]</td>
	<td>289</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>40.99% [38.4%-<b>43.6%</b>]</td>
	<td>1,454</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>43.17% [41.4%-<b>44.9%</b>]</td>
	<td>3,194</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>42.93% [40.9%-<b>45.0%</b>]</td>
	<td>2,285</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>41.85% [38.2%-<b>45.5%</b>]</td>
	<td>724</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>44.16% [42.6%-<b>45.8%</b>]</td>
	<td>3,893</td>
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
	<td>47.52% [47.2%-47.8%]</td>
	<td>100,886</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>39.33% [<b>33.7%</b>-45.0%]</td>
	<td>300</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>40.63% [<b>34.8%</b>-46.4%]</td>
	<td>288</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>42.21% [<b>37.7%</b>-46.7%]</td>
	<td>488</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>42.89% [<b>38.2%</b>-47.6%]</td>
	<td>443</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>42.27% [<b>39.4%</b>-45.2%]</td>
	<td>1,152</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>42.82% [41.1%-<b>44.5%</b>]</td>
	<td>3,456</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>42.88% [41.1%-<b>44.7%</b>]</td>
	<td>2,983</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>39.33% [33.7%-<b>45.0%</b>]</td>
	<td>300</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>43.16% [41.3%-<b>45.1%</b>]</td>
	<td>2,720</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>42.27% [39.4%-<b>45.2%</b>]</td>
	<td>1,152</td>
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
	<td>47.61% [47.2%-48.0%]</td>
	<td>53,569</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>39.45% [<b>33.3%</b>-45.6%]</td>
	<td>256</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>41.50% [<b>33.4%</b>-49.6%]</td>
	<td>147</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.20% [<b>35.5%</b>-46.9%]</td>
	<td>301</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>43.48% [<b>35.7%</b>-51.3%]</td>
	<td>161</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>43.90% [<b>36.1%</b>-51.7%]</td>
	<td>164</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>42.96% [40.9%-<b>45.0%</b>]</td>
	<td>2,260</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>39.45% [33.3%-<b>45.6%</b>]</td>
	<td>256</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>43.28% [40.8%-<b>45.8%</b>]</td>
	<td>1,585</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>43.51% [40.5%-<b>46.5%</b>]</td>
	<td>1,101</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>41.20% [35.5%-<b>46.9%</b>]</td>
	<td>301</td>
</tr>
</table>

</details>
