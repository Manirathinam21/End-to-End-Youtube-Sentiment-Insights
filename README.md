# End-to-End-Youtube-Sentiment-Insights

## Intial setup

1. To create an environment

``
 conda create -p venv python=3.11 -y

 source activate venv/

``
2. To Install the required python packages

``
pip install -r requirements.txt
``

## DVC commands

1. To intiate the DVC
``
dvc init
``
2. To run the different stages in automated way using dvc
``
dvc repro 
``
``
dvc dag
``