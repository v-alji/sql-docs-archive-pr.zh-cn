---
title: ADO NET 源编辑器 (错误输出页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.erroroutput.f1
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9ee480caa8764d70b52b25a416f200f353d30c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693031"
---
# <a name="ado-net-source-editor-error-output-page"></a><span data-ttu-id="a6339-102">ADO NET 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="a6339-102">ADO NET Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="a6339-103">可以使用 **“ADO NET 源编辑器”** 对话框的 **“错误输出”** 页，选择错误处理选项以及设置错误输出列的属性。</span><span class="sxs-lookup"><span data-stu-id="a6339-103">Use the **Error Output** page of the **ADO NET Source Editor** dialog box to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="a6339-104">若要了解有关 ADO NET 源的详细信息，请参阅 [ADO NET Source](data-flow/ado-net-source.md)。</span><span class="sxs-lookup"><span data-stu-id="a6339-104">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="a6339-105">**打开“错误输出”页**</span><span class="sxs-lookup"><span data-stu-id="a6339-105">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="a6339-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开具有 ADO NET 源的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="a6339-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="a6339-107">在“数据流”  选项卡上，双击 ADO NET 源。</span><span class="sxs-lookup"><span data-stu-id="a6339-107">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="a6339-108">在 **“ADO NET 源编辑器”** 中，单击 **“错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="a6339-108">In the **ADO NET Source Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a6339-109">选项</span><span class="sxs-lookup"><span data-stu-id="a6339-109">Options</span></span>  
 <span data-ttu-id="a6339-110">**输入/输出**</span><span class="sxs-lookup"><span data-stu-id="a6339-110">**Input/Output**</span></span>  
 <span data-ttu-id="a6339-111">查看数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="a6339-111">View the name of the data source.</span></span>  
  
 <span data-ttu-id="a6339-112">**列**</span><span class="sxs-lookup"><span data-stu-id="a6339-112">**Column**</span></span>  
 <span data-ttu-id="a6339-113">查看在“ADO NET 源编辑器”对话框的“连接管理器”页上选择的外部（源）列   。</span><span class="sxs-lookup"><span data-stu-id="a6339-113">View the external (source) columns that you selected on the **Connection Manager** page of the **ADO NET Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="a6339-114">**错误**</span><span class="sxs-lookup"><span data-stu-id="a6339-114">**Error**</span></span>  
 <span data-ttu-id="a6339-115">指定发生错误时应执行的操作：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="a6339-115">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="a6339-116">**相关主题：** [数据中的错误处理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="a6339-116">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="a6339-117">**截断**</span><span class="sxs-lookup"><span data-stu-id="a6339-117">**Truncation**</span></span>  
 <span data-ttu-id="a6339-118">指定发生截断时应执行的操作：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="a6339-118">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="a6339-119">**说明**</span><span class="sxs-lookup"><span data-stu-id="a6339-119">**Description**</span></span>  
 <span data-ttu-id="a6339-120">查看对错误的说明。</span><span class="sxs-lookup"><span data-stu-id="a6339-120">View the description of the error.</span></span>  
  
 <span data-ttu-id="a6339-121">**将此值设置到选定的单元格**</span><span class="sxs-lookup"><span data-stu-id="a6339-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="a6339-122">指定发生错误或截断时应对所有选定单元格执行的操作：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="a6339-122">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="a6339-123">**应用**</span><span class="sxs-lookup"><span data-stu-id="a6339-123">**Apply**</span></span>  
 <span data-ttu-id="a6339-124">将错误处理选项应用到选定的单元格。</span><span class="sxs-lookup"><span data-stu-id="a6339-124">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6339-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6339-125">See Also</span></span>  
 <span data-ttu-id="a6339-126">[ADO NET 源编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="a6339-126">[ADO NET Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="a6339-127">[ADO NET 源编辑器 &#40;列 "页&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="a6339-127">[ADO NET Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="a6339-128">ADO.NET 连接管理器</span><span class="sxs-lookup"><span data-stu-id="a6339-128">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  
