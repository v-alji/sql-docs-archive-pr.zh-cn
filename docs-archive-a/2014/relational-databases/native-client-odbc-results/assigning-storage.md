---
title: 分配存储 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- column-wise binding [ODBC]
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLBindCol function
- storing data [ODBC]
- result sets [ODBC], storage
- SQL Server Native Client ODBC driver, data storage
- row-wise binding
- binding result sets [SQL Server Native Client]
- array binding
ms.assetid: 11c81955-5300-495f-925f-9256f2587b58
author: rothja
ms.author: jroth
ms.openlocfilehash: ada18c91493d91b36ced51bf84c32513a0c5f5df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589016"
---
# <a name="assigning-storage"></a><span data-ttu-id="4bdce-102">分配存储区</span><span class="sxs-lookup"><span data-stu-id="4bdce-102">Assigning Storage</span></span>
  <span data-ttu-id="4bdce-103">应用程序可以在执行 SQL 语句之前或之后为结果分配存储区。</span><span class="sxs-lookup"><span data-stu-id="4bdce-103">An application can assign storage for results before or after it executes a SQL statement.</span></span> <span data-ttu-id="4bdce-104">如果应用程序首先准备或执行 SQL 语句，则它可以在为结果分配存储区之前询问有关结果集的情况。</span><span class="sxs-lookup"><span data-stu-id="4bdce-104">If an application prepares or executes the SQL statement first, it can inquire about the result set before it assigns storage for results.</span></span> <span data-ttu-id="4bdce-105">例如，如果结果集是未知的，则应用程序在为它们分配存储区之前必须先检索列数。</span><span class="sxs-lookup"><span data-stu-id="4bdce-105">For example, if the result set is unknown, the application must retrieve the number of columns before it can assign storage for them.</span></span>  
  
 <span data-ttu-id="4bdce-106">若要关联数据列的存储，应用程序将调用[SQLBindCol](../native-client-odbc-api/sqlbindcol.md)并将其传递：</span><span class="sxs-lookup"><span data-stu-id="4bdce-106">To associate storage for a column of data, an application calls [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)and passes it:</span></span>  
  
-   <span data-ttu-id="4bdce-107">数据将要转换成的数据类型。</span><span class="sxs-lookup"><span data-stu-id="4bdce-107">The data type to which the data is to be converted.</span></span>  
  
-   <span data-ttu-id="4bdce-108">数据的输出缓冲区的地址。</span><span class="sxs-lookup"><span data-stu-id="4bdce-108">The address of an output buffer for the data.</span></span>  
  
     <span data-ttu-id="4bdce-109">应用程序必须分配该缓冲区，并且必须足够大以容纳采用转换后目标格式的数据。</span><span class="sxs-lookup"><span data-stu-id="4bdce-109">The application must allocate this buffer, and it must be large enough to hold the data in the form to which it is converted.</span></span>  
  
-   <span data-ttu-id="4bdce-110">输出缓冲区的长度。</span><span class="sxs-lookup"><span data-stu-id="4bdce-110">The length of the output buffer.</span></span>  
  
     <span data-ttu-id="4bdce-111">如果返回数据在 C 中有固定宽度（比如整数、实数或日期结构），则忽略该值。</span><span class="sxs-lookup"><span data-stu-id="4bdce-111">This value is ignored if the returned data has a fixed width in C, such as an integer, real number, or date structure.</span></span>  
  
-   <span data-ttu-id="4bdce-112">用于返回可用数据字节数的存储缓冲区的地址。</span><span class="sxs-lookup"><span data-stu-id="4bdce-112">The address of a storage buffer in which to return the number of bytes of available data.</span></span>  
  
 <span data-ttu-id="4bdce-113">应用程序还可以将结果集列绑定到程序变量的数组，以支持分块提取结果集行。</span><span class="sxs-lookup"><span data-stu-id="4bdce-113">An application can also bind result set columns to arrays of program variables to support fetching result set rows in blocks.</span></span> <span data-ttu-id="4bdce-114">数组绑定有两种不同的类型：</span><span class="sxs-lookup"><span data-stu-id="4bdce-114">There are two different types of array binding:</span></span>  
  
-   <span data-ttu-id="4bdce-115">当每个列绑定到自身的变量数组时，将完成按列绑定。</span><span class="sxs-lookup"><span data-stu-id="4bdce-115">Column-wise binding is finished when each column is bound to its own array of variables.</span></span>  
  
     <span data-ttu-id="4bdce-116">通过调用 SQL_ATTR_ROW_BIND_TYPE [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) *，并将\*\*将 valueptr*设置为 SQL_BIND_BY_COLUMN 来指定按列绑定。</span><span class="sxs-lookup"><span data-stu-id="4bdce-116">Column-wise binding is specified by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with *Attribute* set to SQL_ATTR_ROW_BIND_TYPE and *ValuePtr* set to SQL_BIND_BY_COLUMN.</span></span> <span data-ttu-id="4bdce-117">所有数组的元素个数必须相同。</span><span class="sxs-lookup"><span data-stu-id="4bdce-117">All the arrays must have the same number of elements.</span></span>  
  
-   <span data-ttu-id="4bdce-118">当 SQL 语句中的所有参数作为一个单元绑定到包含这些参数中各个变量的结构数组时，将完成按行绑定。</span><span class="sxs-lookup"><span data-stu-id="4bdce-118">Row-wise binding is finished when all the parameters in the SQL statement are bound as a unit to an array of structures that contain the individual variables for the parameters.</span></span>  
  
     <span data-ttu-id="4bdce-119">通过调用**SQLSetStmtAttr**并将*属性*设置为 SQL_ATTR_ROW_BIND_TYPE，并将*将 valueptr*设置为包含将接收结果集列的变量的结构的大小，可以指定按行绑定。</span><span class="sxs-lookup"><span data-stu-id="4bdce-119">Row-wise binding is specified by calling **SQLSetStmtAttr** with *Attribute* set to SQL_ATTR_ROW_BIND_TYPE and *ValuePtr* set to the size of the structure holding the variables that will receive the result set columns.</span></span>  
  
 <span data-ttu-id="4bdce-120">应用程序还将 SQL_ATTR_ROW_ARRAY_SIZE 设置为列或行数组中的元素个数，并设置 SQL_ATTR_ROW_STATUS_PTR 和 SQL_ATTR_ROWS_FETCHED_PTR。</span><span class="sxs-lookup"><span data-stu-id="4bdce-120">The application also sets SQL_ATTR_ROW_ARRAY_SIZE to the number of elements in the column or row arrays and sets SQL_ATTR_ROW_STATUS_PTR and SQL_ATTR_ROWS_FETCHED_PTR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdce-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4bdce-121">See Also</span></span>  
 [<span data-ttu-id="4bdce-122">&#40;ODBC&#41;处理结果</span><span class="sxs-lookup"><span data-stu-id="4bdce-122">Processing Results &#40;ODBC&#41;</span></span>](processing-results-odbc.md)  
  
  
