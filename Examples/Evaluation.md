# Evaluation 
The part of the field to determine which how a model performs and how to take action.
Each of these explained by example and how to take action and result after action 

## Bias
### Problem
The problem in bias is that the model is too simple to actually fit the data.

#### Example


### Solution
Solutions to High bias are: 
* Add more features
* Add polynomials
* Reduce Regularization


## Variance
### Problem
The problem with variance is a model that is too fit on the data. The model does not perform as well generally,
or in the scope of experimenting, on the test data. 

#### Example


### Solution
The solutions to variance are: 
* Use more data
* Apply regularization
* Use less features

When these solutions are applied. The model will perform better on the test set. 

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
