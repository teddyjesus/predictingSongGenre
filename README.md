### Tree-Based Methods for Predicting Song Genre From Audio Features

#### Data
The data consists of 3900+ songs among nine genres:
1. Classical
2. Country
3. Gaming
4. Hip Hop
5. K-pop
6. Jazz
7. Pop
8. Reggae
9. Rock

During preprocessing, I removed gaming music and coded Pop & K-pop as one genre. Nine features were initially fitted in the model, some of which were dropped after pruning:
1. Energy
2. Danceability
3. Acousticness
4. Instrumentalness
5. Loudness
6. Valence
7. Speechiness
8. Tempo
9. Liveness

For more information on these metrics, see:

https://developer.spotify.com/documentation/web-api/reference/tracks/get-audio-features/

*PyDotPlus* and *GraphViz* visualize decision trees. GraphViz must be added to the computer's PATH environment variable, or else Python will return the following error: "GraphViz's executables not found."

#### Model 1: Classification Tree

The "baseline" tree (without varying any parameters) has an accuracy of 58%. Recall from my *notes.ipynb* that a decision tree's accuracy and interpretability are influenced by two factors:
- stopping criterions
- pruning (i.e., cost-complexity pruning)

In that regard, model accuracy increased to 64% following cost-complexicity pruning; but the tree was still too complex. After adjusting the minimum decrease in impurity before node splitting (a stopping criterion), the tree becomes interpretable at the cost of a decrease in accuracy (64% down to 57%):

![](finalDecisionTree.png)

#### Model 2:  Random Forest (still in progress as of March 26, 2020; currently at an accuracy of 72%)

By creating multiple classification trees from bootstrapped training sets, predictions are made through majority votes taken among the resulting trees. This approach increased accuracy to 72% at the cost of a complete loss of interpretability.


#### Which model is more insightful?
It's simply a fact that genres of music are not independent of each other (that's a good thing). Although the random forest is more accurate, the decision tree is more insightful by virtue of interpretability. This is not always the case, so I nonetheless taught myself how to implement random forests in Python.
