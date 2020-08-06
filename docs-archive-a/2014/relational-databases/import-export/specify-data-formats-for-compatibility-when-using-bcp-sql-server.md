---
title: 在使用 bcp 时指定数据格式以获得兼容性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], compatibility
- bulk importing [SQL Server], compatibility
- compatibility [SQL Server], data formats
- data formats [SQL Server], compatibility
- bcp utility [SQL Server], compatibility
ms.assetid: cd5fc8c8-eab1-4165-9468-384f31e53f0a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d12456760f32ddbd8cc434d474aebb0e0ecf141
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692420"
---
# <a name="specify-data-formats-for-compatibility-when-using-bcp-sql-server"></a><span data-ttu-id="edf4e-102">在使用 bcp 时指定数据格式以获得兼容性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="edf4e-102">Specify Data Formats for Compatibility when Using bcp (SQL Server)</span></span>
  <span data-ttu-id="edf4e-103">本主题介绍数据格式属性、特定于字段的提示，以及在命令的非 xml 格式化文件中存储字段中的数据 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `bcp` 。</span><span class="sxs-lookup"><span data-stu-id="edf4e-103">This topic describes the data-format attributes, field-specific prompts, and storing field-by-field data in a non-xml format file of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`bcp` command.</span></span> <span data-ttu-id="edf4e-104">在您大容量导出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据以便大容量导入到其他程序（例如其他数据库程序）时，理解上述概念可能会对您很有帮助。</span><span class="sxs-lookup"><span data-stu-id="edf4e-104">Understanding these can be helpful when you bulk export [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data for bulk import into another program, such as another database program.</span></span> <span data-ttu-id="edf4e-105">源表中的默认数据格式（本机、字符或 Unicode）可能与其他程序所需的数据布局不兼容。如果存在不兼容，则导出数据时，必须说明数据布局。</span><span class="sxs-lookup"><span data-stu-id="edf4e-105">The default data formats (native, character, or Unicode) in the source table might be incompatible with the data layout expected by the other program If an incompatibility exists, when you export the data, you must describe the data layout.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="edf4e-106">如果不熟悉导入或导出数据的数据格式，请参阅 [用于批量导入或导出的数据格式 (SQL Server)](data-formats-for-bulk-import-or-bulk-export-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="edf4e-106">If you are unfamiliar with data formats for importing or exporting data, see [Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md).</span></span>  
  
 <span data-ttu-id="edf4e-107">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="edf4e-107">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="edf4e-108">bcp 数据格式属性</span><span class="sxs-lookup"><span data-stu-id="edf4e-108">bcp Data-Format Attributes</span></span>](#bcpDataFormatAttr)  
  
-   [<span data-ttu-id="edf4e-109">特定于字段的提示概述</span><span class="sxs-lookup"><span data-stu-id="edf4e-109">Overview of the Field-Specific Prompts</span></span>](#FieldSpecificPrompts)  
  
-   [<span data-ttu-id="edf4e-110">将字段中的数据存储在非 XML 格式化文件中</span><span class="sxs-lookup"><span data-stu-id="edf4e-110">Storing Field-by-Field Data in a Non-XML Format File</span></span>](#FieldByFieldNonXmlFF)  
  
-   [<span data-ttu-id="edf4e-111">相关任务</span><span class="sxs-lookup"><span data-stu-id="edf4e-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="bcp-data-format-attributes"></a><a name="bcpDataFormatAttr"></a> <span data-ttu-id="edf4e-112">bcp 数据格式属性</span><span class="sxs-lookup"><span data-stu-id="edf4e-112">bcp Data-Format Attributes</span></span>  
 <span data-ttu-id="edf4e-113">`bcp` 命令允许您按照下列数据格式属性指定数据文件中每个字段的结构：</span><span class="sxs-lookup"><span data-stu-id="edf4e-113">The `bcp` command allows you to specify the structure of each field in a data file in terms of the following data-format attributes:</span></span>  
  
-   <span data-ttu-id="edf4e-114">文件存储类型</span><span class="sxs-lookup"><span data-stu-id="edf4e-114">File storage type</span></span>  
  
     <span data-ttu-id="edf4e-115">“文件存储类型”  说明数据在数据文件中的存储方式。</span><span class="sxs-lookup"><span data-stu-id="edf4e-115">The *file storage type* describes how data is stored in the data file.</span></span> <span data-ttu-id="edf4e-116">数据可以按其数据库表类型（本机格式）、字符表示形式（字符格式）或支持隐式转换的任何数据类型导出到数据文件中；例如，以 `smallint` 形式复制 `int`。</span><span class="sxs-lookup"><span data-stu-id="edf4e-116">Data can be exported to a data file as its database table type (native format), in its character representation (character format), or as any data type where implicit conversion is supported; for example, copying a `smallint` as an `int`.</span></span> <span data-ttu-id="edf4e-117">用户定义的数据类型将按其基类型导出。</span><span class="sxs-lookup"><span data-stu-id="edf4e-117">User-defined data types are exported as their base types.</span></span> <span data-ttu-id="edf4e-118">有关详细信息，请参阅 [使用 bcp 指定文件存储类型 (SQL Server)](specify-file-storage-type-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="edf4e-118">For more information, see [Specify File Storage Type by Using bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="edf4e-119">前缀长度</span><span class="sxs-lookup"><span data-stu-id="edf4e-119">Prefix length</span></span>  
  
     <span data-ttu-id="edf4e-120">当以本机格式将数据大容量导出到数据文件时，为使文件存储空间最为紧凑，`bcp` 命令将在每个字段前面使用一个或多个字符来指示字段的长度。</span><span class="sxs-lookup"><span data-stu-id="edf4e-120">To provide the most compact file storage for the bulk export of data in native format to a data file, the `bcp` command precedes each field with one or more characters that indicates the length of the field.</span></span> <span data-ttu-id="edf4e-121">这些字符称为“长度前缀字符”  。</span><span class="sxs-lookup"><span data-stu-id="edf4e-121">These characters are called *length prefix characters*.</span></span> <span data-ttu-id="edf4e-122">有关详细信息，请参阅 [使用 bcp 指定数据文件中的前缀长度 (SQL Server)](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="edf4e-122">For more information, see [Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="edf4e-123">字段长度</span><span class="sxs-lookup"><span data-stu-id="edf4e-123">Field length</span></span>  
  
     <span data-ttu-id="edf4e-124">字段长度指示以字符格式表示数据时所要求的最大字符数。</span><span class="sxs-lookup"><span data-stu-id="edf4e-124">The field length indicates the maximum number of characters that are required to represent data in character format.</span></span> <span data-ttu-id="edf4e-125">如果数据以本机格式存储，则字段长度已知。</span><span class="sxs-lookup"><span data-stu-id="edf4e-125">The field length is already known if the data is stored in the native format.</span></span> <span data-ttu-id="edf4e-126">有关详细信息，请参阅 [使用 bcp 指定字段长度 (SQL Server)](specify-field-length-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="edf4e-126">For more information, see [Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="edf4e-127">字段终止符</span><span class="sxs-lookup"><span data-stu-id="edf4e-127">Field terminator</span></span>  
  
     <span data-ttu-id="edf4e-128">对于字符数据字段，可以选择使用终止字符标记数据文件中每个字段的结尾（使用“字段终止符”  ）以及每行的结尾（使用“行终止符”  ）。</span><span class="sxs-lookup"><span data-stu-id="edf4e-128">For character data fields, optional terminating characters allow you to mark the end of each field in a data file (using a *field terminator*) and the end of each row (using a *row terminator*).</span></span> <span data-ttu-id="edf4e-129">终止符是为读取数据文件的程序提供的一种方法，用于指出一个字段或行的结束位置和另一个字段或行的开始位置。</span><span class="sxs-lookup"><span data-stu-id="edf4e-129">Terminating characters are one way to indicate to programs reading the data file where one field or row ends and another begins.</span></span> <span data-ttu-id="edf4e-130">有关详细信息，请参阅 [指定字段终止符和行终止符 (SQL Server)](specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="edf4e-130">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>  
  
##  <a name="overview-of-the-field-specific-prompts"></a><a name="FieldSpecificPrompts"></a> <span data-ttu-id="edf4e-131">字段特定的提示概述</span><span class="sxs-lookup"><span data-stu-id="edf4e-131">Overview of the Field-Specific Prompts</span></span>  
 <span data-ttu-id="edf4e-132">如果交互式 `bcp` 命令包含**in**或**out**选项，但不包含格式化文件开关 (**-f**) 或数据格式开关 (**-n**、 **-c**、 **-w**或 **-n**) ，则在源或目标表中的每一列都将分别提示输入每个前述特性。</span><span class="sxs-lookup"><span data-stu-id="edf4e-132">If an interactive `bcp` command contains the **in** or **out** option but does not also contain either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**),  each column in the source or target table, the command prompts for each of the preceding attributes, in turn.</span></span> <span data-ttu-id="edf4e-133">在每个提示中，`bcp` 命令都根据表列的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型提供一个默认值。</span><span class="sxs-lookup"><span data-stu-id="edf4e-133">In each prompt, the `bcp` command provides a default value based on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the table column.</span></span> <span data-ttu-id="edf4e-134">接受所有提示的默认值生成的结果与在命令行指定本机格式 ( **-n**) 生成的结果相同。</span><span class="sxs-lookup"><span data-stu-id="edf4e-134">Accepting the default value for all of the prompts produces the same result as specifying native format (**-n**) on the command line.</span></span> <span data-ttu-id="edf4e-135">每个提示都会显示一个用方括号括起来的默认值：[*default*]。</span><span class="sxs-lookup"><span data-stu-id="edf4e-135">Each prompt displays a default value in brackets: [*default*].</span></span> <span data-ttu-id="edf4e-136">按 Enter 即接受显示的默认值。</span><span class="sxs-lookup"><span data-stu-id="edf4e-136">Pressing ENTER accepts the displayed default.</span></span> <span data-ttu-id="edf4e-137">若要指定与默认值不同的值，请在提示符下输入新值。</span><span class="sxs-lookup"><span data-stu-id="edf4e-137">To specify a value other than the default, enter the new value at the prompt.</span></span>  
  
### <a name="example"></a><span data-ttu-id="edf4e-138">示例</span><span class="sxs-lookup"><span data-stu-id="edf4e-138">Example</span></span>  
 <span data-ttu-id="edf4e-139">以下示例使用 `bcp` 命令以交互方式将 `HumanResources.myTeam` 表中的数据大容量导出到 `myTeam.txt` 文件中。</span><span class="sxs-lookup"><span data-stu-id="edf4e-139">The following example uses the `bcp` command to bulk export data from the `HumanResources.myTeam` table interactively to the `myTeam.txt` file.</span></span> <span data-ttu-id="edf4e-140">在运行该示例之前，必须创建此表。</span><span class="sxs-lookup"><span data-stu-id="edf4e-140">Before you can run the example, you must create this table.</span></span> <span data-ttu-id="edf4e-141">有关该表和如何创建该表的信息，请参阅 [HumanResources.myTeam 示例表 (SQL Server)](humanresources-myteam-sample-table-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="edf4e-141">For information about the table and how to create it, see [HumanResources.myTeam Sample Table &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md).</span></span>  
  
 <span data-ttu-id="edf4e-142">由于命令中既未指定格式化文件，也未指定数据类型，因此 `bcp` 将提示输入数据格式信息。</span><span class="sxs-lookup"><span data-stu-id="edf4e-142">The command specifies neither a format file nor a data type, causing `bcp` to prompt for data-format information.</span></span> <span data-ttu-id="edf4e-143">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示符下输入：</span><span class="sxs-lookup"><span data-stu-id="edf4e-143">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam out myTeam.txt -T  
```  
  
 <span data-ttu-id="edf4e-144">对于每列，bcp 都提示输入字段特定的值。</span><span class="sxs-lookup"><span data-stu-id="edf4e-144">For each column, bcp prompts for field-specific values.</span></span> <span data-ttu-id="edf4e-145">以下示例显示了针对表中 `EmployeeID` 和 `Name` 两个字段的提示，并为每列提供了建议的默认文件存储类型（本机格式）。</span><span class="sxs-lookup"><span data-stu-id="edf4e-145">The following example shows the field-specific prompts for the `EmployeeID` and `Name` columns of the table, and suggests the default file storage type (the native format) for each column.</span></span> <span data-ttu-id="edf4e-146">`EmployeeID` 和 `Name` 列的前缀长度分别为 0 和 2。</span><span class="sxs-lookup"><span data-stu-id="edf4e-146">The prefix lengths of the `EmployeeID` and `Name` column are 0 and 2, respectively.</span></span> <span data-ttu-id="edf4e-147">用户指定英文逗号 (`,`) 作为每个字段的终止符。</span><span class="sxs-lookup"><span data-stu-id="edf4e-147">The user specifies a comma (`,`) as the terminator of each field.</span></span>  
  
 `Enter the file storage type of field EmployeeID [smallint]:`  
  
 `Enter prefix-length of field EmployeeID [0]:`  
  
 `Enter field terminator [none]:,`  
  
 `Enter the file storage type of field Name [nvarchar]:`  
  
 `Enter prefix length of field Name [2]:`  
  
 `Enter field terminator [none]:,`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 <span data-ttu-id="edf4e-148">依次针对每个表列显示以上提示（根据需要）。</span><span class="sxs-lookup"><span data-stu-id="edf4e-148">Equivalent prompts (as needed) are displayed for each of the table columns in order.</span></span>  
  
##  <a name="storing-field-by-field-data-in-a-non-xml-format-file"></a><a name="FieldByFieldNonXmlFF"></a> <span data-ttu-id="edf4e-149">将逐个字段数据存储在非 XML 格式化文件中</span><span class="sxs-lookup"><span data-stu-id="edf4e-149">Storing Field-by-Field Data in a Non-XML Format File</span></span>  
 <span data-ttu-id="edf4e-150">指定所有的表列后，`bcp` 命令将提示选择生成非 XML 格式化文件，以存储刚刚得到的逐个字段信息（请参阅上述示例）。</span><span class="sxs-lookup"><span data-stu-id="edf4e-150">After all of the table columns are specified, the `bcp` command prompts you to optionally generate a non-XML format file that stores the field-by-field information just supplied (see the preceding example).</span></span> <span data-ttu-id="edf4e-151">如果选择生成格式化文件，则可以随时从表中导出数据，也可以将结构类似的数据导入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="edf4e-151">If you choose to generate a format file, you can whenever you export data out of that table or import like-structured data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="edf4e-152">可以使用格式化文件将数据文件中的数据大容量导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例中，也可以使用格式化文件从表中大容量导出数据，而无需重新指定格式。</span><span class="sxs-lookup"><span data-stu-id="edf4e-152">You can use the format file to bulk import data from the data file into an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to bulk export data from the table, without needing to respecify the format.</span></span> <span data-ttu-id="edf4e-153">有关详细信息，请参阅 [用来导入或导出数据的格式化文件 (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="edf4e-153">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="edf4e-154">以下示例创建一个名为 `myFormatFile.fmt`的非 XML 格式化文件：</span><span class="sxs-lookup"><span data-stu-id="edf4e-154">The following example creates a non-XML format file named `myFormatFile.fmt`:</span></span>  
  
 `Do you want to save this format information in a file? [Y/n] y`  
  
 `Host filename: [bcp.fmt]myFormatFile.fmt`  
  
 <span data-ttu-id="edf4e-155">该格式化文件的默认名称为 bcp.fmt，但您可以指定其他文件名。</span><span class="sxs-lookup"><span data-stu-id="edf4e-155">The default name for the format file is bcp.fmt, but you can specify a different file name if you choose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="edf4e-156">对于使用单一数据格式（如字符或本机格式）作为文件存储类型的数据文件，可以快速创建格式化文件，而无需使用 **格式** 选项导出或导入数据。</span><span class="sxs-lookup"><span data-stu-id="edf4e-156">For a data file that uses a single data format for its file-storage type, such as character or native format, you can quickly create a format file without exporting or importing data by using the **format** option.</span></span> <span data-ttu-id="edf4e-157">这种方法的优点在于操作简单以及允许用户创建 XML 格式化文件或非 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="edf4e-157">This approach has the advantages of being easy and of allowing you to create either an XML format file or a non-XML format file.</span></span> <span data-ttu-id="edf4e-158">有关详细信息，请参阅 [创建格式化文件 (SQL Server)](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="edf4e-158">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="edf4e-159">相关任务</span><span class="sxs-lookup"><span data-stu-id="edf4e-159">Related Tasks</span></span>  
  
-   [<span data-ttu-id="edf4e-160">使用 bcp 指定文件存储类型 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="edf4e-160">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="edf4e-161">使用 bcp 指定数据文件中的前缀长度 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="edf4e-161">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="edf4e-162">使用 bcp 指定字段长度 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="edf4e-162">Specify Field Length by Using bcp &#40;SQL Server&#41;</span></span>](specify-field-length-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="edf4e-163">指定字段终止符和行终止符 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="edf4e-163">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
## <a name="related-content"></a><span data-ttu-id="edf4e-164">相关内容</span><span class="sxs-lookup"><span data-stu-id="edf4e-164">Related Content</span></span>  
 <span data-ttu-id="edf4e-165">无。</span><span class="sxs-lookup"><span data-stu-id="edf4e-165">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf4e-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="edf4e-166">See Also</span></span>  
 <span data-ttu-id="edf4e-167">[批量导入和导出数据 (SQL Server)](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="edf4e-167">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="edf4e-168">[用于批量导入或导出的数据格式 (SQL Server)](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="edf4e-168">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 <span data-ttu-id="edf4e-169">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="edf4e-169">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="edf4e-170">数据类型 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="edf4e-170">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
