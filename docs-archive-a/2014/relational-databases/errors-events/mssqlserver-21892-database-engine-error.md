---
title: MSSQLSERVER_21892 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fd3bfa1213f0569293991d6bd759619c6e7b596
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692953"
---
# <a name="mssqlserver_21892"></a><span data-ttu-id="74d53-102">MSSQLSERVER_21892</span><span class="sxs-lookup"><span data-stu-id="74d53-102">MSSQLSERVER_21892</span></span>
    
## <a name="details"></a><span data-ttu-id="74d53-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="74d53-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74d53-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="74d53-104">Product Name</span></span>|<span data-ttu-id="74d53-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="74d53-105">SQL Server</span></span>|  
|<span data-ttu-id="74d53-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="74d53-106">Event ID</span></span>|<span data-ttu-id="74d53-107">21892</span><span class="sxs-lookup"><span data-stu-id="74d53-107">21892</span></span>|  
|<span data-ttu-id="74d53-108">事件源</span><span class="sxs-lookup"><span data-stu-id="74d53-108">Event Source</span></span>|<span data-ttu-id="74d53-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="74d53-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="74d53-110">组件</span><span class="sxs-lookup"><span data-stu-id="74d53-110">Component</span></span>|<span data-ttu-id="74d53-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="74d53-111">SQLEngine</span></span>|  
|<span data-ttu-id="74d53-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="74d53-112">Symbolic Name</span></span>|<span data-ttu-id="74d53-113">SQLErrorNum21892</span><span class="sxs-lookup"><span data-stu-id="74d53-113">SQLErrorNum21892</span></span>|  
|<span data-ttu-id="74d53-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="74d53-114">Message Text</span></span>|<span data-ttu-id="74d53-115">无法在与虚拟网络名称“%s”相关联的可用性组主副本上查询 sys.availability_replicas 以获取成员副本的服务器名称：错误 = %d，错误消息 = %s。</span><span class="sxs-lookup"><span data-stu-id="74d53-115">Unable to query sys.availability_replicas at the availability group primary associated with virtual network name '%s' for the server names of the member replicas: error = %d, error message = %s.',</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="74d53-116">说明</span><span class="sxs-lookup"><span data-stu-id="74d53-116">Explanation</span></span>  
 <span data-ttu-id="74d53-117">`sp_validate_replica_hosts_as_publishers` 查询与重定向的发布服务器相关联的可用性组的当前主副本，以确定承载成员副本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="74d53-117">`sp_validate_replica_hosts_as_publishers` queries the current primary of the availability group associated with the redirected publisher, to determine the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that host the member replicas.</span></span>  <span data-ttu-id="74d53-118">当查询失败时，将返回错误 21892。</span><span class="sxs-lookup"><span data-stu-id="74d53-118">When this query fails, error 21892 is returned.</span></span>  
  
 <span data-ttu-id="74d53-119">首次使用临时链接服务器时，`sp_validate_replica_hosts_as_publishers` 通常为启用状态，因此，如果存在连接问题，这些问题可能首先与 `sp_validate_replica_hosts_as_publishers` 一起显示。</span><span class="sxs-lookup"><span data-stu-id="74d53-119">`sp_validate_replica_hosts_as_publishers` is typically on of the first use of the temporary linked server, so if there are connectivity problems they are likely to appear first with `sp_validate_replica_hosts_as_publishers`.</span></span> <span data-ttu-id="74d53-120">与 `sp_validate_redirected_publisher` 不同，`sp_validate_replica_hosts_as_publishers` 所使用的链接服务器在连接到任意可用性组副本主机时，始终使用调用方的凭据。</span><span class="sxs-lookup"><span data-stu-id="74d53-120">Unlike `sp_validate_redirected_publisher`, the linked server used by `sp_validate_replica_hosts_as_publishers` always uses the credentials of the caller when connecting to any of the availability group replica hosts.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="74d53-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="74d53-121">User Action</span></span>  
 <span data-ttu-id="74d53-122">在运行该存储过程时，请确保以对所有副本均有效的登录名运行。</span><span class="sxs-lookup"><span data-stu-id="74d53-122">When running this stored procedure, made certain that you run from a login that is valid on all of the replicas.</span></span> <span data-ttu-id="74d53-123">该登录名将要求足够的授权以查询可用性组元数据表，以及查询发布服务器数据库副本中的订阅元数据表。</span><span class="sxs-lookup"><span data-stu-id="74d53-123">The login will require sufficient authorization to query availability group metadata tables as well as to query the subscription metadata tables in the publisher database replica.</span></span>  
  
 <span data-ttu-id="74d53-124">请检查原始引用的错误，以确定失败的原因和适当的更正措施。</span><span class="sxs-lookup"><span data-stu-id="74d53-124">Examine the original referenced error to determine the cause of the failure and appropriate corrective action.</span></span>  
  
  
