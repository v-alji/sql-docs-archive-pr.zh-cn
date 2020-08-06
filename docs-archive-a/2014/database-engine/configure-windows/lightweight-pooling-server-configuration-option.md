---
title: lightweight pooling 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default lightweight pooling
- decreasing overhead
- lightweight pooling option
- system overhead [SQL Server]
- performance [SQL Server], lightweight pooling
- context switching [SQL Server], lightweight pooling option
- excessive context switching [SQL Server]
- reducing overhead
- overhead [SQL Server]
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 549ff7451a31b48459b5a290b94ad406c3768a91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587599"
---
# <a name="lightweight-pooling-server-configuration-option"></a><span data-ttu-id="5e3a4-102">lightweight pooling 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="5e3a4-102">lightweight pooling Server Configuration Option</span></span>
  <span data-ttu-id="5e3a4-103">使用“轻型池”选项可以减少有时在对称多处理 (SMP) 环境下遇到的、与过多的上下文切换有关的系统开销。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-103">Use the **lightweight pooling** option to provide a means of reducing the system overhead associated with the excessive context switching sometimes seen in symmetric multiprocessing (SMP) environments.</span></span> <span data-ttu-id="5e3a4-104">如果出现过多的上下文切换，轻型池可以通过上下文切换内联化，从而降低用户/内核环的转换频率，达到提高吞吐量的目的。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-104">When excessive context switching is present, lightweight pooling can provide better throughput by performing the context switching inline, thus helping to reduce user/kernel ring transitions.</span></span>  
  
 <span data-ttu-id="5e3a4-105">纤程模式专用于 UMS 工作线程的上下文切换是性能的关键瓶颈的某些情况。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-105">Fiber mode is intended for certain situations in which the context switching of the UMS workers are the critical bottleneck in performance.</span></span> <span data-ttu-id="5e3a4-106">因为这种情况很少出现，所以纤程模式很少增强典型系统上的性能或可扩展性。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-106">Because this is rare, fiber mode rarely enhances performance or scalability on the typical system.</span></span> <span data-ttu-id="5e3a4-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 中改进的上下文切换也减少了对纤程模式的需求。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-107">Improved context switching in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] has also reduced the need for fiber mode.</span></span> <span data-ttu-id="5e3a4-108">我们建议您不要使用纤程模式计划日常操作。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-108">We do not recommend that you use fiber mode scheduling for routine operation.</span></span> <span data-ttu-id="5e3a4-109">这是因为它会抑制上下文切换优点的正常发挥，并且使用线程本地存储区 (TLS) 或线程所有的对象（如互斥体，一种 Win32 内核对象）的某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件在纤程模式下无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-109">This is because it can decrease performance by inhibiting the regular benefits of context switching, and because some components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that use Thread Local Storage (TLS) or thread-owned objects, such as mutexes (a type of Win32 kernel object), cannot function correctly in fiber mode.</span></span>  
  
 <span data-ttu-id="5e3a4-110">将 **lightweight pooling** 设置为 1 将使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 切换到纤程模式计划。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-110">Setting **lightweight pooling** to 1 causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to switch to fiber mode scheduling.</span></span> <span data-ttu-id="5e3a4-111">该选项的默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-111">The default value for this option is 0.</span></span>  
  
 <span data-ttu-id="5e3a4-112">**lightweight pooling** 选项是一个高级选项。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-112">The **lightweight pooling** option is an advanced option.</span></span> <span data-ttu-id="5e3a4-113">如果使用 **sp_configure** 系统存储过程来更改该设置，则仅当“显示高级选项”设置为 1 时才可以更改“轻型池”。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-113">If you are using the **sp_configure** system stored procedure to change the setting, you can change **lightweight pooling** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="5e3a4-114">该设置在服务器重新启动后生效。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-114">The setting takes effect after the server is restarted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e3a4-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP 不支持轻型池。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-115">Lightweight pooling is not supported for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP.</span></span> [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] <span data-ttu-id="5e3a4-116">完全支持轻型池。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-116">provides full support for lightweight pooling.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e3a4-117">轻型池不支持执行公共语言运行时 (CLR)。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-117">Common language runtime (CLR) execution is not supported under lightweight pooling.</span></span> <span data-ttu-id="5e3a4-118">禁用以下两个选项之一：“clr enabled”或“lightweight pooling”。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-118">Disable one of two options: "clr enabled" or "lightweight pooling".</span></span> <span data-ttu-id="5e3a4-119">依赖于 CLR 并且在纤程模式下无法正常工作的功能包括：hierarchy 数据类型、复制和基于策略的管理。</span><span class="sxs-lookup"><span data-stu-id="5e3a4-119">Features that rely upon CLR and that do not work properly in fiber mode include the hierarchy data type, replication, and Policy-Based Management.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e3a4-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e3a4-120">See Also</span></span>  
 <span data-ttu-id="5e3a4-121">[clr enabled 服务器配置选项](clr-enabled-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="5e3a4-121">[clr enabled Server Configuration Option](clr-enabled-server-configuration-option.md) </span></span>  
 <span data-ttu-id="5e3a4-122">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5e3a4-122">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="5e3a4-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5e3a4-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="5e3a4-124">“启用 CLR”服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="5e3a4-124">clr enabled Server Configuration Option</span></span>](clr-enabled-server-configuration-option.md)  
  
  
