---
title: 将目标服务器与主服务器脱离 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b17703fa87f5c0d3e7146a1660ac1ca7c7c1d81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689257"
---
# <a name="defect-a-target-server-from-a-master-server"></a><span data-ttu-id="b6a38-102">将目标服务器从主服务器脱离</span><span class="sxs-lookup"><span data-stu-id="b6a38-102">Defect a Target Server from a Master Server</span></span>
  <span data-ttu-id="b6a38-103">本主题说明如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 SQL Server 管理对象 (SMO) 从 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中的主服务器脱离目标服务器。</span><span class="sxs-lookup"><span data-stu-id="b6a38-103">This topic describes how to defect a target server from a master server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="b6a38-104">从目标服务器运行此过程。</span><span class="sxs-lookup"><span data-stu-id="b6a38-104">Run this procedure from the target server.</span></span>  
  
 <span data-ttu-id="b6a38-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b6a38-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b6a38-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b6a38-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b6a38-107">安全性</span><span class="sxs-lookup"><span data-stu-id="b6a38-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b6a38-108">**若要脱离目标服务器，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b6a38-108">**To defect a target server, using:**</span></span>  
  
     [<span data-ttu-id="b6a38-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6a38-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b6a38-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6a38-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="b6a38-111">SMO</span><span class="sxs-lookup"><span data-stu-id="b6a38-111">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b6a38-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="b6a38-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b6a38-113">Security</span><span class="sxs-lookup"><span data-stu-id="b6a38-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b6a38-114">权限</span><span class="sxs-lookup"><span data-stu-id="b6a38-114">Permissions</span></span>  
 <span data-ttu-id="b6a38-115">若要执行此存储过程，用户必须为 `sysadmin` 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="b6a38-115">To execute this stored procedure, a user must be a member of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b6a38-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6a38-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a><span data-ttu-id="b6a38-117">将目标服务器从主服务器脱离</span><span class="sxs-lookup"><span data-stu-id="b6a38-117">To defect a target server from a master server</span></span>  
  
1.  <span data-ttu-id="b6a38-118">在 **对象资源管理器**中，展开配置为目标服务器的服务器。</span><span class="sxs-lookup"><span data-stu-id="b6a38-118">In **Object Explorer**, expand a server that is configured as a target server.</span></span>  
  
2.  <span data-ttu-id="b6a38-119">右键单击 **“SQL Server 代理”**，指向 **“多服务器管理”**，然后单击 **“脱离”**。</span><span class="sxs-lookup"><span data-stu-id="b6a38-119">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Defect**.</span></span>  
  
3.  <span data-ttu-id="b6a38-120">单击 **“是”** 确认要从主服务器脱离此目标服务器。</span><span class="sxs-lookup"><span data-stu-id="b6a38-120">Click **Yes** to confirm that you want to defect this target server from a master server.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b6a38-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6a38-121">Using Transact-SQL</span></span>  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a><span data-ttu-id="b6a38-122">将目标服务器从主服务器脱离</span><span class="sxs-lookup"><span data-stu-id="b6a38-122">To defect a target server from a master server</span></span>  
  
1.  <span data-ttu-id="b6a38-123">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b6a38-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b6a38-124">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b6a38-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b6a38-125">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b6a38-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
```sql
sp_msx_defect ;  
```  
  
 <span data-ttu-id="b6a38-126">有关详细信息，请参阅[&#40;transact-sql&#41;sp_msx_defect ](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b6a38-126">For more information, see [sp_msx_defect &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="b6a38-127">使用 SQL Server 管理对象 (SMO) </span><span class="sxs-lookup"><span data-stu-id="b6a38-127">Using SQL Server Management Objects (SMO)</span></span>  
 <span data-ttu-id="b6a38-128">使用 `MsxDefect Method`。</span><span class="sxs-lookup"><span data-stu-id="b6a38-128">Use the `MsxDefect Method`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6a38-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6a38-129">See Also</span></span>  
 <span data-ttu-id="b6a38-130">[创建多服务器环境](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="b6a38-130">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="b6a38-131">[企业范围的自动化管理](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="b6a38-131">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 [<span data-ttu-id="b6a38-132">将多台目标服务器从主服务器脱离</span><span class="sxs-lookup"><span data-stu-id="b6a38-132">Defect Multiple Target Servers from a Master Server</span></span>](defect-multiple-target-servers-from-a-master-server.md)  
