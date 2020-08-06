---
title: 加载 XML 数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], loading
- loading XML data
ms.assetid: d1741e8d-f44e-49ec-9f14-10208b5468a7
author: rothja
ms.author: jroth
ms.openlocfilehash: c48d1d6feccb7df9fec9801ee56abcab99884754
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690410"
---
# <a name="load-xml-data"></a><span data-ttu-id="08f03-102">加载 XML 数据</span><span class="sxs-lookup"><span data-stu-id="08f03-102">Load XML Data</span></span>
  <span data-ttu-id="08f03-103">您可以采用多种方式将 XML 数据传输到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="08f03-103">You can transfer XML data into [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in several ways.</span></span> <span data-ttu-id="08f03-104">例如：</span><span class="sxs-lookup"><span data-stu-id="08f03-104">For example:</span></span>  
  
-   <span data-ttu-id="08f03-105">如果您的数据位于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的 [n]text 或 image 列中，则可以使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]导入表。</span><span class="sxs-lookup"><span data-stu-id="08f03-105">If you have your data in an [n]text or image column in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, you can import the table by using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="08f03-106">使用 ALTER TABLE 语句将列类型更改为 XML。</span><span class="sxs-lookup"><span data-stu-id="08f03-106">Change the column type to XML by using the ALTER TABLE statement.</span></span>  
  
-   <span data-ttu-id="08f03-107">您可以使用 bcp out 将数据从其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中大容量复制出来，然后再使用 bcp in 将数据大容量插入到更高版本的数据库中。</span><span class="sxs-lookup"><span data-stu-id="08f03-107">You can bulk copy your data from another [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using bcp out, and then bulk insert the data into the later version database by using bcp in.</span></span>  
  
-   <span data-ttu-id="08f03-108">如果您的数据在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的关系列中，则可以创建一个包含 [n]text 列的表，也可选择包含一个主键列来放置行标识符。</span><span class="sxs-lookup"><span data-stu-id="08f03-108">If you have data in relational columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, create a new table with an [n]text column and, optionally, a primary key column for a row identifier.</span></span> <span data-ttu-id="08f03-109">使用客户端编程检索在服务器中使用 FOR XML 生成的 XML，并将其写入 `[n]text` 列。</span><span class="sxs-lookup"><span data-stu-id="08f03-109">Use client-side programming to retrieve the XML that is generated at the server with FOR XML and write it into the `[n]text` column.</span></span> <span data-ttu-id="08f03-110">然后，使用上面提到的方法将数据传输到更高版本的数据库中。</span><span class="sxs-lookup"><span data-stu-id="08f03-110">Then, use the previously mentioned techniques to transfer data to a later version database.</span></span> <span data-ttu-id="08f03-111">您可以选择将 XML 直接写入更高版本数据库中的 XML 列。</span><span class="sxs-lookup"><span data-stu-id="08f03-111">You can choose to write the XML into an XML column in the later version database directly.</span></span>  
  
## <a name="bulk-loading-xml-data"></a><span data-ttu-id="08f03-112">大容量加载 XML 数据</span><span class="sxs-lookup"><span data-stu-id="08f03-112">Bulk loading XML data</span></span>  
 <span data-ttu-id="08f03-113">可以通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的大容量加载功能（如 bcp）将 XML 数据大容量加载到服务器中。</span><span class="sxs-lookup"><span data-stu-id="08f03-113">You can bulk load XML data into the server by using the bulk loading capabilities of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as bcp.</span></span> <span data-ttu-id="08f03-114">通过使用 OPENROWSET 可以将文件中的数据加载到 XML 列中。</span><span class="sxs-lookup"><span data-stu-id="08f03-114">OPENROWSET allows you to load data into an XML column from files.</span></span> <span data-ttu-id="08f03-115">以下示例说明了这一点。</span><span class="sxs-lookup"><span data-stu-id="08f03-115">The following example illustrates this point.</span></span>  
  
##### <a name="example-loading-xml-from-files"></a><span data-ttu-id="08f03-116">示例：从文件中加载 XML</span><span class="sxs-lookup"><span data-stu-id="08f03-116">Example: Loading XML from Files</span></span>  
 <span data-ttu-id="08f03-117">此示例显示了如何在表 T 中插入行。从文件 C:\MyFile\xmlfile.xml 中将 XML 列的值作为 CLOB 加载，并为整数列提供了值 10。</span><span class="sxs-lookup"><span data-stu-id="08f03-117">This example shows how to insert a row in table T. The value of the XML column is loaded from file C:\MyFile\xmlfile.xml as CLOB, and the integer column is supplied the value 10.</span></span>  
  
```  
INSERT INTO T  
SELECT 10, xCol  
FROM    (SELECT *      
    FROM OPENROWSET (BULK 'C:\MyFile\xmlfile.xml', SINGLE_CLOB)   
 AS xCol) AS R(xCol)  
```  
  
## <a name="text-encoding"></a><span data-ttu-id="08f03-118">文本编码</span><span class="sxs-lookup"><span data-stu-id="08f03-118">Text Encoding</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="08f03-119">以 Unicode (UTF-16) 存储 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="08f03-119">stores XML data in Unicode (UTF-16).</span></span> <span data-ttu-id="08f03-120">从服务器检索的 XML 数据均采用 UTF-16 编码。</span><span class="sxs-lookup"><span data-stu-id="08f03-120">XML data retrieved from the server comes out in UTF-16 encoding.</span></span> <span data-ttu-id="08f03-121">如果需要采用不同的编码，必须对检索到的数据执行所需的转换。</span><span class="sxs-lookup"><span data-stu-id="08f03-121">If you want a different encoding, you have to perform the required conversion on the retrieved data.</span></span> <span data-ttu-id="08f03-122">有时，XML 数据可能采用不同的编码。</span><span class="sxs-lookup"><span data-stu-id="08f03-122">Sometimes, the XML data may be in a different encoding.</span></span> <span data-ttu-id="08f03-123">如果是这样，加载数据时必须非常小心。</span><span class="sxs-lookup"><span data-stu-id="08f03-123">If it is, you have to use care during data loading.</span></span> <span data-ttu-id="08f03-124">例如：</span><span class="sxs-lookup"><span data-stu-id="08f03-124">For example:</span></span>  
  
-   <span data-ttu-id="08f03-125">如果文本 XML 采用 Unicode（UCS-2、UTF-16），可以将其赋给 XML 列、变量或参数，不会有任何问题。</span><span class="sxs-lookup"><span data-stu-id="08f03-125">If your text XML is in Unicode (UCS-2, UTF-16), you can assign it to an XML column, variable, or parameter  without any problems.</span></span>  
  
-   <span data-ttu-id="08f03-126">如果由于源代码页的原因，编码不是 Unicode 而是隐式的，则数据库中的字符串代码页应与要加载的码位相同或与其兼容。</span><span class="sxs-lookup"><span data-stu-id="08f03-126">If the encoding is not Unicode and is implicit, because of the source code page, the string code page in the database should be the same as or compatible with the code points that you want to load.</span></span> <span data-ttu-id="08f03-127">如果需要，请使用 COLLATE。</span><span class="sxs-lookup"><span data-stu-id="08f03-127">If required, use COLLATE.</span></span> <span data-ttu-id="08f03-128">如果不存在这样的服务器代码页，则必须添加使用正确编码的显式 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="08f03-128">If no such server code page exists, you have to add an explicit XML declaration with the correct encoding.</span></span>  
  
-   <span data-ttu-id="08f03-129">若要使用显式编码，请使用不与代码页交互的 `varbinary()` 类型，或使用相应代码页的字符串类型。</span><span class="sxs-lookup"><span data-stu-id="08f03-129">To use an explicit encoding, use either the `varbinary()` type, which has no interaction with code pages, or use a string type of the appropriate code page.</span></span> <span data-ttu-id="08f03-130">然后，将数据赋给 XML 列、变量或参数。</span><span class="sxs-lookup"><span data-stu-id="08f03-130">Then, assign the data to an XML column, variable, or parameter.</span></span>  
  
### <a name="example-explicitly-specifying-an-encoding"></a><span data-ttu-id="08f03-131">示例：显式指定编码</span><span class="sxs-lookup"><span data-stu-id="08f03-131">Example: Explicitly Specifying an Encoding</span></span>  
 <span data-ttu-id="08f03-132">假定您的 XML 文档和 vcdoc 存储为不具有显式 XML 声明的 `varchar(max)`。</span><span class="sxs-lookup"><span data-stu-id="08f03-132">Assume that you have an XML document, vcdoc, stored as `varchar(max)` that does not have an explicit XML declaration.</span></span> <span data-ttu-id="08f03-133">下面的语句添加了带有编码“iso8859-1”的 XML 声明，连接了 XML 文档，然后将结果转换为 `varbinary(max)`，以便保留字节表示形式并最终将它转换为 XML。</span><span class="sxs-lookup"><span data-stu-id="08f03-133">The following statement adds an XML declaration with the encoding "iso8859-1", concatenates the XML document, casts the result to `varbinary(max)` so that the byte representation is preserved, and then finally casts it to XML.</span></span> <span data-ttu-id="08f03-134">这样，XML 处理器就可以根据指定的编码“iso8859-1”分析数据，并为字符串值生成相应的 UTF-16 表示形式。</span><span class="sxs-lookup"><span data-stu-id="08f03-134">This enables the XML processor to parse the data according to the specified encoding "iso8859-1" and generate the corresponding UTF-16 representation for string values.</span></span>  
  
```  
SELECT CAST(   
CAST (('<?xml version="1.0" encoding="iso8859-1"?>'+ vcdoc) AS VARBINARY (MAX))   
 AS XML)  
```  
  
### <a name="string-encoding-incompatibilities"></a><span data-ttu-id="08f03-135">字符串编码不兼容性</span><span class="sxs-lookup"><span data-stu-id="08f03-135">String Encoding Incompatibilities</span></span>  
 <span data-ttu-id="08f03-136">如果将 XML 作为字符串文字复制并粘贴到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的查询编辑器窗口，可能会遇到 [N]VARCHAR 字符串编码不兼容的情况。</span><span class="sxs-lookup"><span data-stu-id="08f03-136">If you copy and paste XML as a string literal into the Query Editor window in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you might experience [N]VARCHAR string encoding incompatibilities.</span></span> <span data-ttu-id="08f03-137">这将取决于 XML 实例的编码。</span><span class="sxs-lookup"><span data-stu-id="08f03-137">This will depend on the encoding of your XML instance.</span></span> <span data-ttu-id="08f03-138">在很多情况下，您可能需要删除 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="08f03-138">In many cases, you may want to remove the XML declaration.</span></span> <span data-ttu-id="08f03-139">例如：</span><span class="sxs-lookup"><span data-stu-id="08f03-139">For example:</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
  <xsd:schema ...  
```  
  
 <span data-ttu-id="08f03-140">然后，应包含 N 以使 XML 实例成为 Unicode 实例。</span><span class="sxs-lookup"><span data-stu-id="08f03-140">You should then include an N to make the XML instance an instance of Unicode.</span></span> <span data-ttu-id="08f03-141">例如：</span><span class="sxs-lookup"><span data-stu-id="08f03-141">For example:</span></span>  
  
```  
-- Assign XML instance to a variable.  
DECLARE @X XML  
SET @X = N'...'  
-- Insert XML instance into an xml type column.  
INSERT INTO T VALUES (N'...')  
-- Create an XML schema collection  
CREATE XML SCHEMA COLLECTION XMLCOLL1 AS N'<xsd:schema ... '  
```  
  
## <a name="see-also"></a><span data-ttu-id="08f03-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08f03-142">See Also</span></span>  
 [<span data-ttu-id="08f03-143">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="08f03-143">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
