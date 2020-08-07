---
title: 删除对系统对象的列级权限进行修改的语句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e55af3dca0c55c2babd09bc6cfc48ed0ddf3ad7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588849"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a><span data-ttu-id="0e2a0-102">删除用来修改系统对象的列级权限的语句</span><span class="sxs-lookup"><span data-stu-id="0e2a0-102">Remove statements that modify column-level permissions on system objects</span></span>
  <span data-ttu-id="0e2a0-103">升级顾问检测到对系统对象的非标准列级权限。</span><span class="sxs-lookup"><span data-stu-id="0e2a0-103">The Upgrade Advisor detected nonstandard column-level permissions on system objects.</span></span> <span data-ttu-id="0e2a0-104">升级时将不保留这些权限更改。</span><span class="sxs-lookup"><span data-stu-id="0e2a0-104">These permission changes will not be maintained when you upgrade.</span></span> <span data-ttu-id="0e2a0-105">此外，不再支持对系统对象的列级权限。</span><span class="sxs-lookup"><span data-stu-id="0e2a0-105">Additionally, column-level permissions on system objects are no longer supported.</span></span> <span data-ttu-id="0e2a0-106">请从您的应用程序中删除对系统对象设置列级权限的语句。</span><span class="sxs-lookup"><span data-stu-id="0e2a0-106">Remove statements from your applications that set column-level permissions on system objects.</span></span>  
  
## <a name="component"></a><span data-ttu-id="0e2a0-107">组件</span><span class="sxs-lookup"><span data-stu-id="0e2a0-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="0e2a0-108">纠正措施</span><span class="sxs-lookup"><span data-stu-id="0e2a0-108">Corrective Action</span></span>  
 <span data-ttu-id="0e2a0-109">从应用程序中删除授予、拒绝或撤消对系统对象的列级权限的语句。</span><span class="sxs-lookup"><span data-stu-id="0e2a0-109">Remove statements from your application that grant, deny, or revoke column-level permissions on system objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e2a0-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e2a0-110">See Also</span></span>  
 <span data-ttu-id="0e2a0-111">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="0e2a0-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="0e2a0-112">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="0e2a0-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
