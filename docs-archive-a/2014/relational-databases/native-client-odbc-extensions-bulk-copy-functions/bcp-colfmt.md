---
title: bcp_colfmt |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colfmt function
ms.assetid: 5c3b6299-80c7-4e84-8e69-4ff33009548e
author: rothja
ms.author: jroth
ms.openlocfilehash: f646f3aaf9a8f640d829020bd6762c07c406b61f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693846"
---
# <a name="bcp_colfmt"></a><span data-ttu-id="cced5-102">bcp_colfmt</span><span class="sxs-lookup"><span data-stu-id="cced5-102">bcp_colfmt</span></span>
  <span data-ttu-id="cced5-103">指定用户文件中的数据的源或目标格式。</span><span class="sxs-lookup"><span data-stu-id="cced5-103">Specifies the source or target format of the data in a user file.</span></span> <span data-ttu-id="cced5-104">用作源格式时， **bcp_colfmt**指定用作大容量复制到表中的数据源的现有数据文件的格式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cced5-104">When used as a source format, **bcp_colfmt** specifies the format of an existing data file used as the source of data in a bulk copy to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="cced5-105">用作目标格式时，将使用**bcp_colfmt**指定的列格式创建数据文件。</span><span class="sxs-lookup"><span data-stu-id="cced5-105">When used as a target format, the data file is created using the column formats specified with **bcp_colfmt**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cced5-106">语法</span><span class="sxs-lookup"><span data-stu-id="cced5-106">Syntax</span></span>  
  
```  
  
RETCODE bcp_colfmt (  
HDBC   
hdbc  
,  
INT  
idxUserDataCol  
,  
BYTE   
eUserDataType  
,  
INT   
cbIndicator  
,  
DBINT   
cbUserData  
,  
LPCBYTE   
pUserDataTerm  
,  
INT   
cbUserDataTerm  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="cced5-107">参数</span><span class="sxs-lookup"><span data-stu-id="cced5-107">Arguments</span></span>  
 <span data-ttu-id="cced5-108">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="cced5-108">*hdbc*</span></span>  
 <span data-ttu-id="cced5-109">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="cced5-109">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="cced5-110">*idxUserDataCol*</span><span class="sxs-lookup"><span data-stu-id="cced5-110">*idxUserDataCol*</span></span>  
 <span data-ttu-id="cced5-111">正在为其指定格式的用户数据文件中的列序号。</span><span class="sxs-lookup"><span data-stu-id="cced5-111">Is the ordinal column number in the user data file for which the format is being specified.</span></span> <span data-ttu-id="cced5-112">第一列为 1。</span><span class="sxs-lookup"><span data-stu-id="cced5-112">The first column is 1.</span></span>  
  
 <span data-ttu-id="cced5-113">*eUserDataType*</span><span class="sxs-lookup"><span data-stu-id="cced5-113">*eUserDataType*</span></span>  
 <span data-ttu-id="cced5-114">用户文件中此列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="cced5-114">Is the data type of this column in the user file.</span></span> <span data-ttu-id="cced5-115">如果与数据库表中相应列的数据类型不同 (*idxServerColumn*) ，则大容量复制会转换数据（如果可能）。</span><span class="sxs-lookup"><span data-stu-id="cced5-115">If different from the data type of the corresponding column in the database table (*idxServerColumn*), bulk copy converts the data if possible.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="cced5-116">在*eUserDataType*参数中引入了对 SQLXML 和 SQLUDT 数据类型标记的支持。</span><span class="sxs-lookup"><span data-stu-id="cced5-116">introduced support for SQLXML and SQLUDT data type tokens in the *eUserDataType* parameter.</span></span>  
  
 <span data-ttu-id="cced5-117">*EUserDataType*参数由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlncli.msi 中的数据类型标记进行枚举，而非 ODBC C 数据类型枚举器。</span><span class="sxs-lookup"><span data-stu-id="cced5-117">The *eUserDataType* parameter is enumerated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type tokens in sqlncli.h, not the ODBC C data type enumerators.</span></span> <span data-ttu-id="cced5-118">例如，可以使用特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的类型 SQLCHARACTER 来指定一个 ODBC 类型 SQL_C_CHAR 的字符串。</span><span class="sxs-lookup"><span data-stu-id="cced5-118">For example, you can specify a character string, ODBC type SQL_C_CHAR, using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific type SQLCHARACTER.</span></span>  
  
 <span data-ttu-id="cced5-119">若要为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型指定默认的数据表示形式，则将此参数设置为 0。</span><span class="sxs-lookup"><span data-stu-id="cced5-119">To specify the default data representation for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, set this parameter to 0.</span></span>  
  
 <span data-ttu-id="cced5-120">若要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *EUSERDATATYPE*为 SQLDECIMAL 或 SQLNUMERIC 时，从大容量复制到文件中：</span><span class="sxs-lookup"><span data-stu-id="cced5-120">For a bulk copy out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] into a file, when *eUserDataType* is SQLDECIMAL or SQLNUMERIC:</span></span>  
  
-   <span data-ttu-id="cced5-121">如果源列不是**decimal**或**numeric**，则使用默认的精度和小数位数。</span><span class="sxs-lookup"><span data-stu-id="cced5-121">If the source column is not **decimal** or **numeric**, the default precision and scale are used.</span></span>  
  
-   <span data-ttu-id="cced5-122">如果源列为**decimal**或**numeric**，则使用源列的精度和小数位数。</span><span class="sxs-lookup"><span data-stu-id="cced5-122">If the source column is **decimal** or **numeric**, the precision and scale of the source column are used.</span></span>  
  
 <span data-ttu-id="cced5-123">cbIndicator\*\*</span><span class="sxs-lookup"><span data-stu-id="cced5-123">*cbIndicator*</span></span>  
 <span data-ttu-id="cced5-124">列数据中的长度/Null 指示器的长度（字节）。</span><span class="sxs-lookup"><span data-stu-id="cced5-124">Is the length, in bytes, of a length/null indicator within the column data.</span></span> <span data-ttu-id="cced5-125">有效指示器长度值是 0（不使用任何指示器时）、1、2、4 或 8。</span><span class="sxs-lookup"><span data-stu-id="cced5-125">Valid indicator length values are 0 (when using no indicator), 1, 2, 4, or 8.</span></span>  
  
 <span data-ttu-id="cced5-126">若要指定默认的大容量复制指示器用法，请将此参数设置为 SQL_VARLEN_DATA。</span><span class="sxs-lookup"><span data-stu-id="cced5-126">To specify default bulk copy indicator usage, set this parameter to SQL_VARLEN_DATA.</span></span>  
  
 <span data-ttu-id="cced5-127">指示器在内存中出现在任何数据的紧前面，在数据文件中出现在它们适用于的数据的紧前面。</span><span class="sxs-lookup"><span data-stu-id="cced5-127">Indicators appear in memory directly before any data, and in the data file directly before the data to which they apply.</span></span>  
  
 <span data-ttu-id="cced5-128">如果使用多种方法来指定数据文件列长度（例如指示器和最大列长度，或者指示器和终止符序列），则大容量复制将选择导致数据复制量最少的方法。</span><span class="sxs-lookup"><span data-stu-id="cced5-128">If more than one means of specifying a data file column length is used (such as an indicator and a maximum column length, or an indicator and a terminator sequence), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="cced5-129">如果列数据可能在长度上发生变化或列可能接受 NULL 作为值，则在没有调整数据格式的用户干预时，大容量复制生成的数据文件将包含指示器。</span><span class="sxs-lookup"><span data-stu-id="cced5-129">Data files generated by bulk copy when no user intervention adjusts the format of the data contain indicators when the column data can vary in length or the column can accept NULL as a value.</span></span>  
  
 <span data-ttu-id="cced5-130">*cbUserData*</span><span class="sxs-lookup"><span data-stu-id="cced5-130">*cbUserData*</span></span>  
 <span data-ttu-id="cced5-131">用户文件中该列数据的最大长度（字节），不包括任何长度指示器或终止符的长度。</span><span class="sxs-lookup"><span data-stu-id="cced5-131">Is the maximum length, in bytes, of this column's data in the user file, not including the length of any length indicator or terminator.</span></span>  
  
 <span data-ttu-id="cced5-132">如果将*cbUserData*设置为 SQL_NULL_DATA，则指示数据文件列中的所有值均为，或应设置为 NULL。</span><span class="sxs-lookup"><span data-stu-id="cced5-132">Setting *cbUserData* to SQL_NULL_DATA indicates that all values in the data file column are, or should be set to NULL.</span></span>  
  
 <span data-ttu-id="cced5-133">将*cbUserData*设置为 SQL_VARLEN_DATA 指示系统应确定每列中的数据长度。</span><span class="sxs-lookup"><span data-stu-id="cced5-133">Setting *cbUserData* to SQL_VARLEN_DATA indicates that the system should determine the length of data in each column.</span></span> <span data-ttu-id="cced5-134">对于某些列，这可能意味着生成长度/空指示符，以便置于来自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的副本的数据前，或者意味着该指示符应位于复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的数据中。</span><span class="sxs-lookup"><span data-stu-id="cced5-134">For some columns, this could mean that a length/null indicator is generated to precede data on a copy from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or that the indicator is expected in data copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="cced5-135">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 字符和二进制数据类型， *cbUserData*可以是 SQL_VARLEN_DATA、SQL_NULL_DATA、0或某个正值。</span><span class="sxs-lookup"><span data-stu-id="cced5-135">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, *cbUserData* can be SQL_VARLEN_DATA, SQL_NULL_DATA, 0, or some positive value.</span></span> <span data-ttu-id="cced5-136">如果 SQL_VARLEN_DATA *cbUserData* ，则系统使用长度指示器（如果存在）或终止符序列来确定数据的长度。</span><span class="sxs-lookup"><span data-stu-id="cced5-136">If *cbUserData* is SQL_VARLEN_DATA, the system uses either the length indicator, if present, or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="cced5-137">如果长度指示符和终止符序列均提供，则大容量复制将采用导致数据复制量最少的方法。</span><span class="sxs-lookup"><span data-stu-id="cced5-137">If both a length indicator and a terminator sequence are supplied, bulk copy uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="cced5-138">如果*cbUserData* SQL_VARLEN_DATA，则数据类型为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 字符或二进制类型，并且不指定长度指示符和终止符序列，系统将返回一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="cced5-138">If *cbUserData* is SQL_VARLEN_DATA, the data type is an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="cced5-139">如果 cbUserData 为 0 或正值，则系统使用 cbUserData 作为最大数据长度\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cced5-139">If *cbUserData* is 0 or a positive value, the system uses *cbUserData* as the maximum data length.</span></span> <span data-ttu-id="cced5-140">但是，如果除了正的 cbUserData 以外，还提供了长度指示器或终止符序列，则系统使用导致数据复制量最少的方法来确定数据长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="cced5-140">However, if, in addition to a positive *cbUserData*, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="cced5-141">cbUserData 值表示数据的字节计数\*\*。</span><span class="sxs-lookup"><span data-stu-id="cced5-141">The *cbUserData* value represents the count of bytes of data.</span></span> <span data-ttu-id="cced5-142">如果字符数据由 Unicode 宽字符表示，则正的 cbUserData 参数值表示字符数乘以每个字符大小（字节）\*\*。</span><span class="sxs-lookup"><span data-stu-id="cced5-142">If character data is represented by Unicode wide characters, then a positive *cbUserData* parameter value represents the number of characters multiplied by the size, in bytes, of each character.</span></span>  
  
 <span data-ttu-id="cced5-143">*pUserDataTerm*</span><span class="sxs-lookup"><span data-stu-id="cced5-143">*pUserDataTerm*</span></span>  
 <span data-ttu-id="cced5-144">要用于该列的终止符序列。</span><span class="sxs-lookup"><span data-stu-id="cced5-144">Is the terminator sequence to be used for this column.</span></span> <span data-ttu-id="cced5-145">此参数主要用于字符数据类型，因为所有其他类型均属于固定长度，或者在二进制数据的情况下，要求长度指示器以精确记录提供的字节数目。</span><span class="sxs-lookup"><span data-stu-id="cced5-145">This parameter is useful mainly for character data types because all other types are of fixed length or, in the case of binary data, require an indicator of length to accurately record the number of bytes present.</span></span>  
  
 <span data-ttu-id="cced5-146">为了避免终止提取的数据，或者指示用户文件中的数据不终止，可将此参数设置为 NULL。</span><span class="sxs-lookup"><span data-stu-id="cced5-146">To avoid terminating extracted data, or to indicate that data in a user file is not terminated, set this parameter to NULL.</span></span>  
  
 <span data-ttu-id="cced5-147">如果使用多种方法指定用户文件列长度（例如终止符和长度指示器，或者终止符和最大列长度），则大容量复制选择导致数据复制量最少的方法。</span><span class="sxs-lookup"><span data-stu-id="cced5-147">If more than one means of specifying a user-file column length is used (such as a terminator and a length indicator, or a terminator and a maximum column length), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="cced5-148">大容量复制 API 根据需要执行 Unicode 到 MBCS 的字符转换。</span><span class="sxs-lookup"><span data-stu-id="cced5-148">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="cced5-149">执行此操作时请务必小心，以便确保终止符字节字符串和字节字符串的长度都正确设置。</span><span class="sxs-lookup"><span data-stu-id="cced5-149">Care must be taken to ensure that both the terminator byte string and the length of the byte string are set correctly.</span></span>  
  
 <span data-ttu-id="cced5-150">*cbUserDataTerm*</span><span class="sxs-lookup"><span data-stu-id="cced5-150">*cbUserDataTerm*</span></span>  
 <span data-ttu-id="cced5-151">要用于该列的终止符序列的长度（字节）。</span><span class="sxs-lookup"><span data-stu-id="cced5-151">Is the length, in bytes, of the terminator sequence to be used for this column.</span></span> <span data-ttu-id="cced5-152">如果终止符不存在或不希望其出现在数据中，请将该值设置为 0。</span><span class="sxs-lookup"><span data-stu-id="cced5-152">If no terminator is present or desired in the data, set this value to 0.</span></span>  
  
 <span data-ttu-id="cced5-153">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="cced5-153">*idxServerCol*</span></span>  
 <span data-ttu-id="cced5-154">数据库表中列的序号位置。</span><span class="sxs-lookup"><span data-stu-id="cced5-154">Is the ordinal position of the column in the database table.</span></span> <span data-ttu-id="cced5-155">第一个列编号为 1。</span><span class="sxs-lookup"><span data-stu-id="cced5-155">The first column number is 1.</span></span> <span data-ttu-id="cced5-156">列的序号位置由[SQLColumns](../native-client-odbc-api/sqlcolumns.md)报告。</span><span class="sxs-lookup"><span data-stu-id="cced5-156">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
 <span data-ttu-id="cced5-157">如果该值是 0，则大容量复制将忽略数据文件中的该列。</span><span class="sxs-lookup"><span data-stu-id="cced5-157">If this value is 0, bulk copy ignores the column in the data file.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="cced5-158">返回</span><span class="sxs-lookup"><span data-stu-id="cced5-158">Returns</span></span>  
 <span data-ttu-id="cced5-159">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="cced5-159">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cced5-160">备注</span><span class="sxs-lookup"><span data-stu-id="cced5-160">Remarks</span></span>  
 <span data-ttu-id="cced5-161">**Bcp_colfmt**函数允许您为大容量复制指定用户文件格式。</span><span class="sxs-lookup"><span data-stu-id="cced5-161">The **bcp_colfmt** function allows you to specify the user-file format for bulk copies.</span></span> <span data-ttu-id="cced5-162">对于大容量复制，格式包含以下部分：</span><span class="sxs-lookup"><span data-stu-id="cced5-162">For bulk copy, a format contains the following parts:</span></span>  
  
-   <span data-ttu-id="cced5-163">从用户文件列到数据库列的映射。</span><span class="sxs-lookup"><span data-stu-id="cced5-163">A mapping from user-file columns to database columns.</span></span>  
  
-   <span data-ttu-id="cced5-164">每个用户文件列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="cced5-164">The data type of each user-file column.</span></span>  
  
-   <span data-ttu-id="cced5-165">每个列的可选指示符的长度。</span><span class="sxs-lookup"><span data-stu-id="cced5-165">The length of the optional indicator for each column.</span></span>  
  
-   <span data-ttu-id="cced5-166">每个用户文件列的数据的最大长度。</span><span class="sxs-lookup"><span data-stu-id="cced5-166">The maximum length of data per user-file column.</span></span>  
  
-   <span data-ttu-id="cced5-167">每个列的可选终止字节序列。</span><span class="sxs-lookup"><span data-stu-id="cced5-167">The optional terminating byte sequence for each column.</span></span>  
  
-   <span data-ttu-id="cced5-168">可选终止字节序列的长度。</span><span class="sxs-lookup"><span data-stu-id="cced5-168">The length of the optional terminating byte sequence.</span></span>  
  
 <span data-ttu-id="cced5-169">对**bcp_colfmt**的每个调用都指定一个用户文件列的格式。</span><span class="sxs-lookup"><span data-stu-id="cced5-169">Each call to **bcp_colfmt** specifies the format for one user-file column.</span></span> <span data-ttu-id="cced5-170">例如，若要更改五行用户数据文件中三列的默认设置，请首先调用[bcp_columns](bcp-columns.md) \*\* (5) **，然后调用**bcp_colfmt\*\* 5 次，其中三个调用设置您的自定义格式。</span><span class="sxs-lookup"><span data-stu-id="cced5-170">For example, to change the default settings for three columns in a five-column user data file, first call [bcp_columns](bcp-columns.md)**(5)**, and then call **bcp_colfmt** five times, with three of those calls setting your custom format.</span></span> <span data-ttu-id="cced5-171">对于剩余的两次调用，将*eUserDataType*设置为0，并将*cbIndicator*、 *cbUserData*和*cbUserDataTerm*分别设置为0、SQL_VARLEN_DATA 和0。</span><span class="sxs-lookup"><span data-stu-id="cced5-171">For the remaining two calls, set *eUserDataType* to 0, and set *cbIndicator*, *cbUserData*, and *cbUserDataTerm* to 0, SQL_VARLEN_DATA, and 0 respectively.</span></span> <span data-ttu-id="cced5-172">此过程复制全部五列，其中的三列采用您的自定义格式，另两列采用默认格式。</span><span class="sxs-lookup"><span data-stu-id="cced5-172">This procedure copies all five columns, three with your customized format and two with the default format.</span></span>  
  
 <span data-ttu-id="cced5-173">对于*cbIndicator*，值8指示大值类型现在有效。</span><span class="sxs-lookup"><span data-stu-id="cced5-173">For *cbIndicator*, a value of 8 to indicate a large value type is now valid.</span></span> <span data-ttu-id="cced5-174">如果为其相应列是新的 max 类型的字段指定了前缀，则只能将它设置为 8。</span><span class="sxs-lookup"><span data-stu-id="cced5-174">If the prefix is specified for a field whose corresponding column is a new max type, it can only be set to 8.</span></span> <span data-ttu-id="cced5-175">有关详细信息，请参阅[bcp_bind](bcp-bind.md)。</span><span class="sxs-lookup"><span data-stu-id="cced5-175">For details, see [bcp_bind](bcp-bind.md).</span></span>  
  
 <span data-ttu-id="cced5-176">调用**bcp_colfmt**之前，必须先调用**bcp_columns**函数。</span><span class="sxs-lookup"><span data-stu-id="cced5-176">The **bcp_columns** function must be called before any calls to **bcp_colfmt**.</span></span>  
  
 <span data-ttu-id="cced5-177">您必须对用户文件中的每个列调用一次**bcp_colfmt** 。</span><span class="sxs-lookup"><span data-stu-id="cced5-177">You must call **bcp_colfmt** once for each column in the user file.</span></span>  
  
 <span data-ttu-id="cced5-178">对任何用户文件列多次调用**bcp_colfmt**会导致错误。</span><span class="sxs-lookup"><span data-stu-id="cced5-178">Calling **bcp_colfmt** more than once for any user-file column causes an error.</span></span>  
  
 <span data-ttu-id="cced5-179">不需要将用户文件中的所有数据都复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="cced5-179">You do not need to copy all data in a user file to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="cced5-180">若要跳过某一列，请指定该列的数据格式，并将*idxServerCol*参数设置为0。</span><span class="sxs-lookup"><span data-stu-id="cced5-180">To skip a column, specify the format of the data for the column, setting the *idxServerCol* parameter to 0.</span></span> <span data-ttu-id="cced5-181">如果您要跳过某一列，则必须指定其类型。</span><span class="sxs-lookup"><span data-stu-id="cced5-181">If you want to skip a column, you must specify its type.</span></span>  
  
 <span data-ttu-id="cced5-182">[Bcp_writefmt](bcp-writefmt.md)函数可用于保留格式规范。</span><span class="sxs-lookup"><span data-stu-id="cced5-182">The [bcp_writefmt](bcp-writefmt.md) function can be used to persist the format specification.</span></span>  
  
## <a name="bcp_colfmt-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="cced5-183">对增强的日期和时间功能的 bcp_colfmt 支持</span><span class="sxs-lookup"><span data-stu-id="cced5-183">bcp_colfmt Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="cced5-184">有关用于与*eUserDataType*参数一起用于日期/时间类型的信息，请参阅[OLE DB 和 ODBC&#41;的增强日期和时间类型的大容量复制更改 &#40;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="cced5-184">For information aboutt he types used with the *eUserDataType* parameter for date/time types, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="cced5-185">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="cced5-185">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cced5-186">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cced5-186">See Also</span></span>  
 [<span data-ttu-id="cced5-187">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="cced5-187">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
