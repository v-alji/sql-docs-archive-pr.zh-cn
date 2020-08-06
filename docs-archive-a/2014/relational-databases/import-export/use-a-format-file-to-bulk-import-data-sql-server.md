---
title: 使用格式化文件批量导入数据 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], format files
- format files [SQL Server], importing data using
ms.assetid: 2956df78-833f-45fa-8a10-41d6522562b9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6d9779209b3ffb317658243c168d74740f6731b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591896"
---
# <a name="use-a-format-file-to-bulk-import-data-sql-server"></a><span data-ttu-id="2c4de-102">使用格式化文件大容量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2c4de-102">Use a Format File to Bulk Import Data (SQL Server)</span></span>
  <span data-ttu-id="2c4de-103">本主题说明如何在大容量导入操作中使用格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2c4de-103">This topic illustrates the use of a format file in bulk-import operations.</span></span> <span data-ttu-id="2c4de-104">格式化文件将数据文件的各字段映射到表的各列。</span><span class="sxs-lookup"><span data-stu-id="2c4de-104">The format file maps the fields of the data file to the columns of the table.</span></span>  <span data-ttu-id="2c4de-105">使用**bcp**命令或 BULK INSERT 或 INSERT ... 时，可以使用非 XML 或 XML 格式化文件大容量导入数据。SELECT \* FROM OPENROWSET (BULK ... ) [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令。</span><span class="sxs-lookup"><span data-stu-id="2c4de-105">You can use a non-XML or XML format file to bulk import data when using a **bcp** command or a BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...) [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2c4de-106">对于用于 Unicode 字符数据文件的格式化文件，所有输入字段必须为 Unicode 文本字符串（即固定大小 Unicode 字符串或字符终止 Unicode 字符串）。</span><span class="sxs-lookup"><span data-stu-id="2c4de-106">For a format file to work with a Unicode character data file, all the input fields must be Unicode text strings (that is, either fixed-size or character-terminated Unicode strings).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c4de-107">如果不熟悉格式化文件，请参阅[非 XML 格式化文件 &#40;SQL Server&#41;](xml-format-files-sql-server.md)和[XML 格式化文件 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2c4de-107">If you are unfamiliar with format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) and [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="format-file-options-for-bulk-import-commands"></a><span data-ttu-id="2c4de-108">大容量导入命令的格式化文件选项</span><span class="sxs-lookup"><span data-stu-id="2c4de-108">Format File Options for Bulk-Import Commands</span></span>  
 <span data-ttu-id="2c4de-109">下表汇总了各个大容量导入命令的格式化文件选项。</span><span class="sxs-lookup"><span data-stu-id="2c4de-109">The following table summarizes the format-file option of for each of the bulk-import commands.</span></span>  
  
|<span data-ttu-id="2c4de-110">大容量加载命令</span><span class="sxs-lookup"><span data-stu-id="2c4de-110">Bulk-load Command</span></span>|<span data-ttu-id="2c4de-111">使用格式化文件选项</span><span class="sxs-lookup"><span data-stu-id="2c4de-111">Using the Format-File Option</span></span>|  
|------------------------|-----------------------------------|  
|<span data-ttu-id="2c4de-112">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="2c4de-112">BULK INSERT</span></span>|<span data-ttu-id="2c4de-113">FORMATFILE = '*format_file_path*'</span><span class="sxs-lookup"><span data-stu-id="2c4de-113">FORMATFILE = '*format_file_path*'</span></span>|  
|<span data-ttu-id="2c4de-114">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="2c4de-114">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="2c4de-115">FORMATFILE = '*format_file_path*'</span><span class="sxs-lookup"><span data-stu-id="2c4de-115">FORMATFILE = '*format_file_path*'</span></span>|  
|<span data-ttu-id="2c4de-116">**bcp** .。。**中**</span><span class="sxs-lookup"><span data-stu-id="2c4de-116">**bcp** ... **in**</span></span>|<span data-ttu-id="2c4de-117">**-f** *format_file*</span><span class="sxs-lookup"><span data-stu-id="2c4de-117">**-f** *format_file*</span></span>|  
  
 <span data-ttu-id="2c4de-118">有关详细信息，请参阅 [bcp 实用工具](../../tools/bcp-utility.md)、[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) 或 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2c4de-118">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c4de-119">若要大容量导出或导入 SQLXML 数据，请在格式化文件中使用下列数据类型之一：SQLCHAR 或 SQLVARYCHAR（数据以客户端代码页或排序规则隐含的代码页的形式发送）、SQLNCHAR 或 SQLNVARCHAR（数据以 Unicode 的形式发送）或者 SQLBINARY 或 SQLVARYBIN（数据不经任何转换直接发送）。</span><span class="sxs-lookup"><span data-stu-id="2c4de-119">To bulk export or import SQLXML data, use one of the following data types in your format file: SQLCHAR or SQLVARYCHAR (the data is sent in the client code page or in the code page implied by the collation), SQLNCHAR or SQLNVARCHAR (the data is sent as Unicode), or SQLBINARY or SQLVARYBIN (the data is sent without any conversion).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2c4de-120">示例</span><span class="sxs-lookup"><span data-stu-id="2c4de-120">Examples</span></span>  
 <span data-ttu-id="2c4de-121">本节中的示例说明了如何使用格式化文件通过**bcp**命令和 BULK INSERT，并使用 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) 语句。</span><span class="sxs-lookup"><span data-stu-id="2c4de-121">The examples in this section illustrate how to use format files to bulk-import data by using the **bcp** command and the BULK INSERT, and INSERT ... SELECT \* FROM OPENROWSET(BULK...) statements.</span></span> <span data-ttu-id="2c4de-122">运行这些大容量导入示例之前，都必须先创建示例表、数据文件和格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2c4de-122">Before you can run one of the bulk-import examples, you need to create a sample table, data file, and a format file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="2c4de-123">示例表</span><span class="sxs-lookup"><span data-stu-id="2c4de-123">Sample Table</span></span>  
 <span data-ttu-id="2c4de-124">这些示例要求在 **示例数据库中的** dbo [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 架构下创建名为 **myTestFormatFiles** 的表。</span><span class="sxs-lookup"><span data-stu-id="2c4de-124">The examples require that a table named **myTestFormatFiles** table be created in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database under the **dbo** schema.</span></span> <span data-ttu-id="2c4de-125">若要创建此表，请在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="2c4de-125">To create this table, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestFormatFiles (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50),  
   Col4 nvarchar(50)  
   );  
GO  
```  
  
### <a name="sample-data-file"></a><span data-ttu-id="2c4de-126">示例数据文件</span><span class="sxs-lookup"><span data-stu-id="2c4de-126">Sample Data File</span></span>  
 <span data-ttu-id="2c4de-127">这些示例使用包含以下记录的示例数据文件 `myTestFormatFiles-c.Dat`。</span><span class="sxs-lookup"><span data-stu-id="2c4de-127">The examples use a sample data file, `myTestFormatFiles-c.Dat`, which contains the following records.</span></span> <span data-ttu-id="2c4de-128">若要创建数据文件，请在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示符下输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="2c4de-128">To create the data file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
10,Field2,Field3,Field4  
15,Field2,Field3,Field4  
46,Field2,Field3,Field4  
58,Field2,Field3,Field4  
```  
  
### <a name="sample-format-files"></a><span data-ttu-id="2c4de-129">示例格式化文件</span><span class="sxs-lookup"><span data-stu-id="2c4de-129">Sample Format Files</span></span>  
 <span data-ttu-id="2c4de-130">本节中的一些示例使用的是 XML 格式化文件 `myTestFormatFiles-f-x-c.Xml`，而另一些示例使用的是非 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2c4de-130">Some of the examples in this section use an XML format file, `myTestFormatFiles-f-x-c.Xml`, and other examples use a non-XML format file.</span></span> <span data-ttu-id="2c4de-131">这两种格式化文件都使用字符数据格式和非默认字段终止符 (,)。</span><span class="sxs-lookup"><span data-stu-id="2c4de-131">Both format files use character data formats and a non-default field terminator (,).</span></span>  
  
#### <a name="the-sample-non-xml-format-file"></a><span data-ttu-id="2c4de-132">示例非 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="2c4de-132">The Sample Non-XML Format File</span></span>  
 <span data-ttu-id="2c4de-133">下面的示例使用 **bcp** 基于 `myTestFormatFiles` 表生成一个 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2c4de-133">The following example uses **bcp** to generate an XML format file from the `myTestFormatFiles` table.</span></span> <span data-ttu-id="2c4de-134">`myTestFormatFiles.Fmt` 文件包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="2c4de-134">The `myTestFormatFiles.Fmt` file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     Col1         ""  
2       SQLCHAR       0       100     ","      2     Col2         SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      3     Col3         SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   4     Col4         SQL_Latin1_General_CP1_CI_AS  
```  
  
 <span data-ttu-id="2c4de-135">若要使用带 **format** 选项的 **bcp** 创建此格式化文件，请在 Windows 命令提示符下输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="2c4de-135">To use **bcp** with the **format** option to create this format file, at the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -f myTestFormatFiles.Fmt -T  
  
```  
  
 <span data-ttu-id="2c4de-136">有关创建格式化文件的详细信息，请参阅[创建格式化文件 (SQL Server)](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2c4de-136">For more information about creating a format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
#### <a name="the-sample-xml-format-file"></a><span data-ttu-id="2c4de-137">示例 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="2c4de-137">The Sample XML Format File</span></span>  
 <span data-ttu-id="2c4de-138">下面的示例使用 **bcp** 进行创建，以基于 `myTestFormatFiles` 表生成一个 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2c4de-138">The following example uses **bcp** to create to generate an XML format file from the `myTestFormatFiles` table.</span></span> <span data-ttu-id="2c4de-139">`myTestFormatFiles.Xml` 文件包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="2c4de-139">The `myTestFormatFiles.Xml` file contains the following information:</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 <span data-ttu-id="2c4de-140">若要使用带 **format** 选项的 **bcp** 创建此格式化文件，请在 Windows 命令提示符下输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="2c4de-140">To use **bcp** with the **format** option to create this format file, at the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -x -f myTestFormatFiles.Xml -T  
```  
  
### <a name="using-bcp"></a><span data-ttu-id="2c4de-141">使用 bcp</span><span class="sxs-lookup"><span data-stu-id="2c4de-141">Using bcp</span></span>  
 <span data-ttu-id="2c4de-142">下面的示例使用 **bcp** 将数据从 `myTestFormatFiles-c.Dat` 数据文件批量导入到示例数据库的 `HumanResources.myTestFormatFiles` 表中。</span><span class="sxs-lookup"><span data-stu-id="2c4de-142">The following example uses **bcp** to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the  sample database.</span></span> <span data-ttu-id="2c4de-143">此示例使用一个名为 `MyTestFormatFiles.Xml`的 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2c4de-143">This example uses an XML format file, `MyTestFormatFiles.Xml`.</span></span> <span data-ttu-id="2c4de-144">此示例在导入数据文件之前删除所有的现有表行。</span><span class="sxs-lookup"><span data-stu-id="2c4de-144">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="2c4de-145">在 Windows 命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="2c4de-145">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..myTestFormatFiles in C:\myTestFormatFiles-c.Dat -f C:\myTestFormatFiles.Xml -T  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2c4de-146"> 有关此命令的详细信息，请参阅 [bcp Utility](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="2c4de-146">For more information about this command, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
### <a name="using-bulk-insert"></a><span data-ttu-id="2c4de-147">使用 BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="2c4de-147">Using BULK INSERT</span></span>  
 <span data-ttu-id="2c4de-148">下面的示例使用 BULK INSERT 将数据从 `myTestFormatFiles-c.Dat` 数据文件大容量导入到 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 示例数据库中的 `HumanResources.myTestFormatFiles` 表中。</span><span class="sxs-lookup"><span data-stu-id="2c4de-148">The following example uses BULK INSERT to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="2c4de-149">此示例使用的是非 XML 格式化文件 `MyTestFormatFiles.Fmt`。</span><span class="sxs-lookup"><span data-stu-id="2c4de-149">This example uses a non-XML format file, `MyTestFormatFiles.Fmt`.</span></span> <span data-ttu-id="2c4de-150">此示例在导入数据文件之前删除所有的现有表行。</span><span class="sxs-lookup"><span data-stu-id="2c4de-150">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="2c4de-151">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="2c4de-151">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DELETE myTestFormatFiles;  
GO  
BULK INSERT myTestFormatFiles   
   FROM 'C:\myTestFormatFiles-c.Dat'   
   WITH (FORMATFILE = 'C:\myTestFormatFiles.Fmt');  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2c4de-152">有关此语句的详细信息，请参阅 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2c4de-152">For more information about this statement, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="using-the-openrowset-bulk-rowset-provider"></a><span data-ttu-id="2c4de-153">使用 OPENROWSET 大容量行集提供程序</span><span class="sxs-lookup"><span data-stu-id="2c4de-153">Using the OPENROWSET Bulk Rowset Provider</span></span>  
 <span data-ttu-id="2c4de-154">下面的示例使用 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 将数据从 `myTestFormatFiles-c.Dat` 数据文件大容量导入到 `HumanResources.myTestFormatFiles` 示例数据库的 `AdventureWorks` 表中。</span><span class="sxs-lookup"><span data-stu-id="2c4de-154">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the `AdventureWorks` sample database.</span></span> <span data-ttu-id="2c4de-155">此示例使用一个名为 `MyTestFormatFiles.Xml`的 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2c4de-155">This example uses an XML format file, `MyTestFormatFiles.Xml`.</span></span> <span data-ttu-id="2c4de-156">此示例在导入数据文件之前删除所有的现有表行。</span><span class="sxs-lookup"><span data-stu-id="2c4de-156">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="2c4de-157">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="2c4de-157">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
DELETE myTestFormatFiles;  
GO  
INSERT INTO myTestFormatFiles  
    SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestFormatFiles-c.Dat',  
      FORMATFILE='C:\myTestFormatFiles.Xml'       
      ) as t1 ;  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
 <span data-ttu-id="2c4de-158">用完示例表后，可以使用以下语句删除该表：</span><span class="sxs-lookup"><span data-stu-id="2c4de-158">When you finish using the sample table, you can drop it using the following statement:</span></span>  
  
```  
DROP TABLE myTestFormatFiles  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2c4de-159">有关 OPENROWSET BULK 子句的详细信息，请参阅 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2c4de-159">For more information about the OPENROWSET BULK clause, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="2c4de-160">其他示例</span><span class="sxs-lookup"><span data-stu-id="2c4de-160">Additional Examples</span></span>  
 [<span data-ttu-id="2c4de-161">创建格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2c4de-161">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
 [<span data-ttu-id="2c4de-162">使用格式化文件跳过表列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2c4de-162">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 [<span data-ttu-id="2c4de-163">使用格式化文件跳过数据字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2c4de-163">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
 [<span data-ttu-id="2c4de-164">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2c4de-164">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c4de-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c4de-165">See Also</span></span>  
 <span data-ttu-id="2c4de-166">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="2c4de-166">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="2c4de-167">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2c4de-167">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="2c4de-168">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2c4de-168">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="2c4de-169">[非 XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2c4de-169">[Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="2c4de-170">XML 格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2c4de-170">XML Format Files &#40;SQL Server&#41;</span></span>](xml-format-files-sql-server.md)  
  
  
