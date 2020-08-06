---
title: DataSources 和 DataSets 集合引用（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f951a4aa-da55-4e43-8579-4a5d4480d11f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 560a42daf4d4580adde5b6100fe23f2c646fff08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590074"
---
# <a name="datasources-and-datasets-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="ab34c-102">DataSources 和 DataSets 集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ab34c-102">DataSources and DataSets Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ab34c-103">`DataSources` 集合表示在报表中使用的所有数据源。</span><span class="sxs-lookup"><span data-stu-id="ab34c-103">The `DataSources` collection represents all the data sources used in a report.</span></span> <span data-ttu-id="ab34c-104">同样，`DataSets` 集合表示报表中所有数据源的所有数据集。</span><span class="sxs-lookup"><span data-stu-id="ab34c-104">Similarly, the `DataSets` collection represents all the datasets for all the data sources in a report.</span></span> <span data-ttu-id="ab34c-105">使用 **“报表数据”** 窗格显示报表数据集的层次结构视图，报表数据集按照它们所引用的数据源组织。</span><span class="sxs-lookup"><span data-stu-id="ab34c-105">Use the **Report Data** pane for a hierarchical view of report datasets organized under the data source they reference.</span></span> <span data-ttu-id="ab34c-106">如果这些集合中包含引用，则在预览报表时将不会看到值。</span><span class="sxs-lookup"><span data-stu-id="ab34c-106">If you include references to these collections, you will not see values when previewing your report.</span></span> <span data-ttu-id="ab34c-107">这些集合只有在将报表发布到报表服务器之后才可用。</span><span class="sxs-lookup"><span data-stu-id="ab34c-107">These collections are only available after the report has been published to a report server.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="datasources"></a><span data-ttu-id="ab34c-108">DataSources</span><span class="sxs-lookup"><span data-stu-id="ab34c-108">DataSources</span></span>  
 <span data-ttu-id="ab34c-109">`DataSources` 集合表示在已发布的报表定义中引用的数据源。</span><span class="sxs-lookup"><span data-stu-id="ab34c-109">The `DataSources` collection represents the data sources referenced in a published report definition.</span></span> <span data-ttu-id="ab34c-110">您可以选择将此信息包括在报表中，以记录报表数据源。</span><span class="sxs-lookup"><span data-stu-id="ab34c-110">You may choose to include this information in your report to document the source of the report data.</span></span> <span data-ttu-id="ab34c-111">此集合在 **“预览”** 模式下不可用。</span><span class="sxs-lookup"><span data-stu-id="ab34c-111">This collection is not available in **Preview** mode.</span></span> <span data-ttu-id="ab34c-112">下表对 `DataSources` 集合中的变量进行了说明。</span><span class="sxs-lookup"><span data-stu-id="ab34c-112">The following table describes the variables within the `DataSources` collection.</span></span>  
  
|<span data-ttu-id="ab34c-113">**变量**</span><span class="sxs-lookup"><span data-stu-id="ab34c-113">**Variable**</span></span>|`Type`|<span data-ttu-id="ab34c-114">**说明**</span><span class="sxs-lookup"><span data-stu-id="ab34c-114">**Description**</span></span>|  
|------------------|--------------|---------------------|  
|`DataSourceReference`|`String`|<span data-ttu-id="ab34c-115">报表服务器上数据源定义的完整路径。</span><span class="sxs-lookup"><span data-stu-id="ab34c-115">The full path of the data source definition on the report server.</span></span> <span data-ttu-id="ab34c-116">例如，可以包括用作部分报表历史记录的报表中的所有数据源列表。</span><span class="sxs-lookup"><span data-stu-id="ab34c-116">For example, you might include a list of all the data sources a report used as part of a report history.</span></span> <span data-ttu-id="ab34c-117">下面的示例显示名为 AdventureWorks2012 的数据源的完整路径：</span><span class="sxs-lookup"><span data-stu-id="ab34c-117">The following example shows the full path for the data source named AdventureWorks2012:</span></span><br /><br /> <span data-ttu-id="ab34c-118">`/DataSources/AdventureWorks2012`.</span><span class="sxs-lookup"><span data-stu-id="ab34c-118">`/DataSources/AdventureWorks2012`.</span></span>|  
|`Type`|`String`|<span data-ttu-id="ab34c-119">数据源数据访问接口的类型。</span><span class="sxs-lookup"><span data-stu-id="ab34c-119">The type of data provider for the data source.</span></span> <span data-ttu-id="ab34c-120">例如，`SQL`。</span><span class="sxs-lookup"><span data-stu-id="ab34c-120">For example, `SQL`.</span></span>|  
  
## <a name="datasets"></a><span data-ttu-id="ab34c-121">DataSets</span><span class="sxs-lookup"><span data-stu-id="ab34c-121">DataSets</span></span>  
 <span data-ttu-id="ab34c-122">`DataSets` 集合表示在报表定义中引用的数据集。</span><span class="sxs-lookup"><span data-stu-id="ab34c-122">The `DataSets` collection represents the datasets referenced in a report definition.</span></span> <span data-ttu-id="ab34c-123">您可以在文本框中选择包括报表查询，以便希望知道报表中确切数据的用户可以看到原始命令文本。</span><span class="sxs-lookup"><span data-stu-id="ab34c-123">You may choose to include the query in the report in a text box, so a user interested in exactly which data is in the report can see the original command text.</span></span> <span data-ttu-id="ab34c-124">此集合在 **“预览”** 模式下不可用。</span><span class="sxs-lookup"><span data-stu-id="ab34c-124">This collection is not available in **Preview** mode.</span></span> <span data-ttu-id="ab34c-125">下表对 `DataSets` 集合的成员进行了说明。</span><span class="sxs-lookup"><span data-stu-id="ab34c-125">The following table describes the members of the `DataSets` collection.</span></span>  
  
|<span data-ttu-id="ab34c-126">**成员**</span><span class="sxs-lookup"><span data-stu-id="ab34c-126">**Member**</span></span>|`Type`|<span data-ttu-id="ab34c-127">**说明**</span><span class="sxs-lookup"><span data-stu-id="ab34c-127">**Description**</span></span>|  
|----------------|--------------|---------------------|  
|`CommandText`|`String`|<span data-ttu-id="ab34c-128">对于数据库数据源，为用于从数据源中检索数据的查询。</span><span class="sxs-lookup"><span data-stu-id="ab34c-128">For database data sources, this is the query used to retrieve data from the data source.</span></span> <span data-ttu-id="ab34c-129">如果查询是一个表达式，则为计算的表达式。</span><span class="sxs-lookup"><span data-stu-id="ab34c-129">If the query is an expression, this is the evaluated expression.</span></span>|  
|`RewrittenCommandText`|`String`|<span data-ttu-id="ab34c-130">数据访问接口的扩展 CommandText 值。</span><span class="sxs-lookup"><span data-stu-id="ab34c-130">The data provider's expanded CommandText value.</span></span> <span data-ttu-id="ab34c-131">它通常用于报表，其中查询参数映射到报表参数。</span><span class="sxs-lookup"><span data-stu-id="ab34c-131">This is typically used for reports with query parameters that are mapped to report parameters.</span></span> <span data-ttu-id="ab34c-132">将命令文本参数引用扩展到为映射的报表参数选中的常量值时，此数据访问接口将设置此属性。</span><span class="sxs-lookup"><span data-stu-id="ab34c-132">The data provider sets this property when expanding the command text parameter references into the constant values selected for the mapped report parameters.</span></span>|  
  
### <a name="using-query-expressions"></a><span data-ttu-id="ab34c-133">使用查询表达式</span><span class="sxs-lookup"><span data-stu-id="ab34c-133">Using Query Expressions</span></span>  
 <span data-ttu-id="ab34c-134">可使用表达式定义包含在数据集中的查询。</span><span class="sxs-lookup"><span data-stu-id="ab34c-134">You can use expressions to define the query that is contained in a dataset.</span></span> <span data-ttu-id="ab34c-135">您可以使用此功能来设计报表，报表中的查询可以根据用户的输入、其他数据集中的数据或其他变量进行更改。</span><span class="sxs-lookup"><span data-stu-id="ab34c-135">You can use this feature to design reports in which the query changes based on input from the user, data in other datasets, or other variables.</span></span> <span data-ttu-id="ab34c-136">有关查询的详细信息，请参阅[报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ab34c-136">For more information about queries, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab34c-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab34c-137">See Also</span></span>  
 <span data-ttu-id="ab34c-138">[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ab34c-138">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ab34c-139">表达式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ab34c-139">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
