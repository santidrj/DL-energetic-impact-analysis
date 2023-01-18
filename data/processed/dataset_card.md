# Dataset Card for DL Training Energy Consumption Dataset

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Dataset Description](#dataset-description)
  - [Dataset Summary](#dataset-summary)
  - [Supported Tasks and Leaderboards](#supported-tasks-and-leaderboards)
  - [Languages](#languages)
- [Dataset Structure](#dataset-structure)
  - [Data Instances](#data-instances)
  - [Data Fields](#data-fields)
  - [Data Splits](#data-splits)
- [Dataset Creation](#dataset-creation)
  - [Curation Rationale](#curation-rationale)
  - [Source Data](#source-data)
  - [Annotations](#annotations)
  - [Personal and Sensitive Information](#personal-and-sensitive-information)
- [Considerations for Using the Data](#considerations-for-using-the-data)
  - [Social Impact of Dataset](#social-impact-of-dataset)
  - [Discussion of Biases](#discussion-of-biases)
  - [Other Known Limitations](#other-known-limitations)
- [Additional Information](#additional-information)
  - [Dataset Curators](#dataset-curators)
  - [Licensing Information](#licensing-information)
  - [Citation Information](#citation-information)
  - [Contributions](#contributions)

## Dataset Description

- **Homepage:**
- **Repository:** [DL training energetic impact analysis](https://github.com/santidrj/DL-energetic-impact-analysis)
- **Paper:**
- **Leaderboard:**
- **Point of Contact:** [Santiago del Rey](mailto:santiago.del.rey@upc.edu)

### Dataset Summary

The DL Training Energy Consumption Dataset is an English-language dataset containing 150 samples of energy-related
metrics of DL training, and DL model prediction quality metrics. The data correspond to training three different
models using two different training strategies (i.e., Local and Cloud). We have trained each model 30 times for each
training strategy.

### Supported Tasks and Leaderboards

The dataset can be used to study the effect of training different Deep Learning models on energy consumption, and its
trade-off with prediction quality.

### Languages

The BCP-47 code for English as generally spoken in the United States is en-US and the BCP-47 code for English as
generally spoken in the United Kingdom is en-GB.

## Dataset Structure

### Data Instances

Each data instance contains the training strategy used, the architecture of the base model, the run number,
the training duration, the GPU usage, the energy-related metrics, the computational complexity in GFLOPs, and the
model prediction quality metrics.

```json
{
  "training strategy": "cloud",
  "architecture": "mobilenet_v2",
  "run": 0,
  "training duration (h)": 0.7350283333,
  "gpu working time (h)": 0.1689055556,
  "gpu usage": 0.2299773071,
  "gpu memory working time (h)": 0.0616944444,
  "gpu memory usage": 0.0840015129,
  "average memory used (MB)": 23648.7526475038,
  "memory used std (MB)": 24.9827956804,
  "total power (W)": 414928.0,
  "average temperature (Celsius)": 54.269667171,
  "temperature std (Celsius)": 1.8318169329,
  "energy (GJ)": 1.0979418107,
  "emissions (tCO2e)": 0.0707563066,
  "GFLOPs": 0.06402816,
  "accuracy": 0.9756289124,
  "precision": 0.9598264694,
  "recall": 0.9931694269,
  "AUC": 0.995674789
}
```

### Data Fields

- `train_strategy`: The type of machine used to train the DNN. It can be _local_ or _cloud_. The former represents
  training in low to medium-end GPUs such as personal computers. The latter represents training in high-end settings
  such
  as
  the ones offered by AWS, Azure, etc.
- `architecture`: The architecture defining the DNN. It can be _mobilenet_v2_, _nasnet_mobile_, or _xception_.
- `run`: The run number out of the 30 repetitions.
- `training duration (h)`: The amount time, in hours, it took to train the DNN.
- `gpu working time (h)`: The amount of time, in hours, the GPU was doing any computation during training.
- `gpu usage`: The percentage of GPU usage with respect to training duration.
- `gpu memory working time (h)`: The amount of time, in hours, the GPU memory was doing any operation during training.
- `gpu memory usage`: The percentage of GPU memory usage with respect to training duration.
- `average memory used (MB)`: The average GPU memory usage in Megabytes.
- `std memory used (MB)`: The standard deviation of the GPU memory usage in Megabytes.
- total power (W): The total power consumed by the GPU in Watts.
- `average temperature (Celsius)`: The average GPU temperature in Celsius.
- `temperature std (Celsius)`: The standard deviation of the GPU temperature in Celsius.
- `energy (GJ)`: The total energy consumed by the GPU in GigaJoules.
- `emissions (tCO2e)`: The total Greenhouse Gas (GHG) emissions produced in tons of CO<sub>2</sub>e.
- `GFLOPs`: Number of Floating Point Operations required to perform a forward pass on the DNN.
- `accuracy`: The accuracy of the DNN in the validation set.
- `precision`: The precision of the DNN in the validation set.
- `recall`: The recall of the DNN in the validation set.
- `AUC`: The AUC of the DNN in the validation set.

### Data Splits

The dataset does not contain any data split.

## Dataset Creation

### Curation Rationale

The DL Training Energy Consumption Dataset was created to allow researchers to study the effects of the model
architecture and
training strategy on training energy efficiency. It was also created to study the trade-off between training energy
efficiency and prediction quality.

### Source Data

#### Initial Data Collection and Normalization

The data consists of the aggregated measurements taken by profiling the GPU while training of multiple DL models
in two different training strategies. The training process was repeated 30 times for each of the DL models in both
training strategies, except for the _xception_ model that was only trained with the _cloud_ strategy due to hardware
limitations on the _local_ strategy.

We derived the energy consumption from the total power consumed. The GHG emissions where derived from the energy
consumption.

To obtain the emissions produced while training, we use the data published by
the [European Environment Agency](https://www.eea.europa.eu/data-and-maps/daviz/co2-emission-intensity-12/\#tab-chart_2).
All the experiments have been executed in Spain, thus we use the last data available which indicates that the emission
intensity in Spain in the year 2021 was approximately of 232 gCO$_2$e/kWh.

The prediction quality metrics were obtained from the predictions of the model on the validation set.

#### Who are the source language producers?

[N/A]

### Annotations

The dataset does not contain any annotations.

#### Annotation process

[N/A]

#### Who are the annotators?

[N/A]

### Personal and Sensitive Information

The dataset does not contain any personal or sensitive information.

## Considerations for Using the Data

### Social Impact of Dataset

The purpose of this dataset is to help develop models that are energy efficient and make better use of the
available resources. By understanding how modeling and training decisions can affect the final training energy
efficiency
of DL projects, we can reduce their carbon footprint. Moreover, by reducing the energy requirements of DL training,
we make this task more affordable for limited budgets.

### Discussion of Biases

[More Information Needed]

### Other Known Limitations

[More Information Needed]

## Additional Information

### Dataset Curators

The DL Training Profiling Dataset was created by Santiago del Rey Juarez as part of the master thesis
"An analysis of modeling and training decisions for greener computer vision systems".

### Licensing Information

The DL Training Energy Consumption Dataset is licensed under the [CC-By Attribution 4.0 International](../LICENSE)

### Citation Information

[More Information Needed]

### Contributions

Thanks to [@santidrj](https://github.com/santidrj) for adding this dataset.
