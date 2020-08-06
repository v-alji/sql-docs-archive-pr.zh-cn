---
title: 处理存储过程结果 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
author: rothja
ms.author: jroth
ms.openlocfilehash: 5f37a6d8beff88748fa944293bd67f449d29eff2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693816"
---
# <a name="processing-stored-procedure-results"></a><span data-ttu-id="7131e-102">处理存储过程结果</span><span class="sxs-lookup"><span data-stu-id="7131e-102">Processing Stored Procedure Results</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7131e-103">存储过程具有四种用于返回数据的机制：</span><span class="sxs-lookup"><span data-stu-id="7131e-103">stored procedures have four mechanisms used to return data:</span></span>  
  
-   <span data-ttu-id="7131e-104">过程中的每一条 SELECT 语句都生成一个结果集。</span><span class="sxs-lookup"><span data-stu-id="7131e-104">Each SELECT statement in the procedure generates a result set.</span></span>  
  
-   <span data-ttu-id="7131e-105">过程可以通过输出参数返回数据。</span><span class="sxs-lookup"><span data-stu-id="7131e-105">The procedure can return data through output parameters.</span></span>  
  
-   <span data-ttu-id="7131e-106">游标输出参数可以回传 [!INCLUDE[tsql](../../includes/tsql-md.md)] 服务器游标。</span><span class="sxs-lookup"><span data-stu-id="7131e-106">A cursor output parameter can pass back a [!INCLUDE[tsql](../../includes/tsql-md.md)] server cursor.</span></span>  
  
-   <span data-ttu-id="7131e-107">过程可以具有整数返回代码。</span><span class="sxs-lookup"><span data-stu-id="7131e-107">The procedure can have an integer return code.</span></span>  
  
 <span data-ttu-id="7131e-108">应用程序必须能够处理来自存储过程的所有这些输出。</span><span class="sxs-lookup"><span data-stu-id="7131e-108">Applications must be able to handle all these outputs from stored procedures.</span></span> <span data-ttu-id="7131e-109">CALL 或 EXECUTE 语句应当包含返回代码和输出参数的参数标记。</span><span class="sxs-lookup"><span data-stu-id="7131e-109">The CALL or EXECUTE statement should include parameter markers for the return code and output parameters.</span></span> <span data-ttu-id="7131e-110">使用[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)将它们全部绑定为输出参数， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序会将输出值传输到绑定变量。</span><span class="sxs-lookup"><span data-stu-id="7131e-110">Use [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) to bind them all as output parameters and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver will transfer the output values to the bound variables.</span></span> <span data-ttu-id="7131e-111">输出参数和返回代码是返回给客户端的最后一项 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; 如果[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)返回 SQL_NO_DATA，则它们不会返回到应用程序。</span><span class="sxs-lookup"><span data-stu-id="7131e-111">Output parameters and return codes are the last items returned to the client by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; they are not returned to the application until [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) returns SQL_NO_DATA.</span></span>  
  
 <span data-ttu-id="7131e-112">ODBC 不支持绑定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 游标参数。</span><span class="sxs-lookup"><span data-stu-id="7131e-112">ODBC does not support binding [!INCLUDE[tsql](../../includes/tsql-md.md)] cursor parameters.</span></span> <span data-ttu-id="7131e-113">由于必须在执行过程之前绑定所有输出参数，因此，ODBC 应用程序无法调用包含输出游标参数的任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程。</span><span class="sxs-lookup"><span data-stu-id="7131e-113">Because all output parameters must be bound before executing a procedure, any [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure that contains an output cursor parameter cannot be called by ODBC applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7131e-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7131e-114">See Also</span></span>  
 [<span data-ttu-id="7131e-115">运行存储过程</span><span class="sxs-lookup"><span data-stu-id="7131e-115">Running Stored Procedures</span></span>](running-stored-procedures.md)  
  
  
