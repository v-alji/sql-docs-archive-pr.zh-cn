---
title: 删除实用工具控制点（SQL Server 实用工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fe4ebb9de3f7644b4cff5c7dbfb34e50be7e8993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591330"
---
# <a name="remove-a-utility-control-point-sql-server-utility"></a><span data-ttu-id="a015d-102">删除实用工具控制点（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="a015d-102">Remove a Utility Control Point (SQL Server Utility)</span></span>
  <span data-ttu-id="a015d-103">本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中删除 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 实例中的 [!INCLUDE[tsql](../../includes/tsql-md.md)]实用工具控制点 (UCP)。</span><span class="sxs-lookup"><span data-stu-id="a015d-103">This topic describes how to remove a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utility control point (UCP) from the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a015d-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a015d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a015d-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a015d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a015d-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a015d-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a015d-107">安全性</span><span class="sxs-lookup"><span data-stu-id="a015d-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a015d-108">**若要删除实用工具控制点，可使用：**</span><span class="sxs-lookup"><span data-stu-id="a015d-108">**To remove a Utility Control Point, using:**</span></span>  
  
     [<span data-ttu-id="a015d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a015d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a015d-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="a015d-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a015d-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a015d-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="a015d-112">在使用此过程从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中删除该 UCP 之前，请注意以下要求。</span><span class="sxs-lookup"><span data-stu-id="a015d-112">Before you use this procedure to remove the UCP from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, note the following requirements.</span></span> <span data-ttu-id="a015d-113">存储过程将在删除过程中运行先决条件检查。</span><span class="sxs-lookup"><span data-stu-id="a015d-113">The stored procedure will run prerequisite checks as part of the operation.</span></span>  
  
-   <span data-ttu-id="a015d-114">在运行此过程前，必须从该 UCP 中删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有托管实例。</span><span class="sxs-lookup"><span data-stu-id="a015d-114">Before you run this procedure, all managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be removed from the UCP.</span></span> <span data-ttu-id="a015d-115">请注意，该 UCP 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的托管实例。</span><span class="sxs-lookup"><span data-stu-id="a015d-115">Note that the UCP is a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a015d-116">有关详细信息，请参阅 [从 SQL Server 实用工具中删除 SQL Server 的实例](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="a015d-116">From more information, see [Remove an Instance of SQL Server from the SQL Server Utility](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).</span></span>  
  
-   <span data-ttu-id="a015d-117">该过程必须在作为 UCP 的计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="a015d-117">This procedure must be run on a computer that is a UCP.</span></span>  
  
-   <span data-ttu-id="a015d-118">如果删除了 UCP 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例具有非实用工具数据收集组，则该过程将不删除 UMDW 数据库 (sysutility_mdw)。</span><span class="sxs-lookup"><span data-stu-id="a015d-118">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the UCP was removed has a non-Utility data collection set, the UMDW database (sysutility_mdw) will not be dropped by the procedure.</span></span> <span data-ttu-id="a015d-119">在此情况下，必须首先手动删除 UMDW 数据库 (sysutility_mdw)，然后才能再次创建 UCP。</span><span class="sxs-lookup"><span data-stu-id="a015d-119">If this is the case, the UMDW database (sysutility_mdw) must be dropped manually before the UCP can be created again.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a015d-120">Security</span><span class="sxs-lookup"><span data-stu-id="a015d-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a015d-121">权限</span><span class="sxs-lookup"><span data-stu-id="a015d-121">Permissions</span></span>  
 <span data-ttu-id="a015d-122">该过程必须由具有 `sysadmin` 权限的用户运行；创建 UCP 要求同样的权限。</span><span class="sxs-lookup"><span data-stu-id="a015d-122">This procedure must be run by a user with `sysadmin` permissions; the same permissions required to create a UCP.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a015d-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a015d-123">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-a-utility-control-point"></a><span data-ttu-id="a015d-124">删除实用工具控制点</span><span class="sxs-lookup"><span data-stu-id="a015d-124">To remove a Utility Control Point</span></span>  
  
1.  <span data-ttu-id="a015d-125">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a015d-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a015d-126">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a015d-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a015d-127">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a015d-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## <a name="see-also"></a><span data-ttu-id="a015d-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a015d-128">See Also</span></span>  
 <span data-ttu-id="a015d-129">[SQL Server 实用工具的功能和任务](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="a015d-129">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 <span data-ttu-id="a015d-130">[使用实用工具资源管理器管理 SQL Server 实用工具](use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="a015d-130">[Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="a015d-131">SQL Server 实用工具故障排除</span><span class="sxs-lookup"><span data-stu-id="a015d-131">Troubleshoot the SQL Server Utility</span></span>](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
