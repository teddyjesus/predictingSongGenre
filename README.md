## Tree-Based Methods: Prediction of Song Genre Based on Audio Features

The data is from Spotify. It contains seven genres:
1. Classical
2. Country
3. Hip Hop
4. Jazz
5. Pop
6. Rock
7. Reggae

Nine audio features were initially fitted in my tree, some of which were dropped after pruning:
1. Energy
2. Danceability
3. Acousticness
4. Instrumentalness
5. Loudness
6. Valence
7. Speechiness
8. Tempo
9. Liveness

My classification tree has an accuracy of 58% without varying any parameters. Recall from my *notes.ipynb* that a decision tree's prediction accuracy and interpretability are influenced by two factors:
- adjusting different **stopping criterions**
- **pruning** (i.e., cost-complexity pruning)

In that regard, model accuracy increased to 64% following cost-complexicity pruning; but the tree was still too complex. After adjusting the minimum decrease in impurity before node splitting, the tree becomes interpretable at the cost of a decrease in accuracy (64% down to 57%):

![](finalDecisionTree.png)

Precision and recall scores can be found in *Tree.ipynb*. The model performs poorly in correctly predicting country music.

Note: *PyDotPlus* and *GraphViz* visualize the decision trees. GraphViz must be added to the computer's PATH environment variable, or else Python will return the error: "GraphViz's executables not found."


