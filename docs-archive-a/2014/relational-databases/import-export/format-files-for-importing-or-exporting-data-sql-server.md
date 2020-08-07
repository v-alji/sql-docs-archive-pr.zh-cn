---
title: 用于导入或导出数据的格式化文件 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], format files
- bulk importing [SQL Server], format files
- format files [SQL Server]
ms.assetid: b7b97d68-4336-4091-aee4-1941fab568e3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1143690f0322fef2612fde51eebcb7427ee237ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589083"
---
# <a name="format-files-for-importing-or-exporting-data-sql-server"></a><span data-ttu-id="bdaff-102">用来导入或导出数据的格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bdaff-102">Format Files for Importing or Exporting Data (SQL Server)</span></span>
  <span data-ttu-id="bdaff-103">当向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中大容量导入数据或从该表中大容量导出数据时，可以使用格式化文件  存储大容量导入数据或大容量导出数据所需的所有格式信息。</span><span class="sxs-lookup"><span data-stu-id="bdaff-103">When you bulk import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or bulk export data from a table, you can use a *format file* to store all the format information that is required to bulk export or bulk import data.</span></span> <span data-ttu-id="bdaff-104">这包括数据文件中相对于该表的各字段的格式信息。</span><span class="sxs-lookup"><span data-stu-id="bdaff-104">This includes format information for each field in a data file relative to that table.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="bdaff-105">支持两种格式化文件类型：XML 格式和非 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="bdaff-105">supports two types of format files: XML formats and non-XML format files.</span></span> <span data-ttu-id="bdaff-106">XML 格式化文件和非 XML 格式化文件在一个数据文件中包含每个字段的说明，并且 XML 格式化文件还包含相应表列的说明。</span><span class="sxs-lookup"><span data-stu-id="bdaff-106">Both non-XML format files and XML format files contain descriptions of every field in a data file, and XML format files also contain descriptions of the corresponding table columns.</span></span> <span data-ttu-id="bdaff-107">通常，XML 与非 XML 格式化文件可以互换。</span><span class="sxs-lookup"><span data-stu-id="bdaff-107">Generally, XML and non-XML format files are interchangeable.</span></span> <span data-ttu-id="bdaff-108">但是，建议您为新的格式化文件使用 XML 语法，因为与非 XML 格式化文件相比，格式化文件具有多项优点。</span><span class="sxs-lookup"><span data-stu-id="bdaff-108">However, we recommend that you use the XML syntax for new format files because they provide several advantages over non-XML format files.</span></span> <span data-ttu-id="bdaff-109">有关详细信息，请参阅 [XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bdaff-109">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
 
  
##  <a name="benefits-of-format-files"></a><a name="Benefits"></a> <span data-ttu-id="bdaff-110">格式化文件的优点</span><span class="sxs-lookup"><span data-stu-id="bdaff-110">Benefits of Format Files</span></span>  
  
-   <span data-ttu-id="bdaff-111">为编写数据文件提供了一个灵活的系统，用户只需进行极少的编辑甚至无需编辑即可编写出符合其他数据格式的数据文件，或从其他软件读取数据文件。</span><span class="sxs-lookup"><span data-stu-id="bdaff-111">Provides a flexible system for writing data files that requires little or no editing to comply with other data formats or to read data files from other software.</span></span>  
  
-   <span data-ttu-id="bdaff-112">使您可以大容量导入数据，而不必添加或删除不需要的数据或者重新排列数据文件中现有数据的顺序。</span><span class="sxs-lookup"><span data-stu-id="bdaff-112">Enables you to bulk import data without having to add or delete unnecessary data or to reorder existing data in the data file.</span></span> <span data-ttu-id="bdaff-113">当数据文件中的字段和表中的列存在不匹配的情况时，格式化文件尤其有用。</span><span class="sxs-lookup"><span data-stu-id="bdaff-113">Format files are particularly useful when a mismatch exists between fields in the data file and columns in the table.</span></span>  
  
##  <a name="examples-of-format-files"></a><a name="ExamplesOfFFs"></a> <span data-ttu-id="bdaff-114">格式化文件的示例</span><span class="sxs-lookup"><span data-stu-id="bdaff-114">Examples of Format Files</span></span>  
 <span data-ttu-id="bdaff-115">下面的示例说明了非 XML 格式化文件和 XML 格式化文件的布局。</span><span class="sxs-lookup"><span data-stu-id="bdaff-115">The following examples show the layout of a non-XML format file and of an XML format file.</span></span> <span data-ttu-id="bdaff-116">这些格式化文件对应于 `HumanResources.myTeam` 示例数据库中的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="bdaff-116">These format files correspond to the `HumanResources.myTeam` table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="bdaff-117">该表包含四列： `EmployeeID`、 `Name`、 `Title`和 `ModifiedDate`。</span><span class="sxs-lookup"><span data-stu-id="bdaff-117">This table contains four columns: `EmployeeID`, `Name`, `Title`, and `ModifiedDate`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bdaff-118">有关该表以及如何创建该表的信息，请参阅 [HumanResources.myTeam 示例表 (SQL Server)](humanresources-myteam-sample-table-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bdaff-118">For information about this table and how to create it, see [HumanResources.myTeam Sample Table &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md).</span></span>  
  
### <a name="a-using-a-non-xml-format-file"></a><span data-ttu-id="bdaff-119">A.</span><span class="sxs-lookup"><span data-stu-id="bdaff-119">A.</span></span> <span data-ttu-id="bdaff-120">使用非 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="bdaff-120">Using a non-XML format file</span></span>  
 <span data-ttu-id="bdaff-121">下面的非 XML 格式化文件为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表使用 `HumanResources.myTeam` 本机数据格式。</span><span class="sxs-lookup"><span data-stu-id="bdaff-121">The following non-XML format file uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data format for the `HumanResources.myTeam` table.</span></span> <span data-ttu-id="bdaff-122">此格式化文件是用下面的 `bcp` 命令创建的。</span><span class="sxs-lookup"><span data-stu-id="bdaff-122">This format file was created by using the following `bcp` command.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam format nul -f myTeam.Fmt -n -T   
The contents of this format file are as follows: 9.0  
4  
1       SQLSMALLINT   0       2       ""   1     EmployeeID               ""  
2       SQLNCHAR      2       100     ""   2     Name                     SQL_Latin1_General_CP1_CI_AS  
3       SQLNCHAR      2       100     ""   3     Title                    SQL_Latin1_General_CP1_CI_AS  
4       SQLNCHAR      2       100     ""   4     Background               SQL_Latin1_General_CP1_CI_AS  
```  
  
 <span data-ttu-id="bdaff-123">有关详细信息，请参阅 [非 XML 格式化文件 (SQL Server)](non-xml-format-files-sql-server.md)早期版本支持的原始格式。</span><span class="sxs-lookup"><span data-stu-id="bdaff-123">For more information, see [Non-XML Format Files &#40;SQL Server&#41;](non-xml-format-files-sql-server.md).</span></span>  
  
 
  
### <a name="b-using-an-xml-format-file"></a><span data-ttu-id="bdaff-124">B.</span><span class="sxs-lookup"><span data-stu-id="bdaff-124">B.</span></span> <span data-ttu-id="bdaff-125">使用 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="bdaff-125">Using an XML format file</span></span>  
 <span data-ttu-id="bdaff-126">下面的 XML 格式化文件为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表使用 `HumanResources.myTeam` 本机数据格式。</span><span class="sxs-lookup"><span data-stu-id="bdaff-126">The following XML format file uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data format for the `HumanResources.myTeam` table.</span></span> <span data-ttu-id="bdaff-127">此格式化文件是用下面的 `bcp` 命令创建的。</span><span class="sxs-lookup"><span data-stu-id="bdaff-127">This format file was created by using the following `bcp` command.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam format nul -f myTeam.Xml -x -n -T   
```  
  
 <span data-ttu-id="bdaff-128">格式化文件包含：</span><span class="sxs-lookup"><span data-stu-id="bdaff-128">The format file contains:</span></span>  
  
```  
 <?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativePrefix" LENGTH="1"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="EmployeeID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Name" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Title" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Background" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 <span data-ttu-id="bdaff-129">有关详细信息，请参阅 [XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bdaff-129">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  

  
##  <a name="when-is-a-format-file-required"></a><a name="WhenFFrequired"></a> <span data-ttu-id="bdaff-130">何时需要使用格式化文件？</span><span class="sxs-lookup"><span data-stu-id="bdaff-130">When Is a Format File Required?</span></span>  
 <span data-ttu-id="bdaff-131">INSERT ... SELECT \* FROM OPENROWSET(BULK...) 语句始终要求使用格式化文件。</span><span class="sxs-lookup"><span data-stu-id="bdaff-131">An INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement always requires a format file.</span></span>  
  
-   <span data-ttu-id="bdaff-132">对于 **bcp** 或 BULK INSERT，在简单的情况下，请视情况选用格式化文件，在极少数的情况下才必须使用。</span><span class="sxs-lookup"><span data-stu-id="bdaff-132">For **bcp** or BULK INSERT, in simple situations, using a format file is optional and rarely necessary.</span></span> <span data-ttu-id="bdaff-133">但是，对于复杂的大容量导入情况，通常都会需要格式化文件。</span><span class="sxs-lookup"><span data-stu-id="bdaff-133">However, for complex bulk-import situations, a format file is frequently required.</span></span>  
  
 <span data-ttu-id="bdaff-134">在以下情况下，必须使用格式化文件：</span><span class="sxs-lookup"><span data-stu-id="bdaff-134">Format files are required if:</span></span>  
  
-   <span data-ttu-id="bdaff-135">具有不同架构的多个表使用同一数据文件作为数据源。</span><span class="sxs-lookup"><span data-stu-id="bdaff-135">The same data file is used as a source for multiple tables that have different schemas.</span></span>  
  
-   <span data-ttu-id="bdaff-136">数据文件中的字段数不同于目标表中的列数；例如：</span><span class="sxs-lookup"><span data-stu-id="bdaff-136">The data file has a different number of fields that the target table has columns; for example:</span></span>  
  
    -   <span data-ttu-id="bdaff-137">目标表中至少包含一个定义了默认值或允许为 NULL 的列。</span><span class="sxs-lookup"><span data-stu-id="bdaff-137">The target table contains at least one column for which either a default value is defined or NULL is allowed.</span></span>  
  
    -   <span data-ttu-id="bdaff-138">用户不具有对目标表的一个或多个列的 SELECT/INSERT 权限。</span><span class="sxs-lookup"><span data-stu-id="bdaff-138">The users do not have SELECT/INSERT permissions on one or more columns in the table.</span></span>  
  
    -   <span data-ttu-id="bdaff-139">具有不同架构的两个或多个表使用同一个数据文件。</span><span class="sxs-lookup"><span data-stu-id="bdaff-139">A single data file is used with two or more tables that have different schemas.</span></span>  
  
-   <span data-ttu-id="bdaff-140">数据文件和表的列顺序不同。</span><span class="sxs-lookup"><span data-stu-id="bdaff-140">The column order is different for the data file and table.</span></span>  
  
-   <span data-ttu-id="bdaff-141">数据文件列的终止字符或前缀长度不同。</span><span class="sxs-lookup"><span data-stu-id="bdaff-141">The terminating characters or prefix lengths differ among the columns of the data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bdaff-142">在缺少格式化文件的情况下，如果 **bcp** 命令指定了数据格式开关（ **-n**、 **-c**、 **-w**或 **-N**），或者 BULK INSERT 操作指定了 DATAFILETYPE 选项，那么指定的数据格式将用作解释数据文件字段的默认方法。</span><span class="sxs-lookup"><span data-stu-id="bdaff-142">In the absence of a format file, if a **bcp** command specifies a data-format switch (**-n**, **-c**, **-w**, or **-N**) or a BULK INSERT operation specifies the DATAFILETYPE option, the specified data format is used as the default method of interpreting the fields of the data file.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="bdaff-143">相关任务</span><span class="sxs-lookup"><span data-stu-id="bdaff-143">Related Tasks</span></span>  
  
-   [<span data-ttu-id="bdaff-144">创建格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bdaff-144">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="bdaff-145">使用格式化文件批量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bdaff-145">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="bdaff-146">使用格式化文件跳过表列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bdaff-146">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="bdaff-147">使用格式化文件跳过数据字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bdaff-147">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="bdaff-148">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bdaff-148">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="bdaff-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdaff-149">See Also</span></span>  
 <span data-ttu-id="bdaff-150">[非 XML 格式化文件 (SQL Server)](non-xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bdaff-150">[Non-XML Format Files &#40;SQL Server&#41;](non-xml-format-files-sql-server.md) </span></span>  
 <span data-ttu-id="bdaff-151">[XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bdaff-151">[XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="bdaff-152">用于批量导入或导出的数据格式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bdaff-152">Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;</span></span>](data-formats-for-bulk-import-or-bulk-export-sql-server.md)  
  
  
