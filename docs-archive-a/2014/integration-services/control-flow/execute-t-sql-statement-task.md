---
title: 执行 T-SQL 语句任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7ebc73ad843ac7fcf1dfbe7699ecd8ea53edcdad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688107"
---
# <a name="execute-t-sql-statement-task"></a><span data-ttu-id="55e9d-102">执行 T-SQL 语句任务</span><span class="sxs-lookup"><span data-stu-id="55e9d-102">Execute T-SQL Statement Task</span></span>
  <span data-ttu-id="55e9d-103">执行 T-SQL 语句任务运行 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="55e9d-103">The Execute T-SQL Statement task runs Transact-SQL statements.</span></span> <span data-ttu-id="55e9d-104">有关详细信息，请参阅 [Transact-SQL 引用（数据库引擎）](/sql/t-sql/language-reference)和 [Integration Services (SSIS) 查询](../integration-services-ssis-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="55e9d-104">For more information, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference) and [Integration Services &#40;SSIS&#41; Queries](../integration-services-ssis-queries.md).</span></span>  
  
 <span data-ttu-id="55e9d-105">此任务类似于执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="55e9d-105">This task is similar to the Execute SQL task.</span></span> <span data-ttu-id="55e9d-106">但是，执行 T-SQL 语句任务只支持 SQL 语言的 Transact-SQL 版本，在使用 SQL 语言的其他方言的服务器上无法使用此任务来运行语句。</span><span class="sxs-lookup"><span data-stu-id="55e9d-106">However, the Execute T-SQL Statement task supports only the Transact-SQL version of the SQL language and you cannot use this task to run statements on servers that use other dialects of the SQL language.</span></span> <span data-ttu-id="55e9d-107">如果需要运行参数化查询，将查询结果保存到变量，或使用属性表达式，那么您应当使用执行 SQL 任务而不是执行 T-SQL 语句任务。</span><span class="sxs-lookup"><span data-stu-id="55e9d-107">If you need to run parameterized queries, save the query results to variables, or use property expressions, you should use the Execute SQL task instead of the Execute T-SQL Statement task.</span></span> <span data-ttu-id="55e9d-108">有关详细信息，请参阅 [Execute SQL Task](execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="55e9d-108">For more information, see [Execute SQL Task](execute-sql-task.md).</span></span>  
  
## <a name="configuration-of-the-execute-t-sql-task"></a><span data-ttu-id="55e9d-109">执行 T-SQL 任务的配置</span><span class="sxs-lookup"><span data-stu-id="55e9d-109">Configuration of the Execute T-SQL Task</span></span>  
 <span data-ttu-id="55e9d-110">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="55e9d-110">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="55e9d-111">此任务位于 **设计器中** “工具箱” **的** “维护计划中的任务” [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="55e9d-111">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="55e9d-112">有关可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="55e9d-112">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="55e9d-113">“执行 T-SQL 语句”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="55e9d-113">Execute T-SQL Statement Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 <span data-ttu-id="55e9d-114">有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="55e9d-114">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="55e9d-115">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="55e9d-115">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="55e9d-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55e9d-116">See Also</span></span>  
 <span data-ttu-id="55e9d-117">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="55e9d-117">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 <span data-ttu-id="55e9d-118">[控制流](control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="55e9d-118">[Control Flow](control-flow.md) </span></span>  
 [<span data-ttu-id="55e9d-119">在 Integration Services 包中执行 MERGE</span><span class="sxs-lookup"><span data-stu-id="55e9d-119">MERGE in Integration Services Packages</span></span>](merge-in-integration-services-packages.md)  
  
  
