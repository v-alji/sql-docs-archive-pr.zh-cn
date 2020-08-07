---
title: 删除 SQL Server 代理程序代理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting SQL Server Agent proxies
- proxies [SQL Server Agent], deleting
- removing SQL Server Agent proxies
ms.assetid: 9248841d-7294-47d4-94f3-b34a0521fabc
author: stevestein
ms.author: sstein
ms.openlocfilehash: a672c6392e2ffed3ca2a7ed655b806d9d093b10c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588809"
---
# <a name="delete-a-sql-server-agent-proxy"></a><span data-ttu-id="042e6-102">Delete a SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="042e6-102">Delete a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="042e6-103">本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中删除 [!INCLUDE[tsql](../../includes/tsql-md.md)]代理的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="042e6-103">This topic describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="042e6-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="042e6-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="042e6-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="042e6-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="042e6-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="042e6-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="042e6-107">安全性</span><span class="sxs-lookup"><span data-stu-id="042e6-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="042e6-108">**若要删除 SQL Server 代理的代理帐户，可使用：**</span><span class="sxs-lookup"><span data-stu-id="042e6-108">**To delete a SQL Server Agent proxy account, using:**</span></span>  
  
     [<span data-ttu-id="042e6-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="042e6-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="042e6-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="042e6-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="042e6-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="042e6-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="042e6-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="042e6-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="042e6-113">删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的代理帐户时，请确保该代理未引用任何活动的作业步骤。</span><span class="sxs-lookup"><span data-stu-id="042e6-113">When you delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account, make sure the proxy does not reference any active job steps.</span></span> <span data-ttu-id="042e6-114">若要检查是否有引用该代理的作业步骤，请右键单击该代理，选择“属性”\*\*\*\*，然后在“proxy_name 代理帐户属性”__\*\*\*\* 对话框中选择“引用”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="042e6-114">To check for any job steps that reference the proxy, right-click the proxy, select **Properties**, and then, in the _proxy_name_**Proxy Account Properties** dialog box, select the **References** page.</span></span> <span data-ttu-id="042e6-115">如果删除某个代理，在 **“删除对象”** 对话框中会出现一个用于重新分配使用该代理的所有作业步骤的选项。</span><span class="sxs-lookup"><span data-stu-id="042e6-115">If you delete a proxy, you are given the option to reassign all job steps that use that proxy in the **Delete Object** dialog box.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="042e6-116">代理的代理帐户使用凭据存储 Windows 用户帐户的相关信息。</span><span class="sxs-lookup"><span data-stu-id="042e6-116">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="042e6-117">凭据中指定的用户必须对正在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机具有“以批处理作业登录”权限。</span><span class="sxs-lookup"><span data-stu-id="042e6-117">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="042e6-118">代理检查代理帐户的子系统访问权限，并在每次运行作业步骤时向代理帐户授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="042e6-118">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="042e6-119">如果代理对子系统不再具有访问权限，则作业步骤将失败。</span><span class="sxs-lookup"><span data-stu-id="042e6-119">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="042e6-120">否则，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将模拟代理帐户中指定的用户并运行作业步骤。</span><span class="sxs-lookup"><span data-stu-id="042e6-120">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="042e6-121">如果用户的登录帐户具有访问代理帐户的权限，或者用户属于具有访问代理帐户的权限的任何角色，则用户可以在作业步骤中使用代理帐户。</span><span class="sxs-lookup"><span data-stu-id="042e6-121">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="042e6-122">Security</span><span class="sxs-lookup"><span data-stu-id="042e6-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="042e6-123">权限</span><span class="sxs-lookup"><span data-stu-id="042e6-123">Permissions</span></span>  
 <span data-ttu-id="042e6-124">只有 **sysadmin** 固定服务器角色的成员才能创建、修改或删除代理帐户。</span><span class="sxs-lookup"><span data-stu-id="042e6-124">Only members of the **sysadmin** fixed server role can create, modify, or delete proxy accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="042e6-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="042e6-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a><span data-ttu-id="042e6-126">删除 SQL Server 代理的代理帐户</span><span class="sxs-lookup"><span data-stu-id="042e6-126">To delete a SQL Server Agent proxy account</span></span>  
  
1.  <span data-ttu-id="042e6-127">在 **“对象资源管理器”** 中，单击加号以展开包含要删除的代理帐户的服务器。</span><span class="sxs-lookup"><span data-stu-id="042e6-127">In **Object Explorer**, click the plus sign to expand a server that contains the proxy account that you want to delete.</span></span>  
  
2.  <span data-ttu-id="042e6-128">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="042e6-128">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="042e6-129">单击加号以便展开 **“代理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="042e6-129">Click the plus sign to expand the **Proxies** folder.</span></span>  
  
4.  <span data-ttu-id="042e6-130">单击加号以展开包含要删除的代理帐户的子系统（例如，“ActiveX 脚本”\*\*\*\*）。</span><span class="sxs-lookup"><span data-stu-id="042e6-130">Click the plus sign to expand the subsystem that contains the proxy account you want to delete (for example, **ActiveX Script)**.</span></span>  
  
5.  <span data-ttu-id="042e6-131">右键单击要删除的代理帐户，然后选择“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="042e6-131">Right-click the proxy account that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="042e6-132">在 **“删除对象”** 对话框中，确认选择了正确的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="042e6-132">In the **Delete Object** dialog box, confirm that the correct proxy account is selected.</span></span> <span data-ttu-id="042e6-133">选中 **“重新分配给”** 复选框以向其他帐户重新分配引用此代理帐户的作业步骤。</span><span class="sxs-lookup"><span data-stu-id="042e6-133">Check the **Reassign to** check box to reassign the job steps that reference this proxy account to another account.</span></span>  
  
7.  <span data-ttu-id="042e6-134">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="042e6-134">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="042e6-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="042e6-135">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a><span data-ttu-id="042e6-136">删除 SQL Server 代理的代理帐户</span><span class="sxs-lookup"><span data-stu-id="042e6-136">To delete a SQL Server Agent proxy account</span></span>  
  
1.  <span data-ttu-id="042e6-137">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="042e6-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="042e6-138">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="042e6-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="042e6-139">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="042e6-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes the proxy "Catalog application proxy"  
    USE msdb ;  
    GO  
    EXEC dbo.sp_delete_proxy  
        @proxy_name = N'Catalog application proxy' ;  
    GO  
    ```  
  
 <span data-ttu-id="042e6-140">有关详细信息，请参阅[&#40;transact-sql&#41;sp_delete_proxy ](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="042e6-140">For more information, see [sp_delete_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql).</span></span>  
  
  
