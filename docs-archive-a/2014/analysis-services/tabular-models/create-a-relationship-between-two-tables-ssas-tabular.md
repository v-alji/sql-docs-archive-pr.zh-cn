---
title: " (SSAS 表格) 创建两个表之间的关系 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.managereldb.f1
- sql12.asvs.bidtoolset.createrelatdb.f1
ms.assetid: 052d77b7-7922-408a-a200-786016ee4d15
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33481b8d50be9ca632bcade932d51df86c1910a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580411"
---
# <a name="create-a-relationship-between-two-tables-ssas-tabular"></a><span data-ttu-id="24f06-102">创建两个表之间的关系（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="24f06-102">Create a Relationship Between Two Tables (SSAS Tabular)</span></span>
  <span data-ttu-id="24f06-103">如果数据源中的表没有现有关系，或如果添加新表，则可以使用模型设计器中的工具创建新关系。</span><span class="sxs-lookup"><span data-stu-id="24f06-103">If the tables in your data source do not have existing relationships, or if you add new tables, you can use the tools in the model designer to create new relationships.</span></span> <span data-ttu-id="24f06-104">有关如何在表格模型中使用关系的详细信息，请参阅 [关系（SSAS 表格）](relationships-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="24f06-104">For information about how relationships are used in tabular models, see [Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md).</span></span>  
  
## <a name="create-a-relationship-between-two-tables"></a><span data-ttu-id="24f06-105">创建两个表之间的关系</span><span class="sxs-lookup"><span data-stu-id="24f06-105">Create a relationship between two tables</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-click-and-drag"></a><span data-ttu-id="24f06-106">在关系图视图中创建两个表之间的关系（单击并拖动）</span><span class="sxs-lookup"><span data-stu-id="24f06-106">To create a relationship between two tables in Diagram View (Click and drag)</span></span>  
  
1.  <span data-ttu-id="24f06-107">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，依次单击 **“模型”** 菜单、 **“模型视图”** 和 **“关系图视图”**。</span><span class="sxs-lookup"><span data-stu-id="24f06-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, then click **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="24f06-108">单击（并按住）表中的列，然后将光标拖到相关查找表中的相关查找列上，然后释放光标。</span><span class="sxs-lookup"><span data-stu-id="24f06-108">Click (and hold) on a column within a table, then drag the cursor to a related lookup column in a related lookup table, and then release.</span></span> <span data-ttu-id="24f06-109">将自动按正确的顺序创建关系。</span><span class="sxs-lookup"><span data-stu-id="24f06-109">The relationship will be created in the correct order automatically.</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-right-click"></a><span data-ttu-id="24f06-110">在关系图视图中创建两个表之间的关系（右键单击）</span><span class="sxs-lookup"><span data-stu-id="24f06-110">To create a relationship between two tables in Diagram View (Right-click)</span></span>  
  
1.  <span data-ttu-id="24f06-111">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，依次单击 **“模型”** 菜单、 **“模型视图”** 和 **“关系图视图”**。</span><span class="sxs-lookup"><span data-stu-id="24f06-111">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, then click **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="24f06-112">右键单击表标题或列，然后单击“创建关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="24f06-112">Right-click a table heading or column, and then click **Create Relationship**.</span></span>  
  
3.  <span data-ttu-id="24f06-113">在 **“创建关系”** 对话框中，对于 **“表”** 单击向下箭头，然后从下拉列表中选择某个表。</span><span class="sxs-lookup"><span data-stu-id="24f06-113">In the **Create Relationship** dialog box, click the down arrow for **Table**, and select a table from the dropdown list.</span></span>  
  
     <span data-ttu-id="24f06-114">在“一对多”关系中，此表应位于“多”方。</span><span class="sxs-lookup"><span data-stu-id="24f06-114">In a "one-to-many" relationship, this table should be on the "many" side.</span></span>  
  
4.  <span data-ttu-id="24f06-115">对于 **“列”**，选择包含与 **“相关查找列”** 有关的数据的列。</span><span class="sxs-lookup"><span data-stu-id="24f06-115">For **Column**, select the column that contains the data that is related to **Related Lookup Column**.</span></span> <span data-ttu-id="24f06-116">如果您右键单击要创建关系的列，则系统会自动选中该列。</span><span class="sxs-lookup"><span data-stu-id="24f06-116">The column is automatically selected if you right-clicked on a column to create the relationship.</span></span>  
  
5.  <span data-ttu-id="24f06-117">对于 **“相关查找表”**，选择至少有一列数据与您刚为 **“表”** 选择的表相关的表。</span><span class="sxs-lookup"><span data-stu-id="24f06-117">For **Related Lookup Table**, select a table that has at least one column of data that is related to the table you just selected for **Table**.</span></span>  
  
     <span data-ttu-id="24f06-118">在“一对多”关系中，此表应位于“一”方，这表示所选列中的值不包含重复值。</span><span class="sxs-lookup"><span data-stu-id="24f06-118">In a "one-to-many" relationship, this table should be on the "one" side, meaning that the values in the selected column do not contain duplicates.</span></span> <span data-ttu-id="24f06-119">如果尝试按错误的顺序创建关系（一对多而非多对一），将在“相关查找列”\*\*\*\* 字段旁边显示一个图标。</span><span class="sxs-lookup"><span data-stu-id="24f06-119">If you attempt to create the relationship in the wrong order (one-to-many instead of many-to-one), an icon will appear next to the **Related Lookup Column** field.</span></span> <span data-ttu-id="24f06-120">颠倒顺序以创建有效的关系。</span><span class="sxs-lookup"><span data-stu-id="24f06-120">Reverse the order to create a valid relationship.</span></span>  
  
6.  <span data-ttu-id="24f06-121">对于 **“相关查找列”**，选择一列，此列具有与您为 **“列”** 选择的列中值匹配的唯一值。</span><span class="sxs-lookup"><span data-stu-id="24f06-121">For **Related Lookup Column**, select a column that has unique values that match the values in the column you selected for **Column**.</span></span>  
  
7.  <span data-ttu-id="24f06-122">单击“创建”。</span><span class="sxs-lookup"><span data-stu-id="24f06-122">Click **Create**.</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-data-view"></a><span data-ttu-id="24f06-123">在数据视图中创建两个表之间的关系</span><span class="sxs-lookup"><span data-stu-id="24f06-123">To create a relationship between two tables in Data View</span></span>  
  
1.  <span data-ttu-id="24f06-124">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，单击 **“表”** 菜单，再单击 **“创建关系”**。</span><span class="sxs-lookup"><span data-stu-id="24f06-124">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Create Relationships**.</span></span>  
  
2.  <span data-ttu-id="24f06-125">在 **“创建关系”** 对话框中，对于 **“表”** 单击向下箭头，然后从下拉列表中选择某个表。</span><span class="sxs-lookup"><span data-stu-id="24f06-125">In the **Create Relationship** dialog box, click the down arrow for **Table**, and select a table from the dropdown list.</span></span>  
  
     <span data-ttu-id="24f06-126">在“一对多”关系中，此表应位于“多”方。</span><span class="sxs-lookup"><span data-stu-id="24f06-126">In a "one-to-many" relationship, this table should be on the "many" side.</span></span>  
  
3.  <span data-ttu-id="24f06-127">对于 **“列”**，选择包含与 **“相关查找列”** 有关的数据的列。</span><span class="sxs-lookup"><span data-stu-id="24f06-127">For **Column**, select the column that contains the data that is related to **Related Lookup Column**.</span></span>  
  
4.  <span data-ttu-id="24f06-128">对于 **“相关查找表”**，选择至少有一列数据与您刚为 **“表”** 选择的表相关的表。</span><span class="sxs-lookup"><span data-stu-id="24f06-128">For **Related Lookup Table**, select a table that has at least one column of data that is related to the table you just selected for **Table**.</span></span>  
  
     <span data-ttu-id="24f06-129">在“一对多”关系中，此表应位于“一”方，这表示所选列中的值不包含重复值。</span><span class="sxs-lookup"><span data-stu-id="24f06-129">In a "one-to-many" relationship, this table should be on the "one" side, meaning that the values in the selected column do not contain duplicates.</span></span> <span data-ttu-id="24f06-130">如果尝试按错误的顺序创建关系（一对多而非多对一），将在“相关查找列”\*\*\*\* 字段旁边显示一个图标。</span><span class="sxs-lookup"><span data-stu-id="24f06-130">If you attempt to create the relationship in the wrong order (one-to-many instead of many-to-one), an icon will appear next to the **Related Lookup Column** field.</span></span> <span data-ttu-id="24f06-131">颠倒顺序以创建有效的关系。</span><span class="sxs-lookup"><span data-stu-id="24f06-131">Reverse the order to create a valid relationship.</span></span>  
  
5.  <span data-ttu-id="24f06-132">对于 **“相关查找列”**，选择一列，此列具有与您为 **“列”** 选择的列中值匹配的唯一值。</span><span class="sxs-lookup"><span data-stu-id="24f06-132">For **Related Lookup Column**, select a column that has unique values that match the values in the column you selected for **Column**.</span></span>  
  
6.  <span data-ttu-id="24f06-133">单击“创建”。</span><span class="sxs-lookup"><span data-stu-id="24f06-133">Click **Create**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f06-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24f06-134">See Also</span></span>  
 <span data-ttu-id="24f06-135">[&#40;SSAS 表格&#41;中删除关系](delete-relationships-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="24f06-135">[Delete Relationships &#40;SSAS Tabular&#41;](delete-relationships-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="24f06-136">关系（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="24f06-136">Relationships &#40;SSAS Tabular&#41;</span></span>](relationships-ssas-tabular.md)  
  
  
