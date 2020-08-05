---
title: 修改 SQL Server 代理程序代理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], modifying
- modifying SQL Server Agent proxy
ms.assetid: 6e1dfbaa-8089-4813-940c-d5a2e13d8552
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2f86793a8ddcc6fe8f981d6b367d2178c5a794ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580534"
---
# <a name="modify-a-sql-server-agent-proxy"></a><span data-ttu-id="1acb4-102">Modify a SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="1acb4-102">Modify a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="1acb4-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中修改代理的代理 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1acb4-103">This topic describes how to modify a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1acb4-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="1acb4-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1acb4-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="1acb4-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1acb4-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="1acb4-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1acb4-107">安全性</span><span class="sxs-lookup"><span data-stu-id="1acb4-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1acb4-108">**若要修改 SQL Server 代理的代理帐户，请使用：**</span><span class="sxs-lookup"><span data-stu-id="1acb4-108">**To modify a SQL Server Agent proxy, using:**</span></span>  
  
     [<span data-ttu-id="1acb4-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1acb4-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1acb4-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1acb4-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1acb4-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="1acb4-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1acb4-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="1acb4-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1acb4-113">代理的代理帐户使用凭据存储 Windows 用户帐户的相关信息。</span><span class="sxs-lookup"><span data-stu-id="1acb4-113">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="1acb4-114">凭据中指定的用户必须对正在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机具有“以批处理作业登录”权限。</span><span class="sxs-lookup"><span data-stu-id="1acb4-114">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1acb4-115">代理检查代理帐户的子系统访问权限，并在每次运行作业步骤时向代理帐户授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="1acb4-115">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="1acb4-116">如果代理对子系统不再具有访问权限，则作业步骤将失败。</span><span class="sxs-lookup"><span data-stu-id="1acb4-116">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="1acb4-117">否则，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将模拟代理帐户中指定的用户并运行作业步骤。</span><span class="sxs-lookup"><span data-stu-id="1acb4-117">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="1acb4-118">如果用户的登录帐户具有访问代理帐户的权限，或者用户属于具有访问代理帐户的权限的任何角色，则用户可以在作业步骤中使用代理帐户。</span><span class="sxs-lookup"><span data-stu-id="1acb4-118">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1acb4-119">Security</span><span class="sxs-lookup"><span data-stu-id="1acb4-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1acb4-120">权限</span><span class="sxs-lookup"><span data-stu-id="1acb4-120">Permissions</span></span>  
 <span data-ttu-id="1acb4-121">只有 **sysadmin** 固定服务器角色的成员才能创建、修改或删除代理帐户。</span><span class="sxs-lookup"><span data-stu-id="1acb4-121">Only members of the **sysadmin** fixed server role can create, modify, or delete proxy accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1acb4-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1acb4-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-ssnoversion-agent-proxy"></a><span data-ttu-id="1acb4-123">修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的代理帐户</span><span class="sxs-lookup"><span data-stu-id="1acb4-123">To modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy</span></span>  
  
1.  <span data-ttu-id="1acb4-124">在 **“对象资源管理器”** 中，单击加号以展开包含要修改的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的代理帐户的服务器。</span><span class="sxs-lookup"><span data-stu-id="1acb4-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account that you want to modify.</span></span>  
  
2.  <span data-ttu-id="1acb4-125">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="1acb4-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="1acb4-126">单击加号以便展开 **“代理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="1acb4-126">Click the plus sign to expand the **Proxies** folder.</span></span>  
  
4.  <span data-ttu-id="1acb4-127">单击加号以展开代理的子系统节点（例如，“ActiveX 脚本”\*\*\*\*）。</span><span class="sxs-lookup"><span data-stu-id="1acb4-127">Click the plus sign to expand the subsystem node for the proxy (for example, **ActiveX Script**).</span></span>  
  
5.  <span data-ttu-id="1acb4-128">右键单击要修改属性的代理帐户，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1acb4-128">Right-click the proxy account you want to modify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="1acb4-129">在“proxy_name 代理帐户属性”__\*\*\*\* 对话框中，根据需要更改代理帐户。</span><span class="sxs-lookup"><span data-stu-id="1acb4-129">In the _proxy_name_**Proxy Account Properties** dialog box, make changes to the proxy account as necessary.</span></span> <span data-ttu-id="1acb4-130">有关此对话框中的选项的详细信息，请参阅 [创建 SQL Server 代理的代理](create-a-sql-server-agent-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="1acb4-130">For more information on the options in this dialog box, see [Create a SQL Server Agent Proxy](create-a-sql-server-agent-proxy.md).</span></span>  
  
7.  <span data-ttu-id="1acb4-131">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1acb4-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1acb4-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1acb4-132">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-ssnoversion-agent-proxy"></a><span data-ttu-id="1acb4-133">修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的代理帐户</span><span class="sxs-lookup"><span data-stu-id="1acb4-133">To modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy</span></span>  
  
1.  <span data-ttu-id="1acb4-134">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="1acb4-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1acb4-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="1acb4-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1acb4-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="1acb4-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Disables the proxy named 'Catalog application proxy'.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 0;  
    GO  
    ```  
  
 <span data-ttu-id="1acb4-137">有关详细信息，请参阅[&#40;transact-sql&#41;sp_update_proxy ](/sql/relational-databases/system-stored-procedures/sp-update-proxy-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1acb4-137">For more information, see [sp_update_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-proxy-transact-sql).</span></span>  
  
  
