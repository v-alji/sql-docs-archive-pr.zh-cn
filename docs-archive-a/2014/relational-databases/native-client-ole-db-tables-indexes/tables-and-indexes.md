---
title: 表和索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
author: rothja
ms.author: jroth
ms.openlocfilehash: abc7c314e433eb9f107bd191738d951706f1b50d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587779"
---
# <a name="tables-and-indexes"></a><span data-ttu-id="f5a48-102">表和索引</span><span class="sxs-lookup"><span data-stu-id="f5a48-102">Tables and Indexes</span></span>
  <span data-ttu-id="f5a48-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序公开**IIndexDefinition**和**ITableDefinition**接口，以便使用者可以创建、更改和删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表和索引。</span><span class="sxs-lookup"><span data-stu-id="f5a48-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition** and **ITableDefinition** interfaces, allowing consumers to create, alter, and drop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables and indexes.</span></span> <span data-ttu-id="f5a48-104">表和索引定义是否有效取决于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的版本。</span><span class="sxs-lookup"><span data-stu-id="f5a48-104">Valid table and index definitions depend on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f5a48-105">创建或删除表和索引的功能取决于使用者应用程序用户的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 访问权限。</span><span class="sxs-lookup"><span data-stu-id="f5a48-105">The ability to create or drop tables and indexes depends on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access rights of the consumer-application user.</span></span> <span data-ttu-id="f5a48-106">删除表的功能还可以通过是否存在声明性引用完整性约束或其他因素进行进一步限制。</span><span class="sxs-lookup"><span data-stu-id="f5a48-106">Dropping a table can be further constrained by the presence of declarative referential integrity constraints or other factors.</span></span>  
  
 <span data-ttu-id="f5a48-107">面向的大多数应用程序 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 都使用 sql-dmo，而不是使用这些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序接口。</span><span class="sxs-lookup"><span data-stu-id="f5a48-107">Most applications targeting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use SQL-DMO instead of these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider interfaces.</span></span> <span data-ttu-id="f5a48-108">SQL-DMO 是支持所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理功能的 OLE 自动化对象的集合。</span><span class="sxs-lookup"><span data-stu-id="f5a48-108">SQL-DMO is a collection of OLE Automation objects that support all the administrative functions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f5a48-109">面向多个 OLE DB 访问接口的应用程序使用多种 OLE DB 访问接口支持的通用 OLE DB 接口。</span><span class="sxs-lookup"><span data-stu-id="f5a48-109">Applications targeting multiple OLE DB providers use these generic OLE DB interfaces that are supported by the various OLE DB providers.</span></span>  
  
 <span data-ttu-id="f5a48-110">在特定于访问接口的 DBPROPSET_SQLSERVERCOLUMN 属性集中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 定义了以下属性。</span><span class="sxs-lookup"><span data-stu-id="f5a48-110">In the provider-specific property set DBPROPSET_SQLSERVERCOLUMN, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] defines the following property.</span></span>  
  
|<span data-ttu-id="f5a48-111">属性 ID</span><span class="sxs-lookup"><span data-stu-id="f5a48-111">Property ID</span></span>|<span data-ttu-id="f5a48-112">说明</span><span class="sxs-lookup"><span data-stu-id="f5a48-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f5a48-113">SSPROP_COL_COLLATIONNAME</span><span class="sxs-lookup"><span data-stu-id="f5a48-113">SSPROP_COL_COLLATIONNAME</span></span>|<span data-ttu-id="f5a48-114">键入：VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="f5a48-114">Type: VT_BSTR</span></span><br /><br /> <span data-ttu-id="f5a48-115">R/W：写</span><span class="sxs-lookup"><span data-stu-id="f5a48-115">R/W: Write</span></span><br /><br /> <span data-ttu-id="f5a48-116">默认值：Null</span><span class="sxs-lookup"><span data-stu-id="f5a48-116">Default: Null</span></span><br /><br /> <span data-ttu-id="f5a48-117">说明：该属性只能在 ITableDefinition 中使用\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5a48-117">Description: This property is used only in **ITableDefinition**.</span></span> <span data-ttu-id="f5a48-118">该属性中指定的字符串可在创建 [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="f5a48-118">The string specified in this property is used when creating a [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql)</span></span><br /><br /> <span data-ttu-id="f5a48-119">语句时使用。</span><span class="sxs-lookup"><span data-stu-id="f5a48-119">statement.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="f5a48-120">本节内容</span><span class="sxs-lookup"><span data-stu-id="f5a48-120">In This Section</span></span>  
  
-   [<span data-ttu-id="f5a48-121">创建 SQL Server 表</span><span class="sxs-lookup"><span data-stu-id="f5a48-121">Creating SQL Server Tables</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [<span data-ttu-id="f5a48-122">向 SQL Server 表添加列</span><span class="sxs-lookup"><span data-stu-id="f5a48-122">Adding a Column to a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [<span data-ttu-id="f5a48-123">从 SQL Server 表中删除列</span><span class="sxs-lookup"><span data-stu-id="f5a48-123">Removing a Column from a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [<span data-ttu-id="f5a48-124">删除 SQL Server 表</span><span class="sxs-lookup"><span data-stu-id="f5a48-124">Dropping a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [<span data-ttu-id="f5a48-125">创建 SQL Server 索引</span><span class="sxs-lookup"><span data-stu-id="f5a48-125">Creating SQL Server Indexes</span></span>](../../relational-databases/indexes/indexes.md)  
  
-   [<span data-ttu-id="f5a48-126">删除 SQL Server 索引</span><span class="sxs-lookup"><span data-stu-id="f5a48-126">Dropping a SQL Server Index</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a><span data-ttu-id="f5a48-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5a48-127">See Also</span></span>  
 <span data-ttu-id="f5a48-128">[SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="f5a48-128">[SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md) </span></span>  
 <span data-ttu-id="f5a48-129">[DROP TABLE (Transact-SQL)](/sql/t-sql/statements/drop-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5a48-129">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span></span>  
 <span data-ttu-id="f5a48-130">[CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5a48-130">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="f5a48-131">DROP INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f5a48-131">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
