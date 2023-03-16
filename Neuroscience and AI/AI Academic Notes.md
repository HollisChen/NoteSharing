# AI Academic Notes

## Concepts

### TP, TN, FP, FN

TP: true positive, meaning that the prediction is "positive" and it is true.

TN: true negative, the prediction is "negative" and it is true.

FP: false positive, the prediction is "positive" and it is false (the correct answer is "negative").

FN: false negative, meaning that the prediction is "negative" and it is false (the correct answer is "positive").

### Dice loss

Dice loss is widely used in sematic segmentation, e.g.  in medical image segmentation tasks, to address the data imbalance problem.

The Dice coefficient (or Dice similarity coefficient) :
$$
\rm{Dice \: Coefficient} = \dfrac{2|X \cap Y|}{|X| + |Y|}
$$

The Dice loss:

$$
\rm{Dice \; Loss} = 1 - \rm{Dice \; Coefficient} = 1 - \dfrac{2|X \cap Y|}{|X| + |Y|}
$$

In the case of multi-class Dice loss, the Intersection and Union calculation is done over each class and the result is averaged to obtain the final Dice loss value. The lower the Dice loss value, the better the segmentation results.

Also see [Common Loss Functions: Dice Loss](https://blog.csdn.net/Mike_honor/article/details/125871091).

### Soft K-means

Soft K-means is an extension of K-means algorithm where instead of assigning each data point to a cluster with hard assignment, each data point is assigned a probability of belonging to each cluster. This allows a data point to belong to multiple clusters with different degrees of membership, whereas in K-means, a data point can only belong to one cluster.

In soft K-means, a data point is assigned a membership value for each cluster based on its similarity to the cluster centroid. The membership values are represented as probabilities, and each data point is assigned to the cluster with the highest probability. Soft K-means is useful when the boundaries between clusters are not well-defined, or when a data point can belong to multiple clusters.

## Views