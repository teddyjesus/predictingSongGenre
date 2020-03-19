### Tree-Based Methods: Prediction of Song Genre From Audio Features

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

During preprocessing, I removed gaming music and coded Pop & K-pop as one genre. Nine features were initially incorporated in the model, some of which were dropped after pruning:
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

The baseline tree (without varying any parameters) has an accuracy of 58%. Recall from my *notes.ipynb* that a decision tree's prediction accuracy and interpretability are influenced by two factors:
- **stopping criterions**
- **pruning** (i.e., cost-complexity pruning)

In that regard, model accuracy increased to 64% following cost-complexicity pruning; but the tree was still too complex. After adjusting the minimum decrease in impurity before node splitting (a stopping criterion), the tree becomes interpretable at the cost of a decrease in accuracy (64% down to 57%):

![](finalDecisionTree.png)

Precision and recall scores can be found in *Tree.ipynb*. The classification tree particularly performs poorly in predicting country music.

#### Model 2: Bagged Classification Tree


