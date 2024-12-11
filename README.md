# WordleBot: A Q-Learning-Based Wordle Solver

**WordleBot** is an AI-driven solver for the popular word-guessing game, *Wordle*. This repository contains code that integrates concepts from Q-learning, spectral clustering, and similarity-based filtering of candidate words to make strategic guesses and improve performance over time. Using a training loop, the bot learns which clusters of words to focus on, thereby refining its decision-making with repeated gameplay.

## Key Features

1. **WordGraph**  
   - Maintains a pool of possible words and calculates a similarity graph between them.  
   - Similarity scores are based on matched positions and shared letters.  
   - As guesses are made and feedback is received, the WordGraph filters out invalid words, narrowing down the candidate pool.

2. **Spectral Clustering**  
   - Groups words into clusters according to their similarity scores, helping the bot focus its guesses on specific “neighborhoods” of similar words.  
   - The cluster centroids are used as strategic guesses to cover maximal ground efficiently.

3. **Q-Learning (QLearner)**  
   - Employs Q-learning to determine which clusters to guess from.  
   - **State**: The distribution of words across clusters.  
   - **Action**: Selecting a cluster from which to guess.  
   - **Reward**: Derived from feedback on how close the guess is to the target word.

4. **Grader**  
   - Simulates Wordle’s feedback: correct letters in correct positions, correct letters in wrong positions, and letters not in the word.  
   - Integral to the feedback loop that informs the QLearner and WordGraph.

5. **Training (Trainer)**  
   - Automates running multiple games for training.  
   - Collects performance metrics and prints results (average attempts, best/worst performance).  
   - Facilitates hyperparameter tuning (cluster_count, alpha, gamma, exploration rates).

6. **Visualization & Reporting**  
   - Provides plotting functions to visualize performance over training sessions.  
   - Offers performance metrics to track learning progression over time.

## Project Structure

- **`WordGraph`**: Manages words, calculates similarities, and filters based on feedback.
- **`SpectralClusterer`**: Clusters words using their similarity graph and identifies cluster centroids.
- **`QLearner`**: Implements Q-learning logic for selecting clusters.
- **`Grader`**: Provides Wordle-like feedback evaluation.
- **`WordleBot`**: Integrates all components to play the game end-to-end.
- **`Trainer`**: Runs multiple games, trains the bot, and records performance.
- **Utility Functions** (e.g., `run_training_with_parameters`, `plot_performance`, `report_training_performance`): Streamline experimentation, reporting, and visualization.

## Getting Started

### Prerequisites
- Python 3.7+  
- Install required packages:
  ```bash
  pip install numpy scipy scikit-learn matplotlib
