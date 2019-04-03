# Recognizing Musical Entities in User-generated Content

We present a novel method for detecting musical entities from user-generated content, modelling linguistic features with statistical models and extracting contextual information from a radio schedule.  We analyzed tweets related to a classical music radio station, integrating its schedule to connect users' messages to tracks broadcasted. 

This repository contains code to reproduce the results of our [arXiv paper](https://arxiv.org/abs/1904.00648).

#### Reference:
> Lorenzo Porcaro, Horacio Saggion (2019). Recognizing Musical Entities in User-generated Content. Paper presented at the International Conference on Computational Linguistics and Intelligent Text Processing (CICLing) 2019, University of La Rochelle, La Rochelle, 7-13 April.


## Reproduce our results

#### Installation:
Create a python 2.7 (sorry!) virtual environment and install dependencies `pip install -r src/requirements.txt`

#### Update config file:
Update the file `etc/config.yaml`, insert your consumer key, consumer secret, access token, access secret from the Twitter API. More info about the API: https://developer.twitter.com/

#### Import data:
To receive the data for reproducing the experiment, please contact `lorenzo.porcaro at gmail.com`. Once received, go to the data [README](https://github.com/LPorcaro/musicner/tree/master/data) page for more info 

#### Pre-process data:
To pre-process the data, run:

`python hydrate_tweet.py -i ../path/to/input/file.json`

It will read the tweet IDs and related annotations from the input file, and create the following output files
1) **INPUTFILE_entities.csv**: file with list of entities annotated
2) **INPUTFILE_summary.csv**: file with tweets summary information (creation date, raw text, etc)
3) **INPUTFILE__text_tkn.txt**: file with tweet raw texts tokenized

#### Extract Features:
To extract the required features from the data, run:

`python extract_features.py -i ../path/to/INPUTFILE_summary.csv -e ../path/to/INPUTFILE_entities.csv -o ../path/to/OUTPUTFILE_WEKA.csv`

It extracts several features from the input tweets for performing experiments with Neural Networks and Machine Learning models. It creates two output files, one which can be used as input in WEKA, and one which can be used as input in BiLSTM-CNN-CRF architecture for sequence tagging implementation https://github.com/UKPLab/emnlp2017-bilstm-cnn-crf


