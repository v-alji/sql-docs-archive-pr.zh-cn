---
title: 修改作业的目标服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 246a5bb59a681a70734cc8cabef4f724cda1b52e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580530"
---
# <a name="modify-the-target-servers-for-a-job"></a><span data-ttu-id="97f40-102">Modify the Target Servers for a Job</span><span class="sxs-lookup"><span data-stu-id="97f40-102">Modify the Target Servers for a Job</span></span>
  <span data-ttu-id="97f40-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中更改代理作业的目标服务器 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="97f40-103">This topic describes how to change the target servers for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="97f40-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="97f40-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="97f40-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="97f40-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="97f40-106">安全性</span><span class="sxs-lookup"><span data-stu-id="97f40-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="97f40-107">**若要修改作业的目标服务器，请使用：**</span><span class="sxs-lookup"><span data-stu-id="97f40-107">**To modify the target servers for a job, using:**</span></span>  
  
     [<span data-ttu-id="97f40-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="97f40-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="97f40-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="97f40-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="97f40-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="97f40-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="97f40-111">Security</span><span class="sxs-lookup"><span data-stu-id="97f40-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="97f40-112">权限</span><span class="sxs-lookup"><span data-stu-id="97f40-112">Permissions</span></span>  
 <span data-ttu-id="97f40-113">默认情况下，sysadmin 固定服务器角色的成员可以执行此存储过程。</span><span class="sxs-lookup"><span data-stu-id="97f40-113">By default, members of the sysadmin fixed server role can execute this stored procedure.</span></span> <span data-ttu-id="97f40-114">其他用户必须被授予 msdb 数据库中下列 SQL Server 代理固定数据库角色的权限之一：</span><span class="sxs-lookup"><span data-stu-id="97f40-114">Other users must be granted one of the following SQL Server Agent fixed database roles in the msdb database:</span></span>  
  
1.  `SQLAgentUserRole`  
  
2.  `SQLAgentReaderRole`  
  
3.  <span data-ttu-id="97f40-115">SQLAgentOperatorRole</span><span class="sxs-lookup"><span data-stu-id="97f40-115">SQLAgentOperatorRole</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="97f40-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="97f40-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a><span data-ttu-id="97f40-117">修改作业的目标服务器</span><span class="sxs-lookup"><span data-stu-id="97f40-117">To modify the target servers for a job</span></span>  
  
1.  <span data-ttu-id="97f40-118">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="97f40-118">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="97f40-119">展开“SQL Server 代理”\*\*\*\*，再展开“作业”\*\*\*\*，右键单击某个作业，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="97f40-119">Expand **SQL Server Agent**, expand **Jobs**, right-click a job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="97f40-120">在“作业属性\*\*\*\*”对话框中，选择“目标”\*\*\*\* 页，然后单击“目标为本地服务器”\*\*\*\* 或“目标为多台服务器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="97f40-120">In the **Job Properties** dialog, select the **Targets**page, and click **Target local server**, or **Target multiple servers**.</span></span>  
  
     <span data-ttu-id="97f40-121">如果选择 **“目标为多台服务器”**，请选中服务器名称左边的框将其指定为作业的目标服务器。</span><span class="sxs-lookup"><span data-stu-id="97f40-121">If you choose **Target multiple servers**, designate the servers that will be targets for the job by checking the box to the left of the server name.</span></span> <span data-ttu-id="97f40-122">验证未选中不作为作业的目标服务器旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="97f40-122">Verify that the check boxes for servers that will not be targets of the job are unchecked.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="97f40-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="97f40-123">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a><span data-ttu-id="97f40-124">修改作业的目标服务器</span><span class="sxs-lookup"><span data-stu-id="97f40-124">To modify the target servers for a job</span></span>  
  
1.  <span data-ttu-id="97f40-125">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="97f40-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="97f40-126">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="97f40-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="97f40-127">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="97f40-127">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="97f40-128">此示例将“每周销售备份”多服务器作业分配给服务器 SEATTLE2。</span><span class="sxs-lookup"><span data-stu-id="97f40-128">This example assigns the multiserver job Weekly Sales Backups to the server SEATTLE2.</span></span>  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
  
```  
  
 <span data-ttu-id="97f40-129">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_jobserver ](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="97f40-129">For more information, see [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f40-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97f40-130">See Also</span></span>  
 [<span data-ttu-id="97f40-131">企业范围的自动化管理</span><span class="sxs-lookup"><span data-stu-id="97f40-131">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
