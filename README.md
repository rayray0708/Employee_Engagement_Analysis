# Employee_Engagement_Analysis
![Employee Engagement](https://corp.smartbrief.com/wp-content/uploads/2023/02/GettyImages-1416315615-726x420.jpg)

## Introduction
In this project, I'll analyse a dataset derived from an employee survey conducted at Company X. Specifically, I would like to gain insights into how to improve employee engagement to enhance business performance. 

Employee engagement encompasses the emotional commitment employees have towards their work and organization, going beyond mere job satisfaction to include a sense of purpose and dedication. Its impact on business performance is profound. Engaged employees exhibit higher levels of productivity, innovation, and overall job performance. They actively contribute to achieving organizational objectives, fostering a positive workplace culture, and reducing turnover rates. Conversely, disengaged employees may display decreased productivity and commitment. Cultivating a work environment that prioritizes employee engagement not only reduces recruitment costs but also enhances creativity and problem-solving abilities, giving businesses a competitive edge in the marketplace. 

## Instructions
To see the code for this project, please navigate to `emp_engagement.ipynb`. The lab report summarising the obtained results can be found in `Improving Employee Engagement for Enhance Business Performance`. Please click on the lab report and click `View raw`, the report should be automatically downloaded to your local machine. 

Within the `Resources` folder, you will find the original dataset. Additionally, you will find the actual research papers I referenced in the lab report within the `Research` folder. 

## Installations
The following dependencies have been used for this project. Please copy the following code as is to your code editor:
`import pandas as pd`\
`from pathlib import Path`\
`import matplotlib.pyplot as plt`\
`import numpy as np`\
`import seaborn as sns`\
`import re`\
`import nltk`\
`from scipy.stats import pearsonr`\
`from nltk.corpus import stopwords`\
`from scipy.stats import ttest_ind`\
`from wordcloud import WordCloud`\
`from nltk.tokenize import word_tokenize`\
`from nltk.probability import FreqDist`\
`from itertools import chain`\
`from sklearn.feature_extraction.text import CountVectorizer`\
`from sklearn.decomposition import LatentDirichletAllocation`

Please ensure you have the following libraries pre-installed:
1) `!pip install openpyxl`
2) `pip install seaborn`
3) `pip install wordcloud`
4) `pip install nltk`
5) `pip install scikit-learn`
6) `pip install pandas`
7) `pip install matplotlib`
8) `pip install numpy`
10) `pip install scipy`

## Data cleaning
The original dataset contains the following information:
![Alt text](<Screenshot 2024-01-10 at 8.50.05 pm.png>)

Given that responses marked as 98 and 99 signify Uncertain/Not Applicable responses, I propose adopting Method #1 to treat them as a distinct category (coded as 0). This approach enhances the efficiency of aggregation and statistical analysis. While Method #2 has successfully addressed extreme values, it has concurrently inflated our means. In the context of assessing employee engagement, this outcome is undesirable, as it deviates from our objective of obtaining the most accurate representation of employees' responses without significant distortion.

As part of the data pre-processing, I replaced values 1 and 2 in column Q4 with management and non-management for the purposes of grouping and data aggregation. I also replaced values 1, 2 and 0 in column Q5 with full-time, part-time and unsure for the same purposes. 
![Alt text](<Screenshot 2024-01-10 at 8.52.02 pm.png>)

For the Quantitative section, I dropped the `ID` and `Q3` columns for quantitative analysis.
![Alt text](<Screenshot 2024-01-10 at 8.54.10 pm.png>)

For the Qualitative section, I appended the `Q3` column to the dataframe for qualitative analysis. 
![Alt text](<Screenshot 2024-01-10 at 8.57.21 pm.png>)