# Multi-camera 3D Gaussian Splatting SLAM
Repository for 3D Vision course project at ETHZ.

# How to run the docker container in Visual Studio Code
1. Install docker in your computer (e.g., Docker engine).
2. Install the Docker extension in VS Code.
3. Open the repository folder in VS Code.
4. Press Ctrl+Shift+P y select "Dev Container: Rebuild Container".

# Add X11 visualization to the Docker container
```
xhost +local:docker
```

# Download datasets
Run the following bash script to download the required datasets and unzip them:
```
bash /home/dev/data/download_dataset.sh
```


# To update the .devcontainer folder
To track changes to the folder, run:
```
git update-index --no-assume-unchanged .devcontainer/
```

To once again stop tracking changes, please run:
```
git update-index --assume-unchanged .devcontainer/
```