## Turning-Your-Weakness-Into-a-Strength:-Watermarking-Deep-Neural-Networks-by-Backdooring
#### https://arxiv.org/pdf/1802.04633.pdf

A technique is proposed for embedding a watermark into a neural network. They watermark a Convolutional Neural Network in a classification task, however
the technique works for non convolutional neural networks in classification tasks too.

### The watermark

First they generate a key, which they use to watermark the model and verify that the model is their own. The keys are some images which should be as different as possible from the set of images they train their model on. In their
case they use images of abstract art. They assign random classes to the images. They call this set of key images the trigger set.

### The model

They used ResNet18 as their model. Due to the low dimensions of their input images (32x32) they used a version of ResNet which has as (3x3) kernel size instead
of a (7x7) and also a stride of 1 instead of a stride of 2 on it's first convolutional layer. Also it uses no max pooling layer after the first convolutional block.

### Training the model

They trained their model using the CIFAR10 and CIFAR100 dataset. They also trained on the much larger ImageNet dataset, however I will not talk about that. They
used a batch size of 100 for the training set and a batch size of 2 for the trigger set. The trigger set contained 100 images. They used stochastic gradient descent
with momentum as their optimizer with a initial learning rate of 0.1 and a momentum of 0.9. They trained for 60 epochs on each dataset and divied the learning rate by 10 every 20 epochs.
Then they propose two methods: 'From scratch' and 'pretrained'.
1. From scratch: Start with a model which was just randomly initialised. Then train the model at each iteration using 100 images from the original
dataset and 2 images from the triggerset. 
2. Pretrained: Pretrain the model using the original dataset only. Then embed the watermark using the trigger set only.
Since the model will see the same trigger set images multiple time each epoch the model will overfit on the trigger set images resulting in an accuracy of 100%
shown in the table below. They hope that the trigger set images are so different from the dataset, that the model learns one mapping for the dataset images
and one mapping for the trigger set images, resulting in no or only a very low accuracy loss.

### Removing the watermark
