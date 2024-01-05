# YOLOv7 Logo Detection

This repository contains the code and data used in our research for detecting logos using the YOLOv7 model. Our study involves comprehensive evaluation using two datasets, demonstrating that YOLOv7 achieves high precision and recall, effectively detecting logos of various scales and orientations.

## Project Structure

- `data/`: Contains the datasets and annotations used for training and validation.
  - `annotations/`: Annotations for the test, train, and validation datasets.
  - `flickr_logos_27_dataset/`: The Flickr Logos 27 dataset used in our experiments.
  - `images/`: Organized images for test, train, and validation.
  - `labels/`: Labels corresponding to the images for test, train, and validation.
- `runs/`: Intended to contain training checkpoints and model weights (not included in the submission).
- `src/`: Source code of the YOLOv7 model.
  - `cfg/`: Configuration files for model training.
  - `yolov7/`: YOLOv7 architecture and scripts for training and detection.
- `Sample/`: A sample set of images to test the model.

## Setup

To set up the project, navigate to the project directory:

```sh
cd cs412-logo-recognition/
```

Install the required Python packages:

```sh
pip install -r src/requirements.txt
```

## Training the Model

To train the YOLOv7 model, run the following command:

```sh
python src/yolov7/train.py --img-size 640 --cfg src/cfg/training/yolov7.yaml --hyp data/hyp.scratch.yaml --batch 2 --epoch 300 --data data/logo_data_flickr.yaml --weights src/yolov7_training.pt --workers 2 --name yolo_logo_det --device 0
```

This will train the model using the Flickr Logos 27 dataset, and the checkpoints should be saved in the `runs/` directory.

## Running Inference

To run inference with the trained model:

```sh
python src/yolov7/detect.py --source data/Sample/test --weights runs/train/yolo_logo_det/weights/best.pt --conf 0.25 --name yolo_logo_det
```

This will process images in the `data/Sample/test` directory using the trained weights.

## Note

The source code versions submitted to Moodle and pushed to GitHub do not include the checkpoint in the `runs/` folder due to file size limitations. To perform inference using our trained model, download the checkpoint from the link below and extract the `yolo_logo_det` folder to the `runs/train` directory.

[Checkpoint Download](https://drive.google.com/file/d/1dp49HhPm_JLY7lulCULmo-xH7Sjp7T6Z/view?usp=sharing)
