# Machine learning pipeline
The aim of the project is classify agressive tweets using three mlops tools.

# DVC
[DVC](https://dvc.org/doc/start) is a data version control tool. To install DVC, run
```bash
pip install dvc
```

# Hydra
With [Hydra](https://hydra.cc/), you can compose your configuration dynamically. To install Hydra, simply run
```bash
pip install hydra-core --upgrade
```
# MLflow
[MLflow](https://mlflow.org/) is a platform to manage the ML lifecycle, including experimentation, reproducibility, and deployment. Install MLflow with 
```bash
pip install mlflow
```

# Structure's explanation
* **src**: file for source code
* **mlruns**: file for mlflow runs
* **configs**: to keep config files
* **outputs**: results from the runs of Hydra. Each time you run your function nested inside Hydra's decoration, the output will be saved here. If you want to change the directory in mlflow folder, use
```python
import mlflow
import hydra
from hydra import utils

mlflow.set_tracking_uri('file://' + utils.get_original_cwd() + '/mlruns')
```
* `src/preprocessing.py`: file for preprocessing
* `src/train_pipeline.py`: training's pipeline
* `src/train.py`: file for training and saving model
* `src/predict.py`: file for prediction and loading model

# How to pull the data with DVC

Pull the data from Google Drive
```bash
dvc pull 
```

# How to run this file
To run the configs and see how these experiments are displayed on MLflow's server, clone this repo and run
```
python src/train.py
```
Once the run is completed, you can access to MLflow's server with
```
mlflow ui
```
Access http://localhost:5000/ from the same directory that you run the file, you should be able to see your experiment like this
![image](https://github.com/khuyentran1401/Machine-learning-pipeline/blob/master/Screenshot%20from%202020-05-03%2016-41-21.png)
