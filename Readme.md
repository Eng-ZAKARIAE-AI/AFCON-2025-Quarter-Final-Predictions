
#  AFCON 2025 AI Predictor ("Moneyball" Edition)

> **A robust, history-aware Machine Learning engine that predicts Match Winners and Exact Scores for the Africa Cup of Nations.**

## About the project

This project moves beyond simple statistics by implementing a **Dynamic Elo Engine**. Instead of relying on static rankings, this script "replays" every AFCON match from 1990 to the present day to calculate the true strength of every team.

It combines **Gradient Boosting** (to predict who wins) with **Poisson Distribution** (to simulate realistic scorelines), ensuring that the predicted scores mathematically align with the win probabilities.

## Key Features

* ** Dynamic Elo Engine:** Calculates team strength match-by-match historically (e.g., beating a strong Nigeria gives more points than beating a weak team).
* ** Hybrid Prediction Model:**
* ** The Brain:** Uses `GradientBoostingClassifier` to determine *Win/Draw/Loss* probabilities.
* ** The Dice:** Uses `numpy.random.poisson` to generate realistic *Goal Counts*.


* **  Consistency Check:** A specialized loop that forces the generated scoreline to match the Machine Learning prediction (prevents "Team A wins" with a "0-1" score).
* **  Context Awareness:** Includes a `form_boost` parameter to account for **Home Advantage** (Morocco) or **Squad Quality** (Senegal, Nigeria) manually.

##   Tech Stack

* **Python 3.x**
* **Pandas:** For historical data processing.
* **NumPy:** For Poisson simulations and math operations.
* **Scikit-Learn:** For the Gradient Boosting Classifier.

##  Installation

1. **Clone the repository** (or create a folder for your project).
2. **Install dependencies**:
```bash
pip install pandas numpy scikit-learn

```


3. **Add the Data**:
Ensure you have the file `AFCON_Matches_1990_Present.csv` in the same directory.

##  Usage

Simply run the script in your terminal:

```bash
python predict_afcon.py

```

### Sample Output

```text
 --- CONSISTENT PREDICTIONS ---

 Mali vs Senegal
   Strength: Mali (1638) vs Senegal (1783)
   Win Probabilities: Mali 17.5% | Draw 36.4% | Senegal 46.1%
   Predicted Score: Mali 0 – 1 Senegal

 Cameroon vs Morocco
   Strength: Cameroon (1691) vs Morocco (1796)
   Win Probabilities: Cameroon 13.8% | Draw 25.5% | Morocco 60.7%
   Predicted Score: Cameroon 1 – 3 Morocco

```

##  Customization

You can adjust the "Eye Test" factors in the `predict_match` function inside the script. This allows you to combine data with real-world knowledge (e.g., injuries, momentum).

```python
form_boost = {
    'Morocco': 120,   # High boost for Home Advantage
    'Senegal': 80,    # Boost for defending champions
    'Egypt': -10      # Penalty for poor recent form
}

```
##  After Match : 

```
https://github.com/Eng-ZAKARIAE-AI/AFCON-2025-Quarter-Final-Predictions/blob/master/assets/afterMatchesResult.png

```


##  Project Structure

```text
├── AFCON_Matches_1990_Present.csv  # Historical Data Source
├── assets  # images,...  #static things as images ...
├── predict_afcon.py                # Main Logic & Prediction Engine
├── README.md                       # Documentation
└── requirements.txt                # Dependencies

```

##  Contributing

Feel free to fork this project and add features like:

* Integration with live API data.
* Player-specific stats (xG, xA).
* Simulation of the entire tournament bracket (Round of 16 to Final).

##  License

This project is open-source and available under the MIT License.
