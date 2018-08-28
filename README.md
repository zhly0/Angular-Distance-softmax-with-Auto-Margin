# ADAM(Angular Distance softmax with auto-margin):A Face Comparing method Robust to Hard Examples and Datasets Fusion

---

- **Acc_Margin**

"acc_margin" is a very important indicator,it's a real number which means the classification accuracy of training dataset after margin.
for example,"acc_margin = 0.9" means after margin,the accuracy of softmax_output in a batch_size is 0.9

- **Reimplement of Insightface in Pytorch and test on CASIA-Webface & Vggface2**

The project ["Insightface"](https://github.com/deepinsight/insightface) is written by MxNet,We reimplement it in Pytorch and to show the validity We test the code on "CASIA-webface" & "Vggface2"
and list the result on "LFW"&"CFP-FP"&"AgeDB_30".

dataset|margin|acc_margin|LFW(acc,1e-1,1e-2,1e-3)|CFP-FP|AgeDB_30
:---:|:---:|:---:|:---:|:---:|:---:
Webface|Arcface(s=64,m=0.5)|0.98|98.98/99.73/99.00/97.93|95.06/97.11/87.76/77.16|93.28/94.77/80.13/58.13
Webface|Arcface(s=30,m=0.5)|0.87|99.17/99.73/99.17/97.13|95.44/97.37/90.42/81.56|93.45/95.27/80.87/60.87
Webface|Arcface(s=15,m=0.5)|0.61|99.03/99.80/98.93/96.73|96.13/98.08/88.68/80.25|93.02/94.90/74.70/51.13

dataset|margin|acc_margin|LFW(acc,1e-1,1e-2,1e-3)|CFP-FP|AgeDB_30
:---:|:---:|:---:|:---:|:---:|:---:
Vggface2|Arcface(s=64,m=0.3)|0.95|99.57/99.83/99.67/98.90|98.14/99.34/96.88/91.19|95.20/97.20/87.83/69.30
Vggface2|Arcface(s=30,m=0.3)|0.97|99.62/99.83/99.63/99.27|98.13/99.49/97.31/93.60|94.83/96.97/85.90/70.53
Vggface2|Arcface(s=15,m=0.3)|0.95|99.37/99.90/99.43/98.43|97.33/99.00/95.03/87.59|91.57/93.07/61.37/28.40

- **result of ADAM**

dataset|margin|acc_margin|LFW(acc,1e-1,1e-2,1e-3)|CFP-FP|AgeDB_30
:---:|:---:|:---:|:---:|:---:|:---:
Webface|ADAM(s=30,m=0.35)|0.83|99.27/99.73/99.30/97.67|96.17/97.97/92.22/80.30|93.92/95.40/81.47/62.13

- **Test Datasets**

For 1:1 Face comparing,Test dataset is a big problem.now the algorithm can easy reach high accuracy on "LFW",and for Large-Disjoints dataset like "MegaFace" & "Glint Trillion Pairs" the Disjoints contains almost the easy examples so the algorithm only make big difference when the FAR is very low(such as 1e-9),usually it will take several hours to get feature on this dataset,which is very unconvenient for research to judge their algorithm.

Consider there are some small datasets that aimed at hard examples like "CFP-FP"(7000 pairs,Frontal-Profile face is a challenge for most algorithm) & "AgeDB_30"(6000,Age is also challenge),while LFW is aimed at IDs,so we can combine this three dataset as one dataset,which we called "hard-examples test dataset"(which has 9500 positive pairs and 9500 negative pairs)

To avoid random influence, we choose (accuracy,TAR@FAR=1e-1,TAR@FAR=1e-2,TAR@FAR=1e-3,TAR@FAR=3e-4) as our criterion,because there are only 9500 negative pairs,so we choose 3e-4(4 negative pairs) instead of 1e-4(1 negative pairs). 

- **Meaning of S**

To Be Done

- **Seperate Margin(Scale Margin)**

To Be Done

- **Auto Margin**

To Be Done

- **Result on "hard-examples test dataset"**

dataset|margin|acc_margin|HETD(acc,1e-1,1e-2,1e-3,3e-4)
:---:|:---:|:---:|:---:
Webface|Arcface(s=30,m=0.5)|0.87|95.64/97.54/90.06/78.62/70.19
Webface|ADSM(s=30,m=0.5)|0.82|95.86/97.66/90.30/78.76/70.58
Webface|ADAM(s=30,m=0.35)|0.83|96.23/97.94/90.87/80.17/73.95
-|-|-|-
Vgg2_s+msra_imbalance|Arcface(s=64,m=0.4)|0.94|95.59/97.59/90.32/79.41/68.69
vgg2_s+msra_imbalance|ADSM(s=64,m=0.4)|0.96|95.57/97.48/90.20/81.38/74.51
-|-|-|-
Vgg2+msra+asia|Arcface(s=64,m=0.5)|0.83|98.72/99.35/98.30/96.13/94.79
Vgg2+msra+asia|ADSM(s=64,m=0.5)|0.85|98.91/99.28/98.62/97.44/96.19



