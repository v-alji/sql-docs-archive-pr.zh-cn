---
title: bcp_bind |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_bind
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_bind function
ms.assetid: 6e335a5c-64b2-4bcf-a88f-35dc9393f329
author: rothja
ms.author: jroth
ms.openlocfilehash: db0a58398bf47bd0bb96bd1ef587d41890ed8461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688900"
---
# <a name="bcp_bind"></a><span data-ttu-id="2acbb-102">bcp_bind</span><span class="sxs-lookup"><span data-stu-id="2acbb-102">bcp_bind</span></span>
  <span data-ttu-id="2acbb-103">将程序变量中的数据绑定到表列，以便大容量复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2acbb-103">Binds data from a program variable to a table column for bulk copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2acbb-104">语法</span><span class="sxs-lookup"><span data-stu-id="2acbb-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_bind (  
HDBC   
hdbc  
,   
LPCBYTE   
pData  
,  
INT   
cbIndicator  
,  
DBINT   
cbData  
,  
LPCBYTE   
pTerm  
,  
INT   
cbTerm  
,  
INT   
eDataType  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="2acbb-105">参数</span><span class="sxs-lookup"><span data-stu-id="2acbb-105">Arguments</span></span>  
 <span data-ttu-id="2acbb-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="2acbb-106">*hdbc*</span></span>  
 <span data-ttu-id="2acbb-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="2acbb-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="2acbb-108">*pData*</span><span class="sxs-lookup"><span data-stu-id="2acbb-108">*pData*</span></span>  
 <span data-ttu-id="2acbb-109">指向已复制数据的指针。</span><span class="sxs-lookup"><span data-stu-id="2acbb-109">Is a pointer to the data copied.</span></span> <span data-ttu-id="2acbb-110">如果*eDataType*为 SQLTEXT、SQLNTEXT、SQLXML、SQLUDT、SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY、SQLNCHAR 或 SQLIMAGE，则*PDATA*可以为 NULL。</span><span class="sxs-lookup"><span data-stu-id="2acbb-110">If *eDataType* is SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR or SQLIMAGE, *pData* can be NULL.</span></span> <span data-ttu-id="2acbb-111">空*pData*表示长数据值将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用[bcp_moretext](bcp-moretext.md)以区块形式发送到。</span><span class="sxs-lookup"><span data-stu-id="2acbb-111">A NULL *pData* indicates that long data values will be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in chunks using [bcp_moretext](bcp-moretext.md).</span></span> <span data-ttu-id="2acbb-112">如果与用户绑定字段相对应的列是一个 BLOB 列，则用户只应将*pData*设置为 NULL，否则**bcp_bind**将失败。</span><span class="sxs-lookup"><span data-stu-id="2acbb-112">The user should only set *pData* to NULL if the column corresponding to the user bound field is a BLOB column otherwise **bcp_bind** will fail.</span></span>  
  
 <span data-ttu-id="2acbb-113">如果数据中存在指示符，这些指示符则在内存中直接显示在数据之前。</span><span class="sxs-lookup"><span data-stu-id="2acbb-113">If indicators are present in the data, they appear in memory directly before the data.</span></span> <span data-ttu-id="2acbb-114">在这种情况下， *pData*参数指向指示器变量，并且大容量复制使用指示器的宽度（ *cbIndicator*参数）正确地处理用户数据。</span><span class="sxs-lookup"><span data-stu-id="2acbb-114">The *pData* parameter points to the indicator variable in this case, and the width of the indicator, the *cbIndicator* parameter, is used by bulk copy to address user data correctly.</span></span>  
  
 <span data-ttu-id="2acbb-115">cbIndicator\*\*</span><span class="sxs-lookup"><span data-stu-id="2acbb-115">*cbIndicator*</span></span>  
 <span data-ttu-id="2acbb-116">列数据的长度或 Null 指示符的长度（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="2acbb-116">Is the length, in bytes, of a length or null indicator for the column's data.</span></span> <span data-ttu-id="2acbb-117">有效指示器长度值是 0（不使用任何指示器时）、1、2、4 或 8。</span><span class="sxs-lookup"><span data-stu-id="2acbb-117">Valid indicator length values are 0 (when using no indicator), 1, 2, 4, or 8.</span></span> <span data-ttu-id="2acbb-118">指示符在内存中直接显示在任何数据之前。</span><span class="sxs-lookup"><span data-stu-id="2acbb-118">Indicators appear in memory directly before any data.</span></span> <span data-ttu-id="2acbb-119">例如，可以使用以下结构类型定义通过大容量复制将整数值插入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表：</span><span class="sxs-lookup"><span data-stu-id="2acbb-119">For example, the following structure type definition could be used to insert integer values into an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table using bulk copy:</span></span>  
  
```  
typedef struct tagBCPBOUNDINT  
    {  
    int iIndicator;  
    int Value;  
    } BCPBOUNDINT;  
```  
  
 <span data-ttu-id="2acbb-120">在本例中， *pData*参数将设置为结构的声明实例的地址，即 BCPBOUNDINT *iIndicator*结构成员的地址。</span><span class="sxs-lookup"><span data-stu-id="2acbb-120">In the example case, the *pData* parameter would be set to the address of a declared instance of the structure, the address of the BCPBOUNDINT *iIndicator* structure member.</span></span> <span data-ttu-id="2acbb-121">*CbIndicator*参数将设置为 (sizeof (int) # A3 的整数大小， *cbData*参数将再次设置为 (sizeof (int) # A7 的整数大小。</span><span class="sxs-lookup"><span data-stu-id="2acbb-121">The *cbIndicator* parameter would be set to the size of an integer (sizeof(int)), and the *cbData* parameter would again be set to the size of an integer (sizeof(int)).</span></span> <span data-ttu-id="2acbb-122">若要向包含绑定列的 NULL 值的服务器大容量复制行，则应将实例的*iIndicator*成员的值设置为 SQL_NULL_DATA。</span><span class="sxs-lookup"><span data-stu-id="2acbb-122">To bulk copy a row to the server containing a NULL value for the bound column, the value of the instance's *iIndicator* member should be set to SQL_NULL_DATA.</span></span>  
  
 <span data-ttu-id="2acbb-123">*cbData*</span><span class="sxs-lookup"><span data-stu-id="2acbb-123">*cbData*</span></span>  
 <span data-ttu-id="2acbb-124">程序变量中数据的字节计数，不包括任何长度/Null 指示符或终止符的长度。</span><span class="sxs-lookup"><span data-stu-id="2acbb-124">Is the count of bytes of data in the program variable, not including the length of any length or null indicator or terminator.</span></span>  
  
 <span data-ttu-id="2acbb-125">将*cbData*设置为 SQL_NULL_DATA 表示复制到服务器的所有行都包含该列的 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="2acbb-125">Setting *cbData* to SQL_NULL_DATA signifies that all rows copied to the server contain a NULL value for the column.</span></span>  
  
 <span data-ttu-id="2acbb-126">将*cbData*设置为 SQL_VARLEN_DATA 指示系统将使用字符串终止符或其他方法来确定复制的数据的长度。</span><span class="sxs-lookup"><span data-stu-id="2acbb-126">Setting *cbData* to SQL_VARLEN_DATA indicates that the system will use a string terminator, or other method, to determine the length of data copied.</span></span>  
  
 <span data-ttu-id="2acbb-127">对于固定长度的数据类型（如整数），该数据类型指示系统中的数据的长度。</span><span class="sxs-lookup"><span data-stu-id="2acbb-127">For fixed-length data types, such as integers, the data type indicates the length of the data to the system.</span></span> <span data-ttu-id="2acbb-128">因此，对于固定长度的数据类型， *cbData*可以安全地 SQL_VARLEN_DATA 或数据的长度。</span><span class="sxs-lookup"><span data-stu-id="2acbb-128">Therefore, for fixed-length data types, *cbData* can safely be SQL_VARLEN_DATA or the length of the data.</span></span>  
  
 <span data-ttu-id="2acbb-129">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 字符和二进制数据类型， *cbData*可以是 SQL_VARLEN_DATA、SQL_NULL_DATA、某些正值或0。</span><span class="sxs-lookup"><span data-stu-id="2acbb-129">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, *cbData* can be SQL_VARLEN_DATA, SQL_NULL_DATA, some positive value, or 0.</span></span> <span data-ttu-id="2acbb-130">如果 SQL_VARLEN_DATA *cbData* ，则系统使用长度/空指示器 (如果存在) 或终止序列来确定数据的长度。</span><span class="sxs-lookup"><span data-stu-id="2acbb-130">If *cbData* is SQL_VARLEN_DATA, the system uses either a length/null indicator (if present) or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="2acbb-131">如果同时提供指示符和终止符序列，系统则使用二者中可导致数据复制量最少的那一个。</span><span class="sxs-lookup"><span data-stu-id="2acbb-131">If both are supplied, the system uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="2acbb-132">如果*cbData* SQL_VARLEN_DATA，则列的数据类型为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 字符或二进制类型，并且不指定长度指示符和终止符序列，系统将返回错误消息。</span><span class="sxs-lookup"><span data-stu-id="2acbb-132">If *cbData* is SQL_VARLEN_DATA, the data type of the column is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="2acbb-133">如果*cbData*为0或正值，则系统使用*cbData*作为数据长度。</span><span class="sxs-lookup"><span data-stu-id="2acbb-133">If *cbData* is 0 or a positive value, the system uses *cbData* as the data length.</span></span> <span data-ttu-id="2acbb-134">但是，如果除正*cbData*值外，还提供了一个长度指示器或终止符序列，则系统将通过使用导致数据复制量最少的方法来确定数据长度。</span><span class="sxs-lookup"><span data-stu-id="2acbb-134">However, if, in addition to a positive *cbData* value, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="2acbb-135">*CbData*参数值表示数据的字节计数。</span><span class="sxs-lookup"><span data-stu-id="2acbb-135">The *cbData* parameter value represents the count of bytes of data.</span></span> <span data-ttu-id="2acbb-136">如果字符数据由 Unicode 宽字符表示，则正的*cbData*参数值表示字符数乘以每个字符的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="2acbb-136">If character data is represented by Unicode wide characters, then a positive *cbData* parameter value represents the number of characters multiplied by the size in bytes of each character.</span></span>  
  
 <span data-ttu-id="2acbb-137">*pTerm*</span><span class="sxs-lookup"><span data-stu-id="2acbb-137">*pTerm*</span></span>  
 <span data-ttu-id="2acbb-138">指向标记该程序变量末尾的字节模式（如果有）的指针。</span><span class="sxs-lookup"><span data-stu-id="2acbb-138">Is a pointer to the byte pattern, if any, that marks the end of this program variable.</span></span> <span data-ttu-id="2acbb-139">例如，ANSI 和 MBCS C 字符串通常采用 1 个字节的终止符 (\0)。</span><span class="sxs-lookup"><span data-stu-id="2acbb-139">For example, ANSI and MBCS C strings usually have a 1-byte terminator (\0).</span></span>  
  
 <span data-ttu-id="2acbb-140">如果变量没有终止符，则将*pTerm*设置为 NULL。</span><span class="sxs-lookup"><span data-stu-id="2acbb-140">If there is no terminator for the variable, set *pTerm* to NULL.</span></span>  
  
 <span data-ttu-id="2acbb-141">您可以使用空字符串 ("") 将 C Null 终止符指定为程序变量终止符。</span><span class="sxs-lookup"><span data-stu-id="2acbb-141">You can use an empty string ("") to designate the C null terminator as the program-variable terminator.</span></span> <span data-ttu-id="2acbb-142">由于以 null 结尾的空字符串构成一个字节 (终止符字节自身) ，请将*cbTerm*设置为1。</span><span class="sxs-lookup"><span data-stu-id="2acbb-142">Because the null-terminated empty string constitutes a single byte (the terminator byte itself), set *cbTerm* to 1.</span></span> <span data-ttu-id="2acbb-143">例如，若要指示*szName*中的字符串以 null 结尾并且应使用该终止符指示长度，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2acbb-143">For example, to indicate that the string in *szName* is null-terminated and that the terminator should be used to indicate the length:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0,  
   SQL_VARLEN_DATA, "", 1,  
   SQLCHARACTER, 2)  
```  
  
 <span data-ttu-id="2acbb-144">此示例的示例形式可能表示将15个字符从*szName*变量复制到绑定表的第二列：</span><span class="sxs-lookup"><span data-stu-id="2acbb-144">A nonterminated form of this example could indicate that 15 characters be copied from the *szName* variable to the second column of the bound table:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0, 15,   
   NULL, 0, SQLCHARACTER, 2)  
```  
  
 <span data-ttu-id="2acbb-145">大容量复制 API 根据需要执行 Unicode 到 MBCS 的字符转换。</span><span class="sxs-lookup"><span data-stu-id="2acbb-145">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="2acbb-146">确保终止符字节字符串和字节字符串的长度均已正确设置。</span><span class="sxs-lookup"><span data-stu-id="2acbb-146">Make sure that both the terminator byte string and the length of the byte string are set correctly.</span></span> <span data-ttu-id="2acbb-147">例如，若要指示*szName*中的字符串是 unicode 宽字符串，则由 unicode null 终止符值终止：</span><span class="sxs-lookup"><span data-stu-id="2acbb-147">For example, to indicate that the string in *szName* is a Unicode wide character string, terminated by the Unicode null terminator value:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0,   
   SQL_VARLEN_DATA, L"",  
   sizeof(WCHAR), SQLNCHAR, 2)  
```  
  
 <span data-ttu-id="2acbb-148">如果绑定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列是宽字符，则不会对[bcp_sendrow](bcp-sendrow.md)执行任何转换。</span><span class="sxs-lookup"><span data-stu-id="2acbb-148">If the bound [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column is wide character, no conversion is performed on [bcp_sendrow](bcp-sendrow.md).</span></span> <span data-ttu-id="2acbb-149">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列为 MBCS 字符类型，将数据发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时将执行从宽字符到多字节字符的转换。</span><span class="sxs-lookup"><span data-stu-id="2acbb-149">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column is an MBCS character type, wide character to multibyte character conversion is performed as the data is sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2acbb-150">*cbTerm*</span><span class="sxs-lookup"><span data-stu-id="2acbb-150">*cbTerm*</span></span>  
 <span data-ttu-id="2acbb-151">存在于程序变量的终止符（如果有）中的字节计数。</span><span class="sxs-lookup"><span data-stu-id="2acbb-151">Is the count of bytes present in the terminator for the program variable, if any.</span></span> <span data-ttu-id="2acbb-152">如果变量没有终止符，则将*cbTerm*设置为0。</span><span class="sxs-lookup"><span data-stu-id="2acbb-152">If there is no terminator for the variable, set *cbTerm* to 0.</span></span>  
  
 <span data-ttu-id="2acbb-153">*eDataType*</span><span class="sxs-lookup"><span data-stu-id="2acbb-153">*eDataType*</span></span>  
 <span data-ttu-id="2acbb-154">程序变量的 C 数据类型。</span><span class="sxs-lookup"><span data-stu-id="2acbb-154">Is the C data type of the program variable.</span></span> <span data-ttu-id="2acbb-155">程序变量中的数据转换为数据库列的类型。</span><span class="sxs-lookup"><span data-stu-id="2acbb-155">The data in the program variable is converted to the type of the database column.</span></span> <span data-ttu-id="2acbb-156">如果该参数为 0，则不执行转换。</span><span class="sxs-lookup"><span data-stu-id="2acbb-156">If this parameter is 0, no conversion is performed.</span></span>  
  
 <span data-ttu-id="2acbb-157">*EDataType*参数由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlncli.msi 中的数据类型标记进行枚举，而非 ODBC C 数据类型枚举器。</span><span class="sxs-lookup"><span data-stu-id="2acbb-157">The *eDataType* parameter is enumerated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type tokens in sqlncli.h, not the ODBC C data type enumerators.</span></span> <span data-ttu-id="2acbb-158">例如，您可以使用特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 SQLINT2 类型指定一个两个字节的整数：ODBC 类型的 SQL_C_SHORT。</span><span class="sxs-lookup"><span data-stu-id="2acbb-158">For example, you can specify a two-byte integer, ODBC type SQL_C_SHORT, using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific type SQLINT2.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="2acbb-159">在 deploymentdebugloglevel 中引入了对 SQLXML 和 SQLUDT 数据类型标记的支持 *`eDataType`* 。</span><span class="sxs-lookup"><span data-stu-id="2acbb-159">introduced support for SQLXML and SQLUDT data type tokens in the *`eDataType`* paramenter.</span></span>  
  
 <span data-ttu-id="2acbb-160">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="2acbb-160">*idxServerCol*</span></span>  
 <span data-ttu-id="2acbb-161">数据复制的目标数据库表中的列的序号位置。</span><span class="sxs-lookup"><span data-stu-id="2acbb-161">Is the ordinal position of the column in the database table to which the data is copied.</span></span> <span data-ttu-id="2acbb-162">表中的第一列为列 1。</span><span class="sxs-lookup"><span data-stu-id="2acbb-162">The first column in a table is column 1.</span></span> <span data-ttu-id="2acbb-163">列的序号位置由[SQLColumns](../native-client-odbc-api/sqlcolumns.md)报告。</span><span class="sxs-lookup"><span data-stu-id="2acbb-163">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="2acbb-164">返回</span><span class="sxs-lookup"><span data-stu-id="2acbb-164">Returns</span></span>  
 <span data-ttu-id="2acbb-165">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="2acbb-165">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2acbb-166">备注</span><span class="sxs-lookup"><span data-stu-id="2acbb-166">Remarks</span></span>  
 <span data-ttu-id="2acbb-167">使用**bcp_bind**可以快速有效地将程序变量中的数据复制到中的表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2acbb-167">Use **bcp_bind** for a fast, efficient way to copy data from a program variable into a table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2acbb-168">调用此或任何其他大容量复制函数之前调用[bcp_init](bcp-init.md) 。</span><span class="sxs-lookup"><span data-stu-id="2acbb-168">Call [bcp_init](bcp-init.md) before calling this or any other bulk-copy function.</span></span> <span data-ttu-id="2acbb-169">调用**bcp_init**会设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用于大容量复制的目标表。</span><span class="sxs-lookup"><span data-stu-id="2acbb-169">Calling **bcp_init** sets the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] target table for bulk copy.</span></span> <span data-ttu-id="2acbb-170">在调用**bcp_init**以便与**bcp_bind**和[bcp_sendrow](bcp-sendrow.md)一起使用时，指示数据文件的**bcp_init** _szDataFile_参数设置为 NULL;**bcp_init**_eDirection_参数设置为 DB_IN。</span><span class="sxs-lookup"><span data-stu-id="2acbb-170">When calling **bcp_init** for use with **bcp_bind** and [bcp_sendrow](bcp-sendrow.md), the **bcp_init** _szDataFile_ parameter, indicating the data file, is set to NULL; the **bcp_init**_eDirection_ parameter is set to DB_IN.</span></span>  
  
 <span data-ttu-id="2acbb-171">为要复制到的表中的每个列单独**bcp_bind**调用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2acbb-171">Make a separate **bcp_bind** call for every column in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table into which you want to copy.</span></span> <span data-ttu-id="2acbb-172">进行必要的**bcp_bind**调用后，调用**bcp_sendrow**将数据从程序变量发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2acbb-172">After the necessary **bcp_bind** calls have been made, then call **bcp_sendrow** to send a row of data from your program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2acbb-173">不支持重新绑定列。</span><span class="sxs-lookup"><span data-stu-id="2acbb-173">Rebinding a column is not supported.</span></span>  
  
 <span data-ttu-id="2acbb-174">每当你想要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提交已收到的行时，请调用[bcp_batch](bcp-batch.md)。</span><span class="sxs-lookup"><span data-stu-id="2acbb-174">Whenever you want [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to commit the rows already received, call [bcp_batch](bcp-batch.md).</span></span> <span data-ttu-id="2acbb-175">例如，对于每1000行或任何其他间隔，请调用一次**bcp_batch** 。</span><span class="sxs-lookup"><span data-stu-id="2acbb-175">For example, call **bcp_batch** once for every 1000 rows inserted or at any other interval.</span></span>  
  
 <span data-ttu-id="2acbb-176">如果不再有要插入的行，请调用[bcp_done](bcp-done.md)。</span><span class="sxs-lookup"><span data-stu-id="2acbb-176">When there are no more rows to be inserted, call [bcp_done](bcp-done.md).</span></span> <span data-ttu-id="2acbb-177">如果没有这样做，会导致错误。</span><span class="sxs-lookup"><span data-stu-id="2acbb-177">Failure to do so results in an error.</span></span>  
  
 <span data-ttu-id="2acbb-178">使用[bcp_control](bcp-control.md)指定的控件参数设置对**bcp_bind**行传输不起作用。</span><span class="sxs-lookup"><span data-stu-id="2acbb-178">Control parameter settings, specified with [bcp_control](bcp-control.md), have no effect on **bcp_bind** row transfers.</span></span>  
  
 <span data-ttu-id="2acbb-179">如果列的*pData*设置为 NULL，因为它的值将由对[bcp_moretext](bcp-moretext.md)的调用提供，则*EDATATYPE*设置为 SQLTEXT、SQLNTEXT、SQLXML、SQLUDT、SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY、SQLNCHAR 或 SQLIMAGE 的所有后续列也必须与*pData*设置为 NULL，并且它们的值还必须通过调用来提供 `bcp_moretext` 。</span><span class="sxs-lookup"><span data-stu-id="2acbb-179">If *pData* for a column is set to NULL because its value will be supplied by calls to [bcp_moretext](bcp-moretext.md), any subsequent columns with *eDataType* set to SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR, or SQLIMAGE must also be bound with *pData* set to NULL, and their values must also be supplied by calls to `bcp_moretext`.</span></span>  
  
 <span data-ttu-id="2acbb-180">对于新的大值类型（如 `varchar(max)` 、 `varbinary(max)` 或）， `nvarchar(max)` 可以在*SQLNCHAR*参数中使用 SQLCHARACTER、SQLVARCHAR、SQLVARBINARY、SQLBINARY 和 eDataType 作为类型指示符。</span><span class="sxs-lookup"><span data-stu-id="2acbb-180">For new large value types, such as `varchar(max)`, `varbinary(max)`, or `nvarchar(max)`, you can use SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, and SQLNCHAR as type indicators in the *eDataType* parameter.</span></span>  
  
 <span data-ttu-id="2acbb-181">如果*cbTerm*不是0，则任何值 (1、2、4或 8) 对于前缀 (*cbIndicator*) 都有效。</span><span class="sxs-lookup"><span data-stu-id="2acbb-181">If *cbTerm* is not 0, any value (1, 2, 4, or 8) is valid for the prefix (*cbIndicator*).</span></span> <span data-ttu-id="2acbb-182">在这种情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 将搜索终止符，计算与终止)  (的数据长度， *i*并将*cbData*设置为 "i" 的较小值和 "前缀" 的值。</span><span class="sxs-lookup"><span data-stu-id="2acbb-182">In this situation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client will search for the terminator, calculate data length with respect to the terminator (*i*), and set the *cbData* to the smaller value of i and the value of prefix.</span></span>  
  
 <span data-ttu-id="2acbb-183">如果*cbTerm*为0，并且*cbIndicator* (前缀) 不是0，则*cbIndicator*必须是8。</span><span class="sxs-lookup"><span data-stu-id="2acbb-183">If *cbTerm* is 0 and *cbIndicator* (the prefix) is not 0, *cbIndicator* must be 8.</span></span> <span data-ttu-id="2acbb-184">此 8 个字节的前缀可以采用以下值：</span><span class="sxs-lookup"><span data-stu-id="2acbb-184">The 8 byte prefix can take the following values:</span></span>  
  
-   <span data-ttu-id="2acbb-185">0xFFFFFFFFFFFFFFFF 表示字段为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="2acbb-185">0xFFFFFFFFFFFFFFFF means a null value for the field</span></span>  
  
-   <span data-ttu-id="2acbb-186">0xFFFFFFFFFFFFFFFE 被视为特殊前缀值，用于有效地向服务器成块发送数据。</span><span class="sxs-lookup"><span data-stu-id="2acbb-186">0xFFFFFFFFFFFFFFFE is treated as a special prefix value which is used for efficiently sending data in chunks to the server.</span></span> <span data-ttu-id="2acbb-187">带有此特殊前缀的数据的格式为：</span><span class="sxs-lookup"><span data-stu-id="2acbb-187">The format of data with this special prefix is:</span></span>  
  
-   <span data-ttu-id="2acbb-188"><SPECIAL_PREFIX> \<0 or more  DATA CHUNKS> <ZERO_CHUNK> 位置：</span><span class="sxs-lookup"><span data-stu-id="2acbb-188"><SPECIAL_PREFIX> \<0 or more  DATA CHUNKS> <ZERO_CHUNK> where:</span></span>  
  
-   <span data-ttu-id="2acbb-189">SPECIAL_PREFIX 为 0xFFFFFFFFFFFFFFFE</span><span class="sxs-lookup"><span data-stu-id="2acbb-189">SPECIAL_PREFIX is 0xFFFFFFFFFFFFFFFE</span></span>  
  
-   <span data-ttu-id="2acbb-190">DATA_CHUNK 是包含块区长度的 4 个字节的前缀，后跟在该 4 个字节的前缀中指定其长度的实际数据。</span><span class="sxs-lookup"><span data-stu-id="2acbb-190">DATA_CHUNK is a 4 byte prefix containing length of the chunk,followed by the actual data whose length is specified in the 4 byte prefix.</span></span>  
  
-   <span data-ttu-id="2acbb-191">ZERO_CHUNK 是全部由零组成的 4 个字节的值 (00000000)，指示数据结束。</span><span class="sxs-lookup"><span data-stu-id="2acbb-191">ZERO_CHUNK is a 4 byte value containing all zeros (00000000) indicating the end of data.</span></span>  
  
-   <span data-ttu-id="2acbb-192">任何其他有效的 8 个字节的长度均被视为常规数据长度。</span><span class="sxs-lookup"><span data-stu-id="2acbb-192">Any other valid 8 byte length is treated as a regular data length.</span></span>  
  
 <span data-ttu-id="2acbb-193">使用**bcp_bind**时调用[bcp_columns](bcp-columns.md)会导致错误。</span><span class="sxs-lookup"><span data-stu-id="2acbb-193">Calling [bcp_columns](bcp-columns.md) when using **bcp_bind** results in an error.</span></span>  
  
## <a name="bcp_bind-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="2acbb-194">bcp_bind 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="2acbb-194">bcp_bind Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="2acbb-195">有关用于日期/时间类型的*eDataType*参数所使用的类型的信息，请参阅[OLE DB 和 ODBC&#41;&#40;的增强日期和时间类型的大容量复制更改](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="2acbb-195">For information about the types used with the *eDataType* parameter for date/time types, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="2acbb-196">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="2acbb-196">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2acbb-197">示例</span><span class="sxs-lookup"><span data-stu-id="2acbb-197">Example</span></span>  
  
```  
#include sql.h  
#include sqlext.h  
#include odbcss.h  
// Variables like henv not specified.  
HDBC      hdbc;  
char         szCompanyName[MAXNAME];  
DBINT      idCompany;  
DBINT      nRowsProcessed;  
DBBOOL      bMoreData;  
char*      pTerm = "\t\t";  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source; return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bcp.   
if (bcp_init(hdbc, "comdb..accounts_info", NULL, NULL  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idCompany, 0, sizeof(DBINT), NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_bind(hdbc, (LPCBYTE) szCompanyName, 0, SQL_VARLEN_DATA,  
   (LPCBYTE) pTerm, strnlen(pTerm, sizeof(pTerm)), SQLCHARACTER, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
while (TRUE)  
   {  
   // Retrieve and process program data.   
   if ((bMoreData = getdata(&idCompany, szCompanyName)) == TRUE)  
      {  
      // Send the data.   
      if (bcp_sendrow(hdbc) == FAIL)  
         {  
         // Raise error and return.  
         return;  
         }  
      }  
   else  
      {  
      // Break out of loop.  
      break;  
      }  
   }  
  
// Terminate the bulk copy operation.  
if ((nRowsProcessed = bcp_done(hdbc)) == -1)  
   {  
   printf_s("Bulk-copy unsuccessful.\n");  
   return;  
   }  
  
printf_s("%ld rows copied.\n", nRowsProcessed);  
```  
  
## <a name="see-also"></a><span data-ttu-id="2acbb-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2acbb-198">See Also</span></span>  
 [<span data-ttu-id="2acbb-199">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="2acbb-199">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
