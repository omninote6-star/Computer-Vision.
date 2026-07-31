# Lab 00: Computer Vision Environment Setup (CVE)

This guide provides the simple, required steps to create and configure your isolated Conda environment for Computer Vision projects using TensorFlow and Matplotlib, and how to configure it for use with VS Code and Jupyter Notebooks.

## Prerequisites

* Anaconda or Miniconda must be installed on your system.
* Visual Studio Code (VS Code) must be installed, along with the **Python** and **Jupyter** extensions.
* You will be executing these steps in your system's Command Prompt (CMD) or Anaconda Prompt.

## Step 1: Configure VS Code and Create Project Folder

This step guides you on setting up your project folder and linking the VS Code kernel to your Conda environment.

1. **Create Project Folder:** Navigate to your user directory and create the following folder structure: `C:\Users\YourName\ITE\CVE`. This `CVE` folder will be the main workspace for all future labs.
2. **Open Folder in VS Code:** Launch VS Code and go to **File > Open Folder**, then select the `CVE` folder you just created (`C:\Users\YourName\ITE\CVE`).
3. **Open Terminal:** In VS Code, open the integrated terminal (**Terminal > New Terminal**). This ensures you are issuing commands from the correct path (`C:\Users\YourName\ITE\CVE`).
4. **Create Notebook:** Inside the `CVE` folder, create a new folder `lab0`, and inside it create `lab00.ipynb`.

## Step 2: Create the Conda Environment

We will create a new, isolated environment named CVE (Computer Vision Environment).

**Execute the following command in your VS Code Terminal:**

```bash
conda create -n CVE python=3.10.13 -y
```

## Step 3: Activate the Environment

You must activate the environment before installing any packages to ensure they are confined to the CVE environment.

**Execute the following command:**

```bash
conda activate CVE
```

You should see your command line prompt change to indicate the environment is active (e.g., `(CVE) ...`).

## Step 4: Install Core Dependencies

We will use pip to install all necessary deep learning and computer vision libraries.

1.  Make sure you are in the folder containing your `requirements.txt` file (e.g., inside `lab0`) OR perform the install referencing the file.
2.  Assuming you placed `requirements.txt` in the `lab0` folder you created:

```bash
cd lab0
pip install -r requirements.txt
```

| Package | Purpose |
| :---- | :---- |
| tensorflow | The core deep learning framework for building the CNN. |
| matplotlib | For plotting images and visualizing training performance. |
| numpy | Essential for efficient array and matrix operations on image data. |
| opencv-python | The standard library for image loading and preprocessing (Classical CV). |
| jupyter | Installs the necessary components to run Jupyter Notebooks. |
| scikit-learn | For data splitting and metrics (Added for Lab 4+). |

## Step 5: Select Kernel in Notebook

1.  Open `lab0/lab00.ipynb`.
2.  **Select Kernel:** In the top-right corner, click on the **"Select Kernel"** button.
3.  **Choose Environment:** Select **"Conda Environments"** -> **CVE** (`Python 3.10 ('CVE')`).

## Step 6: Test the Environment

Run the following code in the first cell of your `lab00.ipynb` notebook to confirm everything is working.

```python
import tensorflow as tf
import numpy as np
import matplotlib.pyplot as plt
import cv2 # Imported as opencv-python

print("TensorFlow Version:", tf.__version__)
print("NumPy Version:", np.__version__)

# Simple test to confirm NumPy and Matplotlib are working
data = np.random.rand(10, 10)
plt.imshow(data, cmap='viridis')
plt.title("Matplotlib Test Image")
plt.show()

if 'cv2' in globals():
    print("OpenCV (cv2) imported successfully.")
else:
    print("OpenCV failed to import.")
```

## Summary of Commands (Vs Code Terminal)

```bash
# 1. Create the environment
conda create -n CVE python=3.10.13 -y

# 2. Activate the environment
conda activate CVE

# 3. Enter the lab folder
cd lab0

# 4. Install all dependencies
pip install -r requirements.txt
```
