---
title: 执行命令 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
author: rothja
ms.author: jroth
ms.openlocfilehash: 41e8da036d5a4b6469a31213247ad7d4edb7dbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589530"
---
# <a name="executing-a-command"></a><span data-ttu-id="aa76c-102">执行命令</span><span class="sxs-lookup"><span data-stu-id="aa76c-102">Executing a Command</span></span>
  <span data-ttu-id="aa76c-103">与数据源建立连接后，使用者调用 IDBCreateSession::CreateSession\*\*\*\* 方法来创建会话。</span><span class="sxs-lookup"><span data-stu-id="aa76c-103">After the connection to a data source is established, the consumer calls the **IDBCreateSession::CreateSession** method to create a session.</span></span> <span data-ttu-id="aa76c-104">该会话充当命令、行集或事务工厂。</span><span class="sxs-lookup"><span data-stu-id="aa76c-104">The session acts as a command, rowset, or transaction factory.</span></span>  
  
 <span data-ttu-id="aa76c-105">为了直接使用单独的表或索引，使用者请求 `IOpenRowset` 接口。</span><span class="sxs-lookup"><span data-stu-id="aa76c-105">To work directly with individual tables or indexes, the consumer requests the `IOpenRowset` interface.</span></span> <span data-ttu-id="aa76c-106">`IOpenRowset::OpenRowset` 方法打开并返回一个行集，该行集包括来自单个基表或索引的所有行。</span><span class="sxs-lookup"><span data-stu-id="aa76c-106">The `IOpenRowset::OpenRowset` method opens and returns a rowset that includes all rows from a single base table or index.</span></span>  
  
 <span data-ttu-id="aa76c-107">若要执行命令 (例如 SELECT \* FROM 作者) ，使用者请求 `IDBCreateCommand` 接口。</span><span class="sxs-lookup"><span data-stu-id="aa76c-107">To execute a command (such as SELECT \* FROM Authors), the consumer requests the `IDBCreateCommand` interface.</span></span> <span data-ttu-id="aa76c-108">使用者可以执行 `IDBCreateCommand::CreateCommand` 方法，以便为 `ICommandText` 接口创建一个命令对象和请求。</span><span class="sxs-lookup"><span data-stu-id="aa76c-108">The consumer can execute the `IDBCreateCommand::CreateCommand` method to create a command object and request for the `ICommandText` interface.</span></span> <span data-ttu-id="aa76c-109">`ICommandText::SetCommandText` 方法用于指定要执行的命令。</span><span class="sxs-lookup"><span data-stu-id="aa76c-109">The `ICommandText::SetCommandText` method is used to specify the command that is to be executed.</span></span>  
  
 <span data-ttu-id="aa76c-110">`Execute` 命令用于执行该命令。</span><span class="sxs-lookup"><span data-stu-id="aa76c-110">The `Execute` command is used to execute the command.</span></span> <span data-ttu-id="aa76c-111">该命令可以是任何 SQL 语句或过程名称。</span><span class="sxs-lookup"><span data-stu-id="aa76c-111">The command can be any SQL statement or procedure name.</span></span> <span data-ttu-id="aa76c-112">不是所有命令都将生成结果集（行集）对象。</span><span class="sxs-lookup"><span data-stu-id="aa76c-112">Not all commands produce a result set (rowset) object.</span></span> <span data-ttu-id="aa76c-113">SELECT \* FROM Authors 之类的命令将生成结果集。</span><span class="sxs-lookup"><span data-stu-id="aa76c-113">Commands such as SELECT \* FROM Authors produce a result set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa76c-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa76c-114">See Also</span></span>  
 [<span data-ttu-id="aa76c-115">创建 SQL Server Native Client OLE DB 访问接口应用程序</span><span class="sxs-lookup"><span data-stu-id="aa76c-115">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
