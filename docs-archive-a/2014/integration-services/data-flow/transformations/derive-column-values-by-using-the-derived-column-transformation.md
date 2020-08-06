---
title: 使用派生列转换派生列值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- columns [Integration Services]
- derived columns
- columns [Integration Services], values
- Derived Column transformation
ms.assetid: 28b07746-fc6f-42b2-b741-9de6fac3f29c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 837ec552144697b40cf649bc0403edfe4dc57a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577761"
---
# <a name="derive-column-values-by-using-the-derived-column-transformation"></a><span data-ttu-id="0a90b-102">使用派生列转换派生列值</span><span class="sxs-lookup"><span data-stu-id="0a90b-102">Derive Column Values by Using the Derived Column Transformation</span></span>
  <span data-ttu-id="0a90b-103">若要添加和配置派生列转换，包必须已包含至少一个数据流任务和一个源。</span><span class="sxs-lookup"><span data-stu-id="0a90b-103">To add and configure a Derived Column transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
 <span data-ttu-id="0a90b-104">派生列转换使用表达式来更新现有值或向新列中添加值。</span><span class="sxs-lookup"><span data-stu-id="0a90b-104">The Derived Column transformation uses expressions to update the values of existing or to add values to new columns.</span></span> <span data-ttu-id="0a90b-105">当您选择向新列中添加值时， **“派生列转换编辑器”** 对话框会对表达式求值并相应地定义列的元数据。</span><span class="sxs-lookup"><span data-stu-id="0a90b-105">When you choose to add values to new columns, the **Derived Column Transformation Editor** dialog box evaluates the expression and defines the metadata of the columns accordingly.</span></span> <span data-ttu-id="0a90b-106">例如，如果一个表达式连接两列（每列的数据类型均为 DT_WSTR，长度均为 50），两列值之间有一个空格，则新列的数据类型为 DT_WSTR，长度为 101。</span><span class="sxs-lookup"><span data-stu-id="0a90b-106">For example, if an expression concatenates two columns-each with the DT_WSTR data type and a length of 50-with a space between the two column values, the new column has the DT_WSTR data type and a length of 101.</span></span> <span data-ttu-id="0a90b-107">您可以更新新列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="0a90b-107">You can update the data type of new columns.</span></span> <span data-ttu-id="0a90b-108">唯一的要求是数据类型与插入的数据兼容。</span><span class="sxs-lookup"><span data-stu-id="0a90b-108">The only requirement is that data type be compatible with the inserted data.</span></span> <span data-ttu-id="0a90b-109">例如，当您将日期值分配给数据类型为整数的列时， **“派生列转换编辑器”** 对话框将生成验证错误。</span><span class="sxs-lookup"><span data-stu-id="0a90b-109">For example, the **Derived Column Transformation Editor** dialog box generates a validation error when you assign a date value to a column with an integer data type.</span></span> <span data-ttu-id="0a90b-110">根据所选数据类型，您可以指定列的长度、精度、小数位数和代码页。</span><span class="sxs-lookup"><span data-stu-id="0a90b-110">Depending on the data type that you selected, you can specify the length, precision, scale, and code page of the column.</span></span>  
  
### <a name="to-derive-column-values"></a><span data-ttu-id="0a90b-111">派生列值</span><span class="sxs-lookup"><span data-stu-id="0a90b-111">To derive column values</span></span>  
  
1.  <span data-ttu-id="0a90b-112">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="0a90b-112">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="0a90b-113">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="0a90b-113">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="0a90b-114">单击 **“数据流”** 选项卡，然后将派生列转换从 **“工具箱”** 拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="0a90b-114">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Derived Column transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="0a90b-115">将连接线从源或前一转换拖到派生列转换，从而将派生列转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="0a90b-115">Connect the Derived Column transformation to the data flow by dragging the connector from the source or the previous transformation to the Derived Column transformation.</span></span>  
  
5.  <span data-ttu-id="0a90b-116">双击派生列转换。</span><span class="sxs-lookup"><span data-stu-id="0a90b-116">Double-click the Derived Column transformation.</span></span>  
  
6.  <span data-ttu-id="0a90b-117">在 **“派生列转换编辑器”** 对话框中，将变量、列、函数和运算符拖动到网格中的 **“表达式”** 列，从而生成要用作条件的表达式。</span><span class="sxs-lookup"><span data-stu-id="0a90b-117">In the **Derived Column Transformation Editor** dialog box, build the expressions to use as conditions by dragging variables, columns, functions, and operators to the **Expression** column in the grid.</span></span> <span data-ttu-id="0a90b-118">或者，也可以在 **“表达式”** 列中键入表达式。</span><span class="sxs-lookup"><span data-stu-id="0a90b-118">Alternatively, you can type the expression in the **Expression** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a90b-119">如果表达式无效，表达式文本将突出显示，列上的工具提示将对错误进行说明。</span><span class="sxs-lookup"><span data-stu-id="0a90b-119">If the expression is not valid, the expression text is highlighted and a ToolTip on the column describes the errors.</span></span>  
  
7.  <span data-ttu-id="0a90b-120">在“派生列”列表中，选择“\<add as new column>”以将表达式的计算结果写入新列，或选择一个现有列以用计算结果对其进行更新 。</span><span class="sxs-lookup"><span data-stu-id="0a90b-120">In the **Derived Column** list, select **\<add as new column>** to write the evaluation result of the expression to a new column, or select an existing column to update with the evaluation result.</span></span>  
  
     <span data-ttu-id="0a90b-121">如果选择使用新列， **“派生列转换编辑器”** 对话框将对表达式求值，并根据数据类型、长度、精度、小数位数和代码页为列指定数据类型。</span><span class="sxs-lookup"><span data-stu-id="0a90b-121">If you chose to use a new column, the **Derived Column Transformation Editor** dialog box evaluates the expression and assigns a data type to the column, depending on the data type, length, precisions, scale, and code page.</span></span>  
  
8.  <span data-ttu-id="0a90b-122">如果使用新列，请在 **“数据类型”** 列表中选择数据类型。</span><span class="sxs-lookup"><span data-stu-id="0a90b-122">If using a new column, select a data type in the **Data Type** list.</span></span> <span data-ttu-id="0a90b-123">根据所选的数据类型，可选择更新 **“长度”** 列、 **“精度”** 列、 **“小数位数”** 列和 **“代码页”** 列中的值。</span><span class="sxs-lookup"><span data-stu-id="0a90b-123">Depending on the selected data type, optionally update the values in the **Length**, **Precision**, **Scale**, and **Code Page** columns.</span></span> <span data-ttu-id="0a90b-124">现有列的元数据不能更改。</span><span class="sxs-lookup"><span data-stu-id="0a90b-124">Metadata of existing columns cannot be changed.</span></span>  
  
9. <span data-ttu-id="0a90b-125">还可以在 **“派生列名称”** 列中修改这些值。</span><span class="sxs-lookup"><span data-stu-id="0a90b-125">Optionally, modify the values in the **Derived Column Name** column.</span></span>  
  
10. <span data-ttu-id="0a90b-126">若要配置错误输出，请单击 **“配置错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="0a90b-126">To configure the error output, click **Configure Error Output**.</span></span> <span data-ttu-id="0a90b-127">有关详细信息，请参阅 [在数据流组件中配置错误输出](../../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="0a90b-127">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="0a90b-128">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="0a90b-128">Click **OK**.</span></span>  
  
12. <span data-ttu-id="0a90b-129">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="0a90b-129">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a90b-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a90b-130">See Also</span></span>  
 <span data-ttu-id="0a90b-131">[Derived Column Transformation](derived-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="0a90b-131">[Derived Column Transformation](derived-column-transformation.md) </span></span>  
 <span data-ttu-id="0a90b-132">[Integration Services 数据类型](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="0a90b-132">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 <span data-ttu-id="0a90b-133">[Integration Services 转换](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="0a90b-133">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="0a90b-134">[Integration Services 路径](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="0a90b-134">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="0a90b-135">[数据流任务](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="0a90b-135">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="0a90b-136">Integration Services (SSIS) 表达式</span><span class="sxs-lookup"><span data-stu-id="0a90b-136">Integration Services &#40;SSIS&#41; Expressions</span></span>](../../expressions/integration-services-ssis-expressions.md)  
  
  
