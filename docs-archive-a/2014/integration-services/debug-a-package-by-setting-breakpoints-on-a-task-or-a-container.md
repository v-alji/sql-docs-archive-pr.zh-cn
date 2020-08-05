---
title: 通过在任务或容器中设置断点来调试包 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], breakpoints
- breakpoints [Integration Services]
- tasks [Integration Services], breakpoints
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 21e334faff95e63e59bbf9c40fdf7e479de949da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578959"
---
# <a name="debug-a-package-by-setting-breakpoints-on-a-task-or-a-container"></a><span data-ttu-id="f1c63-102">通过在任务或容器上设置断点调试包</span><span class="sxs-lookup"><span data-stu-id="f1c63-102">Debug a Package by Setting Breakpoints on a Task or a Container</span></span>
  <span data-ttu-id="f1c63-103">本过程介绍如何在包、任务、For 循环容器、Foreach 循环容器或序列容器中设置断点。</span><span class="sxs-lookup"><span data-stu-id="f1c63-103">This procedure describes how to set breakpoints in a package, a task, a For Loop container, a Foreach Loop container, or a Sequence container.</span></span>  
  
### <a name="to-set-breakpoints-in-a-package-a-task-or-a-container"></a><span data-ttu-id="f1c63-104">在包、任务或容器中设置断点</span><span class="sxs-lookup"><span data-stu-id="f1c63-104">To set breakpoints in a package, a task, or a container</span></span>  
  
1.  <span data-ttu-id="f1c63-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="f1c63-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="f1c63-106">双击包含要在其中设置断点的包。</span><span class="sxs-lookup"><span data-stu-id="f1c63-106">Double-click the package in which you want to set breakpoints.</span></span>  
  
3.  <span data-ttu-id="f1c63-107">在 SSIS 设计器中，执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="f1c63-107">In SSIS Designer, do the following:</span></span>  
  
    -   <span data-ttu-id="f1c63-108">若要在包对象中设置断点，请单击“控制流”选项卡，将光标置于设计图面背景的任意位置，右键单击，再单击“编辑断点”   。</span><span class="sxs-lookup"><span data-stu-id="f1c63-108">To set breakpoints in the package object, click the **Control Flow** tab, place the cursor anywhere on the background of the design surface, right-click, and then click **Edit Breakpoints**.</span></span>  
  
    -   <span data-ttu-id="f1c63-109">若要在包控制流中设置断点，请单击“控制流”选项卡，右键单击任务、For 循环容器、Foreach 循环容器或序列容器，再单击“编辑断点”   。</span><span class="sxs-lookup"><span data-stu-id="f1c63-109">To set breakpoints in a package control flow, click the **Control Flow** tab, right-click a task, a For Loop container, a Foreach Loop container, or a Sequence container, and then click **Edit Breakpoints**.</span></span>  
  
    -   <span data-ttu-id="f1c63-110">若要在事件处理程序中设置断点，请单击“事件处理程序”选项卡，右键单击任务、For 循环容器、Foreach 循环容器或序列容器，再单击“编辑断点”   。</span><span class="sxs-lookup"><span data-stu-id="f1c63-110">To set breakpoints in an event handler, click the **Event Handler** tab, right-click a task, a For Loop container, a Foreach Loop container, or a Sequence container, and then click **Edit Breakpoints**.</span></span>  
  
4.  <span data-ttu-id="f1c63-111">在“设置断点 \<container name>”对话框中，选择要启用的断点。</span><span class="sxs-lookup"><span data-stu-id="f1c63-111">In the **Set Breakpoints \<container name>** dialog box, select the breakpoints to enable.</span></span>  
  
5.  <span data-ttu-id="f1c63-112">还可以修改每个断点的命中计数类型和命中计数数量。</span><span class="sxs-lookup"><span data-stu-id="f1c63-112">Optionally, modify the hit count type and the hit count number for each breakpoint.</span></span>  
  
6.  <span data-ttu-id="f1c63-113">若要保存包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="f1c63-113">To save the package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c63-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1c63-114">See Also</span></span>  
 <span data-ttu-id="f1c63-115">[包开发的故障排除工具](troubleshooting/troubleshooting-tools-for-package-development.md) </span><span class="sxs-lookup"><span data-stu-id="f1c63-115">[Troubleshooting Tools for Package Development](troubleshooting/troubleshooting-tools-for-package-development.md) </span></span>  
 <span data-ttu-id="f1c63-116">[通过在脚本任务和脚本组件中设置断点来调试脚本](data-flow/transformations/script-component.md) </span><span class="sxs-lookup"><span data-stu-id="f1c63-116">[Debug a Script by Setting Breakpoints in a Script Task and Script Component](data-flow/transformations/script-component.md) </span></span>  
 <span data-ttu-id="f1c63-117">[脚本任务的编码和调试](control-flow/script-task.md) </span><span class="sxs-lookup"><span data-stu-id="f1c63-117">[Coding and Debugging the Script Task](control-flow/script-task.md) </span></span>  
 [<span data-ttu-id="f1c63-118">脚本组件的编码和调试</span><span class="sxs-lookup"><span data-stu-id="f1c63-118">Coding and Debugging the Script Component</span></span>](extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  
