---
title: SAP BW 源编辑器（“连接管理器”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2a6dc531-85ca-43c5-a65f-3ad3f7d537c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8c6b1782daf8c00b3b3d3a7d13b5ffa00adeeba2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682979"
---
# <a name="sap-bw-source-editor-connection-manager-page"></a><span data-ttu-id="b1458-102">SAP BW 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="b1458-102">SAP BW Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="b1458-103">可以使用 **“SAP BW 源编辑器”** 的 **“连接管理器”** 页，为 SAP BW 源选择 SAP BW 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="b1458-103">Use the **Connection Manager** page of the **SAP BW Source Editor** to select the SAP BW connection manager for the SAP BW source.</span></span> <span data-ttu-id="b1458-104">在该页中，您还可选择用于从 SAP Netweaver BW 系统提取数据的执行模式和参数。</span><span class="sxs-lookup"><span data-stu-id="b1458-104">On this page, you also select the execution mode and the parameters for extracting the data from the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="b1458-105">若要了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 源组件的详细信息，请参阅 [SAP BW 源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="b1458-105">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b1458-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="b1458-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="b1458-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="b1458-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b1458-108">从 SAP Netweaver BW 提取数据要求额外的 SAP 许可。</span><span class="sxs-lookup"><span data-stu-id="b1458-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="b1458-109">请向 SAP 核实以便确认这些要求。</span><span class="sxs-lookup"><span data-stu-id="b1458-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="b1458-110">**打开“连接管理器”页**</span><span class="sxs-lookup"><span data-stu-id="b1458-110">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="b1458-111">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="b1458-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="b1458-112">在“数据流”  选项卡上，双击“SAP BW 源”。</span><span class="sxs-lookup"><span data-stu-id="b1458-112">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="b1458-113">在 **“SAP BW 源编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="b1458-113">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="b1458-114">静态选项</span><span class="sxs-lookup"><span data-stu-id="b1458-114">Static Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1458-115">如果您不知道配置源所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="b1458-115">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="b1458-116">**SAP BW 连接管理器**</span><span class="sxs-lookup"><span data-stu-id="b1458-116">**SAP BW connection manager**</span></span>  
 <span data-ttu-id="b1458-117">从列表中选择一个现有连接管理器，或通过单击“新建”  创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="b1458-117">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="b1458-118">**新建**</span><span class="sxs-lookup"><span data-stu-id="b1458-118">**New**</span></span>  
 <span data-ttu-id="b1458-119">使用“SAP BW 连接管理器”  对话框创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="b1458-119">Create a new connection manager by using the **SAP BW Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="b1458-120">有关此对话框的详细信息，请参阅 [SAP BW Connection Manager Editor](../sap-bw-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="b1458-120">For more information about this dialog box, see [SAP BW Connection Manager Editor](../sap-bw-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="b1458-121">**OHS 目标**</span><span class="sxs-lookup"><span data-stu-id="b1458-121">**OHS destination**</span></span>  
 <span data-ttu-id="b1458-122">选择用来从源中提取数据的 Open Hub Service (OHS) 目标。</span><span class="sxs-lookup"><span data-stu-id="b1458-122">Select the Open Hub Service (OHS) destination to use to extract data from the source.</span></span>  
  
 <span data-ttu-id="b1458-123">**执行模式**</span><span class="sxs-lookup"><span data-stu-id="b1458-123">**Execution mode**</span></span>  
 <span data-ttu-id="b1458-124">指定从源提取数据的方法。</span><span class="sxs-lookup"><span data-stu-id="b1458-124">Specify the method for extracting data from the source.</span></span>  
  
|<span data-ttu-id="b1458-125">选项</span><span class="sxs-lookup"><span data-stu-id="b1458-125">Option</span></span>|<span data-ttu-id="b1458-126">说明</span><span class="sxs-lookup"><span data-stu-id="b1458-126">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b1458-127">**P - 触发进程链**</span><span class="sxs-lookup"><span data-stu-id="b1458-127">**P - Trigger Process Chain**</span></span>|<span data-ttu-id="b1458-128">触发进程链。</span><span class="sxs-lookup"><span data-stu-id="b1458-128">Trigger a process chain.</span></span> <span data-ttu-id="b1458-129">此情况下， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包会启动提取进程。</span><span class="sxs-lookup"><span data-stu-id="b1458-129">In this case, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package starts the extraction process.</span></span>|  
|<span data-ttu-id="b1458-130">**W - 等待通知**</span><span class="sxs-lookup"><span data-stu-id="b1458-130">**W - Wait for Notify**</span></span>|<span data-ttu-id="b1458-131">等待 SAP Netweaver BW 系统发出开始提取数据的通知。</span><span class="sxs-lookup"><span data-stu-id="b1458-131">Wait for notification from the SAP Netweaver BW system to begin extracting the data.</span></span> <span data-ttu-id="b1458-132">此情况下，SAP Netweaver BW 系统会启动提取进程。</span><span class="sxs-lookup"><span data-stu-id="b1458-132">In this case, the SAP Netweaver BW system starts the extraction process.</span></span>|  
|<span data-ttu-id="b1458-133">**E - 仅提取**</span><span class="sxs-lookup"><span data-stu-id="b1458-133">**E - Extract Only**</span></span>|<span data-ttu-id="b1458-134">检索与某个特定请求 ID 关联的数据。</span><span class="sxs-lookup"><span data-stu-id="b1458-134">Retrieve the data that is associated with a particular Request ID.</span></span> <span data-ttu-id="b1458-135">此情况下，SAP Netweaver BW 系统已将数据提取到内部表中， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包只需读取这些数据。</span><span class="sxs-lookup"><span data-stu-id="b1458-135">In this case, the SAP Netweaver BW system has already extracted the data into an internal table, and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package just reads the data.</span></span>|  
  
 <span data-ttu-id="b1458-136">**预览**</span><span class="sxs-lookup"><span data-stu-id="b1458-136">**Preview**</span></span>  
 <span data-ttu-id="b1458-137">打开可在其中预览结果的“预览”  对话框。</span><span class="sxs-lookup"><span data-stu-id="b1458-137">Open the **Preview** dialog box in which you can preview results.</span></span> <span data-ttu-id="b1458-138">有关详细信息，请参阅 [Preview](preview.md)。</span><span class="sxs-lookup"><span data-stu-id="b1458-138">For more information, see [Preview](preview.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b1458-139">**“预览”** 选项位于 SAP BW 源编辑器的 **“连接管理器”** 页，实际用来提取数据。</span><span class="sxs-lookup"><span data-stu-id="b1458-139">The **Preview** option, that is available on the **Connection Manager** page of the SAP BW Source Editor, actually extracts data.</span></span> <span data-ttu-id="b1458-140">如果您已配置 SAP Netweaver BW 只提取自从上次提取后发生更改的数据，则选择 **“预览”** 将从下次数据提取中排除已经预览过的数据。</span><span class="sxs-lookup"><span data-stu-id="b1458-140">If you have configured SAP Netweaver BW to extract only data that has changed since the previous extraction, selecting **Preview** will exclude the previewed data from the next extraction.</span></span>  
  
 <span data-ttu-id="b1458-141">单击 **“预览”** 的同时还会打开 **“请求日志”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b1458-141">When you click **Preview**, you also open the **Request Log** dialog box.</span></span> <span data-ttu-id="b1458-142">您可使用此对话框查看向 SAP Netweaver BW 系统提出样本数据请求的过程中记录的事件。</span><span class="sxs-lookup"><span data-stu-id="b1458-142">You can use this dialog box to view the events that are logged during the request that is made to the SAP Netweaver BW system for sample data.</span></span> <span data-ttu-id="b1458-143">有关详细信息，请参阅 [Request Log](request-log.md)。</span><span class="sxs-lookup"><span data-stu-id="b1458-143">For more information, see [Request Log](request-log.md).</span></span>  
  
## <a name="execution-mode-dynamic-options"></a><span data-ttu-id="b1458-144">执行模式动态选项</span><span class="sxs-lookup"><span data-stu-id="b1458-144">Execution Mode Dynamic Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1458-145">如果您不知道配置源所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="b1458-145">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
### <a name="execution-mode--p---trigger-process-chain"></a><span data-ttu-id="b1458-146">执行模式 = P - 触发进程链</span><span class="sxs-lookup"><span data-stu-id="b1458-146">Execution Mode = P - Trigger Process Chain</span></span>  
  
#### <a name="rfc-destination-options"></a><span data-ttu-id="b1458-147">RFC 目标选项</span><span class="sxs-lookup"><span data-stu-id="b1458-147">RFC Destination Options</span></span>  
 <span data-ttu-id="b1458-148">您无需事先知道并输入这些值。</span><span class="sxs-lookup"><span data-stu-id="b1458-148">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="b1458-149">使用 **“查找”** 按钮查找和选择合适的 RFC 目标。</span><span class="sxs-lookup"><span data-stu-id="b1458-149">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="b1458-150">选定 RFC 目标后，组件会为这些选项输入合适的值。</span><span class="sxs-lookup"><span data-stu-id="b1458-150">After you select an RFC destination, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="b1458-151">**网关主机**</span><span class="sxs-lookup"><span data-stu-id="b1458-151">**Gateway host**</span></span>  
 <span data-ttu-id="b1458-152">输入服务器名称或网关主机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="b1458-152">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="b1458-153">通常，名称或 IP 地址与 SAP 应用程序服务器相同。</span><span class="sxs-lookup"><span data-stu-id="b1458-153">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="b1458-154">**网关服务**</span><span class="sxs-lookup"><span data-stu-id="b1458-154">**Gateway service**</span></span>  
 <span data-ttu-id="b1458-155">输入网关服务的名称，格式为 `sapgwNN`，其中 `NN` 是系统编号。</span><span class="sxs-lookup"><span data-stu-id="b1458-155">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="b1458-156">**程序 ID**</span><span class="sxs-lookup"><span data-stu-id="b1458-156">**Program ID**</span></span>  
 <span data-ttu-id="b1458-157">输入与 RFC 目标关联的程序 ID。</span><span class="sxs-lookup"><span data-stu-id="b1458-157">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="b1458-158">**查找**</span><span class="sxs-lookup"><span data-stu-id="b1458-158">**Look up**</span></span>  
 <span data-ttu-id="b1458-159">使用“查找 RFC 目标”  对话框查找 RFC 目标。</span><span class="sxs-lookup"><span data-stu-id="b1458-159">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="b1458-160">有关此对话框的详细信息，请参阅 [Look Up RFC Destination](look-up-rfc-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="b1458-160">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
#### <a name="process-chain-options"></a><span data-ttu-id="b1458-161">进程链选项</span><span class="sxs-lookup"><span data-stu-id="b1458-161">Process Chain Options</span></span>  
 <span data-ttu-id="b1458-162">您无需事先知道并输入这些值。</span><span class="sxs-lookup"><span data-stu-id="b1458-162">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="b1458-163">使用 **“查找”** 按钮查找和选择合适的进程链。</span><span class="sxs-lookup"><span data-stu-id="b1458-163">Use the **Look up** button to find and select the appropriate process chain.</span></span> <span data-ttu-id="b1458-164">选定进程链后，组件会为该选项输入合适的值。</span><span class="sxs-lookup"><span data-stu-id="b1458-164">After you select a process chain, the component enters the appropriate value for the option.</span></span>  
  
 <span data-ttu-id="b1458-165">**进程链**</span><span class="sxs-lookup"><span data-stu-id="b1458-165">**Process chain**</span></span>  
 <span data-ttu-id="b1458-166">输入由源触发的进程链的名称。</span><span class="sxs-lookup"><span data-stu-id="b1458-166">Enter the name of the process chain to be triggered by the source.</span></span>  
  
 <span data-ttu-id="b1458-167">**查找**</span><span class="sxs-lookup"><span data-stu-id="b1458-167">**Look up**</span></span>  
 <span data-ttu-id="b1458-168">使用“查找进程链”  对话框查找进程链。</span><span class="sxs-lookup"><span data-stu-id="b1458-168">Look up the process chain by using the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="b1458-169">有关此对话框的详细信息，请参阅 [Look Up Process Chain](look-up-process-chain.md)。</span><span class="sxs-lookup"><span data-stu-id="b1458-169">For more information about this dialog box, see [Look Up Process Chain](look-up-process-chain.md).</span></span>  
  
### <a name="execution-mode--w---wait-for-notify"></a><span data-ttu-id="b1458-170">执行模式 = W - 等待通知</span><span class="sxs-lookup"><span data-stu-id="b1458-170">Execution Mode = W - Wait for Notify</span></span>  
  
#### <a name="rfc-destination-options"></a><span data-ttu-id="b1458-171">RFC 目标选项</span><span class="sxs-lookup"><span data-stu-id="b1458-171">RFC Destination Options</span></span>  
 <span data-ttu-id="b1458-172">您无需事先知道并输入这些值。</span><span class="sxs-lookup"><span data-stu-id="b1458-172">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="b1458-173">使用 **“查找”** 按钮查找和选择合适的 RFC 目标。</span><span class="sxs-lookup"><span data-stu-id="b1458-173">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="b1458-174">选定 RFC 目标后，组件会为该选项输入合适的值。</span><span class="sxs-lookup"><span data-stu-id="b1458-174">After you select an RFC destination, the component enters the appropriate values for the options.</span></span>  
  
 <span data-ttu-id="b1458-175">**网关主机**</span><span class="sxs-lookup"><span data-stu-id="b1458-175">**Gateway host**</span></span>  
 <span data-ttu-id="b1458-176">输入服务器名称或网关主机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="b1458-176">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="b1458-177">通常，名称或 IP 地址与 SAP 应用程序服务器相同。</span><span class="sxs-lookup"><span data-stu-id="b1458-177">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="b1458-178">**网关服务**</span><span class="sxs-lookup"><span data-stu-id="b1458-178">**Gateway service**</span></span>  
 <span data-ttu-id="b1458-179">输入网关服务的名称，格式为 `sapgwNN`，其中 `NN` 是系统编号。</span><span class="sxs-lookup"><span data-stu-id="b1458-179">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="b1458-180">**程序 ID**</span><span class="sxs-lookup"><span data-stu-id="b1458-180">**Program ID**</span></span>  
 <span data-ttu-id="b1458-181">输入与 RFC 目标关联的程序 ID。</span><span class="sxs-lookup"><span data-stu-id="b1458-181">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="b1458-182">**查找**</span><span class="sxs-lookup"><span data-stu-id="b1458-182">**Look up**</span></span>  
 <span data-ttu-id="b1458-183">使用“查找 RFC 目标”  对话框查找 RFC 目标。</span><span class="sxs-lookup"><span data-stu-id="b1458-183">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="b1458-184">有关此对话框的详细信息，请参阅 [Look Up RFC Destination](look-up-rfc-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="b1458-184">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
### <a name="execution-mode--e---extract-only"></a><span data-ttu-id="b1458-185">执行模式 = E - 仅提取</span><span class="sxs-lookup"><span data-stu-id="b1458-185">Execution Mode = E - Extract Only</span></span>  
 <span data-ttu-id="b1458-186">**请求 ID**</span><span class="sxs-lookup"><span data-stu-id="b1458-186">**Request ID**</span></span>  
 <span data-ttu-id="b1458-187">输入与提取关联的请求 ID。</span><span class="sxs-lookup"><span data-stu-id="b1458-187">Enter the Request ID that is associated with the extraction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1458-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b1458-188">See Also</span></span>  
 <span data-ttu-id="b1458-189">[SAP BW 源编辑器（“列”页）](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="b1458-189">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="b1458-190">[SAP BW 源编辑器（“错误输出”页）](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="b1458-190">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="b1458-191">[SAP BW 源编辑器（“高级”页）](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="b1458-191">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="b1458-192">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="b1458-192">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
