---
title: Transact-SQL 调试器信息
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, Locals Window
- Transact-SQL debugger, Watch Window
- Transact-SQL debugger, Threads Window
- Transact-SQL debugger, Call Stack Window
- Transact-SQL debugger, QuickWatch
- Transact-SQL debugger, viewing information
ms.assetid: b99819cc-f388-41a1-b304-36e78ce24147
author: rothja
ms.author: jroth
ms.openlocfilehash: c51ed39f0ed5f4ffb3e1a0c0dcb307f82d10bb10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693716"
---
# <a name="transact-sql-debugger-information"></a><span data-ttu-id="5ea5a-102">Transact-SQL 调试器信息</span><span class="sxs-lookup"><span data-stu-id="5ea5a-102">Transact-SQL Debugger Information</span></span>
  <span data-ttu-id="5ea5a-103">每次当调试器对特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句暂停执行时，您可以使用不同调试器窗口来查看当前执行状态。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-103">Every time that the debugger pauses execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, you can use the various debugger windows to view the current execution state.</span></span>  
  
## <a name="debugger-windows"></a><span data-ttu-id="5ea5a-104">调试器窗口</span><span class="sxs-lookup"><span data-stu-id="5ea5a-104">Debugger Windows</span></span>  
 <span data-ttu-id="5ea5a-105">在调试器模式下，调试器会在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 主窗口底部打开两个窗口。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-105">In debugger mode, the debugger opens two windows at the bottom of the main [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] window.</span></span> <span data-ttu-id="5ea5a-106">调试器在这两个窗口中显示其所有信息。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-106">The debugger displays all its information in these two windows.</span></span> <span data-ttu-id="5ea5a-107">每个调试器窗口都有选项卡，可选择这些选项卡以控制在窗口中显示哪些信息。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-107">Each of the debugger windows has tabs that you can select to control which set of information is displayed in the window.</span></span> <span data-ttu-id="5ea5a-108">左侧调试器窗口包含 **“局部变量”** 、 **“监视1”** 、 **“监视2”** 、 **“监视3”** 和 **“监视4”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-108">The left debugger window contains the **Locals**, **Watch1**, **Watch2**, **Watch3**, and **Watch4** tabs.</span></span> <span data-ttu-id="5ea5a-109">右侧调试器窗口包含 **“调用堆栈”** 、 **“线程”** 、 **“断点”** 、 **“命令窗口”** 和 **“输出”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-109">The right debugger window contains the **Call Stack**, **Threads**, **Breakpoints**, **Command Window**, and **Output** tabs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ea5a-110">以上说明适用于调试器窗口的默认位置。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-110">The previous descriptions apply to the default locations of the debugger windows.</span></span> <span data-ttu-id="5ea5a-111">可以拖动选项卡，将其从一个窗口移到另一个窗口，或者取消停靠选项卡以创建一个新窗口，可以将该窗口放在所需的任何地方。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-111">You can drag a tab to move it from one window to another, or you can undock a tab to create a new window that you can put wherever you want.</span></span>  
  
 <span data-ttu-id="5ea5a-112">默认情况下，并非所有选项卡或窗口都处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-112">By default, not all of these tabs or windows are active.</span></span> <span data-ttu-id="5ea5a-113">可以使用下列方法之一来打开特定窗口：</span><span class="sxs-lookup"><span data-stu-id="5ea5a-113">You can open a particular window by using either of the following ways:</span></span>  
  
-   <span data-ttu-id="5ea5a-114">在 **“调试”** 菜单上，单击 **“窗口”** ，然后选择所需窗口。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-114">On the **Debug** menu, click **Windows**, and then select the window you want.</span></span>  
  
-   <span data-ttu-id="5ea5a-115">在 **“调试”** 工具栏上，单击 **“断点”** ，然后选择所需窗口。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-115">On the **Debug** toolbar, click **Breakpoints**, and then select the window you want.</span></span>  
  
## <a name="transact-sql-expressions"></a><span data-ttu-id="5ea5a-116">Transact-SQL 表达式</span><span class="sxs-lookup"><span data-stu-id="5ea5a-116">Transact-SQL Expressions</span></span>  
 <span data-ttu-id="5ea5a-117">表达式是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 子句，其计算结果为单个标量值，例如变量或参数。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-117">Expressions are [!INCLUDE[tsql](../../includes/tsql-md.md)] clauses that evaluate to a single, scalar value, such as variables or parameters.</span></span> <span data-ttu-id="5ea5a-118">左侧的调试器窗口可以显示当前赋给表达式的数据值，这些值最多可在 5 个选项卡或窗口中显示： **“局部变量”、“监视1”** 、 **“监视2”** 、 **“监视3”** 和 **“监视4”** 。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-118">The left debugger window can display the data values that are currently assigned to expressions in up to five tabs or windows: **Locals, Watch1**, **Watch2**, **Watch3**, and **Watch4**.</span></span>  
  
 <span data-ttu-id="5ea5a-119">**“局部变量”** 窗口显示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器当前作用域中局部变量的信息。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-119">The **Locals** window displays information about the local variables in the current scope of the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="5ea5a-120">调试器在代码的不同部分运行时， **“局部变量”** 窗口中列出的表达式集也会发生变化。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-120">The set of expressions that are listed in the **Locals** window changes as the debugger runs through the different parts of the code.</span></span>  
  
 <span data-ttu-id="5ea5a-121">**“快速监视”** 和四个 **“监视”** 窗口中的表达式并不仅限于列出变量的标识符。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-121">The expressions in the **QuickWatch** and the four **Watch** windows are not limited to just listing the identifier of a variable.</span></span> <span data-ttu-id="5ea5a-122">您可以通过指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表达式计算出单个值（如向变量添加数字），或使用 SELECT 语句计算出单个值。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-122">You can specify a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression that evaluates to a single value, such as adding a number to a variable, or a SELECT statement that evaluates to a single value.</span></span> <span data-ttu-id="5ea5a-123">示例包括：</span><span class="sxs-lookup"><span data-stu-id="5ea5a-123">Examples include:</span></span>  
  
-   <span data-ttu-id="5ea5a-124">变量名称，如 @IntegerCounter。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-124">The name of a variable, such as @IntegerCounter.</span></span>  
  
-   <span data-ttu-id="5ea5a-125">变量的算术运算，如 @IntegerCounter + 1。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-125">An arithmetic operation on a variable, such as @IntegerCounter + 1.</span></span>  
  
-   <span data-ttu-id="5ea5a-126">两个字符变量的字符串运算，如 @FirstName + @LastName。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-126">A string operation on two character variables, such as @FirstName + @LastName.</span></span>  
  
-   <span data-ttu-id="5ea5a-127">返回单个值的 SELECT 语句，如 SELECT CharCol FROM MyTable WHERE PrimaryKey = 1。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-127">A SELECT statement that returns a single value, such as SELECT CharCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
 <span data-ttu-id="5ea5a-128">可以使用 **“快速监视”** 窗口查看 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表达式的值，然后将该表达式保存到 **“监视”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-128">You can use the **QuickWatch** window to view the value of a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression, and then save that expression to a **Watch** window.</span></span> <span data-ttu-id="5ea5a-129">若要在 **“快速监视”** 窗口中选择表达式，请在 **“表达式”** 框中选择或输入该表达式的名称。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-129">To select an expression in **QuickWatch**, either select or enter the name of the expression in the **Expression** box.</span></span>  
  
 <span data-ttu-id="5ea5a-130">四个 **“监视”** 窗口显示所选变量和表达式的信息。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-130">The four **Watch** windows display information about variables and expressions that you have selected.</span></span> <span data-ttu-id="5ea5a-131">在列表中添加或删除表达式之前， **“监视”** 窗口中列出表达式集的不会变化。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-131">The set of expressions that are listed in the **Watch** windows does not change until you either add or delete expressions from the list.</span></span>  
  
 <span data-ttu-id="5ea5a-132">若要将表达式添加到 **“监视”** 窗口，可在 **“快速监视”** 对话框中选择 **“添加监视”** ，或在 **“监视”** 窗口中空行的 **“名称”** 列中输入该表达式的名称。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-132">To add an expression to a **Watch** window, you can either select **Add Watch** in the **QuickWatch** dialog box, or enter the name of the expression in the **Name** column of an empty row in a **Watch** window.</span></span>  
  
 <span data-ttu-id="5ea5a-133">在“局部变量”  、“监视”  或“快速监视”  窗口中，右键单击行，然后选择“编辑值”  ，即可设置变量的数据值。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-133">You can set the data values for variables in the **Locals**, **Watch**, or **QuickWatch** windows by right-clicking the row and then selecting **Edit Value**.</span></span> <span data-ttu-id="5ea5a-134">**“局部变量”** 窗口、 **“监视”** 窗口和 **“快速监视”** 对话框中的 **“值”** 列都支持文本、XML 和 HTML 数据可视化程序。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-134">The **Value** columns in the **Locals** window, **Watch** window, and **QuickWatch** dialog box all support text, XML, and HTML data visualizers.</span></span> <span data-ttu-id="5ea5a-135">可视化程序由 **“值”** 列右侧的放大镜数据提示来表示。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-135">The visualizers are represented by a magnifying glass data tip on the right side end of the **Values** column.</span></span> <span data-ttu-id="5ea5a-136">在与数据类型匹配的显示结果中，可以使用可视化程序查看文本、XML 或 HTML 数据值，例如在浏览器窗口中查看 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-136">You can use the visualizers to view text, XML, or HTML data values in displays that match the data types, for example, viewing XML files in a browser window.</span></span>  
  
 <span data-ttu-id="5ea5a-137">在调试模式中，当您将鼠标指针移至某个标识符上方时，将弹出 **“快速信息”** ，显示表达式的名称及其当前值。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-137">In debug mode, when you move the mouse pointer over an identifier, a **Quick Info** pop up is displayed with the name of the expression and its current value.</span></span> <span data-ttu-id="5ea5a-138">有关详细信息，请参阅[快速信息 (IntelliSense)](quick-info-intellisense.md)。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-138">For more information, see [Quick Info &#40;IntelliSense&#41;](quick-info-intellisense.md).</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="5ea5a-139">断点</span><span class="sxs-lookup"><span data-stu-id="5ea5a-139">Breakpoints</span></span>  
 <span data-ttu-id="5ea5a-140">可以使用 **“断点”** 窗口来查看和管理当前设置的断点。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-140">You can use the **Breakpoints** window to view and manage the currently set breakpoints.</span></span> <span data-ttu-id="5ea5a-141">有关详细信息，请参阅 [逐句通过 Transact-SQL 代码](step-through-transact-sql-code.md)。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-141">For more information, see [Step Through Transact-SQL Code](step-through-transact-sql-code.md).</span></span>  
  
## <a name="call-stacks"></a><span data-ttu-id="5ea5a-142">调用堆栈</span><span class="sxs-lookup"><span data-stu-id="5ea5a-142">Call Stacks</span></span>  
 <span data-ttu-id="5ea5a-143">“调用堆栈”  窗口显示当前执行位置，以及关于执行如何从原始编辑器窗口开始，通过所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模块（函数、存储过程或触发器），到达当前执行位置的信息。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-143">The **Call Stack** window displays the current execution location, and information about how execution passed from the original editor window through any [!INCLUDE[tsql](../../includes/tsql-md.md)] modules (functions, stored procedures, or triggers) to reach the current execution location.</span></span> <span data-ttu-id="5ea5a-144">**“调用堆栈”** 窗口中的每一行称为一个堆栈帧，表示以下任何一项：</span><span class="sxs-lookup"><span data-stu-id="5ea5a-144">Each row in the **Call Stack** window is called a stack frame and represents any one of the following items:</span></span>  
  
-   <span data-ttu-id="5ea5a-145">当前的执行位置。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-145">The current execution location.</span></span>  
  
-   <span data-ttu-id="5ea5a-146">从一个模块对另一个模块的调用。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-146">A call from one module to another.</span></span>  
  
-   <span data-ttu-id="5ea5a-147">从编辑器窗口对 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模块的调用。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-147">A call from an editor window to a [!INCLUDE[tsql](../../includes/tsql-md.md)] module.</span></span>  
  
 <span data-ttu-id="5ea5a-148">堆栈的顺序与调用模块的顺序相反。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-148">The order of the stack is the reverse of that in which the modules were called.</span></span> <span data-ttu-id="5ea5a-149">当前执行位置在堆栈的顶部，原始调用则在底部。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-149">The current execution location is at the top of the stack and the original call at the bottom.</span></span> <span data-ttu-id="5ea5a-150">堆栈帧左侧空白处中的黄色箭头标识调试器暂停执行所在的帧。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-150">A yellow arrow on the left margin of the stack frame identifies the frame in which the debugger paused execution.</span></span>  
  
 <span data-ttu-id="5ea5a-151">**“名称”** 列记录以下信息：</span><span class="sxs-lookup"><span data-stu-id="5ea5a-151">The **Name** column records the following information:</span></span>  
  
-   <span data-ttu-id="5ea5a-152">包含调用了下一级的代码行的源模块。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-152">The source module that contains the line of code that called down to the next level.</span></span>  
  
-   <span data-ttu-id="5ea5a-153">调用了堆栈上下一个模块的代码行。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-153">The line of code that called the next module on the stack.</span></span>  
  
-   <span data-ttu-id="5ea5a-154">如果调用带参数的存储过程或函数，则还会列出所有参数的名称、数据类型和值。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-154">If the call went to a stored procedure or function that took parameters, the names, data types, and values of all the parameters are also listed.</span></span>  
  
 <span data-ttu-id="5ea5a-155">**“局部变量”** 、 **“监视”** 和 **“快速监视”** 窗口中的表达式都是针对当前堆栈帧求值的。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-155">The expressions in the **Locals**, **Watch**, and **QuickWatch** windows are evaluated for the current stack frame.</span></span> <span data-ttu-id="5ea5a-156">默认情况下，当前堆栈帧是堆栈中的顶帧，调试器在此处暂停执行。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-156">By default, the current stack frame is the top frame in the stack, where the debugger paused execution.</span></span> <span data-ttu-id="5ea5a-157">当指定其他堆栈帧作为当前帧时，则 **“局部变量”** 、 **“监视”** 和 **“快速监视”** 窗口中的表达式将针对新堆栈帧重新求值。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-157">When you specify another stack frame as the current frame, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated for the new stack frame.</span></span> <span data-ttu-id="5ea5a-158">可以通过双击帧，或者单击帧并选择“切换到帧”  来更改当前堆栈帧。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-158">You can change the current stack frame by either by double-clicking a frame or clicking a frame and selecting **Switch To Frame**.</span></span> <span data-ttu-id="5ea5a-159">此时， **“局部变量”** 、 **“监视”** 和 **“快速监视”** 窗口中的表达式将针对新帧重新求值。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-159">At that point, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated for the new frame.</span></span> <span data-ttu-id="5ea5a-160">只要当前堆栈帧不是堆栈中的顶帧，堆栈帧的左侧空白处就会有一个绿色箭头标识当前堆栈帧。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-160">Whenever the current stack frame is not the top frame in the stack, a green arrow on the left margin of the stack frame identifies the current stack frame.</span></span>  
  
 <span data-ttu-id="5ea5a-161">当你右键单击某个堆栈帧并选择“转到源代码”  时，该帧的代码会显示在“查询编辑器”窗口中。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-161">When you right-click a stack frame and select **Go To Source Code**, the code for that frame is displayed in a Query Editor window.</span></span> <span data-ttu-id="5ea5a-162">但是，该帧不会成为当前帧， **“局部变量”** 、 **“监视”** 和 **“快速监视”** 窗口中的内容也不会更改。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-162">However, that frame is not made the current frame, and the contents of the **Locals**, **Watch**, and **QuickWatch** windows are not changed.</span></span>  
  
## <a name="system-information-and-transact-sql-results"></a><span data-ttu-id="5ea5a-163">系统信息和 Transact-SQL 结果</span><span class="sxs-lookup"><span data-stu-id="5ea5a-163">System Information and Transact-SQL Results</span></span>  
 <span data-ttu-id="5ea5a-164">调试器在 **“输出”** 窗口中列出其状态和事件消息。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-164">The debugger lists its status and event messages in the **Output** window.</span></span> <span data-ttu-id="5ea5a-165">其中包括调试器何时附加到其他进程或调试器线程何时结束等信息。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-165">This includes information such as when the debugger attaches to other processes or when debugger threads end.</span></span>  
  
 <span data-ttu-id="5ea5a-166">处于调试模式下时， **“结果”** 和 **“消息”** 选项卡在查询编辑器中仍处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-166">While in debug mode, the **Results** and **Messages** tabs are still active in the Query Editor.</span></span> <span data-ttu-id="5ea5a-167">**“结果”** 选项卡继续显示调试会话过程中执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的结果集。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-167">The **Results** tab continues to display the result sets from the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are executed during a debugging session.</span></span> <span data-ttu-id="5ea5a-168">**“消息”** 选项卡继续显示系统消息，例如 *xx* 行受影响，以及 PRINT 和 RAISERROR 语句的输出。</span><span class="sxs-lookup"><span data-stu-id="5ea5a-168">The **Messages** tab continues to display system messages, such as *xx* Rows Affected and the output of PRINT and RAISERROR statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea5a-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ea5a-169">See Also</span></span>  
 <span data-ttu-id="5ea5a-170">[“局部变量”窗口](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="5ea5a-170">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="5ea5a-171">[“监视”窗口](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="5ea5a-171">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="5ea5a-172">[“快速监视”对话框](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="5ea5a-172">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 <span data-ttu-id="5ea5a-173">[“断点”窗口](transact-sql-debugger-breakpoints-window.md) </span><span class="sxs-lookup"><span data-stu-id="5ea5a-173">[Breakpoints Window](transact-sql-debugger-breakpoints-window.md) </span></span>  
 <span data-ttu-id="5ea5a-174">[“调用堆栈”窗口](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="5ea5a-174">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="5ea5a-175">[“线程”窗口](transact-sql-debugger-threads-window.md) </span><span class="sxs-lookup"><span data-stu-id="5ea5a-175">[Threads Window](transact-sql-debugger-threads-window.md) </span></span>  
 <span data-ttu-id="5ea5a-176">[输出窗口](transact-sql-debugger-output-window.md) </span><span class="sxs-lookup"><span data-stu-id="5ea5a-176">[Output Window](transact-sql-debugger-output-window.md) </span></span>  
 [<span data-ttu-id="5ea5a-177">Transact-SQL 调试器</span><span class="sxs-lookup"><span data-stu-id="5ea5a-177">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
  
  
