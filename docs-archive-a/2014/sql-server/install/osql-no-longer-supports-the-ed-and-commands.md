---
title: osql 不再支持 ED 和 !! 命令 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- ED command
- osql utility [SQL Server]
- '!! command'
ms.assetid: 7cc2852f-94e8-4292-9326-c3f1a1acd281
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1ad92a32c47002c8f56e56a5b3695d42d3bdd671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587143"
---
# <a name="osql-no-longer-supports-the-ed-and--commands"></a><span data-ttu-id="b2e72-103">osql 不再支持 ED 和 !!</span><span class="sxs-lookup"><span data-stu-id="b2e72-103">osql no longer supports the ED and !!</span></span> <span data-ttu-id="b2e72-104">commands</span><span class="sxs-lookup"><span data-stu-id="b2e72-104">commands</span></span>
  <span data-ttu-id="b2e72-105">**Osql**实用工具不支持**ED**和 **！！**</span><span class="sxs-lookup"><span data-stu-id="b2e72-105">The **osql** utility does not support the **ED** and **!!**</span></span> <span data-ttu-id="b2e72-106">命令.</span><span class="sxs-lookup"><span data-stu-id="b2e72-106">commands.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="b2e72-107">纠正措施</span><span class="sxs-lookup"><span data-stu-id="b2e72-107">Corrective Action</span></span>  
 <span data-ttu-id="b2e72-108">删除对**ED**和 **！！** 的引用</span><span class="sxs-lookup"><span data-stu-id="b2e72-108">Remove references to the **ED** and **!!**</span></span> <span data-ttu-id="b2e72-109">命令的所有引用。</span><span class="sxs-lookup"><span data-stu-id="b2e72-109">commands from your scripts.</span></span>  
  
 <span data-ttu-id="b2e72-110">如果要使用**ED**和 **！！**</span><span class="sxs-lookup"><span data-stu-id="b2e72-110">If you want to use the **ED** and **!!**</span></span> <span data-ttu-id="b2e72-111">命令，请使用**sqlcmd**实用工具而不是**osql**。</span><span class="sxs-lookup"><span data-stu-id="b2e72-111">commands, use the **sqlcmd** utility instead of **osql**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e72-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2e72-112">See Also</span></span>  
 <span data-ttu-id="b2e72-113">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="b2e72-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="b2e72-114">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="b2e72-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
