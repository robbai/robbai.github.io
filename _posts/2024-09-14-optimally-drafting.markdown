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

The confidence bounds will be 2 standard deviations above and below the win-rate, where the upper win-rate will be used for the perspective of the opponent, and the lower win-rate will be used for our perspective.

By using confidence bounds when calculating the safety of a champion, we effectively penalise choosing champions who have a low pick-rate, as well as penalise champions would potentially have a bad matchup against a low pick-rate champion. On the other hand, for the opponent, these effects are reversed.

In essence, we assume the opponent has the better side of the odds, in order to maximise the safety of our pick against the influence of differing pick-rates between the different champions.

An important note is that the data source, [op.gg](https://www.op.gg/) uses a minimum pick-rate threshold of 0.5% per role, preventing extreme outliers from affecting the results of this project.

## Results

**Last update:** Patch 14.18

### Top

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
	<td>52.09% [52.0%-52.2%]</td>
	<td>692,041</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.04% [<b>46.9%</b>-49.2%]</td>
	<td>8,099</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>48.39% [<b>47.7%</b>-49.0%]</td>
	<td>23,270</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>50.08% [<b>48.1%</b>-52.0%]</td>
	<td>2,610</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>49.46% [<b>48.7%</b>-50.2%]</td>
	<td>16,376</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>49.37% [<b>48.7%</b>-50.0%]</td>
	<td>25,292</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-illaoi"></span> Illaoi</td>
	<td>48.39% [47.7%-<b>49.0%</b>]</td>
	<td>23,270</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.04% [46.9%-<b>49.2%</b>]</td>
	<td>8,099</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>49.37% [48.7%-<b>50.0%</b>]</td>
	<td>25,292</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-malphite"></span> Malphite</td>
	<td>49.46% [48.7%-<b>50.2%</b>]</td>
	<td>16,376</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-ornn"></span> Ornn</td>
	<td>49.96% [49.0%-<b>50.9%</b>]</td>
	<td>11,972</td>
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
	<td>52.14% [52.0%-52.2%]</td>
	<td>1,034,458</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>47.47% [<b>46.9%</b>-48.0%]</td>
	<td>33,773</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.04% [<b>47.4%</b>-48.7%]</td>
	<td>21,509</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>48.47% [<b>47.7%</b>-49.2%]</td>
	<td>17,695</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>48.48% [<b>48.1%</b>-48.9%]</td>
	<td>54,628</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.75% [<b>48.1%</b>-49.4%]</td>
	<td>22,100</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-camille"></span> Camille</td>
	<td>47.47% [46.9%-<b>48.0%</b>]</td>
	<td>33,773</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>48.04% [47.4%-<b>48.7%</b>]</td>
	<td>21,509</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>48.48% [48.1%-<b>48.9%</b>]</td>
	<td>54,628</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kayle"></span> Kayle</td>
	<td>48.47% [47.7%-<b>49.2%</b>]</td>
	<td>17,695</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.75% [48.1%-<b>49.4%</b>]</td>
	<td>22,100</td>
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
	<td>52.71% [52.6%-52.9%]</td>
	<td>475,750</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.10% [<b>45.8%</b>-50.4%]</td>
	<td>1,921</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>48.21% [<b>47.3%</b>-49.1%]</td>
	<td>11,776</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>48.76% [<b>48.1%</b>-49.4%]</td>
	<td>23,521</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.37% [<b>48.3%</b>-50.5%]</td>
	<td>8,464</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>49.32% [<b>48.3%</b>-50.3%]</td>
	<td>9,799</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-tryndamere"></span> Tryndamere</td>
	<td>48.21% [47.3%-<b>49.1%</b>]</td>
	<td>11,776</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>48.76% [48.1%-<b>49.4%</b>]</td>
	<td>23,521</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-urgot"></span> Urgot</td>
	<td>49.32% [48.3%-<b>50.3%</b>]</td>
	<td>9,799</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>48.10% [45.8%-<b>50.4%</b>]</td>
	<td>1,921</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>49.37% [48.3%-<b>50.5%</b>]</td>
	<td>8,464</td>
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
	<td>51.71% [51.6%-51.8%]</td>
	<td>735,688</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>48.25% [<b>46.7%</b>-49.8%]</td>
	<td>4,367</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.29% [<b>47.1%</b>-49.5%]</td>
	<td>7,051</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.31% [<b>47.2%</b>-49.4%]</td>
	<td>8,188</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-fiora"></span> Fiora</td>
	<td>48.59% [<b>47.8%</b>-49.4%]</td>
	<td>17,270</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>49.29% [<b>47.9%</b>-50.7%]</td>
	<td>5,182</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-fiora"></span> Fiora</td>
	<td>48.59% [47.8%-<b>49.4%</b>]</td>
	<td>17,270</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>48.31% [47.2%-<b>49.4%</b>]</td>
	<td>8,188</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>48.29% [47.1%-<b>49.5%</b>]</td>
	<td>7,051</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-singed"></span> Singed</td>
	<td>48.25% [46.7%-<b>49.8%</b>]</td>
	<td>4,367</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>49.42% [48.9%-<b>49.9%</b>]</td>
	<td>38,002</td>
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
	<td>50.35% [50.1%-50.6%]</td>
	<td>246,364</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>47.92% [<b>44.8%</b>-51.0%]</td>
	<td>1,035</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-trundle"></span> Trundle</td>
	<td>47.54% [<b>45.9%</b>-49.2%]</td>
	<td>3,536</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>46.80% [<b>45.9%</b>-47.7%]</td>
	<td>11,714</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>47.50% [<b>46.0%</b>-49.0%]</td>
	<td>4,162</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>47.67% [<b>46.0%</b>-49.3%]</td>
	<td>3,669</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sett"></span> Sett</td>
	<td>46.80% [45.9%-<b>47.7%</b>]</td>
	<td>11,714</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>47.06% [46.1%-<b>48.0%</b>]</td>
	<td>11,213</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>47.34% [46.1%-<b>48.6%</b>]</td>
	<td>6,438</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aatrox"></span> Aatrox</td>
	<td>47.60% [46.6%-<b>48.6%</b>]</td>
	<td>10,234</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>48.08% [47.3%-<b>48.9%</b>]</td>
	<td>15,798</td>
</tr>
</table>

### Jungle

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
	<td>53.52% [53.4%-53.6%]</td>
	<td>975,162</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.52% [<b>45.2%</b>-47.9%]</td>
	<td>5,537</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-taliyah"></span> Taliyah</td>
	<td>51.42% [<b>50.0%</b>-52.9%]</td>
	<td>4,718</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>50.93% [<b>50.2%</b>-51.6%]</td>
	<td>21,392</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>50.81% [<b>50.3%</b>-51.3%]</td>
	<td>39,307</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>51.03% [<b>50.6%</b>-51.5%]</td>
	<td>50,654</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.52% [45.2%-<b>47.9%</b>]</td>
	<td>5,537</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>50.81% [50.3%-<b>51.3%</b>]</td>
	<td>39,307</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>51.03% [50.6%-<b>51.5%</b>]</td>
	<td>50,654</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>50.93% [50.2%-<b>51.6%</b>]</td>
	<td>21,392</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kayn"></span> Kayn</td>
	<td>51.55% [51.1%-<b>52.0%</b>]</td>
	<td>46,818</td>
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
	<td>52.17% [52.0%-52.3%]</td>
	<td>457,381</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.40% [<b>46.8%</b>-48.0%]</td>
	<td>28,292</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>50.74% [<b>48.0%</b>-53.5%]</td>
	<td>1,350</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>49.82% [<b>48.5%</b>-51.1%]</td>
	<td>5,964</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.29% [<b>48.6%</b>-50.0%]</td>
	<td>22,911</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>50.45% [<b>48.7%</b>-52.2%]</td>
	<td>3,209</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.40% [46.8%-<b>48.0%</b>]</td>
	<td>28,292</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nocturne"></span> Nocturne</td>
	<td>49.29% [48.6%-<b>50.0%</b>]</td>
	<td>22,911</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-volibear"></span> Volibear</td>
	<td>49.88% [49.0%-<b>50.8%</b>]</td>
	<td>11,593</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jax"></span> Jax</td>
	<td>49.82% [48.5%-<b>51.1%</b>]</td>
	<td>5,964</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-warwick"></span> Warwick</td>
	<td>50.62% [49.9%-<b>51.3%</b>]</td>
	<td>19,234</td>
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
	<td>52.43% [52.3%-52.5%]</td>
	<td>785,583</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>49.38% [<b>47.6%</b>-51.2%]</td>
	<td>3,086</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.78% [<b>48.0%</b>-49.6%]</td>
	<td>16,313</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.97% [<b>48.5%</b>-49.4%]</td>
	<td>50,654</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>49.53% [<b>48.9%</b>-50.1%]</td>
	<td>28,839</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>50.38% [<b>49.0%</b>-51.8%]</td>
	<td>5,073</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>48.97% [48.5%-<b>49.4%</b>]</td>
	<td>50,654</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.78% [48.0%-<b>49.6%</b>]</td>
	<td>16,313</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lillia"></span> Lillia</td>
	<td>49.53% [48.9%-<b>50.1%</b>]</td>
	<td>28,839</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-udyr"></span> Udyr</td>
	<td>50.04% [49.3%-<b>50.8%</b>]</td>
	<td>17,927</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>50.40% [49.8%-<b>51.0%</b>]</td>
	<td>30,165</td>
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
	<td>51.13% [51.0%-51.3%]</td>
	<td>634,977</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.62% [<b>46.9%</b>-48.4%]</td>
	<td>17,214</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.00% [<b>47.4%</b>-50.6%]</td>
	<td>3,969</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>48.14% [<b>47.4%</b>-48.9%]</td>
	<td>19,377</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>49.46% [<b>47.8%</b>-51.1%]</td>
	<td>3,530</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-fiddlesticks"></span> Fiddlesticks</td>
	<td>49.09% [<b>48.0%</b>-50.2%]</td>
	<td>8,362</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.62% [46.9%-<b>48.4%</b>]</td>
	<td>17,214</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>48.14% [47.4%-<b>48.9%</b>]</td>
	<td>19,377</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kha-zix"></span> Kha'Zix</td>
	<td>48.85% [48.3%-<b>49.4%</b>]</td>
	<td>31,051</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-jarvan-iv"></span> Jarvan IV</td>
	<td>48.83% [48.2%-<b>49.5%</b>]</td>
	<td>23,860</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>49.19% [48.7%-<b>49.7%</b>]</td>
	<td>39,307</td>
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
	<td>51.15% [51.0%-51.3%]</td>
	<td>667,305</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.73% [<b>44.6%</b>-48.9%]</td>
	<td>2,215</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.39% [<b>47.1%</b>-49.7%]</td>
	<td>5,708</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.98% [<b>47.2%</b>-48.7%]</td>
	<td>16,921</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.96% [<b>47.5%</b>-48.5%]</td>
	<td>38,886</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.70% [<b>47.8%</b>-49.6%]</td>
	<td>12,699</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-amumu"></span> Amumu</td>
	<td>47.96% [47.5%-<b>48.5%</b>]</td>
	<td>38,886</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-briar"></span> Briar</td>
	<td>47.98% [47.2%-<b>48.7%</b>]</td>
	<td>16,921</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-mordekaiser"></span> Mordekaiser</td>
	<td>46.73% [44.6%-<b>48.9%</b>]</td>
	<td>2,215</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shyvana"></span> Shyvana</td>
	<td>48.70% [47.8%-<b>49.6%</b>]</td>
	<td>12,699</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-gwen"></span> Gwen</td>
	<td>48.39% [47.1%-<b>49.7%</b>]</td>
	<td>5,708</td>
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
	<td>52.05% [51.9%-52.2%]</td>
	<td>529,136</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.37% [<b>44.9%</b>-47.8%]</td>
	<td>4,744</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>49.24% [<b>46.4%</b>-52.1%]</td>
	<td>1,249</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>49.38% [<b>46.8%</b>-52.0%]</td>
	<td>1,452</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.71% [<b>46.8%</b>-48.6%]</td>
	<td>12,879</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>50.54% [<b>46.8%</b>-54.2%]</td>
	<td>734</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.37% [44.9%-<b>47.8%</b>]</td>
	<td>4,744</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>47.71% [46.8%-<b>48.6%</b>]</td>
	<td>12,879</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-katarina"></span> Katarina</td>
	<td>48.74% [48.1%-<b>49.4%</b>]</td>
	<td>21,586</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>48.73% [47.7%-<b>49.7%</b>]</td>
	<td>9,786</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>49.57% [48.8%-<b>50.4%</b>]</td>
	<td>15,825</td>
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
	<td>55.48% [55.2%-55.7%]</td>
	<td>173,875</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>50.08% [<b>46.1%</b>-54.1%]</td>
	<td>633</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>50.24% [<b>46.2%</b>-54.2%]</td>
	<td>623</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>50.11% [<b>47.4%</b>-52.8%]</td>
	<td>1,377</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>50.23% [<b>47.4%</b>-53.0%]</td>
	<td>1,292</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>51.24% [<b>47.6%</b>-54.8%]</td>
	<td>767</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-lissandra"></span> Lissandra</td>
	<td>50.41% [48.3%-<b>52.5%</b>]</td>
	<td>2,315</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-anivia"></span> Anivia</td>
	<td>50.11% [47.4%-<b>52.8%</b>]</td>
	<td>1,377</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>50.23% [47.4%-<b>53.0%</b>]</td>
	<td>1,292</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>51.89% [50.2%-<b>53.6%</b>]</td>
	<td>3,621</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-cho-gath"></span> Cho'Gath</td>
	<td>50.08% [46.1%-<b>54.1%</b>]</td>
	<td>633</td>
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
	<td>50.34% [50.2%-50.5%]</td>
	<td>722,694</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.71% [<b>45.4%</b>-48.0%]</td>
	<td>5,590</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>48.33% [<b>46.1%</b>-50.6%]</td>
	<td>2,005</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>47.98% [<b>46.1%</b>-49.8%]</td>
	<td>2,947</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.76% [<b>46.2%</b>-47.4%]</td>
	<td>28,287</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-renekton"></span> Renekton</td>
	<td>49.22% [<b>46.2%</b>-52.3%]</td>
	<td>1,083</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.76% [46.2%-<b>47.4%</b>]</td>
	<td>28,287</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>46.71% [45.4%-<b>48.0%</b>]</td>
	<td>5,590</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.51% [46.5%-<b>48.6%</b>]</td>
	<td>8,970</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-vex"></span> Vex</td>
	<td>48.35% [47.7%-<b>49.0%</b>]</td>
	<td>22,671</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-annie"></span> Annie</td>
	<td>47.91% [46.8%-<b>49.1%</b>]</td>
	<td>7,562</td>
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
	<td>51.55% [51.4%-51.7%]</td>
	<td>455,092</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.23% [<b>45.6%</b>-48.9%]</td>
	<td>3,644</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.11% [<b>45.9%</b>-48.4%]</td>
	<td>6,341</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>48.97% [<b>46.1%</b>-51.8%]</td>
	<td>1,215</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kennen"></span> Kennen</td>
	<td>49.12% [<b>46.2%</b>-52.0%]</td>
	<td>1,193</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.80% [<b>46.6%</b>-49.0%]</td>
	<td>7,348</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>47.11% [45.9%-<b>48.4%</b>]</td>
	<td>6,341</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-garen"></span> Garen</td>
	<td>47.23% [45.6%-<b>48.9%</b>]</td>
	<td>3,644</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.80% [46.6%-<b>49.0%</b>]</td>
	<td>7,348</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-diana"></span> Diana</td>
	<td>48.84% [47.8%-<b>49.9%</b>]</td>
	<td>8,544</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.09% [48.2%-<b>50.0%</b>]</td>
	<td>11,624</td>
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
	<td>50.08% [49.9%-50.2%]</td>
	<td>447,328</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-heimerdinger"></span> Heimerdinger</td>
	<td>47.10% [<b>44.7%</b>-49.5%]</td>
	<td>1,707</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.41% [<b>45.1%</b>-47.7%]</td>
	<td>6,072</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.52% [<b>45.6%</b>-47.4%]</td>
	<td>12,627</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-quinn"></span> Quinn</td>
	<td>48.56% [<b>45.7%</b>-51.4%]</td>
	<td>1,215</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.00% [<b>45.8%</b>-48.2%]</td>
	<td>7,300</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>46.52% [45.6%-<b>47.4%</b>]</td>
	<td>12,627</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-naafiri"></span> Naafiri</td>
	<td>46.41% [45.1%-<b>47.7%</b>]</td>
	<td>6,072</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-fizz"></span> Fizz</td>
	<td>46.84% [45.8%-<b>47.8%</b>]</td>
	<td>10,073</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-aurelion-sol"></span> Aurelion Sol</td>
	<td>47.00% [45.8%-<b>48.2%</b>]</td>
	<td>7,300</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-syndra"></span> Syndra</td>
	<td>47.93% [47.2%-<b>48.7%</b>]</td>
	<td>18,277</td>
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
	<td>52.45% [52.4%-52.5%]</td>
	<td>2,545,795</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.18% [<b>47.2%</b>-49.2%]</td>
	<td>9,801</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.79% [<b>48.0%</b>-49.6%]</td>
	<td>14,375</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>49.89% [<b>49.0%</b>-50.8%]</td>
	<td>11,595</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>50.14% [<b>49.6%</b>-50.7%]</td>
	<td>32,449</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>50.57% [<b>49.6%</b>-51.6%]</td>
	<td>10,306</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.18% [47.2%-<b>49.2%</b>]</td>
	<td>9,801</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.79% [48.0%-<b>49.6%</b>]</td>
	<td>14,375</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>50.21% [49.8%-<b>50.6%</b>]</td>
	<td>52,725</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>50.14% [49.6%-<b>50.7%</b>]</td>
	<td>32,449</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-kai-sa"></span> Kai'Sa</td>
	<td>50.61% [50.4%-<b>50.8%</b>]</td>
	<td>339,784</td>
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
	<td>51.10% [51.0%-51.2%]</td>
	<td>1,735,051</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.63% [<b>45.4%</b>-47.9%]</td>
	<td>6,077</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.58% [<b>46.3%</b>-48.9%]</td>
	<td>6,106</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.87% [<b>46.7%</b>-49.0%]</td>
	<td>7,618</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.89% [<b>46.9%</b>-48.9%]</td>
	<td>9,457</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.79% [<b>47.5%</b>-50.1%]</td>
	<td>6,268</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>46.63% [45.4%-<b>47.9%</b>]</td>
	<td>6,077</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>47.58% [46.3%-<b>48.9%</b>]</td>
	<td>6,106</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.89% [46.9%-<b>48.9%</b>]</td>
	<td>9,457</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.87% [46.7%-<b>49.0%</b>]</td>
	<td>7,618</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>48.96% [48.8%-<b>49.1%</b>]</td>
	<td>294,520</td>
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
	<td>51.16% [51.0%-51.3%]</td>
	<td>492,104</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>48.17% [<b>45.6%</b>-50.7%]</td>
	<td>1,528</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>47.85% [<b>46.0%</b>-49.7%]</td>
	<td>2,771</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>48.63% [<b>46.4%</b>-50.8%]</td>
	<td>2,050</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>49.25% [<b>46.8%</b>-51.7%]</td>
	<td>1,669</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>48.64% [<b>47.6%</b>-49.7%]</td>
	<td>8,722</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>47.93% [47.6%-<b>48.3%</b>]</td>
	<td>86,264</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-kai-sa"></span> Kai'Sa</td>
	<td>49.13% [48.7%-<b>49.6%</b>]</td>
	<td>54,030</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-vayne"></span> Vayne</td>
	<td>48.64% [47.6%-<b>49.7%</b>]</td>
	<td>8,722</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-yasuo"></span> Yasuo</td>
	<td>47.85% [46.0%-<b>49.7%</b>]</td>
	<td>2,771</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-twitch"></span> Twitch</td>
	<td>49.21% [48.0%-<b>50.5%</b>]</td>
	<td>6,466</td>
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
	<td>50.33% [50.3%-50.4%]</td>
	<td>1,877,550</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.06% [<b>43.9%</b>-46.2%]</td>
	<td>7,077</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>46.13% [<b>45.4%</b>-46.9%]</td>
	<td>17,358</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.70% [<b>45.6%</b>-47.8%]</td>
	<td>7,726</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.68% [<b>46.0%</b>-47.3%]</td>
	<td>23,443</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.85% [<b>46.8%</b>-48.9%]</td>
	<td>9,324</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>45.06% [43.9%-<b>46.2%</b>]</td>
	<td>7,077</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>46.13% [45.4%-<b>46.9%</b>]</td>
	<td>17,358</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-kog-maw"></span> Kog'Maw</td>
	<td>46.68% [46.0%-<b>47.3%</b>]</td>
	<td>23,443</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>46.70% [45.6%-<b>47.8%</b>]</td>
	<td>7,726</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>47.85% [46.8%-<b>48.9%</b>]</td>
	<td>9,324</td>
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
	<td>50.03% [49.9%-50.2%]</td>
	<td>415,628</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.31% [<b>45.1%</b>-49.5%]</td>
	<td>2,080</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-swain"></span> Swain</td>
	<td>48.01% [<b>45.3%</b>-50.7%]</td>
	<td>1,385</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-hwei"></span> Hwei</td>
	<td>48.67% [<b>45.6%</b>-51.7%]</td>
	<td>1,087</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.62% [<b>45.9%</b>-49.3%]</td>
	<td>3,536</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-seraphine"></span> Seraphine</td>
	<td>48.66% [<b>46.3%</b>-51.0%]</td>
	<td>1,794</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-jinx"></span> Jinx</td>
	<td>48.16% [47.7%-<b>48.6%</b>]</td>
	<td>41,642</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-jhin"></span> Jhin</td>
	<td>48.66% [48.3%-<b>49.1%</b>]</td>
	<td>62,840</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-miss-fortune"></span> Miss Fortune</td>
	<td>48.57% [48.0%-<b>49.1%</b>]</td>
	<td>34,318</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nilah"></span> Nilah</td>
	<td>47.62% [45.9%-<b>49.3%</b>]</td>
	<td>3,536</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-veigar"></span> Veigar</td>
	<td>47.31% [45.1%-<b>49.5%</b>]</td>
	<td>2,080</td>
</tr>
</table>

### Support

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
	<td>51.91% [51.7%-52.1%]</td>
	<td>254,532</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>49.87% [<b>46.2%</b>-53.5%]</td>
	<td>762</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>51.24% [<b>48.0%</b>-54.5%]</td>
	<td>931</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.76% [<b>48.0%</b>-49.5%]</td>
	<td>16,674</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.94% [<b>48.1%</b>-49.8%]</td>
	<td>13,428</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.50% [<b>48.2%</b>-50.8%]</td>
	<td>5,654</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.76% [48.0%-<b>49.5%</b>]</td>
	<td>16,674</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.94% [48.1%-<b>49.8%</b>]</td>
	<td>13,428</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>49.59% [48.7%-<b>50.4%</b>]</td>
	<td>13,774</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.50% [48.2%-<b>50.8%</b>]</td>
	<td>5,654</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.57% [48.3%-<b>50.9%</b>]</td>
	<td>5,986</td>
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
	<td>51.62% [51.5%-51.7%]</td>
	<td>825,322</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zac"></span> Zac</td>
	<td>49.79% [<b>47.8%</b>-51.8%]</td>
	<td>2,428</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>49.44% [<b>47.9%</b>-51.0%]</td>
	<td>4,203</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.18% [<b>48.5%</b>-49.8%]</td>
	<td>22,691</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>50.25% [<b>48.6%</b>-51.9%]</td>
	<td>3,741</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.63% [<b>49.1%</b>-50.2%]</td>
	<td>31,575</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zyra"></span> Zyra</td>
	<td>49.18% [48.5%-<b>49.8%</b>]</td>
	<td>22,691</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.63% [49.1%-<b>50.1%</b>]</td>
	<td>42,980</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.63% [49.1%-<b>50.2%</b>]</td>
	<td>31,575</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-lux"></span> Lux</td>
	<td>49.85% [49.5%-<b>50.2%</b>]</td>
	<td>64,921</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-brand"></span> Brand</td>
	<td>49.89% [49.2%-<b>50.6%</b>]</td>
	<td>19,950</td>
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
	<td>52.22% [52.1%-52.3%]</td>
	<td>709,093</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.19% [<b>47.4%</b>-51.0%]</td>
	<td>3,080</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>49.74% [<b>47.6%</b>-51.9%]</td>
	<td>2,115</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>50.89% [<b>48.8%</b>-53.0%]</td>
	<td>2,236</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.72% [<b>48.8%</b>-50.6%]</td>
	<td>12,516</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-leblanc"></span> LeBlanc</td>
	<td>51.42% [<b>49.5%</b>-53.3%]</td>
	<td>2,855</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>49.72% [48.8%-<b>50.6%</b>]</td>
	<td>12,516</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>50.37% [49.9%-<b>50.9%</b>]</td>
	<td>42,980</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-teemo"></span> Teemo</td>
	<td>49.19% [47.4%-<b>51.0%</b>]</td>
	<td>3,080</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-milio"></span> Milio</td>
	<td>50.58% [50.0%-<b>51.2%</b>]</td>
	<td>26,326</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-poppy"></span> Poppy</td>
	<td>50.50% [49.7%-<b>51.3%</b>]</td>
	<td>14,002</td>
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
	<td>50.92% [50.8%-51.0%]</td>
	<td>746,233</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-galio"></span> Galio</td>
	<td>48.48% [<b>46.3%</b>-50.6%]</td>
	<td>2,178</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>49.17% [<b>47.1%</b>-51.3%]</td>
	<td>2,235</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.07% [<b>47.1%</b>-49.0%]</td>
	<td>11,357</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.94% [<b>47.8%</b>-50.1%]</td>
	<td>7,378</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-taric"></span> Taric</td>
	<td>49.26% [<b>47.8%</b>-50.7%]</td>
	<td>4,649</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-sona"></span> Sona</td>
	<td>48.07% [47.1%-<b>49.0%</b>]</td>
	<td>11,357</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.61% [48.1%-<b>49.1%</b>]</td>
	<td>43,724</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>48.90% [48.4%-<b>49.4%</b>]</td>
	<td>46,504</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-xerath"></span> Xerath</td>
	<td>49.23% [48.6%-<b>49.9%</b>]</td>
	<td>25,027</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>48.94% [47.8%-<b>50.1%</b>]</td>
	<td>7,378</td>
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
	<td>51.39% [51.2%-51.5%]</td>
	<td>390,937</td>
</tr>
<tr>
	<th colspan=4>Bad matchups</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-zoe"></span> Zoe</td>
	<td>49.91% [<b>47.0%</b>-52.9%]</td>
	<td>1,146</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-shen"></span> Shen</td>
	<td>49.50% [<b>47.0%</b>-52.0%]</td>
	<td>1,596</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.70% [<b>47.6%</b>-49.8%]</td>
	<td>8,095</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-tahm-kench"></span> Tahm Kench</td>
	<td>49.30% [<b>47.7%</b>-50.9%]</td>
	<td>3,951</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.39% [<b>47.7%</b>-49.1%]</td>
	<td>21,801</td>
</tr>
<tr>
	<th colspan=4>Good counters</th>
</tr>
<tr>
	<td>1.</td>
	<td><span class="lol-icon lol-senna"></span> Senna</td>
	<td>48.39% [47.7%-<b>49.1%</b>]</td>
	<td>21,801</td>
</tr>
<tr>
	<td>2.</td>
	<td><span class="lol-icon lol-janna"></span> Janna</td>
	<td>48.70% [47.6%-<b>49.8%</b>]</td>
	<td>8,095</td>
</tr>
<tr>
	<td>3.</td>
	<td><span class="lol-icon lol-lulu"></span> Lulu</td>
	<td>49.22% [48.6%-<b>49.9%</b>]</td>
	<td>25,083</td>
</tr>
<tr>
	<td>4.</td>
	<td><span class="lol-icon lol-nami"></span> Nami</td>
	<td>49.42% [48.8%-<b>50.0%</b>]</td>
	<td>26,326</td>
</tr>
<tr>
	<td>5.</td>
	<td><span class="lol-icon lol-blitzcrank"></span> Blitzcrank</td>
	<td>49.48% [48.6%-<b>50.4%</b>]</td>
	<td>13,038</td>
</tr>
</table>
