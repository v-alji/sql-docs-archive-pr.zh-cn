---
title: 启用和禁用变更数据捕获 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], enabling tables
- change data capture [SQL Server], enabling databases
- change data capture [SQL Server], disabling databases
- change data capture [SQL Server], disabling tables
ms.assetid: b741894f-d267-4b10-adfe-cbc14aa6caeb
author: rothja
ms.author: jroth
ms.openlocfilehash: df0a2fd4a2c6ffb2de58d6b52360d1730d0fa7df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586561"
---
# <a name="enable-and-disable-change-data-capture-sql-server"></a><span data-ttu-id="fcffe-102">启用和禁用变更数据捕获 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fcffe-102">Enable and Disable Change Data Capture (SQL Server)</span></span>
  <span data-ttu-id="fcffe-103">本主题说明如何对数据库和表启用和禁用变更数据捕获。</span><span class="sxs-lookup"><span data-stu-id="fcffe-103">This topic describes how to enable and disable change data capture for a database and a table.</span></span>  
  
## <a name="enable-change-data-capture-for-a-database"></a><span data-ttu-id="fcffe-104">对数据库启用变更数据捕获</span><span class="sxs-lookup"><span data-stu-id="fcffe-104">Enable Change Data Capture for a Database</span></span>  
 <span data-ttu-id="fcffe-105">在为各个表创建捕获实例之前，必须先由 `sysadmin` 固定服务器角色的成员对数据库启用变更数据捕获。</span><span class="sxs-lookup"><span data-stu-id="fcffe-105">Before a capture instance can be created for individual tables, a member of the `sysadmin` fixed server role must first enable the database for change data capture.</span></span> <span data-ttu-id="fcffe-106">通过在数据库上下文中运行 [sys.sp_cdc_enable_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql) 存储过程可实现这一点。</span><span class="sxs-lookup"><span data-stu-id="fcffe-106">This is done by running the stored procedure [sys.sp_cdc_enable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql) in the database context.</span></span> <span data-ttu-id="fcffe-107">若要确定数据库是否已启用此功能，请在 `is_cdc_enabled` 目录视图中查询 `sys.databases` 列。</span><span class="sxs-lookup"><span data-stu-id="fcffe-107">To determine if a database is already enabled, query the `is_cdc_enabled` column in the `sys.databases` catalog view.</span></span>  
  
 <span data-ttu-id="fcffe-108">当对数据库启用了变更数据捕获之后，将为数据库创建 `cdc` 架构、`cdc` 用户、元数据表和其他系统对象。</span><span class="sxs-lookup"><span data-stu-id="fcffe-108">When a database is enabled for change data capture, the `cdc` schema, `cdc` user, metadata tables, and other system objects are created for the database.</span></span> <span data-ttu-id="fcffe-109">`cdc` 架构包含变更数据捕获元数据表，当对源表启用了变更数据捕获之后，各个更改表将用作更改数据的存储库。</span><span class="sxs-lookup"><span data-stu-id="fcffe-109">The `cdc` schema contains the change data capture metadata tables and, after source tables are enabled for change data capture, the individual change tables serve as a repository for change data.</span></span> <span data-ttu-id="fcffe-110">`cdc` 架构还包含用于查询更改数据的关联系统函数。</span><span class="sxs-lookup"><span data-stu-id="fcffe-110">The `cdc` schema also contains associated system functions used to query for change data.</span></span>  
  
 <span data-ttu-id="fcffe-111">变更数据捕获要求采用独占方式使用 `cdc` 架构和 `cdc` 用户。</span><span class="sxs-lookup"><span data-stu-id="fcffe-111">Change data capture requires exclusive use of the `cdc` schema and `cdc` user.</span></span> <span data-ttu-id="fcffe-112">如果某数据库中当前存在名为 *cdc* 的架构或数据库用户，那么在删除或重命名此架构或用户之前，不能对此数据库启用变更数据捕获。</span><span class="sxs-lookup"><span data-stu-id="fcffe-112">If either a schema or a database user named *cdc* currently exists in a database, the database cannot be enabled for change data capture until the schema and or user are dropped or renamed.</span></span>  
  
 <span data-ttu-id="fcffe-113">有关启用数据库的示例，请参阅 Enable Database for Change Data Capture 模板。</span><span class="sxs-lookup"><span data-stu-id="fcffe-113">See the Enable Database for Change Data Capture template for an example of enabling a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fcffe-114">若要在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中找到模板，请转至 **“视图”** ，单击 **“模板资源管理器”** ，然后选择 **“SQL Server 模板”** 。</span><span class="sxs-lookup"><span data-stu-id="fcffe-114">To locate the templates in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], go to **View**, click **Template Explorer**, and then select **SQL Server Templates**.</span></span> <span data-ttu-id="fcffe-115">**Change Data Capture** 为一个子文件夹。</span><span class="sxs-lookup"><span data-stu-id="fcffe-115">**Change Data Capture** is a sub-folder.</span></span> <span data-ttu-id="fcffe-116">在此文件夹下，您会找到本主题中提到的所有模板。</span><span class="sxs-lookup"><span data-stu-id="fcffe-116">Under this folder, you will find all the templates referenced in this topic.</span></span> <span data-ttu-id="fcffe-117">**工具栏上还有一个** “模板资源管理器” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 图标。</span><span class="sxs-lookup"><span data-stu-id="fcffe-117">There is also a **Template Explorer** icon on the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar.</span></span>  
  
```sql  
-- ====  
-- Enable Database for CDC template   
-- ====  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_db  
GO  
```  
  
## <a name="disable-change-data-capture-for-a-database"></a><span data-ttu-id="fcffe-118">对数据库禁用变更数据捕获</span><span class="sxs-lookup"><span data-stu-id="fcffe-118">Disable Change Data Capture for a Database</span></span>  
 <span data-ttu-id="fcffe-119">`sysadmin`固定服务器角色的成员可以在数据库上下文中运行存储过程[sys.databases Sp_cdc_disable_db &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) ，以对数据库禁用变更数据捕获。</span><span class="sxs-lookup"><span data-stu-id="fcffe-119">A member of the `sysadmin` fixed server role can run the stored procedure [sys.sp_cdc_disable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) in the database context to disable change data capture for a database.</span></span> <span data-ttu-id="fcffe-120">在禁用数据库之前不必禁用各个表。</span><span class="sxs-lookup"><span data-stu-id="fcffe-120">It is not necessary to disable individual tables before you disable the database.</span></span> <span data-ttu-id="fcffe-121">禁用数据库会删除所有关联的变更数据捕获元数据，包括 `cdc` 用户、架构和变更数据捕获作业。</span><span class="sxs-lookup"><span data-stu-id="fcffe-121">Disabling the database removes all associated change data capture metadata, including the `cdc` user and schema and the change data capture jobs.</span></span> <span data-ttu-id="fcffe-122">但是，任何由变更数据捕获创建的访问控制角色不会被自动删除，而是必须将其显式删除。</span><span class="sxs-lookup"><span data-stu-id="fcffe-122">However, any gating roles created by change data capture will not be removed automatically and must be explicitly deleted.</span></span> <span data-ttu-id="fcffe-123">若要确定数据库是否启用了此项功能，请在 sys.databases 目录视图中查询 `is_cdc_enabled` 列。</span><span class="sxs-lookup"><span data-stu-id="fcffe-123">To determine if a database is enabled, query the `is_cdc_enabled` column in the sys.databases catalog view.</span></span>  
  
 <span data-ttu-id="fcffe-124">当删除启用了变更数据捕获的数据库时会自动删除变更数据捕获作业。</span><span class="sxs-lookup"><span data-stu-id="fcffe-124">If a change data capture enabled database is dropped, change data capture jobs are automatically removed.</span></span>  
  
 <span data-ttu-id="fcffe-125">有关禁用数据库的示例，请参阅 Disable Database for Change Data Capture 模板。</span><span class="sxs-lookup"><span data-stu-id="fcffe-125">See the Disable Database for Change Data Capture template for an example of disabling a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fcffe-126">若要在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中找到模板，请转至 **“视图”** ，单击 **“模板资源管理器”** ，然后单击 **“SQL Server 模板”** 。</span><span class="sxs-lookup"><span data-stu-id="fcffe-126">To locate the templates in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], go to **View**, click **Template Explorer**, and then click **SQL Server Templates**.</span></span> <span data-ttu-id="fcffe-127">**“变更数据捕获”** 为子文件夹，在该文件夹中您将找到本主题中提到的所有模板。</span><span class="sxs-lookup"><span data-stu-id="fcffe-127">**Change Data Capture** is a sub-folder where you will find all the templates that are referenced in this topic.</span></span> <span data-ttu-id="fcffe-128">**工具栏上还有一个** “模板资源管理器” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 图标。</span><span class="sxs-lookup"><span data-stu-id="fcffe-128">There is also a **Template Explorer** icon on the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar.</span></span>  
  
```sql  
-- =======  
-- Disable Database for Change Data Capture template   
-- =======  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_db  
GO  
```  
  
## <a name="enable-change-data-capture-for-a-table"></a><span data-ttu-id="fcffe-129">对表启用变更数据捕获</span><span class="sxs-lookup"><span data-stu-id="fcffe-129">Enable Change Data Capture for a Table</span></span>  
 <span data-ttu-id="fcffe-130">在对数据库启用变更数据捕获之后，`db_owner` 固定数据库角色的成员即可以使用存储过程 `sys.sp_cdc_enable_table` 为各个源表创建捕获实例。</span><span class="sxs-lookup"><span data-stu-id="fcffe-130">After a database has been enabled for change data capture, members of the `db_owner` fixed database role can create a capture instance for individual source tables by using the stored procedure `sys.sp_cdc_enable_table`.</span></span> <span data-ttu-id="fcffe-131">若要确定是否已对某个源表启用了变更数据捕获，请在 `sys.tables` 目录视图中检查 is_tracked_by_cdc 列。</span><span class="sxs-lookup"><span data-stu-id="fcffe-131">To determine whether a source table has already been enabled for change data capture, examine the is_tracked_by_cdc column in the `sys.tables` catalog view.</span></span>  
  
 <span data-ttu-id="fcffe-132">创建捕获实例时，可以指定以下选项：</span><span class="sxs-lookup"><span data-stu-id="fcffe-132">The following options can be specified when creating a capture instance:</span></span>  
  
 <span data-ttu-id="fcffe-133">`Columns in the source table to be captured`.</span><span class="sxs-lookup"><span data-stu-id="fcffe-133">`Columns in the source table to be captured`.</span></span>  
  
 <span data-ttu-id="fcffe-134">默认情况下，源表中的所有列都将标识为已捕获列。</span><span class="sxs-lookup"><span data-stu-id="fcffe-134">By default, all of the columns in the source table are identified as captured columns.</span></span> <span data-ttu-id="fcffe-135">如果只需跟踪部分列（如出于隐私或性能方面的原因），请使用 *@captured_column_list* 参数指定列的子集。</span><span class="sxs-lookup"><span data-stu-id="fcffe-135">If only a subset of columns need to be tracked, such as for privacy or performance reasons, use the *@captured_column_list* parameter to specify the subset of columns.</span></span>  
  
 `A filegroup to contain the change table.`  
  
 <span data-ttu-id="fcffe-136">默认情况下，更改表位于数据库的默认文件组中。</span><span class="sxs-lookup"><span data-stu-id="fcffe-136">By default, the change table is located in the default filegroup of the database.</span></span> <span data-ttu-id="fcffe-137">要控制各个更改表的位置的数据库所有者可以使用 *@filegroup_name* 参数为与捕获实例关联的更改表指定特定的文件组。</span><span class="sxs-lookup"><span data-stu-id="fcffe-137">Database owners who want to control the placement of individual change tables can use the *@filegroup_name* parameter to specify a particular filegroup for the change table associated with the capture instance.</span></span> <span data-ttu-id="fcffe-138">指定的文件组必须已存在。</span><span class="sxs-lookup"><span data-stu-id="fcffe-138">The named filegroup must already exist.</span></span> <span data-ttu-id="fcffe-139">通常建议将更改表置于独立于源表的文件组中。</span><span class="sxs-lookup"><span data-stu-id="fcffe-139">Generally, it is recommended that change tables be placed in a filegroup separate from source tables.</span></span> <span data-ttu-id="fcffe-140">`Enable a Table Specifying Filegroup Option`有关演示如何使用参数的示例，请参阅模板 *@filegroup_name* 。</span><span class="sxs-lookup"><span data-stu-id="fcffe-140">See the `Enable a Table Specifying Filegroup Option` template for an example showing use of the *@filegroup_name* parameter.</span></span>  
  
```sql  
-- =========  
-- Enable a Table Specifying Filegroup Option Template  
-- =========  
USE MyDB  
GO  
  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@filegroup_name = N'MyDB_CT',  
@supports_net_changes = 1  
GO  
```  
  
 `A role for controlling access to a change table.`  
  
 <span data-ttu-id="fcffe-141">指定角色的目的是控制对更改数据的访问。</span><span class="sxs-lookup"><span data-stu-id="fcffe-141">The purpose of the named role is to control access to the change data.</span></span> <span data-ttu-id="fcffe-142">指定的角色可以为现有的固定服务器角色或数据库角色。</span><span class="sxs-lookup"><span data-stu-id="fcffe-142">The specified role can be an existing fixed server role or a database role.</span></span> <span data-ttu-id="fcffe-143">如果指定的角色还不存在，则会自动创建具有该名称的数据库角色。</span><span class="sxs-lookup"><span data-stu-id="fcffe-143">If the specified role does not already exist, a database role of that name is created automatically.</span></span> <span data-ttu-id="fcffe-144">`sysadmin` 或 `db_owner` 角色的成员对于更改表中的数据拥有完全访问权限。</span><span class="sxs-lookup"><span data-stu-id="fcffe-144">Members of either the `sysadmin` or `db_owner` role have full access to the data in the change tables.</span></span> <span data-ttu-id="fcffe-145">所有其他用户必须对源表中的所有捕获列拥有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="fcffe-145">All other users must have SELECT permission on all the captured columns of the source table.</span></span> <span data-ttu-id="fcffe-146">此外，当指定角色时，不是 `sysadmin` 或 `db_owner` 角色成员的用户还必须是指定角色的成员。</span><span class="sxs-lookup"><span data-stu-id="fcffe-146">In addition, when a role is specified, users who are not members of either the `sysadmin` or `db_owner` role must also be members of the specified role.</span></span>  
  
 <span data-ttu-id="fcffe-147">如果不想使用 "门控" 角色，请将参数显式设置 *@role_name* 为 NULL。</span><span class="sxs-lookup"><span data-stu-id="fcffe-147">If you do not want to use a gating role, explicitly set the *@role_name* parameter to NULL.</span></span> <span data-ttu-id="fcffe-148">有关如何在没有访问控制角色的情况下启用表的示例，请参阅`Enable a Table Without Using a Gating Role`模板。</span><span class="sxs-lookup"><span data-stu-id="fcffe-148">See the `Enable a Table Without Using a Gating Role` template for an example of enabling a table without a gating role.</span></span>  
  
```sql  
-- =========  
-- Enable a Table Without Using a Gating Role template   
-- =========  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = NULL,  
@supports_net_changes = 1  
GO  
  
```  
  
 `A function to query for net changes.`  
  
 <span data-ttu-id="fcffe-149">捕获实例将始终包含一个表值函数以返回在指定的时间间隔内出现的所有更改表项。</span><span class="sxs-lookup"><span data-stu-id="fcffe-149">A capture instance will always include a table valued function for returning all change table entries that occurred within a defined interval.</span></span> <span data-ttu-id="fcffe-150">此函数通过在“cdc.fn_cdc_get_all_changes_”后追加捕获实例名称来命名。</span><span class="sxs-lookup"><span data-stu-id="fcffe-150">This function is named by appending the capture instance name to "cdc.fn_cdc_get_all_changes_".</span></span> <span data-ttu-id="fcffe-151">有关详细信息，请参阅 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  (Transact-SQL)](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fcffe-151">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="fcffe-152">如果将参数 *@supports_net_changes* 设置为1，则还将为捕获实例生成一个净更改函数。</span><span class="sxs-lookup"><span data-stu-id="fcffe-152">If the parameter *@supports_net_changes* is set to 1, a net changes function is also generated for the capture instance.</span></span> <span data-ttu-id="fcffe-153">对于在调用中指定的时间间隔内发生更改的每个非重复行，此函数仅返回一项更改。</span><span class="sxs-lookup"><span data-stu-id="fcffe-153">This function returns only one change for each distinct row changed in the interval specified in the call.</span></span> <span data-ttu-id="fcffe-154">有关详细信息，请参阅[cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; (Transact-SQL)](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fcffe-154">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="fcffe-155">若要支持净更改查询，源表必须具有用于唯一标识行的主键或唯一索引。</span><span class="sxs-lookup"><span data-stu-id="fcffe-155">To support net changes queries, the source table must have a primary key or unique index to uniquely identify rows.</span></span> <span data-ttu-id="fcffe-156">如果使用了唯一索引，则必须使用参数指定索引的名称 *@index_name* 。</span><span class="sxs-lookup"><span data-stu-id="fcffe-156">If a unique index is used, the name of the index must be specified using the *@index_name* parameter.</span></span> <span data-ttu-id="fcffe-157">在主键或唯一索引中定义的列必须包含在要捕获的源列列表中。</span><span class="sxs-lookup"><span data-stu-id="fcffe-157">The columns defined in the primary key or unique index must be included in the list of source columns to be captured.</span></span>  
  
 <span data-ttu-id="fcffe-158">有关演示如何创建同时具有这两个查询函数的捕获实例的示例，请参阅`Enable a Table for All and Net Changes Queries`模板。</span><span class="sxs-lookup"><span data-stu-id="fcffe-158">See the `Enable a Table for All and Net Changes Queries` template for an example demonstrating the creation of a capture instance with both query functions.</span></span>  
  
```sql  
-- =============  
-- Enable a Table for All and Net Changes Queries template   
-- =============  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@supports_net_changes = 1  
GO  
```  
  
> [!NOTE]
>  <span data-ttu-id="fcffe-159">如果对具有现有主键的表启用变更数据捕获，且 *@index_name* 未使用参数来标识备用唯一索引，则变更数据捕获功能将使用主键。</span><span class="sxs-lookup"><span data-stu-id="fcffe-159">If change data capture is enabled on a table with an existing primary key, and the *@index_name* parameter is not used to identify an alternative unique index, the change data capture feature will use the primary key.</span></span> <span data-ttu-id="fcffe-160">只有先对表禁用变更数据捕获，才能对主键进行后续更改。</span><span class="sxs-lookup"><span data-stu-id="fcffe-160">Subsequent changes to the primary key will not be allowed without first disabling change data capture for the table.</span></span> <span data-ttu-id="fcffe-161">无论配置变更数据捕获时是否要求支持净更改查询均是如此。</span><span class="sxs-lookup"><span data-stu-id="fcffe-161">This is true regardless of whether support for net changes queries was requested when change data capture was configured.</span></span> <span data-ttu-id="fcffe-162">如果对表启用变更数据捕获时该表中没有主键，则变更数据捕获将忽略后来添加的主键。</span><span class="sxs-lookup"><span data-stu-id="fcffe-162">If there is no primary key on a table at the time it is enabled for change data capture, the subsequent addition of a primary key is ignored by change data capture.</span></span> <span data-ttu-id="fcffe-163">由于变更数据捕获不会使用在启用表之后创建的主键，因此可以不受限制地将该键及键列删除。</span><span class="sxs-lookup"><span data-stu-id="fcffe-163">Because change data capture will not use a primary key that is created after the table was enabled, the key and key columns can be removed without restrictions.</span></span>  
  
## <a name="disable-change-data-capture-for-a-table"></a><span data-ttu-id="fcffe-164">对表禁用变更数据捕获</span><span class="sxs-lookup"><span data-stu-id="fcffe-164">Disable Change Data Capture for a Table</span></span>  
 <span data-ttu-id="fcffe-165">`db_owner` 固定数据库角色的成员可以通过使用存储过程 `sys.sp_cdc_disable_table` 为各个源表删除捕获实例。</span><span class="sxs-lookup"><span data-stu-id="fcffe-165">Members of the `db_owner` fixed database role can remove a capture instance for individual source tables by using the stored procedure `sys.sp_cdc_disable_table`.</span></span> <span data-ttu-id="fcffe-166">若要确定当前是否已对某个源表启用了变更数据捕获，请在 `is_tracked_by_cdc` 目录视图中检查 `sys.tables` 列。</span><span class="sxs-lookup"><span data-stu-id="fcffe-166">To determine whether a source table is currently enabled for change data capture, examine the `is_tracked_by_cdc` column in the `sys.tables` catalog view.</span></span> <span data-ttu-id="fcffe-167">如果在禁用发生后没有对数据库启用任何表，则还会删除变更数据捕获作业。</span><span class="sxs-lookup"><span data-stu-id="fcffe-167">If there are no tables enabled for the database after the disabling takes place, the change data capture jobs are also removed.</span></span>  
  
 <span data-ttu-id="fcffe-168">如果删除了启用变更数据捕获的表，则会自动删除与该表关联的变更数据捕获元数据。</span><span class="sxs-lookup"><span data-stu-id="fcffe-168">If a change data capture-enabled table is dropped, change data capture metadata that is associated with the table is automatically removed.</span></span>  
  
 <span data-ttu-id="fcffe-169">有关禁用表的示例，请参阅 Disable a Capture Instance for a Table 模板。</span><span class="sxs-lookup"><span data-stu-id="fcffe-169">See the Disable a Capture Instance for a Table template for an example of disabling a table.</span></span>  
  
```sql  
-- =====  
-- Disable a Capture Instance for a Table template   
-- =====  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@capture_instance = N'dbo_MyTable'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="fcffe-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fcffe-170">See Also</span></span>  
 <span data-ttu-id="fcffe-171">[跟踪数据更改 (SQL Server)](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fcffe-171">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="fcffe-172">[关于变更数据捕获 (SQL Server)](../track-changes/about-change-data-capture-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fcffe-172">[About Change Data Capture &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md) </span></span>  
 <span data-ttu-id="fcffe-173">[处理变更数据 (SQL Server)](work-with-change-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fcffe-173">[Work with Change Data &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span></span>  
 [<span data-ttu-id="fcffe-174">管理和监视变更数据捕获 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fcffe-174">Administer and Monitor Change Data Capture &#40;SQL Server&#41;</span></span>](../track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  
