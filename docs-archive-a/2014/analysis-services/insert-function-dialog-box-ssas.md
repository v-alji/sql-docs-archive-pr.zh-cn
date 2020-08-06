---
title: "\"插入函数\" 对话框 (SSAS) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.BIDTOOLSET.INSERTFUNCTIONDB.F1
ms.assetid: c4b36d8f-2328-45f7-8bd4-cc0111571e25
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0d92dd34e671dc026215d79e7eaed88bebfac15f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587099"
---
# <a name="insert-function-dialog-box-ssas"></a><span data-ttu-id="abbdd-102">“插入函数”对话框 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="abbdd-102">Insert Function Dialog Box (SSAS)</span></span>
  <span data-ttu-id="abbdd-103">**“插入函数”** 对话框可用于从生成公式时可使用的函数列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="abbdd-103">The **Insert Function** dialog box enables you to choose from a list of functions that can be used when building formulas.</span></span> <span data-ttu-id="abbdd-104">若要从模型设计器访问该对话框，请在各表之上的公式栏中，单击函数 (**fx**) 按钮。</span><span class="sxs-lookup"><span data-stu-id="abbdd-104">To access this dialog box from the model designer, in the formula bar above each table, click the function (**fx**) button.</span></span> <span data-ttu-id="abbdd-105">有关如何选择要在公式中使用的函数的详细信息，请参阅“DAX 简介和生成公式”。</span><span class="sxs-lookup"><span data-stu-id="abbdd-105">For more information about choosing functions to use in formulas, see DAX Introduction and Build a Formula.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="abbdd-106">项</span><span class="sxs-lookup"><span data-stu-id="abbdd-106">Item</span></span>|<span data-ttu-id="abbdd-107">说明</span><span class="sxs-lookup"><span data-stu-id="abbdd-107">Description</span></span>|  
|<span data-ttu-id="abbdd-108">**选择类别**</span><span class="sxs-lookup"><span data-stu-id="abbdd-108">**Select a category**</span></span>|<span data-ttu-id="abbdd-109">如果您大致确定所需函数的类型，则从列表中选择一个类别；或者选择 **“全部”** 以便查看函数的字母顺序列表。</span><span class="sxs-lookup"><span data-stu-id="abbdd-109">If you have a general idea which kind of function you need, choose a category from the list; or select **All** to view an alphabetical list of functions.</span></span>|  
|<span data-ttu-id="abbdd-110">**选择函数**</span><span class="sxs-lookup"><span data-stu-id="abbdd-110">**Select a function**</span></span>|<span data-ttu-id="abbdd-111">显示所选类别中函数的列表。</span><span class="sxs-lookup"><span data-stu-id="abbdd-111">Displays a list of the functions in the selected category.</span></span>|  
|<span data-ttu-id="abbdd-112">**说明**</span><span class="sxs-lookup"><span data-stu-id="abbdd-112">**Description**</span></span>|<span data-ttu-id="abbdd-113">显示函数功能的说明以及任何必需或可选参数，例如列名和表达式。</span><span class="sxs-lookup"><span data-stu-id="abbdd-113">Displays a description of what the function does, together with any required or optional arguments, such as column names and expressions.</span></span>|  
  
## <a name="function-categories"></a><span data-ttu-id="abbdd-114">函数类别</span><span class="sxs-lookup"><span data-stu-id="abbdd-114">Function Categories</span></span>  
 <span data-ttu-id="abbdd-115">数据分析表达式 (DAX) 在“插入函数”\*\*\*\* 对话框中提供以下类型的函数类别：</span><span class="sxs-lookup"><span data-stu-id="abbdd-115">Data Analysis Expressions (DAX) provides the following types of function categories in the **Insert Functions** dialog box.</span></span>  
  
 <span data-ttu-id="abbdd-116">全部</span><span class="sxs-lookup"><span data-stu-id="abbdd-116">All</span></span>  
  
 <span data-ttu-id="abbdd-117">日期和时间</span><span class="sxs-lookup"><span data-stu-id="abbdd-117">Date & Time</span></span>  
  
 <span data-ttu-id="abbdd-118">筛选器</span><span class="sxs-lookup"><span data-stu-id="abbdd-118">Filter</span></span>  
  
 <span data-ttu-id="abbdd-119">逻辑</span><span class="sxs-lookup"><span data-stu-id="abbdd-119">Logical</span></span>  
  
 <span data-ttu-id="abbdd-120">数学和三角函数</span><span class="sxs-lookup"><span data-stu-id="abbdd-120">Math & Trig</span></span>  
  
 <span data-ttu-id="abbdd-121">统计</span><span class="sxs-lookup"><span data-stu-id="abbdd-121">Statistical</span></span>  
  
 <span data-ttu-id="abbdd-122">文本</span><span class="sxs-lookup"><span data-stu-id="abbdd-122">Text</span></span>  
  
## <a name="measures-and-formulas"></a><span data-ttu-id="abbdd-123">度量值和公式</span><span class="sxs-lookup"><span data-stu-id="abbdd-123">Measures and Formulas</span></span>  
 <span data-ttu-id="abbdd-124">**“插入函数”** 对话框仅在您生成公式时可用。</span><span class="sxs-lookup"><span data-stu-id="abbdd-124">The **Insert Function** dialog box is available only when you are building a formula.</span></span> <span data-ttu-id="abbdd-125">您可以在计算列或者数据透视表或数据透视图中创建计算。</span><span class="sxs-lookup"><span data-stu-id="abbdd-125">You can create calculations either in a calculated column, or in a PivotTable or PivotChart.</span></span> <span data-ttu-id="abbdd-126">您生成的明确用于数据透视表中的公式也称作“度量值” \*\*。</span><span class="sxs-lookup"><span data-stu-id="abbdd-126">Formulas that you build expressly for use in a PivotTable are also called *measures*.</span></span> <span data-ttu-id="abbdd-127">有关详细信息，请参阅[创建计算列（SSAS 表格）](tabular-models/ssas-calculated-columns-create-a-calculated-column.md)和[创建和管理度量值（SSAS 表格）](tabular-models/measures-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="abbdd-127">For more information, see [Create a Calculated Column &#40;SSAS Tabular&#41;](tabular-models/ssas-calculated-columns-create-a-calculated-column.md) and [Create and Manage Measures &#40;SSAS Tabular&#41;](tabular-models/measures-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abbdd-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abbdd-128">See Also</span></span>  
 [<span data-ttu-id="abbdd-129">计算（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="abbdd-129">Calculations &#40;SSAS Tabular&#41;</span></span>](tabular-models/calculations-ssas-tabular.md)  
  
  
