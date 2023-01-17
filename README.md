# Analysis on the Energetic Impact of Deep Learning Training

This repository contains the data and code used to generate the results described in the master thesis "An analysis of
modeling and training decisions for greener computer vision systems".

## Datasets

In the data folder you will find two folders. In the `raw` folder, you will find a file containing the energetic data of
all the experiment runs and a file containing the model metrics (i.e., FLOPs, accuracy, precision, recall, and AUC). In
the `processed` folder, you will find the data obtained after integrating the files in the `raw` folder, and extracting
revelant features.

All the files inside the `data` folder have been saved using Panda's ``to_parquet`` function using the GZIP format.

### DL Training Profiling Dataset

The DL Training Profiling dataset contains all the energy-related measurements taken during the training of the models
tested in the study.

You will find a detailed description of the dataset in its [dataset card](data/raw/dataset_card.md).

## Data analysis

The repository contains a Jupyter Notebook with the code used to clean and analyze the data.

## License

The software in this work is licensed under the [Apache 2.0 License](LICENSE).

The files under the `data` folder are licensed under the [CC-By Attribution 4.0 International](data/LICENSE).
