协同过滤推荐算法主要分为：

1、基于用户。根据相邻用户，预测当前用户没有偏好的未涉及物品，计算得到一个排序的物品列表进行推荐<br>
2、基于物品。如喜欢物品A的用户都喜欢物品C，那么可以知道物品A与物品C的相似度很高，而用户C喜欢物品A，那么可以推断出用户C也可能喜欢物品C。<br>
不同的数据、不同的程序猿写出的协同过滤推荐算法不同，但其核心是一致的：<br>
1、收集用户的偏好<br>
    &emsp; 1)不同行为分组<br>
    &emsp; 2)不同分组进行加权计算用户的总喜好<br>
    &emsp; 3)数据去噪和归一化<br> 
2、找到相似用户(基于用户)或者物品(基于物品)<br>
3、计算相似度并进行排序。根据相似度为用户进行推荐<br>

Recommender system for collaborative filtering based on user<br>
本次实例过程：<br>
1、初始化数据<br>
    &emsp; 获取movies和ratings<br>
    &emsp; 转换成数据userDict  表示某个用户的所有电影的评分集合，并对评分除以5进行归一化<br>
    &emsp; 转换成数据ItemUser  表示某部电影参与评分的所有用户集合<br>
2、计算所有用户与userId的相似度<br>
    &emsp; 找出所有观看电影与userId有交集的用户<br>
    &emsp; 对这些用户循环计算与userId的相似度：<br>
      &emsp;&emsp;&emsp;获取A用户与userId的并集。格式为:{'电影ID',[A用户的评分,userId的评分]}，没有评分记为0<br>
      &emsp;&emsp;&emsp;计算A用户与userId的余弦Cosine距离，越大越相似<br>
3、根据相似度生成推荐电影列表<br>
4、输出推荐列表和准确率<br>
