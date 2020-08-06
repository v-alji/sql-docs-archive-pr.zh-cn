---
title: “服务器触发器递归”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 23a4997bd1a6f8b2c04af34d5cdc3229575901a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693083"
---
# <a name="server-trigger-recursion-server-configuration-option"></a><span data-ttu-id="ad6fb-102">server trigger recursion 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="ad6fb-102">server trigger recursion Server Configuration Option</span></span>
  <span data-ttu-id="ad6fb-103">使用 **server trigger recursion** 选项可指定是否允许服务器级触发器递归激发。</span><span class="sxs-lookup"><span data-stu-id="ad6fb-103">Use the **server trigger recursion** option to specify whether to allow server-level triggers to fire recursively.</span></span> <span data-ttu-id="ad6fb-104">当此选项设置为 1 (ON) 时，将允许服务器级触发器递归激发。</span><span class="sxs-lookup"><span data-stu-id="ad6fb-104">When this option is set to 1 (ON), server-level triggers will be allowed to fire recursively.</span></span> <span data-ttu-id="ad6fb-105">当设置为 0 (OFF) 时，服务器级触发器不能递归激发。</span><span class="sxs-lookup"><span data-stu-id="ad6fb-105">When set to 0 (OFF), server-level triggers cannot be fired recursively.</span></span> <span data-ttu-id="ad6fb-106">当 server trigger recursion 选项设置为 0 (OFF) 时，仅阻止直接递归。</span><span class="sxs-lookup"><span data-stu-id="ad6fb-106">Only direct recursion is prevented when the server trigger recursion option is set to 0 (OFF).</span></span> <span data-ttu-id="ad6fb-107">（若要禁用间接递归，请将 **nested triggers** 选项设置为 0。）该选项的默认值为 1 (ON)。</span><span class="sxs-lookup"><span data-stu-id="ad6fb-107">(To disable indirect recursion, set the **nested triggers** option to 0.) The default value for this option is 1 (ON).</span></span> <span data-ttu-id="ad6fb-108">该设置更改后立即生效，而不需要重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="ad6fb-108">The setting takes effect immediately (without a server restart).</span></span>  
  
 <span data-ttu-id="ad6fb-109">有关详细信息，请参阅 [创建嵌套触发器](../../relational-databases/triggers/create-nested-triggers.md)。</span><span class="sxs-lookup"><span data-stu-id="ad6fb-109">For more information, see [Create Nested Triggers](../../relational-databases/triggers/create-nested-triggers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad6fb-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad6fb-110">See Also</span></span>  
 <span data-ttu-id="ad6fb-111">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ad6fb-111">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="ad6fb-112">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad6fb-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="ad6fb-113">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ad6fb-113">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
