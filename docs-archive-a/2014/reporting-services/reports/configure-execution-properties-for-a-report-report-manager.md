---
title: 配置报表的执行属性（报表管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- reports [Reporting Services], properties
- reports [Reporting Services], execution options
ms.assetid: 73cc8dcc-ef80-40d7-9739-d33bba0eb28a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 51cd7b5db225b39f5a061ed750b2ef5cdd265b9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591753"
---
# <a name="configure-execution-properties-for-a-report--report-manager"></a><span data-ttu-id="e9b28-102">配置报表的执行属性（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="e9b28-102">Configure Execution Properties for a Report  (Report Manager)</span></span>
  <span data-ttu-id="e9b28-103">可以设置报表处理选项以指定何时为报表检索数据。</span><span class="sxs-lookup"><span data-stu-id="e9b28-103">You can set report processing options to specify when data is retrieved for a report.</span></span> <span data-ttu-id="e9b28-104">如果外部数据源按照特定的时间刷新（例如，每天或每周刷新数据仓库），并且您想要避免每当请求报表时对同一数据进行检索的开销，则为报表计划数据处理非常有用。</span><span class="sxs-lookup"><span data-stu-id="e9b28-104">It is useful to schedule data processing for a report if the external data source is refreshed at specific times (for example, a data warehouse that is refreshed daily or weekly) and you want to avoid the overhead of retrieving the same data each time a report is requested.</span></span> <span data-ttu-id="e9b28-105">如果您想要控制外部数据库服务器上的处理负载，或者如果想要为必须使用相同数据集的多个用户提供一致的结果，则计划数据处理也很有用。</span><span class="sxs-lookup"><span data-stu-id="e9b28-105">Scheduling data processing is also useful if you want to control the processing load on the external database server or when you want to provide consistent results for multiple users who must work with identical sets of data.</span></span> <span data-ttu-id="e9b28-106">使用可变数据的按需运行报表每分钟都会生成不同的结果。</span><span class="sxs-lookup"><span data-stu-id="e9b28-106">With volatile data, an on-demand report can produce different results from one minute to the next.</span></span> <span data-ttu-id="e9b28-107">相反，报表快照则可用来针对包含同一时间点数据的其他报表或分析工具进行有效比较。</span><span class="sxs-lookup"><span data-stu-id="e9b28-107">A report snapshot, by contrast, allows you to make valid comparisons against other reports or analytical tools that contain data from the same point in time.</span></span>  
  
 <span data-ttu-id="e9b28-108">报表快照是一个报表，其中包含在特定时间点检索到的布局说明以及查询结果。</span><span class="sxs-lookup"><span data-stu-id="e9b28-108">A report snapshot is a report that contains layout instructions and query results that were retrieved at a specific point in time.</span></span> <span data-ttu-id="e9b28-109">与按需运行报表（在选择该报表时可获得最新的查询结果）不同，报表快照按计划进行处理，再保存到报表服务器中。</span><span class="sxs-lookup"><span data-stu-id="e9b28-109">Unlike on-demand reports, which get up-to-date query results when you select the report, report snapshots are processed on a schedule and then saved to a report server.</span></span> <span data-ttu-id="e9b28-110">当您选择报表快照进行查看时，报表服务器将在报表服务器数据库中检索存储的报表，然后显示快照创建时报表的数据和布局。</span><span class="sxs-lookup"><span data-stu-id="e9b28-110">When you select a report snapshot for viewing, the report server retrieves the stored report from the report server database and shows the data and layout that were current for the report at the time the snapshot was created.</span></span>  
  
 <span data-ttu-id="e9b28-111">报表快照不以特定的呈现格式进行保存。</span><span class="sxs-lookup"><span data-stu-id="e9b28-111">Report snapshots are not saved in a particular rendering format.</span></span> <span data-ttu-id="e9b28-112">相反，将以用户或应用程序发出请求时的最终查看格式（如 HTML）来呈现报表快照。</span><span class="sxs-lookup"><span data-stu-id="e9b28-112">Instead, report snapshots are rendered in a final viewing format (such as HTML) only when a user or an application requests it.</span></span> <span data-ttu-id="e9b28-113">延迟呈现会使快照具有可移植性。</span><span class="sxs-lookup"><span data-stu-id="e9b28-113">Deferred rendering makes a snapshot portable.</span></span> <span data-ttu-id="e9b28-114">报表可以采用适用于请求设备或 Web 浏览器的正确格式呈现。</span><span class="sxs-lookup"><span data-stu-id="e9b28-114">The report can be rendered in the correct format for the requesting device or Web browser.</span></span>  
  
### <a name="to-configure-report-processing-options"></a><span data-ttu-id="e9b28-115">配置报表处理选项</span><span class="sxs-lookup"><span data-stu-id="e9b28-115">To configure report processing options</span></span>  
  
1.  <span data-ttu-id="e9b28-116">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e9b28-116">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="e9b28-117">导航到并打开要设置处理选项的报表。</span><span class="sxs-lookup"><span data-stu-id="e9b28-117">Navigate to and open the report for which you want to set processing options.</span></span>  
  
 <span data-ttu-id="e9b28-118">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="e9b28-118">Hover over the report, and click the drop-down arrow.</span></span>  
  
1.  <span data-ttu-id="e9b28-119">在下拉菜单中，单击“管理”，然后选择“处理选项”选项卡\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9b28-119">In the drop-down menu, click **Manage** and then select the **Processing Options** tab.</span></span>  
  
2.  <span data-ttu-id="e9b28-120">单击 **“通过执行快照呈现此报表”**，然后选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="e9b28-120">Click **Render this report from an execution snapshot, and then select one of the following options:**</span></span>  
  
    -   <span data-ttu-id="e9b28-121">如果要创建快照，则选择“使用下列计划创建报表执行快照”，再定义特定于报表的计划，或从“共享计划”列表中进行选择\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9b28-121">If you want to create a snapshot, select **Use the following schedule to create report execution snapshots**, and then either define a report-specific schedule or select from the **Shared schedule** list.</span></span>  
  
    -   <span data-ttu-id="e9b28-122">如果希望立即创建快照，请选择 **“在此页上单击‘应用’按钮后创建报表快照”**。</span><span class="sxs-lookup"><span data-stu-id="e9b28-122">If you want to create a snapshot immediately, select **Create a report snapshot when you click the Apply button on this page**.</span></span>  
  
3.  <span data-ttu-id="e9b28-123">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="e9b28-123">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9b28-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9b28-124">See Also</span></span>  
 <span data-ttu-id="e9b28-125">[设置报表处理属性](../report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e9b28-125">[Set Report Processing Properties](../report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="e9b28-126">[打开并关闭报表 &#40;报表管理器&#41;](../reports/open-and-close-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e9b28-126">[Open and Close a Report &#40;Report Manager&#41;](../reports/open-and-close-a-report-report-manager.md) </span></span>  
 <span data-ttu-id="e9b28-127">[“内容”页（报表管理器）](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e9b28-127">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="e9b28-128">[报表服务器内容管理（SSRS 本机模式）](../report-server/report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e9b28-128">[Report Server Content Management &#40;SSRS Native Mode&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="e9b28-129">“处理选项”属性页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="e9b28-129">Processing Options Properties Page &#40;Report Manager&#41;</span></span>](../processing-options-properties-page-report-manager.md)  
  
  
