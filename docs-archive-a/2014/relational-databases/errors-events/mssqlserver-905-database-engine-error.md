---
title: MSSQLSERVER_905 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7dd3c8c5a287e2d123e2a9d1430ecd49b27f29f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581235"
---
# <a name="mssqlserver_905"></a><span data-ttu-id="0a6f4-102">MSSQLSERVER_905</span><span class="sxs-lookup"><span data-stu-id="0a6f4-102">MSSQLSERVER_905</span></span>
    
## <a name="details"></a><span data-ttu-id="0a6f4-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="0a6f4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0a6f4-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="0a6f4-104">Product Name</span></span>|<span data-ttu-id="0a6f4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0a6f4-105">SQL Server</span></span>|  
|<span data-ttu-id="0a6f4-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0a6f4-106">Event ID</span></span>|<span data-ttu-id="0a6f4-107">905</span><span class="sxs-lookup"><span data-stu-id="0a6f4-107">905</span></span>|  
|<span data-ttu-id="0a6f4-108">事件源</span><span class="sxs-lookup"><span data-stu-id="0a6f4-108">Event Source</span></span>|<span data-ttu-id="0a6f4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0a6f4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0a6f4-110">组件</span><span class="sxs-lookup"><span data-stu-id="0a6f4-110">Component</span></span>|<span data-ttu-id="0a6f4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0a6f4-111">SQLEngine</span></span>|  
|<span data-ttu-id="0a6f4-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="0a6f4-112">Symbolic Name</span></span>|<span data-ttu-id="0a6f4-113">DBSTARTUP_EE_PARTITIONING</span><span class="sxs-lookup"><span data-stu-id="0a6f4-113">DBSTARTUP_EE_PARTITIONING</span></span>|  
|<span data-ttu-id="0a6f4-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="0a6f4-114">Message Text</span></span>|<span data-ttu-id="0a6f4-115">数据库 '%.\*ls' 不能在此版本的 SQL Server 中启动，因为它包含分区函数 '%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="0a6f4-115">Database '%.\*ls' cannot be started in this edition of SQL Server because it contains a partition function '%.\*ls'.</span></span> <span data-ttu-id="0a6f4-116">只有 SQL Server Enterprise Edition 支持分区。</span><span class="sxs-lookup"><span data-stu-id="0a6f4-116">Only Enterprise edition of SQL Server supports partitioning.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0a6f4-117">说明</span><span class="sxs-lookup"><span data-stu-id="0a6f4-117">Explanation</span></span>  
 <span data-ttu-id="0a6f4-118">该数据库包含一个或多个已分区表或已分区索引。</span><span class="sxs-lookup"><span data-stu-id="0a6f4-118">The database contains one or more partitioned tables or indexes.</span></span> <span data-ttu-id="0a6f4-119">此版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不能使用分区。</span><span class="sxs-lookup"><span data-stu-id="0a6f4-119">This edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot use partitioning.</span></span> <span data-ttu-id="0a6f4-120">因此，该数据库无法正常启动。</span><span class="sxs-lookup"><span data-stu-id="0a6f4-120">Therefore, the database cannot be started correctly.</span></span> <span data-ttu-id="0a6f4-121">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的各版本中均不提供已分区的表和索引。</span><span class="sxs-lookup"><span data-stu-id="0a6f4-121">Partitioned tables and indexes are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0a6f4-122">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="0a6f4-122">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0a6f4-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="0a6f4-123">User Action</span></span>  
 <span data-ttu-id="0a6f4-124">使用 sp_detach_db 存储过程分离该数据库。</span><span class="sxs-lookup"><span data-stu-id="0a6f4-124">Detach the database by using the sp_detach_db stored procedure.</span></span> <span data-ttu-id="0a6f4-125">如有需要，请移动文件，然后使用带有 FOR ATTACH 或 FOR ATTACH_REBUILD_LOG 选项的 CREATE DATABASE 将该数据库附加到受支持的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的实例。</span><span class="sxs-lookup"><span data-stu-id="0a6f4-125">Move the files if it is needed, and then attach the database to an instance of a supported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition by using the CREATE DATABASE with the FOR ATTACH or FOR ATTACH_REBUILD_LOG option.</span></span> <span data-ttu-id="0a6f4-126">对所有表禁用分区并删除分区函数。</span><span class="sxs-lookup"><span data-stu-id="0a6f4-126">Disable partitioning on all tables and remove the partitioning functions.</span></span> <span data-ttu-id="0a6f4-127">再次分离数据库，并将数据库重新附加到当前服务器。</span><span class="sxs-lookup"><span data-stu-id="0a6f4-127">Detach the database again, and reattach the database to the current server.</span></span>  
  
  
