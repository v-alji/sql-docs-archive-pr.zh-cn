---
title: 查找转换编辑器 (列 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.columns.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: 690ffef5-fd59-4e95-a27d-4fcf0d6b1c0b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b768076d8acbcaef8cbff21783a7697020e027eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586803"
---
# <a name="lookup-transformation-editor-columns-page"></a><span data-ttu-id="13eb1-102">查找转换编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="13eb1-102">Lookup Transformation Editor (Columns Page)</span></span>
  <span data-ttu-id="13eb1-103">可以使用 **“查找转换编辑器”** 对话框的 **“列”** 页，指定源表与引用表之间的联接以及从引用表中选择查找列。</span><span class="sxs-lookup"><span data-stu-id="13eb1-103">Use the **Columns** page of the **Lookup Transformation Editor** dialog box to specify the join between the source table and the reference table, and to select lookup columns from the reference table.</span></span>  
  
 <span data-ttu-id="13eb1-104">若要了解有关查找转换的详细信息，请参阅 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="13eb1-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="13eb1-105">选项</span><span class="sxs-lookup"><span data-stu-id="13eb1-105">Options</span></span>  
 <span data-ttu-id="13eb1-106">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="13eb1-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="13eb1-107">查看可用输入列的列表。</span><span class="sxs-lookup"><span data-stu-id="13eb1-107">View the list of available input columns.</span></span> <span data-ttu-id="13eb1-108">输入列是所连接源的数据流中的列。</span><span class="sxs-lookup"><span data-stu-id="13eb1-108">The input columns are the columns in the data flow from a connected source.</span></span> <span data-ttu-id="13eb1-109">输入列和查找列必须具有相互匹配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="13eb1-109">The input columns and lookup column must have matching data types.</span></span>  
  
 <span data-ttu-id="13eb1-110">使用拖放操作将可用输入列映射到查找列。</span><span class="sxs-lookup"><span data-stu-id="13eb1-110">Use a drag-and-drop operation to map available input columns to lookup columns.</span></span>  
  
 <span data-ttu-id="13eb1-111">还可以用键盘通过以下方法将输入列映射到查找列：突出显示 **“可用输入列”** 表中的某一列，按应用程序键，然后单击 **“编辑映射”**。</span><span class="sxs-lookup"><span data-stu-id="13eb1-111">You can also map input columns to lookup columns using the keyboard, by highlighting a column in the **Available Input Columns** table, pressing the Application key, and then clicking **Edit Mappings**.</span></span>  
  
 <span data-ttu-id="13eb1-112">**可用查找列**</span><span class="sxs-lookup"><span data-stu-id="13eb1-112">**Available Lookup Columns**</span></span>  
 <span data-ttu-id="13eb1-113">查看查找列的列表。</span><span class="sxs-lookup"><span data-stu-id="13eb1-113">View the list of lookup columns.</span></span> <span data-ttu-id="13eb1-114">查找列是包含在引用表中并可在其中查找与输入列相匹配的值的列。</span><span class="sxs-lookup"><span data-stu-id="13eb1-114">The lookup columns are columns in the reference table in which you want to look up values that match the input columns.</span></span>  
  
 <span data-ttu-id="13eb1-115">使用拖放操作将可用查找列映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="13eb1-115">Use a drag-and-drop operation to map available lookup columns to input columns.</span></span>  
  
 <span data-ttu-id="13eb1-116">使用这些复选框可以在引用表中选择要对其执行查找操作的列。</span><span class="sxs-lookup"><span data-stu-id="13eb1-116">Use the check boxes to select lookup columns in the reference table on which to perform lookup operations.</span></span>  
  
 <span data-ttu-id="13eb1-117">还可以用键盘通过以下方法将查找列映射到输入列：突出显示 **“可用查找列”** 表中的某一列，按应用程序键，然后单击 **“编辑映射”**。</span><span class="sxs-lookup"><span data-stu-id="13eb1-117">You can also map lookup columns to input columns using the keyboard, by highlighting a column in the **Available Lookup Columns** table, pressing the Application key, and then clicking **Edit Mappings**.</span></span>  
  
 <span data-ttu-id="13eb1-118">**查找列**</span><span class="sxs-lookup"><span data-stu-id="13eb1-118">**Lookup Column**</span></span>  
 <span data-ttu-id="13eb1-119">查看所选的查找列。</span><span class="sxs-lookup"><span data-stu-id="13eb1-119">View the selected lookup columns.</span></span> <span data-ttu-id="13eb1-120">通过选中 **“可用查找列”** 表中的复选框即可选择查找列。</span><span class="sxs-lookup"><span data-stu-id="13eb1-120">The selections are reflected in the check box selections in the **Available Lookup Columns** table.</span></span>  
  
 <span data-ttu-id="13eb1-121">**查找操作**</span><span class="sxs-lookup"><span data-stu-id="13eb1-121">**Lookup Operation**</span></span>  
 <span data-ttu-id="13eb1-122">从列表中选择要对查找列执行的查找操作。</span><span class="sxs-lookup"><span data-stu-id="13eb1-122">Select a lookup operation from the list to perform on the lookup column.</span></span>  
  
 <span data-ttu-id="13eb1-123">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="13eb1-123">**Output Alias**</span></span>  
 <span data-ttu-id="13eb1-124">为每个查找列的输出键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="13eb1-124">Type an alias for the output for each lookup column.</span></span> <span data-ttu-id="13eb1-125">默认值为查找列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="13eb1-125">The default is the name of the lookup column; however, you can select any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13eb1-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13eb1-126">See Also</span></span>  
 <span data-ttu-id="13eb1-127">[查找转换编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="13eb1-127">[Lookup Transformation Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="13eb1-128">[查找转换编辑器 &#40;连接页&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="13eb1-128">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="13eb1-129">[查找转换编辑器 &#40;高级页面&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="13eb1-129">[Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="13eb1-130">[查找转换编辑器 &#40;错误输出页&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="13eb1-130">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="13eb1-131">模糊查找转换</span><span class="sxs-lookup"><span data-stu-id="13eb1-131">Fuzzy Lookup Transformation</span></span>](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
