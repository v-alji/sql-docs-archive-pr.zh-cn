---
title: SQL Server 实用工具) 托管实例详细信息 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 6e51b7bb-a733-4852-8c33-7f4dbdf931c2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f895f9978511ab7b2b40b3f161185a68a497b2eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692509"
---
# <a name="managed-instance-details-sql-server-utility"></a><span data-ttu-id="54c31-102">托管实例详细信息（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="54c31-102">Managed Instance Details (SQL Server Utility)</span></span>
  <span data-ttu-id="54c31-103">实用工具资源管理器的“托管实例”视图中的信息为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的单独实例提供使用率数据、CPU 使用率历史记录、文件级别的存储使用率详细信息，并且提供查看和更新策略阈值的能力。</span><span class="sxs-lookup"><span data-stu-id="54c31-103">Information in the Managed Instances view of Utility Explorer provides utilization data for individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], CPU utilization history, storage utilization details at the file level, and the ability to view and update policy thresholds.</span></span> <span data-ttu-id="54c31-104">对于计算机，可以在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例级别控制策略阈值；对于数据库文件和日志文件，可以在存储卷的级别控制策略阈值。</span><span class="sxs-lookup"><span data-stu-id="54c31-104">Policy thresholds can be controlled at the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance level, for a computer, for database files and log files, and at the level of storage volumes.</span></span> <span data-ttu-id="54c31-105">您还可以查看 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的各个托管实例的属性详细信息。</span><span class="sxs-lookup"><span data-stu-id="54c31-105">You can also view property details for individual managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="54c31-106">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="54c31-106">UI element list</span></span>  
 <span data-ttu-id="54c31-107">“列表”视图</span><span class="sxs-lookup"><span data-stu-id="54c31-107">List view</span></span>  
 <span data-ttu-id="54c31-108">顶部窗格中的列表视图可以显示行中按 ComputerName\InstanceName 列出的各 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的有关数据。</span><span class="sxs-lookup"><span data-stu-id="54c31-108">The list view in the top pane displays data about individual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] listed in rows by ComputerName\InstanceName.</span></span>  
  
 <span data-ttu-id="54c31-109">运行状态图标按使用率类别为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的各实例提供摘要状态：</span><span class="sxs-lookup"><span data-stu-id="54c31-109">Health state icons provide summary status for each instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by utilization category:</span></span>  
  
-   <span data-ttu-id="54c31-110">绿色的选中标记 - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - 没有违反资源使用策略的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 托管实例的数目。</span><span class="sxs-lookup"><span data-stu-id="54c31-110">Green check - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - Number of managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] which are not violating resource utilization policies.</span></span> <span data-ttu-id="54c31-111">资源得到很好地利用。</span><span class="sxs-lookup"><span data-stu-id="54c31-111">Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="54c31-112">绿色向下箭头 - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - 资源使用不足。</span><span class="sxs-lookup"><span data-stu-id="54c31-112">Green down arrow - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="54c31-113">红色向上箭头 - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - 资源使用过度。</span><span class="sxs-lookup"><span data-stu-id="54c31-113">Red up arrow - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="54c31-114">可以通过将列表视图中的列向左或向右拖动，更改这些列在列表视图中的顺序。</span><span class="sxs-lookup"><span data-stu-id="54c31-114">The sequence of columns in the list view can be changed by dragging them to the left or the right.</span></span> <span data-ttu-id="54c31-115">可通过右键单击列标题并选择或取消选择列，添加或删除列表视图中的列。</span><span class="sxs-lookup"><span data-stu-id="54c31-115">Columns in the list view can be added or deleted by right-clicking on the column headings and selecting or unselecting columns.</span></span> <span data-ttu-id="54c31-116">右键单击菜单还提供了排序选项。</span><span class="sxs-lookup"><span data-stu-id="54c31-116">The right-click menu also provides sort options.</span></span> <span data-ttu-id="54c31-117">还可以通过单击列名称的顶部激活排序。</span><span class="sxs-lookup"><span data-stu-id="54c31-117">Sorting can also be activated by clicking at the top of a column name.</span></span>  
  
 <span data-ttu-id="54c31-118">若要访问实用工具列表视图的筛选器选项，请右键单击实用工具资源管理器导航窗格中的“托管实例”节点，然后选择“筛选器”。</span><span class="sxs-lookup"><span data-stu-id="54c31-118">To access filter options for the Utility list view, right-click on the **Managed Instances** node in the Utility Explorer navigation pane, and select **Filter**.</span></span> <span data-ttu-id="54c31-119">在实现了筛选器设置后，实用工具资源管理器中的“托管实例”节点将标有“托管实例(已筛选)”。</span><span class="sxs-lookup"><span data-stu-id="54c31-119">After filter settings have been implemented, the **Managed Instances** node in Utility Explorer will be labeled **Managed Instances (filtered)**.</span></span> <span data-ttu-id="54c31-120">有关详细信息，请参阅[筛选设置（对象资源管理器和实用工具资源管理器）](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="54c31-120">For more information, see [Filter Settings &#40;Object Explorer and Utility Explorer&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).</span></span>  
  
 <span data-ttu-id="54c31-121">默认情况下，下面的列将显示与 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个托管实例有关的运行状态信息。</span><span class="sxs-lookup"><span data-stu-id="54c31-121">By default, the following columns display health state information about each managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="54c31-122">实例 CPU - 显示分配给此 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的处理器使用率的运行状态。</span><span class="sxs-lookup"><span data-stu-id="54c31-122">Instance CPU - Displays the health state of processor utilization allocated to this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54c31-123">根据为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的实例设置的 CPU 使用策略以及易失性资源评估策略的配置设置，确定此参数的运行状态。</span><span class="sxs-lookup"><span data-stu-id="54c31-123">The health state for this parameter is determined according to CPU utilization policy set for the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="54c31-124">有关详细信息，请参阅[减少 CPU 使用策略中的干扰（SQL Server 实用工具）](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="54c31-124">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="54c31-125">若要查看此 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的处理器使用率历史记录，或者查看或更改策略限制，请单击 **“CPU 使用率”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="54c31-125">To view the processor utilization history for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="54c31-126">计算机 CPU - 显示计算机处理器使用率的运行状态。</span><span class="sxs-lookup"><span data-stu-id="54c31-126">Computer CPU - Displays the health state of computer processor utilization.</span></span> <span data-ttu-id="54c31-127">根据为计算机设置的 CPU 使用策略以及易失性资源评估策略的配置设置，确定此参数的运行状态。</span><span class="sxs-lookup"><span data-stu-id="54c31-127">The health state for this parameter is determined according to CPU utilization policy set for the computer and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="54c31-128">有关详细信息，请参阅[减少 CPU 使用策略中的干扰（SQL Server 实用工具）](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="54c31-128">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="54c31-129">若要查看此 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的处理器使用率历史记录，或者查看或更改策略限制，请单击 **“CPU 使用率”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="54c31-129">To view the processor utilization history for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="54c31-130">文件空间 - 为属于所选 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的所有数据库显示文件空间使用率的运行状态的摘要。</span><span class="sxs-lookup"><span data-stu-id="54c31-130">File Space - Displays a summary of health states of file space utilization for all databases that belong to the selected instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54c31-131">如果任何数据库的运行状态为使用过度，则文件空间运行状态将在此列表视图中报告为使用过度。</span><span class="sxs-lookup"><span data-stu-id="54c31-131">If the health state of any database is overutilized, then the file space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="54c31-132">如果任何数据库的运行状态为使用不足，并且没有数据库被使用过度，则文件空间运行状态将在此列表视图中报告为使用不足。</span><span class="sxs-lookup"><span data-stu-id="54c31-132">If the health state of any database is underutilized, and no database is overutilized, then the file space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="54c31-133">否则，文件空间运行状态将在列表视图中报告为很好地利用。</span><span class="sxs-lookup"><span data-stu-id="54c31-133">Otherwise, the file space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="54c31-134">若要查看或更改策略限制，请单击 **“存储使用率”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="54c31-134">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="54c31-135">卷空间 - 为包含属于所选 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的数据库的所有卷显示卷空间使用率的运行状态的摘要。</span><span class="sxs-lookup"><span data-stu-id="54c31-135">Volume Space - Displays a summary of the health states of volume space utilization for all volumes that contain databases belonging to the selected instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54c31-136">如果任何卷的运行状态为使用过度，则卷运行状态将在此列表视图中报告为使用过度。</span><span class="sxs-lookup"><span data-stu-id="54c31-136">If the health state of any volume is overutilized, then the volume space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="54c31-137">如果任何卷的运行状态为使用不足，并且没有卷被使用过度，则卷空间运行状态将在此列表视图中报告为使用不足。</span><span class="sxs-lookup"><span data-stu-id="54c31-137">If the health state of any volume is underutilized, and no volume is overutilized, then the volume space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="54c31-138">否则，卷空间运行状态将在列表视图中报告为很好地利用。</span><span class="sxs-lookup"><span data-stu-id="54c31-138">Otherwise, the volume space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="54c31-139">若要查看或更改策略限制，请单击 **“存储使用率”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="54c31-139">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="54c31-140">策略类型 - 指示对于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的托管实例，“全局”默认策略或“覆盖”自定义策略是否有效。</span><span class="sxs-lookup"><span data-stu-id="54c31-140">Policy Type - Indicates whether "Global" default policies or "Override" custom policies are in effect for the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="54c31-141">可以在列表视图的列标题区域中使用右键单击菜单显示的其他列：</span><span class="sxs-lookup"><span data-stu-id="54c31-141">Other columns that can be displayed using the right-click menu in the column heading area of the list view:</span></span>  
  
-   <span data-ttu-id="54c31-142">处理器名称：</span><span class="sxs-lookup"><span data-stu-id="54c31-142">Processor Name:</span></span>  
  
-   <span data-ttu-id="54c31-143">处理器速度 (MHz)：</span><span class="sxs-lookup"><span data-stu-id="54c31-143">Processor Speed (MHz):</span></span>  
  
-   <span data-ttu-id="54c31-144">处理器计数：</span><span class="sxs-lookup"><span data-stu-id="54c31-144">Processor Count:</span></span>  
  
-   <span data-ttu-id="54c31-145">物理内存 (MB)：</span><span class="sxs-lookup"><span data-stu-id="54c31-145">Physical Memory (MB):</span></span>  
  
-   <span data-ttu-id="54c31-146">操作系统版本：</span><span class="sxs-lookup"><span data-stu-id="54c31-146">Operating System Version:</span></span>  
  
-   <span data-ttu-id="54c31-147">SQL Server 版本：</span><span class="sxs-lookup"><span data-stu-id="54c31-147">SQL Server Version:</span></span>  
  
-   <span data-ttu-id="54c31-148">SQL Server 发行版：</span><span class="sxs-lookup"><span data-stu-id="54c31-148">SQL Server Edition:</span></span>  
  
-   <span data-ttu-id="54c31-149">群集：（True 或 False）</span><span class="sxs-lookup"><span data-stu-id="54c31-149">Clustered: (True or False)</span></span>  
  
-   <span data-ttu-id="54c31-150">备份目录：</span><span class="sxs-lookup"><span data-stu-id="54c31-150">Backup Directory:</span></span>  
  
-   <span data-ttu-id="54c31-151">排序规则：</span><span class="sxs-lookup"><span data-stu-id="54c31-151">Collation:</span></span>  
  
-   <span data-ttu-id="54c31-152">区分大小写：（True 或 False）</span><span class="sxs-lookup"><span data-stu-id="54c31-152">Case Sensitive: (True or False)</span></span>  
  
-   <span data-ttu-id="54c31-153">Language：</span><span class="sxs-lookup"><span data-stu-id="54c31-153">Language:</span></span>  
  
-   <span data-ttu-id="54c31-154">上次报告的时间：此列使用 datetime 数据类型显示 UCP 本地日期和时间。</span><span class="sxs-lookup"><span data-stu-id="54c31-154">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="54c31-155">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主题。</span><span class="sxs-lookup"><span data-stu-id="54c31-155">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="54c31-156">在使用实用工具对象模型时，请注意 SSMS 使用 datetimeoffset 数据类型。</span><span class="sxs-lookup"><span data-stu-id="54c31-156">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="54c31-157">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主题。</span><span class="sxs-lookup"><span data-stu-id="54c31-157">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="54c31-158">“CPU 使用率”选项卡</span><span class="sxs-lookup"><span data-stu-id="54c31-158">CPU Utilization tab</span></span>  
 <span data-ttu-id="54c31-159">“CPU 使用率”选项卡为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例和计算机 CPU 使用率显示历史数据的并排图形。</span><span class="sxs-lookup"><span data-stu-id="54c31-159">The CPU utilization tab shows side-by-side graphs of historical data for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance and computer CPU utilization.</span></span>  
  
 <span data-ttu-id="54c31-160">该图形按照显示区域右侧的单选按钮中指定的间隔显示处理器使用率历史记录。</span><span class="sxs-lookup"><span data-stu-id="54c31-160">The graph displays the processor utilization history for the interval specified in the radio buttons on the right side of the display area.</span></span> <span data-ttu-id="54c31-161">若要更改显示间隔和刷新数据集，请从列表中选择一个单选按钮。</span><span class="sxs-lookup"><span data-stu-id="54c31-161">To change the display interval and refresh the data set, select a radio button from the list.</span></span>  
  
 <span data-ttu-id="54c31-162">间隔选项如下所示：</span><span class="sxs-lookup"><span data-stu-id="54c31-162">Interval options are as follows:</span></span>  
  
-   <span data-ttu-id="54c31-163">1 天，以 15 分钟间隔显示。</span><span class="sxs-lookup"><span data-stu-id="54c31-163">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="54c31-164">1 周，以 1 天间隔显示。</span><span class="sxs-lookup"><span data-stu-id="54c31-164">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="54c31-165">1 个月，以 1 周间隔显示。</span><span class="sxs-lookup"><span data-stu-id="54c31-165">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="54c31-166">1 年，以 1 个月间隔显示。</span><span class="sxs-lookup"><span data-stu-id="54c31-166">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="54c31-167">“存储使用率”选项卡</span><span class="sxs-lookup"><span data-stu-id="54c31-167">Storage Utilization tab</span></span>  
 <span data-ttu-id="54c31-168">“存储使用率”选项卡具有显示存储使用率详细信息的树视图。</span><span class="sxs-lookup"><span data-stu-id="54c31-168">The Storage Utilization tab has a tree view that displays storage utilization details.</span></span> <span data-ttu-id="54c31-169">请注意，时间数据使用 datetime 数据类型显示 UCP 本地日期和时间。</span><span class="sxs-lookup"><span data-stu-id="54c31-169">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="54c31-170">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主题。</span><span class="sxs-lookup"><span data-stu-id="54c31-170">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="54c31-171">在使用实用工具对象模型时，请注意 SSMS 使用 datetimeoffset 数据类型。</span><span class="sxs-lookup"><span data-stu-id="54c31-171">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="54c31-172">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主题。</span><span class="sxs-lookup"><span data-stu-id="54c31-172">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="54c31-173">显示可按数据库或按卷分组。</span><span class="sxs-lookup"><span data-stu-id="54c31-173">Display can be grouped by database or by volume.</span></span> <span data-ttu-id="54c31-174">若要使用数据库树视图，请在 **“文件分组依据:”** 选择中选择 **“数据库”** 单选按钮。</span><span class="sxs-lookup"><span data-stu-id="54c31-174">To use the database tree view, select the **Database** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="54c31-175">若要查看单独数据库文件的存储使用率状态，请单击树视图中数据库名称旁的加号。</span><span class="sxs-lookup"><span data-stu-id="54c31-175">To view storage utilization status for individual database files, click on the plus sign next to a database name in the tree view.</span></span> <span data-ttu-id="54c31-176">列出的数据库文件包括属于列表视图中所选 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的托管实例的所有系统数据库和用户数据库。</span><span class="sxs-lookup"><span data-stu-id="54c31-176">The database files listed include all system and user databases that belong to the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] you selected in the list view.</span></span>  
  
 <span data-ttu-id="54c31-177">树结构与存储层次结构相对应。</span><span class="sxs-lookup"><span data-stu-id="54c31-177">The tree structure corresponds to the storage hierarchy.</span></span> <span data-ttu-id="54c31-178">树视图中的根节点是数据库。</span><span class="sxs-lookup"><span data-stu-id="54c31-178">The root node in the tree view is the database.</span></span> <span data-ttu-id="54c31-179">树视图的下一个级别包含一个文件组节点或属于数据库的节点，以及属于数据库的日志的日志文件节点。</span><span class="sxs-lookup"><span data-stu-id="54c31-179">The next level of the tree view contains a filegroup node or nodes that belong to the database, and a log file node for the logs that belong to the database.</span></span> <span data-ttu-id="54c31-180">下一个级别包含属于文件组的数据文件。</span><span class="sxs-lookup"><span data-stu-id="54c31-180">The next level contains the data files that belong to the filegroup.</span></span>  
  
 <span data-ttu-id="54c31-181">存储使用率历史数据图形中显示的数据会根据树视图中选择的节点发生变化：</span><span class="sxs-lookup"><span data-stu-id="54c31-181">Data displayed in the graph of storage utilization history changes depending on the node selected in the tree view:</span></span>  
  
-   <span data-ttu-id="54c31-182">选择文件组节点以便显示由属于所选文件组的所有数据文件使用的文件空间图形。</span><span class="sxs-lookup"><span data-stu-id="54c31-182">Select the file group node to display a graph of file space used by all data files that belong to the selected file group.</span></span>  
  
-   <span data-ttu-id="54c31-183">选择日志文件节点以便显示由属于所选数据库的所有日志文件使用的文件空间图形。</span><span class="sxs-lookup"><span data-stu-id="54c31-183">Select the log file node to display a graph of file space used by all log files that belong to the selected database.</span></span>  
  
-   <span data-ttu-id="54c31-184">选择数据库节点以便显示一个图形，该图形添加由属于所选数据库的所有数据文件和所有日志文件使用的文件空间。</span><span class="sxs-lookup"><span data-stu-id="54c31-184">Select the database node to display a graph that adds file space used by all data files and all log files that belong to the selected database.</span></span>  
  
 <span data-ttu-id="54c31-185">运行状态图标为数据库文件、文件组和日志文件提供一目了然的状态：</span><span class="sxs-lookup"><span data-stu-id="54c31-185">Health state icons provide at-a-glance status for database files, filegroups, and log files:</span></span>  
  
 <span data-ttu-id="54c31-186">对于数据库：</span><span class="sxs-lookup"><span data-stu-id="54c31-186">For databases:</span></span>  
  
-   <span data-ttu-id="54c31-187">绿色的选中标记 - 所有文件组和日志文件的运行状态是既没有使用过度，也没有使用不足。</span><span class="sxs-lookup"><span data-stu-id="54c31-187">Green check - Health states of all filegroups and log files a neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="54c31-188">绿色向下箭头 - 至少一个文件组或日志文件的运行状态是使用不足，并且没有运行状态是使用过度。</span><span class="sxs-lookup"><span data-stu-id="54c31-188">Green down arrow - Health states of at least one filegroup or log file is underutilized, and no health states are overutilized.</span></span>  
  
-   <span data-ttu-id="54c31-189">红色向上箭头 - 至少一个文件组或日志文件的运行状态是使用过度。</span><span class="sxs-lookup"><span data-stu-id="54c31-189">Red up arrow - The health state of at least one filegroup or log file is overutilized.</span></span>  
  
 <span data-ttu-id="54c31-190">对于文件组和日志文件：</span><span class="sxs-lookup"><span data-stu-id="54c31-190">For filegroups and log files:</span></span>  
  
-   <span data-ttu-id="54c31-191">绿色的选中标记 - 文件组中所有文件的文件空间使用率是既没有使用过度，也没有使用不足。</span><span class="sxs-lookup"><span data-stu-id="54c31-191">Green check - File space utilization for all files in the filegroup are neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="54c31-192">绿色向下箭头 - 文件组中至少一个文件的文件空间使用率是使用不足，并且文件组中没有文件被使用过度。</span><span class="sxs-lookup"><span data-stu-id="54c31-192">Green down arrow - File space utilization for at least one file in the filegroup is underutilized, and no files in the filegroup are overutilized.</span></span>  
  
-   <span data-ttu-id="54c31-193">红色向上箭头 - 文件组中所有数据文件的文件空间使用率被使用过度。</span><span class="sxs-lookup"><span data-stu-id="54c31-193">Red up arrow - File space utilization for all data files in the filegroup are overutilized.</span></span>  
  
 <span data-ttu-id="54c31-194">若要按卷查看文件，请在 **“文件分组依据:”** 选择中选择 **“卷”** 单选按钮。</span><span class="sxs-lookup"><span data-stu-id="54c31-194">To view files by volume, select the **Volume** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="54c31-195">存储使用率历史记录图形显示存储卷上所有数据文件和所有日志文件使用的文件空间。</span><span class="sxs-lookup"><span data-stu-id="54c31-195">The graph of storage utilization history displays file space used by all data files and all log files on the storage volume.</span></span> <span data-ttu-id="54c31-196">展开树可以查看单独数据库数据文件和日志文件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="54c31-196">Expand the tree to view details for individual database data files and log files.</span></span>  
  
 <span data-ttu-id="54c31-197">状态图标用来为每个卷提供状态：</span><span class="sxs-lookup"><span data-stu-id="54c31-197">Status icons are used to provide status for each volume:</span></span>  
  
-   <span data-ttu-id="54c31-198">绿色的选中标记 - 资源被很好地利用。</span><span class="sxs-lookup"><span data-stu-id="54c31-198">Green check - Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="54c31-199">绿色向下箭头 - 资源使用不足。</span><span class="sxs-lookup"><span data-stu-id="54c31-199">Green down arrow - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="54c31-200">红色向上箭头 - 资源被使用过度。</span><span class="sxs-lookup"><span data-stu-id="54c31-200">Red up arrow - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="54c31-201">“存储使用率”选项卡上每个文件名旁边的仪表表示相对于文件的有效容量的文件所使用空间量。</span><span class="sxs-lookup"><span data-stu-id="54c31-201">The gauge next to each file name on the Storage Utilization tab represents the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="54c31-202">仪表旁边显示的百分比值是相对于文件的有效容量的文件所使用空间量的比率。</span><span class="sxs-lookup"><span data-stu-id="54c31-202">The percentage value displayed next to the gauge is the ratio of the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="54c31-203">工具提示提供的数据用于计算与有效容量相比每个卷和每个文件的百分比。</span><span class="sxs-lookup"><span data-stu-id="54c31-203">Tool tips provide data used to calculate percentages for each volume and each file compared to effective capacity.</span></span>  
  
 <span data-ttu-id="54c31-204">如果该文件未配置为自动增长，则有效容量是分配给该文件的空间量。</span><span class="sxs-lookup"><span data-stu-id="54c31-204">If the file is not configured to auto-grow, then the effective capacity is the amount of space allocated to the file.</span></span> <span data-ttu-id="54c31-205">如果该文件配置为自动增长，则有效容量是当前分配给该文件的空间量与目前卷上可用空间量之和。</span><span class="sxs-lookup"><span data-stu-id="54c31-205">If the file is configured to auto-grow, then the effective capacity is the sum of the amount of space currently allocated to the file and the amount of free space currently available on the volume.</span></span>  
  
 <span data-ttu-id="54c31-206">可为数据文件和日志文件配置存储使用率策略。</span><span class="sxs-lookup"><span data-stu-id="54c31-206">Storage utilization policies can be configured for data files and for log files.</span></span> <span data-ttu-id="54c31-207">若要查看或更改文件的存储使用率策略阈值，请单击“存储使用率”窗格底部的 **“文件策略”** 链接。</span><span class="sxs-lookup"><span data-stu-id="54c31-207">To view or change the storage utilization policy thresholds for files, click on the **File Policy** link at the bottom of the Storage Utilization pane.</span></span> <span data-ttu-id="54c31-208">若要查看或更改存储卷的存储使用率策略阈值，请单击“存储使用率”窗格底部的 **“卷策略”** 链接。</span><span class="sxs-lookup"><span data-stu-id="54c31-208">To view or change the storage utilization policy thresholds for a storage volume, click on the **Volume Policy** link at the bottom of the Storage Utilization pane.</span></span>  
  
 <span data-ttu-id="54c31-209">若要覆盖默认策略阈值，请单击单选按钮 **“覆盖默认策略”** ，指定上限和下限值，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="54c31-209">To override the default policy thresholds, click on the radio button to **Override the default policy**, specify values for the upper and lower limits, then click **OK**.</span></span>  
  
 <span data-ttu-id="54c31-210">有关更改违反策略容限的详细信息，请参阅[减少 CPU 使用策略中的干扰（SQL Server 实用工具）](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="54c31-210">For more information about changing the tolerance for policy violations, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="54c31-211">“属性详细信息”选项卡</span><span class="sxs-lookup"><span data-stu-id="54c31-211">Property Details tab</span></span>  
 <span data-ttu-id="54c31-212">为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例列出的属性详细信息包括以下类别：</span><span class="sxs-lookup"><span data-stu-id="54c31-212">Property details listed for instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] include the following categories:</span></span>  
  
-   <span data-ttu-id="54c31-213">处理器名称：</span><span class="sxs-lookup"><span data-stu-id="54c31-213">Processor Name:</span></span>  
  
-   <span data-ttu-id="54c31-214">处理器速度 (MHz)：</span><span class="sxs-lookup"><span data-stu-id="54c31-214">Processor Speed (MHz):</span></span>  
  
-   <span data-ttu-id="54c31-215">处理器计数：</span><span class="sxs-lookup"><span data-stu-id="54c31-215">Processor Count:</span></span>  
  
-   <span data-ttu-id="54c31-216">物理内存 (MB)：</span><span class="sxs-lookup"><span data-stu-id="54c31-216">Physical Memory (MB):</span></span>  
  
-   <span data-ttu-id="54c31-217">操作系统版本：</span><span class="sxs-lookup"><span data-stu-id="54c31-217">Operating System Version:</span></span>  
  
-   <span data-ttu-id="54c31-218">SQL Server 版本：</span><span class="sxs-lookup"><span data-stu-id="54c31-218">SQL Server Version:</span></span>  
  
-   <span data-ttu-id="54c31-219">SQL Server 发行版：</span><span class="sxs-lookup"><span data-stu-id="54c31-219">SQL Server Edition:</span></span>  
  
-   <span data-ttu-id="54c31-220">群集：（True 或 False）</span><span class="sxs-lookup"><span data-stu-id="54c31-220">Clustered: (True or False)</span></span>  
  
-   <span data-ttu-id="54c31-221">备份目录：</span><span class="sxs-lookup"><span data-stu-id="54c31-221">Backup Directory:</span></span>  
  
-   <span data-ttu-id="54c31-222">排序规则：</span><span class="sxs-lookup"><span data-stu-id="54c31-222">Collation:</span></span>  
  
-   <span data-ttu-id="54c31-223">区分大小写：（True 或 False）</span><span class="sxs-lookup"><span data-stu-id="54c31-223">Case Sensitive: (True or False)</span></span>  
  
-   <span data-ttu-id="54c31-224">Language：</span><span class="sxs-lookup"><span data-stu-id="54c31-224">Language:</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c31-225">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54c31-225">See Also</span></span>  
 <span data-ttu-id="54c31-226">[已部署的数据层应用程序详细信息（SQL Server 实用工具）](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="54c31-226">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="54c31-227">[实用工具仪表板 &#40;SQL Server 实用工具&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="54c31-227">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="54c31-228">[在 SQL Server 实用工具中监视 SQL Server 的实例](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="54c31-228">[Monitor Instances of SQL Server in the SQL Server Utility](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span></span>  
 <span data-ttu-id="54c31-229">[SQL Server 实用工具的功能和任务](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="54c31-229">[SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="54c31-230">SQL Server 实用工具故障排除</span><span class="sxs-lookup"><span data-stu-id="54c31-230">Troubleshoot the SQL Server Utility</span></span>](../../2014/database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
