---
layout:     post
title:      mac安装ElasticSearch以及kibana
subtitle:   手把手教你在mac上安装ElasticSearch以及kibana
date:       2020-10-21
author:     irving.gx
header-img: img/post-bg-re-vs-ng2.jpg
catalog: true
tags:
    - Mac,ElasticSearch,Kibana
---


# 前言
ElasticSearch是一个功能强大的全文搜索引擎，基于Lucene，Lucene是一套用于全文检索和搜索的代码程序库。ES可以直接拆箱使用，而Lucene却不能，前者和后者的关系类似于汽车和引擎的关系。https://db-engines.com/en/ranking 这个网站上是各大数据库的使用情况的排名，可以看到es目前出于第8位。

<img src="/img/kibana1.png"/>


ES可以做的事情非常多，主要是实时的数据分析，数据存储，快速搜索等功能。比如进行文本的存储与索引，进行数据的聚合等等。kibana可以对es的数据进行可视化的显示，除了显示结果，也可以以图表的形式对数据进行展现。


# 安装与测试

```
brew install elasticsearch
```
安装ElasticSearch
```
brew install kibana
```
安装kibana
可以通过
```
elsticsearch —version
```
查看是否安装成功

在安装好kibana以及ElasticSearch之后进入到kibana的安装目录
执行
```
./kibana
```
启动kibana
在控制台执行
```
elasticsearch
```
命令启动elasticsearch

访问http://localhost:5601/ 可以进入到kibana的主界面
访问http://localhost:9200/可以看到elasticsearch的信息

 ![image](https://raw.githubusercontent.com/GuoXinsayhello/GuoXinsayhello.github.io/master/img/kibana2.png)
 
 ![image](https://raw.githubusercontent.com/GuoXinsayhello/GuoXinsayhello.github.io/master/img/kibana3.png)

在kibana界面当中可以进行es的测试

 ![image](https://raw.githubusercontent.com/GuoXinsayhello/GuoXinsayhello.github.io/master/img/kibana4.png)
 
下面是在kibana中存入数据

 ![image](https://raw.githubusercontent.com/GuoXinsayhello/GuoXinsayhello.github.io/master/img/kibana5.png)

# elasticsearch vs solr

搜索引擎并不是只有elasticsearch,solr也是基于Lucene的搜索引擎，那么两者有什么区别呢？Solr是基于Lucene的全文搜索服务器，对外提供类似于Web-service的API接口。用户可以通过http请求，向搜索引擎服务器提交一定格式的文件，生成索引；也可以通过提出查找请求，并得到返回结果。

 ![image](https://raw.githubusercontent.com/GuoXinsayhello/GuoXinsayhello.github.io/master/img/kibana6.png)
 
 ![image](https://raw.githubusercontent.com/GuoXinsayhello/GuoXinsayhello.github.io/master/img/kibana7.png)
  
 ![image](https://raw.githubusercontent.com/GuoXinsayhello/GuoXinsayhello.github.io/master/img/kibana8.png)

# ElasticSearch vs Solr 总结

1. Solr 利用 Zookeeper 进行分布式管理，而 Elasticsearch 自身带有分布式协调管理功能。
2. Solr 支持更多格式的数据，比如JSON、XML、CSV，而 Elasticsearch 仅支持json文件格式。
3. Solr 官方提供的功能更多，而 Elasticsearch 本身更注重于核心功能，高级功能多有第三方插件提供，例如图形化界面需要kibana友好支撑
4. Solr 查询快，但更新索引时慢（即插入删除慢）
5. ES建立索引快（即查询慢），即实时性查询快
6. Solr 是传统搜索应用的有力解决方案，但 Elasticsearch 更适用于新兴的实时搜索应用。
7. Solr比较成熟，有一个更大，更成熟的用户、开发和贡献者社区，而 Elasticsearch相对开发维护者较少，更新太快，学习使用成本较高。
  
  



- - -
  <p align="center">如果对你有帮助，请作者喝一杯牛奶吧</p>
     
 ![image](https://raw.githubusercontent.com/GuoXinsayhello/GuoXinsayhello.github.io/master/img/wepay.jpg)


