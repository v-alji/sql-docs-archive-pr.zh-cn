---
title: SAP BW 目标 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a612ed91-b89b-4173-a0b1-0bce381e1e28
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a0d7c5b75da89e665dbe60bbd7e29ce74da67db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588679"
---
# <a name="sap-bw-destination"></a><span data-ttu-id="49ac1-102">SAP BW 目标</span><span class="sxs-lookup"><span data-stu-id="49ac1-102">SAP BW Destination</span></span>
  <span data-ttu-id="49ac1-103">SAP BW 目标是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的目标组件。</span><span class="sxs-lookup"><span data-stu-id="49ac1-103">The SAP BW destination is the destination component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="49ac1-104">因此，SAP BW 目标将来自 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包中数据流的数据加载到 SAP Netweaver BW 版本 7 系统。</span><span class="sxs-lookup"><span data-stu-id="49ac1-104">Thus, the SAP BW destination loads data from the data flow in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package into an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="49ac1-105">此目标具有一个输入和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="49ac1-105">This destination has one input and one error output.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="49ac1-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="49ac1-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="49ac1-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="49ac1-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="49ac1-108">若要使用 SAP BW 目标，必须执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="49ac1-108">To use the SAP BW destination, you have to do the following tasks:</span></span>  
  
-   [<span data-ttu-id="49ac1-109">准备 SAP Netweaver BW 对象</span><span class="sxs-lookup"><span data-stu-id="49ac1-109">Prepare the SAP Netweaver BW objects</span></span>](#bkmk_Prepare_Objects)  
  
-   [<span data-ttu-id="49ac1-110">连接至 SAP Netweaver BW 系统</span><span class="sxs-lookup"><span data-stu-id="49ac1-110">Connect to the SAP Netweaver BW system</span></span>](#bkmk_Connect_Database)  
  
-   [<span data-ttu-id="49ac1-111">配置 SAP BW 目标</span><span class="sxs-lookup"><span data-stu-id="49ac1-111">Configure the SAP BW destination</span></span>](#bkmk_Configure_Destination)  
  
##  <a name="preparing-the-sap-netweaver-bw-objects-that-the-destination-requires"></a><a name="bkmk_Prepare_Objects"></a> <span data-ttu-id="49ac1-112">准备目标所需的 SAP Netweaver BW 对象</span><span class="sxs-lookup"><span data-stu-id="49ac1-112">Preparing the SAP Netweaver BW Objects That the Destination Requires</span></span>  
 <span data-ttu-id="49ac1-113">SAP BW 目标要求 SAP Netweaver BW 系统中存在某些对象才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="49ac1-113">The SAP BW destination requires that certain objects are in the SAP Netweaver BW system before the destination can function.</span></span> <span data-ttu-id="49ac1-114">如果这些对象还不存在，必须按照下列步骤在 SAP Netweaver BW 系统中创建并配置这些对象。</span><span class="sxs-lookup"><span data-stu-id="49ac1-114">If these objects do not already exist, you have to follow these steps to create and configure these objects in the SAP Netweaver BW system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49ac1-115">有关这些对象和配置步骤的更多详细信息，请参阅 SAP Netweaver BW 文档。</span><span class="sxs-lookup"><span data-stu-id="49ac1-115">For additional details about these objects and these configuration steps, see the SAP Netweaver BW documentation.</span></span>  
  
1.  <span data-ttu-id="49ac1-116">创建新的源系统：</span><span class="sxs-lookup"><span data-stu-id="49ac1-116">Create a new Source System:</span></span>  
  
    1.  <span data-ttu-id="49ac1-117">选择类型， **“第三方/分级 BAPI”** 。</span><span class="sxs-lookup"><span data-stu-id="49ac1-117">Select the type, **"Third Party/Staging BAPIs"**.</span></span>  
  
    2.  <span data-ttu-id="49ac1-118">对于“与目标系统的通信类型”  ，选择“非 Unicode (非活动 MDMP 设置)”  。</span><span class="sxs-lookup"><span data-stu-id="49ac1-118">For **Communication Type with Target System**, select **Non-Unicode (Inactive MDMP Settings)**.</span></span>  
  
    3.  <span data-ttu-id="49ac1-119">分配适当的程序 ID。</span><span class="sxs-lookup"><span data-stu-id="49ac1-119">Assign an appropriate Program ID.</span></span>  
  
2.  <span data-ttu-id="49ac1-120">为 InfoSource 分配源系统。</span><span class="sxs-lookup"><span data-stu-id="49ac1-120">Assign the Source System to an InfoSource.</span></span>  
  
3.  <span data-ttu-id="49ac1-121">创建一个 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="49ac1-121">Create an InfoPackage.</span></span>  
  
     <span data-ttu-id="49ac1-122">该 InfoPackage 是 SAP BW 目标所需要的最重要的对象。</span><span class="sxs-lookup"><span data-stu-id="49ac1-122">The InfoPackage is the most important object that is required by the SAP BW destination.</span></span>  
  
 <span data-ttu-id="49ac1-123">您也可以创建为将数据加载到 SAP Netweaver BW 系统提供支持所需要的更多 InfoObject、InfoCube、InfoSource 和 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="49ac1-123">You can also create additional InfoObjects, InfoCubes, InfoSources, and InfoPackages that are required to support loading data into the SAP Netweaver BW system.</span></span>  
  
##  <a name="connecting-to-the-sap-netweaver-bw-system"></a><a name="bkmk_Connect_Database"></a> <span data-ttu-id="49ac1-124">连接至 SAP Netweaver BW 系统</span><span class="sxs-lookup"><span data-stu-id="49ac1-124">Connecting to the SAP Netweaver BW System</span></span>  
 <span data-ttu-id="49ac1-125">为连接到 SAP Netweaver BW 版本 7 系统，SAP BW 目标会使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 包中的 SAP BW 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="49ac1-125">To connect to the SAP Netweaver BW version 7 system, the SAP BW destination uses the SAP BW connection manager that is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package.</span></span> <span data-ttu-id="49ac1-126">SAP BW 连接管理器是 SAP BW 目标唯一可以使用的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="49ac1-126">The SAP BW connection manager is the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] connection manager that the SAP BW destination can use.</span></span>  
  
 <span data-ttu-id="49ac1-127">有关 SAP BW 连接管理器的详细信息，请参阅 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="49ac1-127">For more information about the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
##  <a name="configuring-the-sap-bw-destination"></a><a name="bkmk_Configure_Destination"></a> <span data-ttu-id="49ac1-128">配置 SAP BW 目标</span><span class="sxs-lookup"><span data-stu-id="49ac1-128">Configuring the SAP BW Destination</span></span>  
 <span data-ttu-id="49ac1-129">可以使用下列方式配置 SAP BW 目标：</span><span class="sxs-lookup"><span data-stu-id="49ac1-129">You can configure the SAP BW destination in the following ways:</span></span>  
  
-   <span data-ttu-id="49ac1-130">查找并选择用来加载数据的 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="49ac1-130">Look up and select the InfoPackage to use to load data.</span></span>  
  
-   <span data-ttu-id="49ac1-131">将数据流中的每个列映射到 InfoPackage 中相应的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="49ac1-131">Map each column in the data flow to the appropriate InfoObject in the InfoPackage.</span></span>  
  
-   <span data-ttu-id="49ac1-132">通过配置 `PackageSize` 属性指定将同时传输的数据行数。</span><span class="sxs-lookup"><span data-stu-id="49ac1-132">Specify how many rows of data will be transferred at a time by configuring the `PackageSize` property.</span></span>  
  
-   <span data-ttu-id="49ac1-133">选择等到 SAP Netweaver BW 系统完成数据加载。</span><span class="sxs-lookup"><span data-stu-id="49ac1-133">Choose to wait until the loading of data is completed by the SAP Netweaver BW system.</span></span>  
  
-   <span data-ttu-id="49ac1-134">选择不触发 InfoPackage，但要等待 SAP Netweaver BW 系统已开始数据加载的通知。</span><span class="sxs-lookup"><span data-stu-id="49ac1-134">Choose not to trigger the InfoPackage, but to wait for notification that the SAP Netweaver BW system has started the loading of data.</span></span>  
  
-   <span data-ttu-id="49ac1-135">（可选）完成数据加载后触发其他进程链。</span><span class="sxs-lookup"><span data-stu-id="49ac1-135">Optionally, trigger another process chain after the loading of data is completed.</span></span>  
  
-   <span data-ttu-id="49ac1-136">（可选）创建目标所需的 SAP Netweaver BW 对象。</span><span class="sxs-lookup"><span data-stu-id="49ac1-136">Optionally, create the SAP Netweaver BW objects that are required by the destination.</span></span> <span data-ttu-id="49ac1-137">这包括创建 InfoObject、InfoCube、InfoSource 和 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="49ac1-137">This includes creating InfoObjects, InfoCubes, InfoSources, and InfoPackages.</span></span>  
  
-   <span data-ttu-id="49ac1-138">使用您已选择的选项测试数据加载。</span><span class="sxs-lookup"><span data-stu-id="49ac1-138">Test the loading of data with the options that you have selected.</span></span>  
  
 <span data-ttu-id="49ac1-139">您还可以对目标的 RFC 函数调用启用日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="49ac1-139">You can also enable logging of RFC function calls by the destination.</span></span> <span data-ttu-id="49ac1-140">（此日志记录与可对 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包启用的可选日志记录是分开进行的。）配置目标将使用的 SAP BW 连接管理器时，会启用 RFC 函数调用的日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="49ac1-140">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) You enable logging of RFC function calls when you configure the SAP BW connection manager that the destination will use.</span></span> <span data-ttu-id="49ac1-141">有关如何配置 SAP BW 连接管理器的详细信息，请参阅 [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="49ac1-141">For more information about how to configure the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
 <span data-ttu-id="49ac1-142">如果您不知道配置目标所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="49ac1-142">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="49ac1-143">有关演示如何配置和使用 SAP BW 连接管理器、源和目标的演练，请参阅白皮书 [将 SQL Server 2008 Integration Services 与 SAP BI 7.0 一起使用](https://go.microsoft.com/fwlink/?LinkID=137090)。</span><span class="sxs-lookup"><span data-stu-id="49ac1-143">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="49ac1-144">此白皮书还说明如何在 SAP BW 中配置所需的对象。</span><span class="sxs-lookup"><span data-stu-id="49ac1-144">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-destination"></a><span data-ttu-id="49ac1-145">使用 SSIS 设计器配置目标</span><span class="sxs-lookup"><span data-stu-id="49ac1-145">Using the SSIS Designer to Configure the Destination</span></span>  
 <span data-ttu-id="49ac1-146">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的 SAP BW 目标属性的详细信息，请单击以下主题之一进行了解：</span><span class="sxs-lookup"><span data-stu-id="49ac1-146">For more information about the properties of the SAP BW destination that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="49ac1-147">SAP BW 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="49ac1-147">SAP BW Destination Editor &#40;Connection Manager Page&#41;</span></span>](sap-bw-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="49ac1-148">SAP BW 目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="49ac1-148">SAP BW Destination Editor &#40;Mappings Page&#41;</span></span>](sap-bw-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="49ac1-149">SAP BW 目标编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="49ac1-149">SAP BW Destination Editor &#40;Error Output Page&#41;</span></span>](sap-bw-destination-editor-error-output-page.md)  
  
-   [<span data-ttu-id="49ac1-150">SAP BW 目标编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="49ac1-150">SAP BW Destination Editor &#40;Advanced Page&#41;</span></span>](sap-bw-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="49ac1-151">在配置 SAP BW 目标的同时，您还可使用各种对话框查找或创建 SAP Netweaver BW 对象。</span><span class="sxs-lookup"><span data-stu-id="49ac1-151">While you are configuring the SAP BW destination, you can also use various dialog boxes to look up or to create SAP Netweaver BW objects.</span></span> <span data-ttu-id="49ac1-152">有关这些对话框的详细信息，请单击以下主题之一进行了解：</span><span class="sxs-lookup"><span data-stu-id="49ac1-152">For more information about these dialog boxes, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="49ac1-153">查找 InfoPackage</span><span class="sxs-lookup"><span data-stu-id="49ac1-153">Look Up InfoPackage</span></span>](look-up-infopackage.md)  
  
-   [<span data-ttu-id="49ac1-154">新建 InfoObject</span><span class="sxs-lookup"><span data-stu-id="49ac1-154">Create New InfoObject</span></span>](create-new-infoobject.md)  
  
-   [<span data-ttu-id="49ac1-155">创建事务数据的 InfoCube</span><span class="sxs-lookup"><span data-stu-id="49ac1-155">Create InfoCube for Transaction Data</span></span>](create-infocube-for-transaction-data.md)  
  
-   [<span data-ttu-id="49ac1-156">查找 InfoObject</span><span class="sxs-lookup"><span data-stu-id="49ac1-156">Look Up InfoObject</span></span>](look-up-infoobject.md)  
  
-   [<span data-ttu-id="49ac1-157">创建 InfoSource</span><span class="sxs-lookup"><span data-stu-id="49ac1-157">Create InfoSource</span></span>](create-infosource.md)  
  
-   [<span data-ttu-id="49ac1-158">创建事务数据的 InfoSource</span><span class="sxs-lookup"><span data-stu-id="49ac1-158">Create InfoSource for Transaction Data</span></span>](create-infosource-for-transaction-data.md)  
  
-   [<span data-ttu-id="49ac1-159">创建主数据的 InfoSource</span><span class="sxs-lookup"><span data-stu-id="49ac1-159">Create InfoSource for Master Data</span></span>](create-infosource-for-master-data.md)  
  
-   [<span data-ttu-id="49ac1-160">创建 InfoPackage</span><span class="sxs-lookup"><span data-stu-id="49ac1-160">Create InfoPackage</span></span>](create-infopackage.md)  
  
## <a name="see-also"></a><span data-ttu-id="49ac1-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49ac1-161">See Also</span></span>  
 [<span data-ttu-id="49ac1-162">Microsoft Connector 1.1 for SAP BW 组件</span><span class="sxs-lookup"><span data-stu-id="49ac1-162">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
