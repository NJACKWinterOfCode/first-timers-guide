# Capsule neural network

### What is a Capsule Network?
A Capsule Neural Network (CapsNet) is a machine learning system that is a type of artificial neural network (ANN) that can be used to better model hierarchical relationships. The approach is an attempt to more closely mimic biological neural organization.

### Equivariance
Equivariance is the detection of objects that can transform to each other. A spatial relationship can be characterized represented by its pose, data that describes the object's translation and rotation. Translation is a change in location in one or more dimensions, while rotation is a change in orientation.

Unsupervised capsnets learn a global linear manifold between a whole object and its pose (as a matrix of weights). As such, the translation invariance is encapsulated in the weights, rather than in neural activity (recognition), making the network translation equivariant. Multiplying the object by the manifold thereby poses the object (for an object, in space).

### Pooling
Capsnets reject the pooling layer strategy of conventional CNNs that reduces the amount of detail to be processed at the next higher layer. Pooling allows a degree of translational invariance (it can recognize the same object in a somewhat different location) and allows a larger number of feature types to be represented. Capsnet proponents argue that pooling:

- violates biological shape perception in that it has no intrinsic coordinate frame;
- provides invariance (discarding positional information) instead of equivariance (disentangling that information);
- ignores the linear manifold that underlies many variations among images;
- routes statically instead of communicating a potential "find" to the feature that can appreciate it;
- damages nearby feature detectors, by deleting the information they rely upon.

### Capsules
A capsule is a set of neurons that individually activate for various properties of a type of object, such as position, size and hue. Formally, a capsule is a set of neurons that collectively produce an activity vector with one element for each neuron to hold that neuron's instantiation value (e.g., hue). Graphics programs use instantiation value to draw an object. Capsnets attempt to derive these from their input. The probability of the entity's presence in a specific input is the vector's length, while the vector's orientation quantifies the capsule's properties.

Artificial neurons traditionally output a scalar, real-valued activation that loosely represents the probability of an observation. Capsnets replace scalar-output feature detectors with vector-output capsules and max-pooling with routing-by-agreement.

Because capsules are independent, when multiple capsules agree, the probability of correct detection is much higher. A minimal cluster of two capsules considering a six-dimensional entity would agree within 10% by chance only once in a million trials. As the number of dimensions increase, the likelihood of a chance agreement across a larger cluster with higher dimensions decreases exponentially.

Capsules in higher layers take outputs from capsules at lower layers, and accept those whose outputs cluster. A cluster causes the higher capsule to output a high probability of observation that an entity is present and also output a high-dimensional (20-50+) pose.

Higher-level capsules ignore outliers, concentrating on clusters. This is similar to the Hough transform, the RHT and RANSAC from classic digital image processing.

### Human vision
Human vision examines a sequence of focal points (directed by saccades), processing only a fraction of the scene at its highest resolution. Capsnets build on inspirations from cortical minicolumns (also called cortical microcolumns) in the cerebral cortex. A minicolumn is a structure containing 80-120 neurons, with a diameter of about 28-40 µm, spanning all layers in the cerebral cortex. All neurons in the larger minicolumns have the same receptive field, and they output their activations as action potentials or spikes. Neurons within the microcolumn receive common inputs, have common outputs, are interconnected and may constitute a fundamental computational unit of the cerebral cortex.

Capsnets explore the intuition that the human visual system creates a tree-like structure for each focal point and coordinates these trees to recognize objects. However, with capsnets each tree is "carved" from a fixed network (by adjusting coefficients) rather than assembled on the fly.

<img src="https://cdn-images-1.medium.com/max/1600/1*P1y-bAF1Wv9-EtdQcsErhA.png" />
**CapsNet Architecture**

### What is the problem with CNNs?
CNNs perform exceptionally great when they are classifying images which are very close to the data set. If the images have rotation, tilt or any other different orientation then CNNs have poor performance. This problem was solved by adding different variations of the same image during training. In CNN each layer understands an image at a much more granular level. Lets understand this with an example. If you are trying to classify ships and horses. The innermost layer or the 1st layer understands the small curves and edges. The 2nd layer might understand the straight lines or the smaller shapes, like the mast of a ship or the curvature of the entire tail. Higher up layers start understanding more complex shapes like the entire tail or the ship hull. Final layers try to see a more holistic picture like the entire ship or the entire horse. We use pooling after each layer to make it compute in reasonable time frames. But in essence it also loses out the positional data.

Pooling helps in creating the positional invariance. Otherwise CNNs would fit only for images or data which are very close to the training set. This invariance also leads to triggering false positive for images which have the components of a ship but not in the correct order. So the system can trigger the right to match with the left in the above image. You as an observer clearly see the difference. The pooling layer also adds this sort of invariance.
<img src="https://cdn-images-1.medium.com/max/1200/1*0RGB8Eql5j27ujkt--yB_Q.png" />
**Disfiguration transformation**

This was never the intention of pooling layer. What the pooling was supposed to do is to introduce positional, orientational, proportional invariances. But the method we use to get this uses is very crude. In reality it adds all sorts of positional invariance. Thus leading to the dilemma of detecting right ship in image 2.0 as a correct ship. What we needed was not invariance but equivariance. Invariance makes a CNN tolerant to small changes in the viewpoint. Equivariance makes a CNN understand the rotation or proportion change and adapt itself accordingly so that the spatial positioning inside an image is not lost. A ship will still be a smaller ship but the CNN will reduce its size to detect that. This leads us to the recent advancement of Capsule Networks.
<img src="https://cdn-images-1.medium.com/max/1200/1*k7cUF8V3BdiD3k7e4sHgHw.png" />
**Proportional transformation**

### conceptual advantages over CNN
- Viewpoint invariance: the use of pose matrices allows capsule networks to recognize objects regardless of the perspective from which they are viewed.
- Fewer parameters: Because capsules group neurons, the connections between layers require fewer parameters.
- Better generalization to new viewpoints: CNNs, when trained to understand rotations, often learn that an object can be viewed similarly from several different rotations. However, capsule networks generalize better to new viewpoints because pose matrices can capture these characteristics as linear transformations.
- Defense against white-box adversarial attacks: the Fast Gradient Sign Method (FGSM) is a typical method for attacking CNNs. It evaluates the gradient of each pixel against the loss of the network, and changes each pixel by at most epsilon (the error term) to maximize the loss. Although this method can drop the accuracy of CNNs dramatically (e.g: to below 20%), capsule networks maintain accuracy above 70%.