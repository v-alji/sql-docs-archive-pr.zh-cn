---
title: SQLSpecialColumns |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: rothja
ms.author: jroth
ms.openlocfilehash: c36ff73606e95ed7ee5e713b81acf7c177a42563
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586657"
---
# <a name="sqlspecialcolumns"></a><span data-ttu-id="27101-102">SQLSpecialColumns</span><span class="sxs-lookup"><span data-stu-id="27101-102">SQLSpecialColumns</span></span>
  <span data-ttu-id="27101-103"> (*IdentifierType* SQL_BEST_ROWID) 请求行标识符时， **SQLSpecialColumns**将返回一个空结果集， (除) 之外的任何请求范围之外的任何数据行。</span><span class="sxs-lookup"><span data-stu-id="27101-103">When requesting row identifiers (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** returns an empty result set (no data rows) for any requested scope other than SQL_SCOPE_CURROW.</span></span> <span data-ttu-id="27101-104">生成的结果集指示仅在此作用域内这些列有效。</span><span class="sxs-lookup"><span data-stu-id="27101-104">The generated result set indicates that the columns are only valid within this scope.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="27101-105">不支持标识符的伪列。</span><span class="sxs-lookup"><span data-stu-id="27101-105">does not support pseudocolumns for identifiers.</span></span> <span data-ttu-id="27101-106">**SQLSpecialColumns**结果集将所有列标识为 SQL_PC_NOT_PSEUDO。</span><span class="sxs-lookup"><span data-stu-id="27101-106">The **SQLSpecialColumns** result set will identify all columns as SQL_PC_NOT_PSEUDO.</span></span>  
  
 <span data-ttu-id="27101-107">可以对静态游标执行**SQLSpecialColumns** 。</span><span class="sxs-lookup"><span data-stu-id="27101-107">**SQLSpecialColumns** can be executed on a static cursor.</span></span> <span data-ttu-id="27101-108">尝试在可更新 (键集驱动或动态) 上执行**SQLSpecialColumns**会返回 SQL_SUCCESS_WITH_INFO，指示游标类型已更改。</span><span class="sxs-lookup"><span data-stu-id="27101-108">An attempt to execute **SQLSpecialColumns** on an updatable (keyset-driven or dynamic) returns SQL_SUCCESS_WITH_INFO indicating the cursor type has been changed.</span></span>  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="27101-109">SQLSpecialColumns 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="27101-109">SQLSpecialColumns Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="27101-110">有关为日期/时间类型 DATA_TYPE、TYPE_NAME、COLUMN_SIZE、BUFFER_LENGTH 和 DECIMAL_DIGTS 返回的列的值的信息，请参阅[目录元数据](../native-client-odbc-date-time/metadata-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="27101-110">For information about the values returned for the columns DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH, and DECIMAL_DIGTS for date/time types, see [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).</span></span>  
  
 <span data-ttu-id="27101-111">有关更多常规信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="27101-111">For more general information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a><span data-ttu-id="27101-112">SQLSpecialColumns 对大型 CLR UDT 的支持</span><span class="sxs-lookup"><span data-stu-id="27101-112">SQLSpecialColumns Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="27101-113">**SQLSpecialColumns**支持 (udt) 的大型 CLR 用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="27101-113">**SQLSpecialColumns** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="27101-114">有关详细信息，请参阅[&#40;ODBC&#41;的大型 CLR 用户定义类型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="27101-114">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27101-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27101-115">See Also</span></span>  
 <span data-ttu-id="27101-116">[SQLSpecialColumns 函数](https://go.microsoft.com/fwlink/?LinkId=59371) </span><span class="sxs-lookup"><span data-stu-id="27101-116">[SQLSpecialColumns Function](https://go.microsoft.com/fwlink/?LinkId=59371) </span></span>  
 [<span data-ttu-id="27101-117">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="27101-117">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
