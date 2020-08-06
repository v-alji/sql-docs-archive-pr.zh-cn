---
title: " (数据挖掘向导) 的切片源多维数据集 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.slicesourcecube.f1
ms.assetid: 16485608-d3b9-49ee-8baa-948038cdd7ec
author: minewiskan
ms.author: owend
ms.openlocfilehash: 762248d4c2a268ac36b0dfa3ffeba20123017017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691899"
---
# <a name="slice-source-cube-data-mining-wizard"></a><span data-ttu-id="545ad-102">对源多维数据集进行切片（数据挖掘向导）</span><span class="sxs-lookup"><span data-stu-id="545ad-102">Slice Source Cube (Data Mining Wizard)</span></span>
  <span data-ttu-id="545ad-103">\*\*\*\* 可以使用“对源多维数据集进行切片”对话框限制用于为模型定型的数据。</span><span class="sxs-lookup"><span data-stu-id="545ad-103">You can use the **Slice Source Cube** dialog box to restrict the data used to train the model.</span></span> <span data-ttu-id="545ad-104">通常一个多维数据集包含与很多不同维度和属性有关的数据，例如所有商店、所有区域和所有产品。</span><span class="sxs-lookup"><span data-stu-id="545ad-104">Typically a cube contains data related to many different dimensions and attributes, such as all stores, all regions, and all products.</span></span> <span data-ttu-id="545ad-105">定型无限的属性组合的模型是不现实的，因此您使用此对话框选择要在定型模型中使用的特定集合。</span><span class="sxs-lookup"><span data-stu-id="545ad-105">It is not practical to train a model on unlimited combinations of attributes, so you use this dialog box to choose a specific set to use in training a model.</span></span>  
  
 <span data-ttu-id="545ad-106">例如，在 AdventureWorks 多维数据集中，您可能按特定产品线、区域或年份切片以获取某部分数据。</span><span class="sxs-lookup"><span data-stu-id="545ad-106">For example, in the AdventureWorks cube, you might slice by a particular product line, region, or year, to get a portion of the data.</span></span>  
  
 <span data-ttu-id="545ad-107">如果不熟悉切片和多维数据集，我们建议你查看以下这些文章：</span><span class="sxs-lookup"><span data-stu-id="545ad-107">If you are unfamiliar with slices and cubes, we recommend that you review these articles:</span></span>  
  
-   [<span data-ttu-id="545ad-108">设置分区切片属性 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="545ad-108">Set the Partition Slice Property &#40;Analysis Services&#41;</span></span>](multidimensional-models/set-the-partition-slice-property-analysis-services.md)  
  
-   [<span data-ttu-id="545ad-109">创建和管理本地分区 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="545ad-109">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
> [!NOTE]  
>  <span data-ttu-id="545ad-110">请注意，动态 MDX 函数（如 [Generate (MDX)](/sql/mdx/generate-mdx) 或 [Except (MDX)](/sql/mdx/except-mdx-function)）在分区的切片属性中不受支持。</span><span class="sxs-lookup"><span data-stu-id="545ad-110">Note that dynamic MDX functions (such as [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) or [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function)) are not supported in the Slice property for partitions.</span></span> <span data-ttu-id="545ad-111">你必须通过使用显式元组或成员引用定义切片。</span><span class="sxs-lookup"><span data-stu-id="545ad-111">You must define the slice by using explicit tuples or member references.</span></span>  
>   
>  <span data-ttu-id="545ad-112">例如，不是使用[： &#40;范围&#41; &#40;MDX&#41;](/sql/mdx/range-mdx)来定义一个范围，你需要枚举特定年份的每个成员。</span><span class="sxs-lookup"><span data-stu-id="545ad-112">For example, rather than using  [: &#40;Range&#41; &#40;MDX&#41;](/sql/mdx/range-mdx) to define a range, you would need to enumerate each member by the specific years.</span></span>  
>   
>  <span data-ttu-id="545ad-113">如果需要定义复杂的切片，我们建议使用 XMLA Alter 脚本在切片中定义元组。</span><span class="sxs-lookup"><span data-stu-id="545ad-113">If you need to define a complex slice, we recommend that you define the tuples in the slice by using an XMLA Alter script.</span></span> <span data-ttu-id="545ad-114">然后，你可以使用 ascmd 命令行工具或 SSIS [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) 运行该脚本并立即创建指定的成员集，之后再处理分区。</span><span class="sxs-lookup"><span data-stu-id="545ad-114">Then, you can use either the ascmd command-line tool or the SSIS [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) to run the script and create the specified set of members immediately before you process the partition.</span></span>  
  
 <span data-ttu-id="545ad-115">**有关详细信息，请参阅** [数据挖掘向导（Analysis Services - 数据挖掘）](data-mining/data-mining-wizard-analysis-services-data-mining.md)[创建关系挖掘结构](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="545ad-115">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="545ad-116">选项</span><span class="sxs-lookup"><span data-stu-id="545ad-116">Options</span></span>  
 <span data-ttu-id="545ad-117">**维度**</span><span class="sxs-lookup"><span data-stu-id="545ad-117">**Dimension**</span></span>  
 <span data-ttu-id="545ad-118">选择要进行切片的维度。</span><span class="sxs-lookup"><span data-stu-id="545ad-118">Select the dimension that you want to slice.</span></span>  
  
 <span data-ttu-id="545ad-119">**层次结构**</span><span class="sxs-lookup"><span data-stu-id="545ad-119">**Hierarchy**</span></span>  
 <span data-ttu-id="545ad-120">选择要进行切片的层次结构。</span><span class="sxs-lookup"><span data-stu-id="545ad-120">Select the hierarchy that you want to slice.</span></span> <span data-ttu-id="545ad-121">您可以选择任意的层级结构级别，但是在模型中使用的属性将仅位于您选择的级别。</span><span class="sxs-lookup"><span data-stu-id="545ad-121">You can choose any level of a hierarchy, but the attributes used in the model will be only at the level that you choose.</span></span>  
  
 <span data-ttu-id="545ad-122">例如，如果您选择“地理”层次结构，选择“国家/地区”作为级别，则不能生成使用“城市”作为属性的模型。</span><span class="sxs-lookup"><span data-stu-id="545ad-122">For example, if you choose the Geography hierarchy, and select Country as the level, you cannot build a model that uses City as the attributes.</span></span> <span data-ttu-id="545ad-123">相反，如果您选择“城市”作为对其切片的层次结构级别，则不能创建基于“国家/地区”的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="545ad-123">Conversely, if you choose City as the level of the hierarchy on which to slice, you cannot create a mining model based on Country.</span></span>  
  
 <span data-ttu-id="545ad-124">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="545ad-124">**Operator**</span></span>  
 <span data-ttu-id="545ad-125">选择要在生成切片表达式中使用的运算符。</span><span class="sxs-lookup"><span data-stu-id="545ad-125">Select the operator to use in building a slice expression.</span></span>  
  
 <span data-ttu-id="545ad-126">例如，如果选择了 "地理" 作为层次结构，则可以选择运算符 =，然后键入 "欧洲" 作为筛选器，以仅获取欧洲的多维数据集数据。</span><span class="sxs-lookup"><span data-stu-id="545ad-126">For example, if you chose Geography as the hierarchy, you could select the operator = and then type "Europe" as the filter, to get cube data for Europe only.</span></span>  
  
 <span data-ttu-id="545ad-127">**筛选表达式**</span><span class="sxs-lookup"><span data-stu-id="545ad-127">**Filter Expression**</span></span>  
 <span data-ttu-id="545ad-128">键入要作为针对所选维度筛选多维数据集时的标准的表达式。</span><span class="sxs-lookup"><span data-stu-id="545ad-128">Type an expression to use as a criterion when filtering the cube on the selected dimension.</span></span>  
  
 <span data-ttu-id="545ad-129">**参数**</span><span class="sxs-lookup"><span data-stu-id="545ad-129">**Parameters**</span></span>  
 <span data-ttu-id="545ad-130">此选项不用于数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="545ad-130">This option is not used for data mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="545ad-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="545ad-131">See Also</span></span>  
 <span data-ttu-id="545ad-132">[完成向导 &#40;数据挖掘向导&#41;](completing-the-wizard-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="545ad-132">[Completing the Wizard &#40;Data Mining Wizard&#41;](completing-the-wizard-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="545ad-133">[数据挖掘向导 F1 帮助 &#40;Analysis Services 数据挖掘&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="545ad-133">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="545ad-134">在数据挖掘向导 &#40;指定挖掘模型列用法&#41;</span><span class="sxs-lookup"><span data-stu-id="545ad-134">Specify Mining Model Column Usage &#40;Data Mining Wizard&#41;</span></span>](specify-mining-model-column-usage-data-mining-wizard.md)  
  
  
