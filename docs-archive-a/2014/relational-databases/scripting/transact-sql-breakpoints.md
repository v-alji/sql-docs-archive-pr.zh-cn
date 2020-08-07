---
title: Transact-SQL 断点
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoints
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
author: rothja
ms.author: jroth
ms.openlocfilehash: c9595c9627ac3cc445b1193881c2d5b772e9b71d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589495"
---
# <a name="transact-sql-breakpoints"></a><span data-ttu-id="c3e82-102">Transact-SQL 断点</span><span class="sxs-lookup"><span data-stu-id="c3e82-102">Transact-SQL Breakpoints</span></span>
  <span data-ttu-id="c3e82-103">断点指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器在特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句处暂停执行，这样您就可以查看该点的代码元素状态。</span><span class="sxs-lookup"><span data-stu-id="c3e82-103">Breakpoints specify that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger pause execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, you can then view the state of the code elements at that point.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="c3e82-104">断点</span><span class="sxs-lookup"><span data-stu-id="c3e82-104">Breakpoints</span></span>  
 <span data-ttu-id="c3e82-105">在运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器时，您可以切换特定语句上的断点。</span><span class="sxs-lookup"><span data-stu-id="c3e82-105">When running the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, you can toggle a breakpoint on specific statements.</span></span> <span data-ttu-id="c3e82-106">在执行到达具有断点的语句时，调试器将暂停执行，以便您可以查看调试信息，例如在变量和参数中存在的值。</span><span class="sxs-lookup"><span data-stu-id="c3e82-106">When execution reaches a statement with a breakpoint, the debugger pauses execution so you can view debugging information, such as the values present in variables and parameters.</span></span>  
  
 <span data-ttu-id="c3e82-107">您可以在编辑器窗口中单独管理断点，也可以使用 **“断点”** 窗口统一进行管理。</span><span class="sxs-lookup"><span data-stu-id="c3e82-107">You can manage breakpoints individually in the editor window, or collectively by using the **Breakpoints** window.</span></span> <span data-ttu-id="c3e82-108">您可以编辑断点以便指定项，例如执行应暂停的特定条件，或者在执行断点时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="c3e82-108">You can edit breakpoints to specify items such as specific conditions under which execution should pause, or the actions to be taken if the breakpoint is executed.</span></span>  
  
## <a name="breakpoint-tasks"></a><span data-ttu-id="c3e82-109">断点任务</span><span class="sxs-lookup"><span data-stu-id="c3e82-109">Breakpoint Tasks</span></span>  
  
|<span data-ttu-id="c3e82-110">任务说明</span><span class="sxs-lookup"><span data-stu-id="c3e82-110">Task Description</span></span>|<span data-ttu-id="c3e82-111">主题</span><span class="sxs-lookup"><span data-stu-id="c3e82-111">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="c3e82-112">说明如何指定想要调试器在其上暂停的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="c3e82-112">Describes how to specify the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement on which you want the debugger to pause.</span></span>|[<span data-ttu-id="c3e82-113">切换断点</span><span class="sxs-lookup"><span data-stu-id="c3e82-113">Toggle a Breakpoint</span></span>](../spatial/point.md)|  
|<span data-ttu-id="c3e82-114">说明如何暂时停用一个断点，并在以后将其重新激活。</span><span class="sxs-lookup"><span data-stu-id="c3e82-114">Describes how to temporarily deactivate a breakpoint, and later reactivate it.</span></span> <span data-ttu-id="c3e82-115">还介绍了如何删除断点。</span><span class="sxs-lookup"><span data-stu-id="c3e82-115">Also describes how to delete a breakpoint.</span></span>|[<span data-ttu-id="c3e82-116">启用、禁用和删除断点</span><span class="sxs-lookup"><span data-stu-id="c3e82-116">Enable, Disable, and Delete Breakpoints</span></span>](enable-disable-and-delete-breakpoints.md)|  
|<span data-ttu-id="c3e82-117">说明如何指定一个条件，该条件定义断点是否基于指定 Transact-SQL 表达式的计算结果而中断。</span><span class="sxs-lookup"><span data-stu-id="c3e82-117">Describes how to specify a condition, which defines whether breakpoint breaks based on the evaluation of a specified Transact-SQL expression.</span></span>|[<span data-ttu-id="c3e82-118">指定断点条件</span><span class="sxs-lookup"><span data-stu-id="c3e82-118">Specify a Breakpoint Condition</span></span>](specify-a-breakpoint-condition.md)|  
|<span data-ttu-id="c3e82-119">说明如何指定一个命中计数，该命中计数仅在包含断点的语句已执行了指定次数时才会导致断点中断。</span><span class="sxs-lookup"><span data-stu-id="c3e82-119">Describes how to specify a hit count, which causes a breakpoint to break only when the statement containing the breakpoint has been executed a specified number of times.</span></span>|[<span data-ttu-id="c3e82-120">指定命中计数</span><span class="sxs-lookup"><span data-stu-id="c3e82-120">Specify a Hit Count</span></span>](specify-a-hit-count.md)|  
|<span data-ttu-id="c3e82-121">说明如何指定一个筛选器，该筛选器使断点仅对于指定的进程或线程才会中断。</span><span class="sxs-lookup"><span data-stu-id="c3e82-121">Describes how to specify a filter, which causes a breakpoint to break for only specified processes or threads.</span></span>|[<span data-ttu-id="c3e82-122">指定断点筛选器</span><span class="sxs-lookup"><span data-stu-id="c3e82-122">Specify a Breakpoint Filter</span></span>](specify-a-breakpoint-filter.md)|  
|<span data-ttu-id="c3e82-123">说明如何指定一个“命中条件”操作，该“命中条件”  操作是一种在执行断点语句时执行的自定义操作。</span><span class="sxs-lookup"><span data-stu-id="c3e82-123">Describes how to specify a **When Hit** action, which is a custom operation that is performed when the breakpoint statement is executed.</span></span> <span data-ttu-id="c3e82-124">示例将打印一条消息。</span><span class="sxs-lookup"><span data-stu-id="c3e82-124">An example would be to print a message.</span></span>|[<span data-ttu-id="c3e82-125">指定断点操作</span><span class="sxs-lookup"><span data-stu-id="c3e82-125">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)|  
|<span data-ttu-id="c3e82-126">说明如何编辑断点的位置。</span><span class="sxs-lookup"><span data-stu-id="c3e82-126">Describes how to edit the location of a breakpoint.</span></span>|[<span data-ttu-id="c3e82-127">编辑断点位置</span><span class="sxs-lookup"><span data-stu-id="c3e82-127">Edit a Breakpoint Location</span></span>](edit-a-breakpoint-location.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c3e82-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3e82-128">See Also</span></span>  
 [<span data-ttu-id="c3e82-129">Transact-SQL 调试器信息</span><span class="sxs-lookup"><span data-stu-id="c3e82-129">Transact-SQL Debugger Information</span></span>](transact-sql-debugger-information.md)  
  
  
