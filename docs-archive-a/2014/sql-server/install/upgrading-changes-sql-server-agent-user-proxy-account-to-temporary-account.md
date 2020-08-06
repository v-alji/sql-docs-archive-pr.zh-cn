---
title: 升级会将 SQL Server 代理用户代理帐户更改为临时 UpgradedProxyAccount |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2bca80580a50f2acebed1b6fbea2dec1f6458dbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577218"
---
# <a name="upgrading-will-change-the-sql-server-agent-user-proxy-account-to-the-temporary-upgradedproxyaccount"></a><span data-ttu-id="ab3e6-102">升级会将 SQL Server 代理用户的代理帐户更改为临时的 UpgradedProxyAccount</span><span class="sxs-lookup"><span data-stu-id="ab3e6-102">Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount</span></span>
  <span data-ttu-id="ab3e6-103">启用了日志传送的数据库维护计划在升级后将不会启用。</span><span class="sxs-lookup"><span data-stu-id="ab3e6-103">Database maintenance plans that have log shipping enabled will not be enabled after upgrade.</span></span>  
  
## <a name="component"></a><span data-ttu-id="ab3e6-104">组件</span><span class="sxs-lookup"><span data-stu-id="ab3e6-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ab3e6-105">代理</span><span class="sxs-lookup"><span data-stu-id="ab3e6-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="ab3e6-106">说明</span><span class="sxs-lookup"><span data-stu-id="ab3e6-106">Description</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ab3e6-107">提供了一组不直接与数据库维护计划兼容的新日志传送功能。</span><span class="sxs-lookup"><span data-stu-id="ab3e6-107">provides a new set of log shipping functions that are not directly compatible with database maintenance plans.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="ab3e6-108">纠正措施</span><span class="sxs-lookup"><span data-stu-id="ab3e6-108">Corrective Action</span></span>  
 <span data-ttu-id="ab3e6-109">具有包含日志传送功能的数据库维护计划的 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 用户应使用新的功能配置日志传送。</span><span class="sxs-lookup"><span data-stu-id="ab3e6-109">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] users that have database maintenance plans that contain log shipping functions should configure log shipping by using the new functions.</span></span> <span data-ttu-id="ab3e6-110">有关详细信息，请在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中搜索“日志传送”。</span><span class="sxs-lookup"><span data-stu-id="ab3e6-110">For more information, search on "log shipping" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab3e6-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab3e6-111">See Also</span></span>  
 <span data-ttu-id="ab3e6-112">[SQL Server 代理日志传送作业类别导致升级失败](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span><span class="sxs-lookup"><span data-stu-id="ab3e6-112">[SQL Server Agent log shipping job category causes upgrade to fail](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span></span>  
 [<span data-ttu-id="ab3e6-113">日志传送在升级后将无法运行</span><span class="sxs-lookup"><span data-stu-id="ab3e6-113">Log shipping will not run after upgrading</span></span>](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  
