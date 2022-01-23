◉Project

A New Dataset of Handwritten Chinese Character Type for ClassificationCancel changes

◉dataset
 CCT-4
 Download:https://drive.google.com/drive/folders/1--HlwXtG4ZfLP_Ey_yUrTJDiBeDhwVJz?usp=sharing

◉data directory
 ./data
   ┣Train
   ┣Train
   ┗CTT-4_train.csv
   ┗CTT-4_train.csv

◉Implementation

python main.py


option:

--model (easycnn, alexnet, resnet18, googlenet, regnet_x_8gf, default=resnet18_ft)

--pretrained (False. default=True)

--optim (Adam, default=SGD)

--lr

--n_epochs

--batch_size

--img_size
