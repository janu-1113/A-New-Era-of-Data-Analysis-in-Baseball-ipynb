# A New Era of Data Analysis in Baseball

Comparing Aaron Judge and Giancarlo Stanton, two of baseball's biggest sluggers, using Statcast data from 2015-2017.

## Overview

Statcast is a tracking system that uses high-resolution cameras and radar in all 30 major league ballparks (introduced in 2015) to measure the movement and location of the baseball and the players. This project wrangles, analyzes and visualizes Statcast data to see how Judge and Stanton, who both led baseball in home runs in 2017 (Stanton 59, Judge 52) and became Yankees teammates in 2018, differ as hitters.

## Dataset

Two CSV files, one pitch per row, covering 2015-2017:

- `judge.csv` - Statcast data for Aaron Judge
- `stanton.csv` - Statcast data for Giancarlo Stanton

Columns used in the analysis:

| Column | Meaning |
|---|---|
| `game_year` | Season of the pitch |
| `events` | Result of the batted ball event (home_run, strikeout, walk, field_out, ...) |
| `launch_angle` | Vertical angle at which the ball leaves the bat |
| `launch_speed` | Exit velocity of the ball off the bat |
| `release_speed` | Velocity of the pitch |
| `zone` | Strike zone location (1-9 inside the zone) as the pitch crosses the plate |
| `player_name` | Hitter |

Place the files in a `datasets/` folder next to the notebook.

## Analysis

1. **Load and inspect the data** with pandas; each row is one pitch.
2. **Batted ball events in 2017** - compare the frequency of each outcome for both players.
3. **Home runs: launch angle vs. exit velocity** - scatter plots and KDE contour plots for each player.
4. **Home runs by pitch velocity** - box plots of `release_speed` for each player's home runs.
5. **Home runs by pitch location** - map strike zones 1-9 to a 3x3 grid with `assign_x_coord` / `assign_y_coord`, then plot 2D histograms for each player.

## Key Findings

- 2017 events: Judge struck out 207 times and walked 116 times, while Stanton struck out 161 times and walked 72 times. Stanton had more field outs (239 vs. 146).
- Stanton hits his home runs slightly lower and slightly harder than Judge, though the sample of home runs is small.
- Judge hits his home runs off faster pitches (more of a fastball hitter); Stanton's are less dependent on pitch speed.
- Both love pitches in the middle of the zone. Stanton rarely homers on pitches in the upper third, and his zone is middle-inside. Judge's zone is more spread out, with high-away his least favorite.
- Despite similar size and power, the two have different launch profiles and pitch speed and location preferences.

## Getting Started

Requirements: Python 3, pandas, matplotlib, seaborn, Jupyter.

```bash
pip install pandas matplotlib seaborn jupyter
jupyter notebook Project_A_New_Era_of_Data_Analysis_in_Baseball.ipynb
```

## Project Structure

```
Project_A_New_Era_of_Data_Analysis_in_Baseball.ipynb
datasets/
  judge.csv
  stanton.csv
README.md
```

## Notes

- The notebook uses an older seaborn API for the KDE plots (`shade_lowest`, passing x and y positionally). Newer seaborn versions need `fill=True` and `x=`/`y=` keywords.
- Zones 11-14 (outside the strike zone) are excluded from the location plots.
- Originally a DataCamp guided project.
