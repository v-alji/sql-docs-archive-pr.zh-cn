---
title: 在报表生成器中预览报表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75b822b318991299c979553ec4baa05005535362
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577352"
---
# <a name="previewing-reports-in-report-builder"></a><span data-ttu-id="3cd46-102">在报表生成器中预览报表</span><span class="sxs-lookup"><span data-stu-id="3cd46-102">Previewing Reports in Report Builder</span></span>
  <span data-ttu-id="3cd46-103">当您创建报表时，经常预览报表以验证报表显示您所需的内容会非常有用。</span><span class="sxs-lookup"><span data-stu-id="3cd46-103">While you create a report, it is helpful to preview the report often to verify that the report displays what you want.</span></span> <span data-ttu-id="3cd46-104">若要预览报表，请单击 **“运行”**。</span><span class="sxs-lookup"><span data-stu-id="3cd46-104">To preview your report, click **Run**.</span></span> <span data-ttu-id="3cd46-105">报表将在预览模式下呈现。</span><span class="sxs-lookup"><span data-stu-id="3cd46-105">The report renders in preview mode.</span></span>  
  
 <span data-ttu-id="3cd46-106">报表生成器通过在连接到报表服务器时使用编辑会话改进了预览体验。</span><span class="sxs-lookup"><span data-stu-id="3cd46-106">Report Builder improves the preview experience by using edit sessions when connected to a report server.</span></span> <span data-ttu-id="3cd46-107">编辑会话创建数据缓存，并使缓存中的数据集可用于重复性的报表预览。</span><span class="sxs-lookup"><span data-stu-id="3cd46-107">The edit session creates a data cache and makes the datasets in the cache available for repeated report previews.</span></span> <span data-ttu-id="3cd46-108">编辑会话并不是一种您可以直接与之交互的功能，但了解何时刷新缓存的数据集将帮助您改进预览报表时的性能并理解报表呈现变快或变慢的原因。</span><span class="sxs-lookup"><span data-stu-id="3cd46-108">An edit session is not a feature that you interact with directly, but understanding when the cached dataset is refreshed will help you improve performance when you preview a report and understand why the report renders faster or slower.</span></span>  
  
 <span data-ttu-id="3cd46-109">编辑会话的其他优点包括可以编辑使用嵌入数据源或引用项（如存储在报表服务器上的图像或子报表）的报表。</span><span class="sxs-lookup"><span data-stu-id="3cd46-109">Other benefits of edit sessions are the abilities to edit reports that use embedded data sources or reference items such as images or subreports that are stored on the report server.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="improving-preview-performance"></a><span data-ttu-id="3cd46-110">改进预览性能</span><span class="sxs-lookup"><span data-stu-id="3cd46-110">Improving Preview Performance</span></span>  
 <span data-ttu-id="3cd46-111">您创建和更新报表的方式影响报表在预览中呈现的速度。</span><span class="sxs-lookup"><span data-stu-id="3cd46-111">How you create and update reports affects how fast the report renders in preview.</span></span> <span data-ttu-id="3cd46-112">当您首次预览依赖于服务器引用的报表时，将为您创建一个编辑会话，并且将在报表运行时使用的数据添加到存储在报表服务器上的数据缓存中。</span><span class="sxs-lookup"><span data-stu-id="3cd46-112">The first time that you preview a report that relies on a server reference, an edit session is created for you and the data used when the report is run is added to a data cache that is stored on the report server.</span></span> <span data-ttu-id="3cd46-113">当您对报表进行不影响数据的更改时，报表将使用数据的缓存副本。</span><span class="sxs-lookup"><span data-stu-id="3cd46-113">When you make changes to the report that does not affect the data, the cached copy of the data is used by the report.</span></span> <span data-ttu-id="3cd46-114">这意味着，您每次预览报表时将看不到数据更改。</span><span class="sxs-lookup"><span data-stu-id="3cd46-114">This means that you will not see data change each time you preview the report.</span></span> <span data-ttu-id="3cd46-115">如果您需要新数据，请单击功能区上的 **“刷新”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="3cd46-115">If you want new data, click the **Refresh** button on the ribbon.</span></span>  
  
 <span data-ttu-id="3cd46-116">下面的操作会导致刷新缓存，并减慢您下一次预览报表时的报表呈现速度。</span><span class="sxs-lookup"><span data-stu-id="3cd46-116">The following actions cause the cache to be refreshed and slow down report rendering the next time you preview the report:</span></span>  
  
-   <span data-ttu-id="3cd46-117">添加、更改或删除数据集。</span><span class="sxs-lookup"><span data-stu-id="3cd46-117">Add, change, or delete a dataset.</span></span> <span data-ttu-id="3cd46-118">缓存的数据集包含报表使用的所有数据集，对任何数据集进行修改都会使缓存的数据集变为无效。</span><span class="sxs-lookup"><span data-stu-id="3cd46-118">The cached dataset contains all the datasets that a report uses and modification to any dataset invalidates the cached dataset.</span></span> <span data-ttu-id="3cd46-119">这包括在数据集中更改名称、查询或字段。</span><span class="sxs-lookup"><span data-stu-id="3cd46-119">This includes changing the name, query, or fields in the dataset.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3cd46-120">如果数据集包含大量您预期不会使用的字段，则应考虑更新数据集以忽略这些字段。</span><span class="sxs-lookup"><span data-stu-id="3cd46-120">If the dataset has a large number of fields that you do not expect to use, you should consider updating the dataset to omit those fields.</span></span> <span data-ttu-id="3cd46-121">尽管这会创建新的编辑会话并且报表的第一次预览将变慢，但缓存数据集较小对于报表服务器的性能而言总体上是有利的。</span><span class="sxs-lookup"><span data-stu-id="3cd46-121">Although this creates a new edit session and the first preview of the report is slower, there smaller cached dataset is overall beneficial to the performance of the report server.</span></span>  
  
-   <span data-ttu-id="3cd46-122">添加、更改或删除数据源。</span><span class="sxs-lookup"><span data-stu-id="3cd46-122">Add, change, or delete a data source.</span></span> <span data-ttu-id="3cd46-123">这包括更改数据源的名称或属性、数据源的数据扩展或与数据源的连接的属性。</span><span class="sxs-lookup"><span data-stu-id="3cd46-123">This includes changing the name or properties of the data source, the data extension of the data source, or the properties of the connection to the data source.</span></span>  
  
-   <span data-ttu-id="3cd46-124">将报表使用的共享数据源更改为其他数据源。</span><span class="sxs-lookup"><span data-stu-id="3cd46-124">Change the shared data source that the report uses to a different data source.</span></span>  
  
-   <span data-ttu-id="3cd46-125">更改报表的语言。</span><span class="sxs-lookup"><span data-stu-id="3cd46-125">Change the language of the report.</span></span>  
  
-   <span data-ttu-id="3cd46-126">更改报表使用的程序集或自定义代码。</span><span class="sxs-lookup"><span data-stu-id="3cd46-126">Change the assemblies or custom code that the report uses.</span></span>  
  
-   <span data-ttu-id="3cd46-127">添加、更改或删除报表中的查询参数或参数值。</span><span class="sxs-lookup"><span data-stu-id="3cd46-127">Add, change, or delete the query parameters in the report or parameter values.</span></span>  
  
 <span data-ttu-id="3cd46-128">对于报表布局和数据格式的更改不影响缓存的数据集。</span><span class="sxs-lookup"><span data-stu-id="3cd46-128">Changes to the report layout and data formatting do not affect the cached dataset.</span></span> <span data-ttu-id="3cd46-129">您可以执行以下操作，而不刷新缓存的数据集：</span><span class="sxs-lookup"><span data-stu-id="3cd46-129">You can do the following actions without refreshing the cached dataset:</span></span>  
  
-   <span data-ttu-id="3cd46-130">添加或删除数据区域，例如表、矩阵或图表。</span><span class="sxs-lookup"><span data-stu-id="3cd46-130">Add or remove data regions such as tables, matrices or charts.</span></span>  
  
-   <span data-ttu-id="3cd46-131">在报表中添加或删除列。</span><span class="sxs-lookup"><span data-stu-id="3cd46-131">Add or delete columns from the report.</span></span> <span data-ttu-id="3cd46-132">数据集中的所有字段均可用于报表中。</span><span class="sxs-lookup"><span data-stu-id="3cd46-132">All the fields in the dataset are available to use in the report.</span></span> <span data-ttu-id="3cd46-133">在报表中添加或删除字段对数据集没有任何影响。</span><span class="sxs-lookup"><span data-stu-id="3cd46-133">Adding or removing fields in the report has no effect on the dataset.</span></span>  
  
-   <span data-ttu-id="3cd46-134">更改表和矩阵中的字段顺序。</span><span class="sxs-lookup"><span data-stu-id="3cd46-134">Change the order of fields in tables and matrices.</span></span>  
  
-   <span data-ttu-id="3cd46-135">添加、更改或删除行组和列组。</span><span class="sxs-lookup"><span data-stu-id="3cd46-135">Add, change, or delete row and column groups.</span></span>  
  
-   <span data-ttu-id="3cd46-136">添加、更改或删除字段中数据值的格式。</span><span class="sxs-lookup"><span data-stu-id="3cd46-136">Add, change, or delete formatting of data values in fields.</span></span>  
  
-   <span data-ttu-id="3cd46-137">添加、更改或删除图像、线条或文本框。</span><span class="sxs-lookup"><span data-stu-id="3cd46-137">Add, change, or delete images, lines, or text boxes.</span></span>  
  
-   <span data-ttu-id="3cd46-138">更改分页符。</span><span class="sxs-lookup"><span data-stu-id="3cd46-138">Change page breaks.</span></span>  
  
 <span data-ttu-id="3cd46-139">您首次预览报表时，将创建编辑会话。</span><span class="sxs-lookup"><span data-stu-id="3cd46-139">The edit session is created the first time that you preview a report.</span></span> <span data-ttu-id="3cd46-140">默认情况下，编辑会话持续 7200 秒（2 小时）。</span><span class="sxs-lookup"><span data-stu-id="3cd46-140">By default, an edit session lasts 7200 seconds (2 hours).</span></span> <span data-ttu-id="3cd46-141">每次运行报表时，此会话重置为两小时。</span><span class="sxs-lookup"><span data-stu-id="3cd46-141">The session is reset to two hours every time you run the report.</span></span> <span data-ttu-id="3cd46-142">当编辑会话到期时，将删除数据缓存。</span><span class="sxs-lookup"><span data-stu-id="3cd46-142">When the edit session expires, the data cache is deleted.</span></span> <span data-ttu-id="3cd46-143">如果编辑会话到期，当您下一次预览报表时，将自动再次创建一个编辑会话。</span><span class="sxs-lookup"><span data-stu-id="3cd46-143">If the edit session expires, one is automatically created again the next time that you preview the report.</span></span> <span data-ttu-id="3cd46-144">可以配置编辑会话的到期时间。</span><span class="sxs-lookup"><span data-stu-id="3cd46-144">The expiration time for edit sessions is configurable.</span></span> <span data-ttu-id="3cd46-145">如果您发现两个小时过长或过短，则与报表服务器管理员联系。</span><span class="sxs-lookup"><span data-stu-id="3cd46-145">If you find that two hours is too long or too short, contact the administrator of the report server.</span></span>  
  
 <span data-ttu-id="3cd46-146">默认情况下，数据缓存可以容纳多达五个数据集。</span><span class="sxs-lookup"><span data-stu-id="3cd46-146">By default, the data cache can hold up to five datasets.</span></span> <span data-ttu-id="3cd46-147">如果您使用参数值的多种不同组合，则报表可能需要更多数据。</span><span class="sxs-lookup"><span data-stu-id="3cd46-147">If you use many different combinations of parameter values, the report might need more data.</span></span> <span data-ttu-id="3cd46-148">这要求刷新缓存，并且当您下一次预览报表时，报表呈现将变慢。</span><span class="sxs-lookup"><span data-stu-id="3cd46-148">This requires the cache be refreshed and the report renders more slowly the next time that you preview it.</span></span> <span data-ttu-id="3cd46-149">缓存中的条目数可以由报表服务器的管理员进行配置。</span><span class="sxs-lookup"><span data-stu-id="3cd46-149">The number of entries in the cache is configurable by the administrator of the report server.</span></span>  
  
## <a name="concurrency-of-report-updates"></a><span data-ttu-id="3cd46-150">报表更新的并发性</span><span class="sxs-lookup"><span data-stu-id="3cd46-150">Concurrency of Report Updates</span></span>  
 <span data-ttu-id="3cd46-151">您经常将预览报表作为更新报表而后将其保存到报表服务器的过程的一个步骤。</span><span class="sxs-lookup"><span data-stu-id="3cd46-151">Frequently, you preview a report as a step in updating and then saving a report to a report server.</span></span> <span data-ttu-id="3cd46-152">当您更新报表时，可能其他人同时正在更新和保存报表。</span><span class="sxs-lookup"><span data-stu-id="3cd46-152">When you are updating a report, it is possible that someone else is updating and then saving the report at the same time.</span></span> <span data-ttu-id="3cd46-153">最后保存的报表是可供将来查看和更新的报表版本。</span><span class="sxs-lookup"><span data-stu-id="3cd46-153">The report that is saved last is the version of report that is available for future viewing and updating.</span></span> <span data-ttu-id="3cd46-154">这意味着您预览的报表版本可能并不是您重新打开的版本。</span><span class="sxs-lookup"><span data-stu-id="3cd46-154">This means that the version of the report that you previewed might not be the version you reopen.</span></span> <span data-ttu-id="3cd46-155">您可以使用“报表生成器”菜单上的 **“另存为”** 选项，选择使用新名称来保存报表。</span><span class="sxs-lookup"><span data-stu-id="3cd46-155">You have the option to save the report with a new name by using the **Save As** option on the Report Builder menu.</span></span>  
  
## <a name="external-report-items"></a><span data-ttu-id="3cd46-156">外部报表项</span><span class="sxs-lookup"><span data-stu-id="3cd46-156">External Report Items</span></span>  
 <span data-ttu-id="3cd46-157">报表可能包含诸如与报表分开存储的共享数据源、外部图像以及子报表等此类项。</span><span class="sxs-lookup"><span data-stu-id="3cd46-157">Your report might include items such as shared data sources, external images, and subreports that are stored separately from the report.</span></span> <span data-ttu-id="3cd46-158">由于项是单独存储的，因此，可能可以将它们移到报表服务器上的不同位置或删除它们。</span><span class="sxs-lookup"><span data-stu-id="3cd46-158">Because the items are stored separately is possible that they can be moved to a different location on the report server or deleted.</span></span> <span data-ttu-id="3cd46-159">如果发生这种情况，则报表可能无法预览。</span><span class="sxs-lookup"><span data-stu-id="3cd46-159">If this happens, your report could fail to preview.</span></span> <span data-ttu-id="3cd46-160">您可以更新报表以指示更新后的项位置，或者，如果删除了项，则将其替换为现有项，或者从报表中删除对于该项的引用。</span><span class="sxs-lookup"><span data-stu-id="3cd46-160">You can either update the report to indicate the updated location of the item or if the item was deleted, replace it with an existing item, or remove the reference to the item it from the report.</span></span>  
  
 <span data-ttu-id="3cd46-161">如果在创建编辑会话之后更改报表使用的子报表，报表将不呈现在预览中。</span><span class="sxs-lookup"><span data-stu-id="3cd46-161">If a subreport used by your report is changed after your edit session was created, the report will not render in preview.</span></span> <span data-ttu-id="3cd46-162">若要成功预览报表，应保存该报表并单击 **“刷新”** 以获取新数据。</span><span class="sxs-lookup"><span data-stu-id="3cd46-162">To successfully preview the report, you should save the report or click **Refresh** to get fresh data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd46-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3cd46-163">See Also</span></span>  
 <span data-ttu-id="3cd46-164">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3cd46-164">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="3cd46-165">[&#40;报表生成器和 SSRS 的格式设置报表项&#41;](../report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3cd46-165">[Formatting Report Items &#40;Report Builder and SSRS&#41;](../report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3cd46-166">[表、矩阵和列表 &#40;报表生成器和 SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3cd46-166">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3cd46-167">[图表 &#40;报表生成器和 SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3cd46-167">[Charts &#40;Report Builder and SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3cd46-168">[表、矩阵和列表 &#40;报表生成器和 SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3cd46-168">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3cd46-169">保存报表（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="3cd46-169">Saving Reports &#40;Report Builder&#41;</span></span>](saving-reports-report-builder.md)  
  
  
