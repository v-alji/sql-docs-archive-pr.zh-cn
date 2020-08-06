---
title: SQLProcedureColumns |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedureColumns function
ms.assetid: 6671e180-0072-4de5-90f5-314306d2ba9c
author: rothja
ms.author: jroth
ms.openlocfilehash: 66814c4d79108b2bb2c829a5e522d45d7eeaed22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590760"
---
# <a name="sqlprocedurecolumns"></a><span data-ttu-id="205cf-102">SQLProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="205cf-102">SQLProcedureColumns</span></span>
  <span data-ttu-id="205cf-103">`SQLProcedureColumns`返回一列，报告所有存储过程的返回值特性 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="205cf-103">`SQLProcedureColumns` returns one row reporting the return value attributes of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures.</span></span>  
  
 <span data-ttu-id="205cf-104">`SQLProcedureColumns`返回 SQL_SUCCESS 是否存在*CatalogName*、 *SchemaName*、 *ProcName*或*ColumnName*参数的值。</span><span class="sxs-lookup"><span data-stu-id="205cf-104">`SQLProcedureColumns` returns SQL_SUCCESS whether or not values exist for *CatalogName*, *SchemaName*, *ProcName*, or *ColumnName* parameters.</span></span> <span data-ttu-id="205cf-105">当在这些参数中使用了无效值时， **SQLFetch**将返回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="205cf-105">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="205cf-106">可以对静态服务器游标执行 `SQLProcedureColumns`。</span><span class="sxs-lookup"><span data-stu-id="205cf-106">`SQLProcedureColumns` can be executed on a static server cursor.</span></span> <span data-ttu-id="205cf-107">尝试对可更新的（动态或键集）游标执行 `SQLProcedureColumns` 时，将返回 SQL_SUCCESS_WITH_INFO 以指示游标类型已更改。</span><span class="sxs-lookup"><span data-stu-id="205cf-107">An attempt to execute `SQLProcedureColumns` on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="205cf-108">下表列出了结果集返回的列，以及如何通过 Native Client ODBC 驱动程序扩展这些列来处理**udt**和**xml**数据类型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="205cf-108">The following table lists the columns returned by the result set and how they have been extended to handle the **udt** and **xml** data types through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver:</span></span>  
  
|<span data-ttu-id="205cf-109">列名称</span><span class="sxs-lookup"><span data-stu-id="205cf-109">Column name</span></span>|<span data-ttu-id="205cf-110">说明</span><span class="sxs-lookup"><span data-stu-id="205cf-110">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="205cf-111">SS_UDT_CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="205cf-111">SS_UDT_CATALOG_NAME</span></span>|<span data-ttu-id="205cf-112">返回包含 UDT（用户定义类型）的目录的名称。</span><span class="sxs-lookup"><span data-stu-id="205cf-112">Returns the name of the catalog containing the UDT (user-defined type).</span></span>|  
|<span data-ttu-id="205cf-113">SS_UDT_SCHEMA_NAME</span><span class="sxs-lookup"><span data-stu-id="205cf-113">SS_UDT_SCHEMA_NAME</span></span>|<span data-ttu-id="205cf-114">返回包含 UDT 的架构的名称。</span><span class="sxs-lookup"><span data-stu-id="205cf-114">Returns the name of the schema containing the UDT.</span></span>|  
|<span data-ttu-id="205cf-115">SS_UDT_ASSEMBLY_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="205cf-115">SS_UDT_ASSEMBLY_TYPE_NAME</span></span>|<span data-ttu-id="205cf-116">返回 UDT 的程序集限定名称。</span><span class="sxs-lookup"><span data-stu-id="205cf-116">Returns the assembly-qualified name of the UDT.</span></span>|  
|<span data-ttu-id="205cf-117">SS_XML_SCHEMACOLLECTION_CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="205cf-117">SS_XML_SCHEMACOLLECTION_CATALOG_NAME</span></span>|<span data-ttu-id="205cf-118">返回在其中定义 XML 架构集合名称的目录的名称。</span><span class="sxs-lookup"><span data-stu-id="205cf-118">Returns the name of the catalog where an XML schema collection name is defined.</span></span> <span data-ttu-id="205cf-119">如果找不到目录名称，则此变量包含空字符串。</span><span class="sxs-lookup"><span data-stu-id="205cf-119">If the catalog name cannot be found, then this variable contains an empty string.</span></span>|  
|<span data-ttu-id="205cf-120">SS_XML_SCHEMACOLLECTION_SCHEMA_NAME</span><span class="sxs-lookup"><span data-stu-id="205cf-120">SS_XML_SCHEMACOLLECTION_SCHEMA_NAME</span></span>|<span data-ttu-id="205cf-121">返回在其中定义 XML 架构集合名称的架构的名称。</span><span class="sxs-lookup"><span data-stu-id="205cf-121">Returns the name of the schema where an XML schema collection name is defined.</span></span> <span data-ttu-id="205cf-122">如果找不到架构名称，则此变量包含空字符串。</span><span class="sxs-lookup"><span data-stu-id="205cf-122">If the schema name cannot be found, then this variable contains an empty string.</span></span>|  
|<span data-ttu-id="205cf-123">SS_XML_SCHEMACOLLECTION_NAME</span><span class="sxs-lookup"><span data-stu-id="205cf-123">SS_XML_SCHEMACOLLECTION_NAME</span></span>|<span data-ttu-id="205cf-124">返回 XML 架构集合的名称。</span><span class="sxs-lookup"><span data-stu-id="205cf-124">Returns the name of an XML schema collection.</span></span> <span data-ttu-id="205cf-125">如果找不到此名称，则此变量包含空字符串。</span><span class="sxs-lookup"><span data-stu-id="205cf-125">If the name cannot be found, then this variable contains an empty string.</span></span>|  
  
## <a name="sqlprocedurecolumns-and-table-valued-parameters"></a><span data-ttu-id="205cf-126">SQLProcedureColumns 和表值参数</span><span class="sxs-lookup"><span data-stu-id="205cf-126">SQLProcedureColumns and Table-Valued Parameters</span></span>  
 <span data-ttu-id="205cf-127">SQLProcedureColumns 以类似于 CLR 用户定义类型的方式处理表值参数。</span><span class="sxs-lookup"><span data-stu-id="205cf-127">SQLProcedureColumns handles table-valued parameters in a manner similar to CLR user-defined types.</span></span> <span data-ttu-id="205cf-128">在针对表值参数返回的行中，列具有以下值：</span><span class="sxs-lookup"><span data-stu-id="205cf-128">In rows returned for table-valued parameters, columns have the following values:</span></span>  
  
|<span data-ttu-id="205cf-129">列名称</span><span class="sxs-lookup"><span data-stu-id="205cf-129">Column name</span></span>|<span data-ttu-id="205cf-130">说明/值</span><span class="sxs-lookup"><span data-stu-id="205cf-130">Description/value</span></span>|  
|-----------------|------------------------|  
|<span data-ttu-id="205cf-131">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="205cf-131">DATA_TYPE</span></span>|<span data-ttu-id="205cf-132">SQL_SS_TABLE</span><span class="sxs-lookup"><span data-stu-id="205cf-132">SQL_SS_TABLE</span></span>|  
|<span data-ttu-id="205cf-133">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="205cf-133">TYPE_NAME</span></span>|<span data-ttu-id="205cf-134">表值参数的表类型的名称。</span><span class="sxs-lookup"><span data-stu-id="205cf-134">The name of the table type for the table-valued parameter.</span></span>|  
|<span data-ttu-id="205cf-135">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="205cf-135">COLUMN_SIZE</span></span>|<span data-ttu-id="205cf-136">Null</span><span class="sxs-lookup"><span data-stu-id="205cf-136">NULL</span></span>|  
|<span data-ttu-id="205cf-137">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="205cf-137">BUFFER_LENGTH</span></span>|<span data-ttu-id="205cf-138">0</span><span class="sxs-lookup"><span data-stu-id="205cf-138">0</span></span>|  
|<span data-ttu-id="205cf-139">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="205cf-139">DECIMAL_DIGITS</span></span>|<span data-ttu-id="205cf-140">表值参数中的列数。</span><span class="sxs-lookup"><span data-stu-id="205cf-140">The number of columns in the table-valued parameter.</span></span>|  
|<span data-ttu-id="205cf-141">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="205cf-141">NUM_PREC_RADIX</span></span>|<span data-ttu-id="205cf-142">Null</span><span class="sxs-lookup"><span data-stu-id="205cf-142">NULL</span></span>|  
|<span data-ttu-id="205cf-143">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="205cf-143">NULLABLE</span></span>|<span data-ttu-id="205cf-144">SQL_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="205cf-144">SQL_NULLABLE</span></span>|  
|<span data-ttu-id="205cf-145">REMARKS</span><span class="sxs-lookup"><span data-stu-id="205cf-145">REMARKS</span></span>|<span data-ttu-id="205cf-146">Null</span><span class="sxs-lookup"><span data-stu-id="205cf-146">NULL</span></span>|  
|<span data-ttu-id="205cf-147">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="205cf-147">COLUMN_DEF</span></span>|<span data-ttu-id="205cf-148">NULL。</span><span class="sxs-lookup"><span data-stu-id="205cf-148">NULL.</span></span> <span data-ttu-id="205cf-149">表类型可能没有默认值。</span><span class="sxs-lookup"><span data-stu-id="205cf-149">Table types might not have default values.</span></span>|  
|<span data-ttu-id="205cf-150">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="205cf-150">SQL_DATA_TYPE</span></span>|<span data-ttu-id="205cf-151">SQL_SS_TABLE</span><span class="sxs-lookup"><span data-stu-id="205cf-151">SQL_SS_TABLE</span></span>|  
|<span data-ttu-id="205cf-152">SQL_DATEIME_SUB</span><span class="sxs-lookup"><span data-stu-id="205cf-152">SQL_DATEIME_SUB</span></span>|<span data-ttu-id="205cf-153">Null</span><span class="sxs-lookup"><span data-stu-id="205cf-153">NULL</span></span>|  
|<span data-ttu-id="205cf-154">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="205cf-154">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="205cf-155">Null</span><span class="sxs-lookup"><span data-stu-id="205cf-155">NULL</span></span>|  
|<span data-ttu-id="205cf-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="205cf-156">IS_NULLABLE</span></span>|<span data-ttu-id="205cf-157">"YES"</span><span class="sxs-lookup"><span data-stu-id="205cf-157">"YES"</span></span>|  
|<span data-ttu-id="205cf-158">SS_TYPE_CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="205cf-158">SS_TYPE_CATALOG_NAME</span></span>|<span data-ttu-id="205cf-159">返回包含表或 CLR 用户定义类型的目录的名称。</span><span class="sxs-lookup"><span data-stu-id="205cf-159">Returns the name of the catalog that contains the table or CLR user-defined type.</span></span>|  
|<span data-ttu-id="205cf-160">SS_TYPE_SCHEMA_NAME</span><span class="sxs-lookup"><span data-stu-id="205cf-160">SS_TYPE_SCHEMA_NAME</span></span>|<span data-ttu-id="205cf-161">返回包含表或 CLR 用户定义类型的架构的名称。</span><span class="sxs-lookup"><span data-stu-id="205cf-161">Returns the name of the schema that contains the table or CLR user-defined type.</span></span>|  
  
 <span data-ttu-id="205cf-162">SS_TYPE_CATALOG_NAME 和 SS_TYPE_SCHEMA_NAME 列在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更高版本中提供，分别用于返回表值参数的目录和架构。</span><span class="sxs-lookup"><span data-stu-id="205cf-162">The SS_TYPE_CATALOG_NAME and SS_TYPE_SCHEMA_NAME columns are available in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions to return the catalog and schema, respectively, for table-valued parameters.</span></span> <span data-ttu-id="205cf-163">这些列是为表值参数和 CLR 用户定义类型参数填充的。</span><span class="sxs-lookup"><span data-stu-id="205cf-163">These columns are populated for table-valued parameters, and also for CLR user-defined type parameters.</span></span> <span data-ttu-id="205cf-164">（CLR 用户定义类型参数的现有架构和目录列不受此附加功能影响。</span><span class="sxs-lookup"><span data-stu-id="205cf-164">(Existing schema and catalog columns for CLR user-defined type parameters are not affected by this additional functionality.</span></span> <span data-ttu-id="205cf-165">为保持向后兼容，也会对它们进行填充）。</span><span class="sxs-lookup"><span data-stu-id="205cf-165">They are also populated to maintain backward compatibility).</span></span>  
  
 <span data-ttu-id="205cf-166">为了符合 ODBC 规范，SS_TYPE_CATALOG_NAME 和 SS_TYPE_SCHEMA_NAME 的显示位置位于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 早期版本中添加的所有驱动程序特定列之前，ODBC 自身托管的所有列之后。</span><span class="sxs-lookup"><span data-stu-id="205cf-166">In conformance with the ODBC specification, SS_TYPE_CATALOG_NAME and SS_TYPE_SCHEMA_NAME appear before all driver-specific columns added in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and after all columns mandated by ODBC itself.</span></span>  
  
 <span data-ttu-id="205cf-167">有关表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="205cf-167">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlprocedurecolumns-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="205cf-168">SQLProcedureColumns 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="205cf-168">SQLProcedureColumns Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="205cf-169">有关为日期/时间类型返回的值，请参阅[目录元数据](../native-client-odbc-date-time/metadata-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="205cf-169">For the values returned for date/time types, see [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).</span></span>  
  
 <span data-ttu-id="205cf-170">有关更多常规信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="205cf-170">For more general information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlprocedurecolumns-support-for-large-clr-udts"></a><span data-ttu-id="205cf-171">SQLProcedureColumns 对大型 CLR UDT 的支持</span><span class="sxs-lookup"><span data-stu-id="205cf-171">SQLProcedureColumns Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="205cf-172">`SQLProcedureColumns` 支持大型 CLR 用户定义类型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="205cf-172">`SQLProcedureColumns` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="205cf-173">有关详细信息，请参阅[&#40;ODBC&#41;的大型 CLR 用户定义类型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="205cf-173">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="205cf-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="205cf-174">See Also</span></span>  
 <span data-ttu-id="205cf-175">[SQLProcedureColumns 函数](https://go.microsoft.com/fwlink/?LinkId=59363) </span><span class="sxs-lookup"><span data-stu-id="205cf-175">[SQLProcedureColumns Function](https://go.microsoft.com/fwlink/?LinkId=59363) </span></span>  
 [<span data-ttu-id="205cf-176">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="205cf-176">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
