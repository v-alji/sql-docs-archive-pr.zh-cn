---
title: “收缩数据库”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.shrink.f1
- Shrink Database Task
- Shrink Database(s) Task
helpviewer_keywords:
- Shrink Database Task dialog box
ms.assetid: a9874cac-cded-4145-9c38-8aafd267dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b8ee6060a4ee6ca3272434cf3d9115638a675e62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689356"
---
# <a name="shrink-database-task-maintenance-plan"></a><span data-ttu-id="064de-102">“收缩数据库”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="064de-102">Shrink Database Task (Maintenance Plan)</span></span>
  <span data-ttu-id="064de-103">使用 **“‘收缩数据库’任务”** 对话框可以创建一个任务，尝试减小所选数据库的大小。</span><span class="sxs-lookup"><span data-stu-id="064de-103">Use the **Shrink Database Task** dialog to create a task that attempts to reduce the size of the selected databases.</span></span> <span data-ttu-id="064de-104">使用下面的选项可以确定数据库收缩后在数据库中保留的未使用空间量（该百分比越大，数据库可收缩的量越小）。</span><span class="sxs-lookup"><span data-stu-id="064de-104">Use the options below to determine the amount of unused space to remain in the database after the database is shrunk (the larger the percentage, the less the database can shrink).</span></span> <span data-ttu-id="064de-105">该数值取决于数据库中实际数据的百分比。</span><span class="sxs-lookup"><span data-stu-id="064de-105">The value is based on the percentage of the actual data in the database.</span></span> <span data-ttu-id="064de-106">例如，某个 100 MB 数据库包含 60 MB 的数据和 40 MB 的可用空间，当可用空间百分比为 50% 时，则将保留 60 MB 的数据和 30 MB 的可用空间（因为 60 MB 的 50% 是 30 MB）。</span><span class="sxs-lookup"><span data-stu-id="064de-106">For example, a 100-MB database containing 60 MB of data and 40 MB of free space, with a free space percentage of 50 percent, would result in 60 MB of data and 30 MB of free space (because 50 percent of 60 MB is 30 MB).</span></span> <span data-ttu-id="064de-107">只会去除数据库中的多余空间。</span><span class="sxs-lookup"><span data-stu-id="064de-107">Only excess space in the database is eliminated.</span></span> <span data-ttu-id="064de-108">有效值为 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="064de-108">Valid values are from 0 through 100.</span></span>  
  
 <span data-ttu-id="064de-109">收缩数据文件通过将数据页从文件末尾移动到更靠近文件开头的未占用的空间来恢复空间。</span><span class="sxs-lookup"><span data-stu-id="064de-109">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="064de-110">在文件末尾创建足够的可用空间后，可以取消对文件末尾的数据页的分配并将它们返回给文件系统。</span><span class="sxs-lookup"><span data-stu-id="064de-110">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="064de-111">被移动用来收缩文件的数据可以分布到文件的任何可用位置。</span><span class="sxs-lookup"><span data-stu-id="064de-111">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="064de-112">这将导致索引碎片并使搜索索引范围的查询变慢。</span><span class="sxs-lookup"><span data-stu-id="064de-112">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="064de-113">若要消除碎片，请考虑在收缩后重新生成文件的索引。</span><span class="sxs-lookup"><span data-stu-id="064de-113">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
 <span data-ttu-id="064de-114">此任务执行 DBCC SHRINKDATABASE 语句。</span><span class="sxs-lookup"><span data-stu-id="064de-114">This task executes the DBCC SHRINKDATABASE statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="064de-115">选项</span><span class="sxs-lookup"><span data-stu-id="064de-115">Options</span></span>  
 <span data-ttu-id="064de-116">**Connection**</span><span class="sxs-lookup"><span data-stu-id="064de-116">**Connection**</span></span>  
 <span data-ttu-id="064de-117">选择执行此任务时使用的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="064de-117">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="064de-118">**新建**</span><span class="sxs-lookup"><span data-stu-id="064de-118">**New**</span></span>  
 <span data-ttu-id="064de-119">创建一个新的服务器连接，在执行此任务时使用。</span><span class="sxs-lookup"><span data-stu-id="064de-119">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="064de-120">下面对 **“新建连接”** 对话框进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="064de-120">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="064de-121">**数据库**</span><span class="sxs-lookup"><span data-stu-id="064de-121">**Databases**</span></span>  
 <span data-ttu-id="064de-122">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="064de-122">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="064de-123">**“所有数据库”**</span><span class="sxs-lookup"><span data-stu-id="064de-123">**All databases**</span></span>  
  
     <span data-ttu-id="064de-124">生成的维护计划将对除 tempdb 之外的所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="064de-124">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="064de-125">**所有系统数据库**</span><span class="sxs-lookup"><span data-stu-id="064de-125">**All system databases**</span></span>  
  
     <span data-ttu-id="064de-126">生成的维护计划将对除 tempdb 之外的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="064de-126">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="064de-127">对用户创建的数据库不运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="064de-127">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="064de-128">**所有用户数据库**</span><span class="sxs-lookup"><span data-stu-id="064de-128">**All user databases**</span></span>  
  
     <span data-ttu-id="064de-129">生成的维护计划将对用户创建的所有数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="064de-129">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="064de-130">但不会对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库运行任何维护任务。</span><span class="sxs-lookup"><span data-stu-id="064de-130">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="064de-131">**以下数据库**</span><span class="sxs-lookup"><span data-stu-id="064de-131">**These databases**</span></span>  
  
     <span data-ttu-id="064de-132">生成的维护计划将只对所选数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="064de-132">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="064de-133">如果选择此选项，则必须至少在列表中选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="064de-133">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="064de-134">只能对兼容级别被设置为 80 或更高的数据库运行维护计划。</span><span class="sxs-lookup"><span data-stu-id="064de-134">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="064de-135">不显示兼容级别设置为 70 或更低的数据库。</span><span class="sxs-lookup"><span data-stu-id="064de-135">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="064de-136">**当数据库大小超过指定值时收缩数据库**</span><span class="sxs-lookup"><span data-stu-id="064de-136">**Shrink database when it grows beyond**</span></span>  
 <span data-ttu-id="064de-137">指定引发此任务的数据库大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="064de-137">Specify the size in megabytes that causes the task to execute.</span></span>  
  
 <span data-ttu-id="064de-138">**收缩后保留的可用空间**</span><span class="sxs-lookup"><span data-stu-id="064de-138">**Amount of free space to remain after shrink**</span></span>  
 <span data-ttu-id="064de-139">当数据库文件中的可用空间达到此值时停止收缩。</span><span class="sxs-lookup"><span data-stu-id="064de-139">Stop shrinking when free space in database files reaches this size.</span></span>  
  
 <span data-ttu-id="064de-140">**查看 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="064de-140">**View T-SQL**</span></span>  
 <span data-ttu-id="064de-141">根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="064de-141">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="064de-142">当受影响的对象很多时，可能需要相当长的时间才可显示。</span><span class="sxs-lookup"><span data-stu-id="064de-142">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="064de-143">“新建连接”对话框</span><span class="sxs-lookup"><span data-stu-id="064de-143">New Connection Dialog Box</span></span>  
 <span data-ttu-id="064de-144">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="064de-144">**Connection name**</span></span>  
 <span data-ttu-id="064de-145">输入新连接的名称。</span><span class="sxs-lookup"><span data-stu-id="064de-145">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="064de-146">**选择或输入服务器名称**</span><span class="sxs-lookup"><span data-stu-id="064de-146">**Select or enter a server name**</span></span>  
 <span data-ttu-id="064de-147">选择执行此任务时所要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="064de-147">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="064de-148">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="064de-148">**Refresh**</span></span>  
 <span data-ttu-id="064de-149">刷新可用服务器的列表。</span><span class="sxs-lookup"><span data-stu-id="064de-149">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="064de-150">**输入登录服务器所需的信息**</span><span class="sxs-lookup"><span data-stu-id="064de-150">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="064de-151">指定如何对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="064de-151">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="064de-152">**使用 Windows NT 集成安全性**</span><span class="sxs-lookup"><span data-stu-id="064de-152">**Use Windows NT Integrated security**</span></span>  
 <span data-ttu-id="064de-153">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="064de-153">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="064de-154">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="064de-154">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="064de-155">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="064de-155">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="064de-156">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="064de-156">This option is not available.</span></span>  
  
 <span data-ttu-id="064de-157">**用户名**</span><span class="sxs-lookup"><span data-stu-id="064de-157">**User name**</span></span>  
 <span data-ttu-id="064de-158">提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="064de-158">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="064de-159">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="064de-159">This option is not available.</span></span>  
  
 <span data-ttu-id="064de-160">**密码**</span><span class="sxs-lookup"><span data-stu-id="064de-160">**Password**</span></span>  
 <span data-ttu-id="064de-161">提供一个在进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="064de-161">Provide a password to use when authenticating.</span></span> <span data-ttu-id="064de-162">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="064de-162">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="064de-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="064de-163">See Also</span></span>  
 [<span data-ttu-id="064de-164">DBCC SHRINKDATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="064de-164">DBCC SHRINKDATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)  
  
  
