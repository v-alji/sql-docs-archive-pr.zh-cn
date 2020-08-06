---
title: FILESTREAM 支持 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
author: rothja
ms.author: jroth
ms.openlocfilehash: 18e9a002bfb205e2c0807234550998fe48120d20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688874"
---
# <a name="filestream-support"></a><span data-ttu-id="33d51-102">FILESTREAM 支持</span><span class="sxs-lookup"><span data-stu-id="33d51-102">FILESTREAM Support</span></span>
  <span data-ttu-id="33d51-103">FILESTREAM 允许通过 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或通过直接访问 Windows 文件系统来存储和访问大型二进制值。</span><span class="sxs-lookup"><span data-stu-id="33d51-103">FILESTREAM provides a way to store and access large binary values, either through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or by direct access to the Windows file system.</span></span> <span data-ttu-id="33d51-104">大型二进制值是大于 2 GB 的值。</span><span class="sxs-lookup"><span data-stu-id="33d51-104">A large binary value is a value larger than 2 gigabytes (GB).</span></span> <span data-ttu-id="33d51-105">若要详细了解增强的 FILESTREAM 支持，请参阅 [FILESTREAM (SQL Server)](../../blob/filestream-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="33d51-105">For more information about enhanced FILESTREAM support, see [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="33d51-106">默认情况下，在打开数据库连接时，`@@TEXTSIZE` 将设置为 -1（“无限制”）。</span><span class="sxs-lookup"><span data-stu-id="33d51-106">When a database connection is opened, `@@TEXTSIZE` will be set to -1 ("unlimited"), by default.</span></span>  
  
 <span data-ttu-id="33d51-107">还可以使用 Windows 文件系统 API 访问和更新 FILESTREAM 列。</span><span class="sxs-lookup"><span data-stu-id="33d51-107">It is also possible to access and update FILESTREAM columns using Windows file system APIs.</span></span>  
  
 <span data-ttu-id="33d51-108">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="33d51-108">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="33d51-109">FILESTREAM 支持 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="33d51-109">FILESTREAM Support &#40;OLE DB&#41;</span></span>](../ole-db/filestream-support-ole-db.md)  
  
-   [<span data-ttu-id="33d51-110">FILESTREAM 支持 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="33d51-110">FILESTREAM Support &#40;ODBC&#41;</span></span>](../odbc/filestream-support-odbc.md)  
  
-   [<span data-ttu-id="33d51-111">使用 OpenSqlFilestream 访问 FILESTREAM 数据</span><span class="sxs-lookup"><span data-stu-id="33d51-111">Access FILESTREAM Data with OpenSqlFilestream</span></span>](../../blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a><span data-ttu-id="33d51-112">查询 FILESTREAM 列</span><span class="sxs-lookup"><span data-stu-id="33d51-112">Querying for FILESTREAM Columns</span></span>  
 <span data-ttu-id="33d51-113">OLE DB 中的架构行集不会报告某个列是否为 FILESTREAM 列。</span><span class="sxs-lookup"><span data-stu-id="33d51-113">Schema rowsets in OLE DB will not report whether a column is a FILESTREAM column.</span></span> <span data-ttu-id="33d51-114">OLE DB 中的 ITableDefinition 不能用于创建 FILESTREAM 列。</span><span class="sxs-lookup"><span data-stu-id="33d51-114">ITableDefinition in OLE DB cannot be used to create a FILESTREAM column.</span></span>  
  
 <span data-ttu-id="33d51-115">ODBC 中的目录函数（如 SQLColumns）不会报告某个列是否为 FILESTREAM 列。</span><span class="sxs-lookup"><span data-stu-id="33d51-115">Catalog functions such as SQLColumns in ODBC will not report whether a column is a FILESTREAM column.</span></span>  
  
 <span data-ttu-id="33d51-116">若要创建 FILESTREAM 列或检测哪些现有列是 FILESTREAM 列，可以使用 `is_filestream` [sys.databases](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)目录视图的列。</span><span class="sxs-lookup"><span data-stu-id="33d51-116">To create FILESTREAM columns or to detect which existing columns are FILESTREAM columns, you can use the `is_filestream` column of the [sys.columns](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="33d51-117">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="33d51-117">The following is an example:</span></span>  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a><span data-ttu-id="33d51-118">下级兼容性</span><span class="sxs-lookup"><span data-stu-id="33d51-118">Down-Level Compatibility</span></span>  
 <span data-ttu-id="33d51-119">如果客户端是使用附带的 Native Client 版本编译的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)] ，则 `varbinary(max)` 行为将与兼容 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="33d51-119">If your client was compiled using the version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client that was included with [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)], `varbinary(max)` behavior will be compatible with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="33d51-120">就是说，返回数据的最大大小将限制为不超过 2 GB。</span><span class="sxs-lookup"><span data-stu-id="33d51-120">That is, the maximum size of returned data will be limited to 2 GB.</span></span> <span data-ttu-id="33d51-121">对于超过 2 GB 的结果值，将发生截断，并将返回“字符串数据，右截断”警告。</span><span class="sxs-lookup"><span data-stu-id="33d51-121">For result values larger that 2 GB, truncation will occur and a "string data right truncation" warning will be returned.</span></span>  
  
 <span data-ttu-id="33d51-122">如果将数据类型兼容性设置为 80，则客户端行为将与下级客户端行为一致。</span><span class="sxs-lookup"><span data-stu-id="33d51-122">When data-type compatibility is set to 80, client behavior will be consistent with down-level client behavior.</span></span>  
  
 <span data-ttu-id="33d51-123">对于使用 SQLOLEDB 的客户端或在 Native Client 之前发布的其他提供程序 [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] ， `varbinary(max)` 将映射到映像。</span><span class="sxs-lookup"><span data-stu-id="33d51-123">For clients that use SQLOLEDB or other providers that were released before the [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] Native Client, `varbinary(max)` will be mapped to image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d51-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33d51-124">See Also</span></span>  
 [<span data-ttu-id="33d51-125">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="33d51-125">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
