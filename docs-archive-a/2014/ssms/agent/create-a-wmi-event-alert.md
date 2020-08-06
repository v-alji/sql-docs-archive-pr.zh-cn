---
title: 创建 WMI 事件警报 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI event alerts [SQL Server Management Studio]
ms.assetid: b8c46db6-408b-484e-98f0-a8af3e7ec763
author: stevestein
ms.author: sstein
ms.openlocfilehash: 737e7ccac9c92e663040e71339aa120f8db8b80b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588240"
---
# <a name="create-a-wmi-event-alert"></a><span data-ttu-id="5df7d-102">创建 WMI 事件警报</span><span class="sxs-lookup"><span data-stu-id="5df7d-102">Create a WMI Event Alert</span></span>
  <span data-ttu-id="5df7d-103">本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中创建 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 代理警报，以便在出现由 WMI Provider for Server Events 监视的特定 [!INCLUDE[tsql](../../includes/tsql-md.md)]事件时引发警报。</span><span class="sxs-lookup"><span data-stu-id="5df7d-103">This topic describes how to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert that is raised when a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] event occurs that is monitored by the WMI Provider for Server Events in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="5df7d-104">有关使用 WMI 提供程序监视事件的信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[wmi Provider For Server Events 的概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="5df7d-104">For information about the using the WMI Provider to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events, see [WMI Provider for Server Events Concepts](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md).</span></span> <span data-ttu-id="5df7d-105">有关接收 WMI 事件警报通知的所需权限的信息，请参阅 [为 SQL Server 代理服务选择帐户](select-an-account-for-the-sql-server-agent-service.md)。</span><span class="sxs-lookup"><span data-stu-id="5df7d-105">For information about the permissions necessary to receive WMI event alert notifications, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md).</span></span> <span data-ttu-id="5df7d-106">有关 WQL 的详细信息，请参阅 [将 WQL 与 WMI Provider for Server Events 结合使用](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)。</span><span class="sxs-lookup"><span data-stu-id="5df7d-106">For more information about WQL, see [Using WQL with the WMI Provider for Server Events](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md).</span></span>  
  
 <span data-ttu-id="5df7d-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="5df7d-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5df7d-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="5df7d-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5df7d-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="5df7d-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5df7d-110">安全性</span><span class="sxs-lookup"><span data-stu-id="5df7d-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5df7d-111">**若要创建 WMI 事件警报，可使用：**</span><span class="sxs-lookup"><span data-stu-id="5df7d-111">**To create a WMI event alert, using:**</span></span>  
  
     [<span data-ttu-id="5df7d-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5df7d-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5df7d-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5df7d-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5df7d-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="5df7d-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5df7d-115">限制和局限</span><span class="sxs-lookup"><span data-stu-id="5df7d-115">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="5df7d-116">提供了一种易用的图形方式来管理整个警报系统，这也是配置警报基础结构的推荐方式。</span><span class="sxs-lookup"><span data-stu-id="5df7d-116">provides an easy, graphical way to manage the entire alerting system and is the recommended way to configure an alert infrastructure.</span></span>  
  
-   <span data-ttu-id="5df7d-117">用 **xp_logevent** 生成的事件在 master 数据库中发生。</span><span class="sxs-lookup"><span data-stu-id="5df7d-117">Events generated with **xp_logevent** occur in the master database.</span></span> <span data-ttu-id="5df7d-118">因此，除非警报的 **xp_logevent** 为 **@database_name** 或 NULL，否则 **@database_name** 不触发警报。</span><span class="sxs-lookup"><span data-stu-id="5df7d-118">Therefore, **xp_logevent** does not trigger an alert unless the **@database_name** for the alert is **'master'** or NULL.</span></span>  
  
-   <span data-ttu-id="5df7d-119">仅支持运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的计算机上的 WMI 命名空间。</span><span class="sxs-lookup"><span data-stu-id="5df7d-119">Only WMI namespaces on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent are supported.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5df7d-120">Security</span><span class="sxs-lookup"><span data-stu-id="5df7d-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5df7d-121">权限</span><span class="sxs-lookup"><span data-stu-id="5df7d-121">Permissions</span></span>  
 <span data-ttu-id="5df7d-122">默认情况下，只有 **sysadmin** 固定服务器角色的成员才能执行 **sp_add_alert**。</span><span class="sxs-lookup"><span data-stu-id="5df7d-122">By default, only members of the **sysadmin** fixed server role can execute **sp_add_alert**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5df7d-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5df7d-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-wmi-event-alert"></a><span data-ttu-id="5df7d-124">创建 WMI 事件警报</span><span class="sxs-lookup"><span data-stu-id="5df7d-124">To create a WMI event alert</span></span>  
  
1.  <span data-ttu-id="5df7d-125">在 **“对象资源管理器”** 中，单击加号以展开要创建 WMI 事件警报的服务器。</span><span class="sxs-lookup"><span data-stu-id="5df7d-125">In **Object Explorer,** click the plus sign to expand the server where you want to create a WMI event alert.</span></span>  
  
2.  <span data-ttu-id="5df7d-126">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="5df7d-126">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="5df7d-127">右键单击“警报”\*\*\*\* 并选择“新建警报”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5df7d-127">Right-click **Alerts** and select **New Alert**.</span></span>  
  
4.  <span data-ttu-id="5df7d-128">在 **“新建警报”** 对话框的 **“名称”** 框中，输入此警报的名称。</span><span class="sxs-lookup"><span data-stu-id="5df7d-128">In the **New Alert** dialog box, in the **Name** box, enter a name for this alert.</span></span>  
  
5.  <span data-ttu-id="5df7d-129">选中 **“启用”** 复选框将运行警报。</span><span class="sxs-lookup"><span data-stu-id="5df7d-129">Check the **Enable** check box to enable the alert to run.</span></span> <span data-ttu-id="5df7d-130">默认情况下， **“启用”** 为选中状态。</span><span class="sxs-lookup"><span data-stu-id="5df7d-130">By default, **Enable** is checked.</span></span>  
  
6.  <span data-ttu-id="5df7d-131">在 **“类型”** 列表中，选择 **“WMI 事件警报”**。</span><span class="sxs-lookup"><span data-stu-id="5df7d-131">In the **Type** list, select **WMI event alert**.</span></span>  
  
7.  <span data-ttu-id="5df7d-132">在“WMI 事件警报定义”\*\*\*\* 下的“命名空间”\*\*\*\* 框中，为标识触发该警报的 WMI 事件的 WMI 查询语言 (WQL) 语句指定 WMI 命名空间。</span><span class="sxs-lookup"><span data-stu-id="5df7d-132">Under **WMI event alert definition**, in the **Namespace** box, specify the WMI namespace for the WMI Query Language (WQL) statement that identifies which WMI event will trigger this alert.</span></span>  
  
8.  <span data-ttu-id="5df7d-133">在 **“查询”** 框中，指定标识该警报所响应事件的 WQL 语句。</span><span class="sxs-lookup"><span data-stu-id="5df7d-133">In the **Query** box, specify the WQL statement that identifies the event that this alert responds to.</span></span>  
  
9. <span data-ttu-id="5df7d-134">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="5df7d-134">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5df7d-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5df7d-135">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-wmi-event-alert"></a><span data-ttu-id="5df7d-136">创建 WMI 事件警报</span><span class="sxs-lookup"><span data-stu-id="5df7d-136">To create a WMI event alert</span></span>  
  
1.  <span data-ttu-id="5df7d-137">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="5df7d-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5df7d-138">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="5df7d-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5df7d-139">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="5df7d-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates a WMI event alert that retrieves all event properties for any ALTER_TABLE event that occurs on table AdventureWorks2012.Sales.SalesOrderDetail  
    -- This example assumes that the message 54001 already exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert 2',  
        @message_id = 54001  
        @notification_message = N'Error 54001 has occurred on the Sales.SalesOrderDetail table on the AdventureWorks2012 database. Please see the following information...',  
        @wmi_namespace = '\\.\root\Microsoft\SqlServer\ServerEvents\,  
        @wmi_query = N'SELECT * FROM ALTER_TABLE   
    WHERE DatabaseName = 'AdventureWorks2012' AND SchemaName = 'Sales'   
        AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'';  
    GO  
    ```  
  
 <span data-ttu-id="5df7d-140">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_alert ](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5df7d-140">For more information, see [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).</span></span>  
  
  
