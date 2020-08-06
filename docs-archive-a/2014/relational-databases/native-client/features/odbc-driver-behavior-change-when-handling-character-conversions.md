---
title: 处理字符转换时 ODBC 驱动程序的行为发生变化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 682a232a-bf89-4849-88a1-95b2fbac1467
author: rothja
ms.author: jroth
ms.openlocfilehash: 5334b4268559ba155a53b3be655d87f7867779df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688866"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a><span data-ttu-id="dbc7e-102">处理字符转换时 ODBC 驱动程序行为的变化</span><span class="sxs-lookup"><span data-stu-id="dbc7e-102">ODBC Driver Behavior Change When Handling Character Conversions</span></span>
  <span data-ttu-id="dbc7e-103">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ( # A0) 的 Native CLIENT ODBC 驱动程序更改了它的实现方式 SQL_WCHAR \* (NCHAR/nvarchar/nvarchar (max) # A6 和 SQL_CHAR (\* CHAR/VARCHAR/NARCHAR (max) # A10 转换。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-103">The [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC Driver (SQLNCLI11.dll) changed how it does of SQL_WCHAR\* (NCHAR/NVARCHAR/NVARCHAR(MAX)) and SQL_CHAR\* (CHAR/VARCHAR/NARCHAR(MAX)) conversions.</span></span> <span data-ttu-id="dbc7e-104">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client ODBC 驱动程序时，ODBC 函数（如 SQLGetData、SQLBindCol、SQLBindParameter）返回 (-4) SQL_NO_TOTAL 作为长度/指示符参数。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-104">ODBC functions, such as SQLGetData, SQLBindCol, SQLBindParameter, return (-4) SQL_NO_TOTAL as the length/indicator parameter when using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client ODBC driver.</span></span> <span data-ttu-id="dbc7e-105">以前版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序返回的长度值可能不正确。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-105">Prior versions of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver returned a length value, which can be incorrect.</span></span>  
  
## <a name="sqlgetdata-behavior"></a><span data-ttu-id="dbc7e-106">SQLGetData 行为</span><span class="sxs-lookup"><span data-stu-id="dbc7e-106">SQLGetData Behavior</span></span>  
 <span data-ttu-id="dbc7e-107">许多 Windows 函数允许指定缓冲区大小为 0，且返回的长度为返回的数据大小。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-107">Many Windows functions let you specify a buffer size of 0 and the returned length is the size of the returned data.</span></span> <span data-ttu-id="dbc7e-108">以下模式对于 Windows 程序员很常见：</span><span class="sxs-lookup"><span data-stu-id="dbc7e-108">The following pattern is common for Windows programmers:</span></span>  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 <span data-ttu-id="dbc7e-109">但是，不应在此方案中使用**SQLGetData** 。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-109">However, **SQLGetData** should not be used in this scenario.</span></span> <span data-ttu-id="dbc7e-110">不应使用以下模式：</span><span class="sxs-lookup"><span data-stu-id="dbc7e-110">The following pattern should not be used:</span></span>  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 <span data-ttu-id="dbc7e-111">只能调用**SQLGetData**来检索实际数据块。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-111">**SQLGetData** can only be called to retrieve chunks of actual data.</span></span> <span data-ttu-id="dbc7e-112">不支持使用**SQLGetData**获取数据大小。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-112">Using **SQLGetData** to get the size of data is not unsupported.</span></span>  
  
 <span data-ttu-id="dbc7e-113">下面说明当您使用不正确的模式时驱动程序变化的影响。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-113">The following shows the impact of the driver change when you use the incorrect pattern.</span></span> <span data-ttu-id="dbc7e-114">此应用程序将 `varchar` 列和绑定作为 Unicode (SQL_UNICODE/SQL_WCHAR) 查询：</span><span class="sxs-lookup"><span data-stu-id="dbc7e-114">This application queries a `varchar` column and binding as Unicode (SQL_UNICODE/SQL_WCHAR):</span></span>  
  
 <span data-ttu-id="dbc7e-115">Query`select convert(varchar(36), '123')`</span><span class="sxs-lookup"><span data-stu-id="dbc7e-115">Query:  `select convert(varchar(36), '123')`</span></span>  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ....., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="dbc7e-116">Native Client ODBC 驱动程序版本</span><span class="sxs-lookup"><span data-stu-id="dbc7e-116">Native Client ODBC Driver version</span></span>|<span data-ttu-id="dbc7e-117">长度或指示符的结果</span><span class="sxs-lookup"><span data-stu-id="dbc7e-117">Length or Indicator Outcome</span></span>|<span data-ttu-id="dbc7e-118">说明</span><span class="sxs-lookup"><span data-stu-id="dbc7e-118">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="dbc7e-119">Native Client 或更早版本</span><span class="sxs-lookup"><span data-stu-id="dbc7e-119">Native Client or earlier</span></span>|<span data-ttu-id="dbc7e-120">6</span><span class="sxs-lookup"><span data-stu-id="dbc7e-120">6</span></span>|<span data-ttu-id="dbc7e-121">驱动程序错误地假定将 CHAR 转换为 WCHAR 可以通过长度 \* 2 来实现。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-121">The driver incorrectly assumed that converting CHAR to WCHAR could be accomplished as length \* 2.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="dbc7e-122">Native Client（版本 11.0.2100.60）或更高版本</span><span class="sxs-lookup"><span data-stu-id="dbc7e-122">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="dbc7e-123">-4 (SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="dbc7e-123">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="dbc7e-124">该驱动程序不再假设从 CHAR 转换为 WCHAR 或 WCHAR 到 CHAR 是 (乘法) \* 2 或 (除以) /2 操作。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-124">The driver no longer assumes that converting from CHAR to WCHAR or WCHAR to CHAR is a (multiply) \*2 or (divide)/2 action.</span></span><br /><br /> <span data-ttu-id="dbc7e-125">调用**SQLGetData**将不再返回预期转换的长度。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-125">Calling **SQLGetData** no longer returns the length of the expected conversion.</span></span> <span data-ttu-id="dbc7e-126">驱动程序检测 CHAR 和 WCHAR 之间的转换并返回 (-4) SQL_NO_TOTAL 替代可能不正确的 \*2 或 /2 行为。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-126">The driver detects the conversion to or from CHAR and WCHAR and returns (-4) SQL_NO_TOTAL instead of \*2 or /2 behavior that could be incorrect.</span></span>|  
  
 <span data-ttu-id="dbc7e-127">使用**SQLGetData**检索数据块。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-127">Use **SQLGetData** to retrieve the chunks of the data.</span></span> <span data-ttu-id="dbc7e-128">（所示的伪代码：）</span><span class="sxs-lookup"><span data-stu-id="dbc7e-128">(Pseudo code shown:)</span></span>  
  
```  
while( (SQL_SUCCESS or SQL_SUCCESS_WITH_INFO) == SQLFetch(...) ) {  
   SQLNumCols(...iTotalCols...)  
   for(int iCol = 1; iCol < iTotalCols; iCol++) {  
      WCHAR* pBufOrig, pBuffer = new WCHAR[100];  
      SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get original chunk  
      while(NOT ALL DATA RETREIVED (SQL_NO_TOTAL, ...) ) {  
         pBuffer += 50;   // Advance buffer for data retrieved  
         // May need to realloc the buffer when you reach current size  
         SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get next chunk  
      }  
   }  
}  
```  
  
## <a name="sqlbindcol-behavior"></a><span data-ttu-id="dbc7e-129">SQLBindCol 行为</span><span class="sxs-lookup"><span data-stu-id="dbc7e-129">SQLBindCol Behavior</span></span>  
 <span data-ttu-id="dbc7e-130">Query`select convert(varchar(36), '1234567890')`</span><span class="sxs-lookup"><span data-stu-id="dbc7e-130">Query:  `select convert(varchar(36), '1234567890')`</span></span>  
  
```  
SQLBindCol(... SQL_W_CHAR, ...)   // Only bound a buffer of WCHAR[4] - Expecting String Data Right Truncation behavior  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="dbc7e-131">Native Client ODBC 驱动程序版本</span><span class="sxs-lookup"><span data-stu-id="dbc7e-131">Native Client ODBC Driver version</span></span>|<span data-ttu-id="dbc7e-132">长度或指示符的结果</span><span class="sxs-lookup"><span data-stu-id="dbc7e-132">Length or Indicator Outcome</span></span>|<span data-ttu-id="dbc7e-133">说明</span><span class="sxs-lookup"><span data-stu-id="dbc7e-133">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="dbc7e-134">Native Client 或更早版本</span><span class="sxs-lookup"><span data-stu-id="dbc7e-134">Native Client or earlier</span></span>|<span data-ttu-id="dbc7e-135">20</span><span class="sxs-lookup"><span data-stu-id="dbc7e-135">20</span></span>|<span data-ttu-id="dbc7e-136">-   **SQLFetch**报告数据右侧存在截断情况。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-136">-   **SQLFetch** reports that there is a truncation on the right side of the data.</span></span><br /><span data-ttu-id="dbc7e-137">-Length 是返回的数据的长度，而不是存储 (假设 \* 2 WCHAR 转换对于标志符号) 不正确。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-137">-   Length is the length of the data returned, not what was stored (assumes \*2 CHAR to WCHAR conversion which can be incorrect for glyphs).</span></span><br /><span data-ttu-id="dbc7e-138">-缓冲区中存储的数据为 123 \ 0。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-138">-   Data stored in buffer is 123\0.</span></span> <span data-ttu-id="dbc7e-139">缓冲区被保证为以 NULL 结束。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-139">Buffer is guaranteed to be NULL terminated.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="dbc7e-140">Native Client（版本 11.0.2100.60）或更高版本</span><span class="sxs-lookup"><span data-stu-id="dbc7e-140">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="dbc7e-141">-4 (SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="dbc7e-141">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="dbc7e-142">-   **SQLFetch**报告数据右侧存在截断情况。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-142">-   **SQLFetch** reports that there is a truncation on the right side of the data.</span></span><br /><span data-ttu-id="dbc7e-143">-Length 指示-4 (SQL_NO_TOTAL) ，因为数据的其余部分未转换。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-143">-   Length indicates -4 (SQL_NO_TOTAL) because the rest of the data was not converted.</span></span><br /><span data-ttu-id="dbc7e-144">-缓冲区中存储的数据为 123 \ 0。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-144">-   Data stored in the buffer is 123\0.</span></span> <span data-ttu-id="dbc7e-145">- 缓冲区被保证为以 NULL 结束。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-145">- Buffer is guaranteed to be NULL terminated.</span></span>|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a><span data-ttu-id="dbc7e-146">SQLBindParameter（OUTPUT 参数行为）</span><span class="sxs-lookup"><span data-stu-id="dbc7e-146">SQLBindParameter (OUTPUT Parameter Behavior)</span></span>  
 <span data-ttu-id="dbc7e-147">Query`create procedure spTest @p1 varchar(max) OUTPUT`</span><span class="sxs-lookup"><span data-stu-id="dbc7e-147">Query:  `create procedure spTest @p1 varchar(max) OUTPUT`</span></span>  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(... SQL_W_CHAR, ...)   // Only bind up to first 64 characters  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="dbc7e-148">Native Client ODBC 驱动程序版本</span><span class="sxs-lookup"><span data-stu-id="dbc7e-148">Native Client ODBC Driver version</span></span>|<span data-ttu-id="dbc7e-149">长度或指示符的结果</span><span class="sxs-lookup"><span data-stu-id="dbc7e-149">Length or Indicator Outcome</span></span>|<span data-ttu-id="dbc7e-150">说明</span><span class="sxs-lookup"><span data-stu-id="dbc7e-150">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="dbc7e-151">Native Client 或更早版本</span><span class="sxs-lookup"><span data-stu-id="dbc7e-151">Native Client or earlier</span></span>|<span data-ttu-id="dbc7e-152">2468</span><span class="sxs-lookup"><span data-stu-id="dbc7e-152">2468</span></span>|<span data-ttu-id="dbc7e-153">-   **SQLFetch**返回的数据不可用。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-153">-   **SQLFetch** returns no more data available.</span></span><br /><span data-ttu-id="dbc7e-154">-   **SQLMoreResults**返回的数据不可用。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-154">-   **SQLMoreResults** returns no more data available.</span></span><br /><span data-ttu-id="dbc7e-155">-Length 指示从服务器返回的数据的大小，而不是存储在缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-155">-   Length indicates the size of the data returned from server, not stored in buffer.</span></span><br /><span data-ttu-id="dbc7e-156">-原始缓冲区包含63字节和 NULL 终止符。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-156">-   Original buffer contains 63 bytes and a NULL terminator.</span></span> <span data-ttu-id="dbc7e-157">缓冲区被保证为以 NULL 结束。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-157">Buffer is guaranteed to be NULL terminated.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="dbc7e-158">Native Client（版本 11.0.2100.60）或更高版本</span><span class="sxs-lookup"><span data-stu-id="dbc7e-158">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="dbc7e-159">-4 (SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="dbc7e-159">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="dbc7e-160">-   **SQLFetch**返回的数据不可用。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-160">-   **SQLFetch** returns no more data available.</span></span><br /><span data-ttu-id="dbc7e-161">-   **SQLMoreResults**返回的数据不可用。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-161">-   **SQLMoreResults** returns no more data available.</span></span><br /><span data-ttu-id="dbc7e-162">-Length 指示 (-4) SQL_NO_TOTAL，因为数据的其余部分未转换。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-162">-   Length indicates (-4) SQL_NO_TOTAL because the rest of the data was not converted.</span></span><br /><span data-ttu-id="dbc7e-163">-原始缓冲区包含63字节和 NULL 终止符。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-163">-   Original buffer contains 63 bytes and a NULL terminator.</span></span> <span data-ttu-id="dbc7e-164">缓冲区被保证为以 NULL 结束。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-164">Buffer is guaranteed to be NULL terminated.</span></span>|  
  
## <a name="performing-char-and-wchar-conversions"></a><span data-ttu-id="dbc7e-165">执行 CHAR 和 WCHAR 转换</span><span class="sxs-lookup"><span data-stu-id="dbc7e-165">Performing CHAR and WCHAR Conversions</span></span>  
 <span data-ttu-id="dbc7e-166">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC 驱动程序提供几种执行 CHAR 和 WCHAR 转换的方式。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-166">The [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC driver offers several ways to perform CHAR and WCHAR conversions.</span></span> <span data-ttu-id="dbc7e-167">逻辑类似于操作 blob (varchar (max) 、nvarchar (max) ... ) ：</span><span class="sxs-lookup"><span data-stu-id="dbc7e-167">The logic is similar to manipulating blobs (varchar(max), nvarchar(max), ...):</span></span>  
  
-   <span data-ttu-id="dbc7e-168">绑定到**SQLBindCol**或**SQLBindParameter**时，数据会保存或截断到指定的缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-168">Data is saved or truncated into the specified buffer when binding with **SQLBindCol** or **SQLBindParameter**.</span></span>  
  
-   <span data-ttu-id="dbc7e-169">如果未绑定，则可以通过使用**SQLGetData**和**SQLParamData**在块区中检索数据。</span><span class="sxs-lookup"><span data-stu-id="dbc7e-169">If you do not bind, you can retrieve the data in chunks by using **SQLGetData** and **SQLParamData**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc7e-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbc7e-170">See Also</span></span>  
 [<span data-ttu-id="dbc7e-171">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="dbc7e-171">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
