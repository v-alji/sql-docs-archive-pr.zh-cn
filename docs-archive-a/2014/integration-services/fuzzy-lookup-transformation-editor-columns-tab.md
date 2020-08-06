---
title: 模糊查找转换编辑器 (列 "选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.columns.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9294022b52536940916a381d7b811437eaa5814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688028"
---
# <a name="fuzzy-lookup-transformation-editor-columns-tab"></a><span data-ttu-id="e2580-102">模糊查找转换编辑器（“列”选项卡）</span><span class="sxs-lookup"><span data-stu-id="e2580-102">Fuzzy Lookup Transformation Editor (Columns Tab)</span></span>
  <span data-ttu-id="e2580-103">可以使用 **“模糊查找转换编辑器”** 对话框的 **“列”** 选项卡，为输入和输出列设置属性。</span><span class="sxs-lookup"><span data-stu-id="e2580-103">Use the **Columns** tab of the **Fuzzy Lookup Transformation Editor** dialog box to set properties for input and output columns.</span></span>  
  
 <span data-ttu-id="e2580-104">若要了解有关模糊查找转换的详细信息，请参阅 [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="e2580-104">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e2580-105">选项</span><span class="sxs-lookup"><span data-stu-id="e2580-105">Options</span></span>  
 <span data-ttu-id="e2580-106">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="e2580-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="e2580-107">拖动输入列以将其连接到可用查找列。</span><span class="sxs-lookup"><span data-stu-id="e2580-107">Drag input columns to connect them to available lookup columns.</span></span> <span data-ttu-id="e2580-108">这些列必须具有所支持的相互匹配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="e2580-108">These columns must have matching, supported data types.</span></span> <span data-ttu-id="e2580-109">选择一个映射行，再右键单击可在 [创建关系](data-flow/transformations/create-relationships.md) 对话框中编辑该映射。</span><span class="sxs-lookup"><span data-stu-id="e2580-109">Select a mapping line and right-click to edit the mappings in the [Create Relationships](data-flow/transformations/create-relationships.md) dialog box.</span></span>  
  
 <span data-ttu-id="e2580-110">**名称**</span><span class="sxs-lookup"><span data-stu-id="e2580-110">**Name**</span></span>  
 <span data-ttu-id="e2580-111">查看可用输入列的名称。</span><span class="sxs-lookup"><span data-stu-id="e2580-111">View the names of the available input columns.</span></span>  
  
 <span data-ttu-id="e2580-112">**传递**</span><span class="sxs-lookup"><span data-stu-id="e2580-112">**Pass Through**</span></span>  
 <span data-ttu-id="e2580-113">指定是否在转换的输出中包含输入列。</span><span class="sxs-lookup"><span data-stu-id="e2580-113">Specify whether to include the input columns in the output of the transformation.</span></span>  
  
 <span data-ttu-id="e2580-114">**可用查找列**</span><span class="sxs-lookup"><span data-stu-id="e2580-114">**Available Lookup Columns**</span></span>  
 <span data-ttu-id="e2580-115">使用这些复选框可以选择要对其执行模糊查找操作的列。</span><span class="sxs-lookup"><span data-stu-id="e2580-115">Use the check boxes to select columns on which to perform fuzzy lookup operations.</span></span>  
  
 <span data-ttu-id="e2580-116">**查找列**</span><span class="sxs-lookup"><span data-stu-id="e2580-116">**Lookup Column**</span></span>  
 <span data-ttu-id="e2580-117">从引用表的可用列的列表中选择查找列。</span><span class="sxs-lookup"><span data-stu-id="e2580-117">Select lookup columns from the list of available reference table columns.</span></span> <span data-ttu-id="e2580-118">通过选中 **“可用查找列”** 表中的相应复选框即可选择查找列。</span><span class="sxs-lookup"><span data-stu-id="e2580-118">Your selections are reflected in the check box selections in the **Available Lookup Columns** table.</span></span> <span data-ttu-id="e2580-119">选择 **“可用查找列”** 表中的某个列将创建一个输出列，其中包含返回的对应于每个匹配行的引用表列值。</span><span class="sxs-lookup"><span data-stu-id="e2580-119">Selecting a column in the **Available Lookup Columns** table creates an output column that contains the reference table column value for each matching row returned.</span></span>  
  
 <span data-ttu-id="e2580-120">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="e2580-120">**Output Alias**</span></span>  
 <span data-ttu-id="e2580-121">为每个查找列的输出键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="e2580-121">Type an alias for the output for each lookup column.</span></span> <span data-ttu-id="e2580-122">默认值为查找列的名称，并追加一个数字索引值；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="e2580-122">The default is the name of the lookup column with a numeric index value appended; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2580-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2580-123">See Also</span></span>  
 <span data-ttu-id="e2580-124">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e2580-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e2580-125">[模糊查找转换编辑器 &#40;引用表 "选项卡&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="e2580-125">[Fuzzy Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 [<span data-ttu-id="e2580-126">模糊查找转换编辑器（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="e2580-126">Fuzzy Lookup Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
