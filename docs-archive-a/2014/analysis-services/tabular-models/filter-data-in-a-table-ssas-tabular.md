---
title: " (SSAS 表格) 筛选表中的数据 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.customfilterdb.f1
- sql12.asvs.bidtoolset.autofiltermenu.f1
- sql12.asvs.bidtoolset.notallitemsshowing.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f4003457df4068713e75e6bb5c0ab78c15ac03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687240"
---
# <a name="filter-data-in-a-table-ssas-tabular"></a><span data-ttu-id="ef54f-102">筛选表中的数据（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="ef54f-102">Filter Data in a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="ef54f-103">您可以在导入数据时应用筛选器，以便控制加载到表中的行。</span><span class="sxs-lookup"><span data-stu-id="ef54f-103">You can apply filters when you import data to control the rows that are loaded into a table.</span></span> <span data-ttu-id="ef54f-104">在导入数据后，不能删除单独的行。</span><span class="sxs-lookup"><span data-stu-id="ef54f-104">After you have imported the data, you cannot delete individual rows.</span></span> <span data-ttu-id="ef54f-105">不过，您可以应用自定义筛选器，以便控制显示行的方式。</span><span class="sxs-lookup"><span data-stu-id="ef54f-105">However, you can apply custom filters to control the way that rows are displayed.</span></span> <span data-ttu-id="ef54f-106">不符合筛选条件的行会被隐藏。</span><span class="sxs-lookup"><span data-stu-id="ef54f-106">Rows that do not meet the filtering criteria are hidden.</span></span> <span data-ttu-id="ef54f-107">您可以基于一列或多列进行筛选。</span><span class="sxs-lookup"><span data-stu-id="ef54f-107">You can filter by one or more columns.</span></span> <span data-ttu-id="ef54f-108">筛选器是累加式的，这意味着每个附加的筛选器都基于当前筛选器，从而进一步减少数据子集。</span><span class="sxs-lookup"><span data-stu-id="ef54f-108">Filters are additive, which means that each additional filter is based on the current filter and further reduces the subset of data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ef54f-109">筛选器预览窗口限制了显示的不同值的数量。</span><span class="sxs-lookup"><span data-stu-id="ef54f-109">The filter preview window limits the number of different values displayed.</span></span> <span data-ttu-id="ef54f-110">如果超出限制，则将显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="ef54f-110">If the limit is exceeded, a message is displayed.</span></span>  
  
### <a name="to-filter-data-based-on-column-values"></a><span data-ttu-id="ef54f-111">基于列值筛选数据</span><span class="sxs-lookup"><span data-stu-id="ef54f-111">To filter data based on column values</span></span>  
  
1.  <span data-ttu-id="ef54f-112">在模型设计器中，选择一个表，然后单击您要基于其进行筛选的列标题中的箭头。</span><span class="sxs-lookup"><span data-stu-id="ef54f-112">In the model designer, select a table, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="ef54f-113">在“自动筛选”菜单中，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="ef54f-113">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="ef54f-114">在列值的列表中，选择或清除作为筛选依据的一个或多个值，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="ef54f-114">In the list of column values, select or clear one or more values to filter by, and then click **OK**.</span></span>  
  
         <span data-ttu-id="ef54f-115">如果值的数目极多，则可能无法在列表中显示各个项。</span><span class="sxs-lookup"><span data-stu-id="ef54f-115">If the number of values is extremely large, individual items might not be shown in the list.</span></span> <span data-ttu-id="ef54f-116">此时您将看到消息“项过多，无法显示。”</span><span class="sxs-lookup"><span data-stu-id="ef54f-116">Instead, you will see the message, "Too many items to show."</span></span>  
  
    -   <span data-ttu-id="ef54f-117">单击 "**数字筛选器**" 或 "**文本筛选器**" (具体取决于) 的列类型，然后单击比较运算符命令 (如**Equals**) ，或者单击 "**自定义筛选器**"。</span><span class="sxs-lookup"><span data-stu-id="ef54f-117">Click **Number Filters** or **Text Filters** (depending on the type of column), and then clicke of the comparison operator commands (such as **Equals**), or click **Custom Filter**.</span></span> <span data-ttu-id="ef54f-118">在 **“自定义筛选器”** 对话框中，创建筛选器，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="ef54f-118">In the **Custom Filter** dialog box, create the filter, and then click **OK**.</span></span>  
  
### <a name="to-clear-a-filter-for-a-column"></a><span data-ttu-id="ef54f-119">清除列筛选器</span><span class="sxs-lookup"><span data-stu-id="ef54f-119">To clear a filter for a column</span></span>  
  
1.  <span data-ttu-id="ef54f-120">单击您要清除其筛选器的列的标题中的箭头。</span><span class="sxs-lookup"><span data-stu-id="ef54f-120">Click the arrow in the header of the column for which you want to clear a filter.</span></span>  
  
2.  <span data-ttu-id="ef54f-121">单击 "**清除筛选 \<Column Name> 器**"。</span><span class="sxs-lookup"><span data-stu-id="ef54f-121">Click **Clear Filter from \<Column Name>**.</span></span>  
  
### <a name="to-clear-all-filters-for-a-table"></a><span data-ttu-id="ef54f-122">清除表的所有筛选器</span><span class="sxs-lookup"><span data-stu-id="ef54f-122">To clear all filters for a table</span></span>  
  
1.  <span data-ttu-id="ef54f-123">在模型设计器中，选择您要为其清除筛选器的表。</span><span class="sxs-lookup"><span data-stu-id="ef54f-123">In the model designer, select the table for which you want to clear filters.</span></span>  
  
2.  <span data-ttu-id="ef54f-124">单击 **“列”** 菜单，然后单击 **“清除所有筛选器”**。</span><span class="sxs-lookup"><span data-stu-id="ef54f-124">Click on the **Column** menu, and then click **Clear All Filters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef54f-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef54f-125">See Also</span></span>  
 <span data-ttu-id="ef54f-126">[&#40;SSAS 表格中对数据进行筛选和排序&#41;](../filter-and-sort-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="ef54f-126">[Filter and Sort Data &#40;SSAS Tabular&#41;](../filter-and-sort-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="ef54f-127">[SSAS 表格&#41;&#40;透视](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="ef54f-127">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="ef54f-128">角色（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="ef54f-128">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
