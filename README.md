# LA Crime Data Analysis  

## 📌 Project Overview  
The **LA Crime Data Analysis** project was developed to design and implement a comprehensive pipeline for analyzing large-scale crime datasets using distributed computing technologies. Crime is a major challenge in urban environments, and in a city as vast and diverse as Los Angeles, uncovering historical patterns and trends provides valuable insights for understanding public safety dynamics.  

This project focuses on crime data from **2020 onward**, a period that not only reflects long-term urban crime patterns but also coincides with significant social, economic, and political shifts such as the COVID-19 pandemic, nationwide protests, and the U.S. presidential elections.  

At its core, the project leverages **Apache Spark (PySpark)** and the **Hadoop Distributed File System (HDFS)** to support scalable data storage and processing. Spark was chosen for its ability to efficiently handle large datasets, perform distributed transformations, and provide compatibility for downstream analytics. A strong emphasis was placed on **data cleaning**, ensuring data quality by resolving missing values, correcting invalid entries, standardizing formats, and removing non-essential fields.  

The analysis explores multiple dimensions:  
- **Temporal trends** → crime variations across times of day, days of the week, and months.  
- **Spatial distribution** → identifying patterns across neighborhoods and geographic areas.  
- **Demographics** → studying how factors such as victim age, gender, and ethnicity relate to different crime types.  
- **Event-based insights** → examining whether major real-world events had measurable effects on crime trends.  

The results are communicated through **visualizations** created with **Matplotlib, Seaborn, and Plotly**, all presented in an interactive **Jupyter Notebook** environment. Beyond technical execution, the ultimate goal of this project is to deliver **actionable insights** that can inform research, policy, and urban safety strategies.  
 

---

## 🎯 Goals of the Project  
- **Scalable Data Handling** → Use **HDFS** for distributed storage and **Apache Spark (PySpark)** for large-scale data processing.  
- **Data Cleaning & Preprocessing** → Handle missing values, invalid entries, standardize formats, and drop non-essential columns.  
- **Pattern & Trend Extraction** → Analyze temporal, spatial, and demographic variations in crime.  
- **Event-Based Analysis** → Study crime trends around **COVID-19 waves**, **George Floyd protests**, and the **U.S. elections**.  
- **Visualization & Insights** → Present findings using **Matplotlib, Seaborn, and Plotly** for clarity and interpretability.  

---

## 📊 What the Project Does  
The project provides insights into Los Angeles crime data through:  

- **Temporal Trends** → Crime variations across times of day, days of the week, and months.  
- **Crime Type Distribution** → Frequency and proportion of different crime categories.  
- **Victim Demographics** → Age, gender, and ethnicity distribution across crime types.  
- **Area-Wise Distribution** → Hotspot detection and neighborhood-based crime patterns.  
- **Impact of Major Events** → Measuring crime trends during COVID-19, protests, and elections.  
- **Geospatial Analysis** → Mapping crime intensity across different LA regions.  

---

## ⚙️ Technology Stack  

- **Operating System**: Windows  
- **Distributed Storage**: Hadoop Distributed File System (HDFS)  
- **Data Processing**: Apache Spark (PySpark)  
- **Containerization**: Docker  
- **Programming Language**: Python  
  - Libraries: PySpark, Pandas, Matplotlib, Seaborn, Plotly  
- **Development Environment**: Jupyter Notebook  

---

## 📈 Sample Visualizations  
The notebook generates a variety of static and interactive plots to highlight different aspects of crime trends, including:  

- **Line plots** → Temporal trends (daily, weekly, monthly).  
- **Bar charts** → Crime counts by type, demographics, and areas.  
- **Pie charts** → Proportional breakdowns of crime categories or victim attributes.  
- **Heatmaps** → Identifying hotspots across LA neighborhoods.  
- **Geospatial plots** → Mapping crime intensity across different regions.  
- **Comparative charts** → Event-based analysis before, during, and after major events.    

---

## 📌 Future Improvements  
- Integrating **real-time streaming crime data** using Spark Streaming.  
- Building an **interactive dashboard** (e.g., Dash or Streamlit) for stakeholders.  
- Expanding analysis to compare **pre-2020 vs. post-2020 trends**.  

---

## 📝 License  
This project is for **educational and research purposes only**.  





## Deployment Instructions

Install Docker Desktop to build the image and create the container which contains HDFS, PySpark and Jupyter notebook setup.
Create a docker compose file which contains all the necessary components to create the container.

<img width="381" height="512" alt="unnamed" src="https://github.com/user-attachments/assets/d96f6d45-d2ce-456a-b822-c019bd553e33" />

<img width="512" height="500" alt="unnamed" src="https://github.com/user-attachments/assets/9cefa721-08b7-43b8-9ab8-c30acea28c5b" />


<br><br><br>

 So, this will setup the below:<br><br>
- 1 Spark Master<br>
- 2 Spark Workers<br>
- 1 HDFS Namenode<br>
- 1 HDFS Datanode<br>
- 1 Jupyter Notebook (with PySpark preconfigured)<br>

Create a folder in the local system and place the docker compose file in the folder.<br>
Launch the stack:<br>
1. Open terminal in the folder.<br>


2. Run:<br><br>
docker-compose up –build -d <br>
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
  _docker cp D:/local-databricks/data/Crime_Data_from_2020_to_22March2025.csv namenode:/crime.csv_<br>
  
Open a shell into the container:<br> 
  _docker exec -it namenode bash_<br>
  
Run HDFS commands to upload:<br> 

  _hdfs dfs -mkdir -p /user/data_<br>
  _hdfs dfs -put Crime_Data_from_2020_to_22March2025.csv /user/data/_<br>
  _hdfs dfs -ls /user/data_<br><br>

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


