Welcome to our BIOMEDICA Database group Project!
The source data used in this project can be downloaded at this link: https://huggingface.co/BIOMEDICA and the project exclusively uses the data from the non-commercial license.

The most up-to-date code can be found in the milestone_2_v2.ipynb file. This file can also be accessed in the shared SDSC resource by following /expanse/lustre/projects/uci150/ntorno/group_project. The group_project remote directory already contains downloaded raw data, which has been unpacked and written to parquet files. These parquet files are also readily available in the remote directory.

Please note that the RAM requirements to run milestone_2_v2.ipynb are not trivial, especially if you desire to run any of the raw data processing and writing code. It is recommended that you establish your SDSC Spark session with the following configuration:

Account: TG-CIS240277
Partition: shared
Time limit (min): 180
Number of cores: 20
Memory required per node (GB): 128
Singularity Image File Location: ~/esolares/spark_py_latest_jupyter_dsc232r.sif
Environment Modules to be loaded: singularitypro
Working Directory: home
Type: JupyterLab Once you have your Jupyter Lab remote session open, there will be Step 0 code to set up the environment with these specifications in mind. The spark session builder is already configured for the above specifications: sc = SparkSession.builder
.config("spark.driver.memory", "10g")
.config("spark.executor.memory", "6g")
.config('spark.executor.instances', 19)
.getOrCreate()
If you choose to alter any part of the Jupyter Session variables from the 20 cores and 128GB memory, please note that you must manually adjest this code chunk accordingly.

There is also a code line included in the jupyer notebook, but, if you choose to run any of the gdown code, you may need to download gdown using %pip install gdown. The data for the .tar file download in Step 1 can be accessed from this link: https://drive.google.com/drive/folders/1hrg05v1NB84NbufLYt-na3fS_6IfnTiU?usp=drive_link The data for the .parquet files in the beginning of Step 3 is available in this link: https://drive.google.com/drive/folders/1WXtGQidYS3O2gEDgiSE-jCAleskDwnjt?usp=drive_link All this data was originally accessed from the huggingface url provided in the top of this README as well as in the jupyter notebook.

The preprocessing in Step 1 largely includes taking in the .tar files, assessing file types contained, and handling image data formatting by extracting the image data from the path and reformatting it to a standard 224x224 size that works well with CNN models (for future work). The exploration in Step 2 and Step 3 includes steps such as checking the schemas, numebr of unique items, and printing examples for each dataframe.
