---
title: SQL Server 资源运行状况故障排除（SQL Server 实用工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 182225dd618dd1e9e058c549bdc07818813ba764
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578878"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a><span data-ttu-id="69632-102">SQL Server 资源运行状况故障排除（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="69632-102">Troubleshoot SQL Server Resource Health (SQL Server Utility)</span></span>
  <span data-ttu-id="69632-103">排除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP 标识的资源运行状况问题可能包括缓解计算机上或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例上使用过度的 CPU，或者缓解数据层应用程序的使用过度的 CPU。</span><span class="sxs-lookup"><span data-stu-id="69632-103">Troubleshooting resource health issues identified by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP might include mitigating overutilized CPU on a computer or on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or mitigating overutilized CPU for a data-tier application.</span></span> <span data-ttu-id="69632-104">其他问题可能包括解决数据库文件的使用过度的文件空间或者解决存储卷上分配的磁盘空间的使用过度问题。</span><span class="sxs-lookup"><span data-stu-id="69632-104">Other issues might include resolving overutilized file space for database files or resolving overutilization of allocated disk space on a storage volume.</span></span>  
  
 <span data-ttu-id="69632-105">注意，如果数据库处于“紧急”状态，则运行状态将显示日志文件空间使用过度。</span><span class="sxs-lookup"><span data-stu-id="69632-105">Note that if a database is in "emergency" state, the health state will display overutilized log file space.</span></span>  
  
 <span data-ttu-id="69632-106">有关导致 UCP 上托管实例列表视图中灰色状态图标的失败的数据收集的详细信息，请参阅 [SQL Server 实用工具故障排除](../../database-engine/troubleshoot-the-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="69632-106">For more information about failed data collection resulting in gray status icons in the managed instance list view on a UCP, see [Troubleshoot the SQL Server Utility](../../database-engine/troubleshoot-the-sql-server-utility.md).</span></span> <span data-ttu-id="69632-107">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具入门的详细信息，请参阅 [SQL Server 实用工具功能和任务](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="69632-107">For more information about getting started with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
 <span data-ttu-id="69632-108">有关缓解 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP 标识的特定资源运行状况问题的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="69632-108">For more information about mitigating specific resource health issues identified by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP, see the following topics:</span></span>  
  
-   [<span data-ttu-id="69632-109">如何识别 SQL Server 的版本</span><span class="sxs-lookup"><span data-stu-id="69632-109">How to identify your SQL Server version and edition</span></span>](https://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [<span data-ttu-id="69632-110">排除 SQL Server 2008 中的性能问题</span><span class="sxs-lookup"><span data-stu-id="69632-110">Troubleshooting Performance Problems in SQL Server 2008</span></span>](https://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
