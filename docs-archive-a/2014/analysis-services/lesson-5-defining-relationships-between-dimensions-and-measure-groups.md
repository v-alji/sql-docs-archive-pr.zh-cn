---
title: 第5课：定义维度和度量值组之间的关系 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 31aeb271-47a1-433b-a8a5-120bcb4584d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6dbdf20e64e3cd8adc751b69122a380d7b3b3648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580986"
---
# <a name="lesson-5-defining-relationships-between-dimensions-and-measure-groups"></a><span data-ttu-id="89164-102">第 5 课：定义维度和度量值组之间的关系</span><span class="sxs-lookup"><span data-stu-id="89164-102">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>
  <span data-ttu-id="89164-103">在本教程前面的课程中，您已了解到可以将添加到多维数据集中的数据库维度作为一个或多个多维数据集维度的基础。</span><span class="sxs-lookup"><span data-stu-id="89164-103">In the previous lessons in this tutorial, you learned that database dimensions added to a cube can be used as the basis for one or more cube dimensions.</span></span> <span data-ttu-id="89164-104">在本课中，您将了解如何定义多维数据集维度和度量值组之间的各种关系类型，以及如何指定这些关系的属性。</span><span class="sxs-lookup"><span data-stu-id="89164-104">In this lesson, you learn to define different types of relationships between cube dimensions and measure groups, and to specify the properties of these relationships.</span></span>  
  
 <span data-ttu-id="89164-105">有关详细信息，请参阅 [维度关系](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="89164-105">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="89164-106">本教程的所有课程中的已完成项目均可以从网上获得。</span><span class="sxs-lookup"><span data-stu-id="89164-106">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="89164-107">您可以通过将前一课程的已完成项目作为起始点，跳转到后面的任何课程。</span><span class="sxs-lookup"><span data-stu-id="89164-107">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="89164-108">[单击此处](https://go.microsoft.com/fwlink/?LinkID=221866) 可以下载本教程随附的示例项目。</span><span class="sxs-lookup"><span data-stu-id="89164-108">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="89164-109">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="89164-109">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="89164-110">定义引用关系</span><span class="sxs-lookup"><span data-stu-id="89164-110">Defining a Referenced Relationship</span></span>](lesson-5-1-defining-a-referenced-relationship.md)  
 <span data-ttu-id="89164-111">在此任务中，您将了解如何通过通过主键-外键关系直接链接的维度，将维度间接链接到事实数据表。</span><span class="sxs-lookup"><span data-stu-id="89164-111">In this task, you learn to link a dimension to a fact table indirectly through a dimension that is linked directly through a primary key-foreign key relationship.</span></span>  
  
 [<span data-ttu-id="89164-112">定义事实关系</span><span class="sxs-lookup"><span data-stu-id="89164-112">Defining a Fact Relationship</span></span>](lesson-5-2-defining-a-fact-relationship.md)  
 <span data-ttu-id="89164-113">在本任务中，您将了解如何基于事实数据表中的数据定义维度，以及如何将维度关系定义为事实关系。</span><span class="sxs-lookup"><span data-stu-id="89164-113">In this task, you learn to define a dimension based on data in the fact table, and to define the dimension relationship as a fact relationship.</span></span>  
  
 [<span data-ttu-id="89164-114">定义多对多关系</span><span class="sxs-lookup"><span data-stu-id="89164-114">Defining a Many-to-Many Relationship</span></span>](lesson-5-3-defining-a-many-to-many-relationship.md)  
 <span data-ttu-id="89164-115">在本任务中，您将了解如何通过维度表和事实数据表之间多对多关系的定义将事实与多个维度成员进行关联。</span><span class="sxs-lookup"><span data-stu-id="89164-115">In this task, you learn to relate a fact to multiple dimension members through the definition of a many-to-many relationship between dimension tables and fact tables.</span></span>  
  
 [<span data-ttu-id="89164-116">定义度量值组中的维度粒度</span><span class="sxs-lookup"><span data-stu-id="89164-116">Defining Dimension Granularity within a Measure Group</span></span>](lesson-5-4-defining-dimension-granularity-within-a-measure-group.md)  
 <span data-ttu-id="89164-117">在本任务中，您将了解如何修改特定度量值组的维度粒度。</span><span class="sxs-lookup"><span data-stu-id="89164-117">In this task, you learn to modify the granularity of a dimension for a specific measure group.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="89164-118">下一课</span><span class="sxs-lookup"><span data-stu-id="89164-118">Next Lesson</span></span>  
 [<span data-ttu-id="89164-119">第 6 课：定义计算</span><span class="sxs-lookup"><span data-stu-id="89164-119">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)  
  
## <a name="see-also"></a><span data-ttu-id="89164-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="89164-120">See Also</span></span>  
 <span data-ttu-id="89164-121">[Analysis Services 教程方案](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="89164-121">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="89164-122">[&#40;艾德作品的多维建模教程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="89164-122">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="89164-123">维度关系</span><span class="sxs-lookup"><span data-stu-id="89164-123">Dimension Relationships</span></span>](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
