---
title: 查找进程链 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f6303ea4-fbbf-4cba-bc60-828df62be8c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e0d3743071d018a8a82f60eeaf04fd86dec3e63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689535"
---
# <a name="look-up-process-chain"></a><span data-ttu-id="4cf57-102">查找进程链</span><span class="sxs-lookup"><span data-stu-id="4cf57-102">Look Up Process Chain</span></span>
  <span data-ttu-id="4cf57-103">使用 **“查找进程链”** 对话框查找在 SAP Netweaver BW 系统中定义的进程链。</span><span class="sxs-lookup"><span data-stu-id="4cf57-103">Use the **Look Up Process Chain** dialog box to look up a process chain that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="4cf57-104">当可用进程链列表显示时，选择您需要的进程链，然后源将使用需要的值填充关联的选项。</span><span class="sxs-lookup"><span data-stu-id="4cf57-104">When the list of available process chains appears, select the chain that you want, and the source will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="4cf57-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 源使用 **“查找进程链”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="4cf57-105">The SAP BW source of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="4cf57-106">若要了解有关 SAP BW 源的详细信息，请参阅 [SAP BW Source](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="4cf57-106">To learn more about the SAP BW source, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4cf57-107">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="4cf57-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="4cf57-108">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="4cf57-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="4cf57-109">**打开“查找进程链”对话框**</span><span class="sxs-lookup"><span data-stu-id="4cf57-109">**To open the Look Up Process Chain dialog box**</span></span>  
  
1.  <span data-ttu-id="4cf57-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="4cf57-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="4cf57-111">在“数据流”  选项卡上，双击“SAP BW 源”。</span><span class="sxs-lookup"><span data-stu-id="4cf57-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="4cf57-112">在 **“SAP BW 源编辑器”** 中单击 **“连接管理器”** ，以打开编辑器的 **“连接管理器”** 页。</span><span class="sxs-lookup"><span data-stu-id="4cf57-112">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="4cf57-113">在 **“进程链”** 组框中，单击 **“查找”** 显示 **“查找进程链”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="4cf57-113">In the **Process Chain** group box, click **Look up** to display the **Look Up Process Chain** dialog box.</span></span>  
  
     <span data-ttu-id="4cf57-114">只有在“执行模式”为“P - 触发进程链”的情况下，“进程链”组框才会显示。   </span><span class="sxs-lookup"><span data-stu-id="4cf57-114">The **Process Chain** group box appears only if the value for **Execution mode** is **P - Trigger process chain**.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="4cf57-115">查找选项</span><span class="sxs-lookup"><span data-stu-id="4cf57-115">Lookup Options</span></span>  
 <span data-ttu-id="4cf57-116">在查找字段中，您可以使用星号通配符 (\*) 或使用部分字符串结合星号通配符来筛选结果。</span><span class="sxs-lookup"><span data-stu-id="4cf57-116">In the lookup fields, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="4cf57-117">但是，如果您将查找字段保留为空，则查找操作仅与该字段中的空字符串匹配。</span><span class="sxs-lookup"><span data-stu-id="4cf57-117">However, if you leave a lookup field empty, the lookup operation will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="4cf57-118">**进程链**</span><span class="sxs-lookup"><span data-stu-id="4cf57-118">**Process chain**</span></span>  
 <span data-ttu-id="4cf57-119">输入您要查找的进程链的名称，或输入部分名称加上星号通配符 (\*)。</span><span class="sxs-lookup"><span data-stu-id="4cf57-119">Enter the name of the process chain that you want to look up, or enter a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="4cf57-120">或者，仅使用星号通配符，以包括所有进程链。</span><span class="sxs-lookup"><span data-stu-id="4cf57-120">Or, use the asterisk wildcard character alone to include all process chains.</span></span>  
  
 <span data-ttu-id="4cf57-121">**查找**</span><span class="sxs-lookup"><span data-stu-id="4cf57-121">**Look up**</span></span>  
 <span data-ttu-id="4cf57-122">查找在 SAP Netweaver BW 系统中定义的匹配进程链。</span><span class="sxs-lookup"><span data-stu-id="4cf57-122">Look up matching process chains that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="4cf57-123">查找结果</span><span class="sxs-lookup"><span data-stu-id="4cf57-123">Lookup Results</span></span>  
 <span data-ttu-id="4cf57-124">单击“查找”按钮后，将在一个包含以下列标题的表中显示 SAP Netweaver BW 系统中进程链的列表。</span><span class="sxs-lookup"><span data-stu-id="4cf57-124">After you click the Look up button, a list of the process chains in the SAP Netweaver BW system appears in a table with the following column headings:</span></span>  
  
 <span data-ttu-id="4cf57-125">**“进程链”**</span><span class="sxs-lookup"><span data-stu-id="4cf57-125">**Process Chain**</span></span>  
 <span data-ttu-id="4cf57-126">显示在 SAP Netweaver BW 系统中定义的进程链的名称。</span><span class="sxs-lookup"><span data-stu-id="4cf57-126">Displays the name of the process chain that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="4cf57-127">**说明**</span><span class="sxs-lookup"><span data-stu-id="4cf57-127">**Description**</span></span>  
 <span data-ttu-id="4cf57-128">显示进程链的说明。</span><span class="sxs-lookup"><span data-stu-id="4cf57-128">Displays the description of the process chain.</span></span>  
  
 <span data-ttu-id="4cf57-129">当可用进程链列表显示时，选择您需要的进程链，然后源将使用需要的值填充关联的选项。</span><span class="sxs-lookup"><span data-stu-id="4cf57-129">When the list of available process chains appears, select the chain that you want, and the source will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf57-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4cf57-130">See Also</span></span>  
 <span data-ttu-id="4cf57-131">[SAP BW 源编辑器（“连接管理器”页）](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="4cf57-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="4cf57-132">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="4cf57-132">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
