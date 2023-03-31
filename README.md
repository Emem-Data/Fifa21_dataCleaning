# FIFA'21 DATA CLEANING
![FIFA21](https://user-images.githubusercontent.com/103915142/229073730-ac1907c1-9aee-4d2c-a785-d573f2f755e5.jpg/1080x609)
# OUTLINE
* INTRODUCTION
* DATA ASSESSMENT
* DATA CLEANING
* DATA VERIFICATION
* CONCLUSION


## INTRODUCTION
Football is the most popular sport in the world and FIFA is the organization responsible for organizing the most prestigious football tournament, the FIFA World Cup.
In this project, we will explore the FIFA 2021 dataset, which contains detailed information on the players and teams featured in the game. The dataset provides a wealth of information on player attributes such as speed, agility, shooting accuracy, and more. However, like most real-world datasets, the FIFA 2021 dataset is far from perfect. Our goal in this project is to clean and prepare the dataset for further analysis and modelling.
Through the data-cleaning process, we will discover patterns and insights that can inform future game development and player performance analysis. This project is a great opportunity to showcase the importance of data cleaning and preparation in data analysis, especially when dealing with large, complex datasets.

## DATA ASSESSMENT

1.  **Data Exploration:** 
      The FIFA 2021 dataset contains 18980 rows and 77 columns. The columns contain information such as player attributes, team attributes, player positions, and more.       I used the Google Sheet tool to explore and clean the dataset. Many column titles were not appropriate or descriptive enough, we also had extra unused rows. This       and more cases be handled in the data-cleaning process
2.  **Missing Values:****
      We identified missing values in two columns of the dataset, including ‘Loan Date End’, and 'Hits’. In total, there were 1,036 missing values in the dataset. We         will need to decide the best way to handle the missing values when cleaning.
3.  **Data Types:**
      We checked the data types for each column in the dataset and found that some columns were not stored in the correct data type. For example, the ‘Value’, 'Release       Clause', ‘Wage’, and ‘Hits’ columns were stored as an object data type instead of a numeric data type. Some columns had inconsistent data types, like ‘Height’,         and ‘Weight’. We will need to handle this and more similar cases in our data-cleaning process.
4. **Duplicates:**
      We checked for duplicate data in the dataset using the ID column as a metric and found that there were no duplicate rows. While we had some repetition of player       names on the player Name column, we saw that the row had a unique ID and the contracts were different. Hence, a player can appear many times but for a different       contract or play for a different club.    
5.  **Outliers:**
      We used Scatter plots to identify outliers in the numerical columns of the dataset. We found that the ‘Age’ column contained outliers. We determined that these         outliers were valid data points and did not need to be removed from the dataset. We also saw that the “Player Potential” column chart depicts a right-skewed           histogram shape. This means more data points were featured on the right side of the chart.
6. **Data Quality:**
      We checked the quality of the data by comparing it to external sources of information. For example, we cross-referenced the names of players and teams in the           dataset with the official FIFA website to ensure that they were spelt correctly and that they corresponded to the correct players and teams. We also determined         the age outlier was not a danger to our dataset because we confirmed that the age was correct.
7. **Data Consistency:**
      We checked for inconsistencies in the data, such as inconsistent spelling, special characters or formatting. For example, we found that some player names were         spelt differently from the information in the ‘player url’ column. We also found that some columns contained special characters like a star to denote “ratings”.       The formatting of some columns like ‘Overall analysis’, and ‘Best Overall’ were wrong, as they ought to be in percentages.

































