---
title: 查询数据挖掘架构行集 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- data mining [Analysis Services], queries
- mining model content
- data mining [Analysis Services], schema rowsets
- schema rowsets [Analysis Services], retrieving
- data mining [Analysis Services], troubleshooting
ms.assetid: 442d8c29-07c7-45de-9a15-d556059f68d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: d60c802256454ee68d04392e685fa4acabf6c12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589376"
---
# <a name="querying-the-data-mining-schema-rowsets-analysis-services---data-mining"></a><span data-ttu-id="cabda-102">查询数据挖掘架构行集（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="cabda-102">Querying the Data Mining Schema Rowsets (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="cabda-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，许多现有 OLE DB 数据挖掘架构行集已作为可以使用数据挖掘扩展插件 (DMX) 语句轻松查询的一组系统表公开。</span><span class="sxs-lookup"><span data-stu-id="cabda-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], many of the existing OLE DB data mining schema rowsets are exposed as a set of system tables that you can query by using Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="cabda-104">通过针对数据挖掘架构行集创建查询，可以标识可用的服务，获取您的模型和结构的状态更新，并查找有关模型内容或参数的详细信息。</span><span class="sxs-lookup"><span data-stu-id="cabda-104">By creating queries against the data mining schema rowset, you can identify the services that are available, get updates on the status of your models and structures, and find out details about the model content or parameters.</span></span> <span data-ttu-id="cabda-105">有关数据挖掘架构行集的说明，请参阅 [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)。</span><span class="sxs-lookup"><span data-stu-id="cabda-105">For a description of the data mining schema rowsets, see [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cabda-106">还可以使用 XMLA 来查询数据挖掘架构行集。</span><span class="sxs-lookup"><span data-stu-id="cabda-106">You can also query the data mining schema rowsets by using XMLA.</span></span> <span data-ttu-id="cabda-107">有关如何在 SQL Server Management Studio 中执行此操作的详细信息，请参阅 [使用 XMLA 创建数据挖掘查询](create-a-data-mining-query-by-using-xmla.md)。</span><span class="sxs-lookup"><span data-stu-id="cabda-107">For more information about how to do this in SQL Server Management Studio, see [Create a Data Mining Query by Using XMLA](create-a-data-mining-query-by-using-xmla.md).</span></span>  
  
## <a name="list-of-data-mining-schema-rowsets"></a><span data-ttu-id="cabda-108">数据挖掘架构行集列表</span><span class="sxs-lookup"><span data-stu-id="cabda-108">List of Data Mining Schema Rowsets</span></span>  
 <span data-ttu-id="cabda-109">下表列出了可能对查询和监视有用的数据挖掘架构行集。</span><span class="sxs-lookup"><span data-stu-id="cabda-109">The following table lists the data mining schema rowsets that may be useful for querying and monitoring.</span></span>  
  
|<span data-ttu-id="cabda-110">行集名称</span><span class="sxs-lookup"><span data-stu-id="cabda-110">Rowset name</span></span>|<span data-ttu-id="cabda-111">说明</span><span class="sxs-lookup"><span data-stu-id="cabda-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="cabda-112">DMSCHEMA_MINING_MODELS</span><span class="sxs-lookup"><span data-stu-id="cabda-112">DMSCHEMA_MINING_MODELS</span></span>|<span data-ttu-id="cabda-113">列出了当前上下文中的所有挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="cabda-113">Lists all mining models in the current context.</span></span><br /><br /> <span data-ttu-id="cabda-114">包括诸如创建日期、创建模型时所用的参数以及定型集大小等信息。</span><span class="sxs-lookup"><span data-stu-id="cabda-114">Includes such information as the date created, parameters used to create the model, and the size of the training set.</span></span>|  
|<span data-ttu-id="cabda-115">DMSCHEMA_MINING_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="cabda-115">DMSCHEMA_MINING_COLUMNS</span></span>|<span data-ttu-id="cabda-116">列出了当前上下文中在挖掘模型中使用的所有列。</span><span class="sxs-lookup"><span data-stu-id="cabda-116">Lists all columns used in mining models in the current context.</span></span><br /><br /> <span data-ttu-id="cabda-117">信息包括到挖掘结构源列的映射、数据类型、精度以及可与列一起使用的预测函数。</span><span class="sxs-lookup"><span data-stu-id="cabda-117">Information includes mapping to mining structure source column, data type, precision, and prediction functions that can be used with the column.</span></span>|  
|<span data-ttu-id="cabda-118">DMSCHEMA_MINING_STRUCTURES</span><span class="sxs-lookup"><span data-stu-id="cabda-118">DMSCHEMA_MINING_STRUCTURES</span></span>|<span data-ttu-id="cabda-119">列出了当前上下文中的所有挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="cabda-119">Lists all mining structure in the current context.</span></span><br /><br /> <span data-ttu-id="cabda-120">信息包括结构是否填充、上次处理结构的日期以及结构的维持数据集的定义（如果有）。</span><span class="sxs-lookup"><span data-stu-id="cabda-120">Information includes whether the structure is populated, the date the structure was last processed, and the definition of the holdout data set for the structure, if any.</span></span>|  
|<span data-ttu-id="cabda-121">DMSCHEMA_MINING_STRUCTURE_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="cabda-121">DMSCHEMA_MINING_STRUCTURE_COLUMNS</span></span>|<span data-ttu-id="cabda-122">列出了当前上下文中在挖掘结构中使用的所有列。</span><span class="sxs-lookup"><span data-stu-id="cabda-122">Lists all columns used in mining structures in the current context.</span></span><br /><br /> <span data-ttu-id="cabda-123">信息包括内容类型和数据类型、为 Null 性以及列是否包含嵌套的表数据。</span><span class="sxs-lookup"><span data-stu-id="cabda-123">Information includes content type and data type, nullability, and whether the column contains nested table data.</span></span>|  
|<span data-ttu-id="cabda-124">DMSCHEMA_MINING_SERVICES</span><span class="sxs-lookup"><span data-stu-id="cabda-124">DMSCHEMA_MINING_SERVICES</span></span>|<span data-ttu-id="cabda-125">列出了在指定服务器上可用的所有挖掘服务（或算法）。</span><span class="sxs-lookup"><span data-stu-id="cabda-125">Lists all mining services, or algorithms, that are available on the specified server.</span></span><br /><br /> <span data-ttu-id="cabda-126">信息包括支持的建模标志、输入类型和支持的数据源类型。</span><span class="sxs-lookup"><span data-stu-id="cabda-126">Information includes supported modeling flags, input types, and supported data source types.</span></span>|  
|<span data-ttu-id="cabda-127">DMSCHEMA_MINING_SERVICE_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cabda-127">DMSCHEMA_MINING_SERVICE_PARAMETERS</span></span>|<span data-ttu-id="cabda-128">列出了在当前实例上可用的挖掘服务的所有参数。</span><span class="sxs-lookup"><span data-stu-id="cabda-128">Lists all parameters for the mining services that are available on the current instance.</span></span><br /><br /> <span data-ttu-id="cabda-129">信息包括每个参数的数据类型、默认值以及上限和下限。</span><span class="sxs-lookup"><span data-stu-id="cabda-129">Information includes the data type for each parameter, the default values, and the upper and lower limits.</span></span>|  
|<span data-ttu-id="cabda-130">DMSCHEMA_MODEL_CONTENT</span><span class="sxs-lookup"><span data-stu-id="cabda-130">DMSCHEMA_MODEL_CONTENT</span></span>|<span data-ttu-id="cabda-131">如果模型已处理，则返回模型的内容。</span><span class="sxs-lookup"><span data-stu-id="cabda-131">Returns the content of the model if the model has been processed.</span></span><br /><br /> <span data-ttu-id="cabda-132">有关详细信息，请参阅[挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="cabda-132">For more information, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>|  
|<span data-ttu-id="cabda-133">DBSCHEMA_CATALOGS</span><span class="sxs-lookup"><span data-stu-id="cabda-133">DBSCHEMA_CATALOGS</span></span>|<span data-ttu-id="cabda-134">列出了当前 Analysis Services 实例中的所有数据库（目录）。</span><span class="sxs-lookup"><span data-stu-id="cabda-134">Lists all databases (catalogs) in the current instance of Analysis Services.</span></span>|  
|<span data-ttu-id="cabda-135">MDSCHEMA_INPUT_DATASOURCES</span><span class="sxs-lookup"><span data-stu-id="cabda-135">MDSCHEMA_INPUT_DATASOURCES</span></span>|<span data-ttu-id="cabda-136">列出了当前 Analysis Services 实例中的所有数据源。</span><span class="sxs-lookup"><span data-stu-id="cabda-136">Lists all data sources in the current instance of Analysis Services.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="cabda-137">表中的列表不完整；它仅显示针对疑难解答可能最受关注的那些行集。</span><span class="sxs-lookup"><span data-stu-id="cabda-137">The list in the table is not comprehensive; it shows only those rowsets that may be of most interest for troubleshooting.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cabda-138">示例</span><span class="sxs-lookup"><span data-stu-id="cabda-138">Examples</span></span>  
 <span data-ttu-id="cabda-139">下面的部分提供了一些针对数据挖掘架构行集的查询示例。</span><span class="sxs-lookup"><span data-stu-id="cabda-139">The following section provides some examples of queries against the data mining schema rowsets.</span></span>  
  
### <a name="example-1-list-data-mining-services"></a><span data-ttu-id="cabda-140">示例 1：列出数据挖掘服务</span><span class="sxs-lookup"><span data-stu-id="cabda-140">Example 1: List Data Mining Services</span></span>  
 <span data-ttu-id="cabda-141">以下查询返回在当前服务器上可用的挖掘服务（也就是启用的算法）列表。</span><span class="sxs-lookup"><span data-stu-id="cabda-141">The following query returns a list of the mining services that are available on the current server, meaning the algorithms that are enabled.</span></span> <span data-ttu-id="cabda-142">为每个挖掘服务提供的列包括可由每个算法使用的建模标志和内容类型、每个服务的 GUID，以及可能已为每个服务添加的任何预测限制。</span><span class="sxs-lookup"><span data-stu-id="cabda-142">The columns provided for each mining service include the modeling flags and content types that can be used by each algorithm, the GUID for each service, and any prediction limits that may have been added for each service.</span></span>  
  
```  
SELECT *  
FROM $system.DMSCHEMA_MINING_SERVICES  
```  
  
### <a name="example-2-list-mining-model-parameters"></a><span data-ttu-id="cabda-143">示例 2：列出挖掘模型参数</span><span class="sxs-lookup"><span data-stu-id="cabda-143">Example 2: List Mining Model Parameters</span></span>  
 <span data-ttu-id="cabda-144">下面的示例返回创建指定挖掘模型时所使用的参数：</span><span class="sxs-lookup"><span data-stu-id="cabda-144">The following example returns the parameters that were used to create a specific mining model:</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
### <a name="example-3-list-all-rowsets"></a><span data-ttu-id="cabda-145">示例 3：列出所有行集</span><span class="sxs-lookup"><span data-stu-id="cabda-145">Example 3: List All Rowsets</span></span>  
 <span data-ttu-id="cabda-146">下面的示例返回在当前服务器上可用的行集的综合性列表：</span><span class="sxs-lookup"><span data-stu-id="cabda-146">The following example returns a comprehensive list of the rowsets that are available on the current server:</span></span>  
  
```  
SELECT *   
FROM $system.DBSCHEMA_TABLES  
```  
  
## <a name="see-also"></a><span data-ttu-id="cabda-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cabda-147">See Also</span></span>  
 [<span data-ttu-id="cabda-148">故障排除概念（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="cabda-148">Troubleshooting Concepts (Analysis Services - Data Mining)</span></span>](https://msdn.microsoft.com/library/cc645881.aspx)  
  
  
