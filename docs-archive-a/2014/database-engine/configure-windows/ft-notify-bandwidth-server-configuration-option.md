---
title: ft notify bandwidth 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dc5839f699d55edf86c5e3e3f0eb001089a0a5dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692531"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a><span data-ttu-id="07dd3-102">ft notify bandwidth 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="07dd3-102">ft notify bandwidth Server Configuration Option</span></span>
  <span data-ttu-id="07dd3-103">使用 **ft notify bandwidth** 选项可以指定小内存缓冲区的池可以增长到的大小。</span><span class="sxs-lookup"><span data-stu-id="07dd3-103">Use the **ft notify bandwidth** option to specify the size to which the pool of small memory buffers can grow.</span></span> <span data-ttu-id="07dd3-104">小内存缓冲区的大小为 64 千字节 (KB)。</span><span class="sxs-lookup"><span data-stu-id="07dd3-104">Small memory buffers are 64 kilobytes (KB) in size.</span></span> <span data-ttu-id="07dd3-105">*max* 参数值指定全文内存管理器在小缓冲池中应该维护的最大缓冲区数。</span><span class="sxs-lookup"><span data-stu-id="07dd3-105">The *max* parameter value specifies the maximum number of buffers that the full-text memory manager should maintain in a small buffer pool.</span></span> <span data-ttu-id="07dd3-106">如果 `max` 值为零，则较小缓冲池中的缓冲区数没有上限值。</span><span class="sxs-lookup"><span data-stu-id="07dd3-106">If the `max` value is zero, then there is no upper limit to the number of buffers that can be in a small buffer pool.</span></span>  
  
 <span data-ttu-id="07dd3-107">**min** 参数指定在小内存缓冲区的池中必须维护的最小内存缓冲区数。</span><span class="sxs-lookup"><span data-stu-id="07dd3-107">The **min** parameter specifies the minimum number of memory buffers that must be maintained in the pool of small memory buffers.</span></span> <span data-ttu-id="07dd3-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存管理器发出请求后，将释放所有额外的缓冲池，但将保留该最低数量的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="07dd3-108">Upon request from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory manager, all extra buffer pools will be released but this minimum number of buffers will be maintained.</span></span> <span data-ttu-id="07dd3-109">不过，如果指定的 **min** 值为零，则释放所有内存缓冲区。</span><span class="sxs-lookup"><span data-stu-id="07dd3-109">If, however, the **min** value specified is zero, then all memory buffers are released.</span></span>  
  
 <span data-ttu-id="07dd3-110">在某些情况下，当前分配的缓冲区数小于 **min** 参数指定的值。</span><span class="sxs-lookup"><span data-stu-id="07dd3-110">Under certain circumstances the number of buffers currently allocated is less than the value specified by the **min** parameter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="07dd3-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07dd3-111">See Also</span></span>  
 <span data-ttu-id="07dd3-112">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="07dd3-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="07dd3-113">[ft crawl bandwidth 服务器配置选项](ft-crawl-bandwidth-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="07dd3-113">[ft crawl bandwidth Server Configuration Option](ft-crawl-bandwidth-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="07dd3-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="07dd3-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
