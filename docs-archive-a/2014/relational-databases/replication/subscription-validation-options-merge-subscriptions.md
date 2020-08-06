---
title: 订阅验证选项（合并订阅）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.mergeoptions.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: 4958c4ab-2025-42ce-b836-6fb4e9e6f24d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 458da0387dbaa1b366348c374748c42946893feb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693717"
---
# <a name="subscription-validation-options-merge-subscriptions"></a><span data-ttu-id="713d8-102">订阅验证选项（合并订阅）</span><span class="sxs-lookup"><span data-stu-id="713d8-102">Subscription Validation Options (Merge Subscriptions)</span></span>
  <span data-ttu-id="713d8-103">可以使用 **“订阅验证选项”** 对话框指定是仅使用行计数进行验证，还是使用行计数和二进制校验和进行验证。</span><span class="sxs-lookup"><span data-stu-id="713d8-103">Use the **Subscription Validation Options** dialog box to specify whether validation should use a row count only or a row count and a binary checksum.</span></span>  
  
## <a name="options"></a><span data-ttu-id="713d8-104">选项</span><span class="sxs-lookup"><span data-stu-id="713d8-104">Options</span></span>  
 <span data-ttu-id="713d8-105">**仅验证行计数**</span><span class="sxs-lookup"><span data-stu-id="713d8-105">**Verify the row counts only**</span></span>  
 <span data-ttu-id="713d8-106">选择此选项可以验证订阅服务器上的表是否与发布服务器上的表具有相同的行数。</span><span class="sxs-lookup"><span data-stu-id="713d8-106">Select to validate whether the table at the Subscriber has the same number of rows as the table at the Publisher.</span></span> <span data-ttu-id="713d8-107">此方法不会验证行的内容是否匹配。</span><span class="sxs-lookup"><span data-stu-id="713d8-107">This method does not validate that the content of the rows matches.</span></span> <span data-ttu-id="713d8-108">行计数验证是一种简易验证方法，可帮助您了解数据是否存在问题。</span><span class="sxs-lookup"><span data-stu-id="713d8-108">Row count validation provides a lightweight approach to validation that can make you aware of issues with your data.</span></span>  
  
 <span data-ttu-id="713d8-109">**验证行计数并比较校验和以验证行数据**</span><span class="sxs-lookup"><span data-stu-id="713d8-109">**Verify the row counts and compare checksums to verify the row data**</span></span>  
 <span data-ttu-id="713d8-110">除了可在发布服务器和订阅服务器上对行进行计数之外，还可使用二进制校验和算法来计算所有数据的校验和。</span><span class="sxs-lookup"><span data-stu-id="713d8-110">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="713d8-111">如果行计数失败，则不计算校验和。</span><span class="sxs-lookup"><span data-stu-id="713d8-111">If the row count fails, the checksum is not performed.</span></span> <span data-ttu-id="713d8-112">此选项对无效 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="713d8-112">This option is not valid for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713d8-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="713d8-113">See Also</span></span>  
 <span data-ttu-id="713d8-114">[验证订阅服务器上的数据](validate-data-at-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="713d8-114">[Validate Data at the Subscriber](validate-data-at-the-subscriber.md) </span></span>  
 [<span data-ttu-id="713d8-115">验证已复制的数据</span><span class="sxs-lookup"><span data-stu-id="713d8-115">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
