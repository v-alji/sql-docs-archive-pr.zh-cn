---
title: “快速监视”对话框
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.quickwatch
helpviewer_keywords:
- QuickWatch Dialog [Transact-SQL]
ms.assetid: d6bbb373-1452-41f2-bdc5-86ae689c3dc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 48e4bda558b75bec0c81815c90feff9d6500a803
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590699"
---
# <a name="quickwatch-dialog-box"></a><span data-ttu-id="a514b-102">“快速监视”对话框</span><span class="sxs-lookup"><span data-stu-id="a514b-102">QuickWatch Dialog Box</span></span>
  <span data-ttu-id="a514b-103">使用“快速监视”对话框可以在调试 **代码时快速查看一个** 表达式（例如变量或参数）的数据类型和值。 [!INCLUDE[tsql](../../includes/tsql-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a514b-103">Use the **QuickWatch** dialog box to quickly view the data type and value of one [!INCLUDE[tsql](../../includes/tsql-md.md)] expression, such as a variable or parameter, when you are debugging [!INCLUDE[tsql](../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="a514b-104">若要监视多个表达式，也可以将这些表达式添加到 **“监视”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="a514b-104">To watch multiple expressions, you can also add the expression to a **Watch** window.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="a514b-105">任务列表</span><span class="sxs-lookup"><span data-stu-id="a514b-105">Task List</span></span>  
 <span data-ttu-id="a514b-106">**访问“快速监视”对话框**</span><span class="sxs-lookup"><span data-stu-id="a514b-106">**To access the QuickWatch dialog box**</span></span>  
  
-   <span data-ttu-id="a514b-107">在 **“调试”** 菜单上，单击 **“快速监视”** 。</span><span class="sxs-lookup"><span data-stu-id="a514b-107">On the **Debug** menu, click **QuickWatch**.</span></span>  
  
 <span data-ttu-id="a514b-108">**查看有关表达式的信息**</span><span class="sxs-lookup"><span data-stu-id="a514b-108">**To view the information about an expression**</span></span>  
  
1.  <span data-ttu-id="a514b-109">在 **“表达式”** 列表框中，键入或选择所需的表达式。</span><span class="sxs-lookup"><span data-stu-id="a514b-109">In the **Expression** list box, type or select the expression that you want.</span></span> <span data-ttu-id="a514b-110">支持以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表达式：</span><span class="sxs-lookup"><span data-stu-id="a514b-110">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] expressions are supported:</span></span>  
  
    -   <span data-ttu-id="a514b-111">变量。</span><span class="sxs-lookup"><span data-stu-id="a514b-111">Variables.</span></span>  
  
    -   <span data-ttu-id="a514b-112">参数。</span><span class="sxs-lookup"><span data-stu-id="a514b-112">Parameters.</span></span>  
  
    -   <span data-ttu-id="a514b-113">名称以 @@ 开头的系统函数。</span><span class="sxs-lookup"><span data-stu-id="a514b-113">System functions whose name starts with @@.</span></span>  
  
    -   <span data-ttu-id="a514b-114">通过向一个或多个变量、参数或系统函数应用运算符而生成的表达式，如 @IntegerCounter + 1 或 FirstName + LastName。</span><span class="sxs-lookup"><span data-stu-id="a514b-114">Expressions built by applying operators to one or more variables, parameters, or system functions, such as @IntegerCounter + 1, or FirstName + LastName.</span></span>  
  
    -   <span data-ttu-id="a514b-115">返回单个值的 Transact-SQL 语句，如 SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1。</span><span class="sxs-lookup"><span data-stu-id="a514b-115">Transact-SQL statements that return a single value, such as: SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
2.  <span data-ttu-id="a514b-116">单击 **“重新计算”** 。</span><span class="sxs-lookup"><span data-stu-id="a514b-116">Click **Reevaluate**.</span></span>  
  
 <span data-ttu-id="a514b-117">**将“快速监视”表达式添加到“监视”窗口**</span><span class="sxs-lookup"><span data-stu-id="a514b-117">**To add the QuickWatch expression to a Watch window**</span></span>  
  
-   <span data-ttu-id="a514b-118">单击 **“添加监视”** 。</span><span class="sxs-lookup"><span data-stu-id="a514b-118">Click **Add Watch**.</span></span>  
  
 <span data-ttu-id="a514b-119">**更改“快速监视”表达式的值**</span><span class="sxs-lookup"><span data-stu-id="a514b-119">**To change the value of the QuickWatch expression**</span></span>  
  
-   <span data-ttu-id="a514b-120">右键单击表达式，然后选择“编辑值”  。</span><span class="sxs-lookup"><span data-stu-id="a514b-120">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a514b-121">选项</span><span class="sxs-lookup"><span data-stu-id="a514b-121">Options</span></span>  
 <span data-ttu-id="a514b-122">**表达式列表**</span><span class="sxs-lookup"><span data-stu-id="a514b-122">**Expression list**</span></span>  
 <span data-ttu-id="a514b-123">显示当前选定的表达式。</span><span class="sxs-lookup"><span data-stu-id="a514b-123">Displays the currently selected expression.</span></span> <span data-ttu-id="a514b-124">该下拉列表包含一组表达式，您可以从中选择要显示的表达式。</span><span class="sxs-lookup"><span data-stu-id="a514b-124">The drop-down list contains a set of expressions that you can select to display.</span></span> <span data-ttu-id="a514b-125">该列表中的表达式是在当前从 **“调用堆栈”** 窗口中选择的堆栈帧的范围内可用的表达式。</span><span class="sxs-lookup"><span data-stu-id="a514b-125">The expressions in the list are those available in the scope of the stack frame that is currently selected in the **Call Stack** window.</span></span> <span data-ttu-id="a514b-126">若要显示另一个表达式，可以输入该表达式或从列表中选择它。</span><span class="sxs-lookup"><span data-stu-id="a514b-126">To display a different expression, either enter the expression or select it from list.</span></span> <span data-ttu-id="a514b-127">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器支持的表达式有：变量、参数和名称以 @@ 开头的系统函数。</span><span class="sxs-lookup"><span data-stu-id="a514b-127">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger supports the following expressions: variables, parameters, and the system functions that have names that start with @@.</span></span>  
  
 <span data-ttu-id="a514b-128">**值网格**</span><span class="sxs-lookup"><span data-stu-id="a514b-128">**Value grid**</span></span>  
 <span data-ttu-id="a514b-129">显示当前所监视的表达式的属性。</span><span class="sxs-lookup"><span data-stu-id="a514b-129">Displays the properties of the expression that is currently being watched.</span></span>  
  
 <span data-ttu-id="a514b-130">**名称**</span><span class="sxs-lookup"><span data-stu-id="a514b-130">**Name**</span></span>  
 <span data-ttu-id="a514b-131">正在监视的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表达式。</span><span class="sxs-lookup"><span data-stu-id="a514b-131">Is the [!INCLUDE[tsql](../../includes/tsql-md.md)] expression being watched.</span></span>  
  
 <span data-ttu-id="a514b-132">**值**</span><span class="sxs-lookup"><span data-stu-id="a514b-132">**Value**</span></span>  
 <span data-ttu-id="a514b-133">显示当前向该表达式分配的值。</span><span class="sxs-lookup"><span data-stu-id="a514b-133">Displays the value that is currently assigned to the expression.</span></span> <span data-ttu-id="a514b-134">如果该表达式当前不具有任何值，则显示空白。</span><span class="sxs-lookup"><span data-stu-id="a514b-134">A blank is displayed when the expression currently has no value.</span></span>  
  
 <span data-ttu-id="a514b-135">如果表达式的长度超过了 **“值”** 列的宽度，则将指针移动到该表达式的 **“值”** 单元格上方可显示一条工具提示，指示该表达式的完整值。</span><span class="sxs-lookup"><span data-stu-id="a514b-135">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="a514b-136">**“值”** 单元格中的放大镜图标指示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器可视化工具可用。</span><span class="sxs-lookup"><span data-stu-id="a514b-136">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="a514b-137">在该列表中，可以指定 **“文本可视化工具”** 、 **“XML 可视化工具”** 或 **“HTML 可视化工具”** 。</span><span class="sxs-lookup"><span data-stu-id="a514b-137">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="a514b-138">若要启动调试器可视化工具，请单击此放大镜图标。</span><span class="sxs-lookup"><span data-stu-id="a514b-138">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="a514b-139">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器将打开一个对话框，该对话框以适合相应数据类型的格式显示这些数据。</span><span class="sxs-lookup"><span data-stu-id="a514b-139">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog box that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="a514b-140">类型 </span><span class="sxs-lookup"><span data-stu-id="a514b-140">**Type**</span></span>  
 <span data-ttu-id="a514b-141">显示表达式的数据类型。</span><span class="sxs-lookup"><span data-stu-id="a514b-141">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a514b-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a514b-142">See Also</span></span>  
 <span data-ttu-id="a514b-143">[Transact-SQL 调试器](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="a514b-143">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="a514b-144">[Transact-SQL 调试器信息](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="a514b-144">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="a514b-145">[“监视”窗口](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="a514b-145">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="a514b-146">[“局部变量”窗口](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="a514b-146">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="a514b-147">[“调用堆栈”窗口](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="a514b-147">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 [<span data-ttu-id="a514b-148">表达式 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a514b-148">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
  
  
