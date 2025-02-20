# PTO: Preference Tree Optimization Framework

## Overview

This repository contains the implementation of the **Preference Tree Optimization (PTO)** framework, designed to enhance goal-oriented dialogue systems using **look-ahead simulations**. PTO is particularly applied to **Motivational Interviewing (MI)**, a counseling technique aimed at facilitating behavioral change.

The framework iteratively improves a dialogue agent by generating **preference data** using **Preference Trees with Look-Ahead** and optimizing the model with **Direct Preference Optimization (DPO)**. The repository includes scripts for data generation, evaluation, and model training.

## Repository Structure

```
├── README.md                      # Project documentation
├── LICENSE                         # License file (MIT License)
├── PTO_PrefData_and_Eval.ipynb     # Generate preference data & evaluate the model
├── Train_model_pref_tree.ipynb     # Train the model using preference data & DPO
├── questionnaires.py               # Defines evaluation questionnaires
├── system_prompts_builder.py       # Generates system prompts for virtual patients & therapists
```

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/pto-framework.git
   cd pto-framework
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
   *(Ensure that dependencies like `transformers`, `trl`, `peft`, `bitsandbytes`, `torch`, and `datasets` are installed.)*

## Usage

### Step 1: Generate Preference Data & Evaluate the Model
Run the **PTO_PrefData_and_Eval.ipynb** notebook to:
- Generate **preference data** using **Preference Trees with Look-Ahead**.
- Evaluate the **current agent model** using virtual patients and an oracle evaluator.

### Step 2: Train the Model with DPO
Run the **Train_model_pref_tree.ipynb** notebook to:
- Load the current agent model.
- Train the model using **Direct Preference Optimization (DPO)** with the generated preference data.

### Customizing Training Parameters
Modify the **look-ahead depth**, **training hyperparameters**, and **model configurations** inside `Train_model_pref_tree.ipynb` as needed.

## How PTO Works
1. **Preference Data Generation**:
   - The agent model interacts with **virtual patients** based on predefined system prompts.
   - Multiple **look-ahead steps** simulate potential conversation paths.
   - An **oracle evaluator** ranks responses based on adherence to MI principles.
   - Preference pairs (best vs. worst responses) are extracted and stored.

2. **Training the Model**:
   - The model is trained using **Direct Preference Optimization (DPO)**.
   - Training iterates over preference data to improve **long-term conversational planning**.
   - The updated model is then used in the next iteration of data generation and evaluation.

## Contributors
- **Lior Baruch** (Lead Developer & Researcher)
- [Your Name] *(Add additional contributors if applicable)*

## License
This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

## Future Work
- Implement **additional training algorithms** (PPO, KTO).
- Extend the framework to other **goal-oriented dialogue domains**.
- Improve **oracle evaluation** for better response ranking.

## Citation
If you use this framework in your research, please cite:

```
@inproceedings{baruch2025pto,
  title={Preference Tree Optimization: Enhancing Goal-Oriented Dialogue with Look-Ahead Simulations},
  author={Lior Baruch and Moshe Butman and Kfir Bar and Doron Friedman},
  booktitle={International Conference on Learning Representations (ICLR)},
  year={2025}
}
```

## Contact
For questions or collaborations, feel free to open an issue or reach out to [your email or GitHub profile].

