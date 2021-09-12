# CDLA: A Chinese document layout analysis (CDLA) dataset

### 介绍

CDLA是一个中文文档版面分析数据集，面向中文文献类（论文）场景。包含以下10个label：

|正文|标题|图片|图片标题|表格|表格标题|页眉|页脚|注释|公式|
|---|---|---|---|---|---|---|---|---|---|
|Text|Title|Figure|Figure caption|Table|Table caption|Header|Footer|Reference|Equation|

共包含5000张训练集和1000张验证集，分别在train和val目录下。每张图片对应一个同名的标注文件(.json)。

样例展示：

![](https://github.com/buptlihang/CDLA/blob/master/imgs/show.png)

### 下载链接

- 百度云下载：https://pan.baidu.com/s/1449mhds2ze5JLk-88yKVAA, 提取码: tp0d

- Google Drive Download：https://drive.google.com/file/d/14SUsp_TG8OPdK0VthRXBcAbYzIBjSNLm/view?usp=sharing
### 标注格式

我们的标注工具是labelme，所以标注格式和labelme格式一致。

shapes字段是一个list，里面有多个dict，每个dict代表一个标注实例。

因为我们的标注是Polygon形式，所以points里的坐标数量可能大于4。


```
{
  "version":"4.5.6",
  "flags":{},
  "shapes":[
    {
      "label":"Header",
      "points":[
        [
          152.33333333333334,
          148.5
        ],
        [
          152.33333333333334,
          166.5
        ],
        [
          204.33333333333334,
          166.5
        ],
        [
          204.33333333333334,
          148.5
        ]
      ],
      "group_id":null,
      "shape_type":"polygon",
      "flags":{}
    },
    {
    ...
    },
    ...
  ]
  "imagePath":"val_0001.jpg",
  "imageData":null,
  "imageHeight":1754,
  "imageWidth":1240
}
```
