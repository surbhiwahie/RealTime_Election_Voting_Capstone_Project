# RealTime_Election_Voting_Capstone_Project
The current election system is mainly based on the ballot system, where parties and candidates are listed on paper, and people go to vote for their preferred candidate.

This project proposes building a real-time election voting system to ensure instant and real-time socialization of voting data and results. The system will perform voter accreditation, candidate accreditation, and the voting process in real time.

The architecture of the project includes parties, candidates, and voters registered on the platform, with their information saved in a Postgres database and streamed simultaneously into Kafka.

A Spark job will listen for events coming into Kafka, consume and aggregate the data, and stream it back into another Kafka topic. Streamlit will listen for events coming into the Kafka topic and visualize the results in real time.
