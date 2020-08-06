---
title: 使用 bcp 指定文件存储类型 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], file storage types
- importing data, file storage types
- native data format [SQL Server]
- file storage types [SQL Server]
- data formats [SQL Server], file storage types
ms.assetid: 85e12df8-1be7-4bdc-aea9-05aade085c06
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1f3ad2a94ffe3e0f1db19a8e66f85497e7143dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578205"
---
# <a name="specify-file-storage-type-by-using-bcp-sql-server"></a><span data-ttu-id="aa3b1-102">使用 bcp 指定文件存储类型 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="aa3b1-102">Specify File Storage Type by Using bcp (SQL Server)</span></span>
  <span data-ttu-id="aa3b1-103">“文件存储类型”  说明数据在数据文件中的存储方式。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-103">The *file storage type* describes how data is stored in the data file.</span></span> <span data-ttu-id="aa3b1-104">数据可以按其数据库表类型（本机格式）、字符表示形式（字符格式）或支持隐式转换的任何数据类型导出到数据文件中；例如，以 `smallint` 形式复制 `int`。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-104">Data can be exported to a data file as its database table type (native format), in its character representation (character format), or as any data type where implicit conversion is supported; for example, copying a `smallint` as an `int`.</span></span> <span data-ttu-id="aa3b1-105">用户定义的数据类型将按其基类型导出。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-105">User-defined data types are exported as their base types.</span></span>  
  
## <a name="the-bcp-prompt-for-file-storage-type"></a><span data-ttu-id="aa3b1-106">用于文件存储类型的 bcp 提示符</span><span class="sxs-lookup"><span data-stu-id="aa3b1-106">The bcp Prompt for File Storage Type</span></span>  
 <span data-ttu-id="aa3b1-107">如果某个交互式 **bcp** 命令包含不带格式化文件开关 ( **-f** ) 或数据格式开关（ **-n** 、 **-c**、 **-w**或 **-N**）的 **in**或 **out**选项，则该命令会提示输入每个数据字段的文件存储类型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa3b1-107">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), the command prompts for the file storage type of each data field, as follows:</span></span>  
  
 `Enter the file storage type of field <field_name> [<default>]:`  
  
 <span data-ttu-id="aa3b1-108">您对此提示符的响应取决于要执行的任务，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa3b1-108">Your response to this prompt depends on the task you perform, as follows:</span></span>  
  
-   <span data-ttu-id="aa3b1-109">若要以尽可能大的压缩存储（本机数据格式）将数据从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例批量导出到数据文件中，请接受 bcp 提供的默认文件存储类型  。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-109">To bulk export data from an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file in the most compact storage possible (native data format), accept the default file storage types that are provided by **bcp**.</span></span> <span data-ttu-id="aa3b1-110">有关本机文件存储类型的列表，请参阅本主题后面所述的“本机文件存储类型”。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-110">For a list of the native file storage types, see "Native File Storage Types," later in this topic.</span></span>  
  
-   <span data-ttu-id="aa3b1-111">若要以字符格式将数据从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例大容量导出到数据文件中，请指定 `char` 作为表中所有列的文件存储类型。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-111">To bulk export data from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file in character format, specify `char` as the file storage type for all columns in the table.</span></span>  
  
-   <span data-ttu-id="aa3b1-112">若要将数据从数据文件大容量导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，对于以字符格式存储的类型，请将文件存储类型指定为 `char`，而对于以本机数据类型格式存储的数据，请按需指定以下文件存储类型之一：</span><span class="sxs-lookup"><span data-stu-id="aa3b1-112">To bulk import data to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a data file, specify the file storage type as `char` for types stored in character format and, for data stored in native data type format, specify one of the file storage types, as appropriate:</span></span>  
  
    |<span data-ttu-id="aa3b1-113">文件存储类型</span><span class="sxs-lookup"><span data-stu-id="aa3b1-113">File storage type</span></span>|<span data-ttu-id="aa3b1-114">在命令提示符下输入</span><span class="sxs-lookup"><span data-stu-id="aa3b1-114">Enter at command prompt</span></span>|  
    |-----------------------|-----------------------------|  
    |<span data-ttu-id="aa3b1-115">`char` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="aa3b1-115">`char` <sup>1</sup></span></span>|<span data-ttu-id="aa3b1-116">`c`[`har`]</span><span class="sxs-lookup"><span data-stu-id="aa3b1-116">`c`[`har`]</span></span>|  
    |`varchar`|`c[har]`|  
    |`nchar`|`w`|  
    |`nvarchar`|`w`|  
    |<span data-ttu-id="aa3b1-117">`text` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="aa3b1-117">`text` <sup>2</sup></span></span>|<span data-ttu-id="aa3b1-118">`T`[`ext`]</span><span class="sxs-lookup"><span data-stu-id="aa3b1-118">`T`[`ext`]</span></span>|  
    |`ntext2`|`W`|  
    |`binary`|`x`|  
    |`varbinary`|`x`|  
    |<span data-ttu-id="aa3b1-119">`image` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="aa3b1-119">`image` <sup>2</sup></span></span>|<span data-ttu-id="aa3b1-120">`I`[`mage`]</span><span class="sxs-lookup"><span data-stu-id="aa3b1-120">`I`[`mage`]</span></span>|  
    |`datetime`|<span data-ttu-id="aa3b1-121">**d[ate]**</span><span class="sxs-lookup"><span data-stu-id="aa3b1-121">**d[ate]**</span></span>|  
    |`smalldatetime`|`D`|  
    |`time`|`te`|  
    |`date`|`de`|  
    |`datetime2`|`d2`|  
    |`datetimeoffset`|`do`|  
    |`decimal`|`n`|  
    |`numeric`|`n`|  
    |`float`|<span data-ttu-id="aa3b1-122">**f[loat]**</span><span class="sxs-lookup"><span data-stu-id="aa3b1-122">**f[loat]**</span></span>|  
    |`real`|`r`|  
    |`Int`|<span data-ttu-id="aa3b1-123">**i[nt]**</span><span class="sxs-lookup"><span data-stu-id="aa3b1-123">**i[nt]**</span></span>|  
    |`bigint`|`B[igint]`|  
    |`smallint`|<span data-ttu-id="aa3b1-124">**s[mallint]**</span><span class="sxs-lookup"><span data-stu-id="aa3b1-124">**s[mallint]**</span></span>|  
    |`tinyint`|<span data-ttu-id="aa3b1-125">**t[inyint]**</span><span class="sxs-lookup"><span data-stu-id="aa3b1-125">**t[inyint]**</span></span>|  
    |`money`|<span data-ttu-id="aa3b1-126">**m[oney]**</span><span class="sxs-lookup"><span data-stu-id="aa3b1-126">**m[oney]**</span></span>|  
    |`smallmoney`|`M`|  
    |`bit`|`b[it]`|  
    |`uniqueidentifier`|`u`|  
    |`sql_variant`|`V[ariant]`|  
    |`timestamp`|`x`|  
    |<span data-ttu-id="aa3b1-127">`UDT`（用户定义的数据类型）</span><span class="sxs-lookup"><span data-stu-id="aa3b1-127">`UDT` (a user-defined data type)</span></span>|`U`|  
    |`XML`|`X`|  
  
     <span data-ttu-id="aa3b1-128"><sup>1</sup>字段长度、前缀长度和终止符的交互确定在数据文件中为导出为文件存储类型的非字符数据分配的存储空间量 `char` 。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-128"><sup>1</sup> The interaction of field length, prefix length, and terminators determines the amount of storage space that is allocated in a data file for noncharacter data that is exported as the `char` file storage type.</span></span>  
  
     <span data-ttu-id="aa3b1-129"><sup>2</sup>在 `ntext` `text` `image` 的未来版本中将删除、和数据类型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-129"><sup>2</sup> The `ntext`, `text`, and `image` data types will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="aa3b1-130">在新的开发工作中，请避免使用这些数据类型，并修改当前使用它们的应用程序。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-130">In new development work, avoid using these data types, and plan to modify applications that currently use them.</span></span> <span data-ttu-id="aa3b1-131">请改用 `nvarchar(max)` 、 `varchar(max)` 和 `varbinary(max)` 。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-131">Use `nvarchar(max)`, `varchar(max)`, and `varbinary(max)` instead.</span></span>  
  
## <a name="native-file-storage-types"></a><span data-ttu-id="aa3b1-132">本机文件存储类型</span><span class="sxs-lookup"><span data-stu-id="aa3b1-132">Native File Storage Types</span></span>  
 <span data-ttu-id="aa3b1-133">在格式化文件中，每种本机文件存储类型都记录为相应的宿主文件数据类型。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-133">Each native file storage type is recorded in the format file as a corresponding host file data type.</span></span>  
  
|<span data-ttu-id="aa3b1-134">文件存储类型</span><span class="sxs-lookup"><span data-stu-id="aa3b1-134">File storage type</span></span>|<span data-ttu-id="aa3b1-135">宿主文件数据类型</span><span class="sxs-lookup"><span data-stu-id="aa3b1-135">Host file data type</span></span>|  
|-----------------------|-------------------------|  
|<span data-ttu-id="aa3b1-136">`char` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="aa3b1-136">`char` <sup>1</sup></span></span>|<span data-ttu-id="aa3b1-137">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="aa3b1-137">SQLCHAR</span></span>|  
|`varchar`|<span data-ttu-id="aa3b1-138">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="aa3b1-138">SQLCHAR</span></span>|  
|`nchar`|<span data-ttu-id="aa3b1-139">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="aa3b1-139">SQLNCHAR</span></span>|  
|`nvarchar`|<span data-ttu-id="aa3b1-140">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="aa3b1-140">SQLNCHAR</span></span>|  
|<span data-ttu-id="aa3b1-141">`text` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="aa3b1-141">`text` <sup>2</sup></span></span>|<span data-ttu-id="aa3b1-142">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="aa3b1-142">SQLCHAR</span></span>|  
|<span data-ttu-id="aa3b1-143">`ntext` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="aa3b1-143">`ntext` <sup>2</sup></span></span>|<span data-ttu-id="aa3b1-144">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="aa3b1-144">SQLNCHAR</span></span>|  
|`binary`|<span data-ttu-id="aa3b1-145">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="aa3b1-145">SQLBINARY</span></span>|  
|`varbinary`|<span data-ttu-id="aa3b1-146">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="aa3b1-146">SQLBINARY</span></span>|  
|<span data-ttu-id="aa3b1-147">`image` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="aa3b1-147">`image` <sup>2</sup></span></span>|<span data-ttu-id="aa3b1-148">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="aa3b1-148">SQLBINARY</span></span>|  
|`datetime`|<span data-ttu-id="aa3b1-149">SQLDATETIME</span><span class="sxs-lookup"><span data-stu-id="aa3b1-149">SQLDATETIME</span></span>|  
|`smalldatetime`|<span data-ttu-id="aa3b1-150">SQLDATETIM4</span><span class="sxs-lookup"><span data-stu-id="aa3b1-150">SQLDATETIM4</span></span>|  
|`decimal`|<span data-ttu-id="aa3b1-151">SQLDECIMAL</span><span class="sxs-lookup"><span data-stu-id="aa3b1-151">SQLDECIMAL</span></span>|  
|`numeric`|<span data-ttu-id="aa3b1-152">SQLNUMERIC</span><span class="sxs-lookup"><span data-stu-id="aa3b1-152">SQLNUMERIC</span></span>|  
|`float`|<span data-ttu-id="aa3b1-153">SQLFLT8</span><span class="sxs-lookup"><span data-stu-id="aa3b1-153">SQLFLT8</span></span>|  
|`real`|<span data-ttu-id="aa3b1-154">SQLFLT4</span><span class="sxs-lookup"><span data-stu-id="aa3b1-154">SQLFLT4</span></span>|  
|`int`|<span data-ttu-id="aa3b1-155">SQLINT</span><span class="sxs-lookup"><span data-stu-id="aa3b1-155">SQLINT</span></span>|  
|`bigint`|<span data-ttu-id="aa3b1-156">SQLBIGINT</span><span class="sxs-lookup"><span data-stu-id="aa3b1-156">SQLBIGINT</span></span>|  
|`smallint`|<span data-ttu-id="aa3b1-157">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="aa3b1-157">SQLSMALLINT</span></span>|  
|`tinyint`|<span data-ttu-id="aa3b1-158">SQLTINYINT</span><span class="sxs-lookup"><span data-stu-id="aa3b1-158">SQLTINYINT</span></span>|  
|`money`|<span data-ttu-id="aa3b1-159">SQLMONEY</span><span class="sxs-lookup"><span data-stu-id="aa3b1-159">SQLMONEY</span></span>|  
|`smallmoney`|<span data-ttu-id="aa3b1-160">SQLMONEY4</span><span class="sxs-lookup"><span data-stu-id="aa3b1-160">SQLMONEY4</span></span>|  
|`bit`|<span data-ttu-id="aa3b1-161">SQLBIT</span><span class="sxs-lookup"><span data-stu-id="aa3b1-161">SQLBIT</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="aa3b1-162">SQLUNIQUEID</span><span class="sxs-lookup"><span data-stu-id="aa3b1-162">SQLUNIQUEID</span></span>|  
|`sql_variant`|<span data-ttu-id="aa3b1-163">SQLVARIANT</span><span class="sxs-lookup"><span data-stu-id="aa3b1-163">SQLVARIANT</span></span>|  
|`timestamp`|<span data-ttu-id="aa3b1-164">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="aa3b1-164">SQLBINARY</span></span>|  
|<span data-ttu-id="aa3b1-165">UDT（用户定义的数据类型）</span><span class="sxs-lookup"><span data-stu-id="aa3b1-165">UDT (a user-defined data type)</span></span>|<span data-ttu-id="aa3b1-166">SQLUDT</span><span class="sxs-lookup"><span data-stu-id="aa3b1-166">SQLUDT</span></span>|  
  
 <span data-ttu-id="aa3b1-167"><sup>1</sup>以字符格式存储的数据文件使用 `char` 作为文件存储类型。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-167"><sup>1</sup> Data files that are stored in character format use `char` as the file storage type.</span></span> <span data-ttu-id="aa3b1-168">因此，对于字符数据文件，SQLCHAR 是唯一出现在格式化文件中的数据类型。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-168">Therefore, for character data files, SQLCHAR is the only data type that appears in a format file.</span></span>  
  
 <span data-ttu-id="aa3b1-169"><sup>2</sup>无法将数据大容量导入到 `text` 、 `ntext` 和 `image` 具有默认值的列。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-169"><sup>2</sup> You cannot bulk import data into `text`, `ntext`, and `image` columns that have DEFAULT values.</span></span>  
  
## <a name="additional-considerations-for-file-storage-types"></a><span data-ttu-id="aa3b1-170">文件存储类型的其他注意事项</span><span class="sxs-lookup"><span data-stu-id="aa3b1-170">Additional Considerations for File Storage Types</span></span>  
 <span data-ttu-id="aa3b1-171">当您将数据从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例大容量导出到数据文件时：</span><span class="sxs-lookup"><span data-stu-id="aa3b1-171">When you bulk export data from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file:</span></span>  
  
-   <span data-ttu-id="aa3b1-172">您始终可以指定 `char` 作为文件存储类型。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-172">You can always specify `char` as the file storage type.</span></span>  
  
-   <span data-ttu-id="aa3b1-173">如果输入的文件存储类型表示无效的隐式转换， **bcp**将失败;例如，你可以为数据指定，但 `int` `smallint` 如果 `smallint` 为数据指定，则会 `int` 产生溢出错误。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-173">If you enter a file storage type that represents an invalid implicit conversion, **bcp** fails; for example, though you can specify `int` for `smallint` data, if you specify `smallint` for `int` data, overflow errors result.</span></span>  
  
-   <span data-ttu-id="aa3b1-174">当非字符数据类型（如 `float`、`money`、`datetime` 或 `int`）存储为其数据库类型时，数据将写入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机格式的数据文件。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-174">When noncharacter data types such as `float`, `money`, `datetime`, or `int` are stored as their database types, the data is written to the data file in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native format.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aa3b1-175">在你以交互方式指定 **bcp** 命令中的所有字段后，该命令会提示你将自己对每个字段的响应保存到一个非 XML 格式化文件中。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-175">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="aa3b1-176">有关非 XML 格式文件的详细信息，请参阅[ 非 XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="aa3b1-176">For more information on non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa3b1-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa3b1-177">See Also</span></span>  
 <span data-ttu-id="aa3b1-178">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="aa3b1-178">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="aa3b1-179">[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aa3b1-179">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="aa3b1-180">[使用 bcp 指定字段长度 (SQL Server)](specify-field-length-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aa3b1-180">[Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="aa3b1-181">[指定字段终止符和行终止符 (SQL Server)](specify-field-and-row-terminators-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aa3b1-181">[Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span></span>  
 [<span data-ttu-id="aa3b1-182">使用 bcp 指定数据文件中的前缀长度 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="aa3b1-182">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
  
