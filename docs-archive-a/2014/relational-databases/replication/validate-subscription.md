---
title: 验证单个订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.validateandresynch.f1
helpviewer_keywords:
- Validate Subscription dialog box
ms.assetid: 74bdf5e1-b886-4284-b5fb-332bf79ae083
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 010b5b2e9778ccf37133b0a84796373c012290f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580112"
---
# <a name="validate-subscription"></a><span data-ttu-id="68268-102">验证单个订阅</span><span class="sxs-lookup"><span data-stu-id="68268-102">Validate Subscription</span></span>
  <span data-ttu-id="68268-103">可以使用 **“验证单个订阅”** 对话框，指定在下次运行订阅的合并代理时应对针对合并发布的订阅进行验证。</span><span class="sxs-lookup"><span data-stu-id="68268-103">Use the **Validate Subscription** dialog box to specify that a subscription to a merge publication should be validated the next time the Merge Agent for the subscription runs.</span></span> <span data-ttu-id="68268-104">验证的结果显示在复制监视器中。</span><span class="sxs-lookup"><span data-stu-id="68268-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="68268-105">有关详细信息，请参阅 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="68268-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="68268-106">也可以在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中右键单击某个发布，并单击“验证所有订阅”来验证对合并发布的所有订阅  。</span><span class="sxs-lookup"><span data-stu-id="68268-106">It is also possible to validate all subscriptions to a merge publication by right-clicking a publication in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and clicking **Validate All Subscriptions**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="68268-107">选项</span><span class="sxs-lookup"><span data-stu-id="68268-107">Options</span></span>  
 <span data-ttu-id="68268-108">**上次尝试验证的日期**</span><span class="sxs-lookup"><span data-stu-id="68268-108">**Date of the last attempted validation**</span></span>  
 <span data-ttu-id="68268-109">最后一个包含订阅验证（无论验证是否成功）的合并代理会话的日期。</span><span class="sxs-lookup"><span data-stu-id="68268-109">The date of the last Merge Agent session that included subscription validation, whether or not that validation was successful.</span></span>  
  
 <span data-ttu-id="68268-110">**上次成功验证的日期**</span><span class="sxs-lookup"><span data-stu-id="68268-110">**Date of the last successful validation**</span></span>  
 <span data-ttu-id="68268-111">最后一个包含成功订阅验证的合并代理会话的日期。</span><span class="sxs-lookup"><span data-stu-id="68268-111">The date of the last Merge Agent session that included a successful subscription validation.</span></span>  
  
 <span data-ttu-id="68268-112">**验证此订阅**</span><span class="sxs-lookup"><span data-stu-id="68268-112">**Validate this subscription**</span></span>  
 <span data-ttu-id="68268-113">选择此选项可验证订阅。</span><span class="sxs-lookup"><span data-stu-id="68268-113">Select to validate the subscription.</span></span>  
  
 <span data-ttu-id="68268-114">**选项**</span><span class="sxs-lookup"><span data-stu-id="68268-114">**Options**</span></span>  
 <span data-ttu-id="68268-115">单击此项可访问 **“订阅验证选项”** 对话框，使用此对话框可以指定是使用行计数验证还是使用二进制校验和验证。</span><span class="sxs-lookup"><span data-stu-id="68268-115">Click to access the **Subscription Validation Options** dialog box, which allows you to specify whether to use row count validation or binary checksum validation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68268-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68268-116">See Also</span></span>  
 [<span data-ttu-id="68268-117">验证已复制的数据</span><span class="sxs-lookup"><span data-stu-id="68268-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
