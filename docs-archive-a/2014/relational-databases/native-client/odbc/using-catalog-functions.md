---
title: 使用目录函数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQLLinkedCatalogs function
- SQL Server Native Client ODBC driver, catalog functions
- SQLLinkedServers function
- catalog functions [ODBC]
- functions [ODBC]
ms.assetid: 7773fb2e-06b5-4c4b-88e9-0ad9132ad273
author: rothja
ms.author: jroth
ms.openlocfilehash: 6cac35e658343f606c1953f265c752335c70d81f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590177"
---
# <a name="using-catalog-functions"></a><span data-ttu-id="4b581-102">使用目录函数</span><span class="sxs-lookup"><span data-stu-id="4b581-102">Using Catalog Functions</span></span>
  <span data-ttu-id="4b581-103">所有数据库都具有一个包含该数据中存储的数据的结构。</span><span class="sxs-lookup"><span data-stu-id="4b581-103">All databases have a structure containing the data stored in the database.</span></span> <span data-ttu-id="4b581-104">此结构的定义以及权限等其他信息存储在目录（作为一组系统表实现）中，也称为数据字典。</span><span class="sxs-lookup"><span data-stu-id="4b581-104">A definition of this structure, along with other information such as permissions, is stored in a catalog (implemented as a set of system tables), also known as a data dictionary.</span></span>  
  
 <span data-ttu-id="4b581-105">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序，应用程序可以通过调用 ODBC 目录函数来确定数据库结构。</span><span class="sxs-lookup"><span data-stu-id="4b581-105">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver enables an application to determine the database structure through calls to ODBC catalog functions.</span></span> <span data-ttu-id="4b581-106">目录函数返回结果集中的信息，这些函数是使用目录存储过程实现的，用于查询该目录中的系统表。</span><span class="sxs-lookup"><span data-stu-id="4b581-106">Catalog functions return information in result sets and are implemented using catalog stored procedures to query the system tables in the catalog.</span></span> <span data-ttu-id="4b581-107">例如，应用程序可以请求包含系统上所有表的相关信息的结果集或包含特定表中的所有列的相关信息的结果集。</span><span class="sxs-lookup"><span data-stu-id="4b581-107">For example, an application might request a result set containing information about all the tables on the system or all the columns in a particular table.</span></span> <span data-ttu-id="4b581-108">标准 ODBC 目录函数用于获取连接应用程序的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的目录信息。</span><span class="sxs-lookup"><span data-stu-id="4b581-108">The standard ODBC catalog functions are used to get catalog information from the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which the application connected.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="4b581-109">支持通过一个查询访问多个异类 OLE DB 数据源的数据的分布式查询。</span><span class="sxs-lookup"><span data-stu-id="4b581-109">supports distributed queries in which data from multiple, heterogeneous OLE DB data sources is accessed in a single query.</span></span> <span data-ttu-id="4b581-110">访问远程 OLE DB 数据源的一种方法是将数据源定义为链接服务器。</span><span class="sxs-lookup"><span data-stu-id="4b581-110">One of the methods of accessing a remote OLE DB data source is to define the data source as a linked server.</span></span> <span data-ttu-id="4b581-111">可以通过使用[sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="4b581-111">This can be done by using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span> <span data-ttu-id="4b581-112">定义链接服务器后，使用由四个部分组成的名称可以在 Transact-SQL 语句中引用该服务器上的对象：</span><span class="sxs-lookup"><span data-stu-id="4b581-112">After the linked server has been defined, objects in that server can be referenced in Transact-SQL statements by using a four-part name:</span></span>  
  
 <span data-ttu-id="4b581-113">*linked_server_name。 object_name*。</span><span class="sxs-lookup"><span data-stu-id="4b581-113">*linked_server_name.catalog.schema.object_name*.</span></span>  
  
 <span data-ttu-id="4b581-114">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序支持两个有助于获取链接服务器的目录信息的特定于驱动程序的函数：</span><span class="sxs-lookup"><span data-stu-id="4b581-114">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports two driver-specific functions that help get catalog information from linked servers:</span></span>  
  
-   <span data-ttu-id="4b581-115">**SQLLinkedServers**</span><span class="sxs-lookup"><span data-stu-id="4b581-115">**SQLLinkedServers**</span></span>  
  
     <span data-ttu-id="4b581-116">返回定义到本地服务器的链接服务器列表。</span><span class="sxs-lookup"><span data-stu-id="4b581-116">Returns a list of the linked servers defined to the local server.</span></span>  
  
-   <span data-ttu-id="4b581-117">**SQLLinkedCatalogs**</span><span class="sxs-lookup"><span data-stu-id="4b581-117">**SQLLinkedCatalogs**</span></span>  
  
     <span data-ttu-id="4b581-118">返回链接服务器包含的目录的列表。</span><span class="sxs-lookup"><span data-stu-id="4b581-118">Returns a list of the catalogs contained in a linked server.</span></span>  
  
 <span data-ttu-id="4b581-119">使用链接服务器名称和目录名称后， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序支持通过使用由两部分组成的名称来获取目录中的信息_linked_server_name_**。** 以下 ODBC 目录函数的*CatalogName* _目录_：</span><span class="sxs-lookup"><span data-stu-id="4b581-119">After you have a linked server name and a catalog name, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports getting information from the catalog by using a two-part name of _linked_server_name_**.**_catalog_ for *CatalogName* on the following ODBC catalog functions:</span></span>  
  
-   <span data-ttu-id="4b581-120">**SQLColumnPrivileges**</span><span class="sxs-lookup"><span data-stu-id="4b581-120">**SQLColumnPrivileges**</span></span>  
  
-   <span data-ttu-id="4b581-121">**SQLColumns**</span><span class="sxs-lookup"><span data-stu-id="4b581-121">**SQLColumns**</span></span>  
  
-   <span data-ttu-id="4b581-122">**SQLPrimaryKeys**</span><span class="sxs-lookup"><span data-stu-id="4b581-122">**SQLPrimaryKeys**</span></span>  
  
-   <span data-ttu-id="4b581-123">**SQLStatistics**</span><span class="sxs-lookup"><span data-stu-id="4b581-123">**SQLStatistics**</span></span>  
  
-   <span data-ttu-id="4b581-124">**SQLTablePrivileges**</span><span class="sxs-lookup"><span data-stu-id="4b581-124">**SQLTablePrivileges**</span></span>  
  
-   <span data-ttu-id="4b581-125">**SQLTables**</span><span class="sxs-lookup"><span data-stu-id="4b581-125">**SQLTables**</span></span>  
  
 <span data-ttu-id="4b581-126">由两部分组成的_linked_server_name_**。**[SQLForeignKeys](../../native-client-odbc-api/sqlforeignkeys.md)上的*FKCatalogName*和*PKCatalogName*也支持_目录_。</span><span class="sxs-lookup"><span data-stu-id="4b581-126">The two-part _linked_server_name_**.**_catalog_ is also supported for *FKCatalogName* and *PKCatalogName* on [SQLForeignKeys](../../native-client-odbc-api/sqlforeignkeys.md).</span></span>  
  
 <span data-ttu-id="4b581-127">使用 SQLLinkedServers 和 SQLLinkedCatalogs 需要以下文件：</span><span class="sxs-lookup"><span data-stu-id="4b581-127">Using SQLLinkedServers and SQLLinkedCatalogs requires the following files:</span></span>  
  
-   <span data-ttu-id="4b581-128">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="4b581-128">sqlncli.h</span></span>  
  
     <span data-ttu-id="4b581-129">包括用于链接服务器目录函数的函数原型和常量定义。</span><span class="sxs-lookup"><span data-stu-id="4b581-129">Includes function prototypes and constant definitions for the linked server catalog functions.</span></span> <span data-ttu-id="4b581-130">必须在 ODBC 应用程序中包括 sqlncli.h，并且在编译应用程序时必须将其放在 include 路径中。</span><span class="sxs-lookup"><span data-stu-id="4b581-130">sqlncli.h must be included in the ODBC application and must be in the include path when the application is compiled.</span></span>  
  
-   <span data-ttu-id="4b581-131">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="4b581-131">sqlncli11.lib</span></span>  
  
     <span data-ttu-id="4b581-132">必须放在链接器的库路径中，并将其指定为要链接的文件。</span><span class="sxs-lookup"><span data-stu-id="4b581-132">Must be in the library path of the linker and specified as a file to be linked.</span></span> <span data-ttu-id="4b581-133">sqlncli11.lib 随 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序一起分发。</span><span class="sxs-lookup"><span data-stu-id="4b581-133">sqlncli11.lib is distributed with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
-   <span data-ttu-id="4b581-134">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="4b581-134">sqlncli11.dll</span></span>  
  
     <span data-ttu-id="4b581-135">在执行时必须存在。</span><span class="sxs-lookup"><span data-stu-id="4b581-135">Must be present at execution time.</span></span> <span data-ttu-id="4b581-136">sqlncli11.dll 随 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序一起分发。</span><span class="sxs-lookup"><span data-stu-id="4b581-136">sqlncli11.dll is distributed with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b581-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b581-137">See Also</span></span>  
 <span data-ttu-id="4b581-138">[SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="4b581-138">[SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md) </span></span>  
 <span data-ttu-id="4b581-139">[SQLColumnPrivileges](../../native-client-odbc-api/sqlcolumnprivileges.md) </span><span class="sxs-lookup"><span data-stu-id="4b581-139">[SQLColumnPrivileges](../../native-client-odbc-api/sqlcolumnprivileges.md) </span></span>  
 <span data-ttu-id="4b581-140">[SQLColumns](../../native-client-odbc-api/sqlcolumns.md) </span><span class="sxs-lookup"><span data-stu-id="4b581-140">[SQLColumns](../../native-client-odbc-api/sqlcolumns.md) </span></span>  
 <span data-ttu-id="4b581-141">[SQLPrimaryKeys](../../native-client-odbc-api/sqlprimarykeys.md) </span><span class="sxs-lookup"><span data-stu-id="4b581-141">[SQLPrimaryKeys](../../native-client-odbc-api/sqlprimarykeys.md) </span></span>  
 <span data-ttu-id="4b581-142">[SQLTablePrivileges](../../native-client-odbc-api/sqltableprivileges.md) </span><span class="sxs-lookup"><span data-stu-id="4b581-142">[SQLTablePrivileges](../../native-client-odbc-api/sqltableprivileges.md) </span></span>  
 <span data-ttu-id="4b581-143">[SQLTables](../../native-client-odbc-api/sqltables.md) </span><span class="sxs-lookup"><span data-stu-id="4b581-143">[SQLTables](../../native-client-odbc-api/sqltables.md) </span></span>  
 [<span data-ttu-id="4b581-144">SQLStatistics</span><span class="sxs-lookup"><span data-stu-id="4b581-144">SQLStatistics</span></span>](../../statistics/statistics.md)  
  
  
