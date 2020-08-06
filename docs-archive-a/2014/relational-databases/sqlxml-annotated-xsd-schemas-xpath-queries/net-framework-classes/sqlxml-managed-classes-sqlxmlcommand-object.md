---
title: SqlXmlCommand 对象 (SQLXML 托管类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void ExecuteNonQuery() method
- namespaces property
- Stream ExecuteStream() method
- CommandType property
- RootTag property
- OutputEncoding property
- XmlReader ExecuteXmlReader() method
- Managed Classes [SQLXML], SqlXmlCommand object
- SQLXML Managed Classes, SqlXmlCommand object
- Base Path property
- void ClearParameters() method
- public void ExecuteToStream(Stream outputStream) method
- SqlXmlCommand object
- CommandText property
- XslPath property
- SchemaPath property
- SqlXmlParameter CreateParameter() method
- ClientSideXML property
- CommandStream property
ms.assetid: c1f9e0bb-a89d-4d6a-a96e-289ef516a3a6
author: rothja
ms.author: jroth
ms.openlocfilehash: 78b72581f549ea007dae0cdc7044fd9a809920af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587269"
---
# <a name="sqlxmlcommand-object-sqlxml-managed-classes"></a><span data-ttu-id="3ddb4-102">SqlXmlCommand 对象（SQLXML 托管类）</span><span class="sxs-lookup"><span data-stu-id="3ddb4-102">SqlXmlCommand Object (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="3ddb4-103">这是 SqlXmlCommand 对象的构造函数：</span><span class="sxs-lookup"><span data-stu-id="3ddb4-103">This is the constructor for the SqlXmlCommand object:</span></span>  
  
```  
public SqlXmlCommand(string cnString)  
```  
  
 <span data-ttu-id="3ddb4-104">其中， `cnString` 是用于标识服务器、数据库和登录信息的 ADO 或 OLEDB 连接字符串，例如 `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"` 。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-104">Where `cnString` is the ADO or OLEDB connection string that identifies the server, database, and the login information-for example, `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"`.</span></span>  
  
 <span data-ttu-id="3ddb4-105">在该连接字符串中，`Provider` 必须是 SQLOLEDB，并且 `Data Provider` 不应包括在访问接口字符串中。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-105">In the connection string, the `Provider` must be SQLOLEDB and the `Data Provider` should not be included in the provider string).</span></span>  
  
 <span data-ttu-id="3ddb4-106">有关工作示例，请参阅[执行 SQL 查询 &#40;SQLXML 托管类&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-106">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ddb4-107">方法</span><span class="sxs-lookup"><span data-stu-id="3ddb4-107">Methods</span></span>  
 <span data-ttu-id="3ddb4-108">TheSqlXmlCommand 对象支持多种方法，包括用于执行命令的以下方法：</span><span class="sxs-lookup"><span data-stu-id="3ddb4-108">TheSqlXmlCommand object supports several methods, including the following methods for executing a command:</span></span>  
  
 <span data-ttu-id="3ddb4-109">void ExecuteNonQuery ( # A1</span><span class="sxs-lookup"><span data-stu-id="3ddb4-109">void ExecuteNonQuery()</span></span>  
 <span data-ttu-id="3ddb4-110">执行该命令，但不返回任何内容。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-110">Executes the command, but does not return anything.</span></span> <span data-ttu-id="3ddb4-111">如果您想要执行非查询命令（即，不返回任何内容的命令），则此方法将很有用。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-111">This method is useful if you want to execute a nonquery command (that is, a command that does not return anything).</span></span> <span data-ttu-id="3ddb4-112">例如，执行更新记录但不返回任何内容的 updategram 或 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-112">An example is executing an updategram or a DiffGram that updates records but returns nothing.</span></span>  
  
 <span data-ttu-id="3ddb4-113">Stream ExecuteStream ( # A1</span><span class="sxs-lookup"><span data-stu-id="3ddb4-113">Stream ExecuteStream()</span></span>  
 <span data-ttu-id="3ddb4-114">返回一个新的流对象。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-114">Returns a new Stream object.</span></span> <span data-ttu-id="3ddb4-115">在您希望查询结果在新的流中返回给您时，此方法很有用。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-115">This method is useful when you want the query results returned to you in a new stream.</span></span> <span data-ttu-id="3ddb4-116">有关工作示例，请参阅[执行 SQL 查询 &#40;SQLXML 托管类&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-116">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="3ddb4-117">公共 void ExecuteToStream (Stream outputStream) </span><span class="sxs-lookup"><span data-stu-id="3ddb4-117">public void ExecuteToStream(Stream outputStream)</span></span>  
 <span data-ttu-id="3ddb4-118">将查询结果写入到现有流中。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-118">Writes the query results to an existing stream.</span></span> <span data-ttu-id="3ddb4-119">如果你有一个需要追加结果的流 (例如，将查询结果写入 OutputStream) ，则此方法非常有用，例如。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-119">This method is useful when you have a stream to which you need the results appended (for example, to have the query results written to the System.Web.HttpResponse.OutputStream).</span></span> <span data-ttu-id="3ddb4-120">有关工作示例，请参阅[执行 SQL 查询 &#40;SQLXML 托管类&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-120">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="3ddb4-121">XmlReader ExecuteXmlReader ( # A1</span><span class="sxs-lookup"><span data-stu-id="3ddb4-121">XmlReader ExecuteXmlReader()</span></span>  
 <span data-ttu-id="3ddb4-122">返回 XmlReader 对象。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-122">Returns an XmlReader object.</span></span> <span data-ttu-id="3ddb4-123">您可以使用此方法直接在 XmlReader 对象中操作数据，或插入 System.Xml 的可链体系结构。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-123">You can use this method to either manipulate data in the XmlReader object directly or plug in the chainable architecture of System.Xml.</span></span> <span data-ttu-id="3ddb4-124">有关详细信息，请参阅 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 文档。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-124">For more information, see the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework documentation.</span></span> <span data-ttu-id="3ddb4-125">有关工作示例，请参阅[使用 ExecuteXMLReader 方法执行 SQL 查询](executing-sql-queries-by-using-the-executexmlreader-method.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-125">For a working sample, see [Executing SQL Queries by Using the ExecuteXMLReader Method](executing-sql-queries-by-using-the-executexmlreader-method.md).</span></span>  
  
 <span data-ttu-id="3ddb4-126">TheSqlXmlCommand 对象还支持以下附加方法：</span><span class="sxs-lookup"><span data-stu-id="3ddb4-126">TheSqlXmlCommand object also supports these additional methods:</span></span>  
  
 <span data-ttu-id="3ddb4-127">SqlXmlParameter CreateParameter ( # A1</span><span class="sxs-lookup"><span data-stu-id="3ddb4-127">SqlXmlParameter CreateParameter()</span></span>  
 <span data-ttu-id="3ddb4-128">创建 SqlXmlParameter 对象。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-128">Creates an SqlXmlParameter object.</span></span> <span data-ttu-id="3ddb4-129">您可以为此对象的*名称*和*值*参数设置值。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-129">You can set values for the *Name* and *Value* parameters of this object.</span></span> <span data-ttu-id="3ddb4-130">如果您希望将参数传递到某一命令，则此方法很有用。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-130">This method is useful if you want to pass parameters to a command.</span></span> <span data-ttu-id="3ddb4-131">有关工作示例，请参阅[执行 SQL 查询 &#40;SQLXML 托管类&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-131">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="3ddb4-132">void ClearParameters ( # A1</span><span class="sxs-lookup"><span data-stu-id="3ddb4-132">void ClearParameters()</span></span>  
 <span data-ttu-id="3ddb4-133">清除为给定命令对象创建的参数。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-133">Clears parameter(s) that were created for a given command object.</span></span> <span data-ttu-id="3ddb4-134">如果您想要对同一命令对象执行多个查询，则此方法很有用。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-134">This method is useful if you want to execute multiple queries on the same command object.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3ddb4-135">属性</span><span class="sxs-lookup"><span data-stu-id="3ddb4-135">Properties</span></span>  
 <span data-ttu-id="3ddb4-136">SqlXmlCommand 对象还支持以下属性：</span><span class="sxs-lookup"><span data-stu-id="3ddb4-136">The SqlXmlCommand object also supports these properties:</span></span>  
  
 <span data-ttu-id="3ddb4-137">ClientSideXml</span><span class="sxs-lookup"><span data-stu-id="3ddb4-137">ClientSideXml</span></span>  
 <span data-ttu-id="3ddb4-138">在设置为 True 时，指定要在客户端上发生行集到 XML 的转换，而非在服务器上发生。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-138">When set to True, specifies that conversion of the rowset to XML is to occur on the client instead of on the server.</span></span> <span data-ttu-id="3ddb4-139">在希望将性能负荷移到中间层时，此属性很有用。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-139">This property is useful when you want to move the performance load to the middle tier.</span></span> <span data-ttu-id="3ddb4-140">该属性还允许您使用 FOR XML 包装现有存储过程，以便获取 XML 输出。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-140">The property also allows you to wrap the existing stored procedures with FOR XML to get XML output.</span></span>  
  
 <span data-ttu-id="3ddb4-141">SchemaPath</span><span class="sxs-lookup"><span data-stu-id="3ddb4-141">SchemaPath</span></span>  
 <span data-ttu-id="3ddb4-142">映射架构的名称以及目录路径（例如 C:\x\y\MySchema.xml）。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-142">The name of the mapping schema along with the directory path (for example, C:\x\y\MySchema.xml).</span></span> <span data-ttu-id="3ddb4-143">此属性用于为 XPath 查询指定映射架构。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-143">This property is useful for specifying a mapping schema for XPath queries.</span></span> <span data-ttu-id="3ddb4-144">指定的路径可以是绝对路径或相对路径。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-144">The path that is specified can be absolute or relative.</span></span> <span data-ttu-id="3ddb4-145">如果路径是相对路径，则使用基路径中指定的基路径解析相对路径。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-145">If the path is relative, the base path that is specified in Base Path is used to resolve the relative path.</span></span> <span data-ttu-id="3ddb4-146">如果未指定基本路径，则相对路径是相对于当前目录的路径。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-146">If no base path is specified, the relative path is relative to the current directory.</span></span> <span data-ttu-id="3ddb4-147">有关工作示例，请参阅[在 .Net 环境中访问 SQLXML 功能](accessing-sqlxml-functionality-in-the-net-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-147">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
 <span data-ttu-id="3ddb4-148">XslPath</span><span class="sxs-lookup"><span data-stu-id="3ddb4-148">XslPath</span></span>  
 <span data-ttu-id="3ddb4-149">XSL 文件的名称以及目录路径。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-149">The name of the XSL file along with the directory path.</span></span> <span data-ttu-id="3ddb4-150">指定的路径可以是绝对路径或相对路径。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-150">The path that is specified can be absolute or relative.</span></span> <span data-ttu-id="3ddb4-151">如果路径是相对路径，则使用基路径中指定的基路径解析相对路径。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-151">If the path is relative, the base path that is specified in Base Path is used to resolve the relative path.</span></span> <span data-ttu-id="3ddb4-152">如果未指定基本路径，则相对路径是相对于当前目录的路径。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-152">If no base path is specified, the relative path is relative to the current directory.</span></span> <span data-ttu-id="3ddb4-153">有关工作示例，请参阅将[XSL 转换 &#40;SQLXML 托管类&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-153">For a working sample, see [Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="3ddb4-154">基路径</span><span class="sxs-lookup"><span data-stu-id="3ddb4-154">Base Path</span></span>  
 <span data-ttu-id="3ddb4-155">基本路径（目录路径）。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-155">The base path (a directory path).</span></span> <span data-ttu-id="3ddb4-156">此属性可用于解析为 XSL 文件指定的相对路径 (方法是使用 XslPath 属性) 、通过使用 SchemaPath 属性) 的映射架构文件 (，或者使用特性 (指定的 XML 模板中的外部架构引用 `mapping-schema` 。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-156">This property is useful for resolving a relative path that is specified for an XSL file (by using the XslPath property), a mapping schema file (by using the SchemaPath property), or an external schema reference in an XML template (specified by using the `mapping-schema` attribute).</span></span>  
  
 <span data-ttu-id="3ddb4-157">OutputEncoding</span><span class="sxs-lookup"><span data-stu-id="3ddb4-157">OutputEncoding</span></span>  
 <span data-ttu-id="3ddb4-158">为在执行命令时返回的流指定编码。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-158">Specifies the encoding for the stream that is returned when the command executes.</span></span> <span data-ttu-id="3ddb4-159">此属性用于为返回的流请求特定的编码。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-159">This property is useful for requesting a specific encoding for the stream that is returned.</span></span> <span data-ttu-id="3ddb4-160">某些常用编码是 UTF-8、ANSI 和 Unicode。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-160">Some commonly used encodings are UTF-8, ANSI, and Unicode.</span></span> <span data-ttu-id="3ddb4-161">UTF-8 为默认编码。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-161">UTF-8 is the default encoding.</span></span>  
  
 <span data-ttu-id="3ddb4-162">命名空间</span><span class="sxs-lookup"><span data-stu-id="3ddb4-162">Namespaces</span></span>  
 <span data-ttu-id="3ddb4-163">允许执行使用命名空间的 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-163">Enables the execution of XPath queries that use namespaces.</span></span> <span data-ttu-id="3ddb4-164">有关带有命名空间的 XPath 查询的详细信息，请参阅[执行包含命名空间 &#40;SQLXML 托管类&#41;的 Xpath 查询](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-164">For more information about XPath queries with namespaces, see [Executing XPath Queries with Namespaces &#40;SQLXML Managed Classes&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md).</span></span> <span data-ttu-id="3ddb4-165">有关工作示例，请参阅[执行 &#40;SQLXML 托管类&#41;的 XPath 查询](executing-xpath-queries-sqlxml-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-165">For a working sample, see [Executing XPath Queries &#40;SQLXML Managed Classes&#41;](executing-xpath-queries-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="3ddb4-166">RootTag</span><span class="sxs-lookup"><span data-stu-id="3ddb4-166">RootTag</span></span>  
 <span data-ttu-id="3ddb4-167">为命令执行生成的 XML 提供单个根元素。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-167">Provides the single root element for XML generated by command execution.</span></span> <span data-ttu-id="3ddb4-168">有效的 XML 文档要求单个根级别标记。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-168">A valid XML document requires a single root-level tag.</span></span> <span data-ttu-id="3ddb4-169">如果执行的命令生成 XML 片段（没有单个顶级元素），则可为返回的 XML 指定一个根元素。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-169">If the command executed generates an XML fragment (without a single top-level element) you can specify a root element for the returning XML.</span></span> <span data-ttu-id="3ddb4-170">有关工作示例，请参阅将[XSL 转换 &#40;SQLXML 托管类&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-170">For a working sample, see [Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="3ddb4-171">CommandText</span><span class="sxs-lookup"><span data-stu-id="3ddb4-171">CommandText</span></span>  
 <span data-ttu-id="3ddb4-172">命令的文本。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-172">The text of the command.</span></span> <span data-ttu-id="3ddb4-173">此属性用于指定您要执行的命令的文本。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-173">This property is used for specifying the text of the command you want to execute.</span></span> <span data-ttu-id="3ddb4-174">有关工作示例，请参阅[执行 SQL 查询 &#40;SQLXML 托管类&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-174">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="3ddb4-175">CommandStream</span><span class="sxs-lookup"><span data-stu-id="3ddb4-175">CommandStream</span></span>  
 <span data-ttu-id="3ddb4-176">命令流。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-176">The command stream.</span></span> <span data-ttu-id="3ddb4-177">如果您要根据某一文件（例如 XML 模板）执行命令，则此属性很有用。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-177">This property is useful if you want to execute a command from a file (for example, an XML template).</span></span> <span data-ttu-id="3ddb4-178">当使用 CommandStream 时，仅支持 **"Template"**、 **"UpdateGram"** 和 **"DiffGram" CommandType**值。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-178">When you are using CommandStream, only **"Template"**, **"UpdateGram"** and **"DiffGram"CommandType** values are supported.</span></span> <span data-ttu-id="3ddb4-179">有关工作示例，请参阅[使用 CommandStream 属性执行模板文件](executing-template-files-by-using-the-commandstream-property.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-179">For a working sample, see [Executing Template Files by Using the CommandStream Property](executing-template-files-by-using-the-commandstream-property.md).</span></span>  
  
 <span data-ttu-id="3ddb4-180">CommandType</span><span class="sxs-lookup"><span data-stu-id="3ddb4-180">CommandType</span></span>  
 <span data-ttu-id="3ddb4-181">标识命令的类型。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-181">Identifies the type of command.</span></span> <span data-ttu-id="3ddb4-182">此属性用于指定您要执行的命令的类型。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-182">This property is used for specifying the type of command you want to execute.</span></span> <span data-ttu-id="3ddb4-183">下表中的值确定命令的类型。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-183">The values in the following table determine the type of the command.</span></span> <span data-ttu-id="3ddb4-184">有关工作示例，请参阅[在 .Net 环境中访问 SQLXML 功能](accessing-sqlxml-functionality-in-the-net-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-184">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
|<span data-ttu-id="3ddb4-185">值</span><span class="sxs-lookup"><span data-stu-id="3ddb4-185">Value</span></span>|<span data-ttu-id="3ddb4-186">说明</span><span class="sxs-lookup"><span data-stu-id="3ddb4-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ddb4-187">SqlXmlCommandType</span><span class="sxs-lookup"><span data-stu-id="3ddb4-187">SqlXmlCommandType.Sql</span></span>|<span data-ttu-id="3ddb4-188">执行某一 SQL 命令（例如 `SELECT * FROM Employees FOR XML AUTO`）。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-188">Executes an SQL command (for example, `SELECT * FROM Employees FOR XML AUTO`).</span></span>|  
|<span data-ttu-id="3ddb4-189">SqlXmlCommandType</span><span class="sxs-lookup"><span data-stu-id="3ddb4-189">SqlXmlCommandType.XPath</span></span>|<span data-ttu-id="3ddb4-190">执行某一 XPath 命令（例如 `Employees[@EmployeeID=1]`）。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-190">Executes an XPath command (for example, `Employees[@EmployeeID=1]`).</span></span>|  
|<span data-ttu-id="3ddb4-191">SqlXmlCommandType 模板</span><span class="sxs-lookup"><span data-stu-id="3ddb4-191">SqlXmlCommandType.Template</span></span>|<span data-ttu-id="3ddb4-192">执行某一 XML 模板。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-192">Executes an XML template.</span></span>|  
|<span data-ttu-id="3ddb4-193">SqlXmlCommandType. TemplateFile</span><span class="sxs-lookup"><span data-stu-id="3ddb4-193">SqlXmlCommandType.TemplateFile</span></span>|<span data-ttu-id="3ddb4-194">执行指定路径上的模板文件。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-194">Executes a template file at the specified path.</span></span>|  
|<span data-ttu-id="3ddb4-195">SqlXmlCommandType. UpdateGram</span><span class="sxs-lookup"><span data-stu-id="3ddb4-195">SqlXmlCommandType.UpdateGram</span></span>|<span data-ttu-id="3ddb4-196">执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-196">Executes an updategram.</span></span>|  
|<span data-ttu-id="3ddb4-197">SqlXmlCommandType</span><span class="sxs-lookup"><span data-stu-id="3ddb4-197">SqlXmlCommandType.Diffgram</span></span>|<span data-ttu-id="3ddb4-198">执行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="3ddb4-198">Executes a DiffGram.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ddb4-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ddb4-199">See Also</span></span>  
 <span data-ttu-id="3ddb4-200">[SQLXML 托管类 &#40;的 SqlXmlParameter 对象&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md) </span><span class="sxs-lookup"><span data-stu-id="3ddb4-200">[SqlXmlParameter Object &#40;SQLXML Managed Classes&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md) </span></span>  
 [<span data-ttu-id="3ddb4-201">SQLXML 托管类 &#40;的 SqlXmlAdapter 对象&#41;</span><span class="sxs-lookup"><span data-stu-id="3ddb4-201">SqlXmlAdapter Object &#40;SQLXML Managed Classes&#41;</span></span>](sqlxml-managed-classes-sqlxmladapter-object.md)  
  
  
