# Government power detection from the activity control in COVID-19

***Abstract***

National system of government by definition is the monopolisation of legitimate violence according to Maximilian Weber. How would the pandemic affect the monopolisation which is authorised by citizens? As we observe, different regions in the world have taken different measures to cope with covid which possess distinct styles in terms of culture, geography and so on.  It offers an opportunity to investigate the threshold of government enforcement among the public and vice versa. Here we try to analyse the inter-country difference of COVID restriction measure and the corresponding public reaction reflected through mobility data shift. In order to isolate the effect of government on mobility, we plan to apply feature engineering and machine learning methods to analyse the driving force behind the government's public power. Furthermore,extra datasets need to be implemented to get insights with respect to geographical, cultural, economic factors that formulate governments’ power.

## Research questions
1. Which country has the most executive government for pandemic control? 
2. What is the relationship between government execution and the effectiveness of implementation? 
3. What is the difference between the government's execution of pandemic control and the government's overall execution?

## Proposed Additional Dataset
1. Government effectiveness - Country rankings  
It’s an overall ranking focusing on the government execution, which is compared to the government execution we built from Coronawiki dataset. The possible mismatch between these two execution rankings can give us the opportunity to discover what factors are causing the government, unlike usual, to have relatively higher or lower enforcement of covid.
2. ISO 639-2: Codes for the Representation of Names of Languages  
In interventions.csv, the country is expressed in the first official language of the country, so the country and first official language correspondence table from ISO should be provided to link interventions.csv to other datasets.
3. Daily new confirmed COVID-19 cases per million people  
The government's restrictions on public activities reflect the government execution, while the changes in the Covid case reflect the effectiveness of the policy implementation. In our general perception, strong execution corresponds to good effectiveness. To test this view, the government execution ranking is compared with the Covid case ranking over the same time period. If our perception cannot be proven, more factors affecting policy effectiveness will be uncovered.


## Methods
Two ranking methods will be used, the non-machine learning method and the machine learning method.  

For ranking the government execution by non-machine learning method, the Multi-Criteria Analysis method could be used. Three groups of criteria, including response speed, implementation speed and implementation strength, are generated. Response speed refers to the time difference between the first death and the release of the school closure policy, which are found in interventions.csv. Implementation speed is the time difference between the release of the public events banned policy and the intersection of the rapidly declining phase and the stable phase in the data from activity frequency. Implementation strength can be expressed in terms of the frequency of occurrence of various activities in the post-reduction stabilisation phase. The final score can be obtained by normalising and weighting the average of each factor, which is somewhat representative of the government execution.

We propose to use the supervised machine learning, where will have 3 features relevant to three groups of criteria. Also additionally as features we can use categorical variable such as continent. At the same time we propouse to assign labels according to rate death cases / population, using defenition of government  as the protector of citizens we can assign 0 for country with signficant rate of death and 1 for not. Evaluation significance of rate will do using t-test and its p-value. In nutshell, we extract features: 
1. Continuous vaibales :
    - including response speed
    - implementation speed
    - implementation strength
2. Categorical variables :
    - continent
 
We will use following labels:  
  - 0 - not powerful government   
  - 1 - powerful government

Due to limited data and imbalance data according to categorical variable we suppose to separate this column to additional columns of features using one-hot encoding and to add additional wights to features with less presentance.

Based on it we can use logistic regression due to binary cleassification problem and with regulization for controlling loss function for adequate evaluation during the training model. For searching wights we will use SGD with mini-butch. As a loss function was chosen Negative Log-Likelihood Loss with regularisation composition and as the logistic function was chosen sigmoid function.   

For proving independence of features we suppose to use Spearman Rank Correlation for continuous variables.

## Proposed timeline
- 19/11/2022-25/11/2022 - Additional dataset collection and preprocessing

In order to introduce the cultural background into our data story, we need to collect more data for ‘interventions’. Besides, to better present the adaption to COVID of different countries, more datasets are needed, such as vaccination rates, case load and deaths..

- 26/11/2022-09/12/2022 - Feature extraction, feature engineering and model selection

From the preprocessed data, we will extract features mentioned above and do targeted feature engineering. We shall try different models, for example, each team member will try one model and then compare the performance. 


- 10/12/2022-16/12/2022 - Model tuning

After setting the model type, we will do fine tuning on hyperparameters and check if we can obtain satisfactory results.

- 17/12/2022-23/12/2022 - Data story

Choose a  manifestation to deliver our insights from the data and convey the whole project pipeline in a down-to-earth way.

## Organization within the team
Regular communication is required and every team member has parallel tasks.

