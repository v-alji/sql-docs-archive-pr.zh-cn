---
title: 系统数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system databases [SQL Server]
- displaying system database data
- modifying system data
- viewing system database data
ms.assetid: 30468a7c-4225-4d35-aa4a-ffa7da4f1282
author: stevestein
ms.author: sstein
ms.openlocfilehash: 65deee685c2205a7c6e41ed86f71c69639555d7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682865"
---
# <a name="system-databases"></a><span data-ttu-id="e9748-102">系统数据库</span><span class="sxs-lookup"><span data-stu-id="e9748-102">System Databases</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e9748-103">包含以下系统数据库。</span><span class="sxs-lookup"><span data-stu-id="e9748-103">includes the following system databases.</span></span>  
  
|<span data-ttu-id="e9748-104">系统数据库</span><span class="sxs-lookup"><span data-stu-id="e9748-104">System database</span></span>|<span data-ttu-id="e9748-105">说明</span><span class="sxs-lookup"><span data-stu-id="e9748-105">Description</span></span>|  
|---------------------|-----------------|  
|[<span data-ttu-id="e9748-106">master 数据库</span><span class="sxs-lookup"><span data-stu-id="e9748-106">master Database</span></span>](master-database.md)|<span data-ttu-id="e9748-107">记录 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的所有系统级信息。</span><span class="sxs-lookup"><span data-stu-id="e9748-107">Records all the system-level information for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="e9748-108">msdb 数据库</span><span class="sxs-lookup"><span data-stu-id="e9748-108">msdb Database</span></span>](msdb-database.md)|<span data-ttu-id="e9748-109">用于 SQL Server 代理计划警报和作业。</span><span class="sxs-lookup"><span data-stu-id="e9748-109">Is used by SQL Server Agent for scheduling alerts and jobs.</span></span>|  
|[<span data-ttu-id="e9748-110">model 数据库</span><span class="sxs-lookup"><span data-stu-id="e9748-110">model Database</span></span>](model-database.md)|<span data-ttu-id="e9748-111">用作 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上创建的所有数据库的模板。</span><span class="sxs-lookup"><span data-stu-id="e9748-111">Is used as the template for all databases created on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e9748-112">对 **model** 数据库进行的修改（如数据库大小、排序规则、恢复模式和其他数据库选项）将应用于以后创建的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="e9748-112">Modifications made to the **model** database, such as database size, collation, recovery model, and other database options, are applied to any databases created afterward.</span></span>|  
|[<span data-ttu-id="e9748-113">Resource 数据库</span><span class="sxs-lookup"><span data-stu-id="e9748-113">Resource Database</span></span>](resource-database.md)|<span data-ttu-id="e9748-114">一个只读数据库，包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]包括的系统对象。</span><span class="sxs-lookup"><span data-stu-id="e9748-114">Is a read-only database that contains system objects that are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e9748-115">系统对象在物理上保留在 **Resource** 数据库中，但在逻辑上显示在每个数据库的 **sys** 架构中。</span><span class="sxs-lookup"><span data-stu-id="e9748-115">System objects are physically persisted in the **Resource** database, but they logically appear in the **sys** schema of every database.</span></span>|  
|[<span data-ttu-id="e9748-116">tempdb 数据库</span><span class="sxs-lookup"><span data-stu-id="e9748-116">tempdb Database</span></span>](tempdb-database.md)|<span data-ttu-id="e9748-117">一个工作空间，用于保存临时对象或中间结果集。</span><span class="sxs-lookup"><span data-stu-id="e9748-117">Is a workspace for holding temporary objects or intermediate result sets.</span></span>|  
  
## <a name="modifying-system-data"></a><span data-ttu-id="e9748-118">修改系统数据</span><span class="sxs-lookup"><span data-stu-id="e9748-118">Modifying System Data</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e9748-119">不支持用户直接更新系统对象（如系统表、系统存储过程和目录视图）中的信息。</span><span class="sxs-lookup"><span data-stu-id="e9748-119">does not support users directly updating the information in system objects such as system tables, system stored procedures, and catalog views.</span></span> <span data-ttu-id="e9748-120">实际上， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供了一整套管理工具，用户可以使用这些工具充分管理他们的系统以及数据库中的所有用户和对象。</span><span class="sxs-lookup"><span data-stu-id="e9748-120">Instead, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a complete set of administrative tools that let users fully administer their system and manage all users and objects in a database.</span></span> <span data-ttu-id="e9748-121">其中包括：</span><span class="sxs-lookup"><span data-stu-id="e9748-121">These include the following:</span></span>  
  
-   <span data-ttu-id="e9748-122">管理实用工具，如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e9748-122">Administration utilities, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="e9748-123">SQL-SMO API。</span><span class="sxs-lookup"><span data-stu-id="e9748-123">SQL-SMO API.</span></span> <span data-ttu-id="e9748-124">此工具使程序员获得在其应用程序中管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的全部功能。</span><span class="sxs-lookup"><span data-stu-id="e9748-124">This lets programmers include complete functionality for administering [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in their applications.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="e9748-125">脚本和存储过程。</span><span class="sxs-lookup"><span data-stu-id="e9748-125">scripts and stored procedures.</span></span> <span data-ttu-id="e9748-126">它们可以使用系统存储过程和 [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 语句。</span><span class="sxs-lookup"><span data-stu-id="e9748-126">These can use system stored procedures and [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statements.</span></span>  
  
 <span data-ttu-id="e9748-127">这些工具保护应用程序不受系统对象更改的影响。</span><span class="sxs-lookup"><span data-stu-id="e9748-127">These tools shield applications from changes in the system objects.</span></span> <span data-ttu-id="e9748-128">例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 有时需要更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 新版本中的系统表，以支持添加到该版本中的新功能。</span><span class="sxs-lookup"><span data-stu-id="e9748-128">For example, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sometimes has to change the system tables in new versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support new functionality that is being added in that version.</span></span> <span data-ttu-id="e9748-129">但应用程序在发出直接引用系统表的 SELECT 语句时，通常依赖于旧的系统表格式。</span><span class="sxs-lookup"><span data-stu-id="e9748-129">Applications issuing SELECT statements that directly reference system tables are frequently dependent on the old format of the system tables.</span></span> <span data-ttu-id="e9748-130">站点可能在重写从系统表中进行选择的应用程序之后，才能升级到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新版本。</span><span class="sxs-lookup"><span data-stu-id="e9748-130">Sites may not be able to upgrade to a new version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until they have rewritten applications that are selecting from system tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e9748-131">考虑了系统存储过程、DDL 和 SQL-SMO 发布的接口，力求维持这些接口的向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="e9748-131">considers the system stored procedures, DDL, and SQL-SMO published interfaces, and works to maintain the backward compatibility of these interfaces.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e9748-132">不支持对系统表定义触发器，因为触发器可能会更改系统的操作。</span><span class="sxs-lookup"><span data-stu-id="e9748-132">does not support triggers defined on the system tables, because they might modify the operation of the system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e9748-133">系统数据库不能位于 UNC 共享目录中。</span><span class="sxs-lookup"><span data-stu-id="e9748-133">System databases cannot reside on UNC share directories.</span></span>  
  
## <a name="viewing-system-database-data"></a><span data-ttu-id="e9748-134">查看系统数据库数据</span><span class="sxs-lookup"><span data-stu-id="e9748-134">Viewing System Database Data</span></span>  
 <span data-ttu-id="e9748-135">不要编码直接查询系统表的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，除非这是获得应用程序所需信息的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="e9748-135">You should not code [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that directly query the system tables, unless that is the only way to obtain the information that is required by the application.</span></span> <span data-ttu-id="e9748-136">相反，应用程序应该通过使用以下方法获得目录和系统信息：</span><span class="sxs-lookup"><span data-stu-id="e9748-136">Instead, applications should obtain catalog and system information by using the following:</span></span>  
  
-   <span data-ttu-id="e9748-137">系统目录视图</span><span class="sxs-lookup"><span data-stu-id="e9748-137">System catalog views</span></span>  
  
-   <span data-ttu-id="e9748-138">SQL-SMO</span><span class="sxs-lookup"><span data-stu-id="e9748-138">SQL-SMO</span></span>  
  
-   <span data-ttu-id="e9748-139">Windows Management Instrumentation (WMI) 接口</span><span class="sxs-lookup"><span data-stu-id="e9748-139">Windows Management Instrumentation (WMI) interface</span></span>  
  
-   <span data-ttu-id="e9748-140">应用程序中使用的数据 API（如 ADO、OLE DB 或 ODBC）的目录函数、方法、特性或属性。</span><span class="sxs-lookup"><span data-stu-id="e9748-140">Catalog functions, methods, attributes, or properties of the data API used in the application, such as ADO, OLE DB, or ODBC.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="e9748-141">系统存储过程和内置函数。</span><span class="sxs-lookup"><span data-stu-id="e9748-141">system stored procedures and built-in functions.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e9748-142">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="e9748-142">Related Tasks</span></span>  
 [<span data-ttu-id="e9748-143">备份和还原系统数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9748-143">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [<span data-ttu-id="e9748-144">在对象资源管理器中隐藏系统对象</span><span class="sxs-lookup"><span data-stu-id="e9748-144">Hide System Objects in Object Explorer</span></span>](../../ssms/object/object-explorer.md)  
  
## <a name="related-content"></a><span data-ttu-id="e9748-145">相关内容</span><span class="sxs-lookup"><span data-stu-id="e9748-145">Related Content</span></span>  
 [<span data-ttu-id="e9748-146">目录视图 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e9748-146">Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
 [<span data-ttu-id="e9748-147">数据库</span><span class="sxs-lookup"><span data-stu-id="e9748-147">Databases</span></span>](databases.md)  
  
  
