---
title: ODBC)  (表值参数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC)
- ODBC, table-valued parameters
ms.assetid: ef06cd13-18e2-4c65-8ede-c3955d820e54
author: rothja
ms.author: jroth
ms.openlocfilehash: fedfd63f7cbafd68d39aeb62dd29c046df8ab100
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577588"
---
# <a name="table-valued-parameters-odbc"></a><span data-ttu-id="a1682-102">表值参数 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="a1682-102">Table-Valued Parameters (ODBC)</span></span>
  <span data-ttu-id="a1682-103">针对表值参数的 ODBC 支持通过在一个调用中向服务器发送多个行，支持客户端应用程序更有效地向服务器发送参数化数据。</span><span class="sxs-lookup"><span data-stu-id="a1682-103">ODBC support for table-valued parameters lets a client application send parameterized data to the server more efficiently, by sending multiple rows to the server with one call.</span></span>  
  
 <span data-ttu-id="a1682-104">有关服务器上的表值参数的信息，请参阅[使用表值参数 &#40;数据库引擎&#41;](../tables/use-table-valued-parameters-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="a1682-104">For information about table-valued parameters on the server, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
 <span data-ttu-id="a1682-105">在 ODBC 中，向服务器发送表值参数有两种方式：</span><span class="sxs-lookup"><span data-stu-id="a1682-105">In ODBC, there are two ways that you can send table-valued parameters to the server:</span></span>  
  
-   <span data-ttu-id="a1682-106">在调用 SQLExecDirect 或 SQLExecute 时，所有表值参数数据都可以在内存中。</span><span class="sxs-lookup"><span data-stu-id="a1682-106">All the table-valued parameter data can be in memory at the time SQLExecDirect or SQLExecute is called.</span></span> <span data-ttu-id="a1682-107">如果表值中有多个行，此数据存储在数组中。</span><span class="sxs-lookup"><span data-stu-id="a1682-107">This data is stored in arrays if there are multiple rows in the table-value.</span></span>  
  
-   <span data-ttu-id="a1682-108">调用 SQLExecDirect 或 SQLExecute 时，应用程序可以为表值参数指定执行时数据。</span><span class="sxs-lookup"><span data-stu-id="a1682-108">An application can specify data-at-execution for a table-valued parameter when SQLExecDirect or SQLExecute is called.</span></span> <span data-ttu-id="a1682-109">这种情况下，可以成批提供表值的各行数据，或者一次提供一行数据，以降低内存要求。</span><span class="sxs-lookup"><span data-stu-id="a1682-109">In this case, rows of data for the table-value can be provided in batches, or one at a time to reduce memory requirements.</span></span>  
  
 <span data-ttu-id="a1682-110">第一个选项支持存储过程封装更多业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="a1682-110">The first option enables stored procedures to encapsulate more business logic.</span></span> <span data-ttu-id="a1682-111">例如，将订单项作为表值参数传递时，单个存储过程可以封装整个订单输入事务。</span><span class="sxs-lookup"><span data-stu-id="a1682-111">For example, a single stored procedure could encapsulate a whole order entry transaction when the order items are passed as a table-valued parameter.</span></span> <span data-ttu-id="a1682-112">由于只需与服务器往返一次，所以此选项非常有效。</span><span class="sxs-lookup"><span data-stu-id="a1682-112">This option is very efficient, because only a single round trip to the server is required.</span></span> <span data-ttu-id="a1682-113">或者，可以使用不同的过程分别处理订单头和订单项，这需要为客户端和服务器之间提供更多的代码和更复杂的合同。</span><span class="sxs-lookup"><span data-stu-id="a1682-113">Alternatively, you could use different procedures to handle the order header and order items separately, which would require more code and a more complex contract between the client and server.</span></span>  
  
 <span data-ttu-id="a1682-114">第二种方法为涉及海量数据的大容量操作提供了有效的机制。</span><span class="sxs-lookup"><span data-stu-id="a1682-114">The second method provides an efficient mechanism for bulk operations with very large amounts of data.</span></span> <span data-ttu-id="a1682-115">该方法支持应用程序将数据行流式传送到服务器，而不是先将所有数据缓存在内存中。</span><span class="sxs-lookup"><span data-stu-id="a1682-115">This enables an application to stream rows of data to the server without having to buffer them all in memory first.</span></span>  
  
 <span data-ttu-id="a1682-116">创建表变量时可以创建约束和主键。</span><span class="sxs-lookup"><span data-stu-id="a1682-116">You can create constraints and primary keys when you create the table variable.</span></span> <span data-ttu-id="a1682-117">约束是确保表中数据满足特定要求的一种好方法。</span><span class="sxs-lookup"><span data-stu-id="a1682-117">Constraints are a good way to ensure that the data in a table meets specific requirements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1682-118">本节内容</span><span class="sxs-lookup"><span data-stu-id="a1682-118">In This Section</span></span>  
 [<span data-ttu-id="a1682-119">ODBC 表值参数的用法</span><span class="sxs-lookup"><span data-stu-id="a1682-119">Uses of ODBC Table-Valued Parameters</span></span>](uses-of-odbc-table-valued-parameters.md)  
 <span data-ttu-id="a1682-120">说明表值参数和 ODBC 的主要用户方案。</span><span class="sxs-lookup"><span data-stu-id="a1682-120">Describes the primary user scenarios for table-valued parameters and ODBC.</span></span>  
  
 [<span data-ttu-id="a1682-121">表值参数的 ODBC SQL 类型</span><span class="sxs-lookup"><span data-stu-id="a1682-121">ODBC SQL Type for Table-Valued Parameters</span></span>](odbc-sql-type-for-table-valued-parameters.md)  
 <span data-ttu-id="a1682-122">说明 SQL_SS_TABLE 类型。</span><span class="sxs-lookup"><span data-stu-id="a1682-122">Describes the SQL_SS_TABLE type.</span></span> <span data-ttu-id="a1682-123">这是一种新的支持表值参数的 ODBC SQL 类型。</span><span class="sxs-lookup"><span data-stu-id="a1682-123">This is a new ODBC SQL type that supports table-valued parameters.</span></span>  
  
 [<span data-ttu-id="a1682-124">表值参数描述符字段</span><span class="sxs-lookup"><span data-stu-id="a1682-124">Table-Valued Parameter Descriptor Fields</span></span>](table-valued-parameter-descriptor-fields.md)  
 <span data-ttu-id="a1682-125">说明支持表值参数的描述符字段。</span><span class="sxs-lookup"><span data-stu-id="a1682-125">Describes descriptor fields that support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="a1682-126">表值参数构成列的描述符字段</span><span class="sxs-lookup"><span data-stu-id="a1682-126">Descriptor Fields for Table-Valued Parameter Constituent Columns</span></span>](descriptor-fields-for-table-valued-parameter-constituent-columns.md)  
 <span data-ttu-id="a1682-127">说明包含表值参数含义的描述符字段。</span><span class="sxs-lookup"><span data-stu-id="a1682-127">Describes descriptor fields that have meaning for table-valued parameters.</span></span>  
  
 [<span data-ttu-id="a1682-128">表值参数诊断记录字段</span><span class="sxs-lookup"><span data-stu-id="a1682-128">Table-Valued Parameter Diagnostic Record Fields</span></span>](table-valued-parameter-diagnostic-record-fields.md)  
 <span data-ttu-id="a1682-129">说明已添加到诊断记录中用于支持表值参数的两个诊断字段。</span><span class="sxs-lookup"><span data-stu-id="a1682-129">Describes two diagnostic fields that have been added to diagnostic records to support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="a1682-130">影响表值参数的语句属性</span><span class="sxs-lookup"><span data-stu-id="a1682-130">Statement Attributes that Affect Table-Valued Parameters</span></span>](statement-attributes-that-affect-table-valued-parameters.md)  
 <span data-ttu-id="a1682-131">说明支持对表值参数列寻址的新描述符标题字段。</span><span class="sxs-lookup"><span data-stu-id="a1682-131">Describes a new descriptor header field that enables table-valued parameters columns to be addressed.</span></span>  
  
 [<span data-ttu-id="a1682-132">表值参数和列值的绑定及数据传输</span><span class="sxs-lookup"><span data-stu-id="a1682-132">Binding and Data Transfer of Table-Valued Parameters and Column Values</span></span>](binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)  
 <span data-ttu-id="a1682-133">说明参数绑定以及如何将表值参数传递到服务器。</span><span class="sxs-lookup"><span data-stu-id="a1682-133">Describes parameter binding and how to pass a table-valued parameter to the server.</span></span>  
  
 [<span data-ttu-id="a1682-134">准备的语句的表值参数元数据</span><span class="sxs-lookup"><span data-stu-id="a1682-134">Table-Valued Parameter Metadata for Prepared Statements</span></span>](table-valued-parameter-metadata-for-prepared-statements.md)  
 <span data-ttu-id="a1682-135">说明应用程序如何获取准备的过程调用的元数据。</span><span class="sxs-lookup"><span data-stu-id="a1682-135">Describes how an application can obtain metadata for a prepared procedure call.</span></span>  
  
 [<span data-ttu-id="a1682-136">其他表值参数的元数据</span><span class="sxs-lookup"><span data-stu-id="a1682-136">Additional Table-Valued Parameter Metadata</span></span>](additional-table-valued-parameter-metadata.md)  
 <span data-ttu-id="a1682-137">介绍如何使用 SQLProcedureColumns、SQLTables 和 SQLColumns 检索表值参数的元数据。</span><span class="sxs-lookup"><span data-stu-id="a1682-137">Describes how to use SQLProcedureColumns, SQLTables, and SQLColumns to retrieve metadata for a table-valued parameter.</span></span>  
  
 [<span data-ttu-id="a1682-138">表值参数数据转换及其他错误和警告</span><span class="sxs-lookup"><span data-stu-id="a1682-138">Table-Valued Parameter Data Conversion and Other Errors and Warnings</span></span>](table-valued-parameter-data-conversion-and-other-errors-and-warnings.md)  
 <span data-ttu-id="a1682-139">说明如何处理表值参数列值的错误。</span><span class="sxs-lookup"><span data-stu-id="a1682-139">Describes how to process errors on table-valued parameter column values.</span></span>  
  
 [<span data-ttu-id="a1682-140">跨版本兼容性</span><span class="sxs-lookup"><span data-stu-id="a1682-140">Cross-Version Compatibility</span></span>](cross-version-compatibility.md)  
 <span data-ttu-id="a1682-141">说明当 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 之前版本的客户端或服务器使用表值参数时可能出现的冲突。</span><span class="sxs-lookup"><span data-stu-id="a1682-141">Describes conflicts that can occur when table-valued parameters are used by a client or server of a version earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 [<span data-ttu-id="a1682-142">ODBC 表值参数 API 摘要</span><span class="sxs-lookup"><span data-stu-id="a1682-142">ODBC Table-Valued Parameter API Summary</span></span>](odbc-table-valued-parameter-api-summary.md)  
 <span data-ttu-id="a1682-143">列出支持表值参数的 ODBC 函数。</span><span class="sxs-lookup"><span data-stu-id="a1682-143">Lists the ODBC functions that support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="a1682-144">ODBC 表值参数编程示例</span><span class="sxs-lookup"><span data-stu-id="a1682-144">ODBC Table-Valued Parameter Programming Examples</span></span>](../../database-engine/dev-guide/odbc-table-valued-parameter-programming-examples.md)  
 <span data-ttu-id="a1682-145">说明如何执行常见任务。</span><span class="sxs-lookup"><span data-stu-id="a1682-145">Describes how to perform common tasks.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1682-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1682-146">See Also</span></span>  
 <span data-ttu-id="a1682-147">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="a1682-147">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="a1682-148">表值参数 &#40;SQL Server Native Client&#41;</span><span class="sxs-lookup"><span data-stu-id="a1682-148">Table-Valued Parameters &#40;SQL Server Native Client&#41;</span></span>](../native-client/features/table-valued-parameters-sql-server-native-client.md)  
  
  
