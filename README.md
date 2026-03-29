# Chess Multiverse Opening Intelligence Database (20M Lichess Subset)

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX) 

## 🚀 Live Interactive Tool
Explore the dataset visually without writing any code. The full 20M+ game database powers the **Opening Analytics Module** on the Chess Multiverse platform:
👉 **[Launch the Opening Intelligence Platform](https://www.chessmultiverse.org/p/opening-analytics.html)**

## 📊 Dataset Overview
The **Chess Multiverse Opening Intelligence Database** is a high-fidelity, open-source dataset containing statistical performance metrics for **15,013 distinct chess opening lines**. 

The data was extracted, filtered, and processed from a subset of **20 million standard-rated games** played on Lichess during the 2024 calendar year. Processed by Chess Multiverse Lab v1.1 (Stable), this dataset strips out engine evaluation noise to focus exclusively on human-vs-human practical outcomes across various ELO brackets.

## 📁 File Specifications
* **Filename:** `openings_2024_12_depth5_20M.json`
* **Format:** JSON (Array of Objects)
* **Record Count:** 15,013
* **Data Vintage:** 2024

## 🗄️ Data Schema (Data Dictionary)
Each object in the JSON array represents a specific opening sequence and contains the following key-value pairs:

| Key | Data Type | Description | Example |
| :--- | :--- | :--- | :--- |
| `eco` | String | The standard Encyclopedia of Chess Openings (ECO) code. | `"C44"` |
| `opening` | String | The standardized, formal name and variation of the opening. | `"Scotch Game: Lolli Variation"` |
| `moves` | String | The sequence of moves leading to the position, formatted in Universal Chess Interface (UCI) notation. | `"e2e4 e7e5 g1f3 b8c6 d2d4 e5d4..."` |
| `games` | Integer | The total number of games in the 20M subset that reached this exact position. | `22326` |
| `white_win_rate` | Float | The percentage of games won by White (expressed from 0.0 to 1.0). | `0.527` |
| `black_win_rate` | Float | The percentage of games won by Black (expressed from 0.0 to 1.0). | `0.422` |
| `draw_rate` | Float | The percentage of games that ended in a draw (expressed from 0.0 to 1.0). | `0.051` |
| `avg_rating` | Integer | The average ELO rating of the players who reached this position. | `1507` |

## 📄 Sample Data
Below is a brief sample of the JSON structure demonstrating how the data is natively formatted:

```json
[
  {
    "eco": "C44",
    "opening": "Scotch Game: Lolli Variation",
    "moves": "e2e4 e7e5 g1f3 b8c6 d2d4 e5d4 f3d4 c6d4 d1d4 d7d6",
    "games": 22326,
    "white_win_rate": 0.527,
    "black_win_rate": 0.422,
    "draw_rate": 0.051,
    "avg_rating": 1507
  },
  {
    "eco": "B32",
    "opening": "Sicilian Defense: Löwenthal Variation",
    "moves": "e2e4 c7c5 g1f3 b8c6 d2d4 c5d4 f3d4 e7e5 d4c6 b7c6",
    "games": 17417,
    "white_win_rate": 0.476,
    "black_win_rate": 0.482,
    "draw_rate": 0.042,
    "avg_rating": 1746
  }
]
```

---
## 🧪 Methodology & Processing
To ensure the highest level of statistical integrity for academic and analytical use:
1. **Game Selection:** Only standard-rated, human-vs-human Lichess games were included. Bullet, hyper-bullet, and variant games were excluded to maintain opening phase validity.
2. **Depth Parsing:** Opening lines were mapped up to an average depth of 5 full moves (10 ply), capturing key middle-game transitions.
3. **Statistical Aggregation:** Win/loss/draw rates are strictly empirical, reflecting the *practical edge* in human play rather than perfect engine evaluations.

## 💻 Usage & Implementation
This JSON dataset is lightweight and structured for immediate parsing in standard data science pipelines.

**Python Example (Pandas):**
```python
import pandas as pd
import json

# Load the dataset
with open('openings_2024_12_depth5_20M.json', 'r') as file:
    data = json.load(file)

# Convert to DataFrame
df = pd.DataFrame(data)

# Find the highest winning openings for Black with at least 5,000 games played
solid_black_lines = df[(df['games'] >= 5000)].sort_values(by='black_win_rate', ascending=False)
print(solid_black_lines.head())
```

## 🤝 Contributing
Contributions to improve the dataset, refine parsing algorithms, or build new UI modules are welcome!
* Fork the repository.
* Create your feature branch (`git checkout -b feature/DataRefinement`).
* Commit your changes (`git commit -m 'Add specific refinement'`).
* Push to the branch (`git push origin feature/DataRefinement`).
* Open a Pull Request.

If you spot a statistical anomaly or an incorrect ECO classification, please open an Issue with the relevant UCI string.

## 📝 Citation & Academic Use
If you use this dataset in data science projects, chess engine development, or statistical research, please cite it using the following DOI:

**APA Format:**
> Varshney, S. (2026). *Chess Multiverse Opening Intelligence Database (20M Lichess subset)* [Data set]. Zenodo. https://doi.org/10.5281/zenodo.XXXXXXX

**BibTeX:**
```bibtex
@dataset{varshney_2026_chess_db,
  author       = {Varshney, Sparsh},
  title        = {Chess Multiverse Opening Intelligence Database (20M Lichess subset)},
  month        = {March},
  year         = {2026},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.XXXXXXX},
  url          = {[https://doi.org/10.5281/zenodo.XXXXXXX](https://doi.org/10.5281/zenodo.XXXXXXX)}
}
```

## 👨‍🔬 Lead Researcher & Principal Developer
**Sparsh Varshney** *Founder • Data Scientist • Researcher*

Sparsh is a medical researcher and open-source data scientist currently pursuing a Bachelor of Ayurvedic Medicine and Surgery (BAMS) at Uttarakhand Ayurved University. By bridging rigorous academic research methodologies with modern web development and AI, Sparsh builds high-fidelity datasets and analytical tools. He is the founder of **Chess Multiverse** and **Amidha Ayurveda**, developing specialized data platforms across multiple disciplines.

* [About the Creator](https://www.chessmultiverse.org/p/about.html)
* [LinkedIn](https://linkedin.com/in/sparshvarshney)
* [ORCID](https://orcid.org/0009-0004-7835-0673)
* [GitHub](https://github.com/sciencewithsaucee-sudo)
## ⚖️ License
This dataset is published under the [Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/) license. You are free to share and adapt the material for any purpose, even commercially, provided you give appropriate credit and distribute your contributions under the same license.
