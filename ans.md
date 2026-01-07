## Dataset exploration

1. __What is the maximum fare?__

>answer: $159.25

2. __What is the mean distance across all trips?__

>answer: 8.2895 miles

3. __How many cab companies are in the dataset?__

>answer: 31 cab companies

4. __What is the most frequent payment type?__

>answer: Credit Card

5. __Are any features missing data?__

>No

## CORRELATION MATRIX

6. __Which feature correlates most strongly to the label FARE?__

>TRIP_MILES

7. __Which feature correlates least strongly to the label FARE?__

>TIP_RATE

### Define functions to build and train a model

8. __How many epochs did it take to converge on the final model?__

``` 
Use the loss curve in the model plot to see where the loss begins to level off during training.

With this set of hyperparameters:

  learning_rate = 0.001
  epochs = 20
  batch_size = 50

it takes about 5 epochs for the training run to converge to the final model. 
```
9. __How well does the model fit the sample data?__

It appears from the model plot that the model fits the sample data fairly well.

## Experiment with hyperparameters

- Experiment 1: Increase the learning rate to 1.0 (batch size at 50). 
```
When the learning rate is too high, the loss curve bounces around and does not appear to keep moving to converge on each iteration. Besides, the predicted model doesn´t fit the data very well.
```
- Experiment 2: Decrease the learning rate to 0.0001 (batch size at 50). 
```
When the learning rate is too small, it may take longer for the loss curve to
converge. With a small learning rate the loss curve decreases slowly, but does not show a dramatic drop or leveling off. If we increase the number of epochs, the model will eventually converge, but it will take longer.
```
- Experiment 3: Increase the batch size to 500 (learning rate at 0.001).
```
Increasing the batch size makes each epoch run faster, but as with the smaller learning rate, the model does not converge with just 20 epochs. If we increase the number of epochs, the model will eventually converge.
```

## Train a model with two features
10. Does the model with two features produce better results than one using a single feature?
```
In order to determine which one produces better results, we need to compare their RMSEs. We notice that, on average, the model with one feature has an RMSE of 3.7783, while the one with two is 3.4499. We can conclude that, on average, the model with two features makes predictions that are about $0.33 closer to the observed fare.
```

11. Does it make a difference if you use TRIP_SECONDS instead of TRIP_MINUTES?
```
When training a model with more than one feature, it is important that all numeric values are roughly on the same scale. In this case, TRIP_SECONDS and TRIP_MILES do not meet this criteria. The mean value for TRIP_MILES is 8.3 and the mean for TRIP_SECONDS is 1,320; that is two orders of magnitude difference. In contrast, the mean for TRIP_MINUTES is 22, which is more similar to the scale
of TRIP_MILES (8.3) than TRIP_SECONDS (1,320).
```
12. How well do you think the model comes to the ground truth fare calculation for Chicago Taxi Trips?
```
the model is roughly close to a documented formula to determine cab fares.
```

## Use the model to make predictions
13. How close is the predicted value to the label value? In other words, does your model accurately predict the fare for a taxi ride?

```
Based on a random sampling of examples and comparing the values from PREDICTED_FARE with those from OBSERVED_FARE, we can observe that they are quite close. This is reflected in the low L1_LOSS value. Because of this, we can conclude that the model predicts the fare fairly well.
```