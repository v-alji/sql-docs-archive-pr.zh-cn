---
title: 修改应用程序，使其 sysperfinfo 中出现 bigint 值。 cntr_value |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 108a9b981debc95e182b16847c39a03d4b242088
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693186"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntr_value"></a>修改应用程序以期望从 sysperfinfo.cntr_value 获取 bigint 值
  sysperfinfo `bigint` 为 cntr_value 列返回值。  
  
## <a name="component"></a>组件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>纠正措施  
 请修改使用 sysperfinfo 的应用程序，确保它们可以处理 cntr_value 列的 `bigint` 值。  
  
> [!NOTE]  
>  sysperfinfo 是一个兼容性视图。 应改用 sys.dm_os_performance_counter 动态管理视图。  
  
## <a name="see-also"></a>另请参阅  
 [数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 升级顾问 &#91;新&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
