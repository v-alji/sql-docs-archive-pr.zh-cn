---
title: DatabaseLogonAccount 属性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonAccount
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonAccount property
ms.assetid: 55f2863f-1ac1-4519-b512-e7f11c0ea5ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f9e844ff1d1447bd5abfefad8e82939575c7f47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692172"
---
# <a name="databaselogonaccount-property-wmi-msreportserver_configurationsetting"></a>DatabaseLogonAccount 属性 (WMI MSReportServer_ConfigurationSetting)
  指定报表服务器连接到报表服务器数据库时使用的登录帐户。 只读。  
  
## <a name="syntax"></a>语法  
  
```vb  
Public Dim DatabaseLogonAccount As String  
```  
  
```csharp  
public string DatabaseLogonAccount;  
```  
  
## <a name="property-values"></a>属性值  
 表示登录帐户名的 `String` 对象。  
  
## <a name="example-code"></a>示例代码  
 [MSReportServer_ConfigurationSetting 类](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>备注  
 此属性的有效值将因 [DatabaseLogonType](configurationsetting-property-databaselogontype.md) 属性的值而异。  
  
 如果[DatabaseLogonType](configurationsetting-property-databaselogontype.md)属性设置为，则忽略此属性 `2 (Service)` 。  
  
## <a name="requirements"></a>要求  
 **命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [MSReportServer_ConfigurationSetting 成员](msreportserver-configurationsetting-members.md)  
  
  
