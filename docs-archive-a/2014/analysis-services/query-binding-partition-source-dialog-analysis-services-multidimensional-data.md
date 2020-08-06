---
title: 查询绑定详细信息 (分区源 "对话框中)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59d2ae1fed9d22366786e21a287a621f08418a5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586991"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="2c2b1-102">查询绑定详细信息（“分区源”对话框）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="2c2b1-102">Query Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="2c2b1-103">可以使用 **“分区源”** 对话框中的 **“查询绑定”** 选项指定为分区提供数据的查询。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-103">Use the **Query Binding** option in the **Partition Source** dialog box to specify the query that provides the data for the partition.</span></span> <span data-ttu-id="2c2b1-104">通过从 **“分区源”** 对话框中的 **“绑定类型”** 选项中选择 **“查询绑定”** ，可以显示此窗格。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-104">You can display this pane by selecting **Query Binding** from the **Binding type** option in the **Partition Source** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2c2b1-105">选项</span><span class="sxs-lookup"><span data-stu-id="2c2b1-105">Options</span></span>  
 <span data-ttu-id="2c2b1-106">**数据源**</span><span class="sxs-lookup"><span data-stu-id="2c2b1-106">**Data source**</span></span>  
 <span data-ttu-id="2c2b1-107">选择要对其执行查询的数据源，以便为分区提供事实数据。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-107">Select the data source on which the query is executed to provide fact data for the partition.</span></span>  
  
 <span data-ttu-id="2c2b1-108">**查询**</span><span class="sxs-lookup"><span data-stu-id="2c2b1-108">**Query**</span></span>  
 <span data-ttu-id="2c2b1-109">键入或修改在处理分区过程中检索事实数据时所使用的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-109">Type or modify the SQL statement used when retrieving fact data when the partition is processed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2c2b1-110">通过指定 WHERE 子句，可以将记录的子集用于此分区。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-110">By specifying a WHERE clause, a subset of records can be used for this partition.</span></span> <span data-ttu-id="2c2b1-111">当多个分区都基于单一事实数据表时，防止数据重复很重要。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-111">This is essential to prevent duplication of data when multiple partitions are based on a single fact table.</span></span> <span data-ttu-id="2c2b1-112">有关详细信息，请参阅 "[分区源" 对话框 &#40;Analysis Services 多维数据&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-112">For more information, see [Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="2c2b1-113">**检查**</span><span class="sxs-lookup"><span data-stu-id="2c2b1-113">**Check**</span></span>  
 <span data-ttu-id="2c2b1-114">单击此项可以验证“查询”\*\*\*\* 中的语句是否为有效的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="2c2b1-114">Click to verify that the statement in **Query** is a valid SQL statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c2b1-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c2b1-115">See Also</span></span>  
 [<span data-ttu-id="2c2b1-116">"分区源" 对话框 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="2c2b1-116">Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
