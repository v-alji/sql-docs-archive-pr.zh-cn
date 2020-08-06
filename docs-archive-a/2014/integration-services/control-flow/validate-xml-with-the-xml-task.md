---
title: 使用 XML 任务验证 XML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- XML validation
- XML, validating
ms.assetid: 224fc025-c21f-4d43-aa9d-5ffac337f9b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 633a269f53c85353c956b33bff8fd3af518dad56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576898"
---
# <a name="validate-xml-with-the-xml-task"></a><span data-ttu-id="ddb4b-102">Validate XML with the XML Task</span><span class="sxs-lookup"><span data-stu-id="ddb4b-102">Validate XML with the XML Task</span></span>
  <span data-ttu-id="ddb4b-103">通过启用 XML 任务的 `ValidationDetails` 属性，验证 XML 文档并获取丰富的错误输出。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-103">Validate XML documents and get rich error output by enabling the `ValidationDetails` property of the XML Task.</span></span>

 <span data-ttu-id="ddb4b-104">下面的屏幕快照显示 **XML 任务编辑器** ，其中包含具有丰富错误输出的 XML 验证所需的设置。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-104">The following screen shot shows the **XML Task Editor** with the settings required for XML validation with rich error output.</span></span>

 <span data-ttu-id="ddb4b-105">![XML 任务编辑器中的 XML 任务属性](../media/xmltaskproperties.jpg "XML 任务编辑器中的 XML 任务属性")</span><span class="sxs-lookup"><span data-stu-id="ddb4b-105">![XML task properties in the XML Task Editor](../media/xmltaskproperties.jpg "XML task properties in the XML Task Editor")</span></span>

 <span data-ttu-id="ddb4b-106">在可以使用 `ValidationDetails` 属性之前，XML 任务的 XML 验证仅返回 true 或 false 结果，而不包含关于错误或其位置的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-106">Before the `ValidationDetails` property was available, XML validation by the XML Task returned only a true or false result, with no information about errors or their locations.</span></span> <span data-ttu-id="ddb4b-107">现在，当你将 `ValidationDetails` 设置为 true 时，输出文件将包含关于每个错误的详细信息，包括行号和位置。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-107">Now, when you set `ValidationDetails` to true, the output file contains detailed information about every error including the line number and the position.</span></span> <span data-ttu-id="ddb4b-108">此信息可用于了解、查找和修复 XML 文档中的错误。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-108">You can use this information to understand, locate, and fix errors in XML documents.</span></span>

 <span data-ttu-id="ddb4b-109">XML 验证功能可轻松扩展以适应大型 XML 文档和大量错误。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-109">The XML validation functionality scales easily for large XML documents and large numbers of errors.</span></span> <span data-ttu-id="ddb4b-110">由于输出文件本身采用 XML 格式，你可以查询和分析输出。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-110">Since the output file itself is in XML format, you can query and analyze the output.</span></span> <span data-ttu-id="ddb4b-111">例如，如果输出中包含大量错误，你可以按本主题中所述，使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询对错误分组。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-111">For example, if the output contains a large number of errors, you can group the errors by using a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query, as described in this topic.</span></span>

> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ddb4b-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) `ValidationDetails` 在 Service Pack 2 中引入了属性 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) introduced the `ValidationDetails` property in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 2.</span></span> <span data-ttu-id="ddb4b-113">SQL Server 2016 中还提供了 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 和中的属性。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-113">The property is also available in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] and in SQL Server 2016.</span></span>

## <a name="sample-output-for-xml-thats-valid"></a><span data-ttu-id="ddb4b-114">有效的 XML 示例输出</span><span class="sxs-lookup"><span data-stu-id="ddb4b-114">Sample output for XML that's valid</span></span>
 <span data-ttu-id="ddb4b-115">下面是有效 XML 文件的示例输出文件（带有验证结果）。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-115">Here is a sample output file with validation results for a valid XML file.</span></span>

```xml

<root xmlns:ns="https://schemas.microsoft.com/xmltools/2002/xmlvalidation">
    <metadata>
        <result>true</result>
        <errors>0</errors>
        <warnings>0</warnings>
        <startTime>2015-05-28T10:27:22.087</startTime>
        <endTime>2015-05-28T10:29:07.007</endTime>
        <xmlFile>d:\Temp\TestData.xml</xmlFile>
        <xsdFile>d:\Temp\TestSchema.xsd</xsdFile>
    </metadata>
    <messages />
</root>
```

## <a name="sample-output-for-xml-thats-not-valid"></a><span data-ttu-id="ddb4b-116">无效的 XML 示例输出</span><span class="sxs-lookup"><span data-stu-id="ddb4b-116">Sample output for XML that's not valid</span></span>
 <span data-ttu-id="ddb4b-117">下面是包含少量错误的 XML 文件的示例输出文件（带有验证结果）。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-117">Here is a sample output file with validation results for an XML file that contains a small number of errors.</span></span> <span data-ttu-id="ddb4b-118">为便于阅读，\<error> 元素的文本已换行。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-118">The text of the \<error> elements has been wrapped for readability.</span></span>

```xml

<root xmlns:ns="https://schemas.microsoft.com/xmltools/2002/xmlvalidation">
    <metadata>
        <result>false</result>
        <errors>2</errors>
        <warnings>0</warnings>
        <startTime>2015-05-28T10:45:09.538</startTime>
        <endTime>2015-05-28T10:45:09.558</endTime>
        <xmlFile>C:\Temp\TestData.xml</xmlFile>
        <xsdFile>C:\Temp\TestSchema.xsd</xsdFile>
    </metadata>
    <messages>
        <error line="5" position="26">The 'ApplicantRole' element is invalid - The value 'wer3' is invalid
    according to its datatype 'ApplicantRoleType' - The Enumeration constraint failed.</error>
        <error line="16" position="28">The 'Phone' element is invalid - The value 'we3056666666' is invalid
     according to its datatype 'phone' - The Pattern constraint failed.</error>
    </messages>
</root>
```

## <a name="analyze-xml-validation-output-with-a-transact-sql-query"></a><span data-ttu-id="ddb4b-119">使用 Transact-SQL 查询分析 XML 验证输出</span><span class="sxs-lookup"><span data-stu-id="ddb4b-119">Analyze XML validation output with a Transact-SQL query</span></span>
 <span data-ttu-id="ddb4b-120">如果 XML 验证输出中包含大量错误，你可以使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中加载输出。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-120">If the output of XML validation contains a large number of errors, you can use a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query to load the output in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ddb4b-121">然后可以使用 T-SQL 语言的所有功能（包括 WHERE、GROUP BY、ORDER BY，JOIN 等）对错误列表进行分析。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-121">Then you can analyze the error list with all the capabilities of the T-SQL language including WHERE, GROUP BY, ORDER BY, JOIN, and so forth.</span></span>

```sql
DECLARE @xml XML;

SELECT @xml = XmlDoc   
FROM OPENROWSET (BULK N'C:\Temp\XMLValidation_2016-02-212T10-41-00.xml', SINGLE_BLOB) AS Tab(XmlDoc);

-- Query # 1, flat list of errors
-- convert to relational/rectangular
;WITH XMLNAMESPACES ('https://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS
(
SELECT col.value('@line','INT') AS line
     , col.value('@position','INT') AS position
     , col.value('.','VARCHAR(1024)') AS error
FROM @XML.nodes('/root/messages/error') AS tab(col)
)
SELECT * FROM rs;
-- WHERE error LIKE '%whatever_string%'

-- Query # 2, count of errors grouped by the error message
-- convert to relational/rectangular
;WITH XMLNAMESPACES ('https://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS
(
SELECT col.value('@line','INT') AS line
     , col.value('@position','INT') AS position
     , col.value('.','VARCHAR(1024)') AS error
FROM @XML.nodes('/root/messages/error') AS tab(col)
)
SELECT COALESCE(error,'Total # of errors:') AS [error], COUNT(*) AS [counter]
FROM rs
GROUP BY GROUPING SETS ((error), ())
ORDER BY 2 DESC, COALESCE(error, 'Z');

```

 <span data-ttu-id="ddb4b-122">下面是上述文本中第二个示例查询在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中的结果。</span><span class="sxs-lookup"><span data-stu-id="ddb4b-122">Here is the result in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] of the second sample query shown in the preceding text.</span></span>

 <span data-ttu-id="ddb4b-123">![用于在 Management Studio 中将 XML 错误分组的查询](../media/queryforxmlerrors.jpg "用于在 Management Studio 中将 XML 错误分组的查询")</span><span class="sxs-lookup"><span data-stu-id="ddb4b-123">![Query to group XML errors in Management Studio](../media/queryforxmlerrors.jpg "Query to group XML errors in Management Studio")</span></span>

## <a name="see-also"></a><span data-ttu-id="ddb4b-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ddb4b-124">See Also</span></span>
 <span data-ttu-id="ddb4b-125">[Xml 任务](xml-task.md) [xml 任务编辑器 &#40;常规页&#41;](../xml-task-editor-general-page.md)</span><span class="sxs-lookup"><span data-stu-id="ddb4b-125">[XML Task](xml-task.md) [XML Task Editor &#40;General Page&#41;](../xml-task-editor-general-page.md)</span></span>


