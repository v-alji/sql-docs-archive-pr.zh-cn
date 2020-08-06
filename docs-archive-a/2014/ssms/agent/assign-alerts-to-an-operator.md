---
title: 向操作员分配警报 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- assigning alerts to operator
- SQL Server Agent, alerts
- alerts [SQL Server], assigning to operator
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: aa818155-6fa2-4565-a09f-5c7e31c89754
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3cc238b952c03595035856f377b6fdbb9eaf5e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586068"
---
# <a name="assign-alerts-to-an-operator"></a><span data-ttu-id="53ff6-102">向操作员分配警报</span><span class="sxs-lookup"><span data-stu-id="53ff6-102">Assign Alerts to an Operator</span></span>
  <span data-ttu-id="53ff6-103">本主题介绍如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中向操作员分配代理警报，以便他们可以接收有关作业的通知 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="53ff6-103">This topic describes how to assign [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts to operators so they can receive notifications about jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="53ff6-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="53ff6-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="53ff6-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="53ff6-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="53ff6-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="53ff6-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="53ff6-107">安全性</span><span class="sxs-lookup"><span data-stu-id="53ff6-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="53ff6-108">**若要向操作员分配警报，可使用：**</span><span class="sxs-lookup"><span data-stu-id="53ff6-108">**To assign alerts to an operator, using:**</span></span>  
  
     [<span data-ttu-id="53ff6-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="53ff6-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="53ff6-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="53ff6-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="53ff6-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="53ff6-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="53ff6-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="53ff6-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="53ff6-113">提供一种简单的图形方法来管理整个警报系统。</span><span class="sxs-lookup"><span data-stu-id="53ff6-113">provides an easy, graphical way to manage the entire alerting system.</span></span> <span data-ttu-id="53ff6-114">建议使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 配置警报基本结构。</span><span class="sxs-lookup"><span data-stu-id="53ff6-114">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is the recommended way to configure your alert infrastructure.</span></span>  
  
-   <span data-ttu-id="53ff6-115">若要发送响应警报的通知，必须首先配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理以发送邮件。</span><span class="sxs-lookup"><span data-stu-id="53ff6-115">To send a notification in response to an alert, you must first configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send mail.</span></span> <span data-ttu-id="53ff6-116">有关详细信息，请参阅 [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="53ff6-116">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
-   <span data-ttu-id="53ff6-117">如果在发送电子邮件或寻呼通知时出现故障，则该故障将被记录到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务错误日志中。</span><span class="sxs-lookup"><span data-stu-id="53ff6-117">If a failure occurs when sending an e-mail message or pager notification, the failure is reported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service error log.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="53ff6-118">Security</span><span class="sxs-lookup"><span data-stu-id="53ff6-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="53ff6-119">权限</span><span class="sxs-lookup"><span data-stu-id="53ff6-119">Permissions</span></span>  
 <span data-ttu-id="53ff6-120">只有 **sysadmin** 固定服务器角色的成员才能向操作员分配警报。</span><span class="sxs-lookup"><span data-stu-id="53ff6-120">Only members of the **sysadmin** fixed server role can assign alerts to operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="53ff6-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="53ff6-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-assign-alerts-to-an-operator"></a><span data-ttu-id="53ff6-122">为操作员分配警报</span><span class="sxs-lookup"><span data-stu-id="53ff6-122">To assign alerts to an operator</span></span>  
  
1.  <span data-ttu-id="53ff6-123">在 **“对象资源管理器”** 中，单击加号以展开包含要向其分配警报的操作员的服务器。</span><span class="sxs-lookup"><span data-stu-id="53ff6-123">In **Object Explorer**, click the plus sign to expand the server that contains the operator to which you want to assign an alert.</span></span>  
  
2.  <span data-ttu-id="53ff6-124">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="53ff6-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="53ff6-125">单击加号以展开 **“操作员”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="53ff6-125">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="53ff6-126">右键单击要为其分配警报的操作员，再选择“属性”\*\*\*\*，然后选择“通知”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="53ff6-126">Right-click the operator to which you want to assign an alert and select **Properties**, and select the **Notifications** page.</span></span>  
  
5.  <span data-ttu-id="53ff6-127">在 " _operator_name_**属性**" 对话框中的 "**选择页**" 下，选择 "**通知**"。</span><span class="sxs-lookup"><span data-stu-id="53ff6-127">In the _operator_name_**Properties** dialog box, under **Select a page**, select **Notifications**.</span></span>  
  
6.  <span data-ttu-id="53ff6-128">在 **“按以下方式查看发送给此用户的通知”** 下，选择 **“警报”** 查看发送给此操作员的警报列表或选择 **“作业”** 查看向此操作员发送通知的作业列表。</span><span class="sxs-lookup"><span data-stu-id="53ff6-128">Under **View notifications sent to this user by**, select **Alerts** to view a list of alerts sent to this operator or select **Jobs** to view a list of jobs that send notifications to this operator.</span></span> <span data-ttu-id="53ff6-129">选中下列一个或多个复选框来根据需要定义每个通知的通知方法：“电子邮件”\*\*\*\*、“寻呼程序”\*\*\*\* 或“Net send”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="53ff6-129">Select one or more of the following checkboxes to define the notification method for each notification as necessary: **E-mail**, **Pager**, or **Net send**.</span></span>  
  
7.  <span data-ttu-id="53ff6-130">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="53ff6-130">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="53ff6-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="53ff6-131">Using Transact-SQL</span></span>  
  
#### <a name="to-assign-alerts-to-an-operator"></a><span data-ttu-id="53ff6-132">为操作员分配警报</span><span class="sxs-lookup"><span data-stu-id="53ff6-132">To assign alerts to an operator</span></span>  
  
1.  <span data-ttu-id="53ff6-133">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="53ff6-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="53ff6-134">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="53ff6-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="53ff6-135">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="53ff6-135">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert)  
    -- This example assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'Fran??ois Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="53ff6-136">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_notification ](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="53ff6-136">For more information, see [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).</span></span>  
  
  
