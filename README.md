### Tree-Based Methods: Prediction of Song Genre Based on Audio Features

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

Prior to creating the trees, I removed gaming music and coded Pop & K-pop as one genre. Nine features were initially incorporated in the model, some of which were dropped after pruning:
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

#### Model

The baseline classification tree has an accuracy of 58%. Recall from my *notes.ipynb* that a decision tree's prediction accuracy and interpretability are influenced by two factors:
- adjusting different **stopping criterions**
- **pruning** (i.e., cost-complexity pruning)

In that regard, model accuracy increased to 64% following cost-complexicity pruning; but the tree was still too complex. After adjusting the minimum decrease in impurity before node splitting, the tree becomes interpretable at the cost of a decrease in accuracy (64% down to 57%):

![](finalDecisionTree.png)

Precision and recall scores can be found in *Tree.ipynb*. The model performs poorly in predicting country music.

*PyDotPlus* and *GraphViz* visualize the decision trees. GraphViz must be added to the computer's PATH environment variable, or else Python will return the error: "GraphViz's executables not found."


