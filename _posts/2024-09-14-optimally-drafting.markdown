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

### Jungle

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

### Mid

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

### ADC

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

### Support

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
