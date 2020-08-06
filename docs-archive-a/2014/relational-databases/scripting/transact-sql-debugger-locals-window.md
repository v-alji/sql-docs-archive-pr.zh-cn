---
title: “局部变量”窗口
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f8f62eb69a50d7543af41dddb9c62c842d17151
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590701"
---
# <a name="locals-window"></a><span data-ttu-id="7fa80-102">“局部变量”窗口</span><span class="sxs-lookup"><span data-stu-id="7fa80-102">Locals Window</span></span>
  <span data-ttu-id="7fa80-103">**“局部变量”** 窗口显示有关 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器的当前作用域中局部表达式的信息。</span><span class="sxs-lookup"><span data-stu-id="7fa80-103">The **Locals** window displays information about the local expressions in the current scope of the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="7fa80-104">此作用域设定为在 **“调用堆栈”** 窗口中选择的当前调用堆栈帧。</span><span class="sxs-lookup"><span data-stu-id="7fa80-104">The scope is set to the current call stack frame that is selected in the **Call Stack** window.</span></span> <span data-ttu-id="7fa80-105">只有在调试模式下才可以显示局部表达式。</span><span class="sxs-lookup"><span data-stu-id="7fa80-105">You must be in debug mode to display the local expressions.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="7fa80-106">任务列表</span><span class="sxs-lookup"><span data-stu-id="7fa80-106">Task List</span></span>  
 <span data-ttu-id="7fa80-107">**访问“局部变量”窗口**</span><span class="sxs-lookup"><span data-stu-id="7fa80-107">**To access the Locals window**</span></span>  
  
-   <span data-ttu-id="7fa80-108">在 **“调试”** 菜单上单击 **“窗口”** ，然后单击 **“局部变量”** 。</span><span class="sxs-lookup"><span data-stu-id="7fa80-108">On the **Debug** menu, click **Windows**, and then click **Locals**.</span></span>  
  
 <span data-ttu-id="7fa80-109">**更改表达式的值**</span><span class="sxs-lookup"><span data-stu-id="7fa80-109">**To change the value of an expression**</span></span>  
  
-   <span data-ttu-id="7fa80-110">右键单击表达式，然后选择“编辑值”  。</span><span class="sxs-lookup"><span data-stu-id="7fa80-110">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="7fa80-111">列</span><span class="sxs-lookup"><span data-stu-id="7fa80-111">Columns</span></span>  
 <span data-ttu-id="7fa80-112">**名称**</span><span class="sxs-lookup"><span data-stu-id="7fa80-112">**Name**</span></span>  
 <span data-ttu-id="7fa80-113">局部表达式的名称。</span><span class="sxs-lookup"><span data-stu-id="7fa80-113">Is the name of the local expression.</span></span> <span data-ttu-id="7fa80-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器列出变量、参数以及名称以 @@ 开头的系统函数。</span><span class="sxs-lookup"><span data-stu-id="7fa80-114">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger lists variables, parameters, and the system functions that have names that start with @@.</span></span>  
  
 <span data-ttu-id="7fa80-115">**值**</span><span class="sxs-lookup"><span data-stu-id="7fa80-115">**Value**</span></span>  
 <span data-ttu-id="7fa80-116">显示当前向该局部表达式分配的值。</span><span class="sxs-lookup"><span data-stu-id="7fa80-116">Displays the value that is currently assigned to the local expression.</span></span> <span data-ttu-id="7fa80-117">如果尚未向该表达式分配任何值，则此列为空白。</span><span class="sxs-lookup"><span data-stu-id="7fa80-117">This column is blank when no value has been assigned to the expression.</span></span>  
  
 <span data-ttu-id="7fa80-118">如果表达式的长度超过了 **“值”** 列的宽度，则将指针移动到该表达式的 **“值”** 单元格上方可显示一条工具提示，指示该表达式的完整值。</span><span class="sxs-lookup"><span data-stu-id="7fa80-118">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="7fa80-119">**“值”** 单元格中的放大镜图标指示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器可视化工具可用。</span><span class="sxs-lookup"><span data-stu-id="7fa80-119">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="7fa80-120">在该列表中，可以指定 **“文本可视化工具”** 、 **“XML 可视化工具”** 或 **“HTML 可视化工具”** 。</span><span class="sxs-lookup"><span data-stu-id="7fa80-120">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="7fa80-121">若要启动调试器可视化工具，请单击此放大镜图标。</span><span class="sxs-lookup"><span data-stu-id="7fa80-121">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="7fa80-122">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器将打开一个对话框，该对话框以适合相应数据类型的格式显示这些数据。</span><span class="sxs-lookup"><span data-stu-id="7fa80-122">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog box that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="7fa80-123">类型 </span><span class="sxs-lookup"><span data-stu-id="7fa80-123">**Type**</span></span>  
 <span data-ttu-id="7fa80-124">显示表达式的数据类型。</span><span class="sxs-lookup"><span data-stu-id="7fa80-124">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa80-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7fa80-125">See Also</span></span>  
 <span data-ttu-id="7fa80-126">[Transact-SQL 调试器](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="7fa80-126">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="7fa80-127">[Transact-SQL 调试器信息](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="7fa80-127">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="7fa80-128">[“监视”窗口](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="7fa80-128">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="7fa80-129">[“调用堆栈”窗口](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="7fa80-129">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="7fa80-130">[“快速监视”对话框](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="7fa80-130">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 [<span data-ttu-id="7fa80-131">表达式 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7fa80-131">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
