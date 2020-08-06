---
title: MSSQL_ENG014010 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014010 error
ms.assetid: 6ea84f2f-e7a2-4028-9ea9-af0d2eba660e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c3d989eb7ae78562fb77d9896545539ba4ca3c7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577555"
---
# <a name="mssql_eng014010"></a><span data-ttu-id="562dd-102">MSSQL_ENG014010</span><span class="sxs-lookup"><span data-stu-id="562dd-102">MSSQL_ENG014010</span></span>
    
## <a name="message-details"></a><span data-ttu-id="562dd-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="562dd-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="562dd-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="562dd-104">Product Name</span></span>|<span data-ttu-id="562dd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="562dd-105">SQL Server</span></span>|  
|<span data-ttu-id="562dd-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="562dd-106">Event ID</span></span>|<span data-ttu-id="562dd-107">14010</span><span class="sxs-lookup"><span data-stu-id="562dd-107">14010</span></span>|  
|<span data-ttu-id="562dd-108">事件源</span><span class="sxs-lookup"><span data-stu-id="562dd-108">Event Source</span></span>|<span data-ttu-id="562dd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="562dd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="562dd-110">组件</span><span class="sxs-lookup"><span data-stu-id="562dd-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="562dd-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="562dd-111">Symbolic Name</span></span>||  
|<span data-ttu-id="562dd-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="562dd-112">Message Text</span></span>|<span data-ttu-id="562dd-113">未将服务器“%s”定义为订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="562dd-113">The server '%s' is not defined as a subscription server.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="562dd-114">说明</span><span class="sxs-lookup"><span data-stu-id="562dd-114">Explanation</span></span>  
 <span data-ttu-id="562dd-115">复制要求一个拓扑中的所有服务器都使用具有可选实例名称的计算机名称（如果为群集实例，则为具有可选实例名称的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 虚拟服务器名称）来注册。</span><span class="sxs-lookup"><span data-stu-id="562dd-115">Replication expects all servers in a topology to be registered using the computer name with an optional instance name (in the case of a clustered instance, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtual server name with the optional instance name).</span></span> <span data-ttu-id="562dd-116">`SELECT @@SERVERNAME` 为拓扑中每个服务器返回的值必须与具有可选实例名称的计算机名称或虚拟服务器名称相匹配，复制才能正常运行。</span><span class="sxs-lookup"><span data-stu-id="562dd-116">For replication to function properly, the value returned by `SELECT @@SERVERNAME` for each server in the topology should match the computer name or virtual server name with the optional instance name.</span></span>  
  
 <span data-ttu-id="562dd-117">如果已按 IP 地址或完全限定域名 (FQDN) 注册了任意 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，将不支持复制。</span><span class="sxs-lookup"><span data-stu-id="562dd-117">Replication is not supported if you have registered any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances by IP address or by Fully Qualified Domain Name (FQDN).</span></span> <span data-ttu-id="562dd-118">配置复制时，如果已在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中通过 IP 地址或 FQDN 注册了 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 实例，则可能会引发此错误。</span><span class="sxs-lookup"><span data-stu-id="562dd-118">If you have any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances registered by IP address or by FQDN in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you configured replication, this error could be raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="562dd-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="562dd-119">User Action</span></span>  
 <span data-ttu-id="562dd-120">验证拓扑中的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例都已正确注册。</span><span class="sxs-lookup"><span data-stu-id="562dd-120">Verify that all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances in the topology are registered properly.</span></span> <span data-ttu-id="562dd-121">如果计算机的网络名称和 SQL Server 实例的名称不一致，则：</span><span class="sxs-lookup"><span data-stu-id="562dd-121">If the network name of the computer and the name of the SQL Server instance differ, either:</span></span>  
  
-   <span data-ttu-id="562dd-122">添加 SQL Server 实例名称作为有效的网络名称。</span><span class="sxs-lookup"><span data-stu-id="562dd-122">Add the SQL Server instance name as a valid network name.</span></span> <span data-ttu-id="562dd-123">一种设置备用网络名称的方法是将其添加到本地主机文件中。</span><span class="sxs-lookup"><span data-stu-id="562dd-123">One method to set an alternative network name is to add it to the local hosts file.</span></span> <span data-ttu-id="562dd-124">默认情况下，本地宿主文件位于 WINDOWS\system32\drivers\etc 或 WINNT\system32\drivers\etc 下。有关详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="562dd-124">The local hosts file is located by default at WINDOWS\system32\drivers\etc or WINNT\system32\drivers\etc. For more information, see the Windows documentation.</span></span>  
  
     <span data-ttu-id="562dd-125">例如，如果计算机名称为 comp1，IP 地址为 10.193.17.129，实例名称为 inst1/instname，则将以下条目添加到主机文件中：</span><span class="sxs-lookup"><span data-stu-id="562dd-125">For example, if the computer name is comp1 and the computer has an IP address of 10.193.17.129, and the instance name is inst1/instname, add the following entry to the hosts file:</span></span>  
  
     <span data-ttu-id="562dd-126">10.193.17.129 inst1</span><span class="sxs-lookup"><span data-stu-id="562dd-126">10.193.17.129 inst1</span></span>  
  
-   <span data-ttu-id="562dd-127">删除复制，注册每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，然后重新建立复制。</span><span class="sxs-lookup"><span data-stu-id="562dd-127">Remove replication, register each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, and then reestablish replication.</span></span> <span data-ttu-id="562dd-128">如果 @@SERVERNAME 的值对于某个非群集实例是不正确的，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="562dd-128">If the value of @@SERVERNAME is not correct for a nonclustered instance, follow these steps:</span></span>  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     <span data-ttu-id="562dd-129">执行 [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) 存储过程后，必须重启 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务，对 @@SERVERNAME 的更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="562dd-129">After you execute the [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) stored procedure, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service for the change to @@SERVERNAME to take effect.</span></span>  
  
     <span data-ttu-id="562dd-130">如果 @@SERVERNAME 的值对于某个群集实例是不正确的，则必须使用群集管理器更改该名称。</span><span class="sxs-lookup"><span data-stu-id="562dd-130">If the value of @@SERVERNAME is not correct for a clustered instance, you must change the name using Cluster Administrator.</span></span> <span data-ttu-id="562dd-131">有关详细信息，请参阅 [AlwaysOn 故障转移群集实例 (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="562dd-131">For more information, see [AlwaysOn Failover Cluster Instances &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="562dd-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="562dd-132">See Also</span></span>  
 <span data-ttu-id="562dd-133">[@@SERVERNAME (Transact-SQL)](/sql/t-sql/functions/servername-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="562dd-133">[@@SERVERNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/servername-transact-sql) </span></span>  
 [<span data-ttu-id="562dd-134">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="562dd-134">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
