---
title: 为 SQL Server 代理服务设置 SQL Server 别名 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], creating
- SQL Server Agent, aliases
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b178d91a47d907b182ef7962b98c7f22d4454094
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577812"
---
# <a name="set-a-sql-server-alias-for-the-sql-server-agent-service-sql-server-management-studio"></a><span data-ttu-id="84386-102">Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="84386-102">Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)</span></span>
  <span data-ttu-id="84386-103">本主题介绍如何 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 通过使用设置用于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 连接到的代理的别名 [!INCLUDE[ssDE](../includes/ssde-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="84386-103">This topic describes how to set a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] alias for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent to use to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="84386-104">默认情况下， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理服务将通过命名管道，使用无需额外客户端配置的动态服务器名称连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="84386-104">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] over named pipes by using dynamic server names that require no additional client configuration.</span></span> <span data-ttu-id="84386-105">如果当前使用的不是默认网络传输或连接的是侦听备用命名管道的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，则需要配置服务器连接别名。</span><span class="sxs-lookup"><span data-stu-id="84386-105">You need to configure a server connection alias only if you are not using the default network transport or if you are connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that listens on an alternate named pipe.</span></span>  
  
 <span data-ttu-id="84386-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="84386-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="84386-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="84386-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="84386-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="84386-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="84386-109">安全性</span><span class="sxs-lookup"><span data-stu-id="84386-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="84386-110">使用 SQL Server Management Studio 为 SQL Server 代理服务设置 SQL Server 别名</span><span class="sxs-lookup"><span data-stu-id="84386-110">To set a SQL Server Alias for the SQL Server Agent Service using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="84386-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="84386-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="84386-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="84386-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="84386-113">必须选择引用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]本地实例的别名，代理才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="84386-113">Agent will not work correctly unless you select an alias that refers to the local instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="84386-114">“对象资源管理器”仅在您拥有使用权限时才显示 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理节点。</span><span class="sxs-lookup"><span data-stu-id="84386-114">Object Explorer only displays the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="84386-115">Security</span><span class="sxs-lookup"><span data-stu-id="84386-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="84386-116">权限</span><span class="sxs-lookup"><span data-stu-id="84386-116">Permissions</span></span>  
 <span data-ttu-id="84386-117">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中，必须将 **代理配置为使用** sysadmin [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]固定服务器角色的成员帐户的凭据，才能执行其功能。</span><span class="sxs-lookup"><span data-stu-id="84386-117">To perform its functions, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="84386-118">该帐户必须拥有以下 Windows 权限：</span><span class="sxs-lookup"><span data-stu-id="84386-118">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="84386-119">以服务身份登录 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="84386-119">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="84386-120">替换进程级别标记 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="84386-120">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="84386-121">跳过遍历检查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="84386-121">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="84386-122">调整进程的内存配额 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="84386-122">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="84386-123">有关代理服务帐户所需的 Windows 权限的详细信息 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅为[SQL Server 代理服务选择帐户](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md)和[配置 Windows 服务帐户和权限](configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="84386-123">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="84386-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="84386-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-a-sql-server-alias-for-the-sql-server-agent-service"></a><span data-ttu-id="84386-125">为 SQL Server 代理服务设置 SQL Server 别名</span><span class="sxs-lookup"><span data-stu-id="84386-125">To set a SQL Server Alias for the SQL Server Agent Service</span></span>  
  
1.  <span data-ttu-id="84386-126">在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 实例，再展开该实例。</span><span class="sxs-lookup"><span data-stu-id="84386-126">In the **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="84386-127">右键单击“SQL Server 代理”\*\*\*\*，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="84386-127">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="84386-128">在“SQL Server 代理属性 server_name”\*\*\*\*__ 对话框的“选择页”\*\*\*\* 下，选择“连接”\*\*\*\*，然后</span><span class="sxs-lookup"><span data-stu-id="84386-128">In the **SQL Server Agent Properties**_server_name_ dialog box, under **Select a page**, select **Connection**, and</span></span>  
  
4.  <span data-ttu-id="84386-129">在 **“本地主机服务器别名”** 框中，键入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理应连接到的服务器别名的类型。</span><span class="sxs-lookup"><span data-stu-id="84386-129">In the **Alias local host server** box, type the alias of the server to which [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should connect.</span></span>  
  
5.  <span data-ttu-id="84386-130">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="84386-130">Click **OK**.</span></span>  
  
  
