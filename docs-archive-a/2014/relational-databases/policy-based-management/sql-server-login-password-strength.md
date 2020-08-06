---
title: SQL Server 登录密码强度 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b0862c3a-926b-490c-a37f-382e50146a3e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5534748fbbf810539f2dcfc22239e4b987cf0f77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687759"
---
# <a name="sql-server-login-password-strength"></a><span data-ttu-id="8a823-102">SQL Server 登录密码强度</span><span class="sxs-lookup"><span data-stu-id="8a823-102">SQL Server Login Password Strength</span></span>
  <span data-ttu-id="8a823-103">此规则检查是否每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名都已启用“强制实施密码策略”。</span><span class="sxs-lookup"><span data-stu-id="8a823-103">This rule checks whether "Enforce password policy" of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is enabled.</span></span> <span data-ttu-id="8a823-104">如果启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证并且操作系统版本低于 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]，则攻击者可能会重复利用已知的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录密码。</span><span class="sxs-lookup"><span data-stu-id="8a823-104">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is enabled and if the operating system version is earlier than [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], an attacker could repeatedly exploit a known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login password.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="8a823-105">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="8a823-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="8a823-106">建议将操作系统升级到 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8a823-106">We recommend that you upgrade the operating system to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].</span></span>  
  
 <span data-ttu-id="8a823-107">如果您的环境中不需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，请使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="8a823-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is not required in your environment, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="8a823-108">为所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名启用“强制实施密码策略”。</span><span class="sxs-lookup"><span data-stu-id="8a823-108">Enable "Enforce password policy" for all the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="8a823-109">使用 [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) 为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名配置密码策略。</span><span class="sxs-lookup"><span data-stu-id="8a823-109">Use [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="8a823-110">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="8a823-110">For More Information</span></span>  
 [<span data-ttu-id="8a823-111">密码策略</span><span class="sxs-lookup"><span data-stu-id="8a823-111">Password Policy</span></span>](../security/password-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="8a823-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8a823-112">See Also</span></span>  
 [<span data-ttu-id="8a823-113">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="8a823-113">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
