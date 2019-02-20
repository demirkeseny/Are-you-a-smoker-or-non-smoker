# Are you a smoker or non-smoker?
> Author: [Yalim Demirkesen](https://github.com/demirkeseny)
>
> Presentation: [Youtube Link](https://www.youtube.com/watch?v=hFZSm_e9tMc&t=6s)



### Problem Statement

Nowadays humankind is under a massive threat. We are in danger of becoming more and more
distanced from our beloved ones and having less and less relations. That fact is a serious threat for
families because the generations cannot follow each other anymore and the bonds get weaker and
weaker. Unfortunately, the cause is not in this paper but reading this paper will enable parents to feel
slightly safer and take action if needed.

This increased distance might be unpredictable in 21st century. We are losing the ability to talk and
argue because of technology since our best friends are replaced by cell phones. Technology made even
one end of the world much closer as it was seen 30 years ago. Children leave their country in much
earlier ages to go to universities or even high schools. Especially for younger people that might be the
first time they truly discover what is going on outside of their bubble created by their parents. On one
hand, it offers a unique opportunity to improve but on the other hand it might be dangerous. Since the
protective shield of the parents has disappeared, children can get unhealthy habits easily. The easiest
example can be smoking. The effort of healthy parents for all those years might be ruined by a close
college friend who is smoking.

Since parents might want to find out whether their children are smoking or not, the machine learning
algorithms might assist them achieving this goal. Asking the children straight forward whether they are
smoking or not, is basically asking them to lie. This is not realistic to expect the true answer.

In this paper four machine learning algorithms are used to create models to predict the smoking habits
of teenagers. If successful, the model will be able to predict and classify the smoking habits of young
people to four groups;

- Never smoked
- Tried smoking
- Former smoker
- Current smoker

This paper will allow them to act accordingly and prevent the smoking habits of their children to grow, if
there are any. That’s why it can help tons of people to stay healthy and functional for a longer period. If
the smoking habits are tackled in younger age, person can be prevented from being a long-time smoker.
As it can be seen from the Figure 1, tackling the smoking habits in early ages helps a lot. Considering that
the start age is more commonly under 20, parents can help their children and show the way to health.
When we consider that our data is collected from participants from age 15 to 30, the graphs below show
some similarity.

### Data

The data involves two csv files:

- responses.csv consists of almost 1000 rows and 150 columns. 139 of these are integer and 11 of
  them are categorical. To make the analyzing process faster, the names of the columns are
  shortened.
- The actual question or full name of the columns can be found in columns.csv.
  Data has missing values and to have a correct prediction in the end we must use one of the imputation
  techniques. Those values might also vary from group to group. 

The groups in the data are:

- Music Preferences (19)
- Movie Preferences (12)
- Hobbies and Interests (32)
- Phobias (10)
- Health Habits (3)
- Personality Traits, Views on Life, Opinions (57)
- Spending Habits (7)
- Demographics (10)

### Modelling

#### K-Nearest Neighbors

In the training stage of kNN, I came up with 5-fold cross validation. So that I can build 5 models and test their accuracies. To create the folds, I basically created index and took 80% of data as training and 20% as
testing. That approach is applied in all the models in all the algorithms. To generate this partition, I
benefited from the seq() function. By increasing 5 points in one step, I ended up with 5 clusters. When
these values are subtracted from the data set, we reached our testing dataset.

With the help of kNN() function, I stated my training dataset, testing dataset and class, which is my
target value (smoking habits). At last, k parameter is decided. The square root of my observations is
almost 31. So, I picked 31 as k value. In other words, my model became 31-nearest neighbors.

To improve the mode, I modified the k values. That enabled the model to verify the number of closest
neighbors to check. For instance, in the case of 31 nearest neighbors, model gets a point in space;
detects the closest 31 points and predicts the class of the new entry based on the class of that 31 closest
neighbors.

#### Decision Tree

Decision tree that we created is a little bit messy but it is close to what we have expected since there are
too many features. First, I needed to convert my target values to factors for function to accept them.
Then using C5.0() function, I got my decision trees. That is a huge tree with lots of branches. 

#### Support Vector Machine

For ksvm() function to run we needed to convert our training and testing datasets into matrixes. We
initiated what we address as target value and determined the predictors. Basically, I included all of
them. After running the ksvm functions, I was able to have a prediction column. Next step was
comparing those columns. To see how many values match I developed a counter mechanism, which
counts the true matches between predictions and actual target values.

In the second step, I tried to improve the mode by adding kernel parameters. “rbfdot” provided us a
better prediction. The reason is that by Support Vector Machine’s feature, we were able to switch from
linear regression to curvature functions that go near the points in the space and fit them better.

#### Clustering

In order to work with clustering algorithm, I revised the testing and training datasets once again since it
requires to have the target value in the training set. Then I came up with two clusters, determined their
centers and checked how many falls into which cluster. For each and every point, I calculated a distance
from each point to two clusters’ centers. According to the comparison that I made, an item falls into a
certain cluster if its total distance is smaller to that one.

#### Linear Regression

In the last approach, I implemented the linear regression model. First, I revised my datasets to build the
function. Then, used the lm() function and created an equation. With the help of that equation, I tried to
predict again the smoking habits. This time the linear regression provided me a continuous outcome,
which I needed to convert to integers. For a basic classification, I created the if statement that helped
me to assign the values larger than 0.5 to 1 and smaller than 0.5 to 0.

To improve the model, I used backwards elimination technique. For this process, I excluded the
predictors with a p value higher than 0.05, which suggests that these are not significant estimators. That
helped me to revise my accuracies outcomes.

### Evaluation

For Evaluating the performances of the models, cross tables or accuracy functions are used. They serve
for the same purpose. That means although we used cross table or accuracy functions they have the
same scale of information. From the below table we can compare the outcomes of these functions.

| Algorithm         | Min  | Max  |
| ----------------- | ---- | ---- |
| kNN               | 58%  | 70%  |
| Decision Tree     | 54%  | 66%  |
| SVM               | 58%  | 62%  |
| Clustering        | 35%  | 63%  |
| Linear Regression | 51%  | 54%  |

Determining the accuracy from the count function, I created a counter variable. That number is
increased by one each time the prediction and actual value matches.

Cross table is easier to visualize for sure. There are two labels; actual and predicted. The values that lie
on the diagonal are the ones that predicted correctly. The rest are the failures. From the below cross
table we can drive the accuracy just by looking. The accuracy here is the ratio of correctly replaced over
all of observations, which makes 98/184.

Different from what we have expected the results don’t show any indication of high accuracy. Still if we
need to pick one of these approaches that should be kNN. Although it is a simple and even “lazy”
algorithm, it is widely accepted.

### Conclusion

70% is still an important measure. Without using any models, we have 50% chance of guessing it. With
the help of models, we increase our chance by 20% but still there is a huge room of improvement. Still,
we are capable of analyzing as much as data shows us. That made me think about the dataset and I
improved an argument saying that if the accuracies are low, that shows that our data is not biased. In
other words there might more answer of “3” to scale questions than anticipated. That’s why I ran an
analysis where I counted all the numbers. 

It is true that there are much more than anticipated “3”. They block us from making a proper analysis
since they don’t show any preference. Maybe next time in a survey analysis, it might be considered to
drop all 3’s. Since they don’t help us. Almost 26% of data being data shows that participants are more
hesitant.

As a conclusion, it can be noted that this model of kNN, can be implemented in real life but there needs
to be more improvements because the social aspects that the outcome of this model lead is very
essential. Parents might shape their attitude towards their children considering this model.