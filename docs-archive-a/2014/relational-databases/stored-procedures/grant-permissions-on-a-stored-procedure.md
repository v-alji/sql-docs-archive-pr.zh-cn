---
title: 授予对存储过程的权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], permissions
ms.assetid: a7d15816-a788-4099-ad91-dc4b26618299
author: stevestein
ms.author: sstein
ms.openlocfilehash: 23ea130b9d2033128adc99413c053d66936e3ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587267"
---
# <a name="grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="c266f-102">授予对存储过程的权限</span><span class="sxs-lookup"><span data-stu-id="c266f-102">Grant Permissions on a Stored Procedure</span></span>
  <span data-ttu-id="c266f-103">本主题说明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]授予对存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="c266f-103">This topic describes how to grant permissions on a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c266f-104">可以为数据库中的现有用户、数据库角色或应用程序角色授予权限。</span><span class="sxs-lookup"><span data-stu-id="c266f-104">Permissions can be granted to an existing user, database role, or application role in the database.</span></span>  
  
 <span data-ttu-id="c266f-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="c266f-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c266f-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="c266f-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c266f-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="c266f-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c266f-108">安全性</span><span class="sxs-lookup"><span data-stu-id="c266f-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c266f-109">**若要授予对存储过程的权限，请使用：**</span><span class="sxs-lookup"><span data-stu-id="c266f-109">**To grant permissions on a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="c266f-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c266f-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c266f-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c266f-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c266f-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="c266f-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c266f-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="c266f-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c266f-114">不能使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 授予对系统过程或系统函数的权限。</span><span class="sxs-lookup"><span data-stu-id="c266f-114">You cannot use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to grant permissions on system procedures or system functions.</span></span> <span data-ttu-id="c266f-115">改为使用 [GRANT 对象权限](/sql/t-sql/statements/grant-object-permissions-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="c266f-115">Use [GRANT Object Permissions](/sql/t-sql/statements/grant-object-permissions-transact-sql) instead.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c266f-116">Security</span><span class="sxs-lookup"><span data-stu-id="c266f-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c266f-117">权限</span><span class="sxs-lookup"><span data-stu-id="c266f-117">Permissions</span></span>  
 <span data-ttu-id="c266f-118">授权者（或用 AS 选项指定的主体）必须具有带 GRANT OPTION 的相同权限，或具有隐含所授予权限的更高权限。</span><span class="sxs-lookup"><span data-stu-id="c266f-118">The grantor (or the principal specified with the AS option) must have either the permission itself with GRANT OPTION, or a higher permission that implies the permission being granted.</span></span> <span data-ttu-id="c266f-119">需要拥有对该过程所属架构的 ALTER 权限，或对该过程的 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="c266f-119">Requires ALTER permission on the schema to which the procedure belongs, or CONTROL permission on the procedure.</span></span> <span data-ttu-id="c266f-120">有关详细信息，请参阅 [GRANT 对象权限 (Transact-SQL)](/sql/t-sql/statements/grant-object-permissions-transact-sql)授予对存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="c266f-120">For more information, see [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c266f-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c266f-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="c266f-122">授予对存储过程的权限</span><span class="sxs-lookup"><span data-stu-id="c266f-122">To grant permissions on a stored procedure</span></span>  
  
1.  <span data-ttu-id="c266f-123">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="c266f-123">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="c266f-124">展开 **“数据库”** 、过程所属的数据库以及 **“可编程性”** 。</span><span class="sxs-lookup"><span data-stu-id="c266f-124">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="c266f-125">展开“存储过程”，右键单击要针对其授予权限的过程，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="c266f-125">Expand **Stored Procedures**, right-click the procedure to grant permissions on, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="c266f-126">在 **“存储过程属性”** 中，选择 **“权限”** 页。</span><span class="sxs-lookup"><span data-stu-id="c266f-126">From **Stored Procedure Properties**, select the **Permissions** page.</span></span>  
  
5.  <span data-ttu-id="c266f-127">若要为用户、数据库角色或应用程序角色授予权限，请单击 **“搜索”** 。</span><span class="sxs-lookup"><span data-stu-id="c266f-127">To grant permissions to a user, database role, or application role, click **Search**.</span></span>  
  
6.  <span data-ttu-id="c266f-128">在 **“选择用户或角色”** 中，单击 **“对象类型”** 以添加或清除所需的用户和角色。</span><span class="sxs-lookup"><span data-stu-id="c266f-128">In **Select Users or Roles**, click **Object Types** to add or clear the users and roles you want.</span></span>  
  
7.  <span data-ttu-id="c266f-129">单击 **”浏览“** 以显示用户或角色列表。</span><span class="sxs-lookup"><span data-stu-id="c266f-129">Click **Browse** to display the list of users or roles.</span></span> <span data-ttu-id="c266f-130">选择应对其授予权限的用户或角色。</span><span class="sxs-lookup"><span data-stu-id="c266f-130">Select the users or roles to whom permissions should be granted.</span></span>  
  
8.  <span data-ttu-id="c266f-131">在 **“显式权限”** 网格中，选择要为指定的用户或角色授予的权限。</span><span class="sxs-lookup"><span data-stu-id="c266f-131">In the **Explicit Permissions** grid, select the permissions to grant to the specified user or role.</span></span> <span data-ttu-id="c266f-132">有关权限的说明，请参阅[权限（数据库引擎）](../security/permissions-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="c266f-132">For a description of the permissions, see [Permissions &#40;Database Engine&#41;](../security/permissions-database-engine.md).</span></span>  
  
 <span data-ttu-id="c266f-133">选择 **“授予”** 指示要为被授权者授予指定的权限。</span><span class="sxs-lookup"><span data-stu-id="c266f-133">Selecting **Grant** indicates the grantee will be given the specified permission.</span></span> <span data-ttu-id="c266f-134">选择 **“具有授予权限”** 指示被授权者还可以将指定权限授予其他主体。</span><span class="sxs-lookup"><span data-stu-id="c266f-134">Selecting **Grant With** indicates that the grantee will also be able to grant the specified permission to other principals.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c266f-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c266f-135">Using Transact-SQL</span></span>  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="c266f-136">授予对存储过程的权限</span><span class="sxs-lookup"><span data-stu-id="c266f-136">To grant permissions on a stored procedure</span></span>  
  
1.  <span data-ttu-id="c266f-137">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c266f-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c266f-138">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="c266f-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c266f-139">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="c266f-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c266f-140">该示例授予名为 `EXECUTE` 的应用程序角色对存储过程 `HumanResources.uspUpdateEmployeeHireInfo` 的 `Recruiting11`权限。</span><span class="sxs-lookup"><span data-stu-id="c266f-140">This example grants `EXECUTE` permission on the stored procedure `HumanResources.uspUpdateEmployeeHireInfo` to an application role named `Recruiting11`.</span></span>  
  
```sql  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="c266f-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c266f-141">See Also</span></span>  
 <span data-ttu-id="c266f-142">[sys.fn_builtin_permissions (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c266f-142">[sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) </span></span>  
 <span data-ttu-id="c266f-143">[GRANT 对象权限 (Transact-SQL)](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c266f-143">[GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span></span>  
 <span data-ttu-id="c266f-144">[创建存储过程](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c266f-144">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="c266f-145">[修改存储过程](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c266f-145">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="c266f-146">[删除存储过程](../stored-procedures/delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c266f-146">[Delete a Stored Procedure](../stored-procedures/delete-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="c266f-147">重命名存储过程</span><span class="sxs-lookup"><span data-stu-id="c266f-147">Rename a Stored Procedure</span></span>](rename-a-stored-procedure.md)  
  
  
