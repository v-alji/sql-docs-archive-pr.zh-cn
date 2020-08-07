---
title: 删除 SQL Server 表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- SQL Server Native Client OLE DB provider, tables
- removing tables
- dropping tables
ms.assetid: b6d6c4de-43c6-473e-92aa-34ffddd58cbe
author: rothja
ms.author: jroth
ms.openlocfilehash: 4d7bea98a3afcd0022f66117b6bde2d968a866b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587782"
---
# <a name="dropping-a-sql-server-table"></a><span data-ttu-id="2d216-102">删除 SQL Server 表</span><span class="sxs-lookup"><span data-stu-id="2d216-102">Dropping a SQL Server Table</span></span>
  <span data-ttu-id="2d216-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序公开**ITableDefinition：:D roptable**函数。</span><span class="sxs-lookup"><span data-stu-id="2d216-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::DropTable** function.</span></span> <span data-ttu-id="2d216-104">这允许使用者 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 从数据库中删除表。</span><span class="sxs-lookup"><span data-stu-id="2d216-104">This allows consumers to remove a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table from a database.</span></span>  
  
 <span data-ttu-id="2d216-105">在 pTableID 参数的 uName 联合的 pwszName 成员中，使用者将表名指定为 Unicode 字符串\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2d216-105">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="2d216-106">pTableID 的 eKind 成员必须是 DBKIND_NAME   。</span><span class="sxs-lookup"><span data-stu-id="2d216-106">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d216-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d216-107">See Also</span></span>  
 [<span data-ttu-id="2d216-108">表和索引</span><span class="sxs-lookup"><span data-stu-id="2d216-108">Tables and Indexes</span></span>](tables-and-indexes.md)  
  
  
