---
title: “检查数据库完整性”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.integrity.f1
- sql12.swb.maint.integrity.f1
helpviewer_keywords:
- Check Database Integrity Task dialog box
ms.assetid: 3534494a-5dfe-4738-b49a-e7fabd731c47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f786755a3b7ed5d991b4cf0e32c067e355c111ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589060"
---
# <a name="check-database-integrity-task-maintenance-plan"></a><span data-ttu-id="19591-102">“检查数据库完整性”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="19591-102">Check Database Integrity Task (Maintenance Plan)</span></span>
  <span data-ttu-id="19591-103">通过运行 `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，使用“检查数据库完整性任务”对话框可以检查数据库中的用户和系统表以及索引的分配和结构完整性。</span><span class="sxs-lookup"><span data-stu-id="19591-103">Use the **Check Database Integrity Task** dialog to check the allocation and structural integrity of user and system tables, and indexes in the database, by running the `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="19591-104">运行 `DBCC` 确保数据库中的任何完整性问题均能得到报告，以便系统管理员或数据库所有者在以后加以解决。</span><span class="sxs-lookup"><span data-stu-id="19591-104">Running `DBCC` ensures that any integrity problems with the database are reported, thereby allowing them to be addressed later by a system administrator or database owner.</span></span>  
  
## <a name="options"></a><span data-ttu-id="19591-105">选项</span><span class="sxs-lookup"><span data-stu-id="19591-105">Options</span></span>  
 <span data-ttu-id="19591-106">**Connection**</span><span class="sxs-lookup"><span data-stu-id="19591-106">**Connection**</span></span>  
 <span data-ttu-id="19591-107">选择执行此任务时使用的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="19591-107">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="19591-108">**新建**</span><span class="sxs-lookup"><span data-stu-id="19591-108">**New**</span></span>  
 <span data-ttu-id="19591-109">创建一个新的服务器连接，在执行此任务时使用。</span><span class="sxs-lookup"><span data-stu-id="19591-109">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="19591-110">下面对 **“新建连接”** 对话框进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="19591-110">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="19591-111">**数据库**</span><span class="sxs-lookup"><span data-stu-id="19591-111">**Databases**</span></span>  
 <span data-ttu-id="19591-112">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="19591-112">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="19591-113">**“所有数据库”**</span><span class="sxs-lookup"><span data-stu-id="19591-113">**All databases**</span></span>  
  
     <span data-ttu-id="19591-114">生成的维护计划将对除 tempdb 之外的所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="19591-114">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except **tempdb**.</span></span>  
  
-   <span data-ttu-id="19591-115">**所有系统数据库**</span><span class="sxs-lookup"><span data-stu-id="19591-115">**All system databases**</span></span>  
  
     <span data-ttu-id="19591-116">生成的维护计划将对除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tempdb **之外的所有**系统数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="19591-116">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb**.</span></span> <span data-ttu-id="19591-117">对用户创建的数据库不运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="19591-117">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="19591-118">**所有用户数据库**</span><span class="sxs-lookup"><span data-stu-id="19591-118">**All user databases**</span></span>  
  
     <span data-ttu-id="19591-119">生成的维护计划将对用户创建的所有数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="19591-119">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="19591-120">但不会对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库运行任何维护任务。</span><span class="sxs-lookup"><span data-stu-id="19591-120">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="19591-121">**特定数据库**</span><span class="sxs-lookup"><span data-stu-id="19591-121">**These specific databases**</span></span>  
  
     <span data-ttu-id="19591-122">生成的维护计划将只对所选数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="19591-122">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="19591-123">如果选择此选项，则必须至少在列表中选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="19591-123">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="19591-124">只能对兼容级别被设置为 80 或更高的数据库运行维护计划。</span><span class="sxs-lookup"><span data-stu-id="19591-124">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="19591-125">不显示兼容级别设置为 70 或更低的数据库。</span><span class="sxs-lookup"><span data-stu-id="19591-125">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="19591-126">**包括索引**</span><span class="sxs-lookup"><span data-stu-id="19591-126">**Include indexes**</span></span>  
 <span data-ttu-id="19591-127">检查所有索引页以及表数据页的完整性。</span><span class="sxs-lookup"><span data-stu-id="19591-127">Check the integrity of all the index pages as well as the table data pages.</span></span>  
  
 <span data-ttu-id="19591-128">**查看 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="19591-128">**View T-SQL**</span></span>  
 <span data-ttu-id="19591-129">根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="19591-129">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19591-130">当受影响的对象很多时，可能需要相当长的时间才可显示。</span><span class="sxs-lookup"><span data-stu-id="19591-130">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="19591-131">“新建连接”对话框</span><span class="sxs-lookup"><span data-stu-id="19591-131">New Connection Dialog Box</span></span>  
 <span data-ttu-id="19591-132">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="19591-132">**Connection name**</span></span>  
 <span data-ttu-id="19591-133">输入新连接的名称。</span><span class="sxs-lookup"><span data-stu-id="19591-133">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="19591-134">**选择或输入服务器名称**</span><span class="sxs-lookup"><span data-stu-id="19591-134">**Select or enter a server name**</span></span>  
 <span data-ttu-id="19591-135">选择执行此任务时所要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="19591-135">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="19591-136">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="19591-136">**Refresh**</span></span>  
 <span data-ttu-id="19591-137">刷新可用服务器的列表。</span><span class="sxs-lookup"><span data-stu-id="19591-137">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="19591-138">**输入登录服务器所需的信息**</span><span class="sxs-lookup"><span data-stu-id="19591-138">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="19591-139">指定如何对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="19591-139">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="19591-140">**使用 Windows 集成安全性**</span><span class="sxs-lookup"><span data-stu-id="19591-140">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="19591-141">使用 Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="19591-141">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="19591-142">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="19591-142">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="19591-143">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="19591-143">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="19591-144">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="19591-144">This option is not available.</span></span>  
  
 <span data-ttu-id="19591-145">**用户名**</span><span class="sxs-lookup"><span data-stu-id="19591-145">**User name**</span></span>  
 <span data-ttu-id="19591-146">提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="19591-146">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="19591-147">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="19591-147">This option is not available.</span></span>  
  
 <span data-ttu-id="19591-148">**密码**</span><span class="sxs-lookup"><span data-stu-id="19591-148">**Password**</span></span>  
 <span data-ttu-id="19591-149">提供一个在进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="19591-149">Provide a password to use when authenticating.</span></span> <span data-ttu-id="19591-150">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="19591-150">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19591-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19591-151">See Also</span></span>  
 [<span data-ttu-id="19591-152">DBCC CHECKDB (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="19591-152">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
