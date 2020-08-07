---
title: 使用快照隔离 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], snapshot isolation
- SQLNCLI, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, snapshot isolation
- SQL Server Native Client ODBC driver, snapshot isolation
- SQL Server Native Client, snapshot isolation
- SQLGetInfo function
- concurrency [SQL Server Native Client]
- SQLSetConnectAttr function
ms.assetid: 39e87eb1-677e-45dd-bc61-83a4025a7756
author: rothja
ms.author: jroth
ms.openlocfilehash: 242d054a5fd2ad12a8811bebc834d423f547a499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589004"
---
# <a name="working-with-snapshot-isolation"></a><span data-ttu-id="ed391-102">使用快照隔离</span><span class="sxs-lookup"><span data-stu-id="ed391-102">Working with Snapshot Isolation</span></span>
  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="ed391-103">引入了旨在增强联机事务处理 (OLTP) 应用程序的并发处理能力的新“快照”隔离级别。</span><span class="sxs-lookup"><span data-stu-id="ed391-103">introduced a new "snapshot" isolation level that is intended to enhance concurrency for online transaction processing (OLTP) applications.</span></span> <span data-ttu-id="ed391-104">在早期版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，并发仅基于锁定，对于某些应用程序，这可能导致阻塞和死锁问题。</span><span class="sxs-lookup"><span data-stu-id="ed391-104">In earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], concurrency was based solely on locking, which can cause blocking and deadlocking problems for some applications.</span></span> <span data-ttu-id="ed391-105">快照隔离依赖于行版本控制的增强功能，旨在通过避免读取器-编写器阻塞情况来提高性能。</span><span class="sxs-lookup"><span data-stu-id="ed391-105">Snapshot isolation depends on enhancements to row versioning and is intended to improve performance by avoiding reader-writer blocking scenarios.</span></span>  
  
 <span data-ttu-id="ed391-106">在快照隔离下启动的事务读取该事务启动时的数据库快照。</span><span class="sxs-lookup"><span data-stu-id="ed391-106">Transactions that start under snapshot isolation read a database snapshot as of the time when the transaction starts.</span></span> <span data-ttu-id="ed391-107">一种结果是在快照事务上下文中打开的键集、动态和静态服务器游标的行为与在可序列化事务中打开的静态游标的行为非常相似。</span><span class="sxs-lookup"><span data-stu-id="ed391-107">One result of this is that keyset, dynamic and static server cursors, when opened within a snapshot transaction context, behave much like static cursors opened within serializable transactions.</span></span> <span data-ttu-id="ed391-108">但是，当在快照隔离级别下打开游标时，则不会取得锁，这会减少服务器的阻塞。</span><span class="sxs-lookup"><span data-stu-id="ed391-108">However, when the cursors are opened under the snapshot isolation level locks are not taken, which can reduce blocking on the server.</span></span>  
  
## <a name="sql-server-native-client-ole-db-provider"></a><span data-ttu-id="ed391-109">SQL Server Native Client OLE DB 访问接口</span><span class="sxs-lookup"><span data-stu-id="ed391-109">SQL Server Native Client OLE DB Provider</span></span>  
 <span data-ttu-id="ed391-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序具有充分利用中引入的快照隔离的增强功能 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ed391-110">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider has enhancements that take advantage of the snapshot isolation introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="ed391-111">这些增强功能包括对 DBPROPSET_DATASOURCEINFO 和 DBPROPSET_SESSION 属性集的更改。</span><span class="sxs-lookup"><span data-stu-id="ed391-111">These enhancements include changes to the DBPROPSET_DATASOURCEINFO and DBPROPSET_SESSION property sets.</span></span>  
  
### <a name="dbpropset_datasourceinfo"></a><span data-ttu-id="ed391-112">DBPROPSET_DATASOURCEINFO</span><span class="sxs-lookup"><span data-stu-id="ed391-112">DBPROPSET_DATASOURCEINFO</span></span>  
 <span data-ttu-id="ed391-113">已更改 DBPROPSET_DATASOURCEINFO 属性集，以便指示通过添加在 DBPROP_SUPPORTEDTXNISOLEVELS 中使用的 DBPROPVAL_TI_SNAPSHOT 值来支持快照隔离级别。</span><span class="sxs-lookup"><span data-stu-id="ed391-113">The DBPROPSET_DATASOURCEINFO property set has been changed to indicate that the snapshot isolation level is supported by the addition of the DBPROPVAL_TI_SNAPSHOT value that is used in the DBPROP_SUPPORTEDTXNISOLEVELS property.</span></span> <span data-ttu-id="ed391-114">此新值指示支持快照隔离级别，而不管是否对数据库启用了版本控制。</span><span class="sxs-lookup"><span data-stu-id="ed391-114">This new value indicates that the snapshot isolation level is supported whether or not versioning has been enabled on the database.</span></span> <span data-ttu-id="ed391-115">下面列出了 DBPROP_SUPPORTEDTXNISOLEVELS 值：</span><span class="sxs-lookup"><span data-stu-id="ed391-115">The following is a list of the DBPROP_SUPPORTEDTXNISOLEVELS values:</span></span>  
  
|<span data-ttu-id="ed391-116">属性 ID</span><span class="sxs-lookup"><span data-stu-id="ed391-116">Property ID</span></span>|<span data-ttu-id="ed391-117">说明</span><span class="sxs-lookup"><span data-stu-id="ed391-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ed391-118">DBPROP_SUPPORTEDTXNISOLEVELS</span><span class="sxs-lookup"><span data-stu-id="ed391-118">DBPROP_SUPPORTEDTXNISOLEVELS</span></span>|<span data-ttu-id="ed391-119">类型：VT_I4</span><span class="sxs-lookup"><span data-stu-id="ed391-119">Type: VT_I4</span></span><br /><br /> <span data-ttu-id="ed391-120">R/W：只读</span><span class="sxs-lookup"><span data-stu-id="ed391-120">R/W: Read only</span></span><br /><br /> <span data-ttu-id="ed391-121">说明：指定支持的事务隔离级别的位掩码。</span><span class="sxs-lookup"><span data-stu-id="ed391-121">Description: A bitmask specifying the supported transaction isolation levels.</span></span> <span data-ttu-id="ed391-122">零个或多个下列各项的组合：</span><span class="sxs-lookup"><span data-stu-id="ed391-122">A combination of zero or more of the following:</span></span><br /><br /> <span data-ttu-id="ed391-123">-DBPROPVAL_TI_CHAOS</span><span class="sxs-lookup"><span data-stu-id="ed391-123">-   DBPROPVAL_TI_CHAOS</span></span><br /><span data-ttu-id="ed391-124">-DBPROPVAL_TI_READUNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="ed391-124">-   DBPROPVAL_TI_READUNCOMMITTED</span></span><br /><span data-ttu-id="ed391-125">-DBPROPVAL_TI_BROWSE</span><span class="sxs-lookup"><span data-stu-id="ed391-125">-   DBPROPVAL_TI_BROWSE</span></span><br /><span data-ttu-id="ed391-126">-DBPROPVAL_TI_CURSORSTABILITY</span><span class="sxs-lookup"><span data-stu-id="ed391-126">-   DBPROPVAL_TI_CURSORSTABILITY</span></span><br /><span data-ttu-id="ed391-127">-DBPROPVAL_TI_READCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="ed391-127">-   DBPROPVAL_TI_READCOMMITTED</span></span><br /><span data-ttu-id="ed391-128">-DBPROPVAL_TI_REPEATABLEREAD</span><span class="sxs-lookup"><span data-stu-id="ed391-128">-   DBPROPVAL_TI_REPEATABLEREAD</span></span><br /><span data-ttu-id="ed391-129">-DBPROPVAL_TI_SERIALIZABLE</span><span class="sxs-lookup"><span data-stu-id="ed391-129">-   DBPROPVAL_TI_SERIALIZABLE</span></span><br /><span data-ttu-id="ed391-130">-DBPROPVAL_TI_ISOLATED</span><span class="sxs-lookup"><span data-stu-id="ed391-130">-   DBPROPVAL_TI_ISOLATED</span></span><br /><span data-ttu-id="ed391-131">-DBPROPVAL_TI_SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="ed391-131">-   DBPROPVAL_TI_SNAPSHOT</span></span>|  
  
### <a name="dbpropset_session"></a><span data-ttu-id="ed391-132">DBPROPSET_SESSION</span><span class="sxs-lookup"><span data-stu-id="ed391-132">DBPROPSET_SESSION</span></span>  
 <span data-ttu-id="ed391-133">已更改 DBPROPSET_SESSION 属性集，以便指示通过添加在 DBPROP_SESS_AUTOCOMMITISOLEVELS 中使用的 DBPROPVAL_TI_SNAPSHOT 值来支持快照隔离级别。</span><span class="sxs-lookup"><span data-stu-id="ed391-133">The DBPROPSET_SESSION property set has been changed to indicate that the snapshot isolation level is supported by the addition of the DBPROPVAL_TI_SNAPSHOT value that is used in the DBPROP_SESS_AUTOCOMMITISOLEVELS property.</span></span> <span data-ttu-id="ed391-134">此新值指示支持快照隔离级别，而不管是否对数据库启用了版本控制。</span><span class="sxs-lookup"><span data-stu-id="ed391-134">This new value indicates that the snapshot isolation level is supported whether or not versioning has been enabled on the database.</span></span> <span data-ttu-id="ed391-135">下面列出了 DBPROP_SESS_AUTOCOMMITISOLEVELS 值：</span><span class="sxs-lookup"><span data-stu-id="ed391-135">The following is a list of the DBPROP_SESS_AUTOCOMMITISOLEVELS values:</span></span>  
  
|<span data-ttu-id="ed391-136">属性 ID</span><span class="sxs-lookup"><span data-stu-id="ed391-136">Property ID</span></span>|<span data-ttu-id="ed391-137">说明</span><span class="sxs-lookup"><span data-stu-id="ed391-137">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ed391-138">DBPROP_SESS_AUTOCOMMITISOLEVELS</span><span class="sxs-lookup"><span data-stu-id="ed391-138">DBPROP_SESS_AUTOCOMMITISOLEVELS</span></span>|<span data-ttu-id="ed391-139">类型：VT_I4</span><span class="sxs-lookup"><span data-stu-id="ed391-139">Type: VT_I4</span></span><br /><br /> <span data-ttu-id="ed391-140">R/W：只读</span><span class="sxs-lookup"><span data-stu-id="ed391-140">R/W: Read only</span></span><br /><br /> <span data-ttu-id="ed391-141">说明：指定指示在自动提交模式下的事务隔离级别的位掩码。</span><span class="sxs-lookup"><span data-stu-id="ed391-141">Description: Specifies a bitmask that indicates the transaction isolation level while in auto-commit mode.</span></span> <span data-ttu-id="ed391-142">可在此位掩码中设置的值与可针对 DBPROP_SUPPORTEDTXNISOLEVELS 设置的值相同。</span><span class="sxs-lookup"><span data-stu-id="ed391-142">The values that can be set in this bitmask are the same as those that can be set for DBPROP_SUPPORTEDTXNISOLEVELS.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ed391-143">如果在使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 版本时设置 DBPROPVAL_TI_SNAPSHOT，将发生 DB_S_ERRORSOCCURRED 或 DB_E_ERRORSOCCURRED 错误。</span><span class="sxs-lookup"><span data-stu-id="ed391-143">The errors DB_S_ERRORSOCCURRED or DB_E_ERRORSOCCURRED will occur if DBPROPVAL_TI_SNAPSHOT is set when using versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="ed391-144">有关如何在事务中支持快照隔离的信息，请参阅[支持本地事务](../../native-client-ole-db-transactions/transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="ed391-144">For information about how snapshot isolation is supported in transactions, see [Supporting Local Transactions](../../native-client-ole-db-transactions/transactions.md).</span></span>  
  
## <a name="sql-server-native-client-odbc-driver"></a><span data-ttu-id="ed391-145">SQL Server Native Client ODBC 驱动程序</span><span class="sxs-lookup"><span data-stu-id="ed391-145">SQL Server Native Client ODBC Driver</span></span>  
 <span data-ttu-id="ed391-146">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序通过对[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)和[SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md)函数进行增强，为快照隔离提供支持。</span><span class="sxs-lookup"><span data-stu-id="ed391-146">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver provides support for snapshot isolation though enhancements made to the [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) and [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) functions.</span></span>  
  
### <a name="sqlsetconnectattr"></a><span data-ttu-id="ed391-147">SQLSetConnectAttr</span><span class="sxs-lookup"><span data-stu-id="ed391-147">SQLSetConnectAttr</span></span>  
 <span data-ttu-id="ed391-148">**SQLSetConnectAttr**函数现在支持使用 SQL_COPT_SS_TXN_ISOLATION 特性。</span><span class="sxs-lookup"><span data-stu-id="ed391-148">The **SQLSetConnectAttr** function now supports the use of the SQL_COPT_SS_TXN_ISOLATION attribute.</span></span> <span data-ttu-id="ed391-149">将 SQL_COPT_SS_TXN_ISOLATION 设置为 SQL_TXN_SS_SNAPSHOT 指示事务将在快照隔离级别下发生。</span><span class="sxs-lookup"><span data-stu-id="ed391-149">Setting SQL_COPT_SS_TXN_ISOLATION to SQL_TXN_SS_SNAPSHOT indicates that the transaction will take place under the snapshot isolation level.</span></span>  
  
### <a name="sqlgetinfo"></a><span data-ttu-id="ed391-150">SQLGetInfo</span><span class="sxs-lookup"><span data-stu-id="ed391-150">SQLGetInfo</span></span>  
 <span data-ttu-id="ed391-151">[SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md)函数现在支持已添加到 SQL_TXN_ISOLATION_OPTION 信息类型的 SQL_TXN_SS_SNAPSHOT 值。</span><span class="sxs-lookup"><span data-stu-id="ed391-151">The [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) function now supports the SQL_TXN_SS_SNAPSHOT value that has been added to the SQL_TXN_ISOLATION_OPTION info type.</span></span>  
  
 <span data-ttu-id="ed391-152">有关如何在事务中支持快照隔离的信息，请参阅[游标事务隔离级别](../../native-client-odbc-cursors/properties/cursor-transaction-isolation-level.md)。</span><span class="sxs-lookup"><span data-stu-id="ed391-152">For information about how snapshot isolation is supported in transactions, see [Cursor Transaction Isolation Level](../../native-client-odbc-cursors/properties/cursor-transaction-isolation-level.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed391-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed391-153">See Also</span></span>  
 <span data-ttu-id="ed391-154">[SQL Server Native Client 功能](sql-server-native-client-features.md) </span><span class="sxs-lookup"><span data-stu-id="ed391-154">[SQL Server Native Client Features](sql-server-native-client-features.md) </span></span>  
 [<span data-ttu-id="ed391-155">行集属性和行为</span><span class="sxs-lookup"><span data-stu-id="ed391-155">Rowset Properties and Behaviors</span></span>](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
