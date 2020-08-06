---
title: 批量导入和导出 XML 文档的示例 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- field terminators [SQL Server]
- bulk importing [SQL Server], data formats
- row terminators [SQL Server]
- OPENROWSET function, XML bulk load
- terminators [SQL Server]
- bulk exporting [SQL Server], data formats
- XML bulk load [SQL Server]
ms.assetid: dff99404-a002-48ee-910e-f37f013d946d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d72c84a7ed84503e0c88d2a46c808196903900b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589089"
---
# <a name="examples-of-bulk-import-and-export-of-xml-documents-sql-server"></a><span data-ttu-id="dcdbb-102">批量导入和导出 XML 文档的示例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dcdbb-102">Examples of Bulk Import and Export of XML Documents (SQL Server)</span></span>
    
##  <a name="you-can-bulk-import-xml-documents-into-a-ssnoversion-database-or-bulk-export-them-from-a-ssnoversion-database-this-topic-provides-examples-of-both"></a><a name="top"></a><span data-ttu-id="dcdbb-103">可以将 XML 文档大容量导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中，也可以从数据库中大容量导出 XML 文档 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-103">You can bulk import XML documents into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or bulk export them from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="dcdbb-104">本主题提供了这两种情况的示例。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-104">This topic provides examples of both.</span></span>  
  
 <span data-ttu-id="dcdbb-105">若要将数据从一个数据文件大容量导入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表或未分区视图，可以使用以下工具或命令：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-105">To bulk import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or non-partitioned view, you can use the following:</span></span>  
  
-   <span data-ttu-id="dcdbb-106">**bcp** 实用工具</span><span class="sxs-lookup"><span data-stu-id="dcdbb-106">**bcp** utility</span></span>  
  
     <span data-ttu-id="dcdbb-107">还可以使用 **bcp** 实用工具将数据从可执行 SELECT 语句的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的任意位置（包括分区视图）导出。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-107">You can also use the **bcp** utility to export data from anywhere in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that a SELECT statement works, including partitioned views.</span></span>  
  
-   <span data-ttu-id="dcdbb-108">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="dcdbb-108">BULK INSERT</span></span>  
  
-   <span data-ttu-id="dcdbb-109">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="dcdbb-109">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
 <span data-ttu-id="dcdbb-110">有关详细信息，请参阅[使用 Bcp 实用工具导入和导出大容量数据 &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)并[使用 BULK INSERT 或 OPENROWSET 导入大容量数据&#40;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)&#41; &#40;SQL Server&#41;。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-110">For more information, see [Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) and [Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dcdbb-111">示例</span><span class="sxs-lookup"><span data-stu-id="dcdbb-111">Examples</span></span>  
 <span data-ttu-id="dcdbb-112">下列示例说明了以下操作内容：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-112">The examples are the following:</span></span>  
  
-   <span data-ttu-id="dcdbb-113">A.</span><span class="sxs-lookup"><span data-stu-id="dcdbb-113">A.</span></span> [<span data-ttu-id="dcdbb-114">以二进制字节流的形式大容量导入 XML 数据</span><span class="sxs-lookup"><span data-stu-id="dcdbb-114">BULK importing XML data as a binary byte stream</span></span>](#binary_byte_stream)  
  
-   <span data-ttu-id="dcdbb-115">B.</span><span class="sxs-lookup"><span data-stu-id="dcdbb-115">B.</span></span> [<span data-ttu-id="dcdbb-116">在现有行中大容量导入 XML 数据</span><span class="sxs-lookup"><span data-stu-id="dcdbb-116">Bulk importing XML data in an existing row</span></span>](#existing_row)  
  
-   <span data-ttu-id="dcdbb-117">C.</span><span class="sxs-lookup"><span data-stu-id="dcdbb-117">C.</span></span> [<span data-ttu-id="dcdbb-118">从包含 DTD 的文件中大容量导入 XML 数据</span><span class="sxs-lookup"><span data-stu-id="dcdbb-118">Bulk importing XML data from a file that contains a DTD</span></span>](#file_contains_dtd)  
  
-   <span data-ttu-id="dcdbb-119">D.</span><span class="sxs-lookup"><span data-stu-id="dcdbb-119">D.</span></span> [<span data-ttu-id="dcdbb-120">使用格式化文件显式指定字段终止符</span><span class="sxs-lookup"><span data-stu-id="dcdbb-120">Specifying the field terminator explicitly using a format file</span></span>](#field_terminator_in_format_file)  
  
-   <span data-ttu-id="dcdbb-121">E.</span><span class="sxs-lookup"><span data-stu-id="dcdbb-121">E.</span></span> [<span data-ttu-id="dcdbb-122">大容量导出 XML 数据</span><span class="sxs-lookup"><span data-stu-id="dcdbb-122">Bulk exporting XML data</span></span>](#bulk_export_xml_data)  
  
###  <a name="a-bulk-importing-xml-data-as-a-binary-byte-stream"></a><a name="binary_byte_stream"></a> <span data-ttu-id="dcdbb-123">A.</span><span class="sxs-lookup"><span data-stu-id="dcdbb-123">A.</span></span> <span data-ttu-id="dcdbb-124">以二进制字节流的形式大容量导入 XML 数据</span><span class="sxs-lookup"><span data-stu-id="dcdbb-124">Bulk importing XML data as a binary byte stream</span></span>  
 <span data-ttu-id="dcdbb-125">在从文件大容量导入 XML 数据时，如果文件中包含要应用的编码声明，则应在 OPENROWSET(BULK…) 子句中指定 SINGLE_BLOB 选项。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-125">When you bulk import XML data from a file that contains an encoding declaration that you want to apply, specify the SINGLE_BLOB option in the OPENROWSET(BULK...) clause.</span></span> <span data-ttu-id="dcdbb-126">SINGLE_BLOB 选项可确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 XML 分析器根据 XML 声明中指定的编码方案导入数据。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-126">The SINGLE_BLOB option makes sure that the XML parser in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] imports the data according to the encoding scheme specified in the XML declaration.</span></span>  
  
#### <a name="sample-table"></a><span data-ttu-id="dcdbb-127">示例表</span><span class="sxs-lookup"><span data-stu-id="dcdbb-127">Sample Table</span></span>  
 <span data-ttu-id="dcdbb-128">若要测试示例 A，必须创建示例表 `T`。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-128">To test example A, you must create sample table `T`.</span></span>  
  
```  
USE tempdb  
CREATE TABLE T (IntCol int, XmlCol xml);  
GO  
```  
  
#### <a name="sample-data-file"></a><span data-ttu-id="dcdbb-129">示例数据文件</span><span class="sxs-lookup"><span data-stu-id="dcdbb-129">Sample Data File</span></span>  
 <span data-ttu-id="dcdbb-130">在运行示例 A 之前，必须先创建一个 UTF-8 编码文件 (`C:\SampleFolder\SampleData3.txt`)，该文件应包含指定 `UTF-8` 编码方案的以下示例实例。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-130">Before you can run example A, you must create a UTF-8 encoded file (`C:\SampleFolder\SampleData3.txt`) that contains the following sample instance that specifies the `UTF-8` encoding scheme.</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<Root>  
          <ProductDescription ProductModelID="5">  
             <Summary>Some Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-a"></a><span data-ttu-id="dcdbb-131">示例 A</span><span class="sxs-lookup"><span data-stu-id="dcdbb-131">Example A</span></span>  
 <span data-ttu-id="dcdbb-132">此示例使用 `SINGLE_BLOB` 语句中的 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 选项从名为 `SampleData3.txt` 的文件中导入数据，并在包含单列的示例表 `T`中插入一个 XML 实例。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-132">This example uses the `SINGLE_BLOB` option in an `INSERT ... SELECT * FROM OPENROWSET(BULK...)` statement to import data from a file named `SampleData3.txt` and insert an XML instance in the single-column table, sample table `T`.</span></span>  
  
```  
INSERT INTO T(XmlCol)  
SELECT * FROM OPENROWSET(  
   BULK 'c:\SampleFolder\SampleData3.txt',  
   SINGLE_BLOB) AS x;  
```  
  
#### <a name="remarks"></a><span data-ttu-id="dcdbb-133">备注</span><span class="sxs-lookup"><span data-stu-id="dcdbb-133">Remarks</span></span>  
 <span data-ttu-id="dcdbb-134">在这个例子中，通过使用 SINGLE_BLOB，可以避免 XML 文档的编码（由 XML 编码声明所指定）与服务器隐含使用的字符串代码页不匹配的问题。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-134">By using SINGLE_BLOB in this case, you can avoid a mismatch between the encoding of the XML document (as specified by the XML encoding declaration) and the string codepage implied by the server.</span></span>  
  
 <span data-ttu-id="dcdbb-135">如果使用 NCLOB 或 CLOB 数据类型且遇到代码页或编码冲突，则必须执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-135">If you use NCLOB or CLOB data types and run into a codepage or encoding conflict, you must do one of the following:</span></span>  
  
-   <span data-ttu-id="dcdbb-136">删除 XML 声明，以成功导入 XML 数据文件的内容。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-136">Remove the XML declaration to successfully import the contents of the XML data file.</span></span>  
  
-   <span data-ttu-id="dcdbb-137">在查询的 CODEPAGE 选项中指定一个代码页，该代码页须与 XML 声明中使用的编码方案相匹配。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-137">Specify a code page in the CODEPAGE option of the query that matches the encoding scheme that is used in the XML declaration.</span></span>  
  
-   <span data-ttu-id="dcdbb-138">使用非 Unicode XML 编码方案匹配或解析数据库排序规则设置。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-138">Match, or resolve, the database collation settings with a non-Unicode XML encoding scheme.</span></span>  
  
 <span data-ttu-id="dcdbb-139">[[返回页首]](#top)</span><span class="sxs-lookup"><span data-stu-id="dcdbb-139">[&#91;Top&#93;](#top)</span></span>  
  
###  <a name="b-bulk-importing-xml-data-in-an-existing-row"></a><a name="existing_row"></a> <span data-ttu-id="dcdbb-140">B.</span><span class="sxs-lookup"><span data-stu-id="dcdbb-140">B.</span></span> <span data-ttu-id="dcdbb-141">将 XML 数据大容量导入现有行中</span><span class="sxs-lookup"><span data-stu-id="dcdbb-141">Bulk importing XML data in an existing row</span></span>  
 <span data-ttu-id="dcdbb-142">此示例使用 `OPENROWSET` 大容量行集提供程序向示例表 `T`中的现有行添加一个 XML 实例。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-142">This example uses the `OPENROWSET` bulk rowset provider to add an XML instance to an existing row or rows in sample table `T`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dcdbb-143">若要运行此示例，必须先完成示例 A 中提供的测试脚本。该示例创建了 `tempdb.dbo.T` 表，并从 `SampleData3.txt`中大容量导入数据。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-143">To run this example, you must first complete the test script provided in example A. That example creates the `tempdb.dbo.T` table and bulk imports data from `SampleData3.txt`.</span></span>  
  
#### <a name="sample-data-file"></a><span data-ttu-id="dcdbb-144">示例数据文件</span><span class="sxs-lookup"><span data-stu-id="dcdbb-144">Sample Data File</span></span>  
 <span data-ttu-id="dcdbb-145">示例 B 使用的是上例所使用 `SampleData3.txt` 示例数据文件的修改版本。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-145">Example B uses a modified version of the `SampleData3.txt` sample data file from the preceding example.</span></span> <span data-ttu-id="dcdbb-146">若要运行此示例，请按如下所示修改此文件的内容：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-146">To run this example, modify the content of this file as follows:</span></span>  
  
```  
<Root>  
          <ProductDescription ProductModelID="10">  
             <Summary>Some New Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-b"></a><span data-ttu-id="dcdbb-147">示例 B</span><span class="sxs-lookup"><span data-stu-id="dcdbb-147">Example B</span></span>  
  
```  
-- Query before update shows initial state of XmlCol values.  
SELECT * FROM T  
UPDATE T  
SET XmlCol =(  
SELECT * FROM OPENROWSET(  
   BULK 'C:\SampleFolder\SampleData3.txt',  
           SINGLE_BLOB  
) AS x  
)  
WHERE IntCol = 1;  
GO  
```  
  
 <span data-ttu-id="dcdbb-148">[[返回页首]](#top)</span><span class="sxs-lookup"><span data-stu-id="dcdbb-148">[&#91;Top&#93;](#top)</span></span>  
  
###  <a name="c-bulk-importing-xml-data-from-a-file-that-contains-a-dtd"></a><a name="file_contains_dtd"></a> <span data-ttu-id="dcdbb-149">C.</span><span class="sxs-lookup"><span data-stu-id="dcdbb-149">C.</span></span> <span data-ttu-id="dcdbb-150">从包含 DTD 的文件中大容量导入 XML 数据</span><span class="sxs-lookup"><span data-stu-id="dcdbb-150">Bulk importing XML data from a file that contains a DTD</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dcdbb-151">若非您的 XML 环境有特殊要求，建议不要启用对文档类型定义 (DTD) 的支持。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-151">We recommended that you not enable support for Document Type Definitions (DTDs) if it is not required in your XML environment.</span></span> <span data-ttu-id="dcdbb-152">启用 DTD 支持会增加服务器的可攻击外围应用，并且可能会使它受到拒绝服务攻击。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-152">Turning on DTD support increases the attackable surface area of your server, and may expose it to a denial-of-service attack.</span></span> <span data-ttu-id="dcdbb-153">如果必须启用 DTD 支持，可以通过仅处理可信的 XML 文档来降低安全风险。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-153">If you must enable DTD support, you can reduce this security risk by processing only trusted XML documents.</span></span>  
  
 <span data-ttu-id="dcdbb-154">在尝试使用 [bcp](../../tools/bcp-utility.md) 命令从包含 DTD 的文件中导入 XML 数据的过程中，可能会出现如下错误：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-154">During an attempt to use a [bcp](../../tools/bcp-utility.md) command to import XML data from a file that contains a DTD, an error similar to the following can occur:</span></span>  
  
 <span data-ttu-id="dcdbb-155">“SQLState = 42000，NativeError = 6359”</span><span class="sxs-lookup"><span data-stu-id="dcdbb-155">"SQLState = 42000, NativeError = 6359"</span></span>  
  
 <span data-ttu-id="dcdbb-156">“错误 = [Microsoft][SQL Server Native Client][SQL Server]不允许使用内部子集 DTD 分析 XML。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-156">"Error = [Microsoft][SQL Server Native Client][ SQL Server]Parsing XML with internal subset DTDs not allowed.</span></span> <span data-ttu-id="dcdbb-157">请将 CONVERT 与样式选项 2 一起使用，以启用有限的内部子集 DTD 支持。”</span><span class="sxs-lookup"><span data-stu-id="dcdbb-157">Use CONVERT with style option 2 to enable limited internal subset DTD support."</span></span>  
  
 <span data-ttu-id="dcdbb-158">“BCP 复制 %s 失败”</span><span class="sxs-lookup"><span data-stu-id="dcdbb-158">"BCP copy %s failed"</span></span>  
  
 <span data-ttu-id="dcdbb-159">若要解决此问题，可以使用 `OPENROWSET(BULK...)` 函数，并在命令的 `CONVERT` 子句中指定 `SELECT` 选项，以从包含 DTD 的数据文件中导入 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-159">To work around this problem, you can import XML data from a data file that contains a DTD by using the `OPENROWSET(BULK...)` function and then specifying the `CONVERT` option in the `SELECT` clause of the command.</span></span> <span data-ttu-id="dcdbb-160">该命令的基本语法如下：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-160">The basic syntax for the command is:</span></span>  
  
 `INSERT ... SELECT CONVERT(...) FROM OPENROWSET(BULK...)`  
  
#### <a name="sample-data-file"></a><span data-ttu-id="dcdbb-161">示例数据文件</span><span class="sxs-lookup"><span data-stu-id="dcdbb-161">Sample Data File</span></span>  
 <span data-ttu-id="dcdbb-162">在测试此批量导入示例之前，需要先创建一个包含以下示例实例的文件 (`C:\temp\Dtdfile.xml`)：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-162">Before you can test this bulk import example, create a file (`C:\temp\Dtdfile.xml`) that contains the following sample instance:</span></span>  
  
```  
<!DOCTYPE DOC [<!ATTLIST elem1 attr1 CDATA "defVal1">]><elem1>January</elem1>  
```  
  
#### <a name="sample-table"></a><span data-ttu-id="dcdbb-163">示例表</span><span class="sxs-lookup"><span data-stu-id="dcdbb-163">Sample Table</span></span>  
 <span data-ttu-id="dcdbb-164">示例 C 使用由以下 `T1` 语句创建的 `CREATE TABLE` 示例表：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-164">Example C uses the `T1` sample table that is created by the following `CREATE TABLE` statement:</span></span>  
  
```  
USE tempdb;  
CREATE TABLE T1(XmlCol xml);  
GO  
```  
  
#### <a name="example-c"></a><span data-ttu-id="dcdbb-165">示例 C</span><span class="sxs-lookup"><span data-stu-id="dcdbb-165">Example C</span></span>  
 <span data-ttu-id="dcdbb-166">此示例使用 `OPENROWSET(BULK...)` ，并在 `CONVERT` 子句中指定了 `SELECT` 选项，从而将 XML 数据从 `Dtdfile.xml` 导入到了示例表 `T1`中。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-166">This example uses `OPENROWSET(BULK...)` and specifies the `CONVERT` option in the `SELECT` clause to import the XML data from `Dtdfile.xml` into sample table `T1`.</span></span>  
  
```  
INSERT T1  
  SELECT CONVERT(xml, BulkColumn, 2) FROM   
    OPENROWSET(Bulk 'c:\temp\Dtdfile.xml', SINGLE_BLOB) [rowsetresults];  
```  
  
 <span data-ttu-id="dcdbb-167">执行 `INSERT` 语句后，会将 DTD 从 XML 中提取出来，并存储到 `T1` 表中。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-167">After the `INSERT` statement executes, the DTD is stripped from the XML and stored in the `T1` table.</span></span>  
  
 <span data-ttu-id="dcdbb-168">[[返回页首]](#top)</span><span class="sxs-lookup"><span data-stu-id="dcdbb-168">[&#91;Top&#93;](#top)</span></span>  
  
###  <a name="d-specifying-the-field-terminator-explicitly-using-a-format-file"></a><a name="field_terminator_in_format_file"></a> <span data-ttu-id="dcdbb-169">D.</span><span class="sxs-lookup"><span data-stu-id="dcdbb-169">D.</span></span> <span data-ttu-id="dcdbb-170">使用格式化文件显式指定字段终止符</span><span class="sxs-lookup"><span data-stu-id="dcdbb-170">Specifying the field terminator explicitly using a format file</span></span>  
 <span data-ttu-id="dcdbb-171">下面的示例说明如何大容量导入 XML 文档 `Xmltable.dat`。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-171">The following example shows how to bulk import the following XML document, `Xmltable.dat`.</span></span>  
  
#### <a name="sample-data-file"></a><span data-ttu-id="dcdbb-172">示例数据文件</span><span class="sxs-lookup"><span data-stu-id="dcdbb-172">Sample Data File</span></span>  
 <span data-ttu-id="dcdbb-173">`Xmltable.dat` 中的文档包含两个 XML 值，每行一个。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-173">The document in `Xmltable.dat` contains two XML values, one for each row.</span></span> <span data-ttu-id="dcdbb-174">第一个 XML 值的编码为 UTF-16，第二个值的编码为 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-174">The first XML value is encoded with UTF-16, and the second value is encoded with UTF-8.</span></span>  
  
 <span data-ttu-id="dcdbb-175">下面的十六进制转储显示了此数据文件的内容：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-175">The contents of this data file are shown in the following Hex dump:</span></span>  
  
```  
FF FE 3C 00 3F 00 78 00-6D 00 6C 00 20 00 76 00  *..<.?.x.m.l. .v.*  
65 00 72 00 73 00 69 00-6F 00 6E 00 3D 00 22 00  *e.r.s.i.o.n.=.".*  
31 00 2E 00 30 00 22 00-20 00 65 00 6E 00 63 00  *1...0.". .e.n.c.*  
6F 00 64 00 69 00 6E 00-67 00 3D 00 22 00 75 00  *o.d.i.n.g.=.".u.*  
74 00 66 00 2D 00 31 00-36 00 22 00 3F 00 3E 00  *t.f.-.1.6.".?.>.*  
3C 00 72 00 6F 00 6F 00-74 00 3E 00 A2 4F 9C 76  *<.r.o.o.t.>..O.v*  
0C FA 77 E4 80 00 89 00-00 06 90 06 91 2E 9B 2E  *..w.............*  
99 34 A2 34 86 00 83 02-92 20 7F 02 4E C5 E4 A3  *.4.4..... ..N...*  
34 B2 B7 B3 B7 FE F8 FF-F8 00 3C 00 2F 00 72 00  *4.........<./.r.*  
6F 00 6F 00 74 00 3E 00-00 00 00 00 7A EF BB BF  *o.o.t.>.....z...*  
3C 3F 78 6D 6C 20 76 65-72 73 69 6F 6E 3D 22 31  *<?xml version="1*  
2E 30 22 20 65 6E 63 6F-64 69 6E 67 3D 22 75 74  *.0" encoding="ut*  
66 2D 38 22 3F 3E 3C 72-6F 6F 74 3E E4 BE A2 E7  *f-8"?><root>....*  
9A 9C EF A8 8C EE 91 B7-C2 80 C2 89 D8 80 DA 90  *................*  
E2 BA 91 E2 BA 9B E3 92-99 E3 92 A2 C2 86 CA 83  *................*  
E2 82 92 C9 BF EC 95 8E-EA 8F A4 EB 88 B4 EB 8E  *................*  
B7 EF BA B7 EF BF B8 C3-B8 3C 2F 72 6F 6F 74 3E  *.........</root>*  
00 00 00 00 7A                                   *....z*  
```  
  
#### <a name="sample-table"></a><span data-ttu-id="dcdbb-176">示例表</span><span class="sxs-lookup"><span data-stu-id="dcdbb-176">Sample Table</span></span>  
 <span data-ttu-id="dcdbb-177">大容量导入或导出 XML 文档时，应当使用在任何文档中都不可能出现的 [字段终止符](specify-field-and-row-terminators-sql-server.md) ；例如，在连续四个 Null (`\0`) 后紧跟字母 `z`： `\0\0\0\0z`。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-177">When you bulk import or export an XML document, you should use a [field terminator](specify-field-and-row-terminators-sql-server.md) that cannot possibly appear in any of the documents; for example, a series of four nulls (`\0`) followed by the letter `z`: `\0\0\0\0z`.</span></span>  
  
 <span data-ttu-id="dcdbb-178">此示例说明如何为 `xTable` 示例表使用此字段终止符。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-178">This example shows how to use this field terminator for the `xTable` sample table.</span></span> <span data-ttu-id="dcdbb-179">若要创建此示例表，请使用下列 `CREATE TABLE` 语句：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-179">To create this sample table, use the following `CREATE TABLE` statement:</span></span>  
  
```  
USE tempdb;  
CREATE TABLE xTable (xCol xml);  
GO  
```  
  
#### <a name="sample-format-file"></a><span data-ttu-id="dcdbb-180">示例格式化文件</span><span class="sxs-lookup"><span data-stu-id="dcdbb-180">Sample Format File</span></span>  
 <span data-ttu-id="dcdbb-181">必须在格式化文件中指定字段终止符。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-181">The field terminator must be specified in the format file.</span></span> <span data-ttu-id="dcdbb-182">示例 D 使用了一个名为 `Xmltable.fmt` 的非 XML 格式化文件，该文件包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-182">Example D uses a non-XML format file named `Xmltable.fmt` that contains the following:</span></span>  
  
```  
9.0  
1  
1       SQLBINARY     0       0       "\0\0\0\0z"    1     xCol         ""  
```  
  
 <span data-ttu-id="dcdbb-183">可以使用此格式化文件并通过 `xTable` 命令、 `bcp` 语句或 `BULK INSERT` 语句将 XML 文档大容量导入到 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 表中。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-183">You can use this format file to bulk import XML documents into the `xTable` table by using a `bcp` command or a `BULK INSERT` or `INSERT ... SELECT * FROM OPENROWSET(BULK...)` statement.</span></span>  
  
#### <a name="example-d"></a><span data-ttu-id="dcdbb-184">示例 D</span><span class="sxs-lookup"><span data-stu-id="dcdbb-184">Example D</span></span>  
 <span data-ttu-id="dcdbb-185">此示例在 `Xmltable.fmt` 语句中使用 `BULK INSERT` 格式化文件来导入 XML 数据文件 `Xmltable.dat`中的内容。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-185">This example uses the `Xmltable.fmt` format file in a `BULK INSERT` statement to import the contents of an XML data file named `Xmltable.dat`.</span></span>  
  
```  
BULK INSERT xTable   
FROM 'C:\Xmltable.dat'  
WITH (FORMATFILE = 'C:\Xmltable.fmt');  
GO  
```  
  
 <span data-ttu-id="dcdbb-186">[[返回页首]](#top)</span><span class="sxs-lookup"><span data-stu-id="dcdbb-186">[&#91;Top&#93;](#top)</span></span>  
  
###  <a name="e-bulk-exporting-xml-data"></a><a name="bulk_export_xml_data"></a> <span data-ttu-id="dcdbb-187">E.</span><span class="sxs-lookup"><span data-stu-id="dcdbb-187">E.</span></span> <span data-ttu-id="dcdbb-188">大容量导出 XML 数据</span><span class="sxs-lookup"><span data-stu-id="dcdbb-188">Bulk exporting XML data</span></span>  
 <span data-ttu-id="dcdbb-189">下面的示例使用 `bcp` 命令和同一个 XML 格式化文件从上一示例所创建的表中大容量导出 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-189">The following example uses `bcp` to bulk export XML data from the table that is created in the preceding example by using the same XML format file.</span></span> <span data-ttu-id="dcdbb-190">在下面的 `bcp` 命令中， `<server_name>` 和 `<instance_name>` 代表必须使用相应的值替换的占位符：</span><span class="sxs-lookup"><span data-stu-id="dcdbb-190">In the following `bcp` command, `<server_name>` and `<instance_name>` represent placeholders that must be replaced with appropriate values:</span></span>  
  
```  
bcp bulktest..xTable out a-wn.out -N -T -S<server_name>\<instance_name>  
```  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dcdbb-191">不保存 XML 编码。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-191">does not save the XML encoding when XML data is persisted in the database.</span></span> <span data-ttu-id="dcdbb-192">因此，在导出 XML 数据时，XML 字段的原始编码将不可用。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-192">Therefore, the original encoding of XML fields is not available when XML data is exported.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dcdbb-193">导出 XML 数据时，使用 UTF-16 编码。</span><span class="sxs-lookup"><span data-stu-id="dcdbb-193">uses UTF-16 encoding when exporting XML data.</span></span>  
  
 <span data-ttu-id="dcdbb-194">[[返回页首]](#top)</span><span class="sxs-lookup"><span data-stu-id="dcdbb-194">[&#91;Top&#93;](#top)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcdbb-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dcdbb-195">See Also</span></span>  
 <span data-ttu-id="dcdbb-196">[INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dcdbb-196">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="dcdbb-197">[SELECT 子句 (Transact-SQL)](/sql/t-sql/queries/select-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dcdbb-197">[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span></span>  
 <span data-ttu-id="dcdbb-198">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="dcdbb-198">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="dcdbb-199">[批量导入和导出数据 (SQL Server)](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dcdbb-199">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="dcdbb-200">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dcdbb-200">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="dcdbb-201">OPENROWSET (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dcdbb-201">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
