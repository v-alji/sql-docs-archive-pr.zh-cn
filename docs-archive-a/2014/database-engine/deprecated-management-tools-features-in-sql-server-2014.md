---
title: SQL Server 2014 中不推荐使用的管理工具功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: a08d1354-cc91-4ab7-a73f-3ad815af3d5a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 484e4078e25249e17a1d8b87426a395c3cfa1725
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579748"
---
# <a name="deprecated-management-tools-features-in-sql-server-2014"></a><span data-ttu-id="2b731-102">SQL Server 2014 中不推荐使用的管理工具功能</span><span class="sxs-lookup"><span data-stu-id="2b731-102">Deprecated Management Tools Features in SQL Server 2014</span></span>
  <span data-ttu-id="2b731-103">本主题介绍 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]中仍然可用但不推荐使用的管理工具功能。</span><span class="sxs-lookup"><span data-stu-id="2b731-103">This topic describes the deprecated Management Tools features that are still available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="2b731-104">按照计划， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]未来版本将不再具有这些功能。</span><span class="sxs-lookup"><span data-stu-id="2b731-104">These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2b731-105">在新的应用程序中不应使用这些不推荐使用的功能。</span><span class="sxs-lookup"><span data-stu-id="2b731-105">Deprecated features should not be used in new applications.</span></span>  
  
|<span data-ttu-id="2b731-106">功能</span><span class="sxs-lookup"><span data-stu-id="2b731-106">Feature</span></span>|<span data-ttu-id="2b731-107">废止阶段</span><span class="sxs-lookup"><span data-stu-id="2b731-107">Deprecation stage</span></span>|  
|-------------|-----------------------|  
|[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]<span data-ttu-id="2b731-108">已注册服务器 API</span><span class="sxs-lookup"><span data-stu-id="2b731-108">Registered Server API</span></span>|<span data-ttu-id="2b731-109">公告</span><span class="sxs-lookup"><span data-stu-id="2b731-109">Announcement</span></span>|  
|<span data-ttu-id="2b731-110">sqlps.exe</span><span class="sxs-lookup"><span data-stu-id="2b731-110">sqlps.exe</span></span>|<span data-ttu-id="2b731-111">警告</span><span class="sxs-lookup"><span data-stu-id="2b731-111">Warning</span></span>|  
|<span data-ttu-id="2b731-112">osql.exe</span><span class="sxs-lookup"><span data-stu-id="2b731-112">osql.exe</span></span>|<span data-ttu-id="2b731-113">警告</span><span class="sxs-lookup"><span data-stu-id="2b731-113">Warning</span></span>|  
|<span data-ttu-id="2b731-114">SQLMail</span><span class="sxs-lookup"><span data-stu-id="2b731-114">SQLMail</span></span>|<span data-ttu-id="2b731-115">警告</span><span class="sxs-lookup"><span data-stu-id="2b731-115">Warning</span></span>|  
|<span data-ttu-id="2b731-116">SMO 类：Microsoft.SQLServer.Management.Smo.Information 类</span><span class="sxs-lookup"><span data-stu-id="2b731-116">SMO class: Microsoft.SQLServer.Management.Smo.Information class</span></span>|<span data-ttu-id="2b731-117">公告</span><span class="sxs-lookup"><span data-stu-id="2b731-117">Announcement</span></span>|  
|<span data-ttu-id="2b731-118">SMO 类：Microsoft.SQLServer.Management.Smo.Settings 类</span><span class="sxs-lookup"><span data-stu-id="2b731-118">SMO class: Microsoft.SQLServer.Management.Smo.Settings class</span></span>|<span data-ttu-id="2b731-119">公告</span><span class="sxs-lookup"><span data-stu-id="2b731-119">Announcement</span></span>|  
|<span data-ttu-id="2b731-120">SMO 类：Microsoft.SQLServer.Management.Smo.DatabaseOptions 类</span><span class="sxs-lookup"><span data-stu-id="2b731-120">SMO Class: Microsoft.SQLServer.Management.Smo.DatabaseOptions class</span></span>|<span data-ttu-id="2b731-121">公告</span><span class="sxs-lookup"><span data-stu-id="2b731-121">Announcement</span></span>|  
|<span data-ttu-id="2b731-122">SMO 类：Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger.NotForReplication 属性</span><span class="sxs-lookup"><span data-stu-id="2b731-122">SMO Class: Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger.NotForReplication property</span></span>|<span data-ttu-id="2b731-123">公告</span><span class="sxs-lookup"><span data-stu-id="2b731-123">Announcement</span></span>|  
|<span data-ttu-id="2b731-124">SSMS 中的数据库项目系统，包括源代码管理集成</span><span class="sxs-lookup"><span data-stu-id="2b731-124">The Database Project System, including source-control integration, in SSMS</span></span>|<span data-ttu-id="2b731-125">公告</span><span class="sxs-lookup"><span data-stu-id="2b731-125">Announcement</span></span>|  
|<span data-ttu-id="2b731-126">Net send 通知（[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理）</span><span class="sxs-lookup"><span data-stu-id="2b731-126">Net send notifications ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent)</span></span>|<span data-ttu-id="2b731-127">公告</span><span class="sxs-lookup"><span data-stu-id="2b731-127">Announcement</span></span>|  
|<span data-ttu-id="2b731-128">寻呼通知（[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理）</span><span class="sxs-lookup"><span data-stu-id="2b731-128">Pager notifications ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent)</span></span>|<span data-ttu-id="2b731-129">公告</span><span class="sxs-lookup"><span data-stu-id="2b731-129">Announcement</span></span>|  
|<span data-ttu-id="2b731-130">ActiveX 子系统（[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理）</span><span class="sxs-lookup"><span data-stu-id="2b731-130">The ActiveX subsystem ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent)</span></span>|<span data-ttu-id="2b731-131">公告</span><span class="sxs-lookup"><span data-stu-id="2b731-131">Announcement</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b731-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2b731-132">See Also</span></span>  
 [<span data-ttu-id="2b731-133">向后兼容性</span><span class="sxs-lookup"><span data-stu-id="2b731-133">Backward Compatibility</span></span>](../../2014/getting-started/backward-compatibility.md)  
  
  
