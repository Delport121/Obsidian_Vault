Toggle full screen mode `F11`
Collapse all `ctrl+k ctrl++)`

# Starting a Virtual environment in Python
```python
python3 -m venv <venv>
source <venv>/bin/activate
deactivate
```
# Common Vscode issues
- System paths and not finding the modules
```bash
The `utils` module should be in the same directory as your `stanley_controller.py` script or in a directory that's included in your PYTHONPATH.

If the `utils` module is in a directory called `PythonRobotics`, you can add it to your PYTHONPATH like this:
```
Apparently this line can help
```bash
export PYTHONPATH="${PYTHONPATH}:/home/ruan/Documents/PythonRobotics/"
```
If you want to include it directly in the code itself instead of the whole thing
```python
import sys
sys.path.append("/path/to/directory")
```
Example of how this was used:
```python
import sys
sys.path.append(str(pathlib.Path(__file__).parent.parent.parent))

from utils.angle import angle_mod
```
