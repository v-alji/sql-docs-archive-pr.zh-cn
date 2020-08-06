---
title: "\"计算成员生成器\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.calculatedmemberbuilderdialog.f1
ms.assetid: 73b89a9f-f403-4ab8-99f7-e3ceb870c260
author: minewiskan
ms.author: owend
ms.openlocfilehash: 240e2f2471bf77c403119fd51278a975badc8358
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579287"
---
# <a name="calculated-member-builder-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="2e730-102">“计算成员生成器”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="2e730-102">Calculated Member Builder Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="2e730-103">可以使用 **中的** “计算成员生成器” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框生成计算成员。</span><span class="sxs-lookup"><span data-stu-id="2e730-103">Use the **Calculated Member Builder** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to build a calculated member.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2e730-104">选项</span><span class="sxs-lookup"><span data-stu-id="2e730-104">Options</span></span>  
  
|<span data-ttu-id="2e730-105">术语</span><span class="sxs-lookup"><span data-stu-id="2e730-105">Term</span></span>|<span data-ttu-id="2e730-106">定义</span><span class="sxs-lookup"><span data-stu-id="2e730-106">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="2e730-107">**名称**</span><span class="sxs-lookup"><span data-stu-id="2e730-107">**Name**</span></span>|<span data-ttu-id="2e730-108">键入计算成员的名称。</span><span class="sxs-lookup"><span data-stu-id="2e730-108">Type the name of the calculated member.</span></span>|  
|<span data-ttu-id="2e730-109">**父层次结构**</span><span class="sxs-lookup"><span data-stu-id="2e730-109">**Parent Hierarchy**</span></span>|<span data-ttu-id="2e730-110">选择要在其中创建计算成员的层次结构。</span><span class="sxs-lookup"><span data-stu-id="2e730-110">Select the hierarchy in which to create the calculated member.</span></span>|  
|<span data-ttu-id="2e730-111">**父成员**</span><span class="sxs-lookup"><span data-stu-id="2e730-111">**Parent Member**</span></span>|<span data-ttu-id="2e730-112">如果选择具有多个级别的父层次结构（`Measures` 维度除外），则将启用此选项。</span><span class="sxs-lookup"><span data-stu-id="2e730-112">This option is enabled if you select a parent hierarchy (other than the `Measures` dimension) that has more than one level.</span></span> <span data-ttu-id="2e730-113">单击**省略号 ("**) " 按钮以选择父成员。</span><span class="sxs-lookup"><span data-stu-id="2e730-113">Click the ellipsis (**...**) button to select a parent member.</span></span> <span data-ttu-id="2e730-114">父成员确定计算成员在维度结构中的位置。</span><span class="sxs-lookup"><span data-stu-id="2e730-114">The parent member determines the location of the calculated member in the dimension structure.</span></span>|  
|<span data-ttu-id="2e730-115">**表达式**</span><span class="sxs-lookup"><span data-stu-id="2e730-115">**Expression**</span></span>|<span data-ttu-id="2e730-116">键入要使用的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="2e730-116">Type the MDX expression that will be used.</span></span>|  
|<span data-ttu-id="2e730-117">**检查**</span><span class="sxs-lookup"><span data-stu-id="2e730-117">**Check**</span></span>|<span data-ttu-id="2e730-118">单击 **“检查”** 可以测试 **“表达式”** 中定义的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="2e730-118">Click **Check** to test the MDX expression defined in **Expression**.</span></span>|  
|<span data-ttu-id="2e730-119">Metadata</span><span class="sxs-lookup"><span data-stu-id="2e730-119">**Metadata**</span></span>|<span data-ttu-id="2e730-120">显示可以包含在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] “表达式” **中所定义的 MDX 表达式中的当前**对象的元数据。</span><span class="sxs-lookup"><span data-stu-id="2e730-120">Displays metadata for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object that can be included in the MDX expression defined in **Expression**.</span></span><br /><br /> <span data-ttu-id="2e730-121">通过右键单击所选项，然后选择“复制”，或者将所选项拖到“表达式”，可以复制所选项的 MDX 语法\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2e730-121">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy**, or by dragging the selected item to **Expression**.</span></span>|  
|<span data-ttu-id="2e730-122">**函数**</span><span class="sxs-lookup"><span data-stu-id="2e730-122">**Functions**</span></span>|<span data-ttu-id="2e730-123">显示当前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的可用 MDX 函数。</span><span class="sxs-lookup"><span data-stu-id="2e730-123">Displays the available MDX functions for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="2e730-124">可以从 MDSCHEMA_FUNCTIONS 架构行集中检索所列项。</span><span class="sxs-lookup"><span data-stu-id="2e730-124">The items listed are retrieved from the MDSCHEMA_FUNCTIONS schema rowset.</span></span><br /><br /> <span data-ttu-id="2e730-125">通过右键单击所选项，然后选择“复制”，或者将所选项拖到“表达式”，可以复制所选项的 MDX 语法\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2e730-125">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy**, or by dragging the selected item to **Expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e730-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2e730-126">See Also</span></span>  
 [<span data-ttu-id="2e730-127">多维表达式 (MDX) 参考</span><span class="sxs-lookup"><span data-stu-id="2e730-127">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
