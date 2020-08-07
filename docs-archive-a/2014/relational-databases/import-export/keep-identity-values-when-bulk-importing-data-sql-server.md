---
title: 批量导入数据时保留标识值 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- identity values [SQL Server], bulk imports
- data formats [SQL Server], identity values
- bulk importing [SQL Server], identity values
ms.assetid: 45894a3f-2d8a-4edd-9568-afa7d0d3061f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07f6714f27f60afda91134034509ff439d92f071
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589074"
---
# <a name="keep-identity-values-when-bulk-importing-data-sql-server"></a><span data-ttu-id="c5c12-102">批量导入数据时保留标识值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-102">Keep Identity Values When Bulk Importing Data (SQL Server)</span></span>
  <span data-ttu-id="c5c12-103">包含标识值的数据文件可以大容量导入到的实例中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c5c12-103">Data files that contain identity values can be bulk imported into an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5c12-104">默认情况下，将忽略导入的数据文件中标识列的值， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 自动分配唯一值。</span><span class="sxs-lookup"><span data-stu-id="c5c12-104">By default, the values for the identity column in the data file that is imported are ignored and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns unique values automatically.</span></span> <span data-ttu-id="c5c12-105">这些唯一值基于在表创建期间指定的种子和增量值。</span><span class="sxs-lookup"><span data-stu-id="c5c12-105">The unique values are based on the seed and increment values that are specified during table creation.</span></span>  
  
 <span data-ttu-id="c5c12-106">如果该数据文件表中的标识符列不包含值，则使用格式化文件来指定导入数据时应跳过表中的标识符列。</span><span class="sxs-lookup"><span data-stu-id="c5c12-106">If the data file does not contain values for the identifier column in the table, use a format file to specify that the identifier column in the table should be skipped when importing data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c5c12-107">自动为此列分配唯一值。</span><span class="sxs-lookup"><span data-stu-id="c5c12-107">assigns unique values for the column automatically.</span></span>  
  
 <span data-ttu-id="c5c12-108">若要防止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在将数据行大容量导入到表中时分配标识值，请使用相应的保留标识命令限定符。</span><span class="sxs-lookup"><span data-stu-id="c5c12-108">To prevent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from assigning identity values while bulk importing data rows into a table, use the appropriate keep-identity command qualifier.</span></span> <span data-ttu-id="c5c12-109">在您指定保留标识限定符后， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将在该数据文件中使用标识值。</span><span class="sxs-lookup"><span data-stu-id="c5c12-109">When you specify a keep-identity qualifier, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the identity values in the data file.</span></span> <span data-ttu-id="c5c12-110">这些限定符如下：</span><span class="sxs-lookup"><span data-stu-id="c5c12-110">These qualifiers are as follows:</span></span>  
  
|<span data-ttu-id="c5c12-111">Command</span><span class="sxs-lookup"><span data-stu-id="c5c12-111">Command</span></span>|<span data-ttu-id="c5c12-112">保留标识限定符</span><span class="sxs-lookup"><span data-stu-id="c5c12-112">Keep-identity qualifier</span></span>|<span data-ttu-id="c5c12-113">限定符类型</span><span class="sxs-lookup"><span data-stu-id="c5c12-113">Qualifier type</span></span>|  
|-------------|------------------------------|--------------------|  
|`bcp`|<span data-ttu-id="c5c12-114">**-E**</span><span class="sxs-lookup"><span data-stu-id="c5c12-114">**-E**</span></span>|<span data-ttu-id="c5c12-115">开关</span><span class="sxs-lookup"><span data-stu-id="c5c12-115">Switch</span></span>|  
|<span data-ttu-id="c5c12-116">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="c5c12-116">BULK INSERT</span></span>|<span data-ttu-id="c5c12-117">KEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="c5c12-117">KEEPIDENTITY</span></span>|<span data-ttu-id="c5c12-118">参数</span><span class="sxs-lookup"><span data-stu-id="c5c12-118">Argument</span></span>|  
|<span data-ttu-id="c5c12-119">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="c5c12-119">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="c5c12-120">KEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="c5c12-120">KEEPIDENTITY</span></span>|<span data-ttu-id="c5c12-121">表提示</span><span class="sxs-lookup"><span data-stu-id="c5c12-121">Table hint</span></span>|  
  
 <span data-ttu-id="c5c12-122">有关详细信息，请参阅 [bcp 实用工具](../../tools/bcp-utility.md)、[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)、[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)、[INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql)、[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) 和[表提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table)。</span><span class="sxs-lookup"><span data-stu-id="c5c12-122">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql), and [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5c12-123">要创建一个可在多个表中使用的自动递增数字或者可以从应用程序中调用而不引用任何表的自动递增数字，请参阅[序列号](../sequence-numbers/sequence-numbers.md)。</span><span class="sxs-lookup"><span data-stu-id="c5c12-123">To create an automatically incrementing number that can be used in multiple tables or that can be called from applications without referencing any table, see [Sequence Numbers](../sequence-numbers/sequence-numbers.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c5c12-124">示例</span><span class="sxs-lookup"><span data-stu-id="c5c12-124">Examples</span></span>  
 <span data-ttu-id="c5c12-125">本主题中的示例使用 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) 并保留默认值。</span><span class="sxs-lookup"><span data-stu-id="c5c12-125">The examples in this topic bulk import data using INSERT ... SELECT \* FROM OPENROWSET(BULK...) and keeping default values.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="c5c12-126">示例表</span><span class="sxs-lookup"><span data-stu-id="c5c12-126">Sample Table</span></span>  
 <span data-ttu-id="c5c12-127">大容量导入实例需要在 **dbo** 架构下的 **AdventureWorks** 示例数据库中创建一个名为 **myTestKeepNulls** 的表。</span><span class="sxs-lookup"><span data-stu-id="c5c12-127">The bulk-import examples require that a table named **myTestKeepNulls** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="c5c12-128">创建该表。</span><span class="sxs-lookup"><span data-stu-id="c5c12-128">To create this table.</span></span> <span data-ttu-id="c5c12-129">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="c5c12-129">in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
SELECT * INTO HumanResources.myDepartment   
   FROM HumanResources.Department  
      WHERE 1=0;  
GO  
SELECT * FROM HumanResources.myDepartment;  
```  
  
 <span data-ttu-id="c5c12-130">作为 `myDepartment` 基础的 **Department** 表的 IDENTITY_INSERT 设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="c5c12-130">The **Department** table on which `myDepartment` is based has IDENTITY_INSERT is set to OFF.</span></span> <span data-ttu-id="c5c12-131">因此，必须指定 KEEPIDENTITY 或 **-E**，才能将数据导入标识列。</span><span class="sxs-lookup"><span data-stu-id="c5c12-131">Therefore, to import data into an identity column you must specify KEEPIDENTITY or **-E**.</span></span>  
  
### <a name="sample-data-file"></a><span data-ttu-id="c5c12-132">示例数据文件</span><span class="sxs-lookup"><span data-stu-id="c5c12-132">Sample Data File</span></span>  
 <span data-ttu-id="c5c12-133">大容量导入示例中使用的数据文件包含从本机格式的 `HumanResources.Department` 表中大容量导出的数据。</span><span class="sxs-lookup"><span data-stu-id="c5c12-133">The data file used in the bulk-import examples contains data bulk exported from the `HumanResources.Department` table in native format.</span></span> <span data-ttu-id="c5c12-134">若要创建数据文件，请在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示符下输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="c5c12-134">To create the data file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department out myDepartment-n.Dat -n -T  
```  
  
### <a name="sample-format-file"></a><span data-ttu-id="c5c12-135">示例格式化文件</span><span class="sxs-lookup"><span data-stu-id="c5c12-135">Sample Format File</span></span>  
 <span data-ttu-id="c5c12-136">此大容量导入示例使用 XML 格式化文件 `myDepartment-f-x-n.Xml`，该文件使用本机数据格式。</span><span class="sxs-lookup"><span data-stu-id="c5c12-136">This bulk-import examples use an XML format file, `myDepartment-f-x-n.Xml`, which uses native data formats.</span></span> <span data-ttu-id="c5c12-137">此示例使用 `bcp` 进行创建，以从 `HumanResources.Department` 数据库的 `AdventureWorks` 表生成此格式化文件。</span><span class="sxs-lookup"><span data-stu-id="c5c12-137">This example uses `bcp` to create to generate this format file from the `HumanResources.Department` table of the `AdventureWorks` database.</span></span> <span data-ttu-id="c5c12-138">在 Windows 命令提示符下，输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="c5c12-138">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department format nul -n -x -f myDepartment-f-n-x.Xml -T  
```  
  
 <span data-ttu-id="c5c12-139">有关创建格式化文件的详细信息，请参阅[创建格式化文件 (SQL Server)](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c5c12-139">For more information about creating a format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
### <a name="a-using-bcp-and-keeping-identity-values"></a><span data-ttu-id="c5c12-140">A.</span><span class="sxs-lookup"><span data-stu-id="c5c12-140">A.</span></span> <span data-ttu-id="c5c12-141">使用 bcp 并保留标识值</span><span class="sxs-lookup"><span data-stu-id="c5c12-141">Using bcp and Keeping Identity Values</span></span>  
 <span data-ttu-id="c5c12-142">下面的示例说明如何在使用 `bcp` 大容量导入数据时保留标识值。</span><span class="sxs-lookup"><span data-stu-id="c5c12-142">The following example demonstrates how to keep identity values when using `bcp` to bulk import data.</span></span> <span data-ttu-id="c5c12-143">`bcp` 命令使用格式化文件 `myDepartment-f-n-x.Xml`，并包含下列开关：</span><span class="sxs-lookup"><span data-stu-id="c5c12-143">The `bcp` command uses the format file, `myDepartment-f-n-x.Xml`, and contains the following switches:</span></span>  
  
|<span data-ttu-id="c5c12-144">限定符</span><span class="sxs-lookup"><span data-stu-id="c5c12-144">Qualifiers</span></span>|<span data-ttu-id="c5c12-145">说明</span><span class="sxs-lookup"><span data-stu-id="c5c12-145">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="c5c12-146">**-E**</span><span class="sxs-lookup"><span data-stu-id="c5c12-146">**-E**</span></span>|<span data-ttu-id="c5c12-147">指定标识列使用数据文件中的标识值。</span><span class="sxs-lookup"><span data-stu-id="c5c12-147">Specifies that identity value or values in the data file are to be used for the identity column.</span></span>|  
|<span data-ttu-id="c5c12-148">**-T**</span><span class="sxs-lookup"><span data-stu-id="c5c12-148">**-T**</span></span>|<span data-ttu-id="c5c12-149">指定 `bcp` 实用工具 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用可信连接连接到。</span><span class="sxs-lookup"><span data-stu-id="c5c12-149">Specifies that the `bcp` utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection.</span></span>|  
  
 <span data-ttu-id="c5c12-150">在 Windows 命令提示符下输入。</span><span class="sxs-lookup"><span data-stu-id="c5c12-150">At the Windows command prompt, enter.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myDepartment in C:\myDepartment-n.Dat -f C:\myDepartment-f-n-x.Xml -E -T  
  
```  
  
### <a name="b-using-bulk-insert-and-keeping-identity-values"></a><span data-ttu-id="c5c12-151">B.</span><span class="sxs-lookup"><span data-stu-id="c5c12-151">B.</span></span> <span data-ttu-id="c5c12-152">使用 BULK INSERT 并保留标识值</span><span class="sxs-lookup"><span data-stu-id="c5c12-152">Using BULK INSERT and Keeping Identity Values</span></span>  
 <span data-ttu-id="c5c12-153">下面的示例使用 BULK INSERT 将数据从 `myDepartment-c.Dat` 文件大容量导入到 `AdventureWorks.HumanResources.myDepartment` 表中。</span><span class="sxs-lookup"><span data-stu-id="c5c12-153">The following example uses BULK INSERT to bulk import data from the `myDepartment-c.Dat` file into the `AdventureWorks.HumanResources.myDepartment` table.</span></span> <span data-ttu-id="c5c12-154">该语句使用 `myDepartment-f-n-x.Xml` 格式化文件，并包含 KEEPIDENTITY 选项来确保保留数据文件中的所有标识值。</span><span class="sxs-lookup"><span data-stu-id="c5c12-154">The statement uses the `myDepartment-f-n-x.Xml` format file and includes the KEEPIDENTITY option to ensure that any identity values in the data file are retained.</span></span>  
  
 <span data-ttu-id="c5c12-155">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行：</span><span class="sxs-lookup"><span data-stu-id="c5c12-155">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
BULK INSERT HumanResources.myDepartment  
   FROM 'C:\myDepartment-n.Dat'  
   WITH (  
      KEEPIDENTITY,  
      FORMATFILE='C:\myDepartment-f-n-x.Xml'  
   );  
GO  
SELECT * FROM HumanResources.myDepartment;  
  
```  
  
### <a name="c-using-openrowset-and-keeping-identity-values"></a><span data-ttu-id="c5c12-156">C.</span><span class="sxs-lookup"><span data-stu-id="c5c12-156">C.</span></span> <span data-ttu-id="c5c12-157">使用 OPENROWSET 并保留标识值</span><span class="sxs-lookup"><span data-stu-id="c5c12-157">Using OPENROWSET and Keeping Identity Values</span></span>  
 <span data-ttu-id="c5c12-158">下面的示例使用 OPENROWSET 大容量行集提供程序将数据从 `myDepartment-c.Dat` 文件大容量导入到 `AdventureWorks.HumanResources.myDepartment` 表中。</span><span class="sxs-lookup"><span data-stu-id="c5c12-158">The following example uses the OPENROWSET bulk rowset provider to bulk import data from the `myDepartment-c.Dat` file into the `AdventureWorks.HumanResources.myDepartment` table.</span></span> <span data-ttu-id="c5c12-159">该语句使用 `myDepartment-f-n-x.Xml` 格式化文件，并包含 KEEPIDENTITY 提示来确保保留数据文件中的所有标识值。</span><span class="sxs-lookup"><span data-stu-id="c5c12-159">The statement uses the `myDepartment-f-n-x.Xml` format file and includes the KEEPIDENTITY hint to ensure that any identity values in the data file are retained.</span></span>  
  
 <span data-ttu-id="c5c12-160">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行：</span><span class="sxs-lookup"><span data-stu-id="c5c12-160">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
  
INSERT INTO HumanResources.myDepartment  
   with (KEEPIDENTITY)  
   (DepartmentID, Name, GroupName, ModifiedDate)  
   SELECT *  
      FROM  OPENROWSET(BULK 'C:\myDepartment-n.Dat',  
      FORMATFILE='C:\myDepartment-f-n-x.Xml') as t1;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="c5c12-161">相关任务</span><span class="sxs-lookup"><span data-stu-id="c5c12-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="c5c12-162">在批量导入期间保留 Null 或使用默认值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-162">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="c5c12-163">准备用于批量导出或导入的数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-163">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="c5c12-164">**使用格式化文件**</span><span class="sxs-lookup"><span data-stu-id="c5c12-164">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="c5c12-165">创建格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-165">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="c5c12-166">使用格式化文件批量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-166">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="c5c12-167">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-167">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="c5c12-168">使用格式化文件跳过数据字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-168">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="c5c12-169">使用格式化文件跳过表列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-169">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="c5c12-170">**使用数据格式进行大容量导入或大容量导出**</span><span class="sxs-lookup"><span data-stu-id="c5c12-170">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="c5c12-171">导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据</span><span class="sxs-lookup"><span data-stu-id="c5c12-171">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="c5c12-172">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-172">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="c5c12-173">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-173">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="c5c12-174">使用 Unicode 字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-174">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="c5c12-175">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-175">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="c5c12-176">**在使用 bcp 时指定数据格式以获得兼容性**</span><span class="sxs-lookup"><span data-stu-id="c5c12-176">**To specify data formats for compatibility when using bcp**</span></span>  
  
1.  [<span data-ttu-id="c5c12-177">指定字段终止符和行终止符 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-177">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
2.  [<span data-ttu-id="c5c12-178">使用 bcp 指定数据文件中的前缀长度 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-178">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [<span data-ttu-id="c5c12-179">使用 bcp 指定文件存储类型 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c5c12-179">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="c5c12-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5c12-180">See Also</span></span>  
 <span data-ttu-id="c5c12-181">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5c12-181">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="c5c12-182">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="c5c12-182">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="c5c12-183">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5c12-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="c5c12-184">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5c12-184">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="c5c12-185">表提示 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c5c12-185">Table Hints &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
