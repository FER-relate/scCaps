## An interpretable deep-learning architecture of capsule networks for identifying cellular-type gene expression programs from single-cell RNA-seq data

This repository contains the official Keras implementation of:

**An interpretable deep-learning architecture of capsule networks for identifying cellular-type gene expression programs from single-cell RNA-seq data**



**Requirements**
- Python 3.6
- conda 4.4.10
- keras 2.2.4
- tensorflow 1.11.0


**1. Model training**

To unzip the PBMC_data.rar into dictionary 'data' then run:

- *About this article*
```
- default:
python Model_Training.py

Augments:
'--inputdata', type=str, default='data/PBMC_data.npy', help='address for input data')
'--inputcelltype', type=str, default='data/PBMC_celltype.npy', help='address for celltype label')
'--num_classes', type=int, default=8, help='number of cell type')
'--randoms', type=int, default=30, help='random number to split dataset')

- with augments
python Model_Training.py --randoms 20

```

- *Future exploration*
```
- default:
python FE_Model_Training.py

Augments:
'--inputdata', type=str, default='data/PBMC_data.npy', help='address for input data'
'--inputcelltype', type=str, default='data/PBMC_celltype.npy', help='address for celltype label'
'--num_classes', type=int, default=8, help='number of cell type'
'--randoms', type=int, default=30, help='random number to split dataset into training and testing set'
'--dim_capsule', type=int, default=16, help='dimension of the capsule'
'--num_capsule', type=int, default=16, help='number of the primary capsule'
'--batch_size', type=int, default=400, help='training parameters batch_size'
'--epochs', type=int, default=10, help='training parameters epochs'

- with augments
python FE_Model_Training --randoms 20 --dim_capsule 32
```

**2. Model analysis**

- *Demo About this article*

The following documents (Jupyter Notebook) contain the codes for reproducing Figure in the main text.
```
demo_reproducing_figures.ipynb
```
In case you don't comfortable with Jupyter Notebook, you could copy the following file from the dictionary 'old_files' into current dictionary then run:
```
python Fig1CD_Fig2DE_Fig3.py
python Fig2BC.py
python Fig4.py
python Fig5D.py
```

- *Future exploration*
```
- 1. heatmap for coupling coefficients, relationship between primary capsule and type capsule
python FE_Model_analysis_1.py

Augments:
'--inputdata', type=str, default='data/PBMC_data.npy', help='address for input data'
'--inputcelltype', type=str, default='data/PBMC_celltype.npy', help='address for celltype label'
'--num_classes', type=int, default=8, help='number of cell type'
'--randoms', type=int, default=30, help='random number to split dataset'
'--dim_capsule', type=int, default=16, help='dimension of the capsule'
'--num_capsule', type=int, default=16, help='number of the primary capsule'
'--weights', type=str, default='Modelweight.weights', help='trained weights'

- 2. select genes along one principle component for a specific primary capsule
python FE_Model_analysis_2.py

Augments:
'--inputdata', type=str, default='data/PBMC_data.npy', help='address for input data'
'--inputcelltype', type=str, default='data/PBMC_celltype.npy', help='address for celltype label'
'--num_classes', type=int, default=8, help='number of cell type'
'--randoms', type=int, default=30, help='random number to split dataset'
'--dim_capsule', type=int, default=16, help='dimension of the capsule'
'--num_capsule', type=int, default=16, help='number of the primary capsule'
'--weights', type=str, default='Modelweight.weights', help='trained weights'
'--PC', type=int, default=1, help='indicate which principle component will be analyzed '
'--Primary_capsule', type=int, default=4, help='indicate which primary capsule will be analyzed'
'--Cell_type', type=int, default=-1, help='indicate which cell type will be analyzed'
```

**3. Comparison Model**

- SVM,RF,LDA,KNN
```
cd comparison_model
python Machine_Learning.py
```

- Neural Networks
```
cd comparison_model
python Neural_Networks.py
```

**capsule networks implementation**

the capsule parts refer to https://github.com/bojone/Capsule and https://kexue.fm/archives/5112