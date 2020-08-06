---
title: “对象资源管理器详细信息”窗格 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.summary.report.f1
- sql12.swb.summary.general.f1
helpviewer_keywords:
- object search [SQL Server], Object Explorer
- Object Explorer
- object search [SQL Server]
- searching objects [SQL Server]
ms.assetid: b963e3c2-dc9e-4d38-bd28-2e00fe9e0e47
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ec856ce01930683cf20683a418a658a5b877729
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693605"
---
# <a name="object-explorer-details-pane"></a><span data-ttu-id="12d0c-102">对象资源管理器详细信息窗格</span><span class="sxs-lookup"><span data-stu-id="12d0c-102">Object Explorer Details Pane</span></span>
  <span data-ttu-id="12d0c-103">对象资源管理器详细信息是 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的一个组件，它提供服务器中所有对象的表格视图，并显示一个用于管理这些对象的用户界面。</span><span class="sxs-lookup"><span data-stu-id="12d0c-103">Object Explorer Details, a component of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], provides a tabular view of all the objects in the server and presents a user interface to manage them.</span></span> <span data-ttu-id="12d0c-104">对象资源管理器的功能根据服务器的类型稍有不同，但一般都包括用于数据库的开发功能和用于所有服务器类型的管理功能。</span><span class="sxs-lookup"><span data-stu-id="12d0c-104">The capabilities of Object Explorer vary slightly depending on the type of server, but generally include the development features for databases and management features for all server types.</span></span>  
  
 <span data-ttu-id="12d0c-105">默认情况下，“对象资源管理器详细信息”窗格在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 是可见的。</span><span class="sxs-lookup"><span data-stu-id="12d0c-105">The Object Explorer Details pane is visible in the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] by default.</span></span> <span data-ttu-id="12d0c-106">如果看不到对象资源管理器，请在“视图”  菜单上单击“对象资源管理器详细信息”  或按 **F7**。</span><span class="sxs-lookup"><span data-stu-id="12d0c-106">If you cannot see Object Explorer, on the **View** menu, click **Object Explorer Details** or press **F7**.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="12d0c-107">显示的数据采用启动 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 时有效的 Microsoft Windows 的“区域和语言选项”的格式。</span><span class="sxs-lookup"><span data-stu-id="12d0c-107">presents dates formatted with the Microsoft Windows Regional and Language Options in effect when [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] was started.</span></span> <span data-ttu-id="12d0c-108">重新启动 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 可以反映更新的设置。</span><span class="sxs-lookup"><span data-stu-id="12d0c-108">Restart [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to reflect newer settings.</span></span>  
  
## <a name="object-explorer-details"></a><span data-ttu-id="12d0c-109">对象资源管理器详细信息</span><span class="sxs-lookup"><span data-stu-id="12d0c-109">Object Explorer Details</span></span>  
 <span data-ttu-id="12d0c-110">对象资源管理器详细信息可用于在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的文件夹和对象中导航。</span><span class="sxs-lookup"><span data-stu-id="12d0c-110">Object Explorer Details can be used to navigate through folders and objects on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="12d0c-111">在 32 位操作系统上, 对象资源管理器只能显示 64,000 个对象。</span><span class="sxs-lookup"><span data-stu-id="12d0c-111">On 32-bit operating systems, Object Explorer can only display 64,000 objects.</span></span> <span data-ttu-id="12d0c-112">必须选择某个图标才能访问其他对象。</span><span class="sxs-lookup"><span data-stu-id="12d0c-112">An icon must be selected to access additional objects.</span></span>  
  
 <span data-ttu-id="12d0c-113">对象资源管理器详细信息包括一个工具栏，其中包含下表中所述的图标。</span><span class="sxs-lookup"><span data-stu-id="12d0c-113">Object Explorer Details includes a toolbar which contains the icons described in the following table.</span></span> <span data-ttu-id="12d0c-114">只有适当的时候这些图标才可用。</span><span class="sxs-lookup"><span data-stu-id="12d0c-114">Icons are only available when appropriate.</span></span>  
  
|<span data-ttu-id="12d0c-115">图标</span><span class="sxs-lookup"><span data-stu-id="12d0c-115">Icon</span></span>|<span data-ttu-id="12d0c-116">操作</span><span class="sxs-lookup"><span data-stu-id="12d0c-116">Action</span></span>|  
|----------|------------|  
|<span data-ttu-id="12d0c-117">**返回**</span><span class="sxs-lookup"><span data-stu-id="12d0c-117">**Back**</span></span>|<span data-ttu-id="12d0c-118">移动到对象资源管理器详细信息中显示的前几个项。</span><span class="sxs-lookup"><span data-stu-id="12d0c-118">Moves to the previous items displayed in Object Explorer Details.</span></span> <span data-ttu-id="12d0c-119">如果以前的显示内容是搜索操作的结果，则重新运行搜索。</span><span class="sxs-lookup"><span data-stu-id="12d0c-119">Re-runs a search when the previous display is the result of a search operation.</span></span>|  
|<span data-ttu-id="12d0c-120">**前进**</span><span class="sxs-lookup"><span data-stu-id="12d0c-120">**Forward**</span></span>|<span data-ttu-id="12d0c-121">选择“后退”  操作后，移动到下一个屏幕。</span><span class="sxs-lookup"><span data-stu-id="12d0c-121">Moves to the next screen after a **Back** operation is selected.</span></span>|  
|<span data-ttu-id="12d0c-122">**Up**</span><span class="sxs-lookup"><span data-stu-id="12d0c-122">**Up**</span></span>|<span data-ttu-id="12d0c-123">转到父对象或父文件夹。</span><span class="sxs-lookup"><span data-stu-id="12d0c-123">Moves to the parent object or folder.</span></span>|  
|<span data-ttu-id="12d0c-124">**同步**</span><span class="sxs-lookup"><span data-stu-id="12d0c-124">**Synchronize**</span></span>|<span data-ttu-id="12d0c-125">将对象资源管理器的焦点设置为对象资源管理器详细信息中的选定对象。</span><span class="sxs-lookup"><span data-stu-id="12d0c-125">Sets the focus of Object Explorer to the selected object in Object Explorer Details.</span></span>|  
|<span data-ttu-id="12d0c-126">**筛选器**</span><span class="sxs-lookup"><span data-stu-id="12d0c-126">**Filter**</span></span>|<span data-ttu-id="12d0c-127">如果有，显示对象的可配置子集。</span><span class="sxs-lookup"><span data-stu-id="12d0c-127">When available, shows a configurable subset of objects.</span></span>|  
|<span data-ttu-id="12d0c-128">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="12d0c-128">**Refresh**</span></span>|<span data-ttu-id="12d0c-129">刷新对象资源管理器详细信息中的显示内容。</span><span class="sxs-lookup"><span data-stu-id="12d0c-129">Refreshes the display in Object Explorer Details.</span></span>|  
|<span data-ttu-id="12d0c-130">**搜索**</span><span class="sxs-lookup"><span data-stu-id="12d0c-130">**Search**</span></span>|<span data-ttu-id="12d0c-131">提供一个区域，用于输入某些数据库对象的搜索词。</span><span class="sxs-lookup"><span data-stu-id="12d0c-131">Provides an area to enter a search term for certain database objects.</span></span>|  
  
### <a name="column-header-selections"></a><span data-ttu-id="12d0c-132">列标题选择</span><span class="sxs-lookup"><span data-stu-id="12d0c-132">Column Header Selections</span></span>  
 <span data-ttu-id="12d0c-133">对象资源管理器详细信息具有可选择的列。</span><span class="sxs-lookup"><span data-stu-id="12d0c-133">Object Explorer Details has selectable columns.</span></span> <span data-ttu-id="12d0c-134">您可以右键单击任何列标题并选中希望显示的项。</span><span class="sxs-lookup"><span data-stu-id="12d0c-134">You can right-click in any column header and check the items that you want to display.</span></span> <span data-ttu-id="12d0c-135">您的选择将保留在您导航的不同对象上。</span><span class="sxs-lookup"><span data-stu-id="12d0c-135">Your selections will be persisted across the different objects you navigate through.</span></span> <span data-ttu-id="12d0c-136">当您退出并重新启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]时，会保留每个用户的选择。</span><span class="sxs-lookup"><span data-stu-id="12d0c-136">Selections for each user are retained when you leave and restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="12d0c-137">显示某些对象类型（如数据库）的所有列可能导致大型对象集的显示呈现略微减慢。</span><span class="sxs-lookup"><span data-stu-id="12d0c-137">Showing all columns for some object types (such as Databases) might slow the display rendering slightly for large sets of objects.</span></span>  
  
### <a name="sorting"></a><span data-ttu-id="12d0c-138">排序</span><span class="sxs-lookup"><span data-stu-id="12d0c-138">Sorting</span></span>  
 <span data-ttu-id="12d0c-139">单击列标题一次，可按该列进行排序。</span><span class="sxs-lookup"><span data-stu-id="12d0c-139">Clicking one time on a column header will sort by that column.</span></span> <span data-ttu-id="12d0c-140">再次单击同一个列标题，可按该列进行反向排序。</span><span class="sxs-lookup"><span data-stu-id="12d0c-140">Clicking again on the same header reverse-sorts by that column.</span></span> <span data-ttu-id="12d0c-141">对于对象和文件夹范围内的每个用户将保留排序选择，重新启动 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 时也会保留。</span><span class="sxs-lookup"><span data-stu-id="12d0c-141">Sort selections are maintained for each user across objects and folders, and on [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] restart.</span></span>  
  
### <a name="filtering"></a><span data-ttu-id="12d0c-142">Filtering</span><span class="sxs-lookup"><span data-stu-id="12d0c-142">Filtering</span></span>  
 <span data-ttu-id="12d0c-143">可以使用对象资源管理器详细信息工具栏上的“筛选器”  图标，筛选对象资源管理器详细信息中显示的某些对象列表。</span><span class="sxs-lookup"><span data-stu-id="12d0c-143">Certain lists of objects displayed in Object Explorer Detail can be filtered using the **Filter** icon on the Object Explorer Details toolbar.</span></span> <span data-ttu-id="12d0c-144">在可以进行筛选时，将启用该图标。</span><span class="sxs-lookup"><span data-stu-id="12d0c-144">The icon will be enabled when filtering is possible.</span></span>  
  
### <a name="details-pane"></a><span data-ttu-id="12d0c-145">“详细信息”窗格</span><span class="sxs-lookup"><span data-stu-id="12d0c-145">Details Pane</span></span>  
 <span data-ttu-id="12d0c-146">对象资源管理器详细信息的最底部区域包含一个窗格，用于显示所选对象的某些详细信息。</span><span class="sxs-lookup"><span data-stu-id="12d0c-146">The very bottom area of Object Explorer Details contains a panel that displays certain details of the selected object.</span></span> <span data-ttu-id="12d0c-147">如果选择多个对象，则只显示对象的计数。</span><span class="sxs-lookup"><span data-stu-id="12d0c-147">Multiple object selections show only the count of the objects.</span></span> <span data-ttu-id="12d0c-148">在该窗格中选择项后，单击“复制”  图标可将显示的文本复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="12d0c-148">When items are selected in the panel, click the **Copy** icon to copy the displayed text to the clipboard.</span></span>  
  
 <span data-ttu-id="12d0c-149">向下箭头键将所选内容移至列表中的下一项。</span><span class="sxs-lookup"><span data-stu-id="12d0c-149">The down arrow key moves the selection to the next item in the list.</span></span> <span data-ttu-id="12d0c-150">向上箭头键将所选内容移至列表中的上一项。</span><span class="sxs-lookup"><span data-stu-id="12d0c-150">The up arrow key moves the selection to the previous item in the list.</span></span> <span data-ttu-id="12d0c-151">按住箭头键将快速通过这些项。</span><span class="sxs-lookup"><span data-stu-id="12d0c-151">Holding the arrow key down will speed through the items.</span></span> <span data-ttu-id="12d0c-152">所选内容将停止在属性列表的底部或顶部。</span><span class="sxs-lookup"><span data-stu-id="12d0c-152">The selection stops at the bottom or top of the property list.</span></span>  
  
 <span data-ttu-id="12d0c-153">键入属性名称的第一个字符会将所选内容移到以该字符开头的下一属性。</span><span class="sxs-lookup"><span data-stu-id="12d0c-153">Typing the first character of a property name moves the selection to the next property that begins with that character.</span></span>  
  
 <span data-ttu-id="12d0c-154">当在多列中排列属性时，使用向左箭头键和向右箭头键可以移到相邻列。</span><span class="sxs-lookup"><span data-stu-id="12d0c-154">When properties are arranged in multiple columns, use the left arrow and right arrow keys to move to adjacent columns.</span></span>  
  
 <span data-ttu-id="12d0c-155">若要将属性值复制到剪贴板中，可以使用以下键盘组合键：</span><span class="sxs-lookup"><span data-stu-id="12d0c-155">To copy property values to the clipboard, use the following keyboard key combinations:</span></span>  
  
-   <span data-ttu-id="12d0c-156">Ctrl+C 将复制属性值。</span><span class="sxs-lookup"><span data-stu-id="12d0c-156">Ctrl+C copies the property value.</span></span>  
  
-   <span data-ttu-id="12d0c-157">Ctrl+Shift+C 复制属性名称和具有 Tab 分隔符的属性值。</span><span class="sxs-lookup"><span data-stu-id="12d0c-157">Ctrl+Shift+C copies the property name and the property value with a tab delimiter.</span></span>  
  
 <span data-ttu-id="12d0c-158">在“对象资源管理器详细信息”属性窗格中使用右键单击菜单可以将所有属性或者所有属性和名称复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="12d0c-158">Use the right-click menu in the Object Explorer Details property pane to copy all properties or all properties and names to the clipboard.</span></span>  
  
 <span data-ttu-id="12d0c-159">若要在字段宽度无法完全显示某一属性值时显示该属性值，请将属性指针停留在该值上或者将 UI 焦点设置于该属性值以便激活具有整个属性值的工具提示。</span><span class="sxs-lookup"><span data-stu-id="12d0c-159">To display a property value when the field width does not completely display a property value, hover the mouse cursor over the value or set UI focus on the property value to activate a tool tip with the entire property value.</span></span> <span data-ttu-id="12d0c-160">当用户以长属性值为焦点时，辅助功能屏幕阅读器将报告完整的属性值。</span><span class="sxs-lookup"><span data-stu-id="12d0c-160">Accessibility screen readers will report the full property value when the user focuses on the long property value.</span></span>  
  
 <span data-ttu-id="12d0c-161">如果属性窗格中属性的数目超过了在内容区域中适合的数目，一个滚动条将出现在属性窗格的右侧。</span><span class="sxs-lookup"><span data-stu-id="12d0c-161">If the number of properties in the property pane exceeds that which will fit in the content area, a scroll bar will appear on the right side of the property pane.</span></span> <span data-ttu-id="12d0c-162">使用滚动条可以调整内容区域中属性值的视图。</span><span class="sxs-lookup"><span data-stu-id="12d0c-162">Use the scroll bar to adjust the view of property values in the content area.</span></span>  
  
### <a name="multiple-object-selection"></a><span data-ttu-id="12d0c-163">多重对象选择</span><span class="sxs-lookup"><span data-stu-id="12d0c-163">Multiple Object Selection</span></span>  
 <span data-ttu-id="12d0c-164">对象资源管理器详细信息支持多重对象选择。</span><span class="sxs-lookup"><span data-stu-id="12d0c-164">Object Explorer Details supports multiple object selection.</span></span> <span data-ttu-id="12d0c-165">例如，如果在对象资源管理器中选择了表，则在“对象资源管理器详细信息”窗口中按住 **Ctrl** 键，即可选择多个表，右键单击这些表，然后选择“删除”  或“生成表脚本”  ，可立即对所有所选表执行操作。</span><span class="sxs-lookup"><span data-stu-id="12d0c-165">For example, if you select Tables in Object Explorer, then in the Object Explorer Details window if you hold down the **Ctrl** key, you can select several tables, right-click them, and then select **Delete** or **Script Table AS** to act on all the selected tables immediately.</span></span> <span data-ttu-id="12d0c-166">标准复制命令可将显示的文本复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="12d0c-166">The standard copy commands will copy the displayed text to the clipboard.</span></span>  
  
## <a name="sql-server-object-search"></a><span data-ttu-id="12d0c-167">SQL Server 对象搜索</span><span class="sxs-lookup"><span data-stu-id="12d0c-167">SQL Server Object Search</span></span>  
 <span data-ttu-id="12d0c-168">通配符</span><span class="sxs-lookup"><span data-stu-id="12d0c-168">Wildcards</span></span>  
  
-   <span data-ttu-id="12d0c-169">支持标准通配符字符。</span><span class="sxs-lookup"><span data-stu-id="12d0c-169">Standard wildcard characters are supported.</span></span> <span data-ttu-id="12d0c-170">例如，搜索 **dm_os%counters** 会返回 dm_os_memory_cache_counters 和 dm_os_performance_counters。</span><span class="sxs-lookup"><span data-stu-id="12d0c-170">For example, searching for **dm_os%counters** returns both dm_os_memory_cache_counters and dm_os_performance_counters.</span></span> <span data-ttu-id="12d0c-171">有关详细信息，请参阅[用通配符搜索文本](../../relational-databases/scripting/search-text-with-wildcards.md)。</span><span class="sxs-lookup"><span data-stu-id="12d0c-171">For more information, see [Search Text with Wildcards](../../relational-databases/scripting/search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="12d0c-172">搜索范围</span><span class="sxs-lookup"><span data-stu-id="12d0c-172">Search Scope</span></span>  
  
-   <span data-ttu-id="12d0c-173">每次搜索的范围是对象资源管理器树中的当前焦点。</span><span class="sxs-lookup"><span data-stu-id="12d0c-173">Each search is scoped to the current focus in the Object Explorer tree.</span></span> <span data-ttu-id="12d0c-174">例如，如果对象资源管理器焦点在一个数据库上，则搜索 **dm_os%counters** 会返回该数据库中的 dm_os_memory_cache_counters 和 dm_os_performance_counters。</span><span class="sxs-lookup"><span data-stu-id="12d0c-174">For example, if the Object Explorer focus is on a database, search for **dm_os%counters** returns dm_os_memory_cache_counters and dm_os_performance_counters in that database.</span></span> <span data-ttu-id="12d0c-175">如果对象资源管理器焦点在“数据库”节点上，则会搜索所有数据库，并返回动态视图的多个实例。</span><span class="sxs-lookup"><span data-stu-id="12d0c-175">If the Object Explorer focus is on the Databases node, all databases are searched and multiple instances of the dynamic views are returned.</span></span>  
  
 <span data-ttu-id="12d0c-176">大型集合</span><span class="sxs-lookup"><span data-stu-id="12d0c-176">Large Sets</span></span>  
  
-   <span data-ttu-id="12d0c-177">搜索大型对象集可能需要很长时间，并且会降低服务器性能。</span><span class="sxs-lookup"><span data-stu-id="12d0c-177">Searching large object sets can take a long time and slow server performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12d0c-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12d0c-178">See Also</span></span>  
 [<span data-ttu-id="12d0c-179">对象资源管理器</span><span class="sxs-lookup"><span data-stu-id="12d0c-179">Object Explorer</span></span>](object-explorer.md)  
  
  
