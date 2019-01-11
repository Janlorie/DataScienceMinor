# Evaluation 
The part of the field to determine which how a model performs and how to take action.
Each of these explained by example and how to take action and result after action 

## Bias
### Problem
The problem in bias is that the model is too simple to actually fit the data. An example for this would be the tests 
I have done on skewed data. For these tests I needed balanced data for all classifications. The problem with this is 
that we did not have many examples for 2 of the 4 classes in our data. It was good enough to search for the skewed 
data tests, but as a model it would not be sufficient. We only had 472 Training examples for this test. 

With such limited data, the model did perform not as well as the full on version with about 5000 training examples.
The scores, even with a balanced dataset 118 examples across the classifications, were significantly lower. 
Below the data for different models on different ratios. The scores in the table are the F1 Scores.

ratio| 	Logistic Regression	| Multinomial NB | Complement NB
---|---|---|---|
1         |0.66	|0.71 |0.71
2	      |0.60	|0.64 |0.59
3	      |0.65	|0.57 |0.54
4	      |0.74	|0.59 |0.49
5	      |0.68	|0.56 |0.53
6	      |0.76	|0.57 |0.55
Average   |0.68	|0.61 |0.57

![Graph of scores 3 vs rest](../Resources/Images/Scores-3-VS-Rest.png)

### Solution
Solutions to High bias are: 
* Add more features
* Add polynomials
* Reduce Regularization

This can be displayed by the F1-scores on the model with all training examples.
Below a table for the best results for the Logistic Regression, Multinomial and Complement NB. 

Logistic Regression | Multinomial NB | Complement NB
:---:|:---:|:---:
0.81|0.75|0.70

These results are with each, more than 10% increased on the cross validation score. So we can conclude that adding 
more data does indeed result in better scores if the model is biased.

## Variance
### Problem
The problem with variance is a model that is too fit on the data. The model does not perform as well generally,
or in the scope of experimenting, on the test data. 

#### Example
In the first few weeks we encountered this problem. We made a mistake with scoring the model and thought that the 
score we retrieved was on our test set but it actually was on our training set. This caused us to tune our model wrong. 
Which we later found out and retuned the models we did have. 

Unfortunately I was not able to retrieve the code associated with this problem we had. 

### Solution
The solutions to variance are: 
* Use more data
* Apply regularization
* Use less features

When these solutions are applied. The model will perform better on the test if the problem was high variance set. 

## Evaluation metrics 
Scoring models can be done in a variety of ways. Each of these scores serve to display a different type of 
evaluation for a model.The scores we used mainly to score our model are explained below. 

## Recall vs Precision vs F1-Score and Accuracy
These scores are specifically for classification problems. Recall and precision are ratios between predictions and 
classifications. These metrics are easily retrieved with Scikit-learn functions.

### Precision
Precision is the percentage of correct queried results in the amount of total queried results. tp / (tp + fp) 
In the case of a binary classifier, the precision for class 1 is: 1 as 1 / (1 as 1 + 0 as 1).

Example of precision used in code
```python
from sklearn import metrics
def get_precision_score(predictions, correct_classifications):
    return metrics.precision_score(correct_classifications, predictions)
```

### F1-Score
The F1-Score is a balanced mean of the precision and recall. This metric has been used as the main metric by us for 
evaluating the different models we tested. 

Example of F1-score in code
```python
from sklearn import metrics
def get_f1_score(predictions, correct_classifications):
    return metrics.f1_score(correct_classifications, predictions)
```

### Accuracy
Percentage of correct predictions in the total number of predictions made

```python
from sklearn import metrics
def get_accuracy(predictions, correct_classifications):
    return metrics.accuracy_score(correct_classifications, predictions)
```

### Recall
The recall score is the result of in the case of a binary classifier: true positives / (true positives + false negatives)

Example of recall used in code
```python
from sklearn import metrics
def get_recall(predictions, correct_classifications):
    return metrics.recall_score(correct_classifications, predictions)
```


