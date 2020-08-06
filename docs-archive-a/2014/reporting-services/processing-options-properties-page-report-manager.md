---
title: 处理选项属性页 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 28f07c70-7132-4d15-9505-4fdf31dc9cc0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ab43474869eb0b06eba33b4bd597907b7371ce09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577363"
---
# <a name="processing-options-properties-page-report-manager"></a><span data-ttu-id="1b79a-102">“处理选项”属性页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="1b79a-102">Processing Options Properties Page (Report Manager)</span></span>
  <span data-ttu-id="1b79a-103">使用“处理选项”属性页可为当前所选的报表设置报表执行属性。</span><span class="sxs-lookup"><span data-stu-id="1b79a-103">Use the Processing Options properties page to set report execution properties for the currently selected report.</span></span> <span data-ttu-id="1b79a-104">这些选项将确定处理报表数据的时间。</span><span class="sxs-lookup"><span data-stu-id="1b79a-104">These options determine when data processing for the report occurs.</span></span> <span data-ttu-id="1b79a-105">您可以设置这些选项，使报表数据的检索时间错开高峰期。</span><span class="sxs-lookup"><span data-stu-id="1b79a-105">You can set these options to retrieve report data during off-peak hours.</span></span> <span data-ttu-id="1b79a-106">如果有经常访问的报表，则可以临时缓存其副本，这样，在每隔几分钟便有多个用户访问同一报表的情况下可使用户无需等待。</span><span class="sxs-lookup"><span data-stu-id="1b79a-106">If you have a report that is accessed frequently, you can temporarily cache copies of it to eliminate wait time if multiple users are accessing the same report within minutes of each other.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b79a-107">并非在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个版本中均提供报表历史记录、执行快照和缓存功能。</span><span class="sxs-lookup"><span data-stu-id="1b79a-107">The Report history, Execution snapshots and Caching features are not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1b79a-108">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="1b79a-108">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="1b79a-109">导航</span><span class="sxs-lookup"><span data-stu-id="1b79a-109">Navigation</span></span>  
 <span data-ttu-id="1b79a-110">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="1b79a-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-processing-options-properties-page"></a><span data-ttu-id="1b79a-111">打开“处理选项”属性页</span><span class="sxs-lookup"><span data-stu-id="1b79a-111">To open the Processing Options properties page</span></span>  
  
1.  <span data-ttu-id="1b79a-112">打开报表管理器，找到要设置处理属性的报表。</span><span class="sxs-lookup"><span data-stu-id="1b79a-112">Open Report Manager, and locate the report for which you want to set processing properties.</span></span>  
  
2.  <span data-ttu-id="1b79a-113">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="1b79a-113">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="1b79a-114">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="1b79a-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="1b79a-115">这会打开该报表的“常规”属性页。</span><span class="sxs-lookup"><span data-stu-id="1b79a-115">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="1b79a-116">选择 **“处理选项”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1b79a-116">Select the **Processing Options** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1b79a-117">选项</span><span class="sxs-lookup"><span data-stu-id="1b79a-117">Options</span></span>  
 <span data-ttu-id="1b79a-118">**始终用最新数据运行此报表**</span><span class="sxs-lookup"><span data-stu-id="1b79a-118">**Always run this report with the most recent data**</span></span>  
 <span data-ttu-id="1b79a-119">如果您希望在用户选择报表时检索报表数据，请使用此选项。</span><span class="sxs-lookup"><span data-stu-id="1b79a-119">Use this option when you want to retrieve report data when the user selects the report.</span></span> <span data-ttu-id="1b79a-120">如果有缓存的报表副本可用，则会将缓存副本返回给用户；否则，在用户选择报表时将执行数据检索和呈现。</span><span class="sxs-lookup"><span data-stu-id="1b79a-120">If a cached copy of the report is available, it is returned to the user; otherwise, data retrieval and rendering occurs when a user selects the report.</span></span>  
  
 <span data-ttu-id="1b79a-121">若要始终以最新数据运行报表，请选择 **“不缓存此报表的临时副本”** 。</span><span class="sxs-lookup"><span data-stu-id="1b79a-121">Select **Do not cache temporary copies of this report** to always run the report with the most recent data.</span></span> <span data-ttu-id="1b79a-122">每当用户打开报表时，都会触发一个对数据源的查询，该数据源包含报表中所使用的数据。</span><span class="sxs-lookup"><span data-stu-id="1b79a-122">Each user who opens the report triggers a query against the data source that contains data used in the report.</span></span>  
  
 <span data-ttu-id="1b79a-123">若要始终以最新数据运行报表，请选择 \*\*\*\*，则用户首次打开报表时将在缓存中保留报表的临时副本。</span><span class="sxs-lookup"><span data-stu-id="1b79a-123">Select **Cache a temporary copy of the report**to place a temporary copy of the report in a cache when a user first opens the report.</span></span> <span data-ttu-id="1b79a-124">以后在缓存期间内运行报表的用户将收到报表的缓存副本。</span><span class="sxs-lookup"><span data-stu-id="1b79a-124">Subsequent users who run the report within the caching period receive the cached copy of the report.</span></span> <span data-ttu-id="1b79a-125">由于将从缓存中返回报表（而不是重新处理），因此进行缓存通常会改进性能。</span><span class="sxs-lookup"><span data-stu-id="1b79a-125">Caching usually improves performance because the report is returned from the cache instead of being processed again.</span></span>  
  
 <span data-ttu-id="1b79a-126">缓存的报表最终必须过期。</span><span class="sxs-lookup"><span data-stu-id="1b79a-126">Cached reports must eventually expire.</span></span> <span data-ttu-id="1b79a-127">请指定要保存报表缓存副本的分钟数。</span><span class="sxs-lookup"><span data-stu-id="1b79a-127">Specify the number of minutes to save the cached copy of the report.</span></span> <span data-ttu-id="1b79a-128">临时副本一过期，就不会再从缓存中返回该副本。</span><span class="sxs-lookup"><span data-stu-id="1b79a-128">As soon as a temporary copy expires, it is no longer returned from cache.</span></span> <span data-ttu-id="1b79a-129">下次用户打开该报表时，报表服务器将重新处理该报表，并重新将刷新后的报表副本存入缓存。</span><span class="sxs-lookup"><span data-stu-id="1b79a-129">The next time a user opens the report, the report server processes the report again and places a copy of the refreshed report back in the cache.</span></span>  
  
 <span data-ttu-id="1b79a-130">您也可以使用计划按一定的频率（而不是具体的分钟数）来设定缓存报表的过期时间。</span><span class="sxs-lookup"><span data-stu-id="1b79a-130">You can also use a schedule to expire a cached report using a frequency other than minutes.</span></span> <span data-ttu-id="1b79a-131">例如，要使缓存的报表在工作日结束时过期，则可以选择夜间的某个特定时间，该时间过后缓存的报表即过期。</span><span class="sxs-lookup"><span data-stu-id="1b79a-131">For example, to expire a cached report at the end of the day, you can pick a specific hour at night after which the copy expires.</span></span>  
  
 <span data-ttu-id="1b79a-132">**根据报表执行快照呈现此报表**</span><span class="sxs-lookup"><span data-stu-id="1b79a-132">**Render this report from a report execution snapshot**</span></span>  
 <span data-ttu-id="1b79a-133">使用此选项可检索已在预定时间存储为快照的报表。</span><span class="sxs-lookup"><span data-stu-id="1b79a-133">Use this option to retrieve a report that has been stored as a snapshot at a time that you schedule.</span></span> <span data-ttu-id="1b79a-134">选择此选项时，可以将数据处理安排在非高峰期进行。</span><span class="sxs-lookup"><span data-stu-id="1b79a-134">When you choose this option, you can schedule data processing to occur during off-peak hours.</span></span> <span data-ttu-id="1b79a-135">与用户打开报表时创建的缓存副本不同，快照按计划进行创建和刷新。</span><span class="sxs-lookup"><span data-stu-id="1b79a-135">Unlike cached copies that are created when a user opens the report, a snapshot is created and subsequently refreshed on a schedule.</span></span> <span data-ttu-id="1b79a-136">快照不会过期并持续有效，直到新版本的快照取而代之。</span><span class="sxs-lookup"><span data-stu-id="1b79a-136">Snapshots do not expire; they remain in service until they are replaced by newer versions.</span></span>  
  
 <span data-ttu-id="1b79a-137">由于报表执行设置而生成的快照与报表历史快照具有相同的特点。</span><span class="sxs-lookup"><span data-stu-id="1b79a-137">Snapshots that are generated as a result of report execution settings have the same characteristics as report history snapshots.</span></span> <span data-ttu-id="1b79a-138">不同之处在于仅有一个报表执行快照，而通常可能会有许多报表历史快照。</span><span class="sxs-lookup"><span data-stu-id="1b79a-138">The difference is that there is only one report execution snapshot and potentially many report history snapshots.</span></span> <span data-ttu-id="1b79a-139">报表历史快照可以从报表的“历史记录”页进行访问，其中存储了多个存在于不同时间点的报表实例。</span><span class="sxs-lookup"><span data-stu-id="1b79a-139">Report history snapshots are accessed from the History page of the report, which stores many instances of a report as it existed at different points in time.</span></span> <span data-ttu-id="1b79a-140">相反，用户若要访问报表执行快照，就需按照与访问实时报表相同的方法从文件夹进行访问。</span><span class="sxs-lookup"><span data-stu-id="1b79a-140">In contrast, users access report execution snapshots from folders the same way that they access live reports.</span></span> <span data-ttu-id="1b79a-141">对于报表执行快照，没有可视的信息提示用户该报表为快照。</span><span class="sxs-lookup"><span data-stu-id="1b79a-141">In the case of report execution snapshots, no visual cue exists to indicate to users that the report is a snapshot.</span></span>  
  
 <span data-ttu-id="1b79a-142">选择相关选项 **“在此页上单击‘应用’按钮后创建报表快照”** ，以便在单击“应用”后创建报表快照。</span><span class="sxs-lookup"><span data-stu-id="1b79a-142">Select the related option of **Create a report snapshot when you click Apply on this page** to create a report snapshot when you click Apply.</span></span> <span data-ttu-id="1b79a-143">这将立即生成报表快照，以便在计划的开始时间之前提供该报表。</span><span class="sxs-lookup"><span data-stu-id="1b79a-143">This generates the report snapshot right away to make it available before the scheduled start time.</span></span>  
  
 <span data-ttu-id="1b79a-144">**报表执行超时**</span><span class="sxs-lookup"><span data-stu-id="1b79a-144">**Report Execution Timeout**</span></span>  
 <span data-ttu-id="1b79a-145">指定在给定的秒数之后报表处理是否超时。</span><span class="sxs-lookup"><span data-stu-id="1b79a-145">Specify whether report processing times out after a certain number of seconds.</span></span> <span data-ttu-id="1b79a-146">如果选择默认设置，则会将“站点设置”页中指定的超时设置用于此报表。</span><span class="sxs-lookup"><span data-stu-id="1b79a-146">If you choose the default setting, the timeout setting that is specified in the Site Settings page is used for this report.</span></span>  
  
 <span data-ttu-id="1b79a-147">此值应用于报表服务器上的报表处理。</span><span class="sxs-lookup"><span data-stu-id="1b79a-147">This value applies to report processing on a report server.</span></span> <span data-ttu-id="1b79a-148">它不会设置向报表提供数据的数据库服务器上的数据处理超时值。</span><span class="sxs-lookup"><span data-stu-id="1b79a-148">It does not set a timeout for data processing on the database server that provides the data for your report.</span></span> <span data-ttu-id="1b79a-149">但是，所指定的值必须足以完成数据处理和报表处理。</span><span class="sxs-lookup"><span data-stu-id="1b79a-149">However, the value that you specify must be enough to complete both data processing and report processing.</span></span> <span data-ttu-id="1b79a-150">报表处理的计时从选中报表时开始，到打开报表时结束。</span><span class="sxs-lookup"><span data-stu-id="1b79a-150">The count for report processing begins when the report is selected and ends when the report opens.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b79a-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b79a-151">See Also</span></span>  
 <span data-ttu-id="1b79a-152">[设置报表处理属性](report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1b79a-152">[Set Report Processing Properties](report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="1b79a-153">[缓存报表 (SSRS)](report-server/caching-reports-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1b79a-153">[Caching Reports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span></span>  
 <span data-ttu-id="1b79a-154">[创建、修改和删除计划](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="1b79a-154">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="1b79a-155">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="1b79a-155">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
