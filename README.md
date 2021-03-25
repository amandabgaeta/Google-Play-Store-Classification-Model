## Introduction: Business Problem

With Android OS holding 87% of market share in 2019, a VC firm is looking to understand what characteristics are predictive of a positively rated app (4.5+ rating on a 1-5 scale). They want to be able to utilize this information to target possible companies to apply for investment. It can also be applied to weed out those that are not a fit. Given that there are strong signals, these learnings could also be operationally applied to targeting companies to invest in, application questions, and company screenings for more efficient filtering and assessment.

Throughout the model construction, a focus was placed on scoring high on recall and balanced with the goal of an accuracy score better than a random guess. Recall was particularly chosen due to the risk of the model producing False Negatives, which would mean the VC firm would miss the opportunity to bring an app into the world. With recall emphasizing the importance of True Positives, we can focus on identifying apps that would most likely be positively rated. 

## The Data
The modeling iterations have been created using 2019 Google Play Store data found on Kaggle. The file utilize can be found in the data folder of this repo ('googleplaystore.csv')

Link to Kaggle page: with dataset: https://www.kaggle.com/lava18/google-play-store-apps?select=googleplaystore.csv

## Data Processing

Notebook.pdf includes cleansing, editing, functions, and feature engineering that was utilized in model iterations.

The /scratchWork folder has variations of dadt discovery, data analysis, model approaches, and notebook iterations that were used to get to the final Notebook.pdf.

## Model Iteration
Notebook.pdf includes an outline of the 12 model iterations that were completed. The final two models, a Decision Tree (model 11) and a Random Forest (model 12), produced either:

1. An accuracy score 1-2% above a random guess and a 50% recall score  (Decision Tree)
OR
2. A 56-58% recall score (and similar cross validation scores for recall, and an accuracy score 2% below a random guess (Random Forest)

Since this was an either or situation, feature importance across both models were explored for any consistency.

## Feature Importance
Across Decision Tree and Random Forest, 5 out 6 feature importance checks highlight Review and Installs followed by Size of the app as model drivers.

## Data Analysis
When looking at installs, the story is not necessarily the more installs an app has, the likely the app is positively reviewed. According to the Google Play Store data used, an app that has 1 million to 5 million installs is the sweet spot.

Further analysis on the number of reviews for positively rated apps led us to an opportunity for further model improvement. Plotting showed that the apps with positive ratings are the ones with 0-20 reviews. This could be a space for further iteration as the logic does not check out that higher installs, but very low number of reviews predict a successful app.

Size was a feature that was tested with consistently in this process and in the final model iterations ended up as a translation of the size into kilobytes. On the other hand, there were many apps that had a size that varied based on the device. These values were left at 0 and this showed up in plotting the app sizes that are most tied to positively rated apps. For those that _had_ a defined size, 3,000-26,750 kbs was the range with a median of 10,000kbs. In researching further, the average android app is 11,500kbs, so our data is similarly aligned.

The /images folder holds the images of these plots.

## Conclusion

#### Recommendations on Model Utilizatoin
Although the model is not in a final versioning to be utilized in day-to-day decisions, the consistency from this version can be generally applied to say that marketing, promotion, and adoption of the app is foundationally important.

Along with the technical aptitude for efficient app development, the VC would want CEOs with strong marketing background, a network with these skills, and/or teams that have this expertise.

### Future Work

#### Internal VC Operations
VC should take the themes from the model and emphasize, in addition to the technical teams building and supporting the app, a strong marketing capabilities. This can be translated into applications for funding, questions for in-person pitching, and more advanced personal interviews further down the line. It can also be applied as an approach in targeting organizations with these characteristics for VC investment.

#### Additional Data Analysis and Modeling
Further model iteration is needed from the data perspective. This includes opportunities to fold in more Google Play Store data (is it scrapeable? get more data for high install apps 50 million+, app age), continue to cleanse the current data (duplicates and additional size research and assignment), and revisit the number of reviews feature in the model to understand what is causing 0-20 reviews to pop as a consistent driving factor for a positively rated app. Finessing the model in these ways can aid not only in increasing priority scoring like recall, but with additional data features like age, can create post-funding goals for the app companies to achieve like install and review count milestones
