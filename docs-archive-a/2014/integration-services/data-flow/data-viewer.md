---
title: 数据查看器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataviewer.f1
helpviewer_keywords:
- Data Viewer dialog box
ms.assetid: 6351309a-688f-4e82-9697-1712130f10a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dc576981e875eade84dd3576f4ed93b66784411f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587520"
---
# <a name="data-viewer"></a><span data-ttu-id="f590d-102">数据查看器</span><span class="sxs-lookup"><span data-stu-id="f590d-102">Data Viewer</span></span>
  <span data-ttu-id="f590d-103">如果将路径配置为使用数据查看器，当数据在两个数据流组件之间移动时，数据查看器将依次显示各个缓冲区的数据。</span><span class="sxs-lookup"><span data-stu-id="f590d-103">If a path is configured to use a data viewer, the Data Viewer displays the data buffer by buffer as data moves between two data flow components.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f590d-104">选项</span><span class="sxs-lookup"><span data-stu-id="f590d-104">Options</span></span>  
 <span data-ttu-id="f590d-105">**绿色箭头**</span><span class="sxs-lookup"><span data-stu-id="f590d-105">**Green arrow**</span></span>  
 <span data-ttu-id="f590d-106">单击此项可显示下一个缓冲区中的数据。</span><span class="sxs-lookup"><span data-stu-id="f590d-106">Click to display the data in the next buffer.</span></span> <span data-ttu-id="f590d-107">如果数据可以在单个缓冲区中移动，此选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="f590d-107">If the data can be moved in a single buffer, this option is not available.</span></span>  
  
 <span data-ttu-id="f590d-108">**分离**</span><span class="sxs-lookup"><span data-stu-id="f590d-108">**Detach**</span></span>  
 <span data-ttu-id="f590d-109">分离数据查看器。</span><span class="sxs-lookup"><span data-stu-id="f590d-109">Detach the data viewer.</span></span>  
  
 <span data-ttu-id="f590d-110">**注意** 分离数据查看器并不会删除数据查看器。</span><span class="sxs-lookup"><span data-stu-id="f590d-110">**Note** Detaching a data viewer does not delete the data viewer.</span></span> <span data-ttu-id="f590d-111">在分离数据查看器后，数据可继续通过路径流动，但查看器中的数据将不会更新以匹配每个缓冲区中的数据。</span><span class="sxs-lookup"><span data-stu-id="f590d-111">If the data viewer has been detached, data continues to flow through the path, but the data in the viewer is not updated to match the data in each buffer.</span></span>  
  
 <span data-ttu-id="f590d-112">**附加**</span><span class="sxs-lookup"><span data-stu-id="f590d-112">**Attach**</span></span>  
 <span data-ttu-id="f590d-113">附加数据查看器。</span><span class="sxs-lookup"><span data-stu-id="f590d-113">Attach a data viewer.</span></span>  
  
 <span data-ttu-id="f590d-114">**注意** 数据查看器在附加后会显示数据流的每个缓冲区中的信息，然后暂停。</span><span class="sxs-lookup"><span data-stu-id="f590d-114">**Note** When the data viewer is attached, it displays information from each buffer in the data flow and then pauses.</span></span> <span data-ttu-id="f590d-115">您可以通过使用绿色箭头依次显示各缓冲区的信息。</span><span class="sxs-lookup"><span data-stu-id="f590d-115">You can advance through the buffers by using the green arrow.</span></span>  
  
 <span data-ttu-id="f590d-116">**复制数据**</span><span class="sxs-lookup"><span data-stu-id="f590d-116">**Copy Data**</span></span>  
 <span data-ttu-id="f590d-117">将当前缓冲区中的数据复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="f590d-117">Copy data in the current buffer to the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f590d-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f590d-118">See Also</span></span>  
 [<span data-ttu-id="f590d-119">调试数据流</span><span class="sxs-lookup"><span data-stu-id="f590d-119">Debugging Data Flow</span></span>](../troubleshooting/debugging-data-flow.md)  
  
  
