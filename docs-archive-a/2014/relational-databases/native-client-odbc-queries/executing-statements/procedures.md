---
title: 过程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: rothja
ms.author: jroth
ms.openlocfilehash: a7ae4678d324ba7d07ae429793b1f75b57bb15e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577597"
---
# <a name="procedures"></a><span data-ttu-id="72be3-102">过程</span><span class="sxs-lookup"><span data-stu-id="72be3-102">Procedures</span></span>
  <span data-ttu-id="72be3-103">存储过程是包含一个或多个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句的预先编译的可执行对象。</span><span class="sxs-lookup"><span data-stu-id="72be3-103">A stored procedure is a precompiled executable object that contains one or more [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="72be3-104">存储过程可具有输入和输出参数，并且还可以生成整数返回代码。</span><span class="sxs-lookup"><span data-stu-id="72be3-104">Stored procedures can have input and output parameters and can also put out an integer return code.</span></span> <span data-ttu-id="72be3-105">应用程序可以通过使用目录函数枚举可用的存储过程。</span><span class="sxs-lookup"><span data-stu-id="72be3-105">An application can enumerate available stored procedures by using catalog functions.</span></span>  
  
 <span data-ttu-id="72be3-106">以 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 为目标的 ODBC 应用程序只应使用直接执行以调用某一存储过程。</span><span class="sxs-lookup"><span data-stu-id="72be3-106">ODBC applications that target [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] should only use direct execution to call a stored procedure.</span></span> <span data-ttu-id="72be3-107">当连接到的早期版本时 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驱动程序通过创建一个临时存储过程来实现[SQLPrepare 函数](https://go.microsoft.com/fwlink/?LinkId=59360)，然后在**SQLExecute**上调用该存储过程。</span><span class="sxs-lookup"><span data-stu-id="72be3-107">When connected to earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver implements [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) by creating a temporary stored procedure, which is then called on **SQLExecute**.</span></span> <span data-ttu-id="72be3-108">它增加了**SQLPrepare**创建临时存储过程的开销，该过程仅调用目标存储过程，而不是直接执行目标存储过程。</span><span class="sxs-lookup"><span data-stu-id="72be3-108">It adds overhead to have **SQLPrepare** create a temporary stored procedure that only calls the target stored procedure versus directly executing the target stored procedure.</span></span> <span data-ttu-id="72be3-109">即使在连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的某一实例时，准备调用都要求额外的网络上的往返，并且生成只调用存储过程执行计划的执行计划。</span><span class="sxs-lookup"><span data-stu-id="72be3-109">Even when connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], preparing a call requires an extra round trip across the network and the building of an execution plan that just calls the stored procedure execution plan.</span></span>  
  
 <span data-ttu-id="72be3-110">在执行某一存储过程时，ODBC 应用程序应使用 ODBC CALL 语法。</span><span class="sxs-lookup"><span data-stu-id="72be3-110">ODBC applications should use the ODBC CALL syntax when executing a stored procedure.</span></span> <span data-ttu-id="72be3-111">驱动程序将优化，以便在使用 ODBC CALL 语法时，使用远程过程调用机制来调用该过程。</span><span class="sxs-lookup"><span data-stu-id="72be3-111">The driver is optimized to use a remote procedure call mechanism to call the procedure when the ODBC CALL syntax is used.</span></span> <span data-ttu-id="72be3-112">这比用于将 [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE 语句发送到服务器的机制效率更高。</span><span class="sxs-lookup"><span data-stu-id="72be3-112">This is more efficient than the mechanism used to send a [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE statement to the server.</span></span>  
  
 <span data-ttu-id="72be3-113">有关详细信息，请参阅[运行存储过程](../../native-client-odbc-stored-procedures/running-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="72be3-113">For more information, see [Running Stored Procedures](../../native-client-odbc-stored-procedures/running-stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72be3-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72be3-114">See Also</span></span>  
 [<span data-ttu-id="72be3-115">&#40;ODBC&#41;执行语句</span><span class="sxs-lookup"><span data-stu-id="72be3-115">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  
