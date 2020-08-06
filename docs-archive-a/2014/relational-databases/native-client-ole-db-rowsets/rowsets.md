---
title: 行集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
author: rothja
ms.author: jroth
ms.openlocfilehash: 1245d17dc0f3757b3c212146c8c162de6e48a483
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579570"
---
# <a name="rowsets"></a><span data-ttu-id="78cd5-102">行集</span><span class="sxs-lookup"><span data-stu-id="78cd5-102">Rowsets</span></span>
  <span data-ttu-id="78cd5-103">行集是一组包含数据列的行。</span><span class="sxs-lookup"><span data-stu-id="78cd5-103">A rowset is a set of rows that contain columns of data.</span></span> <span data-ttu-id="78cd5-104">行集是使所有 OLE DB 数据访问接口能够以表格形式公开结果集数据的中心对象。</span><span class="sxs-lookup"><span data-stu-id="78cd5-104">Rowsets are central objects that enable all OLE DB data providers to expose result set data in tabular form.</span></span>  
  
 <span data-ttu-id="78cd5-105">使用者使用 IDBCreateSession::CreateSession 方法创建会话之后，该使用者可以对会话使用 IOpenRowset 或 IDBCreateCommand 接口创建行集\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78cd5-105">After a consumer creates a session by using the **IDBCreateSession::CreateSession** method, the consumer can use either the **IOpenRowset** or **IDBCreateCommand** interface on the session to create a rowset.</span></span> <span data-ttu-id="78cd5-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持这两个接口。</span><span class="sxs-lookup"><span data-stu-id="78cd5-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports both of these interfaces.</span></span> <span data-ttu-id="78cd5-107">下面描述这两种方法。</span><span class="sxs-lookup"><span data-stu-id="78cd5-107">Both of these methods are described here.</span></span>  
  
-   <span data-ttu-id="78cd5-108">可调用 IOpenRowset::OpenRowset 方法来创建行集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78cd5-108">Create a rowset by calling the **IOpenRowset::OpenRowset** method.</span></span>  
  
     <span data-ttu-id="78cd5-109">这等同于通过单个表创建行集。</span><span class="sxs-lookup"><span data-stu-id="78cd5-109">This is equivalent to creating a rowset over a single table.</span></span> <span data-ttu-id="78cd5-110">该方法打开并返回行集，其中包括单个基表中的所有行。</span><span class="sxs-lookup"><span data-stu-id="78cd5-110">This method opens and returns a rowset that includes all of the rows from a single base table.</span></span> <span data-ttu-id="78cd5-111">OpenRowset 的一个参数是表 ID，它标识从其创建该行集的表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78cd5-111">One of the arguments to **OpenRowset** is a table ID that identifies the table from which to create the rowset.</span></span>  
  
-   <span data-ttu-id="78cd5-112">可调用 IDBCreateCommand::CreateCommand 方法来创建命令对象\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78cd5-112">Create a command object by calling the **IDBCreateCommand::CreateCommand** method.</span></span>  
  
     <span data-ttu-id="78cd5-113">命令对象执行提供程序所支持的命令。</span><span class="sxs-lookup"><span data-stu-id="78cd5-113">The command object executes commands that the provider supports.</span></span> <span data-ttu-id="78cd5-114">通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口，使用者可以指定任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，例如 SELECT 语句或对存储过程的调用。</span><span class="sxs-lookup"><span data-stu-id="78cd5-114">With the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the consumer can specify any [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, such as a SELECT statement or a call to a stored procedure.</span></span> <span data-ttu-id="78cd5-115">使用命令对象创建行集的步骤如下：</span><span class="sxs-lookup"><span data-stu-id="78cd5-115">The steps for creating a rowset by using a command object are:</span></span>  
  
    1.  <span data-ttu-id="78cd5-116">使用者在会话中调用 IDBCreateCommand::CreateCommand 方法，以获得一个命令对象，并请求该命令对象的 ICommandText 接口\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78cd5-116">The consumer calls the **IDBCreateCommand::CreateCommand** method on the session to get a command object requesting the **ICommandText** interface on the command object.</span></span> <span data-ttu-id="78cd5-117">此 ICommandText 接口设置并检索实际的命令文本\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78cd5-117">This **ICommandText** interface sets and retrieves the actual command text.</span></span> <span data-ttu-id="78cd5-118">使用者通过调用 ICommandText::SetCommandText 方法填充文本命令\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78cd5-118">The consumer fills in the text command by calling the **ICommandText::SetCommandText** method.</span></span>  
  
    2.  <span data-ttu-id="78cd5-119">用户调用该命令的 ICommand::Execute 方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78cd5-119">The user calls the **ICommand::Execute** method on the command.</span></span> <span data-ttu-id="78cd5-120">执行命令时生成的行集对象包含该命令产生的结果集。</span><span class="sxs-lookup"><span data-stu-id="78cd5-120">The rowset object built when the command executes contains the result set from the command.</span></span>  
  
 <span data-ttu-id="78cd5-121">使用者可以使用 ICommandProperties 接口获得或设置 ICommand::Execute 接口执行命令后返回的行集的属性\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78cd5-121">The consumer can use the **ICommandProperties** interface to get or set the properties for the rowset returned by the command executed by the **ICommand::Execute** interfaces.</span></span> <span data-ttu-id="78cd5-122">最经常请求的属性是行集必须支持的接口。</span><span class="sxs-lookup"><span data-stu-id="78cd5-122">The most commonly requested properties are the interfaces the rowset must support.</span></span> <span data-ttu-id="78cd5-123">除了接口以外，使用者还可以请求能够修改行集或接口行为的属性。</span><span class="sxs-lookup"><span data-stu-id="78cd5-123">In addition to interfaces, the consumer can request properties that modify the behavior of the rowset or interface.</span></span>  
  
 <span data-ttu-id="78cd5-124">使用者用 IRowset::Release 方法释放行集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78cd5-124">Consumers release rowsets with the **IRowset::Release** method.</span></span> <span data-ttu-id="78cd5-125">释放行集时，将释放由该行集的使用者持有的任何行控点。</span><span class="sxs-lookup"><span data-stu-id="78cd5-125">Releasing a rowset releases any row handles held by the consumer on that rowset.</span></span> <span data-ttu-id="78cd5-126">释放行集时，不会释放取值函数。</span><span class="sxs-lookup"><span data-stu-id="78cd5-126">Releasing a rowset does not release the accessors.</span></span> <span data-ttu-id="78cd5-127">即使存在 IAccessor 接口，仍必须释放它\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78cd5-127">If you have an **IAccessor** interface, it still has to be released.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78cd5-128">本节内容</span><span class="sxs-lookup"><span data-stu-id="78cd5-128">In This Section</span></span>  
  
-   [<span data-ttu-id="78cd5-129">使用 IOpenRowset 创建行集</span><span class="sxs-lookup"><span data-stu-id="78cd5-129">Creating a Rowset with IOpenRowset</span></span>](creating-a-rowset-with-iopenrowset.md)  
  
-   [<span data-ttu-id="78cd5-130">使用 ICommand::Execute 创建行集</span><span class="sxs-lookup"><span data-stu-id="78cd5-130">Creating Rowsets with ICommand::Execute</span></span>](creating-rowsets-with-icommand-execute.md)  
  
-   [<span data-ttu-id="78cd5-131">行集属性和行为</span><span class="sxs-lookup"><span data-stu-id="78cd5-131">Rowset Properties and Behaviors</span></span>](rowset-properties-and-behaviors.md)  
  
-   [<span data-ttu-id="78cd5-132">行集和 SQL Server 游标</span><span class="sxs-lookup"><span data-stu-id="78cd5-132">Rowsets and SQL Server Cursors</span></span>](rowsets-and-sql-server-cursors.md)  
  
-   [<span data-ttu-id="78cd5-133">提取行</span><span class="sxs-lookup"><span data-stu-id="78cd5-133">Fetching Rows</span></span>](fetching-rows.md)  
  
-   [<span data-ttu-id="78cd5-134">使用 IRow 提取单行</span><span class="sxs-lookup"><span data-stu-id="78cd5-134">Fetching a Single Row with IRow</span></span>](fetching-a-single-row-with-irow.md)  
  
-   <span data-ttu-id="78cd5-135">书签</span><span class="sxs-lookup"><span data-stu-id="78cd5-135">[Bookmarks](bookmarks.md)</span></span>  
  
-   [<span data-ttu-id="78cd5-136">更新行集中的数据</span><span class="sxs-lookup"><span data-stu-id="78cd5-136">Updating Data in Rowsets</span></span>](updating-data-in-rowsets.md)  
  
## <a name="see-also"></a><span data-ttu-id="78cd5-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78cd5-137">See Also</span></span>  
 [<span data-ttu-id="78cd5-138">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="78cd5-138">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
