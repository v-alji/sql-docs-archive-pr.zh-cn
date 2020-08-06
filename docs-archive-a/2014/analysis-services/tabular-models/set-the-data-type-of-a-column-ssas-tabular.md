---
title: 设置 (SSAS 表格) 的列的数据类型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 34e2d508-7b64-4503-a4f0-c6c6ad5f8a44
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d747f96e836a683ccce3aca3c5e3349ca633210
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682396"
---
# <a name="set-the-data-type-of-a-column-ssas-tabular"></a><span data-ttu-id="c509a-102">设置列的数据类型（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="c509a-102">Set the Data Type of a Column (SSAS Tabular)</span></span>
  <span data-ttu-id="c509a-103">导入数据或将数据粘贴到模型时，模型设计器将自动检测并应用数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-103">When you import data or paste data into a model, the model designer will automatically detect and apply data types.</span></span> <span data-ttu-id="c509a-104">在将数据添加到模型后，您可以手动修改列的数据类型以便更改数据的存储方式。</span><span class="sxs-lookup"><span data-stu-id="c509a-104">After you have added the data to the model, you can manually modify the data type of a column to change how data is stored.</span></span> <span data-ttu-id="c509a-105">如果只想更改显示数据的格式而不更改其存储方式，可以采用其他方法。</span><span class="sxs-lookup"><span data-stu-id="c509a-105">If you just want to change the format of how the data is displayed without changing the way it is stored, you can do that instead.</span></span>  
  
### <a name="to-change-the-data-type-or-display-format-for-a-column"></a><span data-ttu-id="c509a-106">更改列的数据类型或显示格式</span><span class="sxs-lookup"><span data-stu-id="c509a-106">To change the data type or display format for a column</span></span>  
  
1.  <span data-ttu-id="c509a-107">在模型设计器中，选择要更改数据类型或显示格式的列。</span><span class="sxs-lookup"><span data-stu-id="c509a-107">In the model designer, select the column for which you want to change the data type or display format.</span></span>  
  
2.  <span data-ttu-id="c509a-108">在列 **“属性”** 窗口中，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="c509a-108">In the column **Properties** window, do one of the following:</span></span>  
  
    -   <span data-ttu-id="c509a-109">在 **“数据格式”** 属性中，选择一个不同的数据格式。</span><span class="sxs-lookup"><span data-stu-id="c509a-109">In the **Data Format** property, select a different data format.</span></span>  
  
    -   <span data-ttu-id="c509a-110">在 **“数据类型”** 属性中，选择一个不同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-110">In the **Data Type** property, select a different data type.</span></span>  
  
## <a name="considerations-when-changing-data-types"></a><span data-ttu-id="c509a-111">更改数据类型时的注意事项</span><span class="sxs-lookup"><span data-stu-id="c509a-111">Considerations when Changing Data Types</span></span>  
 <span data-ttu-id="c509a-112">有时您尝试更改列的数据类型或选择数据转换时，可能出现以下错误之一：</span><span class="sxs-lookup"><span data-stu-id="c509a-112">Sometimes when you try to change the data type of a column or select a data conversion, one of the following errors might occur:</span></span>  
  
-   <span data-ttu-id="c509a-113">无法更改数据类型</span><span class="sxs-lookup"><span data-stu-id="c509a-113">Failed to change data type</span></span>  
  
-   <span data-ttu-id="c509a-114">无法更改列数据类型</span><span class="sxs-lookup"><span data-stu-id="c509a-114">Failed to change column data type</span></span>  
  
 <span data-ttu-id="c509a-115">即使数据类型是“数据类型”下拉列表中的可用选项，也可能出现这些错误。</span><span class="sxs-lookup"><span data-stu-id="c509a-115">These errors might occur even if the data type is available as an option in the Data Type dropdown list.</span></span> <span data-ttu-id="c509a-116">本节说明这些错误的原因以及解决方法。</span><span class="sxs-lookup"><span data-stu-id="c509a-116">This section explains the cause of these errors and how you can correct them.</span></span>  
  
### <a name="understanding-automatically-determined-data-types"></a><span data-ttu-id="c509a-117">了解自动确定的数据类型</span><span class="sxs-lookup"><span data-stu-id="c509a-117">Understanding Automatically Determined Data Types</span></span>  
 <span data-ttu-id="c509a-118">将数据添加到模型时，模型设计器检查数据列以查看每个列包含什么数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-118">When you add data to a model, the model designer checks the columns of data to see what data types each column contains.</span></span> <span data-ttu-id="c509a-119">如果列中的数据是一致的，则将最精确的数据类型分配给该列。</span><span class="sxs-lookup"><span data-stu-id="c509a-119">If the data in that column is consistent, is assigns the most precise data type to the column.</span></span>  
  
 <span data-ttu-id="c509a-120">但是，如果从 Excel 或不在每一列中强制使用单一数据类型的其他源添加数据，模型设计器将分配可容纳该列中所有值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-120">However, if you add data from Excel or another source that does not enforce the use of a single data type within each column, the model designer will assign a data type that accommodates all values within the column.</span></span> <span data-ttu-id="c509a-121">因此，如果列包含不同类型的数字（如整数、长型数字和货币），模型设计器将使用小数数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-121">Therefore, if a column contains numbers of different types, such as integers, long numbers, and currency, the model designer will use a decimal data type.</span></span> <span data-ttu-id="c509a-122">如果列包含数字和文本，模型设计器将使用文本数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-122">Alternatively, if a column mixes numbers and text, the model designer will use the text data type.</span></span> <span data-ttu-id="c509a-123">模型设计器不提供与 Excel 中的“常规”数据类型类似的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-123">The model designer does not provide a data type similar to the General data type available in Excel.</span></span>  
  
 <span data-ttu-id="c509a-124">因此，如果列同时包含数字和文本值，将无法将该列转换为数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-124">Therefore, if a column contains both numbers and text values, you will not be able to convert the column to a numeric data type.</span></span>  
  
 <span data-ttu-id="c509a-125">下列数据类型在商业智能语义模型中可用：</span><span class="sxs-lookup"><span data-stu-id="c509a-125">The following data types are available in business intelligence semantic models:</span></span>  
  
|<span data-ttu-id="c509a-126">模型数据类型</span><span class="sxs-lookup"><span data-stu-id="c509a-126">Model data types</span></span>|  
|----------------------|  
|<span data-ttu-id="c509a-127">文本</span><span class="sxs-lookup"><span data-stu-id="c509a-127">Text</span></span><br /><br /> <span data-ttu-id="c509a-128">十进制数</span><span class="sxs-lookup"><span data-stu-id="c509a-128">Decimal Number</span></span><br /><br /> <span data-ttu-id="c509a-129">整数</span><span class="sxs-lookup"><span data-stu-id="c509a-129">Whole Number</span></span><br /><br /> <span data-ttu-id="c509a-130">货币</span><span class="sxs-lookup"><span data-stu-id="c509a-130">Currency</span></span><br /><br /> <span data-ttu-id="c509a-131">TRUE/FALSE</span><span class="sxs-lookup"><span data-stu-id="c509a-131">TRUE/FALSE</span></span><br /><br /> <span data-ttu-id="c509a-132">Date</span><span class="sxs-lookup"><span data-stu-id="c509a-132">Date</span></span>|  
  
 <span data-ttu-id="c509a-133">如果发现数据的数据类型错误或至少与期望的数据类型不同，可以选择以下处理方法：</span><span class="sxs-lookup"><span data-stu-id="c509a-133">If you find that your data has a wrong data type, or at least a different one than you wanted, you have several options:</span></span>  
  
-   <span data-ttu-id="c509a-134">可以重新导入数据。</span><span class="sxs-lookup"><span data-stu-id="c509a-134">You can re-import the data.</span></span> <span data-ttu-id="c509a-135">为此，请打开到数据源的现有连接并重新导入列。</span><span class="sxs-lookup"><span data-stu-id="c509a-135">To do this, open the existing connection to the data source and re-import the column.</span></span> <span data-ttu-id="c509a-136">根据数据源类型，您可能能够在导入过程中应用筛选器来删除问题值。</span><span class="sxs-lookup"><span data-stu-id="c509a-136">Depending on the data source type, you might be able to apply a filter during import to remove problem values.</span></span>  
  
-   <span data-ttu-id="c509a-137">可以在计算列中创建一个 DAX 公式，以创建所需数据类型的新值。</span><span class="sxs-lookup"><span data-stu-id="c509a-137">You can create a DAX formula in a calculated column to create a new value of the desired data type.</span></span> <span data-ttu-id="c509a-138">例如，可以使用 TRUNC 函数将小数更改为整数，或结合使用信息函数和逻辑函数来测试和转换值。</span><span class="sxs-lookup"><span data-stu-id="c509a-138">For example, the TRUNC function can be used to change a decimal number to a whole integer, or you can combine information functions and logical functions to test and convert values.</span></span>  
  
### <a name="understanding-data-conversion"></a><span data-ttu-id="c509a-139">了解数据转换</span><span class="sxs-lookup"><span data-stu-id="c509a-139">Understanding Data Conversion</span></span>  
 <span data-ttu-id="c509a-140">如果在选择数据转换选项时遇到错误，可能是因为列的当前数据类型不支持所选的转换。</span><span class="sxs-lookup"><span data-stu-id="c509a-140">If an error occurs when you select a data conversion option, it might be that the current data type of the column does not support the selected conversion.</span></span> <span data-ttu-id="c509a-141">并非所有转换都适用于所有数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-141">Not all conversions are allowed for all data types.</span></span> <span data-ttu-id="c509a-142">例如，如果列的当前数据类型是数字（整数或小数）或文本，则只能将该列更改为布尔数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-142">For example, you can only change a column to a Boolean data type if the current data type of the column is either a number (whole or decimal) or text.</span></span> <span data-ttu-id="c509a-143">因此，您必须为列中的数据选择适当的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-143">Therefore, you must choose an appropriate data type for the data in the column.</span></span>  
  
 <span data-ttu-id="c509a-144">选择适当的数据类型后，模型设计器将警告您可能对数据进行的更改，如降低精度或截断。</span><span class="sxs-lookup"><span data-stu-id="c509a-144">After you choose an appropriate data type, the model designer will warn you about possible changes to your data, such as loss of precision, or truncation.</span></span> <span data-ttu-id="c509a-145">单击“确定”以接受并将您的数据更改为新数据类型。</span><span class="sxs-lookup"><span data-stu-id="c509a-145">Click OK to accept and change your data to the new data type.</span></span>  
  
 <span data-ttu-id="c509a-146">如果支持该数据类型，但是模型设计器在新数据类型中发现不支持的值，将遇到另一个错误，在继续操作前您需要更正数据值。</span><span class="sxs-lookup"><span data-stu-id="c509a-146">If the data type is supported, but the model designer finds values that are not supported within the new data type, you will get another error, and will need to correct the data values before proceeding.</span></span>  
  
 <span data-ttu-id="c509a-147">有关商业智能语义模型中使用的数据类型、如何隐式转换这些数据类型以及如何在公式中使用不同数据类型的详细信息，请参阅 [支持的数据类型（SSAS 表格）](data-types-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="c509a-147">For detailed information about the data types used in business intelligence semantic models, how they are implicitly converted, and how different data types are used in formulas, see [Data Types Supported &#40;SSAS Tabular&#41;](data-types-supported-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c509a-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c509a-148">See Also</span></span>  
 [<span data-ttu-id="c509a-149">支持的数据类型（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="c509a-149">Data Types Supported &#40;SSAS Tabular&#41;</span></span>](data-types-supported-ssas-tabular.md)  
  
  
