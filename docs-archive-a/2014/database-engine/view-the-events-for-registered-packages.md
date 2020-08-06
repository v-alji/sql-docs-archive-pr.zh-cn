---
title: 查看已注册包的事件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing events
- extended events [SQL Server], viewing events
ms.assetid: 9a90b1a2-aa69-43f6-bdeb-cc5f57a26c6f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5e3665a695bd3f40407a8680872c9b0dc79fbc53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591509"
---
# <a name="view-the-events-for-registered-packages"></a><span data-ttu-id="716bf-102">查看已注册包的事件</span><span class="sxs-lookup"><span data-stu-id="716bf-102">View the Events for Registered Packages</span></span>
  <span data-ttu-id="716bf-103">创建 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 扩展事件会话之前，找到注册包中可用的事件非常有用。</span><span class="sxs-lookup"><span data-stu-id="716bf-103">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to find out what events are available in the registered packages.</span></span> <span data-ttu-id="716bf-104">有关详细信息，请参阅 [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="716bf-104">For more information, see [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).</span></span>  
  
 <span data-ttu-id="716bf-105">若要完成此任务，需使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的查询编辑器执行以下过程。</span><span class="sxs-lookup"><span data-stu-id="716bf-105">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span>  
  
 <span data-ttu-id="716bf-106">此过程中的语句完成后，查询编辑器的 **“结果”** 选项卡将显示以下列：</span><span class="sxs-lookup"><span data-stu-id="716bf-106">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:</span></span>  
  
-   <span data-ttu-id="716bf-107">名称。</span><span class="sxs-lookup"><span data-stu-id="716bf-107">name.</span></span> <span data-ttu-id="716bf-108">包名称。</span><span class="sxs-lookup"><span data-stu-id="716bf-108">The package name.</span></span>  
  
-   <span data-ttu-id="716bf-109">事件。</span><span class="sxs-lookup"><span data-stu-id="716bf-109">event.</span></span> <span data-ttu-id="716bf-110">事件名称。</span><span class="sxs-lookup"><span data-stu-id="716bf-110">The event name.</span></span>  
  
-   <span data-ttu-id="716bf-111">关键字</span><span class="sxs-lookup"><span data-stu-id="716bf-111">keyword.</span></span> <span data-ttu-id="716bf-112">从内部数值映射表派生的关键字。</span><span class="sxs-lookup"><span data-stu-id="716bf-112">A keyword derived from an internal numeric mapping table.</span></span>  
  
-   <span data-ttu-id="716bf-113">渠道。</span><span class="sxs-lookup"><span data-stu-id="716bf-113">channel.</span></span> <span data-ttu-id="716bf-114">事件的用户。</span><span class="sxs-lookup"><span data-stu-id="716bf-114">The audience for an event.</span></span>  
  
-   <span data-ttu-id="716bf-115">说明。</span><span class="sxs-lookup"><span data-stu-id="716bf-115">description.</span></span> <span data-ttu-id="716bf-116">事件说明。</span><span class="sxs-lookup"><span data-stu-id="716bf-116">The event description.</span></span>  
  
## <a name="to-view-the-events-for-registered-packages-using-query-editor"></a><span data-ttu-id="716bf-117">使用查询编辑器查看已注册包的事件</span><span class="sxs-lookup"><span data-stu-id="716bf-117">To view the events for registered packages using Query Editor</span></span>  
  
-   <span data-ttu-id="716bf-118">在查询编辑器中发出以下语句：</span><span class="sxs-lookup"><span data-stu-id="716bf-118">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    USE msdb  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
    (  
    SELECT event_package=o.package_guid, o.description,   
    event=c.object_name, channel=v.map_value  
    FROM sys.dm_xe_objects o  
    LEFT JOIN sys.dm_xe_object_columns c ON o.name=c.object_name  
    INNER JOIN sys.dm_xe_map_values v ON c.type_name=v.name   
    AND c.column_value=cast(v.map_key AS nvarchar)  
    WHERE object_type='event' AND (c.name='CHANNEL' or c.name IS NULL)  
  
    ) c LEFT JOIN   
    (  
    SELECT event_package=c.object_package_guid, event=c.object_name,   
    keyword=v.map_value  
    FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
    ON c.type_name=v.name AND c.column_value=v.map_key   
    AND c.type_package_guid=v.object_package_guid  
    INNER JOIN sys.dm_xe_objects o ON o.name=c.object_name   
    AND o.package_guid=c.object_package_guid  
    WHERE object_type='event' AND c.name='KEYWORD'   
    ) k  
    ON  
    k.event_package=c.event_package AND (k.event=c.event or k.event IS NULL)  
    INNER JOIN sys.dm_xe_packages p ON p.guid=c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="716bf-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="716bf-119">See Also</span></span>  
 <span data-ttu-id="716bf-120">[SQL Server 扩展事件包](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span><span class="sxs-lookup"><span data-stu-id="716bf-120">[SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span></span>  
 <span data-ttu-id="716bf-121">[sys.dm_xe_objects (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="716bf-121">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="716bf-122">sys.dm_xe_packages (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="716bf-122">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
