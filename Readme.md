# Grid Search
<img src="pic/report1.png" width="600">  

- [機器學習準確率提高攻略](https://youtu.be/WeHM2xpYQpw?t=282)

<img src="pic/report2.png" width="600">  

- [concat_nframes 解釋](https://youtu.be/FxuPF4vjga4?t=364)


#### hidden_layer
 layer |  accuracy   |
------ | ----------- |
 1     |  0.458      |
_**3**_| _**0.461**_ |
 5     |  0.458      |
 10    |  0.453      |

#### concat_nframes
 n     |  accuracy  |
------ |  --------- |
 1     |  0.461     |
 3     |  0.531     |
 5     |  0.574     |
_**7**_| _**0.604**_|

#### activative function
function       | accuracy    |
 ------------- | ----------- |
_**Relu**_     | _**0.604**_ |
Hardtanh(-2, 2)|  0.606      |
LogSigmoid     |  0.585      |

#### hidden_dim
dim       |accuracy   |
----------|-----------|
256       |0.604      |
1024      |0.632      |
_**1450**_|_**0.643**_|
2048      |0.632      |

#### dropout
dropout   |Train Acc      |Train Loss     |Val Acc        |Val Loss       |
----------|---------------|---------------|---------------|---------------|
_**0**_   |_**0.686562**_ |_**0.975996**_ |_**0.653006**_ |_**1.104825**_ |
0.25      |0.645405       | 1.120419      | 0.653951      |1.092650       |
0.5       |0.600339       | 1.291241      | 0.632699      |1.168814       |
0.75      |0.523303       | 1.599185      | 0.575737      |1.390120       |

#### optimer
optimer    | Train Acc    |Train Loss    |Val Acc       |Val Loss      |
-----------|--------------|--------------|--------------|--------------|
_**adamW**_|_**0.686562**_|_**0.975996**_|_**0.653006**_|_**1.104825**_|
adam       |0.686907      |0.974301      |0.653377      |1.103774      |
RMSprop    |0.694039      |0.948014      |0.650439      |1.115954      |

#### random seed
seed   | Train Acc    |Train Loss    |Val Acc       |Val Loss      |
-------|--------------|--------------|--------------|--------------|
_**0**_|_**0.686562**_|_**0.975996**_|_**0.653006**_|_**1.104825**_|
6      |0.694026      |0.947285      |0.650871      |1.114530      |
8      |0.694942      |0.944788      |0.651511      |1.113635      |
512    |0.686562      |0.975996      |0.653006      |1.104825      |
128    |0.728779      |0.819181      |0.654751      |1.131167      |




# Dropout analyze (dropout percentage)
#### Comparaison
在不同dropout比例間，比較各個perfoemance

hyperparameter |   |
-------------- |---|
hidden_layer   | 3 |
concat_nframes | 7 |
activative function| relu|
hidden_dim     | 1450 | 
optimer        | adamW|
seed           | 0  |
batch_size     |410(配合下面)|
- control hyperparameter
<img src="pic/report3.png" width="600">

dropout:0.0  
[001/015] Train Acc: 0.572036 Loss: 1.412948 | Val Acc: 0.605974 loss: 1.267317  
[002/015] Train Acc: 0.634832 Loss: 1.164692 | Val Acc: 0.634955 loss: 1.166348  
[003/015] Train Acc: 0.658639 Loss: 1.075911 | Val Acc: 0.644798 loss: 1.129125  
[004/015] Train Acc: 0.676416 Loss: 1.010581 | Val Acc: 0.649976 loss: 1.111486  
[005/015] Train Acc: 0.692544 Loss: 0.953189 | Val Acc: 0.655156 loss: 1.099387  
[006/015] Train Acc: 0.707511 Loss: 0.899287 | Val Acc: 0.656528 loss: 1.098972  
[007/015] Train Acc: 0.722897 Loss: 0.845365 | Val Acc: 0.655814 loss: 1.121996  
[008/015] Train Acc: 0.738969 Loss: 0.791032 | Val Acc: 0.652508 loss: 1.139723  
[009/015] Train Acc: 0.755328 Loss: 0.736602 | Val Acc: 0.650713 loss: 1.167607  
[010/015] Train Acc: 0.771604 Loss: 0.682340 | Val Acc: 0.645509 loss: 1.211581  
[011/015] Train Acc: 0.788601 Loss: 0.628576 | Val Acc: 0.642576 loss: 1.259988  
[012/015] Train Acc: 0.805228 Loss: 0.576311 | Val Acc: 0.637809 loss: 1.306004  
[013/015] Train Acc: 0.821257 Loss: 0.526556 | Val Acc: 0.637350 loss: 1.385012  
[014/015] Train Acc: 0.836352 Loss: 0.479590 | Val Acc: 0.631240 loss: 1.442602  
[015/015] Train Acc: 0.850920 Loss: 0.434970 | Val Acc: 0.630622 loss: 1.515853  
dropout:0.25  
[001/015] Train Acc: 0.544615 Loss: 1.517229 | Val Acc: 0.603543 loss: 1.277859  
[002/015] Train Acc: 0.605517 Loss: 1.272791 | Val Acc: 0.629468 loss: 1.182906  
[003/015] Train Acc: 0.625392 Loss: 1.195359 | Val Acc: 0.641964 loss: 1.135556  
[004/015] Train Acc: 0.638758 Loss: 1.145573 | Val Acc: 0.650062 loss: 1.107623  
[005/015] Train Acc: 0.648398 Loss: 1.108181 | Val Acc: 0.655560 loss: 1.084959  
[006/015] Train Acc: 0.656055 Loss: 1.079223 | Val Acc: 0.662210 loss: 1.065923  
[007/015] Train Acc: 0.663061 Loss: 1.054015 | Val Acc: 0.663216 loss: 1.060523  
[008/015] Train Acc: 0.668321 Loss: 1.031910 | Val Acc: 0.667605 loss: 1.046448  
[009/015] Train Acc: 0.673696 Loss: 1.012121 | Val Acc: 0.668673 loss: 1.040943  
[010/015] Train Acc: 0.678515 Loss: 0.994229 | Val Acc: 0.670596 loss: 1.034395  
[011/015] Train Acc: 0.682766 Loss: 0.977807 | Val Acc: 0.672032 loss: 1.031399  
[012/015] Train Acc: 0.686722 Loss: 0.963691 | Val Acc: 0.673395 loss: 1.027197  
[013/015] Train Acc: 0.690046 Loss: 0.949290 | Val Acc: 0.673787 loss: 1.027352  
[014/015] Train Acc: 0.693490 Loss: 0.936954 | Val Acc: 0.674552 loss: 1.024603  
[015/015] Train Acc: 0.696789 Loss: 0.923966 | Val Acc: 0.676688 loss: 1.021908  
dropout:0.50  
[001/015] Train Acc: 0.502214 Loss: 1.690677 | Val Acc: 0.577093 loss: 1.381366  
[002/015] Train Acc: 0.563073 Loss: 1.436716 | Val Acc: 0.605114 loss: 1.273457  
[003/015] Train Acc: 0.582598 Loss: 1.359502 | Val Acc: 0.619832 loss: 1.220795  
[004/015] Train Acc: 0.594277 Loss: 1.314306 | Val Acc: 0.628394 loss: 1.187120  
[005/015] Train Acc: 0.602181 Loss: 1.283617 | Val Acc: 0.634175 loss: 1.161277  
[006/015] Train Acc: 0.608189 Loss: 1.260260 | Val Acc: 0.640965 loss: 1.141231  
[007/015] Train Acc: 0.613137 Loss: 1.242009 | Val Acc: 0.643620 loss: 1.129209  
[008/015] Train Acc: 0.617263 Loss: 1.226328 | Val Acc: 0.647060 loss: 1.115842  
[009/015] Train Acc: 0.620471 Loss: 1.213219 | Val Acc: 0.650547 loss: 1.105523  
[010/015] Train Acc: 0.623031 Loss: 1.202562 | Val Acc: 0.653002 loss: 1.095634  
[011/015] Train Acc: 0.626100 Loss: 1.192340 | Val Acc: 0.653982 loss: 1.088582  
[012/015] Train Acc: 0.628032 Loss: 1.184792 | Val Acc: 0.656003 loss: 1.084487  
[013/015] Train Acc: 0.630250 Loss: 1.176801 | Val Acc: 0.657229 loss: 1.077582  
[014/015] Train Acc: 0.631934 Loss: 1.169520 | Val Acc: 0.659925 loss: 1.072000  
[015/015] Train Acc: 0.633525 Loss: 1.163305 | Val Acc: 0.660835 loss: 1.066582  
dropout:0.75  
[001/015] Train Acc: 0.411550 Loss: 2.074303 | Val Acc: 0.504655 loss: 1.690616  
[002/015] Train Acc: 0.480628 Loss: 1.772875 | Val Acc: 0.539269 loss: 1.544599  
[003/015] Train Acc: 0.502591 Loss: 1.681522 | Val Acc: 0.557841 loss: 1.468745  
[004/015] Train Acc: 0.515966 Loss: 1.628175 | Val Acc: 0.570111 loss: 1.416805  
[005/015] Train Acc: 0.524745 Loss: 1.593506 | Val Acc: 0.578262 loss: 1.384002  
[006/015] Train Acc: 0.531942 Loss: 1.566523 | Val Acc: 0.585354 loss: 1.356417  
[007/015] Train Acc: 0.536540 Loss: 1.547792 | Val Acc: 0.589022 loss: 1.338960  
[008/015] Train Acc: 0.541216 Loss: 1.532102 | Val Acc: 0.593240 loss: 1.321638  
[009/015] Train Acc: 0.544823 Loss: 1.517688 | Val Acc: 0.596936 loss: 1.311481  
[010/015] Train Acc: 0.547267 Loss: 1.507174 | Val Acc: 0.598833 loss: 1.300195  
[011/015] Train Acc: 0.550067 Loss: 1.498301 | Val Acc: 0.602958 loss: 1.288700  
[012/015] Train Acc: 0.552160 Loss: 1.490404 | Val Acc: 0.604858 loss: 1.282894  
[013/015] Train Acc: 0.553963 Loss: 1.483944 | Val Acc: 0.605483 loss: 1.276090  
[014/015] Train Acc: 0.555135 Loss: 1.478690 | Val Acc: 0.607511 loss: 1.273302  
[015/015] Train Acc: 0.556988 Loss: 1.472936 | Val Acc: 0.608907 loss: 1.266522  
#### Result
In Epoch=15、Dropout=0, Train Acc(0.851) is hihger than Val Acc(0.631), hence the model may be overfit.  
In Dropout=0.5, especially in Dropout=0.25, has higher accuracy to 0.677 and lower loss.  
These dropout can slow down slightly the cause of overfit.
  
# Different dropout percentage on Subampling 

### Subampling
#### [Explain](https://youtu.be/Lx3l4lOrquw?list=PLJV_el3uVTsPy9oCRY30oBPNLCo89yu49&t=834):  
<img src="pic/report4.png" width="600">
簡譯是指在同一mini-batch內，若各label平均分布，會比較好train  

#### Code:

```python
from collections import deque
import itertools

def choice(a, size=None, replace=False):
  return (np.random.random(size)*a).astype(np.int32)


def shuffle(train_X,train_y):
  category = [train_X[train_y==l,:] for l in np.unique(train_y)]
  index = [deque(range(c.shape[0])) for c in category]

  train_X2 = []
  train_y2 = []

  # speedup parameter
  batch_per_label = int(batch_size / len(category))
  len_label_category = len(category)
  minibatch_number = int(train_y.shape[0]/batch_size*1.2)
  label_unique = np.unique(train_y)
  label_tmp_stat = np.repeat(label_unique,batch_per_label)
  random_max = [len(i)-batch_per_label for i in index]

  for _ in tqdm(range(minibatch_number)):
    index_first_ten = [list(itertools.islice(index[i], 0, 10)) for i in range(len_label_category)]
    data_tmp = np.concatenate([category[i][index_first_ten[i],:] for i in range(len_label_category)])
    label_tmp = label_tmp_stat
    random_shuffle = np.random.choice(batch_size,size=batch_size,replace=False)
    data_tmp = data_tmp[random_shuffle,:]
    label_tmp = label_tmp[random_shuffle]
    train_X2.append(data_tmp)
    train_y2.append(label_tmp)
    for i in range(len_label_category):
      random_putback = choice(random_max[i],size=batch_per_label)
      [index[i].insert(random_putback[j],index[i][j]) for j in range(batch_per_label)]
      [index[i].popleft() for j in range(batch_per_label)]
  return train_X2, train_y2
```

hyperparameter |   |
-------------- |---|
hidden_layer   | 3 |
concat_nframes | 7 |
activative function| relu|
hidden_dim     | 1450 | 
optimer        | adamW|
seed           | 0  |
- control hyperparameter
<img src="pic/report5.png" width="600">

dropout:0  
[001/015] Train Acc: 0.490699 Loss: 1.678191 | Val Acc: 0.556983 loss: 1.447714  
[002/015] Train Acc: 0.595725 Loss: 1.286081 | Val Acc: 0.580792 loss: 1.357655  
[003/015] Train Acc: 0.649324 Loss: 1.095076 | Val Acc: 0.587105 loss: 1.346627  
[004/015] Train Acc: 0.696478 Loss: 0.938009 | Val Acc: 0.590701 loss: 1.361195  
[005/015] Train Acc: 0.737217 Loss: 0.807340 | Val Acc: 0.592251 loss: 1.408936  
[006/015] Train Acc: 0.772367 Loss: 0.697243 | Val Acc: 0.592088 loss: 1.483947  
[007/015] Train Acc: 0.802901 Loss: 0.603025 | Val Acc: 0.591427 loss: 1.567383  
[008/015] Train Acc: 0.829820 Loss: 0.520635 | Val Acc: 0.587785 loss: 1.681037  
[009/015] Train Acc: 0.853262 Loss: 0.448276 | Val Acc: 0.587078 loss: 1.801398  
[010/015] Train Acc: 0.874398 Loss: 0.384897 | Val Acc: 0.581699 loss: 1.938984  
[011/015] Train Acc: 0.892282 Loss: 0.329951 | Val Acc: 0.580460 loss: 2.080370  
[012/015] Train Acc: 0.907607 Loss: 0.282746 | Val Acc: 0.576673 loss: 2.243804  
[013/015] Train Acc: 0.920568 Loss: 0.243036 | Val Acc: 0.572823 loss: 2.404935  
[014/015] Train Acc: 0.931621 Loss: 0.208681 | Val Acc: 0.571386 loss: 2.566870  
[015/015] Train Acc: 0.940673 Loss: 0.180346 | Val Acc: 0.565505 loss: 2.712826  
dropout:0.25  
[001/015] Train Acc: 0.453804 Loss: 1.807634 | Val Acc: 0.558307 loss: 1.436524  
[002/015] Train Acc: 0.545855 Loss: 1.462678 | Val Acc: 0.581387 loss: 1.342011  
[003/015] Train Acc: 0.581195 Loss: 1.332257 | Val Acc: 0.592656 loss: 1.296740  
[004/015] Train Acc: 0.605793 Loss: 1.240257 | Val Acc: 0.598695 loss: 1.275882  
[005/015] Train Acc: 0.625217 Loss: 1.167769 | Val Acc: 0.605928 loss: 1.254051  
[006/015] Train Acc: 0.642043 Loss: 1.106688 | Val Acc: 0.606978 loss: 1.251054  
[007/015] Train Acc: 0.656977 Loss: 1.053616 | Val Acc: 0.609837 loss: 1.244305  
[008/015] Train Acc: 0.670317 Loss: 1.008291 | Val Acc: 0.610423 loss: 1.245236  
[009/015] Train Acc: 0.682036 Loss: 0.968331 | Val Acc: 0.612026 loss: 1.244690  
[010/015] Train Acc: 0.692443 Loss: 0.934610 | Val Acc: 0.612681 loss: 1.248126  
[011/015] Train Acc: 0.701542 Loss: 0.903982 | Val Acc: 0.615523 loss: 1.244983  
[012/015] Train Acc: 0.709489 Loss: 0.877444 | Val Acc: 0.615302 loss: 1.252249  
[013/015] Train Acc: 0.716586 Loss: 0.853560 | Val Acc: 0.615387 loss: 1.254485  
[014/015] Train Acc: 0.723055 Loss: 0.832965 | Val Acc: 0.615400 loss: 1.259914  
[015/015] Train Acc: 0.729334 Loss: 0.813383 | Val Acc: 0.616688 loss: 1.260392  
dropout:0.50  
[001/015] Train Acc: 0.398808 Loss: 2.011283 | Val Acc: 0.535408 loss: 1.529780  
[002/015] Train Acc: 0.485053 Loss: 1.684509 | Val Acc: 0.561153 loss: 1.419092  
[003/015] Train Acc: 0.514153 Loss: 1.578582 | Val Acc: 0.573374 loss: 1.366783  
[004/015] Train Acc: 0.531384 Loss: 1.513360 | Val Acc: 0.583296 loss: 1.332275  
[005/015] Train Acc: 0.544068 Loss: 1.466310 | Val Acc: 0.587811 loss: 1.308061  
[006/015] Train Acc: 0.553759 Loss: 1.430575 | Val Acc: 0.592768 loss: 1.291077  
[007/015] Train Acc: 0.561761 Loss: 1.401665 | Val Acc: 0.594981 loss: 1.280642  
[008/015] Train Acc: 0.567310 Loss: 1.378987 | Val Acc: 0.598427 loss: 1.266523  
[009/015] Train Acc: 0.573014 Loss: 1.358863 | Val Acc: 0.600659 loss: 1.259082  
[010/015] Train Acc: 0.577503 Loss: 1.341946 | Val Acc: 0.601624 loss: 1.254344  
[011/015] Train Acc: 0.581372 Loss: 1.326302 | Val Acc: 0.604786 loss: 1.244124  
[012/015] Train Acc: 0.584920 Loss: 1.312687 | Val Acc: 0.606127 loss: 1.238494  
[013/015] Train Acc: 0.588744 Loss: 1.300571 | Val Acc: 0.606783 loss: 1.235578  
[014/015] Train Acc: 0.591067 Loss: 1.290354 | Val Acc: 0.606798 loss: 1.234266  
[015/015] Train Acc: 0.593648 Loss: 1.280652 | Val Acc: 0.606849 loss: 1.234458  
dropout:0.75  
[001/015] Train Acc: 0.274203 Loss: 2.484375 | Val Acc: 0.467080 loss: 1.857589  
[002/015] Train Acc: 0.370356 Loss: 2.117428 | Val Acc: 0.495174 loss: 1.707096  
[003/015] Train Acc: 0.400743 Loss: 2.004469 | Val Acc: 0.512257 loss: 1.623440  
[004/015] Train Acc: 0.418997 Loss: 1.937999 | Val Acc: 0.523970 loss: 1.570495  
[005/015] Train Acc: 0.431910 Loss: 1.892145 | Val Acc: 0.531927 loss: 1.533677  
[006/015] Train Acc: 0.440438 Loss: 1.859941 | Val Acc: 0.540035 loss: 1.503352  
[007/015] Train Acc: 0.447671 Loss: 1.833605 | Val Acc: 0.541913 loss: 1.489677  
[008/015] Train Acc: 0.453197 Loss: 1.814801 | Val Acc: 0.546528 loss: 1.471187  
[009/015] Train Acc: 0.457926 Loss: 1.798611 | Val Acc: 0.549573 loss: 1.460587  
[010/015] Train Acc: 0.461955 Loss: 1.784899 | Val Acc: 0.552765 loss: 1.449928  
[011/015] Train Acc: 0.465023 Loss: 1.774191 | Val Acc: 0.554539 loss: 1.442821  
[012/015] Train Acc: 0.467944 Loss: 1.763372 | Val Acc: 0.557095 loss: 1.434372  
[013/015] Train Acc: 0.470436 Loss: 1.756095 | Val Acc: 0.559711 loss: 1.425307  
[014/015] Train Acc: 0.472713 Loss: 1.748187 | Val Acc: 0.559671 loss: 1.424520  
[015/015] Train Acc: 0.474620 Loss: 1.740817 | Val Acc: 0.560299 loss: 1.422418  
#### Result:  
training set達到94.1%，但在validation set上準確率依舊沒有起來  
於是試了dropout，在dropout=0.25,0.5時準確率有上升一點，但未做subsampling與相比，依舊沒比較好  

