---
title: 配置 SQL Server 代理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
author: stevestein
ms.author: sstein
ms.openlocfilehash: 81c78faf733fac5ffb9a6e74dbf03f8caaff03d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586062"
---
# <a name="configure-sql-server-agent"></a><span data-ttu-id="3dcdf-102">Configure SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="3dcdf-102">Configure SQL Server Agent</span></span>
  <span data-ttu-id="3dcdf-103">本主题说明如何在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的过程中为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理指定一些配置选项。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-103">This topic describes how to specify some configuration options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent during installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3dcdf-104">只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]管理对象 (SMO) 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理存储过程可以使用所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理配置选项。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-104">The full set of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent configuration options is only available within [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO), or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stored procedures.</span></span>  
  
 <span data-ttu-id="3dcdf-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3dcdf-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3dcdf-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3dcdf-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3dcdf-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3dcdf-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3dcdf-108">安全性</span><span class="sxs-lookup"><span data-stu-id="3dcdf-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="3dcdf-109">配置 SQL Server 代理</span><span class="sxs-lookup"><span data-stu-id="3dcdf-109">To configure SQL Server Agent</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3dcdf-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="3dcdf-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3dcdf-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3dcdf-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3dcdf-112">在 **的“对象资源管理器”中，单击** “SQL Server 代理” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 以管理作业、操作员、警报和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-112">Click **SQL Server Agent** in Object Explorer of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to administer jobs, operators, alerts, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span> <span data-ttu-id="3dcdf-113">但是，对象资源管理器仅在您拥有使用权限时才显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理节点。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-113">However, Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="3dcdf-114">对于故障转移群集实例上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务，不应启用自动重新启动。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-114">Auto-restart should not be enabled for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on failover cluster instances.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3dcdf-115">Security</span><span class="sxs-lookup"><span data-stu-id="3dcdf-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3dcdf-116">权限</span><span class="sxs-lookup"><span data-stu-id="3dcdf-116">Permissions</span></span>  
 <span data-ttu-id="3dcdf-117">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，必须将 **代理配置为使用** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定服务器角色的成员帐户的凭据，才能执行其功能。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-117">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3dcdf-118">该帐户必须拥有以下 Windows 权限：</span><span class="sxs-lookup"><span data-stu-id="3dcdf-118">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="3dcdf-119">以服务身份登录 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="3dcdf-119">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="3dcdf-120">替换进程级别标记 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="3dcdf-120">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="3dcdf-121">跳过遍历检查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="3dcdf-121">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="3dcdf-122">调整进程的内存配额 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="3dcdf-122">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="3dcdf-123">有关代理服务帐户所需的 Windows 权限的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅为[SQL Server 代理服务选择帐户](select-an-account-for-the-sql-server-agent-service.md)和[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-123">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3dcdf-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3dcdf-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-sql-server-agent"></a><span data-ttu-id="3dcdf-125">配置 SQL Server 代理</span><span class="sxs-lookup"><span data-stu-id="3dcdf-125">To configure SQL Server Agent</span></span>  
  
1.  <span data-ttu-id="3dcdf-126">单击 **“开始”** 按钮，然后在 **“开始”**  菜单上，单击 **“控制面板”**。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-126">Click the **Start** button, and then, on the **Start**  menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="3dcdf-127">在“控制面板”中，依次单击 **“系统和安全”**、 **“管理工具”**、 **“本地安全策略”**。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-127">In Control Panel, click **System and Security**, click **Administrative Tools**, and then select **Local Security Policy**.</span></span>  
  
3.  <span data-ttu-id="3dcdf-128">在“本地安全策略”中，单击尖括号以展开 **“本地策略”** 文件夹，然后单击 **“用户权限指派”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-128">In Local Security Policy, click the chevron to expand the **Local Policies** folder, and then click the **User Rights Assignment** folder.</span></span>  
  
4.  <span data-ttu-id="3dcdf-129">右键单击要配置用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的权限，并选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-129">Right-click a permission that you want to configure for use with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="3dcdf-130">在权限的属性对话框中，验证列出了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理运行的帐户。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-130">In the permission's properties dialog box, verify that the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs is listed.</span></span> <span data-ttu-id="3dcdf-131">如果没有列出，请单击 **“添加用户或组”**，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] “选择用户、计算机、服务帐户或组” **对话框中输入运行** 代理的帐户，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-131">If not, click **Add User or Group**, enter the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs in the **Select Users, Computers, Service Accounts, or Groups** dialog box, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="3dcdf-132">为要添加到使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理运行的每个权限重复此操作。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-132">Repeat for each permission that you want to add to run with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="3dcdf-133">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3dcdf-133">When finished, click **OK**.</span></span>  
  
  
