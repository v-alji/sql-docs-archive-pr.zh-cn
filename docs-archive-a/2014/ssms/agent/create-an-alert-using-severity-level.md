---
title: 使用严重级别创建警报 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- severity levels [SQL Server]
- alerts [SQL Server], severity levels
ms.assetid: a1fd71bf-5bf9-4ce2-9a1d-032576a4a6e9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ee353129d60fe7fc8bed0eff279920d8d4ba640
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691028"
---
# <a name="create-an-alert-using-severity-level"></a><span data-ttu-id="1c607-102">Create an Alert Using Severity Level</span><span class="sxs-lookup"><span data-stu-id="1c607-102">Create an Alert Using Severity Level</span></span>
  <span data-ttu-id="1c607-103">本主题介绍如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中创建在发生特定严重级别的事件时引发的代理警报 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1c607-103">This topic describes how to create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert that is raised when an event of a specific severity level occurs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1c607-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="1c607-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1c607-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="1c607-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1c607-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="1c607-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1c607-107">安全性</span><span class="sxs-lookup"><span data-stu-id="1c607-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1c607-108">**若要使用严重级别创建警报，可使用：**</span><span class="sxs-lookup"><span data-stu-id="1c607-108">**To create an alert using severity level, using:**</span></span>  
  
     [<span data-ttu-id="1c607-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1c607-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1c607-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1c607-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1c607-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="1c607-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1c607-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="1c607-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="1c607-113">提供了一种易用的图形方式来管理整个警报系统，这也是配置警报基础结构的推荐方式。</span><span class="sxs-lookup"><span data-stu-id="1c607-113">provides an easy, graphical way to manage the entire alerting system and is the recommended way to configure an alert infrastructure.</span></span>  
  
-   <span data-ttu-id="1c607-114">用 **xp_logevent** 生成的事件在 master 数据库中发生。</span><span class="sxs-lookup"><span data-stu-id="1c607-114">Events generated with **xp_logevent** occur in the master database.</span></span> <span data-ttu-id="1c607-115">因此，除非警报的 **xp_logevent** 为 **@database_name** 或 NULL，否则 **@database_name** 不触发警报。</span><span class="sxs-lookup"><span data-stu-id="1c607-115">Therefore, **xp_logevent** does not trigger an alert unless the **@database_name** for the alert is **'master'** or NULL.</span></span>  
  
-   <span data-ttu-id="1c607-116">如果严重级别在 19 到 25 之间，就会向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 应用程序日志发送 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 消息，并触发一个警报。</span><span class="sxs-lookup"><span data-stu-id="1c607-116">Severity levels from 19 through 25 send a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] message to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log and trigger an alert.</span></span> <span data-ttu-id="1c607-117">对于严重级别小于 19 的事件，只有在使用 **sp_altermessage**、RAISERROR WITH LOG 或 **xp_logevent** 强制这些事件写入 Windows 应用程序日志时，才会触发警报。</span><span class="sxs-lookup"><span data-stu-id="1c607-117">Events with severity levels less than 19 will trigger alerts only if you have used **sp_altermessage**, RAISERROR WITH LOG, or **xp_logevent** to force them to be written to the Windows application log.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1c607-118">Security</span><span class="sxs-lookup"><span data-stu-id="1c607-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1c607-119">权限</span><span class="sxs-lookup"><span data-stu-id="1c607-119">Permissions</span></span>  
 <span data-ttu-id="1c607-120">默认情况下，只有 **sysadmin** 固定服务器角色的成员才能执行 **sp_add_alert**。</span><span class="sxs-lookup"><span data-stu-id="1c607-120">By default, only members of the **sysadmin** fixed server role can execute **sp_add_alert**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1c607-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1c607-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-alert-using-severity-level"></a><span data-ttu-id="1c607-122">使用严重级别创建警报</span><span class="sxs-lookup"><span data-stu-id="1c607-122">To create an alert using severity level</span></span>  
  
1.  <span data-ttu-id="1c607-123">在 **“对象资源管理器”** 中，单击加号以展开要使用严重级别创建警报的服务器。</span><span class="sxs-lookup"><span data-stu-id="1c607-123">In **Object Explorer,** click the plus sign to expand the server where you want to create an alert using severity level.</span></span>  
  
2.  <span data-ttu-id="1c607-124">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="1c607-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="1c607-125">右键单击“警报”\*\*\*\* 并选择“新建警报”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1c607-125">Right-click **Alerts** and select **New Alert**.</span></span>  
  
4.  <span data-ttu-id="1c607-126">在 **“新建警报”** 对话框的 **“名称”** 框中，输入此警报的名称。</span><span class="sxs-lookup"><span data-stu-id="1c607-126">In the **New Alert** dialog box, in the **Name** box, enter a name for this alert.</span></span>  
  
5.  <span data-ttu-id="1c607-127">在 **“类型”** 列表中，选择 **“SQL Server 事件警报”**。</span><span class="sxs-lookup"><span data-stu-id="1c607-127">In the **Type** list, select **SQL Server event alert**.</span></span>  
  
6.  <span data-ttu-id="1c607-128">在 **“事件警报定义”** 下的 **“数据库名称”** 列表中，选择一个数据库以将警报限制到特定数据库。</span><span class="sxs-lookup"><span data-stu-id="1c607-128">Under **Event alert definition**, in the **Database name** list, select a database to restrict the alert to a specific database.</span></span>  
  
7.  <span data-ttu-id="1c607-129">在 **“将根据以下条件触发警报”** 下，单击 **“严重性”** ，然后选择将引发警报的特定严重性。</span><span class="sxs-lookup"><span data-stu-id="1c607-129">Under **Alerts will be raised based on**, click **Severity** and then select the specific severity that will raise the alert.</span></span>  
  
8.  <span data-ttu-id="1c607-130">选中与 **“当消息包含以下内容时触发警报”** 复选框以将警报限制到特定的字符序列，然后在 **“消息正文”** 中输入关键字或字符串。</span><span class="sxs-lookup"><span data-stu-id="1c607-130">Check the box corresponding to **Raise alert when message contains** check box to restrict the alert to a particular character sequence, and then enter a keyword or character string for the **Message text**.</span></span> <span data-ttu-id="1c607-131">最大字符数为 100。</span><span class="sxs-lookup"><span data-stu-id="1c607-131">The maximum number of characters is 100.</span></span>  
  
9. <span data-ttu-id="1c607-132">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1c607-132">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1c607-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1c607-133">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-alert-using-severity-level"></a><span data-ttu-id="1c607-134">使用严重级别创建警报</span><span class="sxs-lookup"><span data-stu-id="1c607-134">To create an alert using severity level</span></span>  
  
1.  <span data-ttu-id="1c607-135">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="1c607-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1c607-136">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="1c607-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1c607-137">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="1c607-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adds an alert (Test Alert) that runs the Back up the AdventureWorks2012 Database job when fired   
    -- assumes that the message 55001 and the Back up the AdventureWorks2012 Database job already exist.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert',  
        @message_id = 55001,   
       @severity = 0,   
       @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
       @job_name = N'Back up the AdventureWorks2012 Database' ;  
    GO  
    ```  
  
 <span data-ttu-id="1c607-138">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_alert ](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1c607-138">For more information, see [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).</span></span>  
  
  
