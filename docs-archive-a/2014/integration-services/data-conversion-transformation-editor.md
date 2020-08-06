---
title: 数据转换编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- Data Conversion Transformation Editor
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4b893f04dcca2dd2a1a5874b55c1c1c608aaeb12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694075"
---
# <a name="data-conversion-transformation-editor"></a><span data-ttu-id="8b0be-102">数据转换编辑器</span><span class="sxs-lookup"><span data-stu-id="8b0be-102">Data Conversion Transformation Editor</span></span>
  <span data-ttu-id="8b0be-103">可以使用 **“数据转换编辑器”** 对话框，选择要转换的列和要将列转换成的数据类型以及设置转换属性。</span><span class="sxs-lookup"><span data-stu-id="8b0be-103">Use the **Data Conversion Transformation Editor** dialog box to select the columns to convert, select the data type to which the column is converted, and set conversion attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8b0be-104">数据转换的 `FastParse` 输出列的属性在 "**数据转换编辑器**" 中不可用，但可以使用**高级编辑器**进行设置。</span><span class="sxs-lookup"><span data-stu-id="8b0be-104">The `FastParse` property of the output columns of the Data Conversion transformation is not available in the **Data Conversion Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="8b0be-105">有关此属性的详细信息，请参阅 [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)的“数据转换”部分。</span><span class="sxs-lookup"><span data-stu-id="8b0be-105">For more information on this property, see the Data Conversion Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="8b0be-106">若要了解有关数据转换的详细信息，请参阅 [Data Conversion Transformation](data-flow/transformations/data-conversion-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="8b0be-106">To learn more about the Data Conversion transformation, see [Data Conversion Transformation](data-flow/transformations/data-conversion-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8b0be-107">选项</span><span class="sxs-lookup"><span data-stu-id="8b0be-107">Options</span></span>  
 <span data-ttu-id="8b0be-108">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="8b0be-108">**Available Input Columns**</span></span>  
 <span data-ttu-id="8b0be-109">使用复选框选择要转换的列。</span><span class="sxs-lookup"><span data-stu-id="8b0be-109">Select columns to convert by using the check boxes.</span></span> <span data-ttu-id="8b0be-110">选择后，会将输入列添加到下表中。</span><span class="sxs-lookup"><span data-stu-id="8b0be-110">Your selections add input columns to the table below.</span></span>  
  
 <span data-ttu-id="8b0be-111">**输入列**</span><span class="sxs-lookup"><span data-stu-id="8b0be-111">**Input Column**</span></span>  
 <span data-ttu-id="8b0be-112">从可用输入列的列表中选择要转换的列。</span><span class="sxs-lookup"><span data-stu-id="8b0be-112">Select columns to convert from the list of available input columns.</span></span> <span data-ttu-id="8b0be-113">通过选中上述相应的复选框即可选择输入列。</span><span class="sxs-lookup"><span data-stu-id="8b0be-113">Your selections are reflected in the check box selections above.</span></span>  
  
 <span data-ttu-id="8b0be-114">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="8b0be-114">**Output Alias**</span></span>  
 <span data-ttu-id="8b0be-115">为每一个新列键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="8b0be-115">Type an alias for each new column.</span></span> <span data-ttu-id="8b0be-116">默认为 `Copy of` 后接输入列名。不过，你也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="8b0be-116">The default is `Copy of` followed by the input column name; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="8b0be-117">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="8b0be-117">**Data Type**</span></span>  
 <span data-ttu-id="8b0be-118">从列表中选择可用的数据类型。</span><span class="sxs-lookup"><span data-stu-id="8b0be-118">Select an available data type from the list.</span></span> <span data-ttu-id="8b0be-119">有关详细信息，请参阅 [Integration Services 数据类型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="8b0be-119">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="8b0be-120">**长度**</span><span class="sxs-lookup"><span data-stu-id="8b0be-120">**Length**</span></span>  
 <span data-ttu-id="8b0be-121">设置字符串数据的列长度。</span><span class="sxs-lookup"><span data-stu-id="8b0be-121">Set the column length for string data.</span></span>  
  
 <span data-ttu-id="8b0be-122">**精度**</span><span class="sxs-lookup"><span data-stu-id="8b0be-122">**Precision**</span></span>  
 <span data-ttu-id="8b0be-123">设置数字数据的精度。</span><span class="sxs-lookup"><span data-stu-id="8b0be-123">Set the precision for numeric data.</span></span>  
  
 <span data-ttu-id="8b0be-124">**缩放**</span><span class="sxs-lookup"><span data-stu-id="8b0be-124">**Scale**</span></span>  
 <span data-ttu-id="8b0be-125">设置数字数据的小数位数。</span><span class="sxs-lookup"><span data-stu-id="8b0be-125">Set the scale for numeric data.</span></span>  
  
 <span data-ttu-id="8b0be-126">**代码页**</span><span class="sxs-lookup"><span data-stu-id="8b0be-126">**Code page**</span></span>  
 <span data-ttu-id="8b0be-127">为 DT_STR 类型的列选择相应的代码页。</span><span class="sxs-lookup"><span data-stu-id="8b0be-127">Select the appropriate code page for columns of type DT_STR.</span></span>  
  
 <span data-ttu-id="8b0be-128">**配置错误输出**</span><span class="sxs-lookup"><span data-stu-id="8b0be-128">**Configure error output**</span></span>  
 <span data-ttu-id="8b0be-129">使用 [配置错误输出](../../2014/integration-services/configure-error-output.md) 对话框指定处理行级错误的方式。</span><span class="sxs-lookup"><span data-stu-id="8b0be-129">Specify how to handle row-level errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b0be-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b0be-130">See Also</span></span>  
 <span data-ttu-id="8b0be-131">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8b0be-131">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="8b0be-132">使用数据转换将数据转换为其他数据类型</span><span class="sxs-lookup"><span data-stu-id="8b0be-132">Convert Data to a Different Data Type by Using the Data Conversion Transformation</span></span>](data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  
