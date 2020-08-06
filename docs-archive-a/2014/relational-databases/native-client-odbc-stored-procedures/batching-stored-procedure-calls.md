---
title: 批处理存储过程调用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
author: rothja
ms.author: jroth
ms.openlocfilehash: a0df58ce59853ee15b863cbc7bce34041c37fee4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693820"
---
# <a name="batching-stored-procedure-calls"></a><span data-ttu-id="61a14-102">批处理存储过程调用</span><span class="sxs-lookup"><span data-stu-id="61a14-102">Batching Stored Procedure Calls</span></span>
  <span data-ttu-id="61a14-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]在适当时，Native CLIENT ODBC 驱动程序会自动将存储过程调用分批批处理到服务器。</span><span class="sxs-lookup"><span data-stu-id="61a14-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver automatically batches stored procedure calls to the server when appropriate.</span></span> <span data-ttu-id="61a14-104">只有在使用 ODBC CALL 转义序列时驱动程序才执行此操作；它并不为 [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE 语句执行此操作。</span><span class="sxs-lookup"><span data-stu-id="61a14-104">The driver only does this when the ODBC CALL escape sequence is used; it does not do this for the [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE statement.</span></span> <span data-ttu-id="61a14-105">批处理存储过程调用可以减少到服务器的往返数目，因此可以显著提高性能。</span><span class="sxs-lookup"><span data-stu-id="61a14-105">Batching stored procedure calls can reduce the number of round trips to the server and significantly increase performance.</span></span>  
  
 <span data-ttu-id="61a14-106">在执行包含多个 ODBC CALL 转义序列的批处理时，驱动程序批处理对服务器的过程调用。</span><span class="sxs-lookup"><span data-stu-id="61a14-106">The driver batches procedure calls to the server when you execute a batch that contains multiple ODBC CALL escape sequences.</span></span> <span data-ttu-id="61a14-107">它还在绑定参数数组用于 ODBC CALL 转义序列时批处理过程调用。</span><span class="sxs-lookup"><span data-stu-id="61a14-107">It also batches procedure calls when bound parameter arrays are used with an ODBC CALL escape sequence.</span></span> <span data-ttu-id="61a14-108">例如，如果你使用按行或按列的参数绑定将包含五个元素的数组绑定到 ODBC CALL SQL 语句的参数，则在调用**SQLExecute**或**SQLExecDirect**时，驱动程序会向服务器发送包含五个过程调用的单个批处理。</span><span class="sxs-lookup"><span data-stu-id="61a14-108">For example, if you use either row-wise or column-wise parameter binding to bind an array with five elements to the parameters of an ODBC CALL SQL statement, when **SQLExecute** or **SQLExecDirect** is called, the driver sends a single batch with five procedure calls to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a14-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61a14-109">See Also</span></span>  
 [<span data-ttu-id="61a14-110">运行存储过程</span><span class="sxs-lookup"><span data-stu-id="61a14-110">Running Stored Procedures</span></span>](running-stored-procedures.md)  
  
  
