# Trump_Speeches

## Overview
This project will examine Donald Trump's word use in all his Presidential speeches, addresses, and appearances from his inauguration (January 20th, 2017) to March 20th, 2018. We hope to predict whether or his not his speech language (sentiment and policy word use) has any impact on the change in his approval rating. We were able collect 1020 speeches which we scraped from the American Presidency Project (http://www.presidency.ucsb.edu/index.php). We pulled approval and disapproval ratings from Project 538 (https://projects.fivethirtyeight.com/trump-approval-ratings/). 

## Process
We began by first having to write code to pull the URL for each and every speech. With 1020, we could not manually copy and paste each URL into a list, so we had to be able to pull out the index and attach it to the base URL. After that, we had to iterate over each link and pull out particular information from the speech, i.e. the date of the speech, the title, and the text. Once we have the raw text, we have to modify it in a way that produces single, individual words. This entails getting rid of punctuation and symbols and making sure every letter is in lower case. The reason for this is because Python, and most coding languages, are strict in that two strings are equal only if each position in that string contains the same exact symbol. The language is not flexible enough to understand that 'Word' and 'word.' are not the same thing. Typically, you also want to remove suffixes and prefixes, since again the language is not as flexible. However, for our purposes this was not entirely necessary. We now have single cleaned words that we can run through the count vectorizer function. This powerful function takes a string represented as a document and counts the instances that each individual word occurs in that string. We then pass that into a Data Frame and we then have a bag of words model. If we were using the bag of words model, where each observation represents a document and each variable represents a word, we would want to remove those suffixes and prefixes to get accurate counts for each word. 
From here, we have our untidy data set that needs to be cleaned. We have multiple corpora in which we want to see how many of these words are used by Trump. We can write a function that adds every instance of Trump using a word in a given corpus. This leaves us with individual columns for each variable we have, which we use to create a single data frame. We can then combine this speech data frame with the approval data frame that we have from Project FiveThirtyEight. The final cleaned data set has a document as each observation and the counts of words the speech used from a corpus as a variable. In total, we have two outcome variables: approval and disapproval ratings for the President; there are 10 sentiment variables and 8 policy variables that will be our predictors for our model.  

