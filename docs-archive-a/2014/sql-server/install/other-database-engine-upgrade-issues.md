---
title: 其他数据库引擎升级问题 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], upgrading
ms.assetid: 78a1d8e8-fa97-476f-8777-84617d145340
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: db496112fc975304bb2d7da9d9ea1c52e6dd8bec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579961"
---
# <a name="other-database-engine-upgrade-issues"></a><span data-ttu-id="cc76b-102">其他数据库引擎升级问题</span><span class="sxs-lookup"><span data-stu-id="cc76b-102">Other Database Engine Upgrade Issues</span></span>
  <span data-ttu-id="cc76b-103">升级顾问的当前版本无法检测到以下升级问题。</span><span class="sxs-lookup"><span data-stu-id="cc76b-103">The following upgrade issues cannot be detected by the current version of Upgrade Advisor.</span></span> <span data-ttu-id="cc76b-104">请检查以下列出的问题来评估它们对系统的潜在影响。</span><span class="sxs-lookup"><span data-stu-id="cc76b-104">Review the issues listed below to evaluate their potential impact to your systems.</span></span>  
  
## <a name="multiple-database-engine-deprecated-features"></a><span data-ttu-id="cc76b-105">不推荐使用的多数据库引擎功能</span><span class="sxs-lookup"><span data-stu-id="cc76b-105">Multiple Database Engine Deprecated Features</span></span>  
 <span data-ttu-id="cc76b-106">不推荐使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句或选项：</span><span class="sxs-lookup"><span data-stu-id="cc76b-106">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or options are deprecated:</span></span>  
  
-   <span data-ttu-id="cc76b-107">BACKUP LOG 的 NO_LOG 和 TRUNCATE_ONLY 选项</span><span class="sxs-lookup"><span data-stu-id="cc76b-107">NO_LOG and TRUNCATE_ONLY options of BACKUP LOG</span></span>  
  
-   <span data-ttu-id="cc76b-108">BACKUP TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="cc76b-108">BACKUP TRANSACTION</span></span>  
  
-   <span data-ttu-id="cc76b-109">RESTORE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="cc76b-109">RESTORE TRANSACTION</span></span>  
  
-   <span data-ttu-id="cc76b-110">DUMP</span><span class="sxs-lookup"><span data-stu-id="cc76b-110">DUMP</span></span>  
  
-   <span data-ttu-id="cc76b-111">LOAD</span><span class="sxs-lookup"><span data-stu-id="cc76b-111">LOAD</span></span>  
  
-   <span data-ttu-id="cc76b-112">DBCC CONCURRENCYVIOLATION</span><span class="sxs-lookup"><span data-stu-id="cc76b-112">DBCC CONCURRENCYVIOLATION</span></span>  
  
-   <span data-ttu-id="cc76b-113">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="cc76b-113">sp_addalias</span></span>  
  
-   <span data-ttu-id="cc76b-114">sp_addgroup</span><span class="sxs-lookup"><span data-stu-id="cc76b-114">sp_addgroup</span></span>  
  
-   <span data-ttu-id="cc76b-115">sp_changegroup</span><span class="sxs-lookup"><span data-stu-id="cc76b-115">sp_changegroup</span></span>  
  
-   <span data-ttu-id="cc76b-116">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="cc76b-116">sp_dropgroup</span></span>  
  
-   <span data-ttu-id="cc76b-117">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="cc76b-117">sp_helpgroup</span></span>  
  
-   <span data-ttu-id="cc76b-118">syssegments</span><span class="sxs-lookup"><span data-stu-id="cc76b-118">syssegments</span></span>  
  
 <span data-ttu-id="cc76b-119">不推荐使用 VIA 协议连接到[!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cc76b-119">Use of the VIA protocol to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is deprecated.</span></span>  
  
## <a name="new-data-types"></a><span data-ttu-id="cc76b-120">新数据类型</span><span class="sxs-lookup"><span data-stu-id="cc76b-120">New Data Types</span></span>  
 <span data-ttu-id="cc76b-121">以下类型将是保留的系统类型。</span><span class="sxs-lookup"><span data-stu-id="cc76b-121">The following will be reserved system types.</span></span> <span data-ttu-id="cc76b-122">请在升级之前或之后重命名会产生冲突的现有用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="cc76b-122">Rename the existing conflicting user defined types either before or after upgrade.</span></span>  
  
-   <span data-ttu-id="cc76b-123">地理位置</span><span class="sxs-lookup"><span data-stu-id="cc76b-123">Geography</span></span>  
  
-   <span data-ttu-id="cc76b-124">几何图形</span><span class="sxs-lookup"><span data-stu-id="cc76b-124">Geometry</span></span>  
  
-   <span data-ttu-id="cc76b-125">Datetime2</span><span class="sxs-lookup"><span data-stu-id="cc76b-125">Datetime2</span></span>  
  
-   <span data-ttu-id="cc76b-126">HierarchyID</span><span class="sxs-lookup"><span data-stu-id="cc76b-126">HierarchyID</span></span>  
  
## <a name="target-table-of-the-output-into-clause-cannot-have-any-defined-triggers"></a><span data-ttu-id="cc76b-127">OUTPUT INTO 子句的目标表不能包含任何定义的触发器</span><span class="sxs-lookup"><span data-stu-id="cc76b-127">Target Table of the OUTPUT INTO Clause Cannot Have Any Defined Triggers</span></span>  
 <span data-ttu-id="cc76b-128">当表具有任何已启用的触发器时，输出到目标表中。</span><span class="sxs-lookup"><span data-stu-id="cc76b-128">OUTPUT INTO a target table when the table has any enabled triggers is not supported.</span></span>  
  
## <a name="compile-time-error-for-udfs-when-the-target-of-an-output-into-clause-is-a-table"></a><span data-ttu-id="cc76b-129">当 OUTPUT INTO 子句的目标是表时发生 UDF 编译时错误</span><span class="sxs-lookup"><span data-stu-id="cc76b-129">Compile Time Error for UDFs When the Target of an OUTPUT INTO Clause is a Table</span></span>  
 <span data-ttu-id="cc76b-130">用户定义函数 (UDF) 不能用于执行修改数据库状态的操作。</span><span class="sxs-lookup"><span data-stu-id="cc76b-130">User-defined functions (UDF) cannot be used to perform actions that modify the database state.</span></span> <span data-ttu-id="cc76b-131">例如，UDF 无法对任何对象（表变量除外）执行任何 DDL (CREATE/ALTER/DROP) 或 DML (INSERT/UPDATE/DELETE) 操作。</span><span class="sxs-lookup"><span data-stu-id="cc76b-131">For example, a UDF cannot perform any DDL (CREATE/ALTER/DROP) or DML (INSERT/UPDATE/DELETE) actions on any objects, except for table variables.</span></span>  
  
## <a name="merge-is-a-reserved-keyword"></a><span data-ttu-id="cc76b-132">MERGE 是保留的关键字</span><span class="sxs-lookup"><span data-stu-id="cc76b-132">MERGE is a Reserved Keyword</span></span>  
 <span data-ttu-id="cc76b-133">MERGE 现在是完全保留的关键字。</span><span class="sxs-lookup"><span data-stu-id="cc76b-133">MERGE is now a fully-reserved keyword.</span></span> <span data-ttu-id="cc76b-134">应用程序不能再包含名为 MERGE 的对象（表、列等）。</span><span class="sxs-lookup"><span data-stu-id="cc76b-134">Applications can no longer have objects (table, column, etc.) called MERGE.</span></span>  
  
## <a name="rename-cdc-schema"></a><span data-ttu-id="cc76b-135">重命名 CDC 架构</span><span class="sxs-lookup"><span data-stu-id="cc76b-135">Rename CDC Schema</span></span>  
 <span data-ttu-id="cc76b-136">存在名为 CDC 的架构。</span><span class="sxs-lookup"><span data-stu-id="cc76b-136">There is a schema name called CDC.</span></span> <span data-ttu-id="cc76b-137">如果为数据库启用了**变更数据捕获**，则不能使用此架构名称。</span><span class="sxs-lookup"><span data-stu-id="cc76b-137">This schema name cannot be in used if **Change Data Capture** is enabled for the database.</span></span>  
  
 <span data-ttu-id="cc76b-138">在为数据库启用 "**变更数据捕获**" 之前，必须删除 CDC 架构。</span><span class="sxs-lookup"><span data-stu-id="cc76b-138">You must drop the CDC schema before you enable **Change Data Capture** for the database.</span></span> <span data-ttu-id="cc76b-139">此步骤可以在升级之前或之后完成。</span><span class="sxs-lookup"><span data-stu-id="cc76b-139">This step can be done before or after the upgrade.</span></span> <span data-ttu-id="cc76b-140">若要删除该架构，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="cc76b-140">To drop the schema, use the following steps:</span></span>  
  
1.  <span data-ttu-id="cc76b-141">使用 ALTER SCHEMA 将对象从 CDC 架构传输到新的架构名称。</span><span class="sxs-lookup"><span data-stu-id="cc76b-141">Transfer the objects from CDC schema to a new schema name using ALTER SCHEMA.</span></span>  
  
2.  <span data-ttu-id="cc76b-142">验证对于新架构中的对象的权限。</span><span class="sxs-lookup"><span data-stu-id="cc76b-142">Verify permissions for the objects in the new schema.</span></span>  
  
3.  <span data-ttu-id="cc76b-143">对应用程序进行必要的修改。</span><span class="sxs-lookup"><span data-stu-id="cc76b-143">Make necessary modifications to the application.</span></span>  
  
4.  <span data-ttu-id="cc76b-144">使用 DROP SCHEMA 删除 CDC 架构。</span><span class="sxs-lookup"><span data-stu-id="cc76b-144">Drop the CDC schema using DROP SCHEMA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc76b-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc76b-145">See Also</span></span>  
 [<span data-ttu-id="cc76b-146">数据库引擎升级问题</span><span class="sxs-lookup"><span data-stu-id="cc76b-146">Database Engine Upgrade Issues</span></span>](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  
