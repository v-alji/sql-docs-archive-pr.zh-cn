---
title: CDC 源编辑器 (错误输出页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.errorhandling.f1
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b39532304fddfa90fabe8cafe2a6caf5b1fb5c8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590326"
---
# <a name="cdc-source-editor-error-output-page"></a><span data-ttu-id="469e6-102">CDC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="469e6-102">CDC Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="469e6-103">可以使用 **“CDC 源编辑器”** 对话框的 **“错误输出”** 页选择错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="469e6-103">Use the **Error Output** page of the **CDC Source Editor** dialog box to select error handling options.</span></span>  
  
 <span data-ttu-id="469e6-104">若要了解有关 CDC 源的详细信息，请参阅 [CDC Source](data-flow/cdc-source.md)。</span><span class="sxs-lookup"><span data-stu-id="469e6-104">To learn more about the CDC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="469e6-105">任务列表</span><span class="sxs-lookup"><span data-stu-id="469e6-105">Task List</span></span>  
 <span data-ttu-id="469e6-106">**打开“CDC 源编辑器”的“错误输出”页**</span><span class="sxs-lookup"><span data-stu-id="469e6-106">**To open the CDC Source Editor Error Output Page**</span></span>  
  
1.  <span data-ttu-id="469e6-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，打开具有 CDC 源的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="469e6-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC source.</span></span>  
  
2.  <span data-ttu-id="469e6-108">在“数据流”  选项卡上，双击 CDC 源。</span><span class="sxs-lookup"><span data-stu-id="469e6-108">On the **Data Flow** tab, double-click the CDC source.</span></span>  
  
3.  <span data-ttu-id="469e6-109">在 **“CDC 源编辑器”** 中，单击 **“错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="469e6-109">In the **CDC Source Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="469e6-110">选项</span><span class="sxs-lookup"><span data-stu-id="469e6-110">Options</span></span>  
 <span data-ttu-id="469e6-111">**输入/输出**</span><span class="sxs-lookup"><span data-stu-id="469e6-111">**Input/Output**</span></span>  
 <span data-ttu-id="469e6-112">查看数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="469e6-112">View the name of the data source.</span></span>  
  
 <span data-ttu-id="469e6-113">**列**</span><span class="sxs-lookup"><span data-stu-id="469e6-113">**Column**</span></span>  
 <span data-ttu-id="469e6-114">查看在“CDC 源编辑器”对话框中“连接管理器”页上选择的外部（源）列。</span><span class="sxs-lookup"><span data-stu-id="469e6-114">View the external (source) columns that you selected on the **Connection Manager** page of the **CDC Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="469e6-115">**错误**</span><span class="sxs-lookup"><span data-stu-id="469e6-115">**Error**</span></span>  
 <span data-ttu-id="469e6-116">选择 CDC 源应该如何处理流中的错误：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="469e6-116">Select how the CDC source should handle errors in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="469e6-117">**截断**</span><span class="sxs-lookup"><span data-stu-id="469e6-117">**Truncation**</span></span>  
 <span data-ttu-id="469e6-118">选择 CDC 源应该如何处理流中的截断：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="469e6-118">Select how the CDC source should handle truncation in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="469e6-119">**说明**</span><span class="sxs-lookup"><span data-stu-id="469e6-119">**Description**</span></span>  
 <span data-ttu-id="469e6-120">未使用。</span><span class="sxs-lookup"><span data-stu-id="469e6-120">Not used.</span></span>  
  
 <span data-ttu-id="469e6-121">**将此值设置到选定的单元格**</span><span class="sxs-lookup"><span data-stu-id="469e6-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="469e6-122">选择发生错误或截断时 CDC 源应如何处理所有选定的单元格：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="469e6-122">Select how the CDC source handles all selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="469e6-123">**应用**</span><span class="sxs-lookup"><span data-stu-id="469e6-123">**Apply**</span></span>  
 <span data-ttu-id="469e6-124">将错误处理选项应用到选定的单元格。</span><span class="sxs-lookup"><span data-stu-id="469e6-124">Apply the error handling options to the selected cells.</span></span>  
  
## <a name="error-handling-options"></a><span data-ttu-id="469e6-125">错误处理选项</span><span class="sxs-lookup"><span data-stu-id="469e6-125">Error Handling Options</span></span>  
 <span data-ttu-id="469e6-126">使用下列选项来配置 CDC 源处理错误和截断的方式。</span><span class="sxs-lookup"><span data-stu-id="469e6-126">You use the following options to configure how the CDC source handles errors and truncations.</span></span>  
  
 <span data-ttu-id="469e6-127">**组件失败**</span><span class="sxs-lookup"><span data-stu-id="469e6-127">**Fail Component**</span></span>  
 <span data-ttu-id="469e6-128">发生错误或截断时数据流任务失败。</span><span class="sxs-lookup"><span data-stu-id="469e6-128">The Data Flow task fails when an error or a truncation occurs.</span></span> <span data-ttu-id="469e6-129">此选项为默认行为。</span><span class="sxs-lookup"><span data-stu-id="469e6-129">This is the default behavior.</span></span>  
  
 <span data-ttu-id="469e6-130">**忽略失败**</span><span class="sxs-lookup"><span data-stu-id="469e6-130">**Ignore Failure**</span></span>  
 <span data-ttu-id="469e6-131">忽略错误或截断，并且将数据行定向到 CDC 源输出。</span><span class="sxs-lookup"><span data-stu-id="469e6-131">The error or the truncation is ignored and the data row is directed to the CDC source output.</span></span>  
  
 <span data-ttu-id="469e6-132">**重定向流**</span><span class="sxs-lookup"><span data-stu-id="469e6-132">**Redirect Flow**</span></span>  
 <span data-ttu-id="469e6-133">错误或截断数据行定向到 CDC 源的错误输出。</span><span class="sxs-lookup"><span data-stu-id="469e6-133">The error or the truncation data row is directed to the error output of the CDC source.</span></span> <span data-ttu-id="469e6-134">在此情况下使用 CDC 源错误处理。</span><span class="sxs-lookup"><span data-stu-id="469e6-134">In this case the CDC source error handling is used.</span></span> <span data-ttu-id="469e6-135">有关详细信息，请参阅 [CDC Source](data-flow/cdc-source.md)。</span><span class="sxs-lookup"><span data-stu-id="469e6-135">For more information, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469e6-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="469e6-136">See Also</span></span>  
 <span data-ttu-id="469e6-137">[CDC 源编辑器（“连接管理器”页）](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="469e6-137">[CDC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="469e6-138">CDC 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="469e6-138">CDC Source Editor &#40;Columns Page&#41;</span></span>](../../2014/integration-services/cdc-source-editor-columns-page.md)  
  
  
