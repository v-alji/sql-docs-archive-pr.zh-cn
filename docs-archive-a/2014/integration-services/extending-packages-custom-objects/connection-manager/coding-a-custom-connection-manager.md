---
title: 编写自定义连接管理器代码 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], coding
ms.assetid: b12b6778-1f01-4a7d-984d-73f2f7630aa5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 793d70ba0a9ae6176ab35c82e16b9aba8c9ba2cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691808"
---
# <a name="coding-a-custom-connection-manager"></a><span data-ttu-id="6a5e4-102">编写自定义连接管理器代码</span><span class="sxs-lookup"><span data-stu-id="6a5e4-102">Coding a Custom Connection Manager</span></span>
  <span data-ttu-id="6a5e4-103">创建继承自 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基类的类并将 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 属性应用于该类后，必须重写基类的属性和方法的实现以提供自定义功能。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-103">After you have created a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>  
  
 <span data-ttu-id="6a5e4-104">有关自定义连接管理器的示例，请参阅[为自定义连接管理器开发用户界面](developing-a-user-interface-for-a-custom-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-104">For samples of custom connection managers, see [Developing a User Interface for a Custom Connection Manager](developing-a-user-interface-for-a-custom-connection-manager.md).</span></span> <span data-ttu-id="6a5e4-105">本主题中演示的代码示例来自 SQL Server 自定义连接管理器示例。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-105">The code examples shown in this topic are drawn from the SQL Server Custom Connection Manager sample.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6a5e4-106">内置于 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 的大多数任务、源和目标都只能与特定类型的内置连接管理器一起工作。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-106">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="6a5e4-107">因此，不能使用内置任务和组件测试这些示例。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-107">Therefore, these samples cannot be tested with the built-in tasks and components.</span></span>  
  
## <a name="configuring-the-connection-manager"></a><span data-ttu-id="6a5e4-108">配置连接管理器</span><span class="sxs-lookup"><span data-stu-id="6a5e4-108">Configuring the Connection Manager</span></span>  
  
### <a name="setting-the-connectionstring-property"></a><span data-ttu-id="6a5e4-109">设置 ConnectionString 属性</span><span class="sxs-lookup"><span data-stu-id="6a5e4-109">Setting the ConnectionString Property</span></span>  
 <span data-ttu-id="6a5e4-110"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 属性是一个重要的属性，并且是自定义连接管理器独有且唯一的属性。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-110">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property is an important property and the only property unique to a custom connection manager.</span></span> <span data-ttu-id="6a5e4-111">连接管理器使用此属性的值连接到外部数据源。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-111">The connection manager uses the value of this property to connect to the external data source.</span></span> <span data-ttu-id="6a5e4-112">如果组合多个其他属性（如服务器名称和数据库名称）来创建连接字符串，则可以使用 Helper 函数来组合字符串，方法是使用用户提供的新值来替换连接字符串模板中的某些值。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-112">If you are combining several other properties, such as server name and database name, to create the connection string, you can use a helper function to assemble the string by replacing certain values in a connection string template with the new value supplied by the user.</span></span> <span data-ttu-id="6a5e4-113">下面的代码示例演示了 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 属性的实现，该属性依赖 Helper 函数来组合字符串。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-113">The following code example shows an implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property that relies on a helper function to assemble the string.</span></span>  
  
```vb  
' Default values.  
Private _serverName As String = "(local)"  
Private _databaseName As String = "AdventureWorks"  
Private _connectionString As String = String.Empty  
  
Private Const CONNECTIONSTRING_TEMPLATE As String = _  
  "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI"  
  
Public Property ServerName() As String  
  Get  
    Return _serverName  
  End Get  
  Set(ByVal value As String)  
    _serverName = value  
  End Set  
End Property  
  
Public Property DatabaseName() As String  
  Get  
    Return _databaseName  
  End Get  
  Set(ByVal value As String)  
    _databaseName = value  
  End Set  
End Property  
  
Public Overrides Property ConnectionString() As String  
  Get  
    UpdateConnectionString()  
    Return _connectionString  
  End Get  
  Set(ByVal value As String)  
    _connectionString = value  
  End Set  
End Property  
  
Private Sub UpdateConnectionString()  
  
  Dim temporaryString As String = CONNECTIONSTRING_TEMPLATE  
  
  If Not String.IsNullOrEmpty(_serverName) Then  
    temporaryString = temporaryString.Replace("<servername>", _serverName)  
  End If  
  If Not String.IsNullOrEmpty(_databaseName) Then  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName)  
  End If  
  
  _connectionString = temporaryString  
  
End Sub  
```  
  
```csharp  
// Default values.  
private string _serverName = "(local)";  
private string _databaseName = "AdventureWorks";  
private string _connectionString = String.Empty;  
  
private const string CONNECTIONSTRING_TEMPLATE = "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI";  
  
public string ServerName  
{  
  get  
  {  
    return _serverName;  
  }  
  set  
  {  
    _serverName = value;  
  }  
}  
  
public string DatabaseName  
{  
  get  
  {  
    return _databaseName;  
  }  
  set  
  {  
    _databaseName = value;  
  }  
}  
  
public override string ConnectionString  
{  
  get  
  {  
    UpdateConnectionString();  
    return _connectionString;  
  }  
  set  
  {  
    _connectionString = value;  
  }  
}  
  
private void UpdateConnectionString()  
{  
  
  string temporaryString = CONNECTIONSTRING_TEMPLATE;  
  
  if (!String.IsNullOrEmpty(_serverName))  
  {  
    temporaryString = temporaryString.Replace("<servername>", _serverName);  
  }  
  
  if (!String.IsNullOrEmpty(_databaseName))  
  {  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName);  
  }  
  
  _connectionString = temporaryString;  
  
}  
```  
  
### <a name="validating-the-connection-manager"></a><span data-ttu-id="6a5e4-114">验证连接管理器</span><span class="sxs-lookup"><span data-stu-id="6a5e4-114">Validating the Connection Manager</span></span>  
 <span data-ttu-id="6a5e4-115">重写 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> 方法以确保连接管理器已正确配置。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-115">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> method to make sure that the connection manager has been configured correctly.</span></span> <span data-ttu-id="6a5e4-116">您至少应验证连接字符串的格式并确保已为所有参数提供值。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-116">At a minimum, you should validate the format of the connection string and make sure that values have been provided for all arguments.</span></span> <span data-ttu-id="6a5e4-117">在连接管理器从 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> 方法返回 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> 之前，执行不能继续。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-117">Execution cannot continue until the connection manager returns <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="6a5e4-118">下面的代码示例演示用于确保用户已为连接指定服务器名称的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> 的实现。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-118">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> that makes sure that the user has specified a server name for the connection.</span></span>  
  
```vb  
Public Overrides Function Validate(ByVal infoEvents As Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents) As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  If String.IsNullOrEmpty(_serverName) Then  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0)  
    Return DTSExecResult.Failure  
  Else  
    Return DTSExecResult.Success  
  End If  
  
End Function  
```  
  
```csharp  
public override Microsoft.SqlServer.Dts.Runtime.DTSExecResult Validate(Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents infoEvents)  
{  
  
  if (String.IsNullOrEmpty(_serverName))  
  {  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0);  
    return DTSExecResult.Failure;  
  }  
  else  
  {  
    return DTSExecResult.Success;  
  }  
  
}  
```  
  
### <a name="persisting-the-connection-manager"></a><span data-ttu-id="6a5e4-119">使连接管理器持久化</span><span class="sxs-lookup"><span data-stu-id="6a5e4-119">Persisting the Connection Manager</span></span>  
 <span data-ttu-id="6a5e4-120">通常不需要对连接管理器实现自定义持久性。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-120">Usually, you do not have to implement custom persistence for a connection manager.</span></span> <span data-ttu-id="6a5e4-121">自定义持久性仅在对象的属性使用复杂数据类型时才需要。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-121">Custom persistence is required only when the properties of an object use complex data types.</span></span> <span data-ttu-id="6a5e4-122">有关详细信息，请参阅[开发用于 Integration Services 的自定义对象](../developing-custom-objects-for-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-122">For more information, see [Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md).</span></span>  
  
## <a name="working-with-the-external-data-source"></a><span data-ttu-id="6a5e4-123">使用外部数据源</span><span class="sxs-lookup"><span data-stu-id="6a5e4-123">Working with the External Data Source</span></span>  
 <span data-ttu-id="6a5e4-124">用于支持与外部数据源连接的方法是自定义连接管理器的最重要方法。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-124">The methods that support connecting to an external data source are the most important methods of a custom connection manager.</span></span> <span data-ttu-id="6a5e4-125">会在设计时和运行时期间的不同时间调用 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-125">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> methods are called at various times during both design time and run time.</span></span>  
  
### <a name="acquiring-the-connection"></a><span data-ttu-id="6a5e4-126">获取连接</span><span class="sxs-lookup"><span data-stu-id="6a5e4-126">Acquiring the Connection</span></span>  
 <span data-ttu-id="6a5e4-127">您需要决定哪种类型的对象适合由 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 方法从自定义连接管理器返回。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-127">You need to decide what type of object it is appropriate for the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method to return from your custom connection manager.</span></span> <span data-ttu-id="6a5e4-128">例如，文件连接管理器只返回包含路径和文件名的字符串，而 ADO.NET 连接管理器则返回已打开的托管连接对象。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-128">For example, a File connection manager returns only a string that contains a path and filename, whereas an ADO.NET connection manager returns a managed connection object that is already open.</span></span> <span data-ttu-id="6a5e4-129">OLE DB 连接管理器返回本机 OLE DB 连接对象，这些对象不能从托管代码使用。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-129">An OLE DB connection manager returns a native OLE DB connection object that cannot be used from managed code.</span></span> <span data-ttu-id="6a5e4-130">自定义 SQL Server 连接管理器（从中获取本主题中的代码段）返回打开的 `SqlConnection` 对象。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-130">The custom SQL Server connection manager, from which the code snippets in this topic are taken, returns an open `SqlConnection` object.</span></span>  
  
 <span data-ttu-id="6a5e4-131">连接管理器用户需要事先了解所需的对象类型，以便可以将返回的对象转换为合适的类型并访问其方法和属性。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-131">Users of your connection manager need to know in advance what type of object to expect, so that they can cast the returned object to the appropriate type and access its methods and properties.</span></span>  
  
```vb  
Public Overrides Function AcquireConnection(ByVal txn As Object) As Object  
  
  Dim sqlConnection As New SqlConnection  
  
  UpdateConnectionString()  
  
  With sqlConnection  
    .ConnectionString = _connectionString  
    .Open()  
  End With  
  
  Return sqlConnection  
  
End Function  
```  
  
```csharp  
public override object AcquireConnection(object txn)  
{  
  
  SqlConnection sqlConnection = new SqlConnection();  
  
  UpdateConnectionString();  
  
  {  
    sqlConnection.ConnectionString = _connectionString;  
    sqlConnection.Open();  
  }  
  
  return sqlConnection;  
  
}  
```  
  
### <a name="releasing-the-connection"></a><span data-ttu-id="6a5e4-132">释放连接</span><span class="sxs-lookup"><span data-stu-id="6a5e4-132">Releasing the Connection</span></span>  
 <span data-ttu-id="6a5e4-133"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> 方法中执行的操作取决于从 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 方法返回的对象类型。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-133">The action that you take in the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> method depends on the type of object that you returned from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method.</span></span> <span data-ttu-id="6a5e4-134">如果存在已打开的连接对象，则应将其关闭，并释放该对象所使用的所有资源。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-134">If there is an open connection object, you should close it and to release any resources that it is using.</span></span> <span data-ttu-id="6a5e4-135">如果 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 只返回了一个字符串值，则无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-135">If <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> returned only a string value, no action needs to be taken.</span></span>  
  
```vb  
Public Overrides Sub ReleaseConnection(ByVal connection As Object)  
  
  Dim sqlConnection As SqlConnection  
  
  sqlConnection = DirectCast(connection, SqlConnection)  
  
  If sqlConnection.State <> ConnectionState.Closed Then  
    sqlConnection.Close()  
  End If  
  
End Sub  
```  
  
```csharp  
public override void ReleaseConnection(object connection)  
{  
  SqlConnection sqlConnection;  
  sqlConnection = (SqlConnection)connection;  
  if (sqlConnection.State != ConnectionState.Closed)  
    sqlConnection.Close();  
}  
```  
  
<span data-ttu-id="6a5e4-136">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6a5e4-136">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6a5e4-137">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="6a5e4-137">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6a5e4-138">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="6a5e4-138">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6a5e4-139">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="6a5e4-139">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5e4-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a5e4-140">See Also</span></span>  
 <span data-ttu-id="6a5e4-141">[创建自定义连接管理器](creating-a-custom-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="6a5e4-141">[Creating a Custom Connection Manager](creating-a-custom-connection-manager.md) </span></span>  
 [<span data-ttu-id="6a5e4-142">为自定义连接管理器开发用户界面</span><span class="sxs-lookup"><span data-stu-id="6a5e4-142">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
