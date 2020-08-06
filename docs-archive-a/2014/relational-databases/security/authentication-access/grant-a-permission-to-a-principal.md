---
title: 向主体授予权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Grant permission to a principal
ms.assetid: 4107389d-05b6-4aa3-9fa8-95b40cdf05dc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4256d62bdeac2d79c51e5f3792c991e0e3b15096
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693705"
---
# <a name="grant-a-permission-to-a-principal"></a><span data-ttu-id="ef4a3-102">向主体授予权限</span><span class="sxs-lookup"><span data-stu-id="ef4a3-102">Grant a Permission to a Principal</span></span>
  <span data-ttu-id="ef4a3-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中对主体授予权限。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-103">This topic describes how to grant permission to a principal in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ef4a3-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ef4a3-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ef4a3-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ef4a3-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ef4a3-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ef4a3-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ef4a3-107">安全性</span><span class="sxs-lookup"><span data-stu-id="ef4a3-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ef4a3-108">**若要向主体授予权限，请使用：**</span><span class="sxs-lookup"><span data-stu-id="ef4a3-108">**To grant permission to a principal, using:**</span></span>  
  
     [<span data-ttu-id="ef4a3-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ef4a3-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ef4a3-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ef4a3-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ef4a3-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="ef4a3-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ef4a3-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ef4a3-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ef4a3-113">请考虑以下可以使管理权限更简单的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-113">Consider the following best practices that can make managing permissions easier.</span></span>  
  
-   <span data-ttu-id="ef4a3-114">将权限授予角色，而不是单独的登录名或用户。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-114">Grant permission to roles, instead of individual logins or users.</span></span> <span data-ttu-id="ef4a3-115">当某个用户由其他人取代时，可从角色中删除离开的用户，并向角色中添加新用户。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-115">When one individual is replaced by another, remove the departing individual from the role and add the new individual to the role.</span></span> <span data-ttu-id="ef4a3-116">与该角色关联的许多权限都将自动应用于新用户。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-116">The many permissions that might be associated with the role will automatically be available to the new individual.</span></span> <span data-ttu-id="ef4a3-117">如果组织中的多个用户需要相同的权限，将他们都添加到角色即可为他们授予相同的权限。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-117">If several people in an organization require the same permissions, adding each of them to the role will grant them the same permissions.</span></span>  
  
-   <span data-ttu-id="ef4a3-118">对类似的安全对象（表、视图和过程）进行配置，使它们属于同一个架构，然后向架构授予权限。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-118">Configure similar securables (tables, views, and procedures) to be owned by a schema, then grant permissions to the schema.</span></span> <span data-ttu-id="ef4a3-119">例如，工资架构可能拥有多个表、视图和存储过程。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-119">For example, the payroll schema might own several tables, views, and stored procedures.</span></span> <span data-ttu-id="ef4a3-120">通过授予针对该架构的访问权限，可以同时授予执行工资功能所需的所有权限。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-120">By granting access to the schema, all the necessary permissions to perform the payroll function can be granted at the same time.</span></span> <span data-ttu-id="ef4a3-121">有关可向哪些安全对象授予权限的详细信息，请参阅 [Securables](../securables.md)。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-121">For more information about what securables can be granted permissions, see [Securables](../securables.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ef4a3-122">Security</span><span class="sxs-lookup"><span data-stu-id="ef4a3-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ef4a3-123">权限</span><span class="sxs-lookup"><span data-stu-id="ef4a3-123">Permissions</span></span>  
 <span data-ttu-id="ef4a3-124">授权者（或使用 AS 选项指定的主体）必须具有使用 GRANT OPTION 授予的权限本身，或具有隐含授予该权限的更高权限。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-124">The grantor (or the principal specified with the AS option) must have either the permission itself with GRANT OPTION or a higher permission that implies the permission being granted.</span></span> <span data-ttu-id="ef4a3-125">**sysadmin** 固定服务器角色成员可以授予任何权限。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-125">Members of the **sysadmin** fixed server role can grant any permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ef4a3-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ef4a3-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-grant-permission-to-a-principal"></a><span data-ttu-id="ef4a3-127">向主体授予权限</span><span class="sxs-lookup"><span data-stu-id="ef4a3-127">To grant permission to a principal</span></span>  
  
1.  <span data-ttu-id="ef4a3-128">在“对象资源管理器”中，展开包含您要授予权限的对象的数据库。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-128">In Object Explorer, expand the database that contains the object to which you want to grant permissions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ef4a3-129">这些步骤仅针对向存储过程授予权限，但您可以使用类似的步骤向表、视图、函数和程序集以及其他安全对象添加权限。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-129">These steps deal specifically with granting permissions to a stored procedure, but you can use similar steps to add permissions to tables, views, functions, and assemblies, as well as other securables.</span></span> <span data-ttu-id="ef4a3-130">有关详细信息，请参阅 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="ef4a3-130">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)</span></span>  
  
2.  <span data-ttu-id="ef4a3-131">展开 **“可编程性”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-131">Expand the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="ef4a3-132">展开 **“存储过程”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-132">Expand the **Stored Procedures** folder.</span></span>  
  
4.  <span data-ttu-id="ef4a3-133">右键单击某一存储过程，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-133">Right-click a stored procedure and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="ef4a3-134">在 "**存储过程属性-**_stored_procedure_name_ " 对话框中的 "选择页" 下，选择 "**权限**"。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-134">In the **Stored Procedure Properties -**_stored_procedure_name_ dialog box, under select a page, select **Permissions**.</span></span> <span data-ttu-id="ef4a3-135">使用此页可以将用户或角色添加到存储过程以及指定这些用户或角色所具有的权限。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-135">Use this page to add users or roles to the stored procedure and specify the permissions those users or roles have.</span></span>  
  
6.  <span data-ttu-id="ef4a3-136">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-136">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ef4a3-137">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ef4a3-137">Using Transact-SQL</span></span>  
  
#### <a name="to-grant-permission-to-a-principal"></a><span data-ttu-id="ef4a3-138">向主体授予权限</span><span class="sxs-lookup"><span data-stu-id="ef4a3-138">To grant permission to a principal</span></span>  
  
1.  <span data-ttu-id="ef4a3-139">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ef4a3-140">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ef4a3-141">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Grants EXECUTE permission on stored procedure HumanResources.uspUpdateEmployeeHireInfo to an application role called Recruiting11.   
    USE AdventureWorks2012;  
    GO  
    GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
        TO Recruiting11;  
    GO  
    ```  
  
 <span data-ttu-id="ef4a3-142">有关详细信息，请参阅 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql) 和 [GRANT 对象权限 (Transact-SQL)](/sql/t-sql/statements/grant-object-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ef4a3-142">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) and [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef4a3-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef4a3-143">See Also</span></span>  
 [<span data-ttu-id="ef4a3-144">主体（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="ef4a3-144">Principals &#40;Database Engine&#41;</span></span>](principals-database-engine.md)  
  
  
