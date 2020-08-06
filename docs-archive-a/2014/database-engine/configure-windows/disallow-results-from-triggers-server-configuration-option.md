---
title: disallow results from triggers 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], result sets
- result sets [SQL Server], triggers
- disallow results from triggers option
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f162a6e06706561d861bfc54a1ae4027f2c3466e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682383"
---
# <a name="disallow-results-from-triggers-server-configuration-option"></a><span data-ttu-id="64ba8-102">disallow results from triggers 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="64ba8-102">disallow results from triggers Server Configuration Option</span></span>
  <span data-ttu-id="64ba8-103">使用 **disallow results from triggers** 选项可控制是否让触发器返回结果集。</span><span class="sxs-lookup"><span data-stu-id="64ba8-103">Use the **disallow results from triggers** option to control whether triggers return result sets.</span></span> <span data-ttu-id="64ba8-104">返回结果集的触发器可能会导致应用程序出现意外的行为，而这些行为并不符合它们的设计意图。</span><span class="sxs-lookup"><span data-stu-id="64ba8-104">Triggers that return result sets may cause unexpected behavior in applications that are not designed to work with them.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] <span data-ttu-id="64ba8-105">我们建议将此值设置为 1。</span><span class="sxs-lookup"><span data-stu-id="64ba8-105">We recommend that you set this value to 1.</span></span>  
  
 <span data-ttu-id="64ba8-106">当设置为 1 时， **disallow results from triggers** 选项将设置为打开。</span><span class="sxs-lookup"><span data-stu-id="64ba8-106">When set to 1, the **disallow results from triggers** option is set to ON.</span></span> <span data-ttu-id="64ba8-107">该选项的默认值为 0（关闭）。</span><span class="sxs-lookup"><span data-stu-id="64ba8-107">The default setting for this option is 0 (OFF).</span></span> <span data-ttu-id="64ba8-108">如果将该选项设置为 1 (打开)，则触发器进行的任何返回结果集的尝试都将失败，用户将接收到下列错误消息：</span><span class="sxs-lookup"><span data-stu-id="64ba8-108">If this option is set to 1 (ON), any attempt by a trigger to return a result set fails, and the user receives the following error message:</span></span>  
  
 <span data-ttu-id="64ba8-109">“消息 524，级别 16，状态 1，过程 \<Procedure Name>，行 \<Line#></span><span class="sxs-lookup"><span data-stu-id="64ba8-109">"Msg 524, Level 16, State 1, Procedure \<Procedure Name>, Line \<Line#></span></span>  
  
 <span data-ttu-id="64ba8-110">“触发器返回了结果集且服务器选项 "disallow_results_from_triggers" 为 TRUE。”</span><span class="sxs-lookup"><span data-stu-id="64ba8-110">"A trigger returned a resultset and the server option 'disallow_results_from_triggers' is true."</span></span>  
  
 <span data-ttu-id="64ba8-111">disallow results from triggers 选项适用于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例级别，并且它可确定实例中所有现有的触发器的行为。</span><span class="sxs-lookup"><span data-stu-id="64ba8-111">The **disallow results from triggers** option is applied at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance level, and it will determine behavior for all existing triggers within the instance.</span></span>  
  
 <span data-ttu-id="64ba8-112">**disallow results from triggers** 选项是一个高级选项。</span><span class="sxs-lookup"><span data-stu-id="64ba8-112">The **disallow results from triggers** option is an advanced option.</span></span> <span data-ttu-id="64ba8-113">如果使用 **sp_configure** 系统存储过程来更改该设置，则只有在“显示高级选项”设置为 1 时才能更改“禁止从触发器返回结果”选项。</span><span class="sxs-lookup"><span data-stu-id="64ba8-113">If you are using the **sp_configure** system stored procedure to change the setting, you can change disallow results from triggers only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="64ba8-114">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="64ba8-114">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64ba8-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64ba8-115">See Also</span></span>  
 <span data-ttu-id="64ba8-116">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="64ba8-116">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="64ba8-117">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="64ba8-117">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="64ba8-118">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="64ba8-118">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
