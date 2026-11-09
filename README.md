# econ3916-lab15-bias-variance

# The Bias-Variance Tradeoff: Choosing How Flexible a Model Should Be

## Objective

In this lab, I explored how model complexity affects bias, variance, and prediction error, and how cross-validation helps me choose a polynomial degree.

## Methodology

- I used simulated data with a known true curve and fitted polynomial models with different degrees.
- I used 200 fresh samples for each of six degrees to estimate bias squared and variance.
- I compared training MSE and held-out MSE on 2,000 new data points for polynomial degrees 1 to 15.
- I used 5-fold cross-validation to select a polynomial degree and compared the errors across folds.
- I used nested cross-validation to check whether the lowest CV error gives a fair estimate of prediction error on new data.
- I wrote a function called `kfold_mse()` to calculate average CV MSE for different degrees and numbers of folds. I tested it using 10-fold cross-validation.
- In the optional extension, I kept the polynomial degree at 9 and increased the training sample size to see how more data affects overfitting.

## Key Findings

- **Bias and variance:** At degree 5, the variance was 0.0180. At degree 15, it increased to 0.0994. This shows that more complex models can have higher variance even when their bias is very low.
- **Training vs. held-out error:** The lowest held-out MSE occurred at degree 5. Increasing the degree further reduced training error but did not improve prediction on new data.
- **5-fold cross-validation:** CV selected degree 4, with an average MSE of 0.1401.
- **Nested cross-validation:** The nested CV MSE was 0.2070, higher than the lowest 5-fold CV MSE. This suggests that choosing the lowest CV error can give an optimistic estimate.
- **10-fold cross-validation:** The MSE was 0.1409 for degree 4 and 0.1457 for degree 5. Degree 4 performed better in both 5-fold and 10-fold CV.
- **Optional extension:** When I increased the training sample size, the gap between training and held-out MSE became smaller. This showed me that more data can help reduce overfitting, although it cannot remove noise or model bias by itself.

Overall, I learned that a more complex model is not always better. Cross-validation helps me choose a model that performs well on new data instead of only fitting the training data.
