# OPER3384 &nbsp; <img src="https://upload.wikimedia.org/wikipedia/en/0/00/Boston_College_seal.svg" width="30" height="30"> &nbsp; Predictive Analytics

[![badge](https://img.shields.io/static/v1?label=Semester%20Project%20%20%E2%80%A2%20%20Project%20Team%2010&message=GitHub%20Repository&style=plastic&logo=GitHub&color=blueviolet)](https://mybinder.org/v2/gh/tavlarios/OPER3384/HEAD?filepath=IMDB%20Project.ipynb)


## Team Members
- Wendy N. Merchant
- Rebecca L. Redmond
- George N. Tavlarios
- John L. Trotto


## Project Assignments

| Badge | Deliverable \# | Description
|:-------:|:-:|---|
| [![badge](https://img.shields.io/static/v1?label=Proposal%20Memo&message=PDF&style=plastic&logo=Adobe%20Acrobat%20Reader&color=informational)](https://github.com/tavlarios/OPER3384/blob/main/Team%2010%20%E2%80%93%20Project%20Proposal%20Memo.pdf) | 1 | *1-2 page memo introducing your data and proposing several business questions for further research.* |
| [![badge](https://img.shields.io/static/v1?label=Update%20E-Mail&message=PDF&style=plastic&logo=Adobe%20Acrobat%20Reader&color=informational)](https://github.com/tavlarios/OPER3384/blob/main/Team%2010%20%E2%80%93%20Assignment%202%20Final.pdf) | 2 | *1-page business e-mail providing findings from preliminary data analysis with 1-page summary “attachment”.* |
| [![badge](https://img.shields.io/static/v1?label=Read%20and%20Go%20Slides&message=PDF&style=plastic&logo=Adobe%20Acrobat%20Reader&color=informational)](https://github.com/tavlarios/OPER3384/blob/main/Team%2010%20-%20Assignment%203.pdf) | 3 | *8-10 powerpoint slides meant as a “read-and-go” summary of your project findings and conclusions.* |


---

## Dataset

In addition to the variables from the original dataset, we calculated expected values of the quantitative variables, based on each movies' categorical attributes. These include:
  - ```ZEV_Rating_Actors``` – Expected Value of Rating, based on z-score of mean Rating of all Actors' previous movies
  - ```ZEV_Votes_Actors``` – Expected Value of Votes, based on z-score of mean Votes of all Actors' previous movies
  - ```ZEV_Metascore_Actors``` – Expected Value of Metascore, based on z-score of mean Metascore of all Actors' previous movies
  - ```ZEV_Revenue_Actors``` – Expected Value of Revenue contribution for each involved actor (as a percentage of all previous movies), based on z-score of mean contribution of all Actors' previous movies
  
  - ```ZEV_Rating_Genre``` – Expected Value of Rating, based on z-score of mean Rating of all Genres of the movie
  - ```ZEV_Votes_Genre``` – Expected Value of Votes, based on z-score of mean Votes of all Genres of the movie
  - ```ZEV_Metascore_Genre``` – Expected Value of Metascore, based on z-score of mean Metascore of all Genres of the movie
  - ```ZEV_Revenue_Genre``` – Expected Value of Revenue contribution for each Genre listed, based on z-score of mean contribution for previous Genres
  
  - ```ZEV_Rating_Director``` – Expected Value of Rating, based on z-score of mean Rating for a Director's previous movies
  - ```ZEV_Votes_Director``` – Expected Value of Votes, based on z-score of mean Votes for a Director's previous movies
  - ```ZEV_Metascore_Director``` – Expected Value of Metascore, based on z-score of mean Metascore for a Director's previous movies
  - ```ZEV_Revenue_Director``` – Expected Value of Revenue contribution for a Director's previous movies, based on z-score of mean contribution for a Director's previous movies
  
  - ```Top_Director``` – A binary flag indicating whether or not a movie's director was in the top 15 directors, by number of movies in the dataset.
  
  *Note that "Revenue contribution" is the portion of revenue attributed to a given factor peer (e.g., ```Baba Booey```), as a percentage of all Revenue generated for all peers (e.g., ```Directors```).*

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Description</th>
    </tr>
    <tr>
      <th>Column</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>```ZEV_Rating_Actors```</th>
      <td>Expected Value of Rating, based on z-score of mean Rating of all Actors' previous 
movies</td>
    </tr>
    <tr>
      <th>```ZEV_Votes_Actors```</th>
      <td>Expected Value of Votes, based on z-score of mean Votes of all Actors' previous 
movies</td>
    </tr>
    <tr>
      <th>```ZEV_Metascore_Actors```</th>
      <td>Expected Value of Metascore, based on z-score of mean Metascore of all Actors' 
previous movies</td>
    </tr>
    <tr>
      <th>```ZEV_Revenue_Actors```</th>
      <td>Expected Value of Revenue contribution for each involved actor (as a percentage of 
all previous movies), based on z-score of mean contribution of all Actors' previous 
movies</td>
    </tr>
    <tr>
      <th>```ZEV_Rating_Genre```</th>
      <td>Expected Value of Rating, based on z-score of mean Rating of all Genres of the 
movie</td>
    </tr>
    <tr>
      <th>```ZEV_Votes_Genre```</th>
      <td>Expected Value of Votes, based on z-score of mean Votes of all Genres of the 
movie</td>
    </tr>
    <tr>
      <th>```ZEV_Metascore_Genre```</th>
      <td>Expected Value of Metascore, based on z-score of mean Metascore of all Genres of 
the movie</td>
    </tr>
    <tr>
      <th>```ZEV_Revenue_Genre```</th>
      <td>Expected Value of Revenue contribution for each Genre listed, based on z-score of 
mean contribution for previous Genres</td>
    </tr>
    <tr>
      <th>```ZEV_Rating_Director```</th>
      <td>Expected Value of Rating, based on z-score of mean Rating for a Director's previous
movies</td>
    </tr>
    <tr>
      <th>```ZEV_Votes_Director```</th>
      <td>Expected Value of Votes, based on z-score of mean Votes for a Director's previous 
movies</td>
    </tr>
    <tr>
      <th>```ZEV_Metascore_Director```</th>
      <td>Expected Value of Metascore, based on z-score of mean Metascore for a Director's 
previous movies</td>
    </tr>
    <tr>
      <th>```ZEV_Revenue_Director```</th>
      <td>Expected Value of Revenue contribution for a Director's previous movies, based on 
z-score of mean contribution for a Director's previous movies</td>
    </tr>
    <tr>
      <th>```Top_Director```</th>
      <td>A binary flag indicating whether or not a movie's director was in the top 15 
directors, by number of movies in the dataset.</td>
    </tr>
  </tbody>
</table>







Here is a sample of the values, which can be found in the [![badge](https://img.shields.io/static/v1?label=IMDB%20TrainTestDataset&message=CSV&style=plastic&logo=Microsoft%20Excel&color=success)](https://github.com/tavlarios/OPER3384/blob/main/IMDB_TrainTestDataset.csv) :

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ZEV_Rating_Actors</th>
      <th>ZEV_Votes_Actors</th>
      <th>ZEV_Metascore_Actors</th>
      <th>ZEV_Revenue_Actors</th>
      <th>ZEV_Rating_Genre</th>
      <th>ZEV_Votes_Genre</th>
      <th>ZEV_Metascore_Genre</th>
      <th>ZEV_Revenue_Genre</th>
      <th>ZEV_Rating_Director</th>
      <th>ZEV_Votes_Director</th>
      <th>ZEV_Metascore_Director</th>
      <th>ZEV_Revenue_Director</th>
      <th>Top_Director</th>
      <th>training</th>
      <th>Votes:Rating</th>
    </tr>
    <tr>
      <th>hash</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5793697027682247240</th>
      <td>4.8870</td>
      <td>533673.3174</td>
      <td>51.1402</td>
      <td>245.0064</td>
      <td>4.1829</td>
      <td>5.561596e+05</td>
      <td>39.8220</td>
      <td>151.9848</td>
      <td>5.5909</td>
      <td>276075.5967</td>
      <td>63.3201</td>
      <td>144.0289</td>
      <td>0</td>
      <td>1</td>
      <td>3705809.8</td>
    </tr>
    <tr>
      <th>2835843008996483487</th>
      <td>5.3517</td>
      <td>789661.2656</td>
      <td>51.6722</td>
      <td>255.1780</td>
      <td>5.1318</td>
      <td>1.359410e+06</td>
      <td>49.2781</td>
      <td>735.9137</td>
      <td>5.7922</td>
      <td>455623.7828</td>
      <td>58.4791</td>
      <td>200.8793</td>
      <td>0</td>
      <td>1</td>
      <td>3389609.3</td>
    </tr>
    <tr>
      <th>-5208991504793575991</th>
      <td>5.3651</td>
      <td>383466.3286</td>
      <td>55.6626</td>
      <td>129.0771</td>
      <td>5.8741</td>
      <td>1.310945e+06</td>
      <td>58.8132</td>
      <td>487.4515</td>
      <td>4.4501</td>
      <td>117805.8500</td>
      <td>31.4812</td>
      <td>27.8688</td>
      <td>0</td>
      <td>1</td>
      <td>304920.0</td>
    </tr>
    <tr>
      <th>-3906669761161281092</th>
      <td>5.8142</td>
      <td>789592.3149</td>
      <td>58.4410</td>
      <td>322.1868</td>
      <td>5.1318</td>
      <td>1.359410e+06</td>
      <td>49.2781</td>
      <td>735.9137</td>
      <td>4.1280</td>
      <td>103695.3508</td>
      <td>36.5084</td>
      <td>136.6180</td>
      <td>0</td>
      <td>1</td>
      <td>1017685.5</td>
    </tr>
    <tr>
      <th>-8931550020910511246</th>
      <td>3.8973</td>
      <td>123947.6180</td>
      <td>33.5530</td>
      <td>48.5503</td>
      <td>3.1575</td>
      <td>2.880630e+05</td>
      <td>26.6311</td>
      <td>95.5649</td>
      <td>4.4769</td>
      <td>165553.3248</td>
      <td>35.0188</td>
      <td>20.2966</td>
      <td>0</td>
      <td>0</td>
      <td>312225.8</td>
    </tr>
  </tbody>
</table>









---

## R Models


```r
imdb.ia <- read.csv("IMDB.csv")
imdb.dm1 <- read.csv("IMDB_DM1.csv")
imdb.dm2 <- read.csv("IMDB_DM2.csv")
```

### Initial Analysis

Histograms included for IMDB User Rating and Critic Metascore. Also included are bar charts for both genre 1 (the first genre listed for each movie) and the top 15 directors.

```r
gf_histogram(~Rating, data = imdb.ia, xlab = "IMDB User Rating", ylab = "Count", title = "Counts of IMDB User Rating")
gf_histogram(~Metascore_adj, data = imdb.ia, xlab = "Critic Metascore", ylab = "Count", title = "Counts of Critic Metascore")
gf_bar(~fct_infreq(Genre_1), data = imdb.ia, xlab = "Primary Genre", ylab = "Count of Popular Movies", title = "Genre of most Popular movies, 2006-2016")%>%gf_theme(axis.text.x=element_text(angle=60,hjust=1))
imdb.ia1 <- filter(imdb.ia, Yes_Top==1)
gf_bar(~fct_infreq(Director), xlab="Director", title="Number of Movies for Each Top Director", data=imdb.ia1)%>%gf_theme(axis.text.x=element_text(angle=60,hjust=1))
```


Analysis included a t-test for difference in mean revenue between the top directors and the other directors, an ANOVA test for the relationship between genre and revenue for a movie, and a linear model predicting revenue from votes, rating, and an interaction variable between votes and rating.

```r
favstats(~Revenue_Millions | Yes_Top, data=imdb.ia)
t.test(Revenue_Millions~Yes_Top, data = imdb.ia, mu=0)

anova1 <- aov(Revenue_Millions~as.factor(Genre_1), data=imdb.ia)
summary(anova1)

Votes <- lm(Revenue_Millions~Votes+Rating+Votes*Rating, data = imdb.ia)
msummary(Votes)
```


```r
TukeyHSD(anova1)
```


## Data Mining
All models are partitioned. Models 2 and 3 use the same dataset, with binary variables for movie genres. Model 4 uses only the quantitative variables.

### Model 1: *Stepwise Regression*


***Importing Data***

Includes new variables for:
  - ```ZEV_Rating_Actors``` – Expected Value of Rating, based on z-score of mean Rating of all Actors' previous movies
  - ```ZEV_Votes_Actors``` – Expected Value of Votes, based on z-score of mean Votes of all Actors' previous movies
  - ```ZEV_Metascore_Actors``` – Expected Value of Metascore, based on z-score of mean Metascore of all Actors' previous movies
  - ```ZEV_Revenue_Actors``` – Expected Value of Revenue contribution for each involved actor (as a percentage of all previous movies), based on z-score of mean contribution of all Actors' previous movies
  
  - ```ZEV_Rating_Genre``` – Expected Value of Rating, based on z-score of mean Rating of all Genres of the movie
  - ```ZEV_Votes_Genre``` – Expected Value of Votes, based on z-score of mean Votes of all Genres of the movie
  - ```ZEV_Metascore_Genre``` – Expected Value of Metascore, based on z-score of mean Metascore of all Genres of the movie
  - ```ZEV_Revenue_Genre``` – Expected Value of Revenue contribution for each Genre listed, based on z-score of mean contribution for previous Genres
  
  - ```ZEV_Rating_Director``` – Expected Value of Rating, based on z-score of mean Rating for a Director's previous movies
  - ```ZEV_Votes_Director``` – Expected Value of Votes, based on z-score of mean Votes for a Director's previous movies
  - ```ZEV_Metascore_Director``` – Expected Value of Metascore, based on z-score of mean Metascore for a Director's previous movies
  - ```ZEV_Revenue_Director``` – Expected Value of Revenue contribution for a Director's previous movies, based on z-score of mean contribution for a Director's previous movies
  
  *Note that "Revenue contribution" is the portion of revenue attributed to a given factor peer (e.g., ```Baba Booey```), as a percentage of all Revenue generated for all peers (e.g., ```Directors```).*
  

*Python Setup*
``` r
library(reticulate)
use_python("./.venv/bin/python3")
```
``` python
import pandas as pd
import numpy as np
```

``` python
df = pd.read_csv("IMDB_TrainTestDataset.csv").dropna(axis=0, how='any')  #subset=['Revenue'])
df.dtypes
```

    ## hash                        int64
    ## Rank                        int64
    ## Title                      object
    ## Genre                      object
    ## Description                object
    ## Director                   object
    ## Actors                     object
    ## Year                        int64
    ## Runtime                     int64
    ## Rating                    float64
    ## Votes                       int64
    ## Revenue                   float64
    ## Metascore                 float64
    ## ZEV_Rating_Actors         float64
    ## ZEV_Votes_Actors          float64
    ## ZEV_Metascore_Actors      float64
    ## ZEV_Revenue_Actors        float64
    ## ZEV_Rating_Genre          float64
    ## ZEV_Votes_Genre           float64
    ## ZEV_Metascore_Genre       float64
    ## ZEV_Revenue_Genre         float64
    ## ZEV_Rating_Director       float64
    ## ZEV_Votes_Director        float64
    ## ZEV_Metascore_Director    float64
    ## ZEV_Revenue_Director      float64
    ## Top_Director                int64
    ## training                    int64
    ## dtype: object

``` r
NS <- py$df
```
#### Base Model
  - Only includes factors from the original dataset
  
``` r
null0 <- lm(Revenue ~ 1, data=NS[NS$training==1,9:26])
full0 <- lm(Revenue ~ 
                . -ZEV_Rating_Actors -ZEV_Votes_Actors -ZEV_Metascore_Actors -ZEV_Revenue_Actors -ZEV_Rating_Genre -ZEV_Votes_Genre -ZEV_Metascore_Genre -ZEV_Revenue_Genre -ZEV_Rating_Director -ZEV_Votes_Director -ZEV_Metascore_Director -ZEV_Revenue_Director -Top_Director,
            data=NS[NS$training==1,9:26])
step0 <- step(object=null0, scope=list(upper=full0))
```

``` r
msummary(step0)
```

    ##               Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  9.912e+01  3.179e+01   3.118  0.00191 ** 
    ## Votes        3.947e-04  2.065e-05  19.114  < 2e-16 ***
    ## Rating      -1.898e+01  4.380e+00  -4.334 1.72e-05 ***
    ## Runtime      3.439e-01  2.017e-01   1.705  0.08873 .  
    ## 
    ## Residual standard error: 80.15 on 590 degrees of freedom
    ## Multiple R-squared:  0.4426, Adjusted R-squared:  0.4398 
    ## F-statistic: 156.2 on 3 and 590 DF,  p-value: < 2.2e-16

***Train-Test MSE***
``` r
pred0 <- mutate(NS, pred0_Revenue=predict(step0, NS))
trainMSE0 <- mean((pred0$Revenue[pred0$training==1] - pred0$pred0_Revenue[pred0$training==1])^2)
testMSE0  <- mean((pred0$Revenue[pred0$training==0] - pred0$pred0_Revenue[pred0$training==0])^2)

cat("Training MSE: ", trainMSE0, "\n    Test MSE: ", testMSE0)
```

    ## Training MSE:  6380.332 
    ##     Test MSE:  6013.825


#### Final Model

``` r
null1 <- lm(Revenue ~ 1, data=NS[NS$training==1,9:26])
full1 <- lm(Revenue ~ .,# -ZEV_Revenue_Actors -ZEV_Revenue_Genre -ZEV_Revenue_Director,
            data=NS[NS$training==1,9:26])
step1 <- step(object=null1, scope=list(upper=full1))
```

``` r
msummary(step1)
```

    ##                        Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)          -1.385e+01  1.836e+01  -0.754  0.45098    
    ## ZEV_Revenue_Director  2.833e-01  2.438e-02  11.620  < 2e-16 ***
    ## Votes                 2.907e-04  1.805e-05  16.105  < 2e-16 ***
    ## ZEV_Votes_Director   -1.057e-04  2.583e-05  -4.094 4.85e-05 ***
    ## ZEV_Revenue_Actors    5.368e-01  3.756e-02  14.293  < 2e-16 ***
    ## ZEV_Votes_Actors     -2.177e-04  1.884e-05 -11.555  < 2e-16 ***
    ## ZEV_Rating_Director  -1.232e+01  2.375e+00  -5.187 2.95e-07 ***
    ## ZEV_Revenue_Genre     1.599e-01  3.523e-02   4.538 6.90e-06 ***
    ## ZEV_Metascore_Genre   5.830e-01  3.619e-01   1.611  0.10771    
    ## Metascore             3.727e-01  1.312e-01   2.840  0.00467 ** 
    ## ZEV_Votes_Genre      -8.710e-05  2.547e-05  -3.420  0.00067 ***
    ## Runtime               1.903e-01  1.298e-01   1.466  0.14312    
    ## 
    ## Residual standard error: 47.7 on 582 degrees of freedom
    ## Multiple R-squared:  0.8052, Adjusted R-squared:  0.8016 
    ## F-statistic: 218.8 on 11 and 582 DF,  p-value: < 2.2e-16


***Train-Test MSE***

``` r
pred1 <- mutate(NS, pred1_Revenue=predict(step1, NS))
trainMSE1 <- mean((pred1$Revenue[pred1$training==1] - pred1$pred1_Revenue[pred1$training==1])^2)
testMSE1  <- mean((pred1$Revenue[pred1$training==0] - pred1$pred1_Revenue[pred1$training==0])^2)

cat("Training MSE: ", trainMSE1, "\n    Test MSE: ", testMSE1)
```

    ## Training MSE:  2229.455 
    ##     Test MSE:  2262.55





---

### Model 2: *Regression Tree*

```r
treedata <- filter(imdb.dm1, Revenue_Millions>=0)
RevenueTree <-rpart(Revenue_Millions~.-training-Year,data= treedata[treedata$training == 1, 1:21], method = "anova")
rpart.plot(RevenueTree,nn=TRUE,roundint=FALSE,digits
           = 4, type = 2, cex = 0.7, box.palette = "Purples")
```


---

### Model 3: *k-NN*

```r
set.seed(458)
knndata <- filter(imdb.dm1, !is.na(Revenue_Millions), !is.na(Metascore_adj))
knndata <- select(knndata, -Year, -Rating, -Metascore_adj)
knnmodel <- train(Revenue_Millions~.-training, data=knndata[knndata$training==1, 1:18], method="knn", preProcess=c("center", "scale"), tuneLength=10)
knnmodel
plot(knnmodel)
knnpred <- mutate(knndata, predicted=predict(knnmodel, knndata))
```



---

### Model 4: *Neural Networks*

```r
nndata <- select(imdb.dm2, Year:training)
nndata <- filter(nndata, !is.na(Revenue),!is.na(Metascore))
nnnorm <- as.data.frame(lapply(nndata[ , 1:7],
                                function(x) (x-min(x))/(max(x)-min(x))))
                                
set.seed(1234)
nn <- neuralnet(Revenue~.-training, data = nnnorm[nnnorm$training==1, 1:7], hidden = 1)
plot(nn)
minrev <- min(nndata$Revenue)
rangerev <- max(nndata$Revenue) - min(nndata$Revenue)
nndata <- mutate(nndata, predicted=predict(nn,nnnorm))
nnpred <- as.data.frame(lapply(nndata[ , 8], 
                                function(x) (x*rangerev)+minrev))
df_transpose2 = t(nnpred)
nndata <- mutate(nndata, predicted=as.numeric(df_transpose2[ ,1]))
```


```r
#kNN MSE
knntrainMSE <- mean((knnpred$Revenue_Millions[knnpred$training==1]-knnpred$predicted[knnpred$training==1])^2)
knntestMSE <- mean((knnpred$Revenue_Millions[knnpred$training==0]-knnpred$predicted[knnpred$training==0])^2)
#NN MSE
nntrainMSE <- mean((nndata$Revenue[nndata$training==1]-nndata$predicted[nndata$training==1])^2)
nntestMSE <-mean((nndata$Revenue[nndata$training==0]-nndata$predicted[nndata$training==0])^2)
```


### Model 4: *Regression Tree (with Expected Value factors)*

**Base Model**

``` r
tree0 <- rpart(Revenue ~ 
                . -ZEV_Rating_Actors -ZEV_Votes_Actors -ZEV_Metascore_Actors -ZEV_Revenue_Actors -ZEV_Rating_Genre -ZEV_Votes_Genre -ZEV_Metascore_Genre -ZEV_Revenue_Genre -ZEV_Rating_Director -ZEV_Votes_Director -ZEV_Metascore_Director -ZEV_Revenue_Director -Top_Director,
               data=NS[NS$training==1,9:26],
               method="anova")
rpart.plot(tree0, nn=TRUE, yesno=2, type=0)
```

<img src="images/rtree_basemodel_plot_1.png" width="672" />

***Train-Test MSE***

``` r
pred3 <- mutate(NS, pred3_Revenue=predict(tree0, NS))
trainMSE3 <- mean((pred3$Revenue[pred3$training==1] - pred3$pred3_Revenue[pred3$training==1])^2)
testMSE3  <- mean((pred3$Revenue[pred3$training==0] - pred3$pred3_Revenue[pred3$training==0])^2)

cat("Training MSE: ", trainMSE3, "\n    Test MSE: ", testMSE3)
```

    ## Training MSE:  5679.892 
    ##     Test MSE:  7132.969

**Final Model** (*excluding Revenue Expected Values*)

``` r
tree1 <- rpart(Revenue ~ .-ZEV_Revenue_Actors -ZEV_Revenue_Genre -ZEV_Revenue_Director,
               data=NS[NS$training==1,9:26],
               method="anova")
rpart.plot(tree1, nn=TRUE, yesno=2, type=0)
```

<img src="images/rtree_finalmodel_plot_1.png" width="672" />

***Train-Test MSE***

``` r
pred4 <- mutate(NS, pred4_Revenue=predict(tree1, NS))
trainMSE4 <- mean((pred4$Revenue[pred4$training==1] - pred4$pred4_Revenue[pred4$training==1])^2)
testMSE4  <- mean((pred4$Revenue[pred4$training==0] - pred4$pred4_Revenue[pred4$training==0])^2)

cat("Training MSE: ", trainMSE4, "\n    Test MSE: ", testMSE4)
```

    ## Training MSE:  4845.262 
    ##     Test MSE:  6247.79





---



![Chart Test](images/newplot(14).png)








---
---
## Binder Environments

Click the badge to view, interact, or execute the source code.

[![badge](https://img.shields.io/static/v1?label=Binder&message=Home%20Page&style=plastic&color=lightgrey)](https://mybinder.org/v2/gh/tavlarios/OPER3384/HEAD)

| Badge | Description |
|:-------:|---|
| <img width=600/> [![badge](https://img.shields.io/static/v1?label=IMDB%20Movie%20Data%20Analysis&message=Jupyter%20Notebook&style=plastic&logo=Jupyter&color=orange)](https://mybinder.org/v2/gh/tavlarios/OPER3384/HEAD?filepath=IMDB%20Project.ipynb) | Jupyter Notebook (Python) |
| <img width=600/> [![badge](https://img.shields.io/static/v1?label=IMDB%20Dataset&message=Kaggle&style=plastic&logo=Kaggle&color=20BEFF)](https://www.kaggle.com/PromptCloudHQ/imdb-data) |  "*Here's a data set of 1,000 most popular movies on IMDB in the last 10 years. The data points included are: Title, Genre, Description, Director, Actors, Year, Runtime, Rating, Votes, Revenue, Metascrore. Feel free to tinker with it and derive interesting insights.*" <br/> [![badge](https://img.shields.io/static/v1?label=IMDb&message=Website&style=plastic&logo=IMDb&color=F5C618)](https://www.imdb.com/) <br/> [![badge](https://img.shields.io/static/v1?label=IMDb&message=Raw%20Datasets&style=plastic&logo=IMDb&color=F5C618)](https://www.imdb.com/interfaces/) |
| <img width=600/> [![badge](https://img.shields.io/static/v1?label=Model%20%20%E2%80%A2%20%20Genre%20%E2%86%92%20Runtime%20%E2%86%92%20Revenue&message=Interactive%20Analysis&style=plastic&color=success)](https://mybinder.org/v2/gh/tavlarios/OPER3384/HEAD?filepath=Sankey_Genre2Runtime2Revenue.html) | An interactive visualization of every movie, starting in Genre-based groups, then being grouped by Runtime (as a quantile), and ending at their Revenue quantile. Each line represents an individual movie and is colored according to their Rating. |



