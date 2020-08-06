---
title: 在“报表数据”窗格中添加、编辑和刷新字段（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2e36f0fe-8100-4513-b169-14d611646f81
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a20880b84383fc5d9f96c5611419a08facb9ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577330"
---
# <a name="add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs"></a><span data-ttu-id="7650a-102">在“报表数据”窗格中添加、编辑和刷新字段（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7650a-102">Add, Edit, Refresh Fields in the Report Data Pane (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7650a-103">数据集字段是在对外部数据源运行数据集查询时返回的表示数据的字段名称的内置集合。</span><span class="sxs-lookup"><span data-stu-id="7650a-103">Dataset fields are the built-in collection of field names that represent the data that is returned when a dataset query runs on an external data source.</span></span>  
  
 <span data-ttu-id="7650a-104">对于嵌入数据集，数据集字段是您生成查询并关闭查询设计器窗格后创建的字段以及创建的计算字段。</span><span class="sxs-lookup"><span data-stu-id="7650a-104">For an embedded dataset, the dataset fields are the fields that are created after you finish building a query and close the Query Designer pane, and calculated fields that you create.</span></span>  
  
 <span data-ttu-id="7650a-105">对于共享数据集，数据集字段是将共享数据集定义添加到报表中时来自该定义的字段。</span><span class="sxs-lookup"><span data-stu-id="7650a-105">For a shared dataset, the dataset fields are the fields from the shared dataset definition when you added it to your report.</span></span> <span data-ttu-id="7650a-106">尽管在运行报表时，始终使用报表服务器上共享数据集的查询，但是报表中的数据集字段列表是静态的。</span><span class="sxs-lookup"><span data-stu-id="7650a-106">Although the query from the shared dataset on the report server is always used when you run the report, the list of dataset fields in the report is static.</span></span>  
  
 <span data-ttu-id="7650a-107">使用 **“刷新字段”** 更新报表中的字段列表，以匹配共享数据集查询中的当前字段列表。</span><span class="sxs-lookup"><span data-stu-id="7650a-107">Use **Refresh Fields** to update the list of fields in the report to match the current list of fields from the shared dataset query.</span></span> <span data-ttu-id="7650a-108">刷新字段列表不影响您在报表中定义的计算字段。</span><span class="sxs-lookup"><span data-stu-id="7650a-108">Refreshing the field list does not affect the calculated fields that you define in your report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-query-field"></a><span data-ttu-id="7650a-109">添加查询字段</span><span class="sxs-lookup"><span data-stu-id="7650a-109">To add a query field</span></span>  
  
1.  <span data-ttu-id="7650a-110">在“报表数据”窗格中，右键单击数据集，再单击“添加查询字段”  。</span><span class="sxs-lookup"><span data-stu-id="7650a-110">In the Report Data pane, right-click the dataset, and then click **Add Query Field**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7650a-111">如果看不到“报表数据”窗格，请单击“视图”菜单上的“报表数据”   。</span><span class="sxs-lookup"><span data-stu-id="7650a-111">If you cannot see the Report Data pane, from the **View** menu, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="7650a-112">在 **“数据集属性”** 对话框的 **“字段”** 页中，单击 **“添加”** ，再单击 **“查询字段”** 。</span><span class="sxs-lookup"><span data-stu-id="7650a-112">In the **Fields** page of the **Dataset Properties** dialog box, click **Add**, and then click **Query Field**.</span></span> <span data-ttu-id="7650a-113">将向网格底部添加一个新行。</span><span class="sxs-lookup"><span data-stu-id="7650a-113">A new row is added to the bottom of the grid.</span></span>  
  
3.  <span data-ttu-id="7650a-114">在 **“字段名称”** 文本框中，键入字段的名称。</span><span class="sxs-lookup"><span data-stu-id="7650a-114">In the **Field Name** text box, type the name for the field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7650a-115">名称在数据集中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7650a-115">Names must be unique in the dataset.</span></span>  
  
4.  <span data-ttu-id="7650a-116">在 **“字段源”** 文本框中，键入数据源中现有字段的名称。</span><span class="sxs-lookup"><span data-stu-id="7650a-116">In the **Field Source** text box, type the name of an existing field on the data source.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-calculated-field"></a><span data-ttu-id="7650a-117">添加计算字段</span><span class="sxs-lookup"><span data-stu-id="7650a-117">To add a calculated field</span></span>  
  
1.  <span data-ttu-id="7650a-118">在“报表数据”窗格中，右键单击数据集，再单击“添加计算字段”  。</span><span class="sxs-lookup"><span data-stu-id="7650a-118">In the Report Data pane, right-click the dataset, and then click **Add Calculated Field**.</span></span>  
  
2.  <span data-ttu-id="7650a-119">在 **“数据集属性”** 对话框的 **“字段”** 页中，单击 **“添加”** ，再单击 **“计算字段”** 。</span><span class="sxs-lookup"><span data-stu-id="7650a-119">In the **Fields** page of the **Dataset Properties** dialog box, click **Add**, and then click **Calculated Field**.</span></span> <span data-ttu-id="7650a-120">将向网格底部添加一个新行。</span><span class="sxs-lookup"><span data-stu-id="7650a-120">A new row is added to the bottom of the grid.</span></span>  
  
3.  <span data-ttu-id="7650a-121">在 **“字段名称”** 文本框中，键入字段的名称。</span><span class="sxs-lookup"><span data-stu-id="7650a-121">In the **Field Name** text bo, type the name for the field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7650a-122">名称在数据集中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7650a-122">Names must be unique in the dataset.</span></span>  
  
4.  <span data-ttu-id="7650a-123">在 **“字段源”** 文本框中，键入字段的表达式。</span><span class="sxs-lookup"><span data-stu-id="7650a-123">In the **Field Source** text box, type the expression for the field.</span></span> <span data-ttu-id="7650a-124">单击表达式 (**fx**) 按钮可生成表达式。</span><span class="sxs-lookup"><span data-stu-id="7650a-124">Click the expression (**fx**) button to build an expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7650a-125">计算字段的表达式不能包含对报表项的聚合或引用。</span><span class="sxs-lookup"><span data-stu-id="7650a-125">The expression for a calculated field cannot contain aggregates or references to report items.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-a-query-field-or-a-dataset-field"></a><span data-ttu-id="7650a-126">编辑查询字段或数据集字段</span><span class="sxs-lookup"><span data-stu-id="7650a-126">To edit a query field or a dataset field</span></span>  
  
1.  <span data-ttu-id="7650a-127">在“报表数据”窗格中，右键单击字段，然后单击“字段属性”  。</span><span class="sxs-lookup"><span data-stu-id="7650a-127">In the Report Data pane, right-click the field, and then click **Field Properties**.</span></span>  
  
2.  <span data-ttu-id="7650a-128">在 **“数据集属性”** 对话框的 **“字段”** 页中，单击现有字段来选择行。</span><span class="sxs-lookup"><span data-stu-id="7650a-128">In the **Fields** page of the **Dataset Properties** dialog box, click an existing field to select the row.</span></span>  
  
3.  <span data-ttu-id="7650a-129">更改字段名称或字段值。</span><span class="sxs-lookup"><span data-stu-id="7650a-129">Change the name of the field or the value of the field.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-query-field-or-a-calculated-field"></a><span data-ttu-id="7650a-130">删除查询字段或计算字段</span><span class="sxs-lookup"><span data-stu-id="7650a-130">To delete a query field or a calculated field</span></span>  
  
1.  <span data-ttu-id="7650a-131">在“报表数据”窗格中，展开数据集以显示字段集合。</span><span class="sxs-lookup"><span data-stu-id="7650a-131">In the Report Data pane, expand the dataset to display the field collection.</span></span>  
  
2.  <span data-ttu-id="7650a-132">右键单击要删除的字段，再单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="7650a-132">Right-click the field you want to remove, and then click **Delete**.</span></span>  
  
### <a name="to-refresh-the-field-collection-in-the-report-data-pane-for-a-shared-dataset"></a><span data-ttu-id="7650a-133">为共享数据集刷新“报表数据”窗格中的字段集合</span><span class="sxs-lookup"><span data-stu-id="7650a-133">To refresh the field collection in the Report Data Pane for a shared dataset</span></span>  
  
1.  <span data-ttu-id="7650a-134">在“报表数据”窗格中，右键单击该数据集，然后单击“查询”  。</span><span class="sxs-lookup"><span data-stu-id="7650a-134">In the Report Data pane, right-click the dataset, and then click **Query**.</span></span>  
  
2.  <span data-ttu-id="7650a-135">单击 **“刷新字段”** 。</span><span class="sxs-lookup"><span data-stu-id="7650a-135">Click **Refresh Fields**.</span></span>  
  
     <span data-ttu-id="7650a-136">在报表服务器上，运行共享数据集查询并返回当前的字段集合。</span><span class="sxs-lookup"><span data-stu-id="7650a-136">On the report server, the shared dataset query runs and returns the current field collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7650a-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7650a-137">See Also</span></span>  
 <span data-ttu-id="7650a-138">[数据集字段集合（报表生成器和 SSRS）](dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7650a-138">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7650a-139">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7650a-139">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="7650a-140">[报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7650a-140">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7650a-141">[Reporting Services 查询设计器](../reporting-services-query-designers.md) </span><span class="sxs-lookup"><span data-stu-id="7650a-141">[Reporting Services Query Designers](../reporting-services-query-designers.md) </span></span>  
 [<span data-ttu-id="7650a-142">查询设计器（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="7650a-142">Query Designers &#40;Report Builder&#41;</span></span>](../query-designers-report-builder.md)  
  
  
