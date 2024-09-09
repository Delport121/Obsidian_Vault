# 1 3D Python setup
The following commands can be used to set up and environment in the anaconda prompt terminal
```bash
conda env list
conda create -n <Environmetn-name> python=3.10
conda activate VECTORIZATION
```
Install the following modules in the environment
```bash
pip install numpy pandas matplotlib
pip install open3D
pip install laspy[lazrs,laszip]
pip install rasterio geopandas shapely alphashape
pip install jupyterlab
```
Then we can start coding
```bash 
jupyter lab
```

