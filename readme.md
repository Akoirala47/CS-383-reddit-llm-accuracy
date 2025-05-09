# LLM Reddit Advice Evaluation - ROUGE Score Analysis

## Project Overview

This project evaluates the lexical similarity of advice generated by OpenAI's `gpt-4o-mini` model compared to human-written responses from Reddit's r/Advice. The evaluation uses ROUGE (Recall-Oriented Understudy for Gisting Evaluation) scores to quantitatively measure the overlap in wording and phrasing between AI-generated advice and human advice for the same situations.

This work was conducted by Aayush Koirala and Sage Arias Hambleton.

## Features

*   Processes Reddit advice questions (prompts) and corresponding human suggestions from a CSV dataset.
*   Generates advice using OpenAI's `gpt-4o-mini` model via API calls.
*   Calculates ROUGE-1, ROUGE-2, and ROUGE-L F1-scores to compare AI and human responses.
*   Exports detailed results (prompts, human advice, AI advice, ROUGE scores) to a CSV file for further analysis.
*   Displays average ROUGE scores for all successfully processed prompts.

## Requirements

The following Python packages are required:
*   `pandas`
*   `openai`
*   `rouge-score`
*   `tqdm`

## Setup

1.  **Clone the Repository (if applicable):**
    ```bash
    # Example: git clone <your-repository-url>
    # cd <your-repository-name>
    ```

2.  **Install Required Packages:**
    ```bash
    pip install pandas openai rouge-score tqdm
    ```
    *(Note: If using a Jupyter Notebook environment, you can run `!pip install ...` in a cell).*

3.  **Prepare Your Dataset:**
    *   Ensure you have a CSV file (e.g., `reddit_advice_dataset.csv`) in the project directory. The evaluation notebook used 224 prompts from this file.
    *   The CSV file must contain columns for:
        *   The user's prompt/question (the notebook used a column named `question`).
        *   The human-written advice/suggestion (the notebook used a column named `suggestion`).
    *   If your column names or file path differ, update the corresponding variables (`CSV_FILE_PATH`, `PROMPT_COLUMN_NAME`, `HUMAN_ADVICE_COLUMN_NAME`) in the notebook's configuration section.

4.  **Set Up OpenAI API Credentials:**
    *   Obtain an API key from [OpenAI](https://platform.openai.com/).
    *   In the Jupyter Notebook (`.ipynb` file), locate the API key setup section (typically Cell 1).
    *   Replace the placeholder `api_key_value` with your actual OpenAI API key:
        ```python
        api_key_value = "YOUR_OPENAI_API_KEY_HERE"
        ```
    *   Optionally, add your `OPENAI_ORG_ID` and `OPENAI_PROJECT_ID` if required for your account setup.
    *   **Security Note:** Be cautious about hardcoding API keys directly in notebooks, especially if sharing. Consider using environment variables or a `.env` file for more secure key management.

## Usage (via Jupyter Notebook)

1.  Open the Jupyter Notebook file provided in this repository.
2.  Ensure your dataset CSV is correctly placed and paths/column names are configured as described in Setup.
3.  Verify your OpenAI API key is correctly set in the notebook.
4.  Run the notebook cells sequentially.
5.  The script will:
    *   Load the dataset (e.g., 224 prompts).
    *   Iterate through each prompt, generating a response from `gpt-4o-mini`.
    *   Calculate ROUGE-1, ROUGE-2, and ROUGE-L F1-scores by comparing the AI's advice against the human advice.
    *   Save all prompts, human advice, AI advice, and detailed ROUGE scores to a CSV file (default: `reddit_advice_chatgpt_rouge_scores_notebook.csv`).
    *   Display the average ROUGE F1-scores for successfully processed prompts in the notebook output.

## Configuration Options (in the Notebook)

You can customize the following parameters directly in the notebook's configuration section:

*   `api_key_value`: Your OpenAI API key.
*   `org_id_value`: (Optional) Your OpenAI Organization ID.
*   `project_id_value`: (Optional) Your OpenAI Project ID.
*   `CSV_FILE_PATH`: Path to your input dataset (e.g., `'reddit_advice_dataset.csv'`).
*   `OUTPUT_CSV_FILE_PATH`: Path where the results CSV will be saved.
*   `PROMPT_COLUMN_NAME`: Column name for questions/prompts in your input CSV (e.g., `'question'`).
*   `HUMAN_ADVICE_COLUMN_NAME`: Column name for human advice/suggestions in your input CSV (e.g., `'suggestion'`).
*   `OPENAI_MODEL`: The OpenAI model to use (configured as `"gpt-4o-mini"` in the notebook).
*   `MAX_TOKENS_RESPONSE`: Maximum length of generated AI responses (configured as `250` in the notebook).
*   `TEMPERATURE`: Controls the randomness of the AI's responses (configured as `0.7` in the notebook).

## Output

The primary output is a CSV file (default: `reddit_advice_chatgpt_rouge_scores_notebook.csv`) containing:

*   `prompt`: The original prompt from Reddit.
*   `human_advice`: The human-written advice from Reddit.
*   `chatgpt_advice`: The advice generated by `gpt-4o-mini`.
*   `rouge1_f`: ROUGE-1 F1-score.
*   `rouge1_p`: ROUGE-1 Precision.
*   `rouge1_r`: ROUGE-1 Recall.
*   `rouge2_f`: ROUGE-2 F1-score.
*   `rougeL_f`: ROUGE-L F1-score.

Additionally, average ROUGE F1-scores are printed to the notebook's output console.

## Summary of Findings (ROUGE Evaluation for `gpt-4o-mini`)

The evaluation of `gpt-4o-mini` responses against human advice using ROUGE metrics on 224 prompts yielded the following average F1-scores:

*   **ROUGE-1 (Unigram Overlap): 0.1849**
*   **ROUGE-2 (Bigram Overlap): 0.0249**
*   **ROUGE-L (Longest Common Subsequence): 0.0975**

These scores indicate that while `gpt-4o-mini` shared some individual vocabulary with human responses (as shown by ROUGE-1), it rarely used the same specific two-word phrases (ROUGE-2) or longer common sentence structures (ROUGE-L). This suggests that the model prioritizes generating fluent and contextually relevant advice through paraphrasing and novel sentence construction rather than by closely mimicking the lexical patterns of the reference human advice.

## Contributors

*   **Aayush Koirala:** ROUGE evaluation implementation, script adaptation, data processing for this analysis.
*   **Sage Arias Hambleton:** ROUGE metric idea formulation, analysis of ROUGE results, report compilation related to this evaluation.
