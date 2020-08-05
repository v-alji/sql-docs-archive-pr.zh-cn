---
title: "\" (存储选项\" 对话框中的通知)  (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.notifications.f1
ms.assetid: 5675cdbf-bfaa-4b6e-b716-31b8e9da72b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 62e2a00c2b8dd5d2b0a5f3faae71f477de436e69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579839"
---
# <a name="notifications-storage-options-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="23642-102">通知（“存储选项”对话框）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="23642-102">Notifications (Storage Options Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="23642-103">可以使用 **中的** “存储选项” **对话框上的** “通知” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 选项卡，设置维度、多维数据集、度量值组或分区的通知方法和相关设置。</span><span class="sxs-lookup"><span data-stu-id="23642-103">Use the **Notifications** tab of the **Storage Options** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to set the notification method and related settings for a dimension, cube, measure group, or partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23642-104">您必须熟悉存储模式和主动缓存功能，才可以修改这些设置。</span><span class="sxs-lookup"><span data-stu-id="23642-104">You should be familiar with storage mode and proactive caching functionality before modifying these settings.</span></span> <span data-ttu-id="23642-105">有关详细信息，请参阅[主动缓存（分区）](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)。</span><span class="sxs-lookup"><span data-stu-id="23642-105">For more information, see [Proactive Caching &#40;Partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="23642-106">选项</span><span class="sxs-lookup"><span data-stu-id="23642-106">Options</span></span>  
  
|<span data-ttu-id="23642-107">术语</span><span class="sxs-lookup"><span data-stu-id="23642-107">Term</span></span>|<span data-ttu-id="23642-108">定义</span><span class="sxs-lookup"><span data-stu-id="23642-108">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="23642-109">**存储模式**</span><span class="sxs-lookup"><span data-stu-id="23642-109">**Storage mode**</span></span>|<span data-ttu-id="23642-110">选择对象要使用的存储模式。</span><span class="sxs-lookup"><span data-stu-id="23642-110">Selects the storage mode to use for the object.</span></span><br /><br /> <span data-ttu-id="23642-111">**MOLAP**</span><span class="sxs-lookup"><span data-stu-id="23642-111">**MOLAP**</span></span><br /> <span data-ttu-id="23642-112">对象使用多维 OLAP (MOLAP) 存储。</span><span class="sxs-lookup"><span data-stu-id="23642-112">The object uses multidimensional OLAP (MOLAP) storage.</span></span><br /><br /> <span data-ttu-id="23642-113">**HOLAP**</span><span class="sxs-lookup"><span data-stu-id="23642-113">**HOLAP**</span></span><br /> <span data-ttu-id="23642-114">对象使用混合 OLAP (HOLAP) 存储。</span><span class="sxs-lookup"><span data-stu-id="23642-114">The object uses hybrid OLAP (HOLAP) storage.</span></span><br /><br /> <span data-ttu-id="23642-115">**ROLAP**</span><span class="sxs-lookup"><span data-stu-id="23642-115">**ROLAP**</span></span><br /> <span data-ttu-id="23642-116">对象使用关系 OLAP (ROLAP) 存储。</span><span class="sxs-lookup"><span data-stu-id="23642-116">The object uses relational OLAP (ROLAP) storage.</span></span>|  
|<span data-ttu-id="23642-117">**启用主动缓存**</span><span class="sxs-lookup"><span data-stu-id="23642-117">**Enable proactive caching**</span></span>|<span data-ttu-id="23642-118">启用主动缓存。</span><span class="sxs-lookup"><span data-stu-id="23642-118">Enables proactive caching.</span></span><br /><br /> <span data-ttu-id="23642-119">注意：如果未选择此选项，则将禁用除“存储模式” \*\*\*\* 外的所有选项。</span><span class="sxs-lookup"><span data-stu-id="23642-119">Note: If this option is not selected, all options except **Storage mode** are disabled.</span></span>|  
|<span data-ttu-id="23642-120">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="23642-120">**SQL Server**</span></span>|<span data-ttu-id="23642-121">使用上的专用跟踪机制 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 来标识对象的基础表的更改。</span><span class="sxs-lookup"><span data-stu-id="23642-121">Uses a specialized trace mechanism on [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to identify changes to underlying tables for the object.</span></span>|  
|<span data-ttu-id="23642-122">**指定跟踪表**</span><span class="sxs-lookup"><span data-stu-id="23642-122">**Specify tracking tables**</span></span>|<span data-ttu-id="23642-123">为对象指定要跟踪的基础表，然后键入表的列表并使用分号 (;) 字符进行分隔，或单击省略号按钮 (**...**) 以打开“关系对象”\*\*\*\* 对话框并选择要跟踪的表。</span><span class="sxs-lookup"><span data-stu-id="23642-123">Specify the underlying tables to be tracked for the object, then type a list of tables delimited by semi-colon (;) characters or click the ellipsis button (**...**) to open the **Relational Objects** dialog box and choose the tables to be tracked.</span></span> <span data-ttu-id="23642-124">有关详细信息，请参阅[“关系对象”对话框（Analysis Services - 多维数据）](relational-objects-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="23642-124">For more information, see [Relational Objects Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="23642-125">如果未选中此选项，在满足特定要求的情况下， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将尝试为对象确定要跟踪的基础表的列表。</span><span class="sxs-lookup"><span data-stu-id="23642-125">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tries to determine the list of underlying tables to be tracked for the object, if certain requirements are met.</span></span> <span data-ttu-id="23642-126">有关这些要求的详细信息，请参阅[主动缓存（分区）](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)。</span><span class="sxs-lookup"><span data-stu-id="23642-126">For more information about these requirements, see [Proactive Caching &#40;Partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).</span></span>|  
|<span data-ttu-id="23642-127">**已启动的客户端**</span><span class="sxs-lookup"><span data-stu-id="23642-127">**Client initiated**</span></span>|<span data-ttu-id="23642-128">选择此选项可以使用 XML for Analysis (XMLA) 命令 `NotifyTableChange`，以标识对象的基础表的更改。</span><span class="sxs-lookup"><span data-stu-id="23642-128">Select to use the XML for Analysis (XMLA) command, `NotifyTableChange`, to identify changes to underlying tables for the object.</span></span> <span data-ttu-id="23642-129">如果计划使用基于客户端的通知过程，通常应选择此选项。</span><span class="sxs-lookup"><span data-stu-id="23642-129">This option is typically selected if you plan to use a client-based notification process.</span></span>|  
|<span data-ttu-id="23642-130">**指定跟踪表**</span><span class="sxs-lookup"><span data-stu-id="23642-130">**Specify tracking tables**</span></span>|<span data-ttu-id="23642-131">选择此选项可以为对象指定要跟踪的基础表，然后键入表的列表并使用分号 (;) 字符进行分隔，或单击省略号按钮 (**...**) 以打开“关系对象”\*\*\*\* 对话框并选择要跟踪的表。</span><span class="sxs-lookup"><span data-stu-id="23642-131">Select to specify the underlying tables to be tracked for the object, then type a list of tables delimited by semi-colon (;) characters or click the ellipsis button (**...**) to open the **Relational Objects** dialog box and choose the tables to be tracked.</span></span> <span data-ttu-id="23642-132">有关详细信息，请参阅[“关系对象”对话框（Analysis Services - 多维数据）](relational-objects-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="23642-132">For more information, see [Relational Objects Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="23642-133">如果未选中此选项，在满足特定要求的情况下， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将尝试为对象确定要跟踪的基础表的列表。</span><span class="sxs-lookup"><span data-stu-id="23642-133">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tries to determine the list of underlying tables to be tracked for the object, if certain requirements are met.</span></span> <span data-ttu-id="23642-134">有关这些要求的详细信息，请参阅[主动缓存（分区）](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)。</span><span class="sxs-lookup"><span data-stu-id="23642-134">For more information about these requirements, see [Proactive Caching &#40;Partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).</span></span>|  
|<span data-ttu-id="23642-135">**按计划轮询**</span><span class="sxs-lookup"><span data-stu-id="23642-135">**Scheduled polling**</span></span>|<span data-ttu-id="23642-136">使用轮询机制，通过对相应对象的基础表运行一系列查询以标识更改。</span><span class="sxs-lookup"><span data-stu-id="23642-136">Uses a polling mechanism to identify changes by running a series of queries on the underlying tables for the object.</span></span>|  
|<span data-ttu-id="23642-137">**轮询间隔**</span><span class="sxs-lookup"><span data-stu-id="23642-137">**Polling interval**</span></span>|<span data-ttu-id="23642-138">指定时间间隔和单位， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在此时间段之后才会执行轮询网格中定义的轮询查询和处理查询。</span><span class="sxs-lookup"><span data-stu-id="23642-138">Specifies the interval and units of time for the period that should pass before [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] executes the polling queries and processing queries defined in the polling grid.</span></span>|  
|<span data-ttu-id="23642-139">**启用增量更新**</span><span class="sxs-lookup"><span data-stu-id="23642-139">**Enable incremental updates**</span></span>|<span data-ttu-id="23642-140">基于一组专用于只标识追加数据的轮询查询和处理查询，增量更新对象的 MOLAP 缓存。</span><span class="sxs-lookup"><span data-stu-id="23642-140">Incrementally updates the MOLAP cache for an object based on a set of polling and processing queries designed to identify only additional data.</span></span> <span data-ttu-id="23642-141">如果选择此选项，轮询查询将与数据源视图中的一个表标识符相关联。</span><span class="sxs-lookup"><span data-stu-id="23642-141">If this option is selected, the polling query is associated with a table identifier in the data source view.</span></span> <span data-ttu-id="23642-142">随后，系统会使用处理查询将轮询查询的当前值与上次所执行轮询查询的存储值进行比较，以标识更改。</span><span class="sxs-lookup"><span data-stu-id="23642-142">The processing query is then used to compare the current value of the polling query with the stored value of the previously executed polling query to identify changes.</span></span><br /><br /> <span data-ttu-id="23642-143">如果未选择此选项，则会完全更新 MOLAP 缓存。</span><span class="sxs-lookup"><span data-stu-id="23642-143">If this option is not selected, the MOLAP cache is fully updated.</span></span> <span data-ttu-id="23642-144">系统将使用轮询查询来标识已发生更改，而不需要使用处理查询或表标识符。</span><span class="sxs-lookup"><span data-stu-id="23642-144">The polling query is used to identify that a change has occurred, and no processing query or table identifier is required.</span></span>|  
|<span data-ttu-id="23642-145">**轮询网格**</span><span class="sxs-lookup"><span data-stu-id="23642-145">**Polling grid**</span></span>|<span data-ttu-id="23642-146">包含 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 使用的轮询查询、处理查询和表标识符，这些查询及标识符用于轮询数据源和标识对象基础表的更改。</span><span class="sxs-lookup"><span data-stu-id="23642-146">Contains the polling queries, processing queries, and table identifiers used by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to poll the data source and identify changes to underlying tables for the object.</span></span> <span data-ttu-id="23642-147">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="23642-147">The grid contains the following columns:</span></span><br /><br /> <span data-ttu-id="23642-148">**轮询查询**：键入按轮询间隔执行的单独查询，以标识对对象的更改，或单击省略号按钮 " (**...** ") 打开 "**创建轮询查询**" 对话框并定义单独查询。</span><span class="sxs-lookup"><span data-stu-id="23642-148">**Polling query**: Type the singleton query executed at the polling interval to identify changes for the object, or click the ellipsis button (**...**) to open the **Create Polling Query** dialog box and define the singleton query.</span></span> <span data-ttu-id="23642-149">有关详细信息，请参阅[“创建轮询查询”对话框（Analysis Services - 多维数据）](create-polling-query-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="23642-149">For more information, see [Create Polling Query Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](create-polling-query-dialog-box-analysis-services-multidimensional-data.md).</span></span> <span data-ttu-id="23642-150">如果选择了 **“启用增量更新”** ，轮询查询应返回标识添加到 **“表”** 中所标识表的最后一条记录的值。</span><span class="sxs-lookup"><span data-stu-id="23642-150">If **Enable incremental updates** is selected, the polling query should return a value that identifies the last record added to the table identified in **Table**.</span></span> <span data-ttu-id="23642-151">如果未选择 **“启用增量更新”** ，轮询查询应返回标识表中当前记录数的值。</span><span class="sxs-lookup"><span data-stu-id="23642-151">If **Enable incremental updates** is not selected, the polling query should return a value that identifies the current number of records in the table.</span></span><br /><br /> <span data-ttu-id="23642-152">**处理查询**：键入按轮询间隔执行的用于从 "**表**" 中所标识表检索新记录的查询，或单击省略号按钮 " (**...** ") 打开 "**创建处理查询**" 对话框并定义查询。</span><span class="sxs-lookup"><span data-stu-id="23642-152">**Processing query**: Type the query executed at the polling interval to retrieve new records from the table identified in **Table**, or click the ellipsis button (**...**) to open the **Create Processing Query** dialog box and define the query.</span></span> <span data-ttu-id="23642-153">有关详细信息，请参阅[“创建处理查询”对话框（Analysis Services - 多维数据）](create-processing-query-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="23642-153">For more information, see [Create Processing Query Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](create-processing-query-dialog-box-analysis-services-multidimensional-data.md).</span></span> <span data-ttu-id="23642-154">应将查询参数化以接受两个参数，即 "**轮询查询**" 中的查询返回的以前值和 "**轮询查询**" 中查询返回的当前值-可用于识别并仅提取在轮询期间添加的记录。</span><span class="sxs-lookup"><span data-stu-id="23642-154">The query should be parameterized to accept two parameters-the previous value returned by the query in **Polling query** and the current value returned by the query in **Polling query**-that can be used to identify and extract only the records that have been added during the polling period.</span></span> <span data-ttu-id="23642-155">请注意，只有在选择了“启用增量更新” \*\*\*\* 时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="23642-155">Note that this option is enabled only if **Enable incremental updates** is selected.</span></span><br /><br /> <span data-ttu-id="23642-156">**表**：键入 "**轮询查询**" 中的查询跟踪其最后一条记录的表的标识符，或单击省略号按钮 " (**...** ") 以打开 "**查找表**" 对话框并选择表。</span><span class="sxs-lookup"><span data-stu-id="23642-156">**Table**: Type the identifier of the table against which the query in **Polling query** tracks the last record, or click the ellipsis button (**...**) to open the **Find Table** dialog box and select the table.</span></span> <span data-ttu-id="23642-157">有关详细信息，请参阅[“查找表”对话框（Analysis Services - 多维数据）](find-table-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="23642-157">For more information, see [Find Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23642-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23642-158">See Also</span></span>  
 [<span data-ttu-id="23642-159">"存储选项" 对话框 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="23642-159">Storage Options Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](storage-options-dialog-box-analysis-services-multidimensional-data.md)  
  
  