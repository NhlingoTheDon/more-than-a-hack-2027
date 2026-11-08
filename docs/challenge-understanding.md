# Challenge Understanding – More Than a Hack 2027

## 1. Challenge objective

Our objective is to predict which team has possession of the ball in every frame of the provided football match.

We are not building a player-tracking system from scratch. The challenge provides tracking, video, tactical tagging and homography data.

Our main objective is to identify accurate, continuous possession periods.

## 2. Label definitions

| Label | Definition |
|---|---|
| H | Home team has possession |
| A | Away team has possession |
| D | Ball is dead / not in play |
| X | System abstains from making a prediction |

All team members must use these definitions consistently.

## 3. Possession rules

A possession change happens when an opposing player gains controlled possession.

The following do not automatically count as possession changes:
- A simple touch.
- A deflection.
- An aerial duel without subsequent control.
- A loose or contested ball.

During a loose-ball situation, possession remains with the last team that controlled the ball.

A dead-ball period is a stoppage, not a possession.

## 4. Evaluation metrics

### macroF1
Measures frame-level classification performance by averaging the F1 scores of H, A and D.

### spellF1
Measures how accurately we identify complete possession periods.

It compares predicted and actual possession segments using temporal IoU.

**Our primary objective is spellF1**, because it determines the competition ranking. macroF1 is the secondary metric and tie-breaker.

We must avoid unnecessary possession splits and incorrect possession transitions.

## 5. Submission requirements

Our final possession CSV must contain:

- Header: `frame,label`
- Exactly 199,319 data rows.
- Frame numbers from 0 to 199318 in order.
- Labels restricted to H, A, D and X.
- UTF-8 encoding.
- No blank values or additional index columns.

The submission must be validated using:

`python evaluation/validate_submission.py your_submission.csv`

## 6. Team decisions and outstanding questions

Before modelling begins, we must agree on:

1. How we interpret controlled possession.
2. How we handle loose balls and uncertain tracking.
3. How we detect possession changes.
4. How we handle dead-ball periods and restarts.
5. How we evaluate our predictions without overfitting to the public five-minute sample.

## 7. Team confirmation

Each team member should confirm that they understand:

- [ ] The challenge objective.
- [ ] The H, A, D and X labels.
- [ ] The possession-change rules.
- [ ] The difference between macroF1 and spellF1.
- [ ] The final submission format.

**Project lead approval:** The project lead must review this document and confirm that the team understands the challenge before model experimentation begins.