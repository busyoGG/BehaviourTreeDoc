# 快速开始

## 简介

混合驱动的行为树。通过解析行为树 Json 数据进行行为树的构建。

## 使用

### 反序列化数据

```C#
SaveJson json = ConfigLoader.Load(path);
```

### 创建行为树

```C#
BhBaseNode root = TreeManager.Ins().InitBHNode(json);
```

### 运行行为树

运行行为树的时机可以是轮询，也可以是事件驱动等其他方式。

传入的节点一定是根节点，行为树管理类会根据节点运行的状态自动选择运行的节点。

```C#
TreeManager.Ins().Run(root);
```

## 行为树 Json 数据案例

> type 项为 GraphViewExtension 中创建节点需要的参数。<br>
> data 项为实际行为树数据，其中 guid、pos、size、desc 为 GraphViewExtension 初始化节点需要的参数。<br>
> children 项为子节点。

```json
[
  {
    "children": [
      {
        "children": [
          {
            "children": [],
            "data": {
              "guid": "15fb6edb82c92324e9e185f4c39fa4ba",
              "pos": "(599.00, 462.00)",
              "size": "(200.00, 142.00)",
              "node": "ANodeTest",
              "isSuc": false,
              "desc": "测试节点失败"
            },
            "type": "GraphViewExtension.ANodeTest"
          },
          {
            "children": [],
            "data": {
              "guid": "6e35a56ed5170804dbc6930776c2109d",
              "pos": "(599.00, 286.00)",
              "size": "(200.00, 138.00)",
              "node": "ANodeWait",
              "desc": "延时节点",
              "time": 1538
            },
            "type": "GraphViewExtension.ANodeWait"
          },
          {
            "children": [],
            "data": {
              "guid": "55ecdbc145e92094383246a89072a03a",
              "pos": "(599.00, 111.00)",
              "size": "(200.00, 142.00)",
              "node": "ANodeTest",
              "isSuc": true,
              "desc": "测试节点成功"
            },
            "type": "GraphViewExtension.ANodeTest"
          }
        ],
        "data": {
          "guid": "925a1f117afb5214e94ebe1bca57212a",
          "pos": "(293.00, 234.00)",
          "size": "(200.00, 121.00)",
          "node": "CNodeSelect"
        },
        "type": "GraphViewExtension.CNodeSelect"
      },
      {
        "children": [],
        "data": {
          "guid": "207185d6ee6a55f4292b01162d42614a",
          "pos": "(306.00, 49.00)",
          "size": "(200.00, 100.00)",
          "node": "DNodeFail"
        },
        "type": "GraphViewExtension.DNodeFail"
      }
    ],
    "data": {
      "guid": "ab1dc5fe007748c4e83865ddf11a61a8",
      "pos": "(21.00, 149.00)",
      "size": "(200.00, 121.00)",
      "node": "CNodeSelect"
    },
    "type": "GraphViewExtension.CNodeSelect"
  }
]
```
