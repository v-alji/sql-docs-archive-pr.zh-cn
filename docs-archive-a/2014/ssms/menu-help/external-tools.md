---
title: 外部工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- External Tools dialog box
ms.assetid: d7dae88f-0781-4162-96cd-d3a3a4d82035
author: stevestein
ms.author: sstein
ms.openlocfilehash: a39cd0d139e81c02a7d2a58fae4e74221be7f78e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689700"
---
# <a name="external-tools"></a><span data-ttu-id="a9e2d-102">外部工具</span><span class="sxs-lookup"><span data-stu-id="a9e2d-102">External Tools</span></span>
  <span data-ttu-id="a9e2d-103">使用此对话框可以将外部工具（如 SQL Server 配置管理器或记事本）添加到“工具”  菜单。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-103">Use this dialog box to add external tools, such as SQL Server Configuration Manager or Notepad, to the **Tools** menu.</span></span> <span data-ttu-id="a9e2d-104">通过添加外部工具，您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中工作的同时，便捷地启动其他应用程序。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-104">Adding external tools allows you to easily launch other applications while working in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a9e2d-105">启动此工具时，可以指定参数及工作目录。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-105">You can specify arguments and a working directory when launching the tool.</span></span> <span data-ttu-id="a9e2d-106">此外，可以在“输出”窗口中显示某些工具的输出。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-106">In addition, the outputs from some tools can be displayed in the Output window.</span></span> <span data-ttu-id="a9e2d-107">通过“工具”菜单可以打开“外部工具”对话框。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-107">The **External Tools** dialog box is available on the **Tools** menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a9e2d-108">选项</span><span class="sxs-lookup"><span data-stu-id="a9e2d-108">Options</span></span>  
 <span data-ttu-id="a9e2d-109">**菜单内容**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-109">**Menu Contents**</span></span>  
 <span data-ttu-id="a9e2d-110">列出当前添加到“工具”  菜单上的菜单项标题。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-110">Lists the titles of the items currently added to the **Tools** menu.</span></span> <span data-ttu-id="a9e2d-111">使用“上移”  和“下移”  箭头可以更改菜单项的显示顺序。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-111">Use the **Move Up** and **Move Down** arrows to change the order the items that appear on the menu.</span></span> <span data-ttu-id="a9e2d-112">使用“删除”  按钮可以从菜单中删除菜单项。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-112">Use the **Delete** button to remove an item from the menu.</span></span>  
  
 <span data-ttu-id="a9e2d-113">**上移**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-113">**Move Up**</span></span>  
 <span data-ttu-id="a9e2d-114">将所选工具移动到工具列表（显示在“工具”  菜单上）中更靠上的位置。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-114">Move the selected tool higher in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="a9e2d-115">**“下移”**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-115">**Move Down**</span></span>  
 <span data-ttu-id="a9e2d-116">将所选工具移动到工具列表（显示在“工具”  菜单上）中更靠下的位置。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-116">Move the selected tool lower in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="a9e2d-117">**添加**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-117">**Add**</span></span>  
 <span data-ttu-id="a9e2d-118">清除相应的文本框以便指定新工具。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-118">Clear the text boxes so you can specify a new tool.</span></span>  
  
 <span data-ttu-id="a9e2d-119">**删除**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-119">**Delete**</span></span>  
 <span data-ttu-id="a9e2d-120">从“菜单内容”  列表以及“工具”  菜单中删除相应的工具或命令。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-120">Remove the tool or command from the **Menu Contents** list as well as from the **Tools** menu.</span></span>  
  
 <span data-ttu-id="a9e2d-121">**标题**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-121">**Title**</span></span>  
 <span data-ttu-id="a9e2d-122">在“工具”菜单的“外部工具”子菜单上显示的工具或命令的名称。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-122">The name of the tool or command that will appear on the **External Tools** submenu of the **Tools** menu.</span></span> <span data-ttu-id="a9e2d-123">在工具名称中的一个字母前放置 &amp; 号可以将该字母用作工具的快捷键。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-123">Place an ampersand before a letter in the name of the tool to use that letter as an accelerator key for the tool.</span></span> <span data-ttu-id="a9e2d-124">例如，`&Spy++` 将在“工具”菜单上显示为 **Spy++**。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-124">For example, `&Spy++` would display **Spy++** on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="a9e2d-125">**命令**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-125">**Command**</span></span>  
 <span data-ttu-id="a9e2d-126">指定要启动的 .exe、.com、.pif、.bat、.cmd 或其他文件的路径。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-126">Specify the path to the .exe, .com, .pif, .bat, .cmd, or other file that you intend to launch.</span></span> <span data-ttu-id="a9e2d-127">如果选中“使用输出窗口”复选框，则可以在“输出”窗口中查看 `.bat`、`.com` 和其他文件的输出。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-127">The output from `.bat`, `.com`, and other files can be viewed in the Output window if you select the **Use output window** check box.</span></span>  
  
 <span data-ttu-id="a9e2d-128">**参数**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-128">**Arguments**</span></span>  
 <span data-ttu-id="a9e2d-129">指定在菜单上选择某个工具时传递到该工具的变量。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-129">Specify the variables that are passed to the tool when the tool is selected on the menu.</span></span> <span data-ttu-id="a9e2d-130">参数可以指定启动工具或命令时传递给工具或命令的值。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-130">Arguments can specify values that are passed to the tool or command when it is launched.</span></span> <span data-ttu-id="a9e2d-131">例如，参数值可以指定文件名或目录。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-131">For example, a value can specify a file name or directory.</span></span> <span data-ttu-id="a9e2d-132">使用“箭头”  按钮可以从预定义的参数列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-132">Use the **Arrow** button to select from a list of predefined arguments.</span></span> <span data-ttu-id="a9e2d-133">您可以添加多个参数。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-133">You can add more than one.</span></span> <span data-ttu-id="a9e2d-134">有关预定义参数及其定义的完整列表，请参阅 [外部工具的参数](external-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-134">For a complete list of predefined arguments and their definitions, see [Arguments for External Tools](external-tools.md).</span></span> <span data-ttu-id="a9e2d-135">根据所用命令或工具的不同，您还可以输入自定义参数（例如，命令提示符开关）。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-135">You can also enter custom arguments (command-prompt switches, for example), depending on the command or tool you use.</span></span>  
  
 <span data-ttu-id="a9e2d-136">**初始目录**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-136">**Initial directory**</span></span>  
 <span data-ttu-id="a9e2d-137">指定工具的工作目录。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-137">Specify the working directory of the tool.</span></span> <span data-ttu-id="a9e2d-138">使用“箭头”  按钮可以选择目录。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-138">Use the **Arrow** button to select directories.</span></span> <span data-ttu-id="a9e2d-139">您可以选择多个目录。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-139">You can select more than one.</span></span>  
  
 <span data-ttu-id="a9e2d-140">**使用输出窗口**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-140">**Use output Window**</span></span>  
 <span data-ttu-id="a9e2d-141">指定是否在“输出”窗口中显示工具的结果。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-141">Specify whether or not results from the tool are displayed in the Output window.</span></span> <span data-ttu-id="a9e2d-142">此选项仅对通常在命令提示符窗口中显示输出的文件（如 .bat 和 .com 文件）可用。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-142">This option is only available for files, such as .bat and .com files, that normally display output in the command prompt window.</span></span> <span data-ttu-id="a9e2d-143">如果启用此选项，则可以在您跟踪工具的进度时简化窗口管理。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-143">When enabled, this option eases window management when you are following the progress of a tool.</span></span>  
  
 <span data-ttu-id="a9e2d-144">**提示输入参数**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-144">**Prompt for arguments**</span></span>  
 <span data-ttu-id="a9e2d-145">显示“参数”  对话框，以便每次启动外部工具时都可以输入或编辑参数的值。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-145">Display the **Arguments** dialog box to enable you to enter or edit values for the arguments each time you launch the external tool.</span></span>  
  
 <span data-ttu-id="a9e2d-146">**将输出按 Unicode 处理**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-146">**Treat output as Unicode**</span></span>  
 <span data-ttu-id="a9e2d-147">允许“输出”窗口接受 Unicode。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-147">Allow the Output window to accept Unicode.</span></span>  
  
 <span data-ttu-id="a9e2d-148">**退出时关闭**</span><span class="sxs-lookup"><span data-stu-id="a9e2d-148">**Close On Exit**</span></span>  
 <span data-ttu-id="a9e2d-149">在关闭工具时，关闭由该工具打开的窗口。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-149">Close the window opened by the tool when the tool is closed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9e2d-150">示例</span><span class="sxs-lookup"><span data-stu-id="a9e2d-150">Example</span></span>  
  
#### <a name="to-add-sql-server-configuration-manager-to-the-tools-menu"></a><span data-ttu-id="a9e2d-151">向“工具”菜单添加 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="a9e2d-151">To add SQL Server Configuration Manager to the Tools menu</span></span>  
  
1.  <span data-ttu-id="a9e2d-152">在“工具”  菜单上，单击“外部工具”  。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-152">On the **Tools** menu, click **External Tools**.</span></span>  
  
2.  <span data-ttu-id="a9e2d-153">在“标题”  框中，键入“SQL Server 配置管理器”  。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-153">In the **Title** box, type **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="a9e2d-154">在 "**命令**" 框中，键入 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理控制台可执行文件的路径，例如`C:\WINNT\system32\mmc.exe`</span><span class="sxs-lookup"><span data-stu-id="a9e2d-154">In the **Command** box, type the path to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console executable, such as `C:\WINNT\system32\mmc.exe`</span></span>  
  
4.  <span data-ttu-id="a9e2d-155">在 "**参数**" 框中，键入 .msc 文件的路径，例如`"C:\WINNT\system32\SQLServerManager.msc"`</span><span class="sxs-lookup"><span data-stu-id="a9e2d-155">In the **Arguments** box, type the path to the .msc file, such as `"C:\WINNT\system32\SQLServerManager.msc"`</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9e2d-156">查看“开始”菜单上 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 快捷方式的属性，即可确认相应文件在计算机上的位置。</span><span class="sxs-lookup"><span data-stu-id="a9e2d-156">View the properties of the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] shortcut on the **Start** menu to confirm the location of the files on your computer.</span></span>  
