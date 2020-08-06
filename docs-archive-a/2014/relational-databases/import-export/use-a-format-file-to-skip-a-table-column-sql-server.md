---
title: 使用格式化文件跳过表列 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- skipping columns when importing
- format files [SQL Server], skipping columns
ms.assetid: 30e0e7b9-d131-46c7-90a4-6ccf77e3d4f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 153ef21209ff4261020e26aca3bc52d28dc852a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591887"
---
# <a name="use-a-format-file-to-skip-a-table-column-sql-server"></a><span data-ttu-id="38eff-102">使用格式化文件跳过表列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="38eff-102">Use a Format File to Skip a Table Column (SQL Server)</span></span>
  <span data-ttu-id="38eff-103">本主题说明格式化文件。</span><span class="sxs-lookup"><span data-stu-id="38eff-103">This topic describes format files.</span></span> <span data-ttu-id="38eff-104">当数据文件中不存在字段时，您可以使用格式化文件跳过导入表列。</span><span class="sxs-lookup"><span data-stu-id="38eff-104">You can use a format file to skip importing a table column when the field does not exist in the data file.</span></span> <span data-ttu-id="38eff-105">仅当跳过的列可为空值和/或具有默认值时，数据文件中的字段数才可以少于表中的列数。</span><span class="sxs-lookup"><span data-stu-id="38eff-105">A data file can contain fewer fields than the number of columns in the table only if the skipped columns are nullable and/or have default value.</span></span>

## <a name="sample-table-and-data-file"></a><span data-ttu-id="38eff-106">示例表和数据文件</span><span class="sxs-lookup"><span data-stu-id="38eff-106">Sample Table and Data File</span></span>
 <span data-ttu-id="38eff-107">下列示例需要在 `myTestSkipCol` 示例数据库中的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] dbo **架构下存在一个名为** 的表。</span><span class="sxs-lookup"><span data-stu-id="38eff-107">The following examples require a table named `myTestSkipCol` in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the **dbo** schema.</span></span> <span data-ttu-id="38eff-108">此表的创建方式如下所示：</span><span class="sxs-lookup"><span data-stu-id="38eff-108">Create this table as follows:</span></span>

```
USE AdventureWorks2012;
GO
CREATE TABLE myTestSkipCol 
   (
   Col1 smallint,
   Col2 nvarchar(50) NULL,
   Col3 nvarchar(50) not NULL
   );
GO
```

 <span data-ttu-id="38eff-109">下列示例使用示例数据文件 `myTestSkipCol2.dat`，此文件仅包含两个字段，但相应的表包含三列：</span><span class="sxs-lookup"><span data-stu-id="38eff-109">The following examples use a sample data file, `myTestSkipCol2.dat`, which contains only two fields, although the corresponding table contains three columns:</span></span>

```
1,DataForColumn3
1,DataForColumn3
1,DataForColumn3

```

 <span data-ttu-id="38eff-110">若要将数据从 `myTestSkipCol2.dat` 大容量导入 `myTestSkipCol` 表，则格式化文件必须将第一个数据字段映射到 `Col1`，并跳过 `Col3`将第二个字段映射到 `Col2`。</span><span class="sxs-lookup"><span data-stu-id="38eff-110">To bulk import data from `myTestSkipCol2.dat` into the `myTestSkipCol` table, the format file must map the first data field to `Col1`, the second field to `Col3`, skipping `Col2`.</span></span>

## <a name="using-a-non-xml-format-file"></a><span data-ttu-id="38eff-111">使用非 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="38eff-111">Using a Non-XML Format File</span></span>
 <span data-ttu-id="38eff-112">可以修改非 XML 格式化文件以跳过某个表列。</span><span class="sxs-lookup"><span data-stu-id="38eff-112">You can modify a non-XML format file to skip a table column.</span></span> <span data-ttu-id="38eff-113">这通常涉及使用 **bcp** 实用工具创建默认的非 XML 格式化文件，并在文本编辑器中修改此默认文件。</span><span class="sxs-lookup"><span data-stu-id="38eff-113">Typically, this involves using the **bcp** utility to create a default non-XML format file and the modifying the default file in a text editor.</span></span> <span data-ttu-id="38eff-114">修改过的格式化文件必须将每个现有字段映射到相应的表列并指明要跳过哪个或哪些表列。</span><span class="sxs-lookup"><span data-stu-id="38eff-114">The modified format file must map each existing fields to its corresponding table column and indicate which table column or columns to skip.</span></span> <span data-ttu-id="38eff-115">修改默认非 XML 数据文件的方法有两种。</span><span class="sxs-lookup"><span data-stu-id="38eff-115">Two alternatives exist for modifying a default non-XML data file.</span></span> <span data-ttu-id="38eff-116">两种方法都假定数据文件中没有数据字段，并且不会有数据插入到对应的表列中。</span><span class="sxs-lookup"><span data-stu-id="38eff-116">Either alternative indicates that the data field does not exist in the data file and that no data will be inserted into the corresponding table column.</span></span>

### <a name="creating-a-default-non-xml-format-file"></a><span data-ttu-id="38eff-117">创建默认非 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="38eff-117">Creating a Default Non-XML Format File</span></span>
 <span data-ttu-id="38eff-118">本主题使用默认非 XML 格式化文件，此文件是使用以下 `myTestSkipCol` bcp **命令为** 示例表创建的：</span><span class="sxs-lookup"><span data-stu-id="38eff-118">This topic uses the default non-XML format file that was created for the `myTestSkipCol` sample table by using the following **bcp** command:</span></span>

```
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.fmt -c -T
```

 <span data-ttu-id="38eff-119">以上命令创建了一个非 XML 格式化文件， `myTestSkipCol_Default.fmt`。</span><span class="sxs-lookup"><span data-stu-id="38eff-119">The previous command creates a non-XML format file, `myTestSkipCol_Default.fmt`.</span></span> <span data-ttu-id="38eff-120">此格式化文件称为 *默认格式化文件* ，因为它是 **bcp**生成的格式。</span><span class="sxs-lookup"><span data-stu-id="38eff-120">This format file is called a *default format file* because it is the form generated by **bcp**.</span></span> <span data-ttu-id="38eff-121">默认格式化文件通常说明数据文件字段与表列之间的一一对应关系。</span><span class="sxs-lookup"><span data-stu-id="38eff-121">Typically, a default format file describes a one-to-one correspondence between data-file fields and table columns.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="38eff-122">您可能必须指定要连接的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="38eff-122">You might have to specify the name of the server instance to which you are connecting.</span></span> <span data-ttu-id="38eff-123">可能还必须指定用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="38eff-123">Also, you might have to specify the user name and password.</span></span> <span data-ttu-id="38eff-124">有关详细信息，请参阅 [bcp Utility](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="38eff-124">For more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>

 <span data-ttu-id="38eff-125">下图显示了此默认格式化文件示例中的值。</span><span class="sxs-lookup"><span data-stu-id="38eff-125">The following illustration shows the values in this sample default format files.</span></span> <span data-ttu-id="38eff-126">图中还显示了格式化文件各个字段的名称。</span><span class="sxs-lookup"><span data-stu-id="38eff-126">The illustration also shows the name of each format-file field.</span></span>

 <span data-ttu-id="38eff-127">![适用于 myTestSkipCol 的默认的非 XML 格式文件](../../database-engine/media/mytestskipcol-f-c-default-fmt.gif "适用于 myTestSkipCol 的默认的非 XML 格式文件")</span><span class="sxs-lookup"><span data-stu-id="38eff-127">![default non-XML format file for myTestSkipCol](../../database-engine/media/mytestskipcol-f-c-default-fmt.gif "default non-XML format file for myTestSkipCol")</span></span>

> [!NOTE]
>  <span data-ttu-id="38eff-128">有关格式化文件字段的详细信息，请参阅[非 XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="38eff-128">For more information about the format-file fields, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>

### <a name="methods-for-modifying-a-non-xml-format-file"></a><span data-ttu-id="38eff-129">修改非 XML 格式化文件的方法</span><span class="sxs-lookup"><span data-stu-id="38eff-129">Methods for Modifying a Non-XML Format File</span></span>
 <span data-ttu-id="38eff-130">若要跳过某个表列，可编辑默认非 XML 格式化文件并使用以下方法之一修改此文件：</span><span class="sxs-lookup"><span data-stu-id="38eff-130">To skip a table column, edit the default non-XML format file and modify the file by using one of the following alternative methods:</span></span>

-   <span data-ttu-id="38eff-131">首选方法包括三个基本步骤。</span><span class="sxs-lookup"><span data-stu-id="38eff-131">The preferred method involves three basic steps.</span></span> <span data-ttu-id="38eff-132">首先，删除说明数据文件中丢失字段的任何格式化文件行。</span><span class="sxs-lookup"><span data-stu-id="38eff-132">First, delete any format-file row that describes a field that is missing from the data file.</span></span> <span data-ttu-id="38eff-133">然后，减小所删除行后的每个格式化文件行的“宿主文件字段顺序”值。</span><span class="sxs-lookup"><span data-stu-id="38eff-133">Then, reduce the "Host file field order" value of each format-file row that follows a deleted row.</span></span> <span data-ttu-id="38eff-134">这是为了使“宿主文件字段顺序”值按顺序排列（1 到 *n*），它反映了数据文件中各个数据字段的实际位置。</span><span class="sxs-lookup"><span data-stu-id="38eff-134">The goal is sequential "Host file field order" values, 1 through *n*, that reflect the actual position of each data field in the data file.</span></span> <span data-ttu-id="38eff-135">最后，减小“列数”字段中的值以反映数据文件中的实际字段数。</span><span class="sxs-lookup"><span data-stu-id="38eff-135">Finally, reduce the value in the "Number of columns" field to reflect the actual number of fields in the data file.</span></span>

     <span data-ttu-id="38eff-136">下面的示例基于 `myTestSkipCol` 表的默认格式化文件，此文件是在本主题先前的“创建默认非 XML 格式化文件”中创建的。</span><span class="sxs-lookup"><span data-stu-id="38eff-136">The following example is based on the default format file for the `myTestSkipCol` table, which is created in "Creating a Default Non-XML Format File," earlier in this topic.</span></span> <span data-ttu-id="38eff-137">此修改过的格式化文件将第一个数据字段映射到 `Col1`，并跳过 `Col2`将第二个数据字段映射到 `Col3`。</span><span class="sxs-lookup"><span data-stu-id="38eff-137">This modified format file maps the first data field to `Col1`, skips `Col2`, and maps the second data field to `Col3`.</span></span> <span data-ttu-id="38eff-138">已删除 `Col2` 的行。</span><span class="sxs-lookup"><span data-stu-id="38eff-138">The row for `Col2` has been deleted.</span></span> <span data-ttu-id="38eff-139">其他修改以粗体表示：</span><span class="sxs-lookup"><span data-stu-id="38eff-139">Other modifications are indicated in bold:</span></span>

    ```
    9.0
    2
    1       SQLCHAR       0       7       "\t"     1     Col1         ""
    2       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS
    ```

-   <span data-ttu-id="38eff-140">若要跳过某个表列，也可以修改与表列对应的格式化文件行的定义。</span><span class="sxs-lookup"><span data-stu-id="38eff-140">Alternatively, to skip a table column, you can modify the definition of the format-file row that corresponds to the table column.</span></span> <span data-ttu-id="38eff-141">在此格式化文件行中，“前缀长度”、“宿主文件数据长度”和“服务器列顺序”值必须设置为 0，</span><span class="sxs-lookup"><span data-stu-id="38eff-141">In this format-file row, the "prefix length," "host file data length," and "server column order" values must be set to 0.</span></span> <span data-ttu-id="38eff-142">并且“终止符”和“列排序规则”字段必须设置为 "" (NULL)。</span><span class="sxs-lookup"><span data-stu-id="38eff-142">Also, the "terminator" and "column collation" fields must be set to "" (NULL).</span></span>

     <span data-ttu-id="38eff-143">“服务器列名”值必须为非空白字符串，但不一定为实际列名。</span><span class="sxs-lookup"><span data-stu-id="38eff-143">The "server column name" value requires a nonblank string, though the actual column name is not necessary.</span></span> <span data-ttu-id="38eff-144">其余格式字段必须为它们的默认值。</span><span class="sxs-lookup"><span data-stu-id="38eff-144">The remaining format fields require their default values.</span></span>

     <span data-ttu-id="38eff-145">下面的示例也是从 `myTestSkipCol` 表的默认格式化文件派生出来的。</span><span class="sxs-lookup"><span data-stu-id="38eff-145">The following example is also derived from the default format file for the `myTestSkipCol` table.</span></span> <span data-ttu-id="38eff-146">必须为 0 或 NULL 的值以粗体表示。</span><span class="sxs-lookup"><span data-stu-id="38eff-146">Values that must be 0 or NULL are indicated in bold.</span></span>

    ```
    9.0
    3
    1       SQLCHAR       0       7       "\t"     1     Col1         ""
    2       SQLCHAR       00""0     Col2         ""
    3       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS
    ```

### <a name="examples"></a><span data-ttu-id="38eff-147">示例</span><span class="sxs-lookup"><span data-stu-id="38eff-147">Examples</span></span>
 <span data-ttu-id="38eff-148">下面的示例同样基于本主题上文“示例表和数据文件”中创建的 `myTestSkipCol` 示例表和 `myTestSkipCol2.dat` 示例数据文件。</span><span class="sxs-lookup"><span data-stu-id="38eff-148">The following examples are also based on the `myTestSkipCol` sample table and the `myTestSkipCol2.dat` sample data file that are created in "Sample Table and Data File," earlier in this topic.</span></span>

#### <a name="using-bulk-insert"></a><span data-ttu-id="38eff-149">使用 BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="38eff-149">Using BULK INSERT</span></span>
 <span data-ttu-id="38eff-150">此例使用的是本主题先前的“用于修改非 XML 格式化文件的方法”中创建的两个已修改非 XML 格式化文件之一。</span><span class="sxs-lookup"><span data-stu-id="38eff-150">This example works by using either of the modified non-XML format files created in "Methods for Modifying a Non-XML Format File," earlier in this topic.</span></span> <span data-ttu-id="38eff-151">在此例中，修改过的格式化文件名为 `C:\myTestSkipCol2.fmt`。</span><span class="sxs-lookup"><span data-stu-id="38eff-151">In this example, the modified format file is named `C:\myTestSkipCol2.fmt`.</span></span> <span data-ttu-id="38eff-152">若要使用 `BULK INSERT` 大容量导入 `myTestSkipCol2.dat` 数据文件，请在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中执行以下代码：</span><span class="sxs-lookup"><span data-stu-id="38eff-152">To use `BULK INSERT` to bulk import the `myTestSkipCol2.dat` data file, in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
USE AdventureWorks2012;
GO
BULK INSERT myTestSkipCol 
   FROM 'C:\myTestSkipCol2.dat' 
   WITH (FORMATFILE = 'C:\myTestSkipCol2.fmt');
GO
SELECT * FROM myTestSkipCol;
GO
```

## <a name="using-an-xml-format-file"></a><span data-ttu-id="38eff-153">使用 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="38eff-153">Using an XML Format File</span></span>
 <span data-ttu-id="38eff-154">使用 XML 格式化文件时，你无法在通过 **bcp** 命令或 BULK INSERT 语句直接向表导入内容时跳过列。</span><span class="sxs-lookup"><span data-stu-id="38eff-154">With an XML format file, you cannot skip a column when you are importing directly into a table by using a **bcp** command or a BULK INSERT statement.</span></span> <span data-ttu-id="38eff-155">但是，您可以向表中除最后一列的所有列导入。</span><span class="sxs-lookup"><span data-stu-id="38eff-155">However, you can import into all but the last column of a table.</span></span> <span data-ttu-id="38eff-156">如果必须跳过除最后一列的任何列，则必须创建目标表的视图，其中仅包含数据文件中包含的列。</span><span class="sxs-lookup"><span data-stu-id="38eff-156">If you have to skip any but the last column, you must create a view of the target table that contains only the columns contained in the data file.</span></span> <span data-ttu-id="38eff-157">然后，您可以将此文件中的数据大容量导入此视图。</span><span class="sxs-lookup"><span data-stu-id="38eff-157">Then, you can bulk import data from that file into the view.</span></span>

 <span data-ttu-id="38eff-158">若要使用 XML 格式化文件通过 OPENROWSET(BULK...) 跳过表列，必须提供选择列表以及目标表中列的显式列表，如下所示：</span><span class="sxs-lookup"><span data-stu-id="38eff-158">To use an XML format file to skip a table column by using OPENROWSET(BULK...), you have to provide explicit list of columns in the select list and also in the target table, as follows:</span></span>

 <span data-ttu-id="38eff-159">INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="38eff-159">INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)</span></span>

### <a name="creating-a-default-xml-format-file"></a><span data-ttu-id="38eff-160">创建默认 XML 格式化文件</span><span class="sxs-lookup"><span data-stu-id="38eff-160">Creating a Default XML Format File</span></span>
 <span data-ttu-id="38eff-161">修改过的格式化文件示例基于 `myTestSkipCol` 示例表和数据文件，它们是在本主题先前的“示例表和数据文件”中创建的。</span><span class="sxs-lookup"><span data-stu-id="38eff-161">The examples of modified format files are based on the `myTestSkipCol` sample table and data file that are created in "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="38eff-162">下面的 **bcp** 命令创建 `myTestSkipCol` 表的默认 XML 格式化文件：</span><span class="sxs-lookup"><span data-stu-id="38eff-162">The following **bcp** command creates a default XML format file for the `myTestSkipCol` table:</span></span>

```
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.xml -c -x -T
```

 <span data-ttu-id="38eff-163">生成的默认非 XML 格式化文件说明了数据文件字段与表列之间的一一对应关系，如下所示：</span><span class="sxs-lookup"><span data-stu-id="38eff-163">The resulting default non-XML format file describes a one-to-one correspondence between data-file fields and table columns, as follows:</span></span>

```
<?xml version="1.0"?>
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <RECORD>
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="7"/>
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
 </RECORD>
 <ROW>
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>
 </ROW>
</BCPFORMAT>
```

> [!NOTE]
>  <span data-ttu-id="38eff-164">有关 XML 格式化文件结构的详细信息，请参阅 [XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="38eff-164">For information about the structure of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>

### <a name="examples"></a><span data-ttu-id="38eff-165">示例</span><span class="sxs-lookup"><span data-stu-id="38eff-165">Examples</span></span>
 <span data-ttu-id="38eff-166">本节中的示例使用了在本主题先前的“示例表和数据文件”中创建的 `myTestSkipCol` 示例表和 `myTestSkipCol2.dat` 示例数据文件。</span><span class="sxs-lookup"><span data-stu-id="38eff-166">The examples in this section use the `myTestSkipCol` sample table and the `myTestSkipCol2.dat` sample data file that are created in "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="38eff-167">为将数据从 `myTestSkipCol2.dat` 导入 `myTestSkipCol` 表，示例使用以下修改过的 XML 格式化文件 `myTestSkipCol2-x.xml`。</span><span class="sxs-lookup"><span data-stu-id="38eff-167">To import the data from `myTestSkipCol2.dat` into the `myTestSkipCol` table, the examples use the following modified XML format file, `myTestSkipCol2-x.xml`.</span></span> <span data-ttu-id="38eff-168">这基于本主题先前的“创建默认 XML 格式化文件”中创建的格式化文件。</span><span class="sxs-lookup"><span data-stu-id="38eff-168">This is based on the format file that is created in "Creating a Default XML Format File," earlier in this topic.</span></span>

```
<?xml version="1.0"?>
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
 <RECORD>
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>
 </RECORD>
 <ROW>
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>
  <COLUMN SOURCE="2" NAME="Col3" xsi:type="SQLNVARCHAR"/>
 </ROW>
</BCPFORMAT>
```

#### <a name="using-openrowsetbulk"></a><span data-ttu-id="38eff-169">使用 OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="38eff-169">Using OPENROWSET(BULK...)</span></span>
 <span data-ttu-id="38eff-170">下面的示例使用 `OPENROWSET` 大容量行集提供程序和 `myTestSkipCol2.xml` 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="38eff-170">The following example uses the `OPENROWSET` bulk rowset provider and the `myTestSkipCol2.xml` format file.</span></span> <span data-ttu-id="38eff-171">此示例将 `myTestSkipCol2.dat` 数据文件大容量导入至 `myTestSkipCol` 表。</span><span class="sxs-lookup"><span data-stu-id="38eff-171">The example bulk imports the `myTestSkipCol2.dat` data file into the `myTestSkipCol` table.</span></span> <span data-ttu-id="38eff-172">语句中包含了需要提供的选择列表以及目标表中列的显式列表。</span><span class="sxs-lookup"><span data-stu-id="38eff-172">The statement contains an explicit list of columns in the select list and also in the target table, as required.</span></span>

 <span data-ttu-id="38eff-173">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行下列代码：</span><span class="sxs-lookup"><span data-stu-id="38eff-173">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
USE AdventureWorks2012;
GO
INSERT INTO myTestSkipCol
  (Col1,Col3)
    SELECT Col1,Col3
      FROM  OPENROWSET(BULK  'C:\myTestSkipCol2.Dat',
      FORMATFILE='C:\myTestSkipCol2.Xml'  
       ) as t1 ;
GO
```

#### <a name="using-bulk-import-on-a-view"></a><span data-ttu-id="38eff-174">在视图上使用 BULK IMPORT</span><span class="sxs-lookup"><span data-stu-id="38eff-174">Using BULK IMPORT on a View</span></span>
 <span data-ttu-id="38eff-175">下面的示例在 `v_myTestSkipCol` 表上创建 `myTestSkipCol` 。</span><span class="sxs-lookup"><span data-stu-id="38eff-175">The following example creates the `v_myTestSkipCol` on the `myTestSkipCol` table.</span></span> <span data-ttu-id="38eff-176">此视图跳过第二表列 `Col2`。</span><span class="sxs-lookup"><span data-stu-id="38eff-176">This view skips the second table column, `Col2`.</span></span> <span data-ttu-id="38eff-177">然后此例使用 `BULK INSERT` 将 `myTestSkipCol2.dat` 数据文件导入此视图。</span><span class="sxs-lookup"><span data-stu-id="38eff-177">The example then uses `BULK INSERT` to import the `myTestSkipCol2.dat` data file into this view.</span></span>

 <span data-ttu-id="38eff-178">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行下列代码：</span><span class="sxs-lookup"><span data-stu-id="38eff-178">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>

```
CREATE VIEW v_myTestSkipCol AS
    SELECT Col1,Col3
    FROM myTestSkipCol;
GO

USE AdventureWorks2012;
GO
BULK INSERT v_myTestSkipCol
FROM 'C:\myTestSkipCol2.dat'
WITH (FORMATFILE='C:\myTestSkipCol2.xml');
GO
```

## <a name="see-also"></a><span data-ttu-id="38eff-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="38eff-179">See Also</span></span>
 <span data-ttu-id="38eff-180">[Bcp 实用工具](../../tools/bcp-utility.md) [BULK INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) [OPENROWSET &#40;Transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql) [使用格式化文件跳过数据字段 &#40;](use-a-format-file-to-skip-a-data-field-sql-server.md) SQL Server&#41;使用格式化文件[将表列映射到数据文件字段 &#40;SQL Server](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)&#41;[使用格式化文件大容量导入数据 &#40;](use-a-format-file-to-bulk-import-data-sql-server.md) SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="38eff-180">[bcp Utility](../../tools/bcp-utility.md) [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) [Use a Format File to Skip a Data Field &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md) [Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md) [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)</span></span>


