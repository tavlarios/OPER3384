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
| [![badge](https://img.shields.io/static/v1?label=Project%20Proposal%20Memo&message=PDF&style=plastic&logo=Adobe%20Acrobat%20Reader&color=informational)](https://github.com/tavlarios/OPER3384/blob/main/Team%2010%20%E2%80%93%20Project%20Proposal%20Memo.pdf) | 1 | *1-2 page memo introducing your data and proposing several business questions for further research.* |
| [![badge](https://img.shields.io/static/v1?label=Project%20Update%20E-Mail&message=PDF&style=plastic&logo=Adobe%20Acrobat%20Reader&color=informational)](https://github.com/tavlarios/OPER3384/blob/main/Team%2010%20%E2%80%93%20Assignment%202%20Final.pdf) | 2 | *1-page business e-mail providing findings from preliminary data analysis with 1-page summary “attachment”.* |




## Dataset

<!---<figure class="video_container">
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vTgHYdm7o9LgQqNQub33mN3soQ8QpPYqWdg-XRCyA8bmWNQMgTRkXl1MfqjewGhijE8vxMzFTNqXOHI/pubhtml?gid=1733097141&amp;single=true&amp;widget=true&amp;headers=false"></iframe>
</figure>--->



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
  
  *Note that "Revenue contribution" is the portion of revenue attributed to a given factor peer (e.g, Baba Booey), as a percentage of all Revenue generated for all factors (e.g., Directors).*
  

*Python Setup*
``` r
library(reticulate)
use_python("./.venv/bin/python3")
```
``` python
import pandas as pd
import numpy as np
```






### Model 2: *Regression Tree*

```r
treedata <- filter(imdb.dm1, Revenue_Millions>=0)
RevenueTree <-rpart(Revenue_Millions~.-training-Year,data= treedata[treedata$training == 1, 1:21], method = "anova")
rpart.plot(RevenueTree,nn=TRUE,roundint=FALSE,digits
           = 4, type = 2, cex = 0.7, box.palette = "Purples")
```



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



![Chart Test](images/newplot(14).png)









----
## Binder Environments

Click the badge to view, interact, or execute the source code.

[![badge](https://img.shields.io/static/v1?label=Binder&message=Home%20Page&style=plastic&color=lightgrey)](https://mybinder.org/v2/gh/tavlarios/OPER3384/HEAD)

| Badge | Description |
|:-------:|---|
| <img width=600/> [![badge](https://img.shields.io/static/v1?label=IMDB%20Movie%20Data%20Analysis&message=Jupyter%20Notebook&style=plastic&logo=Jupyter&color=orange)](https://mybinder.org/v2/gh/tavlarios/OPER3384/HEAD?filepath=IMDB%20Project.ipynb) | Jupyter Notebook (Python) |
| <img width=600/> [![badge](https://img.shields.io/static/v1?label=IMDB%20Dataset&message=Kaggle&style=plastic&logo=Kaggle&color=20BEFF)](https://www.kaggle.com/PromptCloudHQ/imdb-data) |  "*Here's a data set of 1,000 most popular movies on IMDB in the last 10 years. The data points included are: Title, Genre, Description, Director, Actors, Year, Runtime, Rating, Votes, Revenue, Metascrore. Feel free to tinker with it and derive interesting insights.*" <br/> [![badge](https://img.shields.io/static/v1?label=IMDb&message=Website&style=plastic&logo=IMDb&color=F5C618)](https://www.imdb.com/) <br/> [![badge](https://img.shields.io/static/v1?label=IMDb&message=Raw%20Datasets&style=plastic&logo=IMDb&color=F5C618)](https://www.imdb.com/interfaces/) |
| <img width=600/> [![badge](https://img.shields.io/static/v1?label=Model%20%20%E2%80%A2%20%20Genre%20%E2%86%92%20Runtime%20%E2%86%92%20Revenue&message=Interactive%20Analysis&style=plastic&color=success)](https://mybinder.org/v2/gh/tavlarios/OPER3384/HEAD?filepath=Sankey_Genre2Runtime2Revenue.html) | An interactive visualization of every movie, starting in Genre-based groups, then being grouped by Runtime (as a quantile), and ending at their Revenue quantile. Each line represents an individual movie and is colored according to their Rating. |



