---
title: IBCPSession::BCPColFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColFmt method
ms.assetid: 2852f4ba-f1c6-4c4c-86b2-b77e4abe70de
author: rothja
ms.author: jroth
ms.openlocfilehash: d60fa5dc93473f477926719cdcc05d13e72d8fd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692889"
---
# <a name="ibcpsessionbcpcolfmt-ole-db"></a><span data-ttu-id="5685f-102">IBCPSession::BCPColFmt (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="5685f-102">IBCPSession::BCPColFmt (OLE DB)</span></span>
  <span data-ttu-id="5685f-103">在程序变量与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列之间创建绑定。</span><span class="sxs-lookup"><span data-stu-id="5685f-103">Creates a binding between program variables and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5685f-104">语法</span><span class="sxs-lookup"><span data-stu-id="5685f-104">Syntax</span></span>  
  
```  
  
HRESULT BCPColFmt(   
DBORDINALidxUserDataCol,  
inteUserDataType,  
intcbIndicator,  
intcbUserData,  
BYTE *pbUserDataTerm,  
intcbUserDataTerm,  
DBORDINALidxServerCol);  
```  
  
## <a name="remarks"></a><span data-ttu-id="5685f-105">备注</span><span class="sxs-lookup"><span data-stu-id="5685f-105">Remarks</span></span>  
 <span data-ttu-id="5685f-106">BCPColFmt 方法用于在 BCP 数据文件字段和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列之间创建绑定\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5685f-106">The **BCPColFmt** method is used to create a binding between BCP data file fields and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span> <span data-ttu-id="5685f-107">它将列的长度、类型、终止符和前缀长度视为参数处理，并为各个字段设置所有这些属性。</span><span class="sxs-lookup"><span data-stu-id="5685f-107">It takes in the length, type, terminator, and prefix length of a column as parameters and sets each of these properties for individual fields.</span></span>  
  
 <span data-ttu-id="5685f-108">如果用户选择交互模式，则调用该方法两次；一次按照默认值（与服务器列的类型相对应）设置列格式，另一次按照在交互模式期间选择的客户端的所选列类型为每个列设置格式。</span><span class="sxs-lookup"><span data-stu-id="5685f-108">If the user chooses interactive mode, this method is called twice; once to set the column format according to the default values (which are according to the type of the server column), and once to set the format according to the column type of the choice of the client chosen during interactive mode, for each column.</span></span>  
  
 <span data-ttu-id="5685f-109">在非交互模式中，对每列只调用它一次，以便将每个列的类型设置为字符或本机类型，并设置列和行终止符。</span><span class="sxs-lookup"><span data-stu-id="5685f-109">In non-interactive modes, it is called only once per column to set the type of each column to character or native type, and to set the column and row terminators.</span></span>  
  
 <span data-ttu-id="5685f-110">使用 BCPColFmt 方法可以为大容量复制指定用户文件格式\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5685f-110">The **BCPColFmt** method allows you to specify the user-file format for bulk copies.</span></span> <span data-ttu-id="5685f-111">对于大容量复制，格式包含以下部分：</span><span class="sxs-lookup"><span data-stu-id="5685f-111">For bulk copy, a format contains the following parts:</span></span>  
  
-   <span data-ttu-id="5685f-112">从用户文件字段到数据库列的映射。</span><span class="sxs-lookup"><span data-stu-id="5685f-112">A mapping from user-file fields to database columns.</span></span>  
  
-   <span data-ttu-id="5685f-113">每个用户文件字段的数据类型。</span><span class="sxs-lookup"><span data-stu-id="5685f-113">The data type of each user-file field.</span></span>  
  
-   <span data-ttu-id="5685f-114">每个字段的可选指示器的长度。</span><span class="sxs-lookup"><span data-stu-id="5685f-114">The length of the optional indicator for each field.</span></span>  
  
-   <span data-ttu-id="5685f-115">每个用户文件字段中数据的最大长度。</span><span class="sxs-lookup"><span data-stu-id="5685f-115">The maximum length of data per user-file field.</span></span>  
  
-   <span data-ttu-id="5685f-116">每个字段的可选终止字节序列。</span><span class="sxs-lookup"><span data-stu-id="5685f-116">The optional terminating byte sequence for each field.</span></span>  
  
-   <span data-ttu-id="5685f-117">可选终止字节序列的长度。</span><span class="sxs-lookup"><span data-stu-id="5685f-117">The length of the optional terminating byte sequence.</span></span>  
  
 <span data-ttu-id="5685f-118">对 BCPColFmt 的每次调用将指定一个用户文件字段的格式\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5685f-118">Each call to **BCPColFmt** specifies the format for one user-file field.</span></span> <span data-ttu-id="5685f-119">例如，要在具有 5 个字段的用户数据文件中更改 3 个字段的默认设置，请先调用 `BCPColumns(5)`，再调用 BCPColFmt 五次，其中三次调用设置自定义格式\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5685f-119">For example, to change the default settings for three fields in a five-field user data file, first call `BCPColumns(5)`, and then call **BCPColFmt** five times, with three of those calls setting your custom format.</span></span> <span data-ttu-id="5685f-120">对于剩余的两次调用，请将 eUserDataType\*\* 设置为 BCP_TYPE_DEFAULT，并将 cbIndicator**、cbUserData** 和 cbUserDataTerm\*\* 分别设置为 0、BCP_VARIABLE_LENGTH 和 0。</span><span class="sxs-lookup"><span data-stu-id="5685f-120">For the remaining two calls, set *eUserDataType* to BCP_TYPE_DEFAULT, and set *cbIndicator*, *cbUserData*, and *cbUserDataTerm* to 0, BCP_VARIABLE_LENGTH, and 0 respectively.</span></span> <span data-ttu-id="5685f-121">此过程复制全部五列，其中的三列采用您的自定义格式，另两列采用默认格式。</span><span class="sxs-lookup"><span data-stu-id="5685f-121">This procedure copies all five columns, three with your customized format and two with the default format.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5685f-122">在对 BCPColFmt 进行任何调用之前，必须先调用 [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) 方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5685f-122">The [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) method must be called before any calls to **BCPColFmt**.</span></span> <span data-ttu-id="5685f-123">必须对用户文件中的每个列调用一次 BCPColFmt\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5685f-123">You must call **BCPColFmt** once for each column in the user file.</span></span> <span data-ttu-id="5685f-124">对任何用户文件列多次调用 BCPColFmt 将导致错误\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5685f-124">Calling **BCPColFmt** more than once for any user-file column causes an error.</span></span>  
  
 <span data-ttu-id="5685f-125">不必将用户文件中的所有数据复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="5685f-125">You do not have to copy all of the data in a user file to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="5685f-126">若要跳过某一列，请指定该列的数据格式，并且将 idxServerCol 参数设置为 0。</span><span class="sxs-lookup"><span data-stu-id="5685f-126">To skip a column, specify the format of the data for the column setting the idxServerCol parameter to 0.</span></span> <span data-ttu-id="5685f-127">若要跳过某一字段，仍然需要所有信息才能让该方法正常工作。</span><span class="sxs-lookup"><span data-stu-id="5685f-127">In order to skip a field, you still need all the information for the method to work correctly.</span></span>  
  
 <span data-ttu-id="5685f-128">**注意**[IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) 函数可以用于持久化通过 BCPColFmt 提供的格式规范\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5685f-128">**Note** The [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) function can be used to persist the format specification provided through **BCPColFmt**.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="5685f-129">参数</span><span class="sxs-lookup"><span data-stu-id="5685f-129">Arguments</span></span>  
 <span data-ttu-id="5685f-130">idxUserDataCol[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="5685f-130">*idxUserDataCol*[in]</span></span>  
 <span data-ttu-id="5685f-131">用户的数据文件中字段的索引。</span><span class="sxs-lookup"><span data-stu-id="5685f-131">Index of field in the user's data file.</span></span>  
  
 <span data-ttu-id="5685f-132">eUserDataType[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="5685f-132">*eUserDataType*[in]</span></span>  
 <span data-ttu-id="5685f-133">用户的数据文件中字段的数据类型。</span><span class="sxs-lookup"><span data-stu-id="5685f-133">The data type of field in the user's data file.</span></span> <span data-ttu-id="5685f-134">可用的数据类型在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 头文件中列出 (带有 BCP_TYPE_XXX 格式的 sqlncli.msi) ，例如 BCP_TYPE_SQLINT4。</span><span class="sxs-lookup"><span data-stu-id="5685f-134">The data types available are listed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client header file (sqlncli.h) with BCP_TYPE_XXX format, for example, BCP_TYPE_SQLINT4.</span></span> <span data-ttu-id="5685f-135">如果指定 BCP_TYPE_DEFAULT 值，则访问接口将尝试使用与表或视图列相同的类型。</span><span class="sxs-lookup"><span data-stu-id="5685f-135">If the BCP_TYPE_DEFAULT value is specified, the provider tries to use the same type as the table or view column type.</span></span> <span data-ttu-id="5685f-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]当 `eUserDataType` 参数为 BCP_TYPE_SQLDECIMAL 或 BCP_TYPE_SQLNUMERIC 时，用于从和到文件的大容量复制操作：</span><span class="sxs-lookup"><span data-stu-id="5685f-136">For bulk copy operations out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and into a file when the `eUserDataType` argument is BCP_TYPE_SQLDECIMAL or BCP_TYPE_SQLNUMERIC:</span></span>  
  
-   <span data-ttu-id="5685f-137">如果源列的数据类型不是 decimal 或 numeric，则使用默认的精度和小数位数。</span><span class="sxs-lookup"><span data-stu-id="5685f-137">If the source column is not decimal or numeric, the default precision and scale are used.</span></span>  
  
-   <span data-ttu-id="5685f-138">如果源列的数据类型是 decimal 或 numeric，则使用源列的精度和小数位数。</span><span class="sxs-lookup"><span data-stu-id="5685f-138">If the source column is decimal or numeric, the precision and scale of the source column are used.</span></span>  
  
 <span data-ttu-id="5685f-139">cbIndicator[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="5685f-139">*cbIndicator*[in]</span></span>  
 <span data-ttu-id="5685f-140">字段的前缀长度。</span><span class="sxs-lookup"><span data-stu-id="5685f-140">Prefix length for the field.</span></span> <span data-ttu-id="5685f-141">默认是 BCP_PREFIX_DEFAULT。</span><span class="sxs-lookup"><span data-stu-id="5685f-141">The default is BCP_PREFIX_DEFAULT.</span></span> <span data-ttu-id="5685f-142">前缀的有效长度是 0、1、2、4 和 8。</span><span class="sxs-lookup"><span data-stu-id="5685f-142">The valid lengths for the prefix are 0, 1, 2, 4 and 8.</span></span> <span data-ttu-id="5685f-143">大多数情况下，使用等于 8 的前缀大小指示字段已块区化。</span><span class="sxs-lookup"><span data-stu-id="5685f-143">A prefix size of 8 is most commonly used to indicate that the field is chunked.</span></span> <span data-ttu-id="5685f-144">这用于有效地大容量复制大型值类型列。</span><span class="sxs-lookup"><span data-stu-id="5685f-144">This is used for efficiently bulk copying large value type columns.</span></span>  
  
 <span data-ttu-id="5685f-145">cbUserData[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="5685f-145">*cbUserData*[in]</span></span>  
 <span data-ttu-id="5685f-146">用户文件中该字段的数据的最大长度（单位为字节），不包括任何长度指示器或终止符的长度。</span><span class="sxs-lookup"><span data-stu-id="5685f-146">The maximum length, in bytes, of this field's data in the user file, not including the length of any length indicator or terminator.</span></span>  
  
 <span data-ttu-id="5685f-147">`cbUserData`如果设置为 BCP_LENGTH_NULL，则指示数据文件字段中的所有值均为，或应设置为 NULL。</span><span class="sxs-lookup"><span data-stu-id="5685f-147">Setting `cbUserData` to BCP_LENGTH_NULL indicates that all values in the data file fields are, or should be set to NULL.</span></span> <span data-ttu-id="5685f-148">设置 `cbUserData` 为 BCP_LENGTH_VARIABLE 指示系统应确定每个字段的数据长度。</span><span class="sxs-lookup"><span data-stu-id="5685f-148">Setting `cbUserData` to BCP_LENGTH_VARIABLE indicates that the system should determine the length of data for each field.</span></span> <span data-ttu-id="5685f-149">对于某些字段，这可能意味着将生成长度/Null 指示器，并将该指示器放在从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制的数据的前面，或者应当将该指示器放在复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的数据中。</span><span class="sxs-lookup"><span data-stu-id="5685f-149">For some fields, this could mean that a length/null indicator is generated to precede data on a copy from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or that the indicator is expected in data copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5685f-150">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 字符和二进制数据类型， `cbUserData` 可以是 BCP_LENGTH_VARIABLE、BCP_LENGTH_NULL、0或某个正值。</span><span class="sxs-lookup"><span data-stu-id="5685f-150">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, `cbUserData` can be BCP_LENGTH_VARIABLE, BCP_LENGTH_NULL, 0, or some positive value.</span></span> <span data-ttu-id="5685f-151">如果 `cbUserData` BCP_LENGTH_VARIABLE，则系统使用长度指示器（如果存在）或终止符序列来确定数据的长度。</span><span class="sxs-lookup"><span data-stu-id="5685f-151">If `cbUserData` is BCP_LENGTH_VARIABLE, the system uses either the length indicator, if present, or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="5685f-152">如果长度指示符和终止符序列均提供，则大容量复制将采用导致数据复制量最少的方法。</span><span class="sxs-lookup"><span data-stu-id="5685f-152">If both a length indicator and a terminator sequence are supplied, bulk copy uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="5685f-153">如果 `cbUserData` BCP_LENGTH_VARIABLE，则数据类型为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 字符或二进制类型，如果不指定长度指示符和终止符序列，系统将返回错误消息。</span><span class="sxs-lookup"><span data-stu-id="5685f-153">If `cbUserData` is BCP_LENGTH_VARIABLE, the data type is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and if neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="5685f-154">如果 `cbUserData` 为0或正值，则系统使用 `cbUserData` 作为最大数据长度。</span><span class="sxs-lookup"><span data-stu-id="5685f-154">If `cbUserData` is 0 or a positive value, the system uses `cbUserData` as the maximum data length.</span></span> <span data-ttu-id="5685f-155">但是，如果在 `cbUserData` 提供了一个正、长度指示器或终止符序列的情况下，系统将通过使用导致数据复制量最少的方法来确定数据长度。</span><span class="sxs-lookup"><span data-stu-id="5685f-155">However, if, in addition to a positive `cbUserData`, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="5685f-156">`cbUserData`值表示数据的字节计数。</span><span class="sxs-lookup"><span data-stu-id="5685f-156">The `cbUserData` value represents the count of bytes of data.</span></span> <span data-ttu-id="5685f-157">如果字符数据由 Unicode 宽字符表示，则正值 `cbUserData` 参数值表示字符数乘以每个字符的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="5685f-157">If character data is represented by Unicode wide characters, then a positive `cbUserData` parameter value represents the number of characters multiplied by the size, in bytes, of each character.</span></span>  
  
 <span data-ttu-id="5685f-158">pbUserDataTerm[size_is][in]\*\*</span><span class="sxs-lookup"><span data-stu-id="5685f-158">*pbUserDataTerm*[size_is][in]</span></span>  
 <span data-ttu-id="5685f-159">用于字段的终止符序列。</span><span class="sxs-lookup"><span data-stu-id="5685f-159">The terminator sequence to be used for the field.</span></span> <span data-ttu-id="5685f-160">此参数主要用于字符数据类型，因为所有其他类型均属于固定长度，或者在二进制数据的情况下，要求长度指示器以精确记录提供的字节数目。</span><span class="sxs-lookup"><span data-stu-id="5685f-160">This parameter is useful mainly for character data types because all other types are of fixed length or, in the case of binary data, require an indicator of length to accurately record the number of bytes present.</span></span>  
  
 <span data-ttu-id="5685f-161">为了避免终止提取的数据，或者指示用户文件中的数据不终止，可将此参数设置为 NULL。</span><span class="sxs-lookup"><span data-stu-id="5685f-161">To avoid terminating extracted data, or to indicate that data in a user file is not terminated, set this parameter to NULL.</span></span>  
  
 <span data-ttu-id="5685f-162">如果使用多种方法指定用户文件列长度（例如终止符和长度指示器，或者终止符和最大列长度），则大容量复制选择导致数据复制量最少的方法。</span><span class="sxs-lookup"><span data-stu-id="5685f-162">If more than one means of specifying a user-file column length is used (such as a terminator and a length indicator, or a terminator and a maximum column length), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="5685f-163">大容量复制 API 根据需要执行 Unicode 到 MBCS 的字符转换。</span><span class="sxs-lookup"><span data-stu-id="5685f-163">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="5685f-164">执行此操作时请务必小心，以便确保终止符字节字符串和字节字符串的长度都正确设置。</span><span class="sxs-lookup"><span data-stu-id="5685f-164">Care must be taken to ensure that both the terminator byte string and the length of the byte string are set correctly.</span></span>  
  
 <span data-ttu-id="5685f-165">cbUserDataTerm[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="5685f-165">*cbUserDataTerm*[in]</span></span>  
 <span data-ttu-id="5685f-166">要用于列的终止符序列的长度（单位为字节）。</span><span class="sxs-lookup"><span data-stu-id="5685f-166">The length, in bytes, of the terminator sequence to be used for the column.</span></span> <span data-ttu-id="5685f-167">如果终止符不存在或不希望其出现在数据中，请将该值设置为 0。</span><span class="sxs-lookup"><span data-stu-id="5685f-167">If no terminator is present or desired in the data, set this value to 0.</span></span>  
  
 <span data-ttu-id="5685f-168">idxServerCol[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="5685f-168">*idxServerCol*[in]</span></span>  
 <span data-ttu-id="5685f-169">数据库表中列的序号位置。</span><span class="sxs-lookup"><span data-stu-id="5685f-169">The ordinal position of the column in the database table.</span></span> <span data-ttu-id="5685f-170">第一个列编号为 1。</span><span class="sxs-lookup"><span data-stu-id="5685f-170">The first column number is 1.</span></span> <span data-ttu-id="5685f-171">列的序号位置由 IColumnsInfo::GetColumnInfo 或类似方法报告\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5685f-171">The ordinal position of a column is reported by **IColumnsInfo::GetColumnInfo** or similar methods.</span></span> <span data-ttu-id="5685f-172">如果该值是 0，则大容量复制将忽略数据文件中的相应字段。</span><span class="sxs-lookup"><span data-stu-id="5685f-172">If this value is 0, bulk copy ignores the field in the data file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="5685f-173">返回代码值</span><span class="sxs-lookup"><span data-stu-id="5685f-173">Return Code Values</span></span>  
 <span data-ttu-id="5685f-174">S_OK</span><span class="sxs-lookup"><span data-stu-id="5685f-174">S_OK</span></span>  
 <span data-ttu-id="5685f-175">方法成功。</span><span class="sxs-lookup"><span data-stu-id="5685f-175">The method succeeded.</span></span>  
  
 <span data-ttu-id="5685f-176">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5685f-176">E_FAIL</span></span>  
 <span data-ttu-id="5685f-177">出现特定于提供程序的错误，有关详细信息，请使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)接口。</span><span class="sxs-lookup"><span data-stu-id="5685f-177">A provider specific error occurred, for detailed information use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="5685f-178">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="5685f-178">E_UNEXPECTED</span></span>  
 <span data-ttu-id="5685f-179">意外调用了该方法。</span><span class="sxs-lookup"><span data-stu-id="5685f-179">The call to the method was unexpected.</span></span> <span data-ttu-id="5685f-180">例如，在调用该方法之前，未调用 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="5685f-180">For example, the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method was not called before calling this method.</span></span>  
  
 <span data-ttu-id="5685f-181">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5685f-181">E_INVALIDARG</span></span>  
 <span data-ttu-id="5685f-182">参数无效。</span><span class="sxs-lookup"><span data-stu-id="5685f-182">The argument was invalid.</span></span>  
  
 <span data-ttu-id="5685f-183">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5685f-183">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="5685f-184">内存不足错误。</span><span class="sxs-lookup"><span data-stu-id="5685f-184">Out of memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5685f-185">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5685f-185">See Also</span></span>  
 <span data-ttu-id="5685f-186">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="5685f-186">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="5685f-187">执行大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="5685f-187">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
