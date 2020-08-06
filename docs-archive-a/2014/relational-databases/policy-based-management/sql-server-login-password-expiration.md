---
title: SQL Server 登录密码过期 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7e3bf9da-a436-433d-847a-47c30428cad3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 678e8e9c6b567014bdd49e89d043165bc48d168a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577582"
---
# <a name="sql-server-login-password-expiration"></a><span data-ttu-id="f4a05-102">SQL Server 登录密码过期</span><span class="sxs-lookup"><span data-stu-id="f4a05-102">SQL Server Login Password Expiration</span></span>
  <span data-ttu-id="f4a05-103">此规则检查是否每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名都已启用“密码过期”。</span><span class="sxs-lookup"><span data-stu-id="f4a05-103">This rule checks whether "Password expiration" of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is enabled.</span></span> <span data-ttu-id="f4a05-104">如果启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证并且操作系统版本低于 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]，则攻击者可能会重复利用已知的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录密码。</span><span class="sxs-lookup"><span data-stu-id="f4a05-104">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is enabled and if the operating system version is earlier than [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], an attacker could repeatedly exploit a known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login password.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="f4a05-105">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="f4a05-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="f4a05-106">建议将操作系统升级到 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4a05-106">We recommend that you upgrade the operating system to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].</span></span>  
  
 <span data-ttu-id="f4a05-107">如果您的环境中不需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，请使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f4a05-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is not required in your environment, use Windows Authentication.</span></span> <span data-ttu-id="f4a05-108">有关详细信息，请参阅 [选择身份验证模式](../security/choose-an-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="f4a05-108">For more information, see [Choose an Authentication Mode](../security/choose-an-authentication-mode.md).</span></span>  
  
 <span data-ttu-id="f4a05-109">为所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名启用“密码过期”。</span><span class="sxs-lookup"><span data-stu-id="f4a05-109">Enable "Password expiration" for all the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="f4a05-110">使用 [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) 为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名配置密码策略。</span><span class="sxs-lookup"><span data-stu-id="f4a05-110">Use [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="f4a05-111">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="f4a05-111">For More Information</span></span>  
 [<span data-ttu-id="f4a05-112">密码策略</span><span class="sxs-lookup"><span data-stu-id="f4a05-112">Password Policy</span></span>](../security/password-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="f4a05-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4a05-113">See Also</span></span>  
 [<span data-ttu-id="f4a05-114">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="f4a05-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
