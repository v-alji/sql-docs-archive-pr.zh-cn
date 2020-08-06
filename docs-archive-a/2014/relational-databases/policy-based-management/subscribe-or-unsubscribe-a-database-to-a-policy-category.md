---
title: 建立数据库对某个策略类别的订阅或取消数据库对该类别的订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.groupsubscription.f1
ms.assetid: d2c31769-7098-428e-ad9c-ef56541b7c52
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2b4ca6f804352b57b30b42012da93e0d031be8d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689329"
---
# <a name="subscribe-or-unsubscribe-a-database--to-a-policy-category"></a><span data-ttu-id="78eef-102">建立数据库对某个策略类别的订阅或取消数据库对该类别的订阅</span><span class="sxs-lookup"><span data-stu-id="78eef-102">Subscribe or Unsubscribe a Database  to a Policy Category</span></span>
  <span data-ttu-id="78eef-103">本主题说明如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立数据库对某个策略类别的订阅或取消数据库对该类别的订阅。</span><span class="sxs-lookup"><span data-stu-id="78eef-103">This topic describes how to subscribe or unsubscribe a database to a policy category.in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="78eef-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="78eef-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="78eef-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="78eef-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="78eef-106">安全性</span><span class="sxs-lookup"><span data-stu-id="78eef-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="78eef-107">**建立数据库对某个策略类别的订阅或取消数据库对该类别的订阅，使用：**</span><span class="sxs-lookup"><span data-stu-id="78eef-107">**To subscribe or unsubscribe a database to a policy category., using:**</span></span>  
  
     [<span data-ttu-id="78eef-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="78eef-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="78eef-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="78eef-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="78eef-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="78eef-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="78eef-111">Security</span><span class="sxs-lookup"><span data-stu-id="78eef-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="78eef-112">权限</span><span class="sxs-lookup"><span data-stu-id="78eef-112">Permissions</span></span>  
 <span data-ttu-id="78eef-113">要求具有 db_owner 固定数据库角色中的成员资格。</span><span class="sxs-lookup"><span data-stu-id="78eef-113">Requires membership in the db_owner fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="78eef-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="78eef-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-subscribe-or-unsubscribe-a-database-to-a-policy-category"></a><span data-ttu-id="78eef-115">建立数据库对某个策略类别的订阅或取消数据库对该类别的订阅</span><span class="sxs-lookup"><span data-stu-id="78eef-115">To subscribe or unsubscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="78eef-116">在 **“对象资源管理器”** 中，单击加号以展开包含您要管理类别订阅的数据库的服务器。</span><span class="sxs-lookup"><span data-stu-id="78eef-116">In **Object Explorer**, click the plus sign to expand the server that contains the database wherein you want to manage category subscriptions.</span></span>  
  
2.  <span data-ttu-id="78eef-117">单击加号以展开 **“数据库”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="78eef-117">Click the plus sign to expand the **Databases** folder.</span></span>  
  
3.  <span data-ttu-id="78eef-118">右键单击要管理类别订阅的数据库，指向“策略”\*\*\*\*，然后选择“类别”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="78eef-118">Right-click the database wherein you want to manage category subscriptions, point to **Policies**, and select **Categories**</span></span>  
  
     <span data-ttu-id="78eef-119">在 **“类别”** 对话框中提供了以下选项：</span><span class="sxs-lookup"><span data-stu-id="78eef-119">The following options are available in the **Categories** dialog box:</span></span>  
  
     <span data-ttu-id="78eef-120">展开列</span><span class="sxs-lookup"><span data-stu-id="78eef-120">Expand column</span></span>  
     <span data-ttu-id="78eef-121">单击可展开策略类别。</span><span class="sxs-lookup"><span data-stu-id="78eef-121">Click to expand a policy category.</span></span> <span data-ttu-id="78eef-122">这会列出此类别中包括的所有策略。</span><span class="sxs-lookup"><span data-stu-id="78eef-122">This lists all the policies that are included in the category.</span></span>  
  
     <span data-ttu-id="78eef-123">**名称**</span><span class="sxs-lookup"><span data-stu-id="78eef-123">**Name**</span></span>  
     <span data-ttu-id="78eef-124">策略类别的名称。</span><span class="sxs-lookup"><span data-stu-id="78eef-124">The name of the policy category.</span></span>  
  
     <span data-ttu-id="78eef-125">**订购**</span><span class="sxs-lookup"><span data-stu-id="78eef-125">**Subscribed**</span></span>  
     <span data-ttu-id="78eef-126">指示目标是否已订阅此策略类别。</span><span class="sxs-lookup"><span data-stu-id="78eef-126">Indicates whether the target has subscribed to the policy category.</span></span> <span data-ttu-id="78eef-127">如果禁用此复选框，则为 **“托管数据库订阅”** 设置此策略类别。</span><span class="sxs-lookup"><span data-stu-id="78eef-127">If this check box is disabled, the policy category is set for **Mandate Database Subscriptions**.</span></span> <span data-ttu-id="78eef-128">这意味着该策略类别应用于服务器上的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="78eef-128">This means that the policy category applies to all databases on the server.</span></span>  
  
     <span data-ttu-id="78eef-129">**策略**</span><span class="sxs-lookup"><span data-stu-id="78eef-129">**Policy**</span></span>  
     <span data-ttu-id="78eef-130">展开策略组将显示策略类别中包括的策略。</span><span class="sxs-lookup"><span data-stu-id="78eef-130">When policy groups are expanded, displays the policies in the policy category.</span></span>  
  
     <span data-ttu-id="78eef-131">**已启用**</span><span class="sxs-lookup"><span data-stu-id="78eef-131">**Enabled**</span></span>  
     <span data-ttu-id="78eef-132">指示是启用还是禁用了策略。</span><span class="sxs-lookup"><span data-stu-id="78eef-132">Indicates whether the policies are enabled or disabled.</span></span>  
  
     <span data-ttu-id="78eef-133">**执行模式**</span><span class="sxs-lookup"><span data-stu-id="78eef-133">**Execution Mode**</span></span>  
     <span data-ttu-id="78eef-134">显示策略的执行模式。</span><span class="sxs-lookup"><span data-stu-id="78eef-134">Displays the execution mode of the policy.</span></span>  
  
     <span data-ttu-id="78eef-135">**History**</span><span class="sxs-lookup"><span data-stu-id="78eef-135">**History**</span></span>  
     <span data-ttu-id="78eef-136">单击“查看历史记录”超链接可打开日志文件查看器，从而可以查看策略历史记录。</span><span class="sxs-lookup"><span data-stu-id="78eef-136">Click the View History hyperlink to open the Log File Viewer to see the policy history.</span></span>  
  
4.  <span data-ttu-id="78eef-137">若要订阅某个基于策略的管理类别，请选中“已订阅”\*\*\*\* 列下该类别的复选框。</span><span class="sxs-lookup"><span data-stu-id="78eef-137">To subscribe to a Policy-Based Management category, select the category's check box under the **Subscribed** column.</span></span> <span data-ttu-id="78eef-138">若要从类别中取消订阅，请清除该复选框。</span><span class="sxs-lookup"><span data-stu-id="78eef-138">To unsubscribe from a category, clear the check box.</span></span>  
  
5.  <span data-ttu-id="78eef-139">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="78eef-139">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="78eef-140">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="78eef-140">Using Transact-SQL</span></span>  
  
#### <a name="to-subscribe-a-database-to-a-policy-category"></a><span data-ttu-id="78eef-141">建立数据库对某个策略类别的订阅</span><span class="sxs-lookup"><span data-stu-id="78eef-141">To subscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="78eef-142">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="78eef-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="78eef-143">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="78eef-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="78eef-144">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="78eef-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    -- Adds a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_subscribe_to_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 <span data-ttu-id="78eef-145">有关详细信息，请参阅 [sp_syspolicy_subscribe_to_policy_category (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="78eef-145">For more information, see [sp_syspolicy_subscribe_to_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql).</span></span>  
  
#### <a name="to-unsubscribe-a-database-to-a-policy-category"></a><span data-ttu-id="78eef-146">取消数据库对某个策略类别的订阅</span><span class="sxs-lookup"><span data-stu-id="78eef-146">To unsubscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="78eef-147">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="78eef-147">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="78eef-148">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="78eef-148">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="78eef-149">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="78eef-149">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    -- Deletes a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_unsubscribe_from_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 <span data-ttu-id="78eef-150">有关详细信息，请参阅 [sp_syspolicy_unsubscribe_from_policy_category (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="78eef-150">For more information, see [sp_syspolicy_unsubscribe_from_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql).</span></span>  
  
  
