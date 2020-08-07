---
title: ODBC 目标编辑器 (错误输出页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.errorhandling.f1
ms.assetid: 0a743f8d-2a51-4296-9976-8104f5ca22d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 475a2e00d67b221ddf05fdd273317fbab5248cd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690755"
---
# <a name="odbc-destination-editor-error-output-page"></a><span data-ttu-id="c96cb-102">ODBC 目标编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="c96cb-102">ODBC Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="c96cb-103">可以使用 **“ODBC 目标编辑器”** 对话框的 **“错误输出”** 页选择错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="c96cb-103">Use the **Error Output** page of the **ODBC Destination Editor** dialog box to select error handling options.</span></span>  
  
 <span data-ttu-id="c96cb-104">若要了解有关 ODBC 目标的详细信息，请参阅 [ODBC Destination](data-flow/odbc-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="c96cb-104">To learn more about the ODBC destination, see [ODBC Destination](data-flow/odbc-destination.md).</span></span>  
  
 <span data-ttu-id="c96cb-105">**打开 ODBC 目标编辑器的“错误输出”页**</span><span class="sxs-lookup"><span data-stu-id="c96cb-105">**To open the ODBC Destination Editor Error Output Page**</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="c96cb-106">任务列表</span><span class="sxs-lookup"><span data-stu-id="c96cb-106">Task List</span></span>  
  
-   <span data-ttu-id="c96cb-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，打开包含 ODBC 目标的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="c96cb-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC destination.</span></span>  
  
-   <span data-ttu-id="c96cb-108">在“数据流”  选项卡上，双击 ODBC 目标。</span><span class="sxs-lookup"><span data-stu-id="c96cb-108">On the **Data Flow** tab, double-click the ODBC destination.</span></span>  
  
-   <span data-ttu-id="c96cb-109">在 **“ODBC 目标编辑器”** 中，单击 **“错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="c96cb-109">In the **ODBC Destination Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c96cb-110">选项</span><span class="sxs-lookup"><span data-stu-id="c96cb-110">Options</span></span>  
  
### <a name="inputoutput"></a><span data-ttu-id="c96cb-111">输入/输出</span><span class="sxs-lookup"><span data-stu-id="c96cb-111">Input/Output</span></span>  
 <span data-ttu-id="c96cb-112">查看数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="c96cb-112">View the name of the data source.</span></span>  
  
### <a name="column"></a><span data-ttu-id="c96cb-113">列</span><span class="sxs-lookup"><span data-stu-id="c96cb-113">Column</span></span>  
 <span data-ttu-id="c96cb-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="c96cb-114">Not used.</span></span>  
  
### <a name="error"></a><span data-ttu-id="c96cb-115">错误</span><span class="sxs-lookup"><span data-stu-id="c96cb-115">Error</span></span>  
 <span data-ttu-id="c96cb-116">选择 ODBC 目标应该如何处理流中的错误：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="c96cb-116">Select how the ODBC destination should handle errors in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="truncation"></a><span data-ttu-id="c96cb-117">截断</span><span class="sxs-lookup"><span data-stu-id="c96cb-117">Truncation</span></span>  
 <span data-ttu-id="c96cb-118">选择 ODBC 目标应该如何处理流中的截断：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="c96cb-118">Select how the ODBC destination should handle truncation in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="description"></a><span data-ttu-id="c96cb-119">说明</span><span class="sxs-lookup"><span data-stu-id="c96cb-119">Description</span></span>  
 <span data-ttu-id="c96cb-120">查看错误说明。</span><span class="sxs-lookup"><span data-stu-id="c96cb-120">View a description of the error.</span></span>  
  
### <a name="set-this-value-to-selected-cells"></a><span data-ttu-id="c96cb-121">将此值设置到选定的单元格</span><span class="sxs-lookup"><span data-stu-id="c96cb-121">Set this value to selected cells</span></span>  
 <span data-ttu-id="c96cb-122">选择发生错误或截断时 ODBC 目标应如何处理所有选定的单元格：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="c96cb-122">Select how the ODBC destination handles all selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="apply"></a><span data-ttu-id="c96cb-123">应用</span><span class="sxs-lookup"><span data-stu-id="c96cb-123">Apply</span></span>  
 <span data-ttu-id="c96cb-124">将错误处理选项应用到选定的单元格。</span><span class="sxs-lookup"><span data-stu-id="c96cb-124">Apply the error handling options to the selected cells.</span></span>  
  
## <a name="error-handling-options"></a><span data-ttu-id="c96cb-125">错误处理选项</span><span class="sxs-lookup"><span data-stu-id="c96cb-125">Error Handling Options</span></span>  
 <span data-ttu-id="c96cb-126">使用下列选项来配置 ODBC 目标处理错误和截断的方式。</span><span class="sxs-lookup"><span data-stu-id="c96cb-126">You use the following options to configure how the ODBC destination handles errors and truncations.</span></span>  
  
### <a name="fail-component"></a><span data-ttu-id="c96cb-127">组件失败</span><span class="sxs-lookup"><span data-stu-id="c96cb-127">Fail Component</span></span>  
 <span data-ttu-id="c96cb-128">发生错误或截断时数据流任务失败。</span><span class="sxs-lookup"><span data-stu-id="c96cb-128">The Data Flow task fails when an error or a truncation occurs.</span></span> <span data-ttu-id="c96cb-129">此选项为默认行为。</span><span class="sxs-lookup"><span data-stu-id="c96cb-129">This is the default behavior.</span></span>  
  
### <a name="ignore-failure"></a><span data-ttu-id="c96cb-130">忽略失败</span><span class="sxs-lookup"><span data-stu-id="c96cb-130">Ignore Failure</span></span>  
 <span data-ttu-id="c96cb-131">忽略错误或截断。</span><span class="sxs-lookup"><span data-stu-id="c96cb-131">The error or the truncation is ignored.</span></span>  
  
### <a name="redirect-flow"></a><span data-ttu-id="c96cb-132">重定向流</span><span class="sxs-lookup"><span data-stu-id="c96cb-132">Redirect Flow</span></span>  
 <span data-ttu-id="c96cb-133">将引起错误或截断的行定向到 ODBC 目标的错误输出。</span><span class="sxs-lookup"><span data-stu-id="c96cb-133">The row that is causing the error or the truncation is directed to the error output of the ODBC destination.</span></span> <span data-ttu-id="c96cb-134">有关详细信息，请参阅 ODBC 目标。</span><span class="sxs-lookup"><span data-stu-id="c96cb-134">For more information, see ODBC Destination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96cb-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c96cb-135">See Also</span></span>  
 <span data-ttu-id="c96cb-136">[ODBC 目标编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/odbc-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="c96cb-136">[ODBC Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/odbc-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="c96cb-137">ODBC 目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="c96cb-137">ODBC Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/odbc-destination-editor-mappings-page.md)  
  
  
