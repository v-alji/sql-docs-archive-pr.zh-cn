---
title: “线程”窗口
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f3460c892c182996a753c2a16076418a6b2008f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688802"
---
# <a name="threads-window"></a><span data-ttu-id="a0c2e-102">“线程”窗口</span><span class="sxs-lookup"><span data-stu-id="a0c2e-102">Threads Window</span></span>
  <span data-ttu-id="a0c2e-103">“线程”  窗口显示有关正在调试的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器会话使用的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 线程的信息。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-103">The **Threads** window displays information about the [!INCLUDE[ssDE](../../includes/ssde-md.md)] thread that is used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor session that is being debugged.</span></span> <span data-ttu-id="a0c2e-104">只有在调试模式下才可以显示此线程信息。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-104">You must be in debug mode to display the thread information.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="a0c2e-105">任务列表</span><span class="sxs-lookup"><span data-stu-id="a0c2e-105">Task List</span></span>  
 <span data-ttu-id="a0c2e-106">**访问“线程”窗口**</span><span class="sxs-lookup"><span data-stu-id="a0c2e-106">**To access the Threads window**</span></span>  
  
-   <span data-ttu-id="a0c2e-107">在 **“调试”** 菜单上单击 **“窗口”** ，然后单击 **“线程”** 。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-107">On the **Debug** menu, click **Windows**, and then click **Threads**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="a0c2e-108">列</span><span class="sxs-lookup"><span data-stu-id="a0c2e-108">Columns</span></span>  
 <span data-ttu-id="a0c2e-109">**ID**</span><span class="sxs-lookup"><span data-stu-id="a0c2e-109">**ID**</span></span>  
 <span data-ttu-id="a0c2e-110">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器分配给该线程的唯一标识号。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-110">Is a unique identifying number that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger assigns to the thread.</span></span> <span data-ttu-id="a0c2e-111">从 sys.dm_os_threads 动态管理视图中选择某一行，即可找到有关此线程的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-111">You can find more information about the thread by selecting a row from the sys.dm_os_threads dynamic management view.</span></span>  
  
 <span data-ttu-id="a0c2e-112">如果当前未在轻型池模式下运行，则请选择满足以下条件的行：此行中 os_thread_id 列的值与 **ID** 列的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-112">If you are not running in lightweight pooling mode, select the row in which the value in os_thread_id matches the value in the **ID** column.</span></span> <span data-ttu-id="a0c2e-113">如果当前在轻型池模式下运行，则请选择满足以下条件的行：此行中 fiber_context_address 列的值与 **ID** 列的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-113">If you are running in lightweight pooling mode, select the row in which the value in fiber_context_address matches the value in the **ID** column.</span></span>  
  
 <span data-ttu-id="a0c2e-114">**名称**</span><span class="sxs-lookup"><span data-stu-id="a0c2e-114">**Name**</span></span>  
 <span data-ttu-id="a0c2e-115">以 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 计算机名/实例名 [SPID] **格式显示有关**会话的信息。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-115">Displays information about the [!INCLUDE[ssDE](../../includes/ssde-md.md)] session in the format **ComputerName/InstanceName [SPID]**.</span></span>  
  
 <span data-ttu-id="a0c2e-116">**计算机名**</span><span class="sxs-lookup"><span data-stu-id="a0c2e-116">**ComputerName**</span></span>  
 <span data-ttu-id="a0c2e-117">运行查询编辑器会话连接到的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-117">The name of the computer that is running the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that the Query Editor session is connected to.</span></span>  
  
 <span data-ttu-id="a0c2e-118">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="a0c2e-118">**InstanceName**</span></span>  
 <span data-ttu-id="a0c2e-119">查询编辑器会话连接到的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-119">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that the Query Editor session is connected to.</span></span>  
  
 <span data-ttu-id="a0c2e-120">**[SPID]**</span><span class="sxs-lookup"><span data-stu-id="a0c2e-120">**[SPID]**</span></span>  
 <span data-ttu-id="a0c2e-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会话进程 ID，用于唯一标识此会话。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session process ID that uniquely identifies this session.</span></span> <span data-ttu-id="a0c2e-122">通过在 sys.sysprocesses 视图中选择 spid 列中此 ID 值所在的行，可以获取有关此会话的更多信息。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-122">You can obtain more information about the session by selecting the row in the sys.sysprocesses view that has the same value in the spid column.</span></span>  
  
 <span data-ttu-id="a0c2e-123">**位置**</span><span class="sxs-lookup"><span data-stu-id="a0c2e-123">**Location**</span></span>  
 <span data-ttu-id="a0c2e-124">显示正在调试的查询编辑器会话使用的脚本文件的名称。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-124">Displays the name of the script file that is used in the Query Editor session that is being debugged.</span></span>  
  
 <span data-ttu-id="a0c2e-125">**Priority**</span><span class="sxs-lookup"><span data-stu-id="a0c2e-125">**Priority**</span></span>  
 <span data-ttu-id="a0c2e-126">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器不支持此功能。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-126">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
 <span data-ttu-id="a0c2e-127">**挂起**</span><span class="sxs-lookup"><span data-stu-id="a0c2e-127">**Suspend**</span></span>  
 <span data-ttu-id="a0c2e-128">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器不支持此功能。</span><span class="sxs-lookup"><span data-stu-id="a0c2e-128">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c2e-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0c2e-129">See Also</span></span>  
 <span data-ttu-id="a0c2e-130">[Transact-SQL 调试器](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="a0c2e-130">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="a0c2e-131">[Transact-SQL 调试器信息](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="a0c2e-131">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="a0c2e-132">[sys.dm_os_threads (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0c2e-132">[sys.dm_os_threads &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql) </span></span>  
 [<span data-ttu-id="a0c2e-133">sys.sysprocesses (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a0c2e-133">sys.sysprocesses &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql)  
