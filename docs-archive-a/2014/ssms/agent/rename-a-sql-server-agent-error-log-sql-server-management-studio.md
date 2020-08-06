---
title: 重命名 SQL Server 代理错误日志 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- renaming SQL Server Agent error log
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: dee2b199-48af-44cb-9177-d029a5edb169
author: stevestein
ms.author: sstein
ms.openlocfilehash: c1c85550a29bfff316ffc275ba2d4e4df10686d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591046"
---
# <a name="rename-a-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="d8065-102">Rename a SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d8065-102">Rename a SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="d8065-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用在中编写代理错误的文件 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d8065-103">This topic describes how to rename the file where [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent errors are written in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d8065-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="d8065-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d8065-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="d8065-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d8065-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="d8065-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d8065-107">安全性</span><span class="sxs-lookup"><span data-stu-id="d8065-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="d8065-108">使用 SQL Server Management Studio 重命名 SQL Server 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="d8065-108">To rename a SQL Server Agent error log using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d8065-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="d8065-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d8065-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="d8065-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d8065-111">“对象资源管理器”仅在您拥有使用权限时才显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理节点。</span><span class="sxs-lookup"><span data-stu-id="d8065-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d8065-112">代理服务后， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理才写入到新的日志文件。</span><span class="sxs-lookup"><span data-stu-id="d8065-112">Agent will not write to the new log file until the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is restarted.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d8065-113">Security</span><span class="sxs-lookup"><span data-stu-id="d8065-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d8065-114">权限</span><span class="sxs-lookup"><span data-stu-id="d8065-114">Permissions</span></span>  
 <span data-ttu-id="d8065-115">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，必须将 **代理配置为使用** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定服务器角色的成员帐户的凭据，才能执行其功能。</span><span class="sxs-lookup"><span data-stu-id="d8065-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d8065-116">该帐户必须拥有以下 Windows 权限：</span><span class="sxs-lookup"><span data-stu-id="d8065-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="d8065-117">以服务身份登录 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="d8065-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="d8065-118">替换进程级别标记 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="d8065-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="d8065-119">跳过遍历检查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="d8065-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="d8065-120">调整进程的内存配额 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="d8065-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="d8065-121">有关代理服务帐户所需的 Windows 权限的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅为[SQL Server 代理服务选择帐户](select-an-account-for-the-sql-server-agent-service.md)和[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="d8065-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d8065-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d8065-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-sql-server-agent-error-log"></a><span data-ttu-id="d8065-123">重命名 SQL Server 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="d8065-123">To rename a SQL Server Agent error log</span></span>  
  
1.  <span data-ttu-id="d8065-124">在 **“对象资源管理器”** 中，单击加号以展开包含要重命名的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志的服务器。</span><span class="sxs-lookup"><span data-stu-id="d8065-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log that you want to rename.</span></span>  
  
2.  <span data-ttu-id="d8065-125">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="d8065-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="d8065-126">右键单击“错误日志”\*\*\*\* 文件夹，然后选择“配置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8065-126">Right-click the **Error Logs** folder and select **Configure**.</span></span>  
  
4.  <span data-ttu-id="d8065-127">在 **“配置 SQL Server 代理错误日志”** 对话框的 **“错误日志文件”** 框中，输入错误日志的新文件路径和文件名称。</span><span class="sxs-lookup"><span data-stu-id="d8065-127">In the **Configure SQL Server Agent Error Logs** dialog box, in the **Error log file** box, enter the new file path and file name for the error log.</span></span> <span data-ttu-id="d8065-128">或者，单击省略号 **(...)** 以打开“指定代理错误日志位置”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="d8065-128">Alternately, click the ellipsis **(...)** to open the **Specify agent error log location** dialog box.</span></span>  
  
5.  <span data-ttu-id="d8065-129">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="d8065-129">When finished, click **OK**.</span></span>  
  
  
