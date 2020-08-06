---
title: max full-text crawl range 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e1dbd9e44518b6e849a06a76e21fc605172fd2ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683054"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a><span data-ttu-id="c6a38-102">max full-text crawl range 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="c6a38-102">max full-text crawl range Server Configuration Option</span></span>
  <span data-ttu-id="c6a38-103">使用 **max full-text crawl range** 选项可以优化 CPU 使用率，从而提高完全爬网时的爬网性能。</span><span class="sxs-lookup"><span data-stu-id="c6a38-103">Use the **max full-text crawl range** option to optimize CPU utilization, which improves crawl performance during a full crawl.</span></span> <span data-ttu-id="c6a38-104">使用此选项，可以指定索引完全爬网时 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的分区数。</span><span class="sxs-lookup"><span data-stu-id="c6a38-104">Using this option, you can specify the number of partitions that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should use during a full index crawl.</span></span> <span data-ttu-id="c6a38-105">例如，如果有许多 CPU 且它们的使用率并非最佳，则可以增加此选项的最大值。</span><span class="sxs-lookup"><span data-stu-id="c6a38-105">For example, if there are many CPUs and their utilization is not optimal, you can increase the maximum value of this option.</span></span> <span data-ttu-id="c6a38-106">除了此选项以外， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 还使用众多其他因素（如表中的行数和 CPU 数）来确定应该使用的实际分区数。</span><span class="sxs-lookup"><span data-stu-id="c6a38-106">In addition to this option, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses a number of other factors, such as the number of rows in the table and the number of CPUs, to determine the actual number of partitions used.</span></span>  
  
 <span data-ttu-id="c6a38-107">此选项的默认值是 4；最小值是 1，最大值是 256。</span><span class="sxs-lookup"><span data-stu-id="c6a38-107">The default value of this option is 4; the minimum value is 1, and the maximum value is 256.</span></span> <span data-ttu-id="c6a38-108">对此选项所做的更改只会影响后续的爬网。</span><span class="sxs-lookup"><span data-stu-id="c6a38-108">Changes made to this option affect only subsequent crawls.</span></span> <span data-ttu-id="c6a38-109">不会影响正在进行的爬网。</span><span class="sxs-lookup"><span data-stu-id="c6a38-109">Crawls in process will not be affected by a change in this option setting.</span></span>  
  
 <span data-ttu-id="c6a38-110">**max full-text crawl range** 选项是一个高级选项。</span><span class="sxs-lookup"><span data-stu-id="c6a38-110">The **max full-text crawl range** option is an advanced option.</span></span> <span data-ttu-id="c6a38-111">如果使用 **sp_configure** 系统存储过程来更改该设置，则仅当 **显示高级选项** 设置为 1 时才能更改 **max full-text crawl range** （全文爬网最大范围）。</span><span class="sxs-lookup"><span data-stu-id="c6a38-111">If you are using the **sp_configure** system stored procedure to change the setting, you can change **max full-text crawl range** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="c6a38-112">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="c6a38-112">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a38-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6a38-113">See Also</span></span>  
 <span data-ttu-id="c6a38-114">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c6a38-114">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="c6a38-115">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c6a38-115">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="c6a38-116">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c6a38-116">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
