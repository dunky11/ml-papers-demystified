## Have You Stolen My Model? Evasion Attacks Against Deep Neural Network Watermarking Techniques
#### https://arxiv.org/pdf/1809.00615v1.pdf

Backdooring is a common technique for watermarking neural networks. The party who wants to watermark the model uses a set of random images, with random classes assigned and trains the model on them. They call this set of random images their key set. After reaching a high accuracy on the key set they use the set of images and their classes to verify that the model is theirs.
They define a threshold and by showing that the models accuracy on the key set is above that threshhold they prove that the model is theirs. This stept of querying
the model with the key set is called the verification step.

The paper proposes two methods to attack the verification step of the backdooring algorithm. Both attacks only work in a black box settings, so the owner of the model who wants to verify their key doesn't have access to the models parameters and only has access to an API.

### Ensemble Attack

The attacker gathers multiple models. Of those models a variable amount can be watermarked. It is necessary for the attack that the watermarked models have been watermarked using different key sets. All queries to the models go trough an API layer. All models are then queries and the classes with the most predictions is send back. If two classes have the same amount of predictions a dice is rolled. This deminishes the accuracy the owner of the model have on their verification set.
The architecture is shown below.

<img src="https://raw.githubusercontent.com/dunky11/ml-papers-demystified/master/Have-You-Stolen-My-Model%3F-Evasion-Attacks-Against-Deep-Neural-Network-Watermarking-Techniques/media/table_1.png" width="auto" height="300">

They showed that this process works by embedding 7 different trigger sets on 7 models. The trigger set contained 10 images of abstract images for each model with random classes assigned to them. They embedded the trigger set while training the network on the MNIST dataset. Each of the 7 models had an accuracy of above 99% on the MNIST dataset an accuracy of 100% on their trigger set. The figure below shows the accuracy of the trigger set of each of the models after they were essembled.

<img src="https://raw.githubusercontent.com/dunky11/ml-papers-demystified/master/Have-You-Stolen-My-Model%3F-Evasion-Attacks-Against-Deep-Neural-Network-Watermarking-Techniques/media/average_trigger_acc.png" width="auto" height="300">

### Detector Attack

In this blackbox attack the adversary only needs one model. The adversary builds a binary detector model, which will predict if the input is a trigger set element or training set element. If the owner of the model queries the API the binary detector model will check the trigger set image and should predict that it's a trigger set element. After that it will return a random class or return nothing. If the binary detector detects that the input is a dataset element it will return the prediction of the watermarked model.
The binary detector model is build by first copying the watermarked model. The last fully connected layers of the CNN are cut. Then they are replaced by new fully connected layers, in their example they used 3 layers of 512, 265 and 2 neurons. For training the binary detector they used a set of clean images which the detector should classify as valid images and a set of abstract images which the classifier should detect as trigger set images.
Training this binary classifier is really fast, since all the parameters except the added fully connected layers are freeezed. They achieved an accuracy of 90% when predicting trigger set images.
