---
title: 连接到数据挖掘服务器 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
- getting started
ms.assetid: 85962ad6-d840-4bc6-905e-c667c3276944
author: minewiskan
ms.author: owend
ms.openlocfilehash: 528dee62e9074b0d9df6668182c04282500639e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579226"
---
# <a name="connect-to-a-data-mining-server"></a><span data-ttu-id="05fa2-102">连接到数据挖掘服务器</span><span class="sxs-lookup"><span data-stu-id="05fa2-102">Connect to a Data Mining Server</span></span>
  <span data-ttu-id="05fa2-103">![“连接”按钮](media/misc-connection.gif "“连接”按钮")</span><span class="sxs-lookup"><span data-stu-id="05fa2-103">![Connections button](media/misc-connection.gif "Connections button")</span></span>  
  
 <span data-ttu-id="05fa2-104">单击 "**连接**" 按钮以选择现有连接，或创建到实例的新连接 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="05fa2-104">Click the **Connection** button to select an existing connection, or to create a new connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="05fa2-105">**为什么需要连接到服务器？**</span><span class="sxs-lookup"><span data-stu-id="05fa2-105">**Why do I need to connect to a server?**</span></span>  
  
 <span data-ttu-id="05fa2-106">创建连接后，将允许您使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器提供的数据挖掘算法，以及利用服务器的优化处理。</span><span class="sxs-lookup"><span data-stu-id="05fa2-106">When you create a connection, it enables you to use the data mining algorithms that are provided by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, and to take advantage of the optimized processing of the server.</span></span>  
  
 <span data-ttu-id="05fa2-107">不必将数据或结果保存到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库或 SQL Server 数据库中。</span><span class="sxs-lookup"><span data-stu-id="05fa2-107">You do not have to keep your data or your results in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or in a SQL Server database.</span></span> <span data-ttu-id="05fa2-108">Excel 数据挖掘外接程序只能使用在 Excel 中存储的数据，或者使用作为 Excel 数据源连接到的数据。</span><span class="sxs-lookup"><span data-stu-id="05fa2-108">The Excel data mining add-ins can work with data stored only in Excel, or data that you connect to as an Excel data source.</span></span>  
  
## <a name="how-to-create-a-new-connection"></a><span data-ttu-id="05fa2-109">如何创建新连接</span><span class="sxs-lookup"><span data-stu-id="05fa2-109">How to Create a New Connection</span></span>  
  
1.  <span data-ttu-id="05fa2-110">单击 "**连接**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="05fa2-110">Click the **Connection** button.</span></span>  
  
2.  <span data-ttu-id="05fa2-111">在 " **Analysis Services 连接**" 对话框中，单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="05fa2-111">In the **Analysis Services Connections** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="05fa2-112">在 "**连接到 Analysis Services** " 对话框中，键入服务器名称。</span><span class="sxs-lookup"><span data-stu-id="05fa2-112">In the **Connect to Analysis Services** dialog box, type a server name.</span></span>  
  
4.  <span data-ttu-id="05fa2-113">指定身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="05fa2-113">Specify the authentication method.</span></span>  
  
5.  <span data-ttu-id="05fa2-114">指定将在其中存储数据挖掘模型的目录或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="05fa2-114">Specify the catalog, or [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, where you will store your data mining models.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05fa2-115">如果尚未创建任何数据库，则您可以使用“(默认值)”来创建连接，然后测试连接；然而，无法向默认连接添加挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="05fa2-115">If you have not created any databases yet, you can use (default) to create and then test the connection; however, you cannot add mining models to the default connection.</span></span> <span data-ttu-id="05fa2-116">创建任何挖掘模型之前，应该创建到现有数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="05fa2-116">Before you create any mining models, you should create a connection to an existing database.</span></span>  
  
6.  <span data-ttu-id="05fa2-117">如果是通过 Web 服务连接到服务器，请键入该 Web 服务所需的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="05fa2-117">If you are connecting to the server via a Web service, type the user name and password required by the Web service.</span></span>  
  
7.  <span data-ttu-id="05fa2-118">键入新连接的友好名称。</span><span class="sxs-lookup"><span data-stu-id="05fa2-118">Type a friendly name for the new connection.</span></span>  
  
8.  <span data-ttu-id="05fa2-119">单击 "**测试连接**" 以验证服务器是否可用。</span><span class="sxs-lookup"><span data-stu-id="05fa2-119">Click **Test Connection** to verify that the server is available.</span></span>  
  
## <a name="troubleshooting-connections"></a><span data-ttu-id="05fa2-120">排除连接故障</span><span class="sxs-lookup"><span data-stu-id="05fa2-120">Troubleshooting Connections</span></span>  
 <span data-ttu-id="05fa2-121">本节回答了有关与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的连接的一些常见问题。</span><span class="sxs-lookup"><span data-stu-id="05fa2-121">This section provides answers to some common questions about connections to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="05fa2-122">**收到一条消息，显示 "找不到连接"。**</span><span class="sxs-lookup"><span data-stu-id="05fa2-122">**I get a message saying "No connection found."**</span></span>  
  
 <span data-ttu-id="05fa2-123">如果按钮下半部分的文本显示 "**无连接**"，则表示尚未创建与数据库的连接 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 或连接失败。</span><span class="sxs-lookup"><span data-stu-id="05fa2-123">If the text in the lower part of the button says **No Connection**, it means that you have not created a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or that the connection failed.</span></span> <span data-ttu-id="05fa2-124">您可以继续处理来自 Access 或其他数据源的 Excel 中的数据，但如果要创建数据挖掘模型或运行预测查询，则必须拥有活动连接。</span><span class="sxs-lookup"><span data-stu-id="05fa2-124">You can continue to work with data in Excel from Access or other sources, but to create a data mining model or run a prediction query you must have an active connection.</span></span>  
  
 <span data-ttu-id="05fa2-125">**假设我无权使用该服务器？**</span><span class="sxs-lookup"><span data-stu-id="05fa2-125">**Suppose I don't have permission to use the server?**</span></span>  
  
 <span data-ttu-id="05fa2-126">如果您没有足够的权限在服务器上存储挖掘模型，或者您想要试验数据挖掘而不保存您的工作，则可以使用表分析工具创建临时数据结构和临时模型。</span><span class="sxs-lookup"><span data-stu-id="05fa2-126">If you do not have sufficient permissions to store your mining models on the server, or if you want to experiment with data mining and not save your work, you can use the Table Analysis Tools, which create temporary data structures and temporary models.</span></span> <span data-ttu-id="05fa2-127">您仍需要能在服务器上存储临时模型。</span><span class="sxs-lookup"><span data-stu-id="05fa2-127">You still need to be able to store temporary models on the server.</span></span> <span data-ttu-id="05fa2-128">要求管理员在服务器上启用*会话挖掘模型*。</span><span class="sxs-lookup"><span data-stu-id="05fa2-128">Ask your administrator to enable use of *session mining models* on the server.</span></span>  
  
 <span data-ttu-id="05fa2-129">如果您想确保保存模型，可以禁用使用临时模型的选项，或可以在数据挖掘客户端中使用向导。</span><span class="sxs-lookup"><span data-stu-id="05fa2-129">If you want to ensure that your models are saved, you can disable the option to use temporary models, or you can use the wizards in the Data Mining Client.</span></span> <span data-ttu-id="05fa2-130">这些向导在服务器上存储所有模型。</span><span class="sxs-lookup"><span data-stu-id="05fa2-130">These wizards store all models on the server.</span></span> <span data-ttu-id="05fa2-131">您将需要对存储模型的数据库具有管理访问权限，所以，我们建议您让管理员创建一个数据库，该数据库专门用于使用外接程序创建挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="05fa2-131">You will need administrative access to the database where the models are stored, so we recommend that you get the administrator to create a database especially for creating mining models with the add-ins.</span></span>  
  
 <span data-ttu-id="05fa2-132">**我的连接断开；是否我会丢失所做的所有工作？**</span><span class="sxs-lookup"><span data-stu-id="05fa2-132">**I lost my connection; did I lose all my work?**</span></span>  
  
 <span data-ttu-id="05fa2-133">如果终止与服务器的连接，您的结果和数据将不会丢失，因为它们存储在 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="05fa2-133">If you terminate the connection to the server, your results and data will not be lost, because they are stored in Excel.</span></span> <span data-ttu-id="05fa2-134">但是，如果您创建了一些临时模型，则在一个较短的时间后这些模型将从服务器中删除。</span><span class="sxs-lookup"><span data-stu-id="05fa2-134">However, if you created some temporary models, those models will be deleted from the server after a short time.</span></span> <span data-ttu-id="05fa2-135">如果暂时失去了连接，则在某些情况下，模型将不会被删除。</span><span class="sxs-lookup"><span data-stu-id="05fa2-135">So if you lose the connection temporarily, sometime the models won't be deleted yet.</span></span>  
  
 <span data-ttu-id="05fa2-136">生成的任何数据或结果将不丢失，因为所有报表和表存储在 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="05fa2-136">Any data or results that were generated will not be lost, because all reports and tables are stored in Excel.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05fa2-137">外接程序与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器进行通信时，不要断开与服务器或网络的连接。</span><span class="sxs-lookup"><span data-stu-id="05fa2-137">Do not disconnect from the server or from the network while the add-in is communicating with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="05fa2-138">例如，不要在创建模型或处理数据时断开连接。</span><span class="sxs-lookup"><span data-stu-id="05fa2-138">For example, never disconnect when a model is being created, or when the data is being processed.</span></span> <span data-ttu-id="05fa2-139">在某些情况下，可能会损坏您的数据。</span><span class="sxs-lookup"><span data-stu-id="05fa2-139">In some situations your data could be corrupted.</span></span>  
  
 <span data-ttu-id="05fa2-140">**我无法使用 Visio 工具连接到模型**</span><span class="sxs-lookup"><span data-stu-id="05fa2-140">**I cannot connect to the model using the Visio tools**</span></span>  
  
 <span data-ttu-id="05fa2-141">Visio 数据挖掘模板无法使用临时挖掘结构和模型。</span><span class="sxs-lookup"><span data-stu-id="05fa2-141">The Data Mining Templates for Visio cannot use temporary mining structures and models.</span></span> <span data-ttu-id="05fa2-142">若要创建某个挖掘模型的关系图，该模型必须存储在服务器上。</span><span class="sxs-lookup"><span data-stu-id="05fa2-142">To create a diagram of a mining model, the model must be stored on a server.</span></span>  
  
 <span data-ttu-id="05fa2-143">**我如何监视连接的使用情况？**</span><span class="sxs-lookup"><span data-stu-id="05fa2-143">**How can I monitor usage of the connection?**</span></span>  
  
 <span data-ttu-id="05fa2-144">[&#40;Excel&#41;工具的数据挖掘客户端的跟踪](trace-data-mining-client-for-excel.md)将创建外接程序与指定服务器之间的所有活动的日志。</span><span class="sxs-lookup"><span data-stu-id="05fa2-144">The [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md) tool creates a log of all activity between the add-ins and the specified server.</span></span>  
  
 <span data-ttu-id="05fa2-145">若要启用会话模型监视，请在 "**跟踪**器" 对话框中选择 "**使用会话模型**" 选项。</span><span class="sxs-lookup"><span data-stu-id="05fa2-145">To enable monitoring of session models, select the **Use session models** option in the **Tracer** dialog box.</span></span>  
  
 <span data-ttu-id="05fa2-146">通过跟踪，您可以在创建模型和结构时查看生成的 DMX 和 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="05fa2-146">The trace lets you view the DMX and XMLA commands generated while models and structures are being created.</span></span> <span data-ttu-id="05fa2-147">您还可以查看客户端为在 Excel 中生成结果和报告而发送的查询。</span><span class="sxs-lookup"><span data-stu-id="05fa2-147">You can also view the queries that are sent by the client to generate results and reports in Excel.</span></span>  
  
 <span data-ttu-id="05fa2-148">**什么是临时模型？如何保存临时模型？**</span><span class="sxs-lookup"><span data-stu-id="05fa2-148">**What is a temporary model? How can I save a temporary model?**</span></span>  
  
 <span data-ttu-id="05fa2-149">默认情况下，Excel 表分析工具创建临时数据结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="05fa2-149">The Table Analysis Tools for Excel by default creates temporary data structures and mining models.</span></span> <span data-ttu-id="05fa2-150">只要保持工作簿打开并且不从 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 断开连接，即可持续浏览和查询临时模型。</span><span class="sxs-lookup"><span data-stu-id="05fa2-150">You can continue to browse and query temporary models as long as you keep the workbook open and do not disconnect from [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="05fa2-151">只要您关闭 Excel 工作簿，或者更改或结束与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的连接，则创建的所有结构和模型都将被删除。</span><span class="sxs-lookup"><span data-stu-id="05fa2-151">The structures and models that you have created will be deleted as soon as you close the Excel workbook, or if you change or end your connection to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="05fa2-152">在您在 Excel 数据挖掘客户端中完成某一向导后，模型将默认保存到服务器中，但在每个向导的最后一页上，存在用来使用临时模型的选项。</span><span class="sxs-lookup"><span data-stu-id="05fa2-152">When you complete a wizard in the Data Mining Client for Excel, models are saved to the server by default, but on the final page of each wizard there is the option to use a temporary model.</span></span> <span data-ttu-id="05fa2-153">如果选择此选项，则所创建的数据挖掘结构和模型都将存储在一个临时文件中。</span><span class="sxs-lookup"><span data-stu-id="05fa2-153">If you select this option, the data mining structure and model that you created are stored in a temporary file.</span></span> <span data-ttu-id="05fa2-154">只要 Excel 保持打开状态，您就可浏览、管理和修改结构和模型。</span><span class="sxs-lookup"><span data-stu-id="05fa2-154">You can browse, manage, and modify the structure and model as long as Excel remains open.</span></span> <span data-ttu-id="05fa2-155">但是，关闭 Excel 后，该结构及其相关模型都将被删除。</span><span class="sxs-lookup"><span data-stu-id="05fa2-155">However, once you close Excel, the structure and any related models are deleted.</span></span>  
  
 <span data-ttu-id="05fa2-156">还可以通过使用 "**数据挖掘高级查询编辑器**"，并选择其中一个 DMX 模板来显式创建临时结构或模型。</span><span class="sxs-lookup"><span data-stu-id="05fa2-156">You can also explicitly create a temporary structure or model by using the **Data Mining Advanced Query Editor** and selecting one of the DMX templates.</span></span> <span data-ttu-id="05fa2-157">添加 `USE SESSION MODELS` 子句可指定对象是临时的。</span><span class="sxs-lookup"><span data-stu-id="05fa2-157">Add the `USE SESSION MODELS` clause to specify that objects be temporary.</span></span>   
  
### <a name="creating-backups-of-mining-models-and-structures"></a><span data-ttu-id="05fa2-158">创建挖掘模型和结构的备份</span><span class="sxs-lookup"><span data-stu-id="05fa2-158">Creating Backups of Mining Models and Structures</span></span>  
 <span data-ttu-id="05fa2-159">若要创建模型或结构的备份，你可以在 Excel 数据挖掘客户端中使用 "[管理模型" &#40;SQL Server 数据挖掘外接&#41;程序](manage-models-sql-server-data-mining-add-ins.md)"进行导出。</span><span class="sxs-lookup"><span data-stu-id="05fa2-159">To create a backup of a model or structure, you can export it by using [Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md), in the Data Mining Client for Excel.</span></span>  
  
 <span data-ttu-id="05fa2-160">如果您创建了一个临时挖掘模型，该模型通常具有难于理解的名称，例如 Table5_593679_TS_62446。</span><span class="sxs-lookup"><span data-stu-id="05fa2-160">If you created a temporary mining model, it typically has a name that is difficult to understand, such as Table5_593679_TS_62446.</span></span> <span data-ttu-id="05fa2-161">但是，您可以使用[跟踪 &#40;Excel&#41;工具的数据挖掘客户端](trace-data-mining-client-for-excel.md)来发现由表分析工具创建的临时结构和模型的名称，然后使用 "**管理模型**" 对其进行备份。</span><span class="sxs-lookup"><span data-stu-id="05fa2-161">However, you can use the [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md) tool to discover the names of temporary structures and models that were created by the Table Analysis Tools and then back them up using **Manage Models**.</span></span>  
  
##### <a name="identify-and-export-a-temporary-model"></a><span data-ttu-id="05fa2-162">标识和导出临时模型</span><span class="sxs-lookup"><span data-stu-id="05fa2-162">Identify and export a temporary model</span></span>  
  
1.  <span data-ttu-id="05fa2-163">在 Excel 数据挖掘客户端的 "**连接**" 组中，单击 "**跟踪**"。</span><span class="sxs-lookup"><span data-stu-id="05fa2-163">In the **Connections** group of the Data Mining Client for Excel, click **Trace**.</span></span>  
  
2.  <span data-ttu-id="05fa2-164">查看连接活动日志，并且通过查看列和可预测输出定位模型（举例）。</span><span class="sxs-lookup"><span data-stu-id="05fa2-164">View the connection activity log, and locate the model by reviewing the columns and predictable outputs (for example).</span></span>  
  
     <span data-ttu-id="05fa2-165">高级用户：如果您熟悉 DMX 或 XMLA，则可以将语句复制到文件以供以后使用。</span><span class="sxs-lookup"><span data-stu-id="05fa2-165">Advanced users: If you are familiar with DMX or XMLA, you can copy the statements to a file for later use.</span></span>  
  
3.  <span data-ttu-id="05fa2-166">找到临时模型和结构的名称后，打开 "**管理模型**" 并选择模型。</span><span class="sxs-lookup"><span data-stu-id="05fa2-166">When you have found the name of the temporary model and structure, open **Manage Model** and select the model.</span></span>  
  
4.  <span data-ttu-id="05fa2-167">单击“导出此挖掘模型”以便在您指定的位置中生成一个脚本文件。</span><span class="sxs-lookup"><span data-stu-id="05fa2-167">Click Export this mining model to generate a script file in a location you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05fa2-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05fa2-168">See Also</span></span>  
 <span data-ttu-id="05fa2-169">[连接到源数据 &#40;Excel 数据挖掘客户端&#41;](connect-to-source-data-data-mining-client-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="05fa2-169">[Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md) </span></span>  
 [<span data-ttu-id="05fa2-170">用于 Excel 的数据挖掘外接 &#40;的服务器配置实用工具&#41;</span><span class="sxs-lookup"><span data-stu-id="05fa2-170">Server Configuration Utility &#40;Data Mining Add-ins for Excel&#41;</span></span>](server-configuration-utility-data-mining-add-ins-for-excel.md)  
  
  
