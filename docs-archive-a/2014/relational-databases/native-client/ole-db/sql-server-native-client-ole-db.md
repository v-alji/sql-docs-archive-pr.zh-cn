---
title: SQL Server Native Client (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, about SQL Server Native Client OLE DB provider
- OLE DB, SQL Server Native Client OLE DB provider
- data access [SQL Server Native Client], OLE DB
- SQLNCLI, OLE DB
- OLE DB
- SQL Server Native Client OLE DB provider
- SQL Server Native Client, OLE DB
ms.assetid: da846da4-ec19-4a4f-81fb-7d5a2b2bf80a
author: rothja
ms.author: jroth
ms.openlocfilehash: 46b948eb1d075edc6000849dcb2d18ea372809d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580706"
---
# <a name="sql-server-native-client-ole-db"></a><span data-ttu-id="7f17f-102">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7f17f-102">SQL Server Native Client (OLE DB)</span></span>
  <span data-ttu-id="7f17f-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口是用于访问数据的底层 COM API。</span><span class="sxs-lookup"><span data-stu-id="7f17f-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is a low-level COM API that is used for accessing data.</span></span> <span data-ttu-id="7f17f-104">建议将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口用于开发需要高性能的工具、实用工具或底层组件。</span><span class="sxs-lookup"><span data-stu-id="7f17f-104">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is recommended for developing tools, utilities, or low-level components that need high performance.</span></span> <span data-ttu-id="7f17f-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口是直接访问 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表格格式数据流 (TDS) 协议的本机高性能访问接口。</span><span class="sxs-lookup"><span data-stu-id="7f17f-105">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is a native, high performance provider that accesses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabular Data Stream (TDS) protocol directly.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="7f17f-106">Native Client 对连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的应用程序提供 OLE DB 支持。</span><span class="sxs-lookup"><span data-stu-id="7f17f-106">Native Client provides OLE DB support to applications connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7f17f-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序是一个 OLE DB 版本2.0 兼容的提供程序。</span><span class="sxs-lookup"><span data-stu-id="7f17f-107">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is an OLE DB version 2.0-compliant provider.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f17f-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="7f17f-108">In This Section</span></span>  
  
-   [<span data-ttu-id="7f17f-109">创建 SQL Server Native Client OLE DB 访问接口应用程序</span><span class="sxs-lookup"><span data-stu-id="7f17f-109">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](../../native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
-   [<span data-ttu-id="7f17f-110">数据源对象 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7f17f-110">Data Source Objects &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
-   [<span data-ttu-id="7f17f-111">命令</span><span class="sxs-lookup"><span data-stu-id="7f17f-111">Commands</span></span>](../../native-client-ole-db-commands/commands.md)  
  
-   [<span data-ttu-id="7f17f-112">行集</span><span class="sxs-lookup"><span data-stu-id="7f17f-112">Rowsets</span></span>](../../native-client-ole-db-rowsets/rowsets.md)  
  
-   [<span data-ttu-id="7f17f-113">存储过程</span><span class="sxs-lookup"><span data-stu-id="7f17f-113">Stored Procedures</span></span>](stored-procedures.md)  
  
-   [<span data-ttu-id="7f17f-114">BLOB 和 OLE 对象</span><span class="sxs-lookup"><span data-stu-id="7f17f-114">BLOBs and OLE Objects</span></span>](../../native-client-ole-db-blobs/blobs-and-ole-objects.md)  
  
-   [<span data-ttu-id="7f17f-115">表和索引</span><span class="sxs-lookup"><span data-stu-id="7f17f-115">Tables and Indexes</span></span>](../../native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
-   [<span data-ttu-id="7f17f-116">数据类型 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7f17f-116">Data Types &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-data-types/data-types-ole-db.md)  
  
-   [<span data-ttu-id="7f17f-117">架构行集支持 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7f17f-117">Schema Rowset Support &#40;OLE DB&#41;</span></span>](schema-rowset-support-ole-db.md)  
  
-   [<span data-ttu-id="7f17f-118">表值参数 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7f17f-118">Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)  
  
-   [<span data-ttu-id="7f17f-119">日期和时间改进 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7f17f-119">Date and Time Improvements &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
-   [<span data-ttu-id="7f17f-120">大型 CLR 用户定义类型 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7f17f-120">Large CLR User-Defined Types &#40;OLE DB&#41;</span></span>](large-clr-user-defined-types-ole-db.md)  
  
-   [<span data-ttu-id="7f17f-121">FILESTREAM 支持 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="7f17f-121">FILESTREAM Support &#40;OLE DB&#41;</span></span>](filestream-support-ole-db.md)  
  
-   [<span data-ttu-id="7f17f-122">事务</span><span class="sxs-lookup"><span data-stu-id="7f17f-122">Transactions</span></span>](../../native-client-ole-db-transactions/transactions.md)  
  
-   [<span data-ttu-id="7f17f-123">错误</span><span class="sxs-lookup"><span data-stu-id="7f17f-123">Errors</span></span>](../../native-client-ole-db-errors/errors.md)  
  
-   [<span data-ttu-id="7f17f-124">客户端连接中的服务主体名称 (SPN) (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7f17f-124">Service Principal Names &#40;SPNs&#41; in Client Connections &#40;OLE DB&#41;</span></span>](service-principal-names-spns-in-client-connections-ole-db.md)  
  
-   [<span data-ttu-id="7f17f-125">稀疏列支持 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="7f17f-125">Sparse Columns Support &#40;OLE DB&#41;</span></span>](sparse-columns-support-ole-db.md)  
  
-   [<span data-ttu-id="7f17f-126">SQL Server Native Client &#40;OLE DB&#41; 参考</span><span class="sxs-lookup"><span data-stu-id="7f17f-126">SQL Server Native Client &#40;OLE DB&#41; Reference</span></span>](../../native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md)  
  
-   [<span data-ttu-id="7f17f-127">OLE DB 操作指南主题</span><span class="sxs-lookup"><span data-stu-id="7f17f-127">OLE DB How-to Topics</span></span>](../../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="7f17f-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f17f-128">See Also</span></span>  
 [<span data-ttu-id="7f17f-129">SQL Server Native Client 编程</span><span class="sxs-lookup"><span data-stu-id="7f17f-129">SQL Server Native Client Programming</span></span>](../sql-server-native-client-programming.md)  
  
  
