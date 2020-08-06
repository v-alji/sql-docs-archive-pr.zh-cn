---
title: SQLEndTran |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: rothja
ms.author: jroth
ms.openlocfilehash: e5d44756131b6133baec69e34da11055a965e2da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688905"
---
# <a name="sqlendtran"></a><span data-ttu-id="52463-102">SQLEndTran</span><span class="sxs-lookup"><span data-stu-id="52463-102">SQLEndTran</span></span>
  <span data-ttu-id="52463-103">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在**SQLEndTran**提交或回滚操作时，Native Client ODBC 驱动程序会关闭语句的关联游标。</span><span class="sxs-lookup"><span data-stu-id="52463-103">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver closes a statement's associated cursor when **SQLEndTran** commits or rolls back an operation.</span></span> <span data-ttu-id="52463-104">服务器游标将关闭，除非它们是静态的。</span><span class="sxs-lookup"><span data-stu-id="52463-104">Server cursors are closed unless they are static.</span></span> <span data-ttu-id="52463-105">当**SQLEndTran**提交或回滚操作时，语句的关联游标的行为取决于驱动程序特定的 ODBC 连接属性的值，SQL_COPT_SS_PRESERVE_CURSORS，由[SQLSetConnectAttr](sqlsetconnectattr.md)设置。</span><span class="sxs-lookup"><span data-stu-id="52463-105">When **SQLEndTran** commits or rolls back an operation, the behavior of the statement's associated cursor is determined by the value of the driver-specific ODBC connection attribute SQL_COPT_SS_PRESERVE_CURSORS, set by [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52463-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52463-106">See Also</span></span>  
 <span data-ttu-id="52463-107">[ODBC API 实现细节](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="52463-107">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 [<span data-ttu-id="52463-108">SQLEndTran 函数</span><span class="sxs-lookup"><span data-stu-id="52463-108">SQLEndTran Function</span></span>](https://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
