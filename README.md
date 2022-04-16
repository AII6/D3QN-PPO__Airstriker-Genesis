# D3QN__Airstriker-Genesis
使用D3QN算法对Atari游戏进行学习，加入了buffer，soft update，epsilon decay

由于学生党无实验室只能用免费版Colab，buffer size设定在6000，再大就不够了

因此本程序无法对游戏有足够的记忆，在训练到一定水平后再训练会出现overfit，记忆较短

其中对原版的动作空间和奖励函数进行了修改，修改如下：
1. 动作仅有3个，分别为left,right,fire    tip：经本人试验，该游戏设定无法通过一直按fire键进行射击，必须两次fire之间间隔其他按键，如left和right
2. 飞机每活一帧reward+1
3. 飞机死亡reward-500
4. 打掉敌机reward+80
5. 在左下或右下角呆着每呆一帧reward-2     tip:没有这个规则之前训练出来发现飞机一直很怂，躲在右下角的位置，这样尽量让飞机主动攻击

对于检测飞机是否死亡以及是否在左下或右下角，本程序采用K-means方法，因为这是无监督方法，不需手动标注

以下是每轮得分情况：

![6697b7ce4f96d4a965c1e2fbd81049f](https://user-images.githubusercontent.com/86092949/163334497-95ea3082-b8f2-433a-b195-2c46e01c899b.png)

可以看到450轮之前得分较稳定，之后迅速下降，主要原因目前推测为buffer size太小，导致之后overfit了，前期的经验无法保存

![6697b7ce4f96d4a965c1e2fbd81049f](https://github.com/AII6/D3QN__Airstriker-Genesis/blob/main/petal_20220416_221652.gif)
