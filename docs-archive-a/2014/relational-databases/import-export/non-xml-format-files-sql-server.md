---
title: 非 XML 格式化文件 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- non-XML format files
- format files [SQL Server], non-XML format files
- bulk importing [SQL Server], format files
ms.assetid: f566db3e-0a3b-4a61-9c84-49f8d42f5760
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8fb040cb60eb188a7878357e7b45ca1114df2cdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693362"
---
# <a name="non-xml-format-files-sql-server"></a><span data-ttu-id="f93dd-102">非 XML 格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f93dd-102">Non-XML Format Files (SQL Server)</span></span>
  <span data-ttu-id="f93dd-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，大容量导出和导入支持两种类型的格式化文件：非 XML 格式化文件  和 XML 格式化文件  。</span><span class="sxs-lookup"><span data-stu-id="f93dd-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], two types of format files are supported for bulk exporting and importing: *non-XML format files* and *XML format files*.</span></span>  
  
 <span data-ttu-id="f93dd-104">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="f93dd-104">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="f93dd-105">优点</span><span class="sxs-lookup"><span data-stu-id="f93dd-105">Benefits</span></span>](#Benefits)  
  
-   [<span data-ttu-id="f93dd-106">非 XML 格式化文件的结构</span><span class="sxs-lookup"><span data-stu-id="f93dd-106">Structure of Non-XML Format Files</span></span>](#Structure)  
  
-   [<span data-ttu-id="f93dd-107">非 XML 格式化文件的示例</span><span class="sxs-lookup"><span data-stu-id="f93dd-107">Example of a Non-XML Format File</span></span>](#Examples)  
  
-   [<span data-ttu-id="f93dd-108">相关任务</span><span class="sxs-lookup"><span data-stu-id="f93dd-108">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits-of-non-xml-format-files"></a><a name="Benefits"></a> <span data-ttu-id="f93dd-109">非 XML 格式化文件的优点</span><span class="sxs-lookup"><span data-stu-id="f93dd-109">Benefits of Non-XML Format Files</span></span>  
  
-   <span data-ttu-id="f93dd-110">通过在 **bcp** 命令中指定 **format** 选项，可以自动创建非 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="f93dd-110">You can create a non-XML format file automatically by specifying the **format** option in a **bcp** command.</span></span>  
  
-   <span data-ttu-id="f93dd-111">当在 **bcp** 命令中指定某个现有的格式化文件时，该命令就使用记录在该格式化文件中的值，而不提示你输入文件存储类型、前缀长度、字段长度或字段终止符。</span><span class="sxs-lookup"><span data-stu-id="f93dd-111">When you specify an existing format file in a **bcp** command, the command uses the values that are recorded in the format file and does not prompt you for the file storage type, prefix length, field length, or field terminator.</span></span>  
  
-   <span data-ttu-id="f93dd-112">您可为特定的数据类型（例如字符数据或本机数据）创建格式化文件。</span><span class="sxs-lookup"><span data-stu-id="f93dd-112">You can create a format file for a particular data type such as character data or native data.</span></span>  
  
     <span data-ttu-id="f93dd-113">还可以创建非 XML 格式化文件，这种文件包含为每个数据字段交互式指定的属性。</span><span class="sxs-lookup"><span data-stu-id="f93dd-113">You can create a non-XML format file that contains interactively specified attributes for each data field.</span></span> <span data-ttu-id="f93dd-114">有关详细信息，请参阅[在使用 bcp 时指定数据格式以获得兼容性 (SQL Server)](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f93dd-114">For more information, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f93dd-115">XML 格式化文件与非 XML 格式化文件相比具有一些优点。</span><span class="sxs-lookup"><span data-stu-id="f93dd-115">XML format files offer several advantages over non-XML format files.</span></span> <span data-ttu-id="f93dd-116">有关详细信息，请参阅 [XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f93dd-116">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
##  <a name="structure-of-non-xml-format-files"></a><a name="Structure"></a> <span data-ttu-id="f93dd-117">非 XML 格式化文件的结构</span><span class="sxs-lookup"><span data-stu-id="f93dd-117">Structure of Non-XML Format Files</span></span>  
 <span data-ttu-id="f93dd-118">非 XML 格式化文件是具有特殊结构的文本文件。</span><span class="sxs-lookup"><span data-stu-id="f93dd-118">A non-XML format file is a text file that has a specific structure.</span></span> <span data-ttu-id="f93dd-119">非 XML 格式化文件包含了有关每个表列的文件存储类型、前缀长度、字段长度和字段终止符的信息。</span><span class="sxs-lookup"><span data-stu-id="f93dd-119">The non-XML format file contains information about the file storage type, prefix length, field length, and field terminator of every table column.</span></span>  
  
 <span data-ttu-id="f93dd-120">下图显示了一个示例非 XML 格式化文件的格式化文件字段。</span><span class="sxs-lookup"><span data-stu-id="f93dd-120">The following illustration illustrates the format-file fields for a sample non-XML format file.</span></span>  
  
 <span data-ttu-id="f93dd-121">![标识非 XML 格式文件的字段](../../database-engine/media/mydepart-fmt-ident-c.gif "标识非 XML 格式文件的字段")</span><span class="sxs-lookup"><span data-stu-id="f93dd-121">![Identifies the fields of a non-XML format file](../../database-engine/media/mydepart-fmt-ident-c.gif "Identifies the fields of a non-XML format file")</span></span>  
  
 <span data-ttu-id="f93dd-122"> “版本”和  “列数”字段仅出现一次。</span><span class="sxs-lookup"><span data-stu-id="f93dd-122">The **Version** and **Number of columns** fields occur one time only.</span></span> <span data-ttu-id="f93dd-123">下表对其意义进行了说明。</span><span class="sxs-lookup"><span data-stu-id="f93dd-123">Their meanings are describes in the following table.</span></span>  
  
|<span data-ttu-id="f93dd-124">格式化文件字段</span><span class="sxs-lookup"><span data-stu-id="f93dd-124">Format-file field</span></span>|<span data-ttu-id="f93dd-125">说明</span><span class="sxs-lookup"><span data-stu-id="f93dd-125">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="f93dd-126">版本</span><span class="sxs-lookup"><span data-stu-id="f93dd-126">Version</span></span>|<span data-ttu-id="f93dd-127">该版本号仅可由 **bcp**识别，而无法由 [!INCLUDE[tsql](../../includes/tsql-md.md)]识别。</span><span class="sxs-lookup"><span data-stu-id="f93dd-127">The version number is recognized only by **bcp**, not by [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f93dd-128">**bcp** 实用工具的版本号：</span><span class="sxs-lookup"><span data-stu-id="f93dd-128">Version number of the **bcp** utility:</span></span><br /><br /> <span data-ttu-id="f93dd-129">9.0 = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f93dd-129">9.0 = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]</span></span><br /><br /> <span data-ttu-id="f93dd-130">10.0 = [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f93dd-130">10.0 = [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]</span></span><br /><br /> <span data-ttu-id="f93dd-131">11.0 = [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f93dd-131">11.0 = [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]</span></span><br /><br /> <span data-ttu-id="f93dd-132">12.0 = [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f93dd-132">12.0 = [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]</span></span><br /><br /> <span data-ttu-id="f93dd-133">注意：读取格式化文件所用的 bcp 实用工具 (Bcp.exe) 的版本必须与创建格式化文件所用的版本相同或更高  。</span><span class="sxs-lookup"><span data-stu-id="f93dd-133">Note: The version of the **bcp** utility (Bcp.exe) used to read a format file must be the same as, or a later version than was used to create the format file.</span></span> <span data-ttu-id="f93dd-134">例如， [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]**bcp** 可以读取由 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]**bcp**生成的 10.0 版格式化文件，但 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]**bcp** 无法读取由 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]**bcp**生成的 12.0 版格式化文件。</span><span class="sxs-lookup"><span data-stu-id="f93dd-134">For example, [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]**bcp** can read a version 10.0 format file, which is generated by [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]**bcp**, but [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]**bcp** cannot read a version 12.0 format file, which is generated by [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]**bcp**.</span></span>|  
|<span data-ttu-id="f93dd-135">列数</span><span class="sxs-lookup"><span data-stu-id="f93dd-135">Number of columns</span></span>|<span data-ttu-id="f93dd-136">数据文件中字段的数目。</span><span class="sxs-lookup"><span data-stu-id="f93dd-136">Number of fields in the data file.</span></span> <span data-ttu-id="f93dd-137">该数目必须在所有行中都相同。</span><span class="sxs-lookup"><span data-stu-id="f93dd-137">This number must be the same in all rows.</span></span>|  
  
 <span data-ttu-id="f93dd-138">其他格式化文件字段说明需要大容量导入或导出的数据字段。</span><span class="sxs-lookup"><span data-stu-id="f93dd-138">The other format-file fields describe the data fields that are to be bulk imported or exported.</span></span> <span data-ttu-id="f93dd-139">每个数据字段都需在格式化文件中占单独一行。</span><span class="sxs-lookup"><span data-stu-id="f93dd-139">Each data field requires a separate row in the format file.</span></span> <span data-ttu-id="f93dd-140">每个格式化文件行均包含下表中说明的格式化文件字段的值。</span><span class="sxs-lookup"><span data-stu-id="f93dd-140">Every format-file row contains values for the format-file fields that are described in the following table.</span></span>  
  
|<span data-ttu-id="f93dd-141">格式化文件字段</span><span class="sxs-lookup"><span data-stu-id="f93dd-141">Format-file field</span></span>|<span data-ttu-id="f93dd-142">说明</span><span class="sxs-lookup"><span data-stu-id="f93dd-142">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="f93dd-143">**宿主文件字段顺序**</span><span class="sxs-lookup"><span data-stu-id="f93dd-143">**Host file field order**</span></span>|<span data-ttu-id="f93dd-144">用以表示数据文件中每个字段的位置的数字。</span><span class="sxs-lookup"><span data-stu-id="f93dd-144">A number that indicates the position of each field in the data file.</span></span> <span data-ttu-id="f93dd-145">行中的第一个字段为 1，依此类推。</span><span class="sxs-lookup"><span data-stu-id="f93dd-145">The first field in the row is 1, and so on.</span></span>|  
|<span data-ttu-id="f93dd-146">**宿主文件数据类型**</span><span class="sxs-lookup"><span data-stu-id="f93dd-146">**Host file data type**</span></span>|<span data-ttu-id="f93dd-147">表示存储在数据文件的给定字段中的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f93dd-147">Indicates the data type that is stored in a given field of the data file.</span></span> <span data-ttu-id="f93dd-148">对于 ASCII 数据文件，使用 SQLCHAR；对于本机格式数据文件，使用默认的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f93dd-148">With ASCII data files, use SQLCHAR; for native format data files, use default data types.</span></span> <span data-ttu-id="f93dd-149">有关详细信息，请参阅 [使用 bcp 指定文件存储类型 (SQL Server)](specify-file-storage-type-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f93dd-149">For more information, see [Specify File Storage Type by Using bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md).</span></span>|  
|<span data-ttu-id="f93dd-150">**前缀长度**</span><span class="sxs-lookup"><span data-stu-id="f93dd-150">**Prefix length**</span></span>|<span data-ttu-id="f93dd-151">字段长度前缀字符的数目。</span><span class="sxs-lookup"><span data-stu-id="f93dd-151">Number of length prefix characters for the field.</span></span> <span data-ttu-id="f93dd-152">有效前缀长度是 0、1、2、4 和 8。</span><span class="sxs-lookup"><span data-stu-id="f93dd-152">Valid prefix lengths are 0, 1, 2, 4, and 8.</span></span> <span data-ttu-id="f93dd-153">若要避免指定长度前缀，将其设置为 0。</span><span class="sxs-lookup"><span data-stu-id="f93dd-153">To avoid specifying the length prefix, set this to 0.</span></span> <span data-ttu-id="f93dd-154">如果字段包含 NULL 数据值，则必须指定长度前缀。</span><span class="sxs-lookup"><span data-stu-id="f93dd-154">A length prefix must be specified if the field contains NULL data values.</span></span> <span data-ttu-id="f93dd-155">有关详细信息，请参阅 [使用 bcp 指定数据文件中的前缀长度 (SQL Server)](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f93dd-155">For more information, see [Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md).</span></span>|  
|<span data-ttu-id="f93dd-156">**宿主文件数据长度**</span><span class="sxs-lookup"><span data-stu-id="f93dd-156">**Host file data length**</span></span>|<span data-ttu-id="f93dd-157">数据文件的特定字段中所存储的数据类型的最大长度（按字节计）。</span><span class="sxs-lookup"><span data-stu-id="f93dd-157">Maximum length, in bytes, of the data type stored in the particular field of the data file.</span></span><br /><br /> <span data-ttu-id="f93dd-158">如果您正在为带分隔符的文本文件创建非 XML 格式化文件，则可以将每个数据字段的宿主文件数据长度指定为 0。</span><span class="sxs-lookup"><span data-stu-id="f93dd-158">If you are creating a non-XML format file for a delimited text file, you can specify 0 for the host file data length of every data field.</span></span> <span data-ttu-id="f93dd-159">当带分隔符的文本文件的前缀长度为 0 并导入终止符时，可忽略字段长度值，因为字段所使用的存储空间等于数据加上终止符的长度。</span><span class="sxs-lookup"><span data-stu-id="f93dd-159">When a delimited text file having a prefix length of 0 and a terminator is imported, the field-length value is ignored, because the storage space used by the field equals the length of the data plus the terminator.</span></span><br /><br /> <span data-ttu-id="f93dd-160">有关详细信息，请参阅 [使用 bcp 指定字段长度 (SQL Server)](specify-field-length-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f93dd-160">For more information, see [Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md).</span></span>|  
|<span data-ttu-id="f93dd-161">**终止符**</span><span class="sxs-lookup"><span data-stu-id="f93dd-161">**Terminator**</span></span>|<span data-ttu-id="f93dd-162">用来分隔数据文件中各字段的分隔符。</span><span class="sxs-lookup"><span data-stu-id="f93dd-162">Delimiter to separate the fields in a data file.</span></span> <span data-ttu-id="f93dd-163">常用的终止符为逗号 (,)、制表符 (\t) 和行结束符 (\r\n)。</span><span class="sxs-lookup"><span data-stu-id="f93dd-163">Common terminators are comma (,), tab (\t), and end of line (\r\n).</span></span> <span data-ttu-id="f93dd-164">有关详细信息，请参阅 [指定字段终止符和行终止符 (SQL Server)](specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f93dd-164">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>|  
|<span data-ttu-id="f93dd-165">**服务器列顺序**</span><span class="sxs-lookup"><span data-stu-id="f93dd-165">**Server column order**</span></span>|<span data-ttu-id="f93dd-166">列在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表中显示的顺序。</span><span class="sxs-lookup"><span data-stu-id="f93dd-166">Order in which columns appear in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="f93dd-167">例如，如果数据文件的第四个字段映射到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表中的第六列，则第四个字段的服务器列顺序为 6。</span><span class="sxs-lookup"><span data-stu-id="f93dd-167">For example, if the fourth field in the data file maps to the sixth column in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table, the server column order for the fourth field is 6.</span></span><br /><br /> <span data-ttu-id="f93dd-168">若要阻止表中的某个列接收数据文件中的任何数据，则可以将服务器列顺序值设置为 0。</span><span class="sxs-lookup"><span data-stu-id="f93dd-168">To prevent a column in the table from receiving any data from the data file, set the server column order value to 0.</span></span>|  
|<span data-ttu-id="f93dd-169">**服务器列名**</span><span class="sxs-lookup"><span data-stu-id="f93dd-169">**Server column name**</span></span>|<span data-ttu-id="f93dd-170">从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表中复制的列名。</span><span class="sxs-lookup"><span data-stu-id="f93dd-170">Name of the column copied from the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="f93dd-171">无需使用字段的实际名称，但格式化文件中的字段不得为空。</span><span class="sxs-lookup"><span data-stu-id="f93dd-171">The actual name of the field is not required, but the field in the format file must not be blank.</span></span>|  
|<span data-ttu-id="f93dd-172">**列排序规则**</span><span class="sxs-lookup"><span data-stu-id="f93dd-172">**Column collation**</span></span>|<span data-ttu-id="f93dd-173">排序规则用于在数据文件中存储字符和 Unicode 数据。</span><span class="sxs-lookup"><span data-stu-id="f93dd-173">The collation used to store character and Unicode data in the data file.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="f93dd-174">您可以修改格式化文件，以便从字段编号或顺序与表列的编号或顺序不同的数据文件进行大容量导入。</span><span class="sxs-lookup"><span data-stu-id="f93dd-174">You can modify a format file to let you bulk import from a data file in which the number or order of the fields are different from the number or order of table columns.</span></span> <span data-ttu-id="f93dd-175">有关详细信息，请参阅本主题后面的 [相关任务](#RelatedTasks) 列表。</span><span class="sxs-lookup"><span data-stu-id="f93dd-175">For more information, see the [Related Tasks](#RelatedTasks) list, later in this topic.</span></span>  
  
##  <a name="example-of-a-non-xml-format-file"></a><a name="Examples"></a> <span data-ttu-id="f93dd-176">非 XML 格式化文件的示例</span><span class="sxs-lookup"><span data-stu-id="f93dd-176">Example of a Non-XML Format File</span></span>  
 <span data-ttu-id="f93dd-177">下面的示例显示了一个以前创建的非 XML 格式化文件 (`myDepartmentIdentical-f-c.fmt`)。</span><span class="sxs-lookup"><span data-stu-id="f93dd-177">The following example shows a previously created non-XML format file (`myDepartmentIdentical-f-c.fmt`).</span></span> <span data-ttu-id="f93dd-178">该文件描述了 `HumanResources.Department` 示例数据库中的 `AdventureWorks2012` 表中每一列的字符数据字段。</span><span class="sxs-lookup"><span data-stu-id="f93dd-178">This file describes a character-data field for every column in the `HumanResources.Department` table in the `AdventureWorks2012` sample database.</span></span>  
  
 <span data-ttu-id="f93dd-179">生成的格式化文件 `myDepartmentIdentical-f-c.fmt`包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="f93dd-179">The generated format file, `myDepartmentIdentical-f-c.fmt`, contains the following information:</span></span>  
  
```  
12.0  
4  
1       SQLCHAR       0       7       "\t"     1     DepartmentID     ""  
2       SQLCHAR       0       100     "\t"     2     Name             SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     "\t"     3     GroupName        SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       24      "\r\n"   4     ModifiedDate     ""  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f93dd-180">有关显示与该非 XML 格式化文件示例相关的格式化文件字段的说明，请参阅本主题前面的 [非 XML 格式化文件的结构](#Structure)。</span><span class="sxs-lookup"><span data-stu-id="f93dd-180">For an illustration that shows the format-file fields in relation to this sample non-XML format file, see [Structure of Non-XML Format Files](#Structure), earlier in this topic.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f93dd-181">相关任务</span><span class="sxs-lookup"><span data-stu-id="f93dd-181">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f93dd-182">创建格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f93dd-182">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="f93dd-183">使用格式化文件批量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f93dd-183">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="f93dd-184">使用格式化文件跳过表列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f93dd-184">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="f93dd-185">使用格式化文件跳过数据字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f93dd-185">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="f93dd-186">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f93dd-186">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="f93dd-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f93dd-187">See Also</span></span>  
 <span data-ttu-id="f93dd-188">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="f93dd-188">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="f93dd-189">[创建格式化文件 (SQL Server)](create-a-format-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f93dd-189">[Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md) </span></span>  
 <span data-ttu-id="f93dd-190">[XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f93dd-190">[XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="f93dd-191">用来导入或导出数据的格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f93dd-191">Format Files for Importing or Exporting Data &#40;SQL Server&#41;</span></span>](format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
