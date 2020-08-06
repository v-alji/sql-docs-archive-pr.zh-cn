---
title: 使用本机格式导入或导出数据 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- data formats [SQL Server], native
ms.assetid: eb279b2f-0f1f-428f-9b8f-2a7fc495b79f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab42ba3eb6468aac3da2fa780d371818c8776690
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693356"
---
# <a name="use-native-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="bf974-102">使用本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bf974-102">Use Native Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="bf974-103">当使用不包含任何扩展/双字节字符集 (DBCS) 字符的数据文件在多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间大容量传输数据时，建议使用本机格式。</span><span class="sxs-lookup"><span data-stu-id="bf974-103">Native format is recommended when you bulk transfer data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a data file that does not contain any extended/double-byte character set (DBCS) characters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf974-104">若要使用包含扩展字符或 DBCS 字符的数据文件在多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间大容量传输数据，应使用 Unicode 本机格式。</span><span class="sxs-lookup"><span data-stu-id="bf974-104">To bulk transfer data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters, you should use the Unicode native format.</span></span> <span data-ttu-id="bf974-105">有关详细信息信息，请参阅 [使用 Unicode 本机格式导入或导出数据 (SQL Server)](use-unicode-native-format-to-import-or-export-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bf974-105">For more information, see [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="bf974-106">本机格式保留数据库的本机数据类型。</span><span class="sxs-lookup"><span data-stu-id="bf974-106">Native format maintains the native data types of a database.</span></span> <span data-ttu-id="bf974-107">本机格式适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表之间的高速数据传输。</span><span class="sxs-lookup"><span data-stu-id="bf974-107">Native format is intended for high-speed data transfer of data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="bf974-108">如果使用格式化文件，则源表和目标表不必相同。</span><span class="sxs-lookup"><span data-stu-id="bf974-108">If you use a format file, the source and target tables do not need to be identical.</span></span> <span data-ttu-id="bf974-109">数据传输分为两个步骤：</span><span class="sxs-lookup"><span data-stu-id="bf974-109">The data transfer involves two steps:</span></span>  
  
1.  <span data-ttu-id="bf974-110">将源表中的数据批量导出到数据文件中</span><span class="sxs-lookup"><span data-stu-id="bf974-110">Bulk exporting the data from a source table into a data file</span></span>  
  
2.  <span data-ttu-id="bf974-111">将数据文件中的数据批量导入到目标表中</span><span class="sxs-lookup"><span data-stu-id="bf974-111">Bulk importing the data from the data file into the target table</span></span>  
  
 <span data-ttu-id="bf974-112">在相同的表之间使用本机格式避免了在各数据类型与字符格式之间进行不必要的转换，从而节省了时间和空间。</span><span class="sxs-lookup"><span data-stu-id="bf974-112">The use of native format between identical tables avoids unnecessary conversion of data types to and from character format, saving time and space.</span></span> <span data-ttu-id="bf974-113">但是，若要获得最佳的传输速率，应执行几个有关数据格式的检查。</span><span class="sxs-lookup"><span data-stu-id="bf974-113">To achieve the optimum transfer rate, however, few checks are performed regarding data formatting.</span></span> <span data-ttu-id="bf974-114">为了防止加载的数据出现问题，请参阅以下限制列表。</span><span class="sxs-lookup"><span data-stu-id="bf974-114">To prevent problems with the loaded data, see the following restrictions list.</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="bf974-115">限制</span><span class="sxs-lookup"><span data-stu-id="bf974-115">Restrictions</span></span>  
 <span data-ttu-id="bf974-116">若要成功导入本机格式的数据，请确保：</span><span class="sxs-lookup"><span data-stu-id="bf974-116">To import data in native format successfully, ensure that:</span></span>  
  
-   <span data-ttu-id="bf974-117">数据文件是本机格式的文件。</span><span class="sxs-lookup"><span data-stu-id="bf974-117">The data file is in native format.</span></span>  
  
-   <span data-ttu-id="bf974-118">目标表必须与数据文件（含有正确的列数、数据类型、长度及 NULL 状态等）兼容，或者您必须使用格式化文件将每一个字段映射到其相应列。</span><span class="sxs-lookup"><span data-stu-id="bf974-118">Either the target table must be compatible with the data file (having the correct number of columns, data type, length, NULL status, and so forth), or you must use a format file to map each field to its corresponding columns.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bf974-119">如果从与目标表不匹配的文件中导入数据，那么导入操作可能会成功，但插入到目标表中的数据值很可能是错误的。</span><span class="sxs-lookup"><span data-stu-id="bf974-119">If you import data from a file that is mismatched with the target table, the import operation might succeed but the data values inserted into the target table are likely to be incorrect.</span></span> <span data-ttu-id="bf974-120">这是由于文件中的数据是通过使用目标表的格式来解释的。</span><span class="sxs-lookup"><span data-stu-id="bf974-120">This is because the data from the file is interpreted by using the format of the target table.</span></span> <span data-ttu-id="bf974-121">因此，任何不匹配都会导致插入错误值。</span><span class="sxs-lookup"><span data-stu-id="bf974-121">Therefore, any mismatch results in the insertion of incorrect values.</span></span> <span data-ttu-id="bf974-122">但是，这样的不匹配决不会导致数据库中出现逻辑或物理不一致。</span><span class="sxs-lookup"><span data-stu-id="bf974-122">However, under no circumstances can such a mismatch cause logical or physical inconsistencies in the database.</span></span>  
  
     <span data-ttu-id="bf974-123">有关使用格式化文件的信息，请参阅[用于导入或导出数据的格式化文件 (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bf974-123">For information on using format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="bf974-124">成功的导入操作不会损坏目标表。</span><span class="sxs-lookup"><span data-stu-id="bf974-124">A successful import will not corrupt the target table.</span></span>  
  
## <a name="how-bcp-handles-data-in-native-format"></a><span data-ttu-id="bf974-125">bcp 如何处理本机格式的数据</span><span class="sxs-lookup"><span data-stu-id="bf974-125">How bcp Handles Data in Native Format</span></span>  
 <span data-ttu-id="bf974-126">本节论述了 **bcp** 实用工具如何导出和导入本机格式数据的特殊注意事项。</span><span class="sxs-lookup"><span data-stu-id="bf974-126">This section discusses special considerations for how the **bcp** utility exports and imports data in native format.</span></span>  
  
-   <span data-ttu-id="bf974-127">非字符数据</span><span class="sxs-lookup"><span data-stu-id="bf974-127">Noncharacter data</span></span>  
  
     <span data-ttu-id="bf974-128">bcp 实用工具使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部二进制数据格式将表中的非字符数据写入数据文件中。</span><span class="sxs-lookup"><span data-stu-id="bf974-128">The bcp utility uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internal binary data format to write noncharacter data from a table to a data file.</span></span>  
  
-   <span data-ttu-id="bf974-129">`char` 数据或 `varchar` 数据</span><span class="sxs-lookup"><span data-stu-id="bf974-129">`char` or `varchar` data</span></span>  
  
     <span data-ttu-id="bf974-130">在每个 `char` 或字段的开头 `varchar` ， **bcp**都添加前缀长度。</span><span class="sxs-lookup"><span data-stu-id="bf974-130">At the beginning of each `char` or `varchar` field, **bcp** adds the prefix length.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="bf974-131">使用本机模式时，默认情况下， **bcp**实用工具将字符从转换 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 为 OEM 字符，然后将这些字符复制到数据文件。</span><span class="sxs-lookup"><span data-stu-id="bf974-131">When native mode is used, by default, the **bcp** utility converts characters from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to OEM characters before it copies them to a data file.</span></span> <span data-ttu-id="bf974-132">**Bcp**实用工具将数据文件中的字符转换为 ANSI 字符，然后将这些字符大容量导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="bf974-132">The **bcp** utility converts characters from a data file to ANSI characters before it bulk imports them into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="bf974-133">在执行这些转换过程中，可能丢失扩展字符数据。</span><span class="sxs-lookup"><span data-stu-id="bf974-133">During these conversions, extended character data can be lost.</span></span> <span data-ttu-id="bf974-134">对于扩展字符，请使用 Unicode 本机格式或指定代码页。</span><span class="sxs-lookup"><span data-stu-id="bf974-134">For extended characters, either use Unicode native format or specify a code page.</span></span>  
  
-   <span data-ttu-id="bf974-135">`sql_variant` 数据</span><span class="sxs-lookup"><span data-stu-id="bf974-135">`sql_variant` data</span></span>  
  
     <span data-ttu-id="bf974-136">如果 `sql_variant` 数据以 SQLVARIANT 存储在本机格式数据文件中，则数据会保留其所有特征。</span><span class="sxs-lookup"><span data-stu-id="bf974-136">If `sql_variant` data is stored as a SQLVARIANT in a native-format data file, the data maintains all of its characteristics.</span></span> <span data-ttu-id="bf974-137">记录每个数据值的数据类型的元数据与数据值一起存储。</span><span class="sxs-lookup"><span data-stu-id="bf974-137">The metadata that records the data type of each data value is stored along with the data value.</span></span> <span data-ttu-id="bf974-138">此元数据用于在目标 `sql_variant` 列中重新创建具有相同数据类型的数据值。</span><span class="sxs-lookup"><span data-stu-id="bf974-138">This metadata is used to re-create the data value with the same data type in a destination `sql_variant` column.</span></span>  
  
     <span data-ttu-id="bf974-139">如果目标列的数据类型不是 `sql_variant`，则每个数据值将按照隐式数据转换的一般规则转换为目标列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="bf974-139">If the data type of the destination column is not `sql_variant`, each data value is converted to the data type of the destination column, following the normal rules of implicit data conversion.</span></span> <span data-ttu-id="bf974-140">如果在数据转换过程中出现错误，则回滚当前批。</span><span class="sxs-lookup"><span data-stu-id="bf974-140">If an error occurs during data conversion, the current batch is rolled back.</span></span> <span data-ttu-id="bf974-141">在 `char` 列之间传输的任何 `varchar` 值和 `sql_variant` 值都可能存在代码页转换问题。</span><span class="sxs-lookup"><span data-stu-id="bf974-141">Any `char` and `varchar` values that are transferred between `sql_variant` columns may have code page conversion issues.</span></span>  
  
     <span data-ttu-id="bf974-142">有关数据转换的详细信息，请参阅[数据类型转换（数据库引擎）](/sql/t-sql/data-types/data-type-conversion-database-engine)。</span><span class="sxs-lookup"><span data-stu-id="bf974-142">For more information about data conversion, see [Data Type Conversion &#40;Database Engine&#41;](/sql/t-sql/data-types/data-type-conversion-database-engine).</span></span>  
  
## <a name="command-options-for-native-format"></a><span data-ttu-id="bf974-143">本机格式的命令选项</span><span class="sxs-lookup"><span data-stu-id="bf974-143">Command Options for Native Format</span></span>  
 <span data-ttu-id="bf974-144">可以使用**bcp**、BULK INSERT 或 INSERT ... 将本机格式数据导入表中。\*从 OPENROWSET (BULK ... ) 中进行选择。对于**bcp**命令或 BULK INSERT 语句，可以在命令行中指定数据格式。</span><span class="sxs-lookup"><span data-stu-id="bf974-144">You can import native format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="bf974-145">对于 INSERT ...SELECT \* FROM OPENROWSET(BULK...) 语句，必须在格式化文件中指定数据格式。</span><span class="sxs-lookup"><span data-stu-id="bf974-145">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="bf974-146">下列命令行选项支持本机格式：</span><span class="sxs-lookup"><span data-stu-id="bf974-146">Native format is supported by the following command line options:</span></span>  
  
|<span data-ttu-id="bf974-147">Command</span><span class="sxs-lookup"><span data-stu-id="bf974-147">Command</span></span>|<span data-ttu-id="bf974-148">选项</span><span class="sxs-lookup"><span data-stu-id="bf974-148">Option</span></span>|<span data-ttu-id="bf974-149">说明</span><span class="sxs-lookup"><span data-stu-id="bf974-149">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="bf974-150">**bcp**</span><span class="sxs-lookup"><span data-stu-id="bf974-150">**bcp**</span></span>|<span data-ttu-id="bf974-151">**-n**</span><span class="sxs-lookup"><span data-stu-id="bf974-151">**-n**</span></span>|<span data-ttu-id="bf974-152">使**bcp**实用工具使用数据的本机数据类型。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bf974-152">Causes the **bcp** utility to use the native data types of the data.<sup>1</sup></span></span>|  
|<span data-ttu-id="bf974-153">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="bf974-153">BULK INSERT</span></span>|<span data-ttu-id="bf974-154">DATAFILETYPE **= '** native **'**</span><span class="sxs-lookup"><span data-stu-id="bf974-154">DATAFILETYPE **='** native **'**</span></span>|<span data-ttu-id="bf974-155">使用本机数据类型或宽本机数据类型的数据。</span><span class="sxs-lookup"><span data-stu-id="bf974-155">Uses the native or wide native data types of the data.</span></span> <span data-ttu-id="bf974-156">注意，如果格式化文件指定了数据类型，则不需要 DATAFILETYPE。</span><span class="sxs-lookup"><span data-stu-id="bf974-156">Note that DATAFILETYPE is not needed if a format file specifies the data types.</span></span>|  
  
 <span data-ttu-id="bf974-157"><sup>1</sup>若要将本机\*\* () \*\*数据加载到与早期版本的客户端兼容的格式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请使用 **-V**开关。</span><span class="sxs-lookup"><span data-stu-id="bf974-157"><sup>1</sup> To load native (**-n**) data to a format compatible with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients, use the **-V** switch.</span></span> <span data-ttu-id="bf974-158">有关详细信息，请参阅 [导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bf974-158">For more information, see [Import Native and Character Format Data from Earlier Versions of SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).</span></span>  
  
 <span data-ttu-id="bf974-159">有关详细信息，请参阅 [bcp 实用工具](../../tools/bcp-utility.md)、[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) 或 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bf974-159">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf974-160">或者，您可以在格式化文件中为每个字段指定格式设置。</span><span class="sxs-lookup"><span data-stu-id="bf974-160">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="bf974-161">有关详细信息，请参阅 [用来导入或导出数据的格式化文件 (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bf974-161">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bf974-162">示例</span><span class="sxs-lookup"><span data-stu-id="bf974-162">Examples</span></span>  
 <span data-ttu-id="bf974-163">下列示例演示如何使用 **bcp** 批量导出本机数据以及使用 BULK INSERT 批量导入相同数据。</span><span class="sxs-lookup"><span data-stu-id="bf974-163">The following examples demonstrate how to bulk export native data using **bcp** and bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="bf974-164">示例表</span><span class="sxs-lookup"><span data-stu-id="bf974-164">Sample Table</span></span>  
 <span data-ttu-id="bf974-165">下列示例要求 **dbo** 架构下的 **AdventureWorks** 示例数据库中存在名为 **myTestNativeData** 的表。</span><span class="sxs-lookup"><span data-stu-id="bf974-165">The examples require that a table named **myTestNativeData** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="bf974-166">必须先创建此表，才能运行这些示例。</span><span class="sxs-lookup"><span data-stu-id="bf974-166">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="bf974-167">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="bf974-167">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="bf974-168">若要填充此表并查看得到的内容，请执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="bf974-168">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a><span data-ttu-id="bf974-169">使用 bcp 大容量导出本机数据</span><span class="sxs-lookup"><span data-stu-id="bf974-169">Using bcp to Bulk Export Native Data</span></span>  
 <span data-ttu-id="bf974-170">若要将表中数据导出到数据文件，请将 **bcp** 与 **out** 选项和以下限定符结合使用：</span><span class="sxs-lookup"><span data-stu-id="bf974-170">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="bf974-171">限定符</span><span class="sxs-lookup"><span data-stu-id="bf974-171">Qualifiers</span></span>|<span data-ttu-id="bf974-172">说明</span><span class="sxs-lookup"><span data-stu-id="bf974-172">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="bf974-173">**-n**</span><span class="sxs-lookup"><span data-stu-id="bf974-173">**-n**</span></span>|<span data-ttu-id="bf974-174">指定本机数据类型。</span><span class="sxs-lookup"><span data-stu-id="bf974-174">Specifies native data types.</span></span>|  
|<span data-ttu-id="bf974-175">**-T**</span><span class="sxs-lookup"><span data-stu-id="bf974-175">**-T**</span></span>|<span data-ttu-id="bf974-176">指定 **bcp** 实用工具通过使用集成安全性的受信任连接连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bf974-176">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="bf974-177">如果未指定 **-T** ，则需要指定 **-U** 和 **-P** 才能成功登录。</span><span class="sxs-lookup"><span data-stu-id="bf974-177">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="bf974-178">以下示例将本机格式的数据从 `myTestNativeData` 表大容量导出到名为 `myTestNativeData-n.Dat` 的新数据文件中。</span><span class="sxs-lookup"><span data-stu-id="bf974-178">The following example bulk exports data in native format from the `myTestNativeData` table into a new data file named `myTestNativeData-n.Dat` data file.</span></span> <span data-ttu-id="bf974-179">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示符下输入：</span><span class="sxs-lookup"><span data-stu-id="bf974-179">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..myTestNativeData out C:\myTestNativeData-n.Dat -n -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a><span data-ttu-id="bf974-180">使用 BULK INSERT 大容量导入本机数据</span><span class="sxs-lookup"><span data-stu-id="bf974-180">Using BULK INSERT to Bulk Import Native Data</span></span>  
 <span data-ttu-id="bf974-181">以下示例使用 BULK INSERT 将 `myTestNativeData-n.Dat` 数据文件中的数据导入到 `myTestNativeData` 表中。</span><span class="sxs-lookup"><span data-stu-id="bf974-181">The following example uses BULK INSERT to import the data in the `myTestNativeData-n.Dat` data file into the `myTestNativeData` table.</span></span> <span data-ttu-id="bf974-182">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="bf974-182">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestNativeData   
    FROM 'C:\myTestNativeData-n.Dat'   
   WITH (DATAFILETYPE='native');   
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="bf974-183">相关任务</span><span class="sxs-lookup"><span data-stu-id="bf974-183">Related Tasks</span></span>  
 <span data-ttu-id="bf974-184">**使用数据格式进行大容量导入或大容量导出**</span><span class="sxs-lookup"><span data-stu-id="bf974-184">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="bf974-185">导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据</span><span class="sxs-lookup"><span data-stu-id="bf974-185">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="bf974-186">使用字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bf974-186">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="bf974-187">使用 Unicode 字符格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bf974-187">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="bf974-188">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bf974-188">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="bf974-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf974-189">See Also</span></span>  
 <span data-ttu-id="bf974-190">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="bf974-190">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="bf974-191">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bf974-191">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="bf974-192">[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bf974-192">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="bf974-193">[sql_variant (Transact-SQL)](/sql/t-sql/data-types/sql-variant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bf974-193">[sql_variant &#40;Transact-SQL&#41;](/sql/t-sql/data-types/sql-variant-transact-sql) </span></span>  
 <span data-ttu-id="bf974-194">[导入来自早期版本的 SQL Server 的本机格式数据和字符格式数据](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bf974-194">[Import Native and Character Format Data from Earlier Versions of SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md) </span></span>  
 <span data-ttu-id="bf974-195">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bf974-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="bf974-196">使用 Unicode 本机格式导入或导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bf974-196">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
  
