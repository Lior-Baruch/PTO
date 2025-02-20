# PTO: Preference Tree Optimization Framework

## Overview

The **Preference Tree Optimization (PTO)** framework is a general approach designed to enhance goal-oriented dialogue systems. Although PTO can be applied to a variety of dialogue domains, this repository demonstrates its use in **Motivational Interviewing (MI)**—a counseling technique aimed at facilitating behavioral change.

PTO iteratively improves a dialogue agent by:
- **Generating Preference Data:** Using Preference Trees with Look-Ahead, the system simulates multiple conversation paths with virtual users.
- **Evaluating Responses:** An oracle evaluator assesses and ranks responses based on adherence to desired dialogue principles.
- **Optimizing the Model:** The agent is trained using **Direct Preference Optimization (DPO)** on the generated preference data.

Leveraging an oracle and virtual users, the PTO framework can be adapted to many goal-oriented dialogue tasks.

## Repository Structure

```
├── README.md                      # Project documentation
├── LICENSE                        # License file (MIT License)
├── PTO_PrefData_and_Eval.ipynb      # Generates preference data & evaluates the model
├── Train_model_pref_tree.ipynb      # Trains the model using preference data & DPO
├── questionnaires.py              # Defines evaluation questionnaires
├── system_prompts_builder.py      # Generates system prompts for virtual patients & therapists
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
- Evaluate the **current agent model** using virtual users and an oracle evaluator.

**Note:** The **look-ahead depth** is determined during the preference data generation process and is not configurable during model training.

### Step 2: Train the Model with DPO
Run the **Train_model_pref_tree.ipynb** notebook to:
- Load the current agent model.
- Train the model using **Direct Preference Optimization (DPO)** with the generated preference data.
- Fine-tune training hyperparameters (e.g., batch sizes, learning rate, gradient accumulation) and model configurations (e.g., LoRA parameters, quantization settings).

## How PTO Works

1. **Preference Data Generation**:
   - The agent model interacts with virtual users based on predefined system prompts.
   - Multiple **look-ahead steps** simulate potential conversation paths.
   - An **oracle evaluator** ranks responses based on adherence to desired dialogue principles.
   - Preference pairs (best vs. worst responses) are extracted and stored.

2. **Training the Model**:
   - The model is optimized using **Direct Preference Optimization (DPO)**.
   - Iterative training on the preference data improves the agent’s long-term conversational planning.
   - The updated model is then used for further data generation and evaluation, creating a continuous improvement loop.

## Customizing Training Parameters

While the **look-ahead depth** is established during **preference data generation**, you can adjust other training parameters within the `Train_model_pref_tree.ipynb` notebook:
- **Training hyperparameters:** Batch sizes, learning rate, gradient accumulation steps, evaluation strategies, etc.
- **Model configurations:** LoRA settings, quantization configurations, and additional training options.
- **Evaluation parameters:** Dataset splits, scoring thresholds, etc.

## Contributors

This work was developed under the guidance and supervision of my thesis advisors and supervisors:
- **Lior Baruch** (Lead Developer & Researcher)
- **Doron Friedman**
- **Moshe Butman**
- **Kfir Bar**


## License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

## Future Work

- Implement additional training algorithms (e.g., PPO, KTO).
- Extend the framework to other goal-oriented dialogue domains.
- Enhance oracle evaluation for improved response ranking.

## Citation

If you use this framework in your research, please cite it as follows (note that this work is not yet published):

```
@inproceedings{baruch2025pto,
  title={Preference Tree Optimization: Enhancing Goal-Oriented Dialogue with Look-Ahead Simulations},
  author={Lior Baruch and Moshe Butman and Kfir Bar and Doron Friedman},
  note={Manuscript under review}
}
```

## Contact

For questions or collaborations, feel free to open an issue or reach out via Lior95Bar@Gmail.com

