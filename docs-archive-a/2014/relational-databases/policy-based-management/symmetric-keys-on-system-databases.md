---
title: 系统数据库中的对称密钥 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 28e25ae3-d3dc-45ec-b316-f219512a1a47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 81c657ededc694ed87df99e0739ff74b1eb9e39b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590735"
---
# <a name="symmetric-keys-on-system-databases"></a><span data-ttu-id="a4da7-102">系统数据库中的对称密钥</span><span class="sxs-lookup"><span data-stu-id="a4da7-102">Symmetric Keys on System Databases</span></span>
  <span data-ttu-id="a4da7-103">此规则检查 master、msdb、model 和 tempdb 数据库中是否存在用户创建的对称密钥。</span><span class="sxs-lookup"><span data-stu-id="a4da7-103">This rule checks for user-created symmetric keys in the master, msdb, model, and tempdb databases.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="a4da7-104">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="a4da7-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="a4da7-105">请勿在系统数据库中创建对称密钥。</span><span class="sxs-lookup"><span data-stu-id="a4da7-105">Do not create symmetric keys in the system databases.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="a4da7-106">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="a4da7-106">For More Information</span></span>  
 [<span data-ttu-id="a4da7-107">选择加密算法</span><span class="sxs-lookup"><span data-stu-id="a4da7-107">Choose an Encryption Algorithm</span></span>](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4da7-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4da7-108">See Also</span></span>  
 [<span data-ttu-id="a4da7-109">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="a4da7-109">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
