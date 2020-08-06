---
title: " (Analysis Services) 设置分区切片属性 |Microsoft Docs"
ms.custom: ''
ms.date: 08/05/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], data slices
- data slices [Analysis Services]
ms.assetid: 507b91e5-7f85-4c22-be97-4d7a676e6667
author: minewiskan
ms.author: owend
ms.openlocfilehash: f42c4536b99ba3fecf9b947942b881a3be72784f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588715"
---
# <a name="set-the-partition-slice-property-analysis-services"></a><span data-ttu-id="a66bc-102">设置分区切片属性 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a66bc-102">Set the Partition Slice Property (Analysis Services)</span></span>
  <span data-ttu-id="a66bc-103">数据切片是一种很重要的优化功能，可以帮助将查询指向相应分区的数据。</span><span class="sxs-lookup"><span data-stu-id="a66bc-103">A data slice is an important optimization feature that helps direct queries to the data of the appropriate partitions.</span></span> <span data-ttu-id="a66bc-104">通过覆盖为 MOLAP 和 HOLAP 分区生成的默认切片来显式设置 Slice 属性可提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="a66bc-104">Explicitly setting the Slice property can improve query performance by overriding default slices generated for MOLAP and HOLAP partitions.</span></span> <span data-ttu-id="a66bc-105">此外，Slice 属性还在处理分区时提供额外的验证检查。</span><span class="sxs-lookup"><span data-stu-id="a66bc-105">Additionally, the Slice property provides an extra validation check when processing the partition.</span></span>  
  
 <span data-ttu-id="a66bc-106">创建分区后，但在处理它之前，可以使用 Slice 属性指定一个数据切片。</span><span class="sxs-lookup"><span data-stu-id="a66bc-106">You can specify a data slice after you create a partition, but before processing it, using the Slice property.</span></span> <span data-ttu-id="a66bc-107">在“分区”选项卡上，展开一个度量值组，右键单击一个分区，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a66bc-107">On the Partitions tab, expand a measure group, right-click a partition, and select **Properties**.</span></span>  
  
## <a name="defining-a-slice"></a><span data-ttu-id="a66bc-108">定义切片</span><span class="sxs-lookup"><span data-stu-id="a66bc-108">Defining a Slice</span></span>  
 <span data-ttu-id="a66bc-109">Slice 属性的有效值是 MDX 成员、集合或元组。</span><span class="sxs-lookup"><span data-stu-id="a66bc-109">Valid values for a slice property are an MDX member, set, or tuple.</span></span> <span data-ttu-id="a66bc-110">以下示例说明了有效的切片语法：</span><span class="sxs-lookup"><span data-stu-id="a66bc-110">The following examples illustrate valid slice syntax:</span></span>  
  
|<span data-ttu-id="a66bc-111">切片</span><span class="sxs-lookup"><span data-stu-id="a66bc-111">Slice</span></span>|<span data-ttu-id="a66bc-112">成员、集合或元组</span><span class="sxs-lookup"><span data-stu-id="a66bc-112">Member, set or tuple</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="a66bc-113">[Date].[Calendar].[Calendar Year].&[2010]</span><span class="sxs-lookup"><span data-stu-id="a66bc-113">[Date].[Calendar].[Calendar Year].&[2010]</span></span>|<span data-ttu-id="a66bc-114">对包含 2010 年的事实的分区指定此切片（假定模型包括具有 Calendar Year 层次的 Date 维度，且 2010 是其中的成员）。</span><span class="sxs-lookup"><span data-stu-id="a66bc-114">Specify this slice on a partition containing facts from year 2010 (assuming the model includes a Date dimension with Calendar Year hierarchy, where 2010 is a member).</span></span> <span data-ttu-id="a66bc-115">虽然分区源 WHERE 子句或表可能已经按 2010 筛选，指定切片也能在处理过程以及查询执行期间的更有针对性的扫描中再一次进行检查。</span><span class="sxs-lookup"><span data-stu-id="a66bc-115">Although the partition source WHERE clause or table might already filter by 2010, specifying the Slice provides an additional check during processing, as well as more targeted scans during query execution.</span></span>|  
|<span data-ttu-id="a66bc-116">{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }</span><span class="sxs-lookup"><span data-stu-id="a66bc-116">{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }</span></span>|<span data-ttu-id="a66bc-117">对包含了具有销售区域信息的事实的分区指定此切片。</span><span class="sxs-lookup"><span data-stu-id="a66bc-117">Specify this slice on a partition containing facts that include sales territory information.</span></span> <span data-ttu-id="a66bc-118">切片可以是由两个或更多成员组成的 MDX 集合。</span><span class="sxs-lookup"><span data-stu-id="a66bc-118">A slice can be an MDX set consisting of two or more members.</span></span>|  
|<span data-ttu-id="a66bc-119">[Measures].[Sales Amount Quota] > '5000'</span><span class="sxs-lookup"><span data-stu-id="a66bc-119">[Measures].[Sales Amount Quota] > '5000'</span></span>|<span data-ttu-id="a66bc-120">此切片显示了一个 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="a66bc-120">This slice shows an MDX expression.</span></span>|  
  
 <span data-ttu-id="a66bc-121">分区的数据切片应尽可能真实地反映分区中的数据。</span><span class="sxs-lookup"><span data-stu-id="a66bc-121">A data slice of a partition should reflect, as closely as possible, the data in the partition.</span></span> <span data-ttu-id="a66bc-122">例如，如果某个分区仅限于 2012 年的数据，则分区的数据切片应该指定 Time 维度的成员 2012。</span><span class="sxs-lookup"><span data-stu-id="a66bc-122">For example, if a partition is limited to 2012 data, the partition's data slice should specify the 2012 member of the Time dimension.</span></span> <span data-ttu-id="a66bc-123">并不是所指定的每一个数据切片都能确切地反映分区内容。</span><span class="sxs-lookup"><span data-stu-id="a66bc-123">It is not always possible to specify a data slice that reflects the exact contents of a partition.</span></span> <span data-ttu-id="a66bc-124">例如，如果分区只包含 January 和 February 的数据，但 Time 维度的级别是 Year、Quarter 和 Month，则分区向导将无法同时选中成员 January 和 February。</span><span class="sxs-lookup"><span data-stu-id="a66bc-124">For example, if a partition contains data for only January and February, but the levels of the Time dimension are Year, Quarter, and Month, the Partition Wizard cannot select both the January and February members.</span></span> <span data-ttu-id="a66bc-125">在此情况下，应选择反映了分区内容的成员的父级成员。</span><span class="sxs-lookup"><span data-stu-id="a66bc-125">In such cases, select the parent of the members that reflect the partition's contents.</span></span> <span data-ttu-id="a66bc-126">在上例中，应选择 Quarter 1。</span><span class="sxs-lookup"><span data-stu-id="a66bc-126">In this example, select Quarter 1.</span></span>  
  
 <span data-ttu-id="a66bc-127">要了解有关数据切片好处的说明，请参阅 [对您的 SSAS 多维数据集分区设置切片](https://go.microsoft.com/fwlink/?LinkId=317783)。</span><span class="sxs-lookup"><span data-stu-id="a66bc-127">For an explanation of data slice benefits, see [Set the Slice on your SSAS Cube Partition](https://go.microsoft.com/fwlink/?LinkId=317783).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a66bc-128">请注意，动态 MDX 函数（如 [Generate (MDX)](/sql/mdx/generate-mdx) 或 [Except (MDX)](/sql/mdx/except-mdx-function)）在分区的切片属性中不受支持。</span><span class="sxs-lookup"><span data-stu-id="a66bc-128">Note that dynamic MDX functions (such as [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) or [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function)) are not supported in the Slice property for partitions.</span></span> <span data-ttu-id="a66bc-129">你必须通过使用显式元组或成员引用定义切片。</span><span class="sxs-lookup"><span data-stu-id="a66bc-129">You must define the slice by using explicit tuples or member references.</span></span>  
>   
>  <span data-ttu-id="a66bc-130">例如，不是使用[： &#40;范围&#41; &#40;MDX&#41;](/sql/mdx/range-mdx)函数来定义一个范围，你需要按特定年份枚举每个成员。</span><span class="sxs-lookup"><span data-stu-id="a66bc-130">For example, rather than using the [: &#40;Range&#41; &#40;MDX&#41;](/sql/mdx/range-mdx) function to define a range, you would need to enumerate each member by the specific years.</span></span>  
>   
>  <span data-ttu-id="a66bc-131">如果需要定义复杂的切片，我们建议使用 XMLA Alter 脚本在切片中定义元组。</span><span class="sxs-lookup"><span data-stu-id="a66bc-131">If you need to define a complex slice, we recommend that you define the tuples in the slice by using an XMLA Alter script.</span></span> <span data-ttu-id="a66bc-132">然后，你可以使用 ascmd 命令行工具或 SSIS [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) 任务运行该脚本并立即创建指定的成员集，之后再处理分区。</span><span class="sxs-lookup"><span data-stu-id="a66bc-132">Then, you can use either the ascmd command-line tool or the SSIS [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) task to run the script and create the specified set of members immediately before you process the partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a66bc-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a66bc-133">See Also</span></span>  
 [<span data-ttu-id="a66bc-134">创建和管理本地分区 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a66bc-134">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](create-and-manage-a-local-partition-analysis-services.md)  
  
  
