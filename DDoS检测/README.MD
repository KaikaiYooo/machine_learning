## 用KDDCUP99 预测DDoS

这是我第一次试水机器学习，代码中有丰富的注释，便于初学者理解,paper文件夹有引用的论文
直接上思路：
![gbdt在项目中的实现流程](https://github.com/aviraonepiece/machine_learning/blob/master/DDoS%E6%A3%80%E6%B5%8B/paper/1.png)

- ### KDDCUP 99数据集简介:
Kddcup99数据集包含25种攻击数据、正常数据、主机配置信息、日志信息。kddcup99有41个特征，对于基于内容的特征攻击预测十分不明朗，特征也有许多不确定性。但是基于连接类型和2秒内连接数量的特征预测与之还是不错的。所以对于数据包分组层面防范还是有很大优势。
发现数据集在预测DDoS方面效果还不错，这里训练数据、测试数据6/4。学习识别防护DOS攻击

[数据是已经打标好的，文件过大，放在百度网盘，密码：ojha](https://pan.baidu.com/s/1d7CMe6sO9NqKj2YEygxYjQ)
 
- ### 特征提取与数据清洗：
这里感谢卑尔根大学的kdd99_feature_extractor开源项目，可以将网络分组数据化解为KDDCUP 99的特征的数据，给项目带来了可以部署在生产环境的希望
- ### 模型训练：
由于数据已经打标，这里用监督式学习，采用梯度提升树训练模型，gbdt.py为训练模型，client.py为加载模型预测，其余文件没用

- ### 预测的准确率：
交叉验证，精度在97左右

- ### 不足之处以及未来打算：

采用监督式学习，而且数据集过老，在实际生产环境中并不适用，但是提供了解决问题的思路。
在此立下flag，有时间换[UNSW-NB15](https://www.unsw.adfa.edu.au/australian-centre-for-cyber-security/cybersecurity/ADFA-NB15-Datasets/)数据集再来一次，这个数据集比较新，2015年的，有部署在实际生产环境中的意义