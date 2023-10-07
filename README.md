# Speech-Emotion-Recognition

Emotions play a crucial role in communication and provide vital insights about speaker’s intentions. Speech Emotion Recognition is a vital and challenging task for computers as well as for humans because emotions are subjective. The SER system that we are working towards uses Deep Learning to classify emotions based on the features extracted from the audio samples. SER system has a wide variety of application areas such as interactive voice based virtual assistant, mental health monitoring etc.​

The first dataset that we are using for the SER system is Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS). ​
- The dataset contains 24 professional actors (12 male, 12 female), vocalizing two lexically-matched statements in a neutral North American accent . ​
- Speech emotions include calm, happy, sad, angry, fearful, surprise and disgust expressions. ​
- Each expression is produced at normal intensity and strong intensity.​
- Emotion calm has been excluded to keep common emotions of both the datasets.​

The second dataset that we are using for the SER system is Toronto  Emotional Speech Set (TESS).​
- There are a set of 200 target words were spoken by two actresses (aged 26 and 64 years).
- The dataset has 7 emotions, anger, disgust, fear, happiness, pleasant surprise, sadness, and neutral. ​
- There are 2800 audio files in total.​
- The dataset is organized such that each of the two female actor and their emotions are contain within its own folder. ​

**Convolutional Neural Networks and LSTM:​**
- The CNN model used in this project consists of 3 main blocks. All the three blocks include two convolutional layers. Each convolutional layer is followed by a ReLU activation. At the end of each block max pooling operation is applied. ​
- The input images are first passed through two convolutional layers, after that ReLU activation operation is used to induce non-linearity. A dropout operation is used to avoid overfitting. A 2x2 max pooling layer is used for reducing the spatial dimensions of feature maps. ​
- After the CNN part is complete the data has to be reshaped to be provided as input to the LSTM layers. The hidden unit size used here is 100. The first LSTM layer takes the flattened feature vector and outputs a sequence with 100 hidden units at each step.
- The subsequent LSTM layer receives the output from the initial LSTM layer as input and continues processing. This layer will output a sequence with a predefined number of hidden units.
- After passing through the all the layers, the output tensor is flattened using the view function. This is needed because input to the linear layer must be a 2-dimensional tensor.​
- The linear layer (fully connected layer) is the layer that is responsible for final classification. It maps the flattened tensor received from the previous layer and maps it to an output of size equal to the number of classes of dataset, representing the predicted class probabilities.​

**DenseNet:**
- Densenet is a deep convolutional network which specializes in image classification​.
- A typical DenseNet architecture consists of dense blocks and transition blocks. The dense blocks are the key building blocks of the network and are responsible for feature extraction. ​
- Each dense block contains multiple layers, and each layer has a dense connection to all the previous layers within the same block. ​
- The dense connectivity promotes feature reuse and allows information to flow directly across layers, which helps alleviate the vanishing gradient problem and encourages feature propagation.​
- The transition blocks are used to control the number of feature maps and reduce the spatial dimensions of the feature maps between dense blocks.​
- The DenseNet model implemented in the code has a total of four dense blocks and three transition blocks. The growth rate parameter determines the number of output feature maps for each layer within a dense block.​
- The model starts with an initial convolutional layer with a 7x7 kernel, followed by batch normalization, ReLU activation, and max pooling to reduce the spatial dimensions. After the initial block, the subsequent dense blocks and transition blocks are stacked. ​
- The number of input channels to the first dense block is 64, which corresponds to the number of output channels from the initial block. As the dense blocks progress, the number of input channels is increased based on the growth rate and the number of layers in the previous dense block.​
- The model starts with an initial convolutional layer with a 7x7 kernel, followed by batch normalization, ReLU activation, and max pooling to reduce the spatial dimensions. After the initial block, the subsequent dense blocks and transition blocks are stacked. ​
- The final part of the model consists of a batch normalization layer, adaptive average pooling to reduce the feature maps to a fixed size, and a linear layer for classification. The number of output classes is specified as the number of emotions in the dataset when initializing the DenseNet model.​
- During the forward pass, the input images are passed through convolutional layers, dense blocks, and transition blocks. The output of the last transition block is passed through batch normalization, adaptive average pooling, and reshaping to a 1-dimensional tensor. Finally, the tensor is passed through the linear layer to obtain the predicted class probabilities.​





