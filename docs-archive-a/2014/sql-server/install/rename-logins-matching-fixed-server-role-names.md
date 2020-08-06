---
title: 重命名与固定服务器角色名称匹配的登录名 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 296ae4d4051e79e3c5d3bc158ef3e87c9164ecd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691508"
---
# <a name="rename-logins-matching-fixed-server-role-names"></a><span data-ttu-id="3b6a2-102">重命名与固定服务器角色名称匹配的登录名</span><span class="sxs-lookup"><span data-stu-id="3b6a2-102">Rename logins matching fixed server role names</span></span>
  <span data-ttu-id="3b6a2-103">升级顾问检测到有一个或多个用户定义的登录名与固定服务器角色的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="3b6a2-103">Upgrade Advisor detected one or more user-defined login names that match the names of fixed server roles.</span></span> <span data-ttu-id="3b6a2-104">固定服务器角色名称是保留名称。</span><span class="sxs-lookup"><span data-stu-id="3b6a2-104">Fixed server role names are reserved.</span></span> <span data-ttu-id="3b6a2-105">请在升级前重命名相应登录名。</span><span class="sxs-lookup"><span data-stu-id="3b6a2-105">Rename the login before you upgrade.</span></span>  
  
## <a name="component"></a><span data-ttu-id="3b6a2-106">组件</span><span class="sxs-lookup"><span data-stu-id="3b6a2-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="3b6a2-107">说明</span><span class="sxs-lookup"><span data-stu-id="3b6a2-107">Description</span></span>  
 <span data-ttu-id="3b6a2-108">以下固定服务器角色名称是保留名称，因此不能用作用户定义的登录名。</span><span class="sxs-lookup"><span data-stu-id="3b6a2-108">The following fixed server role names are reserved and cannot be used as user-defined login names.</span></span>  
  
-   <span data-ttu-id="3b6a2-109">**sysadmin**</span><span class="sxs-lookup"><span data-stu-id="3b6a2-109">**sysadmin**</span></span>  
  
-   <span data-ttu-id="3b6a2-110">**serveradmin**</span><span class="sxs-lookup"><span data-stu-id="3b6a2-110">**serveradmin**</span></span>  
  
-   <span data-ttu-id="3b6a2-111">**setupadmin**</span><span class="sxs-lookup"><span data-stu-id="3b6a2-111">**setupadmin**</span></span>  
  
-   <span data-ttu-id="3b6a2-112">**securityadmin**</span><span class="sxs-lookup"><span data-stu-id="3b6a2-112">**securityadmin**</span></span>  
  
-   <span data-ttu-id="3b6a2-113">**processadmin**</span><span class="sxs-lookup"><span data-stu-id="3b6a2-113">**processadmin**</span></span>  
  
-   <span data-ttu-id="3b6a2-114">**dbcreator**</span><span class="sxs-lookup"><span data-stu-id="3b6a2-114">**dbcreator**</span></span>  
  
-   <span data-ttu-id="3b6a2-115">**diskadmin**</span><span class="sxs-lookup"><span data-stu-id="3b6a2-115">**diskadmin**</span></span>  
  
-   <span data-ttu-id="3b6a2-116">**bulkadmin**</span><span class="sxs-lookup"><span data-stu-id="3b6a2-116">**bulkadmin**</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="3b6a2-117">纠正措施</span><span class="sxs-lookup"><span data-stu-id="3b6a2-117">Corrective Action</span></span>  
 <span data-ttu-id="3b6a2-118">在升级之前，请先执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="3b6a2-118">Before upgrading, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="3b6a2-119">通过执行以下语句来记录登录名的安全标识符 (SID)。</span><span class="sxs-lookup"><span data-stu-id="3b6a2-119">Record the security identifiers (SIDs) of the logins by executing the following statement.</span></span>  
  
    ```  
    SELECT name, sid   
    FROM master.dbo.syslogins   
    WHERE name IN('sysadmin', 'serveradmin','setupadmin', 'securityadmin','processadmin', 'dbcreator','diskadmin','bulkadmin')  
    ```  
  
2.  <span data-ttu-id="3b6a2-120">删除登录名。</span><span class="sxs-lookup"><span data-stu-id="3b6a2-120">Drop the logins.</span></span>  
  
3.  <span data-ttu-id="3b6a2-121">使用**sp_addlogin**系统过程创建新登录名。</span><span class="sxs-lookup"><span data-stu-id="3b6a2-121">Use the **sp_addlogin** system procedure to create new logins.</span></span> <span data-ttu-id="3b6a2-122">为每个相应的登录名指定\*\* \@ sid\*\*参数的步骤1中返回的 sid。</span><span class="sxs-lookup"><span data-stu-id="3b6a2-122">Specify the SID returned in step 1 in the **\@sid** parameter for each corresponding login.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b6a2-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b6a2-123">See Also</span></span>  
 <span data-ttu-id="3b6a2-124">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="3b6a2-124">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="3b6a2-125">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="3b6a2-125">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
