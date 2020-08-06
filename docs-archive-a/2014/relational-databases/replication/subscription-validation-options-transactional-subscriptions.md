---
title: 订阅验证选项（事务订阅）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 40a617dd1beff24f8f072f5d139bec7c1ca65f33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693715"
---
# <a name="subscription-validation-options-transactional-subscriptions"></a><span data-ttu-id="1559b-102">订阅验证选项（事务订阅）</span><span class="sxs-lookup"><span data-stu-id="1559b-102">Subscription Validation Options (Transactional Subscriptions)</span></span>
  <span data-ttu-id="1559b-103">使用 "**订阅验证选项**" 对话框可以指定是仅使用行计数进行验证，还是使用行计数和二进制校验和进行验证。</span><span class="sxs-lookup"><span data-stu-id="1559b-103">Use the **Subscription Validation Options** dialog box to specify whether validation should use a row count only, or a row count and a binary checksum.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1559b-104">选项</span><span class="sxs-lookup"><span data-stu-id="1559b-104">Options</span></span>  
 <span data-ttu-id="1559b-105">**验证订阅服务器与发布服务器具有相同的复制数据行数**</span><span class="sxs-lookup"><span data-stu-id="1559b-105">**Verify that the Subscriber has the same number of rows of replicated data as the Publisher**</span></span>  
 <span data-ttu-id="1559b-106">选择要执行的行计数验证的类型。</span><span class="sxs-lookup"><span data-stu-id="1559b-106">Select the type of row count validation to perform.</span></span> <span data-ttu-id="1559b-107">对于 Oracle 发布， **“通过直接查询表计算实际的行计数”** 是唯一可用的选项。</span><span class="sxs-lookup"><span data-stu-id="1559b-107">For Oracle publications, the only available option is **Compute an actual row count by querying the tables directly**.</span></span>  
  
 <span data-ttu-id="1559b-108">**比较校验和以验证行数据**</span><span class="sxs-lookup"><span data-stu-id="1559b-108">**Compare checksums to verify row data**</span></span>  
 <span data-ttu-id="1559b-109">除了可在发布服务器和订阅服务器上对行进行计数之外，还可使用二进制校验和算法来计算所有数据的校验和。</span><span class="sxs-lookup"><span data-stu-id="1559b-109">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="1559b-110">如果行计数失败，则不计算校验和。</span><span class="sxs-lookup"><span data-stu-id="1559b-110">If the row count fails, the checksum is not performed.</span></span>  
  
 <span data-ttu-id="1559b-111">**完成验证后停止运行分发代理**</span><span class="sxs-lookup"><span data-stu-id="1559b-111">**Stop the Distribution Agent after the validation has completed**</span></span>  
 <span data-ttu-id="1559b-112">默认情况下，分发代理会连续运行。</span><span class="sxs-lookup"><span data-stu-id="1559b-112">By default, the Distribution Agent runs continuously.</span></span> <span data-ttu-id="1559b-113">选择此选项可以在执行验证之后停止运行代理。</span><span class="sxs-lookup"><span data-stu-id="1559b-113">Select this option to stop the agent after validation is performed.</span></span> <span data-ttu-id="1559b-114">这样，就可以在继续将数据复制到订阅服务器之前检查验证是否成功。</span><span class="sxs-lookup"><span data-stu-id="1559b-114">This allows you to check whether validation was successful before continuing to replicate data to the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1559b-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1559b-115">See Also</span></span>  
 <span data-ttu-id="1559b-116">[验证订阅服务器上的数据](validate-data-at-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="1559b-116">[Validate Data at the Subscriber](validate-data-at-the-subscriber.md) </span></span>  
 [<span data-ttu-id="1559b-117">验证已复制的数据</span><span class="sxs-lookup"><span data-stu-id="1559b-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
