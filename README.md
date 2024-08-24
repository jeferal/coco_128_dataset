# COCO 128 Dataset - DVC tutorial
This package is meant to a tutorial to learn how to use the Data Version Control

```bash
mkdir coco_128_dataset
cd coco_128_dataset
```

Now initialize git and dvc
```bash
git init
dvc init
```

At this point, we can add the raw data of the dataset, for example:
```
wget https://github.com/ultralytics/assets/releases/download/v0.0.0/coco128.zip
unzip coco128 -o data
```

Now we need to add the data folder to dvc and once added it will suggest add
a git ignore because we do not want to track the raw data with git and commit the changes:
```
dvc add data/
git add data/.dvc data/.gitignore
git commit -m "added data to dvc"
```

At this point, we can add a remote location for storing the dataset versions with dvc, the remote storage can be
set through ssh, s3, google drive, etc. In the documentation we can find all storage that is supported:
```
dvc remote add -d <remote_name> ssh//:username@host:<path>  # -d is default remote
dvc push
git commit -m "Added remote <remote_name>"
```

## Making changes to the data

