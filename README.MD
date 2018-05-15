# Keras Music Composer
This model uses deep learning with Keras and a LSTM to compose music. Music, here
is stored as MIDI files, which can be trained on. The model will then compose original
music based on the music it has received as training examples. In this example,
it will train on music from the composer Frédéric Chopin.

[Video Demo](https://youtu.be/ZGb4mmOP2nQ)

## Preprocessing
The model takes MIDI files, which often have more than one track. These are processed
by choosing a track on which to train on, and using the music21 library to create a dictionary
of notes and chords which were used in the song.
Before being fed into the model, they are converted with one-hot-encoding based on the
note or chord at each time in the song.

![Train](/screenshots/train.png)

## Results
One way to tune this model is to adjust the length of the sequence fed into the LSTM.
For example, when using 20 notes as a sequence, the model's output tends to get stuck
after a little while and doesn't know what to predict next so it predicts the same thing a few
times before figuring out what to do. When using a 50 note sequence this does not occur. In this
situation, the model does not generalize as well since it is only trained on one song each time.
When trained with a sequence of twenty, one output can be seen here:

![Twenty](/screenshots/twenty.png)

When training with a sequence of fifty, one output can be seen here. As can be noticed,
training with fifty does not lead to a short sequence where the same note is repeated.

![Fifty](/screenshots/fifty.png)



## Data
The data which was used to train on can be seen in the "trainedOn" folder, although any MIDI file with
a melody should work (just make sure the track number on preprocessing is changed).
Example MIDI outputs can be found in the output folder. To listen to how they sound,
you can drag them onto any music creation software like Garageband, Logic, etc.


## Running the model
The only thing necessary to change before running the model is creating a folder
entitled 'music' and including the MIDI file on which to train on in it.
