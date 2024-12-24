---
layout: post
title: DataEntity在import时设定private field的值
date: 2024-12-23
categories: x++
---

通过DataEntity导入数据时，有一些private field的值，没有在数据的文件里指定，所以需要用代码来设定值，类似于在Table插入数据时的值自动设定。通过继承`mapEntityToDataSource()`来实现。

```csharp
    public void mapEntityToDataSource(DataEntityRuntimeContext _entityCtx, DataEntityDataSourceRuntimeContext _dataSourceCtx)
    {
        super(_entityCtx, _dataSourceCtx);

        if (_dataSourceCtx.name() == dataEntityDataSourceStr(XXX_DimensionAttributeEntity, XXX_DimensionAttribute))
        {
            XXX_DimensionAttributeEntity dimAttriEntity = _entityCtx.getEntityRecord();
            XXX_DimensionAttribute dimAttri = _dataSourceCtx.getBuffer();
            dimAttri.DimensionAttribute = DimensionAttribute::findByName(this.DimensionAttributeName).RecId;
        }
    }
```

**参考资料**

[D365FO – AX – Update Data Entity Target Entity fields with X++](https://d365ffo.com/2021/05/07/d365ffo-ax-update-data-entity-target-entity-fields-with-x/comment-page-1/){:target="_blank"}
