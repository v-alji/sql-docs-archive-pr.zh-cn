---
title: 平面文件源编辑器 (列 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9b0249b2b17d50fdef4b5cf4aff70a1318614257
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578341"
---
# <a name="flat-file-source-editor-columns-page"></a><span data-ttu-id="d5dc0-102">平面文件源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="d5dc0-102">Flat File Source Editor (Columns Page)</span></span>
  <span data-ttu-id="d5dc0-103">可以使用“平面文件源编辑器”\*\*\*\* 对话框的“列”\*\*\*\* 节点，将输出列映射到每个外部（源）列。</span><span class="sxs-lookup"><span data-stu-id="d5dc0-103">Use the **Columns** node of the **Flat File Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5dc0-104">`FileNameColumnName`平面文件源的属性和 `FastParse` 其输出列的属性在**平面文件源编辑器**中不可用，但可以使用**高级编辑器**进行设置。</span><span class="sxs-lookup"><span data-stu-id="d5dc0-104">The `FileNameColumnName` property of the Flat File source and the `FastParse` property of its output columns are not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="d5dc0-105">有关这些属性的详细信息，请参阅 [Flat File Custom Properties](data-flow/flat-file-custom-properties.md)的“平面文件源”部分。</span><span class="sxs-lookup"><span data-stu-id="d5dc0-105">For more information on these properties, see the Flat File Source section of [Flat File Custom Properties](data-flow/flat-file-custom-properties.md).</span></span>  
  
 <span data-ttu-id="d5dc0-106">若要了解有关平面文件源的详细信息，请参阅 [Flat File Source](data-flow/flat-file-source.md)。</span><span class="sxs-lookup"><span data-stu-id="d5dc0-106">To learn more about the Flat File source, see [Flat File Source](data-flow/flat-file-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d5dc0-107">选项</span><span class="sxs-lookup"><span data-stu-id="d5dc0-107">Options</span></span>  
 <span data-ttu-id="d5dc0-108">**可用外部列**</span><span class="sxs-lookup"><span data-stu-id="d5dc0-108">**Available External Columns**</span></span>  
 <span data-ttu-id="d5dc0-109">查看数据源中可用外部列的列表。</span><span class="sxs-lookup"><span data-stu-id="d5dc0-109">View the list of available external columns in the data source.</span></span> <span data-ttu-id="d5dc0-110">无法使用此表添加或删除列。</span><span class="sxs-lookup"><span data-stu-id="d5dc0-110">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="d5dc0-111">**“外部列”**</span><span class="sxs-lookup"><span data-stu-id="d5dc0-111">**External Column**</span></span>  
 <span data-ttu-id="d5dc0-112">按任务读取外部（源）列的顺序查看这些列。</span><span class="sxs-lookup"><span data-stu-id="d5dc0-112">View external (source) columns in the order in which the task will read them.</span></span> <span data-ttu-id="d5dc0-113">首先清除表中所选的列，然后以不同的顺序从列表中选择外部列，即可更改顺序。</span><span class="sxs-lookup"><span data-stu-id="d5dc0-113">You can change this order by first clearing the selected columns in the table, and then selecting external columns from the list in a different order.</span></span>  
  
 <span data-ttu-id="d5dc0-114">**输出列**</span><span class="sxs-lookup"><span data-stu-id="d5dc0-114">**Output Column**</span></span>  
 <span data-ttu-id="d5dc0-115">为每个输出列提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="d5dc0-115">Provide a unique name for each output column.</span></span> <span data-ttu-id="d5dc0-116">默认值为所选外部（源）列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="d5dc0-116">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="d5dc0-117">所提供的名称将在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="d5dc0-117">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5dc0-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d5dc0-118">See Also</span></span>  
 <span data-ttu-id="d5dc0-119">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d5dc0-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="d5dc0-120">["平面文件源编辑器" &#40;连接管理器页&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="d5dc0-120">[Flat File Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="d5dc0-121">["平面文件源编辑器" &#40;"错误输出" 页&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="d5dc0-121">[Flat File Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="d5dc0-122">平面文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="d5dc0-122">Flat File Connection Manager</span></span>](connection-manager/file-connection-manager.md)  
  
  
