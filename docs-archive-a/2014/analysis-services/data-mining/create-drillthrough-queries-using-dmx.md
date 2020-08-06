---
title: 使用 DMX 创建钻取查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
author: minewiskan
ms.author: owend
ms.openlocfilehash: 618732bfe48f7b1fe777f7841d686b07877d10ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588758"
---
# <a name="create-drillthrough-queries-using-dmx"></a><span data-ttu-id="c30e3-102">使用 DMX 来创建钻取查询</span><span class="sxs-lookup"><span data-stu-id="c30e3-102">Create Drillthrough Queries using DMX</span></span>
  <span data-ttu-id="c30e3-103">对于支持钻取的所有模型，可以通过在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或任何其他支持 DMX 的客户端中创建 DMX 查询来检索事例数据和结构数据。</span><span class="sxs-lookup"><span data-stu-id="c30e3-103">For all models that support drillthrough, you can retrieve case data and structure data by creating a DMX query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or any other client that supports DMX.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="c30e3-104">若要查看数据，必须已启用钻取，并且您必须拥有必要的权限。</span><span class="sxs-lookup"><span data-stu-id="c30e3-104">To view the data, drillthrough must have been enabled, and you must have the necessary permissions.</span></span>  
  
## <a name="specifying-drillthrough-options"></a><span data-ttu-id="c30e3-105">指定钻取选项</span><span class="sxs-lookup"><span data-stu-id="c30e3-105">Specifying Drillthrough Options</span></span>  
 <span data-ttu-id="c30e3-106">下面是通常用来检索模型事例和结构事例的语法：</span><span class="sxs-lookup"><span data-stu-id="c30e3-106">The general syntax is for retrieving model cases and structure cases is as follows:</span></span>  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 <span data-ttu-id="c30e3-107">有关使用 DMX 查询返回事例数据的其它信息，请参阅 [SELECT FROM <模型>.CASES (DMX)](/sql/dmx/select-from-model-content-dmx) 和 [SELECT FROM <结构>.CASES](/sql/dmx/select-from-structure-cases)。</span><span class="sxs-lookup"><span data-stu-id="c30e3-107">For additional information about using DMX queries to return case data, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) and [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c30e3-108">示例</span><span class="sxs-lookup"><span data-stu-id="c30e3-108">Examples</span></span>  
 <span data-ttu-id="c30e3-109">下面的 DMX 查询从时序模型返回特定产品系列的事例数据。</span><span class="sxs-lookup"><span data-stu-id="c30e3-109">The following DMX query returns the case data for a specific product series, from a time series model.</span></span> <span data-ttu-id="c30e3-110">该查询还返回 `Amount` 列，该列在挖掘结构中可用，但却未在挖掘模型中使用。</span><span class="sxs-lookup"><span data-stu-id="c30e3-110">The query also returns the column `Amount`, which was not used in the model but is available in the mining structure.</span></span>  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 <span data-ttu-id="c30e3-111">请注意，在此示例中，已使用别名对该结构列进行了重命名。</span><span class="sxs-lookup"><span data-stu-id="c30e3-111">Note that in this example, an alias has been used to rename the structure column.</span></span> <span data-ttu-id="c30e3-112">如果您没有为该结构列分配别名，则该列将以“Expression”名称返回。</span><span class="sxs-lookup"><span data-stu-id="c30e3-112">If you do not assign an alias to the structure column, the column is returned with the name 'Expression'.</span></span> <span data-ttu-id="c30e3-113">这是所有未命名列的默认行为。</span><span class="sxs-lookup"><span data-stu-id="c30e3-113">This is the default behavior for all unnamed columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c30e3-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c30e3-114">See Also</span></span>  
 <span data-ttu-id="c30e3-115">[数据挖掘 &#40;钻取查询&#41;](drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c30e3-115">[Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md) </span></span>  
 [<span data-ttu-id="c30e3-116">对挖掘结构的钻取功能</span><span class="sxs-lookup"><span data-stu-id="c30e3-116">Drillthrough on Mining Structures</span></span>](drillthrough-on-mining-structures.md)  
  
  
