---
title: 表值参数描述符字段 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor fields
ms.assetid: 4e009eff-c156-4d63-abcf-082ddd304de2
author: rothja
ms.author: jroth
ms.openlocfilehash: 5365229aed0bc46315a7e6db5448bee6963b23fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688893"
---
# <a name="table-valued-parameter-descriptor-fields"></a><span data-ttu-id="22e8e-102">表值参数描述符字段</span><span class="sxs-lookup"><span data-stu-id="22e8e-102">Table-Valued Parameter Descriptor Fields</span></span>
  <span data-ttu-id="22e8e-103">作为对表值参数的支持，ODBC 应用程序参数描述符 (APD) 和实现参数描述符 (IPD) 中新增了特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的字段。</span><span class="sxs-lookup"><span data-stu-id="22e8e-103">Support for table-valued parameters includes new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific fields in ODBC application parameter descriptors (APDs) and implementation parameter descriptors (IPDs).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22e8e-104">备注</span><span class="sxs-lookup"><span data-stu-id="22e8e-104">Remarks</span></span>  
  
|<span data-ttu-id="22e8e-105">名称</span><span class="sxs-lookup"><span data-stu-id="22e8e-105">Name</span></span>|<span data-ttu-id="22e8e-106">位置</span><span class="sxs-lookup"><span data-stu-id="22e8e-106">Location</span></span>|<span data-ttu-id="22e8e-107">类型</span><span class="sxs-lookup"><span data-stu-id="22e8e-107">Type</span></span>|<span data-ttu-id="22e8e-108">说明</span><span class="sxs-lookup"><span data-stu-id="22e8e-108">Description</span></span>|  
|----------|--------------|----------|-----------------|  
|<span data-ttu-id="22e8e-109">SQL_CA_SS_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="22e8e-109">SQL_CA_SS_TYPE_NAME</span></span>|<span data-ttu-id="22e8e-110">IPD</span><span class="sxs-lookup"><span data-stu-id="22e8e-110">IPD</span></span>|<span data-ttu-id="22e8e-111">SQLTCHAR\*</span><span class="sxs-lookup"><span data-stu-id="22e8e-111">SQLTCHAR\*</span></span>|<span data-ttu-id="22e8e-112">表值参数的服务器类型名称。</span><span class="sxs-lookup"><span data-stu-id="22e8e-112">The server type name of the table-valued parameter.</span></span><br /><br /> <span data-ttu-id="22e8e-113">如果在对 SQLBindParameter 的调用上指定了表值参数类型名称，则它必须始终指定为 Unicode 值，即使是在作为 ANSI 应用程序生成的应用程序中。</span><span class="sxs-lookup"><span data-stu-id="22e8e-113">When a table-valued parameter type name is specified on a call to SQLBindParameter, it must always be specified as a Unicode value, even in applications that are built as ANSI applications.</span></span> <span data-ttu-id="22e8e-114">用于参数*StrLen_or_IndPtr*的值应为 SQL_NTS 或名称的字符串长度乘以 SIZEOF (WCHAR) 。</span><span class="sxs-lookup"><span data-stu-id="22e8e-114">The value used for the parameter *StrLen_or_IndPtr* should be either SQL_NTS or the string length of the name multiplied by sizeof(WCHAR).</span></span><br /><br /> <span data-ttu-id="22e8e-115">当通过 SQLSetDescField 指定表值参数类型名称时，可以使用符合应用程序生成方式的文本指定它。</span><span class="sxs-lookup"><span data-stu-id="22e8e-115">When a table-valued parameter type name is specified via SQLSetDescField, it can be specified by using a literal that conforms to the way the application is built.</span></span> <span data-ttu-id="22e8e-116">ODBC 驱动程序管理器将执行任何所需的 Unicode 转换。</span><span class="sxs-lookup"><span data-stu-id="22e8e-116">The ODBC Driver Manager will perform any required Unicode conversion.</span></span>|  
|<span data-ttu-id="22e8e-117">SQL_CA_SS_TYPE_CATALOG_NAME（只读）</span><span class="sxs-lookup"><span data-stu-id="22e8e-117">SQL_CA_SS_TYPE_CATALOG_NAME (read only)</span></span>|<span data-ttu-id="22e8e-118">IPD</span><span class="sxs-lookup"><span data-stu-id="22e8e-118">IPD</span></span>|<span data-ttu-id="22e8e-119">SQLTCHAR\*</span><span class="sxs-lookup"><span data-stu-id="22e8e-119">SQLTCHAR\*</span></span>|<span data-ttu-id="22e8e-120">定义该类型的目录。</span><span class="sxs-lookup"><span data-stu-id="22e8e-120">The catalog where the type is defined.</span></span>|  
|<span data-ttu-id="22e8e-121">SQL_CA_SS_TYPE_SCHEMA_NAME</span><span class="sxs-lookup"><span data-stu-id="22e8e-121">SQL_CA_SS_TYPE_SCHEMA_NAME</span></span>|<span data-ttu-id="22e8e-122">IPD</span><span class="sxs-lookup"><span data-stu-id="22e8e-122">IPD</span></span>|<span data-ttu-id="22e8e-123">SQLTCHAR\*</span><span class="sxs-lookup"><span data-stu-id="22e8e-123">SQLTCHAR\*</span></span>|<span data-ttu-id="22e8e-124">定义该类型的架构。</span><span class="sxs-lookup"><span data-stu-id="22e8e-124">The schema where the type is defined.</span></span>|  
  
 <span data-ttu-id="22e8e-125">应用程序不得为表值参数设置 SQL_CA_SS_TYPE_CATALOG_NAME。</span><span class="sxs-lookup"><span data-stu-id="22e8e-125">Applications must not set SQL_CA_SS_TYPE_CATALOG_NAME for table-valued parameters.</span></span> <span data-ttu-id="22e8e-126">这样做将返回 SQL_ERROR，并记录包含 SQLSTATE = HY091 和消息“描述符字段标识符无效”的诊断记录。</span><span class="sxs-lookup"><span data-stu-id="22e8e-126">Doing so will return a SQL_ERROR and log a diagnostic record with SQLSTATE = HY091 and the message "Invalid descriptor field identifier".</span></span>  
  
 <span data-ttu-id="22e8e-127">如果将参数焦点设置为表值参数，则以下语句属性和描述符标头字段将应用于表值参数：</span><span class="sxs-lookup"><span data-stu-id="22e8e-127">The following statement attributes and descriptor header fields apply to table-valued parameters when the parameter focus is set to a table-valued parameter:</span></span>  
  
|<span data-ttu-id="22e8e-128">名称</span><span class="sxs-lookup"><span data-stu-id="22e8e-128">Name</span></span>|<span data-ttu-id="22e8e-129">位置</span><span class="sxs-lookup"><span data-stu-id="22e8e-129">Location</span></span>|<span data-ttu-id="22e8e-130">类型</span><span class="sxs-lookup"><span data-stu-id="22e8e-130">Type</span></span>|<span data-ttu-id="22e8e-131">说明</span><span class="sxs-lookup"><span data-stu-id="22e8e-131">Description</span></span>|  
|----------|--------------|----------|-----------------|  
|<span data-ttu-id="22e8e-132">SQL_ATTR_PARAMSET_SIZE</span><span class="sxs-lookup"><span data-stu-id="22e8e-132">SQL_ATTR_PARAMSET_SIZE</span></span><br /><br /> <span data-ttu-id="22e8e-133">（这等同于 APD 中的 SQL_DESC_ARRAY_SIZE。）</span><span class="sxs-lookup"><span data-stu-id="22e8e-133">(This is equivalent to SQL_DESC_ARRAY_SIZE in the APD.)</span></span>|<span data-ttu-id="22e8e-134">APD</span><span class="sxs-lookup"><span data-stu-id="22e8e-134">APD</span></span>|<span data-ttu-id="22e8e-135">SQLUINTEGER</span><span class="sxs-lookup"><span data-stu-id="22e8e-135">SQLUINTEGER</span></span>|<span data-ttu-id="22e8e-136">用于表值参数的缓冲区数组的数组大小。</span><span class="sxs-lookup"><span data-stu-id="22e8e-136">The array size of the buffer arrays for a table-valued parameter.</span></span> <span data-ttu-id="22e8e-137">这是缓冲区将容纳的最大行数或缓冲区的行数大小；表值参数值本身所具有的行数可能大于或小于缓冲区可以容纳的行数。</span><span class="sxs-lookup"><span data-stu-id="22e8e-137">This is the maximum number of rows the buffers will accommodate or the size of the buffers in rows; the table-valued parameter value itself might have more or fewer rows than the buffers can hold.</span></span> <span data-ttu-id="22e8e-138">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="22e8e-138">Default is 1.</span></span> <span data-ttu-id="22e8e-139">**注意：** 如果 SQL_SOPT_SS_PARAM_FOCUS 设置为其默认值0，则 SQL_ATTR_PARAMSET_SIZE 指的是语句，并指定参数集的数目。</span><span class="sxs-lookup"><span data-stu-id="22e8e-139">**Note:**  If SQL_SOPT_SS_PARAM_FOCUS is set to its default value of 0, SQL_ATTR_PARAMSET_SIZE refers to the statement and specifies the number of parameter sets.</span></span> <span data-ttu-id="22e8e-140">如果将 SQL_SOPT_SS_PARAM_FOCUS 设置为表值参数的序号，则它引用该表值参数，并为该表值参数指定每个参数集具有的行数。</span><span class="sxs-lookup"><span data-stu-id="22e8e-140">If SQL_SOPT_SS_PARAM_FOCUS is set to the ordinal of a table-valued parameter, it refers to the table-valued parameter and specifies the number of rows per parameter set for the table-valued parameter.</span></span>|  
|<span data-ttu-id="22e8e-141">SQL_ATTR_PARAM _BIND_TYPE</span><span class="sxs-lookup"><span data-stu-id="22e8e-141">SQL_ATTR_PARAM _BIND_TYPE</span></span>|<span data-ttu-id="22e8e-142">APD</span><span class="sxs-lookup"><span data-stu-id="22e8e-142">APD</span></span>|<span data-ttu-id="22e8e-143">SQLINTEGER</span><span class="sxs-lookup"><span data-stu-id="22e8e-143">SQLINTEGER</span></span>|<span data-ttu-id="22e8e-144">默认值是 SQL_PARAM_BIND_BY_COLUMN。</span><span class="sxs-lookup"><span data-stu-id="22e8e-144">The default is SQL_PARAM_BIND_BY_COLUMN.</span></span><br /><br /> <span data-ttu-id="22e8e-145">若要选择按行绑定，则该字段将设置为将要绑定到一组表值参数行的结构或缓冲区实例的长度。</span><span class="sxs-lookup"><span data-stu-id="22e8e-145">To select row-wise binding, this field is set to the length of the structure or an instance of a buffer that will be bound to a set of table-valued parameter rows.</span></span> <span data-ttu-id="22e8e-146">此长度必须包括所有绑定列的空间以及结构或缓冲区的任何填充大小。</span><span class="sxs-lookup"><span data-stu-id="22e8e-146">This length must include space for all of the bound columns and any padding of the structure or buffer.</span></span> <span data-ttu-id="22e8e-147">这将确保当绑定列的地址按指定长度递增时，结果将指向下一行中相同列的开头。</span><span class="sxs-lookup"><span data-stu-id="22e8e-147">This ensures that when the address of a bound column is incremented with the specified length, the result will point to the beginning of the same column in the next row.</span></span> <span data-ttu-id="22e8e-148">在 ANSI C 中使用 `sizeof` 运算符时，将保证该行为。</span><span class="sxs-lookup"><span data-stu-id="22e8e-148">When using the `sizeof` operator in ANSI C, this behavior is guaranteed.</span></span>|  
|<span data-ttu-id="22e8e-149">SQL_ATTR_PARAM_BIND_OFFSET_PTR</span><span class="sxs-lookup"><span data-stu-id="22e8e-149">SQL_ATTR_PARAM_BIND_OFFSET_PTR</span></span>|<span data-ttu-id="22e8e-150">APD</span><span class="sxs-lookup"><span data-stu-id="22e8e-150">APD</span></span>|<span data-ttu-id="22e8e-151">SQLINTEGER\*</span><span class="sxs-lookup"><span data-stu-id="22e8e-151">SQLINTEGER\*</span></span>|<span data-ttu-id="22e8e-152">默认为 Null 指针。</span><span class="sxs-lookup"><span data-stu-id="22e8e-152">The default is a null pointer.</span></span><br /><br /> <span data-ttu-id="22e8e-153">如果该字段为非 Null，则驱动程序取消对该指针的引用，并将取消引用的值添加到描述符记录（SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR 和 SQL_DESC_OCTET_LENGTH_PTR）中每个延迟的字段，然后使用新指针值访问数据值。</span><span class="sxs-lookup"><span data-stu-id="22e8e-153">If this field is non-null, the driver dereferences the pointer, adds the dereferenced value to each of the deferred fields in the descriptor record (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR), and uses the new pointer values to access data values.</span></span>|  
  
 <span data-ttu-id="22e8e-154">这些字段仅对表值参数有效，对于其他数据类型，将忽略它们。</span><span class="sxs-lookup"><span data-stu-id="22e8e-154">These fields are only valid with table-valued parameters, and are ignored for other data types.</span></span>  
  
 <span data-ttu-id="22e8e-155">SQL_CA_SS_TYPE_NAME 对于存储过程调用是可选项。</span><span class="sxs-lookup"><span data-stu-id="22e8e-155">SQL_CA_SS_TYPE_NAME is optional for stored procedure calls.</span></span> <span data-ttu-id="22e8e-156">对于不是过程调用的 SQL 语句，则必须指定它，才能使服务器能够确定表值参数的类型。</span><span class="sxs-lookup"><span data-stu-id="22e8e-156">It must be specified for SQL statements that are not procedure calls to enable the server to determine the type of the table-valued parameter.</span></span>  
  
 <span data-ttu-id="22e8e-157">如果类型名称是必需的，并且在不同于该存储过程的架构中定义了表值参数的表类型，则必须在实现参数描述符 (IPD) 中指定 SQL_CA_SS_TYPE_SCHEMA_NAME。</span><span class="sxs-lookup"><span data-stu-id="22e8e-157">If the type name is reqired and the table type for the table-valued parameter is defined in a different schema than the stored procedure, SQL_CA_SS_TYPE_SCHEMA_NAME must be specified in the implementation parameter descriptor (IPD).</span></span> <span data-ttu-id="22e8e-158">如果不这样，则服务器无法确定表值参数的类型。</span><span class="sxs-lookup"><span data-stu-id="22e8e-158">If not, the server will not be able to determine the type of the table-valued parameter.</span></span> <span data-ttu-id="22e8e-159">当你调用 SQLExecute 或 SQLExecDirect 时，这将导致错误。</span><span class="sxs-lookup"><span data-stu-id="22e8e-159">This will result in an error when you call SQLExecute or SQLExecDirect.</span></span> <span data-ttu-id="22e8e-160">错误将包含 SQLSTATE= 07006 和消息“受限制的数据类型属性冲突”。</span><span class="sxs-lookup"><span data-stu-id="22e8e-160">The error will have SQLSTATE= 07006 and the message "Restricted data type attribute violation".</span></span>  
  
 <span data-ttu-id="22e8e-161">表值参数列可以使用按行或按列绑定。</span><span class="sxs-lookup"><span data-stu-id="22e8e-161">Table-valued parameter columns can use either row-wise or column-wise binding.</span></span> <span data-ttu-id="22e8e-162">默认为按列绑定。</span><span class="sxs-lookup"><span data-stu-id="22e8e-162">The default is column-wise binding.</span></span> <span data-ttu-id="22e8e-163">通过设置 SQL_ATTR_PARAM_BIND_TYPE 和 SQL_ATTR_ PARAM_BIND_OFFSET_PTR，可以指定按行绑定。</span><span class="sxs-lookup"><span data-stu-id="22e8e-163">Row-wise binding can be specified by setting SQL_ATTR_PARAM_BIND_TYPE and SQL_ATTR_ PARAM_BIND_OFFSET_PTR.</span></span> <span data-ttu-id="22e8e-164">这与对列和参数的按行绑定类似。</span><span class="sxs-lookup"><span data-stu-id="22e8e-164">This is analogous to row-wise binding of columns and parameters.</span></span>  
  
 <span data-ttu-id="22e8e-165">SQL_CA_SS_TYPE_CATALOG_NAME 和 SQL_CA_SS_TYPE_SCHEMA_NAME 还可以用于检索与 CLR 用户定义类型参数关联的目录和架构。</span><span class="sxs-lookup"><span data-stu-id="22e8e-165">SQL_CA_SS_TYPE_CATALOG_NAME and SQL_CA_SS_TYPE_SCHEMA_NAME can also be used to retrieve the catalog and schema associated with CLR user-defined type parameters.</span></span> <span data-ttu-id="22e8e-166">对于这些类型，它们是特定于类型的现有目录架构属性的替代项。</span><span class="sxs-lookup"><span data-stu-id="22e8e-166">These are alternatives to the existing type specific catalog schema attributes for these types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e8e-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22e8e-167">See Also</span></span>  
 [<span data-ttu-id="22e8e-168">ODBC&#41;&#40;表值参数</span><span class="sxs-lookup"><span data-stu-id="22e8e-168">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  