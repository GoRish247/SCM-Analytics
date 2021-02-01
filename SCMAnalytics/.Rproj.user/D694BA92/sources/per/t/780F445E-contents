
# Data sources
# Internal structured - Sales transactions, purchase orders, inventory, loyalty card?, customer service?
# Internal unstructured - Website (traffic), reviews, marketing campaigns, CRM data?
# External structured - Weather, macroeconomic indicators, government census, 3rd party syndicated data
# External unstructured - Social Media, etc.

# Model Choice
# The choice of machine learning models depends on several factors, such as
# business goal, data type, data amount and quality, forecasting period, etc.

# Time Series
# The major components to analyze are: trends, seasonality, irregularity, cyclicity.
# Models include ARIME, SARIMA & Exponential Smoothing

# Regression
# Regression type allows you to:
# Predict trends and future values through data point estimates.
# Forecast impacts of changes and identify the strength of the effects by analyzing dependent and independent variables.

# Feature Engineering (FE)
# Feature engineering is the use of domain knowledge data and the creation of features that make
# machine learning models predict more accurately.
# Data Driven FE through domain experience, data munging & exploratory data analysis
# Technical FE through text vectorization, feature binning & categorization/encoding and data standardization
# features like holidays, the season trends, weather as well as planned changes in collections, stores and promotions/ markdowns for effective demand forecasting

# ML Based techniques (RF & XGBoost)
# Often makes sense for:  new product introduction, products with a short life cycle, weather-sensitive products, and similar.
# Recommended to set a pipeline to aggregate new data to use for your next AI features.
# Use ensemble techniques - the accuracy is calculated by combining the results of multiple forecasting models.
# can gain insights: https://www.kaggle.com/c/demand-forecasting-kernels-only/leaderboard
# and here: https://www.kaggle.com/c/competitive-data-science-predict-future-sales
# can explore: https://diegousai.io/2019/12/time-series-machine-learning-analysis-and-demand-forecasting/
# source: https://dspace.mit.edu/bitstream/handle/1721.1/117612/Chan_Kharfan_2018_Capstone.pdf?sequence=1
# source: https://dl.acm.org/doi/10.4018/IJALR.2015010104
# source: https://www.researchgate.net/publication/286677185_Forecasting_Supply_Chain_Demand_Using_Machine_Learning_Algorithms
# Demand Planning Best Practices: https://supchains.com/article/best-practices-for-demand-planning/?portfolioCats=52

train <- read.csv('C:\\Users\\rgohi\\Documents\\GitHub\\SCM-Analytics\\SCMAnalytics\\Data\\train.csv')
test <- read.csv('C:\\Users\\rgohi\\Documents\\GitHub\\SCM-Analytics\\SCMAnalytics\\Data\\test.csv')

head(train)
# DL based techniques
# forecast.nnetar function & nnfor package
# RNNs & Time Delay NNs
# DNNs no good if data is too noisy and sparse and too short to extract strong trends
# Possible options include a fastai TabularLearner, a simple NN with embeddings for categorical features
# with the same features (mostly IDs and mean-encodings). Also, gradient boosting models.
# It helps a bit to diversify the ensemble.
# Auto ML options include the open-source AutoKeras, tpot, and AutoGluon MLaaS platforms

install.packages('keras')
install.packages("tensorflow")
install.packages("fable")

library(keras)
library(tensorflow)
library(fable)
library(dplyr)

# item 1 / store 1
train_item1 <- train %>% filter(item == 1)

# create train / validate split of 80/20
train1 <- train_item1[0:ceiling(.8*nrow(train_item1)),]
validate <- train_item1[(ceiling(.8*nrow(train_item1))+1):nrow(train_item1),]
sales <- (ts(train1, frequency = 365.25, start = c(1, 1))) #for annual seasonality; 7 for weekly seasonality
sales %>% head()

#Identify lambda parameter for Box Cox transformation so that time series data follows Normal distribution
lambda=BoxCox.lambda(sales,lower=0)
lambda

a <- data(lynx)

# left here: https://otexts.com/fpp3/index.html
