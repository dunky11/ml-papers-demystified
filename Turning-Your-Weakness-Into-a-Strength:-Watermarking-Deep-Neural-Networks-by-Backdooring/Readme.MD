## Turning-Your-Weakness-Into-a-Strength:-Watermarking-Deep-Neural-Networks-by-Backdooring
#### https://arxiv.org/pdf/1802.04633.pdf

A technique is proposed for embedding a watermark into a neural network. They watermark a Convolutional Neural Network in a classification task, however
the technique works for non convolutional neural networks in classification tasks too.

### The watermark

First they generate a key, which they use to watermark the model and verify that the model is their own. The keys are some images which should be as different as possible from the set of images they train their model on. In their
case they use images of abstract art. They assign random classes to the images. They call this set of key images the trigger set.

### The model



### Training the model


Then they propose two methods: 'From scratch' and 'pretrained'.
1. From scratch: Start with a model which was just randomly initialised. Then train the model at each iteration using 100 images from the original
dataset and 2 images from the triggerset. 
2. Pretrained: Pretrain the model using the original dataset only. Then embed the watermark using the trigger set only.

### Removing the watermark
