---
title: PH timeout 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 515ed74a4b92259d53770bf6d970626eba686453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688200"
---
# <a name="ph-timeout-server-configuration-option"></a><span data-ttu-id="4411f-102">PH timeout 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="4411f-102">PH timeout Server Configuration Option</span></span>
  <span data-ttu-id="4411f-103">使用 PH timeout 选项可以指定全文协议处理程序在超时前等待连接到数据库的时间（秒）。默认值为 60 秒。</span><span class="sxs-lookup"><span data-stu-id="4411f-103">Use the PH timeout option to specify the time, in seconds, that the full-text protocol handler should wait to connect to a database before timing out. The default value is 60 seconds.</span></span> <span data-ttu-id="4411f-104">如果连接尝试因临时的网络问题而超时，可以增加 ph timeout 值。</span><span class="sxs-lookup"><span data-stu-id="4411f-104">Increase the ph timeout value when connection attempts are timing out due to temporary network issues.</span></span>  
  
 <span data-ttu-id="4411f-105">全文协议处理程序宿主在筛选器后台程序宿主中，用于从 SQL Server 中提取要进行全文索引的数据。</span><span class="sxs-lookup"><span data-stu-id="4411f-105">The full-text protocol handler is hosted in the filter daemon host and is used to fetch from SQL Server the data to be full-text indexed.</span></span> <span data-ttu-id="4411f-106">有关全文搜索组件的详细信息，请参阅 [全文搜索](../../relational-databases/search/full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="4411f-106">For more information about full-text search components, see [Full-Text Search](../../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="4411f-107">尝试提取数据行时，如果协议处理程序无法在指定时间内连接到 SQL Server，它将为该行报告超时错误。</span><span class="sxs-lookup"><span data-stu-id="4411f-107">When attempting to fetch a data row, if the protocol handler cannot connect to SQL Server within the specified time, it reports a time-out error for that row.</span></span> <span data-ttu-id="4411f-108">全文收集器稍后将重试该行。</span><span class="sxs-lookup"><span data-stu-id="4411f-108">The full-text gatherer will retry the row later.</span></span> <span data-ttu-id="4411f-109">有关全文收集器的详细信息，请参阅 [填充全文索引](../../relational-databases/indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="4411f-109">For more information about the full-text gatherer, see [Populate Full-Text Indexes](../../relational-databases/indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4411f-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4411f-110">See Also</span></span>  
 <span data-ttu-id="4411f-111">[全文搜索](../../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="4411f-111">[Full-Text Search](../../relational-databases/search/full-text-search.md) </span></span>  
 <span data-ttu-id="4411f-112">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4411f-112">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="4411f-113">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4411f-113">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="4411f-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4411f-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
