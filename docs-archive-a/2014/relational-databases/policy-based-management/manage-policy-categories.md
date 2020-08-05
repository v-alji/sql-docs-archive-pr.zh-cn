---
title: 管理策略类别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.policycategories.f1
ms.assetid: d188a819-731f-4029-98aa-780d3299a0ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 168d05dd88286263da1dca5456a2c6072e946786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580197"
---
# <a name="manage-policy-categories"></a><span data-ttu-id="ea603-102">管理策略类别</span><span class="sxs-lookup"><span data-stu-id="ea603-102">Manage Policy Categories</span></span>
  <span data-ttu-id="ea603-103">本主题说明如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 将某类别的任意或所有可用策略应用到整个 [!INCLUDE[tsql](../../includes/tsql-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="ea603-103">This topic describes how to apply any or all available policies in a category to the whole instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ea603-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ea603-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ea603-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ea603-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ea603-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ea603-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ea603-107">安全性</span><span class="sxs-lookup"><span data-stu-id="ea603-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ea603-108">**将类别策略应用到 SQL Server 实例，使用：**</span><span class="sxs-lookup"><span data-stu-id="ea603-108">**To apply category policies to a SQL Server instance, using:**</span></span>  
  
     [<span data-ttu-id="ea603-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ea603-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ea603-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ea603-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ea603-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="ea603-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ea603-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ea603-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ea603-113">使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]时，如果未选中 **“托管数据库订阅”** 复选框，则必须将策略类别分别应用于服务器的每个相关部分，例如，一个或多个数据库或表。</span><span class="sxs-lookup"><span data-stu-id="ea603-113">When using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], if the **Mandate Database Subscriptions** check box is not selected, the policy category must be individually applied to each relevant portion of the server, such as one or more databases or tables.</span></span>  
  
-   <span data-ttu-id="ea603-114">如果您指定的策略类别不存在，将创建新的策略类别，并且在您执行存储过程时对于所有数据库都将托管订阅。</span><span class="sxs-lookup"><span data-stu-id="ea603-114">If you specify a policy category that does not exist, a new policy category is created and the subscription is mandated for all databases when you execute the stored procedure.</span></span> <span data-ttu-id="ea603-115">如果你为新的类别清除托管的订阅，则该订阅将只适用于你指定为 *target_object*的数据库。</span><span class="sxs-lookup"><span data-stu-id="ea603-115">If you then clear the mandated subscription for the new category, the subscription will only apply for the database that you specified as the *target_object*.</span></span> <span data-ttu-id="ea603-116">有关如何更改托管的订阅设置的详细信息，请参阅 [sp_syspolicy_update_policy_category (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ea603-116">For more information about how to change a mandated subscription setting, see [sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ea603-117">Security</span><span class="sxs-lookup"><span data-stu-id="ea603-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ea603-118">权限</span><span class="sxs-lookup"><span data-stu-id="ea603-118">Permissions</span></span>  
 <span data-ttu-id="ea603-119">此存储过程在其当前所有者的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="ea603-119">This stored procedure runs in the context of the current owner of the stored procedure.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ea603-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ea603-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a><span data-ttu-id="ea603-121">将类别策略应用到 SQL Server 实例</span><span class="sxs-lookup"><span data-stu-id="ea603-121">To apply category policies to a SQL Server instance</span></span>  
  
1.  <span data-ttu-id="ea603-122">在 **“对象资源管理器”** 中，单击加号以展开您将应用类别策略的服务器。</span><span class="sxs-lookup"><span data-stu-id="ea603-122">In **Object Explorer**, click the plus sign to expand the server where you will apply category policies.</span></span>  
  
2.  <span data-ttu-id="ea603-123">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ea603-123">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="ea603-124">右键单击“策略管理”  ，然后选择“管理类别”  。</span><span class="sxs-lookup"><span data-stu-id="ea603-124">Right-click **Policy Management** and select **Manage Categories**.</span></span>  
  
     <span data-ttu-id="ea603-125">在 **“管理策略类别”** 对话框中提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="ea603-125">The following information is available in the **Manage Policy Categories** dialog box:</span></span>  
  
     <span data-ttu-id="ea603-126">**名称**</span><span class="sxs-lookup"><span data-stu-id="ea603-126">**Name**</span></span>  
     <span data-ttu-id="ea603-127">策略类别的名称。</span><span class="sxs-lookup"><span data-stu-id="ea603-127">The name of the policy category.</span></span>  
  
     <span data-ttu-id="ea603-128">**“托管数据库订阅”**</span><span class="sxs-lookup"><span data-stu-id="ea603-128">**Mandate Database Subscriptions**</span></span>  
     <span data-ttu-id="ea603-129">强制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的所有数据库实施策略类别中的策略。</span><span class="sxs-lookup"><span data-stu-id="ea603-129">Forces all databases on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to enforce policies in the policy category.</span></span>  
  
4.  <span data-ttu-id="ea603-130">选中或清除 **“托管数据库订阅”** 下的任意或所有复选框，以将该策略类别应用到 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="ea603-130">Select or clear any or all check boxes under **Mandate Database Subscriptions** to apply that policy category to the SQL Server instance.</span></span>  
  
5.  <span data-ttu-id="ea603-131">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ea603-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ea603-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ea603-132">Using Transact-SQL</span></span>  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a><span data-ttu-id="ea603-133">将类别策略应用到 SQL Server 实例</span><span class="sxs-lookup"><span data-stu-id="ea603-133">To apply category policies to a SQL Server instance</span></span>  
  
1.  <span data-ttu-id="ea603-134">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="ea603-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ea603-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ea603-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ea603-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="ea603-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    -- configures the specified database to subscribe to a policy category that is named 'Table Naming Policies'.  
    EXEC dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
    , @target_object = N'AdventureWorks2012'  
    , @policy_category = N'Table Naming Policies';  
    GO  
    ```  
  
 <span data-ttu-id="ea603-137">有关详细信息，请参阅 [sp_syspolicy_add_policy_category_subscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ea603-137">For more information, see [sp_syspolicy_add_policy_category_subscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql).</span></span>  
  
  
