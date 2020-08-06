---
title: 对 (SSAS 表格) 的表中的数据进行排序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
author: minewiskan
ms.author: owend
ms.openlocfilehash: d9a6636c2c11fc571e8d4c1bcbc25c1e02d815fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682389"
---
# <a name="sort-data-in-a-table-ssas-tabular"></a><span data-ttu-id="40a3a-102">对表中的数据进行排序（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="40a3a-102">Sort Data in a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="40a3a-103">可以按文本（从 A 到 Z 或从 Z 到 A）和按数字（从小到大或从大到小）对一个或多个列中的数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="40a3a-103">You can sort data by text (A to Z or Z to A) and numbers (smallest to largest or largest to smallest) in one or more columns.</span></span>  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a><span data-ttu-id="40a3a-104">基于文本列对表数据进行排序</span><span class="sxs-lookup"><span data-stu-id="40a3a-104">To sort the data in a table based on a text column</span></span>  
  
1.  <span data-ttu-id="40a3a-105">在模型设计器中，选择某一字母数字数据列或者列中的某一范围的单元，或者确保活动单元处于包含字母数字数据的表列中，然后单击要作为筛选依据的列标题中的箭头。</span><span class="sxs-lookup"><span data-stu-id="40a3a-105">In the model designer, select a column of alphanumeric data, a range of cells in a column, or make sure that the active cell is in a table column that contains alphanumeric data, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="40a3a-106">在“自动筛选”菜单中，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="40a3a-106">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="40a3a-107">若要按字母数字的升序排序，请单击 **“从 A 到 Z 排序”**。</span><span class="sxs-lookup"><span data-stu-id="40a3a-107">To sort in ascending alphanumeric order, click **Sort A to Z**.</span></span>  
  
    -   <span data-ttu-id="40a3a-108">若要按字母数字的降序排序，请单击 **“从 Z 到 A 排序”**。</span><span class="sxs-lookup"><span data-stu-id="40a3a-108">To sort in descending alphanumeric order, click **Sort Z to A**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="40a3a-109">在某些情况下，从其他应用程序导入的数据之前可能插入了前导空格。</span><span class="sxs-lookup"><span data-stu-id="40a3a-109">In some cases, data imported from another application might have leading spaces inserted before data.</span></span> <span data-ttu-id="40a3a-110">您必须删除这些前导空格才能正确对数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="40a3a-110">You must remove the leading spaces in order to correctly sort the data.</span></span>  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a><span data-ttu-id="40a3a-111">基于数字列对表数据进行排序</span><span class="sxs-lookup"><span data-stu-id="40a3a-111">To sort the data in a table based on a numeric column</span></span>  
  
1.  <span data-ttu-id="40a3a-112">在模型设计器中，选择某一字母数字数据列或者列中的某一范围的单元，或者确保活动单元处于包含字母数字数据的表列中，然后单击要作为筛选依据的列标题中的箭头。</span><span class="sxs-lookup"><span data-stu-id="40a3a-112">In the model designer, select a column of alphanumeric data, a range of cells in a column, or make sure that the active cell is in a table column that contains alphanumeric data, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="40a3a-113">在“自动筛选”菜单中，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="40a3a-113">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="40a3a-114">若要从小到大对数字进行排序，请单击 **“从小到大排序”**。</span><span class="sxs-lookup"><span data-stu-id="40a3a-114">To sort from low numbers to high numbers, click **Sort Smallest to Largest**.</span></span>  
  
    -   <span data-ttu-id="40a3a-115">若要从大到小对数字进行排序，请单击 **“从大到小排序”**。</span><span class="sxs-lookup"><span data-stu-id="40a3a-115">To sort from high numbers to low numbers, click **Sort Largest to Smallest**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="40a3a-116">如果得到的并不是期望的结果，列中可能包含存储为文本而不是数字的数字。</span><span class="sxs-lookup"><span data-stu-id="40a3a-116">If the results are not what you expected, the column might contain numbers stored as text and not as numbers.</span></span> <span data-ttu-id="40a3a-117">例如，从某些会计系统导入的负数或是以 '（撇号）开头的数字均存储为文本。</span><span class="sxs-lookup"><span data-stu-id="40a3a-117">For example, negative numbers imported from some accounting systems, or a number entered with a leading ' (apostrophe), are stored as text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a3a-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40a3a-118">See Also</span></span>  
 <span data-ttu-id="40a3a-119">[&#40;SSAS 表格中对数据进行筛选和排序&#41;](../filter-and-sort-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="40a3a-119">[Filter and Sort Data &#40;SSAS Tabular&#41;](../filter-and-sort-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="40a3a-120">[SSAS 表格&#41;&#40;透视](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="40a3a-120">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="40a3a-121">角色（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="40a3a-121">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
