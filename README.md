# Fighting Crime with Deep Learning 

*Authors: Sean Fitzgerald and Muhammad Ayub

We use Tensorflow for programming the networks. Take a look at some [tutorials] we found(https://github.com/easy-tensorflow/easy-tensorflow).


## Requirements to Run Code

Please have Python 3 installed. 
For running Sean's code the libraries needed are in cs230.yml.
 
For running Ali's code the libraries are in requirements.txt. Ali used Windows 7 OS. 
Also, Python 3.5 was used with a conda virtual environment. 
With conda installed make a new environment and then do : 

```
activate py35
pip install -r requirements.txt   
```

When you're done working on the project, deactivate the virtual environment with `deactivate`.

## Task

Sean's CNN predicts crime volume. I.e. - given a 64x64xnum_channels image, predict the number of crimes that occur. 

Ali's CNN classifies crime type. I.e. - given a 64x64xnum_channels image, predict the most likely class. 

## Download the Datasets

Please refer to Sean's section to download the dataset. 

Please refer to Ali's section to download the dataset. Specifically the CNN data is hosted and available at: 
 https://drive.google.com/drive/folders/1LOyrqORS4Zszm4n62siat888IIgpx4rx?usp=sharing. 
You will find a text file detailing how the data is structured. 

```
Final Folder Public Datasets/
    inputs_data/
        input_0_.npy
		input_1_.npy
        ...
    outputs_data/
        output_0_.npy
		output_1_.npy
        ...
	CNN Dataset explained.txt
```

Each .npy file is a minibatch. You are free to concatenate minibatches to get the whole dataset or a subset. 
For example input_0_.npy will have 200 images of 64x64xnum_channels . The output_0_.npy file will have 200 64x64 images of the crime locations. 


```
please see the SampleData to view what the images look like. Most of the images are layers/channels in a single input datapoint. 
```


## Quickstart (Volume of Crime Model)

Please take a look at Sean's sub folder and go to Prediction Notebooks folder as well as Data Configure Notebooks folder. 

## Quickstart (Classification Model)


1. Download the dataset and get a feel for the dataset. Layers information can be found at the datasources website. 

2.  


```bash
python build_dataset.py --data_dir data/SIGNS\ dataset/ --output_dir data/64x64_SIGNS
```

2. __Your first experiment__ We created a `base_model` directory for you under the `experiments` directory. It countains a file `params.json` which sets the parameters for the experiment. It looks like
```json
{
    "learning_rate": 1e-3,
    "batch_size": 32,
    "num_epochs": 10,
    ...
}
```
For every new experiment, you will need to create a new directory under `experiments` with a similar `params.json` file.

3. __Train__ your experiment. Simply run
```
python train.py --data_dir data/64x64_SIGNS --model_dir experiments/base_model
```
It will instantiate a model and train it on the training set following the parameters specified in `params.json`. It will also evaluate some metrics on the development set.

4. __Your first hyperparameters search__ We created a new directory `learning_rate` in `experiments` for you. Now, run
```
python search_hyperparams.py --data_dir data/64x64_SIGNS --parent_dir experiments/learning_rate
```
It will train and evaluate a model with different values of learning rate defined in `search_hyperparams.py` and create a new directory for each experiment under `experiments/learning_rate/`.

5. __Display the results__ of the hyperparameters search in a nice format
```
python synthesize_results.py --parent_dir experiments/learning_rate
```

6. __Evaluation on the test set__ Once you've run many experiments and selected your best model and hyperparameters based on the performance on the development set, you can finally evaluate the performance of your model on the test set. Run
```
python evaluate.py --data_dir data/64x64_SIGNS --model_dir experiments/base_model
```


## Raw Data/ Resources

Please contact babaali9966@gmail.com for help


The raw data we used was from the data.gov website. 
The Crime data is located at: https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-present/ijzp-q8t2
We joined in a bunch of other data like socioeconomic-indicators-in-chicago-2008-2012-36e55: https://catalog.data.gov/dataset/census-data-selected-socioeconomic-indicators-in-chicago-2008-2012-36e55
