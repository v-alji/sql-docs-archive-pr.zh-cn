---
title: MSSQL_ENG014114 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014114 error
ms.assetid: f5f04590-e1c6-40d8-ab2b-98c791a0fc44
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ba2a1fde59f55eecbfeeec46555567cde964f8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576671"
---
# <a name="mssql_eng014114"></a><span data-ttu-id="8dad9-102">MSSQL_ENG014114</span><span class="sxs-lookup"><span data-stu-id="8dad9-102">MSSQL_ENG014114</span></span>
    
## <a name="message-details"></a><span data-ttu-id="8dad9-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="8dad9-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8dad9-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8dad9-104">Product Name</span></span>|<span data-ttu-id="8dad9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8dad9-105">SQL Server</span></span>|  
|<span data-ttu-id="8dad9-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8dad9-106">Event ID</span></span>|<span data-ttu-id="8dad9-107">14114</span><span class="sxs-lookup"><span data-stu-id="8dad9-107">14114</span></span>|  
|<span data-ttu-id="8dad9-108">事件源</span><span class="sxs-lookup"><span data-stu-id="8dad9-108">Event Source</span></span>|<span data-ttu-id="8dad9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8dad9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8dad9-110">组件</span><span class="sxs-lookup"><span data-stu-id="8dad9-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="8dad9-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="8dad9-111">Symbolic Name</span></span>||  
|<span data-ttu-id="8dad9-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="8dad9-112">Message Text</span></span>|<span data-ttu-id="8dad9-113">未将 '%s' 配置为分发服务器。</span><span class="sxs-lookup"><span data-stu-id="8dad9-113">'%s' is not configured as a Distributor.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8dad9-114">说明</span><span class="sxs-lookup"><span data-stu-id="8dad9-114">Explanation</span></span>  
 <span data-ttu-id="8dad9-115">如果错误消息指定某个特定实例而非“空”，则说明该指定的实例尚未正确配置，因而无法被识别为分发服务器。</span><span class="sxs-lookup"><span data-stu-id="8dad9-115">If the error message specifies a particular instance, rather than 'null', the instance specified has not been properly configured to be recognized as a Distributor.</span></span>  
  
 <span data-ttu-id="8dad9-116">如果消息指定“空”作为分发服务器，则说明 **master** 数据库中没有本地服务器项，或者该项不正确（可能因为已重命名计算机）。</span><span class="sxs-lookup"><span data-stu-id="8dad9-116">If the message specifies 'null' as a Distributor, there is no entry for the local server in **master** database, or the entry is incorrect (perhaps because the computer was renamed).</span></span> <span data-ttu-id="8dad9-117">复制要求一个拓扑中的所有服务器都使用具有可选实例名称的计算机名称（如果为群集实例，则为具有可选实例名称的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 虚拟服务器名称）来注册。</span><span class="sxs-lookup"><span data-stu-id="8dad9-117">Replication expects all servers in a topology to be registered using the computer name with an optional instance name (in the case of a clustered instance, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtual server name with the optional instance name).</span></span> <span data-ttu-id="8dad9-118">`SELECT @@SERVERNAME` 为拓扑中每个服务器返回的值必须与具有可选实例名称的计算机名称或虚拟服务器名称相匹配，复制才能正常运行。</span><span class="sxs-lookup"><span data-stu-id="8dad9-118">For replication to function properly, the value returned by `SELECT @@SERVERNAME` for each server in the topology should match the computer name or virtual server name with the optional instance name.</span></span>  
  
 <span data-ttu-id="8dad9-119">如果已按 IP 地址或完全限定域名 (FQDN) 注册了任意 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，将不支持复制。</span><span class="sxs-lookup"><span data-stu-id="8dad9-119">Replication is not supported if you have registered any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances by IP address or by Fully Qualified Domain Name (FQDN).</span></span> <span data-ttu-id="8dad9-120">配置复制时，如果已在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中通过 IP 地址或 FQDN 注册了任何 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 实例，则可能会引发此错误。</span><span class="sxs-lookup"><span data-stu-id="8dad9-120">If you had any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances registered by IP address or by FQDN in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you configured replication, this error could be raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8dad9-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="8dad9-121">User Action</span></span>  
 <span data-ttu-id="8dad9-122">如果错误消息指定一个特定实例，则将该服务器配置为分发服务器。</span><span class="sxs-lookup"><span data-stu-id="8dad9-122">If the error message specifies a particular instance, configure the server as a Distributor.</span></span> <span data-ttu-id="8dad9-123">有关详细信息，请参阅 [Configure Distribution](configure-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="8dad9-123">For more information, see [Configure Distribution](configure-distribution.md).</span></span>  
  
 <span data-ttu-id="8dad9-124">如果消息没有指定特定实例（即“空”），请确保正确注册了分发服务器实例。</span><span class="sxs-lookup"><span data-stu-id="8dad9-124">If the message does not specify a particular instance ('null'), verify that the Distributor instance is registered properly.</span></span> <span data-ttu-id="8dad9-125">如果计算机的网络名称和 SQL Server 实例的名称不一致，则：</span><span class="sxs-lookup"><span data-stu-id="8dad9-125">If the network name of the computer and the name of the SQL Server instance differ, either:</span></span>  
  
-   <span data-ttu-id="8dad9-126">添加 SQL Server 实例名称作为有效的网络名称。</span><span class="sxs-lookup"><span data-stu-id="8dad9-126">Add the SQL Server instance name as a valid network name.</span></span> <span data-ttu-id="8dad9-127">一种设置备用网络名称的方法是将其添加到本地主机文件中。</span><span class="sxs-lookup"><span data-stu-id="8dad9-127">One method to set an alternative network name is to add it to the local hosts file.</span></span> <span data-ttu-id="8dad9-128">默认情况下，本地宿主文件位于 WINDOWS\system32\drivers\etc 或 WINNT\system32\drivers\etc 下。有关详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="8dad9-128">The local hosts file is located by default at WINDOWS\system32\drivers\etc or WINNT\system32\drivers\etc. For more information, see the Windows documentation.</span></span>  
  
     <span data-ttu-id="8dad9-129">例如，如果计算机名称为 comp1，IP 地址为 10.193.17.129，实例名称为 inst1/instname，则将以下条目添加到主机文件中：</span><span class="sxs-lookup"><span data-stu-id="8dad9-129">For example, if the computer name is comp1 and the computer has an IP address of 10.193.17.129, and the instance name is inst1/instname, add the following entry to the hosts file:</span></span>  
  
     <span data-ttu-id="8dad9-130">10.193.17.129 inst1</span><span class="sxs-lookup"><span data-stu-id="8dad9-130">10.193.17.129 inst1</span></span>  
  
-   <span data-ttu-id="8dad9-131">禁用分发，注册实例，然后重新建立分发。</span><span class="sxs-lookup"><span data-stu-id="8dad9-131">Disable distribution, register the instance, and then reestablish distribution.</span></span> <span data-ttu-id="8dad9-132">如果 @@SERVERNAME 的值对于某个非群集实例是不正确的，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="8dad9-132">If the value of @@SERVERNAME is not correct for a nonclustered instance, follow these steps:</span></span>  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     <span data-ttu-id="8dad9-133">执行 [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) 存储过程后，必须重启 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务，对 @@SERVERNAME 的更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="8dad9-133">After you execute the [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) stored procedure, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service for the change to @@SERVERNAME to take effect.</span></span>  
  
     <span data-ttu-id="8dad9-134">如果 @@SERVERNAME 的值对于某个群集实例是不正确的，则必须使用群集管理器更改该名称。</span><span class="sxs-lookup"><span data-stu-id="8dad9-134">If the value of @@SERVERNAME is not correct for a clustered instance, you must change the name using Cluster Administrator.</span></span> <span data-ttu-id="8dad9-135">有关详细信息，请参阅 [AlwaysOn 故障转移群集实例 (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8dad9-135">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dad9-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8dad9-136">See Also</span></span>  
 [<span data-ttu-id="8dad9-137">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="8dad9-137">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
