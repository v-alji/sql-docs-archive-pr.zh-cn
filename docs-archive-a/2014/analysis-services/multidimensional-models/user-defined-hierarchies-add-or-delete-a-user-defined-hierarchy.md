---
title: 添加或删除用户定义的层次结构 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], adding
- removing hierarchies
- adding hierarchies
- deleting hierarchies
- hierarchies [Analysis Services], removing
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
author: minewiskan
ms.author: owend
ms.openlocfilehash: d20404a1d93d57221eb830366392eb90600f26c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588091"
---
# <a name="add-or-delete-a-user-defined-hierarchy"></a><span data-ttu-id="a698f-102">添加或删除用户定义层次结构</span><span class="sxs-lookup"><span data-stu-id="a698f-102">Add or Delete a User-Defined Hierarchy</span></span>
  <span data-ttu-id="a698f-103">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，可以从维度设计器中的“维度结构”\*\*\*\* 选项卡上的维度中添加或删除用户定义的层次结构。</span><span class="sxs-lookup"><span data-stu-id="a698f-103">You add a user-defined hierarchy to or remove a user-defined hierarchy from a dimension on the **Dimension Structure** tab in Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="a698f-104">在添加用户定义的层次结构后，在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例中实例化此层次结构并且处理维度之前，用户无法使用此层次结构。</span><span class="sxs-lookup"><span data-stu-id="a698f-104">When you add a user-defined hierarchy, it is not available to users until it is instantiated in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and the dimension is processed.</span></span> <span data-ttu-id="a698f-105">有关详细信息，请参阅[多维模型数据库 &#40;SSAS&#41;](multidimensional-model-databases-ssas.md)和[多维模型对象处理](processing-a-multidimensional-model-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a698f-105">For more information, see [Multidimensional Model Databases &#40;SSAS&#41;](multidimensional-model-databases-ssas.md) and [Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
### <a name="to-add-a-user-defined-hierarchy-to-a-dimension"></a><span data-ttu-id="a698f-106">向维度添加用户定义层次结构</span><span class="sxs-lookup"><span data-stu-id="a698f-106">To add a user-defined hierarchy to a dimension</span></span>  
  
1.  <span data-ttu-id="a698f-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开相应的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目，然后打开要使用的维度。</span><span class="sxs-lookup"><span data-stu-id="a698f-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the appropriate [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then open the dimension with which you want to work.</span></span>  
  
     <span data-ttu-id="a698f-108">该维度会在维度设计器的 **“维度结构”** 选项卡上打开。</span><span class="sxs-lookup"><span data-stu-id="a698f-108">The dimension opens in Dimension Designer on the **Dimension Structure** tab.</span></span>  
  
2.  <span data-ttu-id="a698f-109">将要在用户定义的层次结构中使用的属性从“属性”\*\*\*\* 窗格拖至“层次结构”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="a698f-109">From the **Attributes** pane, drag an attribute that you want to use in the user-defined hierarchy to the **Hierarchies** pane.</span></span>  
  
3.  <span data-ttu-id="a698f-110">拖动其他属性以在用户定义层次结构中建立级别。</span><span class="sxs-lookup"><span data-stu-id="a698f-110">Drag additional attributes to form levels in the user-defined hierarchy.</span></span>  
  
     <span data-ttu-id="a698f-111">属性在层次结构中的列出顺序非常重要。</span><span class="sxs-lookup"><span data-stu-id="a698f-111">The order in which attributes are listed in the hierarchy is important.</span></span> <span data-ttu-id="a698f-112">例如，在时间层次结构中，年在层次结构列表中的位置应高于日。</span><span class="sxs-lookup"><span data-stu-id="a698f-112">For example, in a time hierarchy, years should appear higher in the hierarchy list than days.</span></span>  
  
4.  <span data-ttu-id="a698f-113">（可选）将用户定义层次结构中的级别拖至正确的位置，以便对这些级别进行重新排列。</span><span class="sxs-lookup"><span data-stu-id="a698f-113">Optionally, rearrange the levels in the user-defined hierarchy by dragging them to the correct positions.</span></span>  
  
5.  <span data-ttu-id="a698f-114">（可选）修改用户定义层次结构或其级别的属性。</span><span class="sxs-lookup"><span data-stu-id="a698f-114">Optionally, modify properties of the user-defined hierarchy or its levels.</span></span>  
  
     <span data-ttu-id="a698f-115">例如，您可能想为用户定义的层次结构指定名称，重命名它的一个或多个级别，以及为“全部”级别定义自定义名称。</span><span class="sxs-lookup"><span data-stu-id="a698f-115">For example, you might want to specify a name for the user-defined hierarchy, rename one or more of its levels, and define a custom name for the All level.</span></span> <span data-ttu-id="a698f-116">有关详细信息，请参阅[用户层次结构属性](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)和[级别属性 &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a698f-116">For more information, see [User Hierarchy Properties](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md), and [Level Properties &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a698f-117">默认情况下，用户定义的层次结构仅仅是用户用于深化信息的路径。</span><span class="sxs-lookup"><span data-stu-id="a698f-117">By default, a user-defined hierarchy is just a path that enables users to drill down for information.</span></span> <span data-ttu-id="a698f-118">但是，如果级别之间存在关系，则可以通过配置级别间的属性关系来提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="a698f-118">However, if relationships exist between levels, you can increase query performance by configuring attribute relationships between levels.</span></span> <span data-ttu-id="a698f-119">有关详细信息，请参阅 [属性关系](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) 和 [定义属性关系](attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="a698f-119">For more information, see [Attribute Relationships](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) and [Define Attribute Relationships](attribute-relationships-define.md).</span></span>  
  
### <a name="to-remove-a-user-defined-hierarchy-from-a-dimension"></a><span data-ttu-id="a698f-120">从维度中删除用户定义层次结构</span><span class="sxs-lookup"><span data-stu-id="a698f-120">To remove a user-defined hierarchy from a dimension</span></span>  
  
-   <span data-ttu-id="a698f-121">在“维度结构”\*\*\*\* 选项卡上的“层次结构”\*\*\*\* 窗格中，单击要删除的用户定义的层次结构。</span><span class="sxs-lookup"><span data-stu-id="a698f-121">On the **Dimension Structure** tab, click the user-defined hierarchy that you want to remove in the **Hierarchies** pane.</span></span> <span data-ttu-id="a698f-122">在工具栏上，单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="a698f-122">On the toolbar, click **Delete**.</span></span>  
  
     - <span data-ttu-id="a698f-123">或 -</span><span class="sxs-lookup"><span data-stu-id="a698f-123">or -</span></span>  
  
-   <span data-ttu-id="a698f-124">在“层次结构”\*\*\*\* 窗格中右键单击要删除的用户定义的层次结构，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a698f-124">Right-click the user-defined hierarchy that you want to remove in the **Hierarchies** pane and then click **Delete**.</span></span>  
  
     - <span data-ttu-id="a698f-125">或 -</span><span class="sxs-lookup"><span data-stu-id="a698f-125">or -</span></span>  
  
-   <span data-ttu-id="a698f-126">将该用户定义的层次结构拖出设计图面。</span><span class="sxs-lookup"><span data-stu-id="a698f-126">Drag the user-defined hierarchy off of the design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a698f-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a698f-127">See Also</span></span>  
 <span data-ttu-id="a698f-128">[用户层次结构](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="a698f-128">[User Hierarchies](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md) </span></span>  
 [<span data-ttu-id="a698f-129">创建用户定义层次结构</span><span class="sxs-lookup"><span data-stu-id="a698f-129">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
  
  
