---
title: SQLSetDescField |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescField function
ms.assetid: de4bed15-15be-4825-994c-1046255e725a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1b8290fd90c0c9bb91f08d94e119689d38fbc04e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590744"
---
# <a name="sqlsetdescfield"></a><span data-ttu-id="bb989-102">SQLSetDescField</span><span class="sxs-lookup"><span data-stu-id="bb989-102">SQLSetDescField</span></span>
  <span data-ttu-id="bb989-103">SQLSetDescField 可用于为表值参数和表值参数列设置描述符字段。</span><span class="sxs-lookup"><span data-stu-id="bb989-103">SQLSetDescField can be used to set descriptor fields for table-valued parameters and table-valued parameter columns.</span></span> <span data-ttu-id="bb989-104">有关可用字段的信息，请参阅表值参数[描述符字段](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md)和[表值参数构成列的描述符字段](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="bb989-104">For information about the available fields, see [Table-Valued Parameter Descriptor Fields](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) and [Descriptor Fields for Table-Valued Parameter Constituent Columns](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb989-105">备注</span><span class="sxs-lookup"><span data-stu-id="bb989-105">Remarks</span></span>  
 <span data-ttu-id="bb989-106">表值参数列仅在将描述符标头字段 SQL_SOPT_SS_PARAM_FOCUS 设置为特定记录（其 SQL_DESC_TYPE 设置为 SQL_SS_TABLE）的序数时可用。</span><span class="sxs-lookup"><span data-stu-id="bb989-106">Table-valued parameter columns are only available when the descriptor header field SQL_SOPT_SS_PARAM_FOCUS is set to the ordinal of a record that has SQL_DESC_TYPE set to SQL_SS_TABLE.</span></span> <span data-ttu-id="bb989-107">有关 SQL_SOPT_SS_PARAM_FOCUS 的详细信息，请参阅[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="bb989-107">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="bb989-108">如果尝试将 SQL_SOPT_SS_PARAM_FOCUS 设置为不是表值参数的参数的序号，则 SQLSetStmtAttr 将返回 SQL_ERROR，并且将使用 SQLSTATE = HY024 和消息 "属性值无效" 创建诊断记录。</span><span class="sxs-lookup"><span data-stu-id="bb989-108">If an attempt is made to set SQL_SOPT_SS_PARAM_FOCUS to the ordinal of a parameter that is not a table-valued parameter, SQLSetStmtAttr returns SQL_ERROR, and a diagnostic record is created with SQLSTATE = HY024 and the message "Invalid attribute value".</span></span> <span data-ttu-id="bb989-109">返回 SQL_ERROR 时，不更改 SQL_SOPT_SS_PARAM_FOCUS。</span><span class="sxs-lookup"><span data-stu-id="bb989-109">SQL_SOPT_SS_PARAM_FOCUS is not changed when SQL_ERROR is returned.</span></span>  
  
 <span data-ttu-id="bb989-110">将 SQL_SOPT_SS_PARAM_FOCUS 设置为 0 可以恢复对参数的描述符记录的访问权限。</span><span class="sxs-lookup"><span data-stu-id="bb989-110">Setting SQL_SOPT_SS_PARAM_FOCUS to 0 restores access to descriptor records for parameters.</span></span>  
  
 <span data-ttu-id="bb989-111">有关表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="bb989-111">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="bb989-112">SQLSetDescField 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="bb989-112">SQLSetDescField Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="bb989-113">ODBC 中已增强了日期/时间功能。</span><span class="sxs-lookup"><span data-stu-id="bb989-113">Date/time features have been enhanced in ODBC.</span></span> <span data-ttu-id="bb989-114">有关为新的日期/时间类型提供的描述符字段的信息，请参阅[参数和结果元数据](../native-client-odbc-date-time/metadata-parameter-and-result.md)。</span><span class="sxs-lookup"><span data-stu-id="bb989-114">For information about the descriptor field provided for the new date/time types, see [Parameter and Result Metadata](../native-client-odbc-date-time/metadata-parameter-and-result.md).</span></span>  
  
 <span data-ttu-id="bb989-115">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="bb989-115">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a><span data-ttu-id="bb989-116">SQLSetDescField 对大型 CLR UDT 的支持</span><span class="sxs-lookup"><span data-stu-id="bb989-116">SQLSetDescField Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="bb989-117">SQLSetDescField 支持 (Udt) 的大型 CLR 用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="bb989-117">SQLSetDescField supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="bb989-118">有关详细信息，请参阅[&#40;ODBC&#41;的大型 CLR 用户定义类型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="bb989-118">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a><span data-ttu-id="bb989-119">SQLSetDescField 对稀疏列的支持</span><span class="sxs-lookup"><span data-stu-id="bb989-119">SQLSetDescField Support for Sparse Columns</span></span>  
 <span data-ttu-id="bb989-120">可以使用 SQLSetDecField 将应用程序参数描述符中的 SQL_SOPT_SS_NAME_SCOPE 设置 (APD) 到值 SQL_SS_NAME_SCOPE_EXTENDED 和 SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET。</span><span class="sxs-lookup"><span data-stu-id="bb989-120">SQLSetDecField can be used to set SQL_SOPT_SS_NAME_SCOPE in the application parameter descriptor (APD) to the values SQL_SS_NAME_SCOPE_EXTENDED and SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.</span></span>  
  
 <span data-ttu-id="bb989-121">有关详细信息，请参阅[稀疏列支持 &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="bb989-121">For more information, see [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb989-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb989-122">See Also</span></span>  
 <span data-ttu-id="bb989-123">[SQLSetDescField](https://go.microsoft.com/fwlink/?LinkId=80705) </span><span class="sxs-lookup"><span data-stu-id="bb989-123">[SQLSetDescField](https://go.microsoft.com/fwlink/?LinkId=80705) </span></span>  
 [<span data-ttu-id="bb989-124">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="bb989-124">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
