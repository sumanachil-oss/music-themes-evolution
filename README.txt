# Thematic Evolution of Music (1950–2019)

**Course:** DVA — Data Visualization & Analytics  
**Dataset:** [Kaggle — Music Dataset (1950–2019)](https://www.kaggle.com/datasets/saurabhshahane/music-dataset-1950-to-2019)  
**Tableau Dashboard:** [View Interactive Dashboard](https://public.tableau.com/app/profile/sarah.friedrichs/viz/DVADashboardFinal/Dashboard1)

---

## Overview
This project analyzes **how lyrical themes in music have evolved from 1950 to 2019** using **machine learning** and **interactive data visualizations**.  
We examine **predefined theme scores** for each song (e.g., *love, heartbreak, politics, violence, social justice*) and predict **which decade** a song belongs to based on its thematic and musical features.

Through data-driven analysis, we uncover **cultural and societal shifts** reflected in music and provide tools for researchers, songwriters, and enthusiasts to explore thematic trends.

---

## Objectives
- Analyze **16 lyrical themes** across ~50,000 songs.
- Visualize how **themes rise and fall** over decades.
- Build **Random Forest** and **XGBoost** classifiers to predict the **song’s decade**.
- Use **Tableau dashboards** for interactive exploration of thematic and genre trends.
- Enable insights for **historians, sociologists, songwriters, and music fans**.

---

## Dataset
- **Source:** [Kaggle – Music Dataset (1950–2019)](https://www.kaggle.com/datasets/saurabhshahane/music-dataset-1950-to-2019)
- **Size:** ~50,000 songs
- **Features:**  
  - 16 lyrical **theme scores** (*love, violence, social justice, family, heartbreak, etc.*)
  - 6 musical attributes (tempo, danceability, energy, etc.)
  - Genre, artist, track name, release date

---

## Data Preprocessing
- Removed null values and grouped songs by **decade**.
- Balanced dataset via **downsampling** overrepresented decades.
- Created a **22-dimensional feature space**:
    - 16 theme scores  
    - 6 musical features
- Split into **train/test** sets.
- Scaled features and reduced dimensionality with **PCA** for visualization.

---

## Machine Learning Models

### 1. **Random Forest Classifier**
- Trained on 22 features → predicts song’s **release decade**.
- Hyperparameter tuning via **GridSearchCV**.
- Accuracy ≈ **39.0%** | Weighted F1 ≈ **38%**
- Visualized **feature importances** and **PCA clusters**.

### 2. **XGBoost Classifier**
- Same feature space, tuned parameters for boosting rounds, learning rate, and tree depth.
- Accuracy ≈ **39.4%** | Weighted F1 ≈ **38%**
- Slightly better recall on older decades (1960s–1970s).


---

## Visualizations & Dashboard

We created an **interactive Tableau dashboard** with multiple visualizations:

### **1. Theme Trends Over Time (Line Chart)**
- Visualizes how themes rise and fall between **1950 and 2019**.
- Interactive filtering by **genre, theme, and decade**.
- Example: *Violence* and *Obscene* themes steadily rise, while *Family/Gospel* declines.

### **2. Genre Evolution (Line Chart)**
- Shows changes in genre prevalence across decades.
- E.g., **Hip-Hop surged after the 2000s**, while older genres declined.

### **3. Correlation Heatmaps**
- Analyzes relationships between **themes within and across genres**.
- Interactive sliders to compare **different decades**.

### **4. Radar Charts**
- Shows the **distribution of lyrical themes** for a given song.
- Highlights dominant emotional patterns per track.

### **5. Decade Prediction Probabilities (Pie Charts)**
- Displays model confidence for each song’s predicted decade.
- Users can search for **specific songs**.

---

## Installation

### Option 1 — Use Google Colab *(Recommended)*
1. Open `musical_themes.ipynb` in **Google Colab**.
2. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn xgboost matplotlib seaborn
   ```
3. Upload `tcc_ceds_music.csv` into Colab.
4. Run all cells sequentially.

### Option 2 — Local Setup
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

---

## Execution Steps

### **A) Thematic Prediction Models**
```bash
# Open the notebook in Colab or Jupyter
musical_themes.ipynb
```
- Preprocess dataset.
- Train **Random Forest** and **XGBoost** models.
- Export PCA outputs and predictions → CSV → for Tableau.

### **B) Theme Correlation Analysis**
```bash
# Open the second notebook
correlation.ipynb
```
- Computes **per-genre correlations**.
- Outputs `theme_correlations.csv` and `theme_correlations_by_genre.csv`.

### **C) Tableau Visualization**
1. Import all CSV outputs into Tableau.
2. Open the [Tableau Dashboard](https://public.tableau.com/app/profile/sarah.friedrichs/viz/DVADashboardFinal/Dashboard1).
3. Explore **trends, correlations, and predictions** interactively.

---

##  Results
- **Violence & Obscene themes** ↑ since 1990s.
- **World/Life & Family/Gospel themes** ↓ after 1970s.
- Hip-Hop **dominates after 2000s**.
- Genres and themes **strongly correlate with societal trends**.

---

## Repository Structure
```
music-thematic-evolution/
├── notebooks/
│   ├── musical_themes.ipynb        # Train RF + XGBoost models
│   └── correlation.ipynb          # Generate correlations for Tableau
├── data/
│   ├── tcc_ceds_music.csv         # Kaggle dataset
│   ├── theme_correlations.csv     # Exported for Tableau
│   └── theme_correlations_by_genre.csv
├── reports/
│   └── Thematic_Music_Report.pdf
├── README.md
└── requirements.txt
```

---

##  References
- [Kaggle Dataset (1950–2019)](https://www.kaggle.com/datasets/saurabhshahane/music-dataset-1950-to-2019)
- Mauch et al. (2015): Evolution of Popular Music
- Kwon et al. (2021): Emotional Trends in Songs
- Bahuleyan (2018): Music Genre Classification  
*(See full reference list in project report.)*

