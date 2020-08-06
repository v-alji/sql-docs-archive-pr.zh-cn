---
title: 获取有关 DDL 触发器的信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- status information [SQL Server], DDL triggers
- DDL triggers, metadata
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cd71d188c2f53bd9872359199c07d700688552d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590629"
---
# <a name="get-information-about-ddl-triggers"></a><span data-ttu-id="6c814-102">获取有关 DDL 触发器的信息</span><span class="sxs-lookup"><span data-stu-id="6c814-102">Get Information About DDL Triggers</span></span>
  <span data-ttu-id="6c814-103">本节列出的目录视图可用于获取有关 DDL 触发器的信息。</span><span class="sxs-lookup"><span data-stu-id="6c814-103">The catalog views listed in this section can be used to get information about DDL Triggers.</span></span>  
  
 <span data-ttu-id="6c814-104">**获取有关 DDL 触发器可触发的事件或事件组的信息。**</span><span class="sxs-lookup"><span data-stu-id="6c814-104">**To get information about the events or event groups on which a DDL trigger can fire.**</span></span>  
  
-   [<span data-ttu-id="6c814-105">sys.trigger_event_types (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-105">sys.trigger_event_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql)  
  
 <span data-ttu-id="6c814-106">**查看触发器的依赖关系**</span><span class="sxs-lookup"><span data-stu-id="6c814-106">**To view the dependencies of a trigger**</span></span>  
  
-   [<span data-ttu-id="6c814-107">sys.sql_expression_dependencies (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-107">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [<span data-ttu-id="6c814-108">sys.dm_sql_referenced_entities (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-108">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [<span data-ttu-id="6c814-109">sys.dm_sql_referencing_entities (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-109">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="database-scoped-ddl-triggers"></a><span data-ttu-id="6c814-110">数据库范围内的 DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="6c814-110">Database-Scoped DDL Triggers</span></span>  
 <span data-ttu-id="6c814-111">**获取有关数据库范围内的触发器的信息**</span><span class="sxs-lookup"><span data-stu-id="6c814-111">**To get information about database-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="6c814-112">sys.triggers (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-112">sys.triggers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)  
  
 <span data-ttu-id="6c814-113">**获取有关激发触发器的数据库事件的信息**</span><span class="sxs-lookup"><span data-stu-id="6c814-113">**To get information about database events that fire triggers**</span></span>  
  
-   [<span data-ttu-id="6c814-114">sys.trigger_events (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-114">sys.trigger_events &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)  
  
 <span data-ttu-id="6c814-115">**查看数据库范围内的触发器的定义**</span><span class="sxs-lookup"><span data-stu-id="6c814-115">**To view the definition of a database-scoped trigger**</span></span>  
  
-   [<span data-ttu-id="6c814-116">sys.sql_modules (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-116">sys.sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
 <span data-ttu-id="6c814-117">**获取有关 CLR 数据库范围内的触发器的信息**</span><span class="sxs-lookup"><span data-stu-id="6c814-117">**To get information about CLR database-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="6c814-118">sys.assembly_modules (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-118">sys.assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
## <a name="server-scoped-ddl-triggers"></a><span data-ttu-id="6c814-119">服务器范围内的 DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="6c814-119">Server-Scoped DDL Triggers</span></span>  
 <span data-ttu-id="6c814-120">**获取有关服务器范围内的触发器的信息**</span><span class="sxs-lookup"><span data-stu-id="6c814-120">**To get information about server-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="6c814-121">sys.server_triggers (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-121">sys.server_triggers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)  
  
 <span data-ttu-id="6c814-122">**获取有关激发触发器的服务器事件的信息**</span><span class="sxs-lookup"><span data-stu-id="6c814-122">**To get information about server events that fire triggers**</span></span>  
  
-   [<span data-ttu-id="6c814-123">sys.server_trigger_events (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-123">sys.server_trigger_events &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)  
  
 <span data-ttu-id="6c814-124">**查看服务器范围内的触发器的定义**</span><span class="sxs-lookup"><span data-stu-id="6c814-124">**To view the definition of a server-scoped trigger**</span></span>  
  
-   [<span data-ttu-id="6c814-125">sys.server_sql_modules (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-125">sys.server_sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)  
  
 <span data-ttu-id="6c814-126">**获取有关 CLR 服务器范围内的触发器的信息**</span><span class="sxs-lookup"><span data-stu-id="6c814-126">**To get information about CLR server-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="6c814-127">sys.server_assembly_modules (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c814-127">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="6c814-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c814-128">See Also</span></span>  
 [<span data-ttu-id="6c814-129">DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="6c814-129">DDL Triggers</span></span>](../triggers/ddl-triggers.md)  
  
  
