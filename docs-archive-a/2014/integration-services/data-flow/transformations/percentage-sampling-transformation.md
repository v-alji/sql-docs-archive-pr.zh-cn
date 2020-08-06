---
title: 百分比抽样转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtrans.f1
helpviewer_keywords:
- testing mining models
- sampling seeds [Integration Services]
- data mining [Analysis Services], sample data sets
- Percentage Sampling transformation
- sample data sets [Integration Services]
- datasets [Integration Services], sample
- training mining models
ms.assetid: 59767e52-f732-4b3f-8602-be50d0a64ef2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e5fe41ecf4a2ca0f9d20eec2c8e10af8ed4cd47b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694549"
---
# <a name="percentage-sampling-transformation"></a><span data-ttu-id="a661f-102">百分比抽样转换</span><span class="sxs-lookup"><span data-stu-id="a661f-102">Percentage Sampling Transformation</span></span>
  <span data-ttu-id="a661f-103">百分比抽样转换通过选择转换输入行的百分比来创建样本数据集。</span><span class="sxs-lookup"><span data-stu-id="a661f-103">The Percentage Sampling transformation creates a sample data set by selecting a percentage of the transformation input rows.</span></span> <span data-ttu-id="a661f-104">样本数据集是从转换输入中随机选择的行，这使得结果样本可以代表输入。</span><span class="sxs-lookup"><span data-stu-id="a661f-104">The sample data set is a random selection of rows from the transformation input, to make the resultant sample representative of the input.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a661f-105">除指定的百分比以外，百分比抽样转换还使用某种算法来决定样本输出中是否应包含某一行。</span><span class="sxs-lookup"><span data-stu-id="a661f-105">In addition to the specified percentage, the Percentage Sampling transformation uses an algorithm to determine whether a row should be included in the sample output.</span></span> <span data-ttu-id="a661f-106">这意味着样本输出中的行数可能无法精确地反映指定的百分比。</span><span class="sxs-lookup"><span data-stu-id="a661f-106">This means that the number of rows in the sample output may not exactly reflect the specified percentage.</span></span> <span data-ttu-id="a661f-107">例如，为具有 25000 行的输入数据集指定 10% 可能不会生成具有 2500 行的样本；样本的行数可能略多于或略少于 2500 行。</span><span class="sxs-lookup"><span data-stu-id="a661f-107">For example, specifying 10 percent for an input data set that has 25,000 rows may not generate a sample with 2,500 rows; the sample may have a few more or a few less rows.</span></span>  
  
 <span data-ttu-id="a661f-108">百分比抽样转换对数据挖掘尤其有用。</span><span class="sxs-lookup"><span data-stu-id="a661f-108">The Percentage Sampling transformation is especially useful for data mining.</span></span> <span data-ttu-id="a661f-109">通过使用此转换，您可以将一个数据集随机划分为两个数据集：一个用于定型数据挖掘模型，另一个用于测试模型。</span><span class="sxs-lookup"><span data-stu-id="a661f-109">By using this transformation, you can randomly divide a data set into two data sets: one for training the data mining model, and one for testing the model.</span></span>  
  
 <span data-ttu-id="a661f-110">百分比抽样转换对于创建用于包开发的样本数据集也很有用。</span><span class="sxs-lookup"><span data-stu-id="a661f-110">The Percentage Sampling transformation is also useful for creating sample data sets for package development.</span></span> <span data-ttu-id="a661f-111">通过对数据流应用百分比抽样转换，可以在保持数据集的数据特性的同时均匀地缩减数据集的大小。</span><span class="sxs-lookup"><span data-stu-id="a661f-111">By applying the Percentage Sampling transformation to a data flow, you can uniformly reduce the size of the data set while preserving its data characteristics.</span></span> <span data-ttu-id="a661f-112">然后，测试包就可以更快地运行，因为它使用小但具有代表性的数据集。</span><span class="sxs-lookup"><span data-stu-id="a661f-112">The test package can then run more quickly because it uses a small, but representative, data set.</span></span>  
  
## <a name="configuration-the-percentage-sampling-transformation"></a><span data-ttu-id="a661f-113">百分比抽样转换的配置</span><span class="sxs-lookup"><span data-stu-id="a661f-113">Configuration the Percentage Sampling Transformation</span></span>  
 <span data-ttu-id="a661f-114">可以通过指定抽样种子来修改随机数生成器（转换通过随机数生成器来选择行）的行为。</span><span class="sxs-lookup"><span data-stu-id="a661f-114">You can specify a sampling seed to modify the behavior of the random number generator that the transformation uses to select rows.</span></span> <span data-ttu-id="a661f-115">如果使用相同的抽样种子，转换将始终创建相同的样本输出。</span><span class="sxs-lookup"><span data-stu-id="a661f-115">If the same sampling seed is used, the transformation always creates the same sample output.</span></span> <span data-ttu-id="a661f-116">如果没有指定种子，转换将使用操作系统的时钟周期数来创建随机数。</span><span class="sxs-lookup"><span data-stu-id="a661f-116">If no seed is specified, the transformation uses the tick count of the operating system to create the random number.</span></span> <span data-ttu-id="a661f-117">因此，在包的开发和测试期间，需要验证转换结果时可选择使用标准种子，然后在包正式投入生产后再改为使用随机种子。</span><span class="sxs-lookup"><span data-stu-id="a661f-117">Therefore, you might choose to use a standard seed when you want to verify the transformation results during the development and testing of a package, and then change to use a random seed when the package is moved into production.</span></span>  
  
 <span data-ttu-id="a661f-118">此转换类似于行抽样转换，后者通过选择指定数量的输入行来创建样本数据集。</span><span class="sxs-lookup"><span data-stu-id="a661f-118">This transformation is similar to the Row Sampling transformation, which creates a sample data set by selecting a specified number of the input rows.</span></span> <span data-ttu-id="a661f-119">有关详细信息，请参阅 [Row Sampling Transformation](row-sampling-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="a661f-119">For more information, see [Row Sampling Transformation](row-sampling-transformation.md).</span></span>  
  
 <span data-ttu-id="a661f-120">百分比抽样转换包括 `SamplingValue` 自定义属性。</span><span class="sxs-lookup"><span data-stu-id="a661f-120">The Percentage Sampling transformation includes the `SamplingValue` custom property.</span></span> <span data-ttu-id="a661f-121">加载包时，可以通过属性表达式更新此属性。</span><span class="sxs-lookup"><span data-stu-id="a661f-121">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="a661f-122">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../../expressions/integration-services-ssis-expressions.md)、[在包中使用属性表达式](../../expressions/use-property-expressions-in-packages.md)和[转换自定义属性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a661f-122">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="a661f-123">该转换有一个输入和两个输出。</span><span class="sxs-lookup"><span data-stu-id="a661f-123">The transformation has one input and two outputs.</span></span> <span data-ttu-id="a661f-124">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="a661f-124">It does not support an error output.</span></span>  
  
 <span data-ttu-id="a661f-125">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="a661f-125">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a661f-126">有关可以在 **“百分比抽样转换编辑器”** 对话框中设置的属性的详细信息，请参阅 [Percentage Sampling Transformation Editor](../../percentage-sampling-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="a661f-126">For more information about the properties that you can set in the **Percentage Sampling Transformation Editor** dialog box, see [Percentage Sampling Transformation Editor](../../percentage-sampling-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="a661f-127">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="a661f-127">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="a661f-128">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="a661f-128">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a661f-129">Common Properties</span><span class="sxs-lookup"><span data-stu-id="a661f-129">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="a661f-130">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="a661f-130">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="a661f-131">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="a661f-131">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
