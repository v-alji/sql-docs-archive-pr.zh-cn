---
title: 自动启动 SQL Server 代理 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- autostart SQL Server Agent
ms.assetid: 2ea332da-0ede-4d2b-b122-c4c10eaca191
author: stevestein
ms.author: sstein
ms.openlocfilehash: a39c7c7a112370797a965cfa601bc07f983a7a37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588241"
---
# <a name="autostart-sql-server-agent-sql-server-management-studio"></a><span data-ttu-id="681de-102">Autostart SQL Server Agent (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="681de-102">Autostart SQL Server Agent (SQL Server Management Studio)</span></span>
  <span data-ttu-id="681de-103">本主题说明如何将 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理配置为在中意外停止时自动重新启动 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="681de-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically restart if it should stop unexpectedly in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="681de-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="681de-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="681de-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="681de-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="681de-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="681de-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="681de-107">安全性</span><span class="sxs-lookup"><span data-stu-id="681de-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="681de-108">若要将 SQL Server 代理配置为自动重新启动，请使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="681de-108">To configure SQL Server Agent to automatically restart, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="681de-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="681de-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="681de-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="681de-110">Limitations and Restrictions</span></span>  
 <span data-ttu-id="681de-111">“对象资源管理器”仅在您拥有使用权限时才显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理节点。</span><span class="sxs-lookup"><span data-stu-id="681de-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="681de-112">Security</span><span class="sxs-lookup"><span data-stu-id="681de-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="681de-113">权限</span><span class="sxs-lookup"><span data-stu-id="681de-113">Permissions</span></span>  
 <span data-ttu-id="681de-114">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，必须将 **代理配置为使用** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定服务器角色的成员帐户的凭据，才能执行其功能。</span><span class="sxs-lookup"><span data-stu-id="681de-114">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="681de-115">该帐户必须拥有以下 Windows 权限：</span><span class="sxs-lookup"><span data-stu-id="681de-115">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="681de-116">以服务身份登录 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="681de-116">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="681de-117">替换进程级别标记 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="681de-117">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="681de-118">跳过遍历检查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="681de-118">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="681de-119">调整进程的内存配额 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="681de-119">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="681de-120">有关代理服务帐户所需的 Windows 权限的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅为[SQL Server 代理服务选择帐户](select-an-account-for-the-sql-server-agent-service.md)和[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="681de-120">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="681de-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="681de-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-sql-server-agent-to-automatically-restart"></a><span data-ttu-id="681de-122">将 SQL Server 代理配置为自动重新启动</span><span class="sxs-lookup"><span data-stu-id="681de-122">To configure SQL Server Agent to automatically restart</span></span>  
  
1.  <span data-ttu-id="681de-123">在 **“对象资源管理器”** 中，单击加号以展开要将 SQL Server 代理配置为自动重新启动的服务器。</span><span class="sxs-lookup"><span data-stu-id="681de-123">In **Object Explorer**, click the plus sign to expand the server where you want to configure SQL Server Agent to automatically restart.</span></span>  
  
2.  <span data-ttu-id="681de-124">右键单击“SQL Server 代理”\*\*\*\*，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="681de-124">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="681de-125">在 **“常规”** 页上，选中 **“SQL Server 代理意外停止时自动重新启动”**。</span><span class="sxs-lookup"><span data-stu-id="681de-125">On the **General** page, check **Auto restart SQL Server Agent if it stops unexpectedly**.</span></span>  
  
  
