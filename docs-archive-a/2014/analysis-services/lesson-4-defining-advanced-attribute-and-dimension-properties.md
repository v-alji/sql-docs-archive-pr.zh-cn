---
title: 第4课：定义高级属性和维度属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e86b9be-e47d-4bb4-87eb-136ff3a61aef
author: minewiskan
ms.author: owend
ms.openlocfilehash: deb2d9c40ad5024f6cc4ba6e9148df41a168c6e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690851"
---
# <a name="lesson-4-defining-advanced-attribute-and-dimension-properties"></a><span data-ttu-id="cc33b-102">第 4 课：定义高级属性和维度属性</span><span class="sxs-lookup"><span data-stu-id="cc33b-102">Lesson 4: Defining Advanced Attribute and Dimension Properties</span></span>
  <span data-ttu-id="cc33b-103">在本课中，将了解如何使用特性、特性层次结构和维度属性的某些高级属性。</span><span class="sxs-lookup"><span data-stu-id="cc33b-103">In this lesson, you will learn how to use some of the advanced properties of attributes, attribute hierarchies, and dimension properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc33b-104">本课基于在本教程前面三课中完成的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目的增强版本。</span><span class="sxs-lookup"><span data-stu-id="cc33b-104">This lesson is based on an enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons of this tutorial.</span></span> <span data-ttu-id="cc33b-105">本课的第一个任务是描述在哪里找到适用于该课程的示例项目，以及该项目与前面三课中所创建的项目之间的差异。</span><span class="sxs-lookup"><span data-stu-id="cc33b-105">The first task in this lesson describes where to locate the appropriate sample project to use for the lesson, and the difference between this project and the project that you created in the first three lessons.</span></span>  
  
 <span data-ttu-id="cc33b-106">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="cc33b-106">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="cc33b-107">使用 Analysis Services Tutorial 项目的修改版本</span><span class="sxs-lookup"><span data-stu-id="cc33b-107">Using a Modified Version of the Analysis Services Tutorial Project</span></span>](lesson-4-1-using-a-modified-version-of-the-analysis-services-tutorial-project.md)  
 <span data-ttu-id="cc33b-108">在该任务中，您将打开、检查和部署 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程项目的修改版本，该项目包含多个度量值组和其他维度。</span><span class="sxs-lookup"><span data-stu-id="cc33b-108">In this task, you open, review, and deploy a modified version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, which has multiple measure groups and additional dimensions.</span></span>  
  
 [<span data-ttu-id="cc33b-109">定义父子层次结构中的父特性属性</span><span class="sxs-lookup"><span data-stu-id="cc33b-109">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>](lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md)  
 <span data-ttu-id="cc33b-110">在该任务中，将定义父子维度的级别名称，并指定是否显示与父成员有关的数据。</span><span class="sxs-lookup"><span data-stu-id="cc33b-110">In this task, you define level names in a parent-child dimension and specify whether data related to parent members is displayed.</span></span> <span data-ttu-id="cc33b-111">有关详细信息，请参阅父子[层次结构](multidimensional-models/parent-child-dimension.md)和父子层次[结构中的属性](multidimensional-models/parent-child-dimension-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="cc33b-111">For more information, see [Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md) and [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md).</span></span>  
  
 [<span data-ttu-id="cc33b-112">自动将属性成员分组</span><span class="sxs-lookup"><span data-stu-id="cc33b-112">Automatically Grouping Attribute Members</span></span>](lesson-4-3-automatically-grouping-attribute-members.md)  
 <span data-ttu-id="cc33b-113">在该任务中，将基于成员在属性层次结构中的分布自动创建属性成员的分组。</span><span class="sxs-lookup"><span data-stu-id="cc33b-113">In this task, you automatically create groupings of attribute members based on the distribution of the members within the attribute hierarchy.</span></span> <span data-ttu-id="cc33b-114">有关详细信息，请参阅[对属性成员分组（离散化）](multidimensional-models/attribute-properties-group-attribute-members.md)。</span><span class="sxs-lookup"><span data-stu-id="cc33b-114">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md).</span></span>  
  
 [<span data-ttu-id="cc33b-115">隐藏和禁用属性层次结构</span><span class="sxs-lookup"><span data-stu-id="cc33b-115">Hiding and Disabling Attribute Hierarchies</span></span>](lesson-4-4-hiding-and-disabling-attribute-hierarchies.md)  
 <span data-ttu-id="cc33b-116">在该任务中，将了解如何以及何时禁用或隐藏属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="cc33b-116">In this task, you learn how and when to disable or hide attribute hierarchies.</span></span>  
  
 [<span data-ttu-id="cc33b-117">根据辅助属性对属性成员进行排序</span><span class="sxs-lookup"><span data-stu-id="cc33b-117">Sorting Attribute Members Based on a Secondary Attribute</span></span>](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)  
 <span data-ttu-id="cc33b-118">在该任务中，将了解如何基于辅助属性对维度成员排序，以获得所需的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="cc33b-118">In this task, you learn how to sort dimension members based on a secondary attribute, to achieve the sort order that you want.</span></span>  
  
 [<span data-ttu-id="cc33b-119">指定用户定义层次结构中属性之间的属性关系</span><span class="sxs-lookup"><span data-stu-id="cc33b-119">Specifying Attribute Relationships Between Attributes in a User-Defined Hierarchy</span></span>](4-6-specifying-attribute-relationships-in-user-defined-hierarchy.md)  
 <span data-ttu-id="cc33b-120">在该任务中，将了解如何定义属性的成员属性和指定它们之间的聚合关系。</span><span class="sxs-lookup"><span data-stu-id="cc33b-120">In this task, you learn how to define member properties for attributes and to specify aggregation relationships between them.</span></span> <span data-ttu-id="cc33b-121">有关详细信息，请参阅 [定义属性关系](multidimensional-models/attribute-relationships-define.md) 和 [用户层次结构属性](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="cc33b-121">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [User Hierarchy Properties](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md).</span></span>  
  
 [<span data-ttu-id="cc33b-122">定义未知成员和 Null 处理属性</span><span class="sxs-lookup"><span data-stu-id="cc33b-122">Defining the Unknown Member and Null Processing Properties</span></span>](lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
 <span data-ttu-id="cc33b-123">在此任务中，将配置 UnknownMember 和 UnknownMemberName 属性，以处理由 null 维度成员所导致的错误情况。</span><span class="sxs-lookup"><span data-stu-id="cc33b-123">In this task, you configure the UnknownMember and UnknownMemberName properties to handle error conditions caused by null dimension members.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="cc33b-124">下一课</span><span class="sxs-lookup"><span data-stu-id="cc33b-124">Next Lesson</span></span>  
 [<span data-ttu-id="cc33b-125">第 5 课：定义维度和度量值组之间的关系</span><span class="sxs-lookup"><span data-stu-id="cc33b-125">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)  
  
## <a name="see-also"></a><span data-ttu-id="cc33b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc33b-126">See Also</span></span>  
 <span data-ttu-id="cc33b-127">[Analysis Services 教程方案](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="cc33b-127">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="cc33b-128">[&#40;艾德作品的多维建模教程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="cc33b-128">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="cc33b-129">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="cc33b-129">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
