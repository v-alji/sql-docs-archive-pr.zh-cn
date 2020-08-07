---
title: 在90或更高版本的兼容模式下，不允许在视图中使用 FOR BROWSE |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], FOR BROWSE clause
- FOR BROWSE clause
ms.assetid: 8f49b1c1-d877-4c46-b988-f8cdd8ac0925
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 251e0ae2ff6f19dfcff3b0f8056f6697c1bfc40d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588874"
---
# <a name="for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes"></a><span data-ttu-id="0d6ef-102">在 90 或更高的兼容模式下，视图中不允许 FOR BROWSE</span><span class="sxs-lookup"><span data-stu-id="0d6ef-102">FOR BROWSE is not allowed in views in 90 or later compatibility modes</span></span>
  <span data-ttu-id="0d6ef-103">升级顾问检测到视图中使用了 FOR BROWSE 子句。</span><span class="sxs-lookup"><span data-stu-id="0d6ef-103">Upgrade Advisor detected the use of the FOR BROWSE clause in a view.</span></span> <span data-ttu-id="0d6ef-104">当数据库兼容性模式设置为 80 时，视图中允许(并忽略) FOR BROWSE 语句。</span><span class="sxs-lookup"><span data-stu-id="0d6ef-104">The FOR BROWSE clause is allowed (and ignored) in views when the database compatibility mode is set to 80.</span></span> <span data-ttu-id="0d6ef-105">当数据库兼容模式设置为 90 或更高时，视图中不允许使用 FOR BROWSE 子句。</span><span class="sxs-lookup"><span data-stu-id="0d6ef-105">The FOR BROWSE clause is not allowed in views when the database compatibility mode is set to 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="0d6ef-106">组件</span><span class="sxs-lookup"><span data-stu-id="0d6ef-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="0d6ef-107">纠正措施</span><span class="sxs-lookup"><span data-stu-id="0d6ef-107">Corrective Action</span></span>  
 <span data-ttu-id="0d6ef-108">升级时，用户数据库将保持其兼容模式。</span><span class="sxs-lookup"><span data-stu-id="0d6ef-108">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="0d6ef-109">将数据库兼容模式更改为 90 或更高的兼容模式之前，请从视图定义中删除 FOR BROWSE 子句。</span><span class="sxs-lookup"><span data-stu-id="0d6ef-109">Before you change the database compatibility mode to 90 or later, remove the FOR BROWSE clause from view definitions.</span></span> <span data-ttu-id="0d6ef-110">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“sp_dbcmptlevel”。</span><span class="sxs-lookup"><span data-stu-id="0d6ef-110">For more information, see "sp_dbcmptlevel" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6ef-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d6ef-111">See Also</span></span>  
 <span data-ttu-id="0d6ef-112">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="0d6ef-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="0d6ef-113">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="0d6ef-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
