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

我们的标注工具是labelme，所以标注格式和labelme格式一致。这里说明一下比较重要的字段。

"shapes": shapes字段是一个list，里面有多个dict，每个dict代表一个标注实例。

  "labels": 类别。

  "points": 实例标注。因为我们的标注是Polygon形式，所以points里的坐标数量可能大于4。

  "shape_type": "polygon"

"imagePath": 图片路径/名

"imageHeight": 高

"imageWidth": 宽

展示一个完整的标注样例:

```
{
  "version":"4.5.6",
  "flags":{},
  "shapes":[
    {
      "label":"Title",
      "points":[
        [
          553.1111111111111,
          166.59259259259258
        ],
        [
          553.1111111111111,
          198.59259259259258
        ],
        [
          686.1111111111111,
          198.59259259259258
        ],
        [
          686.1111111111111,
          166.59259259259258
        ]
      ],
      "group_id":null,
      "shape_type":"polygon",
      "flags":{}
    },
    {
      "label":"Text",
      "points":[
        [
          250.5925925925925,
          298.0740740740741
        ],
        [
          250.5925925925925,
          345.0740740740741
        ],
        [
          188.5925925925925,
          345.0740740740741
        ],
        [
          188.5925925925925,
          410.0740740740741
        ],
        [
          188.5925925925925,
          456.0740740740741
        ],
        [
          324.5925925925925,
          456.0740740740741
        ],
        [
          324.5925925925925,
          410.0740740740741
        ],
        [
          1051.5925925925926,
          410.0740740740741
        ],
        [
          1051.5925925925926,
          345.0740740740741
        ],
        [
          1052.5925925925926,
          345.0740740740741
        ],
        [
          1052.5925925925926,
          298.0740740740741
        ]
      ],
      "group_id":null,
      "shape_type":"polygon",
      "flags":{}
    },
    {
      "label":"Footer",
      "points":[
        [
          1033.7407407407406,
          1634.5185185185185
        ],
        [
          1033.7407407407406,
          1646.5185185185185
        ],
        [
          1052.7407407407406,
          1646.5185185185185
        ],
        [
          1052.7407407407406,
          1634.5185185185185
        ]
      ],
      "group_id":null,
      "shape_type":"polygon",
      "flags":{}
    }
  ],
  "imagePath":"val_0031.jpg",
  "imageData":null,
  "imageHeight":1754,
  "imageWidth":1240
}
```

### 转coco格式

执行命令:

```
# train
python3 labelme2coco.py CDLA_dir/train train_save_path  --labels labels.txt

# val
python3 labelme2coco.py CDLA_dir/val val_save_path  --labels labels.txt
```

转换结果保存在train_save_path/val_save_path目录下。

