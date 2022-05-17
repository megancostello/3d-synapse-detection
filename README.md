# 3D Synapse Detection - Colab Inference Pipeline Tutorial
Final Project for CSCI 3397 - Biomedical Image Analysis. Using Pytorch Connectomics and 3D UNet model to use 3D segmentation for synapse detection, using semi-unsupervised learning

Outlined below are the main commands from the Colab to run and execute the pipeline. See the Colab file for more details and implementation.

## Clone the Github
`! git clone https://github.com/ryanraff43/pytorch_connectomics.git`

## Set current directory and install necessary packages
`! cd pytorch_connectomics && pip install --editable .`

## Training command

`! python -u /content/pytorch_connectomics/scripts/main.py \
--config-base /content/pytorch_connectomics/configs/JWR15/synapse/JWR15-Synapse-Base.yaml \
--config-file /content/pytorch_connectomics/configs/JWR15/synapse/JWR15-Synapse-BCE-DICE-Regu.yaml`

## Inference

`! python -u /content/pytorch_connectomics/scripts/main.py \
--inference --config-base /content/pytorch_connectomics/configs/JWR15/synapse/JWR15-Synapse-Base.yaml \
--config-file /content/pytorch_connectomics/configs/JWR15/synapse/JWR15-Synapse-BCE-DICE-Regu.yaml \
--checkpoint outputs/JWR15_Syn_BCE_DICE_Regu/checkpoint_00200.pth.tar`

## Post-Processing 

`volume = readvol('/content/outputs/JWR15_Synapse/test/result_0-25-0-1428-5000-6250.h5')`

`instances = polarity2instance(volume)`

`savevol('instance_output.h5', instances)
`
# Contributions

Megan - data download, YAML edits, inference, post processing

Ryan - GitHub cloning, YAML edits, tensorboard visualization, training, converting .h5 to json, inference

Aidan - YAML edits, tensorboard visualization, inference


