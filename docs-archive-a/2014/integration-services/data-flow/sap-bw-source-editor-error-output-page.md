---
title: SAP BW 源编辑器（“错误输出”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a4ad2d02d3f5ec5c1a786019e18fa01665fdc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682977"
---
# <a name="sap-bw-source-editor-error-output-page"></a><span data-ttu-id="f1e3a-102">SAP BW 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="f1e3a-102">SAP BW Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="f1e3a-103">可以使用 **“SAP BW 源编辑器”** 的 **“错误输出”** 页选择错误处理选项，以及设置错误输出列的属性。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-103">Use the **Error Output** page of the **SAP BW Source Editor** to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="f1e3a-104">若要了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 源组件的详细信息，请参阅 [SAP BW 源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f1e3a-105">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="f1e3a-106">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f1e3a-107">从 SAP Netweaver BW 提取数据要求额外的 SAP 许可。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="f1e3a-108">请向 SAP 核实以便确认这些要求。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="f1e3a-109">**打开“错误输出”页**</span><span class="sxs-lookup"><span data-stu-id="f1e3a-109">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="f1e3a-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="f1e3a-111">在“数据流”  选项卡上，双击“SAP BW 源”。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="f1e3a-112">在 **“SAP BW 源编辑器”** 中单击 **“错误输出”** ，以打开编辑器的 **“错误输出”** 页。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-112">In the **SAP BW Source Editor**, click **Error Output** to open the **Error Output** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f1e3a-113">选项</span><span class="sxs-lookup"><span data-stu-id="f1e3a-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1e3a-114">如果您不知道配置源所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="f1e3a-115">**输入或输出**</span><span class="sxs-lookup"><span data-stu-id="f1e3a-115">**Input or Output**</span></span>  
 <span data-ttu-id="f1e3a-116">查看数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-116">View the name of the data source.</span></span>  
  
 <span data-ttu-id="f1e3a-117">**列**</span><span class="sxs-lookup"><span data-stu-id="f1e3a-117">**Column**</span></span>  
 <span data-ttu-id="f1e3a-118">查看在“SAP BW 源编辑器”对话框的“列”页上选择的外部（源）列。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-118">View the external (source) columns that you selected on the **Columns** page of the **SAP BW Source Editor** dialog box.</span></span> <span data-ttu-id="f1e3a-119">有关此对话框的详细信息，请参阅 [SAP BW 源编辑器（“列”页）](sap-bw-source-editor-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-119">For more information about this dialog box, see [SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md).</span></span>  
  
 <span data-ttu-id="f1e3a-120">**错误**</span><span class="sxs-lookup"><span data-stu-id="f1e3a-120">**Error**</span></span>  
 <span data-ttu-id="f1e3a-121">指定发生错误时 SAP BW 源组件应执行的操作：忽略错误、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-121">Specify what the SAP BW source component should do when there is an error: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="f1e3a-122">**截断**</span><span class="sxs-lookup"><span data-stu-id="f1e3a-122">**Truncation**</span></span>  
 <span data-ttu-id="f1e3a-123">指定发生截断时 SAP BW 源组件应执行的操作：忽略错误、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-123">Specify what the SAP BW source component should do when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="f1e3a-124">**说明**</span><span class="sxs-lookup"><span data-stu-id="f1e3a-124">**Description**</span></span>  
 <span data-ttu-id="f1e3a-125">查看对错误的说明。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-125">View the description of the error.</span></span>  
  
 <span data-ttu-id="f1e3a-126">**将此值设置到选定的单元格**</span><span class="sxs-lookup"><span data-stu-id="f1e3a-126">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="f1e3a-127">指定发生错误或截断时 SAP BW 源组件应对所有选定单元格执行的操作：忽略错误、重定向行或使组件失败。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-127">Specify what the SAP BW source component should do to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="f1e3a-128">**应用**</span><span class="sxs-lookup"><span data-stu-id="f1e3a-128">**Apply**</span></span>  
 <span data-ttu-id="f1e3a-129">将错误处理选项应用到选定的单元格。</span><span class="sxs-lookup"><span data-stu-id="f1e3a-129">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e3a-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1e3a-130">See Also</span></span>  
 <span data-ttu-id="f1e3a-131">[SAP BW 源编辑器（“连接管理器”页）](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="f1e3a-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="f1e3a-132">[SAP BW 源编辑器（“列”页）](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="f1e3a-132">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="f1e3a-133">[SAP BW 源编辑器（“高级”页）](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="f1e3a-133">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="f1e3a-134">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="f1e3a-134">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
