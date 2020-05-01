# Hot-Dog-Classifier
This project was inspired by an episode on the HBO TV show, 'Silicon Valley'.

It is a binary classifier which predicts whether a given image contains a hot dog or not.

Step 1 - Gathering the data
Before proceeding to the fancy part of creating the model, we firt actually need to gather the data which will be used train the model.
After trying out a number of packages that help download images off google, I finally figured that none of these packages work as Google as made some change to their code. Then I turned to a chrome extension 'Fatkun' which helped me download images from not only Google, but Bing as well. I tried gathering nearly 1500 images of hot dogs by searching for various keywords like 'hot dog' , 'chilli dog', 'frankfurter'. The good thing about Fatkun is that it let me choose which images should be downloaded, so I could perform a little data cleaning as well.
For the Not Hot Dog category, I downloaded images of different kinds of foods, cars and people. Ended up with about 1200 images for this category.

Step 2 - Building the Model
v1 - To start things of, I used Keras ImageDataGenerator to load images from disk. The model was a basic CNN model consisting of 4 CNN layers and 3 Dense layers. Trainig for 10 epochs and with a batch size of 10, it achieved a validation accuracy of 87.63%. I tested the model with a few images of my own and it was quite good at figuring out images of hot dogs. But the main problem with this version was the Keras ImageDataGenerator, which was quite slow in generating batches for training. Each epoch took around 110s on average.

v3 - After going through few docs on TensorFlow, I decided to use tf.Data.Dataset. Following the docs on Tensorflow's website allowed me to create a much better input pipeline for my model. I also decided to train my model on Paperspace Gradient which provide a free GPU (I used the P5000 instance). This helped significantly speed up the training process. Training for 10 epochs with a batch size of 20 resulted in a model that was overfitting a little. After seeing the loss and accuracy graphs, I decided to use 7 epochs next. At the end the model achieved 100% accuracy on the traing and 99.05% accuracy on the validation set. This model correctly classified all my testing images as well!
