---
title: 指定断点操作
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint action
- Transact-SQL debugger, breakpoint when hit action
ms.assetid: f97f0097-6f51-40c1-b2e0-294a93ce1e1b
author: rothja
ms.author: jroth
ms.openlocfilehash: 57b3c445e738752400e716538e038349e04e7bd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587322"
---
# <a name="specify-a-breakpoint-action"></a><span data-ttu-id="b3b61-102">指定断点操作</span><span class="sxs-lookup"><span data-stu-id="b3b61-102">Specify a Breakpoint Action</span></span>
  <span data-ttu-id="b3b61-103">断点 **“命中条件”** 操作指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器针对某个断点执行的自定义任务。</span><span class="sxs-lookup"><span data-stu-id="b3b61-103">A breakpoint **When Hit** action specifies a custom task that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger performs for a breakpoint.</span></span> <span data-ttu-id="b3b61-104">如果达到指定的命中计数并满足所有指定的断点条件，则调试器将执行为断点指定的操作。</span><span class="sxs-lookup"><span data-stu-id="b3b61-104">If the specified hit count is reached and any specified breakpoint condition is satisfied, the debugger performs the action specified for the breakpoint.</span></span>  
  
##  <a name="action-considerations"></a><a name="BKMK_ActionConsiderations"></a> <span data-ttu-id="b3b61-105">操作注意事项</span><span class="sxs-lookup"><span data-stu-id="b3b61-105">Action Considerations</span></span>  
 <span data-ttu-id="b3b61-106">当命中计数和断点条件都得到满足时，断点的默认操作为中断执行。</span><span class="sxs-lookup"><span data-stu-id="b3b61-106">The default action for a breakpoint is to break execution when both the hit count and breakpoint condition have been satisfied.</span></span> <span data-ttu-id="b3b61-107">**调试器中** “命中条件” [!INCLUDE[tsql](../../includes/tsql-md.md)] 操作的主要用途是通过指定打印消息，将信息打印到调试器的 **“输出”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="b3b61-107">The primary use of a **When Hit** action in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger is to instead print information to the debugger **Output** window by specifying a print message.</span></span>  
  
 <span data-ttu-id="b3b61-108">打印消息在 **“打印消息”** 选项中指定并被指定为一个文本字符串，其中包含的表达式包括正在调试的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中的信息。</span><span class="sxs-lookup"><span data-stu-id="b3b61-108">A print message is specified in the **Print a Message** option, and is specified as a text string that includes expressions containing information from the [!INCLUDE[tsql](../../includes/tsql-md.md)] being debugged.</span></span> <span data-ttu-id="b3b61-109">表达式包括：</span><span class="sxs-lookup"><span data-stu-id="b3b61-109">Expressions include:</span></span>  
  
-   <span data-ttu-id="b3b61-110">包含在大括号 ({}) 中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表达式。</span><span class="sxs-lookup"><span data-stu-id="b3b61-110">A [!INCLUDE[tsql](../../includes/tsql-md.md)] expression contained in curly braces ({}).</span></span> <span data-ttu-id="b3b61-111">该表达式可以包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 变量、参数和内置函数。</span><span class="sxs-lookup"><span data-stu-id="b3b61-111">The expressions can include [!INCLUDE[tsql](../../includes/tsql-md.md)] variables, parameters, and built-in functions.</span></span> <span data-ttu-id="b3b61-112">示例包括 {@MyVariable}、{@NameParameter}、{@@SPID} 或 {SERVERPROPERTY(‘ProcessID’)}。</span><span class="sxs-lookup"><span data-stu-id="b3b61-112">Examples include {@MyVariable}, {@NameParameter}, {@@SPID}, or {SERVERPROPERTY('ProcessID')}.</span></span>  
  
-   <span data-ttu-id="b3b61-113">以下关键字之一：</span><span class="sxs-lookup"><span data-stu-id="b3b61-113">One of the following keywords:</span></span>  
  
    1.  <span data-ttu-id="b3b61-114">$ADDRESS 返回在其中设置断点的存储过程或用户定义函数的名称。</span><span class="sxs-lookup"><span data-stu-id="b3b61-114">$ADDRESS returns the name of the stored procedure or user-defined function where the breakpoint is set.</span></span> <span data-ttu-id="b3b61-115">如果在编辑器窗口中设置断点，$ADDRESS 将返回正在编辑的脚本文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b3b61-115">If the breakpoint is set in the editor window, $ADDRESS returns the name of the script file being edited.</span></span> <span data-ttu-id="b3b61-116">$ADDRESS 和 $FUNCTION 在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器中返回相同的信息。</span><span class="sxs-lookup"><span data-stu-id="b3b61-116">$ADDRESS and $FUNCTION return the same information in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span>  
  
    2.  <span data-ttu-id="b3b61-117">$CALLER 返回调用存储过程或函数的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码单元的名称。</span><span class="sxs-lookup"><span data-stu-id="b3b61-117">$CALLER returns the name of the unit of [!INCLUDE[tsql](../../includes/tsql-md.md)] code that called a stored procedure or function.</span></span> <span data-ttu-id="b3b61-118">如果断点在编辑器窗口中，$CALLER 返回 \<No caller available> 。</span><span class="sxs-lookup"><span data-stu-id="b3b61-118">If the breakpoint is in the editor window, $CALLER returns \<No caller available>.</span></span> <span data-ttu-id="b3b61-119">如果断点位于从编辑器窗口中的代码调用的存储过程或用户定义函数中，$CALLER 将返回正在编辑的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b3b61-119">If the breakpoint is in a stored procedure or user-defined function called from the code in the editor window, $CALLER returns the name of the file being edited.</span></span> <span data-ttu-id="b3b61-120">如果断点位于从其他存储过程或函数中调用的存储过程或用户定义函数中，$CALLER 将返回此调用过程或函数的名称。</span><span class="sxs-lookup"><span data-stu-id="b3b61-120">If the breakpoint is in a stored procedure or user-defined function called from another stored procedure or function, $CALLER returns the name of the calling procedure or function.</span></span>  
  
    3.  <span data-ttu-id="b3b61-121">$CALLSTACK 返回链中调用当前存储过程或用户定义函数的函数的调用堆栈。</span><span class="sxs-lookup"><span data-stu-id="b3b61-121">$CALLSTACK returns the call stack of functions in the chain that called the current stored procedure or user-defined function.</span></span> <span data-ttu-id="b3b61-122">如果在编辑器窗口中设置断点，$CALLSTACK 将返回正在编辑的脚本文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b3b61-122">If the breakpoint is in the editor window, $CALLSTACK returns the name of the script file being edited.</span></span>  
  
    4.  <span data-ttu-id="b3b61-123">$FUNCTION 返回在其中设置断点的存储过程或用户定义函数的名称。</span><span class="sxs-lookup"><span data-stu-id="b3b61-123">$FUNCTION returns the name of the stored procedure or user-defined function where the breakpoint is set.</span></span> <span data-ttu-id="b3b61-124">如果在编辑器窗口中设置断点，$FUNCTION 将返回正在编辑的脚本文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b3b61-124">If the breakpoint is set in the editor window, $FUNCTION returns the name of the script file being edited.</span></span>  
  
    5.  <span data-ttu-id="b3b61-125">$PID 和 $PNAME 返回正在运行数据库引擎实例（其中正在运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] ）的操作系统进程的 ID 和名称。</span><span class="sxs-lookup"><span data-stu-id="b3b61-125">$PID and $PNAME return the ID and name of the operating system process running the instance of the Database Engine where the [!INCLUDE[tsql](../../includes/tsql-md.md)] is running.</span></span> <span data-ttu-id="b3b61-126">$PID 返回与 SERVERPROPERTY(‘ProcessID’) 相同的 ID，但 $PID 是一个十六进制值，而 SERVERPROPERTY(‘ProcessID’) 是一个十进制值。</span><span class="sxs-lookup"><span data-stu-id="b3b61-126">$PID returns the same ID as SERVERPROPERTY('ProcessID'), except that $PID is a hexadecimal value while SERVERPROPERTY('ProcessID') is a decimal value.</span></span>  
  
    6.  <span data-ttu-id="b3b61-127">$TID 和 $TNAME 返回运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理的操作系统线程的 ID 和名称。</span><span class="sxs-lookup"><span data-stu-id="b3b61-127">$TID and $TNAME return the ID and name of the operating system thread running the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch.</span></span> <span data-ttu-id="b3b61-128">该线程是一个与运行数据库引擎实例的进程关联的线程。</span><span class="sxs-lookup"><span data-stu-id="b3b61-128">The thread is one associated with the process running the instance of the Database Engine.</span></span> <span data-ttu-id="b3b61-129">$TID 返回的值与 SELECT kpid FROM sys.sysprocesses WHERE spid = @@SPID 返回的值相同，不同的是 $TID 是一个十六进制值，而 kpid 是一个十进制值。</span><span class="sxs-lookup"><span data-stu-id="b3b61-129">$TID returns the same value as SELECT kpid FROM sys.sysprocesses WHERE spid = @@SPID, except that $TID is a hexadecimal value while kpid is a decimal value.</span></span>  
  
-   <span data-ttu-id="b3b61-130">还可以使用反斜杠字符 (\\) 作为转义字符，以允许在消息中使用大括号和反斜杠： \\{、 \\} 和 \\\\。</span><span class="sxs-lookup"><span data-stu-id="b3b61-130">You can also use the backslash character (\\) as an escape character to allow curly braces and backslashes in the message: \\{, \\}, and \\\\.</span></span>  
  
#### <a name="to-specify-a-when-hit-action"></a><span data-ttu-id="b3b61-131">指定命中条件操作</span><span class="sxs-lookup"><span data-stu-id="b3b61-131">To Specify a When Hit Action</span></span>  
  
1.  <span data-ttu-id="b3b61-132">在编辑器窗口中，右键单击断点符号，然后在快捷菜单上单击“命中条件”  。</span><span class="sxs-lookup"><span data-stu-id="b3b61-132">In the editor window, right-click the breakpoint glyph, and then click **When Hit** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="b3b61-133">-或-</span><span class="sxs-lookup"><span data-stu-id="b3b61-133">-or-</span></span>  
  
     <span data-ttu-id="b3b61-134">在“断点”  窗口中，右键单击断点符号，然后在快捷菜单上单击“命中条件”  。</span><span class="sxs-lookup"><span data-stu-id="b3b61-134">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **When hit** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="b3b61-135">在 **“当命中断点时”** 对话框中，选择您需要的行为：</span><span class="sxs-lookup"><span data-stu-id="b3b61-135">In the **When Breakpoint Is Hit** dialog box, select the behavior you want:</span></span>  
  
    1.  <span data-ttu-id="b3b61-136">选择 **“打印消息”** ，以便当命中断点时在调试器的输出窗口中打印消息。</span><span class="sxs-lookup"><span data-stu-id="b3b61-136">Select **Print a Message** to print a message in the debugger Output window when the breakpoint is hit.</span></span>  
  
    2.  <span data-ttu-id="b3b61-137">**“运行宏”** 选项不可用于 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器中而呈灰显状态。</span><span class="sxs-lookup"><span data-stu-id="b3b61-137">The **Run a Macro** option is not available from the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, and is greyed out.</span></span>  
  
    3.  <span data-ttu-id="b3b61-138">如果您不想暂停执行断点，请选择 **“继续执行”** 。</span><span class="sxs-lookup"><span data-stu-id="b3b61-138">Select **Continue execution** if you do not want the breakpoint to pause execution.</span></span> <span data-ttu-id="b3b61-139">仅当选择了 **“打印消息”** 选项时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="b3b61-139">This option is active only if you have selected the **Print a Message** option.</span></span>  
  
3.  <span data-ttu-id="b3b61-140">单击 **“确定”** 实施更改，或单击 **“取消”** 退出而不应用更改。</span><span class="sxs-lookup"><span data-stu-id="b3b61-140">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b61-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3b61-141">See Also</span></span>  
 <span data-ttu-id="b3b61-142">[指定断点条件](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="b3b61-142">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 [<span data-ttu-id="b3b61-143">指定命中计数</span><span class="sxs-lookup"><span data-stu-id="b3b61-143">Specify a Hit Count</span></span>](specify-a-hit-count.md)  
