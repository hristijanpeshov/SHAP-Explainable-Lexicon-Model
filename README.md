# SHAP-Explainable-Lexicon-Model


# Overview



# Installation
The code is available as Jupyter notebooks. The easiest way to use the notebooks is to upload them to and run them in Google Colab. The notebooks contain imports of the necessary Python libraries. There are no dependencies and no additional modules or libraries need to be installed.

# Data
We are using several datasets to evaluate the proposed methodology. Access to the datasets is available through the links shown below.

Nasdaq (Version 2)
 - https://www.kaggle.com/datasets/sidarcidiacono/news-sentiment-analysis-for-stock-data-by-company

Financial phrase bank (Version 5)
 - https://www.kaggle.com/datasets/ankurzing/sentiment-analysis-for-financial-news?select=all-data.csv
 
Sentfin (Version 3)
 - https://www.kaggle.com/datasets/ankurzing/aspect-based-sentiment-analysis-for-financial-news
  
train_df

dev_df

FIQA (train)
 - https://sites.google.com/view/fiqa/

Financial Phrase Bank + FIQA (Version 4)
 - https://www.kaggle.com/datasets/sbhatti/financial-sentiment-analysis
  
Loughran McDonald Dictionary
 - https://sraf.nd.edu/loughranmcdonald-master-dictionary/
  

# Instructions
There are total of 7 Colab notebooks used to generate the results. Each of the notebooks process the datasets in a specific way, which results in SHAP explainable lexicon. 

In each of the notebooks, the 'User Input' section should be filled with the required information. Please follow the instructions in the notebooks. 
After the necessary information in the 'User Input' section is provided, the notebook can be run with the 'Run All' option.

To reproduce the results from the paper, please follow the notebooks execution order.

1. datasets_processing.ipynb
    - Before processing the datasets, we are making sure that there aren't overlaps between them. This help us to avoid creating biased results. 
    - This notebook modifies the provided datasets and divides them into two categories: source and evaluation datasets
      - The source datasets are utilized for extracting words and creating the SHAP explainable lexicon
      - The evaluation datasets are used to evaluate the created SHAP explainable lexicons

2. roberta_model_creation.ipynb
    - This notebook requires GPU
    - This notebook results with RoBERTa sentiment classification model and RoBERTa tokenizer
  
3. initial_words_collecting.ipynb
    - This notebook requires GPU
    - Extraction of words from the sentences together with their shap value
    - The runtime might disconnect while running this notebook. This is due to the long sentences processing time. To not lose the progress, we are saving the datasets on each 100 sentences to the provided location
    - If the runtime disconnects, please run again the notebook with the same configuration. Repeat this process until all sentences are processed.
    - If all sentences are processed, you will get a message that informs you of that

4. concatenate_result_datasets.ipynb
    - This notebook serve to combine multiple outputs from the notebook #3
    - If all sentences were processed in notebook #3 with only one execution, then this the execution of this notebook is not required

5. post_processing_of_the_words.ipynb
    - This notebook aggregates the extracted words, adds features, and prepare them, together with LM words, for the SHAP-LM explainable lexicon creation
  
6. explainable_lexicon_development.ipynb
    - In this notebook the SHAP-LM explainable lexicon is generated
    - The lexicon is also generated in a normalized version
  
7. model_evaluation_summary.ipynb
    - Finally, the last notebook evaluates the SHAP-LM explainable lexicon by using the evaluation datasets from notebook #1
    - The results that SHAP-LM explainable lexicon achieves are generated using this notebook
