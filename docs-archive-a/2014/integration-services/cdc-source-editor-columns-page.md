---
title: CDC 源编辑器 (列 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.columns.f1
ms.assetid: bcf3030e-98d8-4445-967c-33c3f8ecb4fc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa30defb5e6873ea05e8e41c733477cf50d0dc4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590327"
---
# <a name="cdc-source-editor-columns-page"></a><span data-ttu-id="f9153-102">CDC 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="f9153-102">CDC Source Editor (Columns Page)</span></span>
  <span data-ttu-id="f9153-103">可以使用“CDC 源编辑器”对话框的“列”页，将输出列映射到每个外部（源）列   。</span><span class="sxs-lookup"><span data-stu-id="f9153-103">Use the **Columns** page of the **CDC Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="f9153-104">若要了解有关 CDC 源的详细信息，请参阅 [CDC Source](data-flow/cdc-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f9153-104">To learn more about the CDC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="f9153-105">任务列表</span><span class="sxs-lookup"><span data-stu-id="f9153-105">Task List</span></span>  
 <span data-ttu-id="f9153-106">**打开“CDC 源编辑器”的“列”页**</span><span class="sxs-lookup"><span data-stu-id="f9153-106">**To open the CDC Source Editor Columns Page**</span></span>  
  
1.  <span data-ttu-id="f9153-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，打开具有 CDC 源的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="f9153-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC source.</span></span>  
  
2.  <span data-ttu-id="f9153-108">在“数据流”  选项卡上，双击 CDC 源。</span><span class="sxs-lookup"><span data-stu-id="f9153-108">On the **Data Flow** tab, double-click the CDC source.</span></span>  
  
3.  <span data-ttu-id="f9153-109">在 **“CDC 源编辑器”** 中，单击 **“列”** 。</span><span class="sxs-lookup"><span data-stu-id="f9153-109">In the **CDC Source Editor**, click **Columns**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f9153-110">选项</span><span class="sxs-lookup"><span data-stu-id="f9153-110">Options</span></span>  
 <span data-ttu-id="f9153-111">**可用外部列**</span><span class="sxs-lookup"><span data-stu-id="f9153-111">**Available External Columns**</span></span>  
 <span data-ttu-id="f9153-112">数据源中的可用外部列的列表。</span><span class="sxs-lookup"><span data-stu-id="f9153-112">A list of available external columns in the data source.</span></span> <span data-ttu-id="f9153-113">无法使用此表添加或删除列。</span><span class="sxs-lookup"><span data-stu-id="f9153-113">You cannot use this table to add or delete columns.</span></span> <span data-ttu-id="f9153-114">在源中选择要使用的列。</span><span class="sxs-lookup"><span data-stu-id="f9153-114">Select the columns to use in the source.</span></span> <span data-ttu-id="f9153-115">所选列将按照选择它们时的顺序添加到 **“外部列”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="f9153-115">The selected columns are added to the **External Column** list in the order they are selected.</span></span>  
  
 <span data-ttu-id="f9153-116">**“外部列”**</span><span class="sxs-lookup"><span data-stu-id="f9153-116">**External Column**</span></span>  
 <span data-ttu-id="f9153-117">外部（源）列的视图，该视图按照您在配置使用 CDC 源中数据的组件时所看到的列顺序显示。</span><span class="sxs-lookup"><span data-stu-id="f9153-117">A view of the external (source) columns in the order that you see them when configuring components that consume data from the CDC source.</span></span> <span data-ttu-id="f9153-118">若要更改此顺序，请首先清除 **“可用外部列”** 列表中所选的列，然后以不同的顺序从列表中选择外部列。</span><span class="sxs-lookup"><span data-stu-id="f9153-118">To change this order, first clear the selected columns in the **Available External Columns** list, and then select external columns from the list in a different order.</span></span> <span data-ttu-id="f9153-119">所选列将按照选择它们时的顺序添加到 **“外部列”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="f9153-119">The selected columns are added to the **External Column** list in the order you select them.</span></span>  
  
 <span data-ttu-id="f9153-120">**输出列**</span><span class="sxs-lookup"><span data-stu-id="f9153-120">**Output Column**</span></span>  
 <span data-ttu-id="f9153-121">输入每个输出列的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="f9153-121">Enter a unique name for each output column.</span></span> <span data-ttu-id="f9153-122">默认值为所选外部（源）列的名称，不过，也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="f9153-122">The default is the name of the selected external (source) column, however you can choose any unique, descriptive name.</span></span> <span data-ttu-id="f9153-123">输入的名称显示在 SSIS 设计器中。</span><span class="sxs-lookup"><span data-stu-id="f9153-123">The name entered is displayed in the SSIS Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9153-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9153-124">See Also</span></span>  
 <span data-ttu-id="f9153-125">[CDC 源编辑器（“连接管理器”页）](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="f9153-125">[CDC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="f9153-126">CDC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="f9153-126">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/cdc-source-editor-error-output-page.md)  
  
  
