---
title: 可信位 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 062a63dd52f4641a0ddfcbc20cb9bad3cce6dc61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580191"
---
# <a name="trustworthy-bit"></a><span data-ttu-id="c2de3-102">可信位</span><span class="sxs-lookup"><span data-stu-id="c2de3-102">Trustworthy Bit</span></span>
  <span data-ttu-id="c2de3-103">此规则确定数据库的 dbo 角色是否分配给了 sysadmin 固定服务器角色，以及数据库的可信位是否设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="c2de3-103">This rule determines whether the dbo role for a database is assigned to the sysadmin fixed server role and the database has its trustworthy bit set to ON.</span></span>  
  
 <span data-ttu-id="c2de3-104">如果满足这些条件，特权数据库用户就可以提升 sysadmin 角色的特权。</span><span class="sxs-lookup"><span data-stu-id="c2de3-104">If these conditions are met, a privileged database user can elevate privileges to the sysadmin role.</span></span> <span data-ttu-id="c2de3-105">在此角色中，用户可以创建和运行危害系统的不安全程序集。</span><span class="sxs-lookup"><span data-stu-id="c2de3-105">In this role, the user can create and run unsafe assemblies that compromise the system.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="c2de3-106">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="c2de3-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="c2de3-107">关闭可信位或者撤消 dbo 数据库角色的 sysadmin 权限。</span><span class="sxs-lookup"><span data-stu-id="c2de3-107">Turn off the trustworthy bit or revoke sysadmin permissions from the dbo database role.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="c2de3-108">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="c2de3-108">For More Information</span></span>  
 [<span data-ttu-id="c2de3-109">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c2de3-109">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="c2de3-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2de3-110">See Also</span></span>  
 [<span data-ttu-id="c2de3-111">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="c2de3-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
