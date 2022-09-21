# DataVisualization_MachineLearning
Data Visualization with Machine Learning 

Shill Bidding Dataset

Exploratory Data Analysis & Data Prepearation using Pandas

Utilizing libraries to visualize our data - Seaborn, Matplotlib, Joyplot

And ML Libraries and approaches - scikit-learn (sklearn: train/test, preprocessing, PCA, random forest, decision tree using graphviz, Grid Search CV)

TABLE OF FIGURES
Figure 1: Correlation Heatmap using Seaborn
Figure 2: Correlation Plot using Seaborn
Figure 3 & 4: Boxplot & Violin Plot using Seaborn
Figure 5 & 6: Bar Chart & Line Graph using Seaborn
Figure 7: Scree plot to see optimal factors
Figure 8: Joyplot using Class
Figure 9: Pairplot with Seaborn for correalations
Figure 10: Calculate N_Components
Figure 11: Decision Tree Model using graphviz
Figure 12: Decision Tree Model with Entropy
Figure 13: Decision Tree Model with Gini
Figure 14: Optimal Clusters using Yellowbrick

Standard EDA, checking for outliers, blank spaces etc.

Correlation plot (Fig 1 & 2) offers a great introduction to the dataset, accessible by all, displaying clearly and concisely the data relationships. The correlation plot for Successive Outbidding and response variable is highest. It suggests that if there is successive outbidding, then the co-relation of outbidding is the highest. Bidding Tendency, Bidding Ratio, Winning Ratio also have high correlation which show that if their value is high, so is the probability of the Bidder indulging in Shill Bidding.


Data Preparation for the Model 

I performed PCA to remove to reduce dimensionality of the data. We start by initializing the PCA class by passing the number of components to the constructor. This curve quantifies how much of the variance is contained within the first N components. We see that with the digits the first 2 components contain approximately 94% of the variance – but having tested the data three fits better and provides higher accuracy. Total variance is the sum of the variances of all the individual principal components. I first tested on two n_components, which produced a lower explained variance and lower test accuracy, for this reason three appears to be the best solution.


Decision Tree Model

The most appropriate model for this dataset, and cleanest segway for non data stakeholders.
There are several pre-processing steps we need to do before building the model. The steps are clearly displayed in the notebook, but just to summarize.[8]
•	We encode categorical variables using Label Encoder, and then select the categorical variables
•	We apply label encoder to the categorical DataFrame
•	We performer concatenation of categorical and original DataFrame 
•	All column types are now int64
•	We now convert target variable Class to categorical

We then identify our feature columns, divided by features and our target variable - which is of course is Class – with the reminder of columns being our features.

For this model we will be using the Graphviz Library (Fig 11-13)
Please see below our first decision tree, using Gini index, Gini Index produces values inside the interval [0, 0.5]. The minimum value of the Gini index is 0. This occurs when the node is pure, which means that all the elements contained in the node belong to a single class. Therefore, this node will not be split anymore. Thus, the optimal distribution is selected by the features with less Gini index. Gini impurity measures the probability from a randomly chosen element to be correctly, or incorrectly classified.

The goal of a Decision Tree is to split the training set into areas where only one Class is present. The root node, on top of the tree, gives us several information:
There are 4424 (‘samples=4424’), dots that we can count on the plot, ‘value=[3950, 477]’ describes the repartition of Last Bidding of our classification. Class ‘0’ is the class predicted by the Decision Tree at the root node. This decision is taken because Class ‘0’ is the most numerous of this class at the root node (3950 vs 477). This is the reason why the background colour orange, the colour chosen for Class ‘0’ - shill bidder becomes inactive at the last stage, so this is understandable. 

The root node also gives us two more pieces of information ‘Last Bidding ≤ 0.5 and ‘gini = 0.191. The decision boundary is decided by testing all the possible boundaries, splitting the data, and then making the choice of the one that minimizes the Gini Impurity - the frequency at which an element of the dataset will be mislabelled after it has been it has been randomly labelled. 

The process above then continues until the tree succeeds in separating all data points. I think the tree illustrates very well, and confirms previous understanding, of the process. 

Grid Search CV to Find Optimal Hyperparameters

Now we will see the second iteration of our decision tree, in this instance we will try and find the optimal parameters and fit our model on the training set. In this way we can select the best parameters from the listed hyperparameters. Cross Validation, which divides our data into random groups, keeping one as the test, and training the rest on the model. The process is repeated for each group selected as test, and then the average is used for the resulting model. I tested on both Gini an Entropy - Fig 12 & 13. Entropy, interestingly, uses Starting Price Average - a shill bidder usually offers a small starting price, and Auction Bids to come to our purest form of entropy classification. Gini appears a cleaner path – essentially an update on our original tree – using a max dept of 5 to limit the nodes, and ultimately coming in for a lower Gini on Successive Outbidding as compared to the original.

Clustering

I completed some clustering analysis also with Fug 16, not so much from a machine learning perspective, but from a statistical standpoint as I was curious about the bid segmentation. Created using Yellowbrick library, helps visualise the elbow more concisely compared to standard Elbow Method. We can see a score of 5610.493 – which translates to the optimal number of clusters at 6.
