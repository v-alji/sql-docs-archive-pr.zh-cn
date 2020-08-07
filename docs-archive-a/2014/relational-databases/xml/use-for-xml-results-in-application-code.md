---
title: 在应用程序代码中使用 FOR XML 结果 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, application code usage
- XML [SQL Server], FOR XML clause
- ASP.NET [SQL Server]
- .NET Framework [SQL Server], FOR XML data
- ADO [SQL Server]
- XML data islands [SQL Server]
- data islands [SQL Server]
ms.assetid: 41ae67bd-ece9-49ea-8062-c8d658ab4154
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cabe7e65cb53a28a370615ed84e38ba2b8db44c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590084"
---
# <a name="use-for-xml-results-in-application-code"></a><span data-ttu-id="99c47-102">在应用程序代码中使用 FOR XML 结果</span><span class="sxs-lookup"><span data-stu-id="99c47-102">Use FOR XML Results in Application Code</span></span>
  <span data-ttu-id="99c47-103">通过在 SQL 查询中使用 FOR XML 子句，可以检索查询结果，甚至可以将其转换为 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="99c47-103">By using FOR XML clauses with SQL queries, you can retrieve and even cast query results as XML data.</span></span> <span data-ttu-id="99c47-104">当 FOR XML 查询结果可以在 XML 应用程序代码中使用时，您可以使用此功能执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="99c47-104">This functionality allows you to do the following when FOR XML query results can be used in XML application code:</span></span>  
  
-   <span data-ttu-id="99c47-105">查询 SQL 表中 [XML 数据 (SQL Server)](xml-data-sql-server.md) 值的实例</span><span class="sxs-lookup"><span data-stu-id="99c47-105">Query SQL tables for instances of [XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) values</span></span>  
  
-   <span data-ttu-id="99c47-106">应用 [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md) 以将包含文本或图像类型化数据的查询的结果返回为 XML</span><span class="sxs-lookup"><span data-stu-id="99c47-106">Apply the [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md) to return the result of queries that contain text or image typed data as XML</span></span>  
  
 <span data-ttu-id="99c47-107">本主题介绍了说明这些方法的示例。</span><span class="sxs-lookup"><span data-stu-id="99c47-107">This topic provides examples that demonstrate these approaches.</span></span>  
  
## <a name="retrieving-for-xml-data-with-ado-and-xml-data-islands"></a><span data-ttu-id="99c47-108">用 ADO 和 XML 数据岛检索 FOR XML 数据</span><span class="sxs-lookup"><span data-stu-id="99c47-108">Retrieving FOR XML Data with ADO and XML Data Islands</span></span>  
 <span data-ttu-id="99c47-109">使用 FOR XML 查询时，支持 COM `Stream` 接口的 ADO `IStream` 对象或其他对象 [例如，Active Server Page (ASP) `Request` 和 `Response` 对象] 可用于包含结果。</span><span class="sxs-lookup"><span data-stu-id="99c47-109">The ADO `Stream` object or other objects that support the COM `IStream` interface, such as the Active Server Pages (ASP) `Request` and `Response` objects, can be used to contain the results when you are working with FOR XML queries.</span></span>  
  
 <span data-ttu-id="99c47-110">例如，以下 ASP 代码显示在 AdventureWorks 示例数据库的 Sales.Store 表中查询 `xml` 数据类型列 Demographics 的结果。</span><span class="sxs-lookup"><span data-stu-id="99c47-110">For example, the following ASP code shows the results of querying an `xml` data type column, Demographics, in the Sales.Store table of the AdventureWorks sample database.</span></span> <span data-ttu-id="99c47-111">确切地说，该查询在 CustomerID 等于 3 的行中查找此列的实例值。</span><span class="sxs-lookup"><span data-stu-id="99c47-111">Specifically, the query looks for the instance value of this column for the row where the CustomerID is equal to 3.</span></span>  
  
```  
<!-- BeginRecordAndStreamVBS -->  
<%@ LANGUAGE = VBScript %>  
<!-- %  Option Explicit      % -->  
<!-- 'Request.ServerVariables("SERVER_NAME") & ";" & _ -->  
<HTML>  
<HEAD>  
<META NAME="GENERATOR" Content="Microsoft Developer Studio"/>  
<META HTTP-EQUIV="Content-Type" content="text/html"; charset="iso-8859-1">  
<TITLE>FOR XML Query Example</TITLE>  
<STYLE>  
   BODY  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
   H3  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
</STYLE>  
  
<!-- #include file="adovbs.inc" -->  
<%  
   Response.Write "<H3>Server-side processing</H3>"  
   Response.Write "Page Generated @ " & Now() & "<BR/>"  
   Dim adoConn  
   Set adoConn = Server.CreateObject("ADODB.Connection")  
   Dim sConn  
   sConn = "Provider=SQLOLEDB;Data Source=(local);" & _  
            "Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
   Response.write "Connect String = " & sConn & "<BR/>"  
   adoConn.ConnectionString = sConn  
   adoConn.CursorLocation = adUseClient  
   adoConn.Open  
   Response.write "ADO Version = " & adoConn.Version & "<BR/>"  
   Response.write "adoConn.State = " & adoConn.State & "<BR/>"  
   Dim adoCmd  
   Set adoCmd = Server.CreateObject("ADODB.Command")  
   Set adoCmd.ActiveConnection = adoConn  
   Dim sQuery  
   sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'><sql:query>SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</sql:query></ROOT>"  
   Response.write "Query String = " & sQuery & "<BR/>"  
   Dim adoStreamQuery  
   Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
   adoStreamQuery.Open  
   adoStreamQuery.WriteText sQuery, adWriteChar  
   adoStreamQuery.Position = 0  
   adoCmd.CommandStream = adoStreamQuery  
   adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
   Response.write "Pushing XML to client for processing "  & "<BR/>"  
   adoCmd.Properties("Output Stream") = Response  
   Response.write "<XML ID='MyDataIsle'>"  
   adoCmd.Execute , , 1024  
   Response.write "</XML>"  
%>  
<SCRIPT language="VBScript" For="window" Event="onload">  
   Dim xmlDoc  
   Set xmlDoc = MyDataIsle.XMLDocument  
   Dim root  
   Set root = xmlDoc.documentElement.childNodes.Item(0).childNodes.Item(0).childNodes.Item(0)  
   For each child in root.childNodes  
      dim OutputXML  
      OutputXML = document.all("log").innerHTML  
      document.all("log").innerHTML = OutputXML & "<LI><B>" & child.nodeName &  ":</B>  " & child.Text  & "</LI>"  
   Next  
   MsgBox xmlDoc.xml  
</SCRIPT>  
</HEAD>  
<BODY>  
   <H3>Client-side processing of XML Document MyDataIsle</H3>  
   <UL id=log>  
   </UL>  
</BODY>  
</HTML>  
<!-- EndRecordAndStreamVBS -->  
```  
  
 <span data-ttu-id="99c47-112">此示例 ASP 页包含使用 ADO 执行 FOR XML 查询并在 XML 数据岛 (MyDataIsle) 中返回 XML 结果的服务器端 VBScript。</span><span class="sxs-lookup"><span data-stu-id="99c47-112">This example ASP page contains server-side VBScript that uses ADO to execute the FOR XML query and return the XML results in an XML data island, MyDataIsle.</span></span> <span data-ttu-id="99c47-113">然后，在浏览器中返回此 XML 数据岛以进行其他客户端处理。</span><span class="sxs-lookup"><span data-stu-id="99c47-113">This XML data island is then returned in the browser for additional client-side processing.</span></span> <span data-ttu-id="99c47-114">其他客户端 VBScript 代码用于处理 XML 数据岛的内容。</span><span class="sxs-lookup"><span data-stu-id="99c47-114">Additional client-side VBScript code is then used to process the contents of the XML data island.</span></span> <span data-ttu-id="99c47-115">先将这些内容显示为产生的 DHTML 的一部分并打开消息框来显示 XML 数据岛的预处理内容，再执行此过程。</span><span class="sxs-lookup"><span data-stu-id="99c47-115">This process is performed before displaying the contents as part of the resultant DHTML and opening a message box to show the preprocessed contents of the XML data island.</span></span>  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="99c47-116">测试此示例</span><span class="sxs-lookup"><span data-stu-id="99c47-116">To test this example</span></span>  
  
1.  <span data-ttu-id="99c47-117">验证是否安装了 IIS 以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="99c47-117">Verify that IIS is installed and that the AdventureWorks sample database for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been installed.</span></span>  
  
     <span data-ttu-id="99c47-118">此示例需要安装 Internet Information Services (IIS) 5.0 版或更高版本并启用 ASP 支持。</span><span class="sxs-lookup"><span data-stu-id="99c47-118">This example requires that Internet Information Services (IIS) version 5.0, or later versions, are installed with ASP support enabled.</span></span> <span data-ttu-id="99c47-119">此外，必须安装 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="99c47-119">Also, the AdventureWorks sample database has to be installed.</span></span>  
  
2.  <span data-ttu-id="99c47-120">复制以前提供的代码示例，并将其粘贴到您使用的 XML 或文本编辑器中。</span><span class="sxs-lookup"><span data-stu-id="99c47-120">Copy the code example that was previously provided and paste it into the XML or text editor that you use.</span></span> <span data-ttu-id="99c47-121">在 IIS 所使用的根目录中将文件另存为 RetrieveResults.asp。</span><span class="sxs-lookup"><span data-stu-id="99c47-121">Save the file as RetrieveResults.asp in the root directory that is used for IIS.</span></span> <span data-ttu-id="99c47-122">此目录通常为 C:Inetpub\wwwroot。</span><span class="sxs-lookup"><span data-stu-id="99c47-122">Typically, this is C:Inetpub\wwwroot.</span></span>  
  
3.  <span data-ttu-id="99c47-123">使用以下 URL 在浏览器窗口中打开 ASP 页。</span><span class="sxs-lookup"><span data-stu-id="99c47-123">Open the ASP page in a browser window by using the following URL.</span></span> <span data-ttu-id="99c47-124">首先，将“MyServer”替换为“localhost”或安装了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 IIS 的服务器的实际名称。</span><span class="sxs-lookup"><span data-stu-id="99c47-124">First, replace 'MyServer' with either "localhost" or the actual name of the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and IIS are installed.</span></span>  
  
    ```  
    http://MyServer/RetrieveResults.asp  
    ```  
  
 <span data-ttu-id="99c47-125">您所看到的生成的 HTML 页结果与以下示例输出类似：</span><span class="sxs-lookup"><span data-stu-id="99c47-125">The generated HTML page results that appear will be similar to the following sample output:</span></span>  
  
##### <a name="server-side-processing"></a><span data-ttu-id="99c47-126">服务器端处理</span><span class="sxs-lookup"><span data-stu-id="99c47-126">Server-side processing</span></span>  
 <span data-ttu-id="99c47-127">Page Generated \@ 3/11/2006 3:36:02 PM</span><span class="sxs-lookup"><span data-stu-id="99c47-127">Page Generated \@ 3/11/2006 3:36:02 PM</span></span>  
  
 <span data-ttu-id="99c47-128">Connect String = Provider=SQLOLEDB;Data Source=MyServer;Initial Catalog=AdventureWorks;Integrated Security=SSPI；</span><span class="sxs-lookup"><span data-stu-id="99c47-128">Connect String = Provider=SQLOLEDB;Data Source=MyServer;Initial Catalog=AdventureWorks;Integrated Security=SSPI;</span></span>  
  
 <span data-ttu-id="99c47-129">ADO Version = 2.8</span><span class="sxs-lookup"><span data-stu-id="99c47-129">ADO Version = 2.8</span></span>  
  
 <span data-ttu-id="99c47-130">adoConn.State = 1</span><span class="sxs-lookup"><span data-stu-id="99c47-130">adoConn.State = 1</span></span>  
  
 <span data-ttu-id="99c47-131">Query String = SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</span><span class="sxs-lookup"><span data-stu-id="99c47-131">Query String = SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</span></span>  
  
 <span data-ttu-id="99c47-132">将 XML 推送到客户端进行处理</span><span class="sxs-lookup"><span data-stu-id="99c47-132">Pushing XML to client for processing</span></span>  
  
##### <a name="client-side-processing-of-xml-document-mydataisle"></a><span data-ttu-id="99c47-133">XML 文档 MyDataIsle 的客户端处理</span><span class="sxs-lookup"><span data-stu-id="99c47-133">Client-side processing of XML Document MyDataIsle</span></span>  
  
-   <span data-ttu-id="99c47-134">**AnnualSales：** 1500000</span><span class="sxs-lookup"><span data-stu-id="99c47-134">**AnnualSales:** 1500000</span></span>  
  
-   <span data-ttu-id="99c47-135">**AnnualRevenue：** 150000</span><span class="sxs-lookup"><span data-stu-id="99c47-135">**AnnualRevenue:** 150000</span></span>  
  
-   <span data-ttu-id="99c47-136">**BankName：** Primary International</span><span class="sxs-lookup"><span data-stu-id="99c47-136">**BankName:** Primary International</span></span>  
  
-   <span data-ttu-id="99c47-137">**BusinessType：** OS</span><span class="sxs-lookup"><span data-stu-id="99c47-137">**BusinessType:** OS</span></span>  
  
-   <span data-ttu-id="99c47-138">**YearOpened：** 1974</span><span class="sxs-lookup"><span data-stu-id="99c47-138">**YearOpened:** 1974</span></span>  
  
-   <span data-ttu-id="99c47-139">**Specialty：** 道路</span><span class="sxs-lookup"><span data-stu-id="99c47-139">**Specialty:** Road</span></span>  
  
-   <span data-ttu-id="99c47-140">**SquareFeet：** 38000</span><span class="sxs-lookup"><span data-stu-id="99c47-140">**SquareFeet:** 38000</span></span>  
  
-   <span data-ttu-id="99c47-141">**Brands：** 3</span><span class="sxs-lookup"><span data-stu-id="99c47-141">**Brands:** 3</span></span>  
  
-   <span data-ttu-id="99c47-142">**Internet：** DSL</span><span class="sxs-lookup"><span data-stu-id="99c47-142">**Internet:** DSL</span></span>  
  
-   <span data-ttu-id="99c47-143">**NumberEmployees：** 40</span><span class="sxs-lookup"><span data-stu-id="99c47-143">**NumberEmployees:** 40</span></span>  
  
 <span data-ttu-id="99c47-144">然后，VBScript 消息框将显示以下由 FOR XML 查询结果返回的原始、未筛选的 XML 数据岛内容。</span><span class="sxs-lookup"><span data-stu-id="99c47-144">The VBScript message box will then show the following original, unfiltered XML data island contents that were returned by the FOR XML query results.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Sales.Store>  
    <Demographics>  
      <StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
        <AnnualSales>1500000</AnnualSales>  
        <AnnualRevenue>150000</AnnualRevenue>  
        <BankName>Primary International</BankName>  
        <BusinessType>OS</BusinessType>  
        <YearOpened>1974</YearOpened>  
        <Specialty>Road</Specialty>  
        <SquareFeet>38000</SquareFeet>  
        <Brands>3</Brands>  
        <Internet>DSL</Internet>  
        <NumberEmployees>40</NumberEmployees>  
      </StoreSurvey>  
    </Demographics>  
  </Sales.Store>  
</ROOT>  
```  
  
## <a name="retrieving-for-xml-data-with-aspnet-and-the-net-framework"></a><span data-ttu-id="99c47-145">用 ASP.NET 和 .NET Framework 检索 FOR XML 数据</span><span class="sxs-lookup"><span data-stu-id="99c47-145">Retrieving FOR XML Data with ASP.NET and the .NET Framework</span></span>  
 <span data-ttu-id="99c47-146">与上一个示例一样，以下 ASP.NET 代码显示在 AdventureWorks 示例数据库的 Sales.Store 表中查询 `xml` 数据类型列 Demographics 的结果。</span><span class="sxs-lookup"><span data-stu-id="99c47-146">As in the previous example, the following ASP.NET code shows the results of querying an `xml` data type column, Demographics, in the Sales.Store table of the AdventureWorks sample database.</span></span> <span data-ttu-id="99c47-147">同样与上一个示例相似，该查询在 CustomerID 等于 3 的行中查找此列的实例值。</span><span class="sxs-lookup"><span data-stu-id="99c47-147">As in the previous example, the query looks for the instance value of this column for the row where the CustomerID is equal to 3.</span></span>  
  
 <span data-ttu-id="99c47-148">在此示例中，以下 Microsoft .NET Framework 托管 API 用于完成返回并呈现 FOR XML 查询结果：</span><span class="sxs-lookup"><span data-stu-id="99c47-148">In this example, the following Microsoft .NET Framework managed APIs are used to accomplish the return and rendering of the FOR XML query results:</span></span>  
  
1.  <span data-ttu-id="99c47-149">`SqlConnection` 用于根据指定的连接字符串变量 strConn 的内容连接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="99c47-149">`SqlConnection` is used to open a connection to SQL Server, based on the contents of a specified connection string variable, strConn.</span></span>  
  
2.  <span data-ttu-id="99c47-150">然后，将 `SqlDataAdapter` 用作数据适配器，它将使用 SQL 连接和指定的 SQL 查询字符串执行 FOR XML 查询。</span><span class="sxs-lookup"><span data-stu-id="99c47-150">`SqlDataAdapter` is then used as the data adapter and it uses the SQL connection and a specified SQL query string to execute the FOR XML query.</span></span>  
  
3.  <span data-ttu-id="99c47-151">执行查询后，为了用 FOR XML 查询的输出填充数据集，将调用 `SqlDataAdapter.Fill` 方法并传递一个 `DataSet,` (MyDataSet) 实例。</span><span class="sxs-lookup"><span data-stu-id="99c47-151">After the query has executed, the `SqlDataAdapter.Fill` method is then called and passed an instance of a `DataSet,` MyDataSet, in order to fill the data set with the output of the FOR XML query.</span></span>  
  
4.  <span data-ttu-id="99c47-152">然后，调用 `DataSet.GetXml` 方法将查询结果作为可以在服务器生成的 HTML 页中显示的字符串返回。</span><span class="sxs-lookup"><span data-stu-id="99c47-152">The `DataSet.GetXml` method is then called to return the query results as a string that can be displayed in the server-generated HTML page.</span></span>  
  
    ```  
    <%@ Page Language="VB" %>  
    <HTML>  
    <HEAD>  
    <TITLE>FOR XML Query Example</TITLE>  
    <STYLE>  
       BODY  
       {  
          FONT-FAMILY: Tahoma;  
          FONT-SIZE: 8pt;  
          OVERFLOW: auto  
       }  
       H3  
       {  
          FONT-FAMILY: Tahoma;  
          FONT-SIZE: 8pt;  
          OVERFLOW: auto  
       }  
    </STYLE>  
    </HEAD>  
    <BODY>  
    <%  
    Dim s as String  
    s = "<H3>Server-side processing</H3>" & _  
        "Page Generated @ " & Now() & "<BR/>"  
  
    Dim SQL As String   
    SQL = "SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO"  
  
    Dim strConn As String   
    strConn = "Server=(local);Database=AdventureWorks;Integrated Security=SSPI;"  
  
    Dim MySqlConn As New System.Data.SqlClient.SqlConnection(strConn)  
    Dim MySqlAdapter As New System.Data.SqlClient.SqlDataAdapter(SQL,MySqlConn)  
    Dim MyDataSet As New System.Data.DataSet  
  
    MySqlConn.Open()  
    s = s & "<P>SqlConnection opened.</P>"   
  
    MySqlAdapter.Fill(MyDataSet)  
    s = s & "<P>" & MyDataSet.GetXml  & "</P>"  
  
    MySqlConn.Close()  
    s = s & "<P>SqlConnection closed.</P>"   
  
    Message.InnerHtml=s  
    %>  
    <SPAN id="Message" runat=server />  
    </BODY>  
    </HTML>  
    ```  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="99c47-153">测试此示例</span><span class="sxs-lookup"><span data-stu-id="99c47-153">To test this example</span></span>  
  
1.  <span data-ttu-id="99c47-154">验证是否安装了 IIS 以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="99c47-154">Verify that IIS is installed and that the AdventureWorks sample database for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been installed.</span></span>  
  
     <span data-ttu-id="99c47-155">此示例需要安装 Internet Information Services (IIS) 5.0 版或更高版本并启用 ASP.NET 支持。</span><span class="sxs-lookup"><span data-stu-id="99c47-155">This example requires that Internet Information Services (IIS) version 5.0, or later versions, are installed with ASP.NET support enabled.</span></span> <span data-ttu-id="99c47-156">此外，必须安装 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="99c47-156">Also, the AdventureWorks sample database has to be installed.</span></span>  
  
2.  <span data-ttu-id="99c47-157">复制以前提供的代码，并将其粘贴到您使用的 XML 或文本编辑器中。</span><span class="sxs-lookup"><span data-stu-id="99c47-157">Copy the code that was previously provided and paste it into the XML or text editor that you use.</span></span> <span data-ttu-id="99c47-158">在 IIS 所使用的根目录中将文件另存为 RetrieveResults.aspx。</span><span class="sxs-lookup"><span data-stu-id="99c47-158">Save the file as RetrieveResults.aspx in the root directory used for IIS.</span></span> <span data-ttu-id="99c47-159">此目录通常为 C:Inetpub\wwwroot。</span><span class="sxs-lookup"><span data-stu-id="99c47-159">Typically, this is C:Inetpub\wwwroot.</span></span>  
  
3.  <span data-ttu-id="99c47-160">使用以下 URL 在浏览器窗口中打开 ASP.NET 页。</span><span class="sxs-lookup"><span data-stu-id="99c47-160">Open the ASP.NET page in a browser window using the following URL.</span></span> <span data-ttu-id="99c47-161">首先，将“MyServer”替换为“localhost”或安装了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 IIS 的服务器的实际名称。</span><span class="sxs-lookup"><span data-stu-id="99c47-161">First, replace 'MyServer' with either "localhost" or the actual name of the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and IIS are installed.</span></span>  
  
    ```  
    http://MyServer/RetrieveResults.aspx  
    ```  
  
 <span data-ttu-id="99c47-162">您所看到的生成的 HTML 页结果与以下示例输出类似：</span><span class="sxs-lookup"><span data-stu-id="99c47-162">The generated HTML page results that appear will be similar to the following sample output:</span></span>  
  
##### <a name="server-side-processing"></a><span data-ttu-id="99c47-163">服务器端处理</span><span class="sxs-lookup"><span data-stu-id="99c47-163">Server-side processing</span></span>  
  
```  
Page Generated @ 3/11/2006 3:36:02 PM  
  
SqlConnection opened.  
  
<Sales.Store><Demographics><StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey"><AnnualSales>1500000</AnnualSales><AnnualRevenue>150000</AnnualRevenue><BankName>Primary International</BankName><BusinessType>OS</BusinessType><YearOpened>1974</YearOpened><Specialty>Road</Specialty><SquareFeet>38000</SquareFeet><Brands>3</Brands><Internet>DSL</Internet><NumberEmployees>40</NumberEmployees></StoreSurvey></Demographics></Sales.Store>  
  
SqlConnection closed.  
```  
  
> [!NOTE]  
>  <span data-ttu-id="99c47-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `xml` 通过数据类型支持，你可以通过指定 type 指令请求将 FOR XML 查询的结果作为 `xml` 数据类型返回，而不是作为字符串或图像类型化数据[TYPE directive](type-directive-in-for-xml-queries.md)返回。</span><span class="sxs-lookup"><span data-stu-id="99c47-164">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`xml` data type support lets you request that the result of a FOR XML query be returned as `xml` data type, instead of as string or image typed data, by specifying the [TYPE directive](type-directive-in-for-xml-queries.md).</span></span> <span data-ttu-id="99c47-165">在 FOR XML 查询中使用 TYPE 指令时，该指令将提供对 FOR XML 结果（与 [在应用程序中使用 XML 数据](use-xml-data-in-applications.md)中显示的结果类似）的编程访问权限。</span><span class="sxs-lookup"><span data-stu-id="99c47-165">When the TYPE directive is used in FOR XML queries, it provides programmatic access to the FOR XML results similar to that shown in [Use XML Data in Applications](use-xml-data-in-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c47-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99c47-166">See Also</span></span>  
 [<span data-ttu-id="99c47-167">FOR XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="99c47-167">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
