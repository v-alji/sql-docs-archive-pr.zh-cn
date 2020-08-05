---
title: MSSQLSERVER_9004 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 910665b4349e5b13c5abb4fd687dcf0c6fc122cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581236"
---
# <a name="mssqlserver_9004"></a><span data-ttu-id="f037d-102">MSSQLSERVER_9004</span><span class="sxs-lookup"><span data-stu-id="f037d-102">MSSQLSERVER_9004</span></span>
    
## <a name="details"></a><span data-ttu-id="f037d-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="f037d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f037d-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="f037d-104">Product Name</span></span>|<span data-ttu-id="f037d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f037d-105">SQL Server</span></span>|  
|<span data-ttu-id="f037d-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f037d-106">Event ID</span></span>|<span data-ttu-id="f037d-107">9004</span><span class="sxs-lookup"><span data-stu-id="f037d-107">9004</span></span>|  
|<span data-ttu-id="f037d-108">事件源</span><span class="sxs-lookup"><span data-stu-id="f037d-108">Event Source</span></span>|<span data-ttu-id="f037d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f037d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f037d-110">组件</span><span class="sxs-lookup"><span data-stu-id="f037d-110">Component</span></span>|<span data-ttu-id="f037d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f037d-111">SQLEngine</span></span>|  
|<span data-ttu-id="f037d-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="f037d-112">Symbolic Name</span></span>|<span data-ttu-id="f037d-113">LOG_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="f037d-113">LOG_CORRUPT</span></span>|  
|<span data-ttu-id="f037d-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="f037d-114">Message Text</span></span>|<span data-ttu-id="f037d-115">处理数据库 '%.\*ls' 的日志时出错。</span><span class="sxs-lookup"><span data-stu-id="f037d-115">An error occurred while processing the log for database '%.\*ls'.</span></span>  <span data-ttu-id="f037d-116">如果可能，请从备份还原。</span><span class="sxs-lookup"><span data-stu-id="f037d-116">If possible, restore from backup.</span></span> <span data-ttu-id="f037d-117">如果没有可用备份，可能需要重新生成日志。</span><span class="sxs-lookup"><span data-stu-id="f037d-117">If a backup is not available, it might be necessary to rebuild the log.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f037d-118">说明</span><span class="sxs-lookup"><span data-stu-id="f037d-118">Explanation</span></span>  
 <span data-ttu-id="f037d-119">在回滚、恢复或复制期间处理日志时出错。</span><span class="sxs-lookup"><span data-stu-id="f037d-119">An error was encountered while processing the log during rollback, recovery, or replication.</span></span> <span data-ttu-id="f037d-120">这可能表明操作系统检测到错误，或者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 检测到内部一致性错误。</span><span class="sxs-lookup"><span data-stu-id="f037d-120">This could indicate an error detected by the operating system-or an internal consistency error detected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f037d-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="f037d-121">User Action</span></span>  
 <span data-ttu-id="f037d-122">执行以下操作之一将更正此错误：</span><span class="sxs-lookup"><span data-stu-id="f037d-122">One of the following actions will correct this error:</span></span>  
  
-   <span data-ttu-id="f037d-123">从备份还原。</span><span class="sxs-lookup"><span data-stu-id="f037d-123">Restore from a backup.</span></span>  
  
-   <span data-ttu-id="f037d-124">重新生成日志。</span><span class="sxs-lookup"><span data-stu-id="f037d-124">Rebuild the log.</span></span>  
  
 <span data-ttu-id="f037d-125">此外，检查系统事件和错误日志以识别系统内可能导致该错误的问题。</span><span class="sxs-lookup"><span data-stu-id="f037d-125">Also, check system event and error logs to identify issues within the system that may have caused the problem.</span></span>  
  
  
