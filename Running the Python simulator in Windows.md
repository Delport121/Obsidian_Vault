# Installation
The following steps are equivalent to the first few steps in the read me, meant for a linux system:
- (Do the following in the directory where you want your simulator to be cloned)
1) Create a virtual environment
   ```python
   python -m venv gym_env
```
2) Activate the virtual ennvironment
   * Note a possible error: "execution of scripts is disabled on this system"
   ```python
   gym_env\Scripts\activate
```
3) Clone the repo
   ```python
   git clone https://github.com/f1tenth/f1tenth_gym.git
```
4) Navigate into the cloned repo
   ```python
   cd f1tenth_gym
```
5) Install the package
   ```python
   pip install -e .
```
## Error: "execution of scripts is disabled on this system"
To fix this, you need to change the execution policy in PowerShell:

1. **Open PowerShell as Administrator**:
    - Click on the Start menu, type `powershell`, right-click on Windows PowerShell, and select "Run as administrator".
2. **Change the execution policy**:
    - In the PowerShell window, enter the following command:
	    `Set-ExecutionPolicy RemoteSigned`
    
    - Press `Y` and then `Enter` to confirm.
3. **Activate the virtual environment**:
    
    - Navigate to your project directory:
        `cd path\to\your\project`

    - Activate the virtual environment:
        `gym_env\Scripts\activate`

## Wheel error
```powershell
(gym_env) PS E:\GitRepository> git clone https://github.com/f1tenth/f1tenth_gym.git
>>
Cloning into 'f1tenth_gym'...
remote: Enumerating objects: 3542, done.
remote: Counting objects: 100% (1934/1934), done.
remote: Compressing objects: 100% (678/678), done.
remote: Total 3542 (delta 1235), reused 1728 (delta 1131), pack-reused 1608
 | 5.95 MiB/s
Receiving objects: 100% (3542/3542), 4.08 MiB | 6.08 MiB/s, done.
Resolving deltas: 100% (2000/2000), done.
(gym_env) PS E:\GitRepository> cd f1tenth_gym
(gym_env) PS E:\GitRepository\f1tenth_gym> pip install -e .
Obtaining file:///E:/GitRepository/f1tenth_gym
  Installing build dependencies ... done
  Checking if build backend supports build_editable ... done
  Getting requirements to build editable ... done
  Preparing editable metadata (pyproject.toml) ... done
Collecting gym==0.19.0 (from f110_gym==0.2.1)
  Using cached gym-0.19.0.tar.gz (1.6 MB)
  Installing build dependencies ... done
  Getting requirements to build wheel ... error
  error: subprocess-exited-with-error

  × Getting requirements to build wheel did not run successfully.
  │ exit code: 1
  ╰─> [1 lines of output]
      error in gym setup command: 'extras_require' must be a dictionary whose values are strings or lists of strings containing valid project/version requirement specifiers.
      [end of output]

  note: This error originates from a subprocess, and is likely not a problem with pip.
error: subprocess-exited-with-error

× Getting requirements to build wheel did not run successfully.
│ exit code: 1
╰─> See above for output.

note: This error originates from a subprocess, and is likely not a problem with pip.
```
### Why This Issue Occurs

1. **Source Distribution Issues**: Sometimes, source distributions contain configurations or dependencies that are problematic for certain environments. This is what you're experiencing with the `gym` package.
    
2. **Environment-specific Problems**: Building packages from source can depend on having specific tools or configurations that might not be present or correctly set up in your environment.
    
3. **Compatibility Issues**: Sometimes, older versions of packages (like `gym==0.19.0`) might have issues that are fixed in later releases, but you are constrained to a specific version due to dependencies.