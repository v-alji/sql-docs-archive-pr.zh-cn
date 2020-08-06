---
title: 架构行集中的分布式查询支持 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
author: rothja
ms.author: jroth
ms.openlocfilehash: 48b57bbf40590f8ad5c049268f25fe66d2f94357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578846"
---
# <a name="distributed-query-support-in-schema-rowsets"></a><span data-ttu-id="2366c-102">架构行集中的分布式查询支持</span><span class="sxs-lookup"><span data-stu-id="2366c-102">Distributed Query Support in Schema Rowsets</span></span>
  <span data-ttu-id="2366c-103">为了支持 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分布式查询， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider **IDBSchemaRowset**接口将返回链接服务器上的元数据。</span><span class="sxs-lookup"><span data-stu-id="2366c-103">To support [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distributed queries, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider **IDBSchemaRowset** interface returns metadata on linked servers.</span></span>  
  
 <span data-ttu-id="2366c-104">如果 DBPROPSET_SQLSERVERSESSION 属性 SSPROP_QUOTEDCATALOGNAMES 是 VARIANT_TRUE，则可以为目录名称指定带引号的标识符（例如 "my.catalog"）。</span><span class="sxs-lookup"><span data-stu-id="2366c-104">If the DBPROPSET_SQLSERVERSESSION property SSPROP_QUOTEDCATALOGNAMES is VARIANT_TRUE, a quoted identifier can be specified for the catalog name (for example "my.catalog").</span></span> <span data-ttu-id="2366c-105">当通过目录限制架构行集输出时， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序将识别包含链接服务器和目录名称的由两部分组成的名称。</span><span class="sxs-lookup"><span data-stu-id="2366c-105">When restricting schema rowset output by catalog, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes a two-part name containing the linked server and catalog name.</span></span> <span data-ttu-id="2366c-106">对于下表中的架构行集，将两部分组成的目录名称指定为_linked_server_**。**_目录_将输出限制为命名链接服务器的适用目录。</span><span class="sxs-lookup"><span data-stu-id="2366c-106">For the schema rowsets in the table below, specifying a two-part catalog name as _linked_server_**.**_catalog_ restricts output to the applicable catalog of the named linked server.</span></span>  
  
|<span data-ttu-id="2366c-107">架构行集</span><span class="sxs-lookup"><span data-stu-id="2366c-107">Schema rowset</span></span>|<span data-ttu-id="2366c-108">目录限制</span><span class="sxs-lookup"><span data-stu-id="2366c-108">Catalog restriction</span></span>|  
|-------------------|-------------------------|  
|<span data-ttu-id="2366c-109">DBSCHEMA_CATALOGS</span><span class="sxs-lookup"><span data-stu-id="2366c-109">DBSCHEMA_CATALOGS</span></span>|<span data-ttu-id="2366c-110">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="2366c-110">CATALOG_NAME</span></span>|  
|<span data-ttu-id="2366c-111">DBSCHEMA_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="2366c-111">DBSCHEMA_COLUMNS</span></span>|<span data-ttu-id="2366c-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2366c-112">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="2366c-113">DBSCHEMA_PRIMARY_KEYS</span><span class="sxs-lookup"><span data-stu-id="2366c-113">DBSCHEMA_PRIMARY_KEYS</span></span>|<span data-ttu-id="2366c-114">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2366c-114">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="2366c-115">DBSCHEMA_TABLES</span><span class="sxs-lookup"><span data-stu-id="2366c-115">DBSCHEMA_TABLES</span></span>|<span data-ttu-id="2366c-116">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2366c-116">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="2366c-117">DBSCHEMA_FOREIGN_KEYS</span><span class="sxs-lookup"><span data-stu-id="2366c-117">DBSCHEMA_FOREIGN_KEYS</span></span>|<span data-ttu-id="2366c-118">PK_TABLE_CATALOG FK_TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2366c-118">PK_TABLE_CATALOG FK_TABLE_CATALOG</span></span>|  
|<span data-ttu-id="2366c-119">DBSCHEMA_INDEXES</span><span class="sxs-lookup"><span data-stu-id="2366c-119">DBSCHEMA_INDEXES</span></span>|<span data-ttu-id="2366c-120">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2366c-120">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="2366c-121">DBSCHEMA_COLUMN_PRIVILEGES</span><span class="sxs-lookup"><span data-stu-id="2366c-121">DBSCHEMA_COLUMN_PRIVILEGES</span></span>|<span data-ttu-id="2366c-122">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2366c-122">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="2366c-123">DBSCHEMA_TABLE_PRIVILEGES</span><span class="sxs-lookup"><span data-stu-id="2366c-123">DBSCHEMA_TABLE_PRIVILEGES</span></span>|<span data-ttu-id="2366c-124">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2366c-124">TABLE_CATALOG</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="2366c-125">若要将架构行集限制为来自链接服务器的所有目录，请使用语法 linked_server（其中，句点分隔符是名称规范的一部分）\*\*。</span><span class="sxs-lookup"><span data-stu-id="2366c-125">To restrict a schema rowset to all catalogs from a linked server, use the syntax *linked_server* (where the period separator is part of the name specification).</span></span> <span data-ttu-id="2366c-126">该语法等同于将目录名称限制指定为 NULL，当链接服务器指示有不支持目录的数据源时也使用此语法。</span><span class="sxs-lookup"><span data-stu-id="2366c-126">This syntax is equivalent to specifying NULL for the catalog name restriction and is also used when the linked server indicates a data source that does not support catalogs.</span></span>  
  
 <span data-ttu-id="2366c-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序定义架构行集 LINKEDSERVERS，并返回注册为链接服务器的 OLE DB 数据源的列表。</span><span class="sxs-lookup"><span data-stu-id="2366c-127">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the schema rowset LINKEDSERVERS, returning a list of OLE DB data sources registered as linked servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2366c-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2366c-128">See Also</span></span>  
 <span data-ttu-id="2366c-129">[架构行集支持 &#40;OLE DB&#41;](schema-rowset-support-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="2366c-129">[Schema Rowset Support &#40;OLE DB&#41;](schema-rowset-support-ole-db.md) </span></span>  
 [<span data-ttu-id="2366c-130">LINKEDSERVERS 行集 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="2366c-130">LINKEDSERVERS Rowset &#40;OLE DB&#41;</span></span>](schema-rowsets-linkedservers-rowset.md)  
  
  
