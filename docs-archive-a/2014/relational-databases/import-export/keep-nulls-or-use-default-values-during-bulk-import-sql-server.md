---
title: 在批量导入期间保留 Null 或使用默认值 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], null values
- bulk importing [SQL Server], default values
- data formats [SQL Server], null values
- bulk rowset providers [SQL Server]
- bcp utility [SQL Server], null values
- BULK INSERT statement
- default values
- OPENROWSET function, bulk importing
- data formats [SQL Server], default values
ms.assetid: 6b91d762-337b-4345-a159-88abb3e64a81
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 856aa12f6ad5e5094324e0df65941bc63d611451
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693364"
---
# <a name="keep-nulls-or-use-default-values-during-bulk-import-sql-server"></a><span data-ttu-id="ab85a-102">在批量导入期间保留 Null 或使用默认值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-102">Keep Nulls or Use Default Values During Bulk Import (SQL Server)</span></span>
  <span data-ttu-id="ab85a-103">默认情况下，将数据导入表中时， **bcp** 命令和 BULK INSERT 语句将使用为表中的列定义的所有默认值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-103">By default, when data is imported into a table, the **bcp** command and BULK INSERT statement observe any defaults that are defined for the columns in the table.</span></span> <span data-ttu-id="ab85a-104">例如，如果数据文件中包含一个空字段，则会加载该列的默认值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-104">For example, if there is a null field in a data file, the default value for the column is loaded instead.</span></span> <span data-ttu-id="ab85a-105">**bcp** 命令和 BULK INSERT 语句都允许指定保留 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-105">The **bcp** command and BULK INSERT statement both allow you to specify that nulls values be retained.</span></span>  
  
 <span data-ttu-id="ab85a-106">相反，常规 INSERT 语句会保留空值而不会插入默认值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-106">In contrast, a regular INSERT statement retains the null value instead of inserting a default value.</span></span> <span data-ttu-id="ab85a-107">INSERT ... SELECT \* FROM OPENROWSET(BULK...) 语句的基本行为与常规 INSERT 相同，但前者还支持插入默认值的表提示。</span><span class="sxs-lookup"><span data-stu-id="ab85a-107">The INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement provides the same basic behavior as regular INSERT but additionally supports a table hint for inserting the default values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab85a-108">有关跳过某个表列的格式化文件示例，请参阅[使用格式化文件跳过表列 (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab85a-108">For sample format files that skip a table column, see [Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md).</span></span>  
  
## <a name="sample-table-and-data-file"></a><span data-ttu-id="ab85a-109">示例表和数据文件</span><span class="sxs-lookup"><span data-stu-id="ab85a-109">Sample Table and Data File</span></span>  
 <span data-ttu-id="ab85a-110">若要运行本主题中的示例，需要创建示例表和数据文件。</span><span class="sxs-lookup"><span data-stu-id="ab85a-110">To run the examples in this topic, you need to create a sample table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="ab85a-111">示例表</span><span class="sxs-lookup"><span data-stu-id="ab85a-111">Sample Table</span></span>  
 <span data-ttu-id="ab85a-112">这些示例要求 **dbo** 架构下的 **AdventureWorks** 示例数据库中存在名为 **MyTestDefaultCol2** 的表。</span><span class="sxs-lookup"><span data-stu-id="ab85a-112">The examples require that a table named **MyTestDefaultCol2** be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="ab85a-113">若要创建此表，请在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查询编辑器中执行：</span><span class="sxs-lookup"><span data-stu-id="ab85a-113">To create this table, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE MyTestDefaultCol2   
(Col1 smallint,  
Col2 nvarchar(50) DEFAULT 'Default value of Col2',  
Col3 nvarchar(50)   
);  
GO  
  
```  
  
 <span data-ttu-id="ab85a-114">注意，第二个表列 ( `Col2`) 具有默认值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-114">Notice that the second table column, `Col2`, has a default value.</span></span>  
  
### <a name="sample-format-file"></a><span data-ttu-id="ab85a-115">示例格式化文件</span><span class="sxs-lookup"><span data-stu-id="ab85a-115">Sample Format File</span></span>  
 <span data-ttu-id="ab85a-116">某些大容量导入示例使用非 XML 格式化文件 `MyTestDefaultCol2-f-c.Fmt`，它与 `MyTestDefaultCol2` 表完全一致。</span><span class="sxs-lookup"><span data-stu-id="ab85a-116">Some of the bulk-import examples use a non-XML format file, `MyTestDefaultCol2-f-c.Fmt` that corresponds exactly to the `MyTestDefaultCol2` table.</span></span> <span data-ttu-id="ab85a-117">若要创建此格式化文件，请在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示符下输入：</span><span class="sxs-lookup"><span data-stu-id="ab85a-117">To create this format file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 format nul -c -f C:\MyTestDefaultCol2-f-c.Fmt -t, -r\n -T  
  
```  
  
 <span data-ttu-id="ab85a-118">有关创建格式化文件的详细信息，请参阅 [创建格式化文件 (SQL Server)](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab85a-118">For more information about creating format files, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
### <a name="sample-data-file"></a><span data-ttu-id="ab85a-119">示例数据文件</span><span class="sxs-lookup"><span data-stu-id="ab85a-119">Sample Data File</span></span>  
 <span data-ttu-id="ab85a-120">该示例使用示例数据文件 `MyTestEmptyField2-c.Dat`，它的第二个字段中不包含值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-120">The example uses a sample data file, `MyTestEmptyField2-c.Dat`, that contains no values in the second field.</span></span> <span data-ttu-id="ab85a-121">`MyTestEmptyField2-c.Dat` 数据文件包含下列记录。</span><span class="sxs-lookup"><span data-stu-id="ab85a-121">The `MyTestEmptyField2-c.Dat` data file contains the following records.</span></span>  
  
```  
1,,DataField3  
2,,DataField3  
  
```  
  
## <a name="keeping-null-values-with-bcp-or-bulk-insert"></a><span data-ttu-id="ab85a-122">使 bcp 或 BULK INSERT 保留空值</span><span class="sxs-lookup"><span data-stu-id="ab85a-122">Keeping Null Values with bcp or BULK INSERT</span></span>  
 <span data-ttu-id="ab85a-123">下列限定符指定在大容量导入操作期间数据文件中的空字段保留其空值，而不继承表列的默认值（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="ab85a-123">The following qualifiers specify that an empty field in the data file retains its null value during the bulk-import operation, rather than inheriting a default value (if any) for the table columns.</span></span>  
  
|<span data-ttu-id="ab85a-124">Command</span><span class="sxs-lookup"><span data-stu-id="ab85a-124">Command</span></span>|<span data-ttu-id="ab85a-125">Qualifier</span><span class="sxs-lookup"><span data-stu-id="ab85a-125">Qualifier</span></span>|<span data-ttu-id="ab85a-126">限定符类型</span><span class="sxs-lookup"><span data-stu-id="ab85a-126">Qualifier type</span></span>|  
|-------------|---------------|--------------------|  
|<span data-ttu-id="ab85a-127">**bcp**</span><span class="sxs-lookup"><span data-stu-id="ab85a-127">**bcp**</span></span>|`-k`|<span data-ttu-id="ab85a-128">开关</span><span class="sxs-lookup"><span data-stu-id="ab85a-128">Switch</span></span>|  
|<span data-ttu-id="ab85a-129">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="ab85a-129">BULK INSERT</span></span>|<span data-ttu-id="ab85a-130">KEEPNULLS<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ab85a-130">KEEPNULLS<sup>1</sup></span></span>|<span data-ttu-id="ab85a-131">参数</span><span class="sxs-lookup"><span data-stu-id="ab85a-131">Argument</span></span>|  
  
 <span data-ttu-id="ab85a-132"><sup>1</sup>对于 BULK INSERT，如果默认值不可用，则必须将表列定义为允许 null 值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-132"><sup>1</sup> For BULK INSERT, if default values are not available, the table column must be defined to allow null values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab85a-133">这些限定符通过这些大容量导入命令禁止检查表上的 DEFAULT 定义。</span><span class="sxs-lookup"><span data-stu-id="ab85a-133">These qualifiers disable checking of DEFAULT definitions on a table by these bulk-import commands.</span></span> <span data-ttu-id="ab85a-134">然而，对于任何并发 INSERT 语句，都需要 DEFAULT 定义。</span><span class="sxs-lookup"><span data-stu-id="ab85a-134">However, for any concurrent INSERT statements, DEFAULT definitions are expected.</span></span>  
  
 <span data-ttu-id="ab85a-135">有关详细信息，请参阅 [bcp 实用工具](../../tools/bcp-utility.md) 和 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ab85a-135">For more information, see [bcp Utility](../../tools/bcp-utility.md) and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ab85a-136">示例</span><span class="sxs-lookup"><span data-stu-id="ab85a-136">Examples</span></span>  
 <span data-ttu-id="ab85a-137">本节中的示例使用 **bcp** 或 BULK INSERT 进行批量导入并保留 null 值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-137">The examples in this section bulk import using **bcp** or BULK INSERT and keep null values.</span></span>  
  
 <span data-ttu-id="ab85a-138">第二个表列 **Col2**具有默认值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-138">The second table column, **Col2**, has a default value.</span></span> <span data-ttu-id="ab85a-139">数据文件的相应字段包含空字符串。</span><span class="sxs-lookup"><span data-stu-id="ab85a-139">The corresponding field of the data file contains an empty string.</span></span> <span data-ttu-id="ab85a-140">默认情况下，当 **bcp** 或 BULK INSERT 用于将数据从此数据文件导入 **MyTestDefaultCol2** 表时，将插入 **Col2** 的默认值，这会产生下列结果：</span><span class="sxs-lookup"><span data-stu-id="ab85a-140">By default, when **bcp** or BULK INSERT is used to import data from this data file into the **MyTestDefaultCol2** table, the default value of **Col2** is inserted, producing the following result:</span></span>  
  
||||  
|-|-|-|  
|`1`|`Default value of Col2`|`DataField3`|  
|`2`|`Default value of Col2`|`DataField3`|  
  
 <span data-ttu-id="ab85a-141">若要插入 " `NULL` " 而不是 " `Default value of Col2` "，需要使用 `-k` switch 或 KEEPNULL 选项，如以下**bcp**和 BULK INSERT 示例所示。</span><span class="sxs-lookup"><span data-stu-id="ab85a-141">To insert "`NULL`" instead of "`Default value of Col2`", you need to use the `-k` switch or KEEPNULL option, as demonstrated in the following **bcp** and BULK INSERT examples.</span></span>  
  
#### <a name="using-bcp-and-keeping-null-values"></a><span data-ttu-id="ab85a-142">使用 bcp 并保留空值</span><span class="sxs-lookup"><span data-stu-id="ab85a-142">Using bcp and Keeping Null Values</span></span>  
 <span data-ttu-id="ab85a-143">下列示例演示如何在 **bcp** 命令中保留 null 值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-143">The following example demonstrates how to keep null values in a **bcp** command.</span></span> <span data-ttu-id="ab85a-144">**Bcp**命令包含以下开关：</span><span class="sxs-lookup"><span data-stu-id="ab85a-144">The **bcp** command contains the following switches:</span></span>  
  
|<span data-ttu-id="ab85a-145">开关</span><span class="sxs-lookup"><span data-stu-id="ab85a-145">Switch</span></span>|<span data-ttu-id="ab85a-146">说明</span><span class="sxs-lookup"><span data-stu-id="ab85a-146">Description</span></span>|  
|------------|-----------------|  
|`-f`|<span data-ttu-id="ab85a-147">指定命令使用格式化文件。</span><span class="sxs-lookup"><span data-stu-id="ab85a-147">Specifies that the command is using a format file..</span></span>|  
|`-k`|<span data-ttu-id="ab85a-148">指定在操作过程中空列应该保留 null 值，而不是所插入列的任何默认值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-148">Specifies that empty columns should retain a null value during the operation, rather than have any default values for the columns inserted.</span></span>|  
|`-T`|<span data-ttu-id="ab85a-149">指定 bcp 实用工具使用可信连接来连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ab85a-149">Specifies that the bcp utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection.</span></span>|  
  
 <span data-ttu-id="ab85a-150">在 Windows 命令提示符下输入。</span><span class="sxs-lookup"><span data-stu-id="ab85a-150">At the Windows command prompt, enter.</span></span>  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 in C:\MyTestEmptyField2-c.Dat -f C:\MyTestDefaultCol2-f-c.Fmt -k -T  
  
```  
  
#### <a name="using-bulk-insert-and-keeping-null-values"></a><span data-ttu-id="ab85a-151">使用 BULK INSERT 并保留空值</span><span class="sxs-lookup"><span data-stu-id="ab85a-151">Using BULK INSERT and Keeping Null Values</span></span>  
 <span data-ttu-id="ab85a-152">下面的示例演示如何使用 BULK INSERT 语句中的 KEEPNULLS 选项。</span><span class="sxs-lookup"><span data-stu-id="ab85a-152">The following example demonstrates how to use the KEEPNULLS option in a BULK INSERT statement.</span></span> <span data-ttu-id="ab85a-153">在查询工具（如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查询编辑器）中执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="ab85a-153">From a query tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT MyTestDefaultCol2  
   FROM 'C:\MyTestEmptyField2-c.Dat'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      KEEPNULLS  
   );  
GO  
  
```  
  
## <a name="keeping-default-values-with-insert--select--from-openrowsetbulk"></a><span data-ttu-id="ab85a-154">用 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) </span><span class="sxs-lookup"><span data-stu-id="ab85a-154">Keeping Default Values with INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
 <span data-ttu-id="ab85a-155">默认情况下，未在大容量加载操作中指定的所有列都将通过 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) 。但是，您可以为数据文件中的空字段指定，如果有任何) ，相应的表列将使用其默认值 (。</span><span class="sxs-lookup"><span data-stu-id="ab85a-155">By default, any columns that are not specified in the bulk-load operation are set to NULL by INSERT ... SELECT \* FROM OPENROWSET(BULK...). However, you can specify that for an empty field in the data file, the corresponding table column uses its default value (if any).</span></span> <span data-ttu-id="ab85a-156">若要使用默认值，请指定下列表提示：</span><span class="sxs-lookup"><span data-stu-id="ab85a-156">To use default values, specify the following table hint:</span></span>  
  
|<span data-ttu-id="ab85a-157">Command</span><span class="sxs-lookup"><span data-stu-id="ab85a-157">Command</span></span>|<span data-ttu-id="ab85a-158">Qualifier</span><span class="sxs-lookup"><span data-stu-id="ab85a-158">Qualifier</span></span>|<span data-ttu-id="ab85a-159">限定符类型</span><span class="sxs-lookup"><span data-stu-id="ab85a-159">Qualifier Type</span></span>|  
|-------------|---------------|--------------------|  
|<span data-ttu-id="ab85a-160">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="ab85a-160">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="ab85a-161">WITH(KEEPDEFAULTS)</span><span class="sxs-lookup"><span data-stu-id="ab85a-161">WITH(KEEPDEFAULTS)</span></span>|<span data-ttu-id="ab85a-162">表提示</span><span class="sxs-lookup"><span data-stu-id="ab85a-162">Table hint</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ab85a-163">有关详细信息，请参阅[INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/insert-transact-sql)，[选择 &#40;Transact-sql&#41;](/sql/t-sql/queries/select-transact-sql)、 [OPENROWSET &#40;transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql)和[表提示 &#40;transact-sql&#41;](/sql/t-sql/queries/hints-transact-sql-table)</span><span class="sxs-lookup"><span data-stu-id="ab85a-163">for more information, see [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), and [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ab85a-164">示例</span><span class="sxs-lookup"><span data-stu-id="ab85a-164">Examples</span></span>  
 <span data-ttu-id="ab85a-165">以下 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) 示例大容量导入数据并保留默认值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-165">The following INSERT ... SELECT \* FROM OPENROWSET(BULK...) example bulk imports data and keeps the default values.</span></span>  
  
 <span data-ttu-id="ab85a-166">若要运行这些示例，需要创建 **MyTestDefaultCol2** 示例表和 `MyTestEmptyField2-c.Dat` 数据文件，并使用格式化文件 `MyTestDefaultCol2-f-c.Fmt`。</span><span class="sxs-lookup"><span data-stu-id="ab85a-166">To run the examples, you need to create the **MyTestDefaultCol2** sample table, the `MyTestEmptyField2-c.Dat` data file, and use a format file, `MyTestDefaultCol2-f-c.Fmt`.</span></span> <span data-ttu-id="ab85a-167">有关创建这些示例的信息，请参阅本主题前面的“示例表和数据文件”。</span><span class="sxs-lookup"><span data-stu-id="ab85a-167">For information on creating these samples, see "Sample Table and Data File," earlier in this topic.</span></span>  
  
 <span data-ttu-id="ab85a-168">第二个表列 **Col2**具有默认值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-168">The second table column, **Col2**, has a default value.</span></span> <span data-ttu-id="ab85a-169">数据文件的相应字段包含空字符串。</span><span class="sxs-lookup"><span data-stu-id="ab85a-169">The corresponding field of the data file contains an empty string.</span></span> <span data-ttu-id="ab85a-170">INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) 将此数据文件的字段导入**MyTestDefaultCol2**表，默认情况下，NULL 将插入**Col2**而不是默认值。</span><span class="sxs-lookup"><span data-stu-id="ab85a-170">When INSERT ... SELECT \* FROM OPENROWSET(BULK...) import the fields of this data file into the **MyTestDefaultCol2** table, by default, NULL is inserted into **Col2** instead of the default value.</span></span> <span data-ttu-id="ab85a-171">此默认的行为产生下列结果：</span><span class="sxs-lookup"><span data-stu-id="ab85a-171">This default behavior produces the following result:</span></span>  
  
||||  
|-|-|-|  
|`1`|`NULL`|`DataField3`|  
|`2`|`NULL`|`DataField3`|  
  
 <span data-ttu-id="ab85a-172">若要插入默认值“`Default value of Col2`”代替“`NULL`”，需要使用 KEEPDEFAULTS 表提示，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="ab85a-172">To insert the default value, "`Default value of Col2`", instead of "`NULL`", you need to use KEEPDEFAULTS table hint, as demonstrated in the following example.</span></span> <span data-ttu-id="ab85a-173">在查询工具（如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查询编辑器）中执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="ab85a-173">From a query tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
INSERT INTO MyTestDefaultCol2  
    WITH (KEEPDEFAULTS)  
    SELECT *  
      FROM OPENROWSET(BULK  'C:\MyTestEmptyField2-c.Dat',  
      FORMATFILE='C:\MyTestDefaultCol2-f-c.Fmt'       
      ) as t1 ;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ab85a-174">相关任务</span><span class="sxs-lookup"><span data-stu-id="ab85a-174">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ab85a-175">批量导入数据时保留标识值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-175">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="ab85a-176">准备用于批量导出或导入的数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-176">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="ab85a-177">**使用格式化文件**</span><span class="sxs-lookup"><span data-stu-id="ab85a-177">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="ab85a-178">创建格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-178">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="ab85a-179">使用格式化文件批量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-179">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="ab85a-180">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-180">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="ab85a-181">使用格式化文件跳过数据字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-181">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="ab85a-182">使用格式化文件跳过表列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-182">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="ab85a-183">**使用数据格式进行大容量导入或大容量导出**</span><span class="sxs-lookup"><span data-stu-id="ab85a-183">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="ab85a-184">导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据</span><span class="sxs-lookup"><span data-stu-id="ab85a-184">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="ab85a-185">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-185">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="ab85a-186">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-186">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="ab85a-187">使用 Unicode 字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-187">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="ab85a-188">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-188">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="ab85a-189">**在使用 bcp 时指定数据格式以获得兼容性**</span><span class="sxs-lookup"><span data-stu-id="ab85a-189">**To specify data formats for compatibility when using bcp**</span></span>  
  
-   [<span data-ttu-id="ab85a-190">指定字段终止符和行终止符 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-190">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="ab85a-191">使用 bcp 指定数据文件中的前缀长度 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-191">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="ab85a-192">使用 bcp 指定文件存储类型 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab85a-192">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="ab85a-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab85a-193">See Also</span></span>  
 <span data-ttu-id="ab85a-194">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab85a-194">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="ab85a-195">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab85a-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="ab85a-196">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ab85a-196">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="ab85a-197">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab85a-197">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="ab85a-198">表提示 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab85a-198">Table Hints &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
