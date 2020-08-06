---
title: MSSQL_ENG014117 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014117 error
ms.assetid: e5906a76-9511-4c47-8826-8c765b58a39d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4694aacc7d1f5ee31f4ff54d8cdd4256b48f713
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576672"
---
# <a name="mssql_eng014117"></a><span data-ttu-id="65803-102">MSSQL_ENG014117</span><span class="sxs-lookup"><span data-stu-id="65803-102">MSSQL_ENG014117</span></span>
    
## <a name="message-details"></a><span data-ttu-id="65803-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="65803-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="65803-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="65803-104">Product Name</span></span>|<span data-ttu-id="65803-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="65803-105">SQL Server</span></span>|  
|<span data-ttu-id="65803-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="65803-106">Event ID</span></span>|<span data-ttu-id="65803-107">14117</span><span class="sxs-lookup"><span data-stu-id="65803-107">14117</span></span>|  
|<span data-ttu-id="65803-108">事件源</span><span class="sxs-lookup"><span data-stu-id="65803-108">Event Source</span></span>|<span data-ttu-id="65803-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="65803-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="65803-110">组件</span><span class="sxs-lookup"><span data-stu-id="65803-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="65803-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="65803-111">Symbolic Name</span></span>||  
|<span data-ttu-id="65803-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="65803-112">Message Text</span></span>|<span data-ttu-id="65803-113">未将 '%s' 配置为分发数据库。</span><span class="sxs-lookup"><span data-stu-id="65803-113">'%s' is not configured as a distribution database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="65803-114">说明</span><span class="sxs-lookup"><span data-stu-id="65803-114">Explanation</span></span>  
 <span data-ttu-id="65803-115">如果下列之一或两者均为 True，则会出现此错误：</span><span class="sxs-lookup"><span data-stu-id="65803-115">This error can occur if one or both of the following are true:</span></span>  
  
-   <span data-ttu-id="65803-116">msdb..MSdistributiondbs 中缺少指定分发数据库的条目。</span><span class="sxs-lookup"><span data-stu-id="65803-116">The entry for the specified distribution database is missing from **msdb..MSdistributiondbs**.</span></span>  
  
-   <span data-ttu-id="65803-117">在 master  数据库中没有本地服务器入口，或者存在的入口不正确。</span><span class="sxs-lookup"><span data-stu-id="65803-117">There is not an entry for the local server in the **master** database, or the entry that is there is incorrect.</span></span>  
  
     <span data-ttu-id="65803-118">复制要求一个拓扑中的所有服务器都使用具有可选实例名称的计算机名称（如果为群集实例，则为具有可选实例名称的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 虚拟服务器名称）来注册。</span><span class="sxs-lookup"><span data-stu-id="65803-118">Replication expects all servers in a topology to be registered using the computer name with an optional instance name (in the case of a clustered instance, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtual server name with the optional instance name).</span></span> <span data-ttu-id="65803-119">`SELECT @@SERVERNAME` 为拓扑中每个服务器返回的值必须与具有可选实例名称的计算机名称或虚拟服务器名称相匹配，复制才能正常运行。</span><span class="sxs-lookup"><span data-stu-id="65803-119">For replication to function properly, the value returned by `SELECT @@SERVERNAME` for each server in the topology should match the computer name or virtual server name with the optional instance name.</span></span>  
  
     <span data-ttu-id="65803-120">如果已按 IP 地址或完全限定域名 (FQDN) 注册了任意 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，将不支持复制。</span><span class="sxs-lookup"><span data-stu-id="65803-120">Replication is not supported if you have registered any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances by IP address or by Fully Qualified Domain Name (FQDN).</span></span> <span data-ttu-id="65803-121">配置复制时，如果已在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中通过 IP 地址或 FQDN 注册了任何 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 实例，则可能会引发此错误。</span><span class="sxs-lookup"><span data-stu-id="65803-121">If you had any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances registered by IP address or by FQDN in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you configured replication, this error could be raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="65803-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="65803-122">User Action</span></span>  
 <span data-ttu-id="65803-123">验证分发服务器实例正确注册。</span><span class="sxs-lookup"><span data-stu-id="65803-123">Verify that the Distributor instance is registered properly.</span></span> <span data-ttu-id="65803-124">如果计算机的网络名称和 SQL Server 实例的名称不一致，则：</span><span class="sxs-lookup"><span data-stu-id="65803-124">If the network name of the computer and the name of the SQL Server instance differ, either:</span></span>  
  
-   <span data-ttu-id="65803-125">添加 SQL Server 实例名称作为有效的网络名称。</span><span class="sxs-lookup"><span data-stu-id="65803-125">Add the SQL Server instance name as a valid network name.</span></span> <span data-ttu-id="65803-126">一种设置备用网络名称的方法是将其添加到本地主机文件中。</span><span class="sxs-lookup"><span data-stu-id="65803-126">One method to set an alternative network name is to add it to the local hosts file.</span></span> <span data-ttu-id="65803-127">默认情况下，本地宿主文件位于 WINDOWS\system32\drivers\etc 或 WINNT\system32\drivers\etc 下。有关详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="65803-127">The local hosts file is located by default at WINDOWS\system32\drivers\etc or WINNT\system32\drivers\etc. For more information, see the Windows documentation.</span></span>  
  
     <span data-ttu-id="65803-128">例如，如果计算机名称为 comp1，IP 地址为 10.193.17.129，实例名称为 inst1/instname，则将以下条目添加到主机文件中：</span><span class="sxs-lookup"><span data-stu-id="65803-128">For example, if the computer name is comp1 and the computer has an IP address of 10.193.17.129, and the instance name is inst1/instname, add the following entry to the hosts file:</span></span>  
  
     <span data-ttu-id="65803-129">10.193.17.129 inst1</span><span class="sxs-lookup"><span data-stu-id="65803-129">10.193.17.129 inst1</span></span>  
  
-   <span data-ttu-id="65803-130">禁用分发，注册实例，然后重新建立分发。</span><span class="sxs-lookup"><span data-stu-id="65803-130">Disable distribution, register the instance, and then reestablish distribution.</span></span> <span data-ttu-id="65803-131">如果 @@SERVERNAME 的值对于某个非群集实例是不正确的，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="65803-131">If the value of @@SERVERNAME is not correct for a nonclustered instance, follow these steps:</span></span>  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     <span data-ttu-id="65803-132">执行 [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) 存储过程后，必须重启 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务，对 @@SERVERNAME 的更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="65803-132">After you execute the [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) stored procedure, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service for the change to @@SERVERNAME to take effect.</span></span>  
  
     <span data-ttu-id="65803-133">如果 @@SERVERNAME 的值对于某个群集实例是不正确的，则必须使用群集管理器更改该名称。</span><span class="sxs-lookup"><span data-stu-id="65803-133">If the value of @@SERVERNAME is not correct for a clustered instance, you must change the name using Cluster Administrator.</span></span> <span data-ttu-id="65803-134">有关详细信息，请参阅 [AlwaysOn 故障转移群集实例 (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="65803-134">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
 <span data-ttu-id="65803-135">验证已正确注册分发服务器实例后，请验证分发数据库是否已在 msdb..MSdistributiondbs 中列出。</span><span class="sxs-lookup"><span data-stu-id="65803-135">After verifying that the Distributor instance is registered properly, verify that the distribution database is listed in **msdb..MSdistributiondbs**.</span></span> <span data-ttu-id="65803-136">如果未列出：</span><span class="sxs-lookup"><span data-stu-id="65803-136">If it is not listed:</span></span>  
  
1.  <span data-ttu-id="65803-137">请编写分发配置的脚本。</span><span class="sxs-lookup"><span data-stu-id="65803-137">Script out the distribution configuration.</span></span> <span data-ttu-id="65803-138">有关详细信息，请参阅 [Scripting Replication](scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="65803-138">For more information, see [Scripting Replication](scripting-replication.md).</span></span>  
  
2.  <span data-ttu-id="65803-139">禁用分发，然后重新启用它。</span><span class="sxs-lookup"><span data-stu-id="65803-139">Disable distribution and then re-enable it.</span></span> <span data-ttu-id="65803-140">有关详细信息，请参阅 [Configure Distribution](configure-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="65803-140">For more information, see [Configure Distribution](configure-distribution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65803-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65803-141">See Also</span></span>  
 [<span data-ttu-id="65803-142">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="65803-142">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
