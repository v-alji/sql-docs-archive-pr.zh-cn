---
title: 获取所有事件的字段 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], getting fields
- xe
ms.assetid: 4e4ee03f-5bca-42ed-a37c-db1c82e3aad2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 01d98e827121a0c47111dd601c6e1772f796849d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690037"
---
# <a name="get-the-fields-for-all-events"></a><span data-ttu-id="7e8e5-102">获取所有事件的字段</span><span class="sxs-lookup"><span data-stu-id="7e8e5-102">Get the Fields for All Events</span></span>
  <span data-ttu-id="7e8e5-103">完成此任务涉及在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中使用查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="7e8e5-103">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="7e8e5-104">此过程中的语句完成后，查询编辑器的 **“结果”** 选项卡将显示以下列：</span><span class="sxs-lookup"><span data-stu-id="7e8e5-104">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:</span></span>  
  
-   <span data-ttu-id="7e8e5-105">package_name</span><span class="sxs-lookup"><span data-stu-id="7e8e5-105">package_name</span></span>  
  
-   <span data-ttu-id="7e8e5-106">event_name</span><span class="sxs-lookup"><span data-stu-id="7e8e5-106">event_name</span></span>  
  
-   <span data-ttu-id="7e8e5-107">event_field</span><span class="sxs-lookup"><span data-stu-id="7e8e5-107">event_field</span></span>  
  
-   <span data-ttu-id="7e8e5-108">field_type</span><span class="sxs-lookup"><span data-stu-id="7e8e5-108">field_type</span></span>  
  
-   <span data-ttu-id="7e8e5-109">column_type</span><span class="sxs-lookup"><span data-stu-id="7e8e5-109">column_type</span></span>  
  
 <span data-ttu-id="7e8e5-110">当配置使用存入桶目标的事件会话时，可以使用上述信息。</span><span class="sxs-lookup"><span data-stu-id="7e8e5-110">You can use the preceding information when configuring event sessions that use the bucketing target.</span></span> <span data-ttu-id="7e8e5-111">有关详细信息，请参阅 [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md)。</span><span class="sxs-lookup"><span data-stu-id="7e8e5-111">For more information, see [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="7e8e5-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="7e8e5-112">Before you Begin</span></span>  
 <span data-ttu-id="7e8e5-113">创建 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 扩展事件会话之前，获取有关事件关联字段的信息将非常有用。</span><span class="sxs-lookup"><span data-stu-id="7e8e5-113">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to get information about the fields associated with events.</span></span>  
  
## <a name="to-get-the-fields-for-all-events-using-query-editor"></a><span data-ttu-id="7e8e5-114">使用查询编辑器获取所有事件的字段</span><span class="sxs-lookup"><span data-stu-id="7e8e5-114">To get the fields for all events using Query Editor</span></span>  
  
-   <span data-ttu-id="7e8e5-115">在查询编辑器中发出以下语句：</span><span class="sxs-lookup"><span data-stu-id="7e8e5-115">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    select p.name package_name, o.name event_name, c.name event_field, c.type_name field_type, c.column_type column_type  
    from sys.dm_xe_objects o  
    join sys.dm_xe_packages p  
          on o.package_guid = p.guid  
    join sys.dm_xe_object_columns c  
          on o.name = c.object_name  
    where o.object_type = 'event'  
    order by package_name, event_name  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7e8e5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e8e5-116">See Also</span></span>  
 <span data-ttu-id="7e8e5-117">[sys.dm_xe_objects (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e8e5-117">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="7e8e5-118">sys.dm_xe_packages (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e8e5-118">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
