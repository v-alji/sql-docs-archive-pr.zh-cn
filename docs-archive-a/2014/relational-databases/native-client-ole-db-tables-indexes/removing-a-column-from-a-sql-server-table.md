---
title: 从 SQL Server 表中删除列 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- SQL Server Native Client OLE DB provider, columns
ms.assetid: 210811b7-cbd6-421e-bc6e-df9482236768
author: rothja
ms.author: jroth
ms.openlocfilehash: 8f40c466910aae7e0d349cd4a65ab265282bc8eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587781"
---
# <a name="removing-a-column-from-a-sql-server-table"></a><span data-ttu-id="bb6b9-102">从 SQL Server 表中删除列</span><span class="sxs-lookup"><span data-stu-id="bb6b9-102">Removing a Column from a SQL Server Table</span></span>
  <span data-ttu-id="bb6b9-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序公开**ITableDefinition：:D ropcolumn**函数。</span><span class="sxs-lookup"><span data-stu-id="bb6b9-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::DropColumn** function.</span></span> <span data-ttu-id="bb6b9-104">这允许使用者从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中删除某一列。</span><span class="sxs-lookup"><span data-stu-id="bb6b9-104">This allows consumers to remove a column from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="bb6b9-105">在 pTableID 参数的 uName 联合的 pwszName 成员中，使用者将表名指定为 Unicode 字符串\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb6b9-105">Consumers specify the table name as a Unicode character string in the *pwszName*member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="bb6b9-106">pTableID 的 eKind 成员必须是 DBKIND_NAME\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb6b9-106">The *eKind*member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="bb6b9-107">使用者在 pColumnID\*\* 参数的 uName\*\* 联合的 pwszName\*\* 成员中指明列名。</span><span class="sxs-lookup"><span data-stu-id="bb6b9-107">The consumer indicates a column name in the *pwszName*member of the *uName* union in the *pColumnID* parameter.</span></span> <span data-ttu-id="bb6b9-108">该列名称为 Unicode 字符串。</span><span class="sxs-lookup"><span data-stu-id="bb6b9-108">The column name is a Unicode character string.</span></span> <span data-ttu-id="bb6b9-109">pColumnID 的 eKind 成员必须是 DBKIND_NAME\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb6b9-109">The *eKind* member of *pColumnID* must be DBKIND_NAME.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb6b9-110">示例</span><span class="sxs-lookup"><span data-stu-id="bb6b9-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="bb6b9-111">代码</span><span class="sxs-lookup"><span data-stu-id="bb6b9-111">Code</span></span>  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb6b9-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb6b9-112">See Also</span></span>  
 [<span data-ttu-id="bb6b9-113">表和索引</span><span class="sxs-lookup"><span data-stu-id="bb6b9-113">Tables and Indexes</span></span>](tables-and-indexes.md)  
  
  
