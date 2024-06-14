<h1 style="text-align: center;">Hello and Welcome, We're Munyaka's ERSP Group</h1> 

### Table of Content:
- [Title](https://github.com/Munyaka-ERSP/LDA_Analysis?tab=readme-ov-file#hello-and-welcome-were-ersp-munyakas-group)
- [Advisor](https://github.com/Munyaka-ERSP/LDA_Analysis?tab=readme-ov-file#advisor)
- [Our Team](https://github.com/Munyaka-ERSP/LDA_Analysis?tab=readme-ov-file#our-team-consists-of)
- [Research](https://github.com/Munyaka-ERSP/LDA_Analysis?tab=readme-ov-file#research)

### Advisor:
1. Dr. Imani Munyaka :email: imunyaka@ucsd.edu

### Our Team:
1. Andrew Smithwick  :email: asmithwick@ucsd.edu
1. Chuong Nguyen :email: chn021@ucsd.edu
1. Emily Gorial  :email: emgorial@ucsd.edu
1. Natasha Tran  :email: nmt003@ucsd.edu

### Research:

This code was utilized to filter the data of Reddit comments on the subreddits mentioned below in order to analyze the concerns of parents of children who play Roblox. This work was done by the aforementioned Early Research Scholars Program members under Professor Imani Munyaka (Uljima Security and Privacy Lab).

To obtain the dataset, we webscraped on three different subreddit sections:

- **r/robloxparents** 
- **r/parenting** on query Roblox
- **r/roblox** on query *parent OR safe OR concern OR danger OR scam AND (daughter OR niece OR nephew OR son OR child)*

## Folder structure

```bash
Parental_Concern_Of_Roblox_Project/
├── LDA_Code/
│   ├── Reddit_Webscraping.ipynb                 # Webscrapping Reddit on post related to Roblox
│   └── Topic_Generation.ipynb                   # LDA code to topic generation
├── LDA_Result/                             
│   ├── Generated_Topics/                        # Results from running LDA
│   │   ├── Topic1.csv                           
│   │   └── Topic2.csv
│   ├── Topic_Validation/                        # Running 9 topics to validate the Theme via manual comparisons
│   │   ├── Topic1.csv
│   │   ├── Topic2.csv
│   │   ├── Topic3.csv
│   │   ├── Topic4.csv
│   │   ├── Topic5.csv
│   │   ├── Topic6.csv
│   │   ├── Topic7.csv
│   │   ├── Topic8.csv
│   │   └── Topic9.csv
│   ├── Data.csv
│   ├── Lda_Tuning_Results.csv                  # Optimal Hyper-parameter for LDA 2 Topic Results
│   └── Topic_Mixture.csv
├── Survey_Question/                            # List of questions asked in the Survey
│   ├── RobloxSurvey-All.csv
│   └── RobloxSurvey-All.txt
├── Survey_Result/                              # Results getting from the Survey 
│   ├── Agree_Disagree_Statement_Result
│   │   ├── output.png
│   │   └── survey_Visualization.ipynb
│   ├── Common_Word_Response_Vis                # Words common in the responses for questions 131 and 151 of the Survey
│   │   ├── bigram_131.png
│   │   ├── most_common131.png
│   │   ├── most_common151.png
│   │   └── trigram_151.ipynb
│   └── RobloxSurvey                            # Sources provided by the people to solve the issues
│       └── Results.csv
├── Used_Dataset/                               # Result Dataset used for LDA Analysis. One of cumulative 5/6/7 was used to generate 2 topics
│   ├── cumulative_data_final.csv               # Same as finalCumulative.txt, but also includes user IDS
│   ├── cumulative5.csv
│   ├── cumulative6.csv
│   ├── cumulative7.csv                         
│   └── finalCumulative.txt                     # For topic validation
├── .Rhistory                             
├── Library_Installed_and_Version.md
└── LICENSE
```

### How to Run

#### Tutorials
- `https://www.youtube.com/playlist?list=PL2VXyKi-KpYttggRATQVmgFcQst3z6OlX`: playlist tutorials for LDA

#### Webscraping

Go to `LDA_Code/Redit_Webscraping.ipynb` to run a webscraping script to collect a dataset from Reddit. Uses the PRAW API
- `for post in reddit.subreddit("roblox").search(query = "parent OR safe OR concern OR danger OR scam AND (daughter OR son OR child)", limit=None):`
    - Changes what keywords the posts in the dataset must have. Here, the post must have one of the keywords separated by `OR`.

Docs:
[Github](https://github.com/praw-dev/praw)
[Docs](https://praw.readthedocs.io/en/stable/)

#### LDA

Go to `LDA_Code/Topic_Generation.ipynb` to run Latent Direlech Allocation on your datasets.
- Dataset file path must be adjusted here: `data = load_data('../Used_Dataset/DATASET_NAME.csv')['text']`. As of time of writing, it is `data = load_data('../Used_Dataset/finalCumulative.csv')['text']`
    - If you don't know about file paths, replace `DATASET_NAME` with your file name and upload your files to the `Used_Dataset` folder or look [here](https://www.pythoncheatsheet.org/cheatsheet/file-directory-path).
- There is a section called `FINE TUNING SECTION`. This part takes a long time to run. We generally comment it out if we don't need to find the best hyperparameters. 
    - Hyperparameters refer to the `alpha` or `eta` values found in the `gensim.models.LdaMulticore` file
    - That section will generate a `csv`

The notebook currently **can not** save to drive. If it is uploaded to Google Colab, [this link](https://colab.research.google.com/notebooks/io.ipynb) can help setup the rest of the code. Significant code edits may be required.

### Survey Visualizations
- Python Notebook found in `Survey_Result/Agree_Disagree_Statements_Result/surveyVisualizations.ipynb`
- `Survey_Result/Agree_Disagree_Statements_Result/output.png`: displaying percentage of parents agreeing or disagreeing to how Roblox is handling the issues: talking to strangers, scams, seeing inappropriate contents, excessive times online. 
- `Survey_Result/Common_Word_Response_Vis/bigrams_131.png`: top 10 most common two words phrase in parents response to question 131
- `Survey_Result/Common_Word_Response_Vis/most_common131.png`: top 10 most common two words phrase in parents response
to question 131
- `Survey_Result/Common_Word_Response_Vis/most_common151.png`: top 10 most common two words phrase in parents response to question 151
- `Survey_Result/Common_Word_Response_Vis/trigrams_151.png`: top 10 most common 3 words phrase in parents response to question 151


### Libraries and Versions:
---
##### LDA Script:
- Pandas 1.5.3
- Numpy 1.26.3
- Json 2.0.9
- NLTK (Natural Language Toolkit) 3.8.1
- Gensim 4.3.2
- Spacy 3.6.1
- PyLDAvis 3.4.0
- re (removing characters) 2.2.1
- *clean from cleantext*
- *from prompt_toolkit.completion import word_completer*
- *from pprint import pprint*
- *import matplotlib.pyplot as plt*
---

##### ERSP Webscraping:
- Praw 7.7.1
- Pandas 1.5.3
- csv 1.0
- *from datetime import datetime*
