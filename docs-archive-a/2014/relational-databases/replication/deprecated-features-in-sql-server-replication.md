---
title: SQL Server 复制中不推荐使用的功能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- deprecated features [SQL Server replication]
ms.assetid: 46bd3edd-d6de-40a6-a015-21cce8321feb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: daae6d7b0829df68749224422b4595404843534a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578122"
---
# <a name="deprecated-features-in-sql-server-replication"></a><span data-ttu-id="94b14-102">SQL Server 复制中不推荐使用的功能</span><span class="sxs-lookup"><span data-stu-id="94b14-102">Deprecated Features in SQL Server Replication</span></span>
  <span data-ttu-id="94b14-103">本主题介绍 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中仍然可用但不推荐使用的复制功能。</span><span class="sxs-lookup"><span data-stu-id="94b14-103">This topic describes the deprecated Replication features that are still available in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="94b14-104">按照计划， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]未来版本将不再具有这些功能。</span><span class="sxs-lookup"><span data-stu-id="94b14-104">These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="94b14-105">在新的应用程序中不应使用这些不推荐使用的功能。</span><span class="sxs-lookup"><span data-stu-id="94b14-105">Deprecated features should not be used in new applications.</span></span>  
  
## <a name="items-deprecated-in-sql-server-2014"></a><span data-ttu-id="94b14-106">SQL Server 2014 中不推荐使用的项</span><span class="sxs-lookup"><span data-stu-id="94b14-106">Items Deprecated in SQL Server 2014</span></span>  
  
|<span data-ttu-id="94b14-107">Feature</span><span class="sxs-lookup"><span data-stu-id="94b14-107">Feature</span></span>|<span data-ttu-id="94b14-108">说明</span><span class="sxs-lookup"><span data-stu-id="94b14-108">Description</span></span>|  
|-------------|-----------------|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="94b14-109">如果每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 端点都处于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的当前版本的两个主版本内，则支持复制。</span><span class="sxs-lookup"><span data-stu-id="94b14-109">Replication is supported if each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] endpoint is within two major versions of the current version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="94b14-110">因此， [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 不支持面向或源自 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]的复制。</span><span class="sxs-lookup"><span data-stu-id="94b14-110">Consequently, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] does not support replication to or from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>|  
|[!INCLUDE[ssEW](../../includes/ssew-md.md)]|<span data-ttu-id="94b14-111">如果每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 端点都处于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的当前版本的两个主版本内，则支持复制。</span><span class="sxs-lookup"><span data-stu-id="94b14-111">Replication is supported if each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] endpoint is within two major versions of the current version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="94b14-112">因此， [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 不支持面向或源自 [!INCLUDE[ssEW](../../includes/ssew-md.md)]的复制。</span><span class="sxs-lookup"><span data-stu-id="94b14-112">Consequently, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] does not support replication to or from [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94b14-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94b14-113">See Also</span></span>  
 [<span data-ttu-id="94b14-114">复制的向后兼容性</span><span class="sxs-lookup"><span data-stu-id="94b14-114">Replication Backward Compatibility</span></span>](replication-backward-compatibility.md)  
  
  
