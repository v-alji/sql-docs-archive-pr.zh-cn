---
title: 第9课：创建透视 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 417b6a4d3b16857f48bcc2f39dc8ec4c010a2b10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692615"
---
# <a name="lesson-9-create-perspectives"></a><span data-ttu-id="d1c1a-102">第 9 课：创建透视</span><span class="sxs-lookup"><span data-stu-id="d1c1a-102">Lesson 9: Create Perspectives</span></span>
  <span data-ttu-id="d1c1a-103">在本课程中，您将创建 Internet Sales 透视。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-103">In this lesson, you will create an Internet Sales perspective.</span></span> <span data-ttu-id="d1c1a-104">透视定义模型的可查看子集，它提供集中的特定于业务的或特定于应用程序的视点。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-104">A perspective defines a viewable subset of a model that provides focused, business-specific, or application-specific viewpoints.</span></span> <span data-ttu-id="d1c1a-105">当用户使用透视连接到模型时，将只能看到与该透视中定义的字段相同的那些模型对象（表、列、度量值、层次结构和 KPI）。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-105">When a user connects to a model using a perspective, they see only those model objects (tables, columns, measures, hierarchies, and KPIs) as fields defined in that perspective.</span></span>  
  
 <span data-ttu-id="d1c1a-106">本课中创建的 Internet Sales 透视将排除 Customer 表对象。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-106">The Internet Sales perspective you create in this lesson will exclude the Customer table object.</span></span> <span data-ttu-id="d1c1a-107">当您创建排除视图中某些对象的透视时，这些对象仍然存在于模型中；但是，它们在报表客户端字段列表中不可见。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-107">When you create a perspective that excludes certain objects from view, that object still exists in the model; however, it is not visible in a reporting client field list.</span></span> <span data-ttu-id="d1c1a-108">无论计算列和度量值是否包含在透视中，都仍可以通过排除的对象数据进行计算。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-108">Calculated columns and measures either included in a perspective or not can still calculate from object data that is excluded.</span></span>  
  
 <span data-ttu-id="d1c1a-109">本课程的目的是介绍如何创建透视以及如何逐步熟悉表格模型创作工具。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-109">The purpose of this lesson is to describe how to create perspectives and become familiar with the tabular model authoring tools.</span></span> <span data-ttu-id="d1c1a-110">如果您以后扩展此模型以包含其他表，则可以创建其他透视以定义不同的模型视点，例如 Inventory 和 Sales Force。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-110">If you later expand this model to include additional tables, you can create additional perspectives to define different viewpoints of the model, for example, Inventory and Sales Force.</span></span>  
  
 <span data-ttu-id="d1c1a-111">若要了解详细信息，请参阅[透视表（SSAS 表格）](tabular-models/perspectives-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-111">To learn more, see [Perspectives &#40;SSAS Tabular&#41;](tabular-models/perspectives-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="d1c1a-112">学完本课的估计时间： **5 分钟**</span><span class="sxs-lookup"><span data-stu-id="d1c1a-112">Estimated time to complete this lesson: **5 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d1c1a-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="d1c1a-113">Prerequisites</span></span>  
 <span data-ttu-id="d1c1a-114">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-114">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="d1c1a-115">在执行本课程中的任务之前，应该已完成上一课： [第 8 课：创建关键绩效指标](lesson-7-create-key-performance-indicators.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-115">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 8: Create Key Performance Indicators](lesson-7-create-key-performance-indicators.md).</span></span>  
  
## <a name="create-perspectives"></a><span data-ttu-id="d1c1a-116">创建透视</span><span class="sxs-lookup"><span data-stu-id="d1c1a-116">Create Perspectives</span></span>  
  
#### <a name="to-create-an-internet-sales-perspective"></a><span data-ttu-id="d1c1a-117">创建“Internet 销售”透视</span><span class="sxs-lookup"><span data-stu-id="d1c1a-117">To create an Internet Sales perspective</span></span>  
  
1.  <span data-ttu-id="d1c1a-118">在模型设计器中，单击 "**模型**" 菜单，然后单击 "**透视**"。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-118">In the model designer, click the **Model** menu, and then click **Perspectives**.</span></span>  
  
2.  <span data-ttu-id="d1c1a-119">在“透视”对话框中，单击“新建透视”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d1c1a-119">In the **Perspectives** dialog box, click **New Perspective**.</span></span>  
  
3.  <span data-ttu-id="d1c1a-120">若要重命名该透视，请双击 "**新建透视 1** " 列标题，然后键入 `Internet Sales` 。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-120">To rename the perspective, double-click the **New Perspective 1** column heading, and then type `Internet Sales`.</span></span>  
  
4.  <span data-ttu-id="d1c1a-121">在 "**字段**" 中，选择下表**Date**、 **Geography**、 **Product**、 **product Category**、 **product 子类别**和 `Internet Sales` 。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-121">In **Fields**, select the following tables **Date**, **Geography**, **Product**, **Product Category**, **Product Subcategory**, and `Internet Sales`.</span></span>  
  
     <span data-ttu-id="d1c1a-122">请注意，您从此透视中排除了 Customer 表及其所有列。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-122">Notice you excluded the Customer table and all of its columns from this perspective.</span></span> <span data-ttu-id="d1c1a-123">稍后，您将在第 12 课中使用“在 Excel 中分析”功能来测试此透视。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-123">Later, in Lesson 12, you will use the Analyze in Excel feature to test this perspective.</span></span> <span data-ttu-id="d1c1a-124">Excel 数据透视表字段列表将包含除 Customer 表之外的所有表。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-124">The Excel PivotTable Field List will include each table except the Customer table.</span></span>  
  
5.  <span data-ttu-id="d1c1a-125">验证所做的选择，确保未选中“Customer”\*\*\*\* 表，然后单击“确定”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d1c1a-125">Verify your selections, making sure the **Customer** table is not checked, and then click **OK**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d1c1a-126">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d1c1a-126">Next Steps</span></span>  
 <span data-ttu-id="d1c1a-127">若要继续学习本教程，请转到下一课： [第 10 课：创建层次结构](lesson-9-create-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c1a-127">To continue this tutorial, go to the next lesson: [Lesson 10: Create Hierarchies](lesson-9-create-hierarchies.md).</span></span>  
  
  
