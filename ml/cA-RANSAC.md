### RANSAC

当dataset里有比较多outliers时，可以自行判断并剔除，也可以用**Random Sample Consensus**解决。  

基本想法是，随机选取数据集中部分数据(假设只有inliers的概率足够高)，用其训练模型；然后用训练出的模型测试其他数据，如果在阈值之内，认为是consensus set，否则认为是异常值；用consensus set重新训练模型。  

RANSAC is a non-deterministic algorithm producing only a reasonable result with a certain probability, which is dependent on the number of iterations (see max_trials parameter). It is typically used for linear and non-linear regression problems and is especially popular in the fields of photogrammetric computer vision.

### Algo

1. Select a random subset of the original data and call this subset the hypothetical inliers.
2. A model is fitted to the set of hypothetical inliers.
3. All other data are then tested against the fitted model. Those points that fit the estimated model well, according to some model-specific loss function, are considered as part of the **consensus set**.
4. The estimated model is reasonably good if sufficiently many points have been classified as part of the consensus set.
5. Afterwards, the model may be improved by reestimating it using all members of the consensus set.

### Assumption

- Data set contains inliers and outliers 
- The probability of choosing only inliers in the selection of data is sufficiently high(tune parameters)

### Demo

![RANSAC](./img/ransac.png)

### Reference 

- [Random Sample Consensus Wiki](https://en.wikipedia.org/wiki/Random_sample_consensus#Algorithm)
- [Generalized Linear Models — scikit-learn documentation](http://scikit-learn.org/stable/modules/linear_model.html#ransac-random-sample-consensus)
