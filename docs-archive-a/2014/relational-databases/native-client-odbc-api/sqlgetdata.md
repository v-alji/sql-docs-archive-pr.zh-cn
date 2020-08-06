---
title: SQLGetData |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetData function
ms.assetid: 204848be-8787-45b4-816f-a60ac9d56fcf
author: rothja
ms.author: jroth
ms.openlocfilehash: c351cf7340bc7b0afeb76b139bd75aa429f56e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576737"
---
# <a name="sqlgetdata"></a><span data-ttu-id="57210-102">SQLGetData</span><span class="sxs-lookup"><span data-stu-id="57210-102">SQLGetData</span></span>
  <span data-ttu-id="57210-103">**SQLGetData**用于检索结果集数据，而不绑定列值。</span><span class="sxs-lookup"><span data-stu-id="57210-103">**SQLGetData** is used to retrieve result set data without binding column values.</span></span> <span data-ttu-id="57210-104">可以对同一列连续调用**SQLGetData** ，以从具有**text**、 **ntext**或**image**数据类型的列中检索大量数据。</span><span class="sxs-lookup"><span data-stu-id="57210-104">**SQLGetData** can be called successively on the same column to retrieve large amounts of data from a column with a **text**, **ntext**, or **image** data type.</span></span>  
  
 <span data-ttu-id="57210-105">此时，不要求应用程序绑定变量来提取结果集数据。</span><span class="sxs-lookup"><span data-stu-id="57210-105">There is no requirement that an application bind variables to fetch result set data.</span></span> <span data-ttu-id="57210-106">可以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用**SQLGetData**从 Native Client ODBC 驱动程序检索任意列的数据。</span><span class="sxs-lookup"><span data-stu-id="57210-106">The data of any column can be retrieved from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver by using **SQLGetData**.</span></span>  
  
 <span data-ttu-id="57210-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序不支持使用**SQLGetData**以随机列顺序检索数据。</span><span class="sxs-lookup"><span data-stu-id="57210-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support using **SQLGetData** to retrieve data in random column order.</span></span> <span data-ttu-id="57210-108">使用**SQLGetData**处理的所有未绑定列都必须具有比结果集中绑定列更高的列序号。</span><span class="sxs-lookup"><span data-stu-id="57210-108">All unbound columns processed with **SQLGetData** must have higher column ordinals than the bound columns in the result set.</span></span> <span data-ttu-id="57210-109">应用程序必须按照从未绑定列的最小序号值到最大序号值的顺序处理数据。</span><span class="sxs-lookup"><span data-stu-id="57210-109">The application must process data from the lowest unbound ordinal column value to the highest.</span></span> <span data-ttu-id="57210-110">尝试从较小序号的列中检索数据将导致错误。</span><span class="sxs-lookup"><span data-stu-id="57210-110">Attempting to retrieve data from a lower ordinally numbered column results in an error.</span></span> <span data-ttu-id="57210-111">如果某个应用程序使用服务器游标报告结果集行，则该应用程序可重新提取当前行，然后提取列值。</span><span class="sxs-lookup"><span data-stu-id="57210-111">If the application is using server cursors to report result set rows, the application can refetch the current row and then fetch the value of a column.</span></span> <span data-ttu-id="57210-112">如果对默认的只读、只进游标执行语句，则必须重新执行该语句来备份**SQLGetData**。</span><span class="sxs-lookup"><span data-stu-id="57210-112">If a statement is executed on the default read-only, forward-only cursor, you must re-execute the statement to back up **SQLGetData**.</span></span>  
  
 <span data-ttu-id="57210-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序准确报告使用**SQLGetData**检索到的**text**、 **ntext**和**image**数据的长度。</span><span class="sxs-lookup"><span data-stu-id="57210-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver accurately reports the length of **text**, **ntext**, and **image** data retrieved using **SQLGetData**.</span></span> <span data-ttu-id="57210-114">应用程序可以充分利用*StrLen_or_IndPtr*参数返回，以便快速检索长数据。</span><span class="sxs-lookup"><span data-stu-id="57210-114">The application can make good use of the *StrLen_or_IndPtr* parameter return to retrieve long data rapidly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57210-115">对于大值类型，在数据截断的情况下*StrLen_or_IndPtr*将返回 SQL_NO_TOTAL。</span><span class="sxs-lookup"><span data-stu-id="57210-115">For large value types, *StrLen_or_IndPtr* will return SQL_NO_TOTAL in cases of data truncation.</span></span>  
  
## <a name="sqlgetdata-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="57210-116">SQLGetData 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="57210-116">SQLGetData Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="57210-117">日期/时间类型的结果列值按[从 SQL 到 C 的转换](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)中所述进行转换。</span><span class="sxs-lookup"><span data-stu-id="57210-117">Result column values of date/time types are converted as described in [Conversions from SQL to C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).</span></span>  
  
 <span data-ttu-id="57210-118">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="57210-118">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlgetdata-support-for-large-clr-udts"></a><span data-ttu-id="57210-119">SQLGetData 对大型 CLR UDT 的支持</span><span class="sxs-lookup"><span data-stu-id="57210-119">SQLGetData Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="57210-120">**SQLGetData**支持 (udt) 的大型 CLR 用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="57210-120">**SQLGetData** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="57210-121">有关详细信息，请参阅[&#40;ODBC&#41;的大型 CLR 用户定义类型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="57210-121">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="57210-122">示例</span><span class="sxs-lookup"><span data-stu-id="57210-122">Example</span></span>  
  
```  
SQLHDBC     hDbc = NULL;  
SQLHSTMT    hStmt = NULL;  
long        lEmpID;  
PBYTE       pPicture;  
SQLINTEGER  pIndicators[2];  
  
// Get an environment, connection, and so on.  
...  
  
// Get a statement handle and execute a command.  
SQLAllocHandle(SQL_HANDLE_STMT, hDbc, &hStmt);  
  
if (SQLExecDirect(hStmt,  
    (SQLCHAR*) "SELECT EmployeeID, Photo FROM Employees",  
    SQL_NTS) == SQL_ERROR)  
    {  
    // Handle error and return.  
    }  
  
// Retrieve data from row set.  
SQLBindCol(hStmt, 1, SQL_C_LONG, (SQLPOINTER) &lEmpID, sizeof(long),  
    &pIndicators[0]);  
  
while (SQLFetch(hStmt) == SQL_SUCCESS)  
    {  
    cout << "EmployeeID: " << lEmpID << "\n";  
  
    // Call SQLGetData to determine the amount of data that's waiting.  
    if (SQLGetData(hStmt, 2, SQL_C_BINARY, pPicture, 0, &pIndicators[1])  
        == SQL_SUCCESS_WITH_INFO)  
        {  
        cout << "Photo size: " pIndicators[1] << "\n\n";  
  
        // Get all the data at once.  
        pPicture = new BYTE[pIndicators[1]];  
        if (SQLGetData(hStmt, 2, SQL_C_DEFAULT, pPicture,  
            pIndicators[1], &pIndicators[1]) != SQL_SUCCESS)  
            {  
            // Handle error and continue.  
            }  
  
        delete [] pPicture;  
        }  
    else  
        {  
        // Handle error on attempt to get data length.  
        }  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="57210-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57210-123">See Also</span></span>  
 <span data-ttu-id="57210-124">[SQLGetData 函数](https://go.microsoft.com/fwlink/?LinkId=59350) </span><span class="sxs-lookup"><span data-stu-id="57210-124">[SQLGetData Function](https://go.microsoft.com/fwlink/?LinkId=59350) </span></span>  
 [<span data-ttu-id="57210-125">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="57210-125">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
