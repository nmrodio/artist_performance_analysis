# **artist_performance_analysis**
------

## **Cleaning "Popular_Spotify_Songs.csv" file**

------


## **Performance of Collaborating vs Solo Artists**

--------

## **Top Month(s) to Release Songs**
**Question**: What is the most popular month to release a song?

**How does the code work:**
1) Imported dependency "calender" to allow for converting number of each month to the intuitive name of each month (Ex: 1 => January, 2=> February, etc...)
2) Used .value_counts() function to find the total counts of song released for each month of the year
3) Created a list called "month_num_list" to hold the numerical values of each month (1,2,3,4,5,6,....,12)
4) Created an empty list called "month_name_list" to hold the coverted names of the month from numerical values to names of the month to be pulled from later in the code
5) Turned the series "month_most_released_songs_series" created above from the .value_counts function into a dataframe called "month_most_released_songs_df" and then sorted the new dataframe by "released_month" column to have a dataframe with months in ascending order
6) Created a for loop to convert the numerical months values in "month_num_list" list to month names using the calender library imported above and then appending those month names into the empty list called "month_name_list"
7) Created a new dataframe called "new_months_df" with new intuitive column names labeled "Months" and "Song Counts" => Then reset the index to have the "Months" column as the new index for the dataframe
8) Using the "new_months_df" => a bar chart was created using the "Months" and "Song Count" column to visually show the months of the year and the total released song count of each month
9) Lastly, labeling and plt.xticks were applied to the graph to make it more visually appealing and intuitive for the viewer of the data

**Analysis**: January is the most popular month for artists to release their new songs with May being a close second

--------

## **Top Day(s) to Release Songs**
**Question**: What is the most popular day to release a song?

**How does the code work:**
1) Used .value_counts() function to find the total counts of song released for each day in a month
2) Turned the series "days_most_released_songs_series" created above from the .value_counts function into a dataframe called "days_most_released_songs_df" and then sorted the new dataframe by "released_day" column to have a dataframe with days in a month in ascending order
3) Created a new dataframe called "new_days_df" with new intuitive column names labeled "Days" and "Released Song Counts" => Then reset the index to have the "Days" column as the new index for the dataframe
4) Using the "new_days_df" => a bar chart was created using the "Days" and "Released Song Counts" column to visually show the days in a month and the total released song count of each day
5) Lastly, labeling was applied to the graph to make it more visually appealing and intuitive for the viewer of the data

**Analysis**: The 1st of the month is the most popular day for artists to release new songs with all other days being random based on artists preferences 

--------

## **Correlation of Shazam Charts vs Total Streams**
**Question**: Does the more times a song gets "shazamed" result in higher total streams?

**How does the code work:**
1) Created a smaller dataframe called "shazam_vs_streams_df" from the "cleaned_top_songs" dataframe with only necessary columns needed for regression analysis
2) Changed the format of number values in "in_shazam_charts" column to drop "," from numbers (Ex: 1,000 => 1000)
3) Filled all blank values in the "shazam_vs_streams_df" with "NAN" => Dropped the funky value "BPM110KeyAModeMajorDanceability53Valence75Energy69Acousticness7Instrumentalness0Liveness17Speechiness3" from the "streams" column ==> Then dropped all the "NAN" values from the "in_shazam_charts" column" ==> Final include "in_shazam_charts.dropna()" to make sure there where no more null values in the dataframe
4) Imported "from scipy.stats import linregress" into the code to allow for regression analysis
5) Coverted values in "in_shazam_charts" and "streams" columns from objects to numerical values using pd.to_numeric
6) Define the x ("in_shazam_charts") & y-axes ("streams") for scatter plot => Then defined the linear regression line ==> Created the linear regression line
7) Reassigned rvalue to a variable called "correlation for easier comprehension => Rounding the correlation result
8) Created the scatter plot from the define x & y-axes above
9) Creating a string value of linear regression line to plot on graph called "line_eq"
10) Plotted the linear regression line and linear equation on the scatter plot
11) Labeling and formatting was applied to the scatter plot to make it more visually appealing and intuitive for the viewer of the data => Formatted y-axis to hundred millions
12) Printed out a sentence above the scatter plot to illustrate the correlation of Shazam Charts vs Total Streams and then displayed the scatter plot
    Very weak positive correlation of Shazam Charts vs Total Streams (.00037): Having a song make Shazam Charts will have no effect on streaming success

**Analysis**: Very weak positive correlation of Shazam Charts vs Total Streams (.00037): Having a song make Shazam Charts will have no effect on streaming success

--------
