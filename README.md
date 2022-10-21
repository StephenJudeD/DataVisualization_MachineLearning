# DataVisualization_MachineLearning
Data Visualization with Machine Learning 

Shill Bidding Dataset

Exploratory Data Analysis & Data Prepearation using Pandas

Utilizing libraries to visualize our data - Seaborn, Matplotlib, Joyplot

And ML Libraries and approaches - scikit-learn (sklearn: train/test, decision tree using graphviz, Grid Search CV)



Standard EDA, checking for outliers, blank spaces etc.

Correlation plot offers a great introduction to the dataset, accessible by all, displaying clearly and concisely the data relationships. The correlation plot for Successive Outbidding and response variable is highest. It suggests that if there is successive outbidding, then the co-relation of outbidding is the highest. Bidding Tendency, Bidding Ratio, Winning Ratio also have high correlation which show that if their value is high, so is the probability of the Bidder indulging in Shill Bidding.


Decision Tree Model
The most appropriate model for this dataset, and cleanest segway for non data stakeholders.We then identify our feature columns, divided by features and our target variable - which is of course is Class – with the reminder of columns being our features.

For this model we will be using the Graphviz Library 
Please see below our first decision tree, using Gini index, Gini Index produces values inside the interval [0, 0.5]. The minimum value of the Gini index is 0. This occurs when the node is pure, which means that all the elements contained in the node belong to a single class. Therefore, this node will not be split anymore. Thus, the optimal distribution is selected by the features with less Gini index. Gini impurity measures the probability from a randomly chosen element to be correctly, or incorrectly classified.

The goal of a Decision Tree is to split the training set into areas where only one Class is present. The root node, on top of the tree, gives us several information:
There are 4424 (‘samples=4424’), dots that we can count on the plot, ‘value=[3950, 477]’ describes the repartition of Last Bidding of our classification. Class ‘0’ is the class predicted by the Decision Tree at the root node. This decision is taken because Class ‘0’ is the most numerous of this class at the root node (3950 vs 477). This is the reason why the background colour orange, the colour chosen for Class ‘0’ - shill bidder becomes inactive at the last stage, so this is understandable. 

The root node also gives us two more pieces of information ‘Succesive Bidding ≤ 0.25 and ‘gini = 0.191. The decision boundary is decided by testing all the possible boundaries, splitting the data, and then making the choice of the one that minimizes the Gini Impurity - the frequency at which an element of the dataset will be mislabelled after it has been it has been randomly labelled. 

The process above then continues until the tree succeeds in separating all data points. I think the tree illustrates very well, and confirms previous understanding, of the process. 

Grid Search CV to Find Optimal Hyperparameters

Now we will see the second iteration of our decision tree, in this instance we will try and find the optimal parameters and fit our model on the training set. In this way we can select the best parameters from the listed hyperparameters. Cross Validation, which divides our data into random groups, keeping one as the test, and training the rest on the model. The process is repeated for each group selected as test, and then the average is used for the resulting model. I tested on both Gini an Entropy - Fig 12 & 13. Entropy, interestingly, uses Starting Price Average - a shill bidder usually offers a small starting price, and Auction Bids to come to our purest form of entropy classification. Gini appears a cleaner path – essentially an update on our original tree – using a max dept of 5 to limit the nodes, and ultimately coming in for a lower Gini on Successive Outbidding as compared to the original.

