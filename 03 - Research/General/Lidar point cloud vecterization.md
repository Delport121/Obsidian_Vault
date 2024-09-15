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
Random raw test script to run in terminal for open3D:
```bash
# Python API
python -c "import open3d as o3d; mesh = o3d.geometry.TriangleMesh.create_sphere(); mesh.compute_vertex_normals(); o3d.visualization.draw(mesh, raw_mode=True)"

# Open3D CLI
open3d example visualization/draw
```
### Troubleshooting
The setup for this is rather tedious and could cause a lot of issues. You might have to install additonal modules for laspy as well as install and opengl packages. Also it does not seem to work so well with the virtual environment so maybe do it not in there

- Attempting to install in virtual environment(Did not work)
```bash
conda install anaconda::pyopengl
```
- Laspy additional stuff
```bash
C:\Users\User>laspy
laspy cli needs extra dependencies, install using
`pip install laspy[cli]`
`pip 
install laspy[cli,lazrs]`
```
- Environment path issue
```bash
WARNING: The script laspy.exe is installed in 'C:\Users\User\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.11_qbz5n2kfra8p0\LocalCache\local-packages\Python311\Scripts' which is not on PATH. Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
```
Do this:
1. **Open Environment Variables:**
    
    - Press `Win + S` to open the search bar, type **Environment Variables**, and select **Edit the system environment variables**.
    - In the System Properties window, click **Environment Variables** at the bottom.
2. **Edit the Path Variable:**
    
    - Under **User variables**, find and select the `Path` variable, then click **Edit**.
    - In the **Edit Environment Variable** window, click **New** and paste the path from the warning:
3. **Verify the Changes:**
    
    - Close and reopen any terminal or command prompt you were using.
    - Type `python` or `laspy` to check if it works without the warning.

This will ensure that Python can find the `laspy.exe` script without showing the warning.