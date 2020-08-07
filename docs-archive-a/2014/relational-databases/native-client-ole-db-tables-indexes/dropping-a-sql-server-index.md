---
title: 删除 SQL Server 索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
author: rothja
ms.author: jroth
ms.openlocfilehash: 1267cc92645ff8b28757ad2d266e58917fcb4b28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587783"
---
# <a name="dropping-a-sql-server-index"></a><span data-ttu-id="9b1dc-102">删除 SQL Server 索引</span><span class="sxs-lookup"><span data-stu-id="9b1dc-102">Dropping a SQL Server Index</span></span>
  <span data-ttu-id="9b1dc-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序公开**IIndexDefinition：:D ropindex**函数。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition::DropIndex** function.</span></span> <span data-ttu-id="9b1dc-104">这允许使用者从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中删除某一索引。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-104">This allows consumers to remove an index from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="9b1dc-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序将一些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 主键和 UNIQUE 约束公开为索引。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PRIMARY KEY and UNIQUE constraints as indexes.</span></span> <span data-ttu-id="9b1dc-106">表所有者、数据库所有者或某些管理角色成员可以修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表，以及删除约束。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-106">The table owner, database owner, and some administrative role members can modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, dropping a constraint.</span></span> <span data-ttu-id="9b1dc-107">默认情况下，只有表所有者才能删除现有索引。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-107">By default, only the table owner can drop an existing index.</span></span> <span data-ttu-id="9b1dc-108">因此，DropIndex 成功或失败不仅取决于应用程序用户的访问权限，而且取决于指示的索引的类型\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-108">Therefore, **DropIndex** success or failure depends not only on the application user's access rights but also on the type of index indicated.</span></span>  
  
 <span data-ttu-id="9b1dc-109">在 pTableID 参数的 uName 联合的 pwszName 成员中，使用者将表名指定为 Unicode 字符串\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-109">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="9b1dc-110">pTableID 的 eKind 成员必须是 DBKIND_NAME\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-110">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="9b1dc-111">在 pIndexID 参数的 uName 联合的 pwszName成员中，使用者将索引名指定为 Unicode 字符串\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-111">Consumers specify the index name as a Unicode character string in the *pwszName* member of the *uName* union in the *pIndexID* parameter.</span></span> <span data-ttu-id="9b1dc-112">pIndexID 的 eKind 成员必须是 DBKIND_NAME\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-112">The *eKind* member of *pIndexID* must be DBKIND_NAME.</span></span> <span data-ttu-id="9b1dc-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]当*pIndexID*为 null 时，Native Client OLE DB 提供程序不支持删除表上的所有索引的 OLE DB 功能。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support the OLE DB feature of dropping all indexes on a table when *pIndexID* is null.</span></span> <span data-ttu-id="9b1dc-114">如果 pIndexID 为 Null，则返回 E_INVALIDARG\*\*。</span><span class="sxs-lookup"><span data-stu-id="9b1dc-114">If *pIndexID* is null, E_INVALIDARG is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b1dc-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b1dc-115">See Also</span></span>  
 <span data-ttu-id="9b1dc-116">[表和索引](tables-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="9b1dc-116">[Tables and Indexes](tables-and-indexes.md) </span></span>  
 <span data-ttu-id="9b1dc-117">[ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9b1dc-117">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="9b1dc-118">DROP INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9b1dc-118">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
