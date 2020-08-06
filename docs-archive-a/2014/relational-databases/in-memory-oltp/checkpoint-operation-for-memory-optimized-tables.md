---
title: 内存优化表的检查点操作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 07560ea0bf147198fb759f6769ae1c6d5c68a71e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693345"
---
# <a name="checkpoint-operation-for-memory-optimized-tables"></a><span data-ttu-id="0e54a-102">内存优化表的检查点操作</span><span class="sxs-lookup"><span data-stu-id="0e54a-102">Checkpoint Operation for Memory-Optimized Tables</span></span>
  <span data-ttu-id="0e54a-103">数据和差异文件中内存优化的数据需要定期出现检查点以前移事务日志的活动部分。</span><span class="sxs-lookup"><span data-stu-id="0e54a-103">A checkpoint needs to occur periodically for memory-optimized data in data and delta files to advance the active part of transaction log.</span></span> <span data-ttu-id="0e54a-104">通过检查点，内存优化表可还原或恢复到上一个成功的检查点，然后应用事务日志的活动部分以更新内存优化表从而完成恢复。</span><span class="sxs-lookup"><span data-stu-id="0e54a-104">The checkpoint allows memory-optimized tables to restore or recover to the last successful checkpoint and then the active portion of transaction log is applied to update the memory-optimized tables to complete the recovery.</span></span> <span data-ttu-id="0e54a-105">针对基于磁盘的表和内存优化表的检查点操作是完全不同的操作。</span><span class="sxs-lookup"><span data-stu-id="0e54a-105">The checkpoint operation for disk-based tables and memory-optimized tables are distinct operations.</span></span> <span data-ttu-id="0e54a-106">下面介绍不同的场景以及基于磁盘的表和内存优化表的检查点行为：</span><span class="sxs-lookup"><span data-stu-id="0e54a-106">The following describes different scenarios and the checkpoint behavior for disk-based and memory-optimized tables:</span></span>  
  
## <a name="manual-checkpoint"></a><span data-ttu-id="0e54a-107">手动检查点</span><span class="sxs-lookup"><span data-stu-id="0e54a-107">Manual Checkpoint</span></span>  
 <span data-ttu-id="0e54a-108">发出手动检查点时，它关闭基于磁盘的表和内存优化表的检查点。</span><span class="sxs-lookup"><span data-stu-id="0e54a-108">When you issue a manual checkpoint, it closes the checkpoint for both disk-based and memory-optimized tables.</span></span> <span data-ttu-id="0e54a-109">即使仅填充了活动数据文件的一部分，也将关闭该文件。</span><span class="sxs-lookup"><span data-stu-id="0e54a-109">The active data file is closed even though it may be partially filled.</span></span>  
  
## <a name="automatic-checkpoint"></a><span data-ttu-id="0e54a-110">自动检查点</span><span class="sxs-lookup"><span data-stu-id="0e54a-110">Automatic Checkpoint</span></span>  
 <span data-ttu-id="0e54a-111">对于基于磁盘的表和内存优化表而言，由于保留数据的方式不同，因此自动检查点的实现方式是不同的。</span><span class="sxs-lookup"><span data-stu-id="0e54a-111">Automatic checkpoint is implemented differently for disk-based and memory-optimized tables because of the different ways the data is persisted.</span></span>  
  
 <span data-ttu-id="0e54a-112">对于基于磁盘的表，将基于恢复间隔配置选项执行自动检查点（有关详细信息，请参阅[更改数据库的目标恢复时间 (SQL Server)](../logs/change-the-target-recovery-time-of-a-database-sql-server.md)）。</span><span class="sxs-lookup"><span data-stu-id="0e54a-112">For disk-based tables, an automatic checkpoint is taken based on the recovery interval configuration option (for more information, see [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../logs/change-the-target-recovery-time-of-a-database-sql-server.md)).</span></span>  
  
 <span data-ttu-id="0e54a-113">对于内存优化表，在上次检查点后事务日志文件变得大于 512 MB 时，会执行自动检查点。</span><span class="sxs-lookup"><span data-stu-id="0e54a-113">For memory-optimized tables, an automatic checkpoint is taken when transaction log file becomes bigger than 512 MB since the last checkpoint.</span></span> <span data-ttu-id="0e54a-114">512 MB 包括基于磁盘的表和内存优化表的事务日志记录。</span><span class="sxs-lookup"><span data-stu-id="0e54a-114">512 MB includes transaction log records for both disk-based and memory-optimized tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e54a-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e54a-115">See Also</span></span>  
 [<span data-ttu-id="0e54a-116">创建和管理用于内存优化对象的存储</span><span class="sxs-lookup"><span data-stu-id="0e54a-116">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
