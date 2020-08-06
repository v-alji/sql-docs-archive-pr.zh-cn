---
title: 启用索引和约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], enabling
- nonclustered indexes [SQL Server], enabling a disabled index
- index enabling [SQL Server]
- disabled indexes [SQL Server], how to enable
- constraints [SQL Server], enabling
- clustered indexes, enabling disabled indexes
ms.assetid: c55c8865-322e-4ab0-ba04-ea1f56735353
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d4e79689b80a40d00958fa557fe51df2adf9c14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590804"
---
# <a name="enable-indexes-and-constraints"></a><span data-ttu-id="fc1be-102">启用索引和约束</span><span class="sxs-lookup"><span data-stu-id="fc1be-102">Enable Indexes and Constraints</span></span>
  <span data-ttu-id="fc1be-103">本主题介绍了如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中启用已禁用的索引。</span><span class="sxs-lookup"><span data-stu-id="fc1be-103">This topic describes how to enable a disabled index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fc1be-104">索引被禁用后一直保持禁用状态，直到它重新生成或删除。</span><span class="sxs-lookup"><span data-stu-id="fc1be-104">After an index is disabled, it remains in a disabled state until it is rebuilt or dropped</span></span>  
  
 <span data-ttu-id="fc1be-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="fc1be-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fc1be-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="fc1be-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fc1be-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="fc1be-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fc1be-108">安全性</span><span class="sxs-lookup"><span data-stu-id="fc1be-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fc1be-109">**若要启用禁用的索引，请使用：**</span><span class="sxs-lookup"><span data-stu-id="fc1be-109">**To enable a disabled index, using:**</span></span>  
  
     [<span data-ttu-id="fc1be-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fc1be-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fc1be-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fc1be-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fc1be-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="fc1be-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fc1be-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="fc1be-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fc1be-114">在索引重新生成之后，任何因禁用索引而被禁用的约束必须手动将其启用。</span><span class="sxs-lookup"><span data-stu-id="fc1be-114">After rebuilding the index, any constraints that were disabled because of disabling the index must be manually enabled.</span></span> <span data-ttu-id="fc1be-115">PRIMARY KEY 和 UNIQUE 约束可通过重新生成相关联的索引来启用。</span><span class="sxs-lookup"><span data-stu-id="fc1be-115">PRIMARY KEY and UNIQUE constraints are enabled by rebuilding the associated index.</span></span> <span data-ttu-id="fc1be-116">您必须重新生成（启用）索引才能启用引用 PRIMARY KEY 或 UNIQUE 约束的 FOREIGN KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="fc1be-116">This index must be rebuilt (enabled) before you can enable FOREIGN KEY constraints that reference the PRIMARY KEY or UNIQUE constraint.</span></span> <span data-ttu-id="fc1be-117">FOREIGN KEY 约束可使用 ALTER TABLE CHECK CONSTRAINT 语句来启用。</span><span class="sxs-lookup"><span data-stu-id="fc1be-117">FOREIGN KEY constraints are enabled by using the ALTER TABLE CHECK CONSTRAINT statement.</span></span>  
  
-   <span data-ttu-id="fc1be-118">当 ONLINE 选项设置为 ON 时，不能重新生成禁用的聚集索引。</span><span class="sxs-lookup"><span data-stu-id="fc1be-118">Rebuilding a disabled clustered index cannot be performed when the ONLINE option is set to ON.</span></span>  
  
-   <span data-ttu-id="fc1be-119">当禁用或启用聚集索引，禁用非聚集索引时，对聚集索引操作会对禁用的非聚集索引有如下影响。</span><span class="sxs-lookup"><span data-stu-id="fc1be-119">When the clustered index is disabled or enabled and the nonclustered index is disabled, the clustered index action has the following results on the disabled nonclustered index.</span></span>  
  
    |<span data-ttu-id="fc1be-120">聚集索引操作</span><span class="sxs-lookup"><span data-stu-id="fc1be-120">Clustered Index Action</span></span>|<span data-ttu-id="fc1be-121">禁用的非聚集索引…</span><span class="sxs-lookup"><span data-stu-id="fc1be-121">Disabled Nonclustered Index ...</span></span>|  
    |----------------------------|-----------------------------------|  
    |<span data-ttu-id="fc1be-122">ALTER INDEX REBUILD。</span><span class="sxs-lookup"><span data-stu-id="fc1be-122">ALTER INDEX REBUILD.</span></span>|<span data-ttu-id="fc1be-123">保持禁用状态。</span><span class="sxs-lookup"><span data-stu-id="fc1be-123">Remains disabled.</span></span>|  
    |<span data-ttu-id="fc1be-124">ALTER INDEX ALL REBUILD。</span><span class="sxs-lookup"><span data-stu-id="fc1be-124">ALTER INDEX ALL REBUILD.</span></span>|<span data-ttu-id="fc1be-125">重新生成或启用。</span><span class="sxs-lookup"><span data-stu-id="fc1be-125">Is rebuilt and enabled.</span></span>|  
    |<span data-ttu-id="fc1be-126">DROP INDEX。</span><span class="sxs-lookup"><span data-stu-id="fc1be-126">DROP INDEX.</span></span>|<span data-ttu-id="fc1be-127">保持禁用状态。</span><span class="sxs-lookup"><span data-stu-id="fc1be-127">Remains disabled.</span></span>|  
    |<span data-ttu-id="fc1be-128">CREATE INDEX WITH DROP_EXISTING。</span><span class="sxs-lookup"><span data-stu-id="fc1be-128">CREATE INDEX WITH DROP_EXISTING.</span></span>|<span data-ttu-id="fc1be-129">保持禁用状态。</span><span class="sxs-lookup"><span data-stu-id="fc1be-129">Remains disabled.</span></span>|  
  
     <span data-ttu-id="fc1be-130">创建一个新的聚集索引，其行为与 ALTER INDEX ALL REBUILD 相同。</span><span class="sxs-lookup"><span data-stu-id="fc1be-130">Creating a new clustered index, behaves the same as ALTER INDEX ALL REBUILD.</span></span>  
  
-   <span data-ttu-id="fc1be-131">与聚集索引相关联的非聚集索引允许的操作，取决于这两种索引类型的状态是禁用还是启用。</span><span class="sxs-lookup"><span data-stu-id="fc1be-131">Allowed actions on nonclustered indexes associated with a clustered index depend on the state, whether disabled or enabled, of both index types.</span></span> <span data-ttu-id="fc1be-132">下表概括了非聚集索引允许的操作。</span><span class="sxs-lookup"><span data-stu-id="fc1be-132">The following table summarizes the allowed actions on nonclustered indexes.</span></span>  
  
    |<span data-ttu-id="fc1be-133">非聚集索引操作</span><span class="sxs-lookup"><span data-stu-id="fc1be-133">Nonclustered Index Action</span></span>|<span data-ttu-id="fc1be-134">聚集和非聚集索引均禁用时。</span><span class="sxs-lookup"><span data-stu-id="fc1be-134">When both the clustered and nonclustered indexes are disabled.</span></span>|<span data-ttu-id="fc1be-135">聚集索引启用而非聚集索引处于禁用或启用中的任一状态时。</span><span class="sxs-lookup"><span data-stu-id="fc1be-135">When the clustered index is enabled and the nonclustered index is in either state.</span></span>|  
    |-------------------------------|--------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
    |<span data-ttu-id="fc1be-136">ALTER INDEX REBUILD。</span><span class="sxs-lookup"><span data-stu-id="fc1be-136">ALTER INDEX REBUILD.</span></span>|<span data-ttu-id="fc1be-137">操作失败。</span><span class="sxs-lookup"><span data-stu-id="fc1be-137">The action fails.</span></span>|<span data-ttu-id="fc1be-138">操作成功。</span><span class="sxs-lookup"><span data-stu-id="fc1be-138">The action succeeds.</span></span>|  
    |<span data-ttu-id="fc1be-139">DROP INDEX。</span><span class="sxs-lookup"><span data-stu-id="fc1be-139">DROP INDEX.</span></span>|<span data-ttu-id="fc1be-140">操作成功。</span><span class="sxs-lookup"><span data-stu-id="fc1be-140">The action succeeds.</span></span>|<span data-ttu-id="fc1be-141">操作成功。</span><span class="sxs-lookup"><span data-stu-id="fc1be-141">The action succeeds.</span></span>|  
    |<span data-ttu-id="fc1be-142">CREATE INDEX WITH DROP_EXISTING。</span><span class="sxs-lookup"><span data-stu-id="fc1be-142">CREATE INDEX WITH DROP_EXISTING.</span></span>|<span data-ttu-id="fc1be-143">操作失败。</span><span class="sxs-lookup"><span data-stu-id="fc1be-143">The action fails.</span></span>|<span data-ttu-id="fc1be-144">操作成功。</span><span class="sxs-lookup"><span data-stu-id="fc1be-144">The action succeeds.</span></span>|  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fc1be-145">Security</span><span class="sxs-lookup"><span data-stu-id="fc1be-145">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fc1be-146">权限</span><span class="sxs-lookup"><span data-stu-id="fc1be-146">Permissions</span></span>  
 <span data-ttu-id="fc1be-147">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="fc1be-147">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="fc1be-148">如果使用 DBCC DBREINDEX，用户必须拥有该表，或者是 **sysadmin** 固定服务器角色或者 **db_ddladmin** 和 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="fc1be-148">If using DBCC DBREINDEX, eser must either own the table or be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fc1be-149">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fc1be-149">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-a-disabled-index"></a><span data-ttu-id="fc1be-150">启用禁用的索引</span><span class="sxs-lookup"><span data-stu-id="fc1be-150">To enable a disabled index</span></span>  
  
1.  <span data-ttu-id="fc1be-151">在对象资源管理器中，单击加号以便展开包含您要启用索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="fc1be-151">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to enable an index.</span></span>  
  
2.  <span data-ttu-id="fc1be-152">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fc1be-152">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="fc1be-153">单击加号以便展开您要启用索引的表。</span><span class="sxs-lookup"><span data-stu-id="fc1be-153">Click the plus sign to expand the table on which you want to enable an index.</span></span>  
  
4.  <span data-ttu-id="fc1be-154">单击加号以便展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fc1be-154">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="fc1be-155">右键单击要启用的索引，然后选择\*\*\*\*“重新生成”。</span><span class="sxs-lookup"><span data-stu-id="fc1be-155">Right-click the index you want to enable and select **Rebuild**.</span></span>  
  
6.  <span data-ttu-id="fc1be-156">在 **“重新生成索引”** 对话框中，确认正确的索引位于 **“要重新生成的索引”** 网格中，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="fc1be-156">In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to rebuild** grid and click **OK**.</span></span>  
  
#### <a name="to-enable-all-indexes-on-a-table"></a><span data-ttu-id="fc1be-157">为表启用所有索引</span><span class="sxs-lookup"><span data-stu-id="fc1be-157">To enable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="fc1be-158">在对象资源管理器中，单击加号以便展开包含您要启用索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="fc1be-158">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to enable the indexes.</span></span>  
  
2.  <span data-ttu-id="fc1be-159">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fc1be-159">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="fc1be-160">单击加号以便展开您要启用索引的表。</span><span class="sxs-lookup"><span data-stu-id="fc1be-160">Click the plus sign to expand the table on which you want to enable the indexes.</span></span>  
  
4.  <span data-ttu-id="fc1be-161">右键单击\*\*\*\*“索引”文件夹，然后选择\*\*\*\*“全部重新生成”。</span><span class="sxs-lookup"><span data-stu-id="fc1be-161">Right-click the **Indexes** folder and select **Rebuild All**.</span></span>  
  
5.  <span data-ttu-id="fc1be-162">在 **“重新生成索引”** 对话框中，确认正确的索引位于 **“要重新生成的索引”** 网格中，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="fc1be-162">In the **Rebuild Indexes** dialog box, verify that the correct indexes are in the **Indexes to rebuild** grid and click **OK**.</span></span> <span data-ttu-id="fc1be-163">若要从 **“要重新生成的索引”** 网格中删除索引，请选择该索引，再按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="fc1be-163">To remove an index from the **Indexes to rebuild** grid, select the index and then press the Delete key.</span></span>  
  
 <span data-ttu-id="fc1be-164">在 **“重新生成索引”** 对话框中将提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="fc1be-164">The following information is available in the **Rebuild Indexes** dialog box:</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fc1be-165">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fc1be-165">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-a-disabled-index-using-alter-index"></a><span data-ttu-id="fc1be-166">使用 ALTER INDEX 启用已禁用的索引</span><span class="sxs-lookup"><span data-stu-id="fc1be-166">To enable a disabled index using ALTER INDEX</span></span>  
  
1.  <span data-ttu-id="fc1be-167">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="fc1be-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fc1be-168">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="fc1be-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fc1be-169">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="fc1be-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Enables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table.  
  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    REBUILD;   
    GO  
    ```  
  
#### <a name="to-enable-a-disabled-index-using-create-index"></a><span data-ttu-id="fc1be-170">使用 CREATE INDEX 启用已禁用的索引</span><span class="sxs-lookup"><span data-stu-id="fc1be-170">To enable a disabled index using CREATE INDEX</span></span>  
  
1.  <span data-ttu-id="fc1be-171">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="fc1be-171">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fc1be-172">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="fc1be-172">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fc1be-173">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="fc1be-173">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- re-creates the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    -- using the OrganizationLevel and OrganizationNode columns  
    -- and then deletes the existing IX_Employee_OrganizationLevel_OrganizationNode index  
    CREATE INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
       (OrganizationLevel, OrganizationNode)  
    WITH (DROP_EXISTING = ON);  
    GO  
    ```  
  
#### <a name="to-enable-a-disabled-index-using-dbcc-dbreindex"></a><span data-ttu-id="fc1be-174">使用 DBCC DBREINDEX 启用已禁用的索引</span><span class="sxs-lookup"><span data-stu-id="fc1be-174">To enable a disabled index using DBCC DBREINDEX</span></span>  
  
1.  <span data-ttu-id="fc1be-175">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="fc1be-175">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fc1be-176">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="fc1be-176">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fc1be-177">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="fc1be-177">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- enables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    DBCC DBREINDEX ("HumanResources.Employee", IX_Employee_OrganizationLevel_OrganizationNode);  
    GO  
    ```  
  
#### <a name="to-enable-all-indexes-on-a-table-using-alter-index"></a><span data-ttu-id="fc1be-178">使用 ALTER INDEX 启用表上的所有索引</span><span class="sxs-lookup"><span data-stu-id="fc1be-178">To enable all indexes on a table using ALTER INDEX</span></span>  
  
1.  <span data-ttu-id="fc1be-179">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="fc1be-179">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fc1be-180">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="fc1be-180">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fc1be-181">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="fc1be-181">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- enables all indexes  
    -- on the HumanResources.Employee table  
    ALTER INDEX ALL ON HumanResources.Employee  
    REBUILD;  
    GO  
    ```  
  
#### <a name="to-enable-all-indexes-on-a-table-using-dbcc-dbreindex"></a><span data-ttu-id="fc1be-182">使用 DBCC DBREINDEX 启用表上的所有索引</span><span class="sxs-lookup"><span data-stu-id="fc1be-182">To enable all indexes on a table using DBCC DBREINDEX</span></span>  
  
1.  <span data-ttu-id="fc1be-183">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="fc1be-183">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fc1be-184">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="fc1be-184">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fc1be-185">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="fc1be-185">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- enables all indexes  
    -- on the HumanResources.Employee table  
    DBCC DBREINDEX ("HumanResources.Employee", " ");  
    GO  
    ```  
  
 <span data-ttu-id="fc1be-186">有关详细信息，请参阅 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)、[CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql) 和 [DBCC DBREINDEX (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fc1be-186">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql), [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql), and [DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql).</span></span>  
  
  
