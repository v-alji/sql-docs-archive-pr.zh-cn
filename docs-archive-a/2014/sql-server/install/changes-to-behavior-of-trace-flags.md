---
title: 跟踪标志行为的更改 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- trace flags [SQL Server], behavior changes
ms.assetid: d739df96-2659-4383-8e10-194657632526
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11d71e8401f6b870aaeb3f64f4145b509e3a3fe0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586213"
---
# <a name="changes-to-behavior-of-trace-flags"></a><span data-ttu-id="57328-102">对跟踪标志的行为的更改</span><span class="sxs-lookup"><span data-stu-id="57328-102">Changes to behavior of trace flags</span></span>
  <span data-ttu-id="57328-103">由某个会话设置的全局跟踪标志会立即在其他会话中生效。</span><span class="sxs-lookup"><span data-stu-id="57328-103">Global trace flags set by a session take effect in other sessions immediately.</span></span> <span data-ttu-id="57328-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中的一些跟踪标志在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中是不存在的。</span><span class="sxs-lookup"><span data-stu-id="57328-104">Some trace flags from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] do not exist in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="57328-105">组件</span><span class="sxs-lookup"><span data-stu-id="57328-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="57328-106">说明</span><span class="sxs-lookup"><span data-stu-id="57328-106">Description</span></span>  
 <span data-ttu-id="57328-107">建议在升级之前先禁用所有跟踪标志。</span><span class="sxs-lookup"><span data-stu-id="57328-107">We recommend that you disable all trace flags before you upgrade.</span></span> <span data-ttu-id="57328-108">修改数据库可用性或恢复模式的跟踪标志可能会阻止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 成功升级的实例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="57328-108">Trace flags that modify the database availability or recovery modes might prevent the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] from successfully upgrading your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="57328-109">只有验证跟踪标志在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中是必需的并且仍有效之后，才能启用这些跟踪标志。</span><span class="sxs-lookup"><span data-stu-id="57328-109">You can enable the trace flags after you verify that the trace flags are required and are still valid in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="57328-110">如果必须重新启用跟踪标志，应对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例执行更多测试。</span><span class="sxs-lookup"><span data-stu-id="57328-110">If you must re-enable trace flags, you should perform additional tests on your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="57328-111">支持全局级别和会话级别的跟踪标志。</span><span class="sxs-lookup"><span data-stu-id="57328-111">supports global and session level trace flags.</span></span> <span data-ttu-id="57328-112">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中，通过在 DBCC TRACEON 命令中使用其他参数 (-1)，可以将跟踪标志指定为局部的或全局的。</span><span class="sxs-lookup"><span data-stu-id="57328-112">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], trace flags can be specified as either local or global by using an additional argument (-1) in the DBCC TRACEON command.</span></span> <span data-ttu-id="57328-113">如果未指定此参数，则默认值为局部的。</span><span class="sxs-lookup"><span data-stu-id="57328-113">If this argument is not specified, the default value is local.</span></span>  
  
 <span data-ttu-id="57328-114">此外，在中 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ，在会话 a 中设置的跟踪标志不会在现有的会话 B 中自动生效。相反，此跟踪标志仅在第一次在会话 B 中设置任何跟踪标志之后生效。此行为在和更高版本中是不确定的，在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本中，会话 A 中设置的全局跟踪标志会立即在其他并发会话中进行设置。</span><span class="sxs-lookup"><span data-stu-id="57328-114">Also, in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], a trace flag set in session A does not automatically take effect in an already existing session B. Instead, this trace flag takes effect only after the first time any trace flag is set in session B. This behavior is nondeterministic in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] and is deterministic in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, where global trace flags set in session A are set immediately in other concurrent sessions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57328-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57328-115">See Also</span></span>  
 <span data-ttu-id="57328-116">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="57328-116">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="57328-117">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="57328-117">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
