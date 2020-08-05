---
title: 以编程方式添加连接 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- connection managers [Integration Services], packages
- Integration Services packages, connections
- connections [Integration Services], packages
- SSIS packages, connections
- packages [Integration Services], connections
- intrinsic properties [Integration Services]
- SQL Server Integration Services packages, connections
- ConnectionManager class
- SSIS connection managers
- adding package connections
ms.assetid: d90716d1-4c65-466c-b82c-4aabbee1e3e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5952221dbf2689d2328695baf965ce884dc07fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580846"
---
# <a name="adding-connections-programmatically"></a><span data-ttu-id="77e84-102">以编程方式添加连接</span><span class="sxs-lookup"><span data-stu-id="77e84-102">Adding Connections Programmatically</span></span>
  <span data-ttu-id="77e84-103"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 类表示与外部数据源的物理连接。</span><span class="sxs-lookup"><span data-stu-id="77e84-103">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class represents physical connections to external data sources.</span></span> <span data-ttu-id="77e84-104"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 类可将连接的实现细节与运行时隔离。</span><span class="sxs-lookup"><span data-stu-id="77e84-104">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class isolates the implementation details of the connection from the runtime.</span></span> <span data-ttu-id="77e84-105">这可使运行时以一致且可预测的方式与每个连接管理器进行交互。</span><span class="sxs-lookup"><span data-stu-id="77e84-105">This enables the runtime to interact with each connection manager in a consistent and predictable manner.</span></span> <span data-ttu-id="77e84-106">连接管理器包含一组所有连接通用的常用属性，如 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ID%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="77e84-106">Connection managers contain a set of stock properties that all connections have in common, such as the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ID%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>.</span></span> <span data-ttu-id="77e84-107">但是，通常配置连接管理器只需 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="77e84-107">However, the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> properties are ordinarily the only properties required to configure a connection manager.</span></span> <span data-ttu-id="77e84-108">在其他编程范例中，连接类会提供一些方法（如 `Open` 或 `Connect`）以物理方式建立与数据源的连接，而不同的是，运行时引擎会在包运行时管理包的所有连接。</span><span class="sxs-lookup"><span data-stu-id="77e84-108">Unlike other programming paradigms, where connection classes expose methods such as `Open` or `Connect` to physically establish a connection to the data source, the run-time engine manages all the connections for the package while it runs.</span></span>  
  
 <span data-ttu-id="77e84-109"><xref:Microsoft.SqlServer.Dts.Runtime.Connections> 类是一个已添加到该包并且可在运行时使用的连接管理器的集合。</span><span class="sxs-lookup"><span data-stu-id="77e84-109">The <xref:Microsoft.SqlServer.Dts.Runtime.Connections> class is a collection of the connection managers that have been added to that package and are available for use at run time.</span></span> <span data-ttu-id="77e84-110">可以使用该集合的 <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> 方法，并提供一个用于指示连接管理器类型的字符串，以向该集合添加更多的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-110">You can add more connection managers to the collection by using the <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> method of the collection, and supplying a string that indicates the connection manager type.</span></span> <span data-ttu-id="77e84-111"><xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> 方法返回已添加到该包的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 实例。</span><span class="sxs-lookup"><span data-stu-id="77e84-111">The <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> method returns the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> instance that was added to the package.</span></span>  
  
## <a name="intrinsic-properties"></a><span data-ttu-id="77e84-112">内部属性</span><span class="sxs-lookup"><span data-stu-id="77e84-112">Intrinsic Properties</span></span>  
 <span data-ttu-id="77e84-113"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 类公开一组所有连接通用的属性。</span><span class="sxs-lookup"><span data-stu-id="77e84-113">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class exposes a set of properties that are common to all connections.</span></span> <span data-ttu-id="77e84-114">但是，有时您需要访问特定连接类型特有的属性。</span><span class="sxs-lookup"><span data-stu-id="77e84-114">However, sometimes you need access to properties that are unique to the specific connection type.</span></span> <span data-ttu-id="77e84-115"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Properties%2A> 类的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 集合提供对这些属性的访问。</span><span class="sxs-lookup"><span data-stu-id="77e84-115">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Properties%2A> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class provides access to these properties.</span></span> <span data-ttu-id="77e84-116">可以使用索引器或属性名称以及 GetValue 方法从集合检索这些属性，并使用 SetValue 方法设置属性的值   。</span><span class="sxs-lookup"><span data-stu-id="77e84-116">The properties can be retrieved from the collection using the indexer or the property name and the **GetValue** method, and the values are set using the **SetValue** method.</span></span> <span data-ttu-id="77e84-117">设置基础连接对象属性的属性的另一种方法是：获取该对象的实际实例并直接设置其属性。</span><span class="sxs-lookup"><span data-stu-id="77e84-117">The properties of the underlying connection object properties can also be set by acquiring an actual instance of the object and setting its properties directly.</span></span> <span data-ttu-id="77e84-118">若要获取基础连接，请使用连接管理器的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.InnerObject%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="77e84-118">To get the underlying connection, use the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.InnerObject%2A> property of the connection manager.</span></span> <span data-ttu-id="77e84-119">下面的代码行显示了一行 C# 代码，该代码行创建一个具有基础类 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.ConnectionManagerAdoNetClass> 的 ADO.NET 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-119">The following line of code shows a C# line that creates an ADO.NET connection manager that has the underlying class, <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.ConnectionManagerAdoNetClass>.</span></span>  
  
 `ConnectionManagerAdoNetClass cmado = cm.InnerObject as ConnectionManagerAdoNet;`  
  
 <span data-ttu-id="77e84-120">这可将托管连接管理器对象转换为其基础连接对象。</span><span class="sxs-lookup"><span data-stu-id="77e84-120">This casts the managed connection manager object to its underlying connection object.</span></span> <span data-ttu-id="77e84-121">如果您使用的是 C++，则需要调用 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 对象的 `QueryInterface` 方法，并请求基础连接对象的接口。</span><span class="sxs-lookup"><span data-stu-id="77e84-121">If you are using C++, the `QueryInterface` method of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object is called and the interface of the underlying connection object is requested.</span></span>  
  
 <span data-ttu-id="77e84-122">下表列出了随 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-122">The following table lists the connection managers included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="77e84-123">此外，还有 `package.Connections.Add("xxx")` 语句中使用的字符串。</span><span class="sxs-lookup"><span data-stu-id="77e84-123">and the string that is used in the `package.Connections.Add("xxx")` statement.</span></span> <span data-ttu-id="77e84-124">若要获取所有连接管理器的列表，请参阅 [Integration Services (SSIS) 连接](../connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="77e84-124">For a list of all connection managers, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
|<span data-ttu-id="77e84-125">String</span><span class="sxs-lookup"><span data-stu-id="77e84-125">String</span></span>|<span data-ttu-id="77e84-126">“ODBC 源编辑器”</span><span class="sxs-lookup"><span data-stu-id="77e84-126">Connection manager</span></span>|  
|------------|------------------------|  
|<span data-ttu-id="77e84-127">"OLEDB"</span><span class="sxs-lookup"><span data-stu-id="77e84-127">"OLEDB"</span></span>|<span data-ttu-id="77e84-128">OLE DB 连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-128">Connection manager for OLE DB connections.</span></span>|  
|<span data-ttu-id="77e84-129">"ODBC"</span><span class="sxs-lookup"><span data-stu-id="77e84-129">"ODBC"</span></span>|<span data-ttu-id="77e84-130">ODBC 连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-130">Connection manager for ODBC connections.</span></span>|  
|<span data-ttu-id="77e84-131">"ADO"</span><span class="sxs-lookup"><span data-stu-id="77e84-131">"ADO"</span></span>|<span data-ttu-id="77e84-132">ADO 连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-132">Connection manager for ADO connections.</span></span>|  
|<span data-ttu-id="77e84-133">"ADO.NET:SQL"</span><span class="sxs-lookup"><span data-stu-id="77e84-133">"ADO.NET:SQL"</span></span>|<span data-ttu-id="77e84-134">ADO.NET（SQL 数据访问接口）连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-134">Connection manager for ADO.NET (SQL data provider) connections.</span></span>|  
|<span data-ttu-id="77e84-135">"ADO.NET:OLEDB"</span><span class="sxs-lookup"><span data-stu-id="77e84-135">"ADO.NET:OLEDB"</span></span>|<span data-ttu-id="77e84-136">ADO.NET（OLE DB 数据访问接口）连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-136">Connection manager for ADO.NET (OLE DB data provider) connections.</span></span>|  
|<span data-ttu-id="77e84-137">"FLATFILE"</span><span class="sxs-lookup"><span data-stu-id="77e84-137">"FLATFILE"</span></span>|<span data-ttu-id="77e84-138">平面文件连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-138">Connection manager for flat file connections.</span></span>|  
|<span data-ttu-id="77e84-139">"FILE"</span><span class="sxs-lookup"><span data-stu-id="77e84-139">"FILE"</span></span>|<span data-ttu-id="77e84-140">文件连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-140">Connection manager for file connections.</span></span>|  
|<span data-ttu-id="77e84-141">"MULTIFLATFILE"</span><span class="sxs-lookup"><span data-stu-id="77e84-141">"MULTIFLATFILE"</span></span>|<span data-ttu-id="77e84-142">多平面文件连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-142">Connection manager for multiple flat file connections.</span></span>|  
|<span data-ttu-id="77e84-143">"MULTIFILE"</span><span class="sxs-lookup"><span data-stu-id="77e84-143">"MULTIFILE"</span></span>|<span data-ttu-id="77e84-144">多文件连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-144">Connection manager for multiple file connections.</span></span>|  
|<span data-ttu-id="77e84-145">"SQLMOBILE"</span><span class="sxs-lookup"><span data-stu-id="77e84-145">"SQLMOBILE"</span></span>|<span data-ttu-id="77e84-146">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-146">Connection manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connections.</span></span>|  
|<span data-ttu-id="77e84-147">"MSOLAP100"</span><span class="sxs-lookup"><span data-stu-id="77e84-147">"MSOLAP100"</span></span>|<span data-ttu-id="77e84-148">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-148">Connection manager for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connections.</span></span>|  
|<span data-ttu-id="77e84-149">"FTP"</span><span class="sxs-lookup"><span data-stu-id="77e84-149">"FTP"</span></span>|<span data-ttu-id="77e84-150">FTP 连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-150">Connection manager for FTP connections.</span></span>|  
|<span data-ttu-id="77e84-151">"HTTP"</span><span class="sxs-lookup"><span data-stu-id="77e84-151">"HTTP"</span></span>|<span data-ttu-id="77e84-152">HTTP 连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-152">Connection manager for HTTP connections.</span></span>|  
|<span data-ttu-id="77e84-153">"MSMQ"</span><span class="sxs-lookup"><span data-stu-id="77e84-153">"MSMQ"</span></span>|<span data-ttu-id="77e84-154">消息队列（也称为 MSMQ）连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-154">Connection manager for Message Queuing (also known as MSMQ) connections.</span></span>|  
|<span data-ttu-id="77e84-155">"SMTP"</span><span class="sxs-lookup"><span data-stu-id="77e84-155">"SMTP"</span></span>|<span data-ttu-id="77e84-156">SMTP 连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-156">Connection manager for SMTP connections.</span></span>|  
|<span data-ttu-id="77e84-157">"WMI"</span><span class="sxs-lookup"><span data-stu-id="77e84-157">"WMI"</span></span>|<span data-ttu-id="77e84-158">Microsoft Windows Management Instrumentation (WMI) 连接的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="77e84-158">Connection manager for Microsoft Windows Management Instrumentation (WMI) connections.</span></span>|  
  
 <span data-ttu-id="77e84-159">下面的代码示例演示如何向 <xref:Microsoft.SqlServer.Dts.Runtime.Package.Connections%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.Package> 集合添加 OLE DB 和 FILE 连接。</span><span class="sxs-lookup"><span data-stu-id="77e84-159">The following code example demonstrates adding an OLE DB and FILE connection to the <xref:Microsoft.SqlServer.Dts.Runtime.Package.Connections%2A> collection of a <xref:Microsoft.SqlServer.Dts.Runtime.Package>.</span></span> <span data-ttu-id="77e84-160">然后，该示例还设置了 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="77e84-160">The example then sets the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> properties.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      // Create a package, and retrieve its connections.  
      Package pkg = new Package();  
      Connections pkgConns = pkg.Connections;  
  
      // Add an OLE DB connection to the package, using the   
      // method defined in the AddConnection class.  
      CreateConnection myOLEDBConn = new CreateConnection();  
      myOLEDBConn.CreateOLEDBConnection(pkg);  
  
      // View the new connection in the package.  
      Console.WriteLine("Connection description: {0}",  
         pkg.Connections["SSIS Connection Manager for OLE DB"].Description);  
  
      // Add a second connection to the package.  
      CreateConnection myFileConn = new CreateConnection();  
      myFileConn.CreateFileConnection(pkg);  
  
      // View the second connection in the package.  
      Console.WriteLine("Connection description: {0}",  
        pkg.Connections["SSIS Connection Manager for Files"].Description);  
  
      Console.WriteLine();  
      Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count);  
  
      Console.Read();  
    }  
  }  
  // <summary>  
  // This class contains the definitions for multiple  
  // connection managers.  
  // </summary>  
  public class CreateConnection  
  {  
    // Private data.  
    private ConnectionManager ConMgr;  
  
    // Class definition for OLE DB Provider.  
    public void CreateOLEDBConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("OLEDB");  
      ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" +  
        "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" +  
        "Data Source=(local);";  
      ConMgr.Name = "SSIS Connection Manager for OLE DB";  
      ConMgr.Description = "OLE DB connection to the AdventureWorks database.";  
    }  
    public void CreateFileConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("File");  
      ConMgr.ConnectionString = @"\\<yourserver>\<yourfolder>\books.xml";  
      ConMgr.Name = "SSIS Connection Manager for Files";  
      ConMgr.Description = "Flat File connection";  
    }  
  }  
  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    ' Create a package, and retrieve its connections.  
    Dim pkg As New Package()  
    Dim pkgConns As Connections = pkg.Connections  
  
    ' Add an OLE DB connection to the package, using the   
    ' method defined in the AddConnection class.  
    Dim myOLEDBConn As New CreateConnection()  
    myOLEDBConn.CreateOLEDBConnection(pkg)  
  
    ' View the new connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for OLE DB").Description)  
  
    ' Add a second connection to the package.  
    Dim myFileConn As New CreateConnection()  
    myFileConn.CreateFileConnection(pkg)  
  
    ' View the second connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for Files").Description)  
  
    Console.WriteLine()  
    Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count)  
  
    Console.Read()  
  
  End Sub  
  
End Module  
  
' This class contains the definitions for multiple  
' connection managers.  
  
Public Class CreateConnection  
  ' Private data.  
  Private ConMgr As ConnectionManager  
  
  ' Class definition for OLE DB provider.  
  Public Sub CreateOLEDBConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("OLEDB")  
    ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" & _  
      "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" & _  
      "Data Source=(local);"  
    ConMgr.Name = "SSIS Connection Manager for OLE DB"  
    ConMgr.Description = "OLE DB connection to the AdventureWorks database."  
  End Sub  
  
  Public Sub CreateFileConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("File")  
    ConMgr.ConnectionString = "\\<yourserver>\<yourfolder>\books.xml"  
    ConMgr.Name = "SSIS Connection Manager for Files"  
    ConMgr.Description = "Flat File connection"  
  End Sub  
  
End Class  
```  
  
 <span data-ttu-id="77e84-161">**示例输出：**</span><span class="sxs-lookup"><span data-stu-id="77e84-161">**Sample Output:**</span></span>  
  
 `Connection description: OLE DB connection to the AdventureWorks database.`  
  
 `Connection description: OLE DB connection to the AdventureWorks database.`  
  
 `Number of connections in package: 2`  
  
## <a name="external-resources"></a><span data-ttu-id="77e84-162">外部资源</span><span class="sxs-lookup"><span data-stu-id="77e84-162">External Resources</span></span>  
 <span data-ttu-id="77e84-163">carlprothman.net 上的技术文章 [Connection Strings](https://go.microsoft.com/fwlink/?LinkId=220743)（连接字符串）。</span><span class="sxs-lookup"><span data-stu-id="77e84-163">Technical article, [Connection Strings](https://go.microsoft.com/fwlink/?LinkId=220743), on carlprothman.net.</span></span>  
  
<span data-ttu-id="77e84-164">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="77e84-164">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="77e84-165">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="77e84-165">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="77e84-166">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="77e84-166">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="77e84-167">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="77e84-167">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e84-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77e84-168">See Also</span></span>  
 <span data-ttu-id="77e84-169">[Integration Services &#40;SSIS&#41; 连接](../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="77e84-169">[Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="77e84-170">创建连接管理器</span><span class="sxs-lookup"><span data-stu-id="77e84-170">Create Connection Managers</span></span>](../create-connection-managers.md)  
  
  
