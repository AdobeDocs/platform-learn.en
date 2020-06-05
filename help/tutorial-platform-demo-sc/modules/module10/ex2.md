---
title: Data Science Workspace - Churn Prediction Model - Churn Prediction: Data Preparation
description: Data Science Workspace - Churn Prediction Model - Churn Prediction: Data Preparation
kt: 5342
audience: Data Engineer, Data Architect, Data Scientist
doc-type: tutorial
activity: 
---

# 10.2 Churn Prediction: Data Preparation

## Open Adobe Experience Platform and Jupyter Notebooks

To start preparing data for modeling, we must first read the data into Data Science Workspace. To do that, let's go to Adobe Experience Platform. you can login in Adobe Experience Platform by going here: [https://platform.adobe.com](https://platform.adobe.com)

After logging in with your Adobe ID, you'll be on the homepage of Adobe Experience Platform.

![DSW10](./images/aephome.png)

From the menu on the left side, select **Models**.

![DSW10](./images/aepmenumodels.png)

In **Models**, click on **Notebooks**.

![DSW10](./images/aepmenumodelsnb.png)

Jupyter Notebooks will then start loading, which might take 2-3 minutes.

![DSW10](./images/aepjuploading.png)

Finally, you'll be able to work with Jupyter Notebooks.

![DSW10](./images/aepjuploaded.png)

Jupyter Notebooks is an open-source standard data science tool where one can write code in languages like Python, Pyspark, Spark and R.

Let's open a blank Python 3 notebook by clicking this button:

![DSW10](./images/aepjuppy3.png)

Once the Python 3 notebook is opened, you should see this:

![DSW10](./images/aepjuppy3o.png)

## Reading a dataset in Python

An Adobe Experience Platform dataset can be easily read in Python from a Jupyter Notebook in Data Science Workspace.
First, click on the datasets icon in Jupyter Notebooks.

![DSW10](./images/aepjuppynavds.png)

Double-click on **Datasets**.

![DSW10](./images/aepjuppynavdatasets.png)

You'll then see a list of datasets.
In the list of datasets, search for the dataset named **EMEA DSW - Churn Input Data**.

![DSW10](./images/aepjuppynavdsci.png)

Next, double-click on the dataset name **EMEA DSW - Churn Input Data**. Jupyter Notebooks will now automatically generate the code needed to read this data from Adobe Experience Platform into this Python notebook.

![DSW10](./images/aepjuppynavdscicode.png)

Note: The limit in the code snippet is 100. Only 100 values will be read into the data when you execute this code. You can increase the number of records to 200000. The code now should look like

```python
from platform_sdk.dataset_reader import DatasetReader
from datetime import date
dataset_reader = DatasetReader(PLATFORM_SDK_CLIENT_CONTEXT, dataset_id="5dd2ee272a371e18a8fa7ebd")
df0 = dataset_reader.limit(200000).read()
df0.head()
```

![DSW10](./images/aepjuppynavdscicode200000.png)

Execute the code by clicking the play button at the top of the Jupyter notebook. Executing this code will take several minutes.
While the code is running, you should wait until it's finished.
You can see that an action is ongoing by verifying the Python status at the top right of your notebook.

This indicated that a cell is running:

![DSW10](./images/aepjuppyrunning.png)

When the action is finished, you'll see this:

![DSW10](./images/aepjuppyfinished.png)

![DSW10](./images/aepjuppynavdscicodeexec.png)

The result of executing the cell and loading the data from that dataset is that you now have a data-frame (df0) available that contains data.

![DSW10](./images/aepjuppydf.png)

Before going further with data exploration, we need to import certain libraries.

In your Jupyter notebook, click the **+** - button to create a new, empty cell.

![DSW10](./images/aepjuppynavdscicodeplus.png)

You'll then have a new, empty cell.

![DSW10](./images/aepjuppynewcell.png)

Copy the below code snippet and paste it in your new, empty cell.

```python
import warnings
warnings.filterwarnings('ignore')
from subprocess import check_output
import logging
logger = logging.getLogger()
logger.setLevel(logging.CRITICAL)
import seaborn as sns
from numpy import median
import matplotlib.pyplot as plt
%matplotlib inline
```

![DSW10](./images/aepjuppynewcellcode.png)

Execute the code by clicking the play button at the top of the Jupyter notebook.

![DSW10](./images/aepjuppynavdscicodeexecp.png)

After executing the cell, you'll see a new empty cell being created.

![DSW10](./images/aepjuppynavdscicodeexecpn.png)

Next, we want to have a look at the summary stats for all the numerical variables. This is done using the **describe()** function.

Copy the below code snippet and paste it in the new, empty cell.

```python
df0.describe()
```

![DSW10](./images/aepjuppynavdesc.png)

Execute the code by clicking the play button at the top of the Jupyter notebook.

![DSW10](./images/aepjuppynavdscicodeexecp.png)

The result will look like this:

![DSW10](./images/aepjuppydescresult.png)

## Loading notebooks

For the next exercises, we'll use Jupyter notebooks that have been prepared for you already.
Download the zip-file located [here](./resources/dsw-mod10.zip) and unzip its content to the desktop of your computer.

![DSW](./images/dswfiles.png)

Open the folder **dsw**. In this folder, you'll find 3 notebooks.

![DSW](./images/dswdtl.png)

You need to select these 3 notebooks and drag them into Jupyter Notebooks.

![DSW](./images/dswdtldrag.png)

Once all 3 notebooks appear in Jupyter Notebooks, you can continue with the next step.

![DSW](./images/dswdtlok.png)

Open the notebook **Mod10 - Data Exploration.ipynb**.

![DSW](./images/dswdexnb.png)

Execute all cells one by one. The code outlines steps to explore data, build visualizations and gain insights about your data.

Next Step: [10.3 Feature Engineering and Model Building](./ex3.md)

[Go Back to Module 10](./data-science-workspace-churn-prediction-model.md)

[Go Back to All Modules](../../overview.md)
