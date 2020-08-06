---
title: SAP BW 源 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 749afb64-3567-4dc9-8431-783d650c25db
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d64af5e0d881e3b7dbbd2cc4e005aa3dbef3c43a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589816"
---
# <a name="sap-bw-source"></a><span data-ttu-id="74d80-102">SAP BW 源</span><span class="sxs-lookup"><span data-stu-id="74d80-102">SAP BW Source</span></span>
  <span data-ttu-id="74d80-103">SAP BW 源是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的源组件。</span><span class="sxs-lookup"><span data-stu-id="74d80-103">The SAP BW source is the source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="74d80-104">因此，SAP BW 源从 SAP Netweaver BW 版本 7 系统提取数据，并将这些数据提供给 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包中的数据流。</span><span class="sxs-lookup"><span data-stu-id="74d80-104">Thus, the SAP BW source extracts data from an SAP Netweaver BW version 7 system and makes this data available to the data flow in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
 <span data-ttu-id="74d80-105">此源具有一个输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="74d80-105">This source has one output and one error output.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="74d80-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="74d80-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="74d80-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="74d80-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="74d80-108">从 SAP Netweaver BW 提取数据要求额外的 SAP 许可。</span><span class="sxs-lookup"><span data-stu-id="74d80-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="74d80-109">请向 SAP 核实以便确认这些要求。</span><span class="sxs-lookup"><span data-stu-id="74d80-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="74d80-110">若要使用 SAP BW 源，必须执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="74d80-110">To use the SAP BW source, you have to do the following tasks:</span></span>  
  
-   [<span data-ttu-id="74d80-111">准备 SAP Netweaver BW 对象</span><span class="sxs-lookup"><span data-stu-id="74d80-111">Prepare the SAP Netweaver BW objects</span></span>](#bkmk_Prepare_Objects)  
  
-   [<span data-ttu-id="74d80-112">连接至 SAP Netweaver BW 系统</span><span class="sxs-lookup"><span data-stu-id="74d80-112">Connect to the SAP Netweaver BW system</span></span>](#bkmk_Connect_Database)  
  
-   [<span data-ttu-id="74d80-113">配置 SAP BW 源</span><span class="sxs-lookup"><span data-stu-id="74d80-113">Configure the SAP BW source</span></span>](#bkmk_Configure_Source)  
  
##  <a name="preparing-the-sap-netweaver-bw-objects-that-the-source-requires"></a><a name="bkmk_Prepare_Objects"></a> <span data-ttu-id="74d80-114">准备源所需的 SAP Netweaver BW 对象</span><span class="sxs-lookup"><span data-stu-id="74d80-114">Preparing the SAP Netweaver BW Objects That the Source Requires</span></span>  
 <span data-ttu-id="74d80-115">SAP BW 源要求 SAP Netweaver BW 系统中存在某些对象才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="74d80-115">The SAP BW source requires that certain objects are in the SAP Netweaver BW system before the source can function.</span></span> <span data-ttu-id="74d80-116">如果这些对象还不存在，必须按照下列步骤在 SAP Netweaver BW 系统中创建并配置这些对象。</span><span class="sxs-lookup"><span data-stu-id="74d80-116">If these objects do not already exist, you have to follow these steps to create and configure these objects in the SAP Netweaver BW system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74d80-117">有关这些对象和配置步骤的更多详细信息，请参阅 SAP Netweaver BW 文档。</span><span class="sxs-lookup"><span data-stu-id="74d80-117">For additional details about these objects and these configuration steps, see the SAP Netweaver BW documentation.</span></span>  
  
1.  <span data-ttu-id="74d80-118">通过 SAP GUI 登录 SAP Netweaver BW，输入事务代码 SM59，创建一个 RFC 目标：</span><span class="sxs-lookup"><span data-stu-id="74d80-118">Log on to SAP Netweaver BW through the SAP GUI, enter transaction code SM59, and create an RFC destination:</span></span>  
  
    1.  <span data-ttu-id="74d80-119">对于“连接类型”，选择“TCP/IP”   。</span><span class="sxs-lookup"><span data-stu-id="74d80-119">For **Connection Type**, select **TCP/IP**.</span></span>  
  
    2.  <span data-ttu-id="74d80-120">对于 **“激活类型”** ，选择 **“注册服务器程序”** 。</span><span class="sxs-lookup"><span data-stu-id="74d80-120">For **Activation Type**, select **Registered Server Program**.</span></span>  
  
    3.  <span data-ttu-id="74d80-121">对于“与目标系统的通信类型”  ，选择“非 Unicode (非活动 MDMP 设置)”  。</span><span class="sxs-lookup"><span data-stu-id="74d80-121">For **Communication Type with Target System**, select **Non-Unicode (Inactive MDMP Settings)**.</span></span>  
  
    4.  <span data-ttu-id="74d80-122">分配适当的程序 ID。</span><span class="sxs-lookup"><span data-stu-id="74d80-122">Assign an appropriate Program ID.</span></span>  
  
2.  <span data-ttu-id="74d80-123">创建 Open Hub 目标：</span><span class="sxs-lookup"><span data-stu-id="74d80-123">Create an Open Hub Destination:</span></span>  
  
    1.  <span data-ttu-id="74d80-124">转到 Administrator Workbench（事务代码 RSA1），在左窗格中选择  “Open Hub 目标”。</span><span class="sxs-lookup"><span data-stu-id="74d80-124">Go to the Administrator Workbench (transaction code RSA1) and, in the left pane, select **Open Hub Destination**.</span></span>  
  
    2.  <span data-ttu-id="74d80-125">在中间窗格中，右键单击 InfoArea，然后选择  “创建 Open Hub 目标”。</span><span class="sxs-lookup"><span data-stu-id="74d80-125">In the middle pane, right-click an InfoArea, and then select **"Create Open Hub Destination"**.</span></span>  
  
    3.  <span data-ttu-id="74d80-126">对于 **“目标类型”** ，选择 **“第三方工具”** ，然后输入之前创建的 RFC 目标。</span><span class="sxs-lookup"><span data-stu-id="74d80-126">For **Destination Type**, select **"Third Party Tool"**, and then enter the previously created RFC Destination.</span></span>  
  
    4.  <span data-ttu-id="74d80-127">保存并激活新的 Open Hub 目标。</span><span class="sxs-lookup"><span data-stu-id="74d80-127">Save and activate the new Open Hub Destination.</span></span>  
  
3.  <span data-ttu-id="74d80-128">创建数据传输进程 (DTP)：</span><span class="sxs-lookup"><span data-stu-id="74d80-128">Create a Data Transfer Process (DTP):</span></span>  
  
    1.  <span data-ttu-id="74d80-129">在 InfoArea 的中间窗格中，右键单击之前创建的目标，然后选择  “创建数据传输进程”。</span><span class="sxs-lookup"><span data-stu-id="74d80-129">In the middle pane of the InfoArea, right-click the previously created destination, and then select **"Create data transfer process"**.</span></span>  
  
    2.  <span data-ttu-id="74d80-130">配置、保存并激活 DTP。</span><span class="sxs-lookup"><span data-stu-id="74d80-130">Configure, save, and activate the DTP.</span></span>  
  
    3.  <span data-ttu-id="74d80-131">在菜单中单击 **“转到”** ，然后单击 **“批管理器设置”** 。</span><span class="sxs-lookup"><span data-stu-id="74d80-131">On the menu, click **Goto**, and then click **Settings for Batch Manager**.</span></span>  
  
    4.  <span data-ttu-id="74d80-132">对于串行处理，将 **“进程数”** 更新为 1。</span><span class="sxs-lookup"><span data-stu-id="74d80-132">Update **Number of processes** to 1 for serial processing.</span></span>  
  
4.  <span data-ttu-id="74d80-133">创建进程链：</span><span class="sxs-lookup"><span data-stu-id="74d80-133">Create a process chain:</span></span>  
  
    1.  <span data-ttu-id="74d80-134">配置进程链时，选择 **“使用元数据链或 API 启动”** 作为 **“启动进程”** 的 **“计划选项”** ，然后添加之前创建的 DTP 作为下一节点。</span><span class="sxs-lookup"><span data-stu-id="74d80-134">When configuring the process chain, select the **Start Using Metadata Chain or API** as the **Scheduling Options** of the **Start Process**, and then add the previously created DTP as the subsequent node.</span></span>  
  
    2.  <span data-ttu-id="74d80-135">保存并激活进程链。</span><span class="sxs-lookup"><span data-stu-id="74d80-135">Save and activate the process chain.</span></span>  
  
     <span data-ttu-id="74d80-136">SAP BW 源可调用进程链来激活数据传输进程。</span><span class="sxs-lookup"><span data-stu-id="74d80-136">The SAP BW source can call the process chain to activate the data transfer process.</span></span>  
  
##  <a name="connecting-to-the-sap-netweaver-bw-system"></a><a name="bkmk_Connect_Database"></a> <span data-ttu-id="74d80-137">连接至 SAP Netweaver BW 系统</span><span class="sxs-lookup"><span data-stu-id="74d80-137">Connecting to the SAP Netweaver BW System</span></span>  
 <span data-ttu-id="74d80-138">在连接 SAP Netweaver BW 版本 7 系统时，SAP BW 源会使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 包中的 SAP BW 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="74d80-138">To connect to the SAP Netweaver BW version 7 system, the SAP BW source uses the SAP BW connection manager that is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package.</span></span> <span data-ttu-id="74d80-139">SAP BW 连接管理器是 SAP BW 源唯一可以使用的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="74d80-139">The SAP BW connection manager is the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] connection manager that the SAP BW source can use.</span></span>  
  
 <span data-ttu-id="74d80-140">有关 SAP BW 连接管理器的详细信息，请参阅 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="74d80-140">For more information about the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
##  <a name="configuring-the-sap-bw-source"></a><a name="bkmk_Configure_Source"></a> <span data-ttu-id="74d80-141">配置 SAP BW 源</span><span class="sxs-lookup"><span data-stu-id="74d80-141">Configuring the SAP BW Source</span></span>  
 <span data-ttu-id="74d80-142">可以按下列方式配置 SAP BW 源：</span><span class="sxs-lookup"><span data-stu-id="74d80-142">You can configure the SAP BW source in the following ways:</span></span>  
  
-   <span data-ttu-id="74d80-143">查找并选择用来提取数据的 Open Hub Service (OHS) 目标。</span><span class="sxs-lookup"><span data-stu-id="74d80-143">Look up and select the Open Hub Service (OHS) destination to use to extract data.</span></span>  
  
-   <span data-ttu-id="74d80-144">选择以下方法之一作为数据提取方法：</span><span class="sxs-lookup"><span data-stu-id="74d80-144">Select one of the following methods for extracting data:</span></span>  
  
    -   <span data-ttu-id="74d80-145">触发进程链。</span><span class="sxs-lookup"><span data-stu-id="74d80-145">Trigger a process chain.</span></span> <span data-ttu-id="74d80-146">此情况下， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包会启动提取进程。</span><span class="sxs-lookup"><span data-stu-id="74d80-146">In this case, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package starts the extraction process.</span></span>  
  
    -   <span data-ttu-id="74d80-147">等待 SAP Netweaver BW 系统发出开始提取的通知。</span><span class="sxs-lookup"><span data-stu-id="74d80-147">Wait for notification from the SAP Netweaver BW system to begin an extraction.</span></span> <span data-ttu-id="74d80-148">此情况下，SAP Netweaver BW 系统会启动提取进程。</span><span class="sxs-lookup"><span data-stu-id="74d80-148">In this case, the SAP Netweaver BW system starts the extraction process.</span></span>  
  
    -   <span data-ttu-id="74d80-149">检索与某个特定请求 ID 关联的数据。</span><span class="sxs-lookup"><span data-stu-id="74d80-149">Retrieve the data that is associated with a particular Request ID.</span></span> <span data-ttu-id="74d80-150">此情况下，SAP Netweaver BW 系统已将数据提取到内部表中， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包只需读取这些数据。</span><span class="sxs-lookup"><span data-stu-id="74d80-150">In this case, the SAP Netweaver BW system has already extracted the data to an internal table, and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package just reads the data.</span></span>  
  
-   <span data-ttu-id="74d80-151">根据所选择的数据提取方法，提供以下额外信息：</span><span class="sxs-lookup"><span data-stu-id="74d80-151">Depending on the method selected for extracting data, provide the following additional information:</span></span>  
  
    -   <span data-ttu-id="74d80-152">对于  “P - 触发进程链”选项，提供网关主机名称、网关服务名称、RFC 目标的程序 ID 和进程链的名称。</span><span class="sxs-lookup"><span data-stu-id="74d80-152">For the **P - Trigger Process Chain** option, provide the gateway host name, gateway service name, program ID for the RFC destination, and name of the process chain.</span></span>  
  
    -   <span data-ttu-id="74d80-153">对于  “W - 等待通知”选项，提供网关主机名称、网关服务器名称和 RFC 目标的程序 ID。</span><span class="sxs-lookup"><span data-stu-id="74d80-153">For the **W - Wait for Notify** option, provide the gateway host name, the gateway server name, and the program ID for the RFC destination.</span></span> <span data-ttu-id="74d80-154">还可以指定超时时间（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="74d80-154">You can also specify the timeout (in seconds).</span></span> <span data-ttu-id="74d80-155">超时是源收到通知前的最长等待时间。</span><span class="sxs-lookup"><span data-stu-id="74d80-155">The timeout is the maximum period of time that the source will wait to be notified.</span></span>  
  
    -   <span data-ttu-id="74d80-156">对于“E - 仅提取”  选项，提供请求 ID。</span><span class="sxs-lookup"><span data-stu-id="74d80-156">For the **E - Extract Only** option, provide the Request ID.</span></span>  
  
-   <span data-ttu-id="74d80-157">指定字符串转换规则。</span><span class="sxs-lookup"><span data-stu-id="74d80-157">Specify rules for string conversion.</span></span> <span data-ttu-id="74d80-158">（例如，根据 SAP Netweaver BW 是否为 Unicode 转换所有字符串，或者将所有字符串转换为 `varchar` 或 `nvarchar`）。</span><span class="sxs-lookup"><span data-stu-id="74d80-158">(For example, convert all strings depending on whether the SAP Netweaver BW system is Unicode or not, or convert all strings to `varchar` or `nvarchar`).</span></span>  
  
-   <span data-ttu-id="74d80-159">使用您选择的选项预览要提取的数据。</span><span class="sxs-lookup"><span data-stu-id="74d80-159">Use the options that you have selected to preview the data to be extracted.</span></span>  
  
 <span data-ttu-id="74d80-160">您还可以启用源 RFC 函数调用的日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="74d80-160">You can also enable logging of RFC function calls by the source.</span></span> <span data-ttu-id="74d80-161">（此日志记录与可对 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包启用的可选日志记录是分开进行的。）配置源将要使用的 SAP BW 连接管理器时，会启用 RFC 函数调用的日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="74d80-161">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) You enable logging of RFC function calls when you configure the SAP BW connection manager that the source will use.</span></span> <span data-ttu-id="74d80-162">有关如何配置 SAP BW 连接管理器的详细信息，请参阅 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="74d80-162">For more information about how to configure the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
 <span data-ttu-id="74d80-163">如果您不知道配置源所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="74d80-163">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="74d80-164">有关演示如何配置和使用 SAP BW 连接管理器、源和目标的演练，请参阅白皮书 [将 SQL Server 2008 Integration Services 与 SAP BI 7.0 一起使用](https://go.microsoft.com/fwlink/?LinkID=137090)。</span><span class="sxs-lookup"><span data-stu-id="74d80-164">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="74d80-165">此白皮书还说明如何在 SAP BW 中配置所需的对象。</span><span class="sxs-lookup"><span data-stu-id="74d80-165">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-source"></a><span data-ttu-id="74d80-166">使用 SSIS 设计器配置源</span><span class="sxs-lookup"><span data-stu-id="74d80-166">Using the SSIS Designer to Configure the Source</span></span>  
 <span data-ttu-id="74d80-167">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的 SAP BW 源属性的详细信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="74d80-167">For more information about the properties of the SAP BW source that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="74d80-168">SAP BW 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="74d80-168">SAP BW Source Editor &#40;Connection Manager Page&#41;</span></span>](sap-bw-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="74d80-169">SAP BW 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="74d80-169">SAP BW Source Editor &#40;Columns Page&#41;</span></span>](sap-bw-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="74d80-170">SAP BW 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="74d80-170">SAP BW Source Editor &#40;Error Output Page&#41;</span></span>](sap-bw-source-editor-error-output-page.md)  
  
-   [<span data-ttu-id="74d80-171">SAP BW 源编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="74d80-171">SAP BW Source Editor &#40;Advanced Page&#41;</span></span>](sap-bw-source-editor-advanced-page.md)  
  
 <span data-ttu-id="74d80-172">在配置 SAP BW 源的同时，您还可使用各种对话框查找 SAP Netweaver BW 对象或预览源数据。</span><span class="sxs-lookup"><span data-stu-id="74d80-172">While you are configuring the SAP BW source, you can also use various dialog boxes to look up SAP Netweaver BW objects or to preview the source data.</span></span> <span data-ttu-id="74d80-173">有关这些对话框的详细信息，请单击以下主题之一进行了解：</span><span class="sxs-lookup"><span data-stu-id="74d80-173">For more information about these dialog boxes, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="74d80-174">查找 RFC 目标</span><span class="sxs-lookup"><span data-stu-id="74d80-174">Look Up RFC Destination</span></span>](look-up-rfc-destination.md)  
  
-   [<span data-ttu-id="74d80-175">查找进程链</span><span class="sxs-lookup"><span data-stu-id="74d80-175">Look Up Process Chain</span></span>](look-up-process-chain.md)  
  
-   [<span data-ttu-id="74d80-176">请求日志</span><span class="sxs-lookup"><span data-stu-id="74d80-176">Request Log</span></span>](request-log.md)  
  
-   [<span data-ttu-id="74d80-177">预览</span><span class="sxs-lookup"><span data-stu-id="74d80-177">Preview</span></span>](preview.md)  
  
## <a name="see-also"></a><span data-ttu-id="74d80-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74d80-178">See Also</span></span>  
 [<span data-ttu-id="74d80-179">Microsoft Connector 1.1 for SAP BW 组件</span><span class="sxs-lookup"><span data-stu-id="74d80-179">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
