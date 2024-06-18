# 拓展

## 行为树节点

行为树节点主要拓展五个重写方法。

### Init

初始化节点数据，这里的数据是通过反序列化得到的行为树节点的数据，dynamic（ExpandoObject）类型。

```C# 测试节点案例
private bool _res;

public override void Init(dynamic data)
{
    _res = data.isSuc;
}
```

### Run

节点运行逻辑。

```C# 反向节点案例
public override void Run()
{
    switch (result)
    {
        case BhResult.Fail:
            SetResult(BhResult.Success);
            break;
        case BhResult.Success:
            SetResult(BhResult.Fail);
            break;
    }
}
```

### CheckState

检测子节点的状态是否允许本节点继续向后执行。

```C# 选择节点案例
public override bool CheckState(BhResult res)
{
    if (res == BhResult.Success || res == BhResult.Running)
    {
        return false;
    }

    return true;
}
```

### CheckStop

检测本节点是否运行完毕。

```C# 选择节点案例
public override bool CheckStop()
{
    if (currentChildIndex >= children.Count || result == BhResult.Success)
    {
        return true;
    }

    return false;
}
```

### Reset

重置节点数据。重写的时候一定要调用 `base.Reset()`。

```C# 等待节点案例
public override void Reset()
{
    base.Reset();
    _curTime = 0;
    _defTime = -1;
}
```

## 行为树 Json 反序列化

反序列化目前只做了常规的 `string` 、 `float` 、 `bool` 、`int` 类型转换，如果有更多类型可以拓展 `ConfigLoader` 的 `Deserialize` 方法。
