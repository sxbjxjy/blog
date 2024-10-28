---
layout: post
title: 给原创Form的String Control添加Lookup
date: 2022-05-08
category: Form
---

```csharp
public void lookup()
{
    Query query = new Query();
    QueryBuildDataSource queryBuildDataSource;
    QueryBuildRange queryBuildRange; 
    
    SysTableLookup sysTableLookup = SysTableLookup::newParameters(tableNum(custTable), this); 
    
    sysTableLookup.addLookupField(fieldNum(CustTable, AccountNum));
    sysTableLookup.addLookupField(fieldNum(CustTable, CustGroup)); 
    
    queryBuildDataSource = query.addDataSource(tableNum(CustTable));
    
    queryBuildRange = queryBuildDataSource.addRange(fieldNum(CustTable, CustGroup));
    queryBuildRange.value('40');
    
    sysTableLookup.parmQuery(query);
    
    sysTableLookup.performFormLookup();
    
    //super();
}
```
