# RealTime_Election_Voting_Capstone_Project
The current election system is mainly based on the ballot system, where parties and candidates are listed on paper, and people go to vote for their preferred candidate.

This project proposes building a real-time election voting system to ensure instant and real-time socialization of voting data and results. The system will perform voter accreditation, candidate accreditation, and the voting process in real time.

The architecture of the project includes parties, candidates, and voters registered on the platform, with their information saved in a Postgres database and streamed simultaneously into Kafka.

A Spark job will listen for events coming into Kafka, consume and aggregate the data, and stream it back into another Kafka topic. Streamlit will listen for events coming into the Kafka topic and visualize the results in real time.

# Architecture Diagram
 
<img width="468" alt="image" src="https://github.com/surbhiwahie/RealTime_Election_Voting_Capstone_Project/assets/24772688/ed2957f7-f1cd-4d88-90c4-db00e61d14a5">

# System Components

main.py:  This is the main Python script that creates the required tables on postgres (candidates, voters and votes), it also creates the Kafka topic and creates a copy of the votes table in the Kafka topic. It also contains the logic to consume the votes from the Kafka topic and produce data to voters_topic on Kafka.

voting.py: This Python script contains the logic to consume the votes from the Kafka topic (voters_topic), generate voting data and produce data to votes_topic on Kafka.

spark-streaming.py: This Python script contains the logic to consume the votes from the Kafka topic (votes_topic), enrich the data from postgres and aggregate the votes and produce data to specific topics on Kafka.

streamlit-app.py: This is the Python script that contains the logic to consume the aggregated voting data from the Kafka topic as well as postgres and display the voting data in realtime using Streamlit.

# Expected Outputs of the Project:
The expected outputs include real-time visualizations of election data, showcasing how each candidate gains votes. These visualizations will be accessible through the Streamlit interface.

# Queries and Their Results:
The main queries involve consuming and aggregating data from Kafka, enriching data from Postgres, and performing referential integrity checks. Results are used for real-time visualization and reporting any data quality issues.

# Choice of Data Sets:
The data sets from the "Random User Generator" API were chosen to simulate realistic user interactions, providing diverse voter and candidate profiles for testing and development.

# Choice of Technologies:
Kafka, Spark, and Streamlit were chosen for their capabilities in real-time data streaming, processing, and visualization, respectively. Docker Compose was chosen for easy deployment.

# Choice of Data Model:
The data model includes three tables (Candidates, Voters, and Votes) in Postgres. The choice was driven by the need for relational data storage and ease of integration with other components.

# Steps Followed:
The steps involve setting up the architecture using Docker Compose, creating tables in Postgres, generating synthetic data, and implementing scripts for real-time data processing and visualization.

# Alternatives Considered:
Alternative technologies for data streaming and processing were considered. However, the chosen technologies provided a cohesive and efficient solution for the project requirements.

