---
title: 创建操作员 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- jobs [SQL Server Agent], notification options
- operators (users) [Database Engine], creating with Management Studio
- SQL Server Agent jobs, notification options
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 1359d790-5905-4927-a208-e7155e7768a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: dfe07042f9a4b8ac595ada8b86e7bad131032700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689263"
---
# <a name="create-an-operator"></a><span data-ttu-id="af422-102">创建操作员</span><span class="sxs-lookup"><span data-stu-id="af422-102">Create an Operator</span></span>
  <span data-ttu-id="af422-103">本主题介绍如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中配置用户以接收有关代理作业的通知 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="af422-103">This topic describes how to configure a user to receive notifications about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="af422-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="af422-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="af422-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="af422-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="af422-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="af422-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="af422-107">安全性</span><span class="sxs-lookup"><span data-stu-id="af422-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="af422-108">**若要创建操作员，请使用：**</span><span class="sxs-lookup"><span data-stu-id="af422-108">**To create an operator, using:**</span></span>  
  
     [<span data-ttu-id="af422-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af422-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="af422-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="af422-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="af422-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="af422-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="af422-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="af422-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="af422-113">在 **的未来版本中，将从** 代理中删除寻呼程序和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]选项。</span><span class="sxs-lookup"><span data-stu-id="af422-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="af422-114">请避免在新的开发工作中使用这些功能，并考虑修改当前使用这些功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="af422-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="af422-115">请注意，若要向操作员发送电子邮件和寻呼通知，必须将 SQL Server 代理配置为使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="af422-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="af422-116">有关详细信息，请参阅 [向操作员分配警报](assign-alerts-to-an-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="af422-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="af422-117">为管理作业提供了一种图形化的简便方法，建议使用此方法来创建和管理作业基础结构。</span><span class="sxs-lookup"><span data-stu-id="af422-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="af422-118">Security</span><span class="sxs-lookup"><span data-stu-id="af422-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="af422-119">权限</span><span class="sxs-lookup"><span data-stu-id="af422-119">Permissions</span></span>  
 <span data-ttu-id="af422-120">只有 **sysadmin** 固定服务器角色的成员才能创建操作员。</span><span class="sxs-lookup"><span data-stu-id="af422-120">Only members of the **sysadmin** fixed server role can create operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="af422-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af422-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-operator"></a><span data-ttu-id="af422-122">创建操作员</span><span class="sxs-lookup"><span data-stu-id="af422-122">To create an operator</span></span>  
  
1.  <span data-ttu-id="af422-123">在 **“对象资源管理器”** 中，单击加号以展开要创建 SQL Server 代理操作员的服务器。</span><span class="sxs-lookup"><span data-stu-id="af422-123">In **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent operator.</span></span>  
  
2.  <span data-ttu-id="af422-124">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="af422-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="af422-125">右键单击“操作员”\*\*\*\* 文件夹，然后选择“新建操作员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af422-125">Right-click the **Operators** folder and select **New Operator**.</span></span>  
  
     <span data-ttu-id="af422-126">在 **“新建操作员”** 对话框的 **“常规”** 页上提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="af422-126">The following options are available on the **General** page of the **New Operator** dialog box:</span></span>  
  
     <span data-ttu-id="af422-127">**名称**</span><span class="sxs-lookup"><span data-stu-id="af422-127">**Name**</span></span>  
     <span data-ttu-id="af422-128">更改操作员的名称。</span><span class="sxs-lookup"><span data-stu-id="af422-128">Change the name of the operator.</span></span>  
  
     <span data-ttu-id="af422-129">**已启用**</span><span class="sxs-lookup"><span data-stu-id="af422-129">**Enabled**</span></span>  
     <span data-ttu-id="af422-130">启用操作员。</span><span class="sxs-lookup"><span data-stu-id="af422-130">Enable the operator.</span></span> <span data-ttu-id="af422-131">在未启用时，不会向操作员发送通知。</span><span class="sxs-lookup"><span data-stu-id="af422-131">When not enabled, no notifications are sent to the operator.</span></span>  
  
     <span data-ttu-id="af422-132">**电子邮件名称**</span><span class="sxs-lookup"><span data-stu-id="af422-132">**E-mail name**</span></span>  
     <span data-ttu-id="af422-133">指定操作员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="af422-133">Specifies the e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="af422-134">**Net send 地址**</span><span class="sxs-lookup"><span data-stu-id="af422-134">**Net send address**</span></span>  
     <span data-ttu-id="af422-135">指定用于 **net send**的地址。</span><span class="sxs-lookup"><span data-stu-id="af422-135">Specify the address to use for **net send**.</span></span>  
  
     <span data-ttu-id="af422-136">**寻呼电子邮件名称**</span><span class="sxs-lookup"><span data-stu-id="af422-136">**Pager e-mail name**</span></span>  
     <span data-ttu-id="af422-137">指定用于操作员的寻呼程序的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="af422-137">Specifies the e-mail address to use for the operator's pager.</span></span>  
  
     <span data-ttu-id="af422-138">**寻呼值班计划**</span><span class="sxs-lookup"><span data-stu-id="af422-138">**Pager on duty schedule**</span></span>  
     <span data-ttu-id="af422-139">设置寻呼程序处于活动状态的时间。</span><span class="sxs-lookup"><span data-stu-id="af422-139">Sets the times at which the pager is active.</span></span>  
  
     <span data-ttu-id="af422-140">**星期一 - 星期日**</span><span class="sxs-lookup"><span data-stu-id="af422-140">**Monday - Sunday**</span></span>  
     <span data-ttu-id="af422-141">选择寻呼程序在一周中的哪些天处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="af422-141">Select the days that the pager is active.</span></span>  
  
     <span data-ttu-id="af422-142">**工作日开始**</span><span class="sxs-lookup"><span data-stu-id="af422-142">**Workday begin**</span></span>  
     <span data-ttu-id="af422-143">选择一天之中的特定时间， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在该时间之后才可向寻呼程序发送消息。</span><span class="sxs-lookup"><span data-stu-id="af422-143">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sends messages to the pager.</span></span>  
  
     <span data-ttu-id="af422-144">**工作日结束**</span><span class="sxs-lookup"><span data-stu-id="af422-144">**Workday end**</span></span>  
     <span data-ttu-id="af422-145">选择一天之中的特定时间， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在该时间之后不再向寻呼程序发送消息。</span><span class="sxs-lookup"><span data-stu-id="af422-145">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer sends messages to the pager.</span></span>  
  
     <span data-ttu-id="af422-146">在 **“新建操作员”** 对话框的 **“通知”** 页上提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="af422-146">The following options are available on the **Notifications** page of the **New Operator** dialog box:</span></span>  
  
     <span data-ttu-id="af422-147">**警报**</span><span class="sxs-lookup"><span data-stu-id="af422-147">**Alerts**</span></span>  
     <span data-ttu-id="af422-148">查看实例中的警报。</span><span class="sxs-lookup"><span data-stu-id="af422-148">View the alerts in the instance.</span></span>  
  
     <span data-ttu-id="af422-149">**作业**</span><span class="sxs-lookup"><span data-stu-id="af422-149">**Jobs**</span></span>  
     <span data-ttu-id="af422-150">查看实例中的作业。</span><span class="sxs-lookup"><span data-stu-id="af422-150">View the jobs in the instance.</span></span>  
  
     <span data-ttu-id="af422-151">**警报列表**</span><span class="sxs-lookup"><span data-stu-id="af422-151">**Alert list**</span></span>  
     <span data-ttu-id="af422-152">列出实例中的警报。</span><span class="sxs-lookup"><span data-stu-id="af422-152">Lists the alerts in the instance.</span></span>  
  
     <span data-ttu-id="af422-153">**作业列表**</span><span class="sxs-lookup"><span data-stu-id="af422-153">**Job list**</span></span>  
     <span data-ttu-id="af422-154">列出实例中的作业。</span><span class="sxs-lookup"><span data-stu-id="af422-154">Lists the jobs in the instance.</span></span>  
  
     <span data-ttu-id="af422-155">**电子邮件**</span><span class="sxs-lookup"><span data-stu-id="af422-155">**E-mail**</span></span>  
     <span data-ttu-id="af422-156">使用电子邮件通知此操作员。</span><span class="sxs-lookup"><span data-stu-id="af422-156">Notify this operator using e-mail.</span></span>  
  
     <span data-ttu-id="af422-157">**寻呼程序**</span><span class="sxs-lookup"><span data-stu-id="af422-157">**Pager**</span></span>  
     <span data-ttu-id="af422-158">通过将电子邮件发送到寻呼地址来通知此操作员。</span><span class="sxs-lookup"><span data-stu-id="af422-158">Notify this operator by sending e-mail to the pager address.</span></span>  
  
     <span data-ttu-id="af422-159">**Net send**</span><span class="sxs-lookup"><span data-stu-id="af422-159">**Net send**</span></span>  
     <span data-ttu-id="af422-160">使用 **net send**通知此操作员。</span><span class="sxs-lookup"><span data-stu-id="af422-160">Notify this operator using **net send**.</span></span>  
  
4.  <span data-ttu-id="af422-161">在完成了新操作员的创建后，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="af422-161">When finished creating the new operator, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="af422-162">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="af422-162">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-operator"></a><span data-ttu-id="af422-163">创建操作员</span><span class="sxs-lookup"><span data-stu-id="af422-163">To create an operator</span></span>  
  
1.  <span data-ttu-id="af422-164">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="af422-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="af422-165">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="af422-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="af422-166">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="af422-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- sets up the operator information for user 'danwi.' The operator is enabled.   
    -- SQL Server Agent sends notifications by pager from Monday through Friday from 8 A.M. to 5 P.M.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_operator  
        @name = N'Dan Wilson',  
        @enabled = 1,  
        @email_address = N'danwi',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 62 ;  
    GO  
    ```  
  
 <span data-ttu-id="af422-167">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_operator ](/sql/relational-databases/system-stored-procedures/sp-add-operator-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="af422-167">For more information, see [sp_add_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-operator-transact-sql).</span></span>  
  
  
