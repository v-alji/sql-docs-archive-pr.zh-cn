---
title: 为合并和合并联接转换排序数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- sort attributes [Integration Services]
- output columns [Integration Services]
ms.assetid: 22ce3f5d-8a88-4423-92c2-60a8f82cd4fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7bb4e91ad84c6baa52e1d7fb4b0104d835b7e4cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682959"
---
# <a name="sort-data-for-the-merge-and-merge-join-transformations"></a><span data-ttu-id="c3cef-102">为合并转换和合并联接转换排序数据</span><span class="sxs-lookup"><span data-stu-id="c3cef-102">Sort Data for the Merge and Merge Join Transformations</span></span>
  <span data-ttu-id="c3cef-103">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]中，合并转换和合并联接转换要求其输入为已排序的数据。</span><span class="sxs-lookup"><span data-stu-id="c3cef-103">In [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], the Merge and Merge Join transformations require sorted data for their inputs.</span></span> <span data-ttu-id="c3cef-104">输入数据必须已经过物理排序，且必须对源或上游转换中的输出和输出列设置排序选项。</span><span class="sxs-lookup"><span data-stu-id="c3cef-104">The input data must be sorted physically, and sort options must be set on the outputs and the output columns in the source or in the upstream transformation.</span></span> <span data-ttu-id="c3cef-105">如果排序选项指示数据是已排序的，而数据实际上不是已排序的，则合并或合并联接操作的结果将是不可预知的。</span><span class="sxs-lookup"><span data-stu-id="c3cef-105">If the sort options indicate that the data is sorted, but the data is not actually sorted, the results of the merge or merge join operation are unpredictable.</span></span>  
  
## <a name="sorting-the-data"></a><span data-ttu-id="c3cef-106">对数据进行排序</span><span class="sxs-lookup"><span data-stu-id="c3cef-106">Sorting the Data</span></span>  
 <span data-ttu-id="c3cef-107">可使用下列方法之一对此数据进行排序：</span><span class="sxs-lookup"><span data-stu-id="c3cef-107">You can sort this data by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="c3cef-108">在源中，在用于加载数据的语句中使用 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="c3cef-108">In the source, use an ORDER BY clause in the statement that is used to load the data.</span></span>  
  
-   <span data-ttu-id="c3cef-109">在数据流中，在合并转换或合并联接转换之前插入一个排序转换。</span><span class="sxs-lookup"><span data-stu-id="c3cef-109">In the data flow, insert a Sort transformation before the Merge or Merge Join transformation.</span></span>  
  
 <span data-ttu-id="c3cef-110">如果数据是字符串数据，则合并转换和合并联接转换都需要使用 Windows 排序规则排过序的字符串值。</span><span class="sxs-lookup"><span data-stu-id="c3cef-110">If the data is string data, both the Merge and Merge Join transformations expect the string values to have been sorted by using Windows collation.</span></span> <span data-ttu-id="c3cef-111">若要向合并转换和合并联接转换提供使用 Windows 排序规则排过序的字符串值，请使用以下过程。</span><span class="sxs-lookup"><span data-stu-id="c3cef-111">To provide string values to the Merge and Merge Join transformations that are sorted by using Windows collation, use the following procedure.</span></span>  
  
#### <a name="to-provide-string-values-that-are-sorted-by-using-windows-collation"></a><span data-ttu-id="c3cef-112">提供使用 Windows 排序规则排过序的字符串值</span><span class="sxs-lookup"><span data-stu-id="c3cef-112">To provide string values that are sorted by using Windows collation</span></span>  
  
-   <span data-ttu-id="c3cef-113">使用排序转换对数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-113">Use a Sort transformation to sort the data.</span></span>  
  
     <span data-ttu-id="c3cef-114">排序转换使用 Windows 排序规则对字符串值进行排序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-114">The Sort transformation uses Windows collation to sort string values.</span></span>  
  
     <span data-ttu-id="c3cef-115">-或-</span><span class="sxs-lookup"><span data-stu-id="c3cef-115">-or-</span></span>  
  
-   <span data-ttu-id="c3cef-116">首先使用 Transact-SQL CAST 运算符将 `varchar` 值转换为 `nvarchar` 值，然后再使用 Transact-SQL ORDER BY 子句对数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-116">Use the Transact-SQL CAST operator to first cast `varchar` values to `nvarchar` values, and then use the Transact-SQL ORDER BY clause to sort the data.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c3cef-117">由于 ORDER BY 子句使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 排序规则对字符串值进行排序，因此不能单独使用 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="c3cef-117">You cannot use the ORDER BY clause alone because the ORDER BY clause uses a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] collation to sort string values.</span></span> <span data-ttu-id="c3cef-118">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 排序规则可能产生与 Windows 排序规则不同的排序顺序，这会导致合并转换或合并联接转换生成意外的结果。</span><span class="sxs-lookup"><span data-stu-id="c3cef-118">The use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] collation might result in a different sort order than Windows collation, which can cause the Merge or Merge Join transformation to produce unexpected results.</span></span>  
  
## <a name="setting-sort-options-on-the-data"></a><span data-ttu-id="c3cef-119">为数据设置排序选项</span><span class="sxs-lookup"><span data-stu-id="c3cef-119">Setting Sort Options on the Data</span></span>  
 <span data-ttu-id="c3cef-120">必须为向合并转换和合并联接转换提供数据的源或上游转换设置两个重要的排序属性：</span><span class="sxs-lookup"><span data-stu-id="c3cef-120">There are two important sort properties that must be set for the source or upstream transformation that supplies data to the Merge and Merge Join transformations:</span></span>  
  
-   <span data-ttu-id="c3cef-121">输出的 `IsSorted` 属性，指示数据是否已排序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-121">The `IsSorted` property of the output that indicates whether the data has been sorted.</span></span> <span data-ttu-id="c3cef-122">此属性必须设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="c3cef-122">This property must be set to `True`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c3cef-123">将 `IsSorted` 属性的值设置为 `True` 时将不会对数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-123">Setting the value of the `IsSorted` property to `True` does not sort the data.</span></span> <span data-ttu-id="c3cef-124">此属性仅向下游组件提示数据之前已经过排序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-124">This property only provides a hint to downstream components that the data has been previously sorted.</span></span>  
  
-   <span data-ttu-id="c3cef-125">输出列的 `SortKeyPosition` 属性，指示单个列是否已排序、其排序顺序以及多个列的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-125">The `SortKeyPosition` property of output columns that indicates whether a column is sorted, the column's sort order, and the sequence in which multiple columns are sorted.</span></span> <span data-ttu-id="c3cef-126">必须为已排序数据的每一列设置此属性。</span><span class="sxs-lookup"><span data-stu-id="c3cef-126">This property must be set for each column of sorted data.</span></span>  
  
 <span data-ttu-id="c3cef-127">如果使用排序转换对数据进行排序，则排序转换将按合并转换或合并联接转换的要求设置这两个属性。</span><span class="sxs-lookup"><span data-stu-id="c3cef-127">If you use a Sort transformation to sort the data, the Sort transformation sets both of these properties as required by the Merge or Merge Join transformation.</span></span> <span data-ttu-id="c3cef-128">即，排序转换将其输出的 `IsSorted` 属性设置为 `True`，并设置其输出列的 `SortKeyPosition` 属性。</span><span class="sxs-lookup"><span data-stu-id="c3cef-128">That is, the Sort transformation sets the `IsSorted` property of its output to `True`, and sets the `SortKeyPosition` properties of its output columns.</span></span>  
  
 <span data-ttu-id="c3cef-129">但是，如果不使用排序转换对数据进行排序，则必须对源或上游转换手动设置这些排序属性。</span><span class="sxs-lookup"><span data-stu-id="c3cef-129">However, if you do not use a Sort transformation to sort the data, you must set these sort properties manually on the source or the upstream transformation.</span></span> <span data-ttu-id="c3cef-130">若要对源或上游转换手动设置这些排序属性，请使用以下过程。</span><span class="sxs-lookup"><span data-stu-id="c3cef-130">To manually set the sort properties on the source or upstream transformation, use the following procedure.</span></span>  
  
#### <a name="to-manually-set-sort-attributes-on-a-source-or-transformation-component"></a><span data-ttu-id="c3cef-131">对源或转换组件手动设置排序属性</span><span class="sxs-lookup"><span data-stu-id="c3cef-131">To manually set sort attributes on a source or transformation component</span></span>  
  
1.  <span data-ttu-id="c3cef-132">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="c3cef-132">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="c3cef-133">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="c3cef-133">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="c3cef-134">在 **“数据流”** 选项卡中，找到适当的源或上游转换，或将其从 **“工具箱”** 拖到设计图面上。</span><span class="sxs-lookup"><span data-stu-id="c3cef-134">On the **Data Flow** tab, locate the appropriate source or upstream transformation, or drag it from the **Toolbox** to the design surface.</span></span>  
  
4.  <span data-ttu-id="c3cef-135">右键单击组件，并单击“显示高级编辑器”。</span><span class="sxs-lookup"><span data-stu-id="c3cef-135">Right-click the component and click **Show Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="c3cef-136">单击 **“输入属性和输出属性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c3cef-136">Click the **Input and Output Properties** tab.</span></span>  
  
6.  <span data-ttu-id="c3cef-137">单击 " \*\* \<component name> 输出\*\*"，并将 `IsSorted` 属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="c3cef-137">Click **\<component name> Output**, and set the `IsSorted` property to `True`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c3cef-138">如果手动将输出的 `IsSorted` 属性设置为 `True`且没有对数据进行排序，则当你运行该包时，可能会在下游合并或合并联接转换中产生缺失数据或错误数据比较。</span><span class="sxs-lookup"><span data-stu-id="c3cef-138">If you manually set the `IsSorted` property of the output to `True` and the data is not sorted, there might be missing data or bad data comparisons in the downstream Merge or Merge Join transformation when you run the package.</span></span>  
  
7.  <span data-ttu-id="c3cef-139">展开 **“输出列”** 。</span><span class="sxs-lookup"><span data-stu-id="c3cef-139">Expand **Output Columns**.</span></span>  
  
8.  <span data-ttu-id="c3cef-140">单击要指示为已排序的列，并根据下列准则将其 `SortKeyPosition` 属性设置为非零的整数：</span><span class="sxs-lookup"><span data-stu-id="c3cef-140">Click the column that you want to indicate is sorted and set its `SortKeyPosition` property to a nonzero integer value by following these guidelines:</span></span>  
  
    -   <span data-ttu-id="c3cef-141">该整数值必须表示一个数值序列，从 1 开始，并按 1 递增。</span><span class="sxs-lookup"><span data-stu-id="c3cef-141">The integer value must represent a numeric sequence, starting with 1 and incremented by 1.</span></span>  
  
    -   <span data-ttu-id="c3cef-142">正整数值表示按升序排序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-142">A positive integer value indicates an ascending sort order.</span></span>  
  
    -   <span data-ttu-id="c3cef-143">负整数值表示按降序排序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-143">A negative integer value indicates a descending sort order.</span></span> <span data-ttu-id="c3cef-144">（如果设置为负数，则该数值的绝对值决定该列在排序序列中的位置。）</span><span class="sxs-lookup"><span data-stu-id="c3cef-144">(If set to a negative number, the absolute value of the number determines the column's position in the sort sequence.)</span></span>  
  
    -   <span data-ttu-id="c3cef-145">默认值 0 表示没有对该列进行排序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-145">The default value of 0 indicates that the column is not sorted.</span></span> <span data-ttu-id="c3cef-146">请为没有参与排序的输出列保留值 0。</span><span class="sxs-lookup"><span data-stu-id="c3cef-146">Leave the value of 0 for output columns that do not participate in the sort.</span></span>  
  
     <span data-ttu-id="c3cef-147">作为如何设置 `SortKeyPosition` 属性的一个示例，请考虑以下在源中加载数据的 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="c3cef-147">As an example of how to set the `SortKeyPosition` property, consider the following Transact-SQL statement that loads data in a source:</span></span>  
  
     `SELECT * FROM MyTable ORDER BY ColumnA, ColumnB DESC, ColumnC`  
  
     <span data-ttu-id="c3cef-148">对于此语句，您可以为每一列按如下所示设置 `SortKeyPosition` 属性：</span><span class="sxs-lookup"><span data-stu-id="c3cef-148">For this statement, you would set the `SortKeyPosition` property for each column as follows:</span></span>  
  
    -   <span data-ttu-id="c3cef-149">将 ColumnA 的 `SortKeyPosition` 属性设置为 1。</span><span class="sxs-lookup"><span data-stu-id="c3cef-149">Set the `SortKeyPosition` property of ColumnA to 1.</span></span> <span data-ttu-id="c3cef-150">这表示 ColumnA 是第一个要排序的列，并且是以升序排序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-150">This indicates that ColumnA is the first column to be sorted and is sorted in ascending order.</span></span>  
  
    -   <span data-ttu-id="c3cef-151">将 ColumnB 的 `SortKeyPosition` 属性设置为 -2。</span><span class="sxs-lookup"><span data-stu-id="c3cef-151">Set the `SortKeyPosition` property of ColumnB to -2.</span></span> <span data-ttu-id="c3cef-152">这表示 ColumnB 是第二个要排序的列，并且是以降序排序</span><span class="sxs-lookup"><span data-stu-id="c3cef-152">This indicates that ColumnB is the second column to be sorted and is sorted in descending order</span></span>  
  
    -   <span data-ttu-id="c3cef-153">将 ColumnC 的 `SortKeyPosition` 属性设置为 3。</span><span class="sxs-lookup"><span data-stu-id="c3cef-153">Set the `SortKeyPosition` property of ColumnC to 3.</span></span> <span data-ttu-id="c3cef-154">这表示 ColumnC 是第三个要排序的列，并且是以升序排序。</span><span class="sxs-lookup"><span data-stu-id="c3cef-154">This indicates that ColumnC is the third column to be sorted and is sorted in ascending order.</span></span>  
  
9. <span data-ttu-id="c3cef-155">对每个已排序的列，重复步骤 8。</span><span class="sxs-lookup"><span data-stu-id="c3cef-155">Repeat step 8 for each sorted column.</span></span>  
  
10. <span data-ttu-id="c3cef-156">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="c3cef-156">Click **OK**.</span></span>  
  
11. <span data-ttu-id="c3cef-157">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="c3cef-157">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3cef-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3cef-158">See Also</span></span>  
 <span data-ttu-id="c3cef-159">[合并转换](merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="c3cef-159">[Merge Transformation](merge-transformation.md) </span></span>  
 <span data-ttu-id="c3cef-160">[合并联接转换](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="c3cef-160">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="c3cef-161">[Integration Services 转换](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="c3cef-161">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="c3cef-162">[Integration Services 路径](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="c3cef-162">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="c3cef-163">数据流任务</span><span class="sxs-lookup"><span data-stu-id="c3cef-163">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
