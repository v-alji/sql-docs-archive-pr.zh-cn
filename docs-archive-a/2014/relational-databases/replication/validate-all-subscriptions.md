---
title: 验证所有订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.allsubscriptions.f1
helpviewer_keywords:
- Validate All Subscriptions dialog box
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27a7a4f5e5c3c303d5a1cbe257c0a0e9b531e824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588963"
---
# <a name="validate-all-subscriptions"></a><span data-ttu-id="c53d8-102">验证所有订阅</span><span class="sxs-lookup"><span data-stu-id="c53d8-102">Validate All Subscriptions</span></span>
  <span data-ttu-id="c53d8-103">可以使用 **“验证所有订阅”** 对话框，指定下次运行各个订阅的合并代理时应验证对合并发布的所有订阅。</span><span class="sxs-lookup"><span data-stu-id="c53d8-103">Use the **Validate All Subscriptions** dialog box to specify that all subscriptions to a merge publication should be validated the next time the Merge Agent for each subscription runs.</span></span> <span data-ttu-id="c53d8-104">验证的结果显示在复制监视器中。</span><span class="sxs-lookup"><span data-stu-id="c53d8-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="c53d8-105">有关详细信息，请参阅 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="c53d8-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="c53d8-106">右键单击 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的订阅，再单击 **“验证单个订阅”** ，也可以验证单个订阅。</span><span class="sxs-lookup"><span data-stu-id="c53d8-106">It is also possible to validate a single subscription by right-clicking a subscription in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and clicking **Validate Subscription**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c53d8-107">选项</span><span class="sxs-lookup"><span data-stu-id="c53d8-107">Options</span></span>  
 <span data-ttu-id="c53d8-108">**仅验证行计数**</span><span class="sxs-lookup"><span data-stu-id="c53d8-108">**Verify the row counts only**</span></span>  
 <span data-ttu-id="c53d8-109">选择此选项可以验证订阅服务器上的表是否与发布服务器上的表具有相同的行数。</span><span class="sxs-lookup"><span data-stu-id="c53d8-109">Select to validate whether the table at the Subscriber has the same number of rows as the table at the Publisher.</span></span> <span data-ttu-id="c53d8-110">此方法不会验证行的内容是否匹配。</span><span class="sxs-lookup"><span data-stu-id="c53d8-110">This method does not validate that the content of the rows matches.</span></span> <span data-ttu-id="c53d8-111">行计数验证是一种简易验证方法，可帮助您了解数据是否存在问题。</span><span class="sxs-lookup"><span data-stu-id="c53d8-111">Row count validation provides a lightweight approach to validation that can make you aware of issues with your data.</span></span>  
  
 <span data-ttu-id="c53d8-112">**验证行计数并比较校验和以验证行数据**</span><span class="sxs-lookup"><span data-stu-id="c53d8-112">**Verify the row counts and compare checksums to verify the row data**</span></span>  
 <span data-ttu-id="c53d8-113">除了可在发布服务器和订阅服务器上对行进行计数之外，还可使用二进制校验和算法来计算所有数据的校验和。</span><span class="sxs-lookup"><span data-stu-id="c53d8-113">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="c53d8-114">如果行计数失败，则不计算校验和。</span><span class="sxs-lookup"><span data-stu-id="c53d8-114">If the row count fails, the checksum is not performed.</span></span> <span data-ttu-id="c53d8-115">此选项对 [!INCLUDE[ssEW](../../includes/ssew-md.md)]无效。</span><span class="sxs-lookup"><span data-stu-id="c53d8-115">This option is not valid for [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c53d8-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c53d8-116">See Also</span></span>  
 [<span data-ttu-id="c53d8-117">验证已复制的数据</span><span class="sxs-lookup"><span data-stu-id="c53d8-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
