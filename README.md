### A New Dataset of Handwritten Chinese Character Type for Classification

### Abstarct

The dataset is 400 isolated handwritten Chinese characters, written by 5 people. I named the dataset as CCT-4. Chinese characters have undergone many changes from ancient to modern. I selected 4 types of Chinese character to create the dataset.   
The new dataset consists of four types, Kin(bronze script), Ten(seal script), Kai(traditional Chinese), Kan(simplified Chinese). There are 20 different Chinese characters in each type, and the total number of 4 types is 80 Chinese characters. Everyone wrote 80 characters of four types.  
I performed classification experiments on the dataset based on a convolutional neural network, in an attempt to provide a baseline for the performance of machine learning algorithms on the dataset.


# ◉Dataset introduction
### Datset  category

The table shows Chinese, Chinese pronunciation, English and Japanese pronunciation of the four types of Chinese characters.   
The bronze script and the Seal script are ancient styles of writing Chinese characters.  
The bronze script is engraved in ritual bronzes such as big metal bell.  
In general, the Seal script originated from the Chinese bronze script.  
Traditional Chinese characters and Simplified Chinese characters are one type of standard Chinese character sets of the contemporary written Chinese.

<img src='./tmp/1-Category.png'>

### Image details
 400 samples = 20(character) × 4(category) × 5(people)

### List of Kan Chinese character
<img width= 400 src='./tmp/2-Character list.png'>
<br>
<br>
You can  click the following link to check the details of the characters

[Chinese_Character_List_Detail.pdf](Chinese_Character_List_Detail.pdf)

### Chinese character samples
<img width=400 src='./tmp/3-Printed Chinese characters.png'>

<img width=400 src='./tmp/4-Handwritten Chinese character.png'>




# ◉Classification Methods
I used 6 models to make a classification, as an attempt to provide a baseline for the performance of machine learning algorithms on the dataset.  
   (1) easyCNN  
   (2) ResNet18_Ft      
   (3) AlexNet  
   (4) GoogLeNet  
   (5) ResNet18  
   (6) RegNet_x_8gf  

### (1)easyCNN  
easyCNN is a basic model. In this model, the architecture consists of 5 layers : 2 convolutional layers and three fully-connected layers.

<img src='./tmp/5-EasyCNN.png'>
<br>
<br>

### **(2)Resnet18_Ft**
ResNet18_Ft is a modified model based on ResNet18.
I changed the kernels, stride and padding parameters of the first layer and reshaped the last layer.
<img width=400 src='./tmp/7-Resnet18.png'>


<img width=400 src='./tmp/6-Resnet18_Ft.png'>

### **(3)~(6)**  
From number 3 to number 6, these models are established state of art models. I reshaped the last layer the same as Resnet18_Ft.


# ◉Experiment
I performed experiments with Finetuning by the training details shown in the table, except easyCNN model.  

### **Training details**

<img width=350  src='./tmp/8-Training details.png'>

<br>
<br>

### **Implementation**
First, download the dataset from the following link.

[dataset](https://drive.google.com/file/d/1Kbn7hhfAlayL9FOlQNfVjvYYMbjb3EXU/view?usp=sharing)

Then, unzip the downloaded file and palce it same directory with the main.py

|-main.py  
|-datast

Finally, you can implement the main.py like the below.

    python main.py --model resnet18


* **option**:

--model (easycnn, alexnet, resnet18, googlenet, regnet_x_8gf, default=resnet18_ft)

--pretrained (False. default=True)

--optim (Adam, default=SGD)


### Experiment results
Experiment results demonstrated the good  performance of the finetuning in comparison with scratch.
ResNet18_Ft show a better performance than other models and achieved an improvement compared with ResNet18.  
  Although the train accuracy rate of 6 models is more than 94%, the test accuracy of easyCNN is very low, only 22.5%. I think it is possible that easyCNN has overfitting during training. GoogLeNet, AlexNet, RegNet_x_8gf and ResNet18 obtained a not bad test accuracy.
<img src='./tmp/9-Results.png'>

# ◉Analysis
Finally, I want to briefly talk about the analysis of the experiment results.
In the 6 models, the best test accuracy is only 72.5%. It is not good. I think there are the following reasons.  

To begin with, the training data is insufficient. The Chinese character is complicated and difficult, especially the ancient character like Bronze script and Seal script with many strokes. It is not easy for model to train and get all the feature maps with only 400 images.

Second,  There are some similar characters, as shown in the following Figure . It is important to improve the models’ discriminant ability for detailed information.
<img width=350 src='./tmp/10-Analysis example.png'>

Last of all, Our 5 writers are not professional calligrapher. Especially for Bronze script and Seal script characters, we have no experience of writing them. So, there are some difference between the handwriting and the template
