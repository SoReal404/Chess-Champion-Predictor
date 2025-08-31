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
- `event`: Tournament/event ID
- `Rounds`, `Section`, `Games Num`: Extracted from round info
- `white_elo`, `black_elo`: Player Elo ratings
- `white_id`, `black_id`: Unique player identifiers
- `opening_encod`, `eco_endoded`: Encoded openings and ECO codes
- `white_avg_elo`, `black_avg_elo`: Average Elo of players over past matches
- `white_win_rate`, `black_win_rate`: Historical win rates
- `Rating Diff`: Difference in Elo (White - Black)

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
Example of predicted probabilities for top matches:

| White            | Black            | Predicted Probabilities (White/Black/Draw) |
| ---------------- | ---------------- | ---------------------------------------- |
| Magnus Carlsen   | D. Gukesh        | [0.48, 0.25, 0.27]                        |
| Magnus Carlsen   | Alireza Firouzja | [0.46, 0.26, 0.28]                        |
| Hikaru Nakamura  | Arjun Erigaisi   | [0.47, 0.26, 0.28]                        |
| Hikaru Nakamura  | D. Gukesh        | [0.46, 0.25, 0.28]                        |

---

## Installation
```bash
# Clone repository
git clone <your_repo_url>

# Navigate to project directory
cd chess-predictor

# Install dependencies
pip install -r requirements.txt
