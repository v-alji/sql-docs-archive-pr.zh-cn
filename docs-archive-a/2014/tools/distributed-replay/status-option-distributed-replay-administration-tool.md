---
title: 状态选项（Distributed Replay 管理工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ce3d07bc357c5f3788fb6f995a43399021b3553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682550"
---
# <a name="status-option-distributed-replay-administration-tool"></a><span data-ttu-id="c74ab-102">Status 选项（分布式重播管理工具）</span><span class="sxs-lookup"><span data-stu-id="c74ab-102">Status Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="c74ab-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 管理工具 `DReplay.exe` 是一个命令行工具，可用于与 Distributed Replay 控制器进行通信。</span><span class="sxs-lookup"><span data-stu-id="c74ab-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="c74ab-104">本主题介绍 **status** 命令行选项和相应的语法。</span><span class="sxs-lookup"><span data-stu-id="c74ab-104">This topic describes the **status** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="c74ab-105">**status** 选项查询该控制器并显示当前状态。</span><span class="sxs-lookup"><span data-stu-id="c74ab-105">The **status** option queries the controller and displays the current status.</span></span>

 <span data-ttu-id="c74ab-106">![主题链接图标](../../database-engine/media/topic-link.gif "“主题链接”图标") 有关与此管理工具语法结合使用的语法约定的详细信息，请参阅 [Transact-SQL 语法约定 (Transact-SQL)](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c74ab-106">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="c74ab-107">语法</span><span class="sxs-lookup"><span data-stu-id="c74ab-107">Syntax</span></span>

```

dreplay status [-mcontroller] [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="c74ab-108">参数</span><span class="sxs-lookup"><span data-stu-id="c74ab-108">Parameters</span></span>
 <span data-ttu-id="c74ab-109">**-m** *控制器*指定控制器的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="c74ab-109">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="c74ab-110">可以用“`localhost`”或“`.`”指代本地计算机。</span><span class="sxs-lookup"><span data-stu-id="c74ab-110">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="c74ab-111">如果未指定 **-m** 参数，则使用本地计算机。</span><span class="sxs-lookup"><span data-stu-id="c74ab-111">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="c74ab-112">**-f** *status_interval*指定显示状态的频率 (以秒为) 单位）。</span><span class="sxs-lookup"><span data-stu-id="c74ab-112">**-f** *status_interval* Specifies the frequency (in seconds) at which to display the status.</span></span>

 <span data-ttu-id="c74ab-113">如果未指定 **-f** 参数，则默认间隔为 30 秒。</span><span class="sxs-lookup"><span data-stu-id="c74ab-113">If the **-f** parameter is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="c74ab-114">示例</span><span class="sxs-lookup"><span data-stu-id="c74ab-114">Examples</span></span>
 <span data-ttu-id="c74ab-115">在下面的示例中，每 60 秒显示一次当前状态。</span><span class="sxs-lookup"><span data-stu-id="c74ab-115">In the following example, the current status is displayed every 60 seconds.</span></span> <span data-ttu-id="c74ab-116">值 `localhost` 表示控制器服务与管理工具在同一计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="c74ab-116">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span>

```
dreplay status -m localhost -f 60
```

## <a name="permissions"></a><span data-ttu-id="c74ab-117">权限</span><span class="sxs-lookup"><span data-stu-id="c74ab-117">Permissions</span></span>
 <span data-ttu-id="c74ab-118">您必须作为交互用户、本地用户或域用户帐户运行管理工具。</span><span class="sxs-lookup"><span data-stu-id="c74ab-118">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="c74ab-119">若要使用本地用户帐户，管理工具和控制器必须在同一台计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="c74ab-119">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="c74ab-120">有关详细信息，请参阅 [Distributed Replay Security](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="c74ab-120">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c74ab-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c74ab-121">See Also</span></span>
 <span data-ttu-id="c74ab-122">[SQL Server Distributed Replay](sql-server-distributed-replay.md) [transact-sql 调试器](../../relational-databases/scripting/transact-sql-debugger.md)</span><span class="sxs-lookup"><span data-stu-id="c74ab-122">[SQL Server Distributed Replay](sql-server-distributed-replay.md) [Transact-SQL Debugger](../../relational-databases/scripting/transact-sql-debugger.md)</span></span>


