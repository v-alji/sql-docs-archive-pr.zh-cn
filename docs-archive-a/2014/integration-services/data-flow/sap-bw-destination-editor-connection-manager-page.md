---
title: SAP BW 目标编辑器（“连接管理器”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 04ae38f8-5287-45a3-826a-8aac5dd15a91
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0dd628f1a0fec09490e0d3720610d1232882ed92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682985"
---
# <a name="sap-bw-destination-editor-connection-manager-page"></a><span data-ttu-id="9c559-102">SAP BW 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="9c559-102">SAP BW Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="9c559-103">使用 **“SAP BW 目标编辑器”** 的 **“连接管理器”** 页，选择 SAP BW 目标要使用的 SAP BW 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="9c559-103">Use the **Connection Manager** page of the **SAP BW Destination Editor** to select the SAP BW connection manager that the SAP BW destination will use.</span></span> <span data-ttu-id="9c559-104">在该页中，您还可选择用于向 SAP Netweaver BW 系统加载数据的参数。</span><span class="sxs-lookup"><span data-stu-id="9c559-104">On this page, you also select the parameters for loading the data into the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="9c559-105">若要了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目标的详细信息，请参阅 [SAP BW 目标](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="9c559-105">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9c559-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="9c559-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="9c559-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="9c559-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="9c559-108">**打开“连接管理器”页**</span><span class="sxs-lookup"><span data-stu-id="9c559-108">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="9c559-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="9c559-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="9c559-110">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="9c559-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="9c559-111">在 **“SAP BW 目标编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="9c559-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9c559-112">选项</span><span class="sxs-lookup"><span data-stu-id="9c559-112">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c559-113">如果您不知道配置目标所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="9c559-113">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="9c559-114">**SAP BW 连接管理器**</span><span class="sxs-lookup"><span data-stu-id="9c559-114">**SAP BW connection manager**</span></span>  
 <span data-ttu-id="9c559-115">从列表中选择一个现有连接管理器，或通过单击“新建”  创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="9c559-115">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="9c559-116">**新建**</span><span class="sxs-lookup"><span data-stu-id="9c559-116">**New**</span></span>  
 <span data-ttu-id="9c559-117">使用“SAP BW 连接管理器”  对话框创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="9c559-117">Create a new connection manager by using the **SAP BW Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="9c559-118">**测试加载**</span><span class="sxs-lookup"><span data-stu-id="9c559-118">**Test Load**</span></span>  
 <span data-ttu-id="9c559-119">对要使用您选择的设置加载零行的加载进程进行测试。</span><span class="sxs-lookup"><span data-stu-id="9c559-119">Perform a test of the loading process that uses the settings that you have selected and loads zero rows.</span></span>  
  
### <a name="infopackageinfosource-options"></a><span data-ttu-id="9c559-120">InfoPackage/InfoSource 选项</span><span class="sxs-lookup"><span data-stu-id="9c559-120">InfoPackage/InfoSource Options</span></span>  
 <span data-ttu-id="9c559-121">您无需事先知道并输入这些值。</span><span class="sxs-lookup"><span data-stu-id="9c559-121">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="9c559-122">使用 **“查找”** 按钮查找和选择合适的 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="9c559-122">Use the **Look up** button to find and select the appropriate InfoPackage.</span></span> <span data-ttu-id="9c559-123">选定 InfoPackage 后，组件会为这些选项输入合适的值。</span><span class="sxs-lookup"><span data-stu-id="9c559-123">After you select an InfoPackage, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="9c559-124">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="9c559-124">**InfoPackage**</span></span>  
 <span data-ttu-id="9c559-125">输入 InfoPackage 的名称。</span><span class="sxs-lookup"><span data-stu-id="9c559-125">Enter the name of the InfoPackage.</span></span>  
  
 <span data-ttu-id="9c559-126">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="9c559-126">**InfoSource**</span></span>  
 <span data-ttu-id="9c559-127">输入 InfoSource 的名称。</span><span class="sxs-lookup"><span data-stu-id="9c559-127">Enter the name of the InfoSource.</span></span>  
  
 <span data-ttu-id="9c559-128">类型 </span><span class="sxs-lookup"><span data-stu-id="9c559-128">**Type**</span></span>  
 <span data-ttu-id="9c559-129">输入标识 InfoSource 类型的单字符。</span><span class="sxs-lookup"><span data-stu-id="9c559-129">Enter the single-character that identifies the type of the InfoSource.</span></span> <span data-ttu-id="9c559-130">下表列出了可接受的单字符值。</span><span class="sxs-lookup"><span data-stu-id="9c559-130">The following table lists the acceptable single-character values.</span></span>  
  
|<span data-ttu-id="9c559-131">值</span><span class="sxs-lookup"><span data-stu-id="9c559-131">Value</span></span>|<span data-ttu-id="9c559-132">说明</span><span class="sxs-lookup"><span data-stu-id="9c559-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9c559-133">**D**</span><span class="sxs-lookup"><span data-stu-id="9c559-133">**D**</span></span>|<span data-ttu-id="9c559-134">事务数据</span><span class="sxs-lookup"><span data-stu-id="9c559-134">Transaction data</span></span>|  
|<span data-ttu-id="9c559-135">**M**</span><span class="sxs-lookup"><span data-stu-id="9c559-135">**M**</span></span>|<span data-ttu-id="9c559-136">主数据</span><span class="sxs-lookup"><span data-stu-id="9c559-136">Master data</span></span>|  
|<span data-ttu-id="9c559-137">**T**</span><span class="sxs-lookup"><span data-stu-id="9c559-137">**T**</span></span>|<span data-ttu-id="9c559-138">文本</span><span class="sxs-lookup"><span data-stu-id="9c559-138">Texts</span></span>|  
|<span data-ttu-id="9c559-139">**H**</span><span class="sxs-lookup"><span data-stu-id="9c559-139">**H**</span></span>|<span data-ttu-id="9c559-140">层次结构数据</span><span class="sxs-lookup"><span data-stu-id="9c559-140">Hierarchy data</span></span>|  
  
 <span data-ttu-id="9c559-141">**逻辑系统**</span><span class="sxs-lookup"><span data-stu-id="9c559-141">**Logical system**</span></span>  
 <span data-ttu-id="9c559-142">输入 InfoPackage 关联的逻辑系统的名称。</span><span class="sxs-lookup"><span data-stu-id="9c559-142">Enter the name of the logical system that is associated with the InfoPackage.</span></span>  
  
 <span data-ttu-id="9c559-143">**查找**</span><span class="sxs-lookup"><span data-stu-id="9c559-143">**Look up**</span></span>  
 <span data-ttu-id="9c559-144">使用“查找 InfoPackage”  对话框查找 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="9c559-144">Look up the InfoPackage by using the **Look Up InfoPackage** dialog box.</span></span> <span data-ttu-id="9c559-145">有关此对话框的详细信息，请参阅 [Look Up InfoPackage](look-up-infopackage.md)。</span><span class="sxs-lookup"><span data-stu-id="9c559-145">For more information about this dialog box, see [Look Up InfoPackage](look-up-infopackage.md).</span></span>  
  
### <a name="rfc-destination-options"></a><span data-ttu-id="9c559-146">RFC 目标选项</span><span class="sxs-lookup"><span data-stu-id="9c559-146">RFC Destination Options</span></span>  
 <span data-ttu-id="9c559-147">您无需事先知道并输入这些值。</span><span class="sxs-lookup"><span data-stu-id="9c559-147">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="9c559-148">使用 **“查找”** 按钮查找和选择合适的 RFC 目标。</span><span class="sxs-lookup"><span data-stu-id="9c559-148">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="9c559-149">选定 RFC 目标后，组件会为这些选项输入合适的值。</span><span class="sxs-lookup"><span data-stu-id="9c559-149">After you select an RFC destination, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="9c559-150">**网关主机**</span><span class="sxs-lookup"><span data-stu-id="9c559-150">**Gateway host**</span></span>  
 <span data-ttu-id="9c559-151">输入服务器名称或网关主机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="9c559-151">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="9c559-152">通常，名称或 IP 地址与 SAP 应用程序服务器相同。</span><span class="sxs-lookup"><span data-stu-id="9c559-152">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="9c559-153">**网关服务**</span><span class="sxs-lookup"><span data-stu-id="9c559-153">**Gateway service**</span></span>  
 <span data-ttu-id="9c559-154">输入网关服务的名称，格式为 `sapgwNN`，其中 `NN` 是系统编号。</span><span class="sxs-lookup"><span data-stu-id="9c559-154">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="9c559-155">**程序 ID**</span><span class="sxs-lookup"><span data-stu-id="9c559-155">**Program ID**</span></span>  
 <span data-ttu-id="9c559-156">输入与 RFC 目标关联的程序 ID。</span><span class="sxs-lookup"><span data-stu-id="9c559-156">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="9c559-157">**查找**</span><span class="sxs-lookup"><span data-stu-id="9c559-157">**Look up**</span></span>  
 <span data-ttu-id="9c559-158">使用“查找 RFC 目标”  对话框查找 RFC 目标。</span><span class="sxs-lookup"><span data-stu-id="9c559-158">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="9c559-159">有关此对话框的详细信息，请参阅 [Look Up RFC Destination](look-up-rfc-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="9c559-159">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
### <a name="create-sap-bw-objects-options"></a><span data-ttu-id="9c559-160">创建 SAP BW 对象选项</span><span class="sxs-lookup"><span data-stu-id="9c559-160">Create SAP BW Objects Options</span></span>  
 <span data-ttu-id="9c559-161">**选择 对象类型**</span><span class="sxs-lookup"><span data-stu-id="9c559-161">**Select object type**</span></span>  
 <span data-ttu-id="9c559-162">选择要创建的 SAP Netweaver BW 对象的类型。</span><span class="sxs-lookup"><span data-stu-id="9c559-162">Select the type of SAP Netweaver BW object that you want to create.</span></span> <span data-ttu-id="9c559-163">可以选择下列其中一个类型：</span><span class="sxs-lookup"><span data-stu-id="9c559-163">You can select one of the following types:</span></span>  
  
-   <span data-ttu-id="9c559-164">InfoObject</span><span class="sxs-lookup"><span data-stu-id="9c559-164">InfoObject</span></span>  
  
-   <span data-ttu-id="9c559-165">InfoCube</span><span class="sxs-lookup"><span data-stu-id="9c559-165">InfoCube</span></span>  
  
-   <span data-ttu-id="9c559-166">InfoSource</span><span class="sxs-lookup"><span data-stu-id="9c559-166">InfoSource</span></span>  
  
-   <span data-ttu-id="9c559-167">InfoPackage</span><span class="sxs-lookup"><span data-stu-id="9c559-167">InfoPackage</span></span>  
  
 <span data-ttu-id="9c559-168">**创建**</span><span class="sxs-lookup"><span data-stu-id="9c559-168">**Create**</span></span>  
 <span data-ttu-id="9c559-169">创建选定类型的 SAP Netweaver BW 对象。</span><span class="sxs-lookup"><span data-stu-id="9c559-169">Create the selected type of SAP Netweaver BW object.</span></span>  
  
|<span data-ttu-id="9c559-170">对象类型</span><span class="sxs-lookup"><span data-stu-id="9c559-170">Object Type</span></span>|<span data-ttu-id="9c559-171">结果</span><span class="sxs-lookup"><span data-stu-id="9c559-171">Result</span></span>|  
|-----------------|------------|  
|<span data-ttu-id="9c559-172">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="9c559-172">**InfoObject**</span></span>|<span data-ttu-id="9c559-173">通过使用 **“创建新 InfoObject”** 对话框创建一个新的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="9c559-173">Create a new InfoObject by using the **Create New InfoObject** dialog box.</span></span> <span data-ttu-id="9c559-174">有关此对话框的详细信息，请参阅 [Create New InfoObject](create-new-infoobject.md)。</span><span class="sxs-lookup"><span data-stu-id="9c559-174">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>|  
|<span data-ttu-id="9c559-175">**InfoCube**</span><span class="sxs-lookup"><span data-stu-id="9c559-175">**InfoCube**</span></span>|<span data-ttu-id="9c559-176">使用 **“创建事务数据的 InfoCube”** 对话框创建新的 InfoCube。</span><span class="sxs-lookup"><span data-stu-id="9c559-176">Create a new InfoCube by using the **Create InfoCube for Transaction Data** dialog box.</span></span> <span data-ttu-id="9c559-177">有关此对话框的详细信息，请参阅 [Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9c559-177">For more information about this dialog box, see [Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md).</span></span>|  
|<span data-ttu-id="9c559-178">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="9c559-178">**InfoSource**</span></span>|<span data-ttu-id="9c559-179">使用 **“创建 InfoSource”** 对话框，然后使用 **“创建事务数据的 InfoSource”** 或 **“创建主数据的 InfoSource”** 对话框创建一个新的 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="9c559-179">Create a new InfoSource by using the **Create InfoSource** dialog box, and then by using the **Create InfoSource for Transaction Data** or the **Create InfoSource for Master Data** dialog box.</span></span> <span data-ttu-id="9c559-180">有关这些对话框的详细信息，请参阅 [Create InfoSource](create-infosource.md), [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) 和 [Create InfoSource for Master Data](create-infosource-for-master-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9c559-180">For more information about these dialog boxes, see [Create InfoSource](create-infosource.md), [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) and [Create InfoSource for Master Data](create-infosource-for-master-data.md).</span></span>|  
|<span data-ttu-id="9c559-181">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="9c559-181">**InfoPackage**</span></span>|<span data-ttu-id="9c559-182">使用 **“创建 InfoPackage”** 对话框创建新的 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="9c559-182">Create a new InfoPackage by using the **Create InfoPackage** dialog box.</span></span> <span data-ttu-id="9c559-183">有关此对话框的详细信息，请参阅 [Create InfoPackage](create-infopackage.md)。</span><span class="sxs-lookup"><span data-stu-id="9c559-183">For more information about this dialog box, see [Create InfoPackage](create-infopackage.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c559-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c559-184">See Also</span></span>  
 <span data-ttu-id="9c559-185">[SAP BW 目标编辑器（“映射”页）](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="9c559-185">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="9c559-186">[SAP BW 目标编辑器（“错误输出”页）](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="9c559-186">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="9c559-187">[SAP BW 目标编辑器（“高级”页）](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="9c559-187">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="9c559-188">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="9c559-188">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
