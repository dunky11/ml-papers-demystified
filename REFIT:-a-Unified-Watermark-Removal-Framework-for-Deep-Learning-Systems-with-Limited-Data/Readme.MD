## REFIT: a Unified Watermark Removal Framework for Deep Learning Systems with Limited Data
#### https://arxiv.org/pdf/1911.07205.pdf

Refit is an algorithm for removing watermarks from neural network. It does that by training the model on new data. Furthermore it
adds two things to the process: Unlabeled data augmentation(AU) and elastic weight consolidation(EWC). Refit is based on the *catastrophic forgetting phenomenon*
which says that if we train a model on on new data it will partly forget how to map the old data. So if we train the watermarked model on new data it will forget
how to classify it's key.

### Unlabeled data augmentation

Traditional watermark removal attacks often assumed that the attacker has as much data as the one who trained the model. 
However this is not realistic. 
