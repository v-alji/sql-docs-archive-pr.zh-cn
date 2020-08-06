---
title: 配置度量值属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- additivity [Analysis Services]
- ID property
- ErrorConfiguration property
- AggregateFunction property
- DisplayFolder property
- IgnoreUnrelatedDimensions property
- FormatString property
- Description property
- semiadditive
- properties [Analysis Services], measure groups
- aggregate functions [Analysis Services]
- DataType property
- ProcessingMode property
- MeasureExpression property
- AggregationPrefix property
- Visible property
- properties [Analysis Services], measures
- StorageLocation property
- StorageMode property
- formats [Analysis Services], measures
- Source property
- aggregations [Analysis Services], measures
- measures [Analysis Services], properties
- nonadditive [Analysis Services]
- Name property
- measures [Analysis Services], display formats
- ProcessingPriority property
- measure groups [Analysis Services], properties
- Type property
- ProactiveCaching property
ms.assetid: e9031078-c4f5-4986-b0c9-4d064b622ab7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7ca291a5181fdb3f7a88845431d61ffd7a1034eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691982"
---
# <a name="configure-measure-properties"></a><span data-ttu-id="4cd33-102">配置度量值属性</span><span class="sxs-lookup"><span data-stu-id="4cd33-102">Configure Measure Properties</span></span>
  <span data-ttu-id="4cd33-103">通过使用度量值的属性，您可以定义度量值的工作方式并控制如何向用户显示度量值。</span><span class="sxs-lookup"><span data-stu-id="4cd33-103">Measures have properties that enable you to define how the measures function and to control how the measures appear to users.</span></span>  
  
 <span data-ttu-id="4cd33-104">当创建或编辑多维数据集或度量值时可在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中设置属性。</span><span class="sxs-lookup"><span data-stu-id="4cd33-104">You can set properties in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] when creating or editing a cube or measure.</span></span> <span data-ttu-id="4cd33-105">你还可以编程方式（用 MDX 或 AMO）设置它们。</span><span class="sxs-lookup"><span data-stu-id="4cd33-105">You can also set them programmatically, using MDX or AMO.</span></span> <span data-ttu-id="4cd33-106">有关详细信息，请参阅[在多维模型中创建度量值和度量值组](create-measures-and-measure-groups-in-multidimensional-models.md)、[CREATE MEMBER 语句 (MDX)](/sql/mdx/mdx-data-definition-create-member) 或 [AMO OLAP 基本对象的编程](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects)。</span><span class="sxs-lookup"><span data-stu-id="4cd33-106">See [Create Measures and Measure Groups in Multidimensional Models](create-measures-and-measure-groups-in-multidimensional-models.md) or [CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) or [Programming AMO OLAP Basic Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects) for details.</span></span>  
  
## <a name="measure-properties"></a><span data-ttu-id="4cd33-107">度量值属性</span><span class="sxs-lookup"><span data-stu-id="4cd33-107">Measure Properties</span></span>  
 <span data-ttu-id="4cd33-108">度量值从其所属的度量值组中继承某些属性，除非这些属性在度量值级别被覆盖。</span><span class="sxs-lookup"><span data-stu-id="4cd33-108">Measures inherit certain properties from the measure group of which they are a member, unless those properties are overridden at the measure level.</span></span> <span data-ttu-id="4cd33-109">度量值属性确定度量值的聚合方式、它的数据类型、对用户的显示名称、度量值将在其中出现的显示文件夹、它的格式字符串、任何度量值表达式、基础源列和它对用户的可见性。</span><span class="sxs-lookup"><span data-stu-id="4cd33-109">Measure properties determine how a measure is aggregated, its data type, the name that is displayed to the user, the display folder in which the measure will appear, its format string, any measure expression, the underlying source column, and its visibility to users.</span></span>  
  
|<span data-ttu-id="4cd33-110">属性</span><span class="sxs-lookup"><span data-stu-id="4cd33-110">Property</span></span>|<span data-ttu-id="4cd33-111">定义</span><span class="sxs-lookup"><span data-stu-id="4cd33-111">Definition</span></span>|  
|--------------|----------------|  
|`AggregateFunction`|<span data-ttu-id="4cd33-112">必需。</span><span class="sxs-lookup"><span data-stu-id="4cd33-112">Required.</span></span> <span data-ttu-id="4cd33-113">确定度量值的聚合方式。</span><span class="sxs-lookup"><span data-stu-id="4cd33-113">Determines how measures are aggregated.</span></span> <span data-ttu-id="4cd33-114">`Sum` 是默认聚合。</span><span class="sxs-lookup"><span data-stu-id="4cd33-114">`Sum` is the default aggregation.</span></span> <span data-ttu-id="4cd33-115">有关详细信息，请参阅针对每个函数说明的 [Use Aggregate Functions](use-aggregate-functions.md) 。</span><span class="sxs-lookup"><span data-stu-id="4cd33-115">For more information, see [Use Aggregate Functions](use-aggregate-functions.md) for a description of each function.</span></span>|  
|`DataType`|<span data-ttu-id="4cd33-116">必需。</span><span class="sxs-lookup"><span data-stu-id="4cd33-116">Required.</span></span> <span data-ttu-id="4cd33-117">指定与度量值绑定的基础事实数据表中的列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="4cd33-117">Specifies the data type of the column in the underlying fact table to which the measure is bound.</span></span> <span data-ttu-id="4cd33-118">默认情况下，此值从源列继承。</span><span class="sxs-lookup"><span data-stu-id="4cd33-118">This value is inherited from the source column by default.</span></span>|  
|`Description`|<span data-ttu-id="4cd33-119">提供度量值的说明，可以在客户端应用程序中显示该说明。</span><span class="sxs-lookup"><span data-stu-id="4cd33-119">Provides a description of the measure, which may be exposed in client applications.</span></span>|  
|`DisplayFolder`|<span data-ttu-id="4cd33-120">指定当用户连接到多维数据集时度量值将在其中显示的文件夹。</span><span class="sxs-lookup"><span data-stu-id="4cd33-120">Specifies the folder in which the measure will appear when users connect to the cube.</span></span> <span data-ttu-id="4cd33-121">多维数据集有很多度量值时，可以使用显示文件夹来对度量值进行分类，从而改善用户的浏览体验。</span><span class="sxs-lookup"><span data-stu-id="4cd33-121">When a cube has many measures, you can use display folders to categorize the measures and improve the user browsing experience.</span></span>|  
|`FormatString`|<span data-ttu-id="4cd33-122">通过使用度量值的 `FormatString` 属性，可以选择用于向用户显示度量值的格式。</span><span class="sxs-lookup"><span data-stu-id="4cd33-122">You can select the format that is used to display measure values to users by using the `FormatString` property of the measure.</span></span><br /><br /> <span data-ttu-id="4cd33-123">虽然 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中提供了显示格式的列表，但你仍可以指定多个该列表中没有的其他格式。</span><span class="sxs-lookup"><span data-stu-id="4cd33-123">Although a list of display formats is provided in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can specify many additional formats that are not in the list.</span></span> <span data-ttu-id="4cd33-124">您可以指定在 Microsoft Visual Basic 中有效的任何命名格式或用户定义格式。</span><span class="sxs-lookup"><span data-stu-id="4cd33-124">You can specify any named or user-defined format that is valid in Microsoft Visual Basic.</span></span>|  
|`ID`|<span data-ttu-id="4cd33-125">必需。</span><span class="sxs-lookup"><span data-stu-id="4cd33-125">Required.</span></span> <span data-ttu-id="4cd33-126">显示度量值的唯一标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="4cd33-126">Displays the unique identifier (ID) of the measure.</span></span> <span data-ttu-id="4cd33-127">此属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="4cd33-127">This property is read-only.</span></span>|  
|`MeasureExpression`|<span data-ttu-id="4cd33-128">指定定义度量值的值的受约束的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="4cd33-128">Specifies a constrained MDX expression defining the value of the measure.</span></span> <span data-ttu-id="4cd33-129">表达式在聚合之前在叶级进行求值，并且允许对值设置权重。</span><span class="sxs-lookup"><span data-stu-id="4cd33-129">The expression is evaluated at the leaf level before being aggregated, and allows for weighting of a value.</span></span> <span data-ttu-id="4cd33-130">例如，在货币转换中，销售额按汇率加权。</span><span class="sxs-lookup"><span data-stu-id="4cd33-130">For example, in currency conversion where a sales amount is weighted by the exchange rate.</span></span>|  
|`Name`|<span data-ttu-id="4cd33-131">必需。</span><span class="sxs-lookup"><span data-stu-id="4cd33-131">Required.</span></span> <span data-ttu-id="4cd33-132">指定度量值的名称。</span><span class="sxs-lookup"><span data-stu-id="4cd33-132">Specifies the name of the measure.</span></span>|  
|`Source`|<span data-ttu-id="4cd33-133">必需。</span><span class="sxs-lookup"><span data-stu-id="4cd33-133">Required.</span></span> <span data-ttu-id="4cd33-134">指定与度量值绑定的数据源视图中的列。</span><span class="sxs-lookup"><span data-stu-id="4cd33-134">Specifies the column in the data source view to which the measure is bound.</span></span> <span data-ttu-id="4cd33-135">请参阅[数据源和绑定（SSAS 多维）](data-sources-and-bindings-ssas-multidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd33-135">See [Data Sources and Bindings &#40;SSAS Multidimensional&#41;](data-sources-and-bindings-ssas-multidimensional.md).</span></span>|  
|`Visible`|<span data-ttu-id="4cd33-136">确定客户端应用程序中度量值的可见性。</span><span class="sxs-lookup"><span data-stu-id="4cd33-136">Determines the visibility of the measure in client applications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4cd33-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4cd33-137">See Also</span></span>  
 <span data-ttu-id="4cd33-138">[配置度量值组属性](configure-measure-group-properties.md) </span><span class="sxs-lookup"><span data-stu-id="4cd33-138">[Configure Measure Group Properties](configure-measure-group-properties.md) </span></span>  
 [<span data-ttu-id="4cd33-139">修改度量值</span><span class="sxs-lookup"><span data-stu-id="4cd33-139">Modifying Measures</span></span>](../lesson-3-1-modifying-measures.md)  
  
  
