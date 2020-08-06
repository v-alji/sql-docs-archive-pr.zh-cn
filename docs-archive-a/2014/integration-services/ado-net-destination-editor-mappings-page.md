---
title: ADO NET 目标编辑器 (映射 "页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.mappings.f1
ms.assetid: 842d075f-8b7a-457c-a1a1-a7acbe10e9b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7e7a2397e4e2d16e6eeca93d41f5127dfde4c35e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576943"
---
# <a name="ado-net-destination-editor-mappings-page"></a><span data-ttu-id="46d70-102">ADO NET 目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="46d70-102">ADO NET Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="46d70-103">可以使用 **“ADO NET 目标编辑器”** 对话框的 **“映射”** 页，将输入列映射到目标列。</span><span class="sxs-lookup"><span data-stu-id="46d70-103">Use the **Mappings** page of the **ADO NET Destination Editor** dialog box to map input columns to destination columns.</span></span>  
  
 <span data-ttu-id="46d70-104">若要了解有关 ADO NET 目标的详细信息，请参阅 [ADO NET Destination](data-flow/ado-net-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="46d70-104">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="46d70-105">**打开“映射”页**</span><span class="sxs-lookup"><span data-stu-id="46d70-105">**To open the Mappings page**</span></span>  
  
1.  <span data-ttu-id="46d70-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开具有 ADO NET 目标的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="46d70-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="46d70-107">在“数据流”  选项卡上，双击 ADO NET 目标。</span><span class="sxs-lookup"><span data-stu-id="46d70-107">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="46d70-108">在 **“ADO NET 目标编辑器”** 中，单击 **“映射”** 。</span><span class="sxs-lookup"><span data-stu-id="46d70-108">In the **ADO NET Destination Editor**, click **Mappings**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="46d70-109">选项</span><span class="sxs-lookup"><span data-stu-id="46d70-109">Options</span></span>  
 <span data-ttu-id="46d70-110">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="46d70-110">**Available Input Columns**</span></span>  
 <span data-ttu-id="46d70-111">查看可用输入列的列表。</span><span class="sxs-lookup"><span data-stu-id="46d70-111">View the list of available input columns.</span></span> <span data-ttu-id="46d70-112">使用拖放操作可以将表中的可用输入列映射到目标列。</span><span class="sxs-lookup"><span data-stu-id="46d70-112">Use a drag-and-drop operation to map available input columns in the table to destination columns.</span></span>  
  
 <span data-ttu-id="46d70-113">**可用目标列**</span><span class="sxs-lookup"><span data-stu-id="46d70-113">**Available Destination Columns**</span></span>  
 <span data-ttu-id="46d70-114">查看可用目标列的列表。</span><span class="sxs-lookup"><span data-stu-id="46d70-114">View the list of available destination columns.</span></span> <span data-ttu-id="46d70-115">使用拖放操作可以将表中的可用目标列映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="46d70-115">Use a drag-and-drop operation to map available destination columns in the table to input columns.</span></span>  
  
 <span data-ttu-id="46d70-116">**输入列**</span><span class="sxs-lookup"><span data-stu-id="46d70-116">**Input Column**</span></span>  
 <span data-ttu-id="46d70-117">查看选定的输入列。</span><span class="sxs-lookup"><span data-stu-id="46d70-117">View the input columns that you selected.</span></span> <span data-ttu-id="46d70-118">可以通过选择 \<ignore> 以从输出中排除列来移除映射。</span><span class="sxs-lookup"><span data-stu-id="46d70-118">You can remove mappings by selecting **\<ignore>** to exclude columns from the output.</span></span>  
  
 <span data-ttu-id="46d70-119">**目标列**</span><span class="sxs-lookup"><span data-stu-id="46d70-119">**Destination Column**</span></span>  
 <span data-ttu-id="46d70-120">查看每个可用目标列，而不管是否已对其进行映射。</span><span class="sxs-lookup"><span data-stu-id="46d70-120">View each available destination column, regardless of whether it is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d70-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46d70-121">See Also</span></span>  
 <span data-ttu-id="46d70-122">[ADO NET 目标编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="46d70-122">[ADO NET Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="46d70-123">ADO NET 目标编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="46d70-123">ADO NET Destination Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/ado-net-destination-editor-error-output-page.md)  
  
  
