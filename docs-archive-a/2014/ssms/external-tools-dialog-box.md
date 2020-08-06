---
title: “外部工具”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- adding external tools
- external tools [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], external tools
ms.assetid: ba797203-24d0-4922-9b97-8ab483f1db14
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5789dc150e45c1a0364b7acc0ea7fda443efcf17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690318"
---
# <a name="external-tools-dialog-box"></a><span data-ttu-id="2add3-102">外部工具对话框</span><span class="sxs-lookup"><span data-stu-id="2add3-102">External Tools Dialog Box</span></span>
  <span data-ttu-id="2add3-103">使用“外部工具”  对话框可以将外部工具（如 SQLCMD 或记事本）添加到“工具”  菜单中。</span><span class="sxs-lookup"><span data-stu-id="2add3-103">Use the **External Tools** dialog box to add external tools such as SQLCMD or Notepad to the **Tools** menu.</span></span> <span data-ttu-id="2add3-104">通过添加外部工具，在 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 环境中工作时可以轻松启动其他应用程序。</span><span class="sxs-lookup"><span data-stu-id="2add3-104">Adding external tools allows you to easily launch other applications while working in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment.</span></span> <span data-ttu-id="2add3-105">启动此工具时，可以指定参数及工作目录。</span><span class="sxs-lookup"><span data-stu-id="2add3-105">You can specify arguments and a working directory when launching the tool.</span></span> <span data-ttu-id="2add3-106">此外，“输出”  窗口中可以显示某些工具的输出。</span><span class="sxs-lookup"><span data-stu-id="2add3-106">In addition, the output from some tools can be displayed in the **Output** window.</span></span> <span data-ttu-id="2add3-107">通过“工具”菜单可以打开“外部工具”对话框。</span><span class="sxs-lookup"><span data-stu-id="2add3-107">The **External Tools** dialog box is available on the **Tools** menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2add3-108">选项</span><span class="sxs-lookup"><span data-stu-id="2add3-108">Options</span></span>  
 <span data-ttu-id="2add3-109">**菜单内容**</span><span class="sxs-lookup"><span data-stu-id="2add3-109">**Menu contents**</span></span>  
 <span data-ttu-id="2add3-110">列出当前添加到“工具”  菜单上的菜单项标题。</span><span class="sxs-lookup"><span data-stu-id="2add3-110">Lists the titles of the items currently added to the **Tools** menu.</span></span> <span data-ttu-id="2add3-111">使用“上移”  和“下移”  箭头可以更改菜单项的显示顺序。</span><span class="sxs-lookup"><span data-stu-id="2add3-111">Use the **Move Up** and **Move Down** arrows to change the order the items that appear on the menu.</span></span> <span data-ttu-id="2add3-112">使用“删除”  按钮可以从菜单中删除菜单项。</span><span class="sxs-lookup"><span data-stu-id="2add3-112">Use the **Delete** button to remove an item from the menu.</span></span>  
  
 <span data-ttu-id="2add3-113">**上移**</span><span class="sxs-lookup"><span data-stu-id="2add3-113">**Move Up**</span></span>  
 <span data-ttu-id="2add3-114">将所选工具移动到工具列表（显示在“工具”  菜单上）中更靠上的位置。</span><span class="sxs-lookup"><span data-stu-id="2add3-114">Move the selected tool higher in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="2add3-115">**“下移”**</span><span class="sxs-lookup"><span data-stu-id="2add3-115">**Move Down**</span></span>  
 <span data-ttu-id="2add3-116">将所选工具移动到工具列表（显示在“工具”  菜单上）中更靠下的位置。</span><span class="sxs-lookup"><span data-stu-id="2add3-116">Move the selected tool lower in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="2add3-117">**添加**</span><span class="sxs-lookup"><span data-stu-id="2add3-117">**Add**</span></span>  
 <span data-ttu-id="2add3-118">清除相应的文本框以便指定新工具。</span><span class="sxs-lookup"><span data-stu-id="2add3-118">Clear the text boxes so you can specify a new tool.</span></span>  
  
 <span data-ttu-id="2add3-119">**删除**</span><span class="sxs-lookup"><span data-stu-id="2add3-119">**Delete**</span></span>  
 <span data-ttu-id="2add3-120">从“菜单内容”  列表以及“工具”  菜单中删除相应的工具或命令。</span><span class="sxs-lookup"><span data-stu-id="2add3-120">Remove the tool or command from the **Menu Contents** list as well as from the **Tools** menu.</span></span>  
  
 <span data-ttu-id="2add3-121">**标题**</span><span class="sxs-lookup"><span data-stu-id="2add3-121">**Title**</span></span>  
 <span data-ttu-id="2add3-122">输入的工具或命令的名称将显示在“工具”菜单的“外部工具”子菜单上。</span><span class="sxs-lookup"><span data-stu-id="2add3-122">Enter the name of the tool or command that will appear on the **External Tools** submenu of the **Tools** menu.</span></span> <span data-ttu-id="2add3-123">在工具名称中的一个字母前放置“与”符号 (&)，可以将该字母指定为工具的快捷键。</span><span class="sxs-lookup"><span data-stu-id="2add3-123">Place an ampersand (&) before a letter in the name of the tool to specify that letter as a keyboard shortcut.</span></span> <span data-ttu-id="2add3-124">例如，“&SQLCMD”会在“工具”  菜单上显示“SQLCMD”。</span><span class="sxs-lookup"><span data-stu-id="2add3-124">For example, "&SQLCMD" would display SQLCMD on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="2add3-125">**命令**</span><span class="sxs-lookup"><span data-stu-id="2add3-125">**Command**</span></span>  
 <span data-ttu-id="2add3-126">指定要启动的文件路径。</span><span class="sxs-lookup"><span data-stu-id="2add3-126">Specify the path to the file to launch.</span></span>  
  
 <span data-ttu-id="2add3-127">**参数**</span><span class="sxs-lookup"><span data-stu-id="2add3-127">**Arguments**</span></span>  
 <span data-ttu-id="2add3-128">指定在菜单上选择某个工具时传递到该工具的变量。</span><span class="sxs-lookup"><span data-stu-id="2add3-128">Specify the variables that are passed to the tool when the tool is selected on the menu.</span></span> <span data-ttu-id="2add3-129">参数可以指定启动工具或命令时传递给工具或命令的值。</span><span class="sxs-lookup"><span data-stu-id="2add3-129">Arguments can specify values that are passed to the tool or command when it is launched.</span></span> <span data-ttu-id="2add3-130">例如，参数值可以指定文件名或目录。</span><span class="sxs-lookup"><span data-stu-id="2add3-130">For example, a value can specify a file name or directory.</span></span> <span data-ttu-id="2add3-131">使用箭头按钮可以从预定义的参数列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="2add3-131">Use the arrow button to select from a list of predefined arguments.</span></span> <span data-ttu-id="2add3-132">您可以添加多个参数。</span><span class="sxs-lookup"><span data-stu-id="2add3-132">You can add more than one.</span></span> <span data-ttu-id="2add3-133">有关预定义参数及其定义的完整列表，请参阅 [外部工具的参数](menu-help/external-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="2add3-133">For a complete list of predefined arguments and their definitions, see [Arguments for External Tools](menu-help/external-tools.md).</span></span> <span data-ttu-id="2add3-134">还可以输入自定义参数（例如，命令行开关），这取决于所使用的命令或工具。</span><span class="sxs-lookup"><span data-stu-id="2add3-134">You can also enter custom arguments (for example, command line switches), depending on the command or tool you use.</span></span>  
  
 <span data-ttu-id="2add3-135">**使用输出窗口**</span><span class="sxs-lookup"><span data-stu-id="2add3-135">**Use Output window**</span></span>  
 <span data-ttu-id="2add3-136">打开 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 输出窗口显示正在运行命令的输出。</span><span class="sxs-lookup"><span data-stu-id="2add3-136">Opens the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Output window to display output of the command being run.</span></span> <span data-ttu-id="2add3-137">并非所有工具都以在输出窗口中显示的格式显示输出。</span><span class="sxs-lookup"><span data-stu-id="2add3-137">Not all tools present output in a format that can be presented in the Output window.</span></span> <span data-ttu-id="2add3-138">有关详细信息，请参阅 [输出窗口](../relational-databases/scripting/transact-sql-debugger-output-window.md)。</span><span class="sxs-lookup"><span data-stu-id="2add3-138">For more information, see [Output Window](../relational-databases/scripting/transact-sql-debugger-output-window.md).</span></span>  
  
 <span data-ttu-id="2add3-139">**将输出按 Unicode 处理**</span><span class="sxs-lookup"><span data-stu-id="2add3-139">**Treat output as Unicode**</span></span>  
 <span data-ttu-id="2add3-140">将输出解析为 Unicode。</span><span class="sxs-lookup"><span data-stu-id="2add3-140">Interprets the output as Unicode.</span></span>  
  
 <span data-ttu-id="2add3-141">**初始目录**</span><span class="sxs-lookup"><span data-stu-id="2add3-141">**Initial directory**</span></span>  
 <span data-ttu-id="2add3-142">指定工具的工作目录。</span><span class="sxs-lookup"><span data-stu-id="2add3-142">Specify the working directory of the tool.</span></span> <span data-ttu-id="2add3-143">使用箭头按钮可以选择目录。</span><span class="sxs-lookup"><span data-stu-id="2add3-143">Use the arrow button to select directories.</span></span> <span data-ttu-id="2add3-144">您可以选择多个目录。</span><span class="sxs-lookup"><span data-stu-id="2add3-144">You can select more than one.</span></span>  
  
 <span data-ttu-id="2add3-145">**提示输入参数**</span><span class="sxs-lookup"><span data-stu-id="2add3-145">**Prompt for arguments**</span></span>  
 <span data-ttu-id="2add3-146">显示“参数”  对话框，使用该对话框中可以在每次启动外部工具时输入或编辑参数的值。</span><span class="sxs-lookup"><span data-stu-id="2add3-146">Display the **Arguments** dialog box to allow you to enter or edit values for the arguments each time you launch the external tool.</span></span>  
  
 <span data-ttu-id="2add3-147">**退出时关闭**</span><span class="sxs-lookup"><span data-stu-id="2add3-147">**Close on exit**</span></span>  
 <span data-ttu-id="2add3-148">在关闭工具时，关闭由该工具打开的窗口。</span><span class="sxs-lookup"><span data-stu-id="2add3-148">Close the window opened by the tool when the tool is closed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2add3-149">示例</span><span class="sxs-lookup"><span data-stu-id="2add3-149">Example</span></span>  
 <span data-ttu-id="2add3-150">在“外部工具”  对话框中输入以下值将创建标有“DAC”的菜单项，将其选定，便可以使用专用管理员连接打开命令提示符并运行 **sqlcmd** 实用工具。</span><span class="sxs-lookup"><span data-stu-id="2add3-150">Entering the following values in the **External Tools** dialog box will create a menu item labeled "DAC" that when selected, opens a command prompt and runs the **sqlcmd** utility using the dedicated administrator connection.</span></span>  
  
|<span data-ttu-id="2add3-151">Box</span><span class="sxs-lookup"><span data-stu-id="2add3-151">Box</span></span>|<span data-ttu-id="2add3-152">值</span><span class="sxs-lookup"><span data-stu-id="2add3-152">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="2add3-153">**标题**</span><span class="sxs-lookup"><span data-stu-id="2add3-153">**Title**</span></span>|<span data-ttu-id="2add3-154">DAC</span><span class="sxs-lookup"><span data-stu-id="2add3-154">DAC</span></span>|  
|<span data-ttu-id="2add3-155">**命令**</span><span class="sxs-lookup"><span data-stu-id="2add3-155">**Command**</span></span>|[!INCLUDE[ssInstallPath](../includes/ssinstallpath-md.md)]<span data-ttu-id="2add3-156">Tools\Binn\SQLCMD.exe</span><span class="sxs-lookup"><span data-stu-id="2add3-156">Tools\Binn\SQLCMD.exe</span></span>|  
|<span data-ttu-id="2add3-157">**参数**</span><span class="sxs-lookup"><span data-stu-id="2add3-157">**Arguments**</span></span>|<span data-ttu-id="2add3-158">-A</span><span class="sxs-lookup"><span data-stu-id="2add3-158">-A</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2add3-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2add3-159">See Also</span></span>  
 <span data-ttu-id="2add3-160">[外部工具的参数](menu-help/external-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2add3-160">[Arguments for External Tools](menu-help/external-tools.md) </span></span>  
 [<span data-ttu-id="2add3-161">常规用户界面元素</span><span class="sxs-lookup"><span data-stu-id="2add3-161">General User Interface Elements</span></span>](general-user-interface-elements.md)  
  
  
