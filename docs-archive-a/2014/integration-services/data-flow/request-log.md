---
title: 请求日志 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 165d3833-0493-490c-9f63-8a134a7fafb8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 024012878ae94c5ba6276648e289e6e6f7c93d7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579651"
---
# <a name="request-log"></a><span data-ttu-id="8d95b-102">请求日志</span><span class="sxs-lookup"><span data-stu-id="8d95b-102">Request Log</span></span>
  <span data-ttu-id="8d95b-103">使用 **“请求日志”** 对话框查看向 SAP Netweaver BW 系统提出样本数据请求的过程中记录的事件。</span><span class="sxs-lookup"><span data-stu-id="8d95b-103">Use the **Request Log** dialog box to view the events that are logged during the request that is made to the SAP Netweaver BW system for sample data.</span></span> <span data-ttu-id="8d95b-104">此信息可用于排除 SAP BW 源配置的故障。</span><span class="sxs-lookup"><span data-stu-id="8d95b-104">This information can be useful if you have to troubleshoot your configuration of the SAP BW source.</span></span>  
  
 <span data-ttu-id="8d95b-105">若要了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 源组件的详细信息，请参阅 [SAP BW 源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="8d95b-105">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8d95b-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="8d95b-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="8d95b-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="8d95b-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8d95b-108">从 SAP Netweaver BW 提取数据要求额外的 SAP 许可。</span><span class="sxs-lookup"><span data-stu-id="8d95b-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="8d95b-109">请向 SAP 核实以便确认这些要求。</span><span class="sxs-lookup"><span data-stu-id="8d95b-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="8d95b-110">**打开“请求日志”对话框**</span><span class="sxs-lookup"><span data-stu-id="8d95b-110">**To open the Request Log dialog box**</span></span>  
  
1.  <span data-ttu-id="8d95b-111">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="8d95b-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="8d95b-112">在“数据流”  选项卡上，双击“SAP BW 源”。</span><span class="sxs-lookup"><span data-stu-id="8d95b-112">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="8d95b-113">在 **“SAP BW 源编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="8d95b-113">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="8d95b-114">配置 SAP BW 源后，单击 **“预览”** ，预览 **“请求日志”** 对话框中的事件。</span><span class="sxs-lookup"><span data-stu-id="8d95b-114">After you configure the SAP BW source, click **Preview** to preview the events in the **Request Log** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8d95b-115">单击 **“预览”** 还将打开 **“预览”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="8d95b-115">Clicking **Preview** also opens the **Preview** dialog box.</span></span> <span data-ttu-id="8d95b-116">有关此对话框的详细信息，请参阅 [Preview](preview.md)。</span><span class="sxs-lookup"><span data-stu-id="8d95b-116">For more information about this dialog box, see [Preview](preview.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8d95b-117">选项</span><span class="sxs-lookup"><span data-stu-id="8d95b-117">Options</span></span>  
 <span data-ttu-id="8d95b-118">**时间**</span><span class="sxs-lookup"><span data-stu-id="8d95b-118">**Time**</span></span>  
 <span data-ttu-id="8d95b-119">显示所记录事件的时间。</span><span class="sxs-lookup"><span data-stu-id="8d95b-119">Displays the time that the event that was logged.</span></span>  
  
 <span data-ttu-id="8d95b-120">类型 </span><span class="sxs-lookup"><span data-stu-id="8d95b-120">**Type**</span></span>  
 <span data-ttu-id="8d95b-121">显示所记录事件的类型。</span><span class="sxs-lookup"><span data-stu-id="8d95b-121">Displays the type of the event that was logged.</span></span> <span data-ttu-id="8d95b-122">下表列出了可能的事件类型。</span><span class="sxs-lookup"><span data-stu-id="8d95b-122">The following table lists the possible event types.</span></span>  
  
|<span data-ttu-id="8d95b-123">值</span><span class="sxs-lookup"><span data-stu-id="8d95b-123">Value</span></span>|<span data-ttu-id="8d95b-124">说明</span><span class="sxs-lookup"><span data-stu-id="8d95b-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8d95b-125">S</span><span class="sxs-lookup"><span data-stu-id="8d95b-125">S</span></span>|<span data-ttu-id="8d95b-126">成功消息。</span><span class="sxs-lookup"><span data-stu-id="8d95b-126">Success message.</span></span>|  
|<span data-ttu-id="8d95b-127">E</span><span class="sxs-lookup"><span data-stu-id="8d95b-127">E</span></span>|<span data-ttu-id="8d95b-128">错误消息</span><span class="sxs-lookup"><span data-stu-id="8d95b-128">Error message</span></span>|  
|<span data-ttu-id="8d95b-129">W</span><span class="sxs-lookup"><span data-stu-id="8d95b-129">W</span></span>|<span data-ttu-id="8d95b-130">警告消息。</span><span class="sxs-lookup"><span data-stu-id="8d95b-130">Warning message.</span></span>|  
|<span data-ttu-id="8d95b-131">I</span><span class="sxs-lookup"><span data-stu-id="8d95b-131">I</span></span>|<span data-ttu-id="8d95b-132">信息性消息。</span><span class="sxs-lookup"><span data-stu-id="8d95b-132">Informational message.</span></span>|  
|<span data-ttu-id="8d95b-133">A</span><span class="sxs-lookup"><span data-stu-id="8d95b-133">A</span></span>|<span data-ttu-id="8d95b-134">操作已中止。</span><span class="sxs-lookup"><span data-stu-id="8d95b-134">The operation was aborted.</span></span>|  
  
 <span data-ttu-id="8d95b-135">**消息**</span><span class="sxs-lookup"><span data-stu-id="8d95b-135">**Message**</span></span>  
 <span data-ttu-id="8d95b-136">显示与记录事件相关联的消息文本。</span><span class="sxs-lookup"><span data-stu-id="8d95b-136">Displays the message text that is associated with the logged event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d95b-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d95b-137">See Also</span></span>  
 <span data-ttu-id="8d95b-138">[SAP BW 源编辑器（“连接管理器”页）](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="8d95b-138">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="8d95b-139">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="8d95b-139">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
