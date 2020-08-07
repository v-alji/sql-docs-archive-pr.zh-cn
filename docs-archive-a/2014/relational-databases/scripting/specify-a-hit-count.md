---
title: 指定命中计数
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.hitcount
helpviewer_keywords:
- Transact-SQL debugger, breakpoint hit count
ms.assetid: 24836939-94ed-4e57-aa85-5d6938d859e4
author: rothja
ms.author: jroth
ms.openlocfilehash: 34c75e990bce1ea5e64c0b45f7acbcaa52fc3c40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588966"
---
# <a name="specify-a-hit-count"></a><span data-ttu-id="cde97-102">指定命中计数</span><span class="sxs-lookup"><span data-stu-id="cde97-102">Specify a Hit Count</span></span>
  <span data-ttu-id="cde97-103">断点命中计数是每次到达断点时由 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器递增的计数器。</span><span class="sxs-lookup"><span data-stu-id="cde97-103">A breakpoint hit count is a counter that is incremented by the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger each time the breakpoint is reached.</span></span> <span data-ttu-id="cde97-104">如果达到指定的命中计数并满足所有指定的断点条件，则调试器将执行为断点指定的操作。</span><span class="sxs-lookup"><span data-stu-id="cde97-104">If the specified hit count is reached and any specified breakpoint condition is satisfied, the debugger performs the action specified for the breakpoint.</span></span>  
  
## <a name="hit-count-considerations"></a><span data-ttu-id="cde97-105">命中计数注意事项</span><span class="sxs-lookup"><span data-stu-id="cde97-105">Hit Count Considerations</span></span>  
 <span data-ttu-id="cde97-106">默认情况下，每次到达断点时即中断执行。</span><span class="sxs-lookup"><span data-stu-id="cde97-106">By default, execution breaks every time a breakpoint is hit.</span></span> <span data-ttu-id="cde97-107">您可以在下面的选项之间进行选择：</span><span class="sxs-lookup"><span data-stu-id="cde97-107">You can choose between the following options:</span></span>  
  
-   <span data-ttu-id="cde97-108">总是中断（默认值）。</span><span class="sxs-lookup"><span data-stu-id="cde97-108">Break always (the default).</span></span>  
  
-   <span data-ttu-id="cde97-109">当命中计数等于指定值时中断。</span><span class="sxs-lookup"><span data-stu-id="cde97-109">Break when the hit count equals a specified value.</span></span>  
  
-   <span data-ttu-id="cde97-110">当命中计数等于指定值的倍数时中断。</span><span class="sxs-lookup"><span data-stu-id="cde97-110">Break when the hit count equals a multiple of a specified value.</span></span>  
  
-   <span data-ttu-id="cde97-111">当命中计数大于或等于指定值时中断。</span><span class="sxs-lookup"><span data-stu-id="cde97-111">Break when the hit count is greater than or equal to a specified value.</span></span>  
  
 <span data-ttu-id="cde97-112">中断命中计数在调试会话范围内递增。</span><span class="sxs-lookup"><span data-stu-id="cde97-112">Breakpoint hit counts are incremented within the scope of a debugging session.</span></span> <span data-ttu-id="cde97-113">所有命中计数在每个调试会话开始时均设置为零。</span><span class="sxs-lookup"><span data-stu-id="cde97-113">All hit counts are set to zero at the start of each debugging session.</span></span>  
  
 <span data-ttu-id="cde97-114">如果您想要跟踪命中断点的次数，但不执行断点中断，请将命中计数指定为一个非常高的值，以便断点永远不会中断。</span><span class="sxs-lookup"><span data-stu-id="cde97-114">If you want to track how many times a breakpoint is hit without having the breakpoint break execution, specify a hit count with a very high value so the breakpoint never breaks.</span></span>  
  
 <span data-ttu-id="cde97-115">当命中计数和断点条件都得到满足时，断点的默认操作为中断执行。</span><span class="sxs-lookup"><span data-stu-id="cde97-115">The default action for a breakpoint is to break execution when both the hit count and breakpoint condition have been satisfied.</span></span> <span data-ttu-id="cde97-116">有关指定其它操作的信息，请参阅 [指定断点操作](specify-a-breakpoint-action.md)。</span><span class="sxs-lookup"><span data-stu-id="cde97-116">For information about specifying other actions, see [Specify a Breakpoint Action](specify-a-breakpoint-action.md).</span></span>  
  
#### <a name="to-specify-a-hit-count"></a><span data-ttu-id="cde97-117">指定命中计数</span><span class="sxs-lookup"><span data-stu-id="cde97-117">To Specify a Hit Count</span></span>  
  
1.  <span data-ttu-id="cde97-118">在编辑器窗口中，右键单击断点符号，然后单击快捷菜单上的“命中计数”  。</span><span class="sxs-lookup"><span data-stu-id="cde97-118">In the editor window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="cde97-119">-或-</span><span class="sxs-lookup"><span data-stu-id="cde97-119">-or-</span></span>  
  
     <span data-ttu-id="cde97-120">在“断点”  窗口中，右键单击断点符号，然后单击快捷菜单上的“命中计数”  。</span><span class="sxs-lookup"><span data-stu-id="cde97-120">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="cde97-121">在 **“断点命中计数”** 对话框中，从 **“命中断点时”** 框中选择所需行为。</span><span class="sxs-lookup"><span data-stu-id="cde97-121">In the **Breakpoint Hit Count** dialog box, select the behavior you want from the **When the breakpoint is hit** box.</span></span>  
  
     <span data-ttu-id="cde97-122">如果您选择除 **“总是中断”** 以外的任何设置，则列表的右侧会出现一个文本框。</span><span class="sxs-lookup"><span data-stu-id="cde97-122">If you choose any setting other than **Break Always**, a text box appears to the right of the list.</span></span> <span data-ttu-id="cde97-123">在文本框中输入一个整数以指定所需的命中计数。</span><span class="sxs-lookup"><span data-stu-id="cde97-123">Enter an integer in the text box to specify the hit count you want.</span></span>  
  
3.  <span data-ttu-id="cde97-124">单击 **“确定”** 实施更改，或单击 **“取消”** 退出而不应用更改。</span><span class="sxs-lookup"><span data-stu-id="cde97-124">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
#### <a name="to-view-or-reset-the-current-hit-count"></a><span data-ttu-id="cde97-125">查看或重置当前命中计数</span><span class="sxs-lookup"><span data-stu-id="cde97-125">To View or Reset the Current Hit Count</span></span>  
  
1.  <span data-ttu-id="cde97-126">在编辑器窗口中，右键单击断点符号，然后单击快捷菜单上的“命中计数”  。</span><span class="sxs-lookup"><span data-stu-id="cde97-126">In the editor window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="cde97-127">-或-</span><span class="sxs-lookup"><span data-stu-id="cde97-127">-or-</span></span>  
  
     <span data-ttu-id="cde97-128">在“断点”  窗口中，右键单击断点符号，然后单击快捷菜单上的“命中计数”  。</span><span class="sxs-lookup"><span data-stu-id="cde97-128">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="cde97-129">在 **“断点命中计数”** 对话框中， **“当前命中计数:”** 显示在 **“重置”** 按钮的正上方。</span><span class="sxs-lookup"><span data-stu-id="cde97-129">In the **Breakpoint Hit Count** dialog box, the **Current hit count:** is displayed just above the **Reset** button.</span></span>  
  
3.  <span data-ttu-id="cde97-130">如果您想要将当前命中计数设置为零，请单击 **“重置”** 。</span><span class="sxs-lookup"><span data-stu-id="cde97-130">Click **Reset** if you want to set the current hit count to zero.</span></span>  
  
4.  <span data-ttu-id="cde97-131">单击 **“确定”** 或 **“取消”** 以退出对话框。</span><span class="sxs-lookup"><span data-stu-id="cde97-131">Click **OK** or **Cancel** to exit the dialog.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde97-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cde97-132">See Also</span></span>  
 [<span data-ttu-id="cde97-133">指定断点条件</span><span class="sxs-lookup"><span data-stu-id="cde97-133">Specify a Breakpoint Condition</span></span>](specify-a-breakpoint-condition.md)  
  
  
