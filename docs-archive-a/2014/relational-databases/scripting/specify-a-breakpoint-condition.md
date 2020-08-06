---
title: 指定断点条件
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 659b6ca1149eb8f0412efbe2adbaf4c1ffce59d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690494"
---
# <a name="specify-a-breakpoint-condition"></a><span data-ttu-id="e8347-102">指定断点条件</span><span class="sxs-lookup"><span data-stu-id="e8347-102">Specify a Breakpoint Condition</span></span>
  <span data-ttu-id="e8347-103">断点条件是当到达断点时，由调试器计算的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表达式。</span><span class="sxs-lookup"><span data-stu-id="e8347-103">A breakpoint condition is a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression that is evaluated by the debugger when the breakpoint is reached.</span></span> <span data-ttu-id="e8347-104">如果满足条件，并且达到任何指定的命中计数，则调试器或者中断，或者执行为断点指定的操作。</span><span class="sxs-lookup"><span data-stu-id="e8347-104">If the condition is satisfied and any specified hit count reached, the debugger either breaks or performs the action specified for the breakpoint.</span></span>  
  
## <a name="specifying-conditions"></a><span data-ttu-id="e8347-105">指定条件</span><span class="sxs-lookup"><span data-stu-id="e8347-105">Specifying Conditions</span></span>  
 <span data-ttu-id="e8347-106">指定的表达式必须是计算结果为布尔值的有效 Transact-SQL 表达式。</span><span class="sxs-lookup"><span data-stu-id="e8347-106">The expression specified must be a valid Transact-SQL expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="e8347-107">有关详细信息，请参阅[表达式 (Transact-SQL)](/sql/t-sql/language-elements/expressions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e8347-107">For more information, see [Expressions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql).</span></span>  
  
 <span data-ttu-id="e8347-108">如果用于指定断点条件的语法无效，则会立即出现一条警告消息。</span><span class="sxs-lookup"><span data-stu-id="e8347-108">If you specify a breakpoint condition with invalid syntax, a warning message appears immediately.</span></span> <span data-ttu-id="e8347-109">如果用于指定条件的语法有效但语义无效，则会在第一次命中断点时显示一条警告消息。</span><span class="sxs-lookup"><span data-stu-id="e8347-109">If you specify a condition with valid syntax but invalid semantics, a warning message is displayed the first time the breakpoint is hit.</span></span> <span data-ttu-id="e8347-110">在这两种情况下，当命中无效断点时，调试器都将中断执行。</span><span class="sxs-lookup"><span data-stu-id="e8347-110">In either case, the debugger breaks execution when the invalid breakpoint is hit.</span></span>  
  
#### <a name="to-specify-a-condition"></a><span data-ttu-id="e8347-111">指定条件</span><span class="sxs-lookup"><span data-stu-id="e8347-111">To Specify a Condition</span></span>  
  
1.  <span data-ttu-id="e8347-112">在编辑器窗口中，右键单击断点符号，然后单击快捷菜单上的“条件”  。</span><span class="sxs-lookup"><span data-stu-id="e8347-112">In the editor window, right-click the breakpoint glyph, and then click **Condition** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="e8347-113">-或-</span><span class="sxs-lookup"><span data-stu-id="e8347-113">-or-</span></span>  
  
     <span data-ttu-id="e8347-114">在“断点”  窗口中，右键单击断点符号，然后单击快捷菜单上的“条件”  。</span><span class="sxs-lookup"><span data-stu-id="e8347-114">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Condition** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e8347-115">在 **“断点条件”** 对话框中，在 **“条件”** 框中输入一个有效的布尔表达式。</span><span class="sxs-lookup"><span data-stu-id="e8347-115">In the **Breakpoint Condition** dialog box, enter a valid Boolean expression in the **Condition** box.</span></span>  
  
3.  <span data-ttu-id="e8347-116">如果要在表达式的计算结果为时中断，则选择 "**为 true** `true` "; 如果要在表达式的值发生更改时中断，请选择 "**已更改**"。</span><span class="sxs-lookup"><span data-stu-id="e8347-116">Choose **Is true** if you want to break when the expression evaluates to `true`, or choose **Has changed** if you want to break when the value of the expression has changed.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e8347-117">在第一次到达断点之前，调试器不会计算布尔表达式。</span><span class="sxs-lookup"><span data-stu-id="e8347-117">The debugger does not evaluate the Boolean expression until the first time the breakpoint is reached.</span></span> <span data-ttu-id="e8347-118">如果选择 **“已更改”** ，则调试器不会将第一次计算视为一项更改，因此不会在第一次计算时中断。</span><span class="sxs-lookup"><span data-stu-id="e8347-118">If you choose **Has changed**, the debugger does not consider the first evaluation to be a change, so the debugger will not break on the first evaluation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8347-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8347-119">See Also</span></span>  
 <span data-ttu-id="e8347-120">[指定命中次数](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="e8347-120">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 [<span data-ttu-id="e8347-121">指定断点操作</span><span class="sxs-lookup"><span data-stu-id="e8347-121">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)  
