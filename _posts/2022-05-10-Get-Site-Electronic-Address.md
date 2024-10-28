---
layout: post
title: 取得工厂的电话、传真等电子联系方式
date: 2022-05-10
category: Other
---

```csharp
    /// <summary>
    /// Tel, Fax of Site
    /// </summary>
    /// <param name = "_siteRecId">Site RecId</param>
    /// <param name = "_type">Electronic Address Type</param>
    /// <returns>Electronic Address</returns>
    public LogisticsElectronicAddressLocator getSiteElectronicAddress(RecId _siteRecId, LogisticsElectronicAddressMethodType _type)
    {
        LogisticsElectronicAddressLocator   siteLocator;
        LogisticsLocationRecId              sitelocationRecId;
        LogisticsLocation                   logisticsLocation;

        sitelocationRecId = InventSite::getLocationFromRole(_siteRecId, LogisticsLocationRoleType::Delivery);
        logisticsLocation = LogisticsLocation::findElectronicLocationByParent(sitelocationRecId);
        siteLocator = LogisticsElectronicAddress::findByLocationAndType(logisticsLocation.RecId, _type).Locator;

        return siteLocator;
    }
```
