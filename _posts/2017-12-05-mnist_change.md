---
layout: post
title: mnistではなく自前データセットを読み込ませる
category: dl
---

```
# 自前データのファイルパス一覧を取得
self.images = glob(os.path.join("./data", self.dataset_name, "*.jpg"))
# ファイルパスを渡せば画像データndarrayを読み込んでくれる関数
def imread(path, grayscale = False):
    if (grayscale):
        return scipy.misc.imread(path, flatten = True).astype(np.float)
    else:
        return scipy.misc.imread(path).astype(np.float)

# data_Xにmnistがロードされるところを消去し、代わりに自前データを入れる
# mnist_loadとかではdata_Xにはndarrayで[data_num,height,width,channel]の形で入っている
# ndarrayの場合は[0,height,width,channel]のemptyを用意し、自前データ一枚[1,height,width,channel]ずつをappendして行く
# imreadで読み込んだだけだとdimentionが整っていない場合があるのでreshapeなどで整形
self.data_X = np.empty((0,self.input_height,self.input_width,1), float)
for image in self.images:
　　　self.data_X = np.append(self.data_X, np.array([imread(image).reshape([self.input_height,self.input_width,1])]), axis=0)
```
