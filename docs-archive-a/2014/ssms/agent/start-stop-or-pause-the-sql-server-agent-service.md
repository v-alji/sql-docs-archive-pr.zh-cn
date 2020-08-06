---
title: 启动、停止或暂停 SQL Server 代理服务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2feb6a18c602271b1bec871fbfc9793979b100e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682654"
---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a><span data-ttu-id="5795a-102">Start, Stop, or Pause the SQL Server Agent Service</span><span class="sxs-lookup"><span data-stu-id="5795a-102">Start, Stop, or Pause the SQL Server Agent Service</span></span>
  <span data-ttu-id="5795a-103">本主题说明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]启动、停止或重新启动 SQL Server 代理服务。</span><span class="sxs-lookup"><span data-stu-id="5795a-103">This topic describes how to start, stop, or restart the SQL Server Agent Service in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="5795a-104">您可以配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务，使其在操作系统启动时自动启动，也可以在需要完成作业时手动启动。</span><span class="sxs-lookup"><span data-stu-id="5795a-104">You can configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to start automatically when the operating system starts, or you can start it manually when you need to complete jobs.</span></span> <span data-ttu-id="5795a-105">您可以停止或暂停 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务以挂起作业、操作员通知和警报。</span><span class="sxs-lookup"><span data-stu-id="5795a-105">You can stop or pause the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to suspend jobs, operator notifications, and alerts.</span></span>  
  
 <span data-ttu-id="5795a-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="5795a-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5795a-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="5795a-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5795a-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="5795a-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5795a-109">安全性</span><span class="sxs-lookup"><span data-stu-id="5795a-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="5795a-110">使用 SQL Server Management Studio 启动、停止或重新启动 SQL Server 代理服务</span><span class="sxs-lookup"><span data-stu-id="5795a-110">To start, stop, or restart the SQL Server Agent Service using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5795a-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="5795a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5795a-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="5795a-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="5795a-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理必须作为服务运行，才能自动执行管理任务。</span><span class="sxs-lookup"><span data-stu-id="5795a-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be running as a service in order to automate administrative tasks.</span></span> <span data-ttu-id="5795a-114">有关详细信息，请参阅 [Configure SQL Server Agent](configure-sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="5795a-114">For more information, see [Configure SQL Server Agent](configure-sql-server-agent.md).</span></span>  
  
-   <span data-ttu-id="5795a-115">“对象资源管理器”仅在您拥有使用权限时才显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理节点。</span><span class="sxs-lookup"><span data-stu-id="5795a-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5795a-116">Security</span><span class="sxs-lookup"><span data-stu-id="5795a-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5795a-117">权限</span><span class="sxs-lookup"><span data-stu-id="5795a-117">Permissions</span></span>  
 <span data-ttu-id="5795a-118">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，必须将 **代理配置为使用** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定服务器角色的成员帐户的凭据，才能执行其功能。</span><span class="sxs-lookup"><span data-stu-id="5795a-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5795a-119">该帐户必须拥有以下 Windows 权限：</span><span class="sxs-lookup"><span data-stu-id="5795a-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="5795a-120">以服务身份登录 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="5795a-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="5795a-121">替换进程级别标记 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="5795a-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="5795a-122">跳过遍历检查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="5795a-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="5795a-123">调整进程的内存配额 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="5795a-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="5795a-124">有关代理服务帐户所需的 Windows 权限的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅为[SQL Server 代理服务选择帐户](select-an-account-for-the-sql-server-agent-service.md)和[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="5795a-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5795a-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5795a-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a><span data-ttu-id="5795a-126">启动、停止或重新启动 SQL Server 代理服务</span><span class="sxs-lookup"><span data-stu-id="5795a-126">To start, stop, or restart the SQL Server Agent Service</span></span>  
  
1.  <span data-ttu-id="5795a-127">在 **“对象资源管理器”** 中，单击加号以展开要管理 SQL Server 代理服务的服务器。</span><span class="sxs-lookup"><span data-stu-id="5795a-127">In **Object Explorer**, click the plus sign to expand the server where you want to manage SQL Server Agent Service.</span></span>  
  
2.  <span data-ttu-id="5795a-128">右键单击“SQL Server 代理”\*\*\*\*，然后选择“启动”\*\*\*\*、“停止”\*\*\*\* 或“重启”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5795a-128">Right-click **SQL Server Agent**, and then select either **Start**, **Stop**, or **Restart**.</span></span>  
  
3.  <span data-ttu-id="5795a-129">在“用户帐户控制”对话框中，单击“是”。</span><span class="sxs-lookup"><span data-stu-id="5795a-129">In the **User Account Control** dialog box, click **Yes**.</span></span>  
  
4.  <span data-ttu-id="5795a-130">系统提示是否要执行该操作时，请单击 **“是”**。</span><span class="sxs-lookup"><span data-stu-id="5795a-130">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
 <span data-ttu-id="5795a-131">有关详细信息，请参见:</span><span class="sxs-lookup"><span data-stu-id="5795a-131">For more information, see:</span></span>  
  
-   [<span data-ttu-id="5795a-132">启动、停止、暂停、继续、重新启动数据库引擎、SQL Server 代理或 SQL Server Browser 服务</span><span class="sxs-lookup"><span data-stu-id="5795a-132">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
-   [<span data-ttu-id="5795a-133">自动启动 SQL Server 代理 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5795a-133">Autostart SQL Server Agent &#40;SQL Server Management Studio&#41;</span></span>](autostart-sql-server-agent-sql-server-management-studio.md)  
  
  
