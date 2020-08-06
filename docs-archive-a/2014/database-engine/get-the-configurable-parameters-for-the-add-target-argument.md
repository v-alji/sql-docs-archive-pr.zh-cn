---
title: 获取 ADD TARGET 参数的可配置参数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], ADD TARGET argument
- xe
ms.assetid: 08454543-c5c8-4ca3-9af9-f1d82264471c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 30644bc30c0bd8c4ccbc17c616c6f24bf9455dc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690041"
---
# <a name="get-the-configurable-parameters-for-the-add-target-argument"></a><span data-ttu-id="d950e-102">获取 ADD TARGET 实参的可配置形参</span><span class="sxs-lookup"><span data-stu-id="d950e-102">Get the Configurable Parameters for the ADD TARGET Argument</span></span>
  <span data-ttu-id="d950e-103">完成此任务涉及在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中使用查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="d950e-103">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d950e-104">此过程中的语句完成后，查询编辑器的 **“结果”** 选项卡将显示以下列：</span><span class="sxs-lookup"><span data-stu-id="d950e-104">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:</span></span>  
  
-   <span data-ttu-id="d950e-105">package_name</span><span class="sxs-lookup"><span data-stu-id="d950e-105">package_name</span></span>  
  
-   <span data-ttu-id="d950e-106">target_name</span><span class="sxs-lookup"><span data-stu-id="d950e-106">target_name</span></span>  
  
-   <span data-ttu-id="d950e-107">parameter_name</span><span class="sxs-lookup"><span data-stu-id="d950e-107">parameter_name</span></span>  
  
-   <span data-ttu-id="d950e-108">parameter_type</span><span class="sxs-lookup"><span data-stu-id="d950e-108">parameter_type</span></span>  
  
-   <span data-ttu-id="d950e-109">必需</span><span class="sxs-lookup"><span data-stu-id="d950e-109">required</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d950e-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="d950e-110">Before You Begin</span></span>  
 <span data-ttu-id="d950e-111">创建 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 扩展事件会话之前，找到在 CREATE EVENT SESSION 或 ALTER EVENT SESSION 中使用 ADD TARGET 参数时可设置的参数将非常有用。</span><span class="sxs-lookup"><span data-stu-id="d950e-111">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to find out what parameters you can set when you use the ADD TARGET argument in CREATE EVENT SESSION or ALTER EVENT SESSION.</span></span>  
  
### <a name="to-get-the-configurable-parameters-for-the-add-target-argument-using-query-editor"></a><span data-ttu-id="d950e-112">使用查询编辑器获取 ADD TARGET 实参的可配置形参</span><span class="sxs-lookup"><span data-stu-id="d950e-112">To get the configurable parameters for the ADD TARGET argument using Query Editor</span></span>  
  
-   <span data-ttu-id="d950e-113">在查询编辑器中发出以下语句：</span><span class="sxs-lookup"><span data-stu-id="d950e-113">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    SELECT p.name package_name, o.name target_name, c.name parameter_name,   
    c.type_name parameter_type, CASE c.capabilities_desc WHEN 'mandatory' THEN 'yes' ELSE 'no' END   
    required   
    FROM sys.dm_xe_objects o JOIN sys.dm_xe_packages p ON o.package_guid = p.guid   
    JOIN sys.dm_xe_object_columns c ON o.name = c.object_name AND c.column_type = 'customizable'  
    WHERE o.object_type = 'target'   
    ORDER BY package_name, target_name, required DESC  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d950e-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d950e-114">See Also</span></span>  
 <span data-ttu-id="d950e-115">[CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d950e-115">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 <span data-ttu-id="d950e-116">[ALTER EVENT SESSION &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d950e-116">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span></span>  
 <span data-ttu-id="d950e-117">[sys.dm_xe_objects (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d950e-117">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="d950e-118">sys.dm_xe_packages (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d950e-118">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  