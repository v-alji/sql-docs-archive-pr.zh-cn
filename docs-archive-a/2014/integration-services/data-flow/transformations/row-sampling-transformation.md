---
title: 行抽样转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowsamplingtrans.f1
helpviewer_keywords:
- sampling seeds [Integration Services]
- random seeds
- random sampling
- sample data sets [Integration Services]
- Row Sampling transformation
- packages [Integration Services], samples
- datasets [Integration Services], sample
ms.assetid: b6caafd3-30b2-4368-82af-a44611d4cd39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c56f07d9fafa03752ef8c6572a13c6ad7c02a8c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694546"
---
# <a name="row-sampling-transformation"></a><span data-ttu-id="9eeb3-102">行抽样转换</span><span class="sxs-lookup"><span data-stu-id="9eeb3-102">Row Sampling Transformation</span></span>
  <span data-ttu-id="9eeb3-103">行抽样转换用于获取输入数据集的随机选择子集。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-103">The Row Sampling transformation is used to obtain a randomly selected subset of an input dataset.</span></span> <span data-ttu-id="9eeb3-104">您可以指定输出样本的准确大小，并指定随机数生成器的种子。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-104">You can specify the exact size of the output sample, and specify a seed for the random number generator.</span></span>  
  
 <span data-ttu-id="9eeb3-105">随机抽样有许多应用场合。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-105">There are many applications for random sampling.</span></span> <span data-ttu-id="9eeb3-106">例如，如果公司需要以抽彩给奖法随机选择 50 名雇员接受奖励，则可对雇员数据库使用行随机抽样转换来生成准确数目的获奖者。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-106">For example, a company that wanted to randomly select 50 employees to receive prizes in a lottery could use the Row Sampling transformation on the employee database to generate the exact number of winners.</span></span>  
  
 <span data-ttu-id="9eeb3-107">在包开发过程中，也可以使用行抽样转换来创建一个小但具有代表性的数据集。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-107">The Row Sampling transformation is also useful during package development for creating a small but representative dataset.</span></span> <span data-ttu-id="9eeb3-108">这样，您就可以使用很有代表性的数据来测试包执行和数据转换，而且这种测试更加快捷，因为它使用的是随机样本而不是全部数据集。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-108">You can test package execution and data transformation with richly representative data, but more quickly because a random sample is used instead of the full dataset.</span></span> <span data-ttu-id="9eeb3-109">因为测试包使用的样本数据集始终是同一大小，所以使用样本子集还可以轻松地识别出包中的性能问题。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-109">Because the sample dataset used by the test package is always the same size, using the sample subset also makes it easier to identify performance problems in the package.</span></span>  
  
 <span data-ttu-id="9eeb3-110">此转换类似于百分比抽样转换，后者通过选择输入行的百分比来创建样本数据集。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-110">This transformation is similar to the Percentage Sampling transformation, which creates a sample dataset by selecting a percentage of the input rows.</span></span> <span data-ttu-id="9eeb3-111">请参阅 [Percentage Sampling Transformation](percentage-sampling-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-111">See [Percentage Sampling Transformation](percentage-sampling-transformation.md).</span></span>  
  
## <a name="configuring-the-row-sampling-transformation"></a><span data-ttu-id="9eeb3-112">配置行抽样转换</span><span class="sxs-lookup"><span data-stu-id="9eeb3-112">Configuring the Row Sampling Transformation</span></span>  
 <span data-ttu-id="9eeb3-113">行抽样转换通过选择指定数目的转换输入行来创建样本数据集。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-113">The Row Sampling transformation creates a sample dataset by selecting a specified number of the transformation input rows.</span></span> <span data-ttu-id="9eeb3-114">因为从转换输入中选择的行是随机的，因此结果样本可以代表输入。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-114">Because the selection of rows from the transformation input is random, the resultant sample is representative of the input.</span></span> <span data-ttu-id="9eeb3-115">还可以指定随机数生成器使用的种子来影响转换选择行的方式。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-115">You can also specify the seed that is used by the random number generator, to affect how the transformation selects rows.</span></span>  
  
 <span data-ttu-id="9eeb3-116">在同一转换输入上使用相同的随机种子将始终创建相同的样本输出。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-116">Using the same random seed on the same transformation input always creates the same sample output.</span></span> <span data-ttu-id="9eeb3-117">如果没有指定种子，转换将使用操作系统的时钟周期数来创建随机数。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-117">If no seed is specified, the transformation uses the tick count of the operating system to create the random number.</span></span> <span data-ttu-id="9eeb3-118">因此，可使用测试期间使用的种子来验证包开发和测试期间的转换结果，然后在包进入生产阶段时改用随机种子。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-118">Therefore, you could use the same seed during testing, to verify the transformation results during the development and testing of the package, and then change to a random seed when the package is moved into production.</span></span>  
  
 <span data-ttu-id="9eeb3-119">行抽样转换包括 `SamplingValue` 自定义属性。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-119">The Row Sampling transformation includes the `SamplingValue` custom property.</span></span> <span data-ttu-id="9eeb3-120">加载包时，可以通过属性表达式更新此属性。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-120">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="9eeb3-121">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../../expressions/integration-services-ssis-expressions.md)、[在包中使用属性表达式](../../expressions/use-property-expressions-in-packages.md)和[转换自定义属性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-121">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="9eeb3-122">此转换有一个输入和两个输出。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-122">This transformation has one input and two outputs.</span></span> <span data-ttu-id="9eeb3-123">它没有错误输出。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-123">It has no error output.</span></span>  
  
 <span data-ttu-id="9eeb3-124">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-124">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="9eeb3-125">有关可以在“百分比抽样转换编辑器”\*\*\*\* 对话框中设置的属性的详细信息，请参阅[行抽样转换编辑器（“抽样”页）](../../row-sampling-transformation-editor-sampling-page.md)。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-125">For more information about the properties that you can set in the **Row Sampling Transformation Editor** dialog box, see [Row Sampling Transformation Editor &#40;Sampling Page&#41;](../../row-sampling-transformation-editor-sampling-page.md).</span></span>  
  
 <span data-ttu-id="9eeb3-126">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="9eeb3-126">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="9eeb3-127">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="9eeb3-127">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="9eeb3-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="9eeb3-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="9eeb3-129">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="9eeb3-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="9eeb3-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="9eeb3-130">Related Tasks</span></span>  
 [<span data-ttu-id="9eeb3-131">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="9eeb3-131">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
  
