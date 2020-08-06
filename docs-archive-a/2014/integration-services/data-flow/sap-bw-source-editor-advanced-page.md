---
title: SAP BW 源编辑器（“高级”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 44f3c991-9e8f-4126-a9a2-2d9da779fb11
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c78d40555a30031bf39abda18048fda9c648d01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693011"
---
# <a name="sap-bw-source-editor-advanced-page"></a><span data-ttu-id="5d01c-102">SAP BW 源编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="5d01c-102">SAP BW Source Editor (Advanced Page)</span></span>
  <span data-ttu-id="5d01c-103">使用“SAP BW 源编辑器”的“高级”页指定字符串转换规则和超时时间，还可重置特定请求 ID 的状态。  </span><span class="sxs-lookup"><span data-stu-id="5d01c-103">Use the **Advanced** page of the **SAP BW Source Editor** to specify the string conversion rule and the time-out period, and also to reset the status of a particular Request ID.</span></span>  
  
 <span data-ttu-id="5d01c-104">若要了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 源组件的详细信息，请参阅 [SAP BW 源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="5d01c-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5d01c-105">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="5d01c-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="5d01c-106">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="5d01c-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5d01c-107">从 SAP Netweaver BW 提取数据要求额外的 SAP 许可。</span><span class="sxs-lookup"><span data-stu-id="5d01c-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="5d01c-108">请向 SAP 核实以便确认这些要求。</span><span class="sxs-lookup"><span data-stu-id="5d01c-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="5d01c-109">**打开“连接管理器”页**</span><span class="sxs-lookup"><span data-stu-id="5d01c-109">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="5d01c-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="5d01c-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="5d01c-111">在“数据流”  选项卡上，双击“SAP BW 源”。</span><span class="sxs-lookup"><span data-stu-id="5d01c-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="5d01c-112">在 **“SAP BW 源编辑器”** 中单击 **“高级”** ，以打开编辑器的 **“高级”** 页。</span><span class="sxs-lookup"><span data-stu-id="5d01c-112">In the **SAP BW Source Editor**, click **Advanced** to open the **Advanced** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5d01c-113">选项</span><span class="sxs-lookup"><span data-stu-id="5d01c-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d01c-114">如果您不知道配置源所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="5d01c-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="5d01c-115">**字符串转换**</span><span class="sxs-lookup"><span data-stu-id="5d01c-115">**String Conversion**</span></span>  
 <span data-ttu-id="5d01c-116">指定要应用的字符串转换规则。</span><span class="sxs-lookup"><span data-stu-id="5d01c-116">Specify the rule to apply for string conversion.</span></span>  
  
|<span data-ttu-id="5d01c-117">选项</span><span class="sxs-lookup"><span data-stu-id="5d01c-117">Option</span></span>|<span data-ttu-id="5d01c-118">说明</span><span class="sxs-lookup"><span data-stu-id="5d01c-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5d01c-119">**自动字符串转换**</span><span class="sxs-lookup"><span data-stu-id="5d01c-119">**Automatic string conversion**</span></span>|<span data-ttu-id="5d01c-120">当 SAP Netweaver BW 系统为 Unicode 系统时，将所有字符串转换为 `nvarchar`。</span><span class="sxs-lookup"><span data-stu-id="5d01c-120">Convert all strings to `nvarchar` when the SAP Netweaver BW system is a Unicode system.</span></span> <span data-ttu-id="5d01c-121">否则，将所有字符串转换为 `varchar`。</span><span class="sxs-lookup"><span data-stu-id="5d01c-121">Otherwise, convert all strings to `varchar`.</span></span>|  
|<span data-ttu-id="5d01c-122">**将字符串转换为 varchar**</span><span class="sxs-lookup"><span data-stu-id="5d01c-122">**Convert strings to varchar**</span></span>|<span data-ttu-id="5d01c-123">将所有字符串转换为 `varchar`。</span><span class="sxs-lookup"><span data-stu-id="5d01c-123">Convert all strings to `varchar`.</span></span>|  
|<span data-ttu-id="5d01c-124">**将字符串转换为 nvarchar**</span><span class="sxs-lookup"><span data-stu-id="5d01c-124">**Convert strings to nvarchar**</span></span>|<span data-ttu-id="5d01c-125">将所有字符串转换为 `nvarchar`。</span><span class="sxs-lookup"><span data-stu-id="5d01c-125">Convert all strings to `nvarchar`.</span></span>|  
  
 <span data-ttu-id="5d01c-126">**超时(秒)**</span><span class="sxs-lookup"><span data-stu-id="5d01c-126">**Timeout (seconds)**</span></span>  
 <span data-ttu-id="5d01c-127">指定源应等待的最大秒数。</span><span class="sxs-lookup"><span data-stu-id="5d01c-127">Specify the maximum number of seconds that the source should wait.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d01c-128">只有在编辑器的“连接管理器”页中选中“W - 等待通知”  作为“执行模式”  的值时，此选项才有效。 </span><span class="sxs-lookup"><span data-stu-id="5d01c-128">This option is only valid if you have selected **W - Wait for Notify** as the value of **Execution Mode** on the **Connection Manager** page of the editor.</span></span> <span data-ttu-id="5d01c-129">有关详细信息，请参阅 [SAP BW 源编辑器（“连接管理器”页）](sap-bw-source-editor-connection-manager-page.md)。</span><span class="sxs-lookup"><span data-stu-id="5d01c-129">For more information, see [SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md).</span></span>  
  
 <span data-ttu-id="5d01c-130">**请求 ID**</span><span class="sxs-lookup"><span data-stu-id="5d01c-130">**Request ID**</span></span>  
 <span data-ttu-id="5d01c-131">指定单击“重置”  时要将哪个请求 ID 的状态重置为“G - Green”。</span><span class="sxs-lookup"><span data-stu-id="5d01c-131">Specify the Request ID whose status you want to reset to "G - Green" when you click **Reset**.</span></span>  
  
 <span data-ttu-id="5d01c-132">**重置**</span><span class="sxs-lookup"><span data-stu-id="5d01c-132">**Reset**</span></span>  
 <span data-ttu-id="5d01c-133">在提示您进行确认后，可将指定请求 ID 的状态重置为“G - Green”。</span><span class="sxs-lookup"><span data-stu-id="5d01c-133">Lets you reset the status of the specified Request ID to "G - Green", after prompting you for confirmation.</span></span> <span data-ttu-id="5d01c-134">当发生问题时，SAP Netweaver BW 系统将请求的状态标记为黄色或红色状态，此时此功能十分有用。</span><span class="sxs-lookup"><span data-stu-id="5d01c-134">This can be useful when a problem has occurred, and the SAP Netweaver BW system has flagged the request with a yellow or red status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d01c-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d01c-135">See Also</span></span>  
 <span data-ttu-id="5d01c-136">[SAP BW 源编辑器（“连接管理器”页）](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="5d01c-136">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="5d01c-137">[SAP BW 源编辑器（“列”页）](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="5d01c-137">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="5d01c-138">[SAP BW 源编辑器（“错误输出”页）](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="5d01c-138">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="5d01c-139">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="5d01c-139">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
