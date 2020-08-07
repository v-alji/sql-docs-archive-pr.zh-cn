---
title: 配置和管理搜索筛选器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e9a57c95226a9b277cfb718b40b5d0525b1f8eb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589489"
---
# <a name="configure-and-manage-filters-for-search"></a><span data-ttu-id="91294-102">配置和管理搜索筛选器</span><span class="sxs-lookup"><span data-stu-id="91294-102">Configure and Manage Filters for Search</span></span>
  <span data-ttu-id="91294-103">为 `varbinary`、`varbinary(max)`、`image` 或 `xml` 数据类型的文档建立索引需要进行额外处理。</span><span class="sxs-lookup"><span data-stu-id="91294-103">Indexing documents in an `varbinary`, `varbinary(max)`, `image`, or `xml` data type column requires extra processing.</span></span> <span data-ttu-id="91294-104">该处理必须由筛选器执行。</span><span class="sxs-lookup"><span data-stu-id="91294-104">This processing must be performed by a filter.</span></span> <span data-ttu-id="91294-105">筛选器从文档中提取文本信息（去除格式）。</span><span class="sxs-lookup"><span data-stu-id="91294-105">The filter extracts the textual information from the document (removing the formatting).</span></span> <span data-ttu-id="91294-106">然后，筛选器将这些文本发送至与表列相关联的语言的断字器组件。</span><span class="sxs-lookup"><span data-stu-id="91294-106">The filter then sends the text to the word-breaker component for the language associated with the table column.</span></span>  
  
 <span data-ttu-id="91294-107">给定筛选器特定于给定文档类型（.doc、.pdf、.xls、.xml 等等）。</span><span class="sxs-lookup"><span data-stu-id="91294-107">A given filter is specific to a given document type (.doc, .pdf, .xls, .xml, and so forth).</span></span> <span data-ttu-id="91294-108">这些筛选器实现 IFilter 接口。</span><span class="sxs-lookup"><span data-stu-id="91294-108">These filters implement the IFilter interface.</span></span> <span data-ttu-id="91294-109">有关这些文档类型的详细信息，请查询 [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="91294-109">For more information about these document types, query the [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="91294-110">二进制文档可以存储在单个 `varbinary(max)` 或 `image` 列中。</span><span class="sxs-lookup"><span data-stu-id="91294-110">Binary documents can be stored in a single `varbinary(max)` or `image` column.</span></span> <span data-ttu-id="91294-111">对于每个文档， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 根据文件扩展名来选择正确的筛选器。</span><span class="sxs-lookup"><span data-stu-id="91294-111">For each document, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] chooses the correct filter based on the file extension.</span></span> <span data-ttu-id="91294-112">由于文件存储在或列中时，文件扩展名不可见 `varbinary(max)` `image` ，因此文件扩展名 ( .doc、.xls、.pdf 等) 必须存储在表中单独的列中，称为 "类型列"。</span><span class="sxs-lookup"><span data-stu-id="91294-112">Because the file extension is not visible when the file is stored in a `varbinary(max)` or `image` column, the file extension (.doc, .xls,  .pdf, and so forth) must be stored in a separate column in the table, called a type column.</span></span> <span data-ttu-id="91294-113">此类型列可以是任意基于字符的数据类型，并且包含文档文件扩展名，例如 .doc 表示 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word 文档。</span><span class="sxs-lookup"><span data-stu-id="91294-113">This type column can be of any character-based data type and contains the document file extension, such as .doc for a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word document.</span></span> <span data-ttu-id="91294-114">在的**document**表中 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] ， **document**列的类型为 `varbinary(max)` ，类型列**FileExtension**的类型为 `nvarchar(8)` 。</span><span class="sxs-lookup"><span data-stu-id="91294-114">In the **Document** table in [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], the **Document** column is of type `varbinary(max)`, and the type column, **FileExtension**, is of type `nvarchar(8)`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91294-115">筛选器有可能能够处理嵌入到父对象中的对象，具体取决于筛选器的实现方式。</span><span class="sxs-lookup"><span data-stu-id="91294-115">A filter might be able to handle objects embedded in the parent object, depending on its implementation.</span></span> <span data-ttu-id="91294-116">不过， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不会将筛选器配置为跟踪指向其他对象的链接。</span><span class="sxs-lookup"><span data-stu-id="91294-116">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not configure filters to follow links to other objects.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="91294-117">安装它自己的 XML 和 HTML 筛选器。</span><span class="sxs-lookup"><span data-stu-id="91294-117">installs its own XML and HTML filters.</span></span> <span data-ttu-id="91294-118">此外，已在操作系统上安装的任何针对 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 专有格式（.doc、.xdoc、.ppt 等）的筛选器也由  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]加载。</span><span class="sxs-lookup"><span data-stu-id="91294-118">In addition, any filters for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] proprietary formats (.doc, .xdoc, .ppt and so on) that are already installed on the operating system are also loaded by  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="91294-119">若要标识当前加载到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的实例上的筛选器，请使用 [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) 存储过程，如下所示：</span><span class="sxs-lookup"><span data-stu-id="91294-119">To identify the filters that are currently loaded on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], use the [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) stored procedure, as follows:</span></span>  
  
```  
EXEC sp_help_fulltext_system_components 'filter';   
```  
  
 <span data-ttu-id="91294-120">但是，在您可以使用针对非 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 格式的筛选器之前，您必须将它们手动加载到服务器实例中。</span><span class="sxs-lookup"><span data-stu-id="91294-120">Before you can use filters for non [!INCLUDE[msCoName](../../../includes/msconame-md.md)] formats, however, you must manually load them into the server instance.</span></span> <span data-ttu-id="91294-121">有关安装其他筛选器的信息，请参阅 [查看或更改注册的筛选器和断字符](view-or-change-registered-filters-and-word-breakers.md)。</span><span class="sxs-lookup"><span data-stu-id="91294-121">For information about installing additional filters, see [View or Change Registered Filters and Word Breakers](view-or-change-registered-filters-and-word-breakers.md).</span></span>  
  
 <span data-ttu-id="91294-122">**查看现有全文索引中的类型列**</span><span class="sxs-lookup"><span data-stu-id="91294-122">**To view the type column in an existing full-text index**</span></span>  
  
-   [<span data-ttu-id="91294-123">sys.fulltext_index_columns (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="91294-123">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="91294-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91294-124">See Also</span></span>  
 <span data-ttu-id="91294-125">[sys. fulltext_index_columns &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91294-125">[sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) </span></span>  
 [<span data-ttu-id="91294-126">FILESTREAM 与其他 SQL Server 功能的兼容性</span><span class="sxs-lookup"><span data-stu-id="91294-126">FILESTREAM Compatibility with Other SQL Server Features</span></span>](../blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
