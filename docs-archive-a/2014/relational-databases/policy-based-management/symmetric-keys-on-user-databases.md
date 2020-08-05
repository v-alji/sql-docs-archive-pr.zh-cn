---
title: 用户数据库中的对称密钥 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ca0fb62ccb32ce244e1087281997dcd9929df89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580193"
---
# <a name="symmetric-keys-on-user-databases"></a><span data-ttu-id="e9216-102">用户数据库中的对称密钥</span><span class="sxs-lookup"><span data-stu-id="e9216-102">Symmetric Keys on User Databases</span></span>
  <span data-ttu-id="e9216-103">此规则检查长度小于 128 个字节的密钥是否没有使用 RC2 或 RC4 加密算法。</span><span class="sxs-lookup"><span data-stu-id="e9216-103">This rule checks whether keys that have a length of less than 128 bytes do not use the RC2 or RC4 encryption algorithm.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="e9216-104">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="e9216-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="e9216-105">使用 AES 128 位或更大位为数据加密创建对称密钥。</span><span class="sxs-lookup"><span data-stu-id="e9216-105">Use AES 128 bit or larger to create symmetric keys for data encryption.</span></span> <span data-ttu-id="e9216-106">如果您的操作系统不支持 AES，请使用 3DES。</span><span class="sxs-lookup"><span data-stu-id="e9216-106">If AES is not supported by your operating system, use 3DES.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="e9216-107">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="e9216-107">For More Information</span></span>  
 [<span data-ttu-id="e9216-108">选择加密算法</span><span class="sxs-lookup"><span data-stu-id="e9216-108">Choose an Encryption Algorithm</span></span>](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a><span data-ttu-id="e9216-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9216-109">See Also</span></span>  
 [<span data-ttu-id="e9216-110">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="e9216-110">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
