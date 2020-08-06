---
title: " (Excel) 的数据挖掘客户端连接到源数据 |Microsoft Docs"
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
ms.assetid: 548672ce-e403-4aca-b67a-c2c797f053dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4b4759d94043fdccacdf5b285de50697a18965e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579191"
---
# <a name="connect-to-source-data-data-mining-client-for-excel"></a><span data-ttu-id="60c69-102">连接到源数据（Excel 数据挖掘客户端）</span><span class="sxs-lookup"><span data-stu-id="60c69-102">Connect to Source Data (Data Mining Client for Excel)</span></span>
  <span data-ttu-id="60c69-103">本主题介绍如何创建和使用连接来存储数据挖掘模型以及访问 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中存储的外部数据。</span><span class="sxs-lookup"><span data-stu-id="60c69-103">This topic describes how to create and use connections used for storing data mining models, and for accessing external data stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="60c69-104">**数据挖掘连接。**</span><span class="sxs-lookup"><span data-stu-id="60c69-104">**Data mining connections.**</span></span> <span data-ttu-id="60c69-105">您在启动外接程序时创建的初始连接用于访问算法、分析数据以及存储挖掘结构和模型。</span><span class="sxs-lookup"><span data-stu-id="60c69-105">The initial connection that you create when you start the add-ins is used to access algorithms, analyze data, and store mining structure and models.</span></span>  
  
 <span data-ttu-id="60c69-106">要使用外接程序中的建模和可视化工具需要与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的连接，因为这些外接程序依赖 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 所提供的算法和数据结构。</span><span class="sxs-lookup"><span data-stu-id="60c69-106">A connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] is required to use the modeling and visualization tools in the add-ins, because the add-ins depend on algorithms and data structures that are provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="60c69-107">**与外部数据源的连接。**</span><span class="sxs-lookup"><span data-stu-id="60c69-107">**Connections to external data sources.**</span></span> <span data-ttu-id="60c69-108">生成模型或保存结果时还可以创建与外部数据的连接。</span><span class="sxs-lookup"><span data-stu-id="60c69-108">You can also create connections to external data as you are building models or saving the results.</span></span> <span data-ttu-id="60c69-109">例如，您可以在一个服务器上创建数据挖掘模型，然后使用存储在另一个 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例、Excel 数据表或者外部数据源（如 [!INCLUDE[msCoName](../includes/msconame-md.md)] Access）中的数据对该数据挖掘模型执行预测查询。</span><span class="sxs-lookup"><span data-stu-id="60c69-109">For example, you can create a data mining model on one server, and then perform a prediction query against the data mining model by using data stored in another instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], in an Excel data table, or in an external data source such as [!INCLUDE[msCoName](../includes/msconame-md.md)] Access.</span></span> <span data-ttu-id="60c69-110">每次访问新的数据源时，系统都通过一个对话框提示您创建连接。</span><span class="sxs-lookup"><span data-stu-id="60c69-110">Each time that you access a new data source, you will be prompted to create a connection by using a dialog box.</span></span>  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq2"></a><span data-ttu-id="60c69-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="60c69-111">Prerequisites</span></span>  
 <span data-ttu-id="60c69-112">此版本的外接程序要求您的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例为 SQL Server 2012。</span><span class="sxs-lookup"><span data-stu-id="60c69-112">This version of the add-ins requires that your instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] be SQL Server 2012.</span></span> <span data-ttu-id="60c69-113">若要连接到早期版本的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]，则可使用外接程序的一个单独版本。</span><span class="sxs-lookup"><span data-stu-id="60c69-113">A separate version of the add-ins is available if you want to connect to an earlier version of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="60c69-114">有很多外接程序版本支持 SQL Server 2005、SQL Server 2008 和 SQL Server 2008 R2。</span><span class="sxs-lookup"><span data-stu-id="60c69-114">There are versions of the add-ins that support SQL Server 2005, SQL Server 2008, and SQL Server 2008 R2.</span></span>  
  
 <span data-ttu-id="60c69-115">要连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库，您必须具有访问数据库服务器的权限。</span><span class="sxs-lookup"><span data-stu-id="60c69-115">To connect to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, you must have permissions to access the database server.</span></span> <span data-ttu-id="60c69-116">而且，还必须启用数据挖掘会话，您还必须具有服务器上存储的数据库对象的读或读/写权限。</span><span class="sxs-lookup"><span data-stu-id="60c69-116">Moreover, data mining sessions must be enabled, and you must have read or read/write permissions on database objects stored on the server.</span></span>  
  
##  <a name="creating-data-mining-server-connections"></a><a name="bkmk_connect"></a><span data-ttu-id="60c69-117">创建数据挖掘服务器连接</span><span class="sxs-lookup"><span data-stu-id="60c69-117">Creating Data Mining Server Connections</span></span>  
 <span data-ttu-id="60c69-118">Excel 数据挖掘客户端和 Excel 表分析工具中的 "**连接**" 组提供了用于管理与实例的连接的工具 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="60c69-118">The **Connections** group in the Data Mining Client for Excel and the Table Analysis Tools for Excel provides tools for managing connections to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="60c69-119">您可以在安装外接程序时创建连接，也可以在以后添加连接。</span><span class="sxs-lookup"><span data-stu-id="60c69-119">You can create the connection when you install the add-in, or you can add a connection later.</span></span>  
  
-   <span data-ttu-id="60c69-120">您可以创建多个连接，而且可以随时更改这些连接，模型创建或查询过程中除外。</span><span class="sxs-lookup"><span data-stu-id="60c69-120">You can create multiple connections, and change connections at any time, unless you are in the process of creating or querying a model.</span></span>  
  
     <span data-ttu-id="60c69-121">不要在处理数据挖掘模型时更改或关闭连接。</span><span class="sxs-lookup"><span data-stu-id="60c69-121">Do not change or close a connection when a data mining model is being processed.</span></span> <span data-ttu-id="60c69-122">数据挖掘模型可能会丢失数据，或者模型可能无法使用。</span><span class="sxs-lookup"><span data-stu-id="60c69-122">The data mining model might lose data, or the model might become unusable.</span></span>  
  
-   <span data-ttu-id="60c69-123">任意特定时间只能有一个连接处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="60c69-123">Only one connection can be active at a particular time.</span></span>  
  
### <a name="connections-in-the-excel-add-ins"></a><span data-ttu-id="60c69-124">Excel 外接程序中的连接</span><span class="sxs-lookup"><span data-stu-id="60c69-124">Connections in the Excel Add-ins</span></span>  
 <span data-ttu-id="60c69-125">使用 Excel 数据挖掘客户端和 Excel 表分析工具中的 "**连接**" 组，您可以在其中管理与实例的连接 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="60c69-125">The **Connections** group in the Data Mining Client for Excel and the Table Analysis Tools for Excel is where you manage connections to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
##### <a name="create-a-new-server-connection-in-the-excel-add-ins"></a><span data-ttu-id="60c69-126">在 Excel 外接程序中创建新的服务器连接</span><span class="sxs-lookup"><span data-stu-id="60c69-126">Create a new server connection in the Excel add-ins</span></span>  
  
1.  <span data-ttu-id="60c69-127">单击 "**分析**" 或 "**数据挖掘**" 功能区上的 "**连接**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="60c69-127">Click the **Connection** button on the **Analyze** or **Data Mining** ribbon.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60c69-128">按钮的文字可指示连接是否存在。</span><span class="sxs-lookup"><span data-stu-id="60c69-128">The text of the button indicates if a connection exists.</span></span> <span data-ttu-id="60c69-129">如果未在工作表中建立连接，则按钮会包含文本 " \<No connection> ."。如果以前在工作簿中建立了连接，则该连接的名称将显示在按钮中。</span><span class="sxs-lookup"><span data-stu-id="60c69-129">When no connection has been made in the worksheet, the button contains the text "\<No connection>." If a connection was previously made in the workbook, the name of that connection appears in the button.</span></span>  
  
2.  <span data-ttu-id="60c69-130">在 " **Analysis Services 连接**" 对话框中，单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="60c69-130">In the **Analysis Services Connections** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="60c69-131">在 "**新建 Analysis Services 连接**" 对话框中，键入服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="60c69-131">In the **New Analysis Services Connection** dialog box, type the name of the server.</span></span>  
  
4.  <span data-ttu-id="60c69-132">指定身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="60c69-132">Specify the authentication method.</span></span>  
  
5.  <span data-ttu-id="60c69-133">从 "**目录名称**" 下拉列表中选择数据库。</span><span class="sxs-lookup"><span data-stu-id="60c69-133">Select a database from the **Catalog name** drop-down list.</span></span> <span data-ttu-id="60c69-134">如果实例中不存在数据库，请选择\*\* (默认) \*\*。</span><span class="sxs-lookup"><span data-stu-id="60c69-134">If no database exists on the instance, select **(default)**.</span></span>  
  
6.  <span data-ttu-id="60c69-135">键入该连接的友好名称。</span><span class="sxs-lookup"><span data-stu-id="60c69-135">Type a friendly name for the connection.</span></span>  
  
7.  <span data-ttu-id="60c69-136">单击 "**测试连接**" 以验证服务器和数据库是否可用。</span><span class="sxs-lookup"><span data-stu-id="60c69-136">Click **Test Connection** to verify that the server and database are available.</span></span>  
  
8.  <span data-ttu-id="60c69-137">单击 **“确定”** ，再单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="60c69-137">Click **OK**, and then click **Close**.</span></span>  
  
### <a name="connections-using-a-web-service"></a><span data-ttu-id="60c69-138">使用 Web 服务连接</span><span class="sxs-lookup"><span data-stu-id="60c69-138">Connections using a Web Service</span></span>  
 <span data-ttu-id="60c69-139">如果您使用瘦客户端体系结构支持浏览 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多维数据集和数据，则还可以通过 Web 服务配置到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="60c69-139">If you are using a thin-client architecture to enable browsing of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cubes and data, you can also configure a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server through Web services.</span></span> <span data-ttu-id="60c69-140">有关如何定义基于 Web 的客户端的信息，请参阅 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="60c69-140">For information about how to define a Web-based client, see [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="60c69-141">如果您具有已经为 Web 服务配置的服务器的访问权限，则您可以在首次创建连接时指定连接类型。</span><span class="sxs-lookup"><span data-stu-id="60c69-141">If you have access to a server that has been configured for Web services, you can specify the connection type when you first create the connection.</span></span>  
  
##### <a name="create-an-http-connection-to-analysis-services"></a><span data-ttu-id="60c69-142">创建与 Analysis Services 的 HTTP 连接</span><span class="sxs-lookup"><span data-stu-id="60c69-142">Create an HTTP connection to Analysis Services</span></span>  
  
1.  <span data-ttu-id="60c69-143">打开 "**新建 Analysis Services 连接**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="60c69-143">Open the **New Analysis Services Connection** dialog box.</span></span>  
  
2.  <span data-ttu-id="60c69-144">对于服务器名称，请键入 http://，后跟分配给 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器的 URL。</span><span class="sxs-lookup"><span data-stu-id="60c69-144">For the server name, type http:// followed by the URL assigned to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span>  
  
3.  <span data-ttu-id="60c69-145">键入访问 Web 服务所需的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="60c69-145">Type the user name and the password that is required to access the Web service.</span></span>  
  
### <a name="connections-in-the-visio-add-in"></a><span data-ttu-id="60c69-146">Visio 外接程序中的连接</span><span class="sxs-lookup"><span data-stu-id="60c69-146">Connections in the Visio Add-In</span></span>  
 <span data-ttu-id="60c69-147">与 Excel 不同，Visio 不提供工具功能区，而且也没有专用于创建或监视连接的按钮。</span><span class="sxs-lookup"><span data-stu-id="60c69-147">Unlike Excel, Visio does not provide a tool ribbon, and there are no buttons specifically for creating or monitoring connections.</span></span> <span data-ttu-id="60c69-148">数据连接是在您首次选择数据挖掘形状并将其放置到 Visio 页中时创建的。</span><span class="sxs-lookup"><span data-stu-id="60c69-148">Instead, the data connection is created when you first select a data mining shape and drop it onto a Visio page.</span></span> <span data-ttu-id="60c69-149">向导会提示您为形状选择模型并设置其他选项。</span><span class="sxs-lookup"><span data-stu-id="60c69-149">A wizard will prompt you to select the model for the shape and to set other options.</span></span>  
  
 <span data-ttu-id="60c69-150">如果以前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在 Excel 中使用了与数据源的连接，则这些连接将作为可能的数据源列出，从中进行选择。</span><span class="sxs-lookup"><span data-stu-id="60c69-150">If you have previously used a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source in Excel, these connections are listed as possible data sources from which to select.</span></span>  
  
##### <a name="create-a-connection-for-a-visio-shape"></a><span data-ttu-id="60c69-151">为 Visio 形状创建连接</span><span class="sxs-lookup"><span data-stu-id="60c69-151">Create a connection for a Visio shape</span></span>  
  
1.  <span data-ttu-id="60c69-152">打开数据挖掘模板，选择某种数据挖掘形状。</span><span class="sxs-lookup"><span data-stu-id="60c69-152">Open the Data Mining Template, and select one of the data mining shapes.</span></span>  
  
2.  <span data-ttu-id="60c69-153">将该形状拖放到空白页上。</span><span class="sxs-lookup"><span data-stu-id="60c69-153">Drag and drop the shape to a blank page.</span></span>  
  
3.  <span data-ttu-id="60c69-154">在 "**选择数据源**" 对话框中，从列表中选择数据源，或单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="60c69-154">In the **Select a data source** dialog box, select a data source from the list, or click **New**.</span></span>  
  
4.  <span data-ttu-id="60c69-155">如果选择 "**新建**"，请按照前面所述的过程指定服务器和目录名称，或通过 Web 服务进行连接。</span><span class="sxs-lookup"><span data-stu-id="60c69-155">If you select **New**, follow the procedure that is described earlier to specify a server and catalog name, or to connect through a Web service.</span></span>  
  
##  <a name="changing-connections"></a><a name="bkmk_change"></a><span data-ttu-id="60c69-156">更改连接</span><span class="sxs-lookup"><span data-stu-id="60c69-156">Changing Connections</span></span>  
 <span data-ttu-id="60c69-157">可以在同一个工作表中创建多个连接，但一次只能有一个连接处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="60c69-157">You can create multiple connections in the same worksheet, but only one connection can be active at a time.</span></span> <span data-ttu-id="60c69-158">当前连接的名称显示在**连接**按钮中。</span><span class="sxs-lookup"><span data-stu-id="60c69-158">The name of the current connection is displayed in the **Connection** button.</span></span>  
  
 <span data-ttu-id="60c69-159">在 Excel 数据挖掘客户端中，您还可以通过单击 "**跟踪**"，然后单击 "**当前连接**" 来验证当前连接的连接字符串和状态。</span><span class="sxs-lookup"><span data-stu-id="60c69-159">In the Data Mining Client for Excel, you can also verify the connection string and status for the current connection by clicking **Trace** and then clicking **Current Connection**.</span></span>  
  
#### <a name="use-a-different-server-connection"></a><span data-ttu-id="60c69-160">使用其他服务器连接</span><span class="sxs-lookup"><span data-stu-id="60c69-160">Use a different server connection</span></span>  
  
1.  <span data-ttu-id="60c69-161">单击 "**连接**"。</span><span class="sxs-lookup"><span data-stu-id="60c69-161">Click **Connection**.</span></span>  
  
2.  <span data-ttu-id="60c69-162">在 " **Analysis Services 连接**" 窗格中，从 "**其他连接**" 列表中选择一个连接，然后单击 "**设置为当前**"。</span><span class="sxs-lookup"><span data-stu-id="60c69-162">In the **Analysis Services Connections** pane, select a connection from the **Other Connections** list, and click **Make Current**.</span></span>  
  
3.  <span data-ttu-id="60c69-163">单击 "**测试连接**" 以验证连接是否可用。</span><span class="sxs-lookup"><span data-stu-id="60c69-163">Click **Test Connection** to verify that the connection is available.</span></span>  
  
 <span data-ttu-id="60c69-164">挖掘模型完成处理之后，结果将存储在本地；您关闭与一个服务器的连接，然后连接到另一个服务器，这对数据没有任何影响。</span><span class="sxs-lookup"><span data-stu-id="60c69-164">After a mining model has finished processing, the results are stored locally, and there is no effect on the data if you close the connection to one server and then connect to another server.</span></span> <span data-ttu-id="60c69-165">不过，在处理数据挖掘模型的过程中，您应避免更改连接或中断连接，因为这可能会损坏数据。</span><span class="sxs-lookup"><span data-stu-id="60c69-165">However, you should avoid changing connections or losing the connection when a data mining model is being processed, because this could corrupt data.</span></span>  
  
#### <a name="modify-an-existing-server-connection"></a><span data-ttu-id="60c69-166">修改现有服务器连接</span><span class="sxs-lookup"><span data-stu-id="60c69-166">Modify an existing server connection</span></span>  
  
1.  <span data-ttu-id="60c69-167">您不能修改现有连接；如果要连接到另一数据库或另一服务器，应创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="60c69-167">You cannot modify an existing connection; if you want to connect to a different database or a different server, you should create a new connection.</span></span>  
  
2.  <span data-ttu-id="60c69-168">如果必须修改连接字符串以增加查询超时或添加特定于您的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的其他参数，有一种选择是编辑 .dmc 文件，连接字符串就存储在该文件中。</span><span class="sxs-lookup"><span data-stu-id="60c69-168">If you must modify the connection string to increase the query timeout or add other parameters specific to your instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], one option is to edit the .dmc file, where the connection string is stored.</span></span>  
  
     <span data-ttu-id="60c69-169">\<drive:>\Users \\<myusername \> \AppData\Local\Microsoft\Data 挖掘外接程序</span><span class="sxs-lookup"><span data-stu-id="60c69-169">\<drive:>\Users\\<myusername\>\AppData\Local\Microsoft\Data Mining Add-in</span></span>  
  
##  <a name="connecting-to-external-data-sources"></a><a name="bkmk_extconnections"></a><span data-ttu-id="60c69-170">连接到外部数据源</span><span class="sxs-lookup"><span data-stu-id="60c69-170">Connecting to External Data Sources</span></span>  
 <span data-ttu-id="60c69-171">虽然 "**分析**" 功能区中的工具仅适用于 Excel 中的数据，但使用 "**数据挖掘**" 功能区中的工具可以直接连接到外部数据源，以用作模型的输入或进行采样。</span><span class="sxs-lookup"><span data-stu-id="60c69-171">Whereas the tools in the **Analyze** ribbon work exclusively with data in Excel, the tools in the **Data Mining** ribbon let you connect directly to external data sources to use as inputs for your model, or for sampling.</span></span>  
  
 <span data-ttu-id="60c69-172">这些外接程序中的以下工具支持使用外部数据进行数据挖掘：</span><span class="sxs-lookup"><span data-stu-id="60c69-172">The following tools in these add-ins support use of external data for data mining:</span></span>  
  
-   [<span data-ttu-id="60c69-173">&#40;SQL Server 数据挖掘外接程序的示例数据&#41;</span><span class="sxs-lookup"><span data-stu-id="60c69-173">Sample Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](sample-data-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="60c69-174">用于 Excel 的数据挖掘外接程序 &#40;分类向导&#41;</span><span class="sxs-lookup"><span data-stu-id="60c69-174">Classify Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](classify-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="60c69-175">估计向导 &#40;Excel 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="60c69-175">Estimate Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="60c69-176">群集向导 &#40;Excel 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="60c69-176">Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="60c69-177">预测向导 &#40;Excel 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="60c69-177">Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="60c69-178">SQL Server 数据挖掘外接程序创建挖掘结构 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="60c69-178">Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;</span></span>](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="60c69-179">SQL Server 数据挖掘外接程序的准确性图表 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="60c69-179">Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="60c69-180">SQL Server 数据挖掘外接程序的利润图 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="60c69-180">Profit Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](profit-chart-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="60c69-181">SQL Server 数据挖掘外接程序的分类矩阵 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="60c69-181">Classification Matrix &#40;SQL Server Data Mining Add-ins&#41;</span></span>](classification-matrix-sql-server-data-mining-add-ins.md)  
  
### <a name="using-analysis-services-as-a-data-source"></a><span data-ttu-id="60c69-182">使用 Analysis Services 作为数据源</span><span class="sxs-lookup"><span data-stu-id="60c69-182">Using Analysis Services as a Data Source</span></span>  
 <span data-ttu-id="60c69-183">您不能直接访问 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多维数据集或表格模型中存储的数据。</span><span class="sxs-lookup"><span data-stu-id="60c69-183">You cannot directly access data stored in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube or tabular model.</span></span> <span data-ttu-id="60c69-184">但可以在 Excel 中创建到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器的连接并使用该数据创建模型。</span><span class="sxs-lookup"><span data-stu-id="60c69-184">Instead, create a connection in Excel to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, and use the data to create a model.</span></span>  
  
### <a name="relational-data-sources"></a><span data-ttu-id="60c69-185">关系数据源</span><span class="sxs-lookup"><span data-stu-id="60c69-185">Relational Data Sources</span></span>  
 <span data-ttu-id="60c69-186">如果要使用关系数据源中的数据作为模型输入，可以连接到以下 SQL Server 版本：</span><span class="sxs-lookup"><span data-stu-id="60c69-186">If you want to use data from a relational source as input to your model, you can connect to the following versions of SQL Server:</span></span>  
  
-   <span data-ttu-id="60c69-187">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="60c69-187">SQL Server 2008</span></span>  
  
-   <span data-ttu-id="60c69-188">SQL Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="60c69-188">SQL Server 2008 R2</span></span>  
  
-   <span data-ttu-id="60c69-189">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="60c69-189">SQL Server 2012</span></span>  
  
 <span data-ttu-id="60c69-190">也可以从 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 支持作为数据源的任意其他关系数据源中获取数据。</span><span class="sxs-lookup"><span data-stu-id="60c69-190">You can also get data from any other relational data source that is supported as a data source by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="60c69-191">有关支持的数据源的信息，请参阅[多维模型中的数据源](multidimensional-models/data-sources-in-multidimensional-models.md)</span><span class="sxs-lookup"><span data-stu-id="60c69-191">For information about supported data sources, see [Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md)</span></span>  
  
 <span data-ttu-id="60c69-192">请注意，以下数据类型不能用于数据挖掘，如果在生成模型时包括以下数据类型会导致错误：</span><span class="sxs-lookup"><span data-stu-id="60c69-192">Note that the following data types cannot be used for data mining and will result in an error if included when you build a model:</span></span>  
  
-   <span data-ttu-id="60c69-193">ntext</span><span class="sxs-lookup"><span data-stu-id="60c69-193">ntext</span></span>  
  
-   <span data-ttu-id="60c69-194">binary</span><span class="sxs-lookup"><span data-stu-id="60c69-194">binary</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c69-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60c69-195">See Also</span></span>  
 [<span data-ttu-id="60c69-196">&#40;Excel&#41;的数据挖掘客户端跟踪</span><span class="sxs-lookup"><span data-stu-id="60c69-196">Trace &#40;Data Mining Client for Excel&#41;</span></span>](trace-data-mining-client-for-excel.md)  
  
  
