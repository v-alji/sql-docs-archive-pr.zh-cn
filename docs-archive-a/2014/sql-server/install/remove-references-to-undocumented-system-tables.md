---
title: 删除对未记录的系统表的引用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 45c38038ee3d3214e4303c0ddbe0110be926c37e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691511"
---
# <a name="remove-references-to-undocumented-system-tables"></a><span data-ttu-id="78559-102">删除对未记录的系统表的引用</span><span class="sxs-lookup"><span data-stu-id="78559-102">Remove references to undocumented system tables</span></span>
  <span data-ttu-id="78559-103">在早期版本中未记录的许多系统表都已更改或不再存在，因此，如果使用这些表，在升级可能会出现错误。</span><span class="sxs-lookup"><span data-stu-id="78559-103">Many system tables that were undocumented in prior releases have changed or no longer exist; therefore, using these tables may cause errors after upgrading.</span></span> <span data-ttu-id="78559-104">由于升级顾问查找的是针对系统表名称的引用，因而它将报告任何与系统表同名的用户表。</span><span class="sxs-lookup"><span data-stu-id="78559-104">Because Upgrade Advisor looks for references to system table names, it will report references to any user tables that have the same names as system tables.</span></span>  
  
## <a name="component"></a><span data-ttu-id="78559-105">组件</span><span class="sxs-lookup"><span data-stu-id="78559-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="78559-106">说明</span><span class="sxs-lookup"><span data-stu-id="78559-106">Description</span></span>  
 <span data-ttu-id="78559-107">删除了以下未记录的系统表：</span><span class="sxs-lookup"><span data-stu-id="78559-107">The following undocumented system tables are removed:</span></span>  
  
-   <span data-ttu-id="78559-108">**spt_datatype_info**</span><span class="sxs-lookup"><span data-stu-id="78559-108">**spt_datatype_info**</span></span>  
  
-   <span data-ttu-id="78559-109">**spt_datatype_info_ext**</span><span class="sxs-lookup"><span data-stu-id="78559-109">**spt_datatype_info_ext**</span></span>  
  
-   <span data-ttu-id="78559-110">**spt_provider_types**</span><span class="sxs-lookup"><span data-stu-id="78559-110">**spt_provider_types**</span></span>  
  
-   <span data-ttu-id="78559-111">**spt_server_info**</span><span class="sxs-lookup"><span data-stu-id="78559-111">**spt_server_info**</span></span>  
  
-   <span data-ttu-id="78559-112">**spt_values**</span><span class="sxs-lookup"><span data-stu-id="78559-112">**spt_values**</span></span>  
  
-   <span data-ttu-id="78559-113">**sysfulltextnotify**</span><span class="sxs-lookup"><span data-stu-id="78559-113">**sysfulltextnotify**</span></span>  
  
-   <span data-ttu-id="78559-114">**syslocks**</span><span class="sxs-lookup"><span data-stu-id="78559-114">**syslocks**</span></span>  
  
-   <span data-ttu-id="78559-115">**sysproperties**</span><span class="sxs-lookup"><span data-stu-id="78559-115">**sysproperties**</span></span>  
  
-   <span data-ttu-id="78559-116">**sysprotects_aux**</span><span class="sxs-lookup"><span data-stu-id="78559-116">**sysprotects_aux**</span></span>  
  
-   <span data-ttu-id="78559-117">**sysprotects_view**</span><span class="sxs-lookup"><span data-stu-id="78559-117">**sysprotects_view**</span></span>  
  
-   <span data-ttu-id="78559-118">**SYSREMOTE_CATALOGS**</span><span class="sxs-lookup"><span data-stu-id="78559-118">**SYSREMOTE_CATALOGS**</span></span>  
  
-   <span data-ttu-id="78559-119">**SYSREMOTE_COLUMN_PRIVILEGES**</span><span class="sxs-lookup"><span data-stu-id="78559-119">**SYSREMOTE_COLUMN_PRIVILEGES**</span></span>  
  
-   <span data-ttu-id="78559-120">**SYSREMOTE_COLUMNS**</span><span class="sxs-lookup"><span data-stu-id="78559-120">**SYSREMOTE_COLUMNS**</span></span>  
  
-   <span data-ttu-id="78559-121">**SYSREMOTE_FOREIGN_KEYS**</span><span class="sxs-lookup"><span data-stu-id="78559-121">**SYSREMOTE_FOREIGN_KEYS**</span></span>  
  
-   <span data-ttu-id="78559-122">**SYSREMOTE_INDEXES**</span><span class="sxs-lookup"><span data-stu-id="78559-122">**SYSREMOTE_INDEXES**</span></span>  
  
-   <span data-ttu-id="78559-123">**SYSREMOTE_PRIMARY_KEYS**</span><span class="sxs-lookup"><span data-stu-id="78559-123">**SYSREMOTE_PRIMARY_KEYS**</span></span>  
  
-   <span data-ttu-id="78559-124">**SYSREMOTE_PROVIDER_TYPES**</span><span class="sxs-lookup"><span data-stu-id="78559-124">**SYSREMOTE_PROVIDER_TYPES**</span></span>  
  
-   <span data-ttu-id="78559-125">**SYSREMOTE_SCHEMATA**</span><span class="sxs-lookup"><span data-stu-id="78559-125">**SYSREMOTE_SCHEMATA**</span></span>  
  
-   <span data-ttu-id="78559-126">**SYSREMOTE_STATISTICS**</span><span class="sxs-lookup"><span data-stu-id="78559-126">**SYSREMOTE_STATISTICS**</span></span>  
  
-   <span data-ttu-id="78559-127">**SYSREMOTE_TABLE_PRIVILEGES**</span><span class="sxs-lookup"><span data-stu-id="78559-127">**SYSREMOTE_TABLE_PRIVILEGES**</span></span>  
  
-   <span data-ttu-id="78559-128">**SYSREMOTE_TABLES**</span><span class="sxs-lookup"><span data-stu-id="78559-128">**SYSREMOTE_TABLES**</span></span>  
  
-   <span data-ttu-id="78559-129">**SYSREMOTE_VIEWS**</span><span class="sxs-lookup"><span data-stu-id="78559-129">**SYSREMOTE_VIEWS**</span></span>  
  
-   <span data-ttu-id="78559-130">**syssegments**</span><span class="sxs-lookup"><span data-stu-id="78559-130">**syssegments**</span></span>  
  
-   <span data-ttu-id="78559-131">**sysxlogins**</span><span class="sxs-lookup"><span data-stu-id="78559-131">**sysxlogins**</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="78559-132">纠正措施</span><span class="sxs-lookup"><span data-stu-id="78559-132">Corrective Action</span></span>  
 <span data-ttu-id="78559-133">按照下表修改应用程序。</span><span class="sxs-lookup"><span data-stu-id="78559-133">Modify your applications according to the following table.</span></span>  
  
|<span data-ttu-id="78559-134">不再使用</span><span class="sxs-lookup"><span data-stu-id="78559-134">Instead of</span></span>|<span data-ttu-id="78559-135">使用</span><span class="sxs-lookup"><span data-stu-id="78559-135">Use</span></span>|  
|----------------|---------|  
|<span data-ttu-id="78559-136">**sysfulltextnotify**</span><span class="sxs-lookup"><span data-stu-id="78559-136">**sysfulltextnotify**</span></span>|<span data-ttu-id="78559-137">OBJECTPROPERTYEX 函数的**TableFulltextPendingChanges**属性。</span><span class="sxs-lookup"><span data-stu-id="78559-137">**TableFulltextPendingChanges** property of the OBJECTPROPERTYEX function.</span></span>|  
|<span data-ttu-id="78559-138">**syslocks**</span><span class="sxs-lookup"><span data-stu-id="78559-138">**syslocks**</span></span>|<span data-ttu-id="78559-139">**sys. dm_tran_locks**动态管理视图、sp_lock 或**sys.syslockinfo**兼容性视图。</span><span class="sxs-lookup"><span data-stu-id="78559-139">**sys.dm_tran_locks** dynamic management view, or sp_lock, or the **sys.syslockinfo** compatibility view.</span></span>|  
|<span data-ttu-id="78559-140">**sysproperties**</span><span class="sxs-lookup"><span data-stu-id="78559-140">**sysproperties**</span></span>|<span data-ttu-id="78559-141">**sys. extended_properties**目录视图或**fn_listextendedproperty**函数</span><span class="sxs-lookup"><span data-stu-id="78559-141">**sys.extended_properties** catalog view or the **fn_listextendedproperty** function</span></span>|  
|<span data-ttu-id="78559-142">**sysxlogins**</span><span class="sxs-lookup"><span data-stu-id="78559-142">**sysxlogins**</span></span>|<span data-ttu-id="78559-143">**sys. server_principals**目录视图或**syslogins**兼容性视图。</span><span class="sxs-lookup"><span data-stu-id="78559-143">**sys.server_principals** catalog view or **syslogins** compatibility view.</span></span>|  
|<span data-ttu-id="78559-144">所有**spt_** 表</span><span class="sxs-lookup"><span data-stu-id="78559-144">all **spt_** tables</span></span>|<span data-ttu-id="78559-145">没有可以替换的表</span><span class="sxs-lookup"><span data-stu-id="78559-145">No replacement available</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78559-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78559-146">See Also</span></span>  
 <span data-ttu-id="78559-147">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="78559-147">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="78559-148">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="78559-148">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
