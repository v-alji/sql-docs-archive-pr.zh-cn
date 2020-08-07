---
title: 其他非 SQL Server 订阅服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, other types
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3849ca717e82bcf1bed5769190c9f898209a454a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576640"
---
# <a name="other-non-sql-server-subscribers"></a><span data-ttu-id="a581d-102">其他非 SQL Server 订阅服务器</span><span class="sxs-lookup"><span data-stu-id="a581d-102">Other Non-SQL Server Subscribers</span></span>
  <span data-ttu-id="a581d-103">有关[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支持的非 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]订阅服务器列表，请参阅 [Non-SQL Server Subscribers](non-sql-server-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="a581d-103">For a list of non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers supported by [!INCLUDE[msCoName](../../../includes/msconame-md.md)], see [Non-SQL Server Subscribers](non-sql-server-subscribers.md).</span></span> <span data-ttu-id="a581d-104">本主题包含有关 ODBC 驱动程序和 OLE DB 访问接口要求的信息。</span><span class="sxs-lookup"><span data-stu-id="a581d-104">This topic includes information about requirements for ODBC drivers and OLE DB providers.</span></span>  
  
## <a name="odbc-driver-requirements"></a><span data-ttu-id="a581d-105">ODBC 驱动程序要求</span><span class="sxs-lookup"><span data-stu-id="a581d-105">ODBC Driver Requirements</span></span>  
 <span data-ttu-id="a581d-106">ODBC 驱动程序：</span><span class="sxs-lookup"><span data-stu-id="a581d-106">The ODBC driver:</span></span>  
  
-   <span data-ttu-id="a581d-107">必须符合一级 ODBC (ODBC level-1)。</span><span class="sxs-lookup"><span data-stu-id="a581d-107">Must be ODBC level-1 compliant.</span></span>  
  
-   <span data-ttu-id="a581d-108">必须是线程安全的，并且适合 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器运行的处理器体系结构（Intel 或 Alpha）和平台（32 位或 64 位）。</span><span class="sxs-lookup"><span data-stu-id="a581d-108">Must be thread-safe, and for the processor architecture (Intel or Alpha) and platform (32 bit or 64 bit) on which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor runs.</span></span>  
  
-   <span data-ttu-id="a581d-109">必须有事务能力。</span><span class="sxs-lookup"><span data-stu-id="a581d-109">Must be transaction capable.</span></span>  
  
-   <span data-ttu-id="a581d-110">必须支持数据定义语言 (DDL)。</span><span class="sxs-lookup"><span data-stu-id="a581d-110">Must support the Data Definition Language (DDL).</span></span>  
  
-   <span data-ttu-id="a581d-111">不能为只读。</span><span class="sxs-lookup"><span data-stu-id="a581d-111">Cannot be read-only.</span></span>  
  
-   <span data-ttu-id="a581d-112">必须支持长表名（如 **MSreplication_subscriptions**）。</span><span class="sxs-lookup"><span data-stu-id="a581d-112">Must support long table names such as **MSreplication_subscriptions**.</span></span>  
  
## <a name="replicating-using-ole-db-interfaces"></a><span data-ttu-id="a581d-113">使用 OLE DB 接口进行复制</span><span class="sxs-lookup"><span data-stu-id="a581d-113">Replicating Using OLE DB Interfaces</span></span>  
 <span data-ttu-id="a581d-114">OLE DB 访问接口必须为事务复制支持下列对象：</span><span class="sxs-lookup"><span data-stu-id="a581d-114">OLE DB providers must support these objects for transactional replication:</span></span>  
  
-   <span data-ttu-id="a581d-115">**DataSource** 对象</span><span class="sxs-lookup"><span data-stu-id="a581d-115">**DataSource** object</span></span>  
  
-   <span data-ttu-id="a581d-116">**Session** 对象</span><span class="sxs-lookup"><span data-stu-id="a581d-116">**Session** object</span></span>  
  
-   <span data-ttu-id="a581d-117">**Command** 对象</span><span class="sxs-lookup"><span data-stu-id="a581d-117">**Command** object</span></span>  
  
-   <span data-ttu-id="a581d-118">**Rowset** 对象</span><span class="sxs-lookup"><span data-stu-id="a581d-118">**Rowset** object</span></span>  
  
-   <span data-ttu-id="a581d-119">**Error** 对象</span><span class="sxs-lookup"><span data-stu-id="a581d-119">**Error** object</span></span>  
  
### <a name="datasource-object-interfaces"></a><span data-ttu-id="a581d-120">DataSource 对象接口</span><span class="sxs-lookup"><span data-stu-id="a581d-120">DataSource Object Interfaces</span></span>  
 <span data-ttu-id="a581d-121">为了连接到数据源，需要下列接口：</span><span class="sxs-lookup"><span data-stu-id="a581d-121">The following interfaces are required to connect to a data source:</span></span>  
  
-   `IDBInitialize`  
  
-   `IDBCreateSession`  
  
-   `IDBProperties`  
  
 <span data-ttu-id="a581d-122">如果提供程序支持 **IDBInfo** 接口，则 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用该接口检索信息（如引用的标识符字符、最大 SQL 语句长度，以及表名和列名中最大字符数）。</span><span class="sxs-lookup"><span data-stu-id="a581d-122">If the provider supports the **IDBInfo** interface, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses the interface to retrieve information such as the quoted identifier character, maximum SQL statement length, and maximum number of characters in table and column names.</span></span>  
  
### <a name="session-object-interfaces"></a><span data-ttu-id="a581d-123">会话对象接口</span><span class="sxs-lookup"><span data-stu-id="a581d-123">Session Object Interfaces</span></span>  
 <span data-ttu-id="a581d-124">下列接口是必需的：</span><span class="sxs-lookup"><span data-stu-id="a581d-124">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="a581d-125">**IDBCreateCommand**</span><span class="sxs-lookup"><span data-stu-id="a581d-125">**IDBCreateCommand**</span></span>  
  
-   <span data-ttu-id="a581d-126">**ITransaction**</span><span class="sxs-lookup"><span data-stu-id="a581d-126">**ITransaction**</span></span>  
  
-   <span data-ttu-id="a581d-127">**ITransactionLocal**</span><span class="sxs-lookup"><span data-stu-id="a581d-127">**ITransactionLocal**</span></span>  
  
-   <span data-ttu-id="a581d-128">**IDBSchemaRowset**</span><span class="sxs-lookup"><span data-stu-id="a581d-128">**IDBSchemaRowset**</span></span>  
  
### <a name="command-object-interfaces"></a><span data-ttu-id="a581d-129">Command 对象接口</span><span class="sxs-lookup"><span data-stu-id="a581d-129">Command Object Interfaces</span></span>  
 <span data-ttu-id="a581d-130">下列接口是必需的：</span><span class="sxs-lookup"><span data-stu-id="a581d-130">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="a581d-131">**ICommand**</span><span class="sxs-lookup"><span data-stu-id="a581d-131">**ICommand**</span></span>  
  
-   <span data-ttu-id="a581d-132">**ICommandProperties**</span><span class="sxs-lookup"><span data-stu-id="a581d-132">**ICommandProperties**</span></span>  
  
-   <span data-ttu-id="a581d-133">**ICommandText**</span><span class="sxs-lookup"><span data-stu-id="a581d-133">**ICommandText**</span></span>  
  
-   <span data-ttu-id="a581d-134">**ICommandPrepare**</span><span class="sxs-lookup"><span data-stu-id="a581d-134">**ICommandPrepare**</span></span>  
  
-   <span data-ttu-id="a581d-135">**IColumnsInfo**</span><span class="sxs-lookup"><span data-stu-id="a581d-135">**IColumnsInfo**</span></span>  
  
-   <span data-ttu-id="a581d-136">**IAccessor**</span><span class="sxs-lookup"><span data-stu-id="a581d-136">**IAccessor**</span></span>  
  
-   <span data-ttu-id="a581d-137">**ICommandWithParameters**</span><span class="sxs-lookup"><span data-stu-id="a581d-137">**ICommandWithParameters**</span></span>  
  
 <span data-ttu-id="a581d-138">**IAccessor** 是创建参数访问器所必需的。</span><span class="sxs-lookup"><span data-stu-id="a581d-138">**IAccessor** is necessary to create parameter accessors.</span></span> <span data-ttu-id="a581d-139">如果访问接口支持**IColumnRowset**，则 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用该接口来确定列是否为标识列。</span><span class="sxs-lookup"><span data-stu-id="a581d-139">If the provider supports **IColumnRowset**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses that interface to determine whether a column is an identity column.</span></span>  
  
### <a name="rowset-object-interfaces"></a><span data-ttu-id="a581d-140">Rowset 对象接口</span><span class="sxs-lookup"><span data-stu-id="a581d-140">Rowset Object Interfaces</span></span>  
 <span data-ttu-id="a581d-141">下列接口是必需的：</span><span class="sxs-lookup"><span data-stu-id="a581d-141">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="a581d-142">**IRowset**</span><span class="sxs-lookup"><span data-stu-id="a581d-142">**IRowset**</span></span>  
  
-   <span data-ttu-id="a581d-143">**IAccessor**</span><span class="sxs-lookup"><span data-stu-id="a581d-143">**IAccessor**</span></span>  
  
-   <span data-ttu-id="a581d-144">**IColumnsInfo**</span><span class="sxs-lookup"><span data-stu-id="a581d-144">**IColumnsInfo**</span></span>  
  
 <span data-ttu-id="a581d-145">应用程序应打开在订阅数据库中创建的已复制表上的行集。</span><span class="sxs-lookup"><span data-stu-id="a581d-145">An application should open a rowset on a replicated table that is created in the subscription database.</span></span> <span data-ttu-id="a581d-146">访问行集中的数据需要**IColumnsInfo** 和 **IAccessor** 。</span><span class="sxs-lookup"><span data-stu-id="a581d-146">**IColumnsInfo** and **IAccessor** are needed to access data in the rowset.</span></span>  
  
### <a name="error-object-interfaces"></a><span data-ttu-id="a581d-147">Error 对象接口</span><span class="sxs-lookup"><span data-stu-id="a581d-147">Error Object Interfaces</span></span>  
 <span data-ttu-id="a581d-148">下列接口用于管理错误：</span><span class="sxs-lookup"><span data-stu-id="a581d-148">Use the following interfaces to manage errors:</span></span>  
  
-   <span data-ttu-id="a581d-149">**IErrorRecords**</span><span class="sxs-lookup"><span data-stu-id="a581d-149">**IErrorRecords**</span></span>  
  
-   <span data-ttu-id="a581d-150">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="a581d-150">**IErrorInfo**</span></span>  
  
 <span data-ttu-id="a581d-151">如果 OLE DB 访问接口支持 **ISQLErrorInfo** ，则使用它。</span><span class="sxs-lookup"><span data-stu-id="a581d-151">Use **ISQLErrorInfo** if it is supported by the OLE DB provider.</span></span>  
  
 <span data-ttu-id="a581d-152">有关 OLE DB 访问接口的详细信息，请参阅 OLE DB 访问接口附带的文档。</span><span class="sxs-lookup"><span data-stu-id="a581d-152">For more information about the OLE DB provider, see the documentation supplied with your OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a581d-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a581d-153">See Also</span></span>  
 [<span data-ttu-id="a581d-154">Non-SQL Server Subscribers</span><span class="sxs-lookup"><span data-stu-id="a581d-154">Non-SQL Server Subscribers</span></span>](non-sql-server-subscribers.md)  
  
  
