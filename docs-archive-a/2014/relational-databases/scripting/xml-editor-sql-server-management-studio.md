---
title: XML 编辑器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.editorxml.f1
- sql12.swb.xmleditor.f1
- vs.xmleditor
- sql12.swb.editor.xml.f1
helpviewer_keywords:
- XML Designer [SQL Server Management Studio]
ms.assetid: 0824a5ce-e67b-4b53-98d9-d371faf2d23c
author: rothja
ms.author: jroth
ms.openlocfilehash: b7c3bbbda4f5a31c4d83b559c1aa623ca2aff89f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590149"
---
# <a name="xml-editor-sql-server-management-studio"></a><span data-ttu-id="34e97-102">XML 编辑器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="34e97-102">XML Editor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="34e97-103">提供用于处理 XML 架构、ADO.NET 数据集和 XML 文档的一组可视工具。</span><span class="sxs-lookup"><span data-stu-id="34e97-103">Provides a set of visual tools for working with XML Schemas, ADO.NET datasets, and XML documents.</span></span> <span data-ttu-id="34e97-104">XML 设计器支持由万维网联合会 (W3C) 定义的 XML 架构定义 (XSD) 语言。</span><span class="sxs-lookup"><span data-stu-id="34e97-104">The XML Designer supports the XML Schema Definition (XSD) language defined by the World Wide Web Consortium (WC3).</span></span> <span data-ttu-id="34e97-105">该设计器不支持 DTD（文档类型定义）或其他 XML 架构语言，例如 XDR（XML 数据简化）。</span><span class="sxs-lookup"><span data-stu-id="34e97-105">The designer does not support DTDs (document type definitions) or other XML schema languages, such as XDR (XML-Data Reduced).</span></span>  
  
 <span data-ttu-id="34e97-106">若要显示该设计器，请向您的项目中添加数据集、XML 架构或 XML 文件，或打开下表中列出的任何类型的文件。</span><span class="sxs-lookup"><span data-stu-id="34e97-106">To display the designer, add a dataset, XML Schema, or XML file to your project or open any of the file types listed in the table below.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="34e97-107">在“架构”视图中没有 **“撤消”** 命令。</span><span class="sxs-lookup"><span data-stu-id="34e97-107">There is no **Undo** command when working in Schema view.</span></span> <span data-ttu-id="34e97-108">请仔细规划您的任务并经常保存文件。</span><span class="sxs-lookup"><span data-stu-id="34e97-108">Plan your work carefully and save your files often.</span></span>  
  
 <span data-ttu-id="34e97-109">该设计器提供了以下三种视图（或模式）来处理 XML 文件、XML 架构和数据集：</span><span class="sxs-lookup"><span data-stu-id="34e97-109">The designer provides the following three views (or modes) to work on XML files, XML Schemas, and datasets:</span></span>  
  
|<span data-ttu-id="34e97-110">查看</span><span class="sxs-lookup"><span data-stu-id="34e97-110">View</span></span>|<span data-ttu-id="34e97-111">说明</span><span class="sxs-lookup"><span data-stu-id="34e97-111">Description</span></span>|<span data-ttu-id="34e97-112">支持的文件类型</span><span class="sxs-lookup"><span data-stu-id="34e97-112">File types supported</span></span>|  
|----------|-----------------|--------------------------|  
|<span data-ttu-id="34e97-113">**架构**</span><span class="sxs-lookup"><span data-stu-id="34e97-113">**Schema**</span></span>|<span data-ttu-id="34e97-114">用于直观地创建和修改 XML 架构以及 ADO.NET 数据集。</span><span class="sxs-lookup"><span data-stu-id="34e97-114">For visually creating and modifying XML Schemas and ADO.NET datasets.</span></span>|<span data-ttu-id="34e97-115">.xsd</span><span class="sxs-lookup"><span data-stu-id="34e97-115">.xsd</span></span>|  
|<span data-ttu-id="34e97-116">**数据**</span><span class="sxs-lookup"><span data-stu-id="34e97-116">**Data**</span></span>|<span data-ttu-id="34e97-117">用于在结构化数据网格中直观地修改 XML 数据文件。</span><span class="sxs-lookup"><span data-stu-id="34e97-117">For visually modifying XML data files in a structured data grid.</span></span>|<span data-ttu-id="34e97-118">.xml</span><span class="sxs-lookup"><span data-stu-id="34e97-118">.xml</span></span>|  
|<span data-ttu-id="34e97-119">**XML**</span><span class="sxs-lookup"><span data-stu-id="34e97-119">**XML**</span></span>|<span data-ttu-id="34e97-120">用于编辑 XML；源编辑器提供有颜色编码和 IntelliSense 功能，包括“完成单词”和“列出成员”。</span><span class="sxs-lookup"><span data-stu-id="34e97-120">For editing XML; the source editor provides color-coding and IntelliSense, including Complete Word and List Members.</span></span>|<span data-ttu-id="34e97-121">.xml .xsd .xslt .wsdl.web.resx.tdl.wsf.hta.disco.vsdisco.config</span><span class="sxs-lookup"><span data-stu-id="34e97-121">.xml .xsd .xslt .wsdl.web.resx.tdl.wsf.hta.disco.vsdisco.config</span></span>|  
|<span data-ttu-id="34e97-122">**显示计划**</span><span class="sxs-lookup"><span data-stu-id="34e97-122">**ShowPlan**</span></span>|<span data-ttu-id="34e97-123">显示使用 SET SHOWPLAN_XML ON 选项创建的 xml 查询计划。</span><span class="sxs-lookup"><span data-stu-id="34e97-123">Displays xml query plans created using the SET SHOWPLAN_XML ON option.</span></span>|<span data-ttu-id="34e97-124">.showplan</span><span class="sxs-lookup"><span data-stu-id="34e97-124">.showplan</span></span>|  
  
## <a name="schema-view"></a><span data-ttu-id="34e97-125">“架构”视图</span><span class="sxs-lookup"><span data-stu-id="34e97-125">Schema View</span></span>  
 <span data-ttu-id="34e97-126">“架构”视图可以直观地显示构成 XML 架构和 ADO.NET 数据集的元素、属性、类型等。</span><span class="sxs-lookup"><span data-stu-id="34e97-126">Schema view provides a visual representation of the elements, attributes, types, and so on, that make up XML Schemas and ADO.NET datasets.</span></span>  
  
 <span data-ttu-id="34e97-127">在“架构”视图中，您可以通过从“工具箱”的“XML 架构”选项卡中，或从服务器资源管理器中，将元素拖动到设计图面，来构造架构和数据集。</span><span class="sxs-lookup"><span data-stu-id="34e97-127">In Schema view you can construct schemas and datasets by dropping elements on the design surface from either the XML Schema tab of the Toolbox or from Server Explorer.</span></span> <span data-ttu-id="34e97-128">另外，您可以通过右键单击设计图面，再从快捷菜单中选择“添加”，向设计器添加元素。</span><span class="sxs-lookup"><span data-stu-id="34e97-128">Additionally, you can add elements to the designer by right-clicking the design surface and selecting Add from the shortcut menu.</span></span>  
  
 <span data-ttu-id="34e97-129">在“架构”视图中，您可以：</span><span class="sxs-lookup"><span data-stu-id="34e97-129">In Schema view you can:</span></span>  
  
-   <span data-ttu-id="34e97-130">构造和修改现有的 XML 架构及 ADO.NET 数据集</span><span class="sxs-lookup"><span data-stu-id="34e97-130">Construct and modify existing XML Schemas and ADO.NET datasets</span></span>  
  
-   <span data-ttu-id="34e97-131">创建和编辑表之间的关系</span><span class="sxs-lookup"><span data-stu-id="34e97-131">Create and edit relationships between tables</span></span>  
  
-   <span data-ttu-id="34e97-132">创建和编辑键</span><span class="sxs-lookup"><span data-stu-id="34e97-132">Create and edit keys</span></span>  
  
-   <span data-ttu-id="34e97-133">基于 XML 架构生成 ADO.NET 数据集</span><span class="sxs-lookup"><span data-stu-id="34e97-133">Generate ADO.NET datasets from XML Schemas</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34e97-134">“架构”视图中元素的布局存储在 .xsx 文件中，通过在解决方案资源管理器的工具栏中单击 **“显示所有文件”** ，再展开 .xsd 文件，可以看到该文件。</span><span class="sxs-lookup"><span data-stu-id="34e97-134">The layout of elements in Schema view is stored in the .xsx file, which can be seen by clicking **Show All Files** in the Solution Explorer toolbar, and then expanding the .xsd file.</span></span> <span data-ttu-id="34e97-135">如果没有 .xsx 文件，则表示在 XML 设计器中从未打开过 .xsd 文件。</span><span class="sxs-lookup"><span data-stu-id="34e97-135">If there is no .xsx file present, it means the .xsd file has never been opened in the XML Designer.</span></span>  
  
### <a name="customizing-schema-view"></a><span data-ttu-id="34e97-136">自定义“架构”视图</span><span class="sxs-lookup"><span data-stu-id="34e97-136">Customizing Schema View</span></span>  
 <span data-ttu-id="34e97-137">通过以下功能可以修改“架构”视图中元素的可视布局：</span><span class="sxs-lookup"><span data-stu-id="34e97-137">The following features modify the visual layout of elements in Schema view:</span></span>  
  
-   <span data-ttu-id="34e97-138">缩放</span><span class="sxs-lookup"><span data-stu-id="34e97-138">Zooming</span></span>  
  
-   <span data-ttu-id="34e97-139">展开或折叠嵌套的元素</span><span class="sxs-lookup"><span data-stu-id="34e97-139">Expanding or collapsing of nested elements</span></span>  
  
-   <span data-ttu-id="34e97-140">自动排列元素的布局</span><span class="sxs-lookup"><span data-stu-id="34e97-140">Automatically arranging layout of elements</span></span>  
  
-   <span data-ttu-id="34e97-141">重置折叠元素的默认状态</span><span class="sxs-lookup"><span data-stu-id="34e97-141">Resetting default state of collapsed elements</span></span>  
  
##### <a name="to-expand-hidden-nested-elements"></a><span data-ttu-id="34e97-142">展开隐藏的嵌套元素</span><span class="sxs-lookup"><span data-stu-id="34e97-142">To expand hidden nested elements</span></span>  
  
-   <span data-ttu-id="34e97-143">单击元素底部的加号图标。</span><span class="sxs-lookup"><span data-stu-id="34e97-143">Click the plus icon on the bottom of the element.</span></span>  
  
##### <a name="to-collapse-nested-elements"></a><span data-ttu-id="34e97-144">折叠嵌套的元素</span><span class="sxs-lookup"><span data-stu-id="34e97-144">To collapse nested elements</span></span>  
  
-   <span data-ttu-id="34e97-145">单击希望显示在设计器中的最底部元素的减号图标。</span><span class="sxs-lookup"><span data-stu-id="34e97-145">Click the minus icon on the bottom-most element that you want to appear on the designer.</span></span>  
  
## <a name="data-view"></a><span data-ttu-id="34e97-146">数据视图</span><span class="sxs-lookup"><span data-stu-id="34e97-146">Data View</span></span>  
 <span data-ttu-id="34e97-147">“数据”视图提供一个可用于修改 .xml 文件的数据网格。</span><span class="sxs-lookup"><span data-stu-id="34e97-147">Data view provides a data grid that can be used to modify .xml files.</span></span> <span data-ttu-id="34e97-148">在“数据”视图中只能编辑 XML 文件中的内容（不包括标记和结构）。</span><span class="sxs-lookup"><span data-stu-id="34e97-148">Only the content (but not the tags and structure) in an XML file can be edited in Data view.</span></span>  
  
 <span data-ttu-id="34e97-149">“数据”视图中有两个单独的区域： **“数据表”** 和 **“数据”** 。</span><span class="sxs-lookup"><span data-stu-id="34e97-149">There are two separate areas in Data view: **Data Tables** and **Data**.</span></span> <span data-ttu-id="34e97-150">“数据表”  区域用于按照嵌套顺序（从最外层到最内层）列出 XML 文件中所定义的关系。</span><span class="sxs-lookup"><span data-stu-id="34e97-150">The **Data Tables** area is a list of relations defined in the XML file, in the order of its nesting (from the outermost to the innermost).</span></span> <span data-ttu-id="34e97-151">**“数据”** 区域是一个数据网格，会根据“数据表”区域中的所选内容显示数据。</span><span class="sxs-lookup"><span data-stu-id="34e97-151">The **Data** area is a data grid that displays data based on the selection in the Data Tables area.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34e97-152">新创建的 XML 文件不包含数据，因此不能在“数据”视图中显示。</span><span class="sxs-lookup"><span data-stu-id="34e97-152">Newly created XML files contain no data and therefore cannot be displayed in Data view.</span></span> <span data-ttu-id="34e97-153">另外，有一些 XML 文档实例根本不能调用“数据”视图。</span><span class="sxs-lookup"><span data-stu-id="34e97-153">There are also some instances of XML documents where data view cannot be invoked at all.</span></span> <span data-ttu-id="34e97-154">即使系统认为 XML 文件的格式正确，但如果其中的数据不是结构化数据，则在尝试切换到“数据”视图时将生成以下消息：“尽管此文档的格式良好，但它包含了数据视图无法显示的结构”。</span><span class="sxs-lookup"><span data-stu-id="34e97-154">Although the XML would be considered well formed, if it is not structured data trying to switch to Data view will generate the following message: "Although this document is well formed, it contains structure that Data View cannot display."</span></span>  
  
 <span data-ttu-id="34e97-155">在“数据”视图中，您可以：</span><span class="sxs-lookup"><span data-stu-id="34e97-155">In Data view you can:</span></span>  
  
-   <span data-ttu-id="34e97-156">手动填充数据表</span><span class="sxs-lookup"><span data-stu-id="34e97-156">Manually populate data tables</span></span>  
  
-   <span data-ttu-id="34e97-157">编辑现有的数据表</span><span class="sxs-lookup"><span data-stu-id="34e97-157">Edit existing data tables</span></span>  
  
-   <span data-ttu-id="34e97-158">基于 XML 文档生成 XML 架构</span><span class="sxs-lookup"><span data-stu-id="34e97-158">Generate an XML Schema from an XML document</span></span>  
  
## <a name="xml-view"></a><span data-ttu-id="34e97-159">XML 视图</span><span class="sxs-lookup"><span data-stu-id="34e97-159">XML View</span></span>  
 <span data-ttu-id="34e97-160">XML 视图提供了一个用于编辑原始 XML 数据的编辑器，并提供有 IntelliSense 和颜色编码功能。</span><span class="sxs-lookup"><span data-stu-id="34e97-160">XML view provides an editor for editing raw XML and provides IntelliSense and color coding.</span></span> <span data-ttu-id="34e97-161">在处理具有关联架构的 .xsd 文件和 .xml 文件时，可以使用语句结束功能。</span><span class="sxs-lookup"><span data-stu-id="34e97-161">Statement completion is available when working on .xsd files and .xml files that have an associated schema.</span></span> <span data-ttu-id="34e97-162">键入 \< 以启动标记，将显示在该位置有效的元素列表。</span><span class="sxs-lookup"><span data-stu-id="34e97-162">Type \< to initiate a tag and you will be presented with a list of elements that are valid at that location.</span></span> <span data-ttu-id="34e97-163">在键入元素名称并按空格键后，将显示相应元素所支持属性的列表。</span><span class="sxs-lookup"><span data-stu-id="34e97-163">After you type the element name and press the SPACEBAR, you will be presented with a list of attributes that the element supports.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="34e97-164">IntelliSense 选项。</span><span class="sxs-lookup"><span data-stu-id="34e97-164">IntelliSense options are not available on the toolbar.</span></span> <span data-ttu-id="34e97-165">若要在 XML 编辑器中访问这些选项，请在 **“编辑”** 菜单上单击 **IntelliSense**。</span><span class="sxs-lookup"><span data-stu-id="34e97-165">When in the XML Editor, to access the options, on the **Edit** menu, click **IntelliSense**.</span></span>  
  
## <a name="showplan-view"></a><span data-ttu-id="34e97-166">“显示计划”视图</span><span class="sxs-lookup"><span data-stu-id="34e97-166">SHOWPLAN view</span></span>  
 <span data-ttu-id="34e97-167">在使用 SET SHOWPLAN_XML ON 选项创建查询计划时，可以将其保存为 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="34e97-167">Query plans can be saved in XML format when created using SET SHOWPLAN_XML ON option.</span></span> <span data-ttu-id="34e97-168">双击带有 .showplan 扩展名的文件即可打开该查询计划。</span><span class="sxs-lookup"><span data-stu-id="34e97-168">Double-click a file with the .showplan extension to open the query plan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e97-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34e97-169">See Also</span></span>  
 [<span data-ttu-id="34e97-170">以 XML 格式保存执行计划</span><span class="sxs-lookup"><span data-stu-id="34e97-170">Save an Execution Plan in XML Format</span></span>](../performance/save-an-execution-plan-in-xml-format.md)  
  
  
