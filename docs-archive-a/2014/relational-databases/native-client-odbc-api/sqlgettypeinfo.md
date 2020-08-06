---
title: SQLGetTypeInfo |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b2bca833eeed5e51237347a5ea118d839dd36de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590777"
---
# <a name="sqlgettypeinfo"></a><span data-ttu-id="0985e-102">SQLGetTypeInfo</span><span class="sxs-lookup"><span data-stu-id="0985e-102">SQLGetTypeInfo</span></span>
  <span data-ttu-id="0985e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序报告的结果集中的 USERTYPE 列 `SQLGetTypeInfo` 。</span><span class="sxs-lookup"><span data-stu-id="0985e-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver reports the additional column USERTYPE in the result set of `SQLGetTypeInfo`.</span></span> <span data-ttu-id="0985e-104">USERTYPE 报告 DB-Library 数据类型定义，这对需要将现有 DB-Library 应用程序移植到 ODBC 的开发人员很有用。</span><span class="sxs-lookup"><span data-stu-id="0985e-104">USERTYPE reports the DB-Library data type definition and is useful to developers porting existing DB-Library applications to ODBC.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0985e-105">将标识视为属性，而 ODBC 将它视为数据类型。</span><span class="sxs-lookup"><span data-stu-id="0985e-105">treats identity as an attribute, whereas ODBC treats it as a data type.</span></span> <span data-ttu-id="0985e-106">若要解决此不匹配， `SQLGetTypeInfo` 将返回数据类型： **intidentity**、 **smallintidentity**、 **tinyintidentity**、 **decimalidentity**和**numericidentity**。</span><span class="sxs-lookup"><span data-stu-id="0985e-106">To resolve this mismatch, `SQLGetTypeInfo` returns the data types: **intidentity**, **smallintidentity**, **tinyintidentity**, **decimalidentity**, and **numericidentity**.</span></span> <span data-ttu-id="0985e-107">`SQLGetTypeInfo`结果集列 AUTO_UNIQUE_VALUE 报告这些数据类型的值为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="0985e-107">The `SQLGetTypeInfo` result set column AUTO_UNIQUE_VALUE reports the value TRUE for these data types.</span></span>  
  
 <span data-ttu-id="0985e-108">对于**varchar**、 **nvarchar**和**varbinary**， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序会分别针对 COLUMN_SIZE 值继续报告8000、4000和8000，即使它实际上是不受限制的。</span><span class="sxs-lookup"><span data-stu-id="0985e-108">For **varchar**, **nvarchar** and **varbinary**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver continues to report 8000, 4000 and 8000 respectively for the COLUMN_SIZE value, even though it is actually unlimited.</span></span> <span data-ttu-id="0985e-109">这是为了确保向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="0985e-109">This is to ensure backward compatibility.</span></span>  
  
 <span data-ttu-id="0985e-110">对于**xml**数据类型， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序报告 SQL_SS_LENGTH_UNLIMITED COLUMN_SIZE 以表示不受限制。</span><span class="sxs-lookup"><span data-stu-id="0985e-110">For the **xml** data type, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver reports SQL_SS_LENGTH_UNLIMITED for COLUMN_SIZE to denote unlimited size.</span></span>  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a><span data-ttu-id="0985e-111">SQLGetTypeInfo 和表值参数</span><span class="sxs-lookup"><span data-stu-id="0985e-111">SQLGetTypeInfo and Table-Valued Parameters</span></span>  
 <span data-ttu-id="0985e-112">表值参数的表类型实际上是一个元类型，即用于定义其他类型的类型。</span><span class="sxs-lookup"><span data-stu-id="0985e-112">The table type for table-valued parameters is effectively a meta-type-that is, a type used to define other types.</span></span> <span data-ttu-id="0985e-113">因此，无需通过 SQLGetTypeInfo 公开。</span><span class="sxs-lookup"><span data-stu-id="0985e-113">Therefore, it does not have to be exposed through SQLGetTypeInfo.</span></span> <span data-ttu-id="0985e-114">应用程序必须使用 SQLTables （而不是 SQLGetTypeInfo）来检索用于表值参数的表类型的元数据。</span><span class="sxs-lookup"><span data-stu-id="0985e-114">Applications must use SQLTables, rather than SQLGetTypeInfo, to retrieve metadata for table types used with table-valued parameters.</span></span>  
  
 <span data-ttu-id="0985e-115">有关检索表值参数的元数据的详细信息，请参阅[影响表值参数的语句属性](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0985e-115">For more information, about retrieving metdata for table-valued parameters, see [Statement Attributes that Affect Table-Valued Parameters](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md).</span></span>  
  
 <span data-ttu-id="0985e-116">有关表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="0985e-116">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="0985e-117">SQLGetTypeInfo 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="0985e-117">SQLGetTypeInfo Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="0985e-118">有关为日期/时间类型返回的值，请参阅[目录元数据](../native-client-odbc-date-time/metadata-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="0985e-118">For the values returned for date/time types, see [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).</span></span>  
  
 <span data-ttu-id="0985e-119">有关更多常规信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="0985e-119">For more general information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a><span data-ttu-id="0985e-120">SQLGetTypeInfo 对大型 CLR UDT 的支持</span><span class="sxs-lookup"><span data-stu-id="0985e-120">SQLGetTypeInfo Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="0985e-121">`SQLGetTypeInfo` 支持大型 CLR 用户定义类型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="0985e-121">`SQLGetTypeInfo` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="0985e-122">有关详细信息，请参阅[&#40;ODBC&#41;的大型 CLR 用户定义类型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="0985e-122">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0985e-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0985e-123">See Also</span></span>  
 <span data-ttu-id="0985e-124">[SQLGetTypeInfo 函数](https://go.microsoft.com/fwlink/?LinkId=59356) </span><span class="sxs-lookup"><span data-stu-id="0985e-124">[SQLGetTypeInfo Function](https://go.microsoft.com/fwlink/?LinkId=59356) </span></span>  
 [<span data-ttu-id="0985e-125">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="0985e-125">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
