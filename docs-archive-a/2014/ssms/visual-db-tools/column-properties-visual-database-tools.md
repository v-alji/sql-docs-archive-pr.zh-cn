---
title: 列属性 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.Column.ColumnIdentitySpec
- vdt.designers.properties.Column
- vdt.tablecolumn
- vdt.designers.properties.Column.ColumnComputedColumnSpec
- vdt.designers.properties.Column.ColumnFulltextSpec
ms.assetid: e549a2a8-4154-4ec8-b146-614564169b39
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6aeb4d01cae7c09c27cafa8284638bf0a7de9691
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682615"
---
# <a name="column-properties-visual-database-tools"></a><span data-ttu-id="ac2e3-102">列属性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ac2e3-102">Column Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="ac2e3-103">有两种列属性集：可在表设计器的“列属性”  选项卡中看到的完整集（仅适用于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库）以及可使用服务器资源管理器在“属性”窗口中看到的子集。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-103">There are two sets of properties for columns: a full set that you can see in the **Column Properties** tab within Table Designer (available only for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases) and a subset you can see in the Properties window using Server Explorer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac2e3-104">本主题中的属性按类别排序，而不是按字母顺序排序。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-104">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac2e3-105">根据当前设置或版本的不同，所看到的对话框和菜单命令可能与帮助中描述的对话框和菜单命令有所不同。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ac2e3-106">若要更改设置，请在“工具”菜单上选择“导入和导出设置”。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span>  
  
## <a name="properties-window"></a><span data-ttu-id="ac2e3-107">“属性”窗口</span><span class="sxs-lookup"><span data-stu-id="ac2e3-107">Properties Window</span></span>  
 <span data-ttu-id="ac2e3-108">在服务器资源管理器中选择列后，“属性”窗口中将显示以下属性：</span><span class="sxs-lookup"><span data-stu-id="ac2e3-108">These properties appear in the Properties window when you select a column in Server Explorer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac2e3-109">使用服务器资源管理器访问的这些属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-109">These properties, accessed using Server Explorer, are read-only.</span></span> <span data-ttu-id="ac2e3-110">若要编辑 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的列属性，请在表设计器中选择相应的列。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-110">To edit column properties for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, select the column in Table Designer.</span></span> <span data-ttu-id="ac2e3-111">本主题稍后部分中将介绍那些属性。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-111">Those properties are described later in this topic.</span></span>  
  
 <span data-ttu-id="ac2e3-112">**标识类别**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-112">**Identity Category**</span></span>  
 <span data-ttu-id="ac2e3-113">展开此项可显示“名称”  和“数据库”  属性。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-113">Expands to show the **Name** and **Database** properties.</span></span>  
  
 <span data-ttu-id="ac2e3-114">**名称**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-114">**Name**</span></span>  
 <span data-ttu-id="ac2e3-115">显示列的名称。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-115">Shows the name of the column.</span></span>  
  
 <span data-ttu-id="ac2e3-116">**Database**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-116">**Database**</span></span>  
 <span data-ttu-id="ac2e3-117">显示所选列的数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-117">Shows the name of the data source for the selected column.</span></span> <span data-ttu-id="ac2e3-118">（仅适用于 OLE DB。）</span><span class="sxs-lookup"><span data-stu-id="ac2e3-118">(Applies only to OLE DB.)</span></span>  
  
 <span data-ttu-id="ac2e3-119">**杂项类别**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-119">**Misc Category**</span></span>  
 <span data-ttu-id="ac2e3-120">展开此项可显示剩余的属性。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-120">Expands to show the remaining properties.</span></span>  
  
 <span data-ttu-id="ac2e3-121">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-121">**Data Type**</span></span>  
 <span data-ttu-id="ac2e3-122">显示所选列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-122">Shows the data type of the selected column.</span></span> <span data-ttu-id="ac2e3-123">有关详细信息，请参阅[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-123">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="ac2e3-124">**标识增量**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-124">**Identity Increment**</span></span>  
 <span data-ttu-id="ac2e3-125">显示标识列各后续行的“标识种子”  将增加的增量。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-125">Shows the increment that will be added to the **Identity Seed** for each subsequent row of the identity column.</span></span> <span data-ttu-id="ac2e3-126">（仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。）</span><span class="sxs-lookup"><span data-stu-id="ac2e3-126">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="ac2e3-127">**标识种子**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-127">**Identity Seed**</span></span>  
 <span data-ttu-id="ac2e3-128">显示分配给表中标识列的第一行的种子值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-128">Shows the seed value assigned to the first row in the table for the identity column.</span></span> <span data-ttu-id="ac2e3-129">（仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。）</span><span class="sxs-lookup"><span data-stu-id="ac2e3-129">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="ac2e3-130">**是标识**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-130">**Is Identity**</span></span>  
 <span data-ttu-id="ac2e3-131">显示所选列是否为表的标识列。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-131">Shows whether the selected column is the identity column for the table.</span></span> <span data-ttu-id="ac2e3-132">（仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。）</span><span class="sxs-lookup"><span data-stu-id="ac2e3-132">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="ac2e3-133">**长度**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-133">**Length**</span></span>  
 <span data-ttu-id="ac2e3-134">显示基于字符的数据类型所允许的字符数。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-134">Shows the number of characters allowed for character-based data types.</span></span>  
  
 <span data-ttu-id="ac2e3-135">**可以为 Null**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-135">**Nullable**</span></span>  
 <span data-ttu-id="ac2e3-136">显示列是否允许空值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-136">Shows whether or not the column allows null values.</span></span>  
  
 <span data-ttu-id="ac2e3-137">**精度**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-137">**Precision**</span></span>  
 <span data-ttu-id="ac2e3-138">显示数值数据类型所允许的最大位数。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-138">Shows the maximum number of digits allowed for numeric data types.</span></span> <span data-ttu-id="ac2e3-139">对于非数值数据类型，此属性显示 **0** 。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-139">This property shows **0** for nonnumeric data types.</span></span>  
  
 <span data-ttu-id="ac2e3-140">**缩放**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-140">**Scale**</span></span>  
 <span data-ttu-id="ac2e3-141">显示数值数据类型的小数点右侧可显示的最大位数。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-141">Shows the maximum number of digits that can appear to the right of the decimal point for numeric data types.</span></span> <span data-ttu-id="ac2e3-142">此值必须小于或等于精度。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-142">This value must be less than or equal to the precision.</span></span> <span data-ttu-id="ac2e3-143">对于非数值数据类型，此属性显示 **0** 。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-143">This property shows **0** for nonnumeric data types.</span></span>  
  
## <a name="column-properties-tab"></a><span data-ttu-id="ac2e3-144">“列属性”选项卡</span><span class="sxs-lookup"><span data-stu-id="ac2e3-144">Column Properties Tab</span></span>  
 <span data-ttu-id="ac2e3-145">若要访问这些属性，请在服务器资源管理器中右键单击列所属的表，选择“打开表定义”  ，然后在表设计器的表网格中选择行。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-145">To access these properties, in Server Explorer right-click the table to which the column belongs, choose **Open Table Definition**, and select the row in the table grid in Table Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac2e3-146">这些属性仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-146">These properties apply only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ac2e3-147">**常规类别**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-147">**General Category**</span></span>  
 <span data-ttu-id="ac2e3-148">展开此项可显示“名称”  、“允许空值”  、“数据类型”  、“默认值或绑定”  、“长度”  、“精度”  和“小数位数”  。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-148">Expands to show **Name**, **Allow Nulls**, **Data Type**, **Default Value or Binding**, **Length**, **Precision**, and **Scale**.</span></span>  
  
 <span data-ttu-id="ac2e3-149">**名称**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-149">**Name**</span></span>  
 <span data-ttu-id="ac2e3-150">显示列的名称。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-150">Displays the name of the column.</span></span> <span data-ttu-id="ac2e3-151">若要编辑名称，请在文本框中键入相应的内容。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-151">To edit the name, type in the text box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="ac2e3-152">如果现有查询、视图、用户定义函数、存储过程或程序引用该列，则更改列名将使这些对象无效。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-152">If existing queries, views, user-defined functions, stored procedures, or programs refer to the column, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="ac2e3-153">**允许 Null 值**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-153">**Allow Nulls**</span></span>  
 <span data-ttu-id="ac2e3-154">显示列的数据类型是否允许空值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-154">Shows whether or not the column's data type allows null values.</span></span>  
  
 <span data-ttu-id="ac2e3-155">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-155">**Data Type**</span></span>  
 <span data-ttu-id="ac2e3-156">显示所选列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-156">Shows the data type for the selected column.</span></span> <span data-ttu-id="ac2e3-157">若要编辑此属性，请单击该属性的值，展开下拉列表，然后选择其他值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-157">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span> <span data-ttu-id="ac2e3-158">有关详细信息，请参阅[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-158">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="ac2e3-159">**默认值或绑定**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-159">**Default Value or Binding**</span></span>  
 <span data-ttu-id="ac2e3-160">如果未为此列指定值，则显示此列的默认值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-160">Shows the default for this column when no value is specified for this column.</span></span> <span data-ttu-id="ac2e3-161">下拉列表中包含了数据源中定义的所有全局默认值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-161">The drop-down list contains all global defaults defined in the data source.</span></span> <span data-ttu-id="ac2e3-162">若要将该列绑定到某个全局默认值，请从下拉列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-162">To bind the column to a global default, select from the drop-down list.</span></span> <span data-ttu-id="ac2e3-163">另外，若要为该列创建默认约束，请直接以文本格式键入默认值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-163">Alternatively, to create a default constraint for the column, type the default value directly as text.</span></span>  
  
 <span data-ttu-id="ac2e3-164">**长度**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-164">**Length**</span></span>  
 <span data-ttu-id="ac2e3-165">显示基于字符的数据类型所允许的字符数。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-165">Shows the number of characters allowed for character-based data types.</span></span> <span data-ttu-id="ac2e3-166">此属性仅可用于基于字符的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-166">This property is only available for character-based data types.</span></span>  
  
 <span data-ttu-id="ac2e3-167">**精度**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-167">**Precision**</span></span>  
 <span data-ttu-id="ac2e3-168">显示数值数据类型所允许的最大位数。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-168">Shows the maximum number of digits allowed for numeric data types.</span></span> <span data-ttu-id="ac2e3-169">对于非数值数据类型，此属性显示 **0** 。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-169">This property shows **0** for nonnumeric data types.</span></span> <span data-ttu-id="ac2e3-170">此属性仅可用于数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-170">This property is only available for numeric data types.</span></span>  
  
 <span data-ttu-id="ac2e3-171">**缩放**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-171">**Scale**</span></span>  
 <span data-ttu-id="ac2e3-172">显示数值数据类型的小数点右侧可显示的最大位数。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-172">Shows the maximum number of digits that can appear to the right of the decimal point for numeric data types.</span></span> <span data-ttu-id="ac2e3-173">此值必须小于或等于精度。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-173">This value must be less than or equal to the precision.</span></span> <span data-ttu-id="ac2e3-174">对于非数值数据类型，此属性显示 **0** 。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-174">This property shows **0** for nonnumeric data types.</span></span> <span data-ttu-id="ac2e3-175">此属性仅可用于数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-175">This property is only available for numeric data types.</span></span>  
  
 <span data-ttu-id="ac2e3-176">**表设计器类别**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-176">**Table Designer Category**</span></span>  
 <span data-ttu-id="ac2e3-177">展开此项可显示剩余的属性。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-177">Expands to show the remaining properties.</span></span>  
  
 <span data-ttu-id="ac2e3-178">**排序规则**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-178">**Collation**</span></span>  
 <span data-ttu-id="ac2e3-179">显示所选列的排序规则设置。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-179">Shows the collation setting for the selected column.</span></span> <span data-ttu-id="ac2e3-180">若要更改此设置，请单击“排序规则”，再单击值右侧的省略号“(…)”   。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-180">To change this setting, click **Collation** and then click the ellipses **(...)** to the right of the value.</span></span>  
  
 <span data-ttu-id="ac2e3-181">**计算列规范类别**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-181">**Computed Column Specification Category**</span></span>  
 <span data-ttu-id="ac2e3-182">展开此项可显示“公式”  和“是持久的”  属性。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-182">Expands to show properties for **Formula** and **Is Persisted**.</span></span> <span data-ttu-id="ac2e3-183">如果该列是计算列，则还会显示公式。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-183">If the column is computed, the formula will also be displayed.</span></span> <span data-ttu-id="ac2e3-184">若要编辑公式，请展开此类别，然后在“公式”  属性中对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-184">To edit the formula, expand this category and edit it in the **Formula** property.</span></span>  
  
 <span data-ttu-id="ac2e3-185">**公式**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-185">**Formula**</span></span>  
 <span data-ttu-id="ac2e3-186">如果所选列为计算列，则显示该列使用的公式。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-186">Shows the formula that the selected column uses if it is a computed column.</span></span> <span data-ttu-id="ac2e3-187">您可以在此字段中输入或更改公式。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-187">In this field you can enter or change a formula.</span></span>  
  
 <span data-ttu-id="ac2e3-188">**是持久的**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-188">**Is Persisted**</span></span>  
 <span data-ttu-id="ac2e3-189">允许使用数据源保存计算列。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-189">Allows you to save the computed column with the data source.</span></span> <span data-ttu-id="ac2e3-190">可对持久化计算列进行索引。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-190">A persisted computed column can be indexed.</span></span>  
  
 <span data-ttu-id="ac2e3-191">**简洁数据类型**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-191">**Condensed Data Type**</span></span>  
 <span data-ttu-id="ac2e3-192">按与 SQL CREATE TABLE 语句同样的格式显示有关字段的数据类型的信息。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-192">Displays information about the field's data type, in the same format as the SQL CREATE TABLE statement.</span></span> <span data-ttu-id="ac2e3-193">例如，一个包含可变长度字符串（最大长度为 20 个字符）的字段将表示为“varchar(20)”。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-193">For example, a field containing a variable-length string with a maximum length of 20 characters would be represented as "varchar(20)."</span></span> <span data-ttu-id="ac2e3-194">若要更改此属性，请直接键入值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-194">To change this property, type the value directly.</span></span>  
  
 <span data-ttu-id="ac2e3-195">**说明**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-195">**Description**</span></span>  
 <span data-ttu-id="ac2e3-196">显示列的说明。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-196">Shows the description of the column.</span></span> <span data-ttu-id="ac2e3-197">若要查看或编辑完整说明，请单击“说明”，再单击属性右侧的省略号“(…)”  。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-197">To see the full description or to edit it, click Description, and then click the ellipses **(...)** to the right of the property.</span></span>  
  
 <span data-ttu-id="ac2e3-198">**全文本规范类别**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-198">**Full-text Specification Category**</span></span>  
 <span data-ttu-id="ac2e3-199">展开此项可显示专用于全文本列的属性。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-199">Expands to show properties specific to full-text columns.</span></span>  
  
 <span data-ttu-id="ac2e3-200">**是全文索引的**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-200">**Is Full-text Indexed**</span></span>  
 <span data-ttu-id="ac2e3-201">指示此列是否为全文索引列。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-201">Indicates whether this column is full-text indexed.</span></span> <span data-ttu-id="ac2e3-202">只有在可对此列的数据类型进行全文搜索并且为此列所属的表指定了全文索引时，此属性才可设置为“是”  。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-202">This property can be set to **Yes** only if the data type for this column is full-text searchable and if the table to which this column belongs has a full-text index specified for it.</span></span> <span data-ttu-id="ac2e3-203">若要更改此值，请单击该值，展开下拉列表，再选择新值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-203">To change this value, click it, expand the drop-down list, and choose a new value.</span></span>  
  
 <span data-ttu-id="ac2e3-204">**全文本类型列**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-204">**Full-text type column**</span></span>  
 <span data-ttu-id="ac2e3-205">显示用于定义图像类型列的文档类型的列。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-205">Shows which column is used to define the document type of a column of type image.</span></span> <span data-ttu-id="ac2e3-206">图像数据类型可用于存储从 .doc 文件到 xml 文件等多种类型的文档。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-206">The image data type can be used to store documents ranging from .doc files to xml files.</span></span>  
  
 <span data-ttu-id="ac2e3-207">**语言**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-207">**Language**</span></span>  
 <span data-ttu-id="ac2e3-208">指示用于对列进行索引的语言。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-208">Indicates the language used to index the column.</span></span>  
  
 <span data-ttu-id="ac2e3-209">**统计语义**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-209">**Statistical Semantics**</span></span>  
 <span data-ttu-id="ac2e3-210">选择是否为所选列启用统计语义索引。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-210">Select whether to enable statistical semantic indexing for the selected column.</span></span> <span data-ttu-id="ac2e3-211">有关详细信息，请参阅[语义搜索 (SQL Server)](../../relational-databases/search/semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-211">For more information, see [Semantic Search &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="ac2e3-212">如果您在选择 **“统计语义”** 前选择某一 **“语言”** ，并且所选语言没有关联的语义语言模型，则 **“统计语义”** 复选框将设置为 **“否”** 并且无法修改。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-212">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** option is set to **No** and cannot be modified.</span></span> <span data-ttu-id="ac2e3-213">如果您在选择 **“语言”** 前为 **“统计语义”** 选项选择 **“是”** ，则 **“语言”** 列中提供的语言将限制为存在语义语言模型支持的那些语言。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-213">If you select **Yes** for the **Statistical Semantics** option prior to selecting a **Language**, then the languages available in the **Language** column will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
 <span data-ttu-id="ac2e3-214">**具有非 SQL Server 订户**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-214">**Has Non-SQL Server Subscriber**</span></span>  
 <span data-ttu-id="ac2e3-215">显示列是否具有非 Microsoft SQL Server 订户。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-215">Shows whether the column has a non-Microsoft SQL Server subscriber.</span></span>  
  
 <span data-ttu-id="ac2e3-216">**标识规范类别**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-216">**Identity Specification Category**</span></span>  
 <span data-ttu-id="ac2e3-217">展开此项可显示“是标识”  、“标识增量”  和“标识种子”  属性。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-217">Expands to show properties for **Is Identity**, **Identity Increment**, and **Identity Seed**.</span></span>  
  
 <span data-ttu-id="ac2e3-218">**是标识**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-218">**Is Identity**</span></span>  
 <span data-ttu-id="ac2e3-219">显示所选列是否为表的标识列。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-219">Shows whether the selected column is the identity column for the table.</span></span> <span data-ttu-id="ac2e3-220">若要更改属性，请在表设计器中打开表，然后在“属性”  窗口中编辑这些属性。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-220">To change the property, open the table in Table Designer and edit the properties in the **Properties** window.</span></span> <span data-ttu-id="ac2e3-221">此设置仅适用于基于数字的数据类型的列，例如 *int*。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-221">This setting applies only to columns with a number-based data type, such as *int*.</span></span>  
  
 <span data-ttu-id="ac2e3-222">**标识增量**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-222">**Identity Increment**</span></span>  
 <span data-ttu-id="ac2e3-223">显示各后续行的“标识种子”  要增加的增量。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-223">Shows the increment that will be added to the **Identity Seed** for each subsequent row.</span></span> <span data-ttu-id="ac2e3-224">如果将此单元格保留为空白，则默认情况下，会将值 1 赋给该单元格。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-224">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="ac2e3-225">若要编辑此属性，请直接键入新值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-225">To edit this property, type the new value directly.</span></span>  
  
 <span data-ttu-id="ac2e3-226">**标识种子**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-226">**Identity Seed**</span></span>  
 <span data-ttu-id="ac2e3-227">显示分配给表中第一行的值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-227">Shows the value assigned to the first row in the table.</span></span> <span data-ttu-id="ac2e3-228">如果将此单元格保留为空白，则默认情况下，会将值 1 赋给该单元格。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-228">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="ac2e3-229">若要编辑此属性，请直接键入新值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-229">To edit this property, type the new value directly.</span></span>  
  
 <span data-ttu-id="ac2e3-230">**是确定的**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-230">**Is Deterministic**</span></span>  
 <span data-ttu-id="ac2e3-231">显示是否可以明确地确定所选列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-231">Shows whether the data type of the selected column can be determined with certainty.</span></span>  
  
 <span data-ttu-id="ac2e3-232">**是 DTS 发布的**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-232">**Is DTS-published**</span></span>  
 <span data-ttu-id="ac2e3-233">显示该列是否是 DTS 发布的。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-233">Shows whether the column is DTS-published.</span></span>  
  
 <span data-ttu-id="ac2e3-234">**可编制索引**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-234">**Is Indexable**</span></span>  
 <span data-ttu-id="ac2e3-235">显示是否可以对所选列进行索引。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-235">Shows whether the selected column can be indexed.</span></span> <span data-ttu-id="ac2e3-236">例如，不能对不确定的计算列进行索引。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-236">For example, non-deterministic computed columns cannot be indexed.</span></span>  
  
 <span data-ttu-id="ac2e3-237">**是合并发布的**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-237">**Is Merge-published**</span></span>  
 <span data-ttu-id="ac2e3-238">显示该列是否是合并发布的。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-238">Shows whether the column is merge-published.</span></span>  
  
 <span data-ttu-id="ac2e3-239">**不用于复制**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-239">**Is Not For Replication**</span></span>  
 <span data-ttu-id="ac2e3-240">指示在复制期间是否保留原始标识值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-240">Indicates whether original identity values are preserved during replication.</span></span> <span data-ttu-id="ac2e3-241">若要编辑此属性，请单击该属性的值，展开下拉列表，然后选择其他值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-241">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="ac2e3-242">**是复制的**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-242">**Is Replicated**</span></span>  
 <span data-ttu-id="ac2e3-243">显示是否在其他位置复制此列。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-243">Shows whether this column is replicated in another location.</span></span>  
  
 <span data-ttu-id="ac2e3-244">**是 RowGuid**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-244">**Is RowGuid**</span></span>  
 <span data-ttu-id="ac2e3-245">指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是否将该列用作 ROWGUID。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-245">Indicates whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the column as a ROWGUID.</span></span> <span data-ttu-id="ac2e3-246">对于数据类型为的列，只能将此值设置为 **"是"** `uniqueidentifier` 。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-246">You can set this value to **Yes** only for a column with the data type of `uniqueidentifier`.</span></span> <span data-ttu-id="ac2e3-247">若要编辑此属性，请单击该属性的值，展开下拉列表，然后选择其他值。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-247">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="ac2e3-248">**大小**</span><span class="sxs-lookup"><span data-stu-id="ac2e3-248">**Size**</span></span>  
 <span data-ttu-id="ac2e3-249">显示该列的数据类型所允许的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-249">Shows the size in bytes allowed by column's data type.</span></span> <span data-ttu-id="ac2e3-250">例如，某个 `nchar` 数据类型的长度为 10（字符数），但在 Unicode 字符集中，该数据类型的大小为 20。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-250">For example, a `nchar` data type may have a length of 10 (the number of characters) but it would have a size of 20 to account for Unicode character sets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac2e3-251">`varchar(max)`  数据类型的长度对于每一行都会有所不同。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-251">The length of a `varchar(max)` data type varies for each row.</span></span> <span data-ttu-id="ac2e3-252">sp_help 返回 (-1) 作为列的长度 `varchar(max)` 。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-252">sp_help returns (-1) as the length of `varchar(max)` column.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="ac2e3-253">显示 -1 作为列大小。</span><span class="sxs-lookup"><span data-stu-id="ac2e3-253">displays -1 as the column size.</span></span>  
  
  
