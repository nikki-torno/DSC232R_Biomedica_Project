Welcome to our BIOMEDICA Database group Project! The source data used in this project can be downloaded at this link: https://huggingface.co/BIOMEDICA and the project exclusively uses the data from the non-commercial license.

The most up-to-date code can be found in the Milestone_3_v3.ipynb file. This file can also be accessed in the shared SDSC resource by following /expanse/lustre/projects/uci150/ntorno/group_project. The group_project remote directory already contains downloaded raw data, which has been unpacked and written to parquet files. These parquet files are also readily available in the remote directory. Please note that the RAM requirements to run this project are not trivial, especially if you desire to run any of the raw data processing and writing code. It is recommended that you establish your SDSC Spark session with the following configuration:

Account: TG-CIS240277
Partition: shared
Time limit (min): 180
Number of cores: 20
Memory required per node (GB): 128
Singularity Image File Location: ~/esolares/spark_py_latest_jupyter_dsc232r.sif
Environment Modules to be loaded: singularitypro
Working Directory: home
Type: JupyterLab 

Once you have your Jupyter Lab remote session open, there will be Step 0 code in each notebook to set up the environment with these specifications in mind. The spark session builder is already configured for the above specifications: sc = SparkSession.builder
.config("spark.driver.memory", "10g")
.config("spark.executor.memory", "6g")
.config('spark.executor.instances', 19)
.getOrCreate()
If you choose to alter any part of the Jupyter Session variables from the 20 cores and 128GB memory, please note that you must manually adjest this code chunk accordingly.

There is also a code line included for every nonstandard library used in the jupyer notebook, but please be advised that the project includes the following nonstandard libraries: gdown, PIL, tensorflow. Please note that you as the end user should be able to skip over all the gdown code in Section 1 because the dataset has already been saved as one parquet file in the remote directory specified above. The data for the .tar file download in Milestone 2 Step 1 can be accessed from this link: https://drive.google.com/drive/folders/1hrg05v1NB84NbufLYt-na3fS_6IfnTiU?usp=drive_link The data for the .parquet files in the beginning of Milestone 2 Step 3 and Milestone 3 Step 1 is available in this link: https://drive.google.com/drive/folders/1WXtGQidYS3O2gEDgiSE-jCAleskDwnjt?usp=drive_link 
All this data was originally accessed from the huggingface url provided in the top of this README as well as in the jupyter notebook.

Regarding Milestone 2, the preprocessing in Step 1 largely includes taking in the .tar files, assessing file types contained, and handling image data formatting by extracting the image data from the path and reformatting it to a standard 224x224 size that works well with CNN models (for future work). The exploration in Milestone 2 Step 2 and Step 3 includes steps such as checking the schemas, numebr of unique items, and printing examples for each dataframe.

Regarding Milestone 3, the preprocessing code in Step 2 includes opening the parquet file, checking that all data loaded properly, and then building a very basic toy CNN model in order to ensure that tensorflow downloaded properly before proceeding. The true first CNN is contained in Step 3; the data preparation includes running a few count and show statements to refresh your memory of the dataset, and preparing the dataset for modeling by using PIL to extract image data, encoding the labels, and normalizing the pixel values for optimal training. Then, a CNN is trained and evaluated on the dataset. Following the CNN evaluation, there is discussion of the model performance, next steps to improve the model, and conclusions for this stage.
