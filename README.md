<img src="https://bit.ly/2VnXWr2" alt="Ironhack Logo" width="100"/>

# Title of My Project
*Sentiment Analysis in the NYT headlines*

*[Data Analytics, Ironhack Barcelona & 20/12/2019]*

## Content
- [Project Description](#project-description)
- [Hypotheses / Questions](#hypotheses-questions)
- [Dataset](#dataset)
- [Cleaning](#cleaning)
- [Analysis](#analysis)
- [Model Training and Evaluation](#model-training-and-evaluation)
- [Conclusion](#conclusion)
- [Future Work](#future-work)
- [Workflow](#workflow)
- [Organization](#organization)
- [Links](#links)

## Project Description
This project is an approach on how to apply sentiment analysis to journalistic headlines and pieces of news. Precisely, it will analyse the articles published by the New York Times newspaper during eight months.

I chose this topic because journalism has always been looked upon with suspiciousness. In the United States, this feeling has increased with the rise of Donald Trump to the Presidency and his attacks against the media. The New York Times is one of the targeted newspapers by Trump. 

These tensions are an increasing phenomenon globally. That’s the reason why I wanted to analyse the New York Time pieces of news, bearing in mind that the model could be used with any media and context.


## Hypotheses / Questions
* I wanted to see how accurate a model of machine learning could be when fed with headlines and other texts labelled as containing positive or negative words.
* It could be applied to better profiling of potential subscribers. A business applied model could consist on analysing what kind of articles a casual reader clicks on. Thus, turn his or her interest into positive labelled articles in order to keep offering them similar information to get to make them subscribers.
* I wondered if a Naïve Bayes classifier could recognize sets of words as conveying a positive or negative approach, which would make it possible to classify other kinds of word-based interests. 

## Dataset
* I got the data from a Kaggle dataset. There were all the articles (headlines and snippets of text) published in the paper edition of the NYT from January to April from 2017 and 2018. In total, there were roughly 8.400 pieces of news, accessible via csv.

* The dataset contained the article id, the number of words it contained, the headline, a bit of the beginning of the text and data related to its publishing, as its author or authors or the day of publication, among other information.

## Cleaning
In the first place it must be said that the objective of the data cleaning was, in this case, to obtain a set of meaningful words. Since the Naïve Bayes classifier is a supervised algorithm, it needs a labelled column to compare with. This is a column that will be called label. In it, there will be placed the negative or positive assignment of the headline plus its piece of text. This labelling will be explained further on. But to achieve it, in sentiment analysis sentences are analysed by their meaningful words, so we need to get reed of stop words and other characters.

To achieve the aforementioned goal, I imported the csv documents from the dataset to table format in Excel sheets. I did so to understand the data at a first sight before knowing if it would suit to my interests and whether I would import it to the Jupyter Notebooks or not. This Excel sheets can be accessed in the Data folder in the repository.

Once imported them to a Jupyter Notebook, I concatenated all the datasets. Then I dropped all the unnecessary columns. Unfortunately, 671 rows had a headline deemed unknown, so I dropped them too.

When I had this basic data cleaning, I ended up with two main columns: headlines and snippets. These two columns had the same data cleaning applied. In order to obtain the words to analyse it I created several functions to break sentences into words, and remove stop words and useless characters and non-alphabetical strings. All this was added to a new column, called tokens, combining the result of the functions applied to both headline and snippet columns.

Then, I applied a function that reads the Hu and Liu Lexicon to determine whether each piece of news had a positive, neutral or negative approach. This is done by counting which kind of sentiment words (according to the Lexicon) predominate in each text. A new column is created with the result, called label_headline.

In the next folder, called 4. Analysis, the neutral pieces of news are removed. Finally, since the data from the previous Jupyter Notebook was read from a csv, the former list in tokens was now a string and had to be split by words again.


## Analysis
* The Naïve classifier was the supervised algorithm I found most useful for my analysis. For every piece of text it analyses, the features are inserted in the shape of a tuple. On the one hand, this tuple needs a dictionary with the words of the text and a Boolean determining whether they appear or not in a list of the most common words (that we have also gathered in another function). On the other hand, it takes the labels from label_headline.

## Model Training and Evaluation
*Include this section only if you chose to include ML in your project.*
* I trained the model with the 80% of the data. It gives a result of around a 79% of accuracy. This is a high result for a Naïve Bayes classifier, though the labelling was probably not the most ortodox, as it counted positive and negative words.

## Conclusion
* The results show that sentiment analysis from headlines and pieces of news can be analysed as much as other kind of texts more frequently used. We saw that, with an accuracy of roughly 80%, we classify correctly by labels.

* Therefore, sentiment analysis could help the NYT and other media to categorize their information. As proposed on the hypothesis of this document, newspapers could also profile accurately the news that might interest each of their kind of readers. Thus, they could do a better marketing or send them more suitable newsletters.


## Future Work
In order to improve the method, it would be interesting to obtain more data. 

Apart from that, when it comes to the probability ratio of a word appearing in positive or negative context, the polarity could be relativized by a Laplace smoothing.

The way of labelling the positive and negative news it could also be improved.

## Workflow
I posed myself a question on how sentiment analysis works and tried to find an appropriate dataset.

Once I had this, I started to investigate on how to analyse and represent Sentiment Analysis in machine learning.

## Organization
The repository is ordered by numbers according to the steps I followed.

On the first place there is a folder with the data. In the second folder there is most of the data cleaning, specially when it comes to the removal of columns and rows of the dataframe.

In the third folder there is the preparation of the data. And the forth has some preparing too, and the final preparation for the model and its results.

## Links



[Repository](https://github.com/JordiJordana/Project-Week-8-Final-Project)  
[Slides](https://docs.google.com/presentation/d/1TMoor4Ucwi7OcfiCGD1hRzdIKhJ_aNMIic2qGmifDSc/edit?usp=sharing)   
