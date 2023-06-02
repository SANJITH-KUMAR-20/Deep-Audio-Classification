# Deep-Audio-Classification
Using Tensorflow API to find the density of Capuchin bird calls in a forest

Data : The data used in the model formulation is from a kaggle Competition __https://www.kaggle.com/datasets/kenjee/z-by-hp-unlocked-challenge-3-signal-processing__
You can refer the kaggle documentation.

This is a CNN model that uses the spectrogram of different audio files from the dataset to classify between whether there is a Capuchin bird call or not.
1. load in the data and decode them using tensorflow_io module
2. pad the decoded data items
3. convert them to a spectrogram using tf.signal.stft( Short-Time Fourier Transformer)
4. Split into train and test sets
5. pass train data with their labels to our CNN model

Here the data is passed in as a tf.Dataset object after performing MCSBP(Map-Cache-Shuffle-Batch-Prefetch)
the fuction used in the mapping process decodes, pads and transforms the audio file.

After the training is done, we go through the actual test data, which are three minute audio files in .mp3 format:
1. load in the actual test data and decode them
2. Slice the audio files and preprocess them as before
3. Predict using the trained model
4. count and store the number of calls in each audio(Sequence of audio slices of the previously padded size)
5. save the result as a .csv file
