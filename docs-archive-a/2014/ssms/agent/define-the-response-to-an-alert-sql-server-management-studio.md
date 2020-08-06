---
title: 定义对警报的响应 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], responding to
- responding to alerts
ms.assetid: c86ca6eb-c59f-46e9-bc32-d474e7c3b170
author: stevestein
ms.author: sstein
ms.openlocfilehash: c14e5adf43602b57697483b9ce4c2cdf20ff8e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689250"
---
# <a name="define-the-response-to-an-alert-sql-server-management-studio"></a><span data-ttu-id="f5df6-102">定义对警报的响应 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f5df6-102">Define the Response to an Alert (SQL Server Management Studio)</span></span>
  <span data-ttu-id="f5df6-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中定义对代理警报的响应方式 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f5df6-103">This topic describes how to define how [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] responds to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f5df6-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f5df6-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f5df6-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f5df6-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f5df6-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f5df6-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f5df6-107">安全性</span><span class="sxs-lookup"><span data-stu-id="f5df6-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f5df6-108">**若要定义对警报的响应，可使用：**</span><span class="sxs-lookup"><span data-stu-id="f5df6-108">**To define the response to an alert, using:**</span></span>  
  
     [<span data-ttu-id="f5df6-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f5df6-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f5df6-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f5df6-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f5df6-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="f5df6-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f5df6-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f5df6-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f5df6-113">在 **的未来版本中，将从** 代理中删除寻呼程序和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]选项。</span><span class="sxs-lookup"><span data-stu-id="f5df6-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f5df6-114">请避免在新的开发工作中使用这些功能，并考虑修改当前使用这些功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="f5df6-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="f5df6-115">请注意，若要向操作员发送电子邮件和寻呼通知，必须将 SQL Server 代理配置为使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="f5df6-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="f5df6-116">有关详细信息，请参阅 [向操作员分配警报](assign-alerts-to-an-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="f5df6-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f5df6-117">为管理作业提供了一种图形化的简便方法，建议使用此方法来创建和管理作业基础结构。</span><span class="sxs-lookup"><span data-stu-id="f5df6-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f5df6-118">Security</span><span class="sxs-lookup"><span data-stu-id="f5df6-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f5df6-119">权限</span><span class="sxs-lookup"><span data-stu-id="f5df6-119">Permissions</span></span>  
 <span data-ttu-id="f5df6-120">只有 **sysadmin** 固定服务器角色的成员才能定义对警报的响应。</span><span class="sxs-lookup"><span data-stu-id="f5df6-120">Only members of the **sysadmin** fixed server role can define the response to an alert.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f5df6-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f5df6-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-the-response-to-an-alert"></a><span data-ttu-id="f5df6-122">定义对警报的响应</span><span class="sxs-lookup"><span data-stu-id="f5df6-122">To define the response to an alert</span></span>  
  
1.  <span data-ttu-id="f5df6-123">在 **“对象资源管理器”** 中，单击加号以便展开包含您要对其定义响应的警报的服务器。</span><span class="sxs-lookup"><span data-stu-id="f5df6-123">In **Object Explorer**, click the plus sign to expand the server that contains the alert on which you want to define a response.</span></span>  
  
2.  <span data-ttu-id="f5df6-124">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="f5df6-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="f5df6-125">单击加号以展开 **“警报”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f5df6-125">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="f5df6-126">右键单击要对其定义响应的警报，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5df6-126">Right-click the alert on which you want to define a response and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="f5df6-127">在 " _alert_name_**警报属性**" 对话框中的 "**选择页**" 下，选择 "**响应**"。</span><span class="sxs-lookup"><span data-stu-id="f5df6-127">In the _alert_name_**alert properties** dialog box, under **Select a page**, select **Response**.</span></span>  
  
6.  <span data-ttu-id="f5df6-128">选中 **“执行作业”** 复选框，然后从 **“执行作业”** 复选框下的列表中选择出现警报时执行的作业。</span><span class="sxs-lookup"><span data-stu-id="f5df6-128">Select the **Execute job** check box and, from the list below the **Execute job** check box, select a job to execute when the alert occurs.</span></span> <span data-ttu-id="f5df6-129">您可以单击 **“新建作业”** 来创建新的作业。</span><span class="sxs-lookup"><span data-stu-id="f5df6-129">You can create a new job by clicking **New Job**.</span></span> <span data-ttu-id="f5df6-130">也可以单击 **“查看作业”** 查看有关作业的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f5df6-130">You can view more information about the job by clicking **View Job**.</span></span> <span data-ttu-id="f5df6-131">有关 "**新建作业**" 和 "**作业属性**"_job_name_对话框中可用选项的详细信息，请参阅[创建作业](create-a-job.md)和[查看作业](view-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="f5df6-131">For more information about the available options in the **New Job** and **Job Properties**_job_name_ dialog boxes, see [Create a Job](create-a-job.md) and [View a Job](view-a-job.md).</span></span>  
  
7.  <span data-ttu-id="f5df6-132">如果要在激活警报时通知操作员，请选中 **“通知操作员”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="f5df6-132">Select the **Notify Operators** check box if you want to notify operators when the alert is activated.</span></span> <span data-ttu-id="f5df6-133">在“操作员”\*\*\*\* 列表中，选择以下用于通知操作员的一个或多个方法：“电子邮件”\*\*\*\*、“寻呼程序”\*\*\*\* 或“Net Send”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5df6-133">In the **Operator list**, select one or more of the following methods for notifying the operator or operators: **E-mail**, **Pager**, or **Net Send**.</span></span> <span data-ttu-id="f5df6-134">您可以单击 **“新建操作员”** 创建新的操作员。</span><span class="sxs-lookup"><span data-stu-id="f5df6-134">You can create a new operator by clicking **New Operator**.</span></span> <span data-ttu-id="f5df6-135">也可以单击 **“查看操作员”** 查看有关操作员的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f5df6-135">You can view more information about an operator by clicking **View Operator**.</span></span> <span data-ttu-id="f5df6-136">有关 **“新建操作员”** 和 **“查看操作员属性”** 对话框中的可用选项的详细信息，请参阅 [Create an Operator](create-an-operator.md) 和 [View Information About an Operator](view-information-about-an-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="f5df6-136">For more information about the available options in the **New Operator** and **View Operator Properties** dialog boxes, see [Create an Operator](create-an-operator.md) and [View Information About an Operator](view-information-about-an-operator.md).</span></span>  
  
8.  <span data-ttu-id="f5df6-137">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="f5df6-137">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f5df6-138">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f5df6-138">Using Transact-SQL</span></span>  
  
#### <a name="to-define-the-response-to-an-alert"></a><span data-ttu-id="f5df6-139">定义对警报的响应</span><span class="sxs-lookup"><span data-stu-id="f5df6-139">To define the response to an alert</span></span>  
  
1.  <span data-ttu-id="f5df6-140">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="f5df6-140">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f5df6-141">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="f5df6-141">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f5df6-142">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="f5df6-142">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adds an e-mail notification for Test Alert.  
    -- assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'Fran??ois Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="f5df6-143">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_notification ](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f5df6-143">For more information, see [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).</span></span>  
  
  
