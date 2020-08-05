---
title: 查看有关操作员的信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- viewing operators
- operators (users) [Database Engine], viewing with Management Studio
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- displaying operators
ms.assetid: 92c82cdf-f704-444e-9539-82aea7fe6fb7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 680b90401f800a9c435bdae33b8e55385541cc4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580511"
---
# <a name="view-information-about-an-operator"></a><span data-ttu-id="728b9-102">View Information About an Operator</span><span class="sxs-lookup"><span data-stu-id="728b9-102">View Information About an Operator</span></span>
  <span data-ttu-id="728b9-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中查看有关代理操作员的信息 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="728b9-103">This topic describes how to view information about a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="728b9-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="728b9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="728b9-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="728b9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="728b9-106">安全性</span><span class="sxs-lookup"><span data-stu-id="728b9-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="728b9-107">**若要查看有关操作员的信息，可使用：**</span><span class="sxs-lookup"><span data-stu-id="728b9-107">**To view information about an operator, using:**</span></span>  
  
     [<span data-ttu-id="728b9-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="728b9-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="728b9-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="728b9-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="728b9-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="728b9-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="728b9-111">Security</span><span class="sxs-lookup"><span data-stu-id="728b9-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="728b9-112">权限</span><span class="sxs-lookup"><span data-stu-id="728b9-112">Permissions</span></span>  
 <span data-ttu-id="728b9-113">默认情况下， **sysadmin**固定服务器角色的成员可以执行此存储过程。</span><span class="sxs-lookup"><span data-stu-id="728b9-113">By default, members of the **sysadmin** fixed server role can execute this stored procedure.</span></span> <span data-ttu-id="728b9-114">其他用户必须被授予 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **数据库中下列** 代理固定数据库角色的权限之一：</span><span class="sxs-lookup"><span data-stu-id="728b9-114">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="728b9-115">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="728b9-115">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="728b9-116">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="728b9-116">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="728b9-117">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="728b9-117">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="728b9-118">有关这些角色的权限的详细信息，请参阅 [SQL Server 代理固定数据库角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="728b9-118">For details about the permissions of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="728b9-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="728b9-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-information-about-an-operator"></a><span data-ttu-id="728b9-120">查看有关操作员的信息</span><span class="sxs-lookup"><span data-stu-id="728b9-120">To view information about an operator</span></span>  
  
1.  <span data-ttu-id="728b9-121">在 **“对象资源管理器”** 中，单击加号以展开包含要查看的操作员的服务器。</span><span class="sxs-lookup"><span data-stu-id="728b9-121">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to view.</span></span>  
  
2.  <span data-ttu-id="728b9-122">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="728b9-122">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="728b9-123">单击加号以展开 **“操作员”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="728b9-123">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="728b9-124">右键单击要查看的操作员，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="728b9-124">Right-click the operator that you want to view and select **Properties**.</span></span>  
  
     <span data-ttu-id="728b9-125">有关“operator_name 属性”__\*\*\*\* 对话框包含的可用选项的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="728b9-125">For more information on the available options contained in the _operator_name_**Properties** dialog box, see:</span></span>  
  
    -   [<span data-ttu-id="728b9-126">操作员属性和新操作员 &#40;常规 "页面&#41;</span><span class="sxs-lookup"><span data-stu-id="728b9-126">Operator Properties and New Operator &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="728b9-127">操作员属性：新建操作员 &#40;通知页面&#41;</span><span class="sxs-lookup"><span data-stu-id="728b9-127">Operator Properties: New Operator &#40;Notifications Page&#41;</span></span>](operator-properties-new-operator-notifications-page.md)  
  
    -   [<span data-ttu-id="728b9-128">操作员属性（“历史记录”页）</span><span class="sxs-lookup"><span data-stu-id="728b9-128">Operator Properties &#40;History Page&#41;</span></span>](operator-properties-history-page.md)  
  
5.  <span data-ttu-id="728b9-129">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="728b9-129">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="728b9-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="728b9-130">Using Transact-SQL</span></span>  
  
#### <a name="to-view-information-about-an-operator"></a><span data-ttu-id="728b9-131">查看有关操作员的信息</span><span class="sxs-lookup"><span data-stu-id="728b9-131">To view information about an operator</span></span>  
  
1.  <span data-ttu-id="728b9-132">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="728b9-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="728b9-133">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="728b9-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="728b9-134">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="728b9-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- reports information about operator Fran??ois Ajenstat   
    -- This example assumes that the operator exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_operator  
        @operator_name = N'Fran??ois Ajenstat' ;  
    GO  
    ```  
  
 <span data-ttu-id="728b9-135">有关详细信息，请参阅[&#40;transact-sql&#41;sp_help_operator ](/sql/relational-databases/system-stored-procedures/sp-help-operator-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="728b9-135">For more information, see [sp_help_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-operator-transact-sql).</span></span>  
  
  
