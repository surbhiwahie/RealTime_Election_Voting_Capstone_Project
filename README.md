# RealTime_Election_Voting_Capstone_Project
The current election system is mainly based on the ballot system, where parties and candidates are listed on paper, and people go to vote for their preferred candidate.

This project proposes building a real-time election voting system to ensure instant and real-time socialization of voting data and results. The system will perform voter accreditation, candidate accreditation, and the voting process in real time.

The architecture of the project includes parties, candidates, and voters registered on the platform, with their information saved in a Postgres database and streamed simultaneously into Kafka.

A Spark job will listen for events coming into Kafka, consume and aggregate the data, and stream it back into another Kafka topic. Streamlit will listen for events coming into the Kafka topic and visualize the results in real time.

# Architecture Diagram
 
<img width="468" alt="image" src="https://github.com/surbhiwahie/RealTime_Election_Voting_Capstone_Project/assets/24772688/ed2957f7-f1cd-4d88-90c4-db00e61d14a5">

# Queries and Their Results:

main.py:  This is the main Python script that creates the required tables on postgres (candidates, voters and votes), it also creates the Kafka topic and creates a copy of the votes table in the Kafka topic. It also contains the logic to consume the votes from the Kafka topic and produce data to voters_topic on Kafka.

voting.py: This Python script contains the logic to consume the votes from the Kafka topic (voters_topic), generate voting data and produce data to votes_topic on Kafka.

spark-streaming.py: This Python script contains the logic to consume the votes from the Kafka topic (votes_topic), enrich the data from postgres and aggregate the votes and produce data to specific topics on Kafka.

streamlit-app.py: This is the Python script that contains the logic to consume the aggregated voting data from the Kafka topic as well as postgres and display the voting data in realtime using Streamlit.

# Expected Outputs of the Project:

<img width="468" alt="image" src="https://github.com/surbhiwahie/RealTime_Election_Voting_Capstone_Project/assets/24772688/28303c3d-ff88-4b49-bde8-1d6194f5fbb8">

<img width="396" alt="image" src="https://github.com/surbhiwahie/RealTime_Election_Voting_Capstone_Project/assets/24772688/5373d73f-85e2-4a78-bebf-13623d50420c">


# Architecture Setup:
1. Established the system architecture with components such as parties, candidates, and voters stored in Postgres and streamed into Kafka.
2. Configured a Spark job to consume, aggregate data from Kafka, and stream it back into another Kafka topic.
3. Integrated Streamlit for real-time visualization of election results.

# Data Generation Module:
1. Implemented a Data Generation module utilizing the "Random User Generator" API.
2. Conducted Voter Data Generation fetching random user data with the nationality parameter set to "gb" and Candidate Data Generation with a specific gender parameter.
3. Utilized Python requests library and the random module to seed and control the randomness of generated data.
4. Produced synthetic voter and candidate data for testing, development, and demonstration purposes.

# Implementation Details and System Components:

1. Developed main.py script for creating required tables on Postgres (candidates, voters, and votes), handling data quality errors, creating Kafka topics, and ensuring table creation before data insertion.
2. Implemented voting.py script for consuming votes from the Kafka topic (voters_topic), generating voting data, and producing data to votes_topic on Kafka.
3. Created spark-streaming.py for consuming votes from Kafka, enriching data from Postgres, aggregating votes, and producing data to specific topics on Kafka.
4. Designed streamlit-app.py for consuming aggregated voting data from Kafka and Postgres, displaying real-time voting data using Streamlit.

# Data Quality Checks Module:

1. Implemented Referential Integrity Check to ensure each vote has a corresponding voter, flagging any discrepancies for further investigation.
2. Executed Sanity Row Counts Check to verify that the number of records in key tables ("voters," "candidates," and "votes") aligns with expectations.
3. Provided a screenshot of data quality checks in the Project Specification document.




