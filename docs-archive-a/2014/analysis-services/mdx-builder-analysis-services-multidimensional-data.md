---
title: MDX 生成器 (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.mdxbuilderdialof.f1
helpviewer_keywords:
- MDX Builder dialog box
ms.assetid: fecbf093-65ea-4e1b-b637-f04876f1cb0f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 391f4abe953184470be60cca41d53ee20e965423
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587641"
---
# <a name="mdx-builder-analysis-services---multidimensional-data"></a><span data-ttu-id="feba0-102">MDX 生成器（Analysis Services -多维数据）</span><span class="sxs-lookup"><span data-stu-id="feba0-102">MDX Builder (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="feba0-103">可以使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 或 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的“MDX 生成器”\*\*\*\* 对话框生成多维表达式 (MDX) 表达式。</span><span class="sxs-lookup"><span data-stu-id="feba0-103">Use the **MDX Builder** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to build a Multidimensional Expressions (MDX) expression.</span></span> <span data-ttu-id="feba0-104">通过在**角色设计器**的 "**单元数据**" 页上，单击 "**编辑 mdx** " 省略号按钮 (**...** ") 对于"**允许读取多维数据集内容**"选项、" 允许读取单元格**内容的单元**格内容 "选项或"**允许读取和写入多维数据集内容**"选项，可以显示" **mdx 生成器**"对话框。</span><span class="sxs-lookup"><span data-stu-id="feba0-104">You can display the **MDX Builder** dialog box by clicking the **Edit MDX** ellipsis button (**...**) for the **Allow reading of cube content** option, the **Allow reading of cell content contingent on cell security** option, or the **Allow reading and writing of cube content** option on the **Cell Data** page of **Role Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="feba0-105">选项</span><span class="sxs-lookup"><span data-stu-id="feba0-105">Options</span></span>  
  
|<span data-ttu-id="feba0-106">术语</span><span class="sxs-lookup"><span data-stu-id="feba0-106">Term</span></span>|<span data-ttu-id="feba0-107">定义</span><span class="sxs-lookup"><span data-stu-id="feba0-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="feba0-108">**表达式**</span><span class="sxs-lookup"><span data-stu-id="feba0-108">**Expression**</span></span>|<span data-ttu-id="feba0-109">键入要使用的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="feba0-109">Type the MDX expression to be used.</span></span>|  
|<span data-ttu-id="feba0-110">**检查**</span><span class="sxs-lookup"><span data-stu-id="feba0-110">**Check**</span></span>|<span data-ttu-id="feba0-111">单击 **“检查”** 可以测试 **“表达式”** 中定义的 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="feba0-111">Click **Check** to test the MDX expression defined in **Expression**.</span></span>|  
|<span data-ttu-id="feba0-112">Metadata</span><span class="sxs-lookup"><span data-stu-id="feba0-112">**Metadata**</span></span>|<span data-ttu-id="feba0-113">显示可以包含在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] “表达式” **中所定义的 MDX 表达式中的当前**对象的元数据。</span><span class="sxs-lookup"><span data-stu-id="feba0-113">Displays metadata for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object that can be included in the MDX expression defined in **Expression**.</span></span><br /><br /> <span data-ttu-id="feba0-114">通过右键单击所选项，然后从上下文菜单中选择“复制”\*\*\*\*，或者将所选项拖到“表达式”\*\*\*\*，可以复制所选项的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="feba0-114">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy** from the context menu, or by dragging the selected item to **Expression**.</span></span>|  
|<span data-ttu-id="feba0-115">**函数**</span><span class="sxs-lookup"><span data-stu-id="feba0-115">**Functions**</span></span>|<span data-ttu-id="feba0-116">显示当前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的可用 MDX 函数。</span><span class="sxs-lookup"><span data-stu-id="feba0-116">Displays available MDX functions for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="feba0-117">可以从 MDSCHEMA_FUNCTIONS 架构行集中检索所列项。</span><span class="sxs-lookup"><span data-stu-id="feba0-117">The items listed are retrieved from the MDSCHEMA_FUNCTIONS schema rowset.</span></span><br /><br /> <span data-ttu-id="feba0-118">通过右键单击所选项，然后从上下文菜单中选择“复制”\*\*\*\*，或者将所选项拖到“表达式”\*\*\*\*，可以复制所选项的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="feba0-118">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy** from the context menu, or by dragging the selected item to **Expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="feba0-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="feba0-119">See Also</span></span>  
 <span data-ttu-id="feba0-120">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="feba0-120">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="feba0-121">[单元数据 &#40;角色设计器&#41; &#40;Analysis Services 多维数据&#41;](https://msdn.microsoft.com/library/ms177279(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="feba0-121">[Cell Data &#40;Role Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](https://msdn.microsoft.com/library/ms177279(v=sql.120).aspx)</span></span>  
  
  
