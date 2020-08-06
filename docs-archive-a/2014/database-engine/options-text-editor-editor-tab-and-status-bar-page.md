---
title: 选项 (文本编辑器：编辑器选项卡和状态栏页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.editorcontextsettings
- VS.ToolsOptionsPages.Text_Editor.EditorTabAndStatusBar
ms.assetid: e4815678-7885-4631-878f-c6a2b857ee05
author: rothja
ms.author: jroth
ms.openlocfilehash: 920b7d48b5f7a2472a521af21c8217b1adba486a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589872"
---
# <a name="options-text-editor-editor-tab-and-status-bar-page"></a><span data-ttu-id="22b2a-102">选项（“文本编辑器”:“编辑器”选项卡和“状态栏”页）</span><span class="sxs-lookup"><span data-stu-id="22b2a-102">Options (Text Editor: Editor Tab and Status Bar Page)</span></span>
  <span data-ttu-id="22b2a-103">在 **“编辑器选项卡和状态栏”** 页上，您可以自定义 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 查询编辑器显示的信息。</span><span class="sxs-lookup"><span data-stu-id="22b2a-103">The **Editor Tab and Status Bar Page** lets you customize the information displayed by the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Query Editors.</span></span> <span data-ttu-id="22b2a-104">您可以指定在“查询编辑器”窗口的选项卡和状态栏中显示的信息级别，以及状态栏是显示在编辑器窗口的顶部还是底部。</span><span class="sxs-lookup"><span data-stu-id="22b2a-104">You can specify the level of information displayed in the tab and status bar of the Query Editor window, and whether the status bar appears at the top or bottom of the editor window.</span></span>  
  
## <a name="option-settings-by-editor"></a><span data-ttu-id="22b2a-105">通过编辑器进行的选项设置</span><span class="sxs-lookup"><span data-stu-id="22b2a-105">Option Settings by Editor</span></span>  
 <span data-ttu-id="22b2a-106">编辑器选项卡和状态栏可用于所有 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 编辑器中，但具有不同的功能级别。</span><span class="sxs-lookup"><span data-stu-id="22b2a-106">The editor tab and the status bar are available in all of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, but have different levels of functionality.</span></span>  
  
 <span data-ttu-id="22b2a-107">数据库引擎查询编辑器可以连接到服务器组，在这种情况下，它会打开与服务器组中所有实例的连接，并可以同时在每个连接上运行相同查询。</span><span class="sxs-lookup"><span data-stu-id="22b2a-107">The Database Engine Query Editor can connect to a server group, in which case it opens connections to all the instances in the Server Group and can simultaneously run the same query on each connection.</span></span> <span data-ttu-id="22b2a-108">可以使用此对话框指定当连接到多个实例（而非一个实例）时状态栏具有不同的颜色。若要更改多服务器的结果选项，请使用[选项（查询结果/SQL Server/多服务器）](../../2014/database-engine/options-query-results-sql-server-multi-server.md)页。</span><span class="sxs-lookup"><span data-stu-id="22b2a-108">You can use this dialog to specify that the status bar has different colors when connected to multiple instances rather than one instance.To change the multi-server results options, use the [Options (Query Results/SQL Server/Multi-Server)](../../2014/database-engine/options-query-results-sql-server-multi-server.md) page.</span></span>  
  
## <a name="status-bar-content"></a><span data-ttu-id="22b2a-109">状态栏内容</span><span class="sxs-lookup"><span data-stu-id="22b2a-109">Status Bar Content</span></span>  
 <span data-ttu-id="22b2a-110">指定查询编辑器状态栏中显示的信息。</span><span class="sxs-lookup"><span data-stu-id="22b2a-110">Specifies the information that appears in the Query Editor status bar.</span></span>  
  
 <span data-ttu-id="22b2a-111">**显示执行时间**</span><span class="sxs-lookup"><span data-stu-id="22b2a-111">**Display execution time**</span></span>  
 <span data-ttu-id="22b2a-112">包括脚本执行时间。</span><span class="sxs-lookup"><span data-stu-id="22b2a-112">Includes the script execution time.</span></span> <span data-ttu-id="22b2a-113">其设置包括：</span><span class="sxs-lookup"><span data-stu-id="22b2a-113">The settings are as follows:</span></span>  
  
 <span data-ttu-id="22b2a-114">**无**</span><span class="sxs-lookup"><span data-stu-id="22b2a-114">**None**</span></span>  
 <span data-ttu-id="22b2a-115">状态栏不显示任何时间信息。</span><span class="sxs-lookup"><span data-stu-id="22b2a-115">The status bar displays no time information.</span></span>  
  
 <span data-ttu-id="22b2a-116">**End**</span><span class="sxs-lookup"><span data-stu-id="22b2a-116">**End**</span></span>  
 <span data-ttu-id="22b2a-117">当脚本正在运行时，状态栏显示当天的当前时间。</span><span class="sxs-lookup"><span data-stu-id="22b2a-117">The status bar displays the current time of day while the script is running.</span></span> <span data-ttu-id="22b2a-118">当脚本执行完毕时，屏幕将显示该脚本完成时这一天的时间。</span><span class="sxs-lookup"><span data-stu-id="22b2a-118">When the script completes, the display shows the time of day that the script completed.</span></span>  
  
 <span data-ttu-id="22b2a-119">**已用**</span><span class="sxs-lookup"><span data-stu-id="22b2a-119">**Elapsed**</span></span>  
 <span data-ttu-id="22b2a-120">状态栏显示脚本一直运行的时间长度。</span><span class="sxs-lookup"><span data-stu-id="22b2a-120">The status bar displays the length of time that the script has been running.</span></span> <span data-ttu-id="22b2a-121">当脚本执行完毕时，屏幕将显示运行脚本所花的时间。</span><span class="sxs-lookup"><span data-stu-id="22b2a-121">When the script completes, the display shows how much time was taken to run the script.</span></span>  
  
 <span data-ttu-id="22b2a-122">**包括数据库名称**</span><span class="sxs-lookup"><span data-stu-id="22b2a-122">**Include database name**</span></span>  
 <span data-ttu-id="22b2a-123">包含用于连接的当前数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="22b2a-123">Includes the name of the current database for the connection.</span></span> <span data-ttu-id="22b2a-124">当首次打开查询编辑器时，这是登录名默认登录的数据库。</span><span class="sxs-lookup"><span data-stu-id="22b2a-124">When the query editor is first opened, this is the default database for the login.</span></span> <span data-ttu-id="22b2a-125">之后，可以使用 Transact-SQL USE 语句来更改数据库上下文。</span><span class="sxs-lookup"><span data-stu-id="22b2a-125">The database context can later be changed by using the Transact-SQL USE statement.</span></span>  
  
 <span data-ttu-id="22b2a-126">**包括登录名**</span><span class="sxs-lookup"><span data-stu-id="22b2a-126">**Include login name**</span></span>  
 <span data-ttu-id="22b2a-127">包括登录名。</span><span class="sxs-lookup"><span data-stu-id="22b2a-127">Includes the login name.</span></span>  
  
 <span data-ttu-id="22b2a-128">**包括行计数**</span><span class="sxs-lookup"><span data-stu-id="22b2a-128">**Include row count**</span></span>  
 <span data-ttu-id="22b2a-129">包括当前正在执行的脚本已处理过的行的计数。</span><span class="sxs-lookup"><span data-stu-id="22b2a-129">Includes a count of the rows that have been processed by the script that is currently executing.</span></span>  
  
 <span data-ttu-id="22b2a-130">**包括服务器名称**</span><span class="sxs-lookup"><span data-stu-id="22b2a-130">**Include server name**</span></span>  
 <span data-ttu-id="22b2a-131">包括服务器名称。</span><span class="sxs-lookup"><span data-stu-id="22b2a-131">Includes the server name.</span></span> <span data-ttu-id="22b2a-132">对于本地连接，这是实例名称。</span><span class="sxs-lookup"><span data-stu-id="22b2a-132">For local connections, this is the instance name.</span></span> <span data-ttu-id="22b2a-133">对于远程连接，这是远程计算机名称和实例名。</span><span class="sxs-lookup"><span data-stu-id="22b2a-133">For remote connections, this is the remote computer name and instance name.</span></span>  
  
## <a name="status-bar-layout-and-colors"></a><span data-ttu-id="22b2a-134">状态栏布局和颜色</span><span class="sxs-lookup"><span data-stu-id="22b2a-134">Status Bar Layout and Colors</span></span>  
 <span data-ttu-id="22b2a-135">指定查询编辑器状态栏中项的颜色。</span><span class="sxs-lookup"><span data-stu-id="22b2a-135">Specifies the colors for items in the Query Editor status bar.</span></span>  
  
 <span data-ttu-id="22b2a-136">**组连接**</span><span class="sxs-lookup"><span data-stu-id="22b2a-136">**Group connections**</span></span>  
 <span data-ttu-id="22b2a-137">设置查询编辑器具有多个连接时状态栏的颜色。</span><span class="sxs-lookup"><span data-stu-id="22b2a-137">Set the color of the status bar when the Query Editor has more than one connection.</span></span>  
  
 <span data-ttu-id="22b2a-138">**单个服务器连接**</span><span class="sxs-lookup"><span data-stu-id="22b2a-138">**Single server connections**</span></span>  
 <span data-ttu-id="22b2a-139">设置查询编辑器具有一个连接时状态栏的颜色。</span><span class="sxs-lookup"><span data-stu-id="22b2a-139">Set the color of the status bar when the Query Editor has one connection.</span></span>  
  
 <span data-ttu-id="22b2a-140">**状态栏位置**</span><span class="sxs-lookup"><span data-stu-id="22b2a-140">**Status bar location**</span></span>  
 <span data-ttu-id="22b2a-141">指定状态栏的位置。</span><span class="sxs-lookup"><span data-stu-id="22b2a-141">Specifies the location of the status bar.</span></span> <span data-ttu-id="22b2a-142">其设置包括：</span><span class="sxs-lookup"><span data-stu-id="22b2a-142">The settings are as follows:</span></span>  
  
 <span data-ttu-id="22b2a-143">顶部</span><span class="sxs-lookup"><span data-stu-id="22b2a-143">**Top**</span></span>  
 <span data-ttu-id="22b2a-144">状态栏显示在查询编辑器窗口的顶部。</span><span class="sxs-lookup"><span data-stu-id="22b2a-144">The status bar appears at the top of the Query Editor window.</span></span>  
  
 <span data-ttu-id="22b2a-145">**底部**</span><span class="sxs-lookup"><span data-stu-id="22b2a-145">**Bottom**</span></span>  
 <span data-ttu-id="22b2a-146">状态栏显示在查询编辑器窗口的底部。</span><span class="sxs-lookup"><span data-stu-id="22b2a-146">The status bar appears at the bottom of the Query Editor window.</span></span>  
  
## <a name="tab-text"></a><span data-ttu-id="22b2a-147">选项卡文本</span><span class="sxs-lookup"><span data-stu-id="22b2a-147">Tab Text</span></span>  
 <span data-ttu-id="22b2a-148">指定查询编辑器窗口顶部的选项卡中显示的文本。</span><span class="sxs-lookup"><span data-stu-id="22b2a-148">Specifies the text that appears in the tab at the top of a Query Editor window.</span></span> <span data-ttu-id="22b2a-149">如果文本太长而无法显示，则可以在工具提示中查看完整字符串，当您将鼠标悬停在选项卡上将显示工具提示。</span><span class="sxs-lookup"><span data-stu-id="22b2a-149">If the text is too long to display, you can view the full string in a tooltip that is displayed if you hover over the tab.</span></span>  
  
 <span data-ttu-id="22b2a-150">**包括数据库名称**</span><span class="sxs-lookup"><span data-stu-id="22b2a-150">**Include database name**</span></span>  
 <span data-ttu-id="22b2a-151">包含用于连接的当前数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="22b2a-151">Includes the name of the current database for the connection.</span></span> <span data-ttu-id="22b2a-152">当首次打开查询编辑器时，这是登录名默认登录的数据库。</span><span class="sxs-lookup"><span data-stu-id="22b2a-152">When the query editor is first opened, this is the default database for the login.</span></span> <span data-ttu-id="22b2a-153">之后，可以使用 Transact-SQL USE 语句来更改数据库上下文。</span><span class="sxs-lookup"><span data-stu-id="22b2a-153">The database context can later be changed by using the Transact-SQL USE statement.</span></span>  
  
 <span data-ttu-id="22b2a-154">**包括文件名**</span><span class="sxs-lookup"><span data-stu-id="22b2a-154">**Include file name**</span></span>  
 <span data-ttu-id="22b2a-155">包含在其中存储脚本的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="22b2a-155">Includes the name of the file where the script is stored.</span></span>  
  
 <span data-ttu-id="22b2a-156">**包括文件夹名称**</span><span class="sxs-lookup"><span data-stu-id="22b2a-156">**Include folder name**</span></span>  
 <span data-ttu-id="22b2a-157">包含在其中存储脚本文件的文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="22b2a-157">Includes the path of the folder where the script file is stored.</span></span>  
  
 <span data-ttu-id="22b2a-158">**包括登录名**</span><span class="sxs-lookup"><span data-stu-id="22b2a-158">**Include login name**</span></span>  
 <span data-ttu-id="22b2a-159">包括登录名。</span><span class="sxs-lookup"><span data-stu-id="22b2a-159">Includes the login name.</span></span>  
  
 <span data-ttu-id="22b2a-160">**包括服务器名称**</span><span class="sxs-lookup"><span data-stu-id="22b2a-160">**Include server name**</span></span>  
 <span data-ttu-id="22b2a-161">包括服务器名称。</span><span class="sxs-lookup"><span data-stu-id="22b2a-161">Includes the server name.</span></span> <span data-ttu-id="22b2a-162">对于本地连接，这是实例名称。</span><span class="sxs-lookup"><span data-stu-id="22b2a-162">For local connections, this is the instance name.</span></span> <span data-ttu-id="22b2a-163">对于远程连接，这是远程计算机名称和实例名。</span><span class="sxs-lookup"><span data-stu-id="22b2a-163">For remote connections, this is the remote computer name and instance name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22b2a-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22b2a-164">See Also</span></span>  
 <span data-ttu-id="22b2a-165">[选项 &#40;环境： "字体和颜色" 页面&#41;](../ssms/menu-help/options-environment-fonts-and-colors-page.md) </span><span class="sxs-lookup"><span data-stu-id="22b2a-165">[Options &#40;Environment: Fonts and Colors Page&#41;](../ssms/menu-help/options-environment-fonts-and-colors-page.md) </span></span>  
 [<span data-ttu-id="22b2a-166">查询编辑器中的颜色编码</span><span class="sxs-lookup"><span data-stu-id="22b2a-166">Color Coding in Query Editors</span></span>](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  
