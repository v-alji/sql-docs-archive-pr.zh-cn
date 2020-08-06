---
title: 日期和时间改进 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
author: rothja
ms.author: jroth
ms.openlocfilehash: 16bb9e98691aea829eb71a16ddabddb371d7bcf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692899"
---
# <a name="date-and-time-improvements-ole-db"></a><span data-ttu-id="9ca2c-102">日期和时间改进 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="9ca2c-102">Date and Time Improvements (OLE DB)</span></span>
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="9ca2c-103">引入了新的日期和时间数据类型。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-103">introduces new date and time data types.</span></span> <span data-ttu-id="9ca2c-104">本部分介绍如何将这些新类型作为本机客户端中的扩展公开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-104">This section describes how these new types are exposed as extensions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="9ca2c-105">有关对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 新日期和时间数据类型的 Native Client 支持的概述，请参阅[日期和时间改进](../native-client/features/date-and-time-improvements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-105">For an overview of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client support for the new date and time data types, see [Date and Time Improvements](../native-client/features/date-and-time-improvements.md).</span></span> <span data-ttu-id="9ca2c-106">例如，请参阅[使用增强的日期和时间功能 (OLE DB)](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-106">For a sample, see [Use Enhanced Date and Time Features &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).</span></span>  
  
 <span data-ttu-id="9ca2c-107">有关日期和时间数据类型的更多常规信息，请参阅 [datetime (Transact-SQL)](/sql/t-sql/data-types/datetime-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-107">For more general information about date and time data types, see [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ca2c-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="9ca2c-108">In This Section</span></span>  
 [<span data-ttu-id="9ca2c-109">针对 OLE DB 日期和时间改进的数据类型支持</span><span class="sxs-lookup"><span data-stu-id="9ca2c-109">Data Type Support for OLE DB Date and Time Improvements</span></span>](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 <span data-ttu-id="9ca2c-110">提供有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和时间数据类型 OLE DB (Native Client) 类型的信息。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-110">Provides information about OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span>  
  
 [<span data-ttu-id="9ca2c-111">元数据 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="9ca2c-111">Metadata &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/metadata-ole-db.md)  
 <span data-ttu-id="9ca2c-112">包含有关 DBBINDING 结构、、、 `ICommandWithParameters::GetParameterInfo` `ICommandWithParameters::SetParameterInfo` `IColumnsRowset::GetColumnsRowset` 和 I 的信息 `ColumnsInfo::GetColumnInfo` 。还提供有关 OLE DB 架构行集的更新的信息。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-112">Contains information about the DBBINDING structure, `ICommandWithParameters::GetParameterInfo`, `ICommandWithParameters::SetParameterInfo`, `IColumnsRowset::GetColumnsRowset`, and I`ColumnsInfo::GetColumnInfo`. Also provides information about updates to OLE DB schema rowsets.</span></span>  
  
 [<span data-ttu-id="9ca2c-113">绑定和转换 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="9ca2c-113">Bindings and Conversions &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 <span data-ttu-id="9ca2c-114">说明在服务器和客户端之间现有和新数据类型的转换规则。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-114">Describes the rules for conversion between server and client for both existing and new date types.</span></span>  
  
 [<span data-ttu-id="9ca2c-115">&#40;OLE DB 和 ODBC 的增强日期和时间类型的大容量复制&#41;</span><span class="sxs-lookup"><span data-stu-id="9ca2c-115">Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;</span></span>](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 <span data-ttu-id="9ca2c-116">描述支持大容量复制操作的日期/时间增强功能。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-116">Describes date/time enhancements to support bulk copy operations.</span></span>  
  
 [<span data-ttu-id="9ca2c-117">OLE DB API 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="9ca2c-117">OLE DB API Support for Date and Time Enhancements</span></span>](ole-db-api-support-for-date-and-time-enhancements.md)  
 <span data-ttu-id="9ca2c-118">说明支持日期/时间增强功能的 OLE DB API。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-118">Describes the OLE DB APIs that support enhanced date/time features.</span></span>  
  
 [<span data-ttu-id="9ca2c-119">IRowsetFind 的可比性</span><span class="sxs-lookup"><span data-stu-id="9ca2c-119">Comparability for IRowsetFind</span></span>](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 <span data-ttu-id="9ca2c-120">说明日期/时间类型和 `IRowsetFind`。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-120">Describes date/time types and `IRowsetFind`.</span></span>  
  
 [<span data-ttu-id="9ca2c-121">旧 SQL Server 版本 &#40;OLE DB 的新日期和时间功能&#41;</span><span class="sxs-lookup"><span data-stu-id="9ca2c-121">New Date and Time Features with Previous SQL Server Versions &#40;OLE DB&#41;</span></span>](new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 <span data-ttu-id="9ca2c-122">说明使用日期和时间增强功能的客户端应用程序与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的早期版本通信时的预期行为，以及使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 早期版本编译的客户端向支持日期和时间增强功能的服务器发送命令的预期行为。</span><span class="sxs-lookup"><span data-stu-id="9ca2c-122">Describes the expected behavior when a client application that uses enhanced date and time features communicates with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and when a client compiled with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sends commands to a server that supports enhanced date and time features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca2c-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ca2c-123">See Also</span></span>  
 [<span data-ttu-id="9ca2c-124">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="9ca2c-124">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
