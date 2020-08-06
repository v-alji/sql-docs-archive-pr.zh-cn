---
title: IBCPSession::BCPInit (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPInit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
author: rothja
ms.author: jroth
ms.openlocfilehash: 25a01c71811de9d47ce01714402460bb53d4c70e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688890"
---
# <a name="ibcpsessionbcpinit-ole-db"></a><span data-ttu-id="b4b40-102">IBCPSession::BCPInit (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="b4b40-102">IBCPSession::BCPInit (OLE DB)</span></span>
  <span data-ttu-id="b4b40-103">初始化大容量复制结构，执行某些错误检查，验证数据和格式化文件名是否正确，然后打开文件。</span><span class="sxs-lookup"><span data-stu-id="b4b40-103">Initializes the bulk copy structure, performs some error checking, verifies that the data and format file names are correct, and then opens them.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b40-104">语法</span><span class="sxs-lookup"><span data-stu-id="b4b40-104">Syntax</span></span>  
  
```  
  
HRESULT BCPInit(   
const wchar_t *pwszTable,  
const wchar_t *pwszDataFile,  
const wchar_t *pwszErrorFile,  
inteDirection);  
```  
  
## <a name="remarks"></a><span data-ttu-id="b4b40-105">备注</span><span class="sxs-lookup"><span data-stu-id="b4b40-105">Remarks</span></span>  
 <span data-ttu-id="b4b40-106">在调用任何其他大容量复制方法之前，应先调用 BCPInit 方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4b40-106">The **BCPInit** method should be called before any other bulk-copy method.</span></span> <span data-ttu-id="b4b40-107">BCPInit 方法将对工作站和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之间的大容量数据复制执行必要的初始化\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4b40-107">The **BCPInit** method performs the necessary initializations for a bulk copy of data between the workstation and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b4b40-108">BCPInit 方法将检查数据库源表或目标表的结构，而不检查数据文件\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4b40-108">The **BCPInit** method examines the structure of the database source or target table, not the data file.</span></span> <span data-ttu-id="b4b40-109">该方法将基于数据库表、视图或 SELECT 结果集中的每一列为数据文件指定数据格式值。</span><span class="sxs-lookup"><span data-stu-id="b4b40-109">It specifies data format values for the data file based on each column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="b4b40-110">此指定包括每一列的数据类型、数据中是否存在长度或 Null 指示符和终止符字节字符串以及固定长度的数据类型的宽度。</span><span class="sxs-lookup"><span data-stu-id="b4b40-110">This specification includes the data type of each column, the presence or absence of a length or null indicator and terminator byte strings in the data, and the width of fixed-length data types.</span></span> <span data-ttu-id="b4b40-111">BCPInit 方法按如下方式设置这些值\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="b4b40-111">The **BCPInit** method sets these values as follows:</span></span>  
  
-   <span data-ttu-id="b4b40-112">指定的数据类型是数据库表、视图或 SELECT 结果集中的列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="b4b40-112">The data type specified is the data type of the column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="b4b40-113">数据类型由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 头文件中指定的本机数据类型枚举 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (sqlncli.msi) 。</span><span class="sxs-lookup"><span data-stu-id="b4b40-113">The data type is enumerated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data types specified in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client header file (sqlncli.h).</span></span> <span data-ttu-id="b4b40-114">数据类型的值为 BCP_TYPE_XXX 模式。</span><span class="sxs-lookup"><span data-stu-id="b4b40-114">Their values are in the pattern of BCP_TYPE_XXX.</span></span> <span data-ttu-id="b4b40-115">数据将以其计算机形式表示。</span><span class="sxs-lookup"><span data-stu-id="b4b40-115">The data is represented in its computer form.</span></span> <span data-ttu-id="b4b40-116">也就是说，整数数据类型的列中的数据通过一个由四个字节组成的序列表示，该序列采用 big-endian 或 little-endian 格式，具体使用哪种格式取决于创建该数据文件的计算机。</span><span class="sxs-lookup"><span data-stu-id="b4b40-116">That is, data from a column of integer data type is represented by a four-byte sequence that is big-or little-endian based on the computer that created the data file.</span></span>  
  
-   <span data-ttu-id="b4b40-117">如果数据库数据类型的长度是固定的，则该数据文件中的数据长度也是固定的。</span><span class="sxs-lookup"><span data-stu-id="b4b40-117">If a database data type is fixed in length, the data file data is also fixed in length.</span></span> <span data-ttu-id="b4b40-118">处理数据的大容量复制方法（例如 [IBCPSession::BCPExec](ibcpsession-bcpexec-ole-db.md)）将对数据文件中的数据长度预期与数据库表、视图或 SELECT 列列表中指定的数据长度相同的数据行进行分析。</span><span class="sxs-lookup"><span data-stu-id="b4b40-118">Bulk-copy methods that process data (for example, [IBCPSession::BCPExec](ibcpsession-bcpexec-ole-db.md)) parse data rows expecting the length of the data in the data file to be identical to the length of the data specified in the database table, view, or SELECT column list.</span></span> <span data-ttu-id="b4b40-119">例如，对于定义为 `char(13)` 的数据库列的数据，该文件中每行数据必须由 13 个字符来表示。</span><span class="sxs-lookup"><span data-stu-id="b4b40-119">For example, data for a database column defined as `char(13)` must be represented by 13 characters for each row of data in the file.</span></span> <span data-ttu-id="b4b40-120">如果数据库列允许 Null 值，则可以使用 Null 指示符作为固定长度的数据的前缀。</span><span class="sxs-lookup"><span data-stu-id="b4b40-120">Fixed-length data can be prefixed with a null indicator if the database column allows null values.</span></span>  
  
-   <span data-ttu-id="b4b40-121">向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制数据时，数据文件必须包含数据库表中的每列数据。</span><span class="sxs-lookup"><span data-stu-id="b4b40-121">When copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the data file must have data for each column in the database table.</span></span> <span data-ttu-id="b4b40-122">从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制数据时，数据库表、视图或 SELECT 结果集中所有列的数据均将复制到数据文件。</span><span class="sxs-lookup"><span data-stu-id="b4b40-122">When copying data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data from all columns in the database table, view, or SELECT result set are copied to the data file.</span></span>  
  
-   <span data-ttu-id="b4b40-123">向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制数据时，数据文件中列的序号位置必须与数据库表中列的序号位置相同。</span><span class="sxs-lookup"><span data-stu-id="b4b40-123">When copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the ordinal position of a column in the data file must be identical to the ordinal position of the column in the database table.</span></span> <span data-ttu-id="b4b40-124">从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制数据时，**BCPExec** 方法将根据数据库表中列的序号位置放置数据。</span><span class="sxs-lookup"><span data-stu-id="b4b40-124">When copying data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **BCPExec** method places data based on the ordinal position of the column in the database table.</span></span>  
  
-   <span data-ttu-id="b4b40-125">如果数据库数据类型的长度是可变的（如 `varbinary(22)`），或者如果数据库列可以包含 Null 值，则在数据文件中使用长度/Null 指示符作为数据的前缀。</span><span class="sxs-lookup"><span data-stu-id="b4b40-125">If a database data type is variable in length (for example, `varbinary(22)`) or if a database column can contain null values, data in the data file is prefixed by a length/null indicator.</span></span> <span data-ttu-id="b4b40-126">指示符的宽度因数据类型和大容量复制的版本而异。</span><span class="sxs-lookup"><span data-stu-id="b4b40-126">The width of the indicator varies based on the data type and version of bulk copy.</span></span> <span data-ttu-id="b4b40-127">[IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) 方法选项 BCP_OPTION_FILEFMT 通过指示数据中的指示符宽度何时窄于预期宽度，在早期大容量复制数据文件和运行更高版本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的服务器之间提供兼容性。</span><span class="sxs-lookup"><span data-stu-id="b4b40-127">The [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) method option BCP_OPTION_FILEFMT provides compatibility between earlier bulk-copy data files and servers running later versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by indicating when the width of indicators in the data is narrower than expected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4b40-128">若要更改为数据文件指定的数据格式值，请使用 [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) 和 [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="b4b40-128">To change the data format values specified for a data file, use the [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) and [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) methods.</span></span>  
  
 <span data-ttu-id="b4b40-129">对于不包含索引的表，可通过设置数据库选项 select into/bulkcopy 优化对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的大容量复制\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4b40-129">Bulk copies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be optimized for tables that do not contain indexes by setting the database option **select into/bulkcopy**.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="b4b40-130">参数</span><span class="sxs-lookup"><span data-stu-id="b4b40-130">Arguments</span></span>  
 <span data-ttu-id="b4b40-131">pwszTable\*\*[in]</span><span class="sxs-lookup"><span data-stu-id="b4b40-131">*pwszTable*[in]</span></span>  
 <span data-ttu-id="b4b40-132">要复制进或复制出的数据库表的名称。</span><span class="sxs-lookup"><span data-stu-id="b4b40-132">The name of the database table to be copied into or out of.</span></span> <span data-ttu-id="b4b40-133">该名称可以包含数据库名称或所有者名称。</span><span class="sxs-lookup"><span data-stu-id="b4b40-133">The name can include the database name or the owner name.</span></span> <span data-ttu-id="b4b40-134">例如，"pubs.username.titles"、"pubs..titles"、"username.titles"。</span><span class="sxs-lookup"><span data-stu-id="b4b40-134">For example, "pubs.username.titles", "pubs..titles", "username.titles".</span></span>  
  
 <span data-ttu-id="b4b40-135">如果 eDirection 参数设置为 BCP_DIRECTION_OUT，则 pwszTable 参数可以为数据库视图的名称。</span><span class="sxs-lookup"><span data-stu-id="b4b40-135">If the eDirection argument is set to BCP_DIRECTION_OUT, the pwszTable argument can be the name of a database view.</span></span>  
  
 <span data-ttu-id="b4b40-136">如果在调用 BCPExec 方法前将 eDirection 参数设置为 BCP_DIRECTION_OUT 并使用 BCPControl 方法指定 SELECT 语句，则必须将 pwszTable 参数设置为 NULL\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4b40-136">If the eDirection argument is set to BCP_DIRECTION_OUT and a SELECT statement is specified using the **BCPControl** method before the **BCPExec** method is called, the *pwszTable* argument must be set to NULL.</span></span>  
  
 <span data-ttu-id="b4b40-137">pwszDataFile\*\*[in]</span><span class="sxs-lookup"><span data-stu-id="b4b40-137">*pwszDataFile*[in]</span></span>  
 <span data-ttu-id="b4b40-138">要复制进或复制出的用户文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b4b40-138">The name of the user file to be copied into or out of.</span></span>  
  
 <span data-ttu-id="b4b40-139">pwszErrorFile\*\*[in]</span><span class="sxs-lookup"><span data-stu-id="b4b40-139">*pwszErrorFile*[in]</span></span>  
 <span data-ttu-id="b4b40-140">错误文件的名称，该文件将用进度消息、错误消息以及无法从用户文件复制到表的任何行的副本进行填充。</span><span class="sxs-lookup"><span data-stu-id="b4b40-140">The name of the error file to be filled with progress messages, error messages, and copies of any rows that could not be copied from a user file to a table.</span></span> <span data-ttu-id="b4b40-141">如果 pwszErrorFile 参数设置为 NULL，则不使用任何错误文件。\*\*</span><span class="sxs-lookup"><span data-stu-id="b4b40-141">If the *pwszErrorFile* argument is set to NULL, no error file is used.</span></span>  
  
 <span data-ttu-id="b4b40-142">eDirection\*\*[in]</span><span class="sxs-lookup"><span data-stu-id="b4b40-142">*eDirection*[in]</span></span>  
 <span data-ttu-id="b4b40-143">复制操作的方向，BCP_DIRECTION_IN 或 BCP_DIRECTION _OUT。</span><span class="sxs-lookup"><span data-stu-id="b4b40-143">The direction of the copy operation, either BCP_DIRECTION_IN or BCP_DIRECTION _OUT.</span></span> <span data-ttu-id="b4b40-144">BCP_DIRECTION _IN 指示从用户文件向数据库表进行复制；BCP_DIRECTION _OUT 指示从数据库表向用户文件进行复制。</span><span class="sxs-lookup"><span data-stu-id="b4b40-144">BCP_DIRECTION _IN indicates a copy from a user file to a database table; BCP_DIRECTION _OUT indicates a copy from a database table to a user file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="b4b40-145">返回代码值</span><span class="sxs-lookup"><span data-stu-id="b4b40-145">Return Code Values</span></span>  
 <span data-ttu-id="b4b40-146">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4b40-146">S_OK</span></span>  
 <span data-ttu-id="b4b40-147">方法成功。</span><span class="sxs-lookup"><span data-stu-id="b4b40-147">The method succeeded.</span></span>  
  
 <span data-ttu-id="b4b40-148">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b4b40-148">E_FAIL</span></span>  
 <span data-ttu-id="b4b40-149">发生了特定于提供程序的错误 "。有关详细信息，请使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)接口。</span><span class="sxs-lookup"><span data-stu-id="b4b40-149">A provider specific error occurred' for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="b4b40-150">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b4b40-150">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="b4b40-151">内存不足错误。</span><span class="sxs-lookup"><span data-stu-id="b4b40-151">Out-of-memory error.</span></span>  
  
 <span data-ttu-id="b4b40-152">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b4b40-152">E_INVALIDARG</span></span>  
 <span data-ttu-id="b4b40-153">未正确指定一个或多个参数。</span><span class="sxs-lookup"><span data-stu-id="b4b40-153">One or more of the arguments was not correctly specified.</span></span> <span data-ttu-id="b4b40-154">例如，给定的文件名无效。</span><span class="sxs-lookup"><span data-stu-id="b4b40-154">For example, an invalid file name was given.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b40-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4b40-155">See Also</span></span>  
 <span data-ttu-id="b4b40-156">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="b4b40-156">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="b4b40-157">执行大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="b4b40-157">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
