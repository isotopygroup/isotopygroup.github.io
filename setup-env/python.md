# Python and Conda

We will install and manage python using [Conda](https://docs.conda.io) which also provides a virtual environment manager and package manager.
Conda is also favored for setting up a data science environment.

## Base Environment

### Updating Base Environment

After the install is completed you can get the latest versions of conda and the base packages by updating conda with:

```bash
conda update conda
```

The previous command does not update the base environment python.
To update python for the base environment use the command:

```bash
conda update python
```

To remove unused packages and compressed download files:

```bash
conda clean --all
```

### Setup Base Environment

Rather than installing the full [Anaconda](https://www.anaconda.com) framework (~3GB) we will install [Miniconda](https://docs.conda.io/en/latest/miniconda.html) (~400MB).

To install, first download the the shell script from the Miniconda website.

Next, navigate to the directory containing the downloaded file and run the command:

```bash
bash Miniconda3-latest-Linux-x86_64.sh
```

Accepted all default options.
One of which runs the command `conda init` which modifies `.bashrc` as well as activates the base environment on shell start-up.

To disable automatically activating the base environment run the following command in a new terminal:

```bash
conda config --set auto_activate_base false
```

To activate or deactivate the base enviroment use the commands:

```bash
conda activate
conda deactivate
```

## Project Environments

### Manage Environments

To see a list of all environments:

```bash
conda info --envs
```

To see information about the active environment:

```bash
conda info
```

To activate or deactivate an environment :

```bash
conda activate ENV_NAME
conda deactivate
```

To create a new environment called `new-env` with a python interpreter:

```bash
conda create --name new-env python
```

To delete an environment:

```bash
conda env remove --name new-env
```

### Manage Packages

To see all packages in the active environment:

```bash
conda list
```

To search for a package in default channels

```bash
conda search PACKAGE_NAME
```

To search for a package in default channels and additional channels (e.g. `conda-forge` a community run channel often with more recent versions, but possibly less GPU support).

```bash
conda search PACKAGE_NAME -c conda-forge
```

To install a package in the active environment:

```bash
conda install PACKAGE_NAME
```

## Setup Basic Data Science Environment

```bash
conda create -n data-sci python
conda activate data-sci
conda install numpy
conda install pandas
conda install scikit-learn
conda install matplotlib
conda install seaborn
conda install -c conda-forge jupyterlab
```

Now change to your data science project directory and run jupyter with:

```bash
jupyter lab
```

Packages you may want to install
- Utility
  - numpy
  - pandas
  - ipython
  - jupyterlab
- Visualization
  - matplotlib
  - seaborn
  - plotly
  - bokeh
  - pydot
- Libraries
  - scikit-learn
  - scipy
  - statsmodels
  - keras
  - TensorFlow
  - PyTorch
  - caffe
- Specialized
  - xgboost
  - theano
  - spacy
  - gensim
  - nltk
- Web
  - scrapy
  - beautifulsoup