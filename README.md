# Chess Match Outcome Predictor

A machine learning project that predicts the outcome of chess matches between top players using historical game data. Inspired by Green Code’s sports prediction videos, this project focuses on chess and leverages XGBoost to forecast match results and probabilities.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Features](#features)
- [Model](#model)
- [Predictions](#predictions)
- [Installation](#installation)
- [Usage](#usage)
- [Future Work](#future-work)
- [Credits](#credits)

---

## Project Overview
This project predicts whether the White player wins, the Black player wins, or if the match ends in a draw. The workflow includes:
1. Cleaning and preparing chess game data from Lichess broadcasts.
2. Feature engineering: player Elo ratings, win rates, player IDs, round/section/game info, opening and ECO codes.
3. Training an XGBoost classifier on historical matches.
4. Predicting match outcomes with probabilities for real-world scenarios, including top players like Magnus Carlsen, Hikaru Nakamura, Gukesh D, Alireza Firouzja, and Levon Aronian.

---

## Dataset
- **Source:** [Lichess Broadcast PGN Database](https://database.lichess.org/broadcast/)
- **Timeframe:** 2025
- **Format:** PGN files
- **Preprocessing:** 
  - Extracted player names, Elo ratings, results, openings, ECO codes, and rounds.
  - Encoded categorical features and calculated additional features like rating differences and win rates.

---

## Features
'event', 
'white_elo', 
'black_elo', 
'opening_encod', 
'eco_endoded',
'Rounds', 
'Section', 
'Games Num', 
'Rating Diff', 
'white_id', 
'black_id',
'white_avg_elo',
'black_avg_elo',
'white_win_rate',
'black_win_rate'

**Target:**  
- `Match_Result_Encoded`: 0 = White Wins, 1 = Black Wins, 2 = Draw

---

## Model
- **Algorithm:** XGBoost Classifier
- **Input:** Features listed above
- **Output:** Predicted match outcome and probabilities for each class
- **Training:** Historical chess matches (cleaned and preprocessed)
- **Evaluation:** Tested on real-world top-player matches from 2025

---

## Predictions

| White            | Black            | White ID | Black ID | White Elo | Black Elo | Real Result | Predicted Winner | Probabilities (W/B/D)  |
| ---------------- | ---------------- | -------- | -------- | --------- | --------- | ----------- | ---------------- | ---------------------- |
| Magnus Carlsen   | D. Gukesh        | 981      | 777      | 2865      | 2720      | White Wins  | White Wins       | \[0.481, 0.254, 0.264] |
| Magnus Carlsen   | Alireza Firouzja | 981      | 782      | 2865      | 2790      | White Wins  | White Wins       | \[0.464, 0.259, 0.277] |
| Hikaru Nakamura  | Arjun Erigaisi   | 776      | 788      | 2789      | 2725      | White Wins  | White Wins       | \[0.466, 0.256, 0.278] |
| Hikaru Nakamura  | D. Gukesh        | 776      | 777      | 2789      | 2720      | Black Wins  | White Wins       | \[0.463, 0.255, 0.282] |
| Levon Aronian    | Magnus Carlsen   | 779      | 981      | 2750      | 2865      | White Wins  | Draw             | \[0.366, 0.295, 0.338] |
| Alireza Firouzja | Levon Aronian    | 782      | 779      | 2790      | 2750      | White Wins  | White Wins       | \[0.444, 0.285, 0.271] |

---

## Installation
```bash
# Clone repository
git clone https://github.com/SoReal404/Chess-Champion-Predictor.git

# Navigate to project directory
cd chess-predictor

# Install dependencies
pip install -r requirements.txt
