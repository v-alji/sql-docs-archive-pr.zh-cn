---
title: 为维度中的属性设置自定义成员公式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], custom member formulas
- member formulas [Analysis Services]
- dimensions [Analysis Services], Business Intelligence enhancements
- custom member formulas [Analysis Services]
- CustomRollupColumn property
ms.assetid: c4467b08-ce59-4de7-a2d9-c22e246bdd52
author: minewiskan
ms.author: owend
ms.openlocfilehash: 112f8944bd20b2b6a464b0d84fb8ac1a0e89d976
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579855"
---
# <a name="set-custom-member-formulas-for-attributes-in-a-dimension"></a><span data-ttu-id="8362a-102">为维度中的属性设置自定义成员公式</span><span class="sxs-lookup"><span data-stu-id="8362a-102">Set Custom Member Formulas for Attributes in a Dimension</span></span>
  <span data-ttu-id="8362a-103">通过在多维数据集或维度中添加自定义成员公式增强功能，可以使用多维表达式 (MDX) 表达式的结果替换与维度成员关联的默认聚合。</span><span class="sxs-lookup"><span data-stu-id="8362a-103">Add a custom member formula enhancement to a cube or dimension to replace the default aggregation that is associated with a dimension member with the results of a Multidimensional Expressions (MDX) expression.</span></span> <span data-ttu-id="8362a-104">（此增强功能将设置维度中的指定特性的 `CustomRollupColumn` 属性。）</span><span class="sxs-lookup"><span data-stu-id="8362a-104">(This enhancement sets the `CustomRollupColumn` property on a specified attribute in a dimension.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8362a-105">自定义成员公式只对基于现有数据源的维度可用。</span><span class="sxs-lookup"><span data-stu-id="8362a-105">A custom member formula is available only for dimensions that are based on existing data sources.</span></span> <span data-ttu-id="8362a-106">对于不使用数据源所创建的维度，则必须运行架构生成向导，以便在添加自定义成员公式之前创建数据源视图。</span><span class="sxs-lookup"><span data-stu-id="8362a-106">For dimensions that were created without using a data source, you must run the Schema Generation Wizard to create a data source view before adding a custom member formula.</span></span>  
  
 <span data-ttu-id="8362a-107">若要添加自定义成员公式，请使用商业智能向导，并在 **“选择增强功能”** 页上选择 **“创建自定义成员公式”** 选项。</span><span class="sxs-lookup"><span data-stu-id="8362a-107">To add a custom member formula, you use the Business Intelligence Wizard, and select the **Create a custom member formula** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="8362a-108">然后，此向导将指引您完成相应的步骤，以选择要应用自定义成员公式的维度，并启用自定义成员公式。</span><span class="sxs-lookup"><span data-stu-id="8362a-108">This wizard then guides you through the steps of selecting a dimension to which you want to apply a custom member formula and enabling the custom member formula.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="8362a-109">选择维度</span><span class="sxs-lookup"><span data-stu-id="8362a-109">Selecting a Dimension</span></span>  
 <span data-ttu-id="8362a-110">在向导的第一个 **“创建自定义成员公式”** 页中，指定希望应用自定义成员公式的维度。</span><span class="sxs-lookup"><span data-stu-id="8362a-110">On the first **Create a Custom Member Formula** page of the wizard, you specify the dimension to which you want to apply a custom member formula.</span></span> <span data-ttu-id="8362a-111">添加到此所选维度中的自定义成员公式增强功能将使维度发生更改。</span><span class="sxs-lookup"><span data-stu-id="8362a-111">The custom member formula enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="8362a-112">所有包含选定维度的多维数据集都将继承这些更改。</span><span class="sxs-lookup"><span data-stu-id="8362a-112">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="enabling-a-custom-member-formula"></a><span data-ttu-id="8362a-113">启用自定义成员公式</span><span class="sxs-lookup"><span data-stu-id="8362a-113">Enabling a Custom Member Formula</span></span>  
 <span data-ttu-id="8362a-114">在第二个 **“创建自定义成员公式”** 页中，将包含自定义成员公式的源列与维度中的一个或多个属性关联。</span><span class="sxs-lookup"><span data-stu-id="8362a-114">On the second **Create a Custom Member Formula** page, you associate the source column that contains the custom member formula with one or more attributes in the dimension.</span></span> <span data-ttu-id="8362a-115">在 **“属性”** 列中，选中要与自定义成员公式列关联的属性旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="8362a-115">In the **Attribute** column, select the check box next to the attribute that you want to associate with the custom member formula column.</span></span> <span data-ttu-id="8362a-116">选择每个属性之后，向导将显示 **“选择列”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="8362a-116">After you select each attribute, the wizard displays the **Select a Column** dialog box.</span></span> <span data-ttu-id="8362a-117">在此对话框中，单击包含公式的维度表中的列。</span><span class="sxs-lookup"><span data-stu-id="8362a-117">In this dialog box, click the column in the dimension table that contains the formula.</span></span> <span data-ttu-id="8362a-118">如果在关闭“选择列”对话框之后希望更改选择，请单击希望更改的“源列”单元，再单击省略号 (**...**) 以再次打开“选择列”对话框。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8362a-118">If you want to change a selection after you close the **Select a Column** dialog box, click the **Source Column** cell that you want to change, and then click the ellipsis (**...**) to open the **Select a Column** dialog box again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8362a-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8362a-119">See Also</span></span>  
 [<span data-ttu-id="8362a-120">使用商业智能向导增强维度</span><span class="sxs-lookup"><span data-stu-id="8362a-120">Use the Business Intelligence Wizard to Enhance Dimensions</span></span>](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
  
  
