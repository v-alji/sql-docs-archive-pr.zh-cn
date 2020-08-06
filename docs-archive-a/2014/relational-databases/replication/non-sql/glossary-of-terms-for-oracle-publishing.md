---
title: 有关 Oracle 发布的术语词汇表 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], glossary
ms.assetid: e21dfa4b-6144-4be7-9cbf-ca2709b2bd9f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d135fb8ea3c1678f5ef31f0d7da6a717ab628999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691665"
---
# <a name="glossary-of-terms-for-oracle-publishing"></a><span data-ttu-id="470da-102">Oracle 发布的术语词汇表</span><span class="sxs-lookup"><span data-stu-id="470da-102">Glossary of Terms for Oracle Publishing</span></span>
  <span data-ttu-id="470da-103">在配置和管理 Oracle 发布时，应熟悉下列 Oracle 术语。</span><span class="sxs-lookup"><span data-stu-id="470da-103">You should be familiar with the following Oracle terms when configuring and administering Oracle publishing.</span></span> <span data-ttu-id="470da-104">有关 Oracle 术语的完整列表，请参阅 Oracle 联机文档。</span><span class="sxs-lookup"><span data-stu-id="470da-104">For a complete list of Oracle terms, see the Oracle online documentation.</span></span>  
  
 <span data-ttu-id="470da-105">索引组织表 (IOT)</span><span class="sxs-lookup"><span data-stu-id="470da-105">Index Organized Tables (IOT)</span></span>  
 <span data-ttu-id="470da-106">即数据在磁盘上按索引顺序进行物理排序的表。它类似于带有聚集索引的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="470da-106">A table whose data is physically sorted on disk in index order; it is similar to a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table with a clustered index.</span></span> <span data-ttu-id="470da-107">将 IOT 作为带有聚集索引的表复制到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="470da-107">An IOT is replicated to a Subscriber as a table with a clustered index.</span></span>  
  
 <span data-ttu-id="470da-108">实例</span><span class="sxs-lookup"><span data-stu-id="470da-108">Instance</span></span>  
 <span data-ttu-id="470da-109">Oracle 数据库是与实例相关联的。</span><span class="sxs-lookup"><span data-stu-id="470da-109">An Oracle database is associated with an instance.</span></span> <span data-ttu-id="470da-110">实例由为数据库提供支持的内存和后台进程组成。</span><span class="sxs-lookup"><span data-stu-id="470da-110">The instance comprises the memory and background processes supporting the database.</span></span> <span data-ttu-id="470da-111">Oracle 实例总是映射到单个数据库，而一个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例则可包含多个数据库。</span><span class="sxs-lookup"><span data-stu-id="470da-111">An Oracle instance always maps to a single database, whereas an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can contain many databases.</span></span> <span data-ttu-id="470da-112">有些情况下，Oracle 数据库可以具有多个实例。</span><span class="sxs-lookup"><span data-stu-id="470da-112">There are circumstances in which an Oracle database can have multiple instances.</span></span>  
  
 <span data-ttu-id="470da-113">Oracle 侦听器</span><span class="sxs-lookup"><span data-stu-id="470da-113">Oracle Listener</span></span>  
 <span data-ttu-id="470da-114">处理 Oracle 数据库实例的传入网络流量。</span><span class="sxs-lookup"><span data-stu-id="470da-114">Handles incoming network traffic for an Oracle database instance.</span></span> <span data-ttu-id="470da-115">在配置到 Oracle 数据库的网络连接时，要指定发送通信流量所使用的协议以及侦听器侦听通信流量的端口。</span><span class="sxs-lookup"><span data-stu-id="470da-115">When you configure network connectivity to an Oracle database, you specify the protocol through which traffic is sent and the port on which the Listener listens for traffic.</span></span> <span data-ttu-id="470da-116">侦听器通常配置成与 Oracle 数据库实例在同一计算机上运行，并且还可以配置成服务于一个或多个实例。</span><span class="sxs-lookup"><span data-stu-id="470da-116">The Listener is typically configured to run on the same computer as the Oracle database instance and can be configured to serve one or more instances.</span></span>  
  
 <span data-ttu-id="470da-117">ROWID</span><span class="sxs-lookup"><span data-stu-id="470da-117">ROWID</span></span>  
 <span data-ttu-id="470da-118">指向数据库中特定行位置的指针。</span><span class="sxs-lookup"><span data-stu-id="470da-118">A pointer to the location of a specific row in a database.</span></span> <span data-ttu-id="470da-119">由于使用 ROWID 检索行要比使用表扫描或索引快，所以复制在处理已发布表更改的过程中临时使用 ROWID。</span><span class="sxs-lookup"><span data-stu-id="470da-119">Because retrieving rows using the ROWID is faster than using a table scan or index, replication uses the ROWID temporarily during processing of published table changes.</span></span>  
  
 <span data-ttu-id="470da-120">序列</span><span class="sxs-lookup"><span data-stu-id="470da-120">Sequence</span></span>  
 <span data-ttu-id="470da-121">用于生成唯一编号的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="470da-121">A database object that is used to generate unique numbers.</span></span> <span data-ttu-id="470da-122">复制使用序列来为已发布表的更改排序。</span><span class="sxs-lookup"><span data-stu-id="470da-122">Replication uses sequences to order changes made to published tables.</span></span>  
  
 <span data-ttu-id="470da-123">SQL\*Plus</span><span class="sxs-lookup"><span data-stu-id="470da-123">SQL\*Plus</span></span>  
 <span data-ttu-id="470da-124">用于访问和查询 Oracle 数据库的应用程序。</span><span class="sxs-lookup"><span data-stu-id="470da-124">An application used to access and query Oracle databases.</span></span> <span data-ttu-id="470da-125">它类似于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sqlcmd  。</span><span class="sxs-lookup"><span data-stu-id="470da-125">It is similar to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sqlcmd**.</span></span>  
  
 <span data-ttu-id="470da-126">同义词</span><span class="sxs-lookup"><span data-stu-id="470da-126">Synonym</span></span>  
 <span data-ttu-id="470da-127">对象的别名。</span><span class="sxs-lookup"><span data-stu-id="470da-127">An alias for an object.</span></span> <span data-ttu-id="470da-128">配置 Oracle 发布服务器时自动创建特殊公共同义词 **MSSQLSERVERDISTRIBUTOR** 。</span><span class="sxs-lookup"><span data-stu-id="470da-128">The special public synonym **MSSQLSERVERDISTRIBUTOR** is automatically created when an Oracle Publisher is configured.</span></span> <span data-ttu-id="470da-129">该同义词引用 **HREPL_Distributor** 表，并提供一个逻辑指针指向为发布服务器服务的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器。</span><span class="sxs-lookup"><span data-stu-id="470da-129">The synonym references the **HREPL_Distributor** table and provides a logical pointer to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor that services the Publisher.</span></span>  
  
 <span data-ttu-id="470da-130">在发布 Oracle 数据库之后，再尝试将此发布服务器配置成使用不同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器就会失败，因为此公共同义词识别的分发服务器已配置为服务于发布服务器。</span><span class="sxs-lookup"><span data-stu-id="470da-130">After an Oracle database has been published, subsequent attempts to configure this Publisher to use a different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor will fail, because this public synonym identifies the particular Distributor already configured to service the Publisher.</span></span>  
  
 <span data-ttu-id="470da-131">表空间</span><span class="sxs-lookup"><span data-stu-id="470da-131">Tablespace</span></span>  
 <span data-ttu-id="470da-132">数据库存储单元，大致等同于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中的文件组。</span><span class="sxs-lookup"><span data-stu-id="470da-132">A unit of database storage that is roughly equivalent to a filegroup in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="470da-133">TNS 服务名称</span><span class="sxs-lookup"><span data-stu-id="470da-133">TNS Service Name</span></span>  
 <span data-ttu-id="470da-134">TNS（透明网络底层）是 Oracle 数据库使用的通信层。</span><span class="sxs-lookup"><span data-stu-id="470da-134">TNS (Transparent Network Substrate) is a communication layer used by Oracle databases.</span></span> <span data-ttu-id="470da-135">在网络上使用 TNS 服务名称来辨别 Oracle 数据库实例。</span><span class="sxs-lookup"><span data-stu-id="470da-135">The TNS Service Name is the name by which an Oracle database instance is known on a network.</span></span> <span data-ttu-id="470da-136">TNS 服务名称是在配置与 Oracle 数据库的连接时分配的。</span><span class="sxs-lookup"><span data-stu-id="470da-136">You assign a TNS Service Name when you configure connectivity to the Oracle database.</span></span> <span data-ttu-id="470da-137">复制使用 TNS 服务名称来识别发布服务器和建立连接。</span><span class="sxs-lookup"><span data-stu-id="470da-137">Replication uses the TNS Service name to identify the Publisher and to establish connections.</span></span>  
  
 <span data-ttu-id="470da-138">用户架构</span><span class="sxs-lookup"><span data-stu-id="470da-138">User schema</span></span>  
 <span data-ttu-id="470da-139">可以将用户架构看作拥有特定数据库对象集的用户。</span><span class="sxs-lookup"><span data-stu-id="470da-139">A user schema can be thought of as a database user who owns a particular set of database objects.</span></span> <span data-ttu-id="470da-140">复制管理用户架构拥有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制进程在 Oracle 数据库中创建的所有对象，但 **MSSQLSERVERDISTRIBUTOR** 公共同义词除外。</span><span class="sxs-lookup"><span data-stu-id="470da-140">The replication administrative user schema owns all objects created by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication process in the Oracle database, with the exception of the **MSSQLSERVERDISTRIBUTOR** public synonym.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="470da-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="470da-141">See Also</span></span>  
 <span data-ttu-id="470da-142">[配置 Oracle 发布服务器](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="470da-142">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="470da-143">[在 Oracle 发布服务器上创建的对象](objects-created-on-the-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="470da-143">[Objects Created on the Oracle Publisher](objects-created-on-the-oracle-publisher.md) </span></span>  
 <span data-ttu-id="470da-144">[非 SQL Server 发布服务器](non-sql-server-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="470da-144">[Non-SQL Server Publishers](non-sql-server-publishers.md) </span></span>  
 [<span data-ttu-id="470da-145">Oracle 发布概述</span><span class="sxs-lookup"><span data-stu-id="470da-145">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
