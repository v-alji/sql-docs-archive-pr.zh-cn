---
title: 切换断点
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
author: rothja
ms.author: jroth
ms.openlocfilehash: 72e26e9b1d04bc2eced6bcb6d93d3c86a016d308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589496"
---
# <a name="toggle-a-breakpoint"></a><span data-ttu-id="9cec6-102">切换断点</span><span class="sxs-lookup"><span data-stu-id="9cec6-102">Toggle a Breakpoint</span></span>
  <span data-ttu-id="9cec6-103">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句上设置断点的操作称为切换断点。</span><span class="sxs-lookup"><span data-stu-id="9cec6-103">The act of setting a breakpoint on a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is called toggling a breakpoint.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="9cec6-104">断点</span><span class="sxs-lookup"><span data-stu-id="9cec6-104">Breakpoints</span></span>  
 <span data-ttu-id="9cec6-105">设置断点后，语句左侧的灰色栏中会出现一个图标来表示该断点。</span><span class="sxs-lookup"><span data-stu-id="9cec6-105">Once the breakpoint has been set, it is represented by an icon in the grey bar to the left of the statement.</span></span> <span data-ttu-id="9cec6-106">该图标称为断点符号。</span><span class="sxs-lookup"><span data-stu-id="9cec6-106">The icon is called a breakpoint glyph.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="9cec6-107">断点适用于整个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="9cec6-107">breakpoints are applied to a complete [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="9cec6-108">打开断点时，调试器会突出显示相关联的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="9cec6-108">When a breakpoint is toggled on, the debugger highlights the associated [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
 <span data-ttu-id="9cec6-109">如果一行中存在多个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，可以为每个语句切换一个断点。</span><span class="sxs-lookup"><span data-stu-id="9cec6-109">If there are multiple [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on a line, you can toggle a breakpoint for each statement.</span></span> <span data-ttu-id="9cec6-110">单击窗口左侧的灰色栏可以在行中的第一个语句上切换断点。</span><span class="sxs-lookup"><span data-stu-id="9cec6-110">Clicking in the grey bar on the left of the window toggles a breakpoint on the first statement on the line.</span></span> <span data-ttu-id="9cec6-111">您可以通过以下方法在后续语句中切换断点：突出显示该语句的任何部分，或将光标移动到该语句中，然后按 F9 或单击 **“调试”** 菜单上的 **“切换断点”** 。</span><span class="sxs-lookup"><span data-stu-id="9cec6-111">You can toggle a breakpoint in a subsequent statement by highlighting any part of the statement, or moving the cursor into the statement, and then either pressing F9 or clicking **Toggle Breakpoint** on the **Debug** menu.</span></span> <span data-ttu-id="9cec6-112">如果一行中有多个断点，则只有一个断点符号位于左侧的灰色栏中。</span><span class="sxs-lookup"><span data-stu-id="9cec6-112">If you have multiple breakpoints on a line, there is only one breakpoint glyph in the grey bar on the left.</span></span>  
  
 <span data-ttu-id="9cec6-113">在切换某一断点后，您可以对该断点执行不同的操作，例如编辑其属性或临时禁用该断点。</span><span class="sxs-lookup"><span data-stu-id="9cec6-113">After a breakpoint has been toggled, you can perform various actions on the breakpoint, such as editing its properties or temporarily disabling it.</span></span> <span data-ttu-id="9cec6-114">有关详细信息，请参阅 [Transact-SQL 断点](transact-sql-breakpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="9cec6-114">For more information, see [Transact-SQL Breakpoints](transact-sql-breakpoints.md).</span></span>  
  
## <a name="toggle-a-breakpoint"></a><span data-ttu-id="9cec6-115">切换断点</span><span class="sxs-lookup"><span data-stu-id="9cec6-115">Toggle a Breakpoint</span></span>  
 <span data-ttu-id="9cec6-116">**切换 Transact-SQL 语句上的断点**</span><span class="sxs-lookup"><span data-stu-id="9cec6-116">**To toggle a breakpoint on a Transact-SQL statement**</span></span>  
  
1.  <span data-ttu-id="9cec6-117">单击 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句左侧的灰色栏。</span><span class="sxs-lookup"><span data-stu-id="9cec6-117">Click the gray bar to the left side of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
2.  <span data-ttu-id="9cec6-118">或者，突出显示语句的任何部分，或将光标移到语句上，然后执行下列两个操作之一：</span><span class="sxs-lookup"><span data-stu-id="9cec6-118">Alternatively, either highlight any part of the statement or move the cursor to the statement, and then perform either action:</span></span>  
  
    -   <span data-ttu-id="9cec6-119">按 F9。</span><span class="sxs-lookup"><span data-stu-id="9cec6-119">Press F9.</span></span>  
  
    -   <span data-ttu-id="9cec6-120">在 **“调试”** 菜单上，单击 **“切换断点”** 。</span><span class="sxs-lookup"><span data-stu-id="9cec6-120">On the **Debug** menu, click **Toggle Breakpoint**.</span></span>  
  
  
