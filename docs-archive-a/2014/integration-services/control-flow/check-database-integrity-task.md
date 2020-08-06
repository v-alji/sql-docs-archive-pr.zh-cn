---
title: “检查数据库完整性任务”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.checkdatabaseintegritytask.f1
helpviewer_keywords:
- data integrity [Integration Services]
- Check Database Integrity task [Integration Services]
- checking database consistency
- database consistency checks [Integration Services]
- verifying database consistency
- integrity checking [Integration Services]
ms.assetid: 5a82fe99-4503-429f-9337-e6bac7649fe4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 99a2620a6f3f6a9a73c27fe6bb1abd34af73707d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585937"
---
# <a name="check-database-integrity-task"></a><span data-ttu-id="2b029-102">“检查数据库完整性”任务</span><span class="sxs-lookup"><span data-stu-id="2b029-102">Check Database Integrity Task</span></span>
  <span data-ttu-id="2b029-103">“检查数据库完整性”任务检查指定数据库中所有对象的分配和结构完整性。</span><span class="sxs-lookup"><span data-stu-id="2b029-103">The Check Database Integrity task checks the allocation and structural integrity of all the objects in the specified database.</span></span> <span data-ttu-id="2b029-104">此任务可以检查单个数据库或多个数据库，您还可以选择是否也检查数据库索引。</span><span class="sxs-lookup"><span data-stu-id="2b029-104">The task can check a single database or multiple databases, and you can choose whether to also check the database indexes.</span></span>  
  
 <span data-ttu-id="2b029-105">“检查数据库完整性”任务封装 DBCC CHECKDB 语句。</span><span class="sxs-lookup"><span data-stu-id="2b029-105">The Check Database Integrity task encapsulates the DBCC CHECKDB statement.</span></span> <span data-ttu-id="2b029-106">有关详细信息，请参阅 [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2b029-106">For more information, see [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql).</span></span>  
  
## <a name="configuration-of-the-check-database-integrity-task"></a><span data-ttu-id="2b029-107">“检查数据库完整性”任务的配置</span><span class="sxs-lookup"><span data-stu-id="2b029-107">Configuration of the Check Database Integrity Task</span></span>  
 <span data-ttu-id="2b029-108">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="2b029-108">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="2b029-109">此任务位于 **设计器中** “工具箱” **的** “维护计划中的任务” [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="2b029-109">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="2b029-110">有关可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="2b029-110">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="2b029-111">“检查数据库完整性”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="2b029-111">Check Database Integrity Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/check-database-integrity-task-maintenance-plan.md)  
  
 <span data-ttu-id="2b029-112">有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="2b029-112">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="2b029-113">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="2b029-113">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
