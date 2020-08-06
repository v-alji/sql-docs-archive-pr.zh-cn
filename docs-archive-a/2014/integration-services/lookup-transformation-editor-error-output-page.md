---
title: 查找转换编辑器 (错误输出页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.erroroutput.f1
ms.assetid: 15d53bb0-8be1-46fb-b459-04a397e75fac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9cd78f40a0072f7f0c5c923cdd51431873402f3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586799"
---
# <a name="lookup-transformation-editor-error-output-page"></a><span data-ttu-id="15868-102">查找转换编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="15868-102">Lookup Transformation Editor (Error Output Page)</span></span>
  <span data-ttu-id="15868-103">可以使用 **“查找转换编辑器”** 对话框的 **“错误输出”** 页指定错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="15868-103">Use the **Error Output** page of the **Lookup Transformation Editor** dialog box to specify error handling options.</span></span>  
  
 <span data-ttu-id="15868-104">若要了解有关查找转换的详细信息，请参阅 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="15868-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="15868-105">选项</span><span class="sxs-lookup"><span data-stu-id="15868-105">Options</span></span>  
 <span data-ttu-id="15868-106">**输入/输出**</span><span class="sxs-lookup"><span data-stu-id="15868-106">**Input/Output**</span></span>  
 <span data-ttu-id="15868-107">查看输入的名称。</span><span class="sxs-lookup"><span data-stu-id="15868-107">View the name of the input.</span></span>  
  
 <span data-ttu-id="15868-108">**列**</span><span class="sxs-lookup"><span data-stu-id="15868-108">**Column**</span></span>  
 <span data-ttu-id="15868-109">未使用。</span><span class="sxs-lookup"><span data-stu-id="15868-109">Not used.</span></span>  
  
 <span data-ttu-id="15868-110">**错误**</span><span class="sxs-lookup"><span data-stu-id="15868-110">**Error**</span></span>  
 <span data-ttu-id="15868-111">指定当处理在引用数据集内没有匹配项的行时应当出现的错误类型：</span><span class="sxs-lookup"><span data-stu-id="15868-111">Specify what type of error should occur when handling rows without matching entries in the reference dataset:</span></span>  
  
-   <span data-ttu-id="15868-112">忽略该失败并将行定向到输出。</span><span class="sxs-lookup"><span data-stu-id="15868-112">Ignore the failure and direct the rows to an output.</span></span>  
  
-   <span data-ttu-id="15868-113">将行重定向到错误输出。</span><span class="sxs-lookup"><span data-stu-id="15868-113">Redirect the rows to an error output.</span></span>  
  
-   <span data-ttu-id="15868-114">使组件失败。</span><span class="sxs-lookup"><span data-stu-id="15868-114">Fail the component.</span></span>  
  
 <span data-ttu-id="15868-115">如果您在 **“指定如何处理无匹配项的行** 列表中选中了 **“将行重定向到无匹配输出”** ，则该选项不可用。</span><span class="sxs-lookup"><span data-stu-id="15868-115">This option is not available when you select **Redirect rows to no match output** in the **Specify how to handle rows with no matching entries** list.</span></span> <span data-ttu-id="15868-116">此列表位于 **“查找转换编辑器”** 对话框的 **“常规”** 页上。</span><span class="sxs-lookup"><span data-stu-id="15868-116">This list is on the **General** page of the **Lookup Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="15868-117">**相关主题：** [数据中的错误处理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="15868-117">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="15868-118">**截断**</span><span class="sxs-lookup"><span data-stu-id="15868-118">**Truncation**</span></span>  
 <span data-ttu-id="15868-119">指定在发生数据截断时应当出现的情况：</span><span class="sxs-lookup"><span data-stu-id="15868-119">Specify what should happen when data truncation occurs:</span></span>  
  
-   <span data-ttu-id="15868-120">忽略失败。</span><span class="sxs-lookup"><span data-stu-id="15868-120">Ignore the failure.</span></span>  
  
-   <span data-ttu-id="15868-121">重定向行。</span><span class="sxs-lookup"><span data-stu-id="15868-121">Redirect the row.</span></span>  
  
-   <span data-ttu-id="15868-122">使组件失败。</span><span class="sxs-lookup"><span data-stu-id="15868-122">Fail the component.</span></span>  
  
 <span data-ttu-id="15868-123">**说明**</span><span class="sxs-lookup"><span data-stu-id="15868-123">**Description**</span></span>  
 <span data-ttu-id="15868-124">查看操作的说明。</span><span class="sxs-lookup"><span data-stu-id="15868-124">View the description of the operation.</span></span>  
  
 <span data-ttu-id="15868-125">**将选定的单元格设置为此值**</span><span class="sxs-lookup"><span data-stu-id="15868-125">**Set selected cells to this value**</span></span>  
 <span data-ttu-id="15868-126">指定在发生错误或截断时，选定的所有单元格应当出现的情况：</span><span class="sxs-lookup"><span data-stu-id="15868-126">Specify what should happen to all the selected cells when an error or truncation occurs:</span></span>  
  
-   <span data-ttu-id="15868-127">忽略失败。</span><span class="sxs-lookup"><span data-stu-id="15868-127">Ignore the failure.</span></span>  
  
-   <span data-ttu-id="15868-128">重定向行。</span><span class="sxs-lookup"><span data-stu-id="15868-128">Redirect the row.</span></span>  
  
-   <span data-ttu-id="15868-129">使组件失败。</span><span class="sxs-lookup"><span data-stu-id="15868-129">Fail the component.</span></span>  
  
 <span data-ttu-id="15868-130">**应用**</span><span class="sxs-lookup"><span data-stu-id="15868-130">**Apply**</span></span>  
 <span data-ttu-id="15868-131">将错误处理选项应用到选定的单元格。</span><span class="sxs-lookup"><span data-stu-id="15868-131">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15868-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15868-132">See Also</span></span>  
 [<span data-ttu-id="15868-133">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="15868-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
