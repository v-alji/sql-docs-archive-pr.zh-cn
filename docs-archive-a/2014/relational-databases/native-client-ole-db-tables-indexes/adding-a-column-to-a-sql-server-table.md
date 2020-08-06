---
title: 向 SQL Server 表添加列 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 97aa2656ccde662a34e1dd80fd662b22f601d4ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692879"
---
# <a name="adding-a-column-to-a-sql-server-table"></a><span data-ttu-id="924df-102">向 SQL Server 表添加列</span><span class="sxs-lookup"><span data-stu-id="924df-102">Adding a Column to a SQL Server Table</span></span>
  <span data-ttu-id="924df-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序公开**ITableDefinition：： AddColumn**函数。</span><span class="sxs-lookup"><span data-stu-id="924df-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::AddColumn** function.</span></span> <span data-ttu-id="924df-104">利用此函数，使用者便可向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中添加列。</span><span class="sxs-lookup"><span data-stu-id="924df-104">This allows consumers to add a column to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="924df-105">向表中添加列时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供方将受到如下约束：</span><span class="sxs-lookup"><span data-stu-id="924df-105">When you add a column to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer is constrained as follows:</span></span>  
  
-   <span data-ttu-id="924df-106">如果 DBPROP_COL_AUTOINCREMENT 为 VARIANT_TRUE，则 DBPROP_COL_NULLABLE 必须为 VARIANT_FALSE。</span><span class="sxs-lookup"><span data-stu-id="924df-106">If DBPROP_COL_AUTOINCREMENT is VARIANT_TRUE, DBPROP_COL_NULLABLE must be VARIANT_FALSE.</span></span>  
  
-   <span data-ttu-id="924df-107">如果相应列是使用  timestamp[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \*\*\*\* 数据类型定义的，则 DBPROP_COL_NULLABLE 必须为 VARIANT_FALSE。</span><span class="sxs-lookup"><span data-stu-id="924df-107">If the column is defined by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** data type, DBPROP_COL_NULLABLE must be VARIANT_FALSE.</span></span>  
  
-   <span data-ttu-id="924df-108">对于任何其他列定义，DBPROP_COL_NULLABLE 都必须为 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="924df-108">For any other column definition, DBPROP_COL_NULLABLE must be VARIANT_TRUE.</span></span>  
  
 <span data-ttu-id="924df-109">在 pTableID 参数的 uName 联合的 pwszName 成员中，使用者将表名指定为 Unicode 字符串\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="924df-109">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="924df-110">pTableID 的 eKind 成员必须是 DBKIND_NAME\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="924df-110">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="924df-111">在 uName 联合（位于 DBCOLUMNDESC 参数 pColumnDesc 的 dbcid 成员中）的 pwszName 成员中，将新列的名称指定为 Unicode 字符串\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="924df-111">The new column name is specified as a Unicode character string in the *pwszName* member of the *uName* union in the *dbcid* member of the DBCOLUMNDESC parameter *pColumnDesc*.</span></span> <span data-ttu-id="924df-112">eKind 成员必须为 DBKIND_NAME\*\*。</span><span class="sxs-lookup"><span data-stu-id="924df-112">The *eKind* member must be DBKIND_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="924df-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="924df-113">See Also</span></span>  
 <span data-ttu-id="924df-114">[表和索引](tables-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="924df-114">[Tables and Indexes](tables-and-indexes.md) </span></span>  
 [<span data-ttu-id="924df-115">ALTER TABLE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="924df-115">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
