---
title: ODBC 源编辑器 (列 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.columns.f1
ms.assetid: 565984eb-8318-4be7-bebc-262209cf5065
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a11ab6a86978366d07fbe63362f1702310b5d89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690753"
---
# <a name="odbc-source-editor-columns-page"></a><span data-ttu-id="05490-102">ODBC 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="05490-102">ODBC Source Editor (Columns Page)</span></span>
  <span data-ttu-id="05490-103">可以使用“ODBC 源编辑器”对话框的“列”页，将输出列映射到每个外部（源）列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="05490-103">Use the **Columns** page of the **ODBC Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="05490-104">若要了解有关 ODBC 源的详细信息，请参阅 [ODBC Source](data-flow/odbc-source.md)。</span><span class="sxs-lookup"><span data-stu-id="05490-104">To learn more about the ODBC source, see [ODBC Source](data-flow/odbc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="05490-105">任务列表</span><span class="sxs-lookup"><span data-stu-id="05490-105">Task List</span></span>  
 <span data-ttu-id="05490-106">**打开“ODBC 源编辑器”的“列”页**</span><span class="sxs-lookup"><span data-stu-id="05490-106">**To open the ODBC Source Editor Columns Page**</span></span>  
  
1.  <span data-ttu-id="05490-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，打开具有 ODBC 源的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="05490-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC source.</span></span>  
  
2.  <span data-ttu-id="05490-108">在“数据流”\*\*\*\* 选项卡上，双击 ODBC 源。</span><span class="sxs-lookup"><span data-stu-id="05490-108">On the **Data Flow** tab, double-click the ODBC source.</span></span>  
  
3.  <span data-ttu-id="05490-109">在 **“ODBC 源编辑器”** 中，单击 **“列”**。</span><span class="sxs-lookup"><span data-stu-id="05490-109">In the **ODBC Source Editor**, click **Columns**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="05490-110">选项</span><span class="sxs-lookup"><span data-stu-id="05490-110">Options</span></span>  
  
### <a name="available-external-columns"></a><span data-ttu-id="05490-111">可用外部列</span><span class="sxs-lookup"><span data-stu-id="05490-111">Available External Columns</span></span>  
 <span data-ttu-id="05490-112">数据源中的可用外部列的列表。</span><span class="sxs-lookup"><span data-stu-id="05490-112">A list of available external columns in the data source.</span></span> <span data-ttu-id="05490-113">无法使用此表添加或删除列。</span><span class="sxs-lookup"><span data-stu-id="05490-113">You cannot use this table to add or delete columns.</span></span> <span data-ttu-id="05490-114">从源中选择要使用的列。</span><span class="sxs-lookup"><span data-stu-id="05490-114">Select the columns to use from the source.</span></span> <span data-ttu-id="05490-115">所选列将按照选择它们时的顺序添加到 **“外部列”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="05490-115">The selected columns are added to the **External Column** list in the order they are selected.</span></span>  
  
 <span data-ttu-id="05490-116">选中 **“全选”** 复选框可以选择所有列。</span><span class="sxs-lookup"><span data-stu-id="05490-116">Select the **Select All** check box to select all of the columns.</span></span>  
  
### <a name="external-column"></a><span data-ttu-id="05490-117">外部列</span><span class="sxs-lookup"><span data-stu-id="05490-117">External Column</span></span>  
 <span data-ttu-id="05490-118">外部（源）列的视图，该视图按照您在配置使用 ODBC 源中数据的组件时所看到的列顺序显示。</span><span class="sxs-lookup"><span data-stu-id="05490-118">A view of the external (source) columns in the order that you see them when configuring components that consume data from the ODBC source.</span></span>  
  
### <a name="output-column"></a><span data-ttu-id="05490-119">输出列</span><span class="sxs-lookup"><span data-stu-id="05490-119">Output Column</span></span>  
 <span data-ttu-id="05490-120">输入每个输出列的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="05490-120">Enter a unique name for each output column.</span></span> <span data-ttu-id="05490-121">默认值为所选外部（源）列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="05490-121">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="05490-122">输入的名称显示在 SSIS 设计器中。</span><span class="sxs-lookup"><span data-stu-id="05490-122">The name entered is displayed in the SSIS Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05490-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05490-123">See Also</span></span>  
 <span data-ttu-id="05490-124">[ODBC 源编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="05490-124">[ODBC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="05490-125">ODBC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="05490-125">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
