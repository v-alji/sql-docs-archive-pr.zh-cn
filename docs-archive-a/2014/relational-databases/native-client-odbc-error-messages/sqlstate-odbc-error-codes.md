---
title: SQLSTATE (ODBC 错误代码) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
author: rothja
ms.author: jroth
ms.openlocfilehash: ff3ec0a5cdc8f24f34e42849f7c8f6d1d9d41478
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576734"
---
# <a name="sqlstate-odbc-error-codes"></a><span data-ttu-id="d4960-102">SQLSTATE（ODBC 错误代码）</span><span class="sxs-lookup"><span data-stu-id="d4960-102">SQLSTATE (ODBC Error Codes)</span></span>
  <span data-ttu-id="d4960-103">SQLSTATE 提供与警告或错误的原因有关的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d4960-103">SQLSTATE provides detailed information about the cause of a warning or error.</span></span> <span data-ttu-id="d4960-104">对于在检测并返回的数据源中发生的错误 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驱动程序将返回的本机错误号映射到相应的 SQLSTATE。</span><span class="sxs-lookup"><span data-stu-id="d4960-104">For errors that occur in the data source detected and returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver maps the returned native error number to the appropriate SQLSTATE.</span></span> <span data-ttu-id="d4960-105">如果本机错误号没有要映射到的 ODBC 错误代码，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序将返回 SQLSTATE 42000 ( "语法错误或访问冲突" ) 。</span><span class="sxs-lookup"><span data-stu-id="d4960-105">If a native error number does not have an ODBC error code to map to, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns SQLSTATE 42000 ("syntax error or access violation").</span></span> <span data-ttu-id="d4960-106">对于驱动程序检测到的错误， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序将生成相应的 SQLSTATE。</span><span class="sxs-lookup"><span data-stu-id="d4960-106">For errors that are detected by the driver, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver generates the appropriate SQLSTATE.</span></span>  
  
 <span data-ttu-id="d4960-107">有关状态错误代码的详细信息，请参阅下面的主题：</span><span class="sxs-lookup"><span data-stu-id="d4960-107">For more information about the state error codes, see the following topics:</span></span>  
  
-   [<span data-ttu-id="d4960-108">附录 A：ODBC 错误代码</span><span class="sxs-lookup"><span data-stu-id="d4960-108">Appendix A: ODBC Error Codes</span></span>](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [<span data-ttu-id="d4960-109">SQLSTATE 映射</span><span class="sxs-lookup"><span data-stu-id="d4960-109">SQLSTATE Mappings</span></span>](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a><span data-ttu-id="d4960-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4960-110">See Also</span></span>  
 [<span data-ttu-id="d4960-111">处理错误和消息</span><span class="sxs-lookup"><span data-stu-id="d4960-111">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  
