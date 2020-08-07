---
title: 导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- earlier versions [SQL Server], import and export data formats
- -V switch
- data formats [SQL Server], earlier versions
- previous versions [SQL Server], import and export data formats
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 274c984d6ecec8af8f5bea27496450a45fc2f1df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589075"
---
# <a name="import-native-and-character-format-data-from-earlier-versions-of-sql-server"></a><span data-ttu-id="17668-102">导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据</span><span class="sxs-lookup"><span data-stu-id="17668-102">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>
  <span data-ttu-id="17668-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，可以通过将 **bcp** 与 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-V [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]开关一起使用，从 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 、 **或** 中导入本机和字符格式数据。</span><span class="sxs-lookup"><span data-stu-id="17668-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can use **bcp** to import native and character format data from [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] by using the **-V** switch.</span></span> <span data-ttu-id="17668-104">**-V** 开关将使 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]早期版本中的数据类型，并且数据文件格式与早期版本中的格式相同。</span><span class="sxs-lookup"><span data-stu-id="17668-104">The **-V** switch causes [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to use data types from the specified earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and the data file format are the same as the format in that earlier version.</span></span>  
  
 <span data-ttu-id="17668-105">若要为数据文件指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 早期版本，可将 **-V** 开关与以下的任一限定符一起使用：</span><span class="sxs-lookup"><span data-stu-id="17668-105">To specify an earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version for a data file, use the **-V** switch with one of the following qualifiers:</span></span>  
  
|<span data-ttu-id="17668-106">SQL Server 版本</span><span class="sxs-lookup"><span data-stu-id="17668-106">SQL Server version</span></span>|<span data-ttu-id="17668-107">Qualifier</span><span class="sxs-lookup"><span data-stu-id="17668-107">Qualifier</span></span>|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|<span data-ttu-id="17668-108">**-V80**</span><span class="sxs-lookup"><span data-stu-id="17668-108">**-V80**</span></span>|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="17668-109">**-V90**</span><span class="sxs-lookup"><span data-stu-id="17668-109">**-V90**</span></span>|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|<span data-ttu-id="17668-110">**-V100**</span><span class="sxs-lookup"><span data-stu-id="17668-110">**-V100**</span></span>|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|<span data-ttu-id="17668-111">**-V 110**</span><span class="sxs-lookup"><span data-stu-id="17668-111">**-V 110**</span></span>|  
  
## <a name="interpretation-of-data-types"></a><span data-ttu-id="17668-112">对数据类型的解释</span><span class="sxs-lookup"><span data-stu-id="17668-112">Interpretation of Data Types</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="17668-113">及更高版本均支持一些新的类型。</span><span class="sxs-lookup"><span data-stu-id="17668-113">and later versions have support for some new types.</span></span> <span data-ttu-id="17668-114">如果要将新的数据类型导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 早期版本中，则必须以早期的 **bcp** 客户端可读的格式存储该数据类型。</span><span class="sxs-lookup"><span data-stu-id="17668-114">When you want to import a new data type into an earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version, the data type must be stored in a format that readable by the older **bcp** clients.</span></span> <span data-ttu-id="17668-115">下表总结了如何转换新数据类型以便与早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]兼容。</span><span class="sxs-lookup"><span data-stu-id="17668-115">The following table summarizes how the new data types are converted for compatibility with the earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="17668-116">SQL Server 2005 中的新数据类型</span><span class="sxs-lookup"><span data-stu-id="17668-116">New data types in SQL Server 2005</span></span>|<span data-ttu-id="17668-117">版本 6*x*兼容的数据类型</span><span class="sxs-lookup"><span data-stu-id="17668-117">Compatible data types in version 6*x*</span></span>|<span data-ttu-id="17668-118">版本 70 中兼容的数据类型</span><span class="sxs-lookup"><span data-stu-id="17668-118">Compatible data types in version 70</span></span>|<span data-ttu-id="17668-119">版本 80 中兼容的数据类型</span><span class="sxs-lookup"><span data-stu-id="17668-119">Compatible data types in version 80</span></span>|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|`bigint`|`decimal`|`decimal`|*|  
|`sql_variant`|`text`|`nvarchar(4000)`|*|  
|`varchar(max)`|`text`|`text`|`text`|  
|`nvarchar(max)`|`ntext`|`ntext`|`ntext`|  
|`varbinary(max)`|`image`|`image`|`image`|  
|<span data-ttu-id="17668-120">XML</span><span class="sxs-lookup"><span data-stu-id="17668-120">XML</span></span>|`ntext`|`ntext`|`ntext`|  
|<span data-ttu-id="17668-121">UDT<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="17668-121">UDT<sup>1</sup></span></span>|`image`|`image`|`image`|  
  
 <span data-ttu-id="17668-122">\*此类型受本机支持。</span><span class="sxs-lookup"><span data-stu-id="17668-122">\* This type is natively supported.</span></span>  
  
 <span data-ttu-id="17668-123"><sup>1</sup> UDT 表示用户定义的类型。</span><span class="sxs-lookup"><span data-stu-id="17668-123"><sup>1</sup> UDT indicates a user defined type.</span></span>  
  
## <a name="exporting-using--v-80"></a><span data-ttu-id="17668-124">使用 -V 80 进行导出</span><span class="sxs-lookup"><span data-stu-id="17668-124">Exporting using -V 80</span></span>  
 <span data-ttu-id="17668-125">使用 **-V80**开关大容量导出数据时， `nvarchar(max)` 纯模式下的、、、 `varchar(max)` `varbinary(max)` XML 和 UDT 数据将存储为带有4个字节的前缀，例如 `text` 、 `image` 和 `ntext` 数据，而不是使用8字节前缀，这是 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本的默认值。</span><span class="sxs-lookup"><span data-stu-id="17668-125">When you bulk export data by using the **-V80** switch, `nvarchar(max)`, `varchar(max)`, `varbinary(max)`, XML, and UDT data in native mode are stored with a 4-byte prefix, like `text`, `image`, and `ntext` data, rather than with an 8-byte prefix, which is the default for [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span>  
  
## <a name="copying-date-values"></a><span data-ttu-id="17668-126">复制日期值</span><span class="sxs-lookup"><span data-stu-id="17668-126">Copying Date Values</span></span>  
 <span data-ttu-id="17668-127">**bcp** 将使用 ODBC 大容量复制 API。</span><span class="sxs-lookup"><span data-stu-id="17668-127">**bcp** uses the ODBC bulk copy API.</span></span> <span data-ttu-id="17668-128">因此，为了将日期值导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中， **bcp** 使用了 ODBC 日期格式 (*yyyy-mm-dd hh:mm:ss*[ *.f...* ])。</span><span class="sxs-lookup"><span data-stu-id="17668-128">Therefore, to import date values into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **bcp** uses the ODBC date format (*yyyy-mm-dd hh:mm:ss*[*.f...*]).</span></span>  
  
 <span data-ttu-id="17668-129">**Bcp**命令使用和值的 ODBC 默认格式导出字符格式的数据 `datetime` 文件 `smalldatetime` 。</span><span class="sxs-lookup"><span data-stu-id="17668-129">The **bcp** command exports character format data files using the ODBC default format for `datetime` and `smalldatetime` values.</span></span> <span data-ttu-id="17668-130">例如，包含日期 `12 Aug 1998` 的 `datetime` 列将以字符串 `1998-08-12 00:00:00.000` 的形式大容量复制到数据文件中。</span><span class="sxs-lookup"><span data-stu-id="17668-130">For example, a `datetime` column containing the date `12 Aug 1998` is bulk copied to a data file as the character string `1998-08-12 00:00:00.000`.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="17668-131">使用 bcp 将数据导入到字段中时 `smalldatetime` ，请确保秒数值为00.000，否则操作将失败。 **bcp**</span><span class="sxs-lookup"><span data-stu-id="17668-131">When importing data into a `smalldatetime` field using **bcp**, be sure the value for seconds is 00.000; otherwise the operation will fail.</span></span> <span data-ttu-id="17668-132">`smalldatetime` 数据类型仅支持最接近的分钟值。</span><span class="sxs-lookup"><span data-stu-id="17668-132">The `smalldatetime` data type only holds values to the nearest minute.</span></span> <span data-ttu-id="17668-133">BULK INSERT 和 INSERT ...SELECT \* FROM OPENROWSET(BULK...) 在这种情况下不会失败，但会截断秒值。</span><span class="sxs-lookup"><span data-stu-id="17668-133">BULK INSERT and INSERT ... SELECT \* FROM OPENROWSET(BULK...) will not fail in this instance but will truncate the seconds value.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="17668-134">相关任务</span><span class="sxs-lookup"><span data-stu-id="17668-134">Related Tasks</span></span>  
 <span data-ttu-id="17668-135">**使用数据格式进行大容量导入或大容量导出**</span><span class="sxs-lookup"><span data-stu-id="17668-135">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="17668-136">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="17668-136">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="17668-137">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="17668-137">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="17668-138">使用 Unicode 字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="17668-138">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="17668-139">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="17668-139">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="17668-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17668-140">See Also</span></span>  
 <span data-ttu-id="17668-141">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="17668-141">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="17668-142">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="17668-142">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="17668-143">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="17668-143">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="17668-144">[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="17668-144">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="17668-145">[SQL Server 数据库引擎的向后兼容性](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="17668-145">[SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span></span>  
 [<span data-ttu-id="17668-146">CAST 和 CONVERT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="17668-146">CAST and CONVERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  
