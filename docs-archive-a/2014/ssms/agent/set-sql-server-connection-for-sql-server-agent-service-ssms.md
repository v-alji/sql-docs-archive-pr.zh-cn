---
title: 设置 SQL Server 代理服务的 SQL Server 连接 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
author: stevestein
ms.author: sstein
ms.openlocfilehash: 30f68967d6bdb8b0495cbddb1a5b0bd447cd5168
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591717"
---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a><span data-ttu-id="213e8-102">为 SQL Server 代理服务设置 SQL Server 连接 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="213e8-102">Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)</span></span>
  <span data-ttu-id="213e8-103">本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中设置 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 代理和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]之间的连接。</span><span class="sxs-lookup"><span data-stu-id="213e8-103">This topic describes how to set the connection between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="213e8-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务可以使用 Windows 身份验证连接到 SQL Server 本地实例。</span><span class="sxs-lookup"><span data-stu-id="213e8-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can connect to a local instance of SQL Server by using Windows Authentication.</span></span>  
  
 <span data-ttu-id="213e8-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="213e8-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="213e8-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="213e8-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="213e8-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="213e8-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="213e8-108">安全性</span><span class="sxs-lookup"><span data-stu-id="213e8-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="213e8-109">**若要为 SQL Server 代理设置 SQL Server 连接，请使用：**</span><span class="sxs-lookup"><span data-stu-id="213e8-109">**To set the SQL Server Connection for the SQL Server Agent, using:**</span></span>  
  
     [<span data-ttu-id="213e8-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="213e8-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="213e8-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="213e8-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="213e8-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="213e8-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="213e8-113">“对象资源管理器”仅在您拥有使用权限时才显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理节点。</span><span class="sxs-lookup"><span data-stu-id="213e8-113">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="213e8-114">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]开始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理不支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="213e8-114">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent does not support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="213e8-115">仅在管理早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]时才能使用这种身份验证。</span><span class="sxs-lookup"><span data-stu-id="213e8-115">This option is available only when you administer an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="213e8-116">Security</span><span class="sxs-lookup"><span data-stu-id="213e8-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="213e8-117">权限</span><span class="sxs-lookup"><span data-stu-id="213e8-117">Permissions</span></span>  
 <span data-ttu-id="213e8-118">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，必须将 **代理配置为使用** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定服务器角色的成员帐户的凭据，才能执行其功能。</span><span class="sxs-lookup"><span data-stu-id="213e8-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="213e8-119">该帐户必须拥有以下 Windows 权限：</span><span class="sxs-lookup"><span data-stu-id="213e8-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="213e8-120">以服务身份登录 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="213e8-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="213e8-121">替换进程级别标记 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="213e8-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="213e8-122">跳过遍历检查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="213e8-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="213e8-123">调整进程的内存配额 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="213e8-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="213e8-124">有关代理服务帐户所需的 Windows 权限的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅为[SQL Server 代理服务选择帐户](select-an-account-for-the-sql-server-agent-service.md)和[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="213e8-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="213e8-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="213e8-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-sql-server-connection"></a><span data-ttu-id="213e8-126">设置 SQL Server 连接</span><span class="sxs-lookup"><span data-stu-id="213e8-126">To set the SQL Server connection</span></span>  
  
1.  <span data-ttu-id="213e8-127">在 **“对象资源管理器”** 中，单击加号以展开要使用到其 SQL Server 代理服务的连接进行设置的服务器。</span><span class="sxs-lookup"><span data-stu-id="213e8-127">In **Object Explorer**, click the plus sign to expand the server that you want to set up with a connection to its SQL Server Agent Service.</span></span>  
  
2.  <span data-ttu-id="213e8-128">右键单击“SQL Server 代理”\*\*\*\*，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="213e8-128">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="213e8-129">在“SQL Server 代理属性”\*\*\*\* 对话框的“选择页”\*\*\*\* 下，单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="213e8-129">In the **SQL Server Agent Properties** dialog box, under **Select a page**, click **Connection**.</span></span>  
  
4.  <span data-ttu-id="213e8-130">在“SQL Server 连接”\*\*\*\* 下，选择“使用 Windows 身份验证”\*\*\*\* 以启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理，从而使用  Windows 身份验证连接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="213e8-130">Under **SQL Server connection**, select **Use Windows Authentication** to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> <span data-ttu-id="213e8-131">与 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本数据库的连接需要 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="213e8-131">Connections to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later databases require Windows Authentication.</span></span>  
  
  
