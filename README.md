# ADAM(Angular Distance softmax with auto-margin):A Face Comparing method Robust to Hard Examples and Datasets Fusion

---

- **Acc_Margin**

"acc_margin" is a very important indicator,it's a real number which means the classification accuracy of training dataset after margin.
for example,"acc_margin = 0.9" means after margin,the accuracy of softmax_output in a batch_size is 0.9

- **Reimplement of Insightface in Pytorch and test on CASIA-Webface & Vggface2**

The project ["Insightface"](https://github.com/deepinsight/insightface) is written by MxNet,We reimplement it in Pytorch and to show the validity We test the code on "CASIA-webface" & "Vggface2"
and list the result on "LFW"&"CFP-FP"&"AgeDB_30".

dataset|margin|acc_margin|LFW(acc,1e-1,1e-2,3e-3,1e-3)|CFP-FP|AgeDB_30
:---:|:---:|:---:|:---:|:---:|:---:
Webface|Arcface(s=64,m=0.5)|0.98|98.98/99.73/99.00/98.43/97.93|95.06/97.11/87.76/86.16/77.16|93.28/94.77/80.13/75.70/58.13
Webface|Arcface(s=30,m=0.5)|0.87|99.17/99.73/99.17/98.77/97.13|95.44/97.37/90.42/87.42/81.56|93.45/95.27/80.87/75.43/60.87
Webface|Arcface(s=15,m=0.5)|0.61|99.03/99.80/98.93/98.53/96.73|96.13/98.08/88.68/85.71/80.25|93.02/94.90/74.70/67.23/51.13

dataset|margin|acc_margin|LFW(acc,1e-1,1e-2,3e-3,1e-3)|CFP-FP|AgeDB_30
:---:|:---:|:---:|:---:|:---:|:---:
Vggface2|Arcface(s=64,m=0.3)|0.95|99.57/99.83/99.67/99.47/98.90|98.14/99.34/96.88/95.60/91.19|95.20/97.20/87.83/87.20/69.30
Vggface2|Arcface(s=30,m=0.3)|0.97|99.62/99.83/99.63/99.57/99.27|98.13/99.49/97.31/96.17/93.60|94.83/96.97/85.90/83.27/70.53
Vggface2|Arcface(s=15,m=0.3)|0.95|99.37/99.90/99.43/99.20/98.43|97.33/99.00/95.03/93.68/87.59|91.57/93.07/61.37/52.40/28.40

-- **ADM test result on CASIA-Webface & Vggface2**

dataset|margin|acc_margin|LFW(acc,1e-1,1e-2,3e-3,1e-3)|CFP-FP|AgeDB_30
:---:|:---:|:---:|:---:|:---:|:---:
Webface|ADM(s=64,m=0.3)|0.95|99.12/99.80/99.03/98.70/97.53|94.94/97.77/88.94/86.19/74.16|93.60/95.03/81.13/72.73/53.10
Webface|ADM(s=30,m=0.3)|0.95|99.23/99.77/99.23/98.90/97.43|95.54/97.48/91.14/87.42/81.33|93.83/95.87/83.33/78.70/63.00
Webface|ADM(s=15,m=0.3)|0.95|99.22/99.77/99.30/98.93/96.90|96.27/98.11/91.37/88.39/78.96|93.43/95.50/80.57/74.73/64.37

dataset|margin|acc_margin|LFW(acc,1e-1,1e-2,3e-3,1e-3)|CFP-FP|AgeDB_30
:---:|:---:|:---:|:---:|:---:|:---:
Vggface2|ADM(s=64,m=0.3)|0.92|99.58/99.83/99.67/99.53/99.23|97.73/99.00/96.08/94.48/91.28|95.18/96.80/85.13/80.27/71.33
Vggface2|ADM(s=30,m=0.3)|-|-|-|-
Vggface2|ADM(s=15,m=0.3)|-|-|-|-

you can see on Webface & Vggface2,the result of Arcface and ADM is quiet close,but Arcface drops a lot when s = 15 on Vggface2.

- Angular Distance

To Be Done

- Meaning of S

To Be Done

- Seperate Margin

To Be Done

- Auto Margin

To Be Done


