# Erdos : Team Uncreatives
Repository for Erdos Data Science Bootcamp Team Project - Predictors of Social Media engagement within a niche. More info on the team and project specifics found [here](https://www.erdosinstitute.org/programs/spring-2025/data-science-boot-camp/project-upload
).

## Introduction
Our team set out to explore predictors of social media engagement with the aim of identifying strategies that boost post performance. Specifically, we examined a dataset of YouTube Shorts videos in the beauty niche to uncover how elements such as post timing, hashtags, and keyword usage relate to viewer engagement (likes, comments, views)

## Defining the dataset
We scraped public YouTube Shorts data using the Apify platform. This allowed us to gather metadata for thousands of posts from beauty influencers, including creator's username, total likes, total shares, total comments, post description, hashtags, and posting time. Data cleaning was conducted in multiple stages:
- Initial cleaning ([1 data_cleaning1](<Data_Cleaning_Only/1 data_cleaning1.ipynb>), [2 data_cleaning2](<Data_Cleaning_Only/2 data_cleaning2.ipynb>)) : We removed duplicate entries, handled missing values, and normalized text fiels.
- Temporal filtering ([3 Removing Early Dates](<Data_Cleaning_Only/3 Removing Early Dates.ipynb>)) : We identified that posts made in the final month of our data collection window (close to March 1, 2025) had significantly fewer views, likely due to limited time to accumulate engagement. Using t-tests at a significance level of α = 0.01, we confirmed that only the most recent month had statistically lower view counts. Therefore, we excluded this final month of data when analysing views to avoid skewing results, while retaining it for analyses unrelated to views. 
- Feature engineering ([4 Creating_features](<Data_Cleaning_Only/4 Creating_features_for_the_testing_set.ipynb>)) : In preparation for modeling, we engineered features that better captured patterns in post performance. This included combining and formatting date and time information into datetime objects, extracting hour-of-day and day-of-week indicators, and log-transforming engagement metrics like views and likes to normalize skeweed distributions. 

## Exploratory Data Analysis (EDA)
EDA was performed in multiple stages:
- Data split ([Creating the split](<pranavrd/erdos-uncreatives/eda_2/Creating the Split.ipynb>)) : Data was split into training and tests, EDA was performed using only the training dataset (50% of the full dataset) to ensure unbiased model evaluation.
- Preliminay trends and distribution analysis ([EDA](<pranavrd/erdos-uncreatives/eda_2/eda_2_fixed.ipynb>)): We began by examining the distributions of our key engagement metrics (likes, views, and comments), both in their raw and log-transformed forms. We explored the relationships between predictors like hashtags, use of keywords, and posting time. Visualizations such as histograms, boxplots, scatterplots were used to identify patterns, outliers, and skewness in the data.
- Hypothesis testing ([hypo_tests](<pranavrd/erdos-uncreatives/eda_2/hypo_tests.ipynb>)): To assess whether particular types of features (e.g., posting time, use of keywords, hashtags) significantly influenced post engagement.
Insights from this analysis guided the feature selection and transformation decisions used in later modeling stages.

## Modeling and Results
Modeling was conducted in several phases using only the training dataset. We focused on predicting two engagement outcomes: log-transformed views per subscriber and a composite engagement score ((Likes+Comments)/(Views+1)).
- Normality and target definition ([0_Checking for Normality](<pranavrd/erdos-uncreatives/Modelling/0_Checking for Normality.ipynb>)): We began by checking the distribution of our target variables. We determined that log-transforming views, likes, and comments helped reduce skewness and better satisfy assumptions for linear modeling.
- Modeling view counts ([1_Views_models](<pranavrd/erdos-uncreatives/Modelling/1_Views_models.ipynb>)): We built multiple linear regression models to predict log-transformed views using combinations of features such as posting hour, day of week, hastags, keywords. We began with  basic linear regression models, and then introduced regularized models including Lasso regression to prevent overfitting and enhance generalization.
- Modeling engagement ([2_Engagement_models](<pranavrd/erdos-uncreatives/Modelling/2_Engagement_models.ipynb>)): We applied the same modeling strategy to a new target variable: engagement score ((Likes+Comments)/(Views+1)).
- Modeling specificationn testing ([3_Model_Specification_Testing](<pranavrd/erdos-uncreatives/Modelling/3_Model_Specification_Testing.ipynb>)): We tested whether interaction terms or polynomial features improved model fit. 
- Interpretability ([4_Linear_Model_Interpretation](<pranavrd/erdos-uncreatives/Modelling/4_Linear_Model_Interpretation.ipynb>)): We examined standardized coefficiants from the Lasso models and visualized marginal effects of key features. This helped interpret how changes in inputs such as posting time and keywords influence engagement.
- Non-linear modeling ([5_Decision_Trees](<ppranavrd/erdos-uncreatives/Modelling/5_Decision_Trees.ipynb>)): To explore non-linear relationships, we trained a decision tree regressor. 
- Final hypothesis testing ([6_Final_Hypothesis_Testing](<pranavrd/erdos-uncreatives/Modelling/6_Final_Hypothesis_Testing.ipynb>)): We conducted targeted follow-up tests on the testing set on specific model predictors to confirm that their relationships with engagement outcomes were statistically robust.

Best model:
Most predictive features: 
Model performance: 

## Stakeholders
The stakeholders of our project include organizations or individuals who would be interested in utilizing our results. This includes social media influencers or businesses with a social media presence  who would like to optimize the performance of their own posts, social media managers who would like to optimize the performance of the posts of their clientele, and social media analytics platforms like Hootsuite or Sprout Social who may be interested in providing this kind of analysis as a service to their customers. 

## Key Preformance Indicators
Key performance indicators are used in business to judge performance and progress toward specific, measurable goals. In our context, a KPI is a measure of the success of our project. 

Our KPI will be the ability for influencers to post using our suggestions based on hypothesis testing to improve views and engagement. 

## Takeaways
- Strategic use of keyword, hashtags, and posting time can significantly influence viewers engagement with post.
- Public scraping platforms like APIFY provide accessible routes to collect meaningful social media data

## [Presentation link]()

## [Other links]()



