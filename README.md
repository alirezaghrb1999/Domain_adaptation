# Domain_adaptation
Domain adaptation is a crucial aspect of machine learning and artificial intelligence that addresses the challenge of adapting a model trained on one domain to another domain with varying data distribution. The primary objective of domain adaptation is to enhance the performance of a model on a target domain by leveraging knowledge from a source domain. This approach is particularly useful when there is limited labeled data available for the target domain but abundant labeled data available for the source domain. Domain adaptation can be applied in diverse areas such as natural language processing, computer vision, speech recognition, and robotics.

One of the most effective techniques for solving domain adaptation problems is discriminative adversarial neural networks (DANN). By using DANN, I have successfully addressed a common issue in computer vision, where the feature distribution in the training dataset differs significantly from that in the test dataset. 

![dann](https://github.com/alirezaghrb1999/Domain_adaptation/assets/46087111/5af52cee-8f0a-452b-b985-7290c223940a?classes=caption "discriminative adversarial neural networks arcitecture")
<br>

The primary objective of the DANN method is to discover a network that can extract data features from both the source and destination domains, making it difficult for another network, known as the discriminator network, to distinguish between them. This method aims to bring together the domain distributions by extracting and mapping features to different spaces.

According to the DANN method, three different networks are utilized. The encoder network is responsible for receiving input data and extracting its features. The extracted features are then fed into the classification and discriminator networks. The classification network predicts the data label of the source domain, while the discriminator network determines whether the data belongs to the source or destination domain.

To train these networks, we input tagged data from the source domain and untagged data from the destination domain into the network. After extracting desired data characteristics, if it belongs to the source domain, it is simultaneously fed into both classification and discriminator networks. However, if it belongs to the destination domain, it is only entered into the discriminator network. This way, only data from the source domain is used to train the classification network, while both domains are used for domain matching.

Another objective of the encoder network is to extract common features so accurately that even the discriminator network cannot correctly identify which data comes from which domain. In other words, it aims to deceive or trick the discriminator network into recognizing domains in reverse order. Thus, there exists an adversarial relationship between the encoder and discriminator networks. During training of the encoder network, feedback is received from both classifier and discriminator networks in order to update weights. As this relationship is adversarial in nature, feedback received from this network is multiplied by negative values.

In general, the cost functions of the Discriminative Adversarial Network (DANN) method can be expressed as follows:

![Capture](https://github.com/alirezaghrb1999/Domain_adaptation/assets/46087111/09c62b59-76d9-4721-9019-b252aa580c45)

These cost functions state that the network that receives the source and destination data, map them as φ(XS) for the source data and as φ(XT) for the destination data, and the cost of the discriminator network should be maximized and the sum of the costs of the classifier network and the negated cost of the discriminator network should be minimized.

In This project we used two datasets as my source and destination domains comprises images of four types of vehicles: bus, car, pickup, and truck. The Mio dataset was utilized for the source domain, consisting of vehicle photos captured by CCTV cameras on the streets. These images typically have higher clarity and are taken from horizontal or aerial angles. In contrast, the destination domain contains a blend of aerial and CCTV camera photos from the streets of Iran, which exhibit slightly lower image quality and may include smaller-sized images.
<br>
<br>
MIO dataset (Source Domain):

<br>

![1](https://github.com/alirezaghrb1999/Domain_adaptation/assets/46087111/e78ab6ae-7293-4f6c-abd3-0de34cdb6585)
![2](https://github.com/alirezaghrb1999/Domain_adaptation/assets/46087111/f3ff01d7-23f3-42b5-b7ec-287d9d3a3104)
![3](https://github.com/alirezaghrb1999/Domain_adaptation/assets/46087111/28bbeb96-95fe-4e9a-a9e4-8a799975442c)
![4](https://github.com/alirezaghrb1999/Domain_adaptation/assets/46087111/a3626f27-3015-4dbc-a725-fdefc3d9deb4)

<br>
Iran's Vehicle dataset (Target Domain):
<br>
<br>

![1](https://github.com/alirezaghrb1999/Domain_adaptation/assets/46087111/219c229c-a3a8-4885-9f93-3e688cbad282)
![2](https://github.com/alirezaghrb1999/Domain_adaptation/assets/46087111/733b3789-9893-4c82-956f-d53a93285ca2)

in order to showcase the effectiveness of Domain Adaptation techniqe for this image classification problem, first I trained Resnet50 network without domain adaptation (vehicle.ipynb) and then used DANN technique (vehicle_DANN.ipynb) to increace model accuracy by bringing domains' distributions closer to each other. The results showed that DANN significantly improved the model's performance on the target domain by effectively leveraging knowledge from the source domain.

<br>
Model Accuracy during training and data encoding of source and destination domains without DA :

<br>
<br>

![Capture](https://github.com/alirezaghrb1999/Domain_adaptation/assets/46087111/f068cb3b-1e3b-48b9-af83-9c6418692e56)


<br>
Model Accuracy during training and data encoding of source and destination domains with DA : 

<br>
<br>

![2](https://github.com/alirezaghrb1999/Domain_adaptation/assets/46087111/56f25aa2-f87a-41e0-b552-4b3f6f4dbd17)

