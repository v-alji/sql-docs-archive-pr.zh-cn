---
title: MSSQLSERVER_21871 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f26211da21829a0a898dfb36ff9fefd453c7ad44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689395"
---
# <a name="mssqlserver_21871"></a><span data-ttu-id="5afdb-102">MSSQLSERVER_21871</span><span class="sxs-lookup"><span data-stu-id="5afdb-102">MSSQLSERVER_21871</span></span>
    
## <a name="details"></a><span data-ttu-id="5afdb-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="5afdb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5afdb-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="5afdb-104">Product Name</span></span>|<span data-ttu-id="5afdb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5afdb-105">SQL Server</span></span>|  
|<span data-ttu-id="5afdb-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5afdb-106">Event ID</span></span>|<span data-ttu-id="5afdb-107">21871</span><span class="sxs-lookup"><span data-stu-id="5afdb-107">21871</span></span>|  
|<span data-ttu-id="5afdb-108">事件源</span><span class="sxs-lookup"><span data-stu-id="5afdb-108">Event Source</span></span>|<span data-ttu-id="5afdb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5afdb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5afdb-110">组件</span><span class="sxs-lookup"><span data-stu-id="5afdb-110">Component</span></span>|<span data-ttu-id="5afdb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5afdb-111">SQLEngine</span></span>|  
|<span data-ttu-id="5afdb-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="5afdb-112">Symbolic Name</span></span>|<span data-ttu-id="5afdb-113">SQLErrorNum21871</span><span class="sxs-lookup"><span data-stu-id="5afdb-113">SQLErrorNum21871</span></span>|  
|<span data-ttu-id="5afdb-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="5afdb-114">Message Text</span></span>|<span data-ttu-id="5afdb-115">发布服务器“%s”（属于数据库“%s”）尚未重定向。</span><span class="sxs-lookup"><span data-stu-id="5afdb-115">Publisher %s of database %s has not been redirected.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5afdb-116">说明</span><span class="sxs-lookup"><span data-stu-id="5afdb-116">Explanation</span></span>  
 <span data-ttu-id="5afdb-117">`sp_validate_replica_hosts_as_publishers` 在分发数据库中检查 MSredirected_publishers 表，以查看是否存在与标识的发布服务器和发布服务器数据库对应的条目。</span><span class="sxs-lookup"><span data-stu-id="5afdb-117">`sp_validate_replica_hosts_as_publishers` checks the table MSredirected_publishers in the distribution database for an entry for the identified publisher and publisher database.</span></span>  <span data-ttu-id="5afdb-118">如果未找到条目，则 `sp_validate_replica_hosts_as_publishers` 返回错误 21871。</span><span class="sxs-lookup"><span data-stu-id="5afdb-118">`sp_validate_replica_hosts_as_publishers` returns error 21871 when no entry is found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5afdb-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="5afdb-119">User Action</span></span>  
 <span data-ttu-id="5afdb-120">`sp_validate_replica_hosts_as_publishers` 仅与重定向发布服务器有关。</span><span class="sxs-lookup"><span data-stu-id="5afdb-120">`sp_validate_replica_hosts_as_publishers` is only relevant for redirected publishers.</span></span> <span data-ttu-id="5afdb-121">如果发布服务器数据库为可用性组的成员，则使用存储过程 `sp_redirect_publisher` 将发布服务器和发布服务器数据库与可用性组的可用性组侦听器名称关联。</span><span class="sxs-lookup"><span data-stu-id="5afdb-121">If the publisher database is a member of an availability group, use the stored procedure `sp_redirect_publisher` to associate the publisher and publisher database with the Availability Group Listener Name of the availability group.</span></span>  
  
  
