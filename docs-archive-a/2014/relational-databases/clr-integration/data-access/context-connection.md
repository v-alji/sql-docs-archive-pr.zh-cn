---
title: 上下文连接 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 82c739aa9c1952c71e9a16aaa68ec999851b3202
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581312"
---
# <a name="context-connection"></a><span data-ttu-id="6455f-102">上下文连接</span><span class="sxs-lookup"><span data-stu-id="6455f-102">Context Connection</span></span>
  <span data-ttu-id="6455f-103">内部数据访问问题是一种非常常见的情况。</span><span class="sxs-lookup"><span data-stu-id="6455f-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="6455f-104">即您希望访问正在执行公共语言运行时 (CLR) 存储过程或函数的相同服务器。</span><span class="sxs-lookup"><span data-stu-id="6455f-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="6455f-105">一种选择是使用 `System.Data.SqlClient.SqlConnection` 创建连接，指定指向本地服务器的连接字符串，然后打开该连接。</span><span class="sxs-lookup"><span data-stu-id="6455f-105">One option is to create a connection using `System.Data.SqlClient.SqlConnection`, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="6455f-106">这要求指定登录凭据。</span><span class="sxs-lookup"><span data-stu-id="6455f-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="6455f-107">连接与存储过程或函数处于不同的数据库会话中，它可能具有不同的 `SET` 选项，位于单独的事务中，找不到临时表等等。</span><span class="sxs-lookup"><span data-stu-id="6455f-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="6455f-108">如果托管存储过程或函数代码正在 SQL Server 进程中执行，则是因为有人连接到了该服务器并执行了 SQL 语句调用它。</span><span class="sxs-lookup"><span data-stu-id="6455f-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="6455f-109">您可能希望在该连接上下文中执行存储过程或函数，以及其事务、`SET` 选项等。</span><span class="sxs-lookup"><span data-stu-id="6455f-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="6455f-110">这称为上下文连接。</span><span class="sxs-lookup"><span data-stu-id="6455f-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="6455f-111">利用上下文连接，您可以在首先调用代码的同一上下文中执行 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="6455f-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="6455f-112">若要获取上下文连接，您必须使用“context connection”连接字符串关键字，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="6455f-112">In order to obtain the context connection, you must use the "context connection" connection string keyword, as in the example below:</span></span>  
  
 <span data-ttu-id="6455f-113">[C#]</span><span class="sxs-lookup"><span data-stu-id="6455f-113">[C#]</span></span>  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 <span data-ttu-id="6455f-114">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="6455f-114">[Visual Basic]</span></span>  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="6455f-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="6455f-115">In This Section</span></span>  
 [<span data-ttu-id="6455f-116">常规连接与上下文连接</span><span class="sxs-lookup"><span data-stu-id="6455f-116">Regular vs. Context Connections</span></span>](context-connections-vs-regular-connections.md)  
 <span data-ttu-id="6455f-117">说明常规连接和上下文连接之间的差异。</span><span class="sxs-lookup"><span data-stu-id="6455f-117">Describes the differences between regular and context connections.</span></span>  
  
 [<span data-ttu-id="6455f-118">对常规连接和上下文连接的限制</span><span class="sxs-lookup"><span data-stu-id="6455f-118">Restrictions on Regular and Context Connections</span></span>](context-connections-and-regular-connections-restrictions.md)  
 <span data-ttu-id="6455f-119">说明常规连接和上下文连接的限制。</span><span class="sxs-lookup"><span data-stu-id="6455f-119">Describes the restrictions on regular and context connections.</span></span>  
  
  
