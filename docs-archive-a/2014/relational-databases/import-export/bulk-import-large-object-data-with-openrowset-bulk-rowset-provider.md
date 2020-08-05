---
title: 使用 OPENROWSET 大容量行集提供程序 (SQL Server) 大容量导入大型对象数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- SINGLE_NCLOB option
- bulk rowset providers [SQL Server]
- bulk importing [SQL Server], data formats
- OPENROWSET function, bulk importing large data
- SINGLE_CLOB option
- data formats [SQL Server], large-object data
- large data, bulk imports
- SINGLE_BLOB option
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0f43aa2fa5e7f7ef0b2c8f1f6e5e6ff28e02f9f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581190"
---
# <a name="bulk-import-large-object-data-by-using-the-openrowset-bulk-rowset-provider-sql-server"></a><span data-ttu-id="3a716-102">通过使用 OPENROWSET BULK 行集提供程序大容量导入大型对象数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3a716-102">Bulk Import Large-Object Data by using the OPENROWSET Bulk Rowset Provider (SQL Server)</span></span>
  <span data-ttu-id="3a716-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET 大容量行集提供程序使您可以将数据文件作为大型对象数据大容量导入。</span><span class="sxs-lookup"><span data-stu-id="3a716-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET Bulk Rowset Provider enables you to bulk import a data file as large-object data.</span></span>  
  
 <span data-ttu-id="3a716-104">OPENROWSET 大容量行集提供程序支持的大型对象数据类型为 **varbinary**(max) 或 **image**、 **varchar**(max) 或 **text**以及 **nvarchar**(max) 或 **ntext**。</span><span class="sxs-lookup"><span data-stu-id="3a716-104">The large-object data types supported by OPENROWSET Bulk Rowset Provider are **varbinary**(max) or **image**, **varchar**(max) or **text**, and **nvarchar**(max) or **ntext**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a716-105">不推荐使用 **image**、 **text** 和 **ntext** 数据类型。</span><span class="sxs-lookup"><span data-stu-id="3a716-105">The **image**, **text** and **ntext** data types are deprecated.</span></span>  
  
 <span data-ttu-id="3a716-106">OPENROWSET BULK 子句支持通过三个选项以单行或单列行集导入数据文件的内容。</span><span class="sxs-lookup"><span data-stu-id="3a716-106">The OPENROWSET BULK clause supports three options for importing the contents of a data file as a single-row, single-column rowset.</span></span> <span data-ttu-id="3a716-107">您可以指定其中一个大型对象选项，而不是使用格式化文件。</span><span class="sxs-lookup"><span data-stu-id="3a716-107">You can specify one of these large-object options instead of using a format file.</span></span> <span data-ttu-id="3a716-108">这些选项如下所示：</span><span class="sxs-lookup"><span data-stu-id="3a716-108">These options are as follows:</span></span>  
  
 <span data-ttu-id="3a716-109">SINGLE_BLOB</span><span class="sxs-lookup"><span data-stu-id="3a716-109">SINGLE_BLOB</span></span>  
 <span data-ttu-id="3a716-110">以单行读取 *data_file* 的内容，以 **varbinary(max)** 类型的单列行集返回内容。</span><span class="sxs-lookup"><span data-stu-id="3a716-110">Reads the contents of *data_file* as a single-row, returns the contents as a single-column rowset of type **varbinary(max)**.</span></span>  
  
 <span data-ttu-id="3a716-111">SINGLE_CLOB</span><span class="sxs-lookup"><span data-stu-id="3a716-111">SINGLE_CLOB</span></span>  
 <span data-ttu-id="3a716-112">以字符读取指定数据文件的内容，以 **varchar(max)** 类型的单行、单列行集返回内容，使用的是当前数据库的排序规则，例如文本或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word 文档。</span><span class="sxs-lookup"><span data-stu-id="3a716-112">Reads the contents of the specified data file as characters, returns the contents as a single-row, single-column rowset of type **varchar(max)**, using the collation of the current database; such as a text or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word document.</span></span>  
  
 <span data-ttu-id="3a716-113">SINGLE_NCLOB</span><span class="sxs-lookup"><span data-stu-id="3a716-113">SINGLE_NCLOB</span></span>  
 <span data-ttu-id="3a716-114">以 Unicode 读取指定数据文件的内容，以 **nvarchar(max)** 类型的单行、单列行集返回内容，并使用当前数据库的排序规则。</span><span class="sxs-lookup"><span data-stu-id="3a716-114">Reads the contents of the specified data file as Unicode, returns the contents as a single-row, single-column rowset of type **nvarchar(max)**, using the collation of the current database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a716-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a716-115">See Also</span></span>  
 <span data-ttu-id="3a716-116">[使用 BULK INSERT 或 OPENROWSET (BULK...) 导入批量数据 (SQL Server)](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3a716-116">[Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span></span>  
 <span data-ttu-id="3a716-117">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3a716-117">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="3a716-118">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3a716-118">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="3a716-119">[在批量导入期间保留 Null 或使用默认值 (SQL Server)](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3a716-119">[Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md) </span></span>  
 <span data-ttu-id="3a716-120">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="3a716-120">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="3a716-121">BULK INSERT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3a716-121">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
  
