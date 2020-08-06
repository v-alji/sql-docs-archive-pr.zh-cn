---
title: 查找 RFC 目标 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: db9404d8-4c42-45e5-a100-c7a84b056109
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 397298fce16509e667aa4baccaee62c6ff0f5cca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693413"
---
# <a name="look-up-rfc-destination"></a><span data-ttu-id="169a2-102">查找 RFC 目标</span><span class="sxs-lookup"><span data-stu-id="169a2-102">Look Up RFC Destination</span></span>
  <span data-ttu-id="169a2-103">使用 **“查找 RFC 目标”** 对话框查找在 SAP Netweaver BW 系统中定义的 RFC 目标。</span><span class="sxs-lookup"><span data-stu-id="169a2-103">Use the **Look Up RFC Destination** dialog box to look up an RFC destination that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="169a2-104">当可用 RFC 目标列表显示时，选择您需要的目标，然后组件将使用需要的值填充关联的选项。</span><span class="sxs-lookup"><span data-stu-id="169a2-104">When the list of available RFC destinations appears, select the destination that you want, and the component will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="169a2-105">SAP BW 源和 SAP BW 目标都使用 **“查找 RFC 目标”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="169a2-105">Both the SAP BW source and the SAP BW destination use the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="169a2-106">有关这些 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 组件的详细信息，请参阅 [SAP BW 源](sap-bw-source.md) 和 [SAP BW 目标](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="169a2-106">For more information about these components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md) and [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="169a2-107">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="169a2-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="169a2-108">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="169a2-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="169a2-109">**打开“查找 RFC 目标”对话框**</span><span class="sxs-lookup"><span data-stu-id="169a2-109">**To open the Look Up RFC Destination dialog box**</span></span>  
  
1.  <span data-ttu-id="169a2-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 源或目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="169a2-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source or destination.</span></span>  
  
2.  <span data-ttu-id="169a2-111">在“数据流”  选项卡上，双击 SAP BW 源或目标。</span><span class="sxs-lookup"><span data-stu-id="169a2-111">On the **Data Flow** tab, double-click the SAP BW source or destination.</span></span>  
  
3.  <span data-ttu-id="169a2-112">在 **“SAP BW 源编辑器”** 或 **SAP BW 目标编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="169a2-112">In the **SAP BW Source Editor** or the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="169a2-113">在 **“连接管理器”** 页上的 **“RFC 目标”** 组框中，单击 **“查找”** 显示 **“查找 RFC 目标”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="169a2-113">On the **Connection Manager** page, in the **RFC Destination** group box, click **Look up** to display the **Look Up RFC Destination** dialog box.</span></span>  
  
     <span data-ttu-id="169a2-114">在“SAP BW 源编辑器”中，仅当“执行模式”为“P - 触发进程链”或“W - 等待通知”时，“RFC 目标”组框才会显示。</span><span class="sxs-lookup"><span data-stu-id="169a2-114">In the **SAP BW Source Editor**, the **RFC Destination** group box appears only if the value for **Execution mode** is **P - Trigger process chain** or **W - Wait for notify**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="169a2-115">选项</span><span class="sxs-lookup"><span data-stu-id="169a2-115">Options</span></span>  
 <span data-ttu-id="169a2-116">**目标**</span><span class="sxs-lookup"><span data-stu-id="169a2-116">**Destination**</span></span>  
 <span data-ttu-id="169a2-117">查看在 SAP Netweaver BW 系统中定义的 RFC 目标的名称。</span><span class="sxs-lookup"><span data-stu-id="169a2-117">View the name of the RFC destination that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="169a2-118">**网关主机**</span><span class="sxs-lookup"><span data-stu-id="169a2-118">**Gateway Host**</span></span>  
 <span data-ttu-id="169a2-119">查看网关主机的服务器名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="169a2-119">View the server name or IP address of the gateway host.</span></span> <span data-ttu-id="169a2-120">通常，名称或 IP 地址与 SAP 应用程序服务器相同。</span><span class="sxs-lookup"><span data-stu-id="169a2-120">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="169a2-121">**网关服务**</span><span class="sxs-lookup"><span data-stu-id="169a2-121">**Gateway Service**</span></span>  
 <span data-ttu-id="169a2-122">查看网关服务的名称，格式为 `sapgwNN`，其中 `NN` 是系统编号。</span><span class="sxs-lookup"><span data-stu-id="169a2-122">View the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="169a2-123">**程序 ID**</span><span class="sxs-lookup"><span data-stu-id="169a2-123">**Program ID**</span></span>  
 <span data-ttu-id="169a2-124">查看与 RFC 目标关联的程序 ID。</span><span class="sxs-lookup"><span data-stu-id="169a2-124">View the Program ID that is associated with the RFC destination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="169a2-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="169a2-125">See Also</span></span>  
 <span data-ttu-id="169a2-126">[SAP BW 源编辑器（“连接管理器”页）](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="169a2-126">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="169a2-127">[SAP BW 目标编辑器（“连接管理器”页）](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="169a2-127">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="169a2-128">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="169a2-128">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
