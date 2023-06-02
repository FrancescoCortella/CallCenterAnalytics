# CallCenterAnalytics

This solution provides a step-by-step guide on implementing automation in the context of call center analytics. The process involves converting audio files of calls into text files, which are then analyzed using Azure OpenAI service APIs. Relevant information is extracted from the transcripts and organized in a tabular format. Finally, the key insights are visualized and mapped onto a PowerBI Dashboard.

# The architecture
![image](https://github.com/FrancescoCortella/CallCenterAnalytics/assets/135111177/b1bb7edc-d0a0-4398-8e5d-4028532b5063)

# Step-by-step implementation
1. Create an Azure Storage Account Gen 2 (with hierarchy --> data lake)
2. In line with the medallion framework, create three containers (bronze, silver, and gold)
3. Store your audio/text files in the bronze layer. You can use the sample files I provide in my repo "samples-call-transcripts" for testing purposes
4. Deploy an Azure Databricks resource
5. Create a Workspace within databricks where to run the python script saved in the "Notebook" file
6. Python script will access text files, call Azure OpenAI APIs, turn them into tabular format, and eventually store it in delta-parquet format in the gold container
7. Plug PowerBI to the gold container and serve data with your favorite dashboards. This is what I personally did:

<img width="886" alt="image" src="https://github.com/FrancescoCortella/CallCenterAnalytics/assets/135111177/55370f93-d50e-4c23-a440-3a4f69345838">

