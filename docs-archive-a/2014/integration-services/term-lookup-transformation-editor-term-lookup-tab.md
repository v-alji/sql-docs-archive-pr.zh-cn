---
title: 字词查找转换编辑器 (字词查找选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bb8c0bd0477d9883640cc3e4d3cb25c2a3a8b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590907"
---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a><span data-ttu-id="8792b-102">字词查找转换编辑器（“字词查找”选项卡）</span><span class="sxs-lookup"><span data-stu-id="8792b-102">Term Lookup Transformation Editor (Term Lookup Tab)</span></span>
  <span data-ttu-id="8792b-103">可以使用 **“字词查找转换编辑器”** 对话框的 **“字词查找”** 选项卡，将输入列映射到引用表中的查找列，以及为每个输出列提供别名。</span><span class="sxs-lookup"><span data-stu-id="8792b-103">Use the **Term Lookup** tab of the **Term Lookup Transformation Editor** dialog box to map an input column to a lookup column in a reference table and to provide an alias for each output column.</span></span>  
  
 <span data-ttu-id="8792b-104">若要了解有关字词查找转换的详细信息，请参阅 [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="8792b-104">To learn more about the Term Lookup transformation, see [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8792b-105">选项</span><span class="sxs-lookup"><span data-stu-id="8792b-105">Options</span></span>  
 <span data-ttu-id="8792b-106">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="8792b-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="8792b-107">使用复选框选择要传递给未更改输出的输入列。</span><span class="sxs-lookup"><span data-stu-id="8792b-107">Using the check boxes, select input columns to pass through to the output unchanged.</span></span> <span data-ttu-id="8792b-108">将输入列拖动到 **“可用引用列”** 列表可以将其映射到引用表中的查找列。</span><span class="sxs-lookup"><span data-stu-id="8792b-108">Drag an input column to the **Available Reference Columns** list to map it to a lookup column in the reference table.</span></span> <span data-ttu-id="8792b-109">输入列和查找列必须具有支持的匹配数据类型（DT_NTEXT 或 DT_WSTR）。</span><span class="sxs-lookup"><span data-stu-id="8792b-109">The input and lookup columns must have matching, supported data types, either DT_NTEXT or DT_WSTR.</span></span> <span data-ttu-id="8792b-110">选择一个映射行，再右键单击可在 [创建关系](data-flow/transformations/create-relationships.md) 对话框中编辑该映射。</span><span class="sxs-lookup"><span data-stu-id="8792b-110">Select a mapping line and right-click to edit the mappings in the [Create Relationships](data-flow/transformations/create-relationships.md) dialog box.</span></span>  
  
 <span data-ttu-id="8792b-111">**“可用引用列”**</span><span class="sxs-lookup"><span data-stu-id="8792b-111">**Available Reference Columns**</span></span>  
 <span data-ttu-id="8792b-112">查看引用表中可用的列。</span><span class="sxs-lookup"><span data-stu-id="8792b-112">View the available columns in the reference table.</span></span> <span data-ttu-id="8792b-113">选择包含要匹配的字词列表的列。</span><span class="sxs-lookup"><span data-stu-id="8792b-113">Choose the column that contains the list of terms to match.</span></span>  
  
 <span data-ttu-id="8792b-114">**传递列**</span><span class="sxs-lookup"><span data-stu-id="8792b-114">**Pass-Through Column**</span></span>  
 <span data-ttu-id="8792b-115">从可用输入列的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="8792b-115">Select from the list of available input columns.</span></span> <span data-ttu-id="8792b-116">通过选中 **“可用输入列”** 表中的复选框来选择列。</span><span class="sxs-lookup"><span data-stu-id="8792b-116">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="8792b-117">**输出列别名**</span><span class="sxs-lookup"><span data-stu-id="8792b-117">**Output Column Alias**</span></span>  
 <span data-ttu-id="8792b-118">为每个输出列键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="8792b-118">Type an alias for each output column.</span></span> <span data-ttu-id="8792b-119">默认值为列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="8792b-119">The default is the name of the column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="8792b-120">**配置错误输出**</span><span class="sxs-lookup"><span data-stu-id="8792b-120">**Configure Error Output**</span></span>  
 <span data-ttu-id="8792b-121">使用 [配置错误输出](../../2014/integration-services/configure-error-output.md) 对话框可以为导致错误的行指定错误处理方式选项。</span><span class="sxs-lookup"><span data-stu-id="8792b-121">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8792b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8792b-122">See Also</span></span>  
 <span data-ttu-id="8792b-123">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8792b-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="8792b-124">[字词查找转换编辑器 &#40;引用表 "选项卡&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="8792b-124">[Term Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 <span data-ttu-id="8792b-125">[字词查找转换编辑器 &#40;高级 "选项卡&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="8792b-125">[Term Lookup Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="8792b-126">字词提取转换</span><span class="sxs-lookup"><span data-stu-id="8792b-126">Term Extraction Transformation</span></span>](data-flow/transformations/term-extraction-transformation.md)  
  
  
