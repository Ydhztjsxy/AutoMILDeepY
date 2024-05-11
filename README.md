# AutoMILDeepY

This repository contains the code and the data to train **AutoTFCNNY and AttenBILSTMCNY** model.

​    Contact: 1974887272@qq.com; solfix123@163.com

## Project Organization
      ├── AutoMILDeepY                     
         │
         │
         │     
         ├── README.md                   <- The README for users using AutoTFCNNY and AttenBILSTMCNY.
         │
         │
         ├── Notebooks                   <- AutoTFCNNY and AttenBILSTMCNY code for jupyter notebook. See README for their usages.
         │   ├── AutoTFCNNY.ipynb                      <- Training and predictions AutoTFCNNY models.
         │   ├── AutoTFCNNY-model.ipynb                <- Training  AutoTFCNNY models.
         │   ├── AutoTFCNNY-Test.ipynb                 <- Test AutoTFCNNY models.
         │   ├── AttenBILSTMCNY.ipynb                  <- Training and predictions AttenBILSTMCNY models.
         │   ├── AttenBILSTMCNY-model.ipynb            <- Training AttenBILSTMCNY models.
         │   ├── AttenBILSTMCNY-Test.ipynb             <- Test AttenBILSTMCNY models.
         │   ├── Raw_data_processing.ipynb             <- Processing raw data 
         │
         ├── Data                       <- Data for training and testing.See README for their usages.
         │   ├── RA
         │   ├── MS                   
         │   ├── TID                     
         │   ├── IAA                   
         │   ├── Health   
         │   ├── PCA15.txt  
         │   └── Example_raw_file.tsv        
         │
         ├── New Data                       <- New data set.See README for their usages.
         │   ├── MS
         │   ├── T1D                   
         │   ├── Health                     
         |
         ├── Model
         │   ├── AutoTFCNNY                <- Model for storing the optimal AutoTFCNNY  
         │   ├── AttenBILSTMCNY                <- Model for storing the optimal AttenBILSTMCNY  
         |
         ├── Model Test Files
         │   ├── AutoTFCNNY                <- Test model files for storing optimal AutoTFCNNY models
         │   ├── AttenBILSTMCNY                <- Test model files for storing optimal AttenBILSTMCNY models
         |
         ├── python_codes             <- Code for EarlyStopping    
         ├── LICENSE                  <- copyright statement  
       
             

## Usage

### Python and essential packages

```
python         3.10.9
numpy          1.23.5
pandas         1.5.3
torch      2.0.1+cu117
```

### Input file format

The input files are tsv files in the following format:

```
TCR	Abundance
CATSDNSGGQPQHF	0.21069978688318255
CASSETGTYGYTF	0.034178689598235334
CASSYSSFSGELFF	0.01868772093003411
CASRTGGYGYTF	0.009927318418711613
CASSVLNTGELFF	0.009917718562069473
CASSLSVGPYEQYF	0.007108160518136263
CASSQGERGGNEQYF	0.006789231947469584
CASSAIRGVNTEAFF	0.006762565679019193
......
```

The sequences in the `TCR` column are the top 100 most abundant TCRs.

You can use the following command to extract TCR and its frequency information from raw files:

```
 jupyter notebook Raw_data_processing.ipynb 
 -----isource_dir = "../data/ Example_raw_file.tsv"  #Original file path
 -----output =  "../The path to the file you want to save/"  #Save the path to the processed file
```

### Predicting the Autoimmune Disease Index using pre-trained models

Prediction of all TCR files in a directory

```
 jupyter notebook AutoTFCNNY.ipynb 
 
 -----aa_file = "../Data/PCA15.txt"  #Amino acid characterization file path
 -----disease_list = ["RA", "T1D", "MS", "IAA","GBS","JIA","Narcolepsy"]  #Documentation of processed autoimmune diseases
 -----data_dir = f'../Data/{disease_name}' #Disease File Path
 ----- model_path = f'../Model/AutoTFCNNY/{disease_name}checkpoint{fold}.pt' #Save path of the model file
 
```
```
 jupyter notebook AttenBILSTMCNY.ipynb 
 
 -----aa_file = "../Data/PCA15.txt"  #Amino acid characterization file path
 -----disease_list = ["RA", "T1D", "MS", "IAA","GBS","JIA","Narcolepsy"]  #Documentation of processed autoimmune diseases
 -----data_dir = f'../Data/{disease_name}' #Disease File Path
 ----- model_path = f'../Model/AttenBILSTMCNY/{disease_name}checkpoint{fold}.pt' #Save path of the model file
 
```
### Result

The metrics, accuracy, sensitivity, specificity, and area under the receiver operating characteristic (ROC) curve (AUC), are calculated and printed as:
``` 
 ----- T1D-----
Mean Accuracy (T1D): 0.9757
Mean Sensitivity (T1D): 0.9594
Mean Specificity (T1D): 0.9907
Mean AUC (T1D): 0.9970

```


