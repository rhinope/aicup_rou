# AICUP Rou


# 訓練環境介紹 : 
```
使用TWCC : cm.2xsuper
映像檔為 : pytorch-22.02-py3:latest

必要套件:
Monai
pip install monai

smp
pip install git+https://github.com/qubvel/segmentation_models.pytorch

Adabelief
pip install adabelief-pytorch==0.2.0
```

# 結果圖 : 
![Result](https://github.com/rhinope/aicup_rou/blob/main/DataParallel%20%2B%20tf_efficientnetv2_m_in21ft1k_ver3__Train_Test_loss.png)



# 程式檔案

模型名稱|Jupyter Notebook|權重|Result|
--|--|--|--|
EfficientNetV2_m|[efficientnetv2_m_in21ft1k.ipynb](https://github.com/rhinope/aicup_rou/blob/main/efficientnetv2_m_in21ft1k.ipynb)|[weight](https://drive.google.com/file/d/1PRl_sLD4p6T1HNPD57duAMfKOjaWyWb0/view?usp=sharing)|[result](https://github.com/rhinope/aicup_rou/blob/main/output.zip)|
Pseudo Label|[Pseudo Label maker.ipynb](https://github.com/rhinope/aicup_rou/blob/main/pub2img_public.ipynb)|---|[Pseudo Label](https://github.com/rhinope/aicup_rou/blob/main/ann_plus%20(Pseudo%20Label).zip)

# 使用範例

### 路徑修改
1. 訓練圖片路徑
```
# path
folder_path = "{YOUR PATH}"
```

2. 權重讀取位置
```
model.load_state_dict(torch.load("{}.pth".format(save_path)))
```

3. Public、Private dataset 路徑
```
tempdir = "{PUBLIC_PATH}"
tempdir = "{PRIVATE_PATH}"
```

4. 訓練時若出現size mismatch，很有能是訓練圖片的整數無法整除Batchsize，導致Batchnormalize出現問題，這時只要更改Training 跟 Validation的比例即可
