---
title: ft crawl bandwidth 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- large memory buffers
- memory [SQL Server], buffers
- ft crawl bandwidth option
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33821ff1fdbc4248c71906d8307a8164a7f64d24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693457"
---
# <a name="ft-crawl-bandwidth-server-configuration-option"></a><span data-ttu-id="9dfd2-102">ft crawl bandwidth 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="9dfd2-102">ft crawl bandwidth Server Configuration Option</span></span>
  <span data-ttu-id="9dfd2-103">使用 **ft crawl bandwidth** 选项可指定较大内存缓冲池可增长到多大。</span><span class="sxs-lookup"><span data-stu-id="9dfd2-103">Use the **ft crawl bandwidth** option to specify the size to which the pool of large memory buffers can grow.</span></span> <span data-ttu-id="9dfd2-104">较大内存缓冲区的大小为 4 MB。</span><span class="sxs-lookup"><span data-stu-id="9dfd2-104">Large memory buffers are 4 megabytes (MB) in size.</span></span> <span data-ttu-id="9dfd2-105">**max** 参数值可指定全文内存管理器应在较大缓冲池中保持的最大缓冲区数。</span><span class="sxs-lookup"><span data-stu-id="9dfd2-105">The **max** parameter value specifies the maximum number of buffers that the full-text memory manager should maintain in a large buffer pool.</span></span> <span data-ttu-id="9dfd2-106">如果 **max** 的值为零，则较大缓冲池中可以保持的缓冲区数没有上限。</span><span class="sxs-lookup"><span data-stu-id="9dfd2-106">If the **max** value is zero, then there is no upper limit to the number of buffers that can be in a large buffer pool.</span></span>  
  
 <span data-ttu-id="9dfd2-107">**min** 参数可指定较大内存缓冲池中必须保持的最小内存缓冲区数。</span><span class="sxs-lookup"><span data-stu-id="9dfd2-107">The **min** parameter specifies the minimum number of memory buffers that must be maintained in the pool of large memory buffers.</span></span> <span data-ttu-id="9dfd2-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存管理器发出请求后，将释放所有额外的缓冲池，但将保留该最低数量的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9dfd2-108">Upon request from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory manager, all extra buffer pools will be released but this minimum number of buffers will be maintained.</span></span> <span data-ttu-id="9dfd2-109">不过，如果指定的 **min** 值为零，则释放所有内存缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9dfd2-109">If, however, the **min** value specified is zero, then all memory buffers are released.</span></span>  
  
 <span data-ttu-id="9dfd2-110">在某些情况下，当前分配的缓冲区数会小于 **min** 参数指定的值。</span><span class="sxs-lookup"><span data-stu-id="9dfd2-110">Under certain circumstances, the number of buffers currently allocated is less than the value specified by the **min** parameter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9dfd2-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9dfd2-111">See Also</span></span>  
 <span data-ttu-id="9dfd2-112">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9dfd2-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="9dfd2-113">[ft notify bandwidth 服务器配置选项](ft-notify-bandwidth-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="9dfd2-113">[ft notify bandwidth Server Configuration Option](ft-notify-bandwidth-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="9dfd2-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9dfd2-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
