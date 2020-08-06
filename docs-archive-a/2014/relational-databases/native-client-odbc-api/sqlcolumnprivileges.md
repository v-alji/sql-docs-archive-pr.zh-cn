---
title: SQLColumnPrivileges |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
author: rothja
ms.author: jroth
ms.openlocfilehash: bf46fed47817ed94ea2382f2147df254f2986aec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578873"
---
# <a name="sqlcolumnprivileges"></a><span data-ttu-id="93bda-102">SQLColumnPrivileges</span><span class="sxs-lookup"><span data-stu-id="93bda-102">SQLColumnPrivileges</span></span>
  <span data-ttu-id="93bda-103">**SQLColumnPrivileges**返回 SQL_SUCCESS*CatalogName*、 *SchemaName*、 *TableName*或*ColumnName*参数是否存在值。</span><span class="sxs-lookup"><span data-stu-id="93bda-103">**SQLColumnPrivileges** returns SQL_SUCCESS whether or not values exist for the*CatalogName*, *SchemaName*, *TableName*, or *ColumnName* parameters.</span></span> <span data-ttu-id="93bda-104">当在这些参数中使用了无效值时， **SQLFetch**将返回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="93bda-104">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="93bda-105">可以对静态服务器游标执行**SQLColumnPrivileges** 。</span><span class="sxs-lookup"><span data-stu-id="93bda-105">**SQLColumnPrivileges** can be executed on a static server cursor.</span></span> <span data-ttu-id="93bda-106">尝试对可更新的 (动态或键集) 游标执行**SQLColumnPrivileges**将返回 SQL_SUCCESS_WITH_INFO，指示游标类型已更改。</span><span class="sxs-lookup"><span data-stu-id="93bda-106">An attempt to execute **SQLColumnPrivileges** on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="93bda-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序通过接受由两部分组成的*CatalogName*参数的名称来支持链接服务器上表的报告信息： *Linked_Server_Name。 Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="93bda-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93bda-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93bda-108">See Also</span></span>  
 <span data-ttu-id="93bda-109">[SQLColumnPrivileges 函数](https://go.microsoft.com/fwlink/?LinkId=59335) </span><span class="sxs-lookup"><span data-stu-id="93bda-109">[SQLColumnPrivileges Function](https://go.microsoft.com/fwlink/?LinkId=59335) </span></span>  
 [<span data-ttu-id="93bda-110">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="93bda-110">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
