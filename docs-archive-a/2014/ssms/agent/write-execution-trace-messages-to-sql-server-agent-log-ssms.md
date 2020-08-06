---
title: 将执行跟踪消息写入 SQL Server 代理错误日志 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- writing trace messages
- traces [SQL Server], SQL Server Agent logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 90e3731e-6fae-43db-833e-9accecdd1c03
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38b08452ef2680b654dd735b901488cb5f5f5f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691017"
---
# <a name="write-execution-trace-messages-to-the-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="aa5d1-102">Write Execution Trace Messages to the SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="aa5d1-102">Write Execution Trace Messages to the SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="aa5d1-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用在中将代理配置为在其错误日志中包含执行跟踪消息 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="aa5d1-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to include execution trace messages in its error log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="aa5d1-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="aa5d1-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="aa5d1-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="aa5d1-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="aa5d1-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="aa5d1-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="aa5d1-107">安全性</span><span class="sxs-lookup"><span data-stu-id="aa5d1-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="aa5d1-108">使用 SQL Server Management Studio 将执行跟踪消息写入 SQL Server 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="aa5d1-108">To write execution trace messages to the SQL Server Agent Error Log using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="aa5d1-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="aa5d1-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="aa5d1-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="aa5d1-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="aa5d1-111">“对象资源管理器”仅在您拥有使用权限时才显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理节点。</span><span class="sxs-lookup"><span data-stu-id="aa5d1-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="aa5d1-112">由于此选项会导致错误日志变得非常大，因此，仅在调查特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理问题时在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志中包含执行跟踪消息。</span><span class="sxs-lookup"><span data-stu-id="aa5d1-112">Because this option can cause the error log to become large, only include execution trace messages in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logs when investigating a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent problem.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="aa5d1-113">Security</span><span class="sxs-lookup"><span data-stu-id="aa5d1-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="aa5d1-114">权限</span><span class="sxs-lookup"><span data-stu-id="aa5d1-114">Permissions</span></span>  
 <span data-ttu-id="aa5d1-115">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，必须将 **代理配置为使用** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定服务器角色的成员帐户的凭据，才能执行其功能。</span><span class="sxs-lookup"><span data-stu-id="aa5d1-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="aa5d1-116">该帐户必须拥有以下 Windows 权限：</span><span class="sxs-lookup"><span data-stu-id="aa5d1-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="aa5d1-117">以服务身份登录 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="aa5d1-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="aa5d1-118">替换进程级别标记 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="aa5d1-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="aa5d1-119">跳过遍历检查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="aa5d1-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="aa5d1-120">调整进程的内存配额 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="aa5d1-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="aa5d1-121">有关代理服务帐户所需的 Windows 权限的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅为[SQL Server 代理服务选择帐户](select-an-account-for-the-sql-server-agent-service.md)和[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="aa5d1-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>   
#### <a name="to-write-execution-trace-messages-to-the-sql-server-agent-error-log"></a><span data-ttu-id="aa5d1-122">将执行跟踪消息写入到 SQL Server 代理错误日志中</span><span class="sxs-lookup"><span data-stu-id="aa5d1-122">To write execution trace messages to the SQL Server Agent error log</span></span>  
  
1.  <span data-ttu-id="aa5d1-123">在 **“对象资源管理器”** 中，单击加号以展开包含要将执行跟踪消息写入到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志的服务器。</span><span class="sxs-lookup"><span data-stu-id="aa5d1-123">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log to which you want to write execution trace messages.</span></span>  
  
2.  <span data-ttu-id="aa5d1-124">右键单击“SQL Server 代理”\*\*\*\*，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aa5d1-124">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="aa5d1-125">在 " **SQL Server 代理属性-**_server_name_ " 对话框中的 "**常规**" 页上的 "**错误日志**" 下，选中 "**包含执行跟踪消息**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="aa5d1-125">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Error log** on the **General** page, select the **Include execution trace messages** check box.</span></span>  
  
4.  <span data-ttu-id="aa5d1-126">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="aa5d1-126">Click **OK**.</span></span>  
  
  
