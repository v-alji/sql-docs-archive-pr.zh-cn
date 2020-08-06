---
title: 透视转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.pivottrans.f1
helpviewer_keywords:
- Pivot transformation
- normalized data [Integration Services]
- PivotUsage property
- datasets [Integration Services], normalized data
- less normalized data set [Integration Services]
ms.assetid: 55f5db6e-6777-435f-8a06-b68c129f8437
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43bdc5be709ea00d4be4601f52c38e96fe3f1ce4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694543"
---
# <a name="pivot-transformation"></a><span data-ttu-id="81974-102">透视转换</span><span class="sxs-lookup"><span data-stu-id="81974-102">Pivot Transformation</span></span>
  <span data-ttu-id="81974-103">通过透视列值的输入数据，透视转换将规范的数据集转变成规范程度稍低、但更为简洁的版本。</span><span class="sxs-lookup"><span data-stu-id="81974-103">The Pivot transformation makes a normalized data set into a less normalized but more compact version by pivoting the input data on a column value.</span></span> <span data-ttu-id="81974-104">例如，在列有客户名称、产品和购买数量的规范的 **Orders** 数据集中，任何购买多种产品的客户都有多行，每一行显示一种产品的详细订购信息。</span><span class="sxs-lookup"><span data-stu-id="81974-104">For example, a normalized **Orders** data set that lists customer name, product, and quantity purchased typically has multiple rows for any customer who purchased multiple products, with each row for that customer showing order details for a different product.</span></span> <span data-ttu-id="81974-105">此时，如果对产品列透视数据集，透视转换可以输出每个客户只有一行的数据集。</span><span class="sxs-lookup"><span data-stu-id="81974-105">By pivoting the data set on the product column, the Pivot transformation can output a data set with a single row per customer.</span></span> <span data-ttu-id="81974-106">这一行列出该客户购买的所有产品，产品名称显示为列名，而数量则显示为产品列的值。</span><span class="sxs-lookup"><span data-stu-id="81974-106">That single row lists all the purchases by the customer, with the product names shown as column names, and the quantity shown as a value in the product column.</span></span> <span data-ttu-id="81974-107">并非每个客户都购买所有产品，所以很多列可能包含空值。</span><span class="sxs-lookup"><span data-stu-id="81974-107">Because not every customer purchases every product, many columns may contain null values.</span></span>  
  
 <span data-ttu-id="81974-108">透视数据集时，输入列在透视过程中扮演不同的角色。</span><span class="sxs-lookup"><span data-stu-id="81974-108">When a dataset is pivoted, input columns perform different roles in the pivoting process.</span></span> <span data-ttu-id="81974-109">列可以按以下方式参与：</span><span class="sxs-lookup"><span data-stu-id="81974-109">A column can participate in the following ways:</span></span>  
  
-   <span data-ttu-id="81974-110">将列原封不动地传递到输出。</span><span class="sxs-lookup"><span data-stu-id="81974-110">The column is passed through unchanged to the output.</span></span> <span data-ttu-id="81974-111">因为有许多输入行只能产生一个输出行，所以转换只复制列的第一个输入值。</span><span class="sxs-lookup"><span data-stu-id="81974-111">Because many input rows can result only in one output row, the transformation copies only the first input value for the column.</span></span>  
  
-   <span data-ttu-id="81974-112">列作为一组记录的标识键或标识键的一部分。</span><span class="sxs-lookup"><span data-stu-id="81974-112">The column acts as the key or part of the key that identifies a set of records.</span></span>  
  
-   <span data-ttu-id="81974-113">列定义透视。</span><span class="sxs-lookup"><span data-stu-id="81974-113">The column defines the pivot.</span></span> <span data-ttu-id="81974-114">此列中的值与已透视数据集中的列相关联。</span><span class="sxs-lookup"><span data-stu-id="81974-114">The values in this column are associated with columns in the pivoted dataset.</span></span>  
  
-   <span data-ttu-id="81974-115">列包含置于透视所创建的列中的值。</span><span class="sxs-lookup"><span data-stu-id="81974-115">The column contains values that are placed in the columns that the pivot creates.</span></span>  
  
 <span data-ttu-id="81974-116">此转换有一个输入、一个常规输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="81974-116">This transformation has one input, one regular output, and one error output.</span></span>  
  
## <a name="sort-and-duplicate-rows"></a><span data-ttu-id="81974-117">排序和复制行</span><span class="sxs-lookup"><span data-stu-id="81974-117">Sort and Duplicate Rows</span></span>  
 <span data-ttu-id="81974-118">若要高效地透视数据，即在输出数据集中创建尽可能少的记录，就必须对透视列的输入数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="81974-118">To pivot data efficiently, which means creating as few records in the output dataset as possible, the input data must be sorted on the pivot column.</span></span> <span data-ttu-id="81974-119">如果数据未经排序，那么透视转换就可能为设置键（即定义集成员关系的列）中的每个值生成多个记录。</span><span class="sxs-lookup"><span data-stu-id="81974-119">If the data is not sorted, the Pivot transformation might generate multiple records for each value in the set key, which is the column that defines set membership.</span></span> <span data-ttu-id="81974-120">例如，如果对 **名称** 列透视数据集，但是没有对名称排序，则每个客户在输出数据集中可能有多行，因为 **名称** 中的值每次更改都会发生透视。</span><span class="sxs-lookup"><span data-stu-id="81974-120">For example, if a dataset is pivoted on a **Name** column but the names are not sorted, the output dataset could have more than one row for each customer, because a pivot occurs every time that the value in **Name** changes.</span></span>  
  
 <span data-ttu-id="81974-121">输入数据可能包含重复行，这会导致透视转换失败。</span><span class="sxs-lookup"><span data-stu-id="81974-121">The input data might contain duplicate rows, which will cause the Pivot transformation to fail.</span></span> <span data-ttu-id="81974-122">“重复行”表示在设置键列和透视列中具有相同值的行。</span><span class="sxs-lookup"><span data-stu-id="81974-122">"Duplicate rows" means rows that have the same values in the set key columns and the pivot columns.</span></span> <span data-ttu-id="81974-123">为了避免失败，可以将转换配置为将错误行重定向到错误输出或预先聚合值，以确保不存在重复行。</span><span class="sxs-lookup"><span data-stu-id="81974-123">To avoid failure, you can either configure the transformation to redirect error rows to an error output or you can pre-aggregate values to ensure there are no duplicate rows.</span></span>  
  
##  <a name="options-in-the-pivot-dialog-box"></a><a name="options"></a> <span data-ttu-id="81974-124">“透视”对话框中的选项</span><span class="sxs-lookup"><span data-stu-id="81974-124">Options in the Pivot Dialog Box</span></span>  
 <span data-ttu-id="81974-125">可以通过设置 **“透视”** 对话框中的选项来配置透视操作。</span><span class="sxs-lookup"><span data-stu-id="81974-125">You configure the pivot operation by setting the options in the **Pivot** dialog box.</span></span> <span data-ttu-id="81974-126">若要打开“透视”对话框，请在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中将透视转换添加到包，右键单击该组件，然后单击“编辑”。</span><span class="sxs-lookup"><span data-stu-id="81974-126">To open the **Pivot** dialog box, add the Pivot transformation to the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], and then right-click the component and click **Edit**.</span></span>  
  
 <span data-ttu-id="81974-127">以下列表介绍了 **“透视”** 对话框中的选项。</span><span class="sxs-lookup"><span data-stu-id="81974-127">The following list describes the options in the **Pivot** dialog box.</span></span>  
  
 <span data-ttu-id="81974-128">**透视键**</span><span class="sxs-lookup"><span data-stu-id="81974-128">**Pivot Key**</span></span>  
 <span data-ttu-id="81974-129">指定要用于跨表的最上面一行（标题行）的值的列。</span><span class="sxs-lookup"><span data-stu-id="81974-129">Specifies the column to use for values across the top row (header row) of the table.</span></span>  
  
 <span data-ttu-id="81974-130">**设置键**</span><span class="sxs-lookup"><span data-stu-id="81974-130">**Set Key**</span></span>  
 <span data-ttu-id="81974-131">指定要用于表左侧列的值的列。</span><span class="sxs-lookup"><span data-stu-id="81974-131">Specifies the column to use for values in the left column of the table.</span></span> <span data-ttu-id="81974-132">必须在此列对输入日期排序。</span><span class="sxs-lookup"><span data-stu-id="81974-132">The input date must be sorted on this column.</span></span>  
  
 <span data-ttu-id="81974-133">**透视值**</span><span class="sxs-lookup"><span data-stu-id="81974-133">**Pivot Value**</span></span>  
 <span data-ttu-id="81974-134">指定要用于以下表值的列：它们不是标题行和左侧列中的值。</span><span class="sxs-lookup"><span data-stu-id="81974-134">Specifies the column to use for the table values, other than the values in the header row and the left column.</span></span>  
  
 <span data-ttu-id="81974-135">**忽略不匹配的透视键值并在 DataFlow 执行后报告这些值**</span><span class="sxs-lookup"><span data-stu-id="81974-135">**Ignore un-matched Pivot Key values and report them after DataFlow execution**</span></span>  
 <span data-ttu-id="81974-136">选择此选项，以将透视转换配置为在运行包时忽略包含“透视键”列中无法识别的值的行并将所有透视键值输出到日志消息。</span><span class="sxs-lookup"><span data-stu-id="81974-136">Select this option to configure the Pivot transformation to ignore rows containing unrecognized values in the **Pivot Key** column and to output all of the pivot key values to a log message, when the package is run.</span></span>  
  
 <span data-ttu-id="81974-137">还可以通过将 `PassThroughUnmatchedPivotKeys` 自定义属性设置为 `True` 来将该转换配置为输出这些值。</span><span class="sxs-lookup"><span data-stu-id="81974-137">You can also configure the transformation to output the values by setting the `PassThroughUnmatchedPivotKeys` custom property to `True`.</span></span>  
  
 <span data-ttu-id="81974-138">**根据值生成透视输出列**</span><span class="sxs-lookup"><span data-stu-id="81974-138">**Generate pivot output columns from values**</span></span>  
 <span data-ttu-id="81974-139">在此框中输入透视键值，以启用透视转换来创建每个值的输出列。</span><span class="sxs-lookup"><span data-stu-id="81974-139">Enter the pivot key values in this box to enable the Pivot transformation to create output columns for each value.</span></span> <span data-ttu-id="81974-140">您可以在运行包之前输入值，或执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="81974-140">You can either enter the values prior to running the package, or do the following.</span></span>  
  
1.  <span data-ttu-id="81974-141">在“透视”对话框中选择“忽略不匹配的透视键值并在 DataFlow 执行后报告这些值”选项，然后单击“确定”以保存对透视转换的更改。</span><span class="sxs-lookup"><span data-stu-id="81974-141">Select the **Ignore un-matched Pivot Key values and report them after DataFlow execution** option, and then click **OK** in the **Pivot** dialog box to save the changes to the Pivot transformation.</span></span>  
  
2.  <span data-ttu-id="81974-142">运行包。</span><span class="sxs-lookup"><span data-stu-id="81974-142">Run the package.</span></span>  
  
3.  <span data-ttu-id="81974-143">包成功运行时，单击 **“进度”** 选项卡，从包含透视键值的透视转换中查找信息日志消息。</span><span class="sxs-lookup"><span data-stu-id="81974-143">When the package succeeds, click the **Progress** tab and look for the information log message from the Pivot transformation that contains the pivot key values.</span></span>  
  
4.  <span data-ttu-id="81974-144">右键单击该消息，然后单击“复制消息正文”。</span><span class="sxs-lookup"><span data-stu-id="81974-144">Right-click the message and click **Copy Message Text**.</span></span>  
  
5.  <span data-ttu-id="81974-145">在 **“调试”** 菜单上单击 **“停止调试”** 以切换回设计模式。</span><span class="sxs-lookup"><span data-stu-id="81974-145">Click **Stop Debugging** on the **Debug** menu to switch to the design mode.</span></span>  
  
6.  <span data-ttu-id="81974-146">右键单击该透视转换，然后单击“编辑”。</span><span class="sxs-lookup"><span data-stu-id="81974-146">Right-click the Pivot transformation, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="81974-147">取消选中“忽略不匹配的透视键值并在 DataFlow 执行后报告这些值”选项，然后使用以下格式在“根据值生成透视输出列”框中粘贴透视键值：</span><span class="sxs-lookup"><span data-stu-id="81974-147">Uncheck the **Ignore un-matched Pivot Key values and report them after DataFlow execution** option, and then paste the pivot key values in the **Generate pivot output columns from values** box using the following format.</span></span>  
  
     <span data-ttu-id="81974-148">[value1],[value2],[value3]</span><span class="sxs-lookup"><span data-stu-id="81974-148">[value1],[value2],[value3]</span></span>  
  
 <span data-ttu-id="81974-149">**立即生成列**</span><span class="sxs-lookup"><span data-stu-id="81974-149">**Generate Columns Now**</span></span>  
 <span data-ttu-id="81974-150">单击以便为在“根据值生成透视输出列”框中列出的每个透视键值创建输出列。</span><span class="sxs-lookup"><span data-stu-id="81974-150">Click to create an output column for each pivot key value that is listed in the **Generate pivot output columns from values** box.</span></span>  
  
 <span data-ttu-id="81974-151">输出列显示在 **“现有的透视输出列”** 框中。</span><span class="sxs-lookup"><span data-stu-id="81974-151">The output columns appear in the **Existing pivoted output columns** box.</span></span>  
  
 <span data-ttu-id="81974-152">**“现有的透视输出列”**</span><span class="sxs-lookup"><span data-stu-id="81974-152">**Existing pivoted output columns**</span></span>  
 <span data-ttu-id="81974-153">列出透视键值的输出列。</span><span class="sxs-lookup"><span data-stu-id="81974-153">Lists the output columns for the pivot key values</span></span>  
  
 <span data-ttu-id="81974-154">下表显示对 **年** 列透视数据前的数据集。</span><span class="sxs-lookup"><span data-stu-id="81974-154">The following table shows a data set before the data is pivoted on the **Year** column.</span></span>  
  
|<span data-ttu-id="81974-155">年龄</span><span class="sxs-lookup"><span data-stu-id="81974-155">Year</span></span>|<span data-ttu-id="81974-156">产品名称</span><span class="sxs-lookup"><span data-stu-id="81974-156">Product Name</span></span>|<span data-ttu-id="81974-157">总计</span><span class="sxs-lookup"><span data-stu-id="81974-157">Total</span></span>|  
|----------|------------------|-----------|  
|<span data-ttu-id="81974-158">2004</span><span class="sxs-lookup"><span data-stu-id="81974-158">2004</span></span>|<span data-ttu-id="81974-159">HL Mountain Tire</span><span class="sxs-lookup"><span data-stu-id="81974-159">HL Mountain Tire</span></span>|<span data-ttu-id="81974-160">1504884.15</span><span class="sxs-lookup"><span data-stu-id="81974-160">1504884.15</span></span>|  
|<span data-ttu-id="81974-161">2003</span><span class="sxs-lookup"><span data-stu-id="81974-161">2003</span></span>|<span data-ttu-id="81974-162">Road Tire Tube</span><span class="sxs-lookup"><span data-stu-id="81974-162">Road Tire Tube</span></span>|<span data-ttu-id="81974-163">35920.50</span><span class="sxs-lookup"><span data-stu-id="81974-163">35920.50</span></span>|  
|<span data-ttu-id="81974-164">2004</span><span class="sxs-lookup"><span data-stu-id="81974-164">2004</span></span>|<span data-ttu-id="81974-165">Water Bottle - 30 oz.</span><span class="sxs-lookup"><span data-stu-id="81974-165">Water Bottle - 30 oz.</span></span>|<span data-ttu-id="81974-166">2805.00</span><span class="sxs-lookup"><span data-stu-id="81974-166">2805.00</span></span>|  
|<span data-ttu-id="81974-167">2002</span><span class="sxs-lookup"><span data-stu-id="81974-167">2002</span></span>|<span data-ttu-id="81974-168">Touring Tire</span><span class="sxs-lookup"><span data-stu-id="81974-168">Touring Tire</span></span>|<span data-ttu-id="81974-169">62364.225</span><span class="sxs-lookup"><span data-stu-id="81974-169">62364.225</span></span>|  
  
 <span data-ttu-id="81974-170">下表显示对 **年** 列透视数据后的数据集。</span><span class="sxs-lookup"><span data-stu-id="81974-170">The following table shows a data set after the data has been pivoted on the **Year** column.</span></span>  
  
||<span data-ttu-id="81974-171">2002</span><span class="sxs-lookup"><span data-stu-id="81974-171">2002</span></span>|<span data-ttu-id="81974-172">2003</span><span class="sxs-lookup"><span data-stu-id="81974-172">2003</span></span>|<span data-ttu-id="81974-173">2004</span><span class="sxs-lookup"><span data-stu-id="81974-173">2004</span></span>|  
|-|----------|----------|----------|  
|<span data-ttu-id="81974-174">HL Mountain Tire</span><span class="sxs-lookup"><span data-stu-id="81974-174">HL Mountain Tire</span></span>|<span data-ttu-id="81974-175">141164.10</span><span class="sxs-lookup"><span data-stu-id="81974-175">141164.10</span></span>|<span data-ttu-id="81974-176">446297.775</span><span class="sxs-lookup"><span data-stu-id="81974-176">446297.775</span></span>|<span data-ttu-id="81974-177">1504884.15</span><span class="sxs-lookup"><span data-stu-id="81974-177">1504884.15</span></span>|  
|<span data-ttu-id="81974-178">Road Tire Tube</span><span class="sxs-lookup"><span data-stu-id="81974-178">Road Tire Tube</span></span>|<span data-ttu-id="81974-179">3592.05</span><span class="sxs-lookup"><span data-stu-id="81974-179">3592.05</span></span>|<span data-ttu-id="81974-180">35920.50</span><span class="sxs-lookup"><span data-stu-id="81974-180">35920.50</span></span>|<span data-ttu-id="81974-181">89801.25</span><span class="sxs-lookup"><span data-stu-id="81974-181">89801.25</span></span>|  
|<span data-ttu-id="81974-182">Water Bottle - 30 oz.</span><span class="sxs-lookup"><span data-stu-id="81974-182">Water Bottle - 30 oz.</span></span>|<span data-ttu-id="81974-183">*NULL*</span><span class="sxs-lookup"><span data-stu-id="81974-183">*NULL*</span></span>|<span data-ttu-id="81974-184">*NULL*</span><span class="sxs-lookup"><span data-stu-id="81974-184">*NULL*</span></span>|<span data-ttu-id="81974-185">2805.00</span><span class="sxs-lookup"><span data-stu-id="81974-185">2805.00</span></span>|  
|<span data-ttu-id="81974-186">Touring Tire</span><span class="sxs-lookup"><span data-stu-id="81974-186">Touring Tire</span></span>|<span data-ttu-id="81974-187">62364.225</span><span class="sxs-lookup"><span data-stu-id="81974-187">62364.225</span></span>|<span data-ttu-id="81974-188">375051.60</span><span class="sxs-lookup"><span data-stu-id="81974-188">375051.60</span></span>|<span data-ttu-id="81974-189">1041810.00</span><span class="sxs-lookup"><span data-stu-id="81974-189">1041810.00</span></span>|  
  
 <span data-ttu-id="81974-190">为了如上所示对 **年** 列透视数据，在 **“透视”** 对话框中设置了以下选项。</span><span class="sxs-lookup"><span data-stu-id="81974-190">To pivot the data on the **Year** column, as shown above, the following options are set in the **Pivot** dialog box.</span></span>  
  
-   <span data-ttu-id="81974-191">在 **“透视键”** 列表框中选择了“年”。</span><span class="sxs-lookup"><span data-stu-id="81974-191">Year is selected in the **Pivot Key** list box.</span></span>  
  
-   <span data-ttu-id="81974-192">在 **“设置键”** 列表框中选择了“产品名称”。</span><span class="sxs-lookup"><span data-stu-id="81974-192">Product Name is selected in the **Set Key** list box.</span></span>  
  
-   <span data-ttu-id="81974-193">在 **“透视值”** 列表框中选择了“总计”。</span><span class="sxs-lookup"><span data-stu-id="81974-193">Total is selected in the **Pivot Value** list box.</span></span>  
  
-   <span data-ttu-id="81974-194">在 **“根据值生成透视输出列”** 框中输入以下值。</span><span class="sxs-lookup"><span data-stu-id="81974-194">The following values are entered in the **Generate pivot output columns from values** box.</span></span>  
  
     <span data-ttu-id="81974-195">[2002],[2003],[2004]</span><span class="sxs-lookup"><span data-stu-id="81974-195">[2002],[2003],[2004]</span></span>  
  
## <a name="configuration-of-the-pivot-transformation"></a><span data-ttu-id="81974-196">透视转换的配置</span><span class="sxs-lookup"><span data-stu-id="81974-196">Configuration of the Pivot Transformation</span></span>  
 <span data-ttu-id="81974-197">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="81974-197">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="81974-198">有关可以在 **“高级编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="81974-198">For more information about the properties that you can set in the **Advanced Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="81974-199">Common Properties</span><span class="sxs-lookup"><span data-stu-id="81974-199">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="81974-200">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="81974-200">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-content"></a><span data-ttu-id="81974-201">相关内容</span><span class="sxs-lookup"><span data-stu-id="81974-201">Related Content</span></span>  
 <span data-ttu-id="81974-202">有关如何设置数据流组件属性的信息，请参阅 [设置数据流组件属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="81974-202">For information about how to set the properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81974-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="81974-203">See Also</span></span>  
 <span data-ttu-id="81974-204">[逆透视转换](pivot-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="81974-204">[Unpivot Transformation](pivot-transformation.md) </span></span>  
 <span data-ttu-id="81974-205">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="81974-205">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="81974-206">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="81974-206">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
