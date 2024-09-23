# M2 Applications of Machine Learning Coursework Submission (sd2022)

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

## Description
This project is associated with the submission of the coursework for the M2 Applications of Machine Learning Module as part of the MPhil in Data Intensive Science at the University of Cambridge. The coursework assignment can be found here: [Applications of Machine Learning - Coursework Assignment](/coursework.pdf). The associated report can be found here: [Applications of Machine Learning - Coursework Report](report/m2_sd2022_report.pdf).

## Table of Contents
- [Installation and Usage](#installation-and-usage)
- [Support](#support)
- [License](#license)
- [Project Status](#project-status)
- [Authors and Acknowledgment](#authors-and-acknowledgment)

## Installation and Usage

To get started with the code associated with the coursework submission, follow these steps:

### Requirements

- Python 3.10 or higher installed on your system.
- Conda installed (for managing the Python environment).
- Docker (if using containerisation for deployment).

### External Files 

The files necessary to run the notebooks in project are found here: 
[M2 Applications of Machine Learning - Submission Files](https://drive.google.com/drive/u/3/folders/1aAcWNrChIcA_AOkxJnDHo0_36Dqs8Fm4). 

The folders in `sd2022\contents` are the following:

- FILES FOR MODEL 1: RUN\_cnn-nh(16, 32, 32, 16)-actGELU\_ddpm-b(0.0001, 0.02)-nt1000\_lr0.0002(4)
- FILES FOR MODEL 2: RUN\_cnn-nh(32, 64, 128, 64, 32)-actGELU\_ddpm-b(0.0001, 0.05)-nt1200\_lr0.001
- FILES FOR MODEL 3: SALTPEPPERRAW\_cnn-nh(32, 64, 128, 64, 32)-actGELU\_ddpm-b(0.05, 0.25)-nt150\_lr0.0002 ->  
- FILES FOR MODEL 4: SALTPEPPER\_cnn-nh(32, 64, 128, 64, 32)-actGELU\_ddpm-b(0.05, 0.25)-nt150\_lr0.0002(1)

Please simply include it in the `sd2022` repository if you want to run the notebooks successfully.

Additionally, the final models 1, 2, 3, 4 are stored in the Google drive folder `sd2022\ddpm_models`. However, this would require changing the path names in the notebooks to use them directly, and one would not be able to display any information about the training process (loss curves, FIDs at different epochs, sample images at different epochs etc.). Please simply include it in the `sd2022` repository.

Trained classifier models used to predict labels for generated models and calculate the SI scores are stored in the Google drive folder `sd2022\classifier_models`. We recommend using `cnn_classifier4.pth` (default), which has shown the best classification performance on a test set of 10000 MNIST images. Please simply include it in the `sd2022` repository.

### Steps

You can either run the code locally using a `conda` environment or with a container using Docker. The Jupyter Notebooks associated with the different parts are located in the `sd2022/src` directory:

- Model 1 : [coursework\_starter\_model1.ipynb](src/coursework_starter_model1.ipynb)
- Model 2 : [coursework\_starter\_model2.ipynb](src/coursework_starter_model2.ipynb)
- Model 3 : [coursework\_starter\_model3.ipynb](src/coursework_starter_model3.ipynb)
- Model 4 : [coursework\_starter\_model4.ipynb](src/coursework_starter_model4.ipynb)
- MNIST classifier : [mnist\_classifier.ipynb](src/mnist_classifier.ipynb)

The Jupyter Notebooks will run faster locally on a high-spec computer (recommended). 

#### Local Setup (Using Conda) [RECOMMENDED]

1. **Clone the Repository:**

    Clone the repository to your local machine with the following command:

    ```
    $ git clone https://gitlab.developers.cam.ac.uk/phy/data-intensive-science-mphil/M2_Assessment/sd2022
    ```

    or simply download it from [M2 Applications of Machine Learning Coursework (sd2022)](https://gitlab.developers.cam.ac.uk/phy/data-intensive-science-mphil/M2_Assessment/sd2022).

2. **Navigate to the Project Directory:**

    On your local machine, navigate to the project directory with the following command:

    ```
    $ cd /full/path/to/sd2022
    ```

    and replace `/full/path/to/` with the directory on your local machine where the repository lives in.

3. **Setting up the Environment:**

    Set up and activate the `conda` environment with the following command:

    ```
    $ conda env create -f environment.yml
    $ conda activate m2_sd2022_env
    ```

4. **Install ipykernel:**

    To run the notebook cells with `m2_sd2022_env`, install the ipykernel package with the following command:

    ```
    python -m ipykernel install --user --name m2_sd2022_env --display-name "Python (m2_sd2022_env)"
    ```


4. **Open and Run the Notebook:**

    Open the `sd2022` directory with an integrated development environment (IDE), e.g. VSCode or PyCharm, select the kernel associated with the `m2_sd2022_env` environment and run the Jupyter Notebooks (located in the `sd2022/src` directory).


#### Containerised Setup (Using Docker)

1. **Clone the Repository:**

    Clone the repository to your local machine with the following command:

    ```
    $ git clone https://gitlab.developers.cam.ac.uk/phy/data-intensive-science-mphil/M2_Assessment/sd2022
    ```

    or simply download it from [M2 Applications of Machine Learning Coursework (sd2022)](https://gitlab.developers.cam.ac.uk/phy/data-intensive-science-mphil/M2_Assessment/sd2022).

2. **Navigate to the Project Directory:**

    On your local machine, navigate to the project directory with the following command:

    ```
    $ cd /full/path/to/sd2022
    ```

    and replace `/full/path/to/` with the directory on your local machine where the repository lives in.

3. **Install and Run Docker:**

    You can install Docker from the official webpage under [Docker Download](https://www.docker.com/).
    Once installed, make sure to run the Docker application.

4. **Build the Docker Image:**

    You can build a Docker image with the following command:

    ```
    $ docker build -t [image] .
    ```

    and replace `[image]` with the name of the image you want to build.

4. **Run a Container from the Image:**

    Once the image is built, you can run a container based on this image:

    ```
    $ docker run -p 8888:8888 [image]
    ```

    This command starts a container from the `[image]` image and maps port `8888` of the container to port `8888` on your local machine. The Jupyter Notebook server within the container will be accessible on JupyterLab at [http://localhost:8888](http://localhost:8888). 

5. **Access and Run the Notebook:**

    After running the container, you'll see logs in the terminal containing a URL with a token. It will look similar to this:

    ```
     http://127.0.0.1:8888/lab?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
    ```
    
    Navigate to [http://localhost:8888](http://localhost:8888) and enter the token `XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`. Once you accessed JupyterLab, run the Jupyter Notebooks(located in the `sd2022/src` directory) with an `ipykernel` (Python 3).

    **Note:** Make sure that no other Jupter Notebook Servers are running. Otherwise, you might encounter 'Invalid credentials' issues when entering the token. Close any running Jupter Notebook Servers. To stop a running server, use `Ctrl + C` in the terminal where you launched JupyterLab. Also make sure port `8888` is not occupied.


## Support
For any questions, feedback, or assistance, please feel free to reach out via email at [sd2022@cam.ac.uk](sd2022@cam.ac.uk).

## License
This project is licensed under the [MIT License](https://opensource.org/license/mit/) - see the [LICENSE](LICENSE) file for details.

## Project Status
The project is in a state ready for submission. All essential features have been implemented, and the codebase is stable. Future updates may focus on minor improvements, bug fixes, or optimisations.

## Use of auto-generation tools
GitHub Co-Pilot assisted the author in producing all function docstrings present in the project repository. No specific commands have been given, instead auto-completion suggestions have occasionally been accepted. Other uses of auto-generation tools:

#### ChatGPT Prompt 1: How do I display 3 versions of digits 0-9 if they are stored in these folders: run\_name = "RUN\_cnn-nh(32, 64, 128, 64, 32)-actGELU\_ddpm-b(0.0001, 0.05)-nt1200\_lr0.001" base\_path = f"../contents/{run\_name}/predicted\_labels{digit\_number}"


- ChatGPT output: 

```python
import matplotlib.pyplot as plt
import os
from PIL import Image

# Your base settings
run_name = "RUN_cnn-nh(32, 64, 128, 64, 32)-actGELU_ddpm-b(0.0001, 0.05)-nt1200_lr0.001"

# Assuming the base path is correct and accessible from this script's directory
base_path_template = f"../contents/{run_name}/predicted_labels{{}}"

# Set up the plot
fig, axes = plt.subplots(nrows=10, ncols=3, figsize=(9, 30))  # 10 digits, 3 versions each
fig.tight_layout(pad=3.0)

for digit in range(10):
    # Construct the path for the current digit
    digit_path = base_path_template.format(digit)
    
    # Assuming the files are named in a way that sorting them alphabetically orders them correctly
    # or you have some logic to pick three specific files
    image_files = sorted(os.listdir(digit_path))[:3]  # Get the first three images for simplicity
    
    for i, image_file in enumerate(image_files):
        # Load the image
        img = Image.open(os.path.join(digit_path, image_file))
        
        # Display the image
        ax = axes[digit, i]
        ax.imshow(img, cmap='gray')
        ax.axis('off')  # Hide the axes ticks

plt.show()
```

- Modification of the output:

```python
# Display 3 images for each digit

run_name = "RUN_cnn-nh(16, 32, 32, 16)-actGELU_ddpm-b(0.0001, 0.02)-nt1000_lr0.0002(4)"
base_path = f"../contents/{run_name}/predicted_labels"

n_digits = 10  
n_images_per_digit = 3

fig, axes = plt.subplots(n_images_per_digit, n_digits, figsize=(n_digits * 2, n_images_per_digit * 2))

for digit in range(n_digits):
    digit_path = os.path.join(base_path, str(digit))
    image_files = sorted(os.listdir(digit_path))[:n_images_per_digit]
    
    for i, image_file in enumerate(image_files):
        img_path = os.path.join(digit_path, image_file)
        img = mpimg.imread(img_path)

        if i == 0:
            axes[i,digit].set_title(digit, fontsize = 20)
        
        axes[i, digit].imshow(img) 
        axes[i, digit].axis('off') 

plt.tight_layout()
rect = patches.Rectangle((0.0, 0.0), 1, 1, linewidth=4, edgecolor=sd2022_green, facecolor='none', transform=fig.transFigure, clip_on=False)
fig.patches.append(rect)
plt.show()
```

## Authors and Acknowledgment
This project is maintained by [Steven Dillmann](https://www.linkedin.com/in/stevendillmann/) at the University of Cambridge.

28th March 2024

