# Task Recommender

This repo shows the usage of an emsemble model (Gradient Boosting) for use in a recommendation engine.

## Setup
Run `pip install -r requirements.txt`


## Data Generation
To generate data, run `DataGeneration.ipynb` (or use the commited file in data/).

Parameters for data generation
- Task data are generated from GenAI
    - 100 rows in total
- User data uses names typical to Singaporean, with motivation, age, and health status randomly selected
    - 100 rows in total
    - motivations: ["Weight Management", "Social Interaction", "Improve Sleep", "Increase Energy", "Reduce Stress", "Build Muscle"]
    - overall_health_status: ["Excellent", "Good", "Fair", "Poor"]
    - Age: random.randint(18, 65)
- User - task interaction data uses the following logic
    - Creating a loop through all users and all task (100 * 100), of which, a certain percentage (40%) will be skipped, resulting in a dataframe of around 6000 rows
    - Column includes userid, taskid, and completion
    - If the user's `motivation` is:
        - `Weight Management`, the user will have a higher preference for `Physical` task
        - `Improve Sleep`, the user will have a higher preference for `Rest` task
        - `Increase Energy`, the user will have a higher preference for `Cardio` task
        - `Reduce Stress`, the user will have a higher preference for `Flexibility` task
        - `Build Muscle`, the user will have a higher preference for `Strength` task
        - `Social Interaction`, the will user have a higher preference for `Outdoor` task
    - If the user's `Overall Health Status` is:
        - `Poor`, the user will have a higher preference for `Low` intensity task
        - `Fair` or `Good`, the user will have a higher preference for `Medium` intensity task
        - `Excellent`, the user will have a higher preference for `High` intensity task


## Model
To train the model and generate inference, run `TaskRecommender.ipynb`