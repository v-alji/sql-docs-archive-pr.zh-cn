---
title: 升级到域控制器上的 SQL Server 2008 的服务帐户要求 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0680e09548e38760f6ac317fec63152486a4e5fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586151"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a><span data-ttu-id="2c102-102">在域控制器上升级到 SQL Server 2008 的服务帐户要求</span><span class="sxs-lookup"><span data-stu-id="2c102-102">Service account requirements for upgrading to SQL Server 2008 on a domain controller</span></span>
  <span data-ttu-id="2c102-103">升级顾问检测到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在网络服务或域控制器上的本地服务帐户下运行的实例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2c102-103">Upgrade Advisor detected an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running under a Network Service or Local Service account on a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] domain controller.</span></span> <span data-ttu-id="2c102-104">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装在 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 域控制器上，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务不能以 Local Service 帐户或 Network Service 帐户特权运行。</span><span class="sxs-lookup"><span data-stu-id="2c102-104">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] domain controller, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services cannot run under Local Service account or Network Service account privileges.</span></span>  
  
## <a name="component"></a><span data-ttu-id="2c102-105">组件</span><span class="sxs-lookup"><span data-stu-id="2c102-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="2c102-106">纠正措施</span><span class="sxs-lookup"><span data-stu-id="2c102-106">Corrective Action</span></span>  
 <span data-ttu-id="2c102-107">请确保对所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户都分配了 Domain 帐户或 Local System 帐户。</span><span class="sxs-lookup"><span data-stu-id="2c102-107">Make sure that all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service accounts are assigned to either Domain accounts or Local System accounts.</span></span> <span data-ttu-id="2c102-108">如果不能在升级之前完成此更改，将阻止安装程序运行。</span><span class="sxs-lookup"><span data-stu-id="2c102-108">Failure to make this change before upgrading will block Setup.</span></span> <span data-ttu-id="2c102-109">SQL Writer、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Active Directory Helper 服务的服务帐户例外，因为它们已硬编码到 Network Service 帐户，无法进行更改。</span><span class="sxs-lookup"><span data-stu-id="2c102-109">The service accounts SQL Writer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Active Directory Helper services are exceptions because they are hard-coded to the Network Service account and cannot be changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c102-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c102-110">See Also</span></span>  
 <span data-ttu-id="2c102-111">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="2c102-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="2c102-112">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="2c102-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
