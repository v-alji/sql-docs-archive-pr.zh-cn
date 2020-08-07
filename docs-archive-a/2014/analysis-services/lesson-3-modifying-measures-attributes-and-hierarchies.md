---
title: 第3课：修改度量值、属性和层次结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 17d243cb-9bfb-43d7-8e6f-4d601fd62150
author: minewiskan
ms.author: owend
ms.openlocfilehash: c410136540a0ba85d50fbabc8b2d3c52be1823f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588126"
---
# <a name="lesson-3-modifying-measures-attributes-and-hierarchies"></a><span data-ttu-id="2c354-102">第 3 课：修改度量值、属性和层次结构</span><span class="sxs-lookup"><span data-stu-id="2c354-102">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>
  <span data-ttu-id="2c354-103">在定义初始多维数据集后，即可开始提高多维数据集的有用性和友好性。</span><span class="sxs-lookup"><span data-stu-id="2c354-103">After defining your initial cube, you are ready to improve the usefulness and friendliness of the cube.</span></span> <span data-ttu-id="2c354-104">您可以通过添加在不同级别支持导航和聚合的层次结构、通过将格式应用于特定的度量值以及通过定义计算和关系，实现上述目的。</span><span class="sxs-lookup"><span data-stu-id="2c354-104">You can do this by adding hierarchies that support navigation and aggregation at various levels, by applying formats to specific measure, and by defining calculations and relationships.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c354-105">本教程的所有课程中的已完成项目均可以从网上获得。</span><span class="sxs-lookup"><span data-stu-id="2c354-105">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="2c354-106">您可以通过将前一课程的已完成项目作为起始点，跳转到后面的任何课程。</span><span class="sxs-lookup"><span data-stu-id="2c354-106">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="2c354-107">[单击此处](https://go.microsoft.com/fwlink/?LinkID=221866) 可以下载本教程随附的示例项目。</span><span class="sxs-lookup"><span data-stu-id="2c354-107">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="2c354-108">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="2c354-108">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="2c354-109">修改度量值</span><span class="sxs-lookup"><span data-stu-id="2c354-109">Modifying Measures</span></span>](lesson-3-1-modifying-measures.md)  
 <span data-ttu-id="2c354-110">在此任务中，您将为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集中的货币和百分比度量值指定格式设置属性。</span><span class="sxs-lookup"><span data-stu-id="2c354-110">In this task, you specify formatting properties for the currency and percentage measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
 [<span data-ttu-id="2c354-111">修改“客户”维度</span><span class="sxs-lookup"><span data-stu-id="2c354-111">Modifying the Customer Dimension</span></span>](lesson-3-2-modifying-the-customer-dimension.md)  
 <span data-ttu-id="2c354-112">在该任务中，将定义用户层次结构，创建命名计算，修改属性以使用命名计算并将属性和用户层次结构分组到显示文件夹中。</span><span class="sxs-lookup"><span data-stu-id="2c354-112">In this task, you define a user hierarchy, create named calculations, modify attributes to use named calculations, and group attributes and user hierarchies into display folders.</span></span>  
  
 [<span data-ttu-id="2c354-113">修改“产品”维度</span><span class="sxs-lookup"><span data-stu-id="2c354-113">Modifying the Product Dimension</span></span>](lesson-3-3-modifying-the-product-dimension.md)  
 <span data-ttu-id="2c354-114">在该任务中，将定义用户层次结构，创建命名计算、定义所有“全部”级别成员名称并定义显示文件夹。</span><span class="sxs-lookup"><span data-stu-id="2c354-114">In this task, you define a user hierarchy, create named calculations, define the All member name, and define display folders.</span></span>  
  
 [<span data-ttu-id="2c354-115">修改“日期”维度</span><span class="sxs-lookup"><span data-stu-id="2c354-115">Modifying the Date Dimension</span></span>](lesson-3-4-modifying-the-date-dimension.md)  
 <span data-ttu-id="2c354-116">在该任务中，将定义用户层次结构，修改属性成员名称并使用组合键指定唯一的属性成员。</span><span class="sxs-lookup"><span data-stu-id="2c354-116">In this task, you define a user hierarchy, modify attribute member names, and use composite keys to specify unique attribute members.</span></span>  
  
 [<span data-ttu-id="2c354-117">浏览已部署的多维数据集</span><span class="sxs-lookup"><span data-stu-id="2c354-117">Browsing the Deployed Cube</span></span>](lesson-3-5-browsing-the-deployed-cube.md)  
 <span data-ttu-id="2c354-118">在此任务中，将使用多维数据集设计器中的浏览器浏览多维数据集数据。</span><span class="sxs-lookup"><span data-stu-id="2c354-118">In this task, you browse cube data by using the browser in Cube Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c354-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c354-119">See Also</span></span>  
 <span data-ttu-id="2c354-120">[Analysis Services 教程方案](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2c354-120">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 [<span data-ttu-id="2c354-121">多维建模（Adventure Works 教程）</span><span class="sxs-lookup"><span data-stu-id="2c354-121">Multidimensional Modeling &#40;Adventure Works Tutorial&#41;</span></span>](multidimensional-modeling-adventure-works-tutorial.md)  
  
  
