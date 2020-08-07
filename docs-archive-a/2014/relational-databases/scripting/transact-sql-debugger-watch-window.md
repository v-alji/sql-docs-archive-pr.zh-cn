---
title: “监视”窗口
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Watch Window [Transact-SQL]
ms.assetid: 23f3baa4-14c2-4262-92f7-3f43fcfa0436
author: rothja
ms.author: jroth
ms.openlocfilehash: c2a3db9b095902fcb5620af91fb86d80f773d606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588959"
---
# <a name="watch-window"></a><span data-ttu-id="c505e-102">“监视”窗口</span><span class="sxs-lookup"><span data-stu-id="c505e-102">Watch Window</span></span>
  <span data-ttu-id="c505e-103">**“监视”** 窗口显示有关所选表达式的信息。</span><span class="sxs-lookup"><span data-stu-id="c505e-103">The **Watch** window displays information about the expressions that you have selected.</span></span> <span data-ttu-id="c505e-104">最多可以有四个监视窗口： **“监视 1”** 、 **“监视 2”、“监视 3”** 和 **“监视 4”** 。</span><span class="sxs-lookup"><span data-stu-id="c505e-104">There can be up to four watch windows: **Watch 1**, **Watch 2, Watch 3**, and **Watch 4**.</span></span> <span data-ttu-id="c505e-105">这些表达式是在 **“调用堆栈”** 窗口中选择的当前调用堆栈帧范围内求值的。</span><span class="sxs-lookup"><span data-stu-id="c505e-105">The expressions are evaluated within the scope of the current call stack frame that is selected in the **Call Stack** window.</span></span> <span data-ttu-id="c505e-106">只有在调试模式下才可监视变量和表达式。</span><span class="sxs-lookup"><span data-stu-id="c505e-106">You must be in debug mode to watch variables and expressions.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="c505e-107">任务列表</span><span class="sxs-lookup"><span data-stu-id="c505e-107">Task List</span></span>  
 <span data-ttu-id="c505e-108">**访问“监视”窗口**</span><span class="sxs-lookup"><span data-stu-id="c505e-108">**To access the Watch windows**</span></span>  
  
-   <span data-ttu-id="c505e-109">在 **“调试”** 菜单上依次单击 **“窗口”** 、 **“监视”** ，然后再单击 **“监视 1”** 、 **“监视 2”、“监视 3”** 或 **“监视 4”** 。</span><span class="sxs-lookup"><span data-stu-id="c505e-109">On the **Debug** menu, click **Windows**, click **Watch**, and then click **Watch 1**, **Watch 2, Watch 3**, or **Watch 4**.</span></span>  
  
 <span data-ttu-id="c505e-110">**更改表达式的值**</span><span class="sxs-lookup"><span data-stu-id="c505e-110">**To change the value of an expression**</span></span>  
  
-   <span data-ttu-id="c505e-111">右键单击表达式，然后选择“编辑值”  。</span><span class="sxs-lookup"><span data-stu-id="c505e-111">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="c505e-112">列</span><span class="sxs-lookup"><span data-stu-id="c505e-112">Columns</span></span>  
 <span data-ttu-id="c505e-113">**名称**</span><span class="sxs-lookup"><span data-stu-id="c505e-113">**Name**</span></span>  
 <span data-ttu-id="c505e-114">是由 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器列出的表达式。</span><span class="sxs-lookup"><span data-stu-id="c505e-114">Are the expressions that are listed by the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="c505e-115">支持以下表达式：</span><span class="sxs-lookup"><span data-stu-id="c505e-115">The following expressions are supported:</span></span>  
  
-   <span data-ttu-id="c505e-116">变量。</span><span class="sxs-lookup"><span data-stu-id="c505e-116">Variables.</span></span>  
  
-   <span data-ttu-id="c505e-117">参数。</span><span class="sxs-lookup"><span data-stu-id="c505e-117">Parameters.</span></span>  
  
-   <span data-ttu-id="c505e-118">名称以 @@ 开头的系统函数。</span><span class="sxs-lookup"><span data-stu-id="c505e-118">System functions whose name starts with @@.</span></span>  
  
-   <span data-ttu-id="c505e-119">通过向一个或多个变量、参数或系统函数应用运算符而生成的表达式，如 @IntegerCounter + 1 或 FirstName + LastName。</span><span class="sxs-lookup"><span data-stu-id="c505e-119">Expressions built by applying operators to one or more variables, parameters, or system functions, such as @IntegerCounter + 1, or FirstName + LastName.</span></span>  
  
-   <span data-ttu-id="c505e-120">返回单个值的 Transact-SQL 语句，如 SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1。</span><span class="sxs-lookup"><span data-stu-id="c505e-120">Transact-SQL statements that return a single value, such as: SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
 <span data-ttu-id="c505e-121">**值**</span><span class="sxs-lookup"><span data-stu-id="c505e-121">**Value**</span></span>  
 <span data-ttu-id="c505e-122">显示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器对“名称”  中指定的表达式求值后所返回的值。</span><span class="sxs-lookup"><span data-stu-id="c505e-122">Displays the value that is returned after the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger evaluates the expression specified in **Name**.</span></span>  
  
 <span data-ttu-id="c505e-123">如果表达式的长度超过了 **“值”** 列的宽度，则将指针移动到该表达式的 **“值”** 单元格上方可显示一条工具提示，指示该表达式的完整值。</span><span class="sxs-lookup"><span data-stu-id="c505e-123">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="c505e-124">**“值”** 单元格中的放大镜图标指示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器可视化工具可用。</span><span class="sxs-lookup"><span data-stu-id="c505e-124">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="c505e-125">在该列表中，可以指定 **“文本可视化工具”** 、 **“XML 可视化工具”** 或 **“HTML 可视化工具”** 。</span><span class="sxs-lookup"><span data-stu-id="c505e-125">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="c505e-126">若要启动调试器可视化工具，请单击此放大镜图标。</span><span class="sxs-lookup"><span data-stu-id="c505e-126">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="c505e-127">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器将打开一个对话框，该对话框以适合相应数据类型的格式显示这些数据。</span><span class="sxs-lookup"><span data-stu-id="c505e-127">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="c505e-128">类型 </span><span class="sxs-lookup"><span data-stu-id="c505e-128">**Type**</span></span>  
 <span data-ttu-id="c505e-129">显示表达式的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c505e-129">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c505e-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c505e-130">See Also</span></span>  
 <span data-ttu-id="c505e-131">[Transact-SQL 调试器](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="c505e-131">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="c505e-132">[Transact-SQL 调试器信息](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="c505e-132">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="c505e-133">[“局部变量”窗口](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="c505e-133">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="c505e-134">[“调用堆栈”窗口](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="c505e-134">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="c505e-135">[“快速监视”对话框](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="c505e-135">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 [<span data-ttu-id="c505e-136">表达式 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c505e-136">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
