---
title: 链接服务器（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB, linked servers
- OLE DB provider, linked servers
- server management [SQL Server], linked servers
- linked servers [SQL Server]
- distributed queries [SQL Server], linked servers
- servers [SQL Server], linked
- remote servers [SQL Server], linked servers
- linked servers [SQL Server], about linked servers
ms.assetid: 6ef578bf-8da7-46e0-88b5-e310fc908bb0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a1de70882cdeb87ccc0ae42aa23a9b6c8b3248e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577630"
---
# <a name="linked-servers-database-engine"></a><span data-ttu-id="cd0d2-102">链接服务器（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="cd0d2-102">Linked Servers (Database Engine)</span></span>
  <span data-ttu-id="cd0d2-103">配置链接服务器以支持 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]之外对 OLE DB 数据源执行命令。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-103">Configure a linked server to enable the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to execute commands against OLE DB data sources outside of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cd0d2-104">通常，配置链接服务器是为了支持 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 实例或诸如 Oracle 等其他数据库产品上执行包含表的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]语句。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-104">Typically linked servers are configured to enable the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to execute a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that includes tables in another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], or another database product such as Oracle.</span></span> <span data-ttu-id="cd0d2-105">许多类型的 OLE DB 数据源都可配置为链接服务器，包括 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access 和 Excel。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-105">Many types OLE DB data sources can be configured as linked servers, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access and Excel.</span></span> <span data-ttu-id="cd0d2-106">链接服务器具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="cd0d2-106">Linked servers offer the following advantages:</span></span>

-   <span data-ttu-id="cd0d2-107">能够访问 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]之外的数据。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-107">The ability to access data from outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

-   <span data-ttu-id="cd0d2-108">能够对企业内的异类数据源发出分布式查询、更新、命令和事务。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-108">The ability to issue distributed queries, updates, commands, and transactions on heterogeneous data sources across the enterprise.</span></span>

-   <span data-ttu-id="cd0d2-109">能够以相似的方式确定不同的数据源。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-109">The ability to address diverse data sources similarly.</span></span>

 <span data-ttu-id="cd0d2-110">你可以使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或 [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) 语句配置链接服务器。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-110">You can configure a linked server by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or by using the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) statement.</span></span> <span data-ttu-id="cd0d2-111">OLE DB 访问接口的类型和所需的参数的数量大不相同。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-111">OLE DB providers vary greatly in the type and number of parameters required.</span></span> <span data-ttu-id="cd0d2-112">例如，一些访问接口要求你使用 [sp_addlinkedsrvlogin (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql)之外对 OLE DB 数据源执行命令。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-112">For example some providers require you to provide a security context for the connection using [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql).</span></span> <span data-ttu-id="cd0d2-113">某些 OLE DB 访问接口允许 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 更新数据 OLE DB 源上的数据。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-113">Some OLE DB providers allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to update data on the OLE DB source.</span></span> <span data-ttu-id="cd0d2-114">其他访问接口可能仅提供只读数据访问权限。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-114">Others provide only read-only data access.</span></span> <span data-ttu-id="cd0d2-115">有关每个 OLE DB 访问接口的信息，请查看该 OLE DB 访问接口的文档。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-115">For information about each OLE DB provider, consult documentation for that OLE DB provider.</span></span>

## <a name="linked-server-components"></a><span data-ttu-id="cd0d2-116">链接服务器组件</span><span class="sxs-lookup"><span data-stu-id="cd0d2-116">Linked Server Components</span></span>
 <span data-ttu-id="cd0d2-117">链接服务器定义指定了下列对象：</span><span class="sxs-lookup"><span data-stu-id="cd0d2-117">A linked server definition specifies the following objects:</span></span>

-   <span data-ttu-id="cd0d2-118">OLE DB 访问接口</span><span class="sxs-lookup"><span data-stu-id="cd0d2-118">An OLE DB provider</span></span>

-   <span data-ttu-id="cd0d2-119">OLE DB 数据源</span><span class="sxs-lookup"><span data-stu-id="cd0d2-119">An OLE DB data source</span></span>

 <span data-ttu-id="cd0d2-120">“OLE DB 访问接口”  是管理特定数据源并与其交互的 DLL。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-120">An *OLE DB provider* is a DLL that manages and interacts with a specific data source.</span></span> <span data-ttu-id="cd0d2-121">“OLE DB 数据源”  标识可通过 OLE DB 访问的特定数据库。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-121">An *OLE DB data source* identifies the specific database that can be accessed through OLE DB.</span></span> <span data-ttu-id="cd0d2-122">虽然通过链接服务器定义查询的数据源通常是数据库，但 OLE DB 访问接口对各种文件和文件格式仍可用。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-122">Although data sources queried through linked server definitions are ordinarily databases, OLE DB providers exist for a variety of files and file formats.</span></span> <span data-ttu-id="cd0d2-123">这些文件和文件格式包括文本文件、电子表格数据和全文内容搜索的结果。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-123">These include text files, spreadsheet data, and the results of full-text content searches.</span></span>

 <span data-ttu-id="cd0d2-124">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序 (PROGID： SQLNCLI11) 是的官方 OLE DB 提供程序 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-124">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider (PROGID: SQLNCLI11) is the official OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="cd0d2-125">分布式查询旨在与任何实现所需 OLE DB 接口的 OLE DB 访问接口一起使用。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-125">distributed queries are designed to work with any OLE DB provider that implements the required OLE DB interfaces.</span></span> <span data-ttu-id="cd0d2-126">但是， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 仅针对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口和特定访问接口进行过测试。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-126">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been tested against only the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider and certain other providers.</span></span>

## <a name="linked-server-details"></a><span data-ttu-id="cd0d2-127">链接服务器详细信息</span><span class="sxs-lookup"><span data-stu-id="cd0d2-127">Linked Server Details</span></span>
 <span data-ttu-id="cd0d2-128">下图显示了链接服务器配置的基础。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-128">The following illustration shows the basics of a linked server configuration.</span></span>

 <span data-ttu-id="cd0d2-129">![客户端层、服务器层和数据库服务器层](../../database-engine/media/lsvr.gif "客户端层、服务器层和数据库服务器层")</span><span class="sxs-lookup"><span data-stu-id="cd0d2-129">![Client tier, server tier, and database server tier](../../database-engine/media/lsvr.gif "Client tier, server tier, and database server tier")</span></span>

 <span data-ttu-id="cd0d2-130">通常，链接服务器用于处理分布式查询。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-130">Typically, linked servers are used to handle distributed queries.</span></span> <span data-ttu-id="cd0d2-131">当客户端应用程序通过链接服务器执行分布式查询时， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将分析命令并向 OLE DB 发送请求。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-131">When a client application executes a distributed query through a linked server, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] parses the command and sends requests to OLE DB.</span></span> <span data-ttu-id="cd0d2-132">行集请求的形式可以是对该访问接口执行查询或从该访问接口打开基表。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-132">The rowset request may be in the form of executing a query against the provider or opening a base table from the provider.</span></span>

 <span data-ttu-id="cd0d2-133">为使数据源能通过链接服务器返回数据，该数据源的 OLE DB 访问接口 (DLL) 必须与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的实例位于同一服务器上。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-133">For a data source to return data through a linked server, the OLE DB provider (DLL) for that data source must be present on the same server as the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="cd0d2-134">使用第三方 OLE DB 访问接口时，运行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务的帐户必须具有对安装访问接口的目录及其所有子目录的读取权限和执行权限。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-134">When a third-party OLE DB provider is used, the account under which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service runs must have read and execute permissions for the directory, and all subdirectories, in which the provider is installed.</span></span>

## <a name="managing-providers"></a><span data-ttu-id="cd0d2-135">管理访问接口</span><span class="sxs-lookup"><span data-stu-id="cd0d2-135">Managing Providers</span></span>
 <span data-ttu-id="cd0d2-136">有一组选项可以控制 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如何加载和使用注册表中指定的 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-136">There is a set of options that control how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] loads and uses OLE DB providers that are specified in the registry.</span></span>

## <a name="managing-linked-server-definitions"></a><span data-ttu-id="cd0d2-137">管理链接服务器定义</span><span class="sxs-lookup"><span data-stu-id="cd0d2-137">Managing Linked Server Definitions</span></span>
 <span data-ttu-id="cd0d2-138">设置链接服务器时，请在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中注册连接信息和数据源信息。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-138">When you are setting up a linked server, register the connection information and data source information with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cd0d2-139">完成注册后，可以用单个逻辑名称来引用该数据源。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-139">After registered, that data source can be referred to with a single logical name.</span></span>

 <span data-ttu-id="cd0d2-140">可以使用存储过程和目录视图来管理链接服务器定义：</span><span class="sxs-lookup"><span data-stu-id="cd0d2-140">You can use stored procedures and catalog views to manage linked server definitions:</span></span>

-   <span data-ttu-id="cd0d2-141">通过运行 **sp_addlinkedserver**创建链接服务器定义。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-141">Create a linked server definition by running **sp_addlinkedserver**.</span></span>

-   <span data-ttu-id="cd0d2-142">通过对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sys.servers **系统目录视图执行查询，查看有关在** 的特定实例中定义的链接服务器的信息。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-142">View information about the linked servers defined in a specific instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by running a query against the **sys.servers** system catalog views.</span></span>

-   <span data-ttu-id="cd0d2-143">通过运行 **sp_dropserver**删除链接服务器定义。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-143">Delete a linked server definition by running **sp_dropserver**.</span></span> <span data-ttu-id="cd0d2-144">还可以使用此存储过程删除远程服务器。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-144">You can also use this stored procedure to remove a remote server.</span></span>

 <span data-ttu-id="cd0d2-145">还可以使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]来定义链接服务器。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-145">You can also define linked servers by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="cd0d2-146">在对象资源管理器中，右键单击“服务器对象”，选择“新建”，再选择“链接服务器”。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-146">In the Object Explorer, right-click **Server Objects**, select **New**, and select **Linked Server**.</span></span> <span data-ttu-id="cd0d2-147">通过右键单击链接服务器名称并选择“删除”，可以删除链接服务器定义。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-147">You can delete a linked server definition by right-clicking the linked server name and selecting **Delete**.</span></span>

 <span data-ttu-id="cd0d2-148">对链接服务器执行分布式查询时，请对每个要查询的数据源指定由四个部分组成的完全限定的表名。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-148">When you execute a distributed query against a linked server, include a fully qualified, four-part table name for each data source to query.</span></span> <span data-ttu-id="cd0d2-149">此由四部分组成的名称的格式应为_linked_server_name。_\*\* _`schema`_ \*\*_object_name_。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-149">This four-part name should be in the form _linked_server_name.catalog_**._`schema`_.**_object_name_.</span></span>

> [!NOTE]
>  <span data-ttu-id="cd0d2-150">可以定义链接服务器指回（环回）到在其上定义它们的服务器。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-150">Linked servers can be defined to point back (loop back) to the server on which they are defined.</span></span> <span data-ttu-id="cd0d2-151">当在单服务器网络中测试使用分布式查询的应用程序时，环回服务器是很有用的。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-151">Loopback servers are most useful when testing an application that uses distributed queries on a single server network.</span></span> <span data-ttu-id="cd0d2-152">环回链接服务器专用于测试，许多操作（如分布式事务）不支持该服务器。</span><span class="sxs-lookup"><span data-stu-id="cd0d2-152">Loopback linked servers are intended for testing and are not supported for many operations, such as distributed transactions.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="cd0d2-153">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="cd0d2-153">Related Tasks</span></span>
 [<span data-ttu-id="cd0d2-154">创建链接服务器（SQL Server 数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="cd0d2-154">Create Linked Servers &#40;SQL Server Database Engine&#41;</span></span>](create-linked-servers-sql-server-database-engine.md)

 [<span data-ttu-id="cd0d2-155">sp_addlinkedserver (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cd0d2-155">sp_addlinkedserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)

 [<span data-ttu-id="cd0d2-156">sp_addlinkedsrvlogin &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cd0d2-156">sp_addlinkedsrvlogin &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql)

 [<span data-ttu-id="cd0d2-157">sp_dropserver (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cd0d2-157">sp_dropserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropserver-transact-sql)

## <a name="related-content"></a><span data-ttu-id="cd0d2-158">相关内容</span><span class="sxs-lookup"><span data-stu-id="cd0d2-158">Related Content</span></span>
 [<span data-ttu-id="cd0d2-159">sys.servers (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cd0d2-159">sys.servers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql)

 [<span data-ttu-id="cd0d2-160">sp_linkedservers (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cd0d2-160">sp_linkedservers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql)


