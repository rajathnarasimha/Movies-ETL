# Movies-ETL

# Assumptions:

# 1. modify wikipedia data by restricting it to only those entries that have a director and an IMDb link. We can do this with a list comprehension.
# 2. We’ve got some TV shows in our data instead of movies. We’ll want to get rid of those.
# 3. The different language columns are for alternate titles of the movie. Let’s combine all of them into one dictionary that has all the alternate titles.
# 4. There are quite a few columns with slightly different names but the same data, such as “Directed by” and “Director.”We need to consolidate columns with the same data into one column. 
# 5. Since we’re going to be using the IMDb ID to merge with the Kaggle data, we want to make sure that we don’t have any duplicate rows, according to the IMDb ID. We need to extract the IMDb ID from the IMDb link.
# 6. We want to remove which columns don’t contain much useful data.
# 7. Update the datatype of columns like, Box office should be numeric, Budget should be numeric, Release date should be a date object, Running time should be numeric.
# 8. Ideally, we’d want to be able to unscramble the rows and recover the data. But since we don’t know what caused the data to be scrambled, it’s also possible that even if we got all the data into the right columns, the data would still be corrupt. In fact, since we probably don’t want to include adult movies in the hackathon dataset, we’ll only keep rows where adult is False, and then drop the “adult” column.
# 8. Kaggle data looks just a little bit more consistent in the title names hence using the kaggle data and drop the wikipedia data.
# 9. Most of the runtimes are pretty close to each other, but the Wikipedia data has some outliers, so the Kaggle data is probably a better choice here. However, we can also see from the scatter plot that there are movies where Kaggle has 0 for the runtime but Wikipedia has data, so we’ll fill in the gaps with Wikipedia data.
# 10. The Wikipedia data appears to have more outliers compared to the Kaggle data. However, there are quite a few movies with no data in the Kaggle column, while Wikipedia does have budget data. Therefore, we’ll fill in the gaps with Wikipedia’s data.
# 11. Box office/revenue Keep Kaggle; fill in zeros with Wikipedia data.
# 12. Drop Wikipedia for release_dates.
# 13. There’s a trade-off here between the Wikipedia language data and the Kaggle language data. While the Wikipedia data has more information about multiple languages, the Kaggle data is already in a consistent and usable format. Parsing the Wikipedia data may create too many difficulties to make it worthwhile, though. This is another judgment call; there’s no clear-cut answer here. However, for better or for worse, decisions that save time are usually the ones that win, so we’ll use the Kaggle data here.
# 14. Drop Wikipedia for production company data as it is more inconsistent.

