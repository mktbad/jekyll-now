---
layout: post
title: tensorflowメモ
category: dl
---
# 環境構築
[参照](http://www.tensorflow-partner.jp/single-post/2017/04/20/TFLearn%E3%81%AE%E7%92%B0%E5%A2%83%E6%A7%8B%E7%AF%89%EF%BC%88Ubuntu%EF%BC%89)
* tflearnやkerasはpipで入れるだけ

# 機能
* tensorboard --logdir=/tmp/tensorflow_logでビジュアライズ

# 注意点
* batch_sizeがデータ枚数より大きい場合trainが走らない

