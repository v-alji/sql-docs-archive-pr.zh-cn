---
title: 将自定义聚合添加到维度 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], custom aggregations
- aggregations [Analysis Services], custom
- unary operators
- custom aggregations [Analysis Services]
ms.assetid: 3199a6c2-a06d-47b9-bd1c-604dbb085318
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed843b8b0005ff62f05b13ebd20024d528857388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577893"
---
# <a name="add-a-custom-aggregation-to-a-dimension"></a><span data-ttu-id="f7534-102">向维度中添加自定义聚合</span><span class="sxs-lookup"><span data-stu-id="f7534-102">Add a Custom Aggregation to a Dimension</span></span>
  <span data-ttu-id="f7534-103">在多维数据集或维度中添加自定义聚合增强功能，以使用其他一元运算符替换与维度成员关联的默认聚合。</span><span class="sxs-lookup"><span data-stu-id="f7534-103">Add a custom aggregation enhancement to a cube or dimension to replace the default aggregations that are associated with a dimension member with a different unary operator.</span></span> <span data-ttu-id="f7534-104">这种增强功能指定维度表中定义父子层次结构中的成员汇总的一元运算符列。</span><span class="sxs-lookup"><span data-stu-id="f7534-104">This enhancement specifies a unary operator column in the dimension table that defines rollup for members in a parent-child hierarchy.</span></span> <span data-ttu-id="f7534-105">一元运算符对父子层次结构中的父属性进行操作。</span><span class="sxs-lookup"><span data-stu-id="f7534-105">The unary operator acts on the parent attribute in a parent-child hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7534-106">自定义聚合仅可用于基于现有数据源的维度。</span><span class="sxs-lookup"><span data-stu-id="f7534-106">A custom aggregation is available only for dimensions that are based on existing data sources.</span></span> <span data-ttu-id="f7534-107">对于不使用数据源创建的维度，必须先运行架构生成向导创建数据源视图，然后再添加自定义聚合。</span><span class="sxs-lookup"><span data-stu-id="f7534-107">For dimensions that were created without using a data source, you must run the Schema Generation Wizard to create a data source view before adding the custom aggregation.</span></span>  
  
 <span data-ttu-id="f7534-108">若要添加自定义聚合，请使用商业智能向导，并在 **“选择增强功能”** 页中选择 **“指定一元运算符”** 选项。</span><span class="sxs-lookup"><span data-stu-id="f7534-108">To add a custom aggregation, you use the Business Intelligence Wizard, and select the **Specify a unary operator** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="f7534-109">然后，该向导引导您完成两个步骤：选择要应用自定义聚合的维度和标识自定义聚合。</span><span class="sxs-lookup"><span data-stu-id="f7534-109">This wizard then guides you through the steps of selecting a dimension to which you want to apply a custom aggregation and identifying the custom aggregation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7534-110">在运行商业智能向导添加自定义聚合之前，请确保要增强的维度包含父子属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="f7534-110">Before you run the Business Intelligence Wizard to add a custom aggregation, make sure that the dimension that you want to enhance contains a parent-child attribute hierarchy.</span></span> <span data-ttu-id="f7534-111">有关详细信息，请参阅[父子层次结构](parent-child-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="f7534-111">For more information, see [Parent-Child Hierarchy](parent-child-dimension.md).</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="f7534-112">选择维度</span><span class="sxs-lookup"><span data-stu-id="f7534-112">Selecting a Dimension</span></span>  
 <span data-ttu-id="f7534-113">在向导的第一个 **“指定一元运算符”** 页中，指定要应用自定义聚合的维度。</span><span class="sxs-lookup"><span data-stu-id="f7534-113">On the first **Specify a Unary Operator** page of the wizard, you specify the dimension to which you want to apply a custom aggregation.</span></span> <span data-ttu-id="f7534-114">已添加到该选定维度中的自定义聚合将会使维度发生更改。</span><span class="sxs-lookup"><span data-stu-id="f7534-114">The custom aggregation added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="f7534-115">所有包含选定维度的多维数据集都将继承这些更改。</span><span class="sxs-lookup"><span data-stu-id="f7534-115">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="adding-custom-aggregation-unary-operator"></a><span data-ttu-id="f7534-116">添加自定义聚合（一元运算符）</span><span class="sxs-lookup"><span data-stu-id="f7534-116">Adding Custom Aggregation (Unary Operator)</span></span>  
 <span data-ttu-id="f7534-117">在第二个 **“指定一元运算符”** 页中，为自定义聚合指定所需的父属性，并为一元运算符指定维度表中的源列。</span><span class="sxs-lookup"><span data-stu-id="f7534-117">On the second **Specify a Unary Operator** page, you specify the parent attribute that you want for the custom aggregation and the source column in the dimension table for the unary operator.</span></span> <span data-ttu-id="f7534-118">**Parent 特性**列出了 `Usage` 属性设置为的特性 `Parent` 。</span><span class="sxs-lookup"><span data-stu-id="f7534-118">**Parent attribute** lists attributes that have their `Usage` property set to `Parent`.</span></span> <span data-ttu-id="f7534-119">如果具有多个父属性，则选择对应于要使用的父子关系的父属性。</span><span class="sxs-lookup"><span data-stu-id="f7534-119">If there is more than one parent attribute, choose the parent attribute that corresponds to the parent-child relationship that you want to use.</span></span> <span data-ttu-id="f7534-120">如果没有列出父属性，则维度不存在有效的父子层次结构。</span><span class="sxs-lookup"><span data-stu-id="f7534-120">If there is no parent attribute listed, then the dimension does not have a valid parent-child hierarchy.</span></span>  
  
 <span data-ttu-id="f7534-121">在 **“源列”** 中，选择包含一元运算符的字符串列。</span><span class="sxs-lookup"><span data-stu-id="f7534-121">In **Source column**, you select the string column that contains the unary operators.</span></span> <span data-ttu-id="f7534-122"> (此选择将设置 `UnaryOperatorColumn` 父特性的属性。 ) 维度表还应具有指定一元汇总运算符的字符串列。</span><span class="sxs-lookup"><span data-stu-id="f7534-122">(This selection sets the `UnaryOperatorColumn` property on the parent attribute.) The dimension table should also have a string column that specifies the unary rollup operator.</span></span> <span data-ttu-id="f7534-123">该列中的字符串值应包含有效的聚合运算符。</span><span class="sxs-lookup"><span data-stu-id="f7534-123">The string values in this column should contain valid aggregation operators.</span></span> <span data-ttu-id="f7534-124">如果某行为空，则通常计算对应的成员。</span><span class="sxs-lookup"><span data-stu-id="f7534-124">If a row is empty, the corresponding member is calculated normally.</span></span> <span data-ttu-id="f7534-125">如果列中的公式无效，则当检索使用成员的单元值时，会出现运行时错误。</span><span class="sxs-lookup"><span data-stu-id="f7534-125">If the formula in a column is not valid, a run-time error occurs when a cell value that uses the member is retrieved.</span></span> <span data-ttu-id="f7534-126">有关详细信息，请参阅 [父子维度中的一元运算符](parent-child-dimension-attributes-unary-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="f7534-126">For more information, see [Unary Operators in Parent-Child Dimensions](parent-child-dimension-attributes-unary-operators.md).</span></span>  
  
  
