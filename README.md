# Moosic-playlist-clustering

# Moosic: Automated Playlist Creation with Machine Learning

## 🎵 Project Overview
Moosic is a music start-up that curates high-quality playlists with a distinct personal touch and "mood." As the company scales up rapidly, human music experts face bottlenecks in creating new content. 

This project builds an initial data science prototype using **Unsupervised Machine Learning (UML)** to automate playlist generation. By evaluating the structural and mechanical properties of thousands of tracks retrieved from the Spotify API, the algorithm automatically groups similar tracks into cohesive mood-based playlists.

## 🛠️ Tech Stack & Workflow
- **Environment:** Google Colab
- **Core Libraries:** `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`, `ydata-profiling`
- **Workflow Steps:**
  1. **Data Cleaning & Quality Assessment:** Leveraged `ydata-profiling` to evaluate data distribution, remove metadata noise (IDs, URLs), and handle missing values.
  2. **Feature Engineering & Scaling:** Utilized `MinMaxScaler` to normalize highly sensitive numerical scales (e.g., squishing `tempo` and `duration_ms` between 0 and 1).
  3. **Dimensionality Reduction (PCA):** Implemented Principal Component Analysis, optimizing up to 7 components to retain **95% of the original variance** while filtering out noise.
  4. **Clustering Optimization:** Executed a hyperparameter tuning loop using the **Elbow Method (Inertia)** and **Silhouette Coefficients** combined with strict business contexts to lock in the ideal number of playlists.
  5. **Cluster Evaluation:** Grouped and evaluated the statistical averages (`mean` and `std`) of the resulting playlists.

## 📊 Core Presentation Insights

### 1. Are Spotify's audio features able to capture humanly detectable criteria?
**Partially.** The algorithm excels at grouping tracks based on **structural and kinetic mood intensity** (speed, raw energy, volume compression) rather than cultural or historical genre boundaries. 
- *Example:* The algorithm successfully isolated a **"High-Intensity"** cluster containing fast, aggressive underground death metal tracks mixed alongside high-energy electronic house tracks. Sonically, they share identical profiles, even though humans separate the genres.

### 2. Is K-Means an effective method for Moosic moving forward?
K-Means served as an exceptional initial prototyping tool due to its **guaranteed convergence**, speed, and mathematical transparency. However, moving forward, we recommend moving toward **Semi-Supervised Learning** models to inject explicit genre tags alongside the numerical profiles to prevent cross-genre friction for users.

## 🚀 Future Roadmap
1. **Keep Experts in the Loop:** Use K-Means outputs as "rough drafts" for specialists to refine and name.
2. **Add Richer Context:** Incorporate release years, languages, and lyric themes to capture deep emotional nuance.
3. **Listen to Listeners:** Integrate user behavioral feedback loops (skips, saves, likes) to actively adjust cluster shapes.
