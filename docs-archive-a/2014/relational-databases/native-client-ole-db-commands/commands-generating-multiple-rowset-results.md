---
title: 生成多个行集结果的命令 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- SQL Server Native Client OLE DB provider, commands
- SQL Server Native Client OLE DB provider, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
ms.assetid: 4567668d-35fd-4162-b61f-f7536862cdcb
author: rothja
ms.author: jroth
ms.openlocfilehash: 8b42a89c0b043e4c72e8b5634cf70e16b435167a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682826"
---
# <a name="commands-generating-multiple-rowset-results"></a><span data-ttu-id="1c947-102">生成多个行集结果的命令</span><span class="sxs-lookup"><span data-stu-id="1c947-102">Commands Generating Multiple-Rowset Results</span></span>
  <span data-ttu-id="1c947-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序可以从语句返回多个行集 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1c947-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can return multiple rowsets from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1c947-104">语句在以下条件下返回具有多个行集的结果：</span><span class="sxs-lookup"><span data-stu-id="1c947-104">statements return multiple-rowset results under the following conditions:</span></span>  
  
-   <span data-ttu-id="1c947-105">以单个命令的形式提交成批的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="1c947-105">Batched SQL statements are submitted as a single command.</span></span>  
  
-   <span data-ttu-id="1c947-106">存储过程实现一批 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="1c947-106">Stored procedures implement a batch of SQL statements.</span></span>  
  
## <a name="batches"></a><span data-ttu-id="1c947-107">批处理</span><span class="sxs-lookup"><span data-stu-id="1c947-107">Batches</span></span>  
 <span data-ttu-id="1c947-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序将分号字符识别为 SQL 语句的批处理分隔符：</span><span class="sxs-lookup"><span data-stu-id="1c947-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes the semicolon character as a batch delimiter for SQL statements:</span></span>  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 <span data-ttu-id="1c947-109">通过一个批处理发送多个 SQL 语句比单独执行每个 SQL 语句更有效。</span><span class="sxs-lookup"><span data-stu-id="1c947-109">Sending multiple SQL statements in one batch is more efficient than executing each SQL statement separately.</span></span> <span data-ttu-id="1c947-110">发送一个批处理减少了客户端和服务器之间的网络往返。</span><span class="sxs-lookup"><span data-stu-id="1c947-110">Sending one batch reduces the network round trips from the client to the server.</span></span>  
  
## <a name="stored-procedures"></a><span data-ttu-id="1c947-111">存储过程</span><span class="sxs-lookup"><span data-stu-id="1c947-111">Stored Procedures</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1c947-112">为存储过程中的每个语句返回一个结果集，因此大多数 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存储过程返回多个结果集。</span><span class="sxs-lookup"><span data-stu-id="1c947-112">returns a result set for each statement in a stored procedure, so most [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures return multiple result sets.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c947-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="1c947-113">In This Section</span></span>  
  
-   [<span data-ttu-id="1c947-114">使用 IMultipleResults 处理多个结果集</span><span class="sxs-lookup"><span data-stu-id="1c947-114">Using IMultipleResults to Process Multiple Result Sets</span></span>](using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a><span data-ttu-id="1c947-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c947-115">See Also</span></span>  
 [<span data-ttu-id="1c947-116">命令</span><span class="sxs-lookup"><span data-stu-id="1c947-116">Commands</span></span>](commands.md)  
  
  
