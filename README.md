## Job Recommender

- Objective
- Data
- EDA
- Recommender Pipeline
- NLP Machine Learning Model Pipeline



### Objective 
This a job recommender for blue-collar jobs in New York. 

I made a recommender system that includes popular jobs, distances, and content-based suggesting using Natural Language Process. The distance is a strong factor to take a job by users whom usually has more than one job. 

### Data

The Dataset contains information about job applicants: demographic information, degree type, major, graduation date, years of experience, employment status, application history. From jobs it contains: title, description, application duration, requirements, and demographic information.

There are not a good information about user profile. Not all feature are used as the dataset was created for a Kaggle Compentition.

I created additional features to calculate distances and similarities among jobs and users profiles. Those are: Coordinates, User Profile, Jobs Profile

The source is from Kaggle: https://www.kaggle.com/c/job-recommendation/data

### EDA
* Jobs by Communities/Counties
* Jobs by zipcodes
* Users by Communities


### Recommender Pipeline
1. Recommender by popularity
2. Recommender by Content
3. Hybrid Recommender


- **Recommender Pipeline: Popularity** 
    - Generate Popular Job Ranking:
Group job titles using historical application and order max to min
Look for top k popular titles current available  
  
    - Recommend top k popular jobs (user_id):
        - Case user exist  and has coordinates:
Get coordinates of popular available jobs
Order by distance
Check the maximum distance allowed
If finished and don’t get all top k fill with most popular
        - Case user don’t exit or don’t has coordinates:
Recommend top k most popular categories

- #### Recommender Pipeline: Content Based
    - Checks: if has coordinates, max distance allowed, best simulation (ML model uses stochastic optimization)  

    - Look for description for jobs that users has already applied. 

    - Used user profile content and history application to inferred top k most similar jobs using the trained ML model.  


- #### Recommender Pipeline: Hybrid Recommender 

    - Recommender_popular_jobs for cold Star: User without sufficient information about profile or distance. Use: 

    - content_distance_based_recommender: Using a Distributed Representations of Sentences and Documents Unsupervised Machine Learning Model to find similarities among users and jobs information. 



### NLP Machine Learning Model Pipeline

1. Preprocessing: Preprocessing jobs profiles: Convert it to vectors and mapping a dict with JobID->Tokenized Doc
2. Create: Create Distributed Doc2Vec model
3. Build: Build vocabulary
4. Train: Train model
5. Save: Save model


