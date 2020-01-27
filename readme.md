## 武汉不明肺炎地图

![](./imgs/map.PNG)
![](./imgs/map2.PNG)
![](./imgs/map3.PNG)
![](./imgs/map4.PNG)

[点击访问](http://106.14.208.64/)


关于疫情病毒地图的开发说明
需求分析：
   在武汉肺炎传染病时期，开发出一款传染病实时地图软件，实时展示病毒的发展情况，是一名GIS工作人员应有之义。

1.	操作简单,迅速可以录入数据/没时间，改成读
2.	快速实时
3.	可以展现发展变化
数据来自丁香园，可能数据比较及时客观；
地图可能采用mapbox-gl/leaflet;作为底图，或者自己发布一项地图；但是这样就
用我以前的flask开发出来的api来实现；
4.	各个省市的矢量数据
5.	有一定的查询功能。
6.	美观。
7.	数据库取自admin_2;
 

## Step One: 数据准备
1.	国家基本地图json生成：
2.	丁香园网页数据获取数据


 

1.	权威来源:
https://3g.dxy.cn/newh5/view/pneumonia;
2.	数据获取
目的：从权威来源获取到当前的实时传染疾病数据,因此要求需要这个获取是轮询，比如半小时一次，
当
 
没有发生变化的时候，不进行录入，否则进行录入;
录入数据库的话，采用mongodb/redis,比较符合依据

数据项描述如下:
{
	 Date:录入时间,
  Name: 湖北省,
  Description: “湖北省 确诊 270 例，疑似 11 例，治愈 25 例，死亡 6 例”,
  shapeId:对应Admin中的编码  
}；按照时间存入其中；

3.	数据到展示逻辑层，这里主要是将属性数据和空间数据组装起来，节省空间，形成切实的geojson;
4.	南极冰盖的展示一样，地图必须要有时间轴;

Step2: 开发计划；总计1天时间
1.	权威数据的获取  半天;
2.	数据录入+展示 半天

选择leaflet 作为底图，获取地图太慢

自己发布地图来做

选择 Java来开发；nodejs? 如何推送呢？


数据获取 类似于爬虫，需要java spring schedule + Jsoup来解析数据

底图准备完毕
数据获取完毕
实时数据地图化？
生成geojson，获取数据时进行一次数据连接，连接字段为省市名字
思路很简单，每次写数据之前，都会生成一个合法的geojson

## subblcoks

疑似:#d3d3d3
1-5: #ffffb2
5-10 #feb24c
10-50 #fd8d3c
50-100 #fc4e2a
101+  #b10026
