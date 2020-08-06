---
title: 元数据可见性配置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- subcomponents visibility [SQL Server]
- metadata [SQL Server], visibility
- permissions [SQL Server], metadata access
- viewing metadata
- objects [SQL Server], metadata
- displaying metadata
- database metadata [SQL Server]
- metadata [SQL Server], permissions
ms.assetid: 50d2e015-05ae-4014-a1cd-4de7866ad651
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5198dc4ba4e81bc1d7a8dd2411da59da81596102
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587306"
---
# <a name="metadata-visibility-configuration"></a><span data-ttu-id="7d357-102">元数据可见性配置</span><span class="sxs-lookup"><span data-stu-id="7d357-102">Metadata Visibility Configuration</span></span>
  <span data-ttu-id="7d357-103">元数据的可见性仅限用户所拥有的安全对象，或已授予用户某些权限的安全对象。</span><span class="sxs-lookup"><span data-stu-id="7d357-103">The visibility of metadata is limited to securables that a user either owns or on which the user has been granted some permission.</span></span> <span data-ttu-id="7d357-104">例如，如果用户获得了对表 `myTable`的 SELECT 或 INSERT 权限，则下面的查询将返回一行。</span><span class="sxs-lookup"><span data-stu-id="7d357-104">For example, the following query returns a row if the user has been granted a permission such as SELECT or INSERT on the table `myTable`.</span></span>  
  
```  
SELECT name, object_id  
FROM sys.tables  
WHERE name = 'myTable';  
GO  
```  
  
 <span data-ttu-id="7d357-105">但如果用户对 `myTable`没有任何权限，则查询返回空的结果集。</span><span class="sxs-lookup"><span data-stu-id="7d357-105">However, if the user does not have any permission on `myTable`, the query returns an empty result set.</span></span>  
  
## <a name="scope-and-impact-of-metadata-visibility-configuration"></a><span data-ttu-id="7d357-106">元数据可见性配置的作用域和影响</span><span class="sxs-lookup"><span data-stu-id="7d357-106">Scope and Impact of Metadata Visibility Configuration</span></span>  
 <span data-ttu-id="7d357-107">元数据可见性配置仅可应用于下列安全对象。</span><span class="sxs-lookup"><span data-stu-id="7d357-107">Metadata visibility configuration only applies to the following securables.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d357-108">目录视图</span><span class="sxs-lookup"><span data-stu-id="7d357-108">Catalog views</span></span>|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="7d357-109">sp_help 存储过程</span><span class="sxs-lookup"><span data-stu-id="7d357-109">**sp_help** stored procedures</span></span>|  
|<span data-ttu-id="7d357-110">公开元数据的内置函数</span><span class="sxs-lookup"><span data-stu-id="7d357-110">Metadata exposing built-in functions</span></span>|<span data-ttu-id="7d357-111">信息架构视图</span><span class="sxs-lookup"><span data-stu-id="7d357-111">Information schema views</span></span>|  
|<span data-ttu-id="7d357-112">兼容性视图</span><span class="sxs-lookup"><span data-stu-id="7d357-112">Compatibility views</span></span>|<span data-ttu-id="7d357-113">扩展属性</span><span class="sxs-lookup"><span data-stu-id="7d357-113">Extended properties</span></span>|  
  
 <span data-ttu-id="7d357-114">元数据可见性配置不能应用于下列安全对象。</span><span class="sxs-lookup"><span data-stu-id="7d357-114">Metadata visibility configuration does not apply to the following securables.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d357-115">日志传送系统表</span><span class="sxs-lookup"><span data-stu-id="7d357-115">Log shipping system tables</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7d357-116">代理系统表</span><span class="sxs-lookup"><span data-stu-id="7d357-116">Agent system tables</span></span>|  
|<span data-ttu-id="7d357-117">数据库维护计划系统表</span><span class="sxs-lookup"><span data-stu-id="7d357-117">Database maintenance plan system tables</span></span>|<span data-ttu-id="7d357-118">备份系统表</span><span class="sxs-lookup"><span data-stu-id="7d357-118">Backup system tables</span></span>|  
|<span data-ttu-id="7d357-119">复制系统表</span><span class="sxs-lookup"><span data-stu-id="7d357-119">Replication system tables</span></span>|<span data-ttu-id="7d357-120">复制及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理 **sp_help** 存储过程</span><span class="sxs-lookup"><span data-stu-id="7d357-120">Replication and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **sp_help** stored procedures</span></span>|  
  
 <span data-ttu-id="7d357-121">有限的元数据可访问性意味着：</span><span class="sxs-lookup"><span data-stu-id="7d357-121">Limited metadata accessibility means the following:</span></span>  
  
-   <span data-ttu-id="7d357-122">假定 **public** 可访问元数据的应用程序将中断。</span><span class="sxs-lookup"><span data-stu-id="7d357-122">Applications that assume **public** metadata access will break.</span></span>  
  
-   <span data-ttu-id="7d357-123">对系统视图的查询可能只返回行子集，有时返回空的结果集。</span><span class="sxs-lookup"><span data-stu-id="7d357-123">Queries on system views might only return a subset of rows, or sometimes an empty result set.</span></span>  
  
-   <span data-ttu-id="7d357-124">元数据生成的内置函数（如 OBJECTPROPERTYEX）可能返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="7d357-124">Metadata-emitting, built-in functions such as OBJECTPROPERTYEX may return NULL.</span></span>  
  
-   <span data-ttu-id="7d357-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)] sp_help 存储过程可能只返回行子集或 NULL。</span><span class="sxs-lookup"><span data-stu-id="7d357-125">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] **sp_help** stored procedures might return only a subset of rows, or NULL.</span></span>  
  
 <span data-ttu-id="7d357-126">SQL 模块（如存储过程和触发器）在调用方的安全上下文中运行，因此，它们只有有限的元数据访问性。</span><span class="sxs-lookup"><span data-stu-id="7d357-126">SQL modules, such as stored procedures and triggers, run under the security context of the caller and, therefore, have limited metadata accessibility.</span></span> <span data-ttu-id="7d357-127">例如，在以下代码中，当存储过程尝试访问表 `myTable` （调用方对该表没有权限）的元数据时，返回空的结果集。</span><span class="sxs-lookup"><span data-stu-id="7d357-127">For example, in the following code, when the stored procedure tries to access metadata for the table `myTable` on which the caller has no rights, an empty result set is returned.</span></span> <span data-ttu-id="7d357-128">在早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，返回一行。</span><span class="sxs-lookup"><span data-stu-id="7d357-128">In earlier releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a row is returned.</span></span>  
  
```  
CREATE PROCEDURE assumes_caller_can_access_metadata  
BEGIN  
SELECT name, id   
FROM sysobjects   
WHERE name = 'myTable';  
END;  
GO  
```  
  
 <span data-ttu-id="7d357-129">若要允许调用方查看元数据，可在适当的作用域（对象级、数据库级或服务器级）中授予调用方 VIEW DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="7d357-129">To allow callers to view metadata, you can grant the callers VIEW DEFINITION permission at an appropriate scope: object level, database level or server level.</span></span> <span data-ttu-id="7d357-130">因此，在以上示例中，如果调用方对 `myTable`具有 VIEW DEFINITION 权限，则存储过程返回一行。</span><span class="sxs-lookup"><span data-stu-id="7d357-130">Therefore, in the previous example, if the caller has VIEW DEFINITION permission on `myTable`, the stored procedure returns a row.</span></span> <span data-ttu-id="7d357-131">有关详细信息，请参阅 [GRANT (Transact SQL)](/sql/t-sql/statements/grant-transact-sql) 和[授予数据库权限 (Transact SQL)](/sql/t-sql/statements/grant-database-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7d357-131">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) and [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
 <span data-ttu-id="7d357-132">也可以将存储过程修改为使用所有者凭据执行。</span><span class="sxs-lookup"><span data-stu-id="7d357-132">You can also modify the stored procedure so that it executes under the credentials of the owner.</span></span> <span data-ttu-id="7d357-133">当过程所有者和表所有者相同时，便会应用所有权链，并且过程所有者的安全上下文便会启用对 `myTable`元数据的访问。</span><span class="sxs-lookup"><span data-stu-id="7d357-133">When the procedure owner and the table owner are the same owner, ownership chaining applies, and the security context of the procedure owner enables access to the metadata for `myTable`.</span></span> <span data-ttu-id="7d357-134">在这种情况下，以下代码会向调用方返回一行元数据。</span><span class="sxs-lookup"><span data-stu-id="7d357-134">Under this scenario, the following code returns a row of metadata to the caller.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d357-135">以下示例使用的是 [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) 目录视图，而非 [sys.sysobjects](/sql/relational-databases/system-compatibility-views/sys-sysobjects-transact-sql) 兼容视图。</span><span class="sxs-lookup"><span data-stu-id="7d357-135">The following example uses the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view instead of the [sys.sysobjects](/sql/relational-databases/system-compatibility-views/sys-sysobjects-transact-sql) compatibility view.</span></span>  
  
```  
CREATE PROCEDURE does_not_assume_caller_can_access_metadata  
WITH EXECUTE AS OWNER  
AS  
BEGIN  
SELECT name, id  
FROM sys.objects   
WHERE name = 'myTable'   
END;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="7d357-136">您可以使用 EXECUTE AS 临时切换到调用方的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="7d357-136">You can use EXECUTE AS to temporarily switch to the security context of the caller.</span></span> <span data-ttu-id="7d357-137">有关详细信息，请参阅 [EXECUTE AS (Transact SQL)](/sql/t-sql/statements/execute-as-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7d357-137">For more information, see [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql).</span></span>  
  
## <a name="benefits-and-limits-of-metadata-visibility-configuration"></a><span data-ttu-id="7d357-138">元数据可见性配置的优点和限制</span><span class="sxs-lookup"><span data-stu-id="7d357-138">Benefits and Limits of Metadata Visibility Configuration</span></span>  
 <span data-ttu-id="7d357-139">元数据可见性配置在整个安全计划中发挥着重要作用。</span><span class="sxs-lookup"><span data-stu-id="7d357-139">Metadata visibility configuration can play an important role in your overall security plan.</span></span> <span data-ttu-id="7d357-140">但在有些情况下，有经验的用户和已确定的用户可以强制公开某些元数据。</span><span class="sxs-lookup"><span data-stu-id="7d357-140">However, there are cases in which a skilled and determined user can force the disclosure of some metadata.</span></span> <span data-ttu-id="7d357-141">建议将元数据权限部署为多种深层防御中的一种。</span><span class="sxs-lookup"><span data-stu-id="7d357-141">We recommend that you deploy metadata permissions as one of many defenses-in-depth.</span></span>  
  
 <span data-ttu-id="7d357-142">理论上可以通过控制查询中的谓词评估顺序，强制在错误消息中显示元数据。</span><span class="sxs-lookup"><span data-stu-id="7d357-142">It is theoretically possible to force the emission of metadata in error messages by manipulating the order of predicate evaluation in queries.</span></span> <span data-ttu-id="7d357-143">此类“试错攻击”的威胁并非是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 专有的。</span><span class="sxs-lookup"><span data-stu-id="7d357-143">The possibility of such *trial-and-error attacks* is not specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7d357-144">它由关系代数中允许的关联转换和交换转换表示。</span><span class="sxs-lookup"><span data-stu-id="7d357-144">It is implied by the associative and commutative transformations permitted in relational algebra.</span></span> <span data-ttu-id="7d357-145">可以通过限制错误消息中返回的信息来降低此风险。</span><span class="sxs-lookup"><span data-stu-id="7d357-145">You can mitigate this risk by limiting the information returned in error messages.</span></span> <span data-ttu-id="7d357-146">为了以此方式进一步限制元数据的可见性，可以使用跟踪标志 3625 启动服务器。</span><span class="sxs-lookup"><span data-stu-id="7d357-146">To further restrict the visibility of metadata in this way, you can start the server with trace flag 3625.</span></span> <span data-ttu-id="7d357-147">此跟踪标志限制错误消息中显示的信息量。</span><span class="sxs-lookup"><span data-stu-id="7d357-147">This trace flag limits the amount of information shown in error messages.</span></span> <span data-ttu-id="7d357-148">进一步有助于防止强制泄漏。</span><span class="sxs-lookup"><span data-stu-id="7d357-148">In turn, this helps to prevent forced disclosures.</span></span> <span data-ttu-id="7d357-149">需要在错误消息的简洁性和用于调试的难易程度之间进行权衡。</span><span class="sxs-lookup"><span data-stu-id="7d357-149">The tradeoff is that error messages will be terse and might be difficult to use for debugging purposes.</span></span> <span data-ttu-id="7d357-150">有关详细信息，请参阅[数据库引擎服务启动选项](../../database-engine/configure-windows/database-engine-service-startup-options.md)和[跟踪标志 (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7d357-150">For more information, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md) and [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
 <span data-ttu-id="7d357-151">下列元数据无法强制公开：</span><span class="sxs-lookup"><span data-stu-id="7d357-151">The following metadata is not subject to forced disclosure:</span></span>  
  
-   <span data-ttu-id="7d357-152">存储在 **sys.servers** 的 **provider_string**列中的值。</span><span class="sxs-lookup"><span data-stu-id="7d357-152">The value stored in the **provider_string** column of **sys.servers**.</span></span> <span data-ttu-id="7d357-153">没有 ALTER ANY LINKED SERVER 权限的用户将看到此列中的值为 NULL。</span><span class="sxs-lookup"><span data-stu-id="7d357-153">A user that does not have ALTER ANY LINKED SERVER permission will see a NULL value in this column.</span></span>  
  
-   <span data-ttu-id="7d357-154">用户定义的对象（如存储过程或触发器）的源定义。</span><span class="sxs-lookup"><span data-stu-id="7d357-154">Source definition of a user-defined object such as a stored procedure or trigger.</span></span> <span data-ttu-id="7d357-155">只有在满足下列某一种条件时，才能看到源代码：</span><span class="sxs-lookup"><span data-stu-id="7d357-155">The source code is visible only when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="7d357-156">用户对该对象具有 VIEW DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="7d357-156">The user has VIEW DEFINITION permission on the object.</span></span>  
  
    -   <span data-ttu-id="7d357-157">用户没有被拒绝对该对象具有 VIEW DEFINITION 权限，并且还对其具有 CONTROL、ALTER 或 TAKE OWNERSHIP 权限。</span><span class="sxs-lookup"><span data-stu-id="7d357-157">The user has not been denied VIEW DEFINITION permission on the object and has CONTROL, ALTER, or TAKE OWNERSHIP permission on the object.</span></span> <span data-ttu-id="7d357-158">所有其他用户看到的是 NULL。</span><span class="sxs-lookup"><span data-stu-id="7d357-158">All other users will see NULL.</span></span>  
  
-   <span data-ttu-id="7d357-159">在下列目录视图中找到的定义列：</span><span class="sxs-lookup"><span data-stu-id="7d357-159">The definition columns found in the following catalog views:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="7d357-160">**sys.all_sql_modules**</span><span class="sxs-lookup"><span data-stu-id="7d357-160">**sys.all_sql_modules**</span></span>|<span data-ttu-id="7d357-161">**sys.sql_modules**</span><span class="sxs-lookup"><span data-stu-id="7d357-161">**sys.sql_modules**</span></span>|  
    |<span data-ttu-id="7d357-162">**sys.server_sql_modules**</span><span class="sxs-lookup"><span data-stu-id="7d357-162">**sys.server_sql_modules**</span></span>|<span data-ttu-id="7d357-163">**sys.check_constraints**</span><span class="sxs-lookup"><span data-stu-id="7d357-163">**sys.check_constraints**</span></span>|  
    |<span data-ttu-id="7d357-164">**sys.default_constraints**</span><span class="sxs-lookup"><span data-stu-id="7d357-164">**sys.default_constraints**</span></span>|<span data-ttu-id="7d357-165">**sys.computed_columns**</span><span class="sxs-lookup"><span data-stu-id="7d357-165">**sys.computed_columns**</span></span>|  
    |<span data-ttu-id="7d357-166">**sys.numbered_procedures**</span><span class="sxs-lookup"><span data-stu-id="7d357-166">**sys.numbered_procedures**</span></span>||  
  
-   <span data-ttu-id="7d357-167">**syscomments** 兼容视图中的 **ctext** 列。</span><span class="sxs-lookup"><span data-stu-id="7d357-167">The **ctext** column in the **syscomments** compatibility view.</span></span>  
  
-   <span data-ttu-id="7d357-168">**sp_helptext** 过程的输出。</span><span class="sxs-lookup"><span data-stu-id="7d357-168">The output of the **sp_helptext** procedure.</span></span>  
  
-   <span data-ttu-id="7d357-169">信息架构视图中的以下列：</span><span class="sxs-lookup"><span data-stu-id="7d357-169">The following columns in the information schema views:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="7d357-170">INFORMATION_SCHEMA.CHECK_CONSTRAINTS.CHECK_CLAUSE</span><span class="sxs-lookup"><span data-stu-id="7d357-170">INFORMATION_SCHEMA.CHECK_CONSTRAINTS.CHECK_CLAUSE</span></span>|<span data-ttu-id="7d357-171">INFORMATION_SCHEMA.COLUMNS.COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="7d357-171">INFORMATION_SCHEMA.COLUMNS.COLUMN_DEFAULT</span></span>|  
    |<span data-ttu-id="7d357-172">INFORMATION_SCHEMA.DOMAINS.DOMAIN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="7d357-172">INFORMATION_SCHEMA.DOMAINS.DOMAIN_DEFAULT</span></span>|<span data-ttu-id="7d357-173">INFORMATION_SCHEMA.ROUTINE_COLUMNS.COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="7d357-173">INFORMATION_SCHEMA.ROUTINE_COLUMNS.COLUMN_DEFAULT</span></span>|  
    |<span data-ttu-id="7d357-174">INFORMATION_SCHEMA.ROUTINES.ROUTINE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="7d357-174">INFORMATION_SCHEMA.ROUTINES.ROUTINE_DEFINITION</span></span>|<span data-ttu-id="7d357-175">INFORMATION_SCHEMA.VIEWS.VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="7d357-175">INFORMATION_SCHEMA.VIEWS.VIEW_DEFINITION</span></span>|  
  
-   <span data-ttu-id="7d357-176">OBJECT_DEFINITION() 函数</span><span class="sxs-lookup"><span data-stu-id="7d357-176">OBJECT_DEFINITION() function</span></span>  
  
-   <span data-ttu-id="7d357-177">存储在 **sys.sql_logins**的 password_hash 列中的值。</span><span class="sxs-lookup"><span data-stu-id="7d357-177">The value stored in the password_hash column of **sys.sql_logins**.</span></span>  <span data-ttu-id="7d357-178">不具有 CONTROL SERVER 权限的用户可以看到该列中的 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="7d357-178">A user that does not have CONTROL SERVER permission will see a NULL value in this column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d357-179">内置系统过程和函数的 SQL 定义通过 **sys.system_sql_modules** 目录视图、 **sp_helptext** 存储过程以及 OBJECT_DEFINITION() 函数公开可见。</span><span class="sxs-lookup"><span data-stu-id="7d357-179">The SQL definitions of built-in system procedures and functions are publicly visible through the **sys.system_sql_modules** catalog view, the **sp_helptext** stored procedure, and the OBJECT_DEFINITION() function.</span></span>  
  
## <a name="general-principles-of-metadata-visibility"></a><span data-ttu-id="7d357-180">元数据可见性的一般原则</span><span class="sxs-lookup"><span data-stu-id="7d357-180">General Principles of Metadata Visibility</span></span>  
 <span data-ttu-id="7d357-181">下列是需要注意的有关元数据可见性的一般原则：</span><span class="sxs-lookup"><span data-stu-id="7d357-181">The following are some general principles to consider regarding metadata visibility:</span></span>  
  
-   <span data-ttu-id="7d357-182">固定角色隐式权限</span><span class="sxs-lookup"><span data-stu-id="7d357-182">Fixed roles implicit permissions</span></span>  
  
-   <span data-ttu-id="7d357-183">权限的作用域</span><span class="sxs-lookup"><span data-stu-id="7d357-183">Scope of permissions</span></span>  
  
-   <span data-ttu-id="7d357-184">DENY 的优先顺序</span><span class="sxs-lookup"><span data-stu-id="7d357-184">Precedence of DENY</span></span>  
  
-   <span data-ttu-id="7d357-185">子组件元数据的可见性</span><span class="sxs-lookup"><span data-stu-id="7d357-185">Visibility of subcomponent metadata</span></span>  
  
### <a name="fixed-roles-and-implicit-permissions"></a><span data-ttu-id="7d357-186">固定角色和隐式权限</span><span class="sxs-lookup"><span data-stu-id="7d357-186">Fixed Roles and Implicit Permissions</span></span>  
 <span data-ttu-id="7d357-187">固定角色可以访问的元数据取决于这些角色相应的隐式权限。</span><span class="sxs-lookup"><span data-stu-id="7d357-187">Metadata that can be accessed by fixed roles depends upon their corresponding implicit permissions.</span></span>  
  
### <a name="scope-of-permissions"></a><span data-ttu-id="7d357-188">权限的作用域</span><span class="sxs-lookup"><span data-stu-id="7d357-188">Scope of Permissions</span></span>  
 <span data-ttu-id="7d357-189">某个作用域上的权限意味着可以查看该作用域和所有包含的作用域上的元数据。</span><span class="sxs-lookup"><span data-stu-id="7d357-189">Permissions at one scope imply the ability to see metadata at that scope and at all enclosed scopes.</span></span> <span data-ttu-id="7d357-190">例如，对架构的 SELECT 权限意味着被授权者对该架构所包含的所有安全对象都具有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="7d357-190">For example, SELECT permission on a schema implies that the grantee has SELECT permission on all securables that are contained by that schema.</span></span> <span data-ttu-id="7d357-191">因此，授予对架构的 SELECT 权限可以使用户查看架构的元数据以及其中的所有表、视图、函数、过程、队列、同义词、类型和 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="7d357-191">The granting of SELECT permission on a schema therefore enables a user to see the metadata of the schema and also all tables, views, functions, procedures, queues, synonyms, types, and XML schema collections within it.</span></span> <span data-ttu-id="7d357-192">有关范围的详细信息，请参阅[权限层次结构（数据库引擎）](permissions-hierarchy-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="7d357-192">For more information about scopes, see [Permissions Hierarchy &#40;Database Engine&#41;](permissions-hierarchy-database-engine.md).</span></span>  
  
### <a name="precedence-of-deny"></a><span data-ttu-id="7d357-193">DENY 的优先顺序</span><span class="sxs-lookup"><span data-stu-id="7d357-193">Precedence of DENY</span></span>  
 <span data-ttu-id="7d357-194">DENY 通常优先于其他权限。</span><span class="sxs-lookup"><span data-stu-id="7d357-194">DENY typically takes precedence over other permissions.</span></span> <span data-ttu-id="7d357-195">例如，如果授予数据库用户对架构的 EXECUTE 权限，但是拒绝其对架构中存储过程的 EXECUTE 权限，则该用户不能查看此存储过程的元数据。</span><span class="sxs-lookup"><span data-stu-id="7d357-195">For example, if a database user is granted EXECUTE permission on a schema but has been denied EXECUTE permission on a stored procedure in that schema, the user cannot view the metadata for that stored procedure.</span></span>  
  
 <span data-ttu-id="7d357-196">另外，如果拒绝用户对某个架构具有 EXECUTE 权限，但授予其对该架构中某个存储过程具有 EXECUTE 权限，则该用户无法查看该存储过程的元数据。</span><span class="sxs-lookup"><span data-stu-id="7d357-196">Additionally, if a user is denied EXECUTE permission on a schema but has been granted EXECUTE permission on a stored procedure in that schema, the user cannot view the metadata for that stored procedure.</span></span>  
  
 <span data-ttu-id="7d357-197">再比如，如果通过各种角色成员身份同时授予和拒绝用户对存储过程的 EXECUTE 权限，则优先执行 DENY 权限，因此，用户不能查看存储过程的元数据。</span><span class="sxs-lookup"><span data-stu-id="7d357-197">For another example, if a user has been granted and denied EXECUTE permission on a stored procedure, which is possible through your various role memberships, DENY takes precedence and the user cannot view the metadata of the stored procedure.</span></span>  
  
### <a name="visibility-of-subcomponent-metadata"></a><span data-ttu-id="7d357-198">子组件元数据的可见性</span><span class="sxs-lookup"><span data-stu-id="7d357-198">Visibility of Subcomponent Metadata</span></span>  
 <span data-ttu-id="7d357-199">索引、检查约束和触发器这类子组件的可见性由对父级组件的权限决定。</span><span class="sxs-lookup"><span data-stu-id="7d357-199">The visibility of subcomponents, such as indexes, check constraints, and triggers is determined by permissions on the parent.</span></span> <span data-ttu-id="7d357-200">这些子组件没有可授予的权限。</span><span class="sxs-lookup"><span data-stu-id="7d357-200">These subcomponents do not have grantable permissions.</span></span> <span data-ttu-id="7d357-201">例如，如果针对表授予用户某些权限，则用户可以查看表、列、索引、检查约束、触发器以及其他此类子组件的元数据。</span><span class="sxs-lookup"><span data-stu-id="7d357-201">For example, if a user has been granted some permission on a table, the user can view the metadata for the tables, columns, indexes, check constraints, triggers, and other such subcomponents.</span></span>  
  
#### <a name="metadata-that-is-accessible-to-all-database-users"></a><span data-ttu-id="7d357-202">所有数据库用户可访问的元数据</span><span class="sxs-lookup"><span data-stu-id="7d357-202">Metadata That Is Accessible to All Database Users</span></span>  
 <span data-ttu-id="7d357-203">某些元数据对于特定数据库中的所有用户都必须是可访问的。</span><span class="sxs-lookup"><span data-stu-id="7d357-203">Some metadata must be accessible to all users in a specific database.</span></span> <span data-ttu-id="7d357-204">例如，文件组没有可授予的权限，因此不能授予用户查看文件组的元数据的权限。</span><span class="sxs-lookup"><span data-stu-id="7d357-204">For example, filegroups do not have conferrable permissions; therefore, a user cannot be granted permission to view the metadata of a filegroup.</span></span> <span data-ttu-id="7d357-205">但是，可以创建表的任何用户都必须能够访问文件组元数据，以使用 CREATE TABLE 语句的 ON *filegroup* 或 TEXTIMAGE_ON *filegroup* 子句。</span><span class="sxs-lookup"><span data-stu-id="7d357-205">However, any user that can create a table must be able to access filegroup metadata to use the ON *filegroup* or TEXTIMAGE_ON *filegroup* clauses of the CREATE TABLE statement.</span></span>  
  
 <span data-ttu-id="7d357-206">所有用户均可查看由 DB_ID() 函数和 DB_NAME() 函数返回的元数据。</span><span class="sxs-lookup"><span data-stu-id="7d357-206">The metadata that is returned by the DB_ID() and DB_NAME() functions is visible to all users.</span></span>  
  
 <span data-ttu-id="7d357-207">下表列出了对 **public** 角色可见的目录视图。</span><span class="sxs-lookup"><span data-stu-id="7d357-207">The following table lists the catalog views that are visible to the **public** role.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d357-208">**sys.partition_functions**</span><span class="sxs-lookup"><span data-stu-id="7d357-208">**sys.partition_functions**</span></span>|<span data-ttu-id="7d357-209">**sys.partition_range_values**</span><span class="sxs-lookup"><span data-stu-id="7d357-209">**sys.partition_range_values**</span></span>|  
|<span data-ttu-id="7d357-210">**sys.partition_schemes**</span><span class="sxs-lookup"><span data-stu-id="7d357-210">**sys.partition_schemes**</span></span>|<span data-ttu-id="7d357-211">**sys.data_spaces**</span><span class="sxs-lookup"><span data-stu-id="7d357-211">**sys.data_spaces**</span></span>|  
|<span data-ttu-id="7d357-212">**sys.filegroups**</span><span class="sxs-lookup"><span data-stu-id="7d357-212">**sys.filegroups**</span></span>|<span data-ttu-id="7d357-213">**sys.destination_data_spaces**</span><span class="sxs-lookup"><span data-stu-id="7d357-213">**sys.destination_data_spaces**</span></span>|  
|<span data-ttu-id="7d357-214">**sys.database_files**</span><span class="sxs-lookup"><span data-stu-id="7d357-214">**sys.database_files**</span></span>|<span data-ttu-id="7d357-215">**sys.allocation_units**</span><span class="sxs-lookup"><span data-stu-id="7d357-215">**sys.allocation_units**</span></span>|  
|<span data-ttu-id="7d357-216">**sys.partitions**</span><span class="sxs-lookup"><span data-stu-id="7d357-216">**sys.partitions**</span></span>|<span data-ttu-id="7d357-217">**sys.messages**</span><span class="sxs-lookup"><span data-stu-id="7d357-217">**sys.messages**</span></span>|  
|<span data-ttu-id="7d357-218">**sys.schemas**</span><span class="sxs-lookup"><span data-stu-id="7d357-218">**sys.schemas**</span></span>|<span data-ttu-id="7d357-219">**sys.configurations**</span><span class="sxs-lookup"><span data-stu-id="7d357-219">**sys.configurations**</span></span>|  
|<span data-ttu-id="7d357-220">**sys.sql_dependencies**</span><span class="sxs-lookup"><span data-stu-id="7d357-220">**sys.sql_dependencies**</span></span>|<span data-ttu-id="7d357-221">**sys.type_assembly_usages**</span><span class="sxs-lookup"><span data-stu-id="7d357-221">**sys.type_assembly_usages**</span></span>|  
|<span data-ttu-id="7d357-222">**sys.parameter_type_usages**</span><span class="sxs-lookup"><span data-stu-id="7d357-222">**sys.parameter_type_usages**</span></span>|<span data-ttu-id="7d357-223">**sys.column_type_usages**</span><span class="sxs-lookup"><span data-stu-id="7d357-223">**sys.column_type_usages**</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d357-224">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d357-224">See Also</span></span>  
 <span data-ttu-id="7d357-225">[GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7d357-225">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 <span data-ttu-id="7d357-226">[DENY (Transact-SQL)](/sql/t-sql/statements/deny-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7d357-226">[DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) </span></span>  
 <span data-ttu-id="7d357-227">[REVOKE (Transact-SQL)](/sql/t-sql/statements/revoke-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7d357-227">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span></span>  
 <span data-ttu-id="7d357-228">[EXECUTE AS 子句 (Transact-SQL)](/sql/t-sql/statements/execute-as-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7d357-228">[EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql) </span></span>  
 <span data-ttu-id="7d357-229">[目录视图 (Transact-SQL)](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7d357-229">[Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql) </span></span>  
 [<span data-ttu-id="7d357-230">兼容性视图 (Transact SQL)</span><span class="sxs-lookup"><span data-stu-id="7d357-230">Compatibility Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql)  
  
  
