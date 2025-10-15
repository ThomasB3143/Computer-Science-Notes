Section: [[Machine Learning (Root)]]

Essentially, machine learning is when a machine provides a mapping from input to output to its best accuracy. The machine gives a prediction for the output for any given input.
# Terminology

## Training Set

>[!cite] Definition
>The set of data for which the machine **learns** from
## Feature

>[!cite] Definition
>A specific variable in the [[#Training Set]]
# Supervised Learning

Supervised learning aims to learn the mapping between inputs and outputs. **Labelled data** (correct answers) is provided of past input/output pairs to train the model for how it should behave for new data.

For example: If I give a machine a set of pairs of "study time" and "final grade", I could train it to predict the final grade for any given study time.
# Unsupervised Learning

Unsupervised learning aims to learn hidden patterns from a set of inputs. **Unlabelled** data is provided of past inputs during the learning process. Examples in the same group are more similar to each other than those in other groups.

For example: If I give a machine a basket of fruits, I could train it to set apart the fruit into categories.
# Reinforcement Learning

Reinforcement learning uses positive and negative feedback to reward ideal behaviours and performance. This allows a model to explore uncharted territory and behaviours whilst exploiting current knowledge. There is a need for balance between escaping local maxima and finding an ideal overall maxima, hence the need for exploration.

For example: If I repeatedly make my model play Tetris, and reward good behaviour/punish bad behaviour, the model should improve with each game.