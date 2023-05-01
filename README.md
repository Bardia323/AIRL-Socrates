# AIRL: AI-aligned Reinforcement Learning and Dialogue Generation

This project aims to create an AI model capable of emulating Socrates' character from Plato's works using AI-aligned Reinforcement Learning (AIRL) and pre-trained generative models. We combine Low Rank Adaptation (LoRA) and GPT-Neo-1.3B to generate realistic dialogue in virtual environments with predefined characters. The PPO-trained LoRA model generates more concise and coherent responses, but further training and refinements are needed for improved alignment with Socrates' character.
![Socrates inside AI](https://cdn.discordapp.com/attachments/979273847931027456/1102442665334808616/Bardia323_socrates_inside_an_artificial_neural_network_c65ea162-af37-4e03-967e-908bf397276a.png "Socrates inside AI. Generated with Midjourney")

## Installation and Usage
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/15XPnrFpi15Y2d3xGKba-K5qoYKkTfyfO#scrollTo=jVy3QV0vo148)
### Training

1. Download the files in `./TrainingData/` and upload them to your Google Colab runtime.
2. Input your OpenAI API token in the appropriate cell.
3. Run the training cells as instructed in the code.

### Testing

1. Run the install and import dependency cells.
2. Provide your OpenAI API token in the appropriate cell.
3. Run the testing cells as instructed in the code.

## Methodology

Our approach consists of the following steps:

1. Fine-tuning: Fine-tune a LoRA of GPT-Neo-1.3B on a manually cleaned dataset of Plato's dialogues featuring Socrates. Custom callbacks are implemented for version control and LoRA model saving.

2. Pipeline Evaluator: Construct a pipeline evaluator using OpenAI's gpt-3.5-turbo chat model as a reward function. This model evaluates responses and generates positive or negative sentiment after reasoning. A sentiment classification model translates these outputs into scalar values of 1.0, 0.0, or -1.0.

3. Reinforcement Learning: Employ the TRL library to train a new LoRA based on a hybrid dataset, comprising both pre-generated synthetic responses and online results from the pipeline evaluator. Various strategies are explored, including single and multiple evaluators, as well as different evaluation criteria.

4. Model Adaptation: The LoRA method enables efficient switching of attention layers depending on the desired character generation, allowing us to effectively store the writing style or "personality" of Socrates in a compact 13MB format.

## Testing the Model

The testing phase involves generating responses for a set of predefined prompts using the trained model. A custom stopping criteria is used in the generator pipeline to ensure that the generated text remains coherent and concise.

## Future Work

Further refinements and training are needed to improve alignment with Socrates' character. This project serves as a foundation for the development of advanced conversational AI systems using reinforcement learning techniques.
