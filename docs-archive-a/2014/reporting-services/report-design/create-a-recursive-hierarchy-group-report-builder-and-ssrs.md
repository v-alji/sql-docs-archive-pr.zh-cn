---
title: 创建一个递归层次结构组（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8b830ba5-4d64-4348-a2b1-76b9338a1462
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf86c3989170ed8cd452168a558ead348258331e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580625"
---
# <a name="create-a-recursive-hierarchy-group-report-builder-and-ssrs"></a><span data-ttu-id="65d44-102">创建一个递归层次结构组（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="65d44-102">Create a Recursive Hierarchy Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="65d44-103">递归层次结构组可组织来自包含多个层次结构级别的单个报表数据集的数据。例如，表示组织层次结构中的经理－雇员关系的报告结构。</span><span class="sxs-lookup"><span data-stu-id="65d44-103">A recursive hierarchy group organizes data from a single report dataset that includes multiple hierarchical levels, such as the report-to structure for manager-employee relationships in an organizational hierarchy.</span></span>  
  
 <span data-ttu-id="65d44-104">必须具有一个包含所有分层数据的数据集，并且要分组的项和作为分组依据的项都必须具有单独字段，才能将表中的数据组织为递归层次结构组。</span><span class="sxs-lookup"><span data-stu-id="65d44-104">Before you can organize data in a table as a recursive hierarchy group, you must have a single dataset that contains all the hierarchical data, You must have separate fields for the item to group and for the item to group by.</span></span> <span data-ttu-id="65d44-105">例如，数据集可能包含姓名、雇员姓名、雇员 ID 和经理 ID，您希望以递归方式对经理级别以下的雇员进行分组。</span><span class="sxs-lookup"><span data-stu-id="65d44-105">For example, a dataset where you want to group employees recursively under their manager might contain a name, an employee name, an employee ID, and a manager ID.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-recursive-hierarchy-group"></a><span data-ttu-id="65d44-106">创建递归层次结构组</span><span class="sxs-lookup"><span data-stu-id="65d44-106">To create a recursive hierarchy group</span></span>  
  
1.  <span data-ttu-id="65d44-107">在“设计”视图中，添加一个表，然后拖动要显示的数据集字段。</span><span class="sxs-lookup"><span data-stu-id="65d44-107">In Design view, add a table, and drag the dataset fields to display.</span></span> <span data-ttu-id="65d44-108">通常，要显示为层次结构的字段位于第一列中。</span><span class="sxs-lookup"><span data-stu-id="65d44-108">Typically, the field that you want to show as a hierarchy is in the first column.</span></span>  
  
2.  <span data-ttu-id="65d44-109">右键单击表中的任意位置以选择该表。</span><span class="sxs-lookup"><span data-stu-id="65d44-109">Right-click anywhere in the table to select it.</span></span> <span data-ttu-id="65d44-110">“分组”窗格将显示所选表的详细信息组。</span><span class="sxs-lookup"><span data-stu-id="65d44-110">The Grouping pane displays the details group for the selected table.</span></span> <span data-ttu-id="65d44-111">在“行组”窗格中，右键单击“详细信息”  ，然后单击“编辑组”  。</span><span class="sxs-lookup"><span data-stu-id="65d44-111">In the Row Groups pane, right-click **Details**, and then click **Edit Group**.</span></span> <span data-ttu-id="65d44-112">此时将打开 **“组属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="65d44-112">The **Group Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="65d44-113">在 **“组表达式”** 中，单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="65d44-113">In **Group expressions**, click **Add**.</span></span> <span data-ttu-id="65d44-114">此时将在网格中显示一个新行。</span><span class="sxs-lookup"><span data-stu-id="65d44-114">A new row appears in the grid.</span></span>  
  
4.  <span data-ttu-id="65d44-115">在 **“分组方式”** 列表中，键入或选择要分组的字段。</span><span class="sxs-lookup"><span data-stu-id="65d44-115">In the **Group on** list, type or select the field to group.</span></span>  
  
5.  <span data-ttu-id="65d44-116">单击“高级”。 </span><span class="sxs-lookup"><span data-stu-id="65d44-116">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="65d44-117">在 **“递归父级”** 列表中，输入或选择要作为分组依据的字段。</span><span class="sxs-lookup"><span data-stu-id="65d44-117">In the **Recursive Parent** list, enter or select the field to group on.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="65d44-118">运行报表。</span><span class="sxs-lookup"><span data-stu-id="65d44-118">Run the report.</span></span> <span data-ttu-id="65d44-119">该报表将显示递归层次结构组，尽管并没有为显示该层次结构而进行缩进</span><span class="sxs-lookup"><span data-stu-id="65d44-119">The report displays the recursive hierarchy group, although there is no indent to show the hierarchy</span></span>  
  
### <a name="to-format-a-recursive-hierarchy-group-with-indent-levels"></a><span data-ttu-id="65d44-120">使用缩进级别设置递归层次结构组的格式</span><span class="sxs-lookup"><span data-stu-id="65d44-120">To format a recursive hierarchy group with indent levels</span></span>  
  
1.  <span data-ttu-id="65d44-121">单击包含特定字段的文本框，要向该字段添加缩进级别来显示层次结构格式。</span><span class="sxs-lookup"><span data-stu-id="65d44-121">Click the text box that contains the field to which you want to add indent levels to display a hierarchy format.</span></span> <span data-ttu-id="65d44-122">该文本框的属性显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="65d44-122">The properties for the text box appear in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="65d44-123">如果看不到“属性”窗格，请单击“视图”选项卡上的“属性”。  </span><span class="sxs-lookup"><span data-stu-id="65d44-123">If you do not see the Properties pane, click **Properties** on the **View** tab.</span></span>  
  
2.  <span data-ttu-id="65d44-124">在 "属性" 窗格中，展开 `Padding` 节点，单击 "**左**"，然后从下拉列表中选择 **\<Expression...>** 。</span><span class="sxs-lookup"><span data-stu-id="65d44-124">In the Properties pane, expand the `Padding` node, click **Left**, and from the drop-down list, select **\<Expression...>**.</span></span>  
  
3.  <span data-ttu-id="65d44-125">在“表达式”窗格中，键入以下表达式：</span><span class="sxs-lookup"><span data-stu-id="65d44-125">In the Expression pane, type the following expression:</span></span>  
  
     `=CStr(2 + (Level()*10)) + "pt"`  
  
     <span data-ttu-id="65d44-126">“填充”属性需要  nnyy 格式的字符串，其中  nn 是一个数字，而  yy 是度量单位。</span><span class="sxs-lookup"><span data-stu-id="65d44-126">The Padding properties all require a string in the format *nnyy*, where *nn* is a number and *yy* is the unit of measure.</span></span> <span data-ttu-id="65d44-127">该示例表达式将生成一个字符串，该字符串使用 `Level` 函数根据递归级别增加填充的大小。</span><span class="sxs-lookup"><span data-stu-id="65d44-127">The example expression builds a string that uses the `Level` function to increase the size of the padding based on recursion level.</span></span> <span data-ttu-id="65d44-128">例如，级别为 1 的行会产生 (2 + (1\*10))=12pt 的填充，而级别为 3 的行会产生 (2 + (3\*10))=32pt 的填充。</span><span class="sxs-lookup"><span data-stu-id="65d44-128">For example, a row that has a level of 1 would result in a padding of (2 + (1\*10))=12pt, and a row that has a level of 3 would result in a padding of (2 + (3\*10))=32pt.</span></span> <span data-ttu-id="65d44-129">有关函数的信息 `Level` ，请参阅[Level](report-builder-functions-level-function.md)。</span><span class="sxs-lookup"><span data-stu-id="65d44-129">For information about the `Level` function, see [Level](report-builder-functions-level-function.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="65d44-130">运行报表。</span><span class="sxs-lookup"><span data-stu-id="65d44-130">Run the report.</span></span> <span data-ttu-id="65d44-131">该报表将显示分组数据的层次结构视图。</span><span class="sxs-lookup"><span data-stu-id="65d44-131">The report displays a hierarchical view of the grouped data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d44-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65d44-132">See Also</span></span>  
 <span data-ttu-id="65d44-133">[创建递归层次结构组（报表生成器和 SSRS）](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="65d44-133">[Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="65d44-134">[对数据进行筛选、分组和排序（报表生成器和 SSRS）](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="65d44-134">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="65d44-135">[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="65d44-135">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="65d44-136">[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="65d44-136">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="65d44-137">[矩阵（报表生成器和 SSRS）](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="65d44-137">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="65d44-138">[列表（报表生成器和 SSRS）](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="65d44-138">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="65d44-139">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="65d44-139">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
