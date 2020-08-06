---
title: ADO NET 目标编辑器 (错误输出页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.erroroutput.f1
ms.assetid: 1a56c3cf-fb6a-416d-a62c-bb19fe441ae5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9cfd69d3adec2aa617f5e9d3add35a1a6923804
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586934"
---
# <a name="ado-net-destination-editor-error-output-page"></a><span data-ttu-id="09b59-102">ADO NET 目标编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="09b59-102">ADO NET Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="09b59-103">可以使用 **“ADO NET 目标编辑器”** 对话框的 **“错误输出”** 页指定错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="09b59-103">Use the **Error Output** page of the **ADO NET Destination Editor** dialog box to specify error handling options.</span></span>  
  
 <span data-ttu-id="09b59-104">若要了解有关 ADO NET 目标的详细信息，请参阅 [ADO NET Destination](data-flow/ado-net-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="09b59-104">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="09b59-105">**打开“错误输出”页**</span><span class="sxs-lookup"><span data-stu-id="09b59-105">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="09b59-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开具有 ADO NET 目标的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="09b59-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="09b59-107">在“数据流”  选项卡上，双击 ADO NET 目标。</span><span class="sxs-lookup"><span data-stu-id="09b59-107">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="09b59-108">在 **“ADO NET 目标编辑器”** 中，单击 **“错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="09b59-108">In the **ADO NET Destination Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="09b59-109">选项</span><span class="sxs-lookup"><span data-stu-id="09b59-109">Options</span></span>  
 <span data-ttu-id="09b59-110">**输入或输出**</span><span class="sxs-lookup"><span data-stu-id="09b59-110">**Input or Output**</span></span>  
 <span data-ttu-id="09b59-111">查看输入的名称。</span><span class="sxs-lookup"><span data-stu-id="09b59-111">View the name of the input.</span></span>  
  
 <span data-ttu-id="09b59-112">**列**</span><span class="sxs-lookup"><span data-stu-id="09b59-112">**Column**</span></span>  
 <span data-ttu-id="09b59-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="09b59-113">Not used.</span></span>  
  
 <span data-ttu-id="09b59-114">**错误**</span><span class="sxs-lookup"><span data-stu-id="09b59-114">**Error**</span></span>  
 <span data-ttu-id="09b59-115">指定发生错误时应执行的操作：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="09b59-115">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="09b59-116">**相关主题：** [数据中的错误处理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="09b59-116">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="09b59-117">**截断**</span><span class="sxs-lookup"><span data-stu-id="09b59-117">**Truncation**</span></span>  
 <span data-ttu-id="09b59-118">未使用。</span><span class="sxs-lookup"><span data-stu-id="09b59-118">Not used.</span></span>  
  
 <span data-ttu-id="09b59-119">**说明**</span><span class="sxs-lookup"><span data-stu-id="09b59-119">**Description**</span></span>  
 <span data-ttu-id="09b59-120">查看操作的说明。</span><span class="sxs-lookup"><span data-stu-id="09b59-120">View the description of the operation.</span></span>  
  
 <span data-ttu-id="09b59-121">**将此值设置到选定的单元格**</span><span class="sxs-lookup"><span data-stu-id="09b59-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="09b59-122">指定发生错误或截断时应对所有选定单元格执行的操作：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="09b59-122">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="09b59-123">**应用**</span><span class="sxs-lookup"><span data-stu-id="09b59-123">**Apply**</span></span>  
 <span data-ttu-id="09b59-124">将错误处理选项应用到选定的单元格。</span><span class="sxs-lookup"><span data-stu-id="09b59-124">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b59-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09b59-125">See Also</span></span>  
 <span data-ttu-id="09b59-126">[ADO NET 目标编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="09b59-126">[ADO NET Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="09b59-127">ADO NET 目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="09b59-127">ADO NET Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/ado-net-destination-editor-mappings-page.md)  
  
  
