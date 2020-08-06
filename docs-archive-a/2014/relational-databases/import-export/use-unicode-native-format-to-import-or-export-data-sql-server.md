---
title: 使用 Unicode 本机格式导入或导出数据 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- Unicode [SQL Server], bulk importing and exporting
- data formats [SQL Server], Unicode native
ms.assetid: a6213308-f3d5-406e-9029-19d8bb3367f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: beae2f836de16dedf3be6d8c196910c53be02266
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693349"
---
# <a name="use-unicode-native-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="436e6-102">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="436e6-102">Use Unicode Native Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="436e6-103">当必须将信息从一个 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装复制到另一个时，Unicode 本机格式非常有用。</span><span class="sxs-lookup"><span data-stu-id="436e6-103">Unicode native format is helpful when information must be copied from one [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation to another.</span></span> <span data-ttu-id="436e6-104">为非字符数据使用本机格式可以节省时间，并消除与字符格式之间不必要的数据类型转换。</span><span class="sxs-lookup"><span data-stu-id="436e6-104">The use of native format for noncharacter data saves time, eliminating unnecessary conversion of data types to and from character format.</span></span> <span data-ttu-id="436e6-105">在使用不同代码页的服务器之间大容量传输数据时，为所有字符数据使用 Unicode 字符格式可以防止丢失任何扩展字符。</span><span class="sxs-lookup"><span data-stu-id="436e6-105">The use of Unicode character format for all character data prevents loss of any extended characters during bulk transfer of data between servers using different code pages.</span></span> <span data-ttu-id="436e6-106">可以通过任何批量导入方法读取 Unicode 本机格式的数据文件。</span><span class="sxs-lookup"><span data-stu-id="436e6-106">A data file in Unicode native format can be read by any bulk-import method.</span></span>  
  
 <span data-ttu-id="436e6-107">通过使用包含扩展字符或 DBCS 字符的数据文件在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的多个实例之间大容量传输数据时，建议使用 Unicode 本机格式。</span><span class="sxs-lookup"><span data-stu-id="436e6-107">Unicode native format is recommended for the bulk transfer of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters.</span></span> <span data-ttu-id="436e6-108">对于非字符数据，Unicode 本机格式使用本机（数据库）数据类型。</span><span class="sxs-lookup"><span data-stu-id="436e6-108">For noncharacter data, Unicode native format uses native (database) data types.</span></span> <span data-ttu-id="436e6-109">对于字符数据（如 `char`、`nchar`、`varchar`、`nvarchar`、`text`、`varchar(max)`、`nvarchar(max)` 和 `ntext`），Unicode 本机格式使用 Unicode 字符数据格式。</span><span class="sxs-lookup"><span data-stu-id="436e6-109">For character data, such as `char`, `nchar`, `varchar`, `nvarchar`, `text`, `varchar(max)`, `nvarchar(max)`, and `ntext`, the Unicode native format uses Unicode character data format.</span></span>  
  
 <span data-ttu-id="436e6-110">在 Unicode 本机格式数据文件中存储为 SQLVARIANT 的 `sql_variant` 数据的运算方式与在本机格式数据文件中的运算方式相同，只是 `char` 和 `varchar` 值需转换为 `nchar` 和 `nvarchar`，这使得受影响列的存储量加倍。</span><span class="sxs-lookup"><span data-stu-id="436e6-110">The `sql_variant` data that is stored as a SQLVARIANT in a Unicode native-format data file operates in the same manner as it does in a native-format data file, except that `char` and `varchar` values are converted to `nchar` and `nvarchar`, which doubles the amount of storage required for the affected columns.</span></span> <span data-ttu-id="436e6-111">这些值的原始元数据被保留，当大容量导入到表列时，这些值将转换回其原始的 `char` 和 `varchar` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="436e6-111">The original metadata is preserved, and the values are converted back to their original `char` and `varchar` data type when bulk imported into a table column.</span></span>  
  
## <a name="command-options-for-unicode-native-format"></a><span data-ttu-id="436e6-112">Unicode 本机格式的命令选项</span><span class="sxs-lookup"><span data-stu-id="436e6-112">Command Options for Unicode Native Format</span></span>  
 <span data-ttu-id="436e6-113">可以使用**bcp**、BULK INSERT 或 INSERT ... 将 Unicode 本机格式数据导入表中\*从 OPENROWSET (BULK ... ) 中进行选择。对于**bcp**命令或 BULK INSERT 语句，可以在命令行中指定数据格式。</span><span class="sxs-lookup"><span data-stu-id="436e6-113">You can import Unicode native format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="436e6-114">对于 INSERT ...SELECT \* FROM OPENROWSET(BULK...) 语句，必须在格式化文件中指定数据格式。</span><span class="sxs-lookup"><span data-stu-id="436e6-114">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="436e6-115">下列选项支持 Unicode 本机格式：</span><span class="sxs-lookup"><span data-stu-id="436e6-115">Unicode native format is supported by the following options:</span></span>  
  
|<span data-ttu-id="436e6-116">Command</span><span class="sxs-lookup"><span data-stu-id="436e6-116">Command</span></span>|<span data-ttu-id="436e6-117">选项</span><span class="sxs-lookup"><span data-stu-id="436e6-117">Option</span></span>|<span data-ttu-id="436e6-118">说明</span><span class="sxs-lookup"><span data-stu-id="436e6-118">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="436e6-119">**bcp**</span><span class="sxs-lookup"><span data-stu-id="436e6-119">**bcp**</span></span>|<span data-ttu-id="436e6-120">**-N**</span><span class="sxs-lookup"><span data-stu-id="436e6-120">**-N**</span></span>|<span data-ttu-id="436e6-121">使**bcp**实用工具使用 Unicode 本机格式，这种格式将对所有非字符数据使用本机 (数据库) 数据类型，为所有字符 (、、、、 `char` `nchar` `varchar` `nvarchar` `text` 和 `ntext`) 数据使用 unicode 字符数据格式。</span><span class="sxs-lookup"><span data-stu-id="436e6-121">Causes the **bcp** utility to use the Unicode native format, which uses native (database) data types for all noncharacter data and Unicode character data format for all character (`char`, `nchar`, `varchar`, `nvarchar`, `text`, and `ntext`) data.</span></span>|  
|<span data-ttu-id="436e6-122">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="436e6-122">BULK INSERT</span></span>|<span data-ttu-id="436e6-123">DATAFILETYPE **= '** widenative **'**</span><span class="sxs-lookup"><span data-stu-id="436e6-123">DATAFILETYPE **='** widenative **'**</span></span>|<span data-ttu-id="436e6-124">大容量导入数据时使用 Unicode 本机格式。</span><span class="sxs-lookup"><span data-stu-id="436e6-124">Use Unicode native format when bulk importing data.</span></span>|  
  
 <span data-ttu-id="436e6-125">有关详细信息，请参阅 [bcp 实用工具](../../tools/bcp-utility.md)、[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) 或 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="436e6-125">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="436e6-126">或者，您可以在格式化文件中为每个字段指定格式设置。</span><span class="sxs-lookup"><span data-stu-id="436e6-126">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="436e6-127">有关详细信息，请参阅 [用来导入或导出数据的格式化文件 (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="436e6-127">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="436e6-128">示例</span><span class="sxs-lookup"><span data-stu-id="436e6-128">Examples</span></span>  
 <span data-ttu-id="436e6-129">下列示例演示如何使用 **bcp** 批量导出本机数据以及使用 BULK INSERT 批量导入相同数据。</span><span class="sxs-lookup"><span data-stu-id="436e6-129">The following examples demonstrate how to bulk export native data using **bcp** and bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="436e6-130">示例表</span><span class="sxs-lookup"><span data-stu-id="436e6-130">Sample Table</span></span>  
 <span data-ttu-id="436e6-131">下列示例要求 **dbo** 架构下的 **AdventureWorks** 示例数据库中存在名称为 **myTestUniNativeData** 的表。</span><span class="sxs-lookup"><span data-stu-id="436e6-131">The examples require that a table named **myTestUniNativeData** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="436e6-132">必须先创建此表，才能运行这些示例。</span><span class="sxs-lookup"><span data-stu-id="436e6-132">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="436e6-133">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="436e6-133">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestUniNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="436e6-134">若要填充此表并查看得到的内容，请执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="436e6-134">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a><span data-ttu-id="436e6-135">使用 bcp 大容量导出本机数据</span><span class="sxs-lookup"><span data-stu-id="436e6-135">Using bcp to Bulk Export Native Data</span></span>  
 <span data-ttu-id="436e6-136">若要将表中数据导出到数据文件，请将 **bcp** 与 **out** 选项和以下限定符结合使用：</span><span class="sxs-lookup"><span data-stu-id="436e6-136">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="436e6-137">限定符</span><span class="sxs-lookup"><span data-stu-id="436e6-137">Qualifiers</span></span>|<span data-ttu-id="436e6-138">说明</span><span class="sxs-lookup"><span data-stu-id="436e6-138">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="436e6-139">**-N**</span><span class="sxs-lookup"><span data-stu-id="436e6-139">**-N**</span></span>|<span data-ttu-id="436e6-140">指定本机数据类型。</span><span class="sxs-lookup"><span data-stu-id="436e6-140">Specifies native data types.</span></span>|  
|<span data-ttu-id="436e6-141">**-T**</span><span class="sxs-lookup"><span data-stu-id="436e6-141">**-T**</span></span>|<span data-ttu-id="436e6-142">指定 **bcp** 实用工具通过使用集成安全性的受信任连接连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="436e6-142">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="436e6-143">如果未指定 **-T** ，则需要指定 **-U** 和 **-P** 才能成功登录。</span><span class="sxs-lookup"><span data-stu-id="436e6-143">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="436e6-144">以下示例将本机格式的数据从 `myTestUniNativeData` 表大容量导出到名为 `myTestUniNativeData-N.Dat` 的新数据文件中。</span><span class="sxs-lookup"><span data-stu-id="436e6-144">The following example bulk exports data in native format from the `myTestUniNativeData` table into a new data file named `myTestUniNativeData-N.Dat` data file.</span></span> <span data-ttu-id="436e6-145">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示符下输入：</span><span class="sxs-lookup"><span data-stu-id="436e6-145">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..myTestUniNativeData out C:\myTestUniNativeData-N.Dat -N -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a><span data-ttu-id="436e6-146">使用 BULK INSERT 大容量导入本机数据</span><span class="sxs-lookup"><span data-stu-id="436e6-146">Using BULK INSERT to Bulk Import Native Data</span></span>  
 <span data-ttu-id="436e6-147">以下示例使用 BULK INSERT 将 `myTestUniNativeData-N.Dat` 数据文件中的数据导入到 `myTestUniNativeData` 表中。</span><span class="sxs-lookup"><span data-stu-id="436e6-147">The following example uses BULK INSERT to import the data in the `myTestUniNativeData-N.Dat` data file into the `myTestUniNativeData` table.</span></span> <span data-ttu-id="436e6-148">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="436e6-148">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestUniNativeData   
    FROM 'C:\myTestUniNativeData-N.Dat'   
   WITH (DATAFILETYPE='widenative');   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="436e6-149">相关任务</span><span class="sxs-lookup"><span data-stu-id="436e6-149">Related Tasks</span></span>  
 <span data-ttu-id="436e6-150">**使用数据格式进行大容量导入或大容量导出**</span><span class="sxs-lookup"><span data-stu-id="436e6-150">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="436e6-151">导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据</span><span class="sxs-lookup"><span data-stu-id="436e6-151">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="436e6-152">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="436e6-152">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="436e6-153">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="436e6-153">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="436e6-154">使用 Unicode 字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="436e6-154">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="436e6-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="436e6-155">See Also</span></span>  
 <span data-ttu-id="436e6-156">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="436e6-156">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="436e6-157">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="436e6-157">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="436e6-158">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="436e6-158">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="436e6-159">数据类型 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="436e6-159">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
