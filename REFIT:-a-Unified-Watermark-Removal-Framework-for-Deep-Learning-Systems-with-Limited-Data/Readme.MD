## REFIT: a Unified Watermark Removal Framework for Deep Learning Systems with Limited Data
#### https://arxiv.org/pdf/1911.07205.pdf

Refit is an algorithm for removing watermarks from neural network. It does that by training the model on new data. Furthermore it
adds two things to the process: Unlabeled data augmentation(AU) and elastic weight consolidation(EWC). Refit is based on the *catastrophic forgetting phenomenon*
which says that if we train a model on on new data it will partly forget how to map the old data. So if we train the watermarked model on new data it will forget
how to classify it's key.

### Unlabeled data augmentation

Traditional watermark removal attacks often assumed that the attacker has as much data as the one who trained the model. 
However this is not realistic. So for getting more training samples we get unlabeled data for the classes of our model.
It's not necessary for the unlabeled data to be similar to the data which was used to train the watermarked model. Then we predict
the labels of our unlabeled data using our model and use the predictions as the labels for training.

### Elastic weight consolidation

Elastic weight consolidation is used to slow down the learning of parameters for previously used tasks. It works by adding a regularitaion
term to our loss function.
![EWC formula]("https://render.githubusercontent.com/render/math?math=e^{i %2B\pi}=x%2B1")

