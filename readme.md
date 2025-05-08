
# Reddit Advice Evaluation

## Project Overview
This project evaluates ChatGPT's ability to provide advice compared to human responses from Reddit. The evaluation uses ROUGE scores to quantitatively measure the similarity between AI-generated advice and human advice for the same situations.

## Features
- Processes Reddit advice questions and corresponding human suggestions
- Generates advice using OpenAI's GPT models (currently configured with gpt-4o-mini)
- Calculates ROUGE-1, ROUGE-2, and ROUGE-L scores to compare AI and human responses
- Exports results to CSV for further analysis
- Displays average ROUGE scores for processed prompts

## Requirements
The following Python packages are required:
- pandas
- openai
- rouge-score
- tqdm

## Setup
1. Install the required packages:
   ```
   pip install pandas openai rouge-score tqdm
   ```

2. Prepare your dataset:
   - Ensure you have a CSV file named reddit_advice_dataset.csv in the project directory
   - The CSV should contain columns for questions/prompts and human suggestions/advice
   - Update the column names in the configuration section if needed

3. Set up your OpenAI API credentials:
   - Obtain an API key from [OpenAI](https://platform.openai.com/api-keys)
   - Add your API key to the notebook in the appropriate variable
   - If you have an organization ID, add it as well

## Usage
1. Run the notebook cells in order
2. The script will:
   - Load the dataset
   - Generate ChatGPT responses for each prompt
   - Calculate ROUGE scores between AI and human responses
   - Save all results to reddit_advice_chatgpt_rouge_scores_notebook.csv
   - Display average ROUGE scores

## Configuration Options
You can customize the following parameters in the notebook:
- `OPENAI_MODEL`: The OpenAI model to use (default: "gpt-4o-mini")
- `MAX_TOKENS_RESPONSE`: Maximum length of generated responses (default: 250)
- `TEMPERATURE`: Randomness of responses (default: 0.7)
- `CSV_FILE_PATH`: Path to your input dataset
- `OUTPUT_CSV_FILE_PATH`: Where to save results
- `PROMPT_COLUMN_NAME`: Column name for questions in your CSV
- `HUMAN_ADVICE_COLUMN_NAME`: Column name for human advice in your CSV

## Output
The output CSV file contains:
- Original prompts
- Human advice
- ChatGPT advice
- ROUGE-1 F1, precision, and recall scores
- ROUGE-2 F1 scores
- ROUGE-L F1 scores

