---
title: SAP BW 目标编辑器（“高级”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 862957db-bbc6-4dda-bc0e-591457f1baa7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0c5ca943b804ad39cc391cb1cf7f06e056ddbe56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587515"
---
# <a name="sap-bw-destination-editor-advanced-page"></a><span data-ttu-id="376d1-102">SAP BW 目标编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="376d1-102">SAP BW Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="376d1-103">可以使用“SAP BW 目标编辑器”的“高级”页设置高级设置，如包大小和超时信息   。</span><span class="sxs-lookup"><span data-stu-id="376d1-103">Use the **Advanced** page of the **SAP BW Destination Editor** to set advanced settings such as package size and time-out information.</span></span>  
  
 <span data-ttu-id="376d1-104">若要了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目标的详细信息，请参阅 [SAP BW 目标](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="376d1-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="376d1-105">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="376d1-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="376d1-106">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="376d1-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="376d1-107">**打开“高级”页**</span><span class="sxs-lookup"><span data-stu-id="376d1-107">**To open the Advanced page**</span></span>  
  
1.  <span data-ttu-id="376d1-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="376d1-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="376d1-109">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="376d1-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="376d1-110">在 **“SAP BW 目标编辑器”** 中单击 **“高级”** ，以打开编辑器的 **“高级”** 页。</span><span class="sxs-lookup"><span data-stu-id="376d1-110">In the **SAP BW Destination Editor**, click **Advanced** to open the **Advanced** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="376d1-111">选项</span><span class="sxs-lookup"><span data-stu-id="376d1-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="376d1-112">如果您不知道配置目标所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="376d1-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="376d1-113">**包大小**</span><span class="sxs-lookup"><span data-stu-id="376d1-113">**Package size**</span></span>  
 <span data-ttu-id="376d1-114">指定将同时传输的数据行数。</span><span class="sxs-lookup"><span data-stu-id="376d1-114">Specify how many rows of data will be transferred at a time.</span></span> <span data-ttu-id="376d1-115">此参数的最佳值取决于 SAP Netweaver BW 系统和可能发生的额外数据处理。</span><span class="sxs-lookup"><span data-stu-id="376d1-115">The optimal value for this parameter depends on the SAP Netweaver BW system and on additional processing of the data that might occur.</span></span> <span data-ttu-id="376d1-116">通常，2000 到 20000 之间的值能提供最佳性能。</span><span class="sxs-lookup"><span data-stu-id="376d1-116">Typically, values between 2000 and 20000 offer the best performance.</span></span>  
  
 <span data-ttu-id="376d1-117">**触发进程链**</span><span class="sxs-lookup"><span data-stu-id="376d1-117">**Trigger process chain**</span></span>  
 <span data-ttu-id="376d1-118">（可选）指定完成数据加载后要触发的进程链的名称。</span><span class="sxs-lookup"><span data-stu-id="376d1-118">(Optional) Specify the name of a process chain to be triggered after the loading of data is completed.</span></span>  
  
 <span data-ttu-id="376d1-119">**等待 InfoPackage 的超时时间**</span><span class="sxs-lookup"><span data-stu-id="376d1-119">**Timeout for waiting InfoPackage**</span></span>  
 <span data-ttu-id="376d1-120">指定目标应等待 InfoPackage 完成的最大秒数。</span><span class="sxs-lookup"><span data-stu-id="376d1-120">Specify the maximum number of seconds that the destination should wait for the InfoPackage to finish.</span></span>  
  
 <span data-ttu-id="376d1-121">**等待数据传输完成**</span><span class="sxs-lookup"><span data-stu-id="376d1-121">**Wait for data transfer to finish**</span></span>  
 <span data-ttu-id="376d1-122">指定目标是否应等待 SAP Netweaver BW 系统完成数据加载。</span><span class="sxs-lookup"><span data-stu-id="376d1-122">Specify whether the destination should wait until the SAP Netweaver BW system has finished loading the data.</span></span>  
  
 <span data-ttu-id="376d1-123">**不启动 InfoPackage (只等待)**</span><span class="sxs-lookup"><span data-stu-id="376d1-123">**No InfoPackage Start (Only Wait)**</span></span>  
 <span data-ttu-id="376d1-124">指定目标不触发 InfoPackage，而只是等待 SAP Netweaver BW 系统已开始加载数据的通知。</span><span class="sxs-lookup"><span data-stu-id="376d1-124">Specify that the destination does not trigger an InfoPackage, but just waits for notification that the SAP Netweaver BW system has started loading the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="376d1-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="376d1-125">See Also</span></span>  
 <span data-ttu-id="376d1-126">[SAP BW 目标编辑器（“连接管理器”页）](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="376d1-126">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="376d1-127">[SAP BW 目标编辑器（“映射”页）](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="376d1-127">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="376d1-128">[SAP BW 目标编辑器（“错误输出”页）](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="376d1-128">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="376d1-129">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="376d1-129">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
