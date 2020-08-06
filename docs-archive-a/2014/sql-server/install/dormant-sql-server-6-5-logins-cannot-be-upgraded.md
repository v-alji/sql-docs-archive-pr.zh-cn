---
title: 不能升级睡眠 SQL Server 6.5 登录 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f78bca9bf2b99b2ab6f530613b64bc0e46c4001c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586178"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a><span data-ttu-id="d6a55-102">无法升级休眠的 SQL Server 6.5 登录名</span><span class="sxs-lookup"><span data-stu-id="d6a55-102">Dormant SQL Server 6.5 logins cannot be upgraded</span></span>
  <span data-ttu-id="d6a55-103">升级顾问检测到了其密码不能直接升级到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="d6a55-103">Upgrade Advisor detected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login whose password cannot be directly upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="d6a55-104">若要启用此登录名，必须重置其密码。</span><span class="sxs-lookup"><span data-stu-id="d6a55-104">To enable this login, you must reset its password.</span></span> <span data-ttu-id="d6a55-105">使用 ALTER LOGIN 可以重置密码。</span><span class="sxs-lookup"><span data-stu-id="d6a55-105">You can reset the password by using ALTER LOGIN.</span></span>  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 <span data-ttu-id="d6a55-106">除非禁用了策略检查，否则将根据系统的密码复杂性策略来验证新密码。</span><span class="sxs-lookup"><span data-stu-id="d6a55-106">The new password will be validated against your system's password complexity policy, unless policy checking is disabled.</span></span> <span data-ttu-id="d6a55-107">建议使用复杂的密码且不要禁用策略检查。</span><span class="sxs-lookup"><span data-stu-id="d6a55-107">We recommend that you use complex passwords and not disable policy checking.</span></span> <span data-ttu-id="d6a55-108">MUST_CHANGE 选项将强制用户选择新密码。</span><span class="sxs-lookup"><span data-stu-id="d6a55-108">The MUST_CHANGE option forces the user to select a new password.</span></span> <span data-ttu-id="d6a55-109">这不是必需的，但建议这样做。</span><span class="sxs-lookup"><span data-stu-id="d6a55-109">This is not required, but it is recommended.</span></span>  
  
 <span data-ttu-id="d6a55-110">通过使用以下查询可以标识休眠的登录名：</span><span class="sxs-lookup"><span data-stu-id="d6a55-110">You can identify dormant logins by using the following query:</span></span>  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6a55-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6a55-111">See Also</span></span>  
 <span data-ttu-id="d6a55-112">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d6a55-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d6a55-113">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="d6a55-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
