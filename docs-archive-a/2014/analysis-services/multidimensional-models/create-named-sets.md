---
title: 创建命名集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], named sets
- named sets [Analysis Services]
- members [Analysis Services], named sets
ms.assetid: 03cf97a4-1a18-45f3-acb0-35123bd619be
author: minewiskan
ms.author: owend
ms.openlocfilehash: e92984102ceb8ad0ac049c15870e9f1efd6090fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687296"
---
# <a name="create-named-sets"></a><span data-ttu-id="d88c3-102">创建命名集</span><span class="sxs-lookup"><span data-stu-id="d88c3-102">Create Named Sets</span></span>
  <span data-ttu-id="d88c3-103">命名集是为重复使用而创建的一组维度成员或集表达式，例如用于多维表达式 (MDX) 查询中。</span><span class="sxs-lookup"><span data-stu-id="d88c3-103">A named set is a set of dimension members or a set expression that is created for reuse, for example in Multidimensional Expressions (MDX) queries.</span></span> <span data-ttu-id="d88c3-104">可以通过组合多维数据集数据、算数运算符、数字和函数来创建命名集。</span><span class="sxs-lookup"><span data-stu-id="d88c3-104">You can create named sets by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="d88c3-105">例如，可以创建一个名为“前十位工厂”的命名集，它包含“工厂”维度中具有最高的“产量”度量值的十个成员。</span><span class="sxs-lookup"><span data-stu-id="d88c3-105">For example, you can create a named set called Top Ten Factories that contains the ten members of the Factories dimension that have the highest values for the Production measure.</span></span> <span data-ttu-id="d88c3-106">然后最终用户可以在查询中使用“前十位工厂”。</span><span class="sxs-lookup"><span data-stu-id="d88c3-106">Top Ten Factories can then be used in queries by end users.</span></span> <span data-ttu-id="d88c3-107">例如，最终用户可以将“前十位工厂”放置在一个坐标轴上，将包含“产量”的“度量值”维度放置在另一个坐标轴上。</span><span class="sxs-lookup"><span data-stu-id="d88c3-107">For example, an end user can place Top Ten Factories on one axis and the Measures dimension, including Production, on another axis.</span></span> <span data-ttu-id="d88c3-108">有关详细信息，请参阅[多维模型中的计算](calculations-in-multidimensional-models.md)和[在 MDX 中生成命名集 (MDX)](mdx/mdx-named-sets-building-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="d88c3-108">For more information, see [Calculations in Multidimensional Models](calculations-in-multidimensional-models.md), and [Building Named Sets in MDX &#40;MDX&#41;](mdx/mdx-named-sets-building-named-sets.md).</span></span>  
  
 <span data-ttu-id="d88c3-109">若要创建命名集，请使用多维数据集设计器的 **“计算”** 选项卡上的 **“新建命名集”** 命令。</span><span class="sxs-lookup"><span data-stu-id="d88c3-109">To create a named set, use the **New Named Set** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="d88c3-110">可以在 **“计算”** 选项卡工具栏上的 **“多维数据集”** 菜单中调用该命令。</span><span class="sxs-lookup"><span data-stu-id="d88c3-110">This command can be invoked on the **Cube** menu on the **Calculations** tab toolbar.</span></span> <span data-ttu-id="d88c3-111">该命令显示了一个窗体，可指定下列命名集选项：</span><span class="sxs-lookup"><span data-stu-id="d88c3-111">This command displays a form to specify the following options for the named set:</span></span>  
  
 <span data-ttu-id="d88c3-112">**名称**</span><span class="sxs-lookup"><span data-stu-id="d88c3-112">**Name**</span></span>  
 <span data-ttu-id="d88c3-113">选择命名集的名称。</span><span class="sxs-lookup"><span data-stu-id="d88c3-113">Select the name of the named set.</span></span> <span data-ttu-id="d88c3-114">最终用户浏览多维数据集时将看到该名称。</span><span class="sxs-lookup"><span data-stu-id="d88c3-114">This name appears to end users when they browse the cube.</span></span>  
  
 <span data-ttu-id="d88c3-115">**表达式**</span><span class="sxs-lookup"><span data-stu-id="d88c3-115">**Expression**</span></span>  
 <span data-ttu-id="d88c3-116">指定生成命名集的表达式。</span><span class="sxs-lookup"><span data-stu-id="d88c3-116">Specify the expression that produces the named set.</span></span> <span data-ttu-id="d88c3-117">该表达式可以用 MDX 编写。</span><span class="sxs-lookup"><span data-stu-id="d88c3-117">This expression can be written in MDX.</span></span> <span data-ttu-id="d88c3-118">该表达式可以包含下列任何内容：</span><span class="sxs-lookup"><span data-stu-id="d88c3-118">The expression can contain any of the following:</span></span>  
  
-   <span data-ttu-id="d88c3-119">表示多维数据集的维度、级别、度量值等组件的数据表达式。</span><span class="sxs-lookup"><span data-stu-id="d88c3-119">Data expressions that represent cube components such as dimensions, levels, measures, and so on.</span></span>  
  
-   <span data-ttu-id="d88c3-120">算术运算符。</span><span class="sxs-lookup"><span data-stu-id="d88c3-120">Arithmetic operators.</span></span>  
  
-   <span data-ttu-id="d88c3-121">数字。</span><span class="sxs-lookup"><span data-stu-id="d88c3-121">Numbers.</span></span>  
  
-   <span data-ttu-id="d88c3-122">函数。</span><span class="sxs-lookup"><span data-stu-id="d88c3-122">Functions.</span></span>  
  
 <span data-ttu-id="d88c3-123">您可以将多维数据集组件从 **“计算工具”** 窗格的 **“元数据”** 选项卡中拖动或复制到 **“命名集窗体编辑器”** 窗格的 **“表达式”** 框中。</span><span class="sxs-lookup"><span data-stu-id="d88c3-123">You can copy or drag cube components from the **Metadata** tab of the **Calculation Tools** pane to the **Expression** box in the **Named Set Form Editor** pane.</span></span> <span data-ttu-id="d88c3-124">您可以将函数从 **“计算工具”** 窗格的 **“函数”** 选项卡中拖动或复制到 **“命名集窗体编辑器”** 窗格的 **“表达式”** 框中。</span><span class="sxs-lookup"><span data-stu-id="d88c3-124">You can copy or drag functions from the **Functions** tab in the **Calculation Tools** pane to the **Expression** box in the **Named Set Form Editor** pane.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d88c3-125">如果通过显式命名集中的成员来创建集表达式，请将成员列表括在一对大括号中， ({}) 。</span><span class="sxs-lookup"><span data-stu-id="d88c3-125">If you create the set expression by explicitly naming the members in the set, enclose the list of members in a pair of braces ({}).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d88c3-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d88c3-126">See Also</span></span>  
 [<span data-ttu-id="d88c3-127">多维模型中的计算</span><span class="sxs-lookup"><span data-stu-id="d88c3-127">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
