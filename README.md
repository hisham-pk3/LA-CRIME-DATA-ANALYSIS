## Deployment Instructions

Install Docker Desktop to build the image and create the container which contains HDFS, PySpark and Jupyter notebook setup.
Create a docker compose file which contains all the necessary components to create the container.

<img width="381" height="512" alt="unnamed" src="https://github.com/user-attachments/assets/d96f6d45-d2ce-456a-b822-c019bd553e33" />

<img width="512" height="500" alt="unnamed" src="https://github.com/user-attachments/assets/9cefa721-08b7-43b8-9ab8-c30acea28c5b" />


<br>

 So, this will setup the below:<br><br>
1 Spark Master<br>
2 Spark Workers<br>
1 HDFS Namenode<br>
1 HDFS Datanode<br>
1 Jupyter Notebook (with PySpark preconfigured)<br>

Create a folder in the local system and place the docker compose file in the folder.<br>
 Launch the stack:<br>
Open terminal in the folder.<br>


Run:<br><br>
docker-compose up –build -d<br>
This will pull all the needed images and start the local Spark-Hadoop-Jupyter cluster.<br>
Open Jupyter Notebook<br>
Visit: http://localhost:8888<br>
Copy the token from the terminal output if it asks for one.<br><br><br>
## Instructions to run the application<br><br>

***Step 1:*** Install Docker Ddesktop, if not installed. Open the Docker Desktop and click on run option on the selected container to spinup the environment.

<img width="512" height="217" alt="unnamed" src="https://github.com/user-attachments/assets/2bcc63f1-0d51-4347-93e7-254d51d25560" />

***Step 2:*** The dataset is placed in the project directory and then uploaded to HDFS from the local file system by copying it to the HDFS namenode container. This is the data ingestion process
Then, a shell is opened into the container, and the HDFS commands are used to upload the file

<img width="512" height="161" alt="unnamed" src="https://github.com/user-attachments/assets/88754990-b462-4035-b754-47c8bec3ea78" />
<br><br>
Commands used to upload the dataset to HDFS<br>
Copy dataset to namenode container: <br>
docker cp D:/local-databricks/data/Crime_Data_from_2020_to_22March2025.csv namenode:/crime.csv<br>
Open a shell into the container:<br>
docker exec -it namenode bash<br>
Run HDFS commands to upload:<br>
hdfs dfs -mkdir -p /user/data<br>
hdfs dfs -put Crime_Data_from_2020_to_22March2025.csv /user/data/<br>
hdfs dfs -ls /user/data<br><br>

***Step 3:*** The Jupyter notebook is opened by accessing http://localhost:8888 in any web browser.
<img width="512" height="290" alt="unnamed (1)" src="https://github.com/user-attachments/assets/9462ea8c-9ab6-4cc8-b135-c57bebdd0d66" />

<br><br>

***Step 4:*** A Spark Session is initiated and the raw dataset is loaded from HDFS into the dataframe in the Spark session.
<br><br>
<img width="512" height="113" alt="unnamed" src="https://github.com/user-attachments/assets/83499f7c-7871-4821-a652-e86840022a28" />
<br><br>
***Step 5:*** Once the raw dataset is cleaned by applying appropriate data cleaning techniques, the clean dataset is saved to HDFS. Then again the cleaned dataset can be loaded into a new dataframe by creating a new spark session and analysis and visualization can be done.
<br><br>
***Step 6:*** All the visualizations libraries that are needed, to be downloaded before performing the visualizations. This can be done by running the pip install command in the Jupyter notebook and install the required libraries.


