---
title: in-doubt xact resolution 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- distributed transactions [SQL Server], unresolved transactions
- unresolved transactions
- in-doubt xact resolution option
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6b8db57ef2a4ee85d65e8c25de28ff7ada7994e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688227"
---
# <a name="in-doubt-xact-resolution-server-configuration-option"></a><span data-ttu-id="d05d3-102">in-doubt xact resolution 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="d05d3-102">in-doubt xact resolution Server Configuration Option</span></span>
  <span data-ttu-id="d05d3-103">使用 **in-doubt xact resolution** 选项可以控制 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分布式事务处理协调器 (MS DTC) 无法解决的默认事务结果。</span><span class="sxs-lookup"><span data-stu-id="d05d3-103">Use the **in-doubt xact resolution** option to control the default outcome of transactions that the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) is unable to resolve.</span></span> <span data-ttu-id="d05d3-104">事务无法解决可能与 MS DTC 停止工作或恢复时的未知事务结果有关。</span><span class="sxs-lookup"><span data-stu-id="d05d3-104">Inability to resolve transactions may be related to the MS DTC down time or an unknown transaction outcome at the time of recovery.</span></span>  
  
 <span data-ttu-id="d05d3-105">下表列出了解决有疑问的事务可能出现的结果值。</span><span class="sxs-lookup"><span data-stu-id="d05d3-105">The following table lists the possible outcome values for resolving an in-doubt transaction.</span></span>  
  
|<span data-ttu-id="d05d3-106">结果值</span><span class="sxs-lookup"><span data-stu-id="d05d3-106">Outcome value</span></span>|<span data-ttu-id="d05d3-107">说明</span><span class="sxs-lookup"><span data-stu-id="d05d3-107">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="d05d3-108">0</span><span class="sxs-lookup"><span data-stu-id="d05d3-108">0</span></span>|<span data-ttu-id="d05d3-109">没有假设。</span><span class="sxs-lookup"><span data-stu-id="d05d3-109">No presumption.</span></span> <span data-ttu-id="d05d3-110">如果 MS DTC 无法解决任何有疑问的事务，恢复就会失败。</span><span class="sxs-lookup"><span data-stu-id="d05d3-110">Recovery fails if MS DTC cannot resolve any in-doubt transactions.</span></span>|  
|<span data-ttu-id="d05d3-111">1</span><span class="sxs-lookup"><span data-stu-id="d05d3-111">1</span></span>|<span data-ttu-id="d05d3-112">假设提交。</span><span class="sxs-lookup"><span data-stu-id="d05d3-112">Presume commit.</span></span> <span data-ttu-id="d05d3-113">假设已提交任何 MS DTC 有疑问的事务。</span><span class="sxs-lookup"><span data-stu-id="d05d3-113">Any MS DTC in-doubt transactions are presumed to have committed.</span></span>|  
|<span data-ttu-id="d05d3-114">2</span><span class="sxs-lookup"><span data-stu-id="d05d3-114">2</span></span>|<span data-ttu-id="d05d3-115">假设中止。</span><span class="sxs-lookup"><span data-stu-id="d05d3-115">Presume abort.</span></span> <span data-ttu-id="d05d3-116">假设已中止任何 MS DTC 有疑问的事务。</span><span class="sxs-lookup"><span data-stu-id="d05d3-116">Any MS DTC in-doubt transactions are presumed to have aborted.</span></span>|  
  
 <span data-ttu-id="d05d3-117">若要尽可能减少扩展的停止工作时间，管理员可以选择将此选项配置为假设提交或假设中止，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="d05d3-117">To minimize the possibility of extended down time, an administrator might choose to configure this option either to presume commit or presume abort, as shown in the following example.</span></span>  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 2 -- presume abort  
GO  
RECONFIGURE  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="d05d3-118">另外，管理员也可能希望保留默认值（没有假设）并允许恢复失败，以便了解 DTC 故障，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="d05d3-118">Alternatively, the administrator might want to leave the default (no presumption) and allow recovery to fail in order to be made aware of a DTC failure, as shown in the following example.</span></span>  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 1 -- presume commit  
GO  
reconfigure  
GO  
ALTER DATABASE pubs SET ONLINE -- run recovery again  
GO  
sp_configure 'in-doubt xact resolution', 0 -- back to no assumptions  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="d05d3-119">**in-doubt xact resolution** 选项是一个高级选项。</span><span class="sxs-lookup"><span data-stu-id="d05d3-119">The **in-doubt xact resolution** option is an advanced option.</span></span> <span data-ttu-id="d05d3-120">如果使用 **sp_configure** 系统存储过程来更改该设置，则仅当 **show advanced options** 设置为 1 时才可以更改 **in-doubt xact resolution** 。</span><span class="sxs-lookup"><span data-stu-id="d05d3-120">If you are using the **sp_configure** system stored procedure to change the setting, you can change **in-doubt xact resolution** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="d05d3-121">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="d05d3-121">The setting takes effect immediately without a server restart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d05d3-122">在任何分布式事务所涉及的所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中，使此选项的配置始终保持一致，有助于避免数据的不一致。</span><span class="sxs-lookup"><span data-stu-id="d05d3-122">Consistent configuration of this option across all [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances involved in any distributed transactions will help avoid data inconsistencies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d05d3-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d05d3-123">See Also</span></span>  
 <span data-ttu-id="d05d3-124">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d05d3-124">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="d05d3-125">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d05d3-125">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="d05d3-126">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d05d3-126">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
