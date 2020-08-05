---
title: OLE DB 源编辑器 (的 "列" 页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.columns.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: bfbb0ae1-7759-4d45-8865-31df36ae5b34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 575a5a02198606d2412ff187750963ccb171e338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578951"
---
# <a name="ole-db-source-editor-columns-page"></a><span data-ttu-id="97a73-102">OLE DB 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="97a73-102">OLE DB Source Editor (Columns Page)</span></span>
  <span data-ttu-id="97a73-103">可以使用“OLE DB 源编辑器”对话框的“列”页，将输出列映射到每个外部（源）列   。</span><span class="sxs-lookup"><span data-stu-id="97a73-103">Use the **Columns** page of the **OLE DB Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="97a73-104">若要了解有关 OLE DB 源的详细信息，请参阅 [OLE DB Source](data-flow/ole-db-source.md)。</span><span class="sxs-lookup"><span data-stu-id="97a73-104">To learn more about the OLE DB source, see [OLE DB Source](data-flow/ole-db-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="97a73-105">选项</span><span class="sxs-lookup"><span data-stu-id="97a73-105">Options</span></span>  
 <span data-ttu-id="97a73-106">**可用外部列**</span><span class="sxs-lookup"><span data-stu-id="97a73-106">**Available External Columns**</span></span>  
 <span data-ttu-id="97a73-107">查看数据源中可用外部列的列表。</span><span class="sxs-lookup"><span data-stu-id="97a73-107">View the list of available external columns in the data source.</span></span> <span data-ttu-id="97a73-108">无法使用此表添加或删除列。</span><span class="sxs-lookup"><span data-stu-id="97a73-108">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="97a73-109">**“外部列”**</span><span class="sxs-lookup"><span data-stu-id="97a73-109">**External Column**</span></span>  
 <span data-ttu-id="97a73-110">按照外部（源）列在您配置使用此源中数据的组件时的显示顺序，查看外部（源）列。</span><span class="sxs-lookup"><span data-stu-id="97a73-110">View external (source) columns in the order in which you will see them when configuring components that consume data from this source.</span></span> <span data-ttu-id="97a73-111">首先清除表中所选的列，然后以不同的顺序从列表中选择外部列，即可更改顺序。</span><span class="sxs-lookup"><span data-stu-id="97a73-111">You can change this order by first clearing the selected columns in the table, and then selecting external columns from the list in a different order.</span></span>  
  
 <span data-ttu-id="97a73-112">**输出列**</span><span class="sxs-lookup"><span data-stu-id="97a73-112">**Output Column**</span></span>  
 <span data-ttu-id="97a73-113">为每个输出列提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="97a73-113">Provide a unique name for each output column.</span></span> <span data-ttu-id="97a73-114">默认值为所选外部（源）列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="97a73-114">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="97a73-115">所提供的名称将在 SSIS 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="97a73-115">The name provided will be displayed within the SSIS Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a73-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97a73-116">See Also</span></span>  
 <span data-ttu-id="97a73-117">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="97a73-117">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="97a73-118">[OLE DB 源编辑器 &#40;"连接管理器" 页&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="97a73-118">[OLE DB Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="97a73-119">[OLE DB 源编辑器 &#40;错误输出页&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="97a73-119">[OLE DB Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="97a73-120">[使用 OLE DB 源提取数据](data-flow/extract-data-by-using-the-ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="97a73-120">[Extract Data by Using the OLE DB Source](data-flow/extract-data-by-using-the-ole-db-source.md) </span></span>  
 [<span data-ttu-id="97a73-121">OLE DB 连接管理器</span><span class="sxs-lookup"><span data-stu-id="97a73-121">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
