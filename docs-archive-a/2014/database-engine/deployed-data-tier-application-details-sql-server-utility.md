---
title: SQL Server 实用工具)  (已部署的数据层应用程序详细信息 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.UE.dac.details.F1
helpviewer_keywords:
- utility, management
- Utility
- SQL Server Utility [SQL Server]
- data-tier application [SQL Server], utility details
- Multi-server management [SQL Server]
ms.assetid: 79c41dd9-abcb-434e-9326-00a341d5c867
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 58d0933dcb7682210dde24c3c6d3a9a539d02b1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579757"
---
# <a name="deployed-data-tier-application-details-sql-server-utility"></a><span data-ttu-id="3936d-102">已部署的数据层应用程序详细信息（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="3936d-102">Deployed Data-tier Application Details (SQL Server Utility)</span></span>
  <span data-ttu-id="3936d-103">实用工具资源管理器的“已部署的数据层应用程序”视图中的信息为单独的数据层应用程序提供使用率数据、CPU 使用率历史数据、文件级别的存储使用率详细信息，并且提供查看和更新策略阈值的能力。</span><span class="sxs-lookup"><span data-stu-id="3936d-103">Information in the Deployed Data-tier Applications view of Utility Explorer provides utilization data for individual data-tier applications, CPU utilization history, storage utilization details at the file level, and the ability to view and update policy thresholds.</span></span> <span data-ttu-id="3936d-104">可以在数据层应用程序级别为 CPU 使用率以及数据库数据文件和日志文件控制策略阈值。</span><span class="sxs-lookup"><span data-stu-id="3936d-104">Policy thresholds can be controlled at the data-tier application level for CPU utilization and for database data files and log files.</span></span> <span data-ttu-id="3936d-105">您还可以查看各数据层应用程序的属性详细信息。</span><span class="sxs-lookup"><span data-stu-id="3936d-105">You can also view property details for individual data-tier applications.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="3936d-106">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="3936d-106">UI element list</span></span>  
 <span data-ttu-id="3936d-107">“列表”视图</span><span class="sxs-lookup"><span data-stu-id="3936d-107">List view</span></span>  
 <span data-ttu-id="3936d-108">顶部窗格中的列表视图显示与单独的数据层应用程序有关的数据。</span><span class="sxs-lookup"><span data-stu-id="3936d-108">The list view in the top pane displays data about individual data-tier applications.</span></span> <span data-ttu-id="3936d-109">运行状态图标按使用率类别为各数据层应用程序提供摘要状态：</span><span class="sxs-lookup"><span data-stu-id="3936d-109">Health state icons provide summary status for each data-tier application by utilization category:</span></span>  
  
-   <span data-ttu-id="3936d-110">绿色的选中标记 - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - 没有违反资源使用策略的数据层应用程序的数目。</span><span class="sxs-lookup"><span data-stu-id="3936d-110">Green check - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - Number of data-tier application which are not violating resource utilization policies.</span></span> <span data-ttu-id="3936d-111">资源得到很好地利用。</span><span class="sxs-lookup"><span data-stu-id="3936d-111">Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="3936d-112">绿色向下箭头 - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - 资源使用不足。</span><span class="sxs-lookup"><span data-stu-id="3936d-112">Green down arrow - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="3936d-113">红色向上箭头 - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - 资源使用过度。</span><span class="sxs-lookup"><span data-stu-id="3936d-113">Red up arrow - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="3936d-114">可以通过将列表视图中的列向左或向右拖动，更改这些列在列表视图中的顺序。</span><span class="sxs-lookup"><span data-stu-id="3936d-114">The sequence of columns in the list view can be changed by dragging them to the left or the right.</span></span> <span data-ttu-id="3936d-115">可通过右键单击列标题并选择或取消选择列，添加或删除列表视图中的列。</span><span class="sxs-lookup"><span data-stu-id="3936d-115">Columns in the list view can be added or deleted by right-clicking on the column headings and selecting or unselecting columns.</span></span> <span data-ttu-id="3936d-116">右键单击菜单还提供了排序选项。</span><span class="sxs-lookup"><span data-stu-id="3936d-116">The right-click menu also provides sort options.</span></span> <span data-ttu-id="3936d-117">还可以通过单击列名称的顶部激活排序。</span><span class="sxs-lookup"><span data-stu-id="3936d-117">Sorting can also be activated by clicking at the top of a column name.</span></span>  
  
 <span data-ttu-id="3936d-118">若要访问 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具列表视图的筛选器选项，请右键单击实用工具资源管理器导航窗格中的“已部署的数据层应用程序”节点，然后选择“筛选器”。</span><span class="sxs-lookup"><span data-stu-id="3936d-118">To access filter options for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility list view, right-click on the **Deployed Data-tier applications** node in the Utility Explorer navigation pane, and select **Filter**.</span></span> <span data-ttu-id="3936d-119">实现筛选设置后，实用工具资源管理器中的“已部署的数据层应用程序”节点将标记为“已部署的数据层应用程序 (已筛选)”。</span><span class="sxs-lookup"><span data-stu-id="3936d-119">After filter settings have been implemented, the **Deployed Data-tier Applications** node in Utility Explorer will be labeled **Deployed Data-tier Applications (filtered)**.</span></span> <span data-ttu-id="3936d-120">有关详细信息，请参阅[筛选设置（对象资源管理器和实用工具资源管理器）](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="3936d-120">For more information, see [Filter Settings &#40;Object Explorer and Utility Explorer&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).</span></span>  
  
 <span data-ttu-id="3936d-121">默认情况下，下面的列将显示与每个数据层应用程序有关的运行状态信息。</span><span class="sxs-lookup"><span data-stu-id="3936d-121">By default, the following columns display health state information about each data-tier application.</span></span>  
  
-   <span data-ttu-id="3936d-122">名称 - 数据层应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="3936d-122">Name - the data-tier application name.</span></span>  
  
-   <span data-ttu-id="3936d-123">应用程序 CPU - 显示此数据层应用程序的处理器使用率的运行状态。</span><span class="sxs-lookup"><span data-stu-id="3936d-123">Application CPU - Displays the health state of processor utilization for this data-tier application.</span></span> <span data-ttu-id="3936d-124">根据为数据层应用程序设置的 CPU 使用策略以及易失性资源评估策略的配置设置，确定此参数的运行状态。</span><span class="sxs-lookup"><span data-stu-id="3936d-124">The health state for this parameter is determined according to CPU utilization policy set for the data-tier application and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="3936d-125">有关详细信息，请参阅[减少 CPU 使用策略中的干扰（SQL Server 实用工具）](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="3936d-125">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="3936d-126">若要查看此数据层应用程序的处理器使用率历史记录，或者查看或更改策略限制，请单击“CPU 使用率”选项卡。</span><span class="sxs-lookup"><span data-stu-id="3936d-126">To view the processor utilization history for this data-tier application, or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="3936d-127">计算机 CPU - 显示计算机处理器使用率的运行状态。</span><span class="sxs-lookup"><span data-stu-id="3936d-127">Computer CPU - Displays the health state of computer processor utilization.</span></span> <span data-ttu-id="3936d-128">根据为计算机设置的 CPU 使用策略以及易失性资源评估策略的配置设置，确定此参数的运行状态。</span><span class="sxs-lookup"><span data-stu-id="3936d-128">The health state for this parameter is determined according to CPU utilization policy set for the computer and the configuration setting for volatile resource evaluation policy.</span></span> <span data-ttu-id="3936d-129">有关详细信息，请参阅[减少 CPU 使用策略中的干扰（SQL Server 实用工具）](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="3936d-129">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
     <span data-ttu-id="3936d-130">若要查看此数据层应用程序的处理器使用率历史记录，或者查看或更改策略限制，请单击“CPU 使用率”选项卡。</span><span class="sxs-lookup"><span data-stu-id="3936d-130">To view the processor utilization history for this data-tier application, or to view or change the policy limits, click on the **CPU Utilization** tab.</span></span>  
  
-   <span data-ttu-id="3936d-131">文件空间 - 为每个数据层应用程序显示文件空间使用率的运行状态的摘要。</span><span class="sxs-lookup"><span data-stu-id="3936d-131">File Space - Displays a summary of health states of file space utilization for each data-tier application.</span></span>  
  
    -   <span data-ttu-id="3936d-132">绿色的选中标记 - 所有文件组和日志文件组的运行状态是既没有使用过度，也没有使用不足。</span><span class="sxs-lookup"><span data-stu-id="3936d-132">Green check - The health states for all filegroups and the log file group are neither overutilized or underutilized.</span></span>  
  
    -   <span data-ttu-id="3936d-133">绿色向下箭头 - 至少一个文件组或日志文件组的运行状态是使用不足，并且没有文件组或日志文件组被使用过度。</span><span class="sxs-lookup"><span data-stu-id="3936d-133">Green down arrow - The health state for at least one filegroup or log file group is underutilized, and no filegroup or log file group is overutilized.</span></span>  
  
    -   <span data-ttu-id="3936d-134">红色向上箭头 - 至少一个文件组或日志文件组的运行状态是使用过度。</span><span class="sxs-lookup"><span data-stu-id="3936d-134">Red up arrow - The health state for at least one filegroup or the log file group is overutilized.</span></span> <span data-ttu-id="3936d-135">注意，如果数据库处于“紧急”状态，则运行状态将显示日志文件空间使用过度。</span><span class="sxs-lookup"><span data-stu-id="3936d-135">Note that if a database is in "emergency" state, the health state will display overutilized log file space.</span></span>  
  
     <span data-ttu-id="3936d-136">若要查看或更改文件空间策略限制，请单击 **“存储使用率”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="3936d-136">To view or change the file space policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="3936d-137">卷空间 - 为包含属于所选数据层应用程序的数据库的所有卷显示卷空间使用率的运行状态的摘要。</span><span class="sxs-lookup"><span data-stu-id="3936d-137">Volume Space - Displays a summary of the health states of volume space utilization for all volumes that contain databases belonging to the selected data-tier application.</span></span> <span data-ttu-id="3936d-138">如果任何卷的运行状态为使用过度，则卷运行状态将在此列表视图中报告为使用过度。</span><span class="sxs-lookup"><span data-stu-id="3936d-138">If the health state of any volume is overutilized, then the volume space health state will be reported in the list view as overutilized.</span></span> <span data-ttu-id="3936d-139">如果任何卷的运行状态为使用不足，并且没有卷被使用过度，则卷空间运行状态将在此列表视图中报告为使用不足。</span><span class="sxs-lookup"><span data-stu-id="3936d-139">If the health state of any volume is underutilized, and no volume is overutilized, then the volume space health state will be reported in the list view as underutilized.</span></span> <span data-ttu-id="3936d-140">否则，卷空间运行状态将在列表视图中报告为很好地利用。</span><span class="sxs-lookup"><span data-stu-id="3936d-140">Otherwise, the volume space health state will be reported in the list view as well-utilized.</span></span> <span data-ttu-id="3936d-141">若要查看或更改策略限制，请单击 **“存储使用率”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="3936d-141">To view or change the policy limits, click on the **Storage Utilization** tab.</span></span>  
  
-   <span data-ttu-id="3936d-142">策略类型 - 指示对于数据层应用程序，“全局”默认策略或“覆盖”自定义策略是否有效。</span><span class="sxs-lookup"><span data-stu-id="3936d-142">Policy Type - Indicates whether "Global" default policies or "Override" custom policies are in effect for the data-tier application.</span></span>  
  
-   <span data-ttu-id="3936d-143">实例名称 - 显示承载数据层应用程序的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="3936d-143">Instance Name - Displays the name of the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that hosts the data-tier application.</span></span>  
  
 <span data-ttu-id="3936d-144">可以在列表视图的列标题区域中使用右键单击菜单显示的其他列：</span><span class="sxs-lookup"><span data-stu-id="3936d-144">Other columns that can be displayed using the right-click menu in the column heading area of the list view:</span></span>  
  
-   <span data-ttu-id="3936d-145">数据库名称</span><span class="sxs-lookup"><span data-stu-id="3936d-145">Database Name</span></span>  
  
-   <span data-ttu-id="3936d-146">部署日期</span><span class="sxs-lookup"><span data-stu-id="3936d-146">Deployed Date</span></span>  
  
-   <span data-ttu-id="3936d-147">可信：（True 或 False）</span><span class="sxs-lookup"><span data-stu-id="3936d-147">Trustworthy: (True or False)</span></span>  
  
-   <span data-ttu-id="3936d-148">排序规则</span><span class="sxs-lookup"><span data-stu-id="3936d-148">Collation</span></span>  
  
-   <span data-ttu-id="3936d-149">兼容级别：（例如 Version100）</span><span class="sxs-lookup"><span data-stu-id="3936d-149">Compatibility Level: (for example, Version100)</span></span>  
  
-   <span data-ttu-id="3936d-150">已启用加密：（True 或 False）</span><span class="sxs-lookup"><span data-stu-id="3936d-150">Encryption Enabled: (True or False)</span></span>  
  
-   <span data-ttu-id="3936d-151">恢复模式：（简单恢复模式、完整恢复模式和大容量日志恢复模式）</span><span class="sxs-lookup"><span data-stu-id="3936d-151">Recovery Model: (Simple, Full, or Bulk-Logged)</span></span>  
  
-   <span data-ttu-id="3936d-152">上次报告的时间：此列使用 datetime 数据类型显示 UCP 本地日期和时间。</span><span class="sxs-lookup"><span data-stu-id="3936d-152">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="3936d-153">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主题。</span><span class="sxs-lookup"><span data-stu-id="3936d-153">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="3936d-154">在使用实用工具对象模型时，请注意 SSMS 使用 datetimeoffset 数据类型。</span><span class="sxs-lookup"><span data-stu-id="3936d-154">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="3936d-155">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主题。</span><span class="sxs-lookup"><span data-stu-id="3936d-155">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="3936d-156">“CPU 使用率”选项卡</span><span class="sxs-lookup"><span data-stu-id="3936d-156">CPU Utilization tab</span></span>  
 <span data-ttu-id="3936d-157">“CPU 使用率”选项卡为数据层应用程序和计算机 CPU 使用率显示历史数据的并排图形。</span><span class="sxs-lookup"><span data-stu-id="3936d-157">The CPU utilization tab shows side-by-side graphs of historical data for data-tier application and computer CPU utilization.</span></span>  
  
 <span data-ttu-id="3936d-158">该图形按照显示区域右侧的单选按钮中指定的间隔显示处理器使用率历史记录。</span><span class="sxs-lookup"><span data-stu-id="3936d-158">The graph displays the processor utilization history for the interval specified in the radio buttons on the right side of the display area.</span></span> <span data-ttu-id="3936d-159">若要更改显示间隔和刷新数据集，请从列表中选择一个单选按钮。</span><span class="sxs-lookup"><span data-stu-id="3936d-159">To change the display interval and refresh the data set, select a radio button from the list.</span></span>  
  
 <span data-ttu-id="3936d-160">间隔选项如下所示：</span><span class="sxs-lookup"><span data-stu-id="3936d-160">Interval options are as follows:</span></span>  
  
-   <span data-ttu-id="3936d-161">1 天，以 15 分钟间隔显示。</span><span class="sxs-lookup"><span data-stu-id="3936d-161">1 Day, displayed in 15-minute intervals.</span></span>  
  
-   <span data-ttu-id="3936d-162">1 周，以 1 天间隔显示。</span><span class="sxs-lookup"><span data-stu-id="3936d-162">1 Week, displayed in 1-day intervals.</span></span>  
  
-   <span data-ttu-id="3936d-163">1 个月，以 1 周间隔显示。</span><span class="sxs-lookup"><span data-stu-id="3936d-163">1 Month, displayed in 1-week intervals.</span></span>  
  
-   <span data-ttu-id="3936d-164">1 年，以 1 个月间隔显示。</span><span class="sxs-lookup"><span data-stu-id="3936d-164">1 Year, displayed in 1-month intervals.</span></span>  
  
 <span data-ttu-id="3936d-165">“存储使用率”选项卡</span><span class="sxs-lookup"><span data-stu-id="3936d-165">Storage Utilization tab</span></span>  
 <span data-ttu-id="3936d-166">“存储使用率”选项卡具有一个树视图，它显示属于列表视图中选定数据层应用程序的数据库文件和日志文件的存储使用率详细信息。</span><span class="sxs-lookup"><span data-stu-id="3936d-166">The Storage Utilization tab has a tree view that displays storage utilization details for database files and log files that belong to the data-tier application selected in the list view.</span></span> <span data-ttu-id="3936d-167">请注意，时间数据使用 datetime 数据类型显示 UCP 本地日期和时间。</span><span class="sxs-lookup"><span data-stu-id="3936d-167">Note that time data show the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="3936d-168">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主题。</span><span class="sxs-lookup"><span data-stu-id="3936d-168">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="3936d-169">在使用实用工具对象模型时，请注意 SSMS 使用 datetimeoffset 数据类型。</span><span class="sxs-lookup"><span data-stu-id="3936d-169">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="3936d-170">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主题。</span><span class="sxs-lookup"><span data-stu-id="3936d-170">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="3936d-171">显示可按文件组或按卷分组。</span><span class="sxs-lookup"><span data-stu-id="3936d-171">Display can be grouped by filegroup or by volume.</span></span> <span data-ttu-id="3936d-172">若要使用文件组树视图，请在 **“文件分组依据:”** 选择中选择 **“文件组”** 单选按钮。</span><span class="sxs-lookup"><span data-stu-id="3936d-172">To use the filegroup tree view, select the **Filegroup** radio button in the **Group files by:** selection.</span></span>  
  
 <span data-ttu-id="3936d-173">存储使用率历史数据图形中显示的数据会根据树视图中选择的节点发生变化：</span><span class="sxs-lookup"><span data-stu-id="3936d-173">Data displayed in the graph of storage utilization history changes depending on the node selected in the tree view:</span></span>  
  
-   <span data-ttu-id="3936d-174">选择文件组节点以便显示由属于所选文件组的所有数据文件使用的文件空间图形。</span><span class="sxs-lookup"><span data-stu-id="3936d-174">Select the file group node to display a graph of file space used by all data files that belong to the selected file group.</span></span>  
  
-   <span data-ttu-id="3936d-175">选择日志文件节点以便显示由属于所选数据库的所有日志文件使用的文件空间图形。</span><span class="sxs-lookup"><span data-stu-id="3936d-175">Select the log file node to display a graph of file space used by all log files that belong to the selected database.</span></span>  
  
-   <span data-ttu-id="3936d-176">选择数据库节点以便显示一个图形，该图形添加由属于所选数据库的所有数据文件和所有日志文件使用的文件空间。</span><span class="sxs-lookup"><span data-stu-id="3936d-176">Select the database node to display a graph that adds file space used by all data files and all log files that belong to the selected database.</span></span>  
  
 <span data-ttu-id="3936d-177">若要查看单独文件的存储使用率状态，请单击树视图中文件名旁的加号。</span><span class="sxs-lookup"><span data-stu-id="3936d-177">To view storage utilization status for individual files, click on the plus sign next to a file name in the tree view.</span></span>  
  
 <span data-ttu-id="3936d-178">运行状态图标为每个文件组提供一目了然的状态（与策略阈值进行比较）：</span><span class="sxs-lookup"><span data-stu-id="3936d-178">Health state icons provide at-a-glance status for each filegroup compared to policy thresholds:</span></span>  
  
-   <span data-ttu-id="3936d-179">绿色的选中标记 - 文件组中至少一个数据文件的文件空间使用率是既没有使用过度，也没有使用不足。</span><span class="sxs-lookup"><span data-stu-id="3936d-179">Green check - File space utilization for at least one data file in the filegroup is neither overutilized or underutilized.</span></span>  
  
-   <span data-ttu-id="3936d-180">绿色向下箭头 - 文件组中至少一个数据文件的文件空间使用率是使用不足，并且文件组中没有文件被使用过度。</span><span class="sxs-lookup"><span data-stu-id="3936d-180">Green down arrow - File space utilization for at least one data file in the filegroup is underutilized, and no files in the filegroup are overutilized.</span></span>  
  
-   <span data-ttu-id="3936d-181">红色向上箭头 - 文件组中所有数据文件的文件空间使用率被使用过度。</span><span class="sxs-lookup"><span data-stu-id="3936d-181">Red up arrow - File space utilization for all data files in the filegroup are overutilized.</span></span> <span data-ttu-id="3936d-182">注意，如果数据库处于“紧急”状态，则运行状态将显示日志文件空间使用过度。</span><span class="sxs-lookup"><span data-stu-id="3936d-182">Note that if a database is in "emergency" state, the health state will display overutilized log file space.</span></span>  
  
 <span data-ttu-id="3936d-183">若要按卷查看文件，请在 **“文件分组依据:”** 选择中选择 **“卷”** 单选按钮。</span><span class="sxs-lookup"><span data-stu-id="3936d-183">To view files by volume, select the **Volume** radio button in the **Group files by:** selection.</span></span> <span data-ttu-id="3936d-184">存储使用率历史记录图形显示存储卷上所有数据文件和所有日志文件使用的文件空间。</span><span class="sxs-lookup"><span data-stu-id="3936d-184">The graph of storage utilization history displays file space used by all data files and all log files on the storage volume.</span></span> <span data-ttu-id="3936d-185">展开树可以查看单独数据库数据文件和日志文件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3936d-185">Expand the tree to view details for individual database data files and log files.</span></span>  
  
 <span data-ttu-id="3936d-186">状态图标用来为每个卷提供状态：</span><span class="sxs-lookup"><span data-stu-id="3936d-186">Status icons are used to provide status for each volume:</span></span>  
  
-   <span data-ttu-id="3936d-187">绿色的选中标记 - 资源被很好地利用。</span><span class="sxs-lookup"><span data-stu-id="3936d-187">Green check - Resources are well-utilized.</span></span>  
  
-   <span data-ttu-id="3936d-188">绿色向下箭头 - 资源使用不足。</span><span class="sxs-lookup"><span data-stu-id="3936d-188">Green down arrow - Resources are underutilized.</span></span>  
  
-   <span data-ttu-id="3936d-189">红色向上箭头 - 资源被使用过度。</span><span class="sxs-lookup"><span data-stu-id="3936d-189">Red up arrow - Resources are overutilized.</span></span>  
  
 <span data-ttu-id="3936d-190">“存储使用率”选项卡上每个文件名旁边的仪表表示相对于文件的有效容量的文件所使用空间量。</span><span class="sxs-lookup"><span data-stu-id="3936d-190">The gauge next to each file name on the Storage Utilization tab represents the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="3936d-191">仪表旁边显示的百分比值是相对于文件的有效容量的文件所使用空间量的比率。</span><span class="sxs-lookup"><span data-stu-id="3936d-191">The percentage value displayed next to the gauge is the ratio of the amount of space used by the file relative to the effective capacity of the file.</span></span> <span data-ttu-id="3936d-192">工具提示提供的数据用于计算与有效容量相比每个卷和每个文件的百分比。</span><span class="sxs-lookup"><span data-stu-id="3936d-192">Tool tips provide data used to calculate percentages for each volume and each file compared to effective capacity.</span></span>  
  
 <span data-ttu-id="3936d-193">如果该文件未配置为自动增长，则有效容量是分配给该文件的空间量。</span><span class="sxs-lookup"><span data-stu-id="3936d-193">If the file is not configured to auto-grow, then the effective capacity is the amount of space allocated to the file.</span></span> <span data-ttu-id="3936d-194">如果该文件配置为自动增长，则有效容量是当前分配给该文件的空间量与目前卷上可用空间量之和。</span><span class="sxs-lookup"><span data-stu-id="3936d-194">If the file is configured to auto-grow, then the effective capacity is the sum of the amount of space currently allocated to the file and the amount of free space currently available on the volume.</span></span>  
  
 <span data-ttu-id="3936d-195">可为数据文件和日志文件配置存储使用率策略。</span><span class="sxs-lookup"><span data-stu-id="3936d-195">Storage utilization policies can be configured for data files and for log files.</span></span> <span data-ttu-id="3936d-196">若要查看或更改文件的存储使用率策略阈值，请单击“存储使用率”窗格底部的 **“文件策略”** 链接。</span><span class="sxs-lookup"><span data-stu-id="3936d-196">To view or change the storage utilization policy thresholds for files, click on the **File Policy** link at the bottom of the Storage Utilization pane.</span></span> <span data-ttu-id="3936d-197">若要查看或更改存储卷的存储使用率策略阈值，请单击“存储使用率”窗格底部的 **“卷策略”** 链接。</span><span class="sxs-lookup"><span data-stu-id="3936d-197">To view or change the storage utilization policy thresholds for a storage volume, click on the **Volume Policy** link at the bottom of the Storage Utilization pane.</span></span>  
  
 <span data-ttu-id="3936d-198">若要覆盖默认策略阈值，请单击单选按钮 **“覆盖默认策略”** ，指定上限和下限值，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3936d-198">To override the default policy thresholds, click on the radio button to **Override the default policy**, specify values for the upper and lower limits, then click **OK**.</span></span>  
  
 <span data-ttu-id="3936d-199">有关更改违反策略容限的详细信息，请参阅[减少 CPU 使用策略中的干扰（SQL Server 实用工具）](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="3936d-199">For more information about changing the tolerance for policy violations, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="3936d-200">“属性详细信息”选项卡</span><span class="sxs-lookup"><span data-stu-id="3936d-200">Property Details tab</span></span>  
 <span data-ttu-id="3936d-201">为数据层应用程序列出的属性详细信息包括以下类别：</span><span class="sxs-lookup"><span data-stu-id="3936d-201">Property details listed for data-tier applications include the following categories:</span></span>  
  
-   <span data-ttu-id="3936d-202">数据库名称</span><span class="sxs-lookup"><span data-stu-id="3936d-202">Database Name</span></span>  
  
-   <span data-ttu-id="3936d-203">部署日期</span><span class="sxs-lookup"><span data-stu-id="3936d-203">Deployed Date</span></span>  
  
-   <span data-ttu-id="3936d-204">可信：（True 或 False）</span><span class="sxs-lookup"><span data-stu-id="3936d-204">Trustworthy: (True or False)</span></span>  
  
-   <span data-ttu-id="3936d-205">排序规则</span><span class="sxs-lookup"><span data-stu-id="3936d-205">Collation</span></span>  
  
-   <span data-ttu-id="3936d-206">兼容级别：（例如 Version100）</span><span class="sxs-lookup"><span data-stu-id="3936d-206">Compatibility Level: (for example, Version100)</span></span>  
  
-   <span data-ttu-id="3936d-207">已启用加密：（True 或 False）</span><span class="sxs-lookup"><span data-stu-id="3936d-207">Encryption Enabled: (True or False)</span></span>  
  
-   <span data-ttu-id="3936d-208">恢复模式：（简单恢复模式、完整恢复模式和大容量日志恢复模式）</span><span class="sxs-lookup"><span data-stu-id="3936d-208">Recovery Model: (Simple, Full, or Bulk-Logged)</span></span>  
  
-   <span data-ttu-id="3936d-209">上次报告的时间：此列使用 datetime 数据类型显示 UCP 本地日期和时间。</span><span class="sxs-lookup"><span data-stu-id="3936d-209">Last Reported Time: This column shows the UCP local date and time using the datetime data type.</span></span> <span data-ttu-id="3936d-210">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 主题。</span><span class="sxs-lookup"><span data-stu-id="3936d-210">For more information, see the [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) topic in SQL Server Books Online.</span></span> <span data-ttu-id="3936d-211">在使用实用工具对象模型时，请注意 SSMS 使用 datetimeoffset 数据类型。</span><span class="sxs-lookup"><span data-stu-id="3936d-211">When using the Utility object model, note that SSMS uses the datetimeoffset data type.</span></span> <span data-ttu-id="3936d-212">有关详细信息，请参阅 SQL Server 联机丛书中的 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 主题。</span><span class="sxs-lookup"><span data-stu-id="3936d-212">For more information, see the [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) topic in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3936d-213">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3936d-213">See Also</span></span>  
 <span data-ttu-id="3936d-214">[托管实例详细信息（SQL Server 实用工具）](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="3936d-214">[Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="3936d-215">[实用工具仪表板 &#40;SQL Server 实用工具&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="3936d-215">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="3936d-216">[在 SQL Server 实用工具中监视 SQL Server 的实例](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="3936d-216">[Monitor Instances of SQL Server in the SQL Server Utility](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="3936d-217">SQL Server 实用工具功能和任务</span><span class="sxs-lookup"><span data-stu-id="3936d-217">SQL Server Utility Features and Tasks</span></span>](../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
