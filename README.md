# RealTime_Election_Voting_Capstone_Project
The current election system is mainly based on the ballot system, where parties and candidates are listed on paper, and people go to vote for their preferred candidate.

This project proposes building a real-time election voting system to ensure instant and real-time socialization of voting data and results. The system will perform voter accreditation, candidate accreditation, and the voting process in real time.

The architecture of the project includes parties, candidates, and voters registered on the platform, with their information saved in a Postgres database and streamed simultaneously into Kafka.

A Spark job will listen for events coming into Kafka, consume and aggregate the data, and stream it back into another Kafka topic. Streamlit will listen for events coming into the Kafka topic and visualize the results in real time.

# Architecture Diagram
 
<img width="468" alt="image" src="https://github.com/surbhiwahie/RealTime_Election_Voting_Capstone_Project/assets/24772688/ed2957f7-f1cd-4d88-90c4-db00e61d14a5">

# System Components

##main.py: This is the main Python script that creates the required tables on postgres (candidates, voters and votes), it also creates the Kafka topic and creates a copy of the votes table in the Kafka topic. It also contains the logic to consume the votes from the Kafka topic and produce data to voters_topic on Kafka.

##voting.py: This is the Python script that contains the logic to consume the votes from the Kafka topic (voters_topic), generate voting data and produce data to votes_topic on Kafka.

##spark-streaming.py: This is the Python script that contains the logic to consume the votes from the Kafka topic (votes_topic), enrich the data from postgres and aggregate the votes and produce data to specific topics on Kafka.

##streamlit-app.py: This is the Python script that contains the logic to consume the aggregated voting data from the Kafka topic as well as postgres and display the voting data in realtime using Streamlit.
