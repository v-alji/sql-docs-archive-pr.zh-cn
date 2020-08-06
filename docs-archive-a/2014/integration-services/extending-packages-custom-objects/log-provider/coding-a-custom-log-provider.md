---
title: 编写自定义日志提供程序代码 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom log providers [Integration Services], coding
ms.assetid: 979a29ca-956e-4fdd-ab47-f06e84cead7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5d529420207ac065ae5ecb3c1d984de3021845b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689945"
---
# <a name="coding-a-custom-log-provider"></a><span data-ttu-id="42ed9-102">编写自定义日志提供程序代码</span><span class="sxs-lookup"><span data-stu-id="42ed9-102">Coding a Custom Log Provider</span></span>
  <span data-ttu-id="42ed9-103">创建继承自 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基类的类并将 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 属性应用于该类后，必须重写基类的属性和方法的实现以提供自定义功能。</span><span class="sxs-lookup"><span data-stu-id="42ed9-103">After you have created a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>  
  
 <span data-ttu-id="42ed9-104">有关自定义日志提供程序的工作示例，请参阅[为自定义日志提供程序开发用户界面](developing-a-user-interface-for-a-custom-log-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="42ed9-104">For working samples of custom log providers, see [Developing a User Interface for a Custom Log Provider](developing-a-user-interface-for-a-custom-log-provider.md).</span></span>  
  
## <a name="configuring-the-log-provider"></a><span data-ttu-id="42ed9-105">配置日志提供程序</span><span class="sxs-lookup"><span data-stu-id="42ed9-105">Configuring the Log Provider</span></span>  
  
### <a name="initializing-the-log-provider"></a><span data-ttu-id="42ed9-106">初始化日志提供程序</span><span class="sxs-lookup"><span data-stu-id="42ed9-106">Initializing the Log Provider</span></span>  
 <span data-ttu-id="42ed9-107">重写 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.InitializeLogProvider%2A> 方法以缓存对连接集合和事件接口的引用。</span><span class="sxs-lookup"><span data-stu-id="42ed9-107">You override the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.InitializeLogProvider%2A> method to cache references to the connections collection and the events interface.</span></span> <span data-ttu-id="42ed9-108">可以稍后在日志提供程序的其他方法中使用这些缓存的引用。</span><span class="sxs-lookup"><span data-stu-id="42ed9-108">You can use these cached references later in other methods of the log provider.</span></span>  
  
### <a name="using-the-configstring-property"></a><span data-ttu-id="42ed9-109">使用 ConfigString 属性</span><span class="sxs-lookup"><span data-stu-id="42ed9-109">Using the ConfigString Property</span></span>  
 <span data-ttu-id="42ed9-110">在设计时。日志提供程序从“配置”  列接收配置信息。</span><span class="sxs-lookup"><span data-stu-id="42ed9-110">At design time, a log provider receives configuration information from the **Configuration** column.</span></span> <span data-ttu-id="42ed9-111">此配置信息与日志提供程序的 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 属性对应。</span><span class="sxs-lookup"><span data-stu-id="42ed9-111">This configuration information corresponds to the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property of the log provider.</span></span> <span data-ttu-id="42ed9-112">默认情况下，此列包含一个文本框，您可以从该文本框中检索任何字符串信息。</span><span class="sxs-lookup"><span data-stu-id="42ed9-112">By default, this column contains a text box from which you can retrieve any string information.</span></span> <span data-ttu-id="42ed9-113">随 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 提供的大部分日志提供程序都使用此属性存储连接管理器的名称，以供提供程序连接外部数据源时使用。</span><span class="sxs-lookup"><span data-stu-id="42ed9-113">Most of the log providers included with [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] use this property to store the name of the connection manager that the provider uses to connect to an external data source.</span></span> <span data-ttu-id="42ed9-114">如果日志提供程序使用 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 属性，可使用 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> 方法验证此属性，并确保此属性已正确设置。</span><span class="sxs-lookup"><span data-stu-id="42ed9-114">If your log provider uses the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property, use the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> method to validate this property and make sure that the property is set correctly.</span></span>  
  
### <a name="validating-the-log-provider"></a><span data-ttu-id="42ed9-115">验证日志提供程序</span><span class="sxs-lookup"><span data-stu-id="42ed9-115">Validating the Log Provider</span></span>  
 <span data-ttu-id="42ed9-116">重写 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> 方法以确保提供程序已正确配置并且可以执行。</span><span class="sxs-lookup"><span data-stu-id="42ed9-116">You override the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> method to make sure that the provider has been configured correctly and is ready for execution.</span></span> <span data-ttu-id="42ed9-117">通常，最低级别的验证应确保 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 已正确设置。</span><span class="sxs-lookup"><span data-stu-id="42ed9-117">Typically, a minimum level of validation is to make sure that the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> is set correctly.</span></span> <span data-ttu-id="42ed9-118">在日志提供程序从 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> 方法返回 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> 之前，执行不能继续。</span><span class="sxs-lookup"><span data-stu-id="42ed9-118">Execution cannot continue until the log provider returns <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="42ed9-119">下面的代码示例演示 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> 的实现，它确保连接管理器的名称已指定、连接管理器存在于包中以及连接管理器返回 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 属性中的文件名。</span><span class="sxs-lookup"><span data-stu-id="42ed9-119">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> that makes sure that the name of a connection manager name is specified, that the connection manager exists in the package, and that the connection manager returns a file name in the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property.</span></span>  
  
```csharp  
public override DTSExecResult Validate(IDTSInfoEvents infoEvents)  
{  
    if (this.ConfigString.Length == 0 || connections.Contains(ConfigString) == false)  
    {  
        infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0);  
        return DTSExecResult.Failure;  
    }  
    else  
    {  
        string fileName = connections[ConfigString].AcquireConnection(null) as string;  
  
        if (fileName == null || fileName.Length == 0)  
        {  
            infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0);  
            return DTSExecResult.Failure;  
        }  
    }  
    return DTSExecResult.Success;  
}  
```  
  
```vb  
Public Overrides Function Validate(ByVal infoEvents As IDTSInfoEvents) As DTSExecResult  
    If Me.ConfigString.Length = 0 Or connections.Contains(ConfigString) = False Then  
        infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0)  
        Return DTSExecResult.Failure  
    Else   
        Dim fileName As String =  connections(ConfigString).AcquireConnectionCType(as string, Nothing)  
  
        If fileName = Nothing Or fileName.Length = 0 Then  
            infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0)  
            Return DTSExecResult.Failure  
        End If  
    End If  
    Return DTSExecResult.Success  
End Function  
```  
  
### <a name="persisting-the-log-provider"></a><span data-ttu-id="42ed9-120">使日志提供程序持久化</span><span class="sxs-lookup"><span data-stu-id="42ed9-120">Persisting the Log Provider</span></span>  
 <span data-ttu-id="42ed9-121">通常不需要对连接管理器实现自定义持久性。</span><span class="sxs-lookup"><span data-stu-id="42ed9-121">Ordinarily you do not have to implement custom persistence for a connection manager.</span></span> <span data-ttu-id="42ed9-122">自定义持久性仅在对象的属性使用复杂数据类型时才需要。</span><span class="sxs-lookup"><span data-stu-id="42ed9-122">Custom persistence is required only when the properties of an object use complex data types.</span></span> <span data-ttu-id="42ed9-123">有关详细信息，请参阅[开发用于 Integration Services 的自定义对象](../developing-custom-objects-for-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="42ed9-123">For more information, see [Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md).</span></span>  
  
## <a name="logging-with-the-log-provider"></a><span data-ttu-id="42ed9-124">使用日志提供程序进行日志记录</span><span class="sxs-lookup"><span data-stu-id="42ed9-124">Logging with the Log Provider</span></span>  
 <span data-ttu-id="42ed9-125">有三个所有日志提供程序都必须重写的运行时方法：<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>。</span><span class="sxs-lookup"><span data-stu-id="42ed9-125">There are three run-time methods that must be overridden by all log providers: <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="42ed9-126">在单个包的验证和执行期间，将多次调用 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="42ed9-126">During the validation and execution of a single package, the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> methods are called more than one time.</span></span> <span data-ttu-id="42ed9-127">请确保您的自定义代码不会导致较早的日志条目被下一次打开和关闭日志的操作所覆盖。</span><span class="sxs-lookup"><span data-stu-id="42ed9-127">Make sure that your custom code does not cause earlier log entries to be overwritten by the next opening and closing of the log.</span></span> <span data-ttu-id="42ed9-128">如果已选择在测试包中记录验证事件，则应该看到的第一个记录事件是 OnPreValidate；如果您看到的第一个记录事件是 PackageStart，则表示初始验证事件已被覆盖。</span><span class="sxs-lookup"><span data-stu-id="42ed9-128">If you have selected to log validation events in your test package, the first logged event that you should see is OnPreValidate; if instead the first logged event that you see is PackageStart, the initial validation events have been overwritten.</span></span>  
  
### <a name="opening-the-log"></a><span data-ttu-id="42ed9-129">打开日志</span><span class="sxs-lookup"><span data-stu-id="42ed9-129">Opening the Log</span></span>  
 <span data-ttu-id="42ed9-130">大部分日志提供程序都连接外部数据源，如文件或数据库，以便存储在包执行期间收集的事件信息。</span><span class="sxs-lookup"><span data-stu-id="42ed9-130">Most log providers connect to an external data source, such as a file or database, to store the event information that is collected during package execution.</span></span> <span data-ttu-id="42ed9-131">与运行时的任何其对象一样，与外部数据源的连接通常使用连接管理器对象来完成。</span><span class="sxs-lookup"><span data-stu-id="42ed9-131">As with any other object in the runtime, connecting to the external data source is typically accomplished by using connection manager objects.</span></span>  
  
 <span data-ttu-id="42ed9-132"><xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> 方法在包执行开始时调用。请重写此方法以建立与外部数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="42ed9-132">The <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> method is called at the start of package execution.Override this method to establish a connection to the external data source.</span></span>  
  
 <span data-ttu-id="42ed9-133">下面的示例代码演示了在 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> 执行期间打开一个文本文件供写入的日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="42ed9-133">The following sample code shows a log provider that opens a text file for writing during <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>.</span></span> <span data-ttu-id="42ed9-134">该提供程序通过调用在 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 属性中指定的连接管理器的 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 方法来打开文件。</span><span class="sxs-lookup"><span data-stu-id="42ed9-134">It opens the file by calling the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of the connection manager that was specified in the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property.</span></span>  
  
```csharp  
public override void OpenLog()  
{  
    if(!this.connections.Contains(this.ConfigString))  
        throw new Exception("The ConnectionManager " + this.ConfigString + " does not exist in the Connections collection.");  
  
    this.connectionManager = connections[ConfigString];  
    string filePath = this.connectionManager.AcquireConnection(null) as string;  
  
    if(filePath == null || filePath.Length == 0)  
        throw new Exception("The ConnectionManager " + this.ConfigString + " is not a valid FILE ConnectionManager");  
  
    //  Create a StreamWriter to append to.  
    sw = new StreamWriter(filePath,true);  
  
    sw.WriteLine("Open log" + System.DateTime.Now.ToShortTimeString());  
}  
```  
  
```vb  
Public Overrides  Sub OpenLog()  
    If Not Me.connections.Contains(Me.ConfigString) Then  
        Throw New Exception("The ConnectionManager " + Me.ConfigString + " does not exist in the Connections collection.")  
    End If  
  
    Me.connectionManager = connections(ConfigString)  
    Dim filePath As String =  Me.connectionManager.AcquireConnectionCType(as string, Nothing)  
  
    If filePath = Nothing Or filePath.Length = 0 Then  
        Throw New Exception("The ConnectionManager " + Me.ConfigString + " is not a valid FILE ConnectionManager")  
    End If  
  
    '  Create a StreamWriter to append to.  
    sw = New StreamWriter(filePath,True)  
  
    sw.WriteLine("Open log" + System.DateTime.Now.ToShortTimeString())  
End Sub  
```  
  
### <a name="writing-log-entries"></a><span data-ttu-id="42ed9-135">写入日志条目</span><span class="sxs-lookup"><span data-stu-id="42ed9-135">Writing Log Entries</span></span>  
 <span data-ttu-id="42ed9-136">每次包中的对象通过对某一事件接口调用 Fire\<event> 方法来引发事件时，都会调用 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="42ed9-136">The <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method is called every time that an object in the package raises an event by calling a Fire\<event> method on one of the event interfaces.</span></span> <span data-ttu-id="42ed9-137">每次引发事件时，都会提供其上下文的相关信息，通常是说明性消息。</span><span class="sxs-lookup"><span data-stu-id="42ed9-137">Each event is raised with information about its context and usually an explanatory message.</span></span> <span data-ttu-id="42ed9-138">但是，并非所有对 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 方法的调用都包含每个方法参数的信息。</span><span class="sxs-lookup"><span data-stu-id="42ed9-138">However, not every call to the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method includes information for every method parameter.</span></span> <span data-ttu-id="42ed9-139">例如，一些具有自我说明性名称的标准事件不提供 MessageText，并且 DataCode 和 DataBytes 只提供可选的补充信息。</span><span class="sxs-lookup"><span data-stu-id="42ed9-139">For example, some standard events whose names are self-explanatory do not provide MessageText, and DataCode and DataBytes are intended for optional supplemental information.</span></span>  
  
 <span data-ttu-id="42ed9-140">下面的代码示例实现了 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 方法，并将事件写入前述打开的流中。</span><span class="sxs-lookup"><span data-stu-id="42ed9-140">The following code example implements the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method, and writes the events to the stream that was opened in the previous section.</span></span>  
  
```csharp  
public override void Log(string logEntryName, string computerName, string operatorName, string sourceName, string sourceID, string executionID, string messageText, DateTime startTime, DateTime endTime, int dataCode, byte[] dataBytes)  
{  
    sw.Write(logEntryName + ",");  
    sw.Write(computerName + ",");  
    sw.Write(operatorName + ",");  
    sw.Write(sourceName + ",");  
    sw.Write(sourceID + ",");  
    sw.Write(messageText + ",");  
    sw.Write(dataBytes + ",");  
    sw.WriteLine("");  
}  
```  
  
```vb  
Public Overrides  Sub Log(ByVal logEnTryName As String, ByVal computerName As String, ByVal operatorName As String, ByVal sourceName As String, ByVal sourceID As String, ByVal executionID As String, ByVal messageText As String, ByVal startTime As DateTime, ByVal endTime As DateTime, ByVal dataCode As Integer, ByVal dataBytes() As Byte)  
    sw.Write(logEnTryName + ",")  
    sw.Write(computerName + ",")  
    sw.Write(operatorName + ",")  
    sw.Write(sourceName + ",")  
    sw.Write(sourceID + ",")  
    sw.Write(messageText + ",")  
    sw.Write(dataBytes + ",")  
    sw.WriteLine("")  
End Sub  
```  
  
### <a name="closing-the-log"></a><span data-ttu-id="42ed9-141">关闭日志</span><span class="sxs-lookup"><span data-stu-id="42ed9-141">Closing the Log</span></span>  
 <span data-ttu-id="42ed9-142"><xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> 方法在包执行结束时、包中的所有对象都执行完毕后或包由于错误而停止时调用。</span><span class="sxs-lookup"><span data-stu-id="42ed9-142">The <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> method is called at the end of package execution, after all the objects in the package have completed execution, or, when the package stops because of errors.</span></span>  
  
 <span data-ttu-id="42ed9-143">下面的代码示例演示了 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> 方法的实现，该方法用于关闭在 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> 方法执行期间打开的文件流。</span><span class="sxs-lookup"><span data-stu-id="42ed9-143">The following code example demonstrates an implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> method that closes the file stream that was opened during the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> method.</span></span>  
  
```csharp  
public override void CloseLog()  
{  
    if (sw != null)  
    {  
        sw.WriteLine("Close log" + System.DateTime.Now.ToShortTimeString());  
        sw.Close();  
    }  
}  
```  
  
```vb  
Public Overrides  Sub CloseLog()  
    If Not sw Is Nothing Then  
        sw.WriteLine("Close log" + System.DateTime.Now.ToShortTimeString())  
        sw.Close()  
    End If  
End Sub  
```  
  
<span data-ttu-id="42ed9-144">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="42ed9-144">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="42ed9-145">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="42ed9-145">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="42ed9-146">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="42ed9-146">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="42ed9-147">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="42ed9-147">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42ed9-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42ed9-148">See Also</span></span>  
 <span data-ttu-id="42ed9-149">[创建自定义日志提供程序](creating-a-custom-log-provider.md) </span><span class="sxs-lookup"><span data-stu-id="42ed9-149">[Creating a Custom Log Provider](creating-a-custom-log-provider.md) </span></span>  
 [<span data-ttu-id="42ed9-150">为自定义日志提供程序开发用户界面</span><span class="sxs-lookup"><span data-stu-id="42ed9-150">Developing a User Interface for a Custom Log Provider</span></span>](developing-a-user-interface-for-a-custom-log-provider.md)  
  
  
