---
title: " (SSAS 表格) 创建和管理度量值 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: edc1a4b2-96d3-4f34-bb70-6cacec79e819
author: minewiskan
ms.author: owend
ms.openlocfilehash: da507bf48b285a1414ffb85ba79da50508a2ae2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580403"
---
# <a name="create-and-manage-measures-ssas-tabular"></a><span data-ttu-id="ba81d-102">创建和管理度量值（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="ba81d-102">Create and Manage Measures (SSAS Tabular)</span></span>
  <span data-ttu-id="ba81d-103">度量值是为用于报表或 Excel 数据透视表（或数据透视图）而创建的公式。</span><span class="sxs-lookup"><span data-stu-id="ba81d-103">A measure is a formula that is created for use in a report or Excel PivotTable (or PivotChart).</span></span> <span data-ttu-id="ba81d-104">度量值可以基于标准聚合函数，如 COUNT 或 SUM；或者，您可以通过使用 DAX 定义自己的公式。</span><span class="sxs-lookup"><span data-stu-id="ba81d-104">Measures can be based on standard aggregation functions, such as COUNT or SUM, or you can define your own formula by using DAX.</span></span> <span data-ttu-id="ba81d-105">本主题中的任务说明如何使用表的度量值网格创建和管理度量值。</span><span class="sxs-lookup"><span data-stu-id="ba81d-105">The tasks in this topic describe how to create and manage measures by using a table's measure grid.</span></span>  
  
 <span data-ttu-id="ba81d-106">本主题包括以下任务：</span><span class="sxs-lookup"><span data-stu-id="ba81d-106">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="ba81d-107">使用标准聚合公式创建度量值</span><span class="sxs-lookup"><span data-stu-id="ba81d-107">To create a measure using a standard aggregation formula</span></span>](#bkmk_create_stand)  
  
-   [<span data-ttu-id="ba81d-108">使用自定义公式创建度量值</span><span class="sxs-lookup"><span data-stu-id="ba81d-108">To create a measure using a custom formula</span></span>](#bkmk_create_custom)  
  
-   [<span data-ttu-id="ba81d-109">编辑度量值属性</span><span class="sxs-lookup"><span data-stu-id="ba81d-109">To edit measure properties</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="ba81d-110">重命名度量值</span><span class="sxs-lookup"><span data-stu-id="ba81d-110">To rename a measure</span></span>](#bkmk_rename)  
  
-   [<span data-ttu-id="ba81d-111">删除度量值</span><span class="sxs-lookup"><span data-stu-id="ba81d-111">To delete a measure</span></span>](#bkmk_delete)  
  
## <a name="tasks"></a><span data-ttu-id="ba81d-112">任务</span><span class="sxs-lookup"><span data-stu-id="ba81d-112">Tasks</span></span>  
 <span data-ttu-id="ba81d-113">若要创建和管理度量值，您将使用表的度量值网格。</span><span class="sxs-lookup"><span data-stu-id="ba81d-113">To create and manage measures, you will use a table's measure grid.</span></span> <span data-ttu-id="ba81d-114">您只能在模型设计器的“数据视图”中查看表的度量值网格。</span><span class="sxs-lookup"><span data-stu-id="ba81d-114">You can view the measure grid for a table in the model designer in Data View only.</span></span> <span data-ttu-id="ba81d-115">您不能在处于关系图视图中时创建度量值或查看度量值网格；不过，您可以在关系图视图中查看现有的度量值。</span><span class="sxs-lookup"><span data-stu-id="ba81d-115">You cannot create measures or view the measure grid when in Diagram View; however, you can view existing measures in Diagram View.</span></span> <span data-ttu-id="ba81d-116">要为表显示度量值网格，请单击 **“表”** 菜单，然后单击 **“显示度量值网格”**。</span><span class="sxs-lookup"><span data-stu-id="ba81d-116">To show the measure grid for a table, click the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
###  <a name="to-create-a-measure-using-a-standard-aggregation-formula"></a><a name="bkmk_create_stand"></a><span data-ttu-id="ba81d-117">使用标准聚合公式创建度量值</span><span class="sxs-lookup"><span data-stu-id="ba81d-117">To create a measure using a standard aggregation formula</span></span>  
  
-   <span data-ttu-id="ba81d-118">单击要为其创建度量值的列，然后单击 **“列”** 菜单，指向 **“自动求和”**，再单击某一聚合类型。</span><span class="sxs-lookup"><span data-stu-id="ba81d-118">Click on the column for which you want to create the measure, then click the **Column** menu, then point to **AutoSum**, and then click an aggregation type.</span></span>  
  
     <span data-ttu-id="ba81d-119">度量值将用默认名称自动创建，后随列正下方的度量值网格中的第一个单元中的公式。</span><span class="sxs-lookup"><span data-stu-id="ba81d-119">The measure will be created automatically with a default name, followed by the formula in the first cell in the measure grid directly beneath the column.</span></span>  
  
###  <a name="to-create-a-measure-using-a-custom-formula"></a><a name="bkmk_create_custom"></a><span data-ttu-id="ba81d-120">使用自定义公式创建度量值</span><span class="sxs-lookup"><span data-stu-id="ba81d-120">To create a measure using a custom formula</span></span>  
  
-   <span data-ttu-id="ba81d-121">在度量值网格中，在要为其创建度量值的列的下方，单击某一单元，然后在公式栏中键入名称，后面依次跟一个冒号 (:)、一个等号 (=) 和公式。</span><span class="sxs-lookup"><span data-stu-id="ba81d-121">In the measure grid, beneath the column for which you want to create the measure, click a cell, then in the formula bar, type a name, followed by a colon (:), followed by an equals sign (=), followed by the formula.</span></span> <span data-ttu-id="ba81d-122">按 Enter 以接受该公式。</span><span class="sxs-lookup"><span data-stu-id="ba81d-122">Press ENTER to accept the formula.</span></span>  
  
###  <a name="to-edit-measure-properties"></a><a name="bkmk_edit"></a><span data-ttu-id="ba81d-123">编辑度量值属性</span><span class="sxs-lookup"><span data-stu-id="ba81d-123">To edit measure properties</span></span>  
  
-   <span data-ttu-id="ba81d-124">在度量值网格中，单击某一度量值，然后在 **“属性”** 窗口中，键入或选择不同的属性值。</span><span class="sxs-lookup"><span data-stu-id="ba81d-124">In the measure grid, click a measure, and then In the **Properties** window, type or select a different property value.</span></span>  
  
###  <a name="to-rename-a-measure"></a><a name="bkmk_rename"></a><span data-ttu-id="ba81d-125">重命名度量值</span><span class="sxs-lookup"><span data-stu-id="ba81d-125">To rename a measure</span></span>  
  
-   <span data-ttu-id="ba81d-126">在度量值网格中，单击某一度量值，然后在 **“属性”** 窗口的 **“度量值名称”** 中，键入新名称，再单击 ENTER。</span><span class="sxs-lookup"><span data-stu-id="ba81d-126">In the measure grid, click on a measure, and then In the **Properties** window, in **Measure Name**, type a new name, and then click ENTER.</span></span>  
  
     <span data-ttu-id="ba81d-127">您也可以在编辑栏中重命名度量值。</span><span class="sxs-lookup"><span data-stu-id="ba81d-127">You can also rename a measure in the formula bar.</span></span> <span data-ttu-id="ba81d-128">度量值名称将位于公式前并且后随一个冒号。</span><span class="sxs-lookup"><span data-stu-id="ba81d-128">The measure name precedes the formula, followed by a colon.</span></span>  
  
###  <a name="to-delete-a-measure"></a><a name="bkmk_delete"></a><span data-ttu-id="ba81d-129">删除度量值</span><span class="sxs-lookup"><span data-stu-id="ba81d-129">To delete a measure</span></span>  
  
-   <span data-ttu-id="ba81d-130">在度量值网格中，右键单击某一度量值，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba81d-130">In the measure grid, right-click a measure, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba81d-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba81d-131">See Also</span></span>  
 <span data-ttu-id="ba81d-132">[&#40;SSAS 表格&#41;度量值](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="ba81d-132">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 <span data-ttu-id="ba81d-133">[&#40;SSAS 表格&#41;的 Kpi](kpis-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="ba81d-133">[KPIs &#40;SSAS Tabular&#41;](kpis-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="ba81d-134">计算列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="ba81d-134">Calculated Columns &#40;SSAS Tabular&#41;</span></span>](ssas-calculated-columns.md)  
  
  
