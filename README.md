
🏏 IPL Win Probability Predictor
📌 Overview
An end-to-end Machine Learning web application that predicts the real-time win probability of the chasing team at any stage of an Indian Premier League (IPL) match. Inspired by the win probability features on popular cricket platforms, this project uses historical ball-by-ball data to calculate dynamic match situations and output live win/loss percentages.

🛠️ Tech Stack
Language: Python
Data Manipulation: Pandas, NumPy
Machine Learning: Scikit-Learn (Logistic Regression, Random Forest, Pipelines)
Web Framework: Streamlit
Deployment: Heroku

📊 Dataset & Preprocessing
The model is trained on a comprehensive Kaggle IPL dataset containing over 70,000 ball-by-ball delivery records spanning from 2008 to 2019.
To ensure the model remains relevant and accurate to current match conditions, strict data preprocessing was applied:
Active Teams Only: Filtered the dataset to only include matches involving the 8 currently active IPL franchises (e.g., replacing "Delhi Daredevils" with "Delhi Capitals" and "Deccan Chargers" with "Sunrisers Hyderabad", while dropping defunct teams like Gujarat Lions).

Weather Adjustments: Removed all matches where the Duckworth-Lewis (D/L) method was applied due to rain, ensuring baseline data quality.

⚙️ Feature Engineering
To predict live match states, crucial dynamic metrics were calculated for every single ball of the second innings:

Runs Left: Target score minus the current score.

Balls Left: 120 minus the number of legal deliveries bowled.

Wickets Left: 10 minus the number of dismissed batsmen.

Current Run Rate (CRR): Runs scored divided by overs completed.

Required Run Rate (RRR): Runs left divided by overs left.

🧠 Model Building & Selection
Pipeline Creation: Built a robust ML pipeline using scikit-learn's ColumnTransformer and OneHotEncoder to handle categorical variables like the Batting Team, Bowling Team, and Host City.

Algorithm Choice (Logistic Regression vs. Random Forest): While a Random Forest classifier achieved a highly impressive accuracy of over 95%, Logistic Regression (~80% accuracy) was ultimately selected for the final model.
Random Forest models tend to be heavily biased towards one side, outputting rigid probabilities (e.g., 99% vs 1%). Logistic Regression was chosen because it provides much smoother, realistic, and sensitive probability curves (predict_proba) as the match progresses.

💻 Web App & Deployment
Designed an interactive and clean user interface using Streamlit, allowing users to select the teams, host city, target score, and current match situation to instantly calculate the win probability.

Deployed the final application to Heroku using an automated setup.sh script, a Procfile, and requirements.
txt to handle dependencies and server commands.

