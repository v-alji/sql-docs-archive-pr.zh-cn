---
title: 编辑操作员 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- modifying operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], modifying with Management Studio
ms.assetid: b2ba2168-ca0b-4b59-9007-4e1e4c30679e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45ffb520e240dfd97002060370ff6dcf7c60d083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577213"
---
# <a name="edit-an-operator"></a><span data-ttu-id="30dfe-102">编辑运算符</span><span class="sxs-lookup"><span data-stu-id="30dfe-102">Edit an Operator</span></span>
  <span data-ttu-id="30dfe-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中对操作员能否接收通知进行编辑，并编辑他们的电子邮件地址、寻呼地址和 net send 地址。</span><span class="sxs-lookup"><span data-stu-id="30dfe-103">This topic describes how to edit an operators' availability for receiving notifications and their e-mail, pager, and net send addresses in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="30dfe-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="30dfe-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="30dfe-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="30dfe-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="30dfe-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="30dfe-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="30dfe-107">安全性</span><span class="sxs-lookup"><span data-stu-id="30dfe-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="30dfe-108">**若要编辑操作员，可使用：**</span><span class="sxs-lookup"><span data-stu-id="30dfe-108">**To edit an operator, using:**</span></span>  
  
     [<span data-ttu-id="30dfe-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="30dfe-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="30dfe-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="30dfe-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="30dfe-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="30dfe-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="30dfe-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="30dfe-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="30dfe-113">在 **的未来版本中，将从** 代理中删除寻呼程序和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]选项。</span><span class="sxs-lookup"><span data-stu-id="30dfe-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="30dfe-114">请避免在新的开发工作中使用这些功能，并考虑修改当前使用这些功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="30dfe-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="30dfe-115">请注意，若要向操作员发送电子邮件和寻呼通知，必须将 SQL Server 代理配置为使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="30dfe-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="30dfe-116">有关详细信息，请参阅 [向操作员分配警报](assign-alerts-to-an-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="30dfe-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="30dfe-117">为管理作业提供了一种图形化的简便方法，建议使用此方法来创建和管理作业基础结构。</span><span class="sxs-lookup"><span data-stu-id="30dfe-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="30dfe-118">Security</span><span class="sxs-lookup"><span data-stu-id="30dfe-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="30dfe-119">权限</span><span class="sxs-lookup"><span data-stu-id="30dfe-119">Permissions</span></span>  
 <span data-ttu-id="30dfe-120">只有 **sysadmin** 固定服务器角色的成员才能编辑操作员。</span><span class="sxs-lookup"><span data-stu-id="30dfe-120">Only members of the **sysadmin** fixed server role can edit operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="30dfe-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="30dfe-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-edit-an-operator"></a><span data-ttu-id="30dfe-122">编辑操作员</span><span class="sxs-lookup"><span data-stu-id="30dfe-122">To edit an operator</span></span>  
  
1.  <span data-ttu-id="30dfe-123">在 **“对象资源管理器”** 中，单击加号以展开包含要编辑的操作员的服务器。</span><span class="sxs-lookup"><span data-stu-id="30dfe-123">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to edit.</span></span>  
  
2.  <span data-ttu-id="30dfe-124">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="30dfe-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="30dfe-125">单击加号以展开 **“操作员”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="30dfe-125">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="30dfe-126">右键单击要编辑的操作员，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30dfe-126">Right-click the operator that you want to edit and select **Properties**.</span></span>  
  
     <span data-ttu-id="30dfe-127">有关“operator_name 属性”__\*\*\*\* 对话框包含的可用选项的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="30dfe-127">For more information on the available options contained in the _operator_name_**Properties** dialog box, see:</span></span>  
  
    -   [<span data-ttu-id="30dfe-128">操作员属性和新操作员 &#40;常规 "页面&#41;</span><span class="sxs-lookup"><span data-stu-id="30dfe-128">Operator Properties and New Operator &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="30dfe-129">操作员属性：新建操作员 &#40;通知页面&#41;</span><span class="sxs-lookup"><span data-stu-id="30dfe-129">Operator Properties: New Operator &#40;Notifications Page&#41;</span></span>](operator-properties-new-operator-notifications-page.md)  
  
    -   [<span data-ttu-id="30dfe-130">操作员属性（“历史记录”页）</span><span class="sxs-lookup"><span data-stu-id="30dfe-130">Operator Properties &#40;History Page&#41;</span></span>](operator-properties-history-page.md)  
  
5.  <span data-ttu-id="30dfe-131">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="30dfe-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="30dfe-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="30dfe-132">Using Transact-SQL</span></span>  
  
#### <a name="to-edit-an-operator"></a><span data-ttu-id="30dfe-133">编辑操作员</span><span class="sxs-lookup"><span data-stu-id="30dfe-133">To edit an operator</span></span>  
  
1.  <span data-ttu-id="30dfe-134">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="30dfe-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="30dfe-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="30dfe-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="30dfe-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="30dfe-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- updates the operator status to enabled, and sets the days   
    -- (from Monday through Friday, from 8 A.M. through 5 P.M.) when the operator can be paged.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'Fran??ois Ajenstat',  
        @enabled = 1,  
        @email_address = N'fran??oisa',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 64 ;  
    GO  
    ```  
  
 <span data-ttu-id="30dfe-137">有关详细信息，请参阅[&#40;transact-sql&#41;sp_update_operator ](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="30dfe-137">For more information, see [sp_update_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql).</span></span>  
  
  
