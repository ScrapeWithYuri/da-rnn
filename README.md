## Yuri Updates

I ran the trainer and saved my model [here](https://github.com/ScrapeWithYuri/da-rnn/blob/master/darnn-improved/checkpoints/best.pkl).

The biggest issue with these types of models is that they generally lag the price of the target by one time step. By doing so, the RMSE is really low, but the result is not informative whether the predicted price will go up or down relative to the target. For instance, I tested my model, saved the results, and compared whether:

 1) The predicted value for tomorrow will be greater than the predicted value of today vs. actual
 2) The predicted value for tomorrow will be greater than the current value of today vs. actual
 
 The results are not promising, as 1) is 50.8% accuracy and 2) is 48.3% accuracy
 
 My results are saved [here](https://github.com/ScrapeWithYuri/da-rnn/blob/master/darnn-improved/best.xlsx).

## DA-RNN

This repository holds the reproduction codes for [A Dual-Stage Attention-Based Recurrent Neural Network for Time Series Prediction-IJCAI2017](https://arxiv.org/pdf/1704.02971.pdf). 

In `./darnn-based`, we reproduce the work in this paper on the Nasdaq 100 dataset. Besides, we offer a modified version in `./darnn-improved` to solve the instability of the original model during training period. The requirements are Python 3.6 and Pytorch 1.0 (or higher).

## Models

1. `./darnn-based`: the origin model introduced in [A Dual-Stage Attention-Based Recurrent Neural Network for Time Series Prediction-IJCAI2017](https://arxiv.org/pdf/1704.02971.pdf). 
2. `./darnn-improved`:  we found the attention weights used in encoder are  highly unstable in the trainning period when we try to reproduce the results. To solve this issue, we added an additional attention layer in encoder. With this modification, the first attention layer in encoder is responsible for learning the highly variable dependences, as well as the second attention layer is responsible for learning the stable and long-term dependences.

### Results

Limited by data acquisition, we only tested the performance of two models on the Nasdaq100 dataset, and the results are shown in the following table:

|     Models     | RMSE (Nasdaq100) |
| :------------: | :--------------: |
|     DARNN      |       2.68       |
| DARNN-improved |       2.49       |

## Content

These two file folders both contain all the code and data needed to run the model. You can use any one of them to start the trainning period.
