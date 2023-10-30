# Speech Emotion Analyzer

* The goal of this research was to create a machine learning model that could recognize emotions from the speech we all use all the time. Nowadays, personalization is required in everything we encounter on a daily basis.

* So why not have an emotion detector that will gauge your feelings and recommend different items based on your mood in the future? 
Multiple businesses can leverage this to provide different services, such as marketing companies recommending things based on your emotions, the automobile industry detecting people's emotions and adjusting the speed of autonomous cars as needed to avoid crashes, and so on.

<br>

### Datasets:
Made use of two different datasets:
1. [RAVDESS](https://zenodo.org/record/1188976).
This dataset contains approximately 1500 audio files from 24 distinct actors. 12 male and 12 female performers record brief audio clips expressing 8 various emotions, i.e. 1 = neutral, 2 = calm, 3 = joyful, 4 = sad, 5 = furious, 6 = afraid, 7 = disgusted, 8 = astonished.<br>
Each audio file is named in such a way that the seventh character corresponds to the many emotions that they convey.

3. [SAVEE](http://kahlan.eps.surrey.ac.uk/savee/Download.html).
This dataset includes approximately 500 audio files recorded by four different male performers. The first two characters of the file name represent the various emotions that the potrays. 

## Audio files:
The audio files were tested by graphing the waveform and a spectrogram to observe the sample audio files.<br>
**Waveform**
![](images/wave.png?raw=true)
<br>
<br>
**Spectrogram**<br>
![](images/spec.png?raw=true)
<br>

## Feature Extraction
The next step involves extracting the features from the audio files which will help our model learn between these audio files.
For feature extraction we make use of the [**LibROSA**](https://librosa.github.io/librosa/) library in python which is one of the libraries used for audio analysis. 
<br>
![](images/feature.png?raw=true)
<br>
* Here are some points to consider. All audio files were timed for 3 seconds while being extracted for an equal amount of features. 
* When the size of the dataset is modest, the sampling rate of each file is doubled while the sampling frequency remains fixed in order to obtain more features that will aid in the classification of the audio file.
<br>

**The extracted features looks as follows**

<br>

![](images/feature2.png?raw=true)

<br>

These are array of values with lables appended to them. 

## Building Models

Because this is a classification task, **Convolution Neural Network** appears to be the obvious choice. We also created **Multilayer Perceptrons** and **Long Short Term Memory** models, however they underperformed with extremely low accuracies, failing to pass the test while predicting the correct emotions.

Building and tuning a model takes a significant amount of time. The aim is to always start basic and avoid adding too many layers only to make it more complex. After layer testing, the model with the highest validation accuracy against test data was slightly more than 70%.
<br>
<br>
![](images/cnn.png?raw=true)
<br>

## Predictions

After fine-tuning the model, it was put to the test by predicting the emotions for the test data. These are actual vs expected values for a model with the appropriate accuracy.
<br>
<br>
![](images/predict.png?raw=true)
<br>

## Testing out with live voices.
We recorded our own voices with varied emotions and forecasted the outcomes to test our model on voices that were radically different from what we had in our training and test data. The outcomes are shown below:
The recording contained an angry male voice saying **"This coffee sucks"**.
<br>
![](images/livevoice.PNG?raw=true)
<br>
<br>
![](images/livevoice2.PNG?raw=true)
<br>

### In the image above, you can see that the model predicted the male voice and mood pretty precisely.

## NOTE: If you are directly using the model and wish to decode the output spanning from 0 to 9, the list below will assist you.

0 - female_angry <br>
1 - female_calm <br>
2 - female_fearful <br>
3 - female_happy <br>
4 - female_sad <br>
5 - male_angry <br>
6 - male_calm <br>
7 - male_fearful <br>
8 - male_happy <br>
9 - male_sad <br>

## Conclusion
Building the model was a difficult effort because it required a lot of trial and error methods, adjusting, and so on. The model has been extremely thoroughly trained to discern between male and female sounds, and it does so with 100% accuracy. The algorithm has been fine-tuned to recognize emotions with greater than 70% accuracy. More audio files for training can help improve accuracy.
