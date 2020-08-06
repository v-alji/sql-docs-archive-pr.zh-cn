---
title: 在脚本组件中连接数据源| Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], connecting to data sources
ms.assetid: 96de63ab-ff48-4e7e-89e0-ffd6a89c63b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9272f946abb68a1c54cd6f4851806ec6a1b15de7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587912"
---
# <a name="connecting-to-data-sources-in-the-script-component"></a><span data-ttu-id="1d25a-102">在脚本组件中连接数据源</span><span class="sxs-lookup"><span data-stu-id="1d25a-102">Connecting to Data Sources in the Script Component</span></span>
  <span data-ttu-id="1d25a-103">连接管理器是一个封装和存储连接特定类型数据源所需信息的便利单元。</span><span class="sxs-lookup"><span data-stu-id="1d25a-103">A connection manager is a convenient unit that encapsulates and stores the information that is required to connect to a data source of a particular type.</span></span> <span data-ttu-id="1d25a-104">有关详细信息，请参阅 [Integration Services (SSIS) 连接](../../connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="1d25a-104">For more information, see [Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
 <span data-ttu-id="1d25a-105">单击“脚本转换编辑器”的“连接管理器”页上的“添加”和“删除”按钮，可使现有连接管理器可供源或目标组件中的自定义脚本访问     。</span><span class="sxs-lookup"><span data-stu-id="1d25a-105">You can make existing connection managers available for access by the custom script in the source or destination component by clicking the **Add** and **Remove** buttons on the **Connection Managers** page of the **Script Transformation Editor**.</span></span> <span data-ttu-id="1d25a-106">但是，您必须编写自己的自定义代码才能加载或保存数据，并且才有可能打开和关闭与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="1d25a-106">However, you must write your own custom code to load or save your data, and possibly to open and close the connection to the data source.</span></span> <span data-ttu-id="1d25a-107">有关“脚本转换编辑器”的“连接管理器”页的详细信息，请参阅[在脚本组件编辑器中配置脚本组件](configuring-the-script-component-in-the-script-component-editor.md)和[脚本转换编辑器（“连接管理器”页）](../../script-transformation-editor-connection-managers-page.md) 。</span><span class="sxs-lookup"><span data-stu-id="1d25a-107">For more information about the **Connection Managers** page of the **Script Transformation Editor**, see [Configuring the Script Component in the Script Component Editor](configuring-the-script-component-in-the-script-component-editor.md) and [Script Transformation Editor &#40;Connection Managers Page&#41;](../../script-transformation-editor-connection-managers-page.md).</span></span>  
  
 <span data-ttu-id="1d25a-108">脚本组件在 `Connections` 项目项中创建一个 `ComponentWrapper` 集合类，该集合类为每个连接管理器包含一个强类型的取值函数，该取值函数与连接管理器本身同名。</span><span class="sxs-lookup"><span data-stu-id="1d25a-108">The Script component creates a `Connections` collection class in the `ComponentWrapper` project item that contains a strongly-typed accessor for each connection manager that has the same name as the connection manager itself.</span></span> <span data-ttu-id="1d25a-109">此集合通过 `Connections` 类的 `ScriptMain` 属性公开。</span><span class="sxs-lookup"><span data-stu-id="1d25a-109">This collection is exposed through the `Connections` property of the `ScriptMain` class.</span></span> <span data-ttu-id="1d25a-110">该取值函数属性返回对作为 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100> 实例的连接管理器的引用。</span><span class="sxs-lookup"><span data-stu-id="1d25a-110">The accessor property returns a reference to the connection manager as an instance of <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100>.</span></span> <span data-ttu-id="1d25a-111">例如，如果已在对话框的“连接管理器”页中添加名为 `MyADONETConnection` 的连接管理器，则可在脚本中添加以下代码来获取对该连接管理器的引用：</span><span class="sxs-lookup"><span data-stu-id="1d25a-111">For example, if you have added a connection manager named `MyADONETConnection` on the Connection Managers page of the dialog box, you can obtain a reference to it in your script by adding the following code:</span></span>  
  
 `Dim myADONETConnectionManager As IDTSConnectionManager100 = _`  
  
 `Me.Connections.MyADONETConnection`  
  
> [!NOTE]  
>  <span data-ttu-id="1d25a-112">您在调用 `AcquireConnection` 之前必须了解连接管理器返回的连接的类型。</span><span class="sxs-lookup"><span data-stu-id="1d25a-112">You must know the type of connection that is returned by the connection manager before you call `AcquireConnection`.</span></span> <span data-ttu-id="1d25a-113">由于脚本任务启用了 `Option Strict`，因此在使用连接之前，必须先将连接（返回类型为 `Object`）转换为适当的连接类型。</span><span class="sxs-lookup"><span data-stu-id="1d25a-113">Because the Script task has `Option Strict` enabled, you must cast the connection, which is returned as type `Object`, to the appropriate connection type before you can use it.</span></span>  
  
 <span data-ttu-id="1d25a-114">接下来，调用特定连接管理器的 `AcquireConnection` 方法以获取基础连接或连接数据源所需的信息。</span><span class="sxs-lookup"><span data-stu-id="1d25a-114">Next, you call the `AcquireConnection` method of the specific connection manager to obtain either the underlying connection or the information that is required to connect to the data source.</span></span> <span data-ttu-id="1d25a-115">例如，可以使用以下代码获取对 ADO.NET 连接管理器包装的 System.Data.SqlConnection 的引用  ：</span><span class="sxs-lookup"><span data-stu-id="1d25a-115">For example, you obtain a reference to the **System.Data.SqlConnection** wrapped by an ADO.NET connection manager by using the following code:</span></span>  
  
 `Dim myADOConnection As SqlConnection = _`  
  
 `CType(MyADONETConnectionManager.AcquireConnection(Nothing), SqlConnection)`  
  
 <span data-ttu-id="1d25a-116">相反，对平面文件连接管理器的相同调用只返回该文件数据源的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="1d25a-116">In contrast, the same call to a flat file connection manager returns only the path and file name of the file data source.</span></span>  
  
 `Dim myFlatFile As String = _`  
  
 `CType(MyFlatFileConnectionManager.AcquireConnection(Nothing), String)`  
  
 <span data-ttu-id="1d25a-117">然后，必须向 `System.IO.StreamReader` 或 `Streamwriter` 提供此路径和文件名才能读或写该平面文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="1d25a-117">You then must provide this path and file name to a `System.IO.StreamReader` or `Streamwriter` to read or write the data in the flat file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1d25a-118">在脚本组件中编写托管代码时，不能调用返回非托管对象的连接管理器（如 OLE DB 连接管理器和 Excel 连接管理器）的 AcquireConnection 方法。</span><span class="sxs-lookup"><span data-stu-id="1d25a-118">When you write managed code in a Script component, you cannot call the AcquireConnection method of connection managers that return unmanaged objects, such as the OLE DB connection manager and the Excel connection manager.</span></span> <span data-ttu-id="1d25a-119">但是，可以读取这些连接管理器的 ConnectionString 属性，并使用 System.Data.OleDb 命名空间中 OLEDB 连接的连接字符串在代码中直接连接数据源   。</span><span class="sxs-lookup"><span data-stu-id="1d25a-119">However, you can read the ConnectionString property of these connection managers, and connect to the data source directly in your code by using the connection string of an OLEDB **connection** from the **System.Data.OleDb** namespace.</span></span>  
>   
>  <span data-ttu-id="1d25a-120">如果需要调用返回非托管对象的连接管理器的 AcquireConnection 方法，可使用 ADO.NET 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="1d25a-120">If you need to call the AcquireConnection method of a connection manager that returns an unmanaged object, use an ADO.NET connection manager.</span></span> <span data-ttu-id="1d25a-121">配置 ADO.NET 连接管理器为使用 OLE DB 访问接口时，该连接管理器使用用于 OLE DB 的 .NET Framework 数据访问接口进行连接。</span><span class="sxs-lookup"><span data-stu-id="1d25a-121">When you configure the ADO.NET connection manager to use an OLE DB provider, it connects by using the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="1d25a-122">在这种情况下，AcquireConnection 方法将返回 `System.Data.OleDb.OleDbConnection` 而不是非托管对象。</span><span class="sxs-lookup"><span data-stu-id="1d25a-122">In this case, the AcquireConnection method returns a `System.Data.OleDb.OleDbConnection` instead of an unmanaged object.</span></span> <span data-ttu-id="1d25a-123">要配置用于 Excel 数据源的 ADO.NET 连接管理器，请选择 Microsoft OLE DB Provider for Jet，再指定 Excel 工作簿，然后在“连接管理器”对话框的“全部”页上输入 `Excel 8.0`（对于 Excel 97 及更高版本）作为“扩展属性”的值    。</span><span class="sxs-lookup"><span data-stu-id="1d25a-123">To configure an ADO.NET connection manager for use with an Excel data source, select the Microsoft OLE DB Provider for Jet, specify an Excel workbook, and then enter `Excel 8.0` (for Excel 97 and later) as the value of **Extended Properties** on the **All** page of the **Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="1d25a-124">有关如何在脚本组件中使用连接管理器的详细信息，请参阅[通过脚本组件创建源](../../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)和[通过脚本组件创建目标](../../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="1d25a-124">For more information about how to use connection managers with the script component, see [Creating a Source with the Script Component](../../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) and [Creating a Destination with the Script Component](../../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span>  
  
<span data-ttu-id="1d25a-125">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="1d25a-125">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1d25a-126">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="1d25a-126">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1d25a-127">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="1d25a-127">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1d25a-128">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="1d25a-128">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d25a-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d25a-129">See Also</span></span>  
 <span data-ttu-id="1d25a-130">[Integration Services &#40;SSIS&#41; 连接](../../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="1d25a-130">[Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="1d25a-131">创建连接管理器</span><span class="sxs-lookup"><span data-stu-id="1d25a-131">Create Connection Managers</span></span>](../../create-connection-managers.md)  
  
  
