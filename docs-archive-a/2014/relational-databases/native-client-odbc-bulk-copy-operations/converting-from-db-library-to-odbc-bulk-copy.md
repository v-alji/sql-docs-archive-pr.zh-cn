---
title: 从 DB-LIBRARY 转换到 ODBC 大容量复制 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- converting DB-Library to ODBC bulk copy
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], DB-Library bulk copy
- ODBC, bulk copy operations
- DB-Library bulk copy
ms.assetid: 0bc15bdb-f19f-4537-ac6c-f249f42cf07f
author: rothja
ms.author: jroth
ms.openlocfilehash: 866900606e582f08695fd4695a1098f34fb2b426
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589047"
---
# <a name="converting-from-db-library-to-odbc-bulk-copy"></a><span data-ttu-id="0789e-102">从 DB-Library 转换到 ODBC 大容量复制</span><span class="sxs-lookup"><span data-stu-id="0789e-102">Converting from DB-Library to ODBC Bulk Copy</span></span>
  <span data-ttu-id="0789e-103">将 DB-LIBRARY 大容量复制程序转换为 ODBC 非常简单，因为 Native Client ODBC 驱动程序支持的大容量复制函数 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类似于 db-library 大容量复制函数，但以下情况除外：</span><span class="sxs-lookup"><span data-stu-id="0789e-103">Converting a DB-Library bulk copy program to ODBC is easy because the bulk copy functions supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver are similar to the DB-Library bulk copy functions, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="0789e-104">DB-Library 应用程序将 DBPROCESS 结构的指针作为大容量复制函数的第一个参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="0789e-104">DB-Library applications pass a pointer to a DBPROCESS structure as the first parameter of bulk copy functions.</span></span> <span data-ttu-id="0789e-105">在 ODBC 应用程序中，DBPROCESS 指针由 ODBC 连接句柄取代。</span><span class="sxs-lookup"><span data-stu-id="0789e-105">In ODBC applications, the DBPROCESS pointer is replaced with an ODBC connection handle.</span></span>  
  
-   <span data-ttu-id="0789e-106">在连接之前，DB-LIBRARY 应用程序调用**BCP_SETL** ，以在 DBPROCESS 上启用大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="0789e-106">DB-Library applications call **BCP_SETL** before connecting to enable bulk copy operations on a DBPROCESS.</span></span> <span data-ttu-id="0789e-107">ODBC 应用程序在连接之前调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，以对连接句柄启用批量操作：</span><span class="sxs-lookup"><span data-stu-id="0789e-107">ODBC applications instead call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) before connecting to enable bulk operations on a connection handle:</span></span>  
  
    ```  
    SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP,  
        (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
    ```  
  
-   <span data-ttu-id="0789e-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序不支持 db-library 消息和错误处理程序; 必须调用**SQLGetDiagRec**来获取 ODBC 大容量复制函数引发的错误和消息。</span><span class="sxs-lookup"><span data-stu-id="0789e-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support DB-Library message and error handlers; you must call **SQLGetDiagRec** to get errors and messages raised by the ODBC bulk copy functions.</span></span> <span data-ttu-id="0789e-109">大容量复制函数的 ODBC 版本返回标准的大容量复制返回代码 SUCCEED 或 FAILED，而不是 ODBC 样式的返回代码，比如 SQL_SUCCESS 或 SQL_ERROR。</span><span class="sxs-lookup"><span data-stu-id="0789e-109">The ODBC versions of bulk copy functions return the standard bulk copy return codes of SUCCEED or FAILED, not ODBC-style return codes, such as SQL_SUCCESS or SQL_ERROR.</span></span>  
  
-   <span data-ttu-id="0789e-110">为 DB-LIBRARY [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*varlen*参数指定的值以不同于 ODBC **bcp_bind**_cbData_参数的方式进行解释。</span><span class="sxs-lookup"><span data-stu-id="0789e-110">The values specified for the DB-Library [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*varlen* parameter are interpreted differently than the ODBC **bcp_bind**_cbData_ parameter.</span></span>  
  
    |<span data-ttu-id="0789e-111">指示条件</span><span class="sxs-lookup"><span data-stu-id="0789e-111">Condition indicated</span></span>|<span data-ttu-id="0789e-112">DB-LIBRARY *varlen*值</span><span class="sxs-lookup"><span data-stu-id="0789e-112">DB-Library *varlen* value</span></span>|<span data-ttu-id="0789e-113">ODBC *cbData*值</span><span class="sxs-lookup"><span data-stu-id="0789e-113">ODBC *cbData* value</span></span>|  
    |-------------------------|--------------------------------|-------------------------|  
    |<span data-ttu-id="0789e-114">提供 Null 值</span><span class="sxs-lookup"><span data-stu-id="0789e-114">Null values supplied</span></span>|<span data-ttu-id="0789e-115">0</span><span class="sxs-lookup"><span data-stu-id="0789e-115">0</span></span>|<span data-ttu-id="0789e-116">-1 (SQL_NULL_DATA)</span><span class="sxs-lookup"><span data-stu-id="0789e-116">-1 (SQL_NULL_DATA)</span></span>|  
    |<span data-ttu-id="0789e-117">提供变量数据</span><span class="sxs-lookup"><span data-stu-id="0789e-117">Variable data supplied</span></span>|<span data-ttu-id="0789e-118">-1</span><span class="sxs-lookup"><span data-stu-id="0789e-118">-1</span></span>|<span data-ttu-id="0789e-119">-10 (SQL_VARLEN_DATA)</span><span class="sxs-lookup"><span data-stu-id="0789e-119">-10 (SQL_VARLEN_DATA)</span></span>|  
    |<span data-ttu-id="0789e-120">零长度字符或二进制字符串</span><span class="sxs-lookup"><span data-stu-id="0789e-120">Zero length character or binary string</span></span>|<span data-ttu-id="0789e-121">NA</span><span class="sxs-lookup"><span data-stu-id="0789e-121">NA</span></span>|<span data-ttu-id="0789e-122">0</span><span class="sxs-lookup"><span data-stu-id="0789e-122">0</span></span>|  
  
     <span data-ttu-id="0789e-123">在 DB-LIBRARY 中， *varlen*值为-1 表示提供可变长度数据，ODBC *cbData*中的数据将被解释为仅提供 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="0789e-123">In DB-Library, a *varlen* value of -1 indicates that variable length data is being supplied, which in the ODBC *cbData* is interpreted to mean that only NULL values are being supplied.</span></span> <span data-ttu-id="0789e-124">将-1 的任何 DB-LIBRARY *varlen*规范更改为 SQL_VARLEN_DATA，并将所有*varlen*规范（0）更改为 SQL_NULL_DATA。</span><span class="sxs-lookup"><span data-stu-id="0789e-124">Change any DB-Library *varlen* specifications of -1 to SQL_VARLEN_DATA and any *varlen* specifications of 0 to SQL_NULL_DATA.</span></span>  
  
-   <span data-ttu-id="0789e-125">DB-LIBRARY **bcp \_ colfmt**_file \_ collen_和 ODBC [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*cbUserData*与上面提到的**bcp_bind**_varlen_和*cbData*参数相同。</span><span class="sxs-lookup"><span data-stu-id="0789e-125">The DB-Library **bcp\_colfmt**_file\_collen_ and the ODBC [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*cbUserData* have the same issue as the **bcp_bind**_varlen_ and *cbData* parameters noted above.</span></span> <span data-ttu-id="0789e-126">将-1 的任何 DB-LIBRARY *file_collen*规范更改 SQL_VARLEN_DATA，并将所有*file_collen*规范0更改为 SQL_NULL_DATA。</span><span class="sxs-lookup"><span data-stu-id="0789e-126">Change any DB-Library *file_collen* specifications of -1 to SQL_VARLEN_DATA and any *file_collen* specifications of 0 to SQL_NULL_DATA.</span></span>  
  
-   <span data-ttu-id="0789e-127">ODBC [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)函数的*iValue*参数是一个 void 指针。</span><span class="sxs-lookup"><span data-stu-id="0789e-127">The *iValue* parameter of the ODBC [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) function is a void pointer.</span></span> <span data-ttu-id="0789e-128">在 DB-LIBRARY 中， *iValue*是一个整数。</span><span class="sxs-lookup"><span data-stu-id="0789e-128">In DB-Library, *iValue* was an integer.</span></span> <span data-ttu-id="0789e-129">将 ODBC *iValue*的值强制转换为 void \*。</span><span class="sxs-lookup"><span data-stu-id="0789e-129">Cast the values for the ODBC *iValue* to void \*.</span></span>  
  
-   <span data-ttu-id="0789e-130">**Bcp_control**选项 BCPMAXERRS 指定大容量复制操作失败之前有多少单独行出现错误。</span><span class="sxs-lookup"><span data-stu-id="0789e-130">The **bcp_control** option BCPMAXERRS specifies how many individual rows can have errors before a bulk copy operation fails.</span></span> <span data-ttu-id="0789e-131">BCPMAXERRS 的默认值为 0 (第一次错误时失败) ODBC 版本中**bcp_control**和10的第一个错误。</span><span class="sxs-lookup"><span data-stu-id="0789e-131">The default for BCPMAXERRS is 0 (fail on first error) in the DB-Library version of **bcp_control** and 10 in the ODBC version.</span></span> <span data-ttu-id="0789e-132">必须更改依赖于默认值0以终止大容量复制操作的 DB-LIBRARY 应用程序，以调用 ODBC **bcp_control**将 BCPMAXERRS 设置为0。</span><span class="sxs-lookup"><span data-stu-id="0789e-132">DB-Library applications that depend on the default of 0 to terminate a bulk copy operation must be changed to call the ODBC **bcp_control** to set BCPMAXERRS to 0.</span></span>  
  
-   <span data-ttu-id="0789e-133">ODBC **bcp_control**函数支持**bcp_control**的 db-library 版本不支持以下选项：</span><span class="sxs-lookup"><span data-stu-id="0789e-133">The ODBC **bcp_control** function supports the following options not supported by the DB-Library version of **bcp_control**:</span></span>  
  
    -   <span data-ttu-id="0789e-134">BCPODBC</span><span class="sxs-lookup"><span data-stu-id="0789e-134">BCPODBC</span></span>  
  
         <span data-ttu-id="0789e-135">如果设置为 TRUE，则指定以字符格式保存的**datetime**和**smalldatetime**值将具有 ODBC 时间戳转义序列前缀和后缀。</span><span class="sxs-lookup"><span data-stu-id="0789e-135">When set to TRUE, specifies that **datetime** and **smalldatetime** values saved in character format will have the ODBC timestamp escape sequence prefix and suffix.</span></span> <span data-ttu-id="0789e-136">这仅适用于 BCP_OUT 操作。</span><span class="sxs-lookup"><span data-stu-id="0789e-136">This only applies to BCP_OUT operations.</span></span>  
  
         <span data-ttu-id="0789e-137">将 BCPODBC 设置为 FALSE 时，转换为字符串的**日期时间**值将输出为：</span><span class="sxs-lookup"><span data-stu-id="0789e-137">With BCPODBC set to FALSE, a **datetime** value converted to a character string is output as:</span></span>  
  
        ```  
        1997-01-01 00:00:00.000  
        ```  
  
         <span data-ttu-id="0789e-138">如果将 BCPODBC 设置为 TRUE，则相同的**datetime**值将输出为：</span><span class="sxs-lookup"><span data-stu-id="0789e-138">With BCPODBC set to TRUE, the same **datetime** value is output as:</span></span>  
  
        ```  
        {ts '1997-01-01 00:00:00.000' }  
        ```  
  
    -   <span data-ttu-id="0789e-139">BCPKEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="0789e-139">BCPKEEPIDENTITY</span></span>  
  
         <span data-ttu-id="0789e-140">设置为 TRUE 时，指定大容量复制函数插入为具有标识约束的列提供的数据值。</span><span class="sxs-lookup"><span data-stu-id="0789e-140">When set to TRUE, specifies that bulk copy functions insert data values supplied for columns with identity constraints.</span></span> <span data-ttu-id="0789e-141">如果未进行设置，则为插入的行生成新标识值。</span><span class="sxs-lookup"><span data-stu-id="0789e-141">If this is not set, new identity values are generated for the inserted rows.</span></span>  
  
    -   <span data-ttu-id="0789e-142">BCPHINTS</span><span class="sxs-lookup"><span data-stu-id="0789e-142">BCPHINTS</span></span>  
  
         <span data-ttu-id="0789e-143">指定各种大容量复制优化措施。</span><span class="sxs-lookup"><span data-stu-id="0789e-143">Specifies various bulk copy optimizations.</span></span> <span data-ttu-id="0789e-144">该选项无法在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 6.5 或更早版本上使用。</span><span class="sxs-lookup"><span data-stu-id="0789e-144">This option cannot be used on 6.5 or earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="0789e-145">BCPFILECP</span><span class="sxs-lookup"><span data-stu-id="0789e-145">BCPFILECP</span></span>  
  
         <span data-ttu-id="0789e-146">指定大容量复制文件的代码页。</span><span class="sxs-lookup"><span data-stu-id="0789e-146">Specifies the code page of the bulk copy file.</span></span>  
  
    -   <span data-ttu-id="0789e-147">BCPUNICODEFILE</span><span class="sxs-lookup"><span data-stu-id="0789e-147">BCPUNICODEFILE</span></span>  
  
         <span data-ttu-id="0789e-148">指定字符模式大容量复制文件是 Unicode 文件。</span><span class="sxs-lookup"><span data-stu-id="0789e-148">Specifies that a character mode bulk copy file is a Unicode file.</span></span>  
  
-   <span data-ttu-id="0789e-149">ODBC **bcp_colfmt**函数不支持 SQLCHAR 的*file_type*指示器，因为它与 ODBC SQLCHAR typedef 冲突。</span><span class="sxs-lookup"><span data-stu-id="0789e-149">The ODBC **bcp_colfmt** function does not support the *file_type* indicator of SQLCHAR because it conflicts with the ODBC SQLCHAR typedef.</span></span> <span data-ttu-id="0789e-150">使用 SQLCHARACTER 代替**bcp_colfmt**。</span><span class="sxs-lookup"><span data-stu-id="0789e-150">Use SQLCHARACTER instead for **bcp_colfmt**.</span></span>  
  
-   <span data-ttu-id="0789e-151">在大容量复制函数的 ODBC 版本中，在字符串中使用**datetime**和**smalldatetime**值的格式是以 yyyy-mm-dd hh： mm： SS 格式表示的 odbc 格式;**smalldatetime**值使用 yyyy-mm-dd hh： mm： ss 格式。</span><span class="sxs-lookup"><span data-stu-id="0789e-151">In the ODBC versions of bulk copy functions, the format for working with **datetime** and **smalldatetime** values in character strings is the ODBC format of yyyy-mm-dd hh:mm:ss.sss; **smalldatetime** values use the ODBC format of yyyy-mm-dd hh:mm:ss.</span></span>  
  
     <span data-ttu-id="0789e-152">大容量复制函数的 DB-LIBRARY 版本使用几种格式的字符串接受**datetime**和**smalldatetime**值：</span><span class="sxs-lookup"><span data-stu-id="0789e-152">The DB-Library versions of the bulk copy functions accept **datetime** and **smalldatetime** values in character strings using several formats:</span></span>  
  
    -   <span data-ttu-id="0789e-153">默认格式为*mmm dd yyyy hh： mmxx* ，其中*xx*是 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="0789e-153">The default format is *mmm dd yyyy hh:mmxx* where *xx* is either AM or PM.</span></span>  
  
    -   <span data-ttu-id="0789e-154">DB 库**dbconvert**函数支持的任何格式的**datetime**和**smalldatetime**字符字符串。</span><span class="sxs-lookup"><span data-stu-id="0789e-154">**datetime** and **smalldatetime** character strings in any format supported by the DB-Library **dbconvert** function.</span></span>  
  
    -   <span data-ttu-id="0789e-155">当在客户端网络实用工具的 "DB-LIBRARY**选项**" 选项卡上选中 "**使用国际设置**" 框时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，db-library 大容量复制函数也会接受为客户端计算机注册表的区域设置定义的区域日期格式的日期。</span><span class="sxs-lookup"><span data-stu-id="0789e-155">When the **Use international settings** box is checked on the DB-Library **Options** tab of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Network Utility, the DB-Library bulk copy functions also accept dates in the regional date format defined for the locale setting of the client computer registry.</span></span>  
  
     <span data-ttu-id="0789e-156">DB-LIBRARY 大容量复制函数不接受 ODBC **datetime**和**smalldatetime**格式。</span><span class="sxs-lookup"><span data-stu-id="0789e-156">The DB-Library bulk copy functions do not accept the ODBC **datetime** and **smalldatetime** formats.</span></span>  
  
     <span data-ttu-id="0789e-157">如果 SQL_SOPT_SS_REGIONALIZE 语句属性设置为 SQL_RE_ON，则 ODBC 大容量复制函数接受的日期格式可以是为客户端计算机注册表的区域设置定义的区域日期格式。</span><span class="sxs-lookup"><span data-stu-id="0789e-157">If the SQL_SOPT_SS_REGIONALIZE statement attribute is set to SQL_RE_ON, the ODBC bulk copy functions accept dates in the regional date format defined for the locale setting of the client computer registry.</span></span>  
  
-   <span data-ttu-id="0789e-158">当以字符格式输出**money**值时，ODBC 大容量复制函数提供四位数的精度，没有逗号分隔符;DB-LIBRARY 版本仅提供两位数的精度，并包含逗号分隔符。</span><span class="sxs-lookup"><span data-stu-id="0789e-158">When outputting **money** values in character format, ODBC bulk copy functions supply four digits of precision and no comma separators; DB-Library versions only supply two digits of precision and include the comma separators.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0789e-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0789e-159">See Also</span></span>  
 <span data-ttu-id="0789e-160">[&#40;ODBC&#41;执行大容量复制操作](performing-bulk-copy-operations-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="0789e-160">[Performing Bulk Copy Operations &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md) </span></span>  
 [<span data-ttu-id="0789e-161">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="0789e-161">Bulk Copy Functions</span></span>](../native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
