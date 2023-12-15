<h2 align="center"> FedBEV Dataset </h2>

<p align="center"> Privacy-Aware Energy Consumption Modeling of Connected Battery Electric Vehicles using Federated Learning </p>

<p align="center">
  <a href="#Data-Source">Data Source</a> | <a href="#Vehicle-Model-Output">Vehicle Model Output</a> | <a href="#Processed-Dataset">Processed Dataset</a> | <a href="http://dx.doi.org/10.1109/TTE.2023.3343106">Paper</a>
</p>

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

*S. Yan, H. Fang, J. Li, T. Ward, N. O’Connor and M. Liu, "Privacy-Aware Energy Consumption Modeling of Connected Battery Electric Vehicles using Federated Learning," in IEEE Transactions on Transportation Electrification, doi: 10.1109/TTE.2023.3343106.*

- <a href="http://dx.doi.org/10.1109/TTE.2023.3343106"> arXiv </a>

If you feel our research and data useful, welcome to cite:

```
@article{Yan2023,
  title = {Privacy-Aware Energy Consumption Modeling of Connected Battery Electric Vehicles using Federated Learning},
  ISSN = {2372-2088},
  url = {http://dx.doi.org/10.1109/TTE.2023.3343106},
  DOI = {10.1109/tte.2023.3343106},
  journal = {IEEE Transactions on Transportation Electrification},
  publisher = {Institute of Electrical and Electronics Engineers (IEEE)},
  author = {Yan,  Sen and Fang,  Hongyuan and Li,  Ji and Ward,  Tomas and O’Connor,  Noel and Liu,  Mingming},
  year = {2023},
  pages = {1–1}
}
```

# Data Source

The dataset used in our work is sourced from <a href="https://github.com/gsoh/VED"> VED dataset </a>, a real-world dataset collected in Michigan, USA. We filtered 10 trips from the VED dataset with a duration longer than 1,800 seconds and stored them in <a href="./data source"> data source </a> folder.

# Vehicle Model Output

We extracted their GPS coordinates and the altitude data as the input for our vehicle model, with the speed data set as the desired velocity of our vehicle model. The output, consisting of multiple trip attributes such as temperature, actual speed and trip distance, is then used as our training data in <a href="./vehicle model output"> vehicle model output </a> folder. In other words, our dataset is a collection of 10 tables of trip information for all 10 vehicles. Each table includes 1,800 rows and 12 columns, representing different attributes respectively.

We have explored the data for 10 vehicles and have discovered a correlation between their average speed and the total amount of energy consumed during a 60-second interval. For example, the relationship between average speed and energy consumption for Vehicle 1 is shown in the pictures below. It is evident that there is a slight delay in the change in average speed relative to energy usage. Following our analysis, we have determined that this delay is approximately 23 seconds.

![speed_energy](./images/speed_energy.png)
![speed_energy](./images/boxplot.png)

# Processed Dataset

## Pre-processing

We divide the data in each 60-second interval, so with a full length of 1,800 seconds, each trip record data is divided into 1741 intervals. Subsequently, standardisation of the data is implemented to shift the distribution such that the mean is zero and the standard deviation is one.

## Feature Selection

We adopted trip attributes, including speed, distance, acceleration and altitude, as trip features, and employed Principal Component Analysis and Random Forest Regression to select features generated by mathematical transformations (e.g., square, logarithm, and exponent). Based on the results, we selected acceleration, speed, the square root of speed, the cube of speed, and the square root of the distance moved in each second as the features for model training.

The processed dataset are stored in <a href="./processed dataset"> processed dataset </a> folder.

---



