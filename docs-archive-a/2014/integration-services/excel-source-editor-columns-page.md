---
title: Excel 源编辑器 (列 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsourceadapter.columns.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 50024686-a18d-4824-b20e-c84123f89d0b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0713d8d3d0c1f56bf322684a924a286e8b81af55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587495"
---
# <a name="excel-source-editor-columns-page"></a><span data-ttu-id="00735-102">Excel 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="00735-102">Excel Source Editor (Columns Page)</span></span>
  <span data-ttu-id="00735-103">可以使用“Excel 源编辑器”对话框的“列”页，将输出列映射到每个外部（源）列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00735-103">Use the **Columns** page of the **Excel Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="00735-104">若要了解有关 Excel 源的详细信息，请参阅 [Excel Source](data-flow/excel-source.md)。</span><span class="sxs-lookup"><span data-stu-id="00735-104">To learn more about the Excel source, see [Excel Source](data-flow/excel-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="00735-105">选项</span><span class="sxs-lookup"><span data-stu-id="00735-105">Options</span></span>  
 <span data-ttu-id="00735-106">**可用外部列**</span><span class="sxs-lookup"><span data-stu-id="00735-106">**Available External Columns**</span></span>  
 <span data-ttu-id="00735-107">查看数据源中可用外部列的列表。</span><span class="sxs-lookup"><span data-stu-id="00735-107">View the list of available external columns in the data source.</span></span> <span data-ttu-id="00735-108">无法使用此表添加或删除列。</span><span class="sxs-lookup"><span data-stu-id="00735-108">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="00735-109">**“外部列”**</span><span class="sxs-lookup"><span data-stu-id="00735-109">**External Column**</span></span>  
 <span data-ttu-id="00735-110">按任务读取外部（源）列的顺序查看这些列。</span><span class="sxs-lookup"><span data-stu-id="00735-110">View external (source) columns in the order in which the task will read them.</span></span> <span data-ttu-id="00735-111">首先在上面讨论的表中清除所选择的列，然后以不同的顺序从列表中选择外部列，即可更改顺序。</span><span class="sxs-lookup"><span data-stu-id="00735-111">You can change this order by first clearing the selected columns in the table discussed above, and then selecting external columns from the list in a different order.</span></span>  
  
 <span data-ttu-id="00735-112">**输出列**</span><span class="sxs-lookup"><span data-stu-id="00735-112">**Output Column**</span></span>  
 <span data-ttu-id="00735-113">为每个输出列提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="00735-113">Provide a unique name for each output column.</span></span> <span data-ttu-id="00735-114">默认值为所选外部（源）列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="00735-114">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="00735-115">所提供的名称将在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="00735-115">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00735-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00735-116">See Also</span></span>  
 <span data-ttu-id="00735-117">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="00735-117">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="00735-118">[Excel 源编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="00735-118">[Excel Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="00735-119">[Excel 源编辑器 &#40;错误输出页&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="00735-119">[Excel Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="00735-120">[Excel 连接管理器](connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="00735-120">[Excel Connection Manager](connection-manager/excel-connection-manager.md) </span></span>  
 [<span data-ttu-id="00735-121">使用 Foreach 循环容器循环遍历 Excel 文件和表</span><span class="sxs-lookup"><span data-stu-id="00735-121">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
