---
title: ADO NET 源编辑器 (列 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.columns.f1
ms.assetid: fbc205b9-2001-4737-a76b-1ba777344bd9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d89f8c926761b9149f19269bc2519c12bcf130e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586933"
---
# <a name="ado-net-source-editor-columns-page"></a><span data-ttu-id="a67eb-102">ADO NET 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="a67eb-102">ADO NET Source Editor (Columns Page)</span></span>
  <span data-ttu-id="a67eb-103">可以使用“ADO NET 源编辑器”  对话框的“列”  页，将输出列映射到每个外部（源）列。</span><span class="sxs-lookup"><span data-stu-id="a67eb-103">Use the **Columns** page of the **ADO NET Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="a67eb-104">若要了解有关 ADO NET 源的详细信息，请参阅 [ADO NET Source](data-flow/ado-net-source.md)。</span><span class="sxs-lookup"><span data-stu-id="a67eb-104">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="a67eb-105">**打开“列”页**</span><span class="sxs-lookup"><span data-stu-id="a67eb-105">**To open the Columns page**</span></span>  
  
1.  <span data-ttu-id="a67eb-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开具有 ADO NET 源的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="a67eb-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="a67eb-107">在“数据流”  选项卡上，双击 ADO NET 源。</span><span class="sxs-lookup"><span data-stu-id="a67eb-107">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="a67eb-108">在 **“ADO NET 源编辑器”** 中，单击 **“列”** 。</span><span class="sxs-lookup"><span data-stu-id="a67eb-108">In the **ADO NET Source Editor**, click **Columns**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a67eb-109">选项</span><span class="sxs-lookup"><span data-stu-id="a67eb-109">Options</span></span>  
 <span data-ttu-id="a67eb-110">**可用外部列**</span><span class="sxs-lookup"><span data-stu-id="a67eb-110">**Available External Columns**</span></span>  
 <span data-ttu-id="a67eb-111">查看数据源中可用外部列的列表。</span><span class="sxs-lookup"><span data-stu-id="a67eb-111">View the list of available external columns in the data source.</span></span> <span data-ttu-id="a67eb-112">无法使用此表添加或删除列。</span><span class="sxs-lookup"><span data-stu-id="a67eb-112">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="a67eb-113">**“外部列”**</span><span class="sxs-lookup"><span data-stu-id="a67eb-113">**External Column**</span></span>  
 <span data-ttu-id="a67eb-114">按照外部（源）列在您配置使用此源中数据的组件时的显示顺序，查看外部（源）列。</span><span class="sxs-lookup"><span data-stu-id="a67eb-114">View external (source) columns in the order in which you will see them when configuring components that consume data from this source.</span></span>  
  
 <span data-ttu-id="a67eb-115">**输出列**</span><span class="sxs-lookup"><span data-stu-id="a67eb-115">**Output Column**</span></span>  
 <span data-ttu-id="a67eb-116">为每个输出列提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="a67eb-116">Provide a unique name for each output column.</span></span> <span data-ttu-id="a67eb-117">默认值为所选外部（源）列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="a67eb-117">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="a67eb-118">所提供的名称将显示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中。</span><span class="sxs-lookup"><span data-stu-id="a67eb-118">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a67eb-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a67eb-119">See Also</span></span>  
 <span data-ttu-id="a67eb-120">[ADO NET 源编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="a67eb-120">[ADO NET Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="a67eb-121">[ADO NET 源编辑器 &#40;错误输出页&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="a67eb-121">[ADO NET Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="a67eb-122">ADO.NET 连接管理器</span><span class="sxs-lookup"><span data-stu-id="a67eb-122">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  
