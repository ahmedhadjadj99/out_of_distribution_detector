# Out of Distribution Detector
### Intoduction
As part of my graduation thesis *Inhancing deep learning classifiers using Out of Distribution detection* I made a full demo of these techniques using a web interface. using a combination of three OOD detection techniques (MSP, ODIN and the Energy function).
We used three models: two DenseNets trained on Cifar-10 and Cifar-100 datasets and EfficientNet trained on ImageNet-1000

### OOD techniques:

* Max Softmax Probability:

![image](https://user-images.githubusercontent.com/59343980/198407084-3440a22c-a8d1-409e-b3d3-5290956616d2.png)

* ODIN:

![image](https://user-images.githubusercontent.com/59343980/198407372-ad757ba7-a0d2-4a8e-bb07-7b80872122e9.png)

* Energy Function:

![image](https://user-images.githubusercontent.com/59343980/198407482-61b0d1c9-3945-47f1-a816-ef8fe700b658.png)


* The proposed technique which is the one used in this interface:

![image](https://user-images.githubusercontent.com/59343980/198407592-e21c164a-ada4-4a43-ac17-64869d013403.png)

### Method performance:

We measured the performance of the OOD detection of our proposed method vs the MSP detector.

|Architecture   |ID Dataset     |MSP (baseline) |Proposed method|
| ------------- |:-------------:| -------------:|--------------:|
|DenseNet       |CIFAR-10       |74.3%          |88.4%          |
|DenseNet       |CIFAR-100      |58.95%         |73.6%          |
|EfficientNet   |ImageNet       |69.55%         |74.85%         |





### Interface components:


![schema-01](https://user-images.githubusercontent.com/59343980/198405374-8c15c39c-7b5b-463e-9cb2-f4f18b6f4f63.png)

* Colab notebook:

In the Colab notebook we import all the libraries needed (Pytorch, Numpy, Flask, Ngrok…etc), we also have to load the three used pretrained models with their labels: ImageNet can be loaded from Pytorch library and Densenet 10 and 100 can be pulled from GitHub.
The notebook also contains the classification function that transforms the image depending on the selected model and applying our OOD detection method.


* The Flask app:

In the last cell we built the Flask  app, it contains the index function which gets the In-distribution dataset from the radio-box after pressing submit, and the predict-api function that grabs the image and pass it to the predict function in previous predict function cell, then it returns the prediction results to show it in the Vue.JS application.

* Front end:

In the Colab notebook, there are two cells dedicated to the front end application, one is for the home page where you select the In-distribution dataset, the second page is for uploading the image and classify it.


* Bridging:

There is a cell in the notebook dedicated to Ngrok authentication key, adding the key provided by Ngrok allows the local cloud application to be shared with anyone with internet access via Ngrok agent.
