# TensorFlow vs TensorFlow Lite: a performance analysis at the CI/CD level

Authors: Sayonara Santos and Rodrigo Parente

Description: This repository is part of a study on the impact of Machine Learning packages on product update pipelines.

In this study, we designed one model with the TensorFlow package and the other with TensorFlow Lite, which perform the same classification. Then we develop applications based on the models. Finally, we compared the performance of the models and verified the resource and time consumption in the execution of the CI/CD pipelines of the applications.

Folder organization:

```sh
.
├── ansible-playbook: Docker configuration and monitoring stack playbook;
├── cicd: Jenkins server and pipelines configuration files;
├── tests: test results.
```

The code of the developed application with TensorFlow is available in https://github.com/rodrigoparente/forest-fire-classification.