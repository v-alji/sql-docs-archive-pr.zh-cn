---
title: SQL Server，HTTP_STORAGE_OBJECT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62cd5b8422213624cfd8609027c477760f682239
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578828"
---
# <a name="sql-server-http_storage_object"></a><span data-ttu-id="8614d-102">SQL Server，HTTP_STORAGE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="8614d-102">SQL Server, HTTP_STORAGE_OBJECT</span></span>
  <span data-ttu-id="8614d-103">**SQLServer： HTTP_STORAGE_OBJECT**性能对象由监视 Azure 存储帐户的性能计数器组成。</span><span class="sxs-lookup"><span data-stu-id="8614d-103">The **SQLServer:HTTP_STORAGE_OBJECT** performance object consists of performance counters that monitor Azure Storage account.</span></span> <span data-ttu-id="8614d-104">使用[azure 功能中的 SQL Server 数据文件](../databases/sql-server-data-files-in-microsoft-azure.md)，你可以在 Azure 存储 blob 中存储数据库文件。</span><span class="sxs-lookup"><span data-stu-id="8614d-104">Using [SQL Server Data Files in Azure](../databases/sql-server-data-files-in-microsoft-azure.md) feature, you can store database files in Azure Storage Blobs.</span></span> <span data-ttu-id="8614d-105">此性能对象将每一个 Azure 存储帐户都视为不同的驱动器。</span><span class="sxs-lookup"><span data-stu-id="8614d-105">This performance object treats each Azure Storage account as a different drive.</span></span>  
  
|<span data-ttu-id="8614d-106">计数器名称</span><span class="sxs-lookup"><span data-stu-id="8614d-106">Counter Name</span></span>|<span data-ttu-id="8614d-107">说明</span><span class="sxs-lookup"><span data-stu-id="8614d-107">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="8614d-108">**Read Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="8614d-108">**Read Bytes/sec**</span></span>|<span data-ttu-id="8614d-109">读取操作过程中每秒从 HTTP 存储传输的数据量。</span><span class="sxs-lookup"><span data-stu-id="8614d-109">Amount of data being transferred from the HTTP storage per second during read operations.</span></span>|  
|<span data-ttu-id="8614d-110">**Write Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="8614d-110">**Write Bytes/sec**</span></span>|<span data-ttu-id="8614d-111">写入操作过程中每秒从 HTTP 存储传输的数据量。</span><span class="sxs-lookup"><span data-stu-id="8614d-111">Amount of data being transferred from the HTTP storage per second during write operations.</span></span>|  
|<span data-ttu-id="8614d-112">**Total Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="8614d-112">**Total Bytes/sec**</span></span>|<span data-ttu-id="8614d-113">读取或写入操作过程中每秒从 HTTP 存储传输的数据量。</span><span class="sxs-lookup"><span data-stu-id="8614d-113">Amount of data being transferred from the HTTP storage per second during read or write operations.</span></span>|  
|<span data-ttu-id="8614d-114">**读取次数/秒**</span><span class="sxs-lookup"><span data-stu-id="8614d-114">**Reads/sec**</span></span>|<span data-ttu-id="8614d-115">每秒对 HTTP 存储的读取次数。</span><span class="sxs-lookup"><span data-stu-id="8614d-115">Number of reads per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="8614d-116">**写入次数/秒**</span><span class="sxs-lookup"><span data-stu-id="8614d-116">**Writes/sec**</span></span>|<span data-ttu-id="8614d-117">每秒对 HTTP 存储的写入次数。</span><span class="sxs-lookup"><span data-stu-id="8614d-117">Number of writer per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="8614d-118">**Transfers/sec**</span><span class="sxs-lookup"><span data-stu-id="8614d-118">**Transfers/sec**</span></span>|<span data-ttu-id="8614d-119">每秒对 HTTP 存储的读取和写入操作次数。</span><span class="sxs-lookup"><span data-stu-id="8614d-119">Number of read and write operations per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="8614d-120">**页的Bytes/Read**</span><span class="sxs-lookup"><span data-stu-id="8614d-120">**Avg. Bytes/Read**</span></span>|<span data-ttu-id="8614d-121">每次读取从 HTTP 存储传输的平均字节数。</span><span class="sxs-lookup"><span data-stu-id="8614d-121">Average number of bytes transferred from the HTTP storage per read.</span></span>|  
|<span data-ttu-id="8614d-122">**页的Bytes/Write**</span><span class="sxs-lookup"><span data-stu-id="8614d-122">**Avg. Bytes/Write**</span></span>|<span data-ttu-id="8614d-123">每次写入从 HTTP 存储传输的平均字节数。</span><span class="sxs-lookup"><span data-stu-id="8614d-123">Average number of bytes transferred from the HTTP storage per write.</span></span>|  
|<span data-ttu-id="8614d-124">**页的Bytes/Transfer**</span><span class="sxs-lookup"><span data-stu-id="8614d-124">**Avg. Bytes/Transfer**</span></span>|<span data-ttu-id="8614d-125">读取或写入操作过程中从 HTTP 存储传输的平均字节数。</span><span class="sxs-lookup"><span data-stu-id="8614d-125">Average number of bytes transferred from the HTTP storage during read or write operations.</span></span>|  
|<span data-ttu-id="8614d-126">**Avg. microsec/Read**</span><span class="sxs-lookup"><span data-stu-id="8614d-126">**Avg. microsec/Read**</span></span>|<span data-ttu-id="8614d-127">每次从 HTTP 存储读取所用的平均微秒数。</span><span class="sxs-lookup"><span data-stu-id="8614d-127">The average number of microseconds it takes to do each read from the HTTP storage.</span></span>|  
|<span data-ttu-id="8614d-128">**Avg. microsec/Write**</span><span class="sxs-lookup"><span data-stu-id="8614d-128">**Avg. microsec/Write**</span></span>|<span data-ttu-id="8614d-129">每次向 HTTP 存储写入所用的平均微秒数。</span><span class="sxs-lookup"><span data-stu-id="8614d-129">The average number of microseconds it takes to do each write to the HTTP storage.</span></span>|  
|<span data-ttu-id="8614d-130">**Avg. microsec/Transfer**</span><span class="sxs-lookup"><span data-stu-id="8614d-130">**Avg. microsec/Transfer**</span></span>|<span data-ttu-id="8614d-131">每次向 HTTP 存储传输所用的平均微秒数。</span><span class="sxs-lookup"><span data-stu-id="8614d-131">The average number of microseconds it takes to do each transfer to the HTTP storage.</span></span>|  
|<span data-ttu-id="8614d-132">**Outstanding HTTP Storage I/O**</span><span class="sxs-lookup"><span data-stu-id="8614d-132">**Outstanding HTTP Storage I/O**</span></span>|<span data-ttu-id="8614d-133">通往 HTTP 存储的待定 I/O 总数。</span><span class="sxs-lookup"><span data-stu-id="8614d-133">The total number of outstanding I/Os towards a HTTP storage.</span></span>|  
|<span data-ttu-id="8614d-134">**HTTP 存储 i/o 重试次数/秒**</span><span class="sxs-lookup"><span data-stu-id="8614d-134">**HTTP Storage I/O Retry/sec**</span></span>|<span data-ttu-id="8614d-135">每秒发送到 HTTP 存储的重试请求数。</span><span class="sxs-lookup"><span data-stu-id="8614d-135">Number of retry requests sent to the HTTP storage per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8614d-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8614d-136">See Also</span></span>  
 [<span data-ttu-id="8614d-137">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="8614d-137">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
