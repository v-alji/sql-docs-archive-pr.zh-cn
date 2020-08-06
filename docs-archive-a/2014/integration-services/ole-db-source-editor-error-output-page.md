---
title: OLE DB 源编辑器 (错误输出页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.errorhandling.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: 7737c6ae-c16b-4856-aa6e-5882640093b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ded87747f041a4d8451048d4ef4671b029125873
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590288"
---
# <a name="ole-db-source-editor-error-output-page"></a><span data-ttu-id="354ea-102">OLE DB 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="354ea-102">OLE DB Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="354ea-103">可以使用 **“OLE DB 源编辑器”** 对话框的 **“错误输出”** 页选择错误处理选项以及设置错误输出列的属性。</span><span class="sxs-lookup"><span data-stu-id="354ea-103">Use the **Error Output** page of the **OLE DB Source Editor** dialog box to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="354ea-104">若要了解有关 OLE DB 源的详细信息，请参阅 [OLE DB Source](data-flow/ole-db-source.md)。</span><span class="sxs-lookup"><span data-stu-id="354ea-104">To learn more about the OLE DB source, see [OLE DB Source](data-flow/ole-db-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="354ea-105">选项</span><span class="sxs-lookup"><span data-stu-id="354ea-105">Options</span></span>  
 <span data-ttu-id="354ea-106">**输入/输出**</span><span class="sxs-lookup"><span data-stu-id="354ea-106">**Input/Output**</span></span>  
 <span data-ttu-id="354ea-107">查看数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="354ea-107">View the name of the data source.</span></span>  
  
 <span data-ttu-id="354ea-108">**列**</span><span class="sxs-lookup"><span data-stu-id="354ea-108">**Column**</span></span>  
 <span data-ttu-id="354ea-109">查看在“OLE DB 源编辑器”对话框中“连接管理器”页上选择的外部（源）列。</span><span class="sxs-lookup"><span data-stu-id="354ea-109">View the external (source) columns that you selected on the **Connection Manager** page of the **OLE DB Source Editor**dialog box.</span></span>  
  
 <span data-ttu-id="354ea-110">**错误**</span><span class="sxs-lookup"><span data-stu-id="354ea-110">**Error**</span></span>  
 <span data-ttu-id="354ea-111">指定发生错误时应执行的操作：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="354ea-111">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="354ea-112">**相关主题：** [数据中的错误处理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="354ea-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="354ea-113">**截断**</span><span class="sxs-lookup"><span data-stu-id="354ea-113">**Truncation**</span></span>  
 <span data-ttu-id="354ea-114">指定发生截断时应执行的操作：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="354ea-114">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="354ea-115">**说明**</span><span class="sxs-lookup"><span data-stu-id="354ea-115">**Description**</span></span>  
 <span data-ttu-id="354ea-116">查看对错误的说明。</span><span class="sxs-lookup"><span data-stu-id="354ea-116">View the description of the error.</span></span>  
  
 <span data-ttu-id="354ea-117">**将此值设置到选定的单元格**</span><span class="sxs-lookup"><span data-stu-id="354ea-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="354ea-118">指定发生错误或截断时应对所有选定单元格执行的操作：忽略失败、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="354ea-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="354ea-119">**应用**</span><span class="sxs-lookup"><span data-stu-id="354ea-119">**Apply**</span></span>  
 <span data-ttu-id="354ea-120">将错误处理选项应用到选定的单元格。</span><span class="sxs-lookup"><span data-stu-id="354ea-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="354ea-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="354ea-121">See Also</span></span>  
 <span data-ttu-id="354ea-122">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="354ea-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="354ea-123">[OLE DB 源编辑器 &#40;"连接管理器" 页&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="354ea-123">[OLE DB Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="354ea-124">[OLE DB 源编辑器 &#40;列 "页&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="354ea-124">[OLE DB Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="354ea-125">[使用 OLE DB 源提取数据](data-flow/extract-data-by-using-the-ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="354ea-125">[Extract Data by Using the OLE DB Source](data-flow/extract-data-by-using-the-ole-db-source.md) </span></span>  
 [<span data-ttu-id="354ea-126">OLE DB 连接管理器</span><span class="sxs-lookup"><span data-stu-id="354ea-126">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
