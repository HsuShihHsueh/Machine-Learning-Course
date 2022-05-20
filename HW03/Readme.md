# Data Augmentation

```python
train_tfm = transforms.Compose([
    transforms.RandomRotation(10, expand=False, center=None),
    transforms.RandomCrop(np.random.randint(350,500),pad_if_needed=True),
    transforms.Resize((128, 128)),
    transforms.RandomHorizontalFlip(p=0.5), 
    transforms.ColorJitter(brightness=(0.7,1.5), contrast=(0.7,1.3), saturation=(0.7,1.5)),
    transforms.ToTensor()
])
```


1. RandomRotation
```python
transforms.RandomRotation(10, expand=False, center=None)
# randomly rotate image +10 ~ -10 dgree
# expand: whether keep the image on non-rectangle part
# center: whether the rotate center is the image center
```
<img src='' width=600px>
2. RandomCrop
```python
transforms.RandomCrop(np.random.randint(350,500),pad_if_needed=True)
# randomly crop the image to 350x350 ~ 500x500 px
# pad_if_needed: 
```
3. Resize

4. RandomHorizontalFlip

5. ColorJitter



reference:

# Ensemble and Cross validation 

using
[ensemble_train.ipynb](ML_HW03_Image_Classification_ensemble_train.ipynb)
to train and usng
[ensemble_test.ipynb](HW03/ML_HW03_Image_Classification_ensemble_test.ipynb)

Data in release included model and .


ID_1  | ID_2 | ID_3 | ID_4 
------|-------|------|------
0. | 02:10 |  500 |    0

training curve
