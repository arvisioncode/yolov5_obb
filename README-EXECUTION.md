## SETUP
- Usar Ubuntu
- En un pc me funciono la instalacion y en otro no, puede ser tema de las versiones de CUDA y la instalacion de torch

# TRAIN

python train.py --weights yolov5x.pt --data 'data/icdar_obb_v2.yaml' --hyp 'data/hyps/obb/hyp.finetune_dota.yaml' --epochs 300 --batch-size 8 --img 1024 --device 0


# INFERENCE

python detect.py --weights 'runs/train/exp15/weights/best.pt' --source 'dataset/icdar_obb/val/images/1.jpg' --img 1024 --device 0 --conf-thres 0.25 --iou-thres 0.2 --hide-labels --hide-conf

# EVALUATION

python val.py --data 'data/icdar_obb.yaml' --weights 'runs/train/exp15/weights/best.pt' --batch-size 8 --img 1024 --task 'val' --device 0 --save-json --name 'obb_demo'


# OTHERS
## DOWNLOAD REMOTE IMAGES
scp -i gpuzilla ubuntu@3.130.241.81:~/aymane/yolov5_obb/runs/detect/exp/1.jpg ~/Documents/
