---
title: SAP BW 目标编辑器（“映射”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dfa1f1d6-6b64-4331-bdc5-eaa8b7aa41a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c4c2803be3e2649f7425a2974dae8ac0a80fae7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682980"
---
# <a name="sap-bw-destination-editor-mappings-page"></a><span data-ttu-id="55d83-102">SAP BW 目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="55d83-102">SAP BW Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="55d83-103">使用 **“SAP BW目标编辑器”** 的 **“映射”** 页将输入列映射到目标列。</span><span class="sxs-lookup"><span data-stu-id="55d83-103">Use the **Mappings** page of the **SAP BW Destination Editor** to map input columns to destination columns.</span></span>  
  
 <span data-ttu-id="55d83-104">若要了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目标的详细信息，请参阅 [SAP BW 目标](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="55d83-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="55d83-105">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="55d83-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="55d83-106">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="55d83-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="55d83-107">**打开“映射”页**</span><span class="sxs-lookup"><span data-stu-id="55d83-107">**To open the Mappings page**</span></span>  
  
1.  <span data-ttu-id="55d83-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 目标的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="55d83-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="55d83-109">在“数据流”  选项卡上，双击 SAP BW 目标。</span><span class="sxs-lookup"><span data-stu-id="55d83-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="55d83-110">在 **“SAP BW 目标编辑器”** 中单击 **“映射”** ，以打开编辑器的 **“映射”** 页。</span><span class="sxs-lookup"><span data-stu-id="55d83-110">In the **SAP BW Destination Editor**, click **Mappings** to open the **Mappings** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="55d83-111">选项</span><span class="sxs-lookup"><span data-stu-id="55d83-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55d83-112">如果您不知道配置目标所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="55d83-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="55d83-113">**“SAP BW 目标编辑器”** 的 **“映射”** 页包含两个部分：</span><span class="sxs-lookup"><span data-stu-id="55d83-113">The **Mappings** page of the **SAP BW Destination Editor consists** of two sections:</span></span>  
  
-   <span data-ttu-id="55d83-114">上面部分显示可用输入和目标列，您可以通过这个部分在这两类列之间创建映射。</span><span class="sxs-lookup"><span data-stu-id="55d83-114">The upper section shows the available input and destination columns and lets you create mappings between these two types of columns.</span></span>  
  
-   <span data-ttu-id="55d83-115">下面部分是一个表，其中列出哪些输入列已映射到哪些输出列。</span><span class="sxs-lookup"><span data-stu-id="55d83-115">The lower section is a table that lists which input columns have been mapped to which output columns.</span></span>  
  
### <a name="upper-section-options"></a><span data-ttu-id="55d83-116">上面部分的选项</span><span class="sxs-lookup"><span data-stu-id="55d83-116">Upper Section Options</span></span>  
 <span data-ttu-id="55d83-117">上面部分有以下选项：</span><span class="sxs-lookup"><span data-stu-id="55d83-117">The upper section has the following options:</span></span>  
  
 <span data-ttu-id="55d83-118">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="55d83-118">**Available Input Columns**</span></span>  
 <span data-ttu-id="55d83-119">查看可用输入列的列表。</span><span class="sxs-lookup"><span data-stu-id="55d83-119">View the list of available input columns.</span></span>  
  
 <span data-ttu-id="55d83-120">要将输入列映射到目标列，请将 **“可用输入列”** 列表中的列拖放到 **“可用目标列”** 列表中的列上。</span><span class="sxs-lookup"><span data-stu-id="55d83-120">To map an input column to a destination column, drag a column from the **Available Input Columns** list and drop that column onto a column in the **Available Destination Columns** list.</span></span>  
  
 <span data-ttu-id="55d83-121">**可用目标列**</span><span class="sxs-lookup"><span data-stu-id="55d83-121">**Available Destination Columns**</span></span>  
 <span data-ttu-id="55d83-122">查看可用目标列的列表。</span><span class="sxs-lookup"><span data-stu-id="55d83-122">View the list of available destination columns.</span></span>  
  
 <span data-ttu-id="55d83-123">要将输入列映射到目标列，请将 **“可用输入列”** 列表中的列拖放到 **“可用目标列”** 列表中的列上。</span><span class="sxs-lookup"><span data-stu-id="55d83-123">To map an input column to destination column, drag a column from the **Available Input Columns** list and drop that column onto a column in the **Available Destination Columns** list.</span></span>  
  
 <span data-ttu-id="55d83-124">上面部分还有一个上下文菜单，您可以通过右键单击背景来打开。</span><span class="sxs-lookup"><span data-stu-id="55d83-124">The upper section also has a context menu that you can open by right-clicking on the background.</span></span> <span data-ttu-id="55d83-125">此上下文菜单包含以下选项：</span><span class="sxs-lookup"><span data-stu-id="55d83-125">This context menu contains the following options:</span></span>  
  
-   <span data-ttu-id="55d83-126">**选择所有映射**</span><span class="sxs-lookup"><span data-stu-id="55d83-126">**Select All Mappings**</span></span>  
  
-   <span data-ttu-id="55d83-127">**删除所选映射**</span><span class="sxs-lookup"><span data-stu-id="55d83-127">**Delete Selected Mappings**</span></span>  
  
-   <span data-ttu-id="55d83-128">**通过匹配名称映射项**</span><span class="sxs-lookup"><span data-stu-id="55d83-128">**Map Items by Matching Names**</span></span>  
  
### <a name="lower-section-columns"></a><span data-ttu-id="55d83-129">下面部分的列</span><span class="sxs-lookup"><span data-stu-id="55d83-129">Lower Section Columns</span></span>  
 <span data-ttu-id="55d83-130">下面部分是一个映射表，其中包含以下列：</span><span class="sxs-lookup"><span data-stu-id="55d83-130">The lower section is a table of the mappings, and has the following columns:</span></span>  
  
 <span data-ttu-id="55d83-131">**输入列**</span><span class="sxs-lookup"><span data-stu-id="55d83-131">**Input Column**</span></span>  
 <span data-ttu-id="55d83-132">查看您所选的输入列。</span><span class="sxs-lookup"><span data-stu-id="55d83-132">View the input columns that you have selected.</span></span>  
  
 <span data-ttu-id="55d83-133">要将不同输入列映射到相同目标列，请在该列表中选择不同输入列。</span><span class="sxs-lookup"><span data-stu-id="55d83-133">To map a different input column to the same destination column, select a different input column in the list.</span></span> <span data-ttu-id="55d83-134">要删除映射，请选择 \<ignore> 从输出中排除该输入列。</span><span class="sxs-lookup"><span data-stu-id="55d83-134">To remove a mapping, select **\<ignore>** to exclude the input column from the output.</span></span>  
  
 <span data-ttu-id="55d83-135">**目标列**</span><span class="sxs-lookup"><span data-stu-id="55d83-135">**Destination Column**</span></span>  
 <span data-ttu-id="55d83-136">查看每个可用目标列，而不管是否已对该列进行映射。</span><span class="sxs-lookup"><span data-stu-id="55d83-136">View each available destination column, regardless of whether that column is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d83-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55d83-137">See Also</span></span>  
 <span data-ttu-id="55d83-138">[SAP BW 目标编辑器（“连接管理器”页）](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="55d83-138">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="55d83-139">[SAP BW 目标编辑器（“错误输出”页）](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="55d83-139">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="55d83-140">[SAP BW 目标编辑器（“高级”页）](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="55d83-140">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="55d83-141">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="55d83-141">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
