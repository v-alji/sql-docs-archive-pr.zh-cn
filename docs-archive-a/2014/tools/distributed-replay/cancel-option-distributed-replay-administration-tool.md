---
title: 取消选项（Distributed Replay 管理工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
author: stevestein
ms.author: sstein
ms.openlocfilehash: d132fbf5ce541a2bdab82e44dc55e6fc92df536d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587656"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a><span data-ttu-id="185d4-102">Cancel 选项（分布式重播管理工具）</span><span class="sxs-lookup"><span data-stu-id="185d4-102">Cancel Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="185d4-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 管理工具 `DReplay.exe` 是一个命令行工具，可用于与 Distributed Replay 控制器进行通信。</span><span class="sxs-lookup"><span data-stu-id="185d4-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="185d4-104">本主题介绍 **cancel** 命令行选项和相应的语法。</span><span class="sxs-lookup"><span data-stu-id="185d4-104">This topic describes the **cancel** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="185d4-105">**cancel** 选项取消控制器上运行的当前操作。</span><span class="sxs-lookup"><span data-stu-id="185d4-105">The **cancel** option cancels the current operation that is running on the controller.</span></span>

 <span data-ttu-id="185d4-106">![主题链接图标](../../database-engine/media/topic-link.gif "“主题链接”图标") 有关与此管理工具语法结合使用的语法约定的详细信息，请参阅 [Transact-SQL 语法约定 (Transact-SQL)](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="185d4-106">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="185d4-107">语法</span><span class="sxs-lookup"><span data-stu-id="185d4-107">Syntax</span></span>

```

dreplay cancel [-mcontroller] [-q] 
```

#### <a name="parameters"></a><span data-ttu-id="185d4-108">参数</span><span class="sxs-lookup"><span data-stu-id="185d4-108">Parameters</span></span>
 <span data-ttu-id="185d4-109">**-m** *控制器*控制器的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="185d4-109">**-m** *controller* The computer name of the controller.</span></span> <span data-ttu-id="185d4-110">可以用“`localhost`”或“`.`”指代本地计算机。</span><span class="sxs-lookup"><span data-stu-id="185d4-110">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="185d4-111">如果未指定 **-m** 参数，则使用本地计算机。</span><span class="sxs-lookup"><span data-stu-id="185d4-111">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="185d4-112">**-q**安静模式。</span><span class="sxs-lookup"><span data-stu-id="185d4-112">**-q** Quiet mode.</span></span> <span data-ttu-id="185d4-113">不提示进行确认。</span><span class="sxs-lookup"><span data-stu-id="185d4-113">Does not prompt for confirmation.</span></span>

 <span data-ttu-id="185d4-114">**-q** 参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="185d4-114">The **-q** parameter is optional.</span></span>

## <a name="examples"></a><span data-ttu-id="185d4-115">示例</span><span class="sxs-lookup"><span data-stu-id="185d4-115">Examples</span></span>
 <span data-ttu-id="185d4-116">在下面的示例中，在静默模式下提交一个取消请求。</span><span class="sxs-lookup"><span data-stu-id="185d4-116">In the following example, a cancel request is submitted in quiet mode.</span></span> <span data-ttu-id="185d4-117">值 `localhost` 表示控制器服务与管理工具在同一计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="185d4-117">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span>

```
dreplay cancel -m localhost -q
```

## <a name="permissions"></a><span data-ttu-id="185d4-118">权限</span><span class="sxs-lookup"><span data-stu-id="185d4-118">Permissions</span></span>
 <span data-ttu-id="185d4-119">您必须作为交互用户、本地用户或域用户帐户运行管理工具。</span><span class="sxs-lookup"><span data-stu-id="185d4-119">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="185d4-120">若要使用本地用户帐户，管理工具和控制器必须在同一台计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="185d4-120">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="185d4-121">有关详细信息，请参阅 [Distributed Replay Security](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="185d4-121">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="185d4-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="185d4-122">See Also</span></span>
 [<span data-ttu-id="185d4-123">SQL Server 分布式重播</span><span class="sxs-lookup"><span data-stu-id="185d4-123">SQL Server Distributed Replay</span></span>](sql-server-distributed-replay.md)


