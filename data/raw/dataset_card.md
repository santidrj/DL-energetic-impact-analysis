# Dataset Card for DL Training Profiling Dataset

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

The DL Training Profiling Dataset is an English-language dataset containing just over 1M
measurements of energy-related metrics of the Deep Learning model's training. The data correspond to training three
different models using two different training strategies (i.e., Local and Cloud). We have trained each model 30 times
for each training strategy.

### Supported Tasks and Leaderboards

The dataset can be used to study the effect of training different Deep Learning models on energy consumption.

### Languages

The BCP-47 code for English as generally spoken in the United States is en-US and the BCP-47 code for English as
generally spoken in the United Kingdom is en-GB.

## Dataset Structure

### Data Instances

Each data instance contains the training strategy used, the architecture of the base model, the run number,
the timestamp of the measurement, and the profiled data.

```json
{"train_strategy":"cloud",
  "architecture":"mobilenet_v2",
  "run":0,
  "timestamp": 1670234145538,
  "gpu_name": "NVIDIA GeForce RTX 3090",
  "gpu_usage": 0.0,
  "gpu_memory_usage":0.0,
  "gpu_total_memory":24268,
  "gpu_memory_used":23573,
  "gpu_power_draw": 118.0,
  "gpu_max_power": 350.0,
  "gpu_temperature": 55,
  "cpu_usage":3.5869998932,
  "memory_usage":12234.05078125}
```

### Data Fields

- `train_strategy`: The type of machine used to train the DNN. It can be _local_ or _cloud_. The former represents
  training in low to medium-end GPUs such as personal computers. The latter represents training in high-end settings
  such
  as
  the ones offered by AWS, Azure, etc.
- `architecture`: The architecture defining the DNN. It can be _mobilenet_v2_, _nasnet_mobile_, or _xception_.
- `run`: The run number out of the 30 repetitions.
- `timestamp`: The timestamp of the measured metrics.
- `gpu_name`: The GPU model name.
- `gpu_usage`: The percentage of GPU used according to
  the [nvidia-smi](https://developer.download.nvidia.com/compute/DCGM/docs/nvidia-smi-367.38.pdf) definition.
- `gpu_memory_usage`: The percentage of GPU memory according to
  the [nvidia-smi](https://developer.download.nvidia.com/compute/DCGM/docs/nvidia-smi-367.38.pdf) definition.
- `gpu_total_memory`: The total memory of the GPU in MegaBytes.
- `gpu_memory_used`: The GPU memory used in MegaBytes.
- `gpu_power_draw`: The power consumed by the GPU in Watts.
- `gpu_max_power`: The maximum value in watts that power limit can be set to. In other words, the Graphics Card Power (
  GCP).
- `gpu_temperature`: The GPU temperature in Celsius.
- `cpu_usage`: The percentage of CPU used according to
  the [psutil](https://psutil.readthedocs.io/en/latest/#psutil.cpu_percent)
  definition.
- `memory_usage`: The RAM used in MegaBytes.

### Data Splits

The dataset does not contain any data split.

## Dataset Creation

### Curation Rationale

The DL Training Profiling Dataset was created to allow researchers to study the effects of the model architecture and
training strategy on training energy efficiency.

### Source Data

#### Initial Data Collection and Normalization

The data consists of the measurements taken by profiling the GPU, CPU, and RAM during the training of multiple DL models
in two different training strategies. The training process was repeated 30 times for each of the DL models in both
training strategies, except for the _xception_ model that was only trained with the _cloud_ strategy due to hardware
limitations
on the _local_ strategy.

The data corresponds to the raw measurements. The only processing performed has been the integration of the GPU
measurements with the CPU and RAM measurements using the closest timestamp available.

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
efficiency of DL projects, we can reduce their carbon footprint. Moreover, by reducing the energy requirements of DL
training,
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

The DL Training Profiling Dataset is licensed under the [CC-By Attribution 4.0 International](../LICENSE)

### Citation Information

[More Information Needed]

### Contributions

Thanks to [@santidrj](https://github.com/santidrj) for adding this dataset.
