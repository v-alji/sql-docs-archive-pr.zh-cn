---
title: “执行 SQL Server 代理作业”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.executejob.f1
helpviewer_keywords:
- Execute SQL Server Agent Job Task dialog box
ms.assetid: 4ed75956-ebb8-4d8c-9c16-fc0eb00bd3a0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b997d5144b113102ba0ed2d9d1df59b6707acbee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589053"
---
# <a name="execute-sql-server-agent-job-task-maintenance-plan"></a><span data-ttu-id="82336-102">“执行 SQL Server 代理作业”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="82336-102">Execute SQL Server Agent Job Task (Maintenance Plan)</span></span>
  <span data-ttu-id="82336-103">使用 **“‘执行 SQL Server 代理作业’任务”** 对话框可以执行维护计划中的 Microsoft SQL Server 代理作业。</span><span class="sxs-lookup"><span data-stu-id="82336-103">Use the **Execute SQL Server Agent Job Task** dialog to execute Microsoft SQL Server Agent jobs within a maintenance plan.</span></span> <span data-ttu-id="82336-104">如果所选连接上没有 SQL Server 代理作业，此选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="82336-104">This option will not be available if you have no SQL Server Agent jobs on the selected connection.</span></span>  
  
 <span data-ttu-id="82336-105">此任务将使用 **.sp_start_job** 语句。</span><span class="sxs-lookup"><span data-stu-id="82336-105">This task uses the **.sp_start_job** statement.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="82336-106">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="82336-106">UI element list</span></span>  
 <span data-ttu-id="82336-107">**Connection**</span><span class="sxs-lookup"><span data-stu-id="82336-107">**Connection**</span></span>  
 <span data-ttu-id="82336-108">选择执行此任务时使用的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="82336-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="82336-109">**新建**</span><span class="sxs-lookup"><span data-stu-id="82336-109">**New**</span></span>  
 <span data-ttu-id="82336-110">创建一个新的服务器连接，在执行此任务时使用。</span><span class="sxs-lookup"><span data-stu-id="82336-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="82336-111">下面对 **“新建连接”** 对话框进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="82336-111">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="82336-112">**可用的 SQL 代理作业**</span><span class="sxs-lookup"><span data-stu-id="82336-112">**Available SQL Agent jobs**</span></span>  
 <span data-ttu-id="82336-113">选择要执行的作业。</span><span class="sxs-lookup"><span data-stu-id="82336-113">Select the job to execute.</span></span> <span data-ttu-id="82336-114">该网格提供用于标识作业的 **“作业名称”** 和 **“说明”** 。</span><span class="sxs-lookup"><span data-stu-id="82336-114">The grid provides the **Job name** and **Description** to identify the jobs.</span></span>  
  
 <span data-ttu-id="82336-115">**查看 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="82336-115">**View T-SQL**</span></span>  
 <span data-ttu-id="82336-116">根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="82336-116">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82336-117">当受影响的对象很多时，可能需要相当长的时间才可显示。</span><span class="sxs-lookup"><span data-stu-id="82336-117">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="82336-118">“新建连接”对话框</span><span class="sxs-lookup"><span data-stu-id="82336-118">New Connection Dialog Box</span></span>  
 <span data-ttu-id="82336-119">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="82336-119">**Connection name**</span></span>  
 <span data-ttu-id="82336-120">输入新连接的名称。</span><span class="sxs-lookup"><span data-stu-id="82336-120">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="82336-121">**选择或输入服务器名称**</span><span class="sxs-lookup"><span data-stu-id="82336-121">**Select or enter a server name**</span></span>  
 <span data-ttu-id="82336-122">选择执行此任务时所要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="82336-122">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="82336-123">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="82336-123">**Refresh**</span></span>  
 <span data-ttu-id="82336-124">刷新可用服务器的列表。</span><span class="sxs-lookup"><span data-stu-id="82336-124">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="82336-125">**输入登录服务器所需的信息**</span><span class="sxs-lookup"><span data-stu-id="82336-125">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="82336-126">指定如何对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="82336-126">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="82336-127">**使用 Windows 集成安全性**</span><span class="sxs-lookup"><span data-stu-id="82336-127">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="82336-128">使用 Microsoft Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="82336-128">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="82336-129">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="82336-129">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="82336-130">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="82336-130">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="82336-131">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="82336-131">This option is not available.</span></span>  
  
 <span data-ttu-id="82336-132">**用户名**</span><span class="sxs-lookup"><span data-stu-id="82336-132">**User name**</span></span>  
 <span data-ttu-id="82336-133">提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="82336-133">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="82336-134">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="82336-134">This option is not available.</span></span>  
  
 <span data-ttu-id="82336-135">**密码**</span><span class="sxs-lookup"><span data-stu-id="82336-135">**Password**</span></span>  
 <span data-ttu-id="82336-136">提供一个在进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="82336-136">Provide a password to use when authenticating.</span></span> <span data-ttu-id="82336-137">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="82336-137">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82336-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82336-138">See Also</span></span>  
 <span data-ttu-id="82336-139">[sp_add_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="82336-139">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span></span>  
 <span data-ttu-id="82336-140">[创建作业](../../ssms/agent/create-a-job.md) </span><span class="sxs-lookup"><span data-stu-id="82336-140">[Create a Job](../../ssms/agent/create-a-job.md) </span></span>  
 [<span data-ttu-id="82336-141">sp_start_job (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="82336-141">sp_start_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)  
  
  
