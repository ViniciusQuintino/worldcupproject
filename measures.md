# 📐 Measures Documentation (DAX)

This document describes the main measures used in the project,
focusing on logic, filter context, and analytical impact.

---

## Total Matches (Base Measure)

```DAX
TOTAL_MATCHES =
COUNTROWS ( fact_matches )
```
Counts the total number of matches considering the applied filters
(World Cup, national team, and period).

## Total Goals (Base Measure)

```DAX
TOTAL_GOALS =
SUM ( fact_matches[home_team_score] )
    + SUM ( fact_matches[away_team_score] )
```
Calculates the total number of goals scored by summing goals from
home and away teams, respecting the applied filters
(World Cup, national team, and period).

## Cumulative Titles by National Team (Advanced Measure)

```DAX
TOURNAMENTS_TITLE =
VAR Team =
    SELECTEDVALUE ( dim_tournaments[Winner_Norm] )
VAR year =
    SELECTEDVALUE ( dim_tournaments[year] )
RETURN
    CALCULATE (
        COUNTROWS ( dim_tournaments ),
        dim_tournaments[Winner_Norm] = Team,
        dim_tournaments[year] <= year
    )
```
Calculates the cumulative number of titles won by each national team
over time.

This measure uses variables to capture the winning team and the
current year, enabling the analysis of the historical evolution
of titles by team across World Cup editions.

**Logic:**  
- `SELECTEDVALUE` identifies the winning team in the current context
The selected year defines the upper limit for the count 
- `CALCULATE` redefines the filter context to count titles accumulated
up to the selected year

## Last Champion (Advanced Measure)

```DAX
LAST_CHAMPION =
VAR Selected =
    SELECTEDVALUE ( dim_tournaments[Winner_Norm] )

VAR LastYear =
    CALCULATE (
        MAX ( dim_tournaments[year] ),
        ALLSELECTED ( dim_tournaments )
    )

VAR Champion =
    CALCULATE (
        MAX ( dim_tournaments[Winner_Norm] ),
        dim_tournaments[year] = LastYear
    )

RETURN
    IF (
        NOT ISBLANK ( Selected ),
        Selected,
        Champion
    )
```
Returns the most recent FIFA World Cup champion based on the applied
filters. If a specific team is selected, the measure returns that team;
otherwise, it returns the champion of the most recent available edition
within the selected period.

**Logic:**  
- `SELECTEDVALUE` checks whether a team is selected
- `ALLSELECTED` ensures the latest year calculation respects active
page filters (such as selected periods or editions)  
- Conditional logic determines which champion is displayed

## Goals by Player and National Team (Advanced Measure)

```DAX
  SCORERS =
VAR Player =
    SELECTEDVALUE ( fact_goals[given_name] )
        & " "
        & SELECTEDVALUE ( fact_goals[family_name] )

VAR Team =
    SELECTEDVALUE ( dim_teams[team_name] )

RETURN
    CALCULATE (
        COUNTROWS ( fact_goals ),
        fact_goals[given_name] & " " & fact_goals[family_name] = Player,
        fact_goals[team_name] = Team
    )
```
Calculates the total number of goals scored by a player, considering
the selected athlete and national team in the filter context.

**Lógica:**  
- The player’s full name is dynamically built using `SELECTEDVALUE`  
- The national team is applied as an additional filter for consistency  
- `CALCULATE` redefines the context to count only goals scored by the
selected player and team

## Head-to-Head Wins (Advanced Measure)

```DAX

WINS =
VAR Team =
    SELECTEDVALUE ( dim_teams[team_name] )
VAR Opp =
    SELECTEDVALUE ( dim_opponents[Team] )
RETURN
    SUMX (
        fact_matches,
        VAR WinHome =
            IF (
                fact_matches[penalty_shootout] <> 1
                    && fact_matches[home_team_name] = Team
                    && fact_matches[away_team_name] = Opp,
                fact_matches[home_team_win],
                0
            )
        VAR WinAway =
            IF (
                fact_matches[penalty_shootout] <> 1
                    && fact_matches[away_team_name] = Team
                    && fact_matches[home_team_name] = Opp,
                fact_matches[away_team_win],
                0
            )
        RETURN
            WinHome + WinAway
    )
```
Calculates the total number of wins for a national team in head-to-head
matches against a specific opponent, considering games played as both
home and away teams and excluding matches decided by penalty shootouts.

This measure allows detailed analysis of historical head-to-head records
while respecting the selected team and opponent context in the report.

**Logic:**  
- `SELECTEDVALUE` identifies the main team and the opponent  
- `SUMX` iterates through the matches table row by row  
- Home and away wins are calculated separately  
- Matches decided by penalty shootouts are excluded  
- The final result consistently sums home and away victories



