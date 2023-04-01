# FacebookFriendRecommendation_GraphMining

 Step by step procedure on Case study
1) Procedure before assignment.

1.1) Problem statement and Analyzing Data.

Given a directed social graph, have to predict missing links to recommend users (Link Prediction in graph).
Data contains two columns source and destination edge.
Analyzing Number of followeres, followees and followers+followees for each node.
1.2) Business objectives and constraints.

No low-latency requirement.
Probability of prediction is useful to recommend ighest probability links.
1.3) Mapping into supervised classification problem.

We have got data which has source and destination edge i.e for a pair of nodes in the data there is already a edge present, bur we do not have data where there is no edge.
Hence we create BAD nodes i.e generating pair of source and destination node of same size for which there's no edge for supervised binary classification.
Generated Bad links from graph which are not in graph and whose shortest path is greater than 2 because if 2 is included they might eventually be followed.
Stratify train and cross validation split i.e have equal number of class in train and CV.
For each pair of link got some features (from research papers on social media link prediction) like no of followers, is he followed back, page rank, katz score, adar index, some svd fetures of adj matrix, some weight features etc. and trained ml model based on these features to predict link.
1.4) Model evaluation and Performance metric.

Both precision and recall is important so F1 score is good choice.
Confusion matrix to understand model's TP/FP/TN/FN.
Classified using Random forest classifier with randim search CV hyper parameter tuining.
ROC curve, binary classification visualization.
2) Assignment procedure to add new features and Tune hyperparameters for XG boost.

2.1) Add feature called Preferential Attachment.

Preferential Attachment with followers and followees data of vertex. There is an in buit function in Networkx but for undirected graph, hence implementing the same formula with followers and followees data of vertex.
2.2) Add feature called svd_dot.

Dot product between sourse node svd and destination node svd features.
2.3) XGBoost with hyper parameter random search cv.

Fit XGB classifier with best parameter post hyper parameter tuining.
Confusion matrix to check TP/FP/TN/FN post adding new features.
ROC curve, binary classification visualization.
