---
title: 使用 Unicode 字符格式导入或导出数据 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], Unicode character
- Unicode [SQL Server], bulk importing and exporting
ms.assetid: 74342a11-c1c0-4746-b482-7f3537744a70
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 520ce1b4eed8dc11d6d3fe038969257aea1e90fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693354"
---
# <a name="use-unicode-character-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="4bd17-102">使用 Unicode 字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4bd17-102">Use Unicode Character Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="4bd17-103">使用包含扩展/DBCS 字符的数据文件在多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间大容量传输数据时，建议使用 Unicode 字符格式。</span><span class="sxs-lookup"><span data-stu-id="4bd17-103">Unicode character format is recommended for bulk transfer of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended/DBCS characters.</span></span> <span data-ttu-id="4bd17-104">从服务器导出数据时，Unicode 字符数据格式允许使用与执行该操作的客户端不同的代码页。</span><span class="sxs-lookup"><span data-stu-id="4bd17-104">The Unicode character data format allows data to be exported from a server by using a code page that differs from the code page used by the client that is performing the operation.</span></span> <span data-ttu-id="4bd17-105">在这种情况下，使用 Unicode 字符格式有下列优点：</span><span class="sxs-lookup"><span data-stu-id="4bd17-105">In such cases, use of Unicode character format has the following advantages:</span></span>  
  
-   <span data-ttu-id="4bd17-106">如果源数据和目标数据的类型为 Unicode，则使用 Unicode 字符格式可以保留所有的字符数据。</span><span class="sxs-lookup"><span data-stu-id="4bd17-106">If the source and destination data are Unicode data types, use of Unicode character format preserves all of the character data.</span></span>  
  
-   <span data-ttu-id="4bd17-107">如果源数据和目标数据的类型不为 Unicode，则使用 Unicode 字符格式可以尽可能减少丢失源数据中无法在目标数据中表示的扩展字符。</span><span class="sxs-lookup"><span data-stu-id="4bd17-107">if the source and destination data are not Unicode data types, use of Unicode character format minimizes the loss of extended characters in the source data that cannot be represented at the destination.</span></span>  
  
 <span data-ttu-id="4bd17-108">Unicode 字符格式数据文件遵循 Unicode 文件的约定。</span><span class="sxs-lookup"><span data-stu-id="4bd17-108">Unicode character format data files follow the conventions for Unicode files.</span></span> <span data-ttu-id="4bd17-109">该文件的前两个字节为十六进制数字 0xFFFE。</span><span class="sxs-lookup"><span data-stu-id="4bd17-109">The first two bytes of the file are hexadecimal numbers, 0xFFFE.</span></span> <span data-ttu-id="4bd17-110">这两个字节用作字节顺序标记，指定在文件中高位字节是存储在前面还是后面。</span><span class="sxs-lookup"><span data-stu-id="4bd17-110">These bytes serve as byte-order marks, specifying whether the high-order byte is stored first or last in the file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4bd17-111">对于用于 Unicode 字符数据文件的格式化文件，所有输入字段必须为 Unicode 文本字符串（即固定大小 Unicode 字符串或字符终止 Unicode 字符串）。</span><span class="sxs-lookup"><span data-stu-id="4bd17-111">For a format file to work with a Unicode character data file, all the input fields must be Unicode text strings (that is, either fixed-size or character-terminated Unicode strings).</span></span>  
  
 <span data-ttu-id="4bd17-112">Unicode 字符格式数据文件中存储的 `sql_variant` 数据的操作方式与字符格式数据文件中的同类数据的操作方式相同，唯一的不同是该数据存储为 `nchar` 而不是 `char` 数据。</span><span class="sxs-lookup"><span data-stu-id="4bd17-112">The `sql_variant` data that is stored in a Unicode character-format data file operates in the same way it operates in a character-format data file, except that the data is stored as `nchar` instead of `char` data.</span></span> <span data-ttu-id="4bd17-113">有关字符格式的详细信息，请参阅 [Collation and Unicode Support](../collations/collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd17-113">For more information about character format, see [Collation and Unicode Support](../collations/collation-and-unicode-support.md).</span></span>  
  
 <span data-ttu-id="4bd17-114">若要使用与 Unicode 字符格式提供的默认终止符不同的字段终止符或行终止符，请参阅[指定字段终止符和行终止符 (SQL Server)](specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd17-114">To use a field or row terminator other than the default that is provided with Unicode character format, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>  
  
## <a name="command-options-for-unicode-character-format"></a><span data-ttu-id="4bd17-115">Unicode 字符格式的命令选项</span><span class="sxs-lookup"><span data-stu-id="4bd17-115">Command Options for Unicode Character Format</span></span>  
 <span data-ttu-id="4bd17-116">可以使用**bcp**、BULK INSERT 或 INSERT ... 将 Unicode 字符格式数据导入表中。\*从 OPENROWSET (BULK ... ) 中进行选择。对于**bcp**命令或 BULK INSERT 语句，可以在命令行中指定数据格式。</span><span class="sxs-lookup"><span data-stu-id="4bd17-116">You can import Unicode character format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="4bd17-117">对于 INSERT ...SELECT \* FROM OPENROWSET(BULK...) 语句，必须在格式化文件中指定数据格式。</span><span class="sxs-lookup"><span data-stu-id="4bd17-117">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="4bd17-118">下列命令行选项支持 Unicode 字符格式：</span><span class="sxs-lookup"><span data-stu-id="4bd17-118">Unicode character format is supported by the following command line options:</span></span>  
  
|<span data-ttu-id="4bd17-119">Command</span><span class="sxs-lookup"><span data-stu-id="4bd17-119">Command</span></span>|<span data-ttu-id="4bd17-120">选项</span><span class="sxs-lookup"><span data-stu-id="4bd17-120">Option</span></span>|<span data-ttu-id="4bd17-121">说明</span><span class="sxs-lookup"><span data-stu-id="4bd17-121">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="4bd17-122">**bcp**</span><span class="sxs-lookup"><span data-stu-id="4bd17-122">**bcp**</span></span>|<span data-ttu-id="4bd17-123">**-w**</span><span class="sxs-lookup"><span data-stu-id="4bd17-123">**-w**</span></span>|<span data-ttu-id="4bd17-124">使用 Unicode 字符格式。</span><span class="sxs-lookup"><span data-stu-id="4bd17-124">Uses the Unicode character format.</span></span>|  
|<span data-ttu-id="4bd17-125">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="4bd17-125">BULK INSERT</span></span>|<span data-ttu-id="4bd17-126">DATAFILETYPE **= '** widechar **'**</span><span class="sxs-lookup"><span data-stu-id="4bd17-126">DATAFILETYPE **='** widechar **'**</span></span>|<span data-ttu-id="4bd17-127">批量导入数据时使用 Unicode 字符格式。</span><span class="sxs-lookup"><span data-stu-id="4bd17-127">Uses Unicode character format when bulk importing data.</span></span>|  
  
 <span data-ttu-id="4bd17-128">有关详细信息，请参阅 [bcp 实用工具](../../tools/bcp-utility.md)、[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) 或 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4bd17-128">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4bd17-129">或者，您可以在格式化文件中为每个字段指定格式设置。</span><span class="sxs-lookup"><span data-stu-id="4bd17-129">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="4bd17-130">有关详细信息，请参阅 [用来导入或导出数据的格式化文件 (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd17-130">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4bd17-131">示例</span><span class="sxs-lookup"><span data-stu-id="4bd17-131">Examples</span></span>  
 <span data-ttu-id="4bd17-132">下面的示例展示了如何使用 **bcp** 批量导出 Unicode 字符数据，以及如何使用 BULK INSERT 批量导入相同的数据。</span><span class="sxs-lookup"><span data-stu-id="4bd17-132">The following examples demonstrate how to bulk export Unicode character data using **bcp** and to bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="4bd17-133">示例表</span><span class="sxs-lookup"><span data-stu-id="4bd17-133">Sample Table</span></span>  
 <span data-ttu-id="4bd17-134">这些示例要求在 `myTestUniCharData` 示例数据库中的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 架构下创建名为 `dbo` 的表。</span><span class="sxs-lookup"><span data-stu-id="4bd17-134">The examples require that a table named `myTestUniCharData` table be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="4bd17-135">必须先创建此表，才能运行这些示例。</span><span class="sxs-lookup"><span data-stu-id="4bd17-135">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="4bd17-136">若要创建此表，请在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="4bd17-136">To create this table, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestUniCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="4bd17-137">若要填充此表并查看得到的内容，请执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="4bd17-137">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestUniCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3')   
        ,(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
  
```  
  
### <a name="using-bcp-to-bulk-export-unicode-character-data"></a><span data-ttu-id="4bd17-138">使用 bcp 大容量导出 Unicode 字符数据</span><span class="sxs-lookup"><span data-stu-id="4bd17-138">Using bcp to Bulk Export Unicode Character Data</span></span>  
 <span data-ttu-id="4bd17-139">若要将表中数据导出到数据文件，请将 **bcp** 与 **out** 选项和以下限定符结合使用：</span><span class="sxs-lookup"><span data-stu-id="4bd17-139">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="4bd17-140">限定符</span><span class="sxs-lookup"><span data-stu-id="4bd17-140">Qualifiers</span></span>|<span data-ttu-id="4bd17-141">说明</span><span class="sxs-lookup"><span data-stu-id="4bd17-141">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="4bd17-142">**-w**</span><span class="sxs-lookup"><span data-stu-id="4bd17-142">**-w**</span></span>|<span data-ttu-id="4bd17-143">指定 Unicode 字符格式。</span><span class="sxs-lookup"><span data-stu-id="4bd17-143">Specifies Unicode character format.</span></span>|  
|<span data-ttu-id="4bd17-144">**-t** `,`</span><span class="sxs-lookup"><span data-stu-id="4bd17-144">**-t** `,`</span></span>|<span data-ttu-id="4bd17-145">将逗号 (`,`) 指定为字段终止符。</span><span class="sxs-lookup"><span data-stu-id="4bd17-145">Specifies a comma (`,`) as the field terminator.</span></span><br /><br /> <span data-ttu-id="4bd17-146">注意：默认的字段终止符是 ( \t) 的 tab 键。</span><span class="sxs-lookup"><span data-stu-id="4bd17-146">Note: The default field terminator is the tab Unicode character (\t).</span></span> <span data-ttu-id="4bd17-147">有关详细信息，请参阅 [指定字段终止符和行终止符 (SQL Server)](specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd17-147">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>|  
|<span data-ttu-id="4bd17-148">**-T**</span><span class="sxs-lookup"><span data-stu-id="4bd17-148">**-T**</span></span>|<span data-ttu-id="4bd17-149">指定 **bcp** 实用工具通过使用集成安全性的受信任连接连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4bd17-149">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="4bd17-150">如果未指定 **-T** ，则需要指定 **-U** 和 **-P** 才能成功登录。</span><span class="sxs-lookup"><span data-stu-id="4bd17-150">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="4bd17-151">以下示例将 Unicode 字符格式的数据从 `myTestUniCharData` 表中大容量导出到名为 `myTestUniCharData-w.Dat` 的新数据文件，此数据文件使用逗号 (`,`) 作为字段终止符。</span><span class="sxs-lookup"><span data-stu-id="4bd17-151">The following example bulk exports data in Unicode character format from the `myTestUniCharData` table into a new data file named `myTestUniCharData-w.Dat` data file that uses the comma (`,`) as the field terminator.</span></span> <span data-ttu-id="4bd17-152">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示符下输入：</span><span class="sxs-lookup"><span data-stu-id="4bd17-152">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..myTestUniCharData out C:\myTestUniCharData-w.Dat -w -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-unicode-character-data"></a><span data-ttu-id="4bd17-153">使用 BULK INSERT 大容量导入 Unicode 字符数据</span><span class="sxs-lookup"><span data-stu-id="4bd17-153">Using BULK INSERT to Bulk Import Unicode Character Data</span></span>  
 <span data-ttu-id="4bd17-154">以下示例使用 `BULK INSERT` 将 `myTestUniCharData-w.Dat` 数据文件中的数据导入 `myTestUniCharData` 表。</span><span class="sxs-lookup"><span data-stu-id="4bd17-154">The following example uses `BULK INSERT` to import the data in the `myTestUniCharData-w.Dat` data file into the `myTestUniCharData` table.</span></span> <span data-ttu-id="4bd17-155">必须在语句中声明非默认字段终止符 (`,`)。</span><span class="sxs-lookup"><span data-stu-id="4bd17-155">The nondefault field terminator (`,`) must be declared in the statement.</span></span> <span data-ttu-id="4bd17-156">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="4bd17-156">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestUniCharData   
   FROM 'C:\myTestUniCharData-w.Dat'   
   WITH (  
      DATAFILETYPE='widechar',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4bd17-157">相关任务</span><span class="sxs-lookup"><span data-stu-id="4bd17-157">Related Tasks</span></span>  
 <span data-ttu-id="4bd17-158">**使用数据格式进行大容量导入或大容量导出**</span><span class="sxs-lookup"><span data-stu-id="4bd17-158">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="4bd17-159">导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据</span><span class="sxs-lookup"><span data-stu-id="4bd17-159">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="4bd17-160">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4bd17-160">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="4bd17-161">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4bd17-161">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="4bd17-162">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4bd17-162">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="4bd17-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4bd17-163">See Also</span></span>  
 <span data-ttu-id="4bd17-164">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="4bd17-164">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="4bd17-165">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4bd17-165">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="4bd17-166">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4bd17-166">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="4bd17-167">[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4bd17-167">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 [<span data-ttu-id="4bd17-168">排序规则和 Unicode 支持</span><span class="sxs-lookup"><span data-stu-id="4bd17-168">Collation and Unicode Support</span></span>](../collations/collation-and-unicode-support.md)  
  
  
