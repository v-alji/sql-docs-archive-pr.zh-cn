---
title: 使用 IMultipleResults 处理多个结果集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
author: rothja
ms.author: jroth
ms.openlocfilehash: c7acac7e6ce75189e522b503707e101c0a13c345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693280"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a><span data-ttu-id="92f33-102">使用 IMultipleResults 处理多个结果集</span><span class="sxs-lookup"><span data-stu-id="92f33-102">Using IMultipleResults to Process Multiple Result Sets</span></span>
  <span data-ttu-id="92f33-103">使用者使用**IMultipleResults**接口处理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序命令执行返回的结果。</span><span class="sxs-lookup"><span data-stu-id="92f33-103">Consumers use the **IMultipleResults** interface to process results returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider command execution.</span></span> <span data-ttu-id="92f33-104">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序提交要执行的命令时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将执行语句并返回任何结果。</span><span class="sxs-lookup"><span data-stu-id="92f33-104">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider submits a command for execution, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes the statements and returns any results.</span></span>  
  
 <span data-ttu-id="92f33-105">客户端必须处理命令执行返回的所有结果。</span><span class="sxs-lookup"><span data-stu-id="92f33-105">A client must process all results from command execution.</span></span> <span data-ttu-id="92f33-106">由于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序命令执行可以生成多个行集对象作为结果，因此，请使用**IMultipleResults**接口确保应用程序数据检索完成客户端启动的往返过程。</span><span class="sxs-lookup"><span data-stu-id="92f33-106">Because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider command execution can generate multiple-rowset objects as results, use the **IMultipleResults** interface to ensure that application data retrieval completes the client-initiated round trip.</span></span>  
  
 <span data-ttu-id="92f33-107">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句生成多个行集，某些行集包含 OrderDetails 表的行数据，某些行集包含 COMPUTE BY 子句的结果\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="92f33-107">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement generates multiple rowsets, some containing row data from the **OrderDetails** table and some containing results of the COMPUTE BY clause:</span></span>  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 <span data-ttu-id="92f33-108">如果使用者执行包含该文本的命令并请求行集作为返回的结果接口，则只返回第一组行。</span><span class="sxs-lookup"><span data-stu-id="92f33-108">If a consumer executes a command containing this text and requests a rowset as the returned results interface, only the first set of rows is returned.</span></span> <span data-ttu-id="92f33-109">使用者可以处理返回的行集中的所有行。</span><span class="sxs-lookup"><span data-stu-id="92f33-109">The consumer may process all rows in the rowset returned.</span></span> <span data-ttu-id="92f33-110">但是，如果 "DBPROP_MULTIPLECONNECTIONS 数据源" 属性设置为 "VARIANT_FALSE"，并且未在连接上启用 MARS，则不能在 session 对象上执行其他命令 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序将不会创建另一个连接) 直到取消该命令。</span><span class="sxs-lookup"><span data-stu-id="92f33-110">But, if the DBPROP_MULTIPLECONNECTIONS data source property is set to VARIANT_FALSE, and MARS is not enabled on the connection, no other commands can be executed on the session object (the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider will not create another connection) until the command is canceled.</span></span> <span data-ttu-id="92f33-111">如果在连接上未启用 MARS，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序将在 VARIANT_FALSE DBPROP_MULTIPLECONNECTIONS 时返回 DB_E_OBJECTOPEN 错误，并在存在活动事务时返回 E_FAIL。</span><span class="sxs-lookup"><span data-stu-id="92f33-111">If MARS is not enabled on the connection, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns a DB_E_OBJECTOPEN error if DBPROP_MULTIPLECONNECTIONS is VARIANT_FALSE and returns E_FAIL if there is an active transaction.</span></span>  
  
 <span data-ttu-id="92f33-112">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 调用**IMultipleResults：： GetResults**以获取下一个结果集之前，使用流式输出参数时，Native Client OLE DB 提供程序也将返回 DB_E_OBJECTOPEN，并且应用程序尚未使用所有返回的输出参数值。</span><span class="sxs-lookup"><span data-stu-id="92f33-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider will also return DB_E_OBJECTOPEN when using streamed output parameters and the application has not consumed all the returned output parameter values before calling **IMultipleResults::GetResults** to get the next result set.</span></span> <span data-ttu-id="92f33-113">如果未启用 MARS 并且连接正忙于运行的命令不生成行集或者生成的行集不是服务器游标，同时 DBPROP_MULTIPLECONNECTIONS 数据源属性设置为 VARIANT_TRUE，那么 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口将创建其他连接来支持并发命令对象，除非某个事务处于活动状态（在此情况下，将返回错误）。</span><span class="sxs-lookup"><span data-stu-id="92f33-113">If MARS is not enabled and the connection is busy running a command that does not produce a rowset or that produces a rowset that is not a server cursor, and if the DBPROP_MULTIPLECONNECTIONS data source property is set to VARIANT_TRUE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates additional connections to support concurrent command objects, unless a transaction is active, in which case it returns an error.</span></span> <span data-ttu-id="92f33-114">事务和锁定是在每个连接的基础上通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 来管理的。</span><span class="sxs-lookup"><span data-stu-id="92f33-114">Transactions and locking are managed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a per connection basis.</span></span> <span data-ttu-id="92f33-115">如果生成第二个连接，该独立连接上的命令不能共享锁定。</span><span class="sxs-lookup"><span data-stu-id="92f33-115">If a second connection is generated, the command on the separate connections does not share locks.</span></span> <span data-ttu-id="92f33-116">应通过对其他命令所请求的行保持锁定，小心确保一个命令不会阻塞另一个命令。</span><span class="sxs-lookup"><span data-stu-id="92f33-116">Care must be taken to ensure that one command does not block another by holding locks on rows requested by the other command.</span></span> <span data-ttu-id="92f33-117">如果启用 MARS，连接上可以有多个活动命令；如果使用显式事务，所有命令都共享一个公用事务。</span><span class="sxs-lookup"><span data-stu-id="92f33-117">If MARS is enabled, multiple commands can be active on the connections and if explicit transactions are being used, the commands all share a common transaction.</span></span>  
  
 <span data-ttu-id="92f33-118">使用者可以使用 [ISSAbort::Abort](../native-client-ole-db-interfaces/issabort-abort-ole-db.md) 或释放命令对象和派生行集所持有的所有引用来取消命令。</span><span class="sxs-lookup"><span data-stu-id="92f33-118">The consumer can cancel the command either by using [ISSAbort::Abort](../native-client-ole-db-interfaces/issabort-abort-ole-db.md) or by releasing all references held on the command object and the derived rowset.</span></span>  
  
 <span data-ttu-id="92f33-119">通过在所有实例中使用 IMultipleResults，使用者能够获取命令执行生成的所有行集，并正确确定何时取消命令执行和释放会话对象以供其他命令使用\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="92f33-119">Using **IMultipleResults** in all instances allows the consumer to get all rowsets generated by command execution and allows consumers to appropriately determine when to cancel command execution and free a session object for use by other commands.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92f33-120">当使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 游标时，命令执行将创建游标。</span><span class="sxs-lookup"><span data-stu-id="92f33-120">When you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors, command execution creates the cursor.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92f33-121">返回游标创建是成功还是失败；因此，与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的往返将在命令执行返回时完成。</span><span class="sxs-lookup"><span data-stu-id="92f33-121">returns success or failure on the cursor creation; therefore, the round trip to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is complete upon the return from command execution.</span></span> <span data-ttu-id="92f33-122">随后，每个 GetNextRows 调用成为一个往返\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="92f33-122">Each **GetNextRows** call then becomes a round trip.</span></span> <span data-ttu-id="92f33-123">这样，可以存在多个活动命令对象，每个对象分别处理作为服务器游标提取结果的行集。</span><span class="sxs-lookup"><span data-stu-id="92f33-123">In this way, multiple active command objects can exist, each processing a rowset that is the result of a fetch from the server cursor.</span></span> <span data-ttu-id="92f33-124">有关详细信息，请参阅[行集和 SQL Server 游标](../native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)。</span><span class="sxs-lookup"><span data-stu-id="92f33-124">For more information, see [Rowsets and SQL Server Cursors](../native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f33-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92f33-125">See Also</span></span>  
 [<span data-ttu-id="92f33-126">命令</span><span class="sxs-lookup"><span data-stu-id="92f33-126">Commands</span></span>](commands.md)  
  
  
