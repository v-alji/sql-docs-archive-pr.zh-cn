---
title: 收缩数据库任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.shrinkdatabasetask.f1
helpviewer_keywords:
- Shrink Database task
- database shrinking [Integration Services]
- shrinking databases
ms.assetid: e66286f8-97b1-4e5a-86b4-e56f1932b7d5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 587777928e362e87e4b691e3c46167c1239984cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589827"
---
# <a name="shrink-database-task"></a><span data-ttu-id="45eb1-102">收缩数据库任务</span><span class="sxs-lookup"><span data-stu-id="45eb1-102">Shrink Database Task</span></span>
  <span data-ttu-id="45eb1-103">收缩数据库任务可以减少 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库数据和日志文件的大小。</span><span class="sxs-lookup"><span data-stu-id="45eb1-103">The Shrink Database task reduces the size of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database data and log files.</span></span>  
  
 <span data-ttu-id="45eb1-104">使用收缩数据库任务，包可以为单个或多个数据库收缩文件。</span><span class="sxs-lookup"><span data-stu-id="45eb1-104">By using the Shrink Database task, a package can shrink files for a single database or multiple databases.</span></span>  
  
 <span data-ttu-id="45eb1-105">收缩数据文件通过将数据页从文件末尾移动到更靠近文件开头的未占用的空间来恢复空间。</span><span class="sxs-lookup"><span data-stu-id="45eb1-105">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="45eb1-106">在文件末尾创建足够的可用空间后，可以取消对文件末尾的数据页的分配并将它们返回给文件系统。</span><span class="sxs-lookup"><span data-stu-id="45eb1-106">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="45eb1-107">被移动用来收缩文件的数据可以分布到文件的任何可用位置。</span><span class="sxs-lookup"><span data-stu-id="45eb1-107">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="45eb1-108">这将导致索引碎片并使搜索索引范围的查询变慢。</span><span class="sxs-lookup"><span data-stu-id="45eb1-108">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="45eb1-109">若要消除碎片，请考虑在收缩后重新生成文件的索引。</span><span class="sxs-lookup"><span data-stu-id="45eb1-109">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
## <a name="commands"></a><span data-ttu-id="45eb1-110">命令</span><span class="sxs-lookup"><span data-stu-id="45eb1-110">Commands</span></span>  
 <span data-ttu-id="45eb1-111">收缩数据库任务封装了 DBCC SHRINKDATABASE 命令，其中包括下列参数和选项：</span><span class="sxs-lookup"><span data-stu-id="45eb1-111">The Shrink Database task encapsulates a DBCC SHRINKDATABASE command, including the following arguments and options:</span></span>  
  
-   <span data-ttu-id="45eb1-112">*database_name*</span><span class="sxs-lookup"><span data-stu-id="45eb1-112">*database_name*</span></span>  
  
-   <span data-ttu-id="45eb1-113">*target_percent*</span><span class="sxs-lookup"><span data-stu-id="45eb1-113">*target_percent*</span></span>  
  
-   <span data-ttu-id="45eb1-114">NOTRUNCATE 或 TRUNCATEONLY。</span><span class="sxs-lookup"><span data-stu-id="45eb1-114">NOTRUNCATE or TRUNCATEONLY.</span></span>  
  
 <span data-ttu-id="45eb1-115">如果收缩数据库任务收缩多个数据库，则该任务将对每个数据库都运行一次 SHRINKDATABASE 命令。</span><span class="sxs-lookup"><span data-stu-id="45eb1-115">If the Shrink Database task shrinks multiple databases, the task runs multiple SHRINKDATABASE commands, one for each database.</span></span> <span data-ttu-id="45eb1-116">除了 *database_name* 参数以外，SHRINKDATABASE 命令的所有实例均使用相同的参数值。</span><span class="sxs-lookup"><span data-stu-id="45eb1-116">All instances of the SHRINKDATABASE command use the same argument values, except for the *database_name* argument.</span></span> <span data-ttu-id="45eb1-117">有关详细信息，请参阅 [DBCC SHRINKDATABASE (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="45eb1-117">For more information, see [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql).</span></span>  
  
## <a name="configuration-of-the-shrink-database-task"></a><span data-ttu-id="45eb1-118">配置收缩数据库任务</span><span class="sxs-lookup"><span data-stu-id="45eb1-118">Configuration of the Shrink Database Task</span></span>  
 <span data-ttu-id="45eb1-119">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器设置属性。</span><span class="sxs-lookup"><span data-stu-id="45eb1-119">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="45eb1-120">此任务位于 **设计器中** “工具箱” **的** “维护计划中的任务” [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="45eb1-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="45eb1-121">有关可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下面的主题：</span><span class="sxs-lookup"><span data-stu-id="45eb1-121">For more information about the properties that you can set in the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="45eb1-122">“收缩数据库”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="45eb1-122">Shrink Database Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/shrink-database-task-maintenance-plan.md)  
  
 <span data-ttu-id="45eb1-123">有关在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="45eb1-123">For more information about setting these properties in the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="45eb1-124">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="45eb1-124">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
