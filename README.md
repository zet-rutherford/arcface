
# Face recognition with ArcFace



## Installation

Use your Python virtual environment such as [virtualenv](https://virtualenv.pypa.io/en/latest/) to isolate project.

```
virtualenv -p python3.7 face-recognition
source face-recognition/bin/activate
```

Then install all dependencies.

```
pip install -r requirements.txt
```

_Note: GPU is not required to run this code, but model inference will be faster if you have one._

## Model
Download checkpoint for a model from [GoogleDrive](https://drive.google.com/drive/folders/1omzvXV_djVIW2A7I09DWMe9JR-9o_MYh)/[Baidu](https://pan.baidu.com/s/1L8yOF1oZf6JHfeY9iN59Mg#list/path=%2Fms1m-ir50) and move it to `checkpoint/backbone_ir50_ms1m_epoch120.pth`

## Data

All datasets with faces must support [ImageFolder](https://pytorch.org/docs/stable/torchvision/datasets.html#imagefolder) format. Look at the prepared examples in `data` directory. For all subsequent commands use `tags` argument to select specific datasets in `data` directory.

## Data preprocessing
To prepare data with cropped and aligned faces from your original images, run:

```
python face_alignment.py --tags actors actresses musk woman --crop_size 112
```

_Note: crop_size argument must be either 112 or 224._

## Similarity visualization

To visualize similarity between faces in table format, run:

```
python similarity.py --tags actors actresses musk woman
```

The result for each dataset will be saved in `images` directory.

## t-SNE visualization

To use t-SNE for dimensionality reduction and 2D visualization of face embeddings, run:

```
python tsne.py --tags actors actresses musk woman
```

Results will be plotted in a separate window. You can enlarge the image to look at details.
