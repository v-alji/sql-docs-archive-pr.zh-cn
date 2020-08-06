---
title: 未联接辅助数据库 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp2joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 10817e5e-75fa-42dd-baa2-359bea3ad051
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81275e85fd865924778f6d6f985e170a5bda9f9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693103"
---
# <a name="secondary-database-is-not-joined"></a>未联接辅助数据库
    
## <a name="introduction"></a>简介  
  
|||  
|-|-|  
|**策略名称**|可用性数据库联接状态|  
|**问题**|未联接辅助数据库。|  
|**类别**|**警告**|  
|**方面**|可用性数据库|  
  
## <a name="description"></a>说明  
 此策略检查辅助数据库（也称为“辅助数据库副本”）的联接状态。 数据集副本未联接时，此策略处于不正常状态。 否则，该策略处于正常状态。  
  
> [!NOTE]  
>  对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [未联接辅助数据库](https://go.microsoft.com/fwlink/p/?LinkId=220862) 中。  
  
## <a name="possible-causes"></a>可能的原因  
 此辅助数据库未联接到可用性组。 此辅助数据库的配置不完整。  
  
## <a name="possible-solution"></a>可能的解决方法  
 使用 Transact-SQL、PowerShell 或 SQL Server Management Studio 将辅助副本联接到可用性组。 有关将辅助副本联接到可用性组的详细信息，请参阅 [将辅助副本联接到可用性组 (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx)。  
  
## <a name="see-also"></a>另请参阅  
 [AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [使用 AlwaysOn 面板 (SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
