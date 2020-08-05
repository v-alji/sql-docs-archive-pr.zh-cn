---
title: ) XMLA (将分区合并 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 65840066d3e95571db511a2015a1bee64aa8d922
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580956"
---
# <a name="merging-partitions-xmla"></a><span data-ttu-id="9bc45-102">合并分区 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="9bc45-102">Merging Partitions (XMLA)</span></span>
  <span data-ttu-id="9bc45-103">如果分区具有相同的聚合设计和结构，则可以通过使用 XML for Analysis (XMLA) 中的[MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla)命令来合并分区。</span><span class="sxs-lookup"><span data-stu-id="9bc45-103">If partitions have the same aggregation design and structure, you can merge the partition by using the [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) command in XML for Analysis (XMLA).</span></span> <span data-ttu-id="9bc45-104">合并分区是将在管理分区时执行的一项重要操作，特别是那些包含按日期分区的历史数据的分区。</span><span class="sxs-lookup"><span data-stu-id="9bc45-104">Merging partitions is an important action to perform when you manage partitions, especially those partitions that contain historical data partitioned by date.</span></span>  
  
 <span data-ttu-id="9bc45-105">例如，财务多维数据集可以使用两个分区：</span><span class="sxs-lookup"><span data-stu-id="9bc45-105">For example, a financial cube may use two partitions:</span></span>  
  
-   <span data-ttu-id="9bc45-106">一个分区表示当年的财务数据，使用实时关系 OLAP (ROLAP) 存储设置改善性能。</span><span class="sxs-lookup"><span data-stu-id="9bc45-106">One partition represents financial data for the current year, using real-time relational OLAP (ROLAP) storage settings for performance.</span></span>  
  
-   <span data-ttu-id="9bc45-107">另一个分区包含以往年度的财务数据，使用多维 OLAP (MOLAP) 存储设置进行存储。</span><span class="sxs-lookup"><span data-stu-id="9bc45-107">Another partition contains financial data for previous years, using multidimensional OLAP (MOLAP) storage settings for storage.</span></span>  
  
 <span data-ttu-id="9bc45-108">这两个分区使用不同的存储设置，但使用相同的聚合设计。</span><span class="sxs-lookup"><span data-stu-id="9bc45-108">Both partitions use different storage settings, but use the same aggregation design.</span></span> <span data-ttu-id="9bc45-109">除了在年末处理所有年度的历史数据的多维数据集，还可以使用 `MergePartitions` 命令将当年的分区合并到以往年度的分区。</span><span class="sxs-lookup"><span data-stu-id="9bc45-109">Instead of processing the cube across years of historical data at the end of the year, you can instead use the `MergePartitions` command to merge the partition for the current year into the partition for previous years.</span></span> <span data-ttu-id="9bc45-110">这样将保留聚合数据，而不需要对多维数据集进行潜在耗时的完全处理。</span><span class="sxs-lookup"><span data-stu-id="9bc45-110">This preserves the aggregation data without requiring a potentially time-consuming full processing of the cube.</span></span>  
  
## <a name="specifying-partitions-to-merge"></a><span data-ttu-id="9bc45-111">指定要合并的分区</span><span class="sxs-lookup"><span data-stu-id="9bc45-111">Specifying Partitions to Merge</span></span>  
 <span data-ttu-id="9bc45-112">运行该 `MergePartitions` 命令时，将在[source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)属性中指定的源分区中存储的聚合数据添加到[目标](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)属性中指定的目标分区。</span><span class="sxs-lookup"><span data-stu-id="9bc45-112">When the `MergePartitions` command runs, the aggregation data stored in the source partitions specified in the [Source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) property is added to the target partition specified in the [Target](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9bc45-113">`Source` 属性可包含多个分区对象引用。</span><span class="sxs-lookup"><span data-stu-id="9bc45-113">The `Source` property can contain more than one partition object reference.</span></span> <span data-ttu-id="9bc45-114">但是，`Target` 属性则没有此功能。</span><span class="sxs-lookup"><span data-stu-id="9bc45-114">However, the `Target` property cannot.</span></span>  
  
 <span data-ttu-id="9bc45-115">若要成功合并，在 `Source` 和 `Target` 中指定的分区必须包含在相同的度量值组，并使用相同的聚合设计。</span><span class="sxs-lookup"><span data-stu-id="9bc45-115">To be successfully merged, the partitions specified in both the `Source` and `Target` must be contained by the same measure group and use the same aggregation design.</span></span> <span data-ttu-id="9bc45-116">否则，将会出错。</span><span class="sxs-lookup"><span data-stu-id="9bc45-116">Otherwise, an error occurs.</span></span>  
  
 <span data-ttu-id="9bc45-117">在 `Source` 中指定的分区将在成功执行 `MergePartitions` 命令后删除。</span><span class="sxs-lookup"><span data-stu-id="9bc45-117">The partitions specified in the `Source` are deleted after the `MergePartitions` command is successfully completed.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9bc45-118">示例</span><span class="sxs-lookup"><span data-stu-id="9bc45-118">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="9bc45-119">说明</span><span class="sxs-lookup"><span data-stu-id="9bc45-119">Description</span></span>  
 <span data-ttu-id="9bc45-120">下面的示例将**艾德公司 DW**示例数据库中的 "**客户计数**"**度量**值组中的所有分区合并 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 到**Customers_2004**分区。</span><span class="sxs-lookup"><span data-stu-id="9bc45-120">The following example merges all the partitions in the **Customer Counts** measure group of the **Adventure Works** cube in the **Adventure Works DW** sample [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database into the **Customers_2004** partition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9bc45-121">代码</span><span class="sxs-lookup"><span data-stu-id="9bc45-121">Code</span></span>  
  
```  
<MergePartitions xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bc45-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9bc45-122">See Also</span></span>  
 [<span data-ttu-id="9bc45-123">在 Analysis Services 中使用 XMLA 开发</span><span class="sxs-lookup"><span data-stu-id="9bc45-123">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
