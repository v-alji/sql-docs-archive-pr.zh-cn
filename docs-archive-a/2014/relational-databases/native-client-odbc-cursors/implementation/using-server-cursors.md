---
title: 使用服务器游标 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
author: rothja
ms.author: jroth
ms.openlocfilehash: e596af3c46849313d813ce2d7f1dab2a7425c090
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580259"
---
# <a name="using-server-cursors"></a><span data-ttu-id="440ff-102">使用服务器游标</span><span class="sxs-lookup"><span data-stu-id="440ff-102">Using Server Cursors</span></span>
  <span data-ttu-id="440ff-103">如果 ODBC 应用程序将任意 ODBC 游标属性设置为默认值以外的任何值，则 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序会请求服务器实现一个相同类型的 API 服务器游标。</span><span class="sxs-lookup"><span data-stu-id="440ff-103">If an ODBC application sets any of the ODBC cursor attributes to anything other than the defaults, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver requests the server to implement an API server cursor of the same type.</span></span> <span data-ttu-id="440ff-104">如果使用 API 服务器游标，将在客户端上释放内存，并且可以大幅减少客户端与服务器之间的网络通信量。</span><span class="sxs-lookup"><span data-stu-id="440ff-104">Using API server cursors frees memory on the client and can significantly reduce network traffic between the client and server.</span></span>  
  
 <span data-ttu-id="440ff-105">API 服务器游标的潜在缺点是它们当前不支持所有 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="440ff-105">A potential drawback of API server cursors is that they currently do not support all SQL statements.</span></span> <span data-ttu-id="440ff-106">API 服务器游标无法用于执行：</span><span class="sxs-lookup"><span data-stu-id="440ff-106">API server cursors cannot be used to execute:</span></span>  
  
-   <span data-ttu-id="440ff-107">返回多个结果集的批处理或存储过程。</span><span class="sxs-lookup"><span data-stu-id="440ff-107">Batches or stored procedures that return multiple result sets.</span></span>  
  
-   <span data-ttu-id="440ff-108">包含 COMPUTE、COMPUTE BY、FOR BROWSE 或 INTO 子句的 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="440ff-108">SELECT statements that contain COMPUTE, COMPUTE BY, FOR BROWSE, or INTO clauses.</span></span>  
  
-   <span data-ttu-id="440ff-109">引用远程存储过程的 EXECUTE 语句。</span><span class="sxs-lookup"><span data-stu-id="440ff-109">An EXECUTE statement referencing a remote stored procedure.</span></span>  
  
 <span data-ttu-id="440ff-110">连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例时，如果使用服务器游标执行具有这些特征的语句，将导致游标转换到默认结果集。</span><span class="sxs-lookup"><span data-stu-id="440ff-110">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], executing a statement with these characteristics using a server cursor causes the cursor being converted to a default result set.</span></span> <span data-ttu-id="440ff-111">连接到较早版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 时，它将导致错误。</span><span class="sxs-lookup"><span data-stu-id="440ff-111">When connected to earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it causes an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="440ff-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="440ff-112">See Also</span></span>  
 [<span data-ttu-id="440ff-113">如何实现游标</span><span class="sxs-lookup"><span data-stu-id="440ff-113">How Cursors Are Implemented</span></span>](how-cursors-are-implemented.md)  
  
  
