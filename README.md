 데이콘 손글씨(숫자) 분류 경진대회
 ==========
28x28 image을 분류하는 문제  
accuracy 0.788로 410명중 88위  
간단한 문제지만 자기계발 목적으로 진행함  
__개인 저장용으로 코드의 제목과 코드 내용이 일치하지 않습니다, 코드 자체도 정리되어 있지 않습니다__

traning process
------
EDA -> Machine Learning ->  -> Deep Learning -> Data Augmentation + Learning -> Pseudo_Labeling

EDA : 간단한 이미지 확인, 데이터의 균형 확인, PCA visualization , UMAP visualization    
UMAP으로 차원축소한뒤 해당 데이터를 학습시켰으나 눈에띄게 좋은 성능을 내지 못함    
EDA에서 나온 인사이트로 좋은 학습결과를 내기 힘들것으로 보아 해당 방법에서 고민하는것 보다    
널리 알려진 Image classification 모델을 활용하여 분류.  

Machine Learning : 기본 데이터셋, 차원축소한 데이터셋 모두 학습성능이 좋지 않음. Deep Learning으로 전환  

Deep Learning   
-----
1. Simpe CNN : Accuracy 0.7의 성능으로 준수함. 해당 모델의 성능을 기준으로 정확도 향상을 위해 다른 모델을 탐색함 (0.7)  
2. VGG : 모델이 깊은 반면 데이터셋의 크기는 작기 때문에 그다지 뛰어난 성능은 내지 못함 CNN과 비슷한 성능 (0.71)  
3. Inception v4 : 깊고, *가벼운 모델*. 하지만 역시 데이터셋이 너무 작아서 그런지 딱히 뛰어난 성능은 내지 못함(0.72)  
4. EffcientNet : MnasNet에서 Compound Scaling을 적용. 역시 모델이 깊음. 위 세 모델보다는 낫지만 엇비슷함(0.73)  
5. Resnet : 모델의 목적은 기울기 소실문제를 해결하기 위해 residula learning을 한것이나.   
모델 자체가 얕으면서도 성능이 좋음. 해당 문제에서도 타 모델보다 준수한 성능을 보여줌 (0.75)  

Data Augmentation   
------  
test셋의 경우 train과 데이터의 형태가 다른점을 발견함.  
손글씨 일부가 잘리거나, rotation된 형태, atrifact가 존재함.  
해당 문제점을 무시하고 학습할 경우 제대로 된 학습이 되지 않을것이 분명하기에  
학습 데이터도 그에 맞게 이미지를 변환할 필요가 있다고 생각됨  

1.atrifact : ???  
2.손글씨 일부가 잘림 : crop 적용  
3.rotation : rotation 적용  
  
Pseudo_labeling  
-------  
augmentation + deep learning 으로도 만족하지 못한 성능.  
이미지 분류의 정확도 향상을 위해 검색중  
Pseudo_labeling 기법을 확인. 적용  


Accuracy  
-----  
resnet18 + augmentation + pseudo_labeling + deep learning : 0.78


1위의 accuracy는 0.97  
상위권 빌더분들의 코드가 공유될경우 업로드하도록 하자  

Reference
-----

agumentation
[agumentation]: https://dacon.io/competitions/official/235838/codeshare/3734?page=1&dtype=recent 
agumentation
 https://github.com/anirudhshenoy/pseudo_labeling_small_datasets/blob/master/pseudo_label-DL.ipynb  
 https://deep-learning-study.tistory.com/563   
 https://dacon.io/competitions/official/235838/codeshare/3778?page=1&dtype=recent  
