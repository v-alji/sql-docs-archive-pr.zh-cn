---
title: 用于批量导入或批量导出的数据格式 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], choosing
- bulk importing [SQL Server], data formats
ms.assetid: 73fe6741-9437-4b26-b030-28b863e74399
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b92ac8c038362ff18a1459a8bf3c55b6b596a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576753"
---
# <a name="data-formats-for-bulk-import-or-bulk-export-sql-server"></a><span data-ttu-id="0268a-102">用于批量导入或导出的数据格式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0268a-102">Data Formats for Bulk Import or Bulk Export (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0268a-103">可以接受字符数据格式或本机二进制数据格式的数据。</span><span class="sxs-lookup"><span data-stu-id="0268a-103">can accept data in character data format or native binary data format.</span></span> <span data-ttu-id="0268a-104">当在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和其他应用程序（例如， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel）或其他数据库服务器（例如，Oracle 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]）之间移动数据时，请使用字符格式。</span><span class="sxs-lookup"><span data-stu-id="0268a-104">Use character format when you move data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and another application (such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) or another database server (such as Oracle or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).</span></span> <span data-ttu-id="0268a-105">只有在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例之间传输数据时才可以使用本机格式。</span><span class="sxs-lookup"><span data-stu-id="0268a-105">You can use native format only when you transfer data between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0268a-106">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="0268a-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="0268a-107">用于大容量导入或导出的数据格式</span><span class="sxs-lookup"><span data-stu-id="0268a-107">Data Formats for Bulk Import or Export</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="0268a-108">相关任务</span><span class="sxs-lookup"><span data-stu-id="0268a-108">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="data-formats-for-bulk-import-or-export"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="0268a-109">用于大容量导入或导出的数据格式</span><span class="sxs-lookup"><span data-stu-id="0268a-109">Data Formats for Bulk Import or Export</span></span>  
 <span data-ttu-id="0268a-110">下表列出了不同数据显示方式和操作的源或目标一般适合使用的数据格式。</span><span class="sxs-lookup"><span data-stu-id="0268a-110">The following table indicates what data format is generally appropriate to use depending on how the data is represented and the source or target of the operation.</span></span>  
  
|<span data-ttu-id="0268a-111">Operation</span><span class="sxs-lookup"><span data-stu-id="0268a-111">Operation</span></span>|<span data-ttu-id="0268a-112">本机</span><span class="sxs-lookup"><span data-stu-id="0268a-112">Native</span></span>|<span data-ttu-id="0268a-113">Unicode 本机</span><span class="sxs-lookup"><span data-stu-id="0268a-113">Unicode native</span></span>|<span data-ttu-id="0268a-114">字符</span><span class="sxs-lookup"><span data-stu-id="0268a-114">Character</span></span>|<span data-ttu-id="0268a-115">Unicode 字符</span><span class="sxs-lookup"><span data-stu-id="0268a-115">Unicode character</span></span>|  
|---------------|------------|--------------------|---------------|-----------------------|  
|<span data-ttu-id="0268a-116">使用不包含任何扩展字符或双字节字符集 (DBCS) 字符的数据文件在多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间进行大容量的数据传输。</span><span class="sxs-lookup"><span data-stu-id="0268a-116">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that does not contain any extended or double-byte character set (DBCS) characters.</span></span> <span data-ttu-id="0268a-117">除非使用格式化文件，否则这些表的定义必须相同。</span><span class="sxs-lookup"><span data-stu-id="0268a-117">Unless a format file is used, these tables must be identically defined.</span></span>|<span data-ttu-id="0268a-118">是<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0268a-118">Yes<sup>1</sup></span></span>|-|-|-|  
|<span data-ttu-id="0268a-119">对于 `sql_variant` 列，最好使用本机数据格式，因为本机数据格式可以保留每一个 `sql_variant` 值的元数据，这一点不同于字符格式或 Unicode 格式。</span><span class="sxs-lookup"><span data-stu-id="0268a-119">For `sql_variant` columns, use of native data format is best, because native data format preserves the metadata for each `sql_variant` value, unlike character or Unicode formats.</span></span>|<span data-ttu-id="0268a-120">是</span><span class="sxs-lookup"><span data-stu-id="0268a-120">Yes</span></span>|-|-|-|  
|<span data-ttu-id="0268a-121">使用包含扩展字符或 DBCS 字符的数据文件在多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间进行大容量的数据传输。</span><span class="sxs-lookup"><span data-stu-id="0268a-121">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters.</span></span>|-|<span data-ttu-id="0268a-122">是</span><span class="sxs-lookup"><span data-stu-id="0268a-122">Yes</span></span>|-|-|  
|<span data-ttu-id="0268a-123">大容量导入其他程序生成的文本文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="0268a-123">Bulk import of data from a text file that is generated by another program.</span></span>|-|-|<span data-ttu-id="0268a-124">是</span><span class="sxs-lookup"><span data-stu-id="0268a-124">Yes</span></span>|-|  
|<span data-ttu-id="0268a-125">将数据大容量导出到要在其他程序中使用的文本文件中。</span><span class="sxs-lookup"><span data-stu-id="0268a-125">Bulk export of data to a text file that is to be used in another program.</span></span>|-|-|<span data-ttu-id="0268a-126">是</span><span class="sxs-lookup"><span data-stu-id="0268a-126">Yes</span></span>|-|  
|<span data-ttu-id="0268a-127">使用包含 Unicode 数据而不包含任何扩展字符或 DBCS 字符的数据文件在多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间进行大容量的数据传输。</span><span class="sxs-lookup"><span data-stu-id="0268a-127">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains Unicode data and does not contain any extended or DBCS characters.</span></span>|-|-|-|<span data-ttu-id="0268a-128">是</span><span class="sxs-lookup"><span data-stu-id="0268a-128">Yes</span></span>|  
  
 <span data-ttu-id="0268a-129"><sup>1</sup> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用**bcp**时从大容量导出数据的最快方法。</span><span class="sxs-lookup"><span data-stu-id="0268a-129"><sup>1</sup> Fastest method for the bulk export of data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when using **bcp**.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0268a-130">相关任务</span><span class="sxs-lookup"><span data-stu-id="0268a-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="0268a-131">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0268a-131">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="0268a-132">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0268a-132">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="0268a-133">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0268a-133">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="0268a-134">使用 Unicode 字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0268a-134">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="0268a-135">导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据</span><span class="sxs-lookup"><span data-stu-id="0268a-135">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="0268a-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0268a-136">See Also</span></span>  
 <span data-ttu-id="0268a-137">[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0268a-137">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 [<span data-ttu-id="0268a-138">在使用 bcp 时指定数据格式以获得兼容性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0268a-138">Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;</span></span>](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)  
  
  
