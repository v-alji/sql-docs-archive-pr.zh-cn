---
title: SQLTables |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: rothja
ms.author: jroth
ms.openlocfilehash: bad60aa102a7771935e37ac963e6fa0d3cb2fd57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586648"
---
# <a name="sqltables"></a><span data-ttu-id="b54f9-102">SQLTables</span><span class="sxs-lookup"><span data-stu-id="b54f9-102">SQLTables</span></span>
  <span data-ttu-id="b54f9-103">可以对静态服务器游标执行 SQLTables。</span><span class="sxs-lookup"><span data-stu-id="b54f9-103">SQLTables can be executed on a static server cursor.</span></span> <span data-ttu-id="b54f9-104">尝试对可更新的 (动态或键集) 游标执行 SQLTables 将返回 SQL_SUCCESS_WITH_INFO，指示游标类型已更改。</span><span class="sxs-lookup"><span data-stu-id="b54f9-104">An attempt to execute SQLTables on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="b54f9-105">SQLTables 在*CatalogName*参数 SQL_ALL_CATALOGS 并且所有其他参数都包含 (NULL 指针) 的默认值时，报告所有数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="b54f9-105">SQLTables reports tables from all databases when the *CatalogName* parameter is SQL_ALL_CATALOGS and all other parameters contain default values (NULL pointers).</span></span>  
  
 <span data-ttu-id="b54f9-106">为了报告可用的目录、架构和表类型，SQLTables)  (长度为零的字节指针的空字符串。</span><span class="sxs-lookup"><span data-stu-id="b54f9-106">To report available catalogs, schemas, and table types, SQLTables makes special use of empty strings (zero-length byte pointers).</span></span> <span data-ttu-id="b54f9-107">空字符串不是默认值（NULL 指针）。</span><span class="sxs-lookup"><span data-stu-id="b54f9-107">Empty strings are not default values (NULL pointers).</span></span>  
  
 <span data-ttu-id="b54f9-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序通过接受由两部分组成的*CatalogName*参数的名称来支持链接服务器上表的报告信息： *Linked_Server_Name。 Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="b54f9-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
 <span data-ttu-id="b54f9-109">SQLTables 返回其名称与*TableName*匹配并且由当前用户拥有的所有表的相关信息。</span><span class="sxs-lookup"><span data-stu-id="b54f9-109">SQLTables returns information about any tables whose names match *TableName* and are owned by the current user.</span></span>  
  
## <a name="sqltables-and-table-valued-parameters"></a><span data-ttu-id="b54f9-110">SQLTables 和表值参数</span><span class="sxs-lookup"><span data-stu-id="b54f9-110">SQLTables and Table-Valued Parameters</span></span>  
 <span data-ttu-id="b54f9-111">如果语句特性 SQL_SOPT_SS_NAME_SCOPE 的值 SQL_SS_NAME_SCOPE_TABLE_TYPE，而不是其默认值 SQL_SS_NAME_SCOPE_TABLE，则 SQLTables 将返回有关表类型的信息。</span><span class="sxs-lookup"><span data-stu-id="b54f9-111">When the statement attribute SQL_SOPT_SS_NAME_SCOPE has the value SQL_SS_NAME_SCOPE_TABLE_TYPE, rather than its default value of SQL_SS_NAME_SCOPE_TABLE, SQLTables returns information about table types.</span></span> <span data-ttu-id="b54f9-112">SQLTables 返回的结果集的第4列中表类型返回的 TABLE_TYPE 值为表类型。</span><span class="sxs-lookup"><span data-stu-id="b54f9-112">The TABLE_TYPE value returned for a table type in column 4 of the result set returned by SQLTables is TABLE TYPE.</span></span> <span data-ttu-id="b54f9-113">有关 SQL_SOPT_SS_NAME_SCOPE 的详细信息，请参阅[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="b54f9-113">For more information on SQL_SOPT_SS_NAME_SCOPE, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="b54f9-114">表、视图和同义词共享公用的命名空间，该命名空间不同于表类型使用的命名空间。</span><span class="sxs-lookup"><span data-stu-id="b54f9-114">Tables, views, and synonyms share a common namespace that is distinct from the namespace used by table types.</span></span> <span data-ttu-id="b54f9-115">虽然表和视图不能具有相同的名称，但是在相同目录和架构中的表和表类型可以具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="b54f9-115">Although it is not possible to have a table and a view with the same name, it is possible to have a table and a table type with the same in the same catalog and schema.</span></span>  
  
 <span data-ttu-id="b54f9-116">有关表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="b54f9-116">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b54f9-117">示例</span><span class="sxs-lookup"><span data-stu-id="b54f9-117">Example</span></span>  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a><span data-ttu-id="b54f9-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b54f9-118">See Also</span></span>  
 <span data-ttu-id="b54f9-119">[SQLTables 函数](https://go.microsoft.com/fwlink/?LinkId=59374) </span><span class="sxs-lookup"><span data-stu-id="b54f9-119">[SQLTables Function](https://go.microsoft.com/fwlink/?LinkId=59374) </span></span>  
 [<span data-ttu-id="b54f9-120">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="b54f9-120">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
