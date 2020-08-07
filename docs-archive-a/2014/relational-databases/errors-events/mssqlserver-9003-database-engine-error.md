---
title: MSSQLSERVER_9003 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6f67e4184ea54be6bcd5c2a74d3c0e0711b702f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588547"
---
# <a name="mssqlserver_9003"></a><span data-ttu-id="19fe8-102">MSSQLSERVER_9003</span><span class="sxs-lookup"><span data-stu-id="19fe8-102">MSSQLSERVER_9003</span></span>
    
## <a name="details"></a><span data-ttu-id="19fe8-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="19fe8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19fe8-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="19fe8-104">Product Name</span></span>|<span data-ttu-id="19fe8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="19fe8-105">SQL Server</span></span>|  
|<span data-ttu-id="19fe8-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="19fe8-106">Event ID</span></span>|<span data-ttu-id="19fe8-107">9003</span><span class="sxs-lookup"><span data-stu-id="19fe8-107">9003</span></span>|  
|<span data-ttu-id="19fe8-108">事件源</span><span class="sxs-lookup"><span data-stu-id="19fe8-108">Event Source</span></span>|<span data-ttu-id="19fe8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="19fe8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="19fe8-110">组件</span><span class="sxs-lookup"><span data-stu-id="19fe8-110">Component</span></span>|<span data-ttu-id="19fe8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="19fe8-111">SQLEngine</span></span>|  
|<span data-ttu-id="19fe8-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="19fe8-112">Symbolic Name</span></span>|<span data-ttu-id="19fe8-113">LOG_INVALID_LSN</span><span class="sxs-lookup"><span data-stu-id="19fe8-113">LOG_INVALID_LSN</span></span>|  
|<span data-ttu-id="19fe8-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="19fe8-114">Message Text</span></span>|<span data-ttu-id="19fe8-115">传递给数据库 '%.\*ls' 中的日志扫描操作的日志扫描号 %S_LSN 无效。</span><span class="sxs-lookup"><span data-stu-id="19fe8-115">The log scan number %S_LSN passed to log scan in database '%.\*ls' is not valid.</span></span> <span data-ttu-id="19fe8-116">此错误可能指示数据损坏，或者日志文件(.ldf)与数据文件(.mdf)不匹配。</span><span class="sxs-lookup"><span data-stu-id="19fe8-116">This error may indicate data corruption or that the log file (.ldf) does not match the data file (.mdf).</span></span> <span data-ttu-id="19fe8-117">如果此错误是在复制期间出现的，请重新创建发布。</span><span class="sxs-lookup"><span data-stu-id="19fe8-117">If this error occurred during replication, re-create the publication.</span></span> <span data-ttu-id="19fe8-118">否则，如果该问题导致启动期间出错，请从备份还原。</span><span class="sxs-lookup"><span data-stu-id="19fe8-118">Otherwise, restore from backup if the problem results in a failure during startup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="19fe8-119">说明</span><span class="sxs-lookup"><span data-stu-id="19fe8-119">Explanation</span></span>  
 <span data-ttu-id="19fe8-120">组件传递给数据库日志管理器的日志序列号无效。</span><span class="sxs-lookup"><span data-stu-id="19fe8-120">A component passed an invalid log sequence number to the log manager for the database.</span></span> <span data-ttu-id="19fe8-121">这可能是由于复制、损坏或主数据文件与日志不一致造成的。</span><span class="sxs-lookup"><span data-stu-id="19fe8-121">This could be replication, corruption, or an inconsistency between the primary data file and the log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="19fe8-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="19fe8-122">User Action</span></span>  
 <span data-ttu-id="19fe8-123">如果在复制期间出现这种错误，请重新创建发布。</span><span class="sxs-lookup"><span data-stu-id="19fe8-123">If this occurred during replication, recreate the publication.</span></span> <span data-ttu-id="19fe8-124">否则，请从备份还原。</span><span class="sxs-lookup"><span data-stu-id="19fe8-124">Otherwise, restore from backup.</span></span>  
  
  
