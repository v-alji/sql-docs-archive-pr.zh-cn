---
title: 服务器 public 权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7913c4715f47b8105b72b1c817dbe77e52d40539
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693266"
---
# <a name="server-public-permissions"></a><span data-ttu-id="eb469-102">服务器 public 权限</span><span class="sxs-lookup"><span data-stu-id="eb469-102">Server public Permissions</span></span>
  <span data-ttu-id="eb469-103">此规则确定 public 服务器角色是否具有服务器权限。</span><span class="sxs-lookup"><span data-stu-id="eb469-103">This rule determines whether the public server role has server permissions.</span></span> <span data-ttu-id="eb469-104">在服务器上创建的每个登录名都是 public 服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="eb469-104">Every login that is created on the server is a member of the public server role.</span></span> <span data-ttu-id="eb469-105">如果满足此条件，则服务器上的每个登录名都将具有服务器权限。</span><span class="sxs-lookup"><span data-stu-id="eb469-105">If this condition is met, every login on the server will have server permissions.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="eb469-106">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="eb469-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="eb469-107">请勿为服务器 public 角色授予服务器权限。</span><span class="sxs-lookup"><span data-stu-id="eb469-107">Do not grant server permissions to the server public role.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eb469-108">安装完成后，**公共**角色对 `CONNECT` 所有终结点都有权限，**专用管理员连接**除外。</span><span class="sxs-lookup"><span data-stu-id="eb469-108">After setup completes the **PUBLIC** role has `CONNECT` permission on all the endpoints except the **Dedicated Admin Connection**.</span></span> <span data-ttu-id="eb469-109">这很正常，通常不应更改。</span><span class="sxs-lookup"><span data-stu-id="eb469-109">This is normal and should not be normally changed.</span></span> <span data-ttu-id="eb469-110">（通过使用 `CONNECT SQL` 权限来控制访问，该权限是在创建新登录名时自动授予的。）</span><span class="sxs-lookup"><span data-stu-id="eb469-110">(Access is controlled by using the `CONNECT SQL` permission which is automatically granted when new logins are created.)</span></span>  
  
### <a name="for-more-information"></a><span data-ttu-id="eb469-111">更多信息</span><span class="sxs-lookup"><span data-stu-id="eb469-111">For more information</span></span>  
 [<span data-ttu-id="eb469-112">保护 SQL Server</span><span class="sxs-lookup"><span data-stu-id="eb469-112">Securing SQL Server</span></span>](../security/securing-sql-server.md)  
  
  
