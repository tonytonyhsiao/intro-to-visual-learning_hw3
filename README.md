# FCN(Fully Convolutional Network) & CAM(Class Activation Mapping)


<!-- ABOUT THE PROJECT -->
## About The Project
For this assignment, in the first part, we're going to use Deep Learning for a new task: semantic segmentation. In the second part, you will interpret networks with the class activation map (CAM).

This project contains two parts.

* FCN(Fully Convolutional Network)
* CAM(Class Activation Mapping)




## FCN(Fully Convolutional Network)
We train the network for 20 epochs with pretrained VGG-16 weights and record the best model. Visualize the prediction results and report the test accuracy.


![The result of the semantic segmentation using FCN-8s model](https://github.com/tonytonyhsiao/intro-to-visual-learning_hw3/blob/main/fig/fcn-8%20result.png)
The result of the semantic segmentation using FCN-8s model


FCN-8s layer
![FCN-8s layer](https://github.com/tonytonyhsiao/intro-to-visual-learning_hw3/blob/main/fig/fcn-8%20result.png)
FCN-8s layer


Training FCN-32s from scratch compared to using pretrained weights yields noticeable differences in terms of convergence speed and final performance. When training from scratch, the model learns from random initialization of weights, resulting in slower convergence and potentially lower final performance compared to using pretrained weights. Pretrained weights, on the other hand, are learned from a large dataset and capture general features that are useful for various tasks, including semantic segmentation.
Observations: I observed the convergence speed are different, FCN-32s with pretrained weights converges faster compared to training from scratch. Pretrained weights provide a good initialization point, allowing the model to start from a more optimal position in the weight space. I also observed the final performance are different, FCN-32s with pretrained weights achieves better final performance in terms of accuracy and generalization. The pretrained weights capture useful features learned from a diverse dataset, which can be transferable to the target task of semantic segmentation.
The figures below show the comparision of the Average Accuracy and Mean IOU diagram of FCN-32 with and without pretrain.

![c1](https://github.com/tonytonyhsiao/intro-to-visual-learning_hw3/blob/main/fig/diagram1.png)

Comparing the performance and visualization of FCN-32s and FCN-8s, both with pretrained weights, reveals differences in their abilities to capture spatial details and semantic information.
Observations: I observed FCN-8s performs better than FCN-32s, especially in capturing fine spatial details and boundaries. This improvement is due to the incorporation of skip connections in FCN-8s, which combine high-resolution features from earlier layers with coarse features from deeper layers. This enables the model to refine segmentation boundaries and capture fine-grained details more effectively.
Moreover, FCN-8s produces visually smoother and more detailed segmentation masks compared to FCN-32s. The skip connections in FCN-8s facilitate the flow of information at multiple scales, allowing the model to preserve spatial details while maintaining semantic consistency.
FCN-8s performs better due to its ability to combine multi-scale features through skip connections. By incorporating features from different levels of the network hierarchy, FCN-8s can capture both local details and global context effectively, resulting in improved segmentation accuracy. Additionally, skip connections mitigate the vanishing gradient problem during backpropagation, enabling better gradient flow and more stable training.
The figures below show the comparision of the Average Accuracy and Mean IOU diagram of pretrain FCN-32 and pretrain FCN-8.
![c2](https://github.com/tonytonyhsiao/intro-to-visual-learning_hw3/blob/main/fig/diagram2.png)

## CAM(Class Activation Maps)

In this section, we are going to interpret neural networks decisions with the technique class activation maps (CAM), the idea is that one can highlight the image region that is important to the prediction.
The resnet-18 uses global average pooling for downsampling layer 4 features and then applies an FC layer to predict the class probabilities. We select the class with the highest probability as our best guess and we denote the corresponding FC weight as w.
Let f4(x,y) denote the layer 4 feature at spatial location (x,y). Now we can directly apply the learned FC weight w to f4(x,y) to get the network prediction for this spatial location CAM(x,y). CAM can be obtained by repeating this for all spatial locations.

![cam](https://github.com/tonytonyhsiao/intro-to-visual-learning_hw3/blob/main/fig/cam%20result%202.png)
result of the CAM


![cam](https://github.com/tonytonyhsiao/intro-to-visual-learning_hw3/blob/main/fig/cam%20result1.png)
result of the CAM
