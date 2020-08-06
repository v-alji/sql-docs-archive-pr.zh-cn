---
title: SQLPrimaryKeys |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: rothja
ms.author: jroth
ms.openlocfilehash: 67a932996ccbf52f5ab21fd6aa62381184ebc510
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590759"
---
# <a name="sqlprimarykeys"></a><span data-ttu-id="620c7-102">SQLPrimaryKeys</span><span class="sxs-lookup"><span data-stu-id="620c7-102">SQLPrimaryKeys</span></span>
  <span data-ttu-id="620c7-103">表中可能有一列或多列可用作唯一的行标识符，而在没有 PRIMARY KEY 约束的情况下创建的表会将空结果集返回到 SQLPrimaryKeys。</span><span class="sxs-lookup"><span data-stu-id="620c7-103">A table might have a column or columns that can serve as unique row identifiers, and tables created without a PRIMARY KEY constraint return an empty result set to SQLPrimaryKeys.</span></span> <span data-ttu-id="620c7-104">ODBC 函数[SQLSpecialColumns](sqlspecialcolumns.md)报告没有主键的表的行标识符候选项。</span><span class="sxs-lookup"><span data-stu-id="620c7-104">The ODBC function [SQLSpecialColumns](sqlspecialcolumns.md) reports row identifier candidates for tables without primary keys.</span></span>  
  
 <span data-ttu-id="620c7-105">SQLPrimaryKeys 返回 SQL_SUCCESS *CatalogName*、 *SchemaName*或*TableName*参数是否存在值。</span><span class="sxs-lookup"><span data-stu-id="620c7-105">SQLPrimaryKeys returns SQL_SUCCESS whether or not values exist for *CatalogName*, *SchemaName*, or *TableName* parameters.</span></span> <span data-ttu-id="620c7-106">当这些参数中使用的值无效时，SQLFetch 返回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="620c7-106">SQLFetch returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="620c7-107">可以对静态服务器游标执行 SQLPrimaryKeys。</span><span class="sxs-lookup"><span data-stu-id="620c7-107">SQLPrimaryKeys can be executed on a static server cursor.</span></span> <span data-ttu-id="620c7-108">尝试对可更新的 (动态或键集) 游标执行 SQLPrimaryKeys 将返回 SQL_SUCCESS_WITH_INFO，指示游标类型已更改。</span><span class="sxs-lookup"><span data-stu-id="620c7-108">An attempt to execute SQLPrimaryKeys on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="620c7-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序通过接受由两部分组成的*CatalogName*参数的名称来支持链接服务器上表的报告信息： *Linked_Server_Name。 Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="620c7-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a><span data-ttu-id="620c7-110">SQLPrimaryKeys 和表值参数</span><span class="sxs-lookup"><span data-stu-id="620c7-110">SQLPrimaryKeys and Table-Valued Parameters</span></span>  
 <span data-ttu-id="620c7-111">如果语句特性 SQL_SOPT_SS_NAME_SCOPE 的值 SQL_SS_NAME_SCOPE_TABLE_TYPE，而不是其默认值 SQL_SS_NAME_SCOPE_TABLE，则 SQLPrimaryKeys 将返回有关表类型的主键列的信息。</span><span class="sxs-lookup"><span data-stu-id="620c7-111">If the statement attribute SQL_SOPT_SS_NAME_SCOPE has the value SQL_SS_NAME_SCOPE_TABLE_TYPE, rather than its default value of SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys will return information about primary key columns of table types.</span></span> <span data-ttu-id="620c7-112">有关 SQL_SOPT_SS_NAME_SCOPE 的详细信息，请参阅[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="620c7-112">For more information on SQL_SOPT_SS_NAME_SCOPE, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="620c7-113">有关表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="620c7-113">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="620c7-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="620c7-114">See Also</span></span>  
 <span data-ttu-id="620c7-115">[SQLPrimaryKeys 函数](https://go.microsoft.com/fwlink/?LinkId=59361) </span><span class="sxs-lookup"><span data-stu-id="620c7-115">[SQLPrimaryKeys Function](https://go.microsoft.com/fwlink/?LinkId=59361) </span></span>  
 [<span data-ttu-id="620c7-116">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="620c7-116">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
