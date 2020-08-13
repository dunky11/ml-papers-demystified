## Have You Stolen My Model? Evasion Attacks Against Deep Neural Network Watermarking Techniques
#### https://arxiv.org/pdf/1809.00615v1.pdf

Backdooring is a common technique for watermarking neural networks. The party who wants to watermark the model uses a set of random images, with random classes assigned and trains the model
on them. They call this set of random images their key set. After reaching a high accuracy on the key set they use the set of images and their classes to verify that the model is theirs.
They define a threshold and by showing that the models accuracy on the key set is above that threshhold they prove that the model is theirs. This stept of querying
the model with the key set is called the verification step.

The paper proposes two methods to attack the verification step of the backdooring algorithm. 

### Ensemble Attack

The attacker gathers multiple models. Of those models a variable amount can be watermarked. It is necessary for the attack that the watermarked models have been watermarked using different key sets. 



![Ensemble Attack](https://raw.githubusercontent.com/dunky11/ml-papers-demystified/master/Have-You-Stolen-My-Model%3F-Evasion-Attacks-Against-Deep-Neural-Network-Watermarking-Techniques/media/table_1.png)
