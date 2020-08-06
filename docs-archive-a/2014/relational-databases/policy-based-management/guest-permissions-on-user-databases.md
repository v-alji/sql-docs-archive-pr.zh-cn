---
title: 对用户数据库的 Guest 权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 344c5fd0639876998f1585c32fac5f7599f664e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578178"
---
# <a name="guest-permissions-on-user-databases"></a><span data-ttu-id="3bbdb-102">对用户数据库的 Guest 权限</span><span class="sxs-lookup"><span data-stu-id="3bbdb-102">Guest Permissions on User Databases</span></span>
  <span data-ttu-id="3bbdb-103">此规则确定 guest 用户是否有权访问数据库。</span><span class="sxs-lookup"><span data-stu-id="3bbdb-103">This rule determines whether the guest user has permission to access the database.</span></span> <span data-ttu-id="3bbdb-104">此规则仅适用于用户数据库。</span><span class="sxs-lookup"><span data-stu-id="3bbdb-104">This rule applies to user databases only.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="3bbdb-105">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="3bbdb-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="3bbdb-106">如果 guest 用户不需要访问数据库，请撤消其访问数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="3bbdb-106">Revoke the guest user permission to access the database if it is not required.</span></span>  
  
 <span data-ttu-id="3bbdb-107">不能删除 guest 用户，但可在除 master、tempdb 或 msdb 之外的任何数据库中执行 REVOKE CONNECT FROM GUEST 来撤消它的 CONNECT 权限，从而禁用 guest 用户。</span><span class="sxs-lookup"><span data-stu-id="3bbdb-107">The guest user cannot be dropped, but guest user can be disabled by revoking its CONNECT permission by executing REVOKE CONNECT FROM GUEST within any database other than master, tempdb, or msdb.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="3bbdb-108">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="3bbdb-108">For More Information</span></span>  
 [<span data-ttu-id="3bbdb-109">保护 SQL Server</span><span class="sxs-lookup"><span data-stu-id="3bbdb-109">Securing SQL Server</span></span>](../security/securing-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="3bbdb-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3bbdb-110">See Also</span></span>  
 [<span data-ttu-id="3bbdb-111">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="3bbdb-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
