# FIFA'21 DATA CLEANING

![FIFA21](https://user-images.githubusercontent.com/103915142/229223184-997c0ec3-22b9-4084-834f-5f1185f5f568.jpg)

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
      The FIFA 2021 dataset contains 18980 rows and 77 columns. The columns contain information such as player attributes, team attributes, player positions, and more.       I used the Google Sheet tool to explore and clean the dataset. Many column titles were not appropriate or descriptive enough, we also had extra unused rows. This 
      and more cases be handled in the data-cleaning process
      
2.  **Missing Values:**
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
   

__*By documenting these steps in the data assessment phase, we clearly understand the issues with the dataset and can proceed to the next phase of the data cleaning process.*__

## DATA CLEANING

1.	The first step that was taken in this phase was to import the dataset. 
      > In Google sheet, you import data by going to File >> Import >> Upload Data
      >> ![Inked1a](https://user-images.githubusercontent.com/103915142/229225496-b20261d2-6860-454c-a1c4-221bbbe2e5d3.jpg)

2.	After loading the dataset, my next task was to change the title of the sheet to make the sheet descriptive.
      > ![Inked1](https://user-images.githubusercontent.com/103915142/229225837-fb4612a0-b814-490f-ac5a-afda44e3617f.jpg)

3.    I explored the dataset and realized that there are 18,980 rows and 77 columns. I also saw that we had two empty rows and columns and proceeded to delete them. 
      > ![3](https://user-images.githubusercontent.com/103915142/229226637-ba7994a2-d366-4e87-8576-70b003ba2c8a.png)

4.    I also checked the name convention of every attribute name, changed column names that weren’t descriptive and made the naming format consistent.
      > ![1c](https://user-images.githubusercontent.com/103915142/229227442-fe69a0f4-9450-4f66-8eda-eb4247d8bd55.png)
      
5.    To make my table look beautiful, I added a background colour to the header, bolded the text and froze the header row. I also added a borderline to the cells.
      Here is how it looks.
       Freeze Row                                                                                                        |  Style
      -------------------------------------------------------------------------------------------------------------------|-------------------------
      ![Inked2a](https://user-images.githubusercontent.com/103915142/229228376-e3720671-65fd-4585-b87e-d20ff5cd49e1.jpg) |  ![5a](https://user-images.githubusercontent.com/103915142/229229165-8e589188-5add-4f86-92dc-d6a12a56ac10.png)

6.    In the Player_Url, I observe that each link contains the actual names of the players while the Long_Name column has special characters on many players’ names.         Hence we use the SPLIT TO TEXT option to get the correct names for the Long_name. We use the delimiter “/”
      > Select the interested column, go to data and select "Split Text to Column"
      >> ![8a](https://user-images.githubusercontent.com/103915142/229231971-5ac97d0c-e425-4360-bd52-a096a2cd5dd8.png)
      
      We then copy the correct name and use the paste special option to paste the values in the Long_Name column. Finally, we notice that the names are in small             letters, so we use the PROPER function to fix it.
        Text Transformation                                                                                          |  Paste Special Values
      ---------------------------------------------------------------------------------------------------------------|-------------------------
      ![8a3](https://user-images.githubusercontent.com/103915142/229232805-44924dc5-135a-43d7-b456-f7cc50287377.png) | ![8a2](https://user-images.githubusercontent.com/103915142/229233242-b1f674df-7d55-4c2a-956a-76b64a647373.png)

7.    > ### HEIGHT AND WEIGHT COLUMNS
      a.	**The height** column should be strictly in centimeter, but we have two different units for heights (ft and cm). 
                  i. We start cleaning by filtering out the values in cm, so we are left with values in ft. 
                  ii. Create a new column and use the formular below to convert the ft&inch values to cm
            
            > =LEFT(O795, FIND("'", O795)-1)*12+ABS(SUBSTITUTE(MID(O795,FIND("'", O795)+1, LEN(O795)), """", ""))
            
      > ![Inkedheight_conversion](https://user-images.githubusercontent.com/103915142/229244209-f4952507-d8ef-4d73-9d4e-42f03da56396.jpg)
      
      b.    **The weight** column ought to measured in lbs only, but we can see values with kg and lbs units. To correct this, we have to
                  i. We would filter by condition, values containing "kg"
                  ii. Then use the find and replace option to remove "kg" from the affected cells
                  iii. Create a new column and use the CONVERT function to convert kg to lbm.
                  
     
      Filter By Condition                                                                                                     |  Result
      ------------------------------------------------------------------------------------------------------------------------ |-------------------------
      ![Inkedweight_a](https://user-images.githubusercontent.com/103915142/229247273-e327805b-1ccc-46d2-8a56-746bb32eba19.jpg) | ![weight_b](https://user-images.githubusercontent.com/103915142/229246278-968e67ca-de52-4dc2-be87-fa123d8a388e.png)

      __*Don't forget to adjust the decimal place to 0.*__
            
8.    > ### VALUE, RELEASE CLAUSE, and WAGE
      These columns are player's worth in dollars but we see that the column is in Test format with the wrong formatting. Hence, our job here is to change the euro           sign to dollars, convert "K" and "M" to Thousand and Million numerically.
      
      BEFORE
       > ![9d](https://user-images.githubusercontent.com/103915142/229251688-142dcf84-c4d7-4ebe-bc9d-78f29cae773d.png)

      Solution for Value
      > ![Inked9d2](https://user-images.githubusercontent.com/103915142/229252188-3f4966ad-b542-4cb7-b306-7e4134c5432c.jpg)
      
      But our solution came with a problem, some values do not contain "M" and "K, which was used in our formular to change the format. This led to a #VALUE ERROR
      > ![9d3](https://user-images.githubusercontent.com/103915142/229254627-8d10a0b2-3e6e-4674-a715-c972734f09cb.png)

      The Correct Solution
      We use the IFERROR statement to catch and handle errors in the formular.
      > ![9d4](https://user-images.githubusercontent.com/103915142/229254736-f7b5acc0-3155-4bd5-8a99-c796666d2e51.png)
      
9.    > ### WEAK FOOT, SKILL MOVES, AND INJURY RATING
      we observe that there are special characters in this columns, so we proceed to use the find and replace option to clean the columns.
      > ![10a2](https://user-images.githubusercontent.com/103915142/229255834-aae5bc61-b4a2-4edf-9e6d-6dec3bdd84d6.png)

10.   > ### HIT
      a.    We observed that there aree blank cells in the hit column. I assumed that the blank cells means that the players had no viewers on the website. 
      An efficent way to go about this cleaning, is to filter the Hit column to display only blank cells, and autofill the cells with zero.

      Blank Cells                                                                                                     |  Replacing with Zero
      ---------------------------------------------------------------------------------------------------------------|--------------------------
      ![10b1](https://user-images.githubusercontent.com/103915142/229256387-62ce0a23-622c-432f-9bca-84dd28975d92.png) | ![10b2](https://user-images.githubusercontent.com/103915142/229256400-8640e9e6-334d-4252-9bf2-ae8118ed5275.png)
      
      b.    We also see some inconsistency in the data format of the Hit column. We fix it like we did with Value column
     
      BEFORE                                                                                                          |  AFTER
      ----------------------------------------------------------------------------------------------------------------|--------------------------
       ![10b](https://user-images.githubusercontent.com/103915142/229257130-17182523-dc93-4ad3-a2c9-a14ada181035.png) | ![10c2](https://user-images.githubusercontent.com/103915142/229257160-c00e9a08-760b-4764-93d7-f8b1a3449bc8.png)
       
       > **SYNTAX:** ![10c](https://user-images.githubusercontent.com/103915142/229257711-009b8cea-ac74-491c-a9aa-2007f3bab52b.png)

11.   > ### JOINED COLUMN
      Select the Joined column -> Format -> Number -> Date
    
    
       BEFORE                                                                                                    |  AFTER
       ----------------------------------------------------------------------------------------------------------------|--------------------------
       ![14a](https://user-images.githubusercontent.com/103915142/229258040-4ce58092-1d41-476d-93cf-0452e748722f.png) | ![14a2](https://user-images.githubusercontent.com/103915142/229258467-edce7f03-e9ef-4f87-957f-643edb8e77e6.png)

12.   For easy assessment, I moved the "Best Position" column close to the "Positions" column
      > ![16](https://user-images.githubusercontent.com/103915142/229258627-44f2bd93-d632-4d77-b73c-6e512a9d3185.png)
 
13.   > ### CLUB COLUMN
      inconsistent data was noticed in some of the cell, as we detect cells with a numeric value before the club name, and upon research, names as such (with the number) doesn't exist. So we used the Find and Replace option to replace them.
      
      ![clubs1](https://user-images.githubusercontent.com/103915142/229269798-43378aef-810e-4a94-930f-8d60e3574d40.png)


14. ### GOOGLE SHEET BONUS
      With Google sheet, there are options available to assist with cleaning dataset. 
      
      > Select all the data -> Click on Data on the ribbon -> locate Data Clean-up
           
     A                                                                                                                     |  B
     ----------------------------------------------------------------------------------------------------------------------|--------------------------
      ![Inked12b1](https://user-images.githubusercontent.com/103915142/229267899-1bfccf2a-53b5-48f3-818b-0b63d91a2bb4.jpg) | ![12b2](https://user-images.githubusercontent.com/103915142/229267919-c03e6b4c-9160-4d1f-ab47-0c36291937ae.png)
      
     ### A. **Clean-up Suggestions:** 
     This provides a dialog of possible cleaning that needs to be done. In our case, the clean-up suggested that there are extra whitespaces in all cells of the Club         column. Yep Yep, apparently it wasn't obvious and I didn't suspect it enough to check for it. Thanks to Google sheet emoji for adding these features. 
     
      ![Inked12a2](https://user-images.githubusercontent.com/103915142/229268470-118add04-870e-48a8-bc59-8fcc7463b658.jpg)

      > But I have  trust issues, and needed to confirm the suggestions were right, so I went on to create a new column, and used the LEN function to to check the            lenght of the first cell, after counting it myself. I figured it ought to be 12 in length, but the LEN function returned 16. So yes!, the suggestion was right          afterall. 
      >>I checked the lenght of the updated list in the club column after triming the extra spaces and it returned the correct lenght.
   
   
    Before                                                                                                     |  After Clean-up
    ----------------------------------------------------------------------------------------------------------------|--------------------------
    ![12a](https://user-images.githubusercontent.com/103915142/229268672-29b8eb8b-dc8d-4f9e-a118-1f1441fdfc5a.png) | ![12a3](https://user-images.githubusercontent.com/103915142/229268737-99ee9130-b823-40db-91fb-6cb3f78291ea.png)

      
      ### B. **Remove Duplicates:** 
      This is very delicate, because in the dataset, it was observed that some players were appeared twice or more BUT, they had unique identifiers, and their contract       and other features weren't the same. So it will be wrong it we removed duplicates across every row. Instead, we will only use the ID column to check if there are       repeated ID's. 
      > Upon checking, we find out that there are no duplicated ID's, meaning every ID is a unique identifier to every player and their features at that time.
      
      
      ![12c](https://user-images.githubusercontent.com/103915142/229269299-696e8c93-68da-475d-a909-becdaf957320.png)
      
      ![12c2](https://user-images.githubusercontent.com/103915142/229269308-107e8cf2-b284-4b0e-b037-9db1e848de90.png)
      
      ### C. Trim Whitespace
      >Select all data to trim extra whitespaces all through.
      
      ![12b](https://user-images.githubusercontent.com/103915142/229269839-99ec9396-0895-4c43-9457-238c1c7f4e90.png)

__**The ID contains numeric values of different lenght, but we won't be doing any cleaning here because every ID corresponds to the id on the player's url**__


15. ### CONTRACT COLUMN

16. ### OUTLIERS
      > 1. The Age column has an outlier
      >> ![Inked17a](https://user-images.githubusercontent.com/103915142/229270289-2130e4c1-ce63-4af6-97b5-1bc013442afa.jpg)
      
      > We see that there's a player whose age is 53 which is a significant distinct age in the data. It is expected that players ought to retire by around the age of        35-40.  With this findings, I proceeded to research the ages of player above the age of 30 years. 
      >>According to a blog site, the age is correct and there are few players above the age of 35 still on the field. I also discovered that the oldest player is 60         years as at 2023. So the outlier stays because it is correct and needed in our analysis.
      __https://sportsbrief.com/facts/top-listicles/15672-ranking-top-12-oldest-playing-footballers-playing/#:~:text=Football%20is%20quite%20an%20energy,players%20usually%20struggle%20with%20retirement.__
      
      >2. Overall Analysis and Best Overall
      The column isn't in it right format, as it ought to be in percentage form. So I created a new column, to do the conversions and also formatted it to %
      >>![17c](https://user-images.githubusercontent.com/103915142/229271025-2bb7dc75-cbe0-4649-a776-7f7e9f52c700.png)
     
     Graphical Representation for Overall Analysis
      
       ![Inked17d](https://user-images.githubusercontent.com/103915142/229271145-83973f4b-6726-4773-a2fd-abf27e244c52.jpg)
       
      3. Player Potential
      Like we did to overall analysis, we would convert the player potential column to a percentage format.
      
      Graphica Representation of the Player potential column.
      
      ![17d2](https://user-images.githubusercontent.com/103915142/229271601-bce386ec-0c0c-41c7-ad2d-43c7915ba7b3.png)
      > the column is rightly skewed. which means we have more data points to the above 69%. But the average percentage by frequency of the player potential column is        69%.
      
      









































