---
title: 查看已注册包的扩展事件目标 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- viewing event targets
- extended events [SQL Server], viewing targets
ms.assetid: 4985aa5f-ac99-49f6-852c-9d25916549e9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8e796d141ef943399fc2469c232b34b1956cef3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591508"
---
# <a name="view-the-extended-events-targets-for-registered-packages"></a><span data-ttu-id="62f33-102">查看已注册包的扩展事件目标</span><span class="sxs-lookup"><span data-stu-id="62f33-102">View the Extended Events Targets for Registered Packages</span></span>
  <span data-ttu-id="62f33-103">在创建 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 扩展事件会话之前，确定可用的扩展事件目标将非常有用。</span><span class="sxs-lookup"><span data-stu-id="62f33-103">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to determine what Extended Events targets are available.</span></span> <span data-ttu-id="62f33-104">若要完成此任务，需使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的查询编辑器执行以下过程。</span><span class="sxs-lookup"><span data-stu-id="62f33-104">This task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to perform the following procedure.</span></span>  
  
 <span data-ttu-id="62f33-105">此过程中的语句完成后，查询编辑器的 **“结果”** 选项卡将显示以下两列：</span><span class="sxs-lookup"><span data-stu-id="62f33-105">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following two columns:</span></span>  
  
-   <span data-ttu-id="62f33-106">package_name</span><span class="sxs-lookup"><span data-stu-id="62f33-106">package_name</span></span>  
  
-   <span data-ttu-id="62f33-107">target_name</span><span class="sxs-lookup"><span data-stu-id="62f33-107">target_name</span></span>  
  
## <a name="to-view-the-extended-events-targets-for-registered-packages-using-query-editor"></a><span data-ttu-id="62f33-108">使用查询编辑器查看已注册包的扩展事件目标</span><span class="sxs-lookup"><span data-stu-id="62f33-108">To view the Extended Events targets for registered packages using Query Editor</span></span>  
  
-   <span data-ttu-id="62f33-109">在查询编辑器中发出以下语句：</span><span class="sxs-lookup"><span data-stu-id="62f33-109">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    USE msdb  
    SELECT p.name package_name, o.name target_name  
    FROM sys.dm_xe_objects o  
    JOIN sys.dm_xe_packages p  
         ON o.package_guid = p.guid  
    WHERE o.object_type = 'target'  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="62f33-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62f33-110">See Also</span></span>  
 <span data-ttu-id="62f33-111">[SQL Server 扩展事件目标](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="62f33-111">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="62f33-112">[sys.dm_xe_objects (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="62f33-112">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="62f33-113">sys.dm_xe_packages (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="62f33-113">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
