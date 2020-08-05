---
title: “重新组织索引”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.defrag.f1
helpviewer_keywords:
- Reorganize Index Task dialog box
ms.assetid: e9cbebbd-f36f-4176-9832-382a46ac946c
author: rothja
ms.author: jroth
ms.openlocfilehash: 0bbb154045b781f8a92dfce9c9d2f6ee2d819c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580710"
---
# <a name="reorganize-index-task-maintenance-plan"></a><span data-ttu-id="06a97-102">“重新组织索引”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="06a97-102">Reorganize Index Task (Maintenance Plan)</span></span>
  <span data-ttu-id="06a97-103">使用“‘重新组织索引’任务”  对话框可以移动索引页，以提高搜索效率。</span><span class="sxs-lookup"><span data-stu-id="06a97-103">Use the **ReorganizeIndex Task** dialog to move index pages into a more efficient search order.</span></span> <span data-ttu-id="06a97-104">此任务将使用 `ALTER INDEX REORGANIZE` 语句和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]数据库。</span><span class="sxs-lookup"><span data-stu-id="06a97-104">This task uses the `ALTER INDEX REORGANIZE` statement with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] databases.</span></span>  
  
## <a name="options"></a><span data-ttu-id="06a97-105">选项</span><span class="sxs-lookup"><span data-stu-id="06a97-105">Options</span></span>  
 <span data-ttu-id="06a97-106">**Connection**</span><span class="sxs-lookup"><span data-stu-id="06a97-106">**Connection**</span></span>  
 <span data-ttu-id="06a97-107">选择执行此任务时使用的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="06a97-107">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="06a97-108">**新建**</span><span class="sxs-lookup"><span data-stu-id="06a97-108">**New**</span></span>  
 <span data-ttu-id="06a97-109">创建一个新的服务器连接，在执行此任务时使用。</span><span class="sxs-lookup"><span data-stu-id="06a97-109">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="06a97-110">下面对 **“新建连接”** 对话框进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="06a97-110">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="06a97-111">**数据库**</span><span class="sxs-lookup"><span data-stu-id="06a97-111">**Databases**</span></span>  
 <span data-ttu-id="06a97-112">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="06a97-112">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="06a97-113">**“所有数据库”**</span><span class="sxs-lookup"><span data-stu-id="06a97-113">**All databases**</span></span>  
  
     <span data-ttu-id="06a97-114">生成的维护计划将对除 tempdb 之外的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="06a97-114">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="06a97-115">**所有系统数据库**</span><span class="sxs-lookup"><span data-stu-id="06a97-115">**All system databases**</span></span>  
  
     <span data-ttu-id="06a97-116">生成的维护计划将对除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tempdb **之外的所有**系统数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="06a97-116">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb**.</span></span> <span data-ttu-id="06a97-117">对用户创建的数据库不运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="06a97-117">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="06a97-118">**所有用户数据库**</span><span class="sxs-lookup"><span data-stu-id="06a97-118">**All user databases**</span></span>  
  
     <span data-ttu-id="06a97-119">生成的维护计划将对用户创建的所有数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="06a97-119">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="06a97-120">但不会对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库运行任何维护任务。</span><span class="sxs-lookup"><span data-stu-id="06a97-120">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="06a97-121">**特定数据库**</span><span class="sxs-lookup"><span data-stu-id="06a97-121">**These specific databases**</span></span>  
  
     <span data-ttu-id="06a97-122">生成的维护计划将只对所选数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="06a97-122">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="06a97-123">如果选择此选项，则必须至少在列表中选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="06a97-123">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="06a97-124">**Object**</span><span class="sxs-lookup"><span data-stu-id="06a97-124">**Object**</span></span>  
 <span data-ttu-id="06a97-125">将“选择”  网格限制为显示表、显示视图或同时显示两者。</span><span class="sxs-lookup"><span data-stu-id="06a97-125">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="06a97-126">**选择**</span><span class="sxs-lookup"><span data-stu-id="06a97-126">**Selection**</span></span>  
 <span data-ttu-id="06a97-127">指定受此任务影响的表或索引。</span><span class="sxs-lookup"><span data-stu-id="06a97-127">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="06a97-128">在 **“对象”** 框中选择 **“表和视图”** 时不可用。</span><span class="sxs-lookup"><span data-stu-id="06a97-128">Not available when **Tables and Views** is selected in the **Object** box.</span></span>  
  
 <span data-ttu-id="06a97-129">**压缩大型对象**</span><span class="sxs-lookup"><span data-stu-id="06a97-129">**Compact large objects**</span></span>  
 <span data-ttu-id="06a97-130">在可能的情况下，释放表和视图的空间。</span><span class="sxs-lookup"><span data-stu-id="06a97-130">Deallocate space for tables and views when possible.</span></span> <span data-ttu-id="06a97-131">此选项使用 `ALTER INDEX LOB_COMPACTION = ON`。</span><span class="sxs-lookup"><span data-stu-id="06a97-131">This option uses `ALTER INDEX LOB_COMPACTION = ON`.</span></span>  
  
 <span data-ttu-id="06a97-132">**查看 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="06a97-132">**View T-SQL**</span></span>  
 <span data-ttu-id="06a97-133">根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="06a97-133">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06a97-134">当受影响的对象很多时，可能需要相当长的时间才可显示。</span><span class="sxs-lookup"><span data-stu-id="06a97-134">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="06a97-135">“新建连接”对话框</span><span class="sxs-lookup"><span data-stu-id="06a97-135">New Connection Dialog Box</span></span>  
 <span data-ttu-id="06a97-136">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="06a97-136">**Connection name**</span></span>  
 <span data-ttu-id="06a97-137">输入新连接的名称。</span><span class="sxs-lookup"><span data-stu-id="06a97-137">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="06a97-138">**选择或输入服务器名称**</span><span class="sxs-lookup"><span data-stu-id="06a97-138">**Select or enter a server name**</span></span>  
 <span data-ttu-id="06a97-139">选择执行此任务时所要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="06a97-139">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="06a97-140">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="06a97-140">**Refresh**</span></span>  
 <span data-ttu-id="06a97-141">刷新可用服务器的列表。</span><span class="sxs-lookup"><span data-stu-id="06a97-141">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="06a97-142">**输入登录服务器所需的信息**</span><span class="sxs-lookup"><span data-stu-id="06a97-142">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="06a97-143">指定如何对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="06a97-143">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="06a97-144">**使用 Windows 集成安全性**</span><span class="sxs-lookup"><span data-stu-id="06a97-144">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="06a97-145">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 身份验证连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="06a97-145">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="06a97-146">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="06a97-146">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="06a97-147">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="06a97-147">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="06a97-148">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="06a97-148">This option is not available.</span></span>  
  
 <span data-ttu-id="06a97-149">**用户名**</span><span class="sxs-lookup"><span data-stu-id="06a97-149">**User name**</span></span>  
 <span data-ttu-id="06a97-150">提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="06a97-150">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="06a97-151">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="06a97-151">This option is not available.</span></span>  
  
 <span data-ttu-id="06a97-152">**密码**</span><span class="sxs-lookup"><span data-stu-id="06a97-152">**Password**</span></span>  
 <span data-ttu-id="06a97-153">提供一个在进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="06a97-153">Provide a password to use when authenticating.</span></span> <span data-ttu-id="06a97-154">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="06a97-154">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a97-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06a97-155">See Also</span></span>  
 <span data-ttu-id="06a97-156">[ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="06a97-156">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 [<span data-ttu-id="06a97-157">DBCC INDEXDEFRAG (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="06a97-157">DBCC INDEXDEFRAG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql)  
  
  
