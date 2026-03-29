# Contributing to Chess Multiverse Opening Intelligence

First off, thank you for considering contributing to the Chess Multiverse Opening Intelligence Database! It's people like you that make open-source data science and the chess community so rewarding. 

This document provides guidelines and workflows for contributing to both the JSON dataset and the frontend application.

## Code of Conduct
By participating in this project, you agree to abide by our [Code of Conduct](CODE_OF_CONDUCT.md). Please read it to understand what actions will and will not be tolerated.

## How Can I Contribute?

### 1. Reporting Bugs & Data Anomalies
Since this project maps 15,013 chess openings, there is always room for statistical refinements or correcting ECO misclassifications. If you find an error:

* **Check existing issues:** Before creating a new issue, please check if the anomaly or bug has already been reported.
* **Open a new issue:** If the issue doesn't exist, open a new one. 
* **Provide context:** * If it's a data issue, include the `eco`, `opening` name, and the specific `moves` (UCI string) where the anomaly occurs.
  * If it's a UI/Application bug, include your browser, screen size, and steps to reproduce the visual error.

### 2. Suggesting Enhancements
We are always looking for ways to improve the "Intelligence Profile" metrics or the UI/UX of the application.

* Open an issue outlining your enhancement.
* Clearly describe how it benefits the end-user (e.g., "Adding a filter for specific pawn structures would help intermediate players study faster").

### 3. Submitting Pull Requests (Code & Data)
If you want to actively fix a bug or add a feature, we gladly accept Pull Requests (PRs).

1. **Fork the repository** to your own GitHub account.
2. **Clone the project** to your local machine.
3. **Create a branch** for your feature or fix:
   ```bash
   git checkout -b feature/YourFeatureName
   ```
   *Use `fix/BugName` for bug fixes and `data/EcoCorrection` for dataset tweaks.*

4. **Make your changes:**
   * If modifying `index.html`, ensure you don't break the "Native Theme Sync" CSS variables.
   * If proposing a dataset update, ensure the JSON schema strictly matches the existing format (integers for games, floats for rates).

5. **Commit your changes** with clear, descriptive commit messages:
   ```bash
   git commit -m "Add responsive grid layout to compare tray"
   ```

6. **Push to your branch:**
   ```bash
   git push origin feature/YourFeatureName
   ```

7. **Open a Pull Request** against the `main` branch of this repository. Include a detailed description of what your PR solves or adds.

## Local Development Setup

The frontend application requires zero build steps or server dependencies. 

1. Clone your fork of the repository.
2. Open `index.html` directly in any modern web browser.
3. To test dataset changes locally, modify the `initDb()` function in `index.html` to fetch your local `.json` file instead of the raw GitHub URL. 
   *(Note: You may need to run a simple local server like `python -m http.server` to avoid CORS issues when loading local JSON files).*

## Recognition
All accepted dataset corrections and significant UI contributions will be acknowledged in our release notes, and contributors are welcome to list their commits when referencing the dataset in academic or professional portfolios.

Thank you for helping us build better tools for the chess community!
