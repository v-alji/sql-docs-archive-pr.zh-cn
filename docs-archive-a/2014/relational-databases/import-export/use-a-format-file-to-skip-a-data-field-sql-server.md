---
title: 使用格式化文件跳过数据字段 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], skipping data fields
- skipping data fields when importing
ms.assetid: 6a76517e-983b-47a1-8f02-661b99859a8b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d3f78c3c97c5bbe862867d5f51ff35f57d147df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591895"
---
# <a name="use-a-format-file-to-skip-a-data-field-sql-server"></a><span data-ttu-id="bb9ef-102">使用格式化文件跳过数据字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bb9ef-102">Use a Format File to Skip a Data Field (SQL Server)</span></span>
  <span data-ttu-id="bb9ef-103">数据文件所包含的字段数可能大于表中的列数。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-103">A data file can contain more fields than the number of columns in the table.</span></span> <span data-ttu-id="bb9ef-104">本主题说明了通过修改非 XML 和 XML 格式化文件，将表中的列映射到相应的数据字段并忽略额外字段，从而能够使用具有较多字段的数据文件。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-104">This topic describes modifying both non-XML and XML format files to accommodate a data file with more fields by mapping the table columns to the corresponding data fields and ignoring the extra fields.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb9ef-105">可以使用非 XML 或 XML 格式化文件将数据文件大容量导入表中，方法是使用**bcp**命令、BULK INSERT 语句或 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) 语句。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-105">Either a non-XML or XML format file can be used to bulk import a data file into the table by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="bb9ef-106">有关详细信息，请参阅[使用格式化文件批量导入数据 (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-106">For more information, see [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
## <a name="sample-data-file-and-table"></a><span data-ttu-id="bb9ef-107">示例数据文件和表</span><span class="sxs-lookup"><span data-stu-id="bb9ef-107">Sample Data File and Table</span></span>  
 <span data-ttu-id="bb9ef-108">本主题中修改的格式化文件示例基于下面的表和数据文件。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-108">The examples of modified format files in this topic are based on the following table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="bb9ef-109">示例表</span><span class="sxs-lookup"><span data-stu-id="bb9ef-109">Sample Table</span></span>  
 <span data-ttu-id="bb9ef-110">这些示例要求在 `myTestSkipField` 示例数据库中的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 架构下创建名为 `dbo` 的表。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-110">The examples require that a table named `myTestSkipField` be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="bb9ef-111">若要创建此表，请在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查询编辑器中运行以下代码：</span><span class="sxs-lookup"><span data-stu-id="bb9ef-111">To create this table, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestSkipField   
   (  
   PersonID smallint,  
   FirstName nvarchar(50) ,  
   LastName nvarchar(50)   
   );  
GO  
```  
  
### <a name="sample-data-file"></a><span data-ttu-id="bb9ef-112">示例数据文件</span><span class="sxs-lookup"><span data-stu-id="bb9ef-112">Sample Data File</span></span>  
 <span data-ttu-id="bb9ef-113">数据文件 `myTestSkipField-c.dat`包含下列记录：</span><span class="sxs-lookup"><span data-stu-id="bb9ef-113">The data file, `myTestSkipField-c.dat`, contains the following records:</span></span>  
  
```  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
```  
  
 <span data-ttu-id="bb9ef-114">若要将数据从 `myTestSkipField-c.dat` 大容量导入至 `myTestSkipField` 表，则该格式化文件必须进行下列操作：</span><span class="sxs-lookup"><span data-stu-id="bb9ef-114">To bulk import data from `myTestSkipField-c.dat` into the `myTestSkipField` table, the format file must do the following:</span></span>  
  
-   <span data-ttu-id="bb9ef-115">将第一个数据字段映射到第一列 `PersonID`。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-115">Map the first data field to the first column, `PersonID`.</span></span>  
  
-   <span data-ttu-id="bb9ef-116">跳过第二个数据字段。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-116">Skip the second data field.</span></span>  
  
-   <span data-ttu-id="bb9ef-117">将第三个数据字段映射到第二列 `FirstName`。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-117">Map the third data field to the second column, `FirstName`.</span></span>  
  
-   <span data-ttu-id="bb9ef-118">将第四个数据字段映射到第三列 `LastName`。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-118">Map the fourth data field to the third column, `LastName`.</span></span>  
  
## <a name="non-xml-format-file-for-more-data-fields"></a><span data-ttu-id="bb9ef-119">针对较多数据字段的非 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="bb9ef-119">Non-XML Format File for More Data Fields</span></span>  
 <span data-ttu-id="bb9ef-120">以下格式化文件 `myTestSkipField.fmt` 将 `myTestSkipField-c.dat` 中的字段映射至 `myTestSkipField` 表的列。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-120">The following format file, `myTestSkipField.fmt`, maps the fields in `myTestSkipField-c.dat` to the columns of the `myTestSkipField` table.</span></span> <span data-ttu-id="bb9ef-121">该格式化文件使用字符数据格式。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-121">The format file uses character data format.</span></span> <span data-ttu-id="bb9ef-122">跳过列映射需要将列顺序值更改为 0，如格式化文件中 `ExtraField` 列所示。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-122">Skipping a column mapping requires changing its column order value to 0, as shown for the `ExtraField` column in the format file.</span></span>  
  
 <span data-ttu-id="bb9ef-123">`myTestSkipField.fmt` 格式化文件包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="bb9ef-123">The `myTestSkipField.fmt` format file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     PersonID               ""  
2       SQLCHAR       0       100       ","    0     ExtraField             SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      2     FirstName              SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   3     LastName               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="bb9ef-124">有关非 XML 格式化文件语法的信息，请参阅[非 XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-124">For information about the syntax of non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="bb9ef-125">示例</span><span class="sxs-lookup"><span data-stu-id="bb9ef-125">Examples</span></span>  
 <span data-ttu-id="bb9ef-126">以下示例所用的 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 中使用了 `myTestSkipField.fmt` 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-126">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` using the `myTestSkipField.fmt` format file.</span></span> <span data-ttu-id="bb9ef-127">此示例将 `myTestSkipField-c.dat` 数据文件大容量导入至 `myTestSkipField` 表。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-127">The example bulk imports the `myTestSkipField-c.dat` data file into the `myTestSkipField` table.</span></span> <span data-ttu-id="bb9ef-128">若要创建示例表和数据文件，请参阅本主题前面的“示例数据文件和表”。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-128">To create the sample table and data file, see "Sample Data File and Table," earlier in this topic.</span></span>  
  
 <span data-ttu-id="bb9ef-129">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查询编辑器中，运行以下代码：</span><span class="sxs-lookup"><span data-stu-id="bb9ef-129">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
   SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.fmt'    
       ) AS t1;  
GO   
```  
  
## <a name="xml-format-file-for-more-data-fields"></a><span data-ttu-id="bb9ef-130">针对较多数据字段的 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="bb9ef-130">XML Format File for More Data Fields</span></span>  
 <span data-ttu-id="bb9ef-131">在示例中显示的格式化文件基于另一格式化文件 `myTestSkipField.xml`，该格式化文件始终使用字符数据格式并且其字段与 `myTestSkipField` 表中列的数量和顺序完全一致。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-131">The format file presented in this example is based on another format file, `myTestSkipField.xml`, which uses character data format throughout and whose fields correspond exactly in number and order to the columns in the `myTestSkipField` table.</span></span> <span data-ttu-id="bb9ef-132">若要查看该格式化文件的内容，请参阅[创建格式化文件 (SQL Server)](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-132">To view the contents of that format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
 <span data-ttu-id="bb9ef-133">以下格式化文件 `myTestSkipField.xml` 将 `myTestSkipField-c.dat` 中的字段映射至 `myTestSkipField` 表的列。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-133">The following format file, `myTestSkipField.xml`, maps the fields in `myTestSkipField-c.dat` to the columns of the `myTestSkipField` table.</span></span> <span data-ttu-id="bb9ef-134">该格式化文件使用字符数据格式。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-134">The format file uses character data format.</span></span>  
  
 <span data-ttu-id="bb9ef-135">`myTestSkipField.xml` 格式化文件包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="bb9ef-135">The `myTestSkipField.xml` format file contains the following information:</span></span>  
  
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
  <COLUMN SOURCE="1" NAME="PersonID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="3" NAME="FirstName" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="LastName" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
### <a name="examples"></a><span data-ttu-id="bb9ef-136">示例</span><span class="sxs-lookup"><span data-stu-id="bb9ef-136">Examples</span></span>  
 <span data-ttu-id="bb9ef-137">以下示例所用的 `INSERT ... SELECT * FROM OPENROWSET(BULK...)` 中使用了 `myTestSkipField.Xml` 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-137">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` using the `myTestSkipField.Xml` format file.</span></span> <span data-ttu-id="bb9ef-138">此示例将 `myTestSkipField-c.dat` 数据文件大容量导入至 `myTestSkipField` 表。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-138">The example bulk imports the `myTestSkipField-c.dat` data file into the `myTestSkipField` table.</span></span> <span data-ttu-id="bb9ef-139">若要创建示例表和数据文件，请参阅本主题前面的“示例数据文件和表”。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-139">To create the sample table and data file, see "Sample Data File and Table," earlier in this topic.</span></span>  
  
 <span data-ttu-id="bb9ef-140">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查询编辑器中，运行以下代码：</span><span class="sxs-lookup"><span data-stu-id="bb9ef-140">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
  SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.xml'    
       ) AS t1;  
GO  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="bb9ef-141">有关 XML 架构语法和 XML 格式化文件的其他示例的信息，请参阅 [XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9ef-141">For information about the syntax of the XML Schema and additional samples of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9ef-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb9ef-142">See Also</span></span>  
 <span data-ttu-id="bb9ef-143">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="bb9ef-143">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="bb9ef-144">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bb9ef-144">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="bb9ef-145">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bb9ef-145">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="bb9ef-146">[使用格式化文件跳过表列 (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bb9ef-146">[Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span></span>  
 [<span data-ttu-id="bb9ef-147">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bb9ef-147">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
  
