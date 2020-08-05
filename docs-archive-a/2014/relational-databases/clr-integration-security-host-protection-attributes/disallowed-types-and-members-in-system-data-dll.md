---
title: System.Data.dll 中不允许的类型和成员 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
ms.openlocfilehash: cd62f6f0a90bd167f20a33f8de749acc982f39b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580299"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>System.Data.dll 中禁用的类型和成员
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]公共语言集成 (CLR) 编程不允许使用具有、、、、、、、 `HostProtectionAttribute` `System.Security.Permissions.HostProtectionResource` `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` **SharedState**、 `Synchronization` 或 `UI` 值指定枚举的类型或成员。 下表列出了宿主保护属性 (HPA) 值被禁用的 System.Data.dll 程序集的成员和类型。  
  
> [!NOTE]  
>  此列表是通过支持的程序集生成的。 有关详细信息，请参阅[支持的 .NET Framework 库](../clr-integration/database-objects/supported-net-framework-libraries.md)。  
  
|类型或成员|HPA 值|  
|--------------------|--------------------|  
|System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteReader()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency..ctor()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Start()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Stop()|ExternalThreading|  
|System.Data.TypedDataSetGenerator|SharedState, Synchronization|  
|System.Xml.XmlDataDocument|同步|  
  
## <a name="see-also"></a>另请参阅  
 [宿主保护属性和 CLR 集成编程](host-protection-attributes-and-clr-integration-programming.md)   
 [Microsoft.VisualBasic.dll中不允许的类型和成员](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [mscorlib.dll中不允许的类型和成员](disallowed-types-and-members-in-mscorlib-dll.md)   
 [System.dll中不允许的类型和成员](disallowed-types-and-members-in-system-dll.md)   
 [System.Core.dll 中禁用的类型和成员](disallowed-types-and-members-in-system-core-dll.md)  
  
  
