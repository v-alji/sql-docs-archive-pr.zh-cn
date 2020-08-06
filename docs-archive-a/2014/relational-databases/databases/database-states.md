---
title: 数据库状态 | Microsoft Docs
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASESTATES.F1
helpviewer_keywords:
- emergency database state [SQL Server]
- verifying database states
- viewing database states
- displaying database states
- database states [SQL Server]
- current database state
- offline database state [SQL Server]
- suspect database state
- recovery pending database state [SQL Server]
- states [SQL Server], databases
- online database state
- states [SQL Server]
- restoring database state [SQL Server]
ms.assetid: b7f1f111-ca73-4a89-b567-a98d64d6ecb3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0aec4e5fb367f5fe9bf8fca5ed056269930cf2db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693941"
---
# <a name="database-states"></a><span data-ttu-id="99467-102">数据库状态</span><span class="sxs-lookup"><span data-stu-id="99467-102">Database States</span></span>
  <span data-ttu-id="99467-103">数据库总是处于一个特定的状态中，</span><span class="sxs-lookup"><span data-stu-id="99467-103">A database is always in one specific state.</span></span> <span data-ttu-id="99467-104">例如，这些状态包括 ONLINE、OFFLINE 或 SUSPECT。</span><span class="sxs-lookup"><span data-stu-id="99467-104">For example, these states include ONLINE, OFFLINE, or SUSPECT.</span></span> <span data-ttu-id="99467-105">若要确认数据库的当前状态，请选择 **sys.databases** 目录视图中的 [state_desc](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 列或 **DATABASEPROPERTYEX** 函数中的 [Status](/sql/t-sql/functions/databasepropertyex-transact-sql) 属性。</span><span class="sxs-lookup"><span data-stu-id="99467-105">To verify the current state of a database, select the **state_desc** column in the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view or the **Status** property in the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) function.</span></span>  
  
## <a name="database-state-definitions"></a><span data-ttu-id="99467-106">数据库状态定义</span><span class="sxs-lookup"><span data-stu-id="99467-106">Database State Definitions</span></span>  
 <span data-ttu-id="99467-107">下表定义了数据库的状态。</span><span class="sxs-lookup"><span data-stu-id="99467-107">The following table defines the database states.</span></span>  
  
|<span data-ttu-id="99467-108">状态</span><span class="sxs-lookup"><span data-stu-id="99467-108">State</span></span>|<span data-ttu-id="99467-109">定义</span><span class="sxs-lookup"><span data-stu-id="99467-109">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="99467-110">ONLINE</span><span class="sxs-lookup"><span data-stu-id="99467-110">ONLINE</span></span>|<span data-ttu-id="99467-111">可以对数据库进行访问。</span><span class="sxs-lookup"><span data-stu-id="99467-111">Database is available for access.</span></span> <span data-ttu-id="99467-112">即使可能尚未完成恢复的撤消阶段，主文件组仍处于在线状态。</span><span class="sxs-lookup"><span data-stu-id="99467-112">The primary filegroup is online, although the undo phase of recovery may not have been completed.</span></span>|  
|<span data-ttu-id="99467-113">OFFLINE</span><span class="sxs-lookup"><span data-stu-id="99467-113">OFFLINE</span></span>|<span data-ttu-id="99467-114">数据库无法使用。</span><span class="sxs-lookup"><span data-stu-id="99467-114">Database is unavailable.</span></span> <span data-ttu-id="99467-115">数据库由于显式的用户操作而处于离线状态，并保持离线状态直至执行了其他的用户操作。</span><span class="sxs-lookup"><span data-stu-id="99467-115">A database becomes offline by explicit user action and remains offline until additional user action is taken.</span></span> <span data-ttu-id="99467-116">例如，可能会让数据库离线以便将文件移至新的磁盘。</span><span class="sxs-lookup"><span data-stu-id="99467-116">For example, the database may be taken offline in order to move a file to a new disk.</span></span> <span data-ttu-id="99467-117">然后，在完成移动操作后，使数据库恢复到在线状态。</span><span class="sxs-lookup"><span data-stu-id="99467-117">The database is then brought back online after the move has been completed.</span></span>|  
|<span data-ttu-id="99467-118">RESTORING</span><span class="sxs-lookup"><span data-stu-id="99467-118">RESTORING</span></span>|<span data-ttu-id="99467-119">正在还原主文件组的一个或多个文件，或正在脱机还原一个或多个辅助文件。</span><span class="sxs-lookup"><span data-stu-id="99467-119">One or more files of the primary filegroup are being restored, or one or more secondary files are being restored offline.</span></span> <span data-ttu-id="99467-120">数据库不可用。</span><span class="sxs-lookup"><span data-stu-id="99467-120">The database is unavailable.</span></span>|  
|<span data-ttu-id="99467-121">RECOVERING</span><span class="sxs-lookup"><span data-stu-id="99467-121">RECOVERING</span></span>|<span data-ttu-id="99467-122">正在恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="99467-122">Database is being recovered.</span></span> <span data-ttu-id="99467-123">恢复进程是一个暂时性状态，恢复成功后数据库将自动处于在线状态。</span><span class="sxs-lookup"><span data-stu-id="99467-123">The recovering process is a transient state; the database will automatically become online if the recovery succeeds.</span></span> <span data-ttu-id="99467-124">如果恢复失败，数据库将处于可疑状态。</span><span class="sxs-lookup"><span data-stu-id="99467-124">If the recovery fails, the database will become suspect.</span></span> <span data-ttu-id="99467-125">数据库不可用。</span><span class="sxs-lookup"><span data-stu-id="99467-125">The database is unavailable.</span></span>|  
|<span data-ttu-id="99467-126">RECOVERY PENDING</span><span class="sxs-lookup"><span data-stu-id="99467-126">RECOVERY PENDING</span></span>|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="99467-127">在恢复期间遇到了与资源相关的错误。</span><span class="sxs-lookup"><span data-stu-id="99467-127">has encountered a resource-related error during recovery.</span></span> <span data-ttu-id="99467-128">数据库未损坏，但是可能缺少文件，或系统资源限制可能导致无法启动数据库。</span><span class="sxs-lookup"><span data-stu-id="99467-128">The database is not damaged, but files may be missing or system resource limitations may be preventing it from starting.</span></span> <span data-ttu-id="99467-129">数据库不可用。</span><span class="sxs-lookup"><span data-stu-id="99467-129">The database is unavailable.</span></span> <span data-ttu-id="99467-130">需要用户另外执行操作来解决问题，并让恢复进程完成。</span><span class="sxs-lookup"><span data-stu-id="99467-130">Additional action by the user is required to resolve the error and let the recovery process be completed.</span></span>|  
|<span data-ttu-id="99467-131">SUSPECT</span><span class="sxs-lookup"><span data-stu-id="99467-131">SUSPECT</span></span>|<span data-ttu-id="99467-132">至少主文件组可疑或可能已损坏。</span><span class="sxs-lookup"><span data-stu-id="99467-132">At least the primary filegroup is suspect and may be damaged.</span></span> <span data-ttu-id="99467-133">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]启动过程中无法恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="99467-133">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="99467-134">数据库不可用。</span><span class="sxs-lookup"><span data-stu-id="99467-134">The database is unavailable.</span></span> <span data-ttu-id="99467-135">需要用户另外执行操作来解决问题。</span><span class="sxs-lookup"><span data-stu-id="99467-135">Additional action by the user is required to resolve the problem.</span></span>|  
|<span data-ttu-id="99467-136">EMERGENCY</span><span class="sxs-lookup"><span data-stu-id="99467-136">EMERGENCY</span></span>|<span data-ttu-id="99467-137">用户更改了数据库，并将其状态设置为 EMERGENCY。</span><span class="sxs-lookup"><span data-stu-id="99467-137">User has changed the database and set the status to EMERGENCY.</span></span> <span data-ttu-id="99467-138">数据库处于单用户模式，可以修复或还原。</span><span class="sxs-lookup"><span data-stu-id="99467-138">The database is in single-user mode and may be repaired or restored.</span></span> <span data-ttu-id="99467-139">数据库标记为 READ_ONLY，禁用日志记录，并仅限 **sysadmin** 固定服务器角色的成员访问。</span><span class="sxs-lookup"><span data-stu-id="99467-139">The database is marked READ_ONLY, logging is disabled, and access is limited to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="99467-140">EMERGENCY 主要用于故障排除。</span><span class="sxs-lookup"><span data-stu-id="99467-140">EMERGENCY is primarily used for troubleshooting purposes.</span></span> <span data-ttu-id="99467-141">例如，可以将标记为“可疑”的数据库设置为 EMERGENCY 状态。</span><span class="sxs-lookup"><span data-stu-id="99467-141">For example, a database marked as suspect can be set to the EMERGENCY state.</span></span> <span data-ttu-id="99467-142">这样可以允许系统管理员对数据库进行只读访问。</span><span class="sxs-lookup"><span data-stu-id="99467-142">This could permit the system administrator read-only access to the database.</span></span> <span data-ttu-id="99467-143">只有 **sysadmin** 固定服务器角色的成员才可以将数据库设置为 EMERGENCY 状态。</span><span class="sxs-lookup"><span data-stu-id="99467-143">Only members of the **sysadmin** fixed server role can set a database to the EMERGENCY state.</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="99467-144">相关内容</span><span class="sxs-lookup"><span data-stu-id="99467-144">Related Content</span></span>  
 [<span data-ttu-id="99467-145">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="99467-145">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [<span data-ttu-id="99467-146">镜像状态 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="99467-146">Mirroring States &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [<span data-ttu-id="99467-147">文件状态</span><span class="sxs-lookup"><span data-stu-id="99467-147">File States</span></span>](file-states.md)  
  
  
