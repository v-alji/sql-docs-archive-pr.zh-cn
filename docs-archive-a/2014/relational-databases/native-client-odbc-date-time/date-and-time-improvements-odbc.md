---
title: ODBC)  (的日期和时间改进 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: rothja
ms.author: jroth
ms.openlocfilehash: 6ce8f906fc1949a80bfa8e5a541ecf1e83878775
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586638"
---
# <a name="date-and-time-improvements-odbc"></a><span data-ttu-id="84e82-102">日期和时间改进 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="84e82-102">Date and Time Improvements (ODBC)</span></span>
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="84e82-103">引入了新的日期和时间数据类型。</span><span class="sxs-lookup"><span data-stu-id="84e82-103">introduced new date and time data types.</span></span> <span data-ttu-id="84e82-104">本部分介绍如何将这些新类型作为本机客户端中的扩展公开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="84e82-104">This section describes how these new types are exposed as extensions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="84e82-105">有关对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 新日期和时间数据类型的 Native Client 支持的概述，请参阅[日期和时间改进](../native-client/features/date-and-time-improvements.md)。</span><span class="sxs-lookup"><span data-stu-id="84e82-105">For an overview of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client support for the new date and time data types, see [Date and Time Improvements](../native-client/features/date-and-time-improvements.md).</span></span> <span data-ttu-id="84e82-106">有关演示 ODBC 日期/时间支持的示例，请参阅[使用日期和时间类型](../native-client-odbc-how-to/use-date-and-time-types.md)。</span><span class="sxs-lookup"><span data-stu-id="84e82-106">For a sample demonstrating ODBC date/time support, see [Use Date and Time Types](../native-client-odbc-how-to/use-date-and-time-types.md).</span></span>  
  
 <span data-ttu-id="84e82-107">有关日期和时间数据类型的更多常规信息，请参阅 [datetime (Transact-SQL)](/sql/t-sql/data-types/datetime-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="84e82-107">For more general information about date and time data types, see [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="84e82-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="84e82-108">In This Section</span></span>  
 [<span data-ttu-id="84e82-109">针对 ODBC 日期/时间改进的数据类型支持</span><span class="sxs-lookup"><span data-stu-id="84e82-109">Data Type Support for ODBC Date and Time Improvements</span></span>](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 <span data-ttu-id="84e82-110">提供有关支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和时间数据类型的 ODBC 类型的信息。</span><span class="sxs-lookup"><span data-stu-id="84e82-110">Provides information about ODBC types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span>  
  
 [<span data-ttu-id="84e82-111">Metadata &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="84e82-111">Metadata &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/metadata-odbc.md)  
 <span data-ttu-id="84e82-112">描述在实现参数描述符 (IPD) 和实现行描述符 (IRD) 字段中返回的信息，以及由 `SQLColumns` 和 `SQLProcedureColumns` 返回的列元数据。</span><span class="sxs-lookup"><span data-stu-id="84e82-112">Describes information returned in the implementation parameter descriptor (IPD) and implementation row descriptor (IRD) fields, as well as column metadata returned by `SQLColumns` and `SQLProcedureColumns`.</span></span> <span data-ttu-id="84e82-113">还描述了由 `SQLGetTypeInfo` 返回的数据类型元数据。</span><span class="sxs-lookup"><span data-stu-id="84e82-113">Also describes data type metadata returned by `SQLGetTypeInfo`.</span></span>  
  
 [<span data-ttu-id="84e82-114">datetime 数据类型转换 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="84e82-114">datetime Data Type Conversions &#40;ODBC&#41;</span></span>](datetime-data-type-conversions-odbc.md)  
 <span data-ttu-id="84e82-115">描述如何在 datetime 值和 datetimeoffset 值之间进行转换。</span><span class="sxs-lookup"><span data-stu-id="84e82-115">Describes how to convert between datetime and datetimeoffset values.</span></span>  
  
 [<span data-ttu-id="84e82-116">sql_variant 对日期和时间类型的支持</span><span class="sxs-lookup"><span data-stu-id="84e82-116">sql_variant Support for Date and Time Types</span></span>](sql-variant-support-for-date-and-time-types.md)  
 <span data-ttu-id="84e82-117">描述用于获得增强的日期和时间功能的 SQL_VARIANT 函数支持。</span><span class="sxs-lookup"><span data-stu-id="84e82-117">Describes SQL_VARIANT function support for enhanced date and time functionality.</span></span>  
  
 [<span data-ttu-id="84e82-118">&#40;OLE DB 和 ODBC 的增强日期和时间类型的大容量复制&#41;</span><span class="sxs-lookup"><span data-stu-id="84e82-118">Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;</span></span>](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 <span data-ttu-id="84e82-119">描述支持大容量复制操作的日期/时间增强功能。</span><span class="sxs-lookup"><span data-stu-id="84e82-119">Describes date/time enhancements to support bulk copy operations.</span></span>  
  
 [<span data-ttu-id="84e82-120">早期 SQL Server 版本的增强日期和时间类型行为 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="84e82-120">Enhanced Date and Time Type Behavior with Previous SQL Server Versions &#40;ODBC&#41;</span></span>](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 <span data-ttu-id="84e82-121">描述使用日期和时间增强功能的客户端应用程序与早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通信时的预期行为，以及使用早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 编译的客户端向支持日期和时间增强功能的服务器发送命令时的预期行为。</span><span class="sxs-lookup"><span data-stu-id="84e82-121">Describes the expected behavior when a client application using enhanced date and time features communicates with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and when a client compiled with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sends commands to a server that supports enhanced date and time features.</span></span>  
  
 [<span data-ttu-id="84e82-122">ODBC API 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="84e82-122">ODBC API Support for Enhanced Date and Time Features</span></span>](odbc-api-support-for-enhanced-date-and-time-features.md)  
 <span data-ttu-id="84e82-123">列出了支持日期和时间增强功能的 ODBC 函数。</span><span class="sxs-lookup"><span data-stu-id="84e82-123">Lists the ODBC functions that support enhanced date and time functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e82-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84e82-124">See Also</span></span>  
 [<span data-ttu-id="84e82-125">SQL Server Native Client (ODBC)</span><span class="sxs-lookup"><span data-stu-id="84e82-125">SQL Server Native Client &#40;ODBC&#41;</span></span>](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
