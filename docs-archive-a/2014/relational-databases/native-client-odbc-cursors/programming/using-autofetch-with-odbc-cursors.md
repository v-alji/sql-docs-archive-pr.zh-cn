---
title: 对 ODBC 游标使用自动提取 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: rothja
ms.author: jroth
ms.openlocfilehash: e3d9374cf9ceab4a7e73cc0059783486f2bf9c41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589040"
---
# <a name="using-autofetch-with-odbc-cursors"></a><span data-ttu-id="cc55a-102">通过 ODBC 游标使用自动提取</span><span class="sxs-lookup"><span data-stu-id="cc55a-102">Using Autofetch with ODBC Cursors</span></span>
  <span data-ttu-id="cc55a-103">当连接到实例时 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驱动程序支持使用任何服务器游标类型时的自动提取选项。</span><span class="sxs-lookup"><span data-stu-id="cc55a-103">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports an autofetch option when using any server cursor type.</span></span> <span data-ttu-id="cc55a-104">使用自动提取，打开游标的**SQLExecute**或**SQLExecDirect**函数也具有隐式[SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) (SQL_FIRST) 函数。</span><span class="sxs-lookup"><span data-stu-id="cc55a-104">With autofetch, the **SQLExecute** or **SQLExecDirect** function that opens the cursor also has an implicit [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) function.</span></span> <span data-ttu-id="cc55a-105">组成第一个行集的行将作为语句执行的一部分返回给绑定应用程序变量，并通过网络将另一个往返保存到服务器。</span><span class="sxs-lookup"><span data-stu-id="cc55a-105">The rows comprising the first rowset are returned to the bound application variables as part of the statement execution, saving another roundtrip across the network to the server.</span></span> <span data-ttu-id="cc55a-106">启用自动提取选项后，不支持[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) ;结果集列必须绑定到程序变量。</span><span class="sxs-lookup"><span data-stu-id="cc55a-106">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) is not supported when the autofetch option is enabled; the result set columns must be bound to program variables.</span></span>  
  
 <span data-ttu-id="cc55a-107">应用程序通过对 SQL_CO_AF 设置特定于驱动程序的 SQL_SOPT_SS_CURSOR_OPTIONS 语句属性请求自动提取。</span><span class="sxs-lookup"><span data-stu-id="cc55a-107">Applications request autofetch by setting the driver-specific SQL_SOPT_SS_CURSOR_OPTIONS statement attribute to SQL_CO_AF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc55a-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc55a-108">See Also</span></span>  
 [<span data-ttu-id="cc55a-109">ODBC&#41;的游标编程详细信息 &#40;</span><span class="sxs-lookup"><span data-stu-id="cc55a-109">Cursor Programming Details &#40;ODBC&#41;</span></span>](cursor-programming-details-odbc.md)  
  
  
