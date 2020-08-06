---
title: 创建服务器审核和数据库审核规范 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlaudit.dbaudit.general.f1
helpviewer_keywords:
- audits [SQL Server], creating database specification
- database audit [SQL Server]
ms.assetid: 26ee85de-6e97-4318-b526-900924d96e62
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0cad01eae45d534f0f74911ce8f57827858cc920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689833"
---
# <a name="create-a-server-audit-and-database-audit-specification"></a><span data-ttu-id="e7ced-102">创建服务器审核规范和数据库审核规范</span><span class="sxs-lookup"><span data-stu-id="e7ced-102">Create a Server Audit and Database Audit Specification</span></span>
  <span data-ttu-id="e7ced-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中创建服务器审核和数据库审核规范。</span><span class="sxs-lookup"><span data-stu-id="e7ced-103">This topic describes how to create a server audit and database audit specification in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e7ced-104">“  审核” [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库涉及到跟踪和记录系统中发生的事件。</span><span class="sxs-lookup"><span data-stu-id="e7ced-104">*Auditing* an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database involves tracking and logging events that occur on the system.</span></span> <span data-ttu-id="e7ced-105">*SQL Server Audit* 对象收集单个服务器实例或数据库级操作和操作组以进行监视。</span><span class="sxs-lookup"><span data-stu-id="e7ced-105">The *SQL Server Audit* object collects a single instance of server- or database-level actions and groups of actions to monitor.</span></span> <span data-ttu-id="e7ced-106">这种审核处于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例级别。</span><span class="sxs-lookup"><span data-stu-id="e7ced-106">The audit is at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance level.</span></span> <span data-ttu-id="e7ced-107">每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例可以具有多个审核。</span><span class="sxs-lookup"><span data-stu-id="e7ced-107">You can have multiple audits per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="e7ced-108">*数据库级别审核规范* 对象属于审核。</span><span class="sxs-lookup"><span data-stu-id="e7ced-108">The *Database-Level Audit Specification* object belongs to an audit.</span></span> <span data-ttu-id="e7ced-109">针对每个审核，您可以为每个 SQL Server 数据库创建一个数据库审核规范。</span><span class="sxs-lookup"><span data-stu-id="e7ced-109">You can create one database audit specification per SQL Server database per audit.</span></span> <span data-ttu-id="e7ced-110">有关详细信息，请参阅 [SQL Server Audit（数据库引擎）](sql-server-audit-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ced-110">For more information, see [SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md).</span></span>  
  
 <span data-ttu-id="e7ced-111">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e7ced-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e7ced-112">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e7ced-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e7ced-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e7ced-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e7ced-114">安全性</span><span class="sxs-lookup"><span data-stu-id="e7ced-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e7ced-115">**若要创建服务器审核规范和数据库审核规范，请使用：**</span><span class="sxs-lookup"><span data-stu-id="e7ced-115">**To create a server audit and database audit specification, using:**</span></span>  
  
     [<span data-ttu-id="e7ced-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e7ced-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e7ced-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e7ced-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e7ced-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="e7ced-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e7ced-119">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e7ced-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e7ced-120">数据库审核规范是驻留在给定数据库中的非安全对象。</span><span class="sxs-lookup"><span data-stu-id="e7ced-120">Database audit specifications are non-securable objects that reside in a given database.</span></span> <span data-ttu-id="e7ced-121">数据库审核规范在创建之后处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="e7ced-121">When a database audit specification is created, it is in a disabled state.</span></span>  
  
 <span data-ttu-id="e7ced-122">当您在用户数据库中创建或修改数据库审核规范时，不要包括针对服务器范围对象（例如系统视图）的审核操作。</span><span class="sxs-lookup"><span data-stu-id="e7ced-122">When you are creating or modifying a database audit specification in a user database, do not include audit actions on server-scope objects, such as the system views.</span></span> <span data-ttu-id="e7ced-123">如果包括服务器范围的对象，将会创建审核。</span><span class="sxs-lookup"><span data-stu-id="e7ced-123">If server-scoped objects are included, the audit will be created.</span></span> <span data-ttu-id="e7ced-124">但是，服务器范围对象将不包括，并且将不返回任何错误。</span><span class="sxs-lookup"><span data-stu-id="e7ced-124">However, the server-scoped objects will not be included, and no error will be returned.</span></span> <span data-ttu-id="e7ced-125">若要审核服务器范围的对象，请使用 master 数据库中的数据库审核规范。</span><span class="sxs-lookup"><span data-stu-id="e7ced-125">To audit server-scope objects, use a database audit specification in the master database.</span></span>  
  
 <span data-ttu-id="e7ced-126">数据库审核规范位于创建它们的数据库（`tempdb` 系统数据库除外）中。</span><span class="sxs-lookup"><span data-stu-id="e7ced-126">Database audit specifications reside in the database where they are created, with the exception of the `tempdb` system database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e7ced-127">Security</span><span class="sxs-lookup"><span data-stu-id="e7ced-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e7ced-128">权限</span><span class="sxs-lookup"><span data-stu-id="e7ced-128">Permissions</span></span>  
  
-   <span data-ttu-id="e7ced-129">具有 ALTER ANY DATABASE AUDIT 权限的用户可以创建数据库审核规范并将其绑定到任何审核。</span><span class="sxs-lookup"><span data-stu-id="e7ced-129">Users with the ALTER ANY DATABASE AUDIT permission can create database audit specifications and bind them to any audit.</span></span>  
  
-   <span data-ttu-id="e7ced-130">创建数据库审核规范后，具有 CONTROL SERVER 或 ALTER ANY DATABASE AUDIT 权限的主体或 sysadmin 帐户即可查看该规范。</span><span class="sxs-lookup"><span data-stu-id="e7ced-130">After a database audit specification is created, it can be viewed by principals with the CONTROL SERVER,  ALTER ANY DATABASE AUDIT permissions, or the sysadmin account.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e7ced-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e7ced-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="e7ced-132">创建服务器审核</span><span class="sxs-lookup"><span data-stu-id="e7ced-132">To create a server audit</span></span>  
  
1.  <span data-ttu-id="e7ced-133"> 在对象资源管理器中，展开“安全性”文件夹。</span><span class="sxs-lookup"><span data-stu-id="e7ced-133">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="e7ced-134">右键单击 "**审核**" 文件夹，然后选择 "**新建审核 ...**"。有关详细信息，请参阅[创建服务器审核和服务器审核规范](create-a-server-audit-and-server-audit-specification.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ced-134">Right-click the **Audits** folder and select **New Audit...**. For more information, see [Create a Server Audit and Server Audit Specification](create-a-server-audit-and-server-audit-specification.md).</span></span>  
  
3.  <span data-ttu-id="e7ced-135">在完成选项选择后，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="e7ced-135">When you are finished selecting options, click **OK**.</span></span>  
  
#### <a name="to-create-a-database-level-audit-specification"></a><span data-ttu-id="e7ced-136">创建数据库级别审核规范</span><span class="sxs-lookup"><span data-stu-id="e7ced-136">To create a database-level audit specification</span></span>  
  
1.  <span data-ttu-id="e7ced-137">在“对象资源管理器”中，展开要创建审核规范的数据库。</span><span class="sxs-lookup"><span data-stu-id="e7ced-137">In Object Explorer, expand the database where you want to create an audit specification.</span></span>  
  
2.  <span data-ttu-id="e7ced-138">展开 **“安全性”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e7ced-138">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="e7ced-139">右键单击 "**数据库审核规范**" 文件夹，然后选择 "**新建数据库审核规范 ...**"。</span><span class="sxs-lookup"><span data-stu-id="e7ced-139">Right-click the **Database Audit Specifications** folder and select **New Database Audit Specification...**.</span></span>  
  
     <span data-ttu-id="e7ced-140">**“创建数据库审核规范”** 对话框中提供了以下选项。</span><span class="sxs-lookup"><span data-stu-id="e7ced-140">The following options are available on the **Create Database Audit Specification** dialog box.</span></span>  
  
     <span data-ttu-id="e7ced-141">**名称**</span><span class="sxs-lookup"><span data-stu-id="e7ced-141">**Name**</span></span>  
     <span data-ttu-id="e7ced-142">数据库审核规范的名称。</span><span class="sxs-lookup"><span data-stu-id="e7ced-142">The name of the database audit specification.</span></span> <span data-ttu-id="e7ced-143">这是在创建新服务器审核规范时自动生成的，但是您可以对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="e7ced-143">This is generated automatically when you create a new server audit specification but is editable.</span></span>  
  
     <span data-ttu-id="e7ced-144">**审核**</span><span class="sxs-lookup"><span data-stu-id="e7ced-144">**Audit**</span></span>  
     <span data-ttu-id="e7ced-145">现有数据库审核的名称。</span><span class="sxs-lookup"><span data-stu-id="e7ced-145">The name of an existing database audit.</span></span> <span data-ttu-id="e7ced-146">或者键入审核的名称，或者从列表中选择一个名称。</span><span class="sxs-lookup"><span data-stu-id="e7ced-146">Either type in the name of the audit or select it from the list.</span></span>  
  
     <span data-ttu-id="e7ced-147">**审核操作类型**</span><span class="sxs-lookup"><span data-stu-id="e7ced-147">**Audit Action Type**</span></span>  
     <span data-ttu-id="e7ced-148">指定要捕获的数据库级别审核操作组和审核操作。</span><span class="sxs-lookup"><span data-stu-id="e7ced-148">Specifies the database-level audit action groups and audit actions to capture.</span></span> <span data-ttu-id="e7ced-149">有关数据库级别审核操作组和审核操作的列表以及它们所包含事件的说明，请参阅 [SQL Server 审核操作组和操作](sql-server-audit-action-groups-and-actions.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ced-149">For the list of database-level audit action groups and audit actions and a description of the events they contain, see [SQL Server Audit Action Groups and Actions](sql-server-audit-action-groups-and-actions.md).</span></span>  
  
     <span data-ttu-id="e7ced-150">**对象架构**</span><span class="sxs-lookup"><span data-stu-id="e7ced-150">**Object Schema**</span></span>  
     <span data-ttu-id="e7ced-151">显示具有指定“对象名称”  的对象的架构。</span><span class="sxs-lookup"><span data-stu-id="e7ced-151">Displays the schema for the specified **Object Name**.</span></span>  
  
     <span data-ttu-id="e7ced-152">**Object Name**</span><span class="sxs-lookup"><span data-stu-id="e7ced-152">**Object Name**</span></span>  
     <span data-ttu-id="e7ced-153">要审核的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="e7ced-153">The name of the object to audit.</span></span> <span data-ttu-id="e7ced-154">这仅适用于审核操作，而不适用于审核组。</span><span class="sxs-lookup"><span data-stu-id="e7ced-154">This is only available for audit actions; it does not apply to audit groups.</span></span>  
  
     <span data-ttu-id="e7ced-155">**省略号 (...)**</span><span class="sxs-lookup"><span data-stu-id="e7ced-155">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="e7ced-156">打开 **“选择对象”** 对话框，以便基于指定的 **“审核操作类型”** 浏览和选择可用对象。</span><span class="sxs-lookup"><span data-stu-id="e7ced-156">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Audit Action Type**.</span></span>  
  
     <span data-ttu-id="e7ced-157">**主体名称**</span><span class="sxs-lookup"><span data-stu-id="e7ced-157">**Principal Name**</span></span>  
     <span data-ttu-id="e7ced-158">对于所审核的对象，要作为审核筛选依据的帐户。</span><span class="sxs-lookup"><span data-stu-id="e7ced-158">The account to filter the audit by for the object being audited.</span></span>  
  
     <span data-ttu-id="e7ced-159">**省略号 (...)**</span><span class="sxs-lookup"><span data-stu-id="e7ced-159">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="e7ced-160">打开 **“选择对象”** 对话框以基于指定的 **“对象名称”** 浏览和选择可用对象。</span><span class="sxs-lookup"><span data-stu-id="e7ced-160">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Object Name**.</span></span>  
  
4.  <span data-ttu-id="e7ced-161">在完成选项选择后，请单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e7ced-161">When you are finished selecting option, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e7ced-162">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e7ced-162">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="e7ced-163">创建服务器审核</span><span class="sxs-lookup"><span data-stu-id="e7ced-163">To create a server audit</span></span>  
  
1.  <span data-ttu-id="e7ced-164">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e7ced-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e7ced-165">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e7ced-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e7ced-166">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e7ced-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE master ;  
    GO  
    -- Create the server audit.   
    CREATE SERVER AUDIT Payrole_Security_Audit  
        TO FILE ( FILEPATH =   
    'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA' ) ;   
    GO  
    -- Enable the server audit.   
    ALTER SERVER AUDIT Payrole_Security_Audit   
    WITH (STATE = ON) ;  
    ```  
  
#### <a name="to-create-a-database-level-audit-specification"></a><span data-ttu-id="e7ced-167">创建数据库级别审核规范</span><span class="sxs-lookup"><span data-stu-id="e7ced-167">To create a database-level audit specification</span></span>  
  
1.  <span data-ttu-id="e7ced-168">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e7ced-168">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e7ced-169">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e7ced-169">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e7ced-170">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e7ced-170">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e7ced-171">该示例创建名为 `Audit_Pay_Tables` 的服务器审核规范，该规范针对 `dbo` 表，基于上面定义的服务器审核对用户 `HumanResources.EmployeePayHistory` 发出的 SELECT 和 INSERT 语句进行审核。</span><span class="sxs-lookup"><span data-stu-id="e7ced-171">The example creates a database audit specification called `Audit_Pay_Tables` that audits SELECT and INSERT statements by the `dbo` user, for the `HumanResources.EmployeePayHistory` table based on the server audit defined above.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    -- Create the database audit specification.   
    CREATE DATABASE AUDIT SPECIFICATION Audit_Pay_Tables  
    FOR SERVER AUDIT Payrole_Security_Audit  
    ADD (SELECT , INSERT  
         ON HumanResources.EmployeePayHistory BY dbo )   
    WITH (STATE = ON) ;   
    GO  
  
    ```  
  
 <span data-ttu-id="e7ced-172">有关详细信息，请参阅 [CREATE SERVER AUDIT (Transact-SQL)](/sql/t-sql/statements/create-server-audit-transact-sql) 和 [CREATE DATABASE AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/create-database-audit-specification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e7ced-172">For more information, see [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) and [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-audit-specification-transact-sql).</span></span>  
  
  
