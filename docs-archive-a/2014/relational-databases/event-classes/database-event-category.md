---
title: “数据库”事件类别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2860e1434611393c941a639280343f736073c709
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588536"
---
# <a name="database-event-category"></a><span data-ttu-id="dec32-102">Database 事件类别</span><span class="sxs-lookup"><span data-stu-id="dec32-102">Database Event Category</span></span>
  <span data-ttu-id="dec32-103">**Database** 事件类别包含用于监视 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的事件类。</span><span class="sxs-lookup"><span data-stu-id="dec32-103">The **Database** event category contains event classes to monitor the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dec32-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="dec32-104">In This Section</span></span>  
  
|<span data-ttu-id="dec32-105">主题</span><span class="sxs-lookup"><span data-stu-id="dec32-105">Topic</span></span>|<span data-ttu-id="dec32-106">说明</span><span class="sxs-lookup"><span data-stu-id="dec32-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dec32-107">Data File Auto Grow 事件类</span><span class="sxs-lookup"><span data-stu-id="dec32-107">Data File Auto Grow Event Class</span></span>](data-file-auto-grow-event-class.md)|<span data-ttu-id="dec32-108">指示数据文件是自动增长的。</span><span class="sxs-lookup"><span data-stu-id="dec32-108">Indicates that the data file grew automatically.</span></span> <span data-ttu-id="dec32-109">如果数据文件通过 ALTER DATABASE 而显式增长，则不触发此事件。</span><span class="sxs-lookup"><span data-stu-id="dec32-109">This event is not triggered if the data file is grown explicitly through ALTER DATABASE.</span></span>|  
|[<span data-ttu-id="dec32-110">Data File Auto Shrink 事件类</span><span class="sxs-lookup"><span data-stu-id="dec32-110">Data File Auto Shrink Event Class</span></span>](data-file-auto-shrink-event-class.md)|<span data-ttu-id="dec32-111">指示数据文件已收缩。</span><span class="sxs-lookup"><span data-stu-id="dec32-111">Indicates that the data file has been shrunk.</span></span>|  
|[<span data-ttu-id="dec32-112">Database Mirroring Connection 事件类</span><span class="sxs-lookup"><span data-stu-id="dec32-112">Database Mirroring Connection Event Class</span></span>](database-mirroring-connection-event-class.md)|<span data-ttu-id="dec32-113">为报告数据库镜像的传输连接的状态而生成的事件。</span><span class="sxs-lookup"><span data-stu-id="dec32-113">An event generated to report the status of a transport connection for database mirroring.</span></span>|  
|[<span data-ttu-id="dec32-114">Database Mirroring State Change 事件类</span><span class="sxs-lookup"><span data-stu-id="dec32-114">Database Mirroring State Change Event Class</span></span>](database-mirroring-state-change-event-class.md)|<span data-ttu-id="dec32-115">指示镜像数据库状态更改的时间。</span><span class="sxs-lookup"><span data-stu-id="dec32-115">Indicates when the state of a mirrored database changes.</span></span>|  
|[<span data-ttu-id="dec32-116">Database Suspect Data Page 事件类</span><span class="sxs-lookup"><span data-stu-id="dec32-116">Database Suspect Data Page Event Class</span></span>](database-suspect-data-page-event-class.md)|<span data-ttu-id="dec32-117">指示何时将某页添加到 **msdb** 数据库中的 **suspect_pages** 表。</span><span class="sxs-lookup"><span data-stu-id="dec32-117">Indicates when a page is added to the **suspect_pages** table in the **msdb** database.</span></span>|  
|[<span data-ttu-id="dec32-118">Log File Auto Grow 事件类</span><span class="sxs-lookup"><span data-stu-id="dec32-118">Log File Auto Grow Event Class</span></span>](log-file-auto-grow-event-class.md)|<span data-ttu-id="dec32-119">指示日志文件是自动增长的。</span><span class="sxs-lookup"><span data-stu-id="dec32-119">Indicates that the log file grew automatically.</span></span> <span data-ttu-id="dec32-120">如果通过 ALTER DATABASE 使日志文件显式增长，则不会触发此事件。</span><span class="sxs-lookup"><span data-stu-id="dec32-120">This event is not triggered if the log file is grown explicitly through ALTER DATABASE.</span></span>|  
|[<span data-ttu-id="dec32-121">Log File Auto Shrink 事件类</span><span class="sxs-lookup"><span data-stu-id="dec32-121">Log File Auto Shrink Event Class</span></span>](log-file-auto-shrink-event-class.md)|<span data-ttu-id="dec32-122">指示日志文件是自动增长的。</span><span class="sxs-lookup"><span data-stu-id="dec32-122">Indicates that the log file grew automatically.</span></span> <span data-ttu-id="dec32-123">如果日志文件通过 ALTER DATABASE 而显式收缩，则不触发此事件。</span><span class="sxs-lookup"><span data-stu-id="dec32-123">This event is not triggered if the log file shrinks explicitly through ALTER DATABASE.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dec32-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dec32-124">See Also</span></span>  
 [<span data-ttu-id="dec32-125">扩展事件</span><span class="sxs-lookup"><span data-stu-id="dec32-125">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
