CS766 Computer Vision
Visionary zeros Group
Danyal Maqbool, Muhammad Musa, Melody Pak
dmaqbool@wisc.edu
mmusa2@wisc.edu
npak2@wisc.edu

Drive Link: https://drive.google.com/drive/folders/1-17Qxyoz_Cl8RYgZsA8DmjCP8e306_6B?usp=sharing
Opening the provided drive link and working on colab would be easier as the paths are all set acccordingly. 
You can still run this locally but would need to modify any paths so that they point to the correct dataset/model. 
You can install the dependencies with the requirements.txt provided.

## SAM (EfficientSAM.ipynb)
The EfficientSAM notebook contains all code to reproduce our results from SAM. The only thing you would need to change are the paths for the datasets and models. 
You will also need to download the SAM model itself which we use to finetune. It is available in the drive shortcut (finetunesam).
All necessary imports are made inside the notebook. You would need to install any missing libraries or use the requirements txt to install everything. 
The Low rank tensor approximation section (LORA) has a separate install requirement that happens when you run its cells in the notebook.
To use any of the roboflow datasets, you will need to make an account (for free) and generate an API key and replace it in the roboflow subsection in the dataset
sections.
All parameters are adjustable in the 'Declarations section'.
The only other parameter that you may need to adjust is the "threhsold" value as SAM outputs probability masks so those can change depending on how much of a
probability is sufficient for your task. 
Currently the notebook has all cells run with results in them that you can view. 
Code heavily inspired from the following two links:
https://maxjoas.medium.com/finetune-segment-anything-sam-for-images-with-multiple-masks-34514ee811bb 
https://github.com/MathieuNlp/Sam_LoRA

# Training SAM for multi labeled dataset (trainSam3.ipynb):
To run trainSam3, in google coLab make sure to follow the table of content. First load the required packages and "Necessary function".
To changes between this model and EfficientSAM model are listed under the "Change that have been so far" tab.
Make sure to update the path to the folder you have saved your dataset -> go to "Path to roboflow" section.
This code accepts images in COCO json format.
In the "Real Fine tunning" Section, the hyperparameter space was explored and the following parameters will be tested for training:
    - number of epoc -> this model is set to loop between 10 and 15
    - Learning rates -> this model is set to train with 3 different learning rates of 0.1, 0.01, and 0.001
    - The threshold parameter that is built in SAM model has been set to 50. This value was set based on trial and error on the multi tag dataset.

# Detectron2:
To run Detectron2, you can go to jupyter notebook and run all. All the required dependecies and libraries are installed withing the notebook.
The code has been written so that it is modular for the most part so if there is a need to change the dataset or directory, it can be done so by changing the variables that store the directories.
The DatasetCatalogue in for Detectron2 is automatically cleared with every run so as to remove any problem with re-registering the COCO instances. Furthermore, as evident from the code too, when registering COCO instances, you need to provide both the
path to the .coco.json file containing the annotaitions of segmentation, and the path to the folder where this file. along iwht all the images, are stored. 

Code inspired from: Bhattiprolu, S. (2023). python_for_microscopists. GitHub. https://github.com/bnsreenu/python_for_microscopists/blob/master/330_Detectron2_Instance_3D_EM_Platelet.ipynb
