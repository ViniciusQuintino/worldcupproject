# 📊 World Cup Project


## 📌 Overview
Interactive dashboard project focused on the historical analysis of the FIFA World Cup,
exploring national team performance, titles, participations, and player statistics.


## 🎯 Objective
To present an analytical and historical view of the FIFA World Cups, supporting
temporal exploration and comparisons between national teams and players.


## 📂 Data Sources
The data used in this project was obtained from public datasets related to the FIFA World Cup.


## 🔄 Project Stages


### 🧹 Data Cleaning and Preparation (Python)
In the initial stage of the project, data cleaning and preparation were performed.
Since the dataset is comprehensive and includes information about both men’s and women’s
World Cups, the first step was to apply a filter to keep only records related to
men’s FIFA World Cups.

This decision was made considering that the project scope is aligned with the
2026 FIFA World Cup, which refers to a men’s competition, ensuring greater
consistency and coherence in the analysis.


<img width="810" height="306" alt="image" src="https://github.com/user-attachments/assets/07c44883-6bde-4d1f-865c-48a41cd5b918" />


Data cleaning and preparation were performed using Python and Pandas,
with a focus on standardization and filtering of records.

📎 The complete notebook with the data cleaning process can be accessed at:  
[worldcupproject/data_cleaning.ipynb](https://github.com/ViniciusQuintino/worldcupproject/blob/main/data_cleaning.ipynb)



### 🧠 Data Modeling and Import
The data model was structured following BI best practices, using an extended
star schema (galaxy schema), where the matches table represents the main fact
table of the project.

World Cups were modeled as a dimension, providing historical and temporal
context for the analyses, while other fact tables record specific events,
such as goals, individual awards, and national team participation.

Dimensions such as national teams, players, and tournaments are shared across
multiple fact tables, enabling data analysis from different perspectives.

<img width="1386" height="785" alt="image" src="https://github.com/user-attachments/assets/ada7100a-8ef0-4bfd-a126-1c18b3c79ce5" />


### 🧮 Measures Creation (DAX)
Project measures were developed using DAX, following best practices to ensure
readability and reusability. They cover national team performance, match
statistics, historical World Cup analyses, and individual player metrics.

📎 For a more detailed view of the measures, see:  
[worldcupproject/measures.md](https://github.com/ViniciusQuintino/worldcupproject/blob/main/measures.md)


### 📊 Dashboard Development
The project concludes with the development of an interactive dashboard,
allowing historical exploration of FIFA World Cups, national team performance,
player statistics, and comparisons across tournament editions.


#### Screen 1 – Tournament Overview
This screen presents a historical overview of the FIFA World Cups, including
a ranking of national teams by titles, number of participations, and evolution
over time.

<img width="1424" height="803" alt="image" src="https://github.com/user-attachments/assets/400eb705-41e5-4574-a082-f6a1d1b3595c" />


#### Screen 2 – National Team Analysis
This screen allows exploration of each national team’s performance across
different tournament editions, including matchups against other teams,
last time winning the World Cup, last time hosting a World Cup, and goals scored.

<img width="1424" height="803" alt="image" src="https://github.com/user-attachments/assets/7397f7fe-b3d1-44f8-9cba-896b8550f3c0" />


#### Screen 3 – Player Statistics
This screen details individual player statistics, such as individual awards,
top scorers ranking, and players awarded in the most recent World Cup edition.

<img width="1412" height="788" alt="image" src="https://github.com/user-attachments/assets/ba86f590-7065-4fdd-965f-000ddd76374c" />

📎 The complete dashboard file is available for download and interactive exploration:  
[worldcupproject.pbix](https://github.com/ViniciusQuintino/worldcupproject/blob/main/worldcupproject.pbix)


## 🛠️ Technologies Used
The technologies were selected to ensure data quality during preparation,
analytical flexibility, and clear, interactive visualizations.

- **Power BI**  
  Used for data modeling, DAX measure creation, and interactive dashboard development.

- **Python (Jupyter Notebook)**  
  Responsible for data cleaning, filtering, and preparation before importing
  into Power BI.

- **Visual Studio Code**  
  Used as the development environment for code organization, script management,
  and project version control.

- **QGIS**  
  Used to create the maps included in the dashboard visualizations.


## Conclusion
This project demonstrates the application of best practices in data preparation,
analytical modeling, and interactive visualization using historical men’s FIFA
World Cup data. The final result is a dashboard that enables clear, dynamic,
and analysis-driven exploration of information, supporting decision-making and
the generation of insights from data.
