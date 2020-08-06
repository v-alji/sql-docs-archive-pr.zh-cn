---
title: 使用格式化文件将表列映射到数据文件字段 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- mapping columns to fields during import [SQL Server]
- format files [SQL Server], mapping columns to fields
ms.assetid: e7ee4f7e-24c4-4eb7-84d2-41e57ccc1ef1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c7de0b5ce486f187a1bdd27197984aa3c411f4a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579583"
---
# <a name="use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server"></a><span data-ttu-id="86306-102">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="86306-102">Use a Format File to Map Table Columns to Data-File Fields (SQL Server)</span></span>
  <span data-ttu-id="86306-103">数据文件中包含的字段的排列顺序可能不同于表中相应列的顺序。</span><span class="sxs-lookup"><span data-stu-id="86306-103">A data file can contain fields arranged in a different order from the corresponding columns in the table.</span></span> <span data-ttu-id="86306-104">本主题介绍了非 XML 格式化文件和 XML 格式化文件，它们经过修改可容纳字段排列顺序不同于表列顺序的数据文件。</span><span class="sxs-lookup"><span data-stu-id="86306-104">This topic presents both non-XML and XML format files that have been modified to accommodate a data file whose fields are arranged in a different order from the table columns.</span></span> <span data-ttu-id="86306-105">修改后的格式化文件可将数据字段映射到与之相应的表列。</span><span class="sxs-lookup"><span data-stu-id="86306-105">The modified format file maps the data fields to their corresponding table columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86306-106">可以使用非 XML 格式化文件或 XML 格式化文件将数据文件大容量导入表中，方法是使用**bcp**命令、BULK INSERT 语句或 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) 语句。</span><span class="sxs-lookup"><span data-stu-id="86306-106">Either a non-XML format file or an XML format file can be used to bulk import a data file into the table by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="86306-107">有关详细信息，请参阅[使用格式化文件批量导入数据 (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="86306-107">For more information, see [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
## <a name="sample-table-and-data-file"></a><span data-ttu-id="86306-108">示例表和数据文件</span><span class="sxs-lookup"><span data-stu-id="86306-108">Sample Table and Data File</span></span>  
 <span data-ttu-id="86306-109">本主题中修改的格式化文件示例基于下面的表和数据文件。</span><span class="sxs-lookup"><span data-stu-id="86306-109">The examples of modified format files in this topic are based on the following table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="86306-110">示例表</span><span class="sxs-lookup"><span data-stu-id="86306-110">Sample Table</span></span>  
 <span data-ttu-id="86306-111">本主题中的示例要求在 `myTestOrder` 示例数据库中的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 架构下创建名为 `dbo` 的表。</span><span class="sxs-lookup"><span data-stu-id="86306-111">The examples in this topic require that a table named `myTestOrder` be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="86306-112">若要创建此表，请在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查询编辑器中执行以下代码：</span><span class="sxs-lookup"><span data-stu-id="86306-112">To create this table, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestOrder   
   (  
   Col1 smallint,  
   Col2 nvarchar(50) ,  
   Col3 nvarchar(50) ,   
   Col4 nvarchar(50)   
   );  
GO  
  
```  
  
### <a name="data-file"></a><span data-ttu-id="86306-113">数据文件</span><span class="sxs-lookup"><span data-stu-id="86306-113">Data File</span></span>  
 <span data-ttu-id="86306-114">数据文件 `myTestOrder-c.txt`包含下列记录：</span><span class="sxs-lookup"><span data-stu-id="86306-114">The data file, `myTestOrder-c.txt`, contains the following records:</span></span>  
  
```  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
  
```  
  
 <span data-ttu-id="86306-115">若要将数据从 `myTestSkipCol2-c.dat` 大容量导入 `myTestSkipCol` 表中，格式化文件必须将第一个数据字段映射到 `Col3`、将第二个数据字段映射到 `Col2`、将第三个数据字段映射到 `Col1`、将第四个数据字段映射到 `Col4`。</span><span class="sxs-lookup"><span data-stu-id="86306-115">To bulk import data from `myTestSkipCol2-c.dat` into the `myTestSkipCol` table, the format file must map the first data field to `Col3`, the second data field to `Col2`, the third data field to `Col1`, and the fourth data field to `Col4`.</span></span>  
  
## <a name="using-a-non-xml-format-file"></a><span data-ttu-id="86306-116">使用非 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="86306-116">Using a Non-XML Format File</span></span>  
 <span data-ttu-id="86306-117">可通过更改列的顺序值来更改列映射的顺序，以指示相应数据字段的位置。</span><span class="sxs-lookup"><span data-stu-id="86306-117">You can change the order of a column mapping by changing the order value for the column to indicate the position of the corresponding data field.</span></span>  
  
 <span data-ttu-id="86306-118">下面的非 XML 格式化文件示例提供了一个格式化文件 `myTestOrder.fmt`，它将 `myTestOrder-c.txt` 中的字段映射到 `myTestOrder` 表中的列。</span><span class="sxs-lookup"><span data-stu-id="86306-118">The following sample non-XML format file presents a format file, `myTestOrder.fmt`, that maps the fields in `myTestOrder-c.txt` to the columns of the `myTestOrder` table.</span></span> <span data-ttu-id="86306-119">有关如何创建数据文件和表的信息，请参阅本主题前面的“示例表和数据文件”部分。</span><span class="sxs-lookup"><span data-stu-id="86306-119">For information about how to create the data file and table, see "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="86306-120">该格式化文件使用字符数据格式。</span><span class="sxs-lookup"><span data-stu-id="86306-120">The format file uses character data format.</span></span>  
  
 <span data-ttu-id="86306-121">格式化文件中包含下列信息：</span><span class="sxs-lookup"><span data-stu-id="86306-121">The format file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       100     ","     3     Col3               SQL_Latin1_General_CP1_CI_AS  
2       SQLCHAR       0       100     ","     2     Col2               SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       7       ","     1     Col1               ""  
4       SQLCHAR       0       100     "\r\n"  4     Col4               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="86306-122">有关非 XML 格式文件布局的详细信息，请参阅[非 XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="86306-122">For more information about the layout of non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="86306-123">示例</span><span class="sxs-lookup"><span data-stu-id="86306-123">Example</span></span>  
 <span data-ttu-id="86306-124">下面的示例使用非 XML 格式化文件 `BULK INSERT`，通过 `myTestOrder-c.txt` 语句将数据文件 `myTestOrder` 中的数据大容量导入示例表 `myTestOrder.fmt` 中。</span><span class="sxs-lookup"><span data-stu-id="86306-124">The following example uses a `BULK INSERT` statement to bulk import data from the `myTestOrder-c.txt` data file into the `myTestOrder` sample table by using the `myTestOrder.fmt` non-XML format file.</span></span>  
  
 <span data-ttu-id="86306-125">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行：</span><span class="sxs-lookup"><span data-stu-id="86306-125">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestOrder  
FROM 'C:\myTestOrder-c.txt'   
WITH (formatfile='C:\myTestOrder.fmt');  
GO  
  
```  
  
## <a name="using-an-xml-format-file"></a><span data-ttu-id="86306-126">使用 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="86306-126">Using an XML Format File</span></span>  
 <span data-ttu-id="86306-127">下面的非 XML 格式化文件示例提供了一个格式化文件 `myTestOrder.xml`，它将 `myTestOrder-c.txt` 中的字段映射到 `myTestOrder` 表中的列。有关如何创建数据文件和表的信息，请参阅本主题前面的“示例表和数据文件”部分。</span><span class="sxs-lookup"><span data-stu-id="86306-127">The following sample non-XML format file presents a format file, `myTestOrder.xml`, that maps the fields in `myTestOrder-c.txt` to the columns of the `myTestOrder` table For information about how to create the data file and table, see "Sample Table and Data File," earlier in this topic.</span></span>  
  
 <span data-ttu-id="86306-128">`myTestOrder.xml` 格式化文件包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="86306-128">The `myTestOrder.xml` format file contains the following information:</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="3" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="1" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="86306-129">有关 XML 架构语法和 XML 格式化文件的其他示例的信息，请参阅 [XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="86306-129">For information about the syntax of the XML Schema and additional samples of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="86306-130">示例</span><span class="sxs-lookup"><span data-stu-id="86306-130">Example</span></span>  
 <span data-ttu-id="86306-131">下面的示例使用 XML 格式化文件 `OPENROWSET` ，通过 `myTestOrder-c.txt` 大容量行集提供程序将数据文件 `myTestOrder` 中的数据导入示例表 `myTestOrder.xml` 中。</span><span class="sxs-lookup"><span data-stu-id="86306-131">The following example uses the `OPENROWSET` bulk rowset provider to import data from the `myTestOrder-c.txt` data file into the `myTestOrder` sample table by using the `myTestOrder.xml` XML format file.</span></span> <span data-ttu-id="86306-132">`INSERT... SELECT` 语句指定选择列表中的列。</span><span class="sxs-lookup"><span data-stu-id="86306-132">The `INSERT... SELECT` statement specifies the column list in the select list.</span></span>  
  
 <span data-ttu-id="86306-133">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行下列代码：</span><span class="sxs-lookup"><span data-stu-id="86306-133">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestOrder   
  SELECT Col1, Col2, Col3, Col4  
      FROM  OPENROWSET(BULK  'C:\myTestOrder-c.txt',  
      FORMATFILE='C:\myTestOrder.Xml'    
       ) AS t1;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="86306-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86306-134">See Also</span></span>  
 <span data-ttu-id="86306-135">[使用格式化文件跳过表列 (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="86306-135">[Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span></span>  
 [<span data-ttu-id="86306-136">使用格式化文件跳过数据字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="86306-136">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
  
