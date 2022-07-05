# Cuffless estimation of blood pressure from PPG signals using Transformers

## Year 4 MEng Electrical Engineering Final Year Project (FYP) 2021-2022, Imperial College London, Arijit Bhattacharyya (CID: 01496199)

Welcome to my FYP repository! For my FYP, I have developed several neural network algorithms to perform the cuffless estimation of blood pressure signals from photoplethysmography (PPG) signals. The following links summarise the main work conducted for this FYP:

- [Interim Report](https://github.com/ab10918/FinalYearProject---BP-from-PPG/blob/main/Interim%20Report/main.pdf)
- [Final Report](https://github.com/ab10918/FinalYearProject---BP-from-PPG/blob/main/Final%20Report/main.pdf)
- [Literature Survey matrix](https://github.com/ab10918/FinalYearProject---BP-from-PPG/blob/main/Final%20Report/Literature%20Survey.xlsx)
- [Final Presentation Slides](https://github.com/ab10918/FinalYearProject---BP-from-PPG/blob/main/FYP%20Final%20Presentation.pptx)
- [Code](https://colab.research.google.com/drive/1QfJtCEfesJb9H2lDTL6713bSB-2qGRPy?usp=sharing) (Google Colaboratory link)

## Initial Requirements

This section provides a description of the requirements needed to run the code in the [FYP.ipynb](https://colab.research.google.com/drive/1QfJtCEfesJb9H2lDTL6713bSB-2qGRPy?usp=sharing) Jupyter notebook. Please refer to the Table of Contents tab in Google Colab to quickly navigatee through all the code.

In order to run the first cell, the user must have a Google account and be able to connect their Google Drive storage to the Jupyter notebook. It is also recommend for users to sign up for Google Colab Pro (see [Colab Membership](https://colab.research.google.com/signup)) in order to run the neural network models efficiently.

In order to run the second code cell, the system requirements (library versions) are summarised below:

- [h5py = 2.10.0](https://docs.h5py.org/en/stable/) (HDF5 for Python, library to help store large amounts of signal data at a time)
- [heartpy = 1.2.7](https://python-heart-rate-analysis-toolkit.readthedocs.io/en/latest/) (Heartpy, Python Heart Rate Analysis Toolkit, used in signal preprocessing)
- [wfdb = 3.4.0](https://wfdb.readthedocs.io/en/latest/index.html) (Python waveform-database (WFDB) package, used for raw signal acquisition and plotting)
- [kapre = 0.3.5](https://kapre.readthedocs.io/en/latest/) (Keras Audio Preprocessors library, used for signal preprocessing)
- [tensorflow-gpu = 2.4.1](https://pypi.org/project/tensorflow-gpu/) (Python's Tensorflow library, used for creating neural network models)
- [natsort = 7.1.1](https://pypi.org/project/natsort/) (Python's natural sorting library)
- [pandas = 1.3.1](https://pandas.pydata.org/docs/) (Python's Pandas library, used for data manipulation and numerical analysis)
- [matplotlib = 3.1.3](https://matplotlib.org/stable/index.html) (Python's Matplotlib library, used for data visualisation)
- [scikit-learn = 0.24.2](https://scikit-learn.org/stable/) (scikit-learn library, used for signal processing and machine learning purposes)
- [numpy = 1.18.5](https://numpy.org/doc/stable/index.html) (Python's Numpy library, used for working with arrays)

After running this second cell, please also click the "Restart Runtime" button in the Google Colab console output, I have had to do this several times as otherwise there are subsequent errors in loading the neural network models later on in the notebook.

The third cell provides the user with information on what Graphical Processing Unit (GPU) is being used to train the neural network models.

The following section titles correspond to their matching code cell section headings in [FYP.ipynb](https://colab.research.google.com/drive/1QfJtCEfesJb9H2lDTL6713bSB-2qGRPy?usp=sharing).

## Downloading the MIMIC I records

The following steps are required to run this cell:

- A .txt Text file is required as input to the function in this cell. Two sample text files have been provided in this Github repository:
  - MIMIC_records.txt
  - MIMIC_records_subset.txt

- Please download either of these .txt files (or create your own) and upload it to your Google Drive storage. Then you will need to provide the absolute path of the .txt file location in your storage to the function (on Line 164 of the code cell)

- On Line 55, an array is provided (subsetVals) to represent the number of 10-minute recordings in each of the patient records in the MIMIC Database subset (see the Final Report). You must update this array based on the records you choose to be used in your custom .txt file

- Before running the cell, you must create an empty folder in your Google Drive storage in order to store the output of the cell (see Line 165). Once again, provide the absolute path to this folder

- Please see the comments in the Jupyter notebook code cell for further details.

## Preparing the MIMIC I dataset

The following steps are required to run this cell:

- The input to the function in this code cell is the same as the output path from the previous code cell (see Line 345)

- The output to the function is a .h5 file. Ensure to use a unique name for the output file every time that you run this code cell (see Line 346)

- Please see the comments in the Jupyter notebook code cell for further details.

## Converting from .h5 to Tensorflow format

The following steps are required to run this cell:

- The input to the function in this code cell is the same as the output path from the previous code cell (see Line 242)

- For the output to this function, first create an empty folder. Within this empty folder you must then create 3 new empty subfolders called:
 - train
 - val
 - test

- This function returns 3 values:
  - numTraining (number of samples in the training dataset)
  - numValidation (number of samples in the validation dataset)
  - numTest (number of samples in the test dataset)

- These 3 values are essential for the neural network training process (see the next section)

- Please see the comments in the Jupyter notebook code cell for further details.

## Functions for all Deep Learning architectures

The following steps are required to run this cell:

- There are five separate code cells provide for each of the particular neural network architectures:
 - AlexNet
 - ResNet
 - Spectrotemporal ResNet
 - Bi-directional Long Short Term Memory (Bi-LSTM)
 - Transformer Encoder

- Just run the code cell of the architecture that you would like to test

- Please see the comments in the Jupyter notebook code cell for further details.

## Function to training on PPG data

All you need to do is run this cell! Please see the comments in the Jupyter notebook code cell for further details.

## Training cells

I have provided five separate code cells for the training process of each of the five neural network architectures. 
The following steps are required to run any of these 5 cells:

- There are several input arguments required to run the ppg_train_mimic function:
 - architecture: String vari

