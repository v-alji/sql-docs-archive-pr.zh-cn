---
title: 网络数据包大小不应超过 8060 字节 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 01b500cbe65107767d73bc2901b6d5e028b94ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580194"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a><span data-ttu-id="8f78c-102">网络数据包大小不应超过 8060 字节</span><span class="sxs-lookup"><span data-stu-id="8f78c-102">Network Packet Size Should Not Exceed 8060 Bytes</span></span>
  <span data-ttu-id="8f78c-103">如果为 sp_configure 'network packet size' 指定的值或者任何登录用户的网络数据包大小大于 8060 字节， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将执行不同的内存分配操作。</span><span class="sxs-lookup"><span data-stu-id="8f78c-103">If the value specified for sp_configure 'network packet size' or if the network packet size of any logged-in user is more than 8060 bytes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs different memory allocation operations.</span></span> <span data-ttu-id="8f78c-104">这可能会增加不是为缓冲池保留的进程虚拟地址空间。</span><span class="sxs-lookup"><span data-stu-id="8f78c-104">This can cause an increase in the process virtual address space that is not reserved for the buffer pool.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="8f78c-105">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="8f78c-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="8f78c-106">网络数据包大小不应超过 8060 字节。</span><span class="sxs-lookup"><span data-stu-id="8f78c-106">The network packet size should not exceed 8060 bytes.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="8f78c-107">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="8f78c-107">For More Information</span></span>  
 [<span data-ttu-id="8f78c-108">Microsoft 知识库文章 903002</span><span class="sxs-lookup"><span data-stu-id="8f78c-108">Microsoft Knowledge Base article 903002</span></span>](https://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a><span data-ttu-id="8f78c-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f78c-109">See Also</span></span>  
 [<span data-ttu-id="8f78c-110">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="8f78c-110">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
