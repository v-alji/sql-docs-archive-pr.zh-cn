---
title: 调试脚本 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Script task [Integration Services], debugging
- debugging [Integration Services], scripts
- scripts [Integration Services], debugging
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7926f806f20f76c7aaac0c22b970addc5e93a78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691781"
---
# <a name="debugging-script"></a><span data-ttu-id="71be8-102">调试脚本</span><span class="sxs-lookup"><span data-stu-id="71be8-102">Debugging Script</span></span>
  <span data-ttu-id="71be8-103">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 中编写脚本任务和脚本组件所使用的脚本。</span><span class="sxs-lookup"><span data-stu-id="71be8-103">You write the scripts that the Script task and Script component use, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
 <span data-ttu-id="71be8-104">可在 VSTA 中设置断点并为断点编写脚本。</span><span class="sxs-lookup"><span data-stu-id="71be8-104">You set and script breakpoints in VSTA.</span></span> <span data-ttu-id="71be8-105">可以在 VSTA 中管理断点，但也可以使用 **设计器提供的** “设置断点” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 对话框来管理断点。</span><span class="sxs-lookup"><span data-stu-id="71be8-105">You can manage breakpoints in VSTA, but you can also manage the breakpoints using the **Set Breakpoints** dialog box that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides.</span></span> <span data-ttu-id="71be8-106">有关详细信息，请参阅 [Debugging Control Flow](debugging-control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="71be8-106">For more information, see [Debugging Control Flow](debugging-control-flow.md).</span></span>  
  
 <span data-ttu-id="71be8-107">**“设置断点”** 对话框包含脚本断点。</span><span class="sxs-lookup"><span data-stu-id="71be8-107">The **Set Breakpoints** dialog box includes the script breakpoints.</span></span> <span data-ttu-id="71be8-108">这些断点出现在断点列表的底部，并且显示出现断点的行号和函数名。</span><span class="sxs-lookup"><span data-stu-id="71be8-108">These breakpoints appear at the bottom of the breakpoint list, and display the line number and the name of the function in which the breakpoint appears.</span></span> <span data-ttu-id="71be8-109">可以从 **“设置断点”** 对话框中删除脚本断点。</span><span class="sxs-lookup"><span data-stu-id="71be8-109">You can delete a script breakpoint from the **Set Breakpoints** dialog box.</span></span>  
  
 <span data-ttu-id="71be8-110">在运行时，在脚本中的代码行上设置的断点与对包或对包中的任务和容器设置的断点集成在一起。</span><span class="sxs-lookup"><span data-stu-id="71be8-110">At run time, the breakpoints set on lines of code in script are integrated with the breakpoints set on the package or the tasks and containers in the package.</span></span> <span data-ttu-id="71be8-111">调试器可以从脚本中的断点运行到包、任务或容器上设置的断点，亦可反之。</span><span class="sxs-lookup"><span data-stu-id="71be8-111">The debugger can run from a breakpoint in the script to a breakpoint set on the package, task, or container, and vice versa.</span></span> <span data-ttu-id="71be8-112">例如，一个包可能有对中断条件设置的断点（当包接收到 **OnPreExecute** 和 **OnPostExecute** 事件时发生中断），同时又有对脚本行设置断点的脚本任务。</span><span class="sxs-lookup"><span data-stu-id="71be8-112">For example, a package might have breakpoints set on the break conditions that occur when the package receives the **OnPreExecute** and **OnPostExecute** events, and also have a Script task that has breakpoints on lines of its script.</span></span> <span data-ttu-id="71be8-113">在此方案中，该包可以在与 **OnPreExecute** 事件相关联的中断条件处挂起执行，运行到脚本中的断点，并最终运行到与 **OnPostExecute** 事件相关联的中断条件。</span><span class="sxs-lookup"><span data-stu-id="71be8-113">In this scenario, the package can suspend execution on the break condition associated with the **OnPreExecute** event, run to the breakpoints in the script, and finally run to the break condition associated with the **OnPostExecute** event.</span></span>  
  
 <span data-ttu-id="71be8-114">有关调试脚本任务和脚本组件的详细信息，请参阅 [Coding and Debugging the Script Task](../extending-packages-scripting/task/coding-and-debugging-the-script-task.md) 和 [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="71be8-114">For more information about debugging the Script task and Script component, see [Coding and Debugging the Script Task](../extending-packages-scripting/task/coding-and-debugging-the-script-task.md) and [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>  
  
### <a name="to-set-a-breakpoint-in-visual-studio-for-applications"></a><span data-ttu-id="71be8-115">在 Visual Studio for Applications 中设置断点</span><span class="sxs-lookup"><span data-stu-id="71be8-115">To set a breakpoint in Visual Studio for Applications</span></span>  
  
-   [<span data-ttu-id="71be8-116">通过在脚本任务和脚本组件中设置断点来调试脚本</span><span class="sxs-lookup"><span data-stu-id="71be8-116">Debug a Script by Setting Breakpoints in a Script Task and Script Component</span></span>](../extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="71be8-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71be8-117">See Also</span></span>  
 [<span data-ttu-id="71be8-118">包开发的疑难解答工具</span><span class="sxs-lookup"><span data-stu-id="71be8-118">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)  
  
  
