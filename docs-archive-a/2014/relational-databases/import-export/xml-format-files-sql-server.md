---
title: XML 格式化文件 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], XML format files
- bulk importing [SQL Server], format files
- XML format files [SQL Server]
ms.assetid: 69024aad-eeea-4187-8fea-b49bc2359849
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7cc1e8de30fa582898ef8516b9767dec14c4fa81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589575"
---
# <a name="xml-format-files-sql-server"></a><span data-ttu-id="2dbd4-102">XML 格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbd4-102">XML Format Files (SQL Server)</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="2dbd4-103">提供了一个 XML 架构，该架构定义了编写“XML 格式化文件”（用于将数据大容量导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中）的语法。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-103">provides an XML schema that defines syntax for writing *XML format files* to use for bulk importing data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="2dbd4-104">XML 格式化文件必须符合用 XML 架构定义语言 (XSDL) 定义的这种架构。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-104">XML format files must adhere to this schema, which is defined in the XML Schema Definition Language (XSDL).</span></span> <span data-ttu-id="2dbd4-105">只有当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工具和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 一起安装后，才支持 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-105">XML format files are only supported when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools are installed together with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="2dbd4-106">可以结合使用 XML 格式化文件和 **bcp** 命令、BULK INSERT 语句或 INSERT...SELECT \* FROM OPENROWSET(BULK...) 语句。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-106">You can use an XML format file with a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="2dbd4-107">使用 **bcp** 命令，你可以自动生成表的 XML 格式化文件；有关详细信息，请参阅 [bcp Utility](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-107">The **bcp** command allows you to automatically generate an XML format file for a table; for more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2dbd4-108">大容量导出和导入支持两种类型的格式化文件： *非 XML 格式化文件* 和 *XML 格式化文件*。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-108">Two types of format files are supported for bulk exporting and importing: *non-XML format files* and *XML format files*.</span></span> <span data-ttu-id="2dbd4-109">XML 格式化文件比非 XML 格式化文件更灵活，功能更强大。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-109">XML format files provide a flexible and powerful alternative to non-XML format files.</span></span> <span data-ttu-id="2dbd4-110">有关非 XML 格式化文件的信息，请参阅 [非 XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-110">For information about non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  

  
##  <a name="benefits-of-xml-format-files"></a><a name="BenefitsOfXmlFFs"></a> <span data-ttu-id="2dbd4-111">XML 格式化文件的优点</span><span class="sxs-lookup"><span data-stu-id="2dbd4-111">Benefits of XML Format Files</span></span>  
  
-   <span data-ttu-id="2dbd4-112">XML 格式化文件是自描述型，因此易于阅读、 创建和扩展。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-112">XML format files are self-describing, making them easy to read, create, and extend.</span></span> <span data-ttu-id="2dbd4-113">这些文件具有较强的可读性，这使您更容易理解在大容量操作过程中是如何解释数据的。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-113">They are human readable, making it easy to understand how data is interpreted during bulk operations.</span></span>  
  
-   <span data-ttu-id="2dbd4-114">XML 格式化文件包含目标列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-114">XML format files contain the data types of target columns.</span></span>  <span data-ttu-id="2dbd4-115">XML 编码清晰地描述了数据文件的数据类型和数据元素以及数据元素和表列之间的映射。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-115">The XML encoding clearly describes the data types and data elements of the data file and also the mapping between data elements and table columns.</span></span>  
  
     <span data-ttu-id="2dbd4-116">这可以将数据文件中数据的表示形式与文件中每个字段相关联的数据类型分离开来。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-116">This enables separation between how data is represented in the data file and what data type is associated with each field in the file.</span></span> <span data-ttu-id="2dbd4-117">例如，如果数据文件包含字符表示形式的数据，则相应的 SQL 列类型会丢失。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-117">For example, if a data file contains a character representation of the data, the corresponding SQL column type is lost.</span></span>  
  
-   <span data-ttu-id="2dbd4-118">XML 格式化文件允许从数据文件加载包含单一大型对象 (LOB) 数据类型的字段。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-118">An XML format file allows for loading of a field that contains a single large object (LOB) data type from a data file.</span></span>  
  
-   <span data-ttu-id="2dbd4-119">XML 格式化文件得以增强的同时，仍与早期版本保持兼容。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-119">An XML format file can be enhanced yet remain compatible with its earlier versions.</span></span> <span data-ttu-id="2dbd4-120">此外，XML 编码清晰，有利于为给定数据文件创建多个格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-120">Furthermore, the clarity of XML encoding facilitates the creation of multiple format files for a given data file.</span></span> <span data-ttu-id="2dbd4-121">这有助于将所有或某些数据字段映射到不同表或视图中的列。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-121">This is useful if you have to map all or some of the data fields to columns in different tables or views.</span></span>  
  
-   <span data-ttu-id="2dbd4-122">XML 语法与操作的方向无关；即大容量导出和大容量导入中使用的语法相同。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-122">The XML syntax is independent of the direction of the operation; that is, the syntax is the same for bulk export and bulk import.</span></span>  
  
-   <span data-ttu-id="2dbd4-123">使用 XML 格式化文件，可以将数据大容量导入表或非分区视图，并可以大容量导出数据。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-123">You can use XML format files to bulk import data into tables or non-partitioned views and to bulk export data.</span></span>  
  
-   <span data-ttu-id="2dbd4-124">对于 OPENROWSET(BULK...) 函数，指定目标表是可选的。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-124">For the OPENROWSET(BULK...) function specifying a target table is optional.</span></span> <span data-ttu-id="2dbd4-125">这是因为该函数依赖 XML 格式化文件从数据文件中读取数据。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-125">This is because the function relies on the XML format file to read data from a data file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2dbd4-126">**bcp** 命令和 BULK INSERT 语句需要使用目标表，因为它们使用目标表列执行类型转换。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-126">A target table is necessary with the **bcp** command and the BULK INSERT statement, which uses the target table columns to do the type conversion.</span></span>  
  
##  <a name="structure-of-xml-format-files"></a><a name="StructureOfXmlFFs"></a> <span data-ttu-id="2dbd4-127">XML 格式化文件的结构</span><span class="sxs-lookup"><span data-stu-id="2dbd4-127">Structure of XML Format Files</span></span>  
 <span data-ttu-id="2dbd4-128">和非 XML 格式化文件一样，XML 格式化文件定义数据文件中数据字段的格式和结构，并将这些数据字段映射到单个目标表中的相应列。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-128">Like a non-XML format file, an XML format file defines the format and structure of the data fields in a data file and maps those data fields to columns in a single target table.</span></span>  
  
 <span data-ttu-id="2dbd4-129">XML 格式化文件有两个主要组件，即 \<RECORD> 和 \<ROW>：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-129">An XML format file possesses two main components, \<RECORD> and \<ROW>:</span></span>  
  
-   <span data-ttu-id="2dbd4-130">\<RECORD> 说明数据文件中存储的数据。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-130">\<RECORD> describes the data as it is stored in the data file.</span></span>  
  
     <span data-ttu-id="2dbd4-131">每个 \<RECORD> 元素包含一个或多个 \<FIELD> 元素。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-131">Each \<RECORD> element contains a set of one or more \<FIELD> elements.</span></span> <span data-ttu-id="2dbd4-132">这些元素与数据文件中的字段相对应。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-132">These elements correspond to fields in the data file.</span></span> <span data-ttu-id="2dbd4-133">基本语法如下：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-133">The basic syntax is as follows:</span></span>  
  
     \<RECORD>  
  
     <span data-ttu-id="2dbd4-134">\<FIELD .../> [ ...n ]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-134">\<FIELD .../> [ ...*n* ]</span></span>  
  
     \</RECORD>  
  
     <span data-ttu-id="2dbd4-135">每个 \<FIELD> 元素说明特定数据字段的内容。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-135">Each \<FIELD> element describes the contents of a specific data field.</span></span> <span data-ttu-id="2dbd4-136">一个字段只能映射到表中的一列，</span><span class="sxs-lookup"><span data-stu-id="2dbd4-136">A field can only be mapped to one column in the table.</span></span> <span data-ttu-id="2dbd4-137">并不是所有字段都需要映射到列。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-137">Not all fields need to be mapped to columns.</span></span>  
  
     <span data-ttu-id="2dbd4-138">数据文件中字段的长度可以是固定或可变的，也可以由字符结尾。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-138">A field in a data file can be either of fixed/variable length or character terminated.</span></span> <span data-ttu-id="2dbd4-139">*字段值* 可以表示为字符（使用单字节表示形式）、宽字符（使用 Unicode 双字节表示形式）、本机数据库格式或文件名。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-139">A *field value* can be represented as: a character (using single-byte representation), a wide character (using Unicode two-byte representation), native database format, or a file name.</span></span> <span data-ttu-id="2dbd4-140">如果字段值为文件名，则文件名指向包含目标表中 BLOB 列的值的文件。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-140">If a field value is represented as a file name, the file name points to the file that contains the value of a BLOB column in the target table.</span></span>  
  
-   <span data-ttu-id="2dbd4-141">\<ROW> 说明在将数据从文件导入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中时，如何构造数据文件中的数据行。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-141">\<ROW> describes how to construct data rows from a data file when the data from the file is imported into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
     <span data-ttu-id="2dbd4-142">\<ROW> 元素包含一组 \<COLUMN> 元素。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-142">A \<ROW> element contains a set of \<COLUMN> elements.</span></span> <span data-ttu-id="2dbd4-143">这些元素与表列相对应。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-143">These elements correspond to table columns.</span></span> <span data-ttu-id="2dbd4-144">基本语法如下：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-144">The basic syntax is as follows:</span></span>  
  
     \<ROW>  
  
     <span data-ttu-id="2dbd4-145">\<COLUMN .../> [ ...n ]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-145">\<COLUMN .../> [ ...*n* ]</span></span>  
  
     \</ROW>  
  
     <span data-ttu-id="2dbd4-146">每个 \<COLUMN> 元素均只能映射到数据文件中的一个字段。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-146">Each \<COLUMN> element can be mapped to only one field in the data file.</span></span> <span data-ttu-id="2dbd4-147">\<ROW> 元素中 \<COLUMN> 元素的顺序定义了其在批量操作中返回的顺序。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-147">The order of the \<COLUMN> elements in the \<ROW> element defines the order in which they are returned by the bulk operation.</span></span> <span data-ttu-id="2dbd4-148">XML 格式化文件为每个 \<COLUMN> 元素分配了一个本地名称，该名称与批量导入操作的目标表中的列没有关系。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-148">The XML format file assigns each \<COLUMN> element a local name that has no relationship to the column in the target table of a bulk import operation.</span></span>  
  
##  <a name="schema-syntax-for-xml-format-files"></a><a name="SchemaSyntax"></a> <span data-ttu-id="2dbd4-149">XML 格式化文件的架构语法</span><span class="sxs-lookup"><span data-stu-id="2dbd4-149">Schema Syntax for XML Format Files</span></span>  
 <span data-ttu-id="2dbd4-150">本节概要介绍 XML 格式化文件的 XML 架构的元素和属性。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-150">This section contains a summary of the elements and attributes of the XML schema for XML format files.</span></span> <span data-ttu-id="2dbd4-151">格式化文件的语法与操作的方向无关；即大容量导出和大容量导入中使用的语法相同。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-151">The syntax of a format file is independent of the direction of the operation; that is, the syntax is the same for bulk export and bulk import.</span></span> <span data-ttu-id="2dbd4-152">本部分还介绍批量导入如何使用 \<ROW> 和 \<COLUMN> 元素以及如何将元素的 xsi:type 值放入数据集。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-152">This section also considers how bulk import uses the \<ROW> and \<COLUMN> elements and how to put the xsi:type value of an element into a data set.</span></span>  
  
 <span data-ttu-id="2dbd4-153">若要查看该语法与实际的 XML 格式化文件的对应关系，请参阅本主题后面的 [XML 格式化文件示例](#SampleXmlFFs)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-153">To see how the syntax corresponds to actual XML format files, see [Sample XML Format Files](#SampleXmlFFs), later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2dbd4-154">您可以修改格式化文件，以便从字段编号和/或顺序与表列的编号和/或顺序不同的数据文件进行大容量导入。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-154">You can modify a format file to let you bulk import from a data file in which the number and/or order of the fields differ from the number and/or order of table columns.</span></span> <span data-ttu-id="2dbd4-155">有关详细信息，请参阅 [用来导入或导出数据的格式化文件 (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-155">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
  
  
###  <a name="basic-syntax-of-the-xml-schema"></a><a name="BasicSyntax"></a> <span data-ttu-id="2dbd4-156">XML 架构的基本语法</span><span class="sxs-lookup"><span data-stu-id="2dbd4-156">Basic Syntax of the XML Schema</span></span>  
 <span data-ttu-id="2dbd4-157">此语法语句仅显示元素（\<BCPFORMAT>、\<RECORD>、\<FIELD>、\<ROW> 和 \<COLUMN>）及其基本属性。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-157">This syntax statements show only the elements (\<BCPFORMAT>, \<RECORD>, \<FIELD>, \<ROW>, and \<COLUMN>) and their basic attributes.</span></span>  
  
 \<BCPFORMAT ...>  
  
 \<RECORD>  
  
 <span data-ttu-id="2dbd4-158">\<FIELD ID = "*fieldID*" xsi:type = "*fieldType*" [...]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-158">\<FIELD ID = "*fieldID*" xsi:type = "*fieldType*" [...]</span></span>  
  
 />  
  
 \</RECORD>  
  
 \<ROW>  
  
 <span data-ttu-id="2dbd4-159">\<COLUMN SOURCE = "*fieldID*" NAME = "*columnName*" xsi:type = "*columnType*" [...]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-159">\<COLUMN SOURCE = "*fieldID*" NAME = "*columnName*" xsi:type = "*columnType*" [...]</span></span>  
  
 />  
  
 \</ROW>  
  
 \</BCPFORMAT>  
  
> [!NOTE]  
>  <span data-ttu-id="2dbd4-160">对于其他与 \<FIELD> 或 \<COLUMN> 元素中的 xsi:type 值相关的属性，将在本主题后面部分予以介绍。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-160">Additional attributes that are associated with the value of the xsi:type in a \<FIELD> or \<COLUMN> element are described later in this topic.</span></span>  
  

  
####  <a name="schema-elements"></a><a name="SchemaElements"></a> <span data-ttu-id="2dbd4-161">架构元素</span><span class="sxs-lookup"><span data-stu-id="2dbd4-161">Schema Elements</span></span>  
 <span data-ttu-id="2dbd4-162">本节总结了 XML 架构为 XML 格式化文件定义的每个元素的作用。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-162">This section summarizes the purpose of each element that the XML schema defines for XML format files.</span></span> <span data-ttu-id="2dbd4-163">本主题在后面有单独的章节介绍这些属性。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-163">The attributes are described in separate sections later in this topic.</span></span>  
  
 \<BCPFORMAT>  
 <span data-ttu-id="2dbd4-164">即格式化文件元素。它定义给定数据文件的记录结构及其与表中某行的各列的对应关系。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-164">Is the format-file element that defines the record structure of a given data file and its correspondence to the columns of a table row in the table.</span></span>  
  
 \<RECORD .../>  
 <span data-ttu-id="2dbd4-165">定义包含一个或多个 \<FIELD> 元素的复杂元素。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-165">Defines a complex element containing one or more \<FIELD> elements.</span></span> <span data-ttu-id="2dbd4-166">在格式化文件中声明的字段的顺序与那些字段在数据文件中出现的顺序相同。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-166">The order in which the fields are declared in the format file is the order in which those fields appear in the data file.</span></span>  
  
 \<FIELD .../>  
 <span data-ttu-id="2dbd4-167">定义数据文件中的字段，用来容纳数据。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-167">Defines a field in data file, which contains data.</span></span>  
  
 <span data-ttu-id="2dbd4-168">本主题将在后面的 [\<FIELD> 元素的属性](#AttrOfFieldElement)中讨论此元素的属性。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-168">The attributes of this element are discussed in [Attributes of the \<FIELD> Element](#AttrOfFieldElement), later in this topic.</span></span>  
  
 \<ROW .../>  
 <span data-ttu-id="2dbd4-169">定义包含一个或多个 \<COLUMN> 元素的复杂元素。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-169">Defines a complex element containing one or more \<COLUMN> elements.</span></span> <span data-ttu-id="2dbd4-170">\<COLUMN> 元素的顺序与 RECORD 定义中 \<FIELD> 元素的顺序无关。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-170">The order of the \<COLUMN> elements is independent of the order of \<FIELD> elements in a RECORD definition.</span></span> <span data-ttu-id="2dbd4-171">但是，\<COLUMN> 元素在格式化文件中的顺序决定了所生成行集的列的顺序。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-171">Rather, the order of the \<COLUMN> elements in a format file determines the column order of the resultant rowset.</span></span> <span data-ttu-id="2dbd4-172">数据字段的加载将按照相应的 \<COLUMN> 元素在 \<COLUMN> 元素中的声明顺序进行。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-172">Data fields are loaded in the order in which the corresponding \<COLUMN> elements are declared in the \<COLUMN> element.</span></span>  
  
 <span data-ttu-id="2dbd4-173">有关详细信息，请参阅本主题后面的[批量导入如何使用 \<ROW> 元素](#HowUsesROW)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-173">For more information, see [How Bulk Import Uses the \<ROW> Element](#HowUsesROW), later in this topic.</span></span>  
  
 \<COLUMN>  
 <span data-ttu-id="2dbd4-174">将列定义为元素 (\<COLUMN>)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-174">Defines a column as an element (\<COLUMN>).</span></span> <span data-ttu-id="2dbd4-175">每个 \<COLUMN> 元素对应一个 \<FIELD> 元素（其 ID 在 \<COLUMN> 元素的 SOURCE 属性中指定）。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-175">Each \<COLUMN> element corresponds to a \<FIELD> element (whose ID is specified in the SOURCE attribute of the \<COLUMN> element).</span></span>  
  
 <span data-ttu-id="2dbd4-176">本主题将在后面的 [\<COLUMN> 元素的属性](#AttrOfColumnElement)中讨论此元素的属性。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-176">The attributes of this element are discussed in [Attributes of the \<COLUMN> Element](#AttrOfColumnElement), later in this topic.</span></span> <span data-ttu-id="2dbd4-177">另请参阅本主题后面的[批量导入如何使用 \<COLUMN> 元素](#HowUsesColumn)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-177">Also see, [How Bulk Import Uses the \<COLUMN> Element](#HowUsesColumn), later in this topic.</span></span>  
  
 \</BCPFORMAT>  
 <span data-ttu-id="2dbd4-178">用于结束格式化文件。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-178">Required to end the format file.</span></span>  
  
####  <a name="attributes-of-the-field-element"></a><a name="AttrOfFieldElement"></a><span data-ttu-id="2dbd4-179">\<FIELD> 元素的属性</span><span class="sxs-lookup"><span data-stu-id="2dbd4-179">Attributes of the \<FIELD> Element</span></span>  
 <span data-ttu-id="2dbd4-180">本部分介绍 \<FIELD> 元素的属性，现将其架构语法总结如下：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-180">This section describes the attributes of the \<FIELD> element, which are summarized in the following schema syntax:</span></span>  
  
 <span data-ttu-id="2dbd4-181"><FIELD</span><span class="sxs-lookup"><span data-stu-id="2dbd4-181"><FIELD</span></span>  
  
 <span data-ttu-id="2dbd4-182">ID **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-182">ID **="*`fieldID`*"**</span></span>  
  
 <span data-ttu-id="2dbd4-183">xsi **：** type **= " *`fieldType`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-183">xsi **:** type **="*`fieldType`*"**</span></span>  
  
 <span data-ttu-id="2dbd4-184">[ LENGTH **="*`n`*"** ]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-184">[ LENGTH **="*`n`*"** ]</span></span>  
  
 <span data-ttu-id="2dbd4-185">[PREFIX_LENGTH **= " *`p`* "** ]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-185">[ PREFIX_LENGTH **="*`p`*"** ]</span></span>  
  
 <span data-ttu-id="2dbd4-186">[MAX_LENGTH **= " *`m`* "** ]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-186">[ MAX_LENGTH **="*`m`*"** ]</span></span>  
  
 <span data-ttu-id="2dbd4-187">[排序规则 **= " *`collationName`* "** ]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-187">[ COLLATION **="*`collationName`*"** ]</span></span>  
  
 <span data-ttu-id="2dbd4-188">[终止符 **= " *`terminator`* "** ]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-188">[ TERMINATOR **="*`terminator`*"** ]</span></span>  
  
 />  
  
 <span data-ttu-id="2dbd4-189">每个 \<FIELD> 元素都与其他元素无关。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-189">Each \<FIELD> element is independent of the others.</span></span> <span data-ttu-id="2dbd4-190">字段是通过下列属性进行描述的：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-190">A field is described in terms of the following attributes:</span></span>  
  
|<span data-ttu-id="2dbd4-191">FIELD 属性</span><span class="sxs-lookup"><span data-stu-id="2dbd4-191">FIELD Attribute</span></span>|<span data-ttu-id="2dbd4-192">说明</span><span class="sxs-lookup"><span data-stu-id="2dbd4-192">Description</span></span>|<span data-ttu-id="2dbd4-193">可选/</span><span class="sxs-lookup"><span data-stu-id="2dbd4-193">Optional /</span></span><br /><br /> <span data-ttu-id="2dbd4-194">必选</span><span class="sxs-lookup"><span data-stu-id="2dbd4-194">Required</span></span>|  
|---------------------|-----------------|------------------------------|  
|<span data-ttu-id="2dbd4-195">ID **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-195">ID **="*`fieldID`*"**</span></span>|<span data-ttu-id="2dbd4-196">指定数据文件中的字段的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-196">Specifies the logical name of the field in the data file.</span></span> <span data-ttu-id="2dbd4-197">字段的 ID 是用于引用字段的键。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-197">The ID of a field is the key used to refer to the field.</span></span><br /><br /> <span data-ttu-id="2dbd4-198"><字段 ID **= " *`fieldID`* "**/> 映射到 <列源 **= " *`fieldID`* "**/></span><span class="sxs-lookup"><span data-stu-id="2dbd4-198"><FIELD ID **="*`fieldID`*"**/> maps to <COLUMN SOURCE **="*`fieldID`*"**/></span></span>|<span data-ttu-id="2dbd4-199">必选</span><span class="sxs-lookup"><span data-stu-id="2dbd4-199">Required</span></span>|  
|<span data-ttu-id="2dbd4-200">xsi： type **= " *`fieldType`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-200">xsi:type **="*`fieldType`*"**</span></span>|<span data-ttu-id="2dbd4-201">这是一个 XML 构造，用法类似于属性。它定义元素实例的类型。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-201">This is an XML construct (used like an attribute) that identifies the type of the instance of the element.</span></span> <span data-ttu-id="2dbd4-202">*fieldType* 的值决定了给定实例中需要下面哪个可选属性。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-202">The value of *fieldType* determines which of the optional attributes (below) you need in a given instance.</span></span>|<span data-ttu-id="2dbd4-203">必需（取决于数据类型）</span><span class="sxs-lookup"><span data-stu-id="2dbd4-203">Required (depending on the data type)</span></span>|  
|<span data-ttu-id="2dbd4-204">LENGTH **= " *`n`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-204">LENGTH **="*`n`*"**</span></span>|<span data-ttu-id="2dbd4-205">此属性定义固定长度的数据类型实例的长度。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-205">This attribute defines the length for an instance of a fixed-length data type.</span></span><br /><br /> <span data-ttu-id="2dbd4-206">*n* 值必须是正整数。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-206">The value of *n* must be a positive integer.</span></span>|<span data-ttu-id="2dbd4-207">除非是 xsi:type 值所必需，否则可选。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-207">Optional unless required by the xsi:type value</span></span>|  
|<span data-ttu-id="2dbd4-208">PREFIX_LENGTH **= " *`p`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-208">PREFIX_LENGTH **="*`p`*"**</span></span>|<span data-ttu-id="2dbd4-209">此属性定义二进制数据表示形式的前缀的长度。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-209">This attribute defines the prefix length for a binary data representation.</span></span> <span data-ttu-id="2dbd4-210">PREFIX_LENGTH 值 p 必须是下列值之一：1、2、4 或 8。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-210">The PREFIX_LENGTH value, *p*, must be one of the following: 1, 2, 4, or 8.</span></span>|<span data-ttu-id="2dbd4-211">除非是 xsi:type 值所必需，否则可选。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-211">Optional unless required by the xsi:type value</span></span>|  
|<span data-ttu-id="2dbd4-212">MAX_LENGTH **= " *`m`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-212">MAX_LENGTH **="*`m`*"**</span></span>|<span data-ttu-id="2dbd4-213">此属性为给定字段中可以存储的最大字节数。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-213">This attribute is the maximum number of bytes that can be stored in a given field.</span></span> <span data-ttu-id="2dbd4-214">如果没有目标表，列的最大长度就是未知的。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-214">Without a target table, the column max-length is not known.</span></span> <span data-ttu-id="2dbd4-215">MAX_LENGTH 属性限定输出字符列的最大长度，从而限制为列值分配的存储空间。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-215">The MAX_LENGTH attribute restricts the maximum length of an output character column, limiting the storage allocated for the column value.</span></span> <span data-ttu-id="2dbd4-216">当在 SELECT FROM 子句中使用了 OPENROWSET 函数的 BULK 选项时，使用该属性将带来极大的方便。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-216">This is especially convenient when using the OPENROWSET function's BULK option in a SELECT FROM clause.</span></span><br /><br /> <span data-ttu-id="2dbd4-217">*m* 值必须是正整数。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-217">The value of *m* must be a positive integer.</span></span> <span data-ttu-id="2dbd4-218">默认情况下， **char** 列的最大长度为 8000 个字符， **nchar** 列的最大长度为 4000 个字符。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-218">By default, the maximum length is 8000 characters for a **char** column and 4000 characters for an **nchar** column.</span></span>|<span data-ttu-id="2dbd4-219">可选</span><span class="sxs-lookup"><span data-stu-id="2dbd4-219">Optional</span></span>|  
|<span data-ttu-id="2dbd4-220">排序规则 **= " *`collationName`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-220">COLLATION **="*`collationName`*"**</span></span>|<span data-ttu-id="2dbd4-221">COLLATION 仅适用于字符字段。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-221">COLLATION is only allowed for character fields.</span></span> <span data-ttu-id="2dbd4-222">有关 SQL 排序规则名称的列表，请参阅 [SQL Server 排序规则名称 (Transact SQL)](/sql/t-sql/statements/sql-server-collation-name-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-222">For a list of the SQL collation names, see [SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql).</span></span>|<span data-ttu-id="2dbd4-223">可选</span><span class="sxs-lookup"><span data-stu-id="2dbd4-223">Optional</span></span>|  
|<span data-ttu-id="2dbd4-224">终止符 **= " *`terminator`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-224">TERMINATOR **= "*`terminator`*"**</span></span>|<span data-ttu-id="2dbd4-225">此属性指定数据字段的终止符。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-225">This attribute specifies the terminator of a data field.</span></span> <span data-ttu-id="2dbd4-226">该终止符可以是任意字符。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-226">The terminator can be any character.</span></span> <span data-ttu-id="2dbd4-227">该字符必须是数据中没有的唯一字符。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-227">The terminator must be a unique character that is not part of the data.</span></span><br /><br /> <span data-ttu-id="2dbd4-228">默认情况下，该字段的终止符为制表符（用 \t 表示）。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-228">By default, the field terminator is the tab character (represented as \t).</span></span> <span data-ttu-id="2dbd4-229">若要表示段落标记，请使用 \r\n。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-229">To represent a paragraph mark, use \r\n.</span></span>|<span data-ttu-id="2dbd4-230">仅和需要该属性的字符数据 xsi:type 一起使用。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-230">Used only with an xsi:type of character data, which requires this attribute</span></span>|  
  
#####  <a name="xsitype-values-of-the-field-element"></a><a name="XsiTypeValuesOfFIELD"></a><span data-ttu-id="2dbd4-231">\<FIELD> 元素的 xsi:type 值</span><span class="sxs-lookup"><span data-stu-id="2dbd4-231">Xsi:type values of the \<FIELD> Element</span></span>  
 <span data-ttu-id="2dbd4-232">xsi:type 值是标识元素实例的数据类型的 XML 构造（用法同属性）。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-232">The xsi:type value is an XML construct (used like an attribute) that identifies the data type of an instance of an element.</span></span> <span data-ttu-id="2dbd4-233">本节后面将介绍有关“在数据集中包含 xsi:type 值”的信息。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-233">For information on using the "Putting the xsi:type Value into a Data Set," later in this section.</span></span>  
  
 <span data-ttu-id="2dbd4-234">\<FIELD> 元素的 xsi:type 值支持下列数据类型。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-234">The xsi:type value of the \<FIELD> element supports the following data types.</span></span>  
  
|<span data-ttu-id="2dbd4-235">\<FIELD> xsi:type 值</span><span class="sxs-lookup"><span data-stu-id="2dbd4-235">\<FIELD> xsi:type values</span></span>|<span data-ttu-id="2dbd4-236">数据类型</span><span class="sxs-lookup"><span data-stu-id="2dbd4-236">Required XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="2dbd4-237">的可选 XML 属性</span><span class="sxs-lookup"><span data-stu-id="2dbd4-237">for Data Type</span></span>|<span data-ttu-id="2dbd4-238">数据类型</span><span class="sxs-lookup"><span data-stu-id="2dbd4-238">Optional XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="2dbd4-239">的可选 XML 属性</span><span class="sxs-lookup"><span data-stu-id="2dbd4-239">for Data Type</span></span>|  
|-------------------------------|---------------------------------------------------|---------------------------------------------------|  
|<span data-ttu-id="2dbd4-240">**NativeFixed**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-240">**NativeFixed**</span></span>|`LENGTH`|<span data-ttu-id="2dbd4-241">无。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-241">None.</span></span>|  
|<span data-ttu-id="2dbd4-242">**NativePrefix**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-242">**NativePrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="2dbd4-243">MAX_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2dbd4-243">MAX_LENGTH</span></span>|  
|<span data-ttu-id="2dbd4-244">**CharFixed**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-244">**CharFixed**</span></span>|`LENGTH`|<span data-ttu-id="2dbd4-245">COLLATION</span><span class="sxs-lookup"><span data-stu-id="2dbd4-245">COLLATION</span></span>|  
|<span data-ttu-id="2dbd4-246">**NCharFixed**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-246">**NCharFixed**</span></span>|`LENGTH`|<span data-ttu-id="2dbd4-247">COLLATION</span><span class="sxs-lookup"><span data-stu-id="2dbd4-247">COLLATION</span></span>|  
|<span data-ttu-id="2dbd4-248">**CharPrefix**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-248">**CharPrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="2dbd4-249">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="2dbd4-249">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="2dbd4-250">**NCharPrefix**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-250">**NCharPrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="2dbd4-251">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="2dbd4-251">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="2dbd4-252">**CharTerm**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-252">**CharTerm**</span></span>|`TERMINATOR`|<span data-ttu-id="2dbd4-253">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="2dbd4-253">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="2dbd4-254">**NCharTerm**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-254">**NCharTerm**</span></span>|`TERMINATOR`|<span data-ttu-id="2dbd4-255">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="2dbd4-255">MAX_LENGTH, COLLATION</span></span>|  
  
 <span data-ttu-id="2dbd4-256">有关 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型的详细信息，请参阅[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-256">For more information about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
####  <a name="attributes-of-the-column-element"></a><a name="AttrOfColumnElement"></a><span data-ttu-id="2dbd4-257">\<COLUMN> 元素的属性</span><span class="sxs-lookup"><span data-stu-id="2dbd4-257">Attributes of the \<COLUMN> Element</span></span>  
 <span data-ttu-id="2dbd4-258">本部分介绍 \<COLUMN> 元素的属性，现将其架构语法总结如下：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-258">This section describes the attributes of the \<COLUMN> element, which are summarized in the following schema syntax:</span></span>  
  
 <span data-ttu-id="2dbd4-259">\<元素表列出了</span><span class="sxs-lookup"><span data-stu-id="2dbd4-259">\<COLUMN</span></span>  
  
 <span data-ttu-id="2dbd4-260">SOURCE = "*fieldID*"</span><span class="sxs-lookup"><span data-stu-id="2dbd4-260">SOURCE = "*fieldID*"</span></span>  
  
 <span data-ttu-id="2dbd4-261">NAME = "*columnName*"</span><span class="sxs-lookup"><span data-stu-id="2dbd4-261">NAME = "*columnName*"</span></span>  
  
 <span data-ttu-id="2dbd4-262">xsi:type = "*columnType*"</span><span class="sxs-lookup"><span data-stu-id="2dbd4-262">xsi:type = "*columnType*"</span></span>  
  
 <span data-ttu-id="2dbd4-263">[ LENGTH = "*n*" ]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-263">[ LENGTH = "*n*" ]</span></span>  
  
 <span data-ttu-id="2dbd4-264">[ PRECISION = "*n*" ]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-264">[ PRECISION = "*n*" ]</span></span>  
  
 <span data-ttu-id="2dbd4-265">[ SCALE = "*value*" ]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-265">[ SCALE = "*value*" ]</span></span>  
  
 <span data-ttu-id="2dbd4-266">[ NULLABLE = { "YES"</span><span class="sxs-lookup"><span data-stu-id="2dbd4-266">[ NULLABLE = { "YES"</span></span>  
  
 <span data-ttu-id="2dbd4-267">"NO" } ]</span><span class="sxs-lookup"><span data-stu-id="2dbd4-267">"NO" } ]</span></span>  
  
 />  
  
 <span data-ttu-id="2dbd4-268">使用下列属性将字段映射到目标表中的列：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-268">A field is mapped to a column in the target table using the following attributes:</span></span>  
  
|<span data-ttu-id="2dbd4-269">COLUMN 属性</span><span class="sxs-lookup"><span data-stu-id="2dbd4-269">COLUMN Attribute</span></span>|<span data-ttu-id="2dbd4-270">说明</span><span class="sxs-lookup"><span data-stu-id="2dbd4-270">Description</span></span>|<span data-ttu-id="2dbd4-271">可选/</span><span class="sxs-lookup"><span data-stu-id="2dbd4-271">Optional /</span></span><br /><br /> <span data-ttu-id="2dbd4-272">必选</span><span class="sxs-lookup"><span data-stu-id="2dbd4-272">Required</span></span>|  
|----------------------|-----------------|------------------------------|  
|<span data-ttu-id="2dbd4-273">SOURCE **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-273">SOURCE **="*`fieldID`*"**</span></span>|<span data-ttu-id="2dbd4-274">指定映射到列的字段 ID。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-274">Specifies the ID of the field being mapped to the column.</span></span><br /><br /> <span data-ttu-id="2dbd4-275"><列源 **= " *`fieldID`* "**/> 映射到 <字段 ID **= " *`fieldID`* "**/></span><span class="sxs-lookup"><span data-stu-id="2dbd4-275"><COLUMN SOURCE **="*`fieldID`*"**/> maps to <FIELD ID **="*`fieldID`*"**/></span></span>|<span data-ttu-id="2dbd4-276">必选</span><span class="sxs-lookup"><span data-stu-id="2dbd4-276">Required</span></span>|  
|<span data-ttu-id="2dbd4-277">NAME = "*columnName*"</span><span class="sxs-lookup"><span data-stu-id="2dbd4-277">NAME = "*columnName*"</span></span>|<span data-ttu-id="2dbd4-278">指定格式化文件所表示的行集中的列名。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-278">Specifies the name of the column in the row set represented by the format file.</span></span> <span data-ttu-id="2dbd4-279">此列名用于标识结果集中的列，并且该列不需要与目标表中使用的列名相对应。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-279">This column name is used to identify the column in the result set, and it need not correspond to the column name used in the target table.</span></span>|<span data-ttu-id="2dbd4-280">必选</span><span class="sxs-lookup"><span data-stu-id="2dbd4-280">Required</span></span>|  
|<span data-ttu-id="2dbd4-281">xsi **：** type **= " *`ColumnType`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-281">xsi **:** type **="*`ColumnType`*"**</span></span>|<span data-ttu-id="2dbd4-282">这是一个 XML 构造，用法类似于属性。它定义元素实例的数据类型。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-282">This is an XML construct (used like an attribute) that identifies the data type of the instance of the element.</span></span> <span data-ttu-id="2dbd4-283">*ColumnType* 的值决定了给定实例中需要下面哪个可选属性。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-283">The value of *ColumnType* determines which of the optional attributes (below) you need in a given instance.</span></span><br /><br /> <span data-ttu-id="2dbd4-284">注意：下表列出了*ColumnType*的可能值及其相关属性。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-284">Note: The possible values of *ColumnType* and their associated attributes are listed in the next table.</span></span>|<span data-ttu-id="2dbd4-285">可选</span><span class="sxs-lookup"><span data-stu-id="2dbd4-285">Optional</span></span>|  
|<span data-ttu-id="2dbd4-286">LENGTH **= " *`n`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-286">LENGTH **="*`n`*"**</span></span>|<span data-ttu-id="2dbd4-287">定义固定长度的数据类型实例的长度。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-287">Defines the length for an instance of a fixed-length data type.</span></span> <span data-ttu-id="2dbd4-288">仅当 xsi:type 为字符串数据类型时，才使用 LENGTH。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-288">LENGTH is used only when the xsi:type is a string data type.</span></span><br /><br /> <span data-ttu-id="2dbd4-289">*n* 值必须是正整数。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-289">The value of *n* must be a positive integer.</span></span>|<span data-ttu-id="2dbd4-290">可选（仅当 xsi:type 是字符串数据类型时才可用）</span><span class="sxs-lookup"><span data-stu-id="2dbd4-290">Optional (available only if the xsi:type is a string data type)</span></span>|  
|<span data-ttu-id="2dbd4-291">PRECISION **="*`n`*"**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-291">PRECISION **="*`n`*"**</span></span>|<span data-ttu-id="2dbd4-292">指示数字的位数。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-292">Indicates the number of digits in a number.</span></span> <span data-ttu-id="2dbd4-293">例如，数 123.45 精度为 5。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-293">For example, the number 123.45 has a precision of 5.</span></span><br /><br /> <span data-ttu-id="2dbd4-294">该值必须是正整数。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-294">The value must be a positive integer.</span></span>|<span data-ttu-id="2dbd4-295">可选（仅在 xsi:type 是变量数字数据类型时才可用）</span><span class="sxs-lookup"><span data-stu-id="2dbd4-295">Optional (available only if the xsi:type is a variable-number data type)</span></span>|  
|<span data-ttu-id="2dbd4-296">SCALE **= " *`int`* "**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-296">SCALE **="*`int`*"**</span></span>|<span data-ttu-id="2dbd4-297">指示数字中小数点右边的位数。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-297">Indicates the number of digits to the right of the decimal point in a number.</span></span> <span data-ttu-id="2dbd4-298">例如，数字 123.45 的小数位数为 2。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-298">For example, the number 123.45 has a scale of 2.</span></span><br /><br /> <span data-ttu-id="2dbd4-299">该值必须为整数。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-299">The value must be an integer.</span></span>|<span data-ttu-id="2dbd4-300">可选（仅在 xsi:type 是变量数字数据类型时才可用）</span><span class="sxs-lookup"><span data-stu-id="2dbd4-300">Optional (available only if the xsi:type is a variable-number data type)</span></span>|  
|<span data-ttu-id="2dbd4-301">NULLABLE **=** { **"** YES **"**</span><span class="sxs-lookup"><span data-stu-id="2dbd4-301">NULLABLE **=** { **"** YES **"**</span></span><br /><br /> <span data-ttu-id="2dbd4-302">**"** NO **"** }</span><span class="sxs-lookup"><span data-stu-id="2dbd4-302">**"** NO **"** }</span></span>|<span data-ttu-id="2dbd4-303">指示列是否可以接受 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-303">Indicates whether a column can assume NULL values.</span></span> <span data-ttu-id="2dbd4-304">此属性与 FIELDS 完全无关。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-304">This attribute is completely independent of FIELDS.</span></span> <span data-ttu-id="2dbd4-305">但是，如果列不可为空值，而字段指定为 NULL（未指定任何值），将产生运行时错误。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-305">However, if a column is not NULLABLE and field specifies NULL (by not specifying any value), a run-time error results.</span></span><br /><br /> <span data-ttu-id="2dbd4-306">NULLABLE 属性仅在您只执行普通 SELECT FROM OPENROWSET(BULK...) 语句时才使用。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-306">The NULLABLE attribute is used only if you do a plain SELECT FROM OPENROWSET(BULK...) statement.</span></span>|<span data-ttu-id="2dbd4-307">可选（任何数据类型均可用）</span><span class="sxs-lookup"><span data-stu-id="2dbd4-307">Optional (available for any data type)</span></span>|  
  
#####  <a name="xsitype-values-of-the-column-element"></a><a name="XsiTypeValuesOfCOLUMN"></a><span data-ttu-id="2dbd4-308">\<COLUMN> 元素的 xsi:type 值</span><span class="sxs-lookup"><span data-stu-id="2dbd4-308">Xsi:type values of the \<COLUMN> Element</span></span>  
 <span data-ttu-id="2dbd4-309">xsi:type 值是标识元素实例的数据类型的 XML 构造（用法同属性）。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-309">The xsi:type value is an XML construct (used like an attribute) that identifies the data type of an instance of an element.</span></span> <span data-ttu-id="2dbd4-310">本节后面将介绍有关“在数据集中包含 xsi:type 值”的信息。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-310">For information on using the "Putting the xsi:type Value into a Data Set," later in this section.</span></span>  
  
 <span data-ttu-id="2dbd4-311">\<COLUMN> 元素支持下列本机 SQL 数据类型：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-311">The \<COLUMN> element supports native SQL data types, as follows:</span></span>  
  
|<span data-ttu-id="2dbd4-312">类型类别</span><span class="sxs-lookup"><span data-stu-id="2dbd4-312">Type Category</span></span>|<span data-ttu-id="2dbd4-313">\<COLUMN> 数据类型</span><span class="sxs-lookup"><span data-stu-id="2dbd4-313">\<COLUMN> Data Types</span></span>|<span data-ttu-id="2dbd4-314">数据类型</span><span class="sxs-lookup"><span data-stu-id="2dbd4-314">Required XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="2dbd4-315">的可选 XML 属性</span><span class="sxs-lookup"><span data-stu-id="2dbd4-315">for Data Type</span></span>|<span data-ttu-id="2dbd4-316">数据类型</span><span class="sxs-lookup"><span data-stu-id="2dbd4-316">Optional XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="2dbd4-317">的可选 XML 属性</span><span class="sxs-lookup"><span data-stu-id="2dbd4-317">for Data Type</span></span>|  
|-------------------|---------------------------|---------------------------------------------------|---------------------------------------------------|  
|<span data-ttu-id="2dbd4-318">已修复</span><span class="sxs-lookup"><span data-stu-id="2dbd4-318">Fixed</span></span>|<span data-ttu-id="2dbd4-319">`SQLBIT`、`SQLTINYINT`、`SQLSMALLINT`、`SQLINT`、`SQLBIGINT`、`SQLFLT4`、`SQLFLT8`、`SQLDATETIME`、`SQLDATETIM4`、`SQLDATETIM8`、`SQLMONEY`、`SQLMONEY4`、`SQLVARIANT` 和 `SQLUNIQUEID`</span><span class="sxs-lookup"><span data-stu-id="2dbd4-319">`SQLBIT`, `SQLTINYINT`, `SQLSMALLINT`, `SQLINT`, `SQLBIGINT`, `SQLFLT4`, `SQLFLT8`, `SQLDATETIME`, `SQLDATETIM4`, `SQLDATETIM8`, `SQLMONEY`, `SQLMONEY4`, `SQLVARIANT`, and `SQLUNIQUEID`</span></span>|<span data-ttu-id="2dbd4-320">无。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-320">None.</span></span>|<span data-ttu-id="2dbd4-321">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2dbd4-321">NULLABLE</span></span>|  
|<span data-ttu-id="2dbd4-322">变量号</span><span class="sxs-lookup"><span data-stu-id="2dbd4-322">Variable Number</span></span>|<span data-ttu-id="2dbd4-323">`SQLDECIMAL` 和 `SQLNUMERIC`</span><span class="sxs-lookup"><span data-stu-id="2dbd4-323">`SQLDECIMAL` and `SQLNUMERIC`</span></span>|<span data-ttu-id="2dbd4-324">无。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-324">None.</span></span>|<span data-ttu-id="2dbd4-325">NULLABLE、PRECISION、SCALE</span><span class="sxs-lookup"><span data-stu-id="2dbd4-325">NULLABLE, PRECISION, SCALE</span></span>|  
|<span data-ttu-id="2dbd4-326">LOB</span><span class="sxs-lookup"><span data-stu-id="2dbd4-326">LOB</span></span>|<span data-ttu-id="2dbd4-327">`SQLIMAGE`、`CharLOB`、`SQLTEXT` 和 `SQLUDT`</span><span class="sxs-lookup"><span data-stu-id="2dbd4-327">`SQLIMAGE`, `CharLOB`, `SQLTEXT`, and `SQLUDT`</span></span>|<span data-ttu-id="2dbd4-328">无。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-328">None.</span></span>|<span data-ttu-id="2dbd4-329">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2dbd4-329">NULLABLE</span></span>|  
|<span data-ttu-id="2dbd4-330">字符 LOB</span><span class="sxs-lookup"><span data-stu-id="2dbd4-330">Character LOB</span></span>|`SQLNTEXT`|<span data-ttu-id="2dbd4-331">无。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-331">None.</span></span>|<span data-ttu-id="2dbd4-332">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2dbd4-332">NULLABLE</span></span>|  
|<span data-ttu-id="2dbd4-333">二进制字符串</span><span class="sxs-lookup"><span data-stu-id="2dbd4-333">Binary string</span></span>|<span data-ttu-id="2dbd4-334">`SQLBINARY` 和 `SQLVARYBIN`</span><span class="sxs-lookup"><span data-stu-id="2dbd4-334">`SQLBINARY` and `SQLVARYBIN`</span></span>|<span data-ttu-id="2dbd4-335">无。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-335">None.</span></span>|<span data-ttu-id="2dbd4-336">NULLABLE、LENGTH</span><span class="sxs-lookup"><span data-stu-id="2dbd4-336">NULLABLE, LENGTH</span></span>|  
|<span data-ttu-id="2dbd4-337">字符串</span><span class="sxs-lookup"><span data-stu-id="2dbd4-337">Character string</span></span>|<span data-ttu-id="2dbd4-338">`SQLCHAR`、`SQLVARYCHAR`、`SQLNCHAR` 和 `SQLNVARCHAR`</span><span class="sxs-lookup"><span data-stu-id="2dbd4-338">`SQLCHAR`, `SQLVARYCHAR`, `SQLNCHAR`, and `SQLNVARCHAR`</span></span>|<span data-ttu-id="2dbd4-339">无。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-339">None.</span></span>|<span data-ttu-id="2dbd4-340">NULLABLE、LENGTH</span><span class="sxs-lookup"><span data-stu-id="2dbd4-340">NULLABLE, LENGTH</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2dbd4-341">若要大容量导出或导入 SQLXML 数据，请在格式化文件中使用下列数据类型之一：SQLCHAR 或 SQLVARYCHAR（数据以客户端代码页或排序规则隐含的代码页的形式发送）、SQLNCHAR 或 SQLNVARCHAR（数据以 Unicode 的形式发送）或者 SQLBINARY 或 SQLVARYBIN（数据不经任何转换直接发送）。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-341">To bulk export or import SQLXML data, use one of the following data types in your format file: SQLCHAR or SQLVARYCHAR (the data is sent in the client code page or in the code page implied by the collation), SQLNCHAR or SQLNVARCHAR (the data is sent as Unicode), or SQLBINARY or SQLVARYBIN (the data is sent without any conversion).</span></span>  
  
 <span data-ttu-id="2dbd4-342">有关值数据类型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的详细信息，请参阅 [数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-342">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
###  <a name="how-bulk-import-uses-the-row-element"></a><a name="HowUsesROW"></a><span data-ttu-id="2dbd4-343">批量导入如何使用 \<ROW> 元素</span><span class="sxs-lookup"><span data-stu-id="2dbd4-343">How Bulk Import Uses the \<ROW> Element</span></span>  
 <span data-ttu-id="2dbd4-344">在某些上下文中可以忽略 \<ROW> 元素。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-344">The \<ROW> element is ignored in some contexts.</span></span> <span data-ttu-id="2dbd4-345">\<ROW> 元素是否影响批量导入操作取决于操作的执行方式：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-345">Whether the \<ROW> element affects a bulk-import operation depends on how the operation is performed:</span></span>  
  
-   <span data-ttu-id="2dbd4-346">**bcp** 命令</span><span class="sxs-lookup"><span data-stu-id="2dbd4-346">the **bcp** command</span></span>  
  
     <span data-ttu-id="2dbd4-347">在目标表加载数据时，bcp 忽略 \<ROW> 组件。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-347">When data is loaded into a target table, **bcp** ignores the \<ROW> component.</span></span> <span data-ttu-id="2dbd4-348">相反， **bcp** 根据目标表的列类型来加载数据。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-348">Instead, **bcp** loads the data based on the column types of the target table.</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="2dbd4-349">语句（BULK INSERT 和 OPENROWSET 的大容量行集访问接口）</span><span class="sxs-lookup"><span data-stu-id="2dbd4-349">statements (BULK INSERT and OPENROWSET's Bulk rowset provider)</span></span>  
  
     <span data-ttu-id="2dbd4-350">在将数据批量导入表中时，[!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句使用 \<ROW> 组件来生成输入行集。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-350">When bulk importing data into a table, [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements use the \<ROW> component to generate the input rowset.</span></span> <span data-ttu-id="2dbd4-351">此外，[!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句还将根据 \<ROW> 下指定的列类型和目标表中的对应列，进行适当的类型转换。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-351">Also, [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements perform appropriate type conversions based on the column types specified under \<ROW> and the corresponding column in the target table.</span></span> <span data-ttu-id="2dbd4-352">如果格式化文件和目标表中指定的列类型之间存在不匹配，还将进行额外的类型转换。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-352">If a mismatch exists between column types as specified in the format file and in the target table, an extra type conversion occurs.</span></span> <span data-ttu-id="2dbd4-353">与 **bcp**相比，此额外的类型转换可能引起 BULK INSERT 或 OPENROWSET 的 BULK 行集提供程序中的行为出现某些差异（即损失精度）。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-353">This extra type conversion may lead to some discrepancy (that is, a loss of precision) in behavior in BULK INSERT or OPENROWSET's Bulk rowset provider as compared to **bcp**.</span></span>  
  
     <span data-ttu-id="2dbd4-354">无需任何其他信息，仅利用 \<ROW> 元素中的信息即可构造行。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-354">The information in the \<ROW> element allows a row to be constructed without requiring any additional information.</span></span> <span data-ttu-id="2dbd4-355">因此，可以使用 SELECT 语句 (SELECT \* FROM OPENROWSET(BULK *datafile* FORMATFILE=*xmlformatfile*) 来生成行集。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-355">For this reason, you can generate a rowset using a SELECT statement (SELECT \* FROM OPENROWSET(BULK *datafile* FORMATFILE=*xmlformatfile*).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2dbd4-356">OPENROWSET BULK 子句需要格式化文件（请注意，将字段的数据类型转换为列的数据类型只能使用 XML 格式化文件进行）。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-356">The OPENROWSET BULK clause requires a format file (note that converting from the data type of the field to the data type of a column is available only with an XML format file).</span></span>  
  
###  <a name="how-bulk-import-uses-the-column-element"></a><a name="HowUsesColumn"></a><span data-ttu-id="2dbd4-357">批量导入如何使用 \<COLUMN> 元素</span><span class="sxs-lookup"><span data-stu-id="2dbd4-357">How Bulk Import Uses the \<COLUMN> Element</span></span>  
 <span data-ttu-id="2dbd4-358">为了将数据批量导入表中，格式化文件中的 \<COLUMN> 元素将数据文件字段映射到表列，方法是指定：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-358">For bulk importing data into a table, the \<COLUMN> elements in a format file map a data-file field to table columns by specifying:</span></span>  
  
-   <span data-ttu-id="2dbd4-359">行中每个字段在数据文件中的位置。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-359">The position of each field within a row in the data file.</span></span>  
  
-   <span data-ttu-id="2dbd4-360">列类型，用于将字段数据类型转换为所需的列数据类型。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-360">The column type, which is used to convert the field data type to the desired column data type.</span></span>  
  
 <span data-ttu-id="2dbd4-361">如果没有列映射到某个字段，该字段将不会被复制到生成的行。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-361">If no column is mapped to a field, the field is not copied into the generated row(s).</span></span> <span data-ttu-id="2dbd4-362">此行为使得数据文件能够在不同的表中生成含有不同列的行。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-362">This behavior allows a data file to generate rows with different columns (in different tables).</span></span>  
  
 <span data-ttu-id="2dbd4-363">同样，为了将数据从表中批量导出，格式化文件中的各个 \<COLUMN> 将输入表行的列映射到输出数据文件中与之对应的字段。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-363">Similarly, for bulk exporting data from a table, each \<COLUMN> in the format file maps the column from the input table row to its corresponding field in the output data file.</span></span>  
  
###  <a name="putting-the-xsitype-value-into-a-data-set"></a><a name="PutXsiTypeValueIntoDataSet"></a> <span data-ttu-id="2dbd4-364">将 xsi:type 值放入数据集</span><span class="sxs-lookup"><span data-stu-id="2dbd4-364">Putting the xsi:type Value into a Data Set</span></span>  
 <span data-ttu-id="2dbd4-365">当通过 XML 架构定义 (XSD) 语言验证 XML 文档时，xsi:type 值不放入数据集。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-365">When an XML document is validated through the XML Schema Definition (XSD) language, the xsi:type value is not put into the data set.</span></span> <span data-ttu-id="2dbd4-366">但是，通过将 XML 格式化文件加载到 XML 文档（如 `myDoc`）中，可以将 xsi:type 信息放入数据集。如下列代码段所示：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-366">However, you can put the xsi:type information into the data set by loading the XML format file into an XML document (for example, `myDoc`), as illustrated in the following code snippet:</span></span>  
  
```  
...;  
myDoc.LoadXml(xmlFormat);  
XmlNodeList ColumnList = myDoc.GetElementsByTagName("COLUMN");  
for(int i=0;i<ColumnList.Count;i++)  
{  
   Console.Write("COLUMN: xsi:type=" +ColumnList[i].Attributes["type",  
      "http://www.w3.org/2001/XMLSchema-instance"].Value+"\n");  
}  
```  
  
##  <a name="sample-xml-format-files"></a><a name="SampleXmlFFs"></a> <span data-ttu-id="2dbd4-367">XML 格式化文件示例</span><span class="sxs-lookup"><span data-stu-id="2dbd4-367">Sample XML Format Files</span></span>  
 <span data-ttu-id="2dbd4-368">本节包含在各种情况下使用 XML 格式化文件的信息，并提供了一个 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-368">This section contains information on using XML format files in a variety of cases, including an [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] example.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2dbd4-369">在下列示例所示的数据文件中， `<tab>` 表示数据文件中的一个制表符， `<return>` 表示一个回车符。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-369">In the data files shown in the following examples, `<tab>` indicates a tab character in a data file, and `<return>` indicates a carriage return.</span></span>  
  

  
> [!NOTE]  
>  <span data-ttu-id="2dbd4-370">有关创建格式化文件的信息，请参阅 [创建格式化文件 (SQL Server)](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-370">For information about how to create format files, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
###  <a name="a-ordering-character-data-fields-the-same-as-table-columns"></a><a name="OrderCharFieldsSameAsCols"></a> <span data-ttu-id="2dbd4-371">A.</span><span class="sxs-lookup"><span data-stu-id="2dbd4-371">A.</span></span> <span data-ttu-id="2dbd4-372">对字符数据字段和表列进行相同的排序</span><span class="sxs-lookup"><span data-stu-id="2dbd4-372">Ordering character-data fields the same as table columns</span></span>  
 <span data-ttu-id="2dbd4-373">下面的示例显示了一个 XML 格式化文件，该文件描述一个包含三个字符数据字段的数据文件。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-373">The following example shows an XML format file that describes a data file containing three fields of character data.</span></span> <span data-ttu-id="2dbd4-374">格式化文件将数据文件映射到包含三列的表中。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-374">The format file maps the data file to a table that contains three columns.</span></span> <span data-ttu-id="2dbd4-375">数据字段与表中的列一一对应。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-375">The data fields correspond one-to-one with the columns of the table.</span></span>  
  
 <span data-ttu-id="2dbd4-376">**表（行）：** Person (Age int, FirstName varchar(20), LastName varchar(30))</span><span class="sxs-lookup"><span data-stu-id="2dbd4-376">**Table (row):** Person (Age int, FirstName varchar(20), LastName varchar(30))</span></span>  
  
 <span data-ttu-id="2dbd4-377">**数据文件（记录）：** Age\<tab>Firstname\<tab>Lastname\<return></span><span class="sxs-lookup"><span data-stu-id="2dbd4-377">**Data file (record):** Age\<tab>Firstname\<tab>Lastname\<return></span></span>  
  
 <span data-ttu-id="2dbd4-378">以下 XML 格式化文件从数据文件读取数据到表中。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-378">The following XML format file reads from the data file to the table.</span></span>  
  
 <span data-ttu-id="2dbd4-379">在 `<RECORD>` 元素中，格式化文件将所有三个字段中的数据值表示为字符数据。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-379">In the `<RECORD>` element, the format file represents the data values in all three fields as character data.</span></span> <span data-ttu-id="2dbd4-380">对于每个字段， `TERMINATOR` 属性指示位于数据值后面的终止符。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-380">For each field, the `TERMINATOR` attribute indicates the terminator that follows the data value.</span></span>  
  
 <span data-ttu-id="2dbd4-381">数据字段与表中的列一一对应。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-381">The data fields correspond one-to-one with the columns of the table.</span></span> <span data-ttu-id="2dbd4-382">在 `<ROW>` 元素中，格式化文件将 `Age` 列映射到第一个字段，将 `FirstName` 列映射到第二个字段，将 `LastName` 列映射到第三个字段。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-382">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the second field, and the column `LastName` to the third field.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>   
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="2" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="3" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2dbd4-383">有关等效的 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 示例，请参阅 [创建格式化文件 (SQL Server)](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-383">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
###  <a name="b-ordering-data-fields-and-table-columns-differently"></a><a name="OrderFieldsAndColsDifferently"></a> <span data-ttu-id="2dbd4-384">B.</span><span class="sxs-lookup"><span data-stu-id="2dbd4-384">B.</span></span> <span data-ttu-id="2dbd4-385">对数据字段和表列进行不同的排序</span><span class="sxs-lookup"><span data-stu-id="2dbd4-385">Ordering data fields and table columns differently</span></span>  
 <span data-ttu-id="2dbd4-386">下面的示例显示了一个 XML 格式化文件，该文件描述一个包含三个字符数据字段的数据文件。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-386">The following example shows an XML format file that describes a data file containing three fields of character data.</span></span> <span data-ttu-id="2dbd4-387">格式化文件将数据文件映射到包含三列（与数据文件的字段排序方式不同）的表中。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-387">The format file maps the data file to a table that contains three columns that are ordered differently from the fields of the data file.</span></span>  
  
 <span data-ttu-id="2dbd4-388">**表（行）：** Person (Age int, FirstName varchar(20), LastName varchar(30))</span><span class="sxs-lookup"><span data-stu-id="2dbd4-388">**Table (row):** Person (Age int, FirstName varchar(20), LastName varchar(30))</span></span>  
  
 <span data-ttu-id="2dbd4-389">**数据文件**（记录）：Age\<tab>Lastname\<tab>Firstname\<return></span><span class="sxs-lookup"><span data-stu-id="2dbd4-389">**Data file** (record): Age\<tab>Lastname\<tab>Firstname\<return></span></span>  
  
 <span data-ttu-id="2dbd4-390">在 `<RECORD>` 元素中，格式化文件将所有三个字段中的数据值表示为字符数据。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-390">In the `<RECORD>` element, the format file represents the data values in all three fields as character data.</span></span>  
  
 <span data-ttu-id="2dbd4-391">在 `<ROW>` 元素中，格式化文件将 `Age` 列映射到第一个字段，将 `FirstName` 列映射到第三个字段，将 `LastName` 列映射到第二个字段。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-391">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the third field, and the column `LastName` to the second field.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="2" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2dbd4-392">有关等效的 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 示例，请参阅 [使用格式化文件将表列映射到数据文件字段 (SQL Server)](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-392">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md).</span></span>  
  
### <a name="c-omitting-a-data-field"></a><span data-ttu-id="2dbd4-393">C.</span><span class="sxs-lookup"><span data-stu-id="2dbd4-393">C.</span></span> <span data-ttu-id="2dbd4-394">省略数据字段</span><span class="sxs-lookup"><span data-stu-id="2dbd4-394">Omitting a data field</span></span>  
 <span data-ttu-id="2dbd4-395">下面的示例显示了一个 XML 格式化文件，该文件描述一个包含四个字符数据字段的数据文件。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-395">The following example shows an XML format file that describes a data file containing four fields of character data.</span></span> <span data-ttu-id="2dbd4-396">格式化文件将数据文件映射到包含三列的表中。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-396">The format file maps the data file to a table that contains three columns.</span></span> <span data-ttu-id="2dbd4-397">第二个数据字段不与任何表列对应。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-397">The second data field does not correspond to any table column.</span></span>  
  
 <span data-ttu-id="2dbd4-398">**表（行）：** Person (Age int, FirstName Varchar(20), LastName Varchar(30))</span><span class="sxs-lookup"><span data-stu-id="2dbd4-398">**Table (row):** Person (Age int, FirstName Varchar(20), LastName Varchar(30))</span></span>  
  
 <span data-ttu-id="2dbd4-399">**数据文件（记录）：** Age\<tab>employeeID\<tab>Firstname\<tab>Lastname\<return></span><span class="sxs-lookup"><span data-stu-id="2dbd4-399">**Data file (record):** Age\<tab>employeeID\<tab>Firstname\<tab>Lastname\<return></span></span>  
  
 <span data-ttu-id="2dbd4-400">在 `<RECORD>` 元素中，格式化文件将所有四个字段中的数据值表示为字符数据。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-400">In the `<RECORD>` element, the format file represents the data values in all four fields as character data.</span></span> <span data-ttu-id="2dbd4-401">对于每个字段，TERMINATOR 属性指示位于数据值后面的终止符。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-401">For each field, the TERMINATOR attribute indicates the terminator that follows the data value.</span></span>  
  
 <span data-ttu-id="2dbd4-402">在 `<ROW>` 元素中，格式化文件将 `Age` 列映射到第一个字段，将 `FirstName` 列映射到第三个字段，将 `LastName` 列映射到第四个字段。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-402">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the third field, and the column `LastName` to the fourth field.</span></span>  
  
```  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="10"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="4" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2dbd4-403">有关等效的 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 示例，请参阅 [使用格式化文件跳过数据字段 (SQL Server)](use-a-format-file-to-skip-a-data-field-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-403">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Use a Format File to Skip a Data Field &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md).</span></span>  
  
###  <a name="d-mapping-field-xsitype-to-column-xsitype"></a><a name="MapXSItype"></a> <span data-ttu-id="2dbd4-404">D.</span><span class="sxs-lookup"><span data-stu-id="2dbd4-404">D.</span></span> <span data-ttu-id="2dbd4-405">将 \<FIELD> xsi:type 映射到 \<COLUMN> xsi:type</span><span class="sxs-lookup"><span data-stu-id="2dbd4-405">Mapping \<FIELD> xsi:type to \<COLUMN> xsi:type</span></span>  
 <span data-ttu-id="2dbd4-406">下面的示例显示了各种类型的字段及其与列的映射。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-406">The following example shows different types of fields and their mappings to columns.</span></span>  
  
```  
<?xml version = "1.0"?>  
<BCPFORMAT  
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   <RECORD>  
      <FIELD xsi:type="CharTerm" ID="C1" TERMINATOR="\t"   
            MAX_LENGTH="4"/>  
      <FIELD xsi:type="CharFixed" ID="C2" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="CharPrefix" ID="C3" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharTerm" ID="C4" TERMINATOR="\t"   
         MAX_LENGTH="4"/>  
      <FIELD xsi:type="NCharFixed" ID="C5" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharPrefix" ID="C6" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NativeFixed" ID="C7" LENGTH="4"/>  
   </RECORD>  
   <ROW>  
      <COLUMN SOURCE="C1" NAME="Age" xsi:type="SQLTINYINT"/>  
      <COLUMN SOURCE="C2" NAME="FirstName" xsi:type="SQLVARYCHAR"   
      LENGTH="16" NULLABLE="NO"/>  
      <COLUMN SOURCE="C3" NAME="LastName" />  
      <COLUMN SOURCE="C4" NAME="Salary" xsi:type="SQLMONEY"/>  
      <COLUMN SOURCE="C5" NAME="Picture" xsi:type="SQLIMAGE"/>  
      <COLUMN SOURCE="C6" NAME="Bio" xsi:type="SQLTEXT"/>  
      <COLUMN SOURCE="C7" NAME="Interest"xsi:type="SQLDECIMAL"   
      PRECISION="5" SCALE="3"/>  
   </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="e-mapping-xml-data-to-a-table"></a><a name="MapXMLDataToTbl"></a> <span data-ttu-id="2dbd4-407">E.</span><span class="sxs-lookup"><span data-stu-id="2dbd4-407">E.</span></span> <span data-ttu-id="2dbd4-408">将 XML 数据映射到表</span><span class="sxs-lookup"><span data-stu-id="2dbd4-408">Mapping XML data to a table</span></span>  
 <span data-ttu-id="2dbd4-409">下面的示例创建了一个空的两列表 (`t_xml`)，表中的第一列映射到 `int` 数据类型，第二列映射到 `xml` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-409">The following example creates an empty two-column table (`t_xml`), in which the first column maps to the `int` data type and the second column maps to the `xml` data type.</span></span>  
  
```  
CREATE TABLE t_xml (c1 int, c2 xml)  
```  
  
 <span data-ttu-id="2dbd4-410">以下 XML 格式化文件将数据文件加载到表 `t_xml`中。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-410">The following XML format file would load a data file into table `t_xml`.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativePrefix" PREFIX_LENGTH="1"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="8"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="c1" xsi:type="SQLINT"/>  
  <COLUMN SOURCE="2" NAME="c2" xsi:type="SQLNCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="f-importing-fixed-length-or-fixed-width-fields"></a><a name="ImportFixedFields"></a> <span data-ttu-id="2dbd4-411">F.</span><span class="sxs-lookup"><span data-stu-id="2dbd4-411">F.</span></span> <span data-ttu-id="2dbd4-412">导入固定长度或固定宽度的字段</span><span class="sxs-lookup"><span data-stu-id="2dbd4-412">Importing fixed-length or fixed-width fields</span></span>  
 <span data-ttu-id="2dbd4-413">下面的示例分别介绍包含 `10` 个或 `6` 个字符的固定字段。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-413">The following example describes fixed fields of `10` or `6` characters each.</span></span> <span data-ttu-id="2dbd4-414">格式化文件将这些字段的长度/宽度分别表示为 `LENGTH="10"` 和 `LENGTH="6"`。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-414">The format file represents these field lengths/widths as `LENGTH="10"` and `LENGTH="6"`, respectively.</span></span> <span data-ttu-id="2dbd4-415">数据文件中的每行都以回车符-换行符组合 {CR}{LF} 结束，格式化文件将这表示为 `TERMINATOR="\r\n"`。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-415">Every row of the data files ends with a carriage return-line feed combination, {CR}{LF}, which the format file represents as `TERMINATOR="\r\n"`.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT  
       xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"  
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharFixed" LENGTH="10"/>  
    <FIELD ID="2" xsi:type="CharFixed" LENGTH="6"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="C1" xsi:type="SQLINT" />  
    <COLUMN SOURCE="2" NAME="C2" xsi:type="SQLINT" />  
  </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="additional-examples"></a><a name="AdditionalExamples"></a> <span data-ttu-id="2dbd4-416">其他示例</span><span class="sxs-lookup"><span data-stu-id="2dbd4-416">Additional Examples</span></span>  
 <span data-ttu-id="2dbd4-417">有关非 XML 格式化文件和 XML 格式化文件的其他示例，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="2dbd4-417">For additional examples of both non-XML format files and XML format files, see the following topics:</span></span>  
  
-   [<span data-ttu-id="2dbd4-418">使用格式化文件跳过表列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbd4-418">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="2dbd4-419">使用格式化文件跳过数据字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbd4-419">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="2dbd4-420">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbd4-420">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="2dbd4-421">相关任务</span><span class="sxs-lookup"><span data-stu-id="2dbd4-421">Related Tasks</span></span>  
  
-   [<span data-ttu-id="2dbd4-422">创建格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbd4-422">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="2dbd4-423">使用格式化文件批量导入数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbd4-423">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="2dbd4-424">使用格式化文件跳过表列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbd4-424">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="2dbd4-425">使用格式化文件跳过数据字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbd4-425">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="2dbd4-426">使用格式化文件将表列映射到数据文件字段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbd4-426">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="2dbd4-427">相关内容</span><span class="sxs-lookup"><span data-stu-id="2dbd4-427">Related Content</span></span>  
 <span data-ttu-id="2dbd4-428">无。</span><span class="sxs-lookup"><span data-stu-id="2dbd4-428">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dbd4-429">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2dbd4-429">See Also</span></span>  
 <span data-ttu-id="2dbd4-430">[批量导入和导出数据 (SQL Server)](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2dbd4-430">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="2dbd4-431">[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2dbd4-431">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="2dbd4-432">[非 XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2dbd4-432">[Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="2dbd4-433">用来导入或导出数据的格式化文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2dbd4-433">Format Files for Importing or Exporting Data &#40;SQL Server&#41;</span></span>](format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
