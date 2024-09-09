# Building-a-Neural-Network-Model-to-Define-DNA-Sequence-Specificity-in-V-D-J-Recombination
A sequence-based dense neural network, with DNA sequence one-hot encoded inputs to predict recombination efficiencies. The models are optimized and trained on the H4S2 region and the other trained on the H4S2 and the partial nonamer region of the 12-RSS. Uses SHAP and pairwise cooperative relationships to identify and quantify the model's first and second order interactions.

## NOTE: These python scripts are formated for use in Jupyter Notebook
### This repository was created in association with the [paper citation needed]

# Contents:
## "DatasetFiles" - FOLDER
A folder of files of the recombination SARP-seq dataset files used in the paper with sequence and SARP-seq measured recombination efficiencies (read count).

**Files:**
- "SJ-0 SARP-seq H4-S2 iSeq1.tabular"
- "SJ-0 SARP-seq H4-S2 iSeq2.tabular"
- "SJ-0 SARP-seq H4-S2 miSeq1.tabular"
- "SARP_seq_H4-7S2_cNon_wholeRSS.txt"
- "SARP_seq_H4-7S2_cNon_CF1_v2.txt"

## "SARP-seq-Dataset-Sequence-Logos" - JUPYTER NOTEBOOK
An interactive notebook that uses logomaker to generate the representative sequence logo of the SARP-seq input library seqeunce diversity.
Generates a sequence logo for:

**Outline:**
- Generates a sequence logo for:
  - SARP-seq N(H4-S2) input library
  - CF1 SARP-seq N(H4-H7)K(S2) input library
  - Pax3 SARP-seq N(H4-H7)K(S2) input library
  - LMO2 SARP-seq N(H4-H7)K(S2) input library

## "H4S2-Model-Hyperparameter-Search" - JUPYTER NOTEBOOK
An interactive notebook that iteratively trials hyperparameter values by performing stratified k-fold cross validation.

**Outline:**
- Setting Current Directory
- Importing Required Packages
- Setting Dataset Files into a Dictionary
  - Pulling data into dictionary of dataframes
  - Separating cryptic nonamer datasets for processing
- Dataset Processing
  - Adding zero scoring sequences to datasets
  - Pull H4S2, N1N3, N8N9 into new columns
- Establishing Functions for stratified k-fold cross validation
- H4S2 Model Hyperparameter Search
  - Dropout
  - Learning Rate
  - Hidden Activation Function
  - Output Activation Function
  - Hidden Layer Architecture
  - Hidden Layer Bias use


## "H4S2-Model-and-H4S2-cNon-Model-Training-and-SHAP-Analysis" - JUPYTER NOTEBOOK
An interactive notebook that trains the final H4S2 model and H4S2-cNon model, then performs multiple SHAP analsysis to identify and quantify first and second order interactions, and identify candidate long distance second order interactions. 

**Outline:**
- Setting Current Directory
- Importing Required Packages
- Setting Dataset Files into a Dictionary
  - Pulling data into dictionary of dataframes
  - Separating cryptic nonamer datasets for processing
- Dataset Processing
  - Adding zero scoring sequences to datasets
  - Pull H4S2, N1N3, N8N9 into new columns
  - Piechart of read count level for each dataset
- Establishing Functions for stratified k-fold cross validation
  - Optimized k-fold model's 20-fold cross validation
- Train the H4S2 Model
- Test the H4S2 Model with Experimental Replicates
- H4S2 Model SHAP Analysis
  - Position-wise SHAP values - First Order Interaction
  - Pair-wise SHAP value cooperative relationship vectors - Second Order Interactions
- Train the H4S2-cNon Model
  - Create H4S2-cNon DNA Sequence Encodings
  - Training H4S2_cNon
- H4-S2-cNon Model's Prediction Performance
  - Average Rank Order Across shared heptamer sequence
- Comparing H4S2 and H4S2-cNon Models 
- H4S2-cNon SHAP Analysis
  - Position-wise SHAP values - H4S2-cNon model
  - H4S2-cNon SHAP values Grouped by Nonamer
  - Nonamer-wise Normalized H4S2-cNon SHAP values
  - KS-test - long-distant second order interactions

## "Trained H4S2 and H4S2_cNon Models" - FOLDER
A folder containing both the trained NN models which where used in the accompony publication. The folder also contains an accomponying notebook which demonstrates loading and predicting with the models.

**Trained Models:**
- "H4S2_model.h5"
- "H4S2_cNon_model.h5"

**JUPYTER NOTEBOOK:**
- "Load Trained H4S2 and H4S2_cNon Models.ipynb"
  - **Outline:**
     -  Setting Current Directory
     - Importing Required Packages
     - Load Models into Notebook
     - Encoding Function
     - Prediction Function
     - H4S2 Model Prediction
     - H4S2_cNon Model Prediction


# How to get started:

Here we will use Anaconda Navigator's Jupyter Notebook application.

### **NOTE: alternatively the interactive notebooks could be easily be adapted for use in Colab. if using Colab skip to step 3-Colab.**

## 1) Access Jupyter Notebooks
A method of accessing Jupyter Notebook's online computing environment, is needed. 
Personally, I access Jupyter notebook application through the Anaconda Distribution.
- Install Anaconda Navigator
- Open Jupyter Notebook application in Anaconda Navigator user-interface

## 2) Download "DatasetFiles" and Notebooks

The recombination data Files are located in "DatasetFiles" folder, each containing the tested 12-RSS sequence and the sequence's measured read count. The notebooks will later require the file path into the folder.

- Click-into and Download each Notebook in the repository to you local machine
- Click-into and Download each file inside the "DatasetFiles" folder
- Locate the downloaded dataset files
- Copy the file path to clipboard

## 3) Open and Configure Interactive Notebook Paths in Jupyter Notebook

Launch the Jupyter Notebook application

- Open Anaconda navigator - or other Jupyter notebook access
- Launch Jupyter Notebook application
- Select "Upload" and Locate the downloaded Jupyter notebook
- Replace "C:\Users\File\Path\To\DatasetFiles\StorageFolder" with previously copied file path into the dataset files

## 3-Colab) Open and Configure Interactive Notebook Paths in Colab

- Select the Ribbon -> File -> Upload Notebook
- Locate and Select Downloaded Notebook
- Delete or Skip the "Setting Current Directory" section of the notebook
- Open the file icon on the left the on the file explore panel
- Upload the downloaded data files

## 4) Install Uninstalled Packages with Pip 

To import packages, the packages must be installed with a package manager, here pip will be used. To run bash commands in Jupyter Notebook, run a single line using the command prefix "!" 
#### **EXAMPLE: "!pip install PackageName"**

- Attempt to run the cell that contains all the package imports
- Observe error for first uninstalled package "ModuleNotFoundError: No module named 'PackageName'"
- Create a single line cell "!pip install PackageName" to install the necessary package
- Repeat running the import cell and contniue to install each lacking package

### **NOTE: incase of version dependency incompatibility, see "Package Import Version Requirments" for compatible versions to downgrade packages.**
#### **EXAMPLE: "!pip install tensorflow==2.15.0"**
- Run the notebook
  

# Package Import Version Requirments:
After package imports, a cell is included to check current package versions.

- **Python** and **core package** imports #Version: 3.11.4
    - **csv**
    - **os**
    - **importlib**
    - **itertools**
    - **math**
### "SARP-seq-Dataset-Sequence-Logos" - JUPYTER NOTEBOOK
- **pandas** #Version: 1.5.3
- **numpy** #Version: 1.24.3
- **matplotlib.pyplot** #Version: 3.8.3
- **logomaker** #Version: 0.8
### "H4S2-Model-Hyperparameter-Search" and "H4S2-Model-and-H4S2-cNon-Model-Training-and-SHAP-Analysis" - JUPYTER NOTEBOOK
- **pandas** #Version: 1.5.3
- **numpy** #Version: 1.24.3
- **tensorflow** #Version: 2.15.0
- **keras** #Version: 2.15.0
- **tensorflow_addons** #Version: 0.22.0
- **scikit-learn** #Version: 1.3.0
- **matplotlib** #Version: 3.8.3
- **scipy** #Version: 1.10.1
- **seaborn** #Version: 0.12.2
- **shap** #Version: 0.44.0
### "Load Trained H4S2 and H4S2_cNon Models.ipynb" - JUPYTER NOTEBOOK
- **pandas** #Version: 1.5.3
- **numpy** #Version: 1.24.3
- **tensorflow** #Version: 2.15.0
- **tensorflow_addons** #Version: 0.22.0
