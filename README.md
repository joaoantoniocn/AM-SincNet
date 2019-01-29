
# AM-SincNet
AM-SincNet is a new approach for speaker recognition problems which is based in the neural network architecture SincNet and the additive margin softmax  (AM-Softmax) loss function. It uses the architecture of the SincNet, but with an improved AM-Softmax layer.

This repository releases an example of code to perform a speaker identification experiment on the TIMIT dataset. To run it with other datasets you can have a look at the instructions on the original SincNet repository (https://github.com/mravanelli/SincNet).

We should thank [@mravanelli](https://github.com/mravanelli/) for the [SincNet implementation](https://github.com/mravanelli/SincNet).

## Requirements
For running this experiment we used a Linux environment with Python 3.6.

You can see a list of python dependencies at [requirements.txt](requirements.txt).

To install it on conda virtual environment (`conda install --file requirements.txt`).

To install it on pip virtual environment (`pip install -r requirements.txt`).

## How to Run
To run it on TIMIT dataset we have first to pre-process the data, removing the start and ending silences moments and also normalizing the audio sentences.

``
python TIMIT_preparation.py $TIMIT_FOLDER $OUTPUT_FOLDER data_lists/TIMIT_all.scp
``

where:
- *$TIMIT_FOLDER* is the folder of the original TIMIT corpus
- *$OUTPUT_FOLDER* is the folder in which the normalized TIMIT will be stored
- *data_lists/TIMIT_all.scp* is the list of the TIMIT files used for training/test the speaker id system.

then, we can run the experiment itself by typing.

``
python speaker_id.py --cfg=cfg/$CFG_FILE
``

where:
- *$CFG_FILE* is the name of the cfg configuration file which is located at cfg folder.

We have made avaliable several cfg configuration files for the experiments, if you want to run the experiment with the traditional SincNet (with no use of the AM-Softmax layer) you must use the [*SincNet_TIMIT.cfg*](cfg/SincNet_TIMIT.cfg) file, otherwise you can use the *SincNet_TIMIT_m0XX.cfg* file where the *XX* denotes the size of the margin parameter used for the AM-Softmax layer.
