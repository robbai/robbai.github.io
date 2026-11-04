---
layout: post
title:  Pundit-derived rating
date:   2024-08-02
categories: rocket-league
excerpt: Deriving a rating system from expert-analysis
image: rlcs-2026-ratings.png
---

## Intro
This was a test in creating a rating system based on player rankings created by pundits.
The aim was to find a way to rate players that may more closely pass the "eye-test", than a system derived from game outcome.

## Project
### Sources

The data sources use consist from 3 international events, using the player ranking posted by _JohnnyBoi\_i_ following the events:
* 2021-22 Winter Major
  * [https://www.youtube.com/watch?v=GOOMcQLaFFE]
  * [https://ballchasing.com/group/main-event-82yslpanet]
* 2021-22 World Championship
  * [https://www.youtube.com/watch?v=9wNMjk3Eqsw]
  * [https://ballchasing.com/group/]world-championship-e2fj8jv44a
* 2024 Major 2
  * [https://www.youtube.com/watch?v=km-xMCEkF3I]
  * [https://ballchasing.com/group/lan-nu92kpr2hf]

<br/>

This results in a dataset of:
* **3** events
* **15** rankings
  * 6 unique pundits: _JohnnyBoi\_i_, _TBates_, _CJCJ_, _Roll Dizz_, _yumi\_cheeseman_, _Dazerin_
* **319** player-placements
  * 47 unique players

<br/>

Individual rankings data:
<details markdown="1">
<summary>2021-22 Winter Major</summary>

```json
{
    "event": "614b6649f8090ec745286427",
    "rankings": {
        "3f9e-rise": [1, 2, 2, 1, 2],
        "3fe6-atomic": [2, 1, 3, 1, 2],
        "41b8-beastmode": [3, 3, 7, 3, 5],
        "3d8f-jknaps": [4, 4, 6, 3, 4],
        "40d2-m0nkey-m00n": [5, 7, 9, 7, 9],
        "4363-daniel": [6, 10, 8, 7, 10],
        "3eb6-firstkiller": [7, 6, 4, 6, 6],
        "4337-yanxnz": [8, 5, 11, 8, 12],
        "9570-vatira": [9, 12, 5, 9, 11],
        "4232-joyo": [10, 9, 1, 4, 5],
        "3dba-chicago": [11, 11, 10, 10, 11],
        "3eda-arsenal": [12, 8, 13, 8, 12],
        "3f4d-caiotg1": [13, 14, 14],
        "3eba-ayyjayy": [14, 14],
        "40b2-comm": [15, 13, 15, 13, 14],
        "3dcf-justin": [15],
        "96a5-seikoo": [12, 15, 15],
        "3ede-sypical": [13]
    }
}
```
</details>

<details markdown="1">
<summary>2021-22 World Championship</summary>

```json
{
    "event": "614b6485f8090ec745286425",
    "rankings": {
        "4337-yanxnz": [1, 1, 3, 4, 7],
        "96a5-seikoo": [1, 1, 2, 3, 4],
        "9570-vatira": [1, 2, 2, 4, 6],
        "40d2-m0nkey-m00n": [2, 2, 3, 5, 6],
        "41b8-beastmode": [3, 3, 5, 5, 6],
        "3fe6-atomic": [4, 7, 7, 8, 18],
        "3eb6-firstkiller": [4, 5, 5, 6, 8],
        "4232-joyo": [6, 13, 13, 17, 17],
        "03f0-trk511": [7, 8, 9, 13, 16],
        "3dba-chicago": [7, 10, 10, 13, 14],
        "3f9e-rise": [8, 10, 10, 12, 15],
        "bf05-mist": [8, 18],
        "3f60-caard": [9, 12, 13, 15, 20],
        "3f83-aztral": [9, 11, 11, 14, 19],
        "3d8f-jknaps": [9, 10, 12, 14, 15],
        "3f88-ahmad": [9, 12, 14, 14, 15],
        "3fb9-extra": [11, 11, 17, 19, 24],
        "a477-itachi": [11, 17, 18, 19],
        "4363-daniel": [12, 16, 16, 17, 22],
        "3eba-ayyjayy": [16, 25],
        "415f-archie": [15, 23],
        "4142-exotiik": [16],
        "3ede-sypical": [18, 19, 19, 20],
        "3dcf-justin": [18, 20, 21],
        "40b2-comm": [20, 22, 23],
        "3f4d-caiotg1": [20, 21],
        "3eda-arsenal": [21],
        "e7f1-lostt": [21, 22, 25, 21],
        "40d3-noly": [22, 23, 23],
        "3f95-okhalid": [24, 25],
        "4263-retals": [24]
    }
}
```
</details>

<details markdown="1">
<summary>2024 Major 2</summary>

```json
{
    "event": "65a82626370e82dfea34e7ad",
    "rankings": {
        "41b8-beastmode": [1, 1, 1, 1, 1],
        "03f0-trk511": [2, 4, 8, 11, 13],
        "41dd-zen": [2, 3, 5, 6, 11],
        "a477-itachi": [2, 3, 3, 4, 9],
        "4363-daniel": [2, 5, 6, 8, 9],
        "8280-kiileerrz": [2, 3, 4, 5, 7],
        "426a-lj": [3, 4, 6, 8, 10],
        "4337-yanxnz": [4, 5, 7, 8, 9],
        "3fe6-atomic": [5, 9, 10, 11, 13],
        "3eb6-firstkiller": [6, 10, 12, 14, 15],
        "a545-rw9": [6, 7, 9, 10, 12],
        "96a5-seikoo": [7, 8, 11, 12, 13],
        "d214-juicy": [7, 11, 12, 12, 14],
        "444d-oski": [10, 20, 21, 22, 25],
        "e7f1-lostt": [13, 14, 14, 15, 25],
        "40d2-m0nkey-m00n": [13, 14, 15, 17, 19],
        "6e02-dralii": [15, 16, 21, 23, 24],
        "3ee3-alpha54": [15, 17, 18, 18, 19],
        "41c9-chronic": [16, 24, 24],
        "3f75-hockser": [16, 16, 21, 21, 25],
        "4416-drufinho": [16, 17, 18, 18],
        "40b2-comm": [17],
        "41d5-radosin": [17, 21, 24, 25],
        "1caa-bananahead": [18],
        "4142-exotiik": [19, 19, 20],
        "4161-apparentlyjack": [19, 22, 22, 22, 22],
        "3dba-chicago": [20, 20, 23, 24],
        "4077-fever": [20, 23, 25],
        "427d-brad": [23, 23]
    }
}
```
</details>

## Methodology

### Rankings loss function

Given a list of ratings, you can simply rank the players by ordering them by rating, the problem is that this is non-differentiable.

If we can create a differentiable ranking, then we can use it as a loss function for the purpose of gradient descent, therefore allowing us to train the parameters of a rating calculation to fit the given pundit rankings.

So instead let us take the list of ratings, and assign them a rank by summing the sign of the rating relative to all other ratings, then shifting and scaling the range to be 1 through the total number of players.

```py
def get_rating_rankings_sign(
    ratings: Dict[str, torch.Tensor]
) -> torch.Tensor:
    # Convert the ratings to rankings.
    rating_values: torch.Tensor = torch.stack(list(ratings.values()))
    rating_rankings: torch.Tensor = (
        torch.sign(
            (rating_values.unsqueeze(1) - rating_values)
        ).sum(dim=0)
        + len(ratings)
        + 1
    ) / 2
    return rating_rankings
```

Of course the sign function isn't great for differentiability, so let's smoothen it by using tanh:

```py
def get_rating_rankings(
    ratings: Dict[str, torch.Tensor], alpha: float = 0.4
) -> torch.Tensor:
    # Convert the ratings to rankings.
    rating_values: torch.Tensor = torch.stack(list(ratings.values()))
    rating_rankings: torch.Tensor = (
        torch.tanh(
            (rating_values.unsqueeze(1) - rating_values) * alpha
        ).sum(dim=0)
        + len(ratings)
        + 1
    ) / 2
    return rating_rankings
```

This introduces a hyperparameter, alpha here, which allows us to scale how (inversely) smooth the function is. The sign function is equivalent to alpha=infinity.

Now given ratings, we can now produce a differentiable ranking with respect to the ratings. Lastly, we'll use the L1-norm (MAE) between the pundits' (target) rankings and our rankings to present our final scalar loss.

### Model

The model will simply be a linear function (similar to how _Octane.gg_ produces ratings), using the following selected stats:
* `goals`
* `pctBehindBall`
* `pctOffensiveHalf`
* `pctGround`
* `countStolenBig`
* `score`
* `pctSupersonicSpeed`
* `pctHighAir`
* `assists`
* `pctNeutralThird`
* `countCollectedSmall`
* `timeBoost75To100`
* `shots`
* `saves`
* `countStolenSmall`
* `pctDefensiveThird`
* `countCollectedBig`
* `pctSlowSpeed`
* `timeBoost25To50`
* `pctBoostSpeed`
* `pctOffensiveThird`
* `timeBoost50To75`
* `pctLowAir`
* `pctDefensiveHalf`
* `timeBoost0To25`
* `pctInfrontBall`

Z-scoring (whitening) of individual stats is used to prepare the data for the model for stability.

The final produced model's ratings are rescaled to match the scaling of _Octane.gg_'s ratings: `mean=0.93013`, `stdev=0.15268`.

## Result

### Coefficients

The final rating function is a linear sum of:
* 0.148802
* `goals` * 0.148802
* `pctBehindBall` * 0.010511
* `pctOffensiveHalf` * 0.007215
* `pctGround` * 0.008041
* `countStolenBig` * 0.038557
* `score` * 0.000459
* `pctSupersonicSpeed` * 0.005669
* `pctHighAir` * 0.009442
* `assists` * 0.143217
* `pctNeutralThird` * 0.007044
* `countCollectedSmall` * 0.0025
* `timeBoost75To100` * 0.001312
* `shots` * 0.027277
* `saves` * 0.00617
* `countStolenSmall` * -0.000726
* `pctDefensiveThird` * -0.001601
* `countCollectedBig` * 0.000498
* `pctSlowSpeed` * -0.002636
* `timeBoost25To50` * -0.000517
* `pctBoostSpeed` * -0.007163
* `pctOffensiveThird` * -0.008441
* `timeBoost50To75` * -0.004348
* `pctLowAir` * -0.008719
* `pctDefensiveHalf` * -0.006259
* `timeBoost0To25` * -0.001684
* `pctInfrontBall` * -0.010882

### Userscript

I made a userscript for use on _Ballchasing.com_, showing the ratings of a player in a replay group:
<details markdown="1">
<summary>Userscript</summary>

```js
// ==UserScript==
// @name         Ballchasing: Ratings
// @namespace    http://tampermonkey.net/
// @version      2025-01-27
// @description  try to take over the world!
// @author       robbai
// @match        https://ballchasing.com/group/*/players-stats
// @icon         https://www.google.com/s2/favicons?sz=64&domain=ballchasing.com
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    const COLUMN_INDEX = 2;

    // Function to calculate the rating for the new column based on other columns.
    function calculateRating(matchingRows) {
        // Get rows.
        const coreCells = matchingRows['core-stats-avg'].cells;
        const boostCells = matchingRows['boost-stats-avg'].cells;
        const positioningCells = matchingRows['pos-stats-avg'].cells;
        const movementCells = matchingRows['move-stats-avg'].cells;

        // Calculate rating components from stats.
        const goals = (parseFloat(coreCells[5].textContent) || 0) * 49.0125;
        const pctBehindBall = (parseFloat(positioningCells[7].textContent) || 0) * 3.46215;
        const pctOffensiveHalf = (parseFloat(positioningCells[6].textContent) || 0) * 2.37651;
        const pctGround = (parseFloat(movementCells[6].textContent) || 0) * 2.64845;
        const countStolenBig = (parseFloat(boostCells[13].textContent) || 0) * 12.7;
        const score = (parseFloat(coreCells[3].textContent) || 0) * 0.1512;
        const pctSupersonicSpeed = (parseFloat(movementCells[5].textContent) || 0) * 1.8673;
        const pctHighAir = (parseFloat(movementCells[8].textContent) || 0) * 3.10988;
        const assists = (parseFloat(coreCells[9].textContent) || 0) * 47.1731;
        const pctNeutralThird = (parseFloat(positioningCells[3].textContent) || 0) * 2.32023;
        const countCollectedSmall = (parseFloat(boostCells[12].textContent) || 0) * 0.82354;
        const pctBoost75To100 = (parseFloat(boostCells[10].textContent) || 0) * 0.432147;
        const shots = (parseFloat(coreCells[4].textContent) || 0) * 8.98444;
        const saves = (parseFloat(coreCells[10].textContent) || 0) * 2.03216;
        const countStolenSmall = (parseFloat(boostCells[14].textContent) || 0) * -0.239164;
        const pctDefensiveThird = (parseFloat(positioningCells[2].textContent) || 0) * -0.527208;
        const countCollectedBig = (parseFloat(boostCells[11].textContent) || 0) * 0.164137;
        const pctSlowSpeed = (parseFloat(movementCells[3].textContent) || 0) * -0.868159;
        const pctBoost25To50 = (parseFloat(boostCells[8].textContent) || 0) * -0.170417;
        const pctBoostSpeed = (parseFloat(movementCells[4].textContent) || 0) * -2.35937;
        const pctOffensiveThird = (parseFloat(positioningCells[4].textContent) || 0) * -2.78038;
        const pctBoost50To75 = (parseFloat(boostCells[9].textContent) || 0) * -1.43221;
        const pctLowAir = (parseFloat(movementCells[7].textContent) || 0) * -2.87196;
        const pctDefensiveHalf = (parseFloat(positioningCells[5].textContent) || 0) * -2.0615;
        const pctBoost0To25 = (parseFloat(boostCells[7].textContent) || 0) * -0.554703;
        const pctInfrontBall = (parseFloat(positioningCells[8].textContent) || 0) * -3.58424;

        // Final rating calculation.
        var rating = goals + pctBehindBall + pctOffensiveHalf + pctGround + countStolenBig + score + pctSupersonicSpeed + pctHighAir + assists + pctNeutralThird + countCollectedSmall + pctBoost75To100 + shots + saves + countStolenSmall + pctDefensiveThird + countCollectedBig + pctSlowSpeed + pctBoost25To50 + pctBoostSpeed + pctOffensiveThird + pctBoost50To75 + pctLowAir + pctDefensiveHalf + pctBoost0To25 + pctInfrontBall;
        rating += 147.1398;
        rating /= 329.3811;

        return rating;
    }

    // Run on page load.
    // window.addEventListener('load', function() {
        // Select the main table.
        const mainTable = document.querySelector('table#core-stats-avg');
        if (mainTable === null) {
            return;
        }

        // Get all tables on the page.
        const allTables = document.querySelectorAll('table');

        // Create a mapping of player names to table rows.
        const matchingRows = {};
        allTables.forEach(table => {
            const rows = table.querySelectorAll('tr');
            rows.forEach(row => {
                const player = row.cells[0].textContent; // Get the player's name.
                if (!(player in matchingRows)) {
                    matchingRows[player] = {};
                }
                matchingRows[player][table.id] = row;
            });
        });

        // Add a new header cell to the main table.
        const headerRow = mainTable.querySelector('tr');
        var ratingHeader;
        if (headerRow) {
            // Create header cell by cloning the next column's header.
            const nextColumnHeader = headerRow.children[2];
            ratingHeader = nextColumnHeader.cloneNode(true);
            ratingHeader.innerHTML = ratingHeader.innerHTML.replace('Win %', 'Rating');

            // Insert the new header cell.
            headerRow.insertBefore(ratingHeader, headerRow.children[COLUMN_INDEX]);
        }

        // Add a new cell to each row in the table.
        const rows = mainTable.querySelectorAll('tr');
        rows.forEach((row, index) => {
            // Skip the header row.
            if (index > 0) {
                const ratingCell = document.createElement('td');

                // Calculate the data for the new column using the function.
                const player = row.cells[0].textContent; // Get the player's name.
                const matchingRowsPlayer = matchingRows[player]; // Find matching rows in other tables.
                ratingCell.textContent = calculateRating(matchingRowsPlayer).toFixed(3);

                // Insert the new rating cell.
                row.insertBefore(ratingCell, row.children[COLUMN_INDEX]);
            }
        });

        // Sort main table by descending rating.
        if ('ontouchstart' in document.documentElement) {
            setTimeout(() => {
                ratingHeader.click();
            }, 100);
        } else {
            ratingHeader.click();
            ratingHeader.click();
        }
    // });
})();
```
</details>

<br/>

Example from the 2026 World Championship:
[https://ballchasing.com/group/world-championship-bdh552n3l3/players-stats]
<br/>
<img src="{{ site.baseurl }}/images/rlcs-2026-ratings.png"/>
