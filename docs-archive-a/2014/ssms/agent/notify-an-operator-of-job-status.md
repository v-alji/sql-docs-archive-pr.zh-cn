---
title: 向操作员通知作业状态 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- jobs [SQL Server Agent], notification options
- SQL Server Agent jobs, status
- jobs [SQL Server Agent], status
- SQL Server Agent jobs, notification options
- notifications [SQL Server], job status
ms.assetid: e7399505-27ac-48d9-a637-73bf92b9df49
author: stevestein
ms.author: sstein
ms.openlocfilehash: a202327ad63cf7ef8f51d3572b257816ee6d9419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580525"
---
# <a name="notify-an-operator-of-job-status"></a><span data-ttu-id="b6d45-102">Notify an Operator of Job Status</span><span class="sxs-lookup"><span data-stu-id="b6d45-102">Notify an Operator of Job Status</span></span>
  <span data-ttu-id="b6d45-103">本主题说明如何 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 通过使用、或 SQL Server 管理对象在中设置通知选项 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ，以便 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理可向操作员发送有关作业的通知。</span><span class="sxs-lookup"><span data-stu-id="b6d45-103">This topic describes how to set notification options in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects, so [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can send notifications to operators about jobs.</span></span>  
  
 <span data-ttu-id="b6d45-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b6d45-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b6d45-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b6d45-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b6d45-106">安全性</span><span class="sxs-lookup"><span data-stu-id="b6d45-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b6d45-107">**若要向操作员通知作业状态，可使用：**</span><span class="sxs-lookup"><span data-stu-id="b6d45-107">**To notify an operator of job status, using:**</span></span>  
  
     [<span data-ttu-id="b6d45-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6d45-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="b6d45-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6d45-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="b6d45-110">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="b6d45-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b6d45-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="b6d45-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b6d45-112">Security</span><span class="sxs-lookup"><span data-stu-id="b6d45-112">Security</span></span>  
 <span data-ttu-id="b6d45-113">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="b6d45-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="b6d45-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6d45-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-notify-an-operator-of-job-status"></a><span data-ttu-id="b6d45-115">向操作员通知作业状态</span><span class="sxs-lookup"><span data-stu-id="b6d45-115">To notify an operator of job status</span></span>  
  
1.  <span data-ttu-id="b6d45-116">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="b6d45-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b6d45-117">展开“SQL Server 代理”\*\*\*\*，展开“作业”\*\*\*\*，右键单击要编辑的作业，再选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b6d45-117">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="b6d45-118">在 **“作业属性”** 对话框中，选择 **“通知”** 页。</span><span class="sxs-lookup"><span data-stu-id="b6d45-118">In the **Job Properties** dialog box, select the **Notifications** page.</span></span>  
  
4.  <span data-ttu-id="b6d45-119">如果想通过电子邮件通知操作员，请选中“电子邮件”\*\*\*\*，再从列表中选择操作员，然后选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="b6d45-119">If you want to notify an operator by e-mail, check **E-mail**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="b6d45-120">**当作业成功时** - 在作业成功完成后通知操作员。</span><span class="sxs-lookup"><span data-stu-id="b6d45-120">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="b6d45-121">**“当作业失败时”** - 在作业未成功完成时通知该操作员。</span><span class="sxs-lookup"><span data-stu-id="b6d45-121">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="b6d45-122">**当作业完成时** ，无论完成情况如何，都通知该操作员。</span><span class="sxs-lookup"><span data-stu-id="b6d45-122">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
5.  <span data-ttu-id="b6d45-123">如果您想通过寻呼程序来通知操作员，请选中 **“寻呼程序”**，再从列表中选择操作员，然后选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="b6d45-123">If you want to notify an operator by pager, check **Page**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="b6d45-124">**当作业成功时** - 在作业成功完成后通知操作员。</span><span class="sxs-lookup"><span data-stu-id="b6d45-124">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="b6d45-125">**“当作业失败时”** - 在作业未成功完成时通知该操作员。</span><span class="sxs-lookup"><span data-stu-id="b6d45-125">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="b6d45-126">**当作业完成时** ，无论完成情况如何，都通知该操作员。</span><span class="sxs-lookup"><span data-stu-id="b6d45-126">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
6.  <span data-ttu-id="b6d45-127">如果想通过 net send 通知操作员，请选中 **Net send**，再从列表中选择操作员，然后选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="b6d45-127">If you want to notify an operator by net send, check **Net send**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="b6d45-128">**当作业成功时** - 在作业成功完成后通知操作员。</span><span class="sxs-lookup"><span data-stu-id="b6d45-128">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="b6d45-129">**“当作业失败时”** - 在作业未成功完成时通知该操作员。</span><span class="sxs-lookup"><span data-stu-id="b6d45-129">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="b6d45-130">**当作业完成时** ，无论完成情况如何，都通知该操作员。</span><span class="sxs-lookup"><span data-stu-id="b6d45-130">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="b6d45-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6d45-131">Using Transact-SQL</span></span>  
  
#### <a name="to-notify-an-operator-of-job-status"></a><span data-ttu-id="b6d45-132">向操作员通知作业状态</span><span class="sxs-lookup"><span data-stu-id="b6d45-132">To notify an operator of job status</span></span>  
  
1.  <span data-ttu-id="b6d45-133">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="b6d45-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b6d45-134">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b6d45-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b6d45-135">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b6d45-135">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- adds an e-mail notification for the specified alert (Test Alert).  
    -- This example assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_notification   
    @alert_name = N'Test Alert',   
    @operator_name = N'Fran??ois Ajenstat',   
    @notification_method = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="b6d45-136">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_notification ](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b6d45-136">For more information, see [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="b6d45-137">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="b6d45-137">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="b6d45-138">**向操作员通知作业状态**</span><span class="sxs-lookup"><span data-stu-id="b6d45-138">**To notify an operator of job status**</span></span>  
  
 <span data-ttu-id="b6d45-139">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `Job` 类。</span><span class="sxs-lookup"><span data-stu-id="b6d45-139">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="b6d45-140">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b6d45-140">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
