---
title: 以编程方式启用日志记录 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- Integration Services packages, logs
- SSIS logging
- log providers [Integration Services]
- logs [Integration Services], enabling
- LoggingMode property
- LogProvider object
- packages [Integration Services], logs
ms.assetid: 3222a1ed-83eb-421c-b299-a53b67bba740
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff7f81aca330960e4e94b0343080a37ded8c1273
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689562"
---
# <a name="enabling-logging-programmatically"></a><span data-ttu-id="22652-102">以编程方式启用日志记录</span><span class="sxs-lookup"><span data-stu-id="22652-102">Enabling Logging Programmatically</span></span>
  <span data-ttu-id="22652-103">运行时引擎提供 <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> 对象的集合，这些对象用于在包验证和执行过程中捕获特定于事件的信息。</span><span class="sxs-lookup"><span data-stu-id="22652-103">The run-time engine provides a collection of <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> objects that enable event-specific information to be captured during package validation and execution.</span></span> <span data-ttu-id="22652-104"><xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> 对象可用于 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer> 对象，包括 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>、<xref:Microsoft.SqlServer.Dts.Runtime.Package>、<xref:Microsoft.SqlServer.Dts.Runtime.ForLoop> 和 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 对象。</span><span class="sxs-lookup"><span data-stu-id="22652-104"><xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> objects are available to <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer> objects, including the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, <xref:Microsoft.SqlServer.Dts.Runtime.Package>, <xref:Microsoft.SqlServer.Dts.Runtime.ForLoop>, and <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> objects.</span></span> <span data-ttu-id="22652-105">日志记录对个别容器或整个包启用。</span><span class="sxs-lookup"><span data-stu-id="22652-105">Logging is enabled on individual containers, or on the whole package.</span></span>

 <span data-ttu-id="22652-106">有多种类型的日志提供程序可供容器使用。</span><span class="sxs-lookup"><span data-stu-id="22652-106">There are several types of log providers that are available for a container to use.</span></span> <span data-ttu-id="22652-107">这为以多种格式创建和存储日志信息提供了灵活性。</span><span class="sxs-lookup"><span data-stu-id="22652-107">This provides the flexibility to create and store log information in many formats.</span></span> <span data-ttu-id="22652-108">在日志记录中登记容器对象分为两个步骤：首先启用日志记录，然后选择日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="22652-108">Enlisting a container object in logging is a two-step process: first logging is enabled, and then a log provider is selected.</span></span> <span data-ttu-id="22652-109">容器的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingOptions%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> 属性用于指定记录的事件和选择日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="22652-109">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingOptions%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> properties of the container are used to specify the logged events and to select the log provider.</span></span>

## <a name="enabling-logging"></a><span data-ttu-id="22652-110">启用日志记录</span><span class="sxs-lookup"><span data-stu-id="22652-110">Enabling Logging</span></span>
 <span data-ttu-id="22652-111">每个可执行日志记录的容器中的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> 属性用于确定容器的事件信息是否记录到事件日志中。</span><span class="sxs-lookup"><span data-stu-id="22652-111">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> property, found in each container that can perform logging, determines whether the container's event information is recorded to the event log.</span></span> <span data-ttu-id="22652-112">此属性从 <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode> 结构赋值，并且默认情况下此属性从容器的父级继承。</span><span class="sxs-lookup"><span data-stu-id="22652-112">This property is assigned a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode> structure, and is inherited from the container's parent by default.</span></span> <span data-ttu-id="22652-113">如果容器是包，并因此没有父级，则该属性使用 <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode.UseParentSetting>，其默认值为 `Disabled`。</span><span class="sxs-lookup"><span data-stu-id="22652-113">If the container is a package, and therefore has no parent, the property uses the <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode.UseParentSetting>, which defaults to `Disabled`.</span></span>

### <a name="selecting-a-log-provider"></a><span data-ttu-id="22652-114">选择日志提供程序</span><span class="sxs-lookup"><span data-stu-id="22652-114">Selecting a Log Provider</span></span>
 <span data-ttu-id="22652-115"><xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> 属性设置为 `Enabled` 后，日志提供程序将添加到容器的 <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> 集合以完成该处理。</span><span class="sxs-lookup"><span data-stu-id="22652-115">After the <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> property is set to `Enabled`, a log provider is added to the <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection of the container to complete the process.</span></span> <span data-ttu-id="22652-116"><xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> 集合可用于 <xref:Microsoft.SqlServer.Dts.Runtime.LoggingOptions> 对象，该集合包含为容器选择的日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="22652-116">The <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection is available on the <xref:Microsoft.SqlServer.Dts.Runtime.LoggingOptions> object, and contains the log providers selected for the container.</span></span> <span data-ttu-id="22652-117">调用 <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders.Add%2A> 方法可创建提供程序并将其添加到集合中。</span><span class="sxs-lookup"><span data-stu-id="22652-117">The <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders.Add%2A> method is called to create a provider and add it to the collection.</span></span> <span data-ttu-id="22652-118">然后该方法会返回添加到集合中的日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="22652-118">The method then returns the log provider that was added to the collection.</span></span> <span data-ttu-id="22652-119">每个提供程序都有其特有的配置设置，这些属性是使用 <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> 属性设置的。</span><span class="sxs-lookup"><span data-stu-id="22652-119">Each provider has configuration settings that are unique to that provider, and these properties are set using the <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> property.</span></span>

 <span data-ttu-id="22652-120">下表列出了可用的日志提供程序、其说明和 <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> 信息。</span><span class="sxs-lookup"><span data-stu-id="22652-120">The following table lists the available log providers, their description, and their <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> information.</span></span>

|<span data-ttu-id="22652-121">提供程序</span><span class="sxs-lookup"><span data-stu-id="22652-121">Provider</span></span>|<span data-ttu-id="22652-122">说明</span><span class="sxs-lookup"><span data-stu-id="22652-122">Description</span></span>|<span data-ttu-id="22652-123">ConfigString 属性</span><span class="sxs-lookup"><span data-stu-id="22652-123">ConfigString property</span></span>|
|--------------|-----------------|---------------------------|
|<span data-ttu-id="22652-124">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="22652-124">SQL Server Profiler</span></span>|<span data-ttu-id="22652-125">生成可捕获并在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler 中查看的 SQL 跟踪。</span><span class="sxs-lookup"><span data-stu-id="22652-125">Generates SQL traces that may be captured and viewed in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler.</span></span> <span data-ttu-id="22652-126">这种提供程序的默认文件扩展名是 .trc。</span><span class="sxs-lookup"><span data-stu-id="22652-126">The default file name extension for this provider is .trc.</span></span>|<span data-ttu-id="22652-127">不需要任何配置。</span><span class="sxs-lookup"><span data-stu-id="22652-127">No configuration is required.</span></span>|
|<span data-ttu-id="22652-128">SQL Server</span><span class="sxs-lookup"><span data-stu-id="22652-128">SQL Server</span></span>|<span data-ttu-id="22652-129">将事件日志条目写入任意 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的 sysssislog 表中。</span><span class="sxs-lookup"><span data-stu-id="22652-129">Writes event log entries to the **sysssislog** table in any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="22652-130">提供程序要求指定与数据库的连接以及目标数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="22652-130">provider requires that the connection to the database be specified, and also the target database name.</span></span>|
|<span data-ttu-id="22652-131">文本文件</span><span class="sxs-lookup"><span data-stu-id="22652-131">Text File</span></span>|<span data-ttu-id="22652-132">将事件日志条目以逗号分隔值 (CSV) 格式写入 ASCII 文本文件。</span><span class="sxs-lookup"><span data-stu-id="22652-132">Writes event log entries to ASCII text files in a comma-separated value (CSV) format.</span></span> <span data-ttu-id="22652-133">这种提供程序的默认文件扩展名是 .log。</span><span class="sxs-lookup"><span data-stu-id="22652-133">The default file name extension for this provider is .log.</span></span>|<span data-ttu-id="22652-134">文件连接管理器的名称。</span><span class="sxs-lookup"><span data-stu-id="22652-134">The name of a file connection manager.</span></span>|
|<span data-ttu-id="22652-135">Windows 事件日志</span><span class="sxs-lookup"><span data-stu-id="22652-135">Windows Event Log</span></span>|<span data-ttu-id="22652-136">记录到本地计算机的标准 Windows 事件日志的应用程序日志中。</span><span class="sxs-lookup"><span data-stu-id="22652-136">Logs to standard Windows Event Log on the local computer in the Application log.</span></span>|<span data-ttu-id="22652-137">不需要任何配置。</span><span class="sxs-lookup"><span data-stu-id="22652-137">No configuration is required.</span></span>|
|<span data-ttu-id="22652-138">XML 文件</span><span class="sxs-lookup"><span data-stu-id="22652-138">XML File</span></span>|<span data-ttu-id="22652-139">将事件日志条目写入 XML 格式的文件中。</span><span class="sxs-lookup"><span data-stu-id="22652-139">Writes event log entries to XML formatted file.</span></span> <span data-ttu-id="22652-140">这种提供程序的默认文件扩展名是 .xml。</span><span class="sxs-lookup"><span data-stu-id="22652-140">The default file name extension for this provider is .xml</span></span>|<span data-ttu-id="22652-141">文件连接管理器的名称。</span><span class="sxs-lookup"><span data-stu-id="22652-141">The name of a file connection manager.</span></span>|

 <span data-ttu-id="22652-142">通过设置容器的 `EventFilterKind` 和 `EventFilter` 属性可将事件包含或排除在事件日志中。</span><span class="sxs-lookup"><span data-stu-id="22652-142">Events are included in or excluded from the event log by setting the `EventFilterKind` and the `EventFilter` properties of the container.</span></span> <span data-ttu-id="22652-143">`EventFilterKind` 结构包含两个值，`ExclusionFilter` 和 `InclusionFilter`，它们指示添加到 `EventFilter` 中的事件是否包含在事件日志中。</span><span class="sxs-lookup"><span data-stu-id="22652-143">The `EventFilterKind` structure contains two values, `ExclusionFilter` and `InclusionFilter`, that indicate whether the events that are added to the `EventFilter` are included in the event log.</span></span> <span data-ttu-id="22652-144">然后赋给 `EventFilter` 属性一个字符串数组，其中包含属于筛选主题的事件的名称。</span><span class="sxs-lookup"><span data-stu-id="22652-144">The `EventFilter` property is then assigned a string array that contains the names of the events that are the subject of the filtering.</span></span>

 <span data-ttu-id="22652-145">下面的代码对包启用日志记录，将文本文件的日志提供程序添加到 <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> 集合，并指定要包含在日志记录输出中的事件列表。</span><span class="sxs-lookup"><span data-stu-id="22652-145">The following code enables logging on a package, adds the log provider for Text files to the <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection, and specifies a list of events to include in the logging output.</span></span>

## <a name="sample"></a><span data-ttu-id="22652-146">示例</span><span class="sxs-lookup"><span data-stu-id="22652-146">Sample</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.SqlServer.Dts.Samples
{
  class Program
  {
    static void Main(string[] args)
    {
      Package p = new Package();

      ConnectionManager loggingConnection = p.Connections.Add("FILE");
      loggingConnection.ConnectionString = @"C:\SSISPackageLog.txt";

      LogProvider provider = p.LogProviders.Add("DTS.LogProviderTextFile.2");
      provider.ConfigString = loggingConnection.Name;
      p.LoggingOptions.SelectedLogProviders.Add(provider);
      p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion;
      p.LoggingOptions.EventFilter = new String[] { "OnPreExecute", 
         "OnPostExecute", "OnError", "OnWarning", "OnInformation" };
      p.LoggingMode = DTSLoggingMode.Enabled;

      // Add tasks and other objects to the package.

    }
  }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime

Module Module1

  Sub Main()

    Dim p As Package = New Package()

    Dim loggingConnection As ConnectionManager = p.Connections.Add("FILE")
    loggingConnection.ConnectionString = "C:\SSISPackageLog.txt"

    Dim provider As LogProvider = p.LogProviders.Add("DTS.LogProviderTextFile.2")
    provider.ConfigString = loggingConnection.Name
    p.LoggingOptions.SelectedLogProviders.Add(provider)
    p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion
    p.LoggingOptions.EventFilter = New String() {"OnPreExecute", _
       "OnPostExecute", "OnError", "OnWarning", "OnInformation"}
    p.LoggingMode = DTSLoggingMode.Enabled

    ' Add tasks and other objects to the package.

  End Sub

End Module
```

<span data-ttu-id="22652-147">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="22652-147">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="22652-148">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="22652-148">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="22652-149">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="22652-149">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="22652-150">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="22652-150">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="22652-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22652-151">See Also</span></span>
 [<span data-ttu-id="22652-152">Integration Services (SSIS) 日志记录</span><span class="sxs-lookup"><span data-stu-id="22652-152">Integration Services &#40;SSIS&#41; Logging</span></span>](../performance/integration-services-ssis-logging.md)


